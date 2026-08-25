---
title: about
date: 2026-08-25 07:24:08
type: "about"
---
## 简介
我是男的。

我X岁。

我是中国人。

新手
## 大事记
一周就被盗号。

三天成蓝名。

5.19 绿名！！！恩情
## 刷题日记
12.13
刷完一个题单

4.9

刷完两个题单

4.16

刷完三个题单

4.23

刷完四个题单

9.10

刷完第五个题单

## 比赛
csp-j 2025 三等奖 
## 古怪代码记录
记于4.22

为了做P1304，写的代码
```cpp
#include<bits/stdc++.h>
using namespace std;
long long a[1200099],b[10530];
void su(long long a[],int n){
	memset(a,0,sizeof(a)*(n+1));
	a[0]=a[1]=1;
	for(int i=2;i*i<=n;i++){
		if(a[i]==0){
			for(int j=i << 1;j<=n;j+=i){
				a[j]=1;
			}
		}
	}
	for(int i=0;i<=n;i++){
		if(!a[i]){
			b[i]=i;
		}
	}
}
int main()
{
	su(a,10900);
	int kk=0;
	int n;
	cin>>n;
	for(int i=1;i<=n;i++){
		kk=0;
		if(i%2==0&&i!=2){
			for(int j=0;j<i;j++){
				if(kk!=0) break;
				for(int h=0;b[j]+b[h]<=i;h++){
					if(b[j]+b[h]==i){
						cout<<i<<"="<<b[j]<<"+"<<b[h]<<endl;
						kk++;
					}
				}
			}
		}
	}
	return 0;
}
```
记于4.23
为了做一道贪心题，写的代码，比好的长几十倍。
```cpp
#include<bits/stdc++.h>
using namespace std;
int a[10000000],b[10000000];
double c[10000000];
int main(){
	int n,m;
	cin>>n>>m;
	for(int i=0;i<n;i++){
		cin>>a[i]>>b[i];
		c[i]=b[i]/(a[i]*1.0);
	}
	for(int i=0;i<n-1;i++){
		for(int i=0;i<n-1;i++){
	    	if(c[i]<c[i+1]){
	    		int temp=a[i];
	    		a[i]=a[i+1];
	    		a[i+1]=temp;
	    		temp=b[i];
	    		b[i]=b[i+1];
	    		b[i+1]=temp;
	    		double temp2=c[i];
	    		c[i]=c[i+1];
	    		c[i+1]=temp2;
			}
	    }
	}
	int kk=0;
	double ans=0;
	while(m>=a[kk]&&kk<n){
		ans+=b[kk];
		m-=a[kk];
		kk++;
	}
	if(kk>=n) kk=n;
	if(m!=0&&kk!=n) ans+=(b[kk]/(a[kk]*1.0))*m;
	printf("%.2lf",ans);
	return 0;
}
```
记与5.13

终于做出来了P2550
代码


------------
```cpp
#include<bits/stdc++.h>
using namespace std;
int ans[9],a[1006][9],n2[10];
int main()
{
	int n;
	cin>>n;
	for(int i=0;i<7;i++) cin>>ans[i];
	for(int i=0;i<n;i++){
		for(int j=0;j<7;j++){
			cin>>a[i][j];
		}
	}
	int ans1;
	for(int i=0;i<n;i++){
		ans1=0;
		for(int j=0;j<7;j++){
			for(int k=0;k<7;k++){
				if(ans[j]==a[i][k]){
					ans1++;
				}
			}
		}
		n2[ans1]++; 
	}
	cout<<n2[7]<<" ";
	for(int i=6;i>0;i--) cout<<n2[i]<<" ";
	return 0;
}
```
5.20
恶心！！！
做P1789所写的代码
```cpp
#include<bits/stdc++.h>
using namespace std;
int a[6000][6000];
//int h[26][26],y[6][6];
const int hdx[]={1,2,-1,-2,0,0,0,0,1,1,-1,-1};
const int hdy[]={0,0,0,0,1,2,-1,-2,-1,1,-1,1};
//const int ydx[]={}
int main()
{
	//memset('0',a,sizeof(a));
	int m,k,n;
	cin>>n>>m>>k;
	for(int i=0;i<m;i++){
		int hx,hy;
		cin>>hx>>hy;
		if(hx>=1&&hy>=1) a[hx][hy]=1;
	    for(int j=0;j<12;j++){
	   		if(hx+hdx[j]>=1&&hy+hdy[j]>=1) a[hx+hdx[j]][hy+hdy[j]]=1;
	   	}
	}
	for(int i=0;i<k;i++){
		int yx,yy;
		cin>>yx>>yy;
		if(yx>=1&&yy>=1) a[yx][yy]=1;
		for(int j=yx-2;j<=yx+2;j++){
	 	    for(int k=yy-2;k<=yy+2;k++){
		    	if(j>=1&&k>=1&&k<=n&&j<=n) a[j][k]=1;
	    	}
		}
	}
	int ans=0;
	for(int i=1;i<=n;i++){
		for(int j=1;j<=n;j++){
			if(a[i][j]==0) ans++;
		}
	}
	cout<<ans;
	return 0;
}
```
5.22

蛇形填数！amns
```cpp
#include<bits/stdc++.h>
//#include<windows.h>
using namespace std;
int a[1000][1000];
int n;
void print()
{
	/*for(int i=0;i<=n+1;i++){
		for(int j=0;j<=n+1;j++){
			cout<<a[i][j]<<" ";
		}
		cout<<'\n';
	}
	Sleep(500);*/
}
int main()
{
	cin>>n;
	for(int i=0;i<=n+1;i++){
		for(int j=0;j<=n+1;j++){
			if(i!=0&&i!=n+1){
				if(j==0||j==n+1) a[i][j]=90;
				else a[i][j]=0;
			}
			else{
				a[i][j]=90;
			}
		}
	}
	print();
	int k=1,i=1,j=1;//temp=0;;
	while(k<=n*n){
		//temp%=4;
		while(a[i][j]==0){
			a[i][j]=k;
			j++;
		    k++;
		}
	    j--;
	    i++;
		print();
		while(a[i][j]==0){
			a[i][j]=k;
			i++;
			k++;	
		}
		i--;
		j--;
		print();
		while(a[i][j]==0){
			a[i][j]=k;
			j--;
			//cout<<i<<'\n';
			k++;
		}
		j++;
		i--;
		print();
		while(a[i][j]==0){
			a[i][j]=k;
			k++;
			i--;
		}
		i++;
		j++;
		print();
	}
	for(int i=1;i<=n;i++){
		for(int j=1;j<=n;j++){
			if(j==1) cout<<" ";
			if(a[i][j]<10) cout<<" "<<a[i][j]<<" ";
			else cout<<a[i][j]<<" ";
		}
		cout<<'\n';
	}
	return 0;
}
```

2025.9.11

今天是个不吉利的日子

写P1068做的，笑

```cpp
#include<bits/stdc++.h>
using namespace std;
struct name{
	long long k;
	long long s;
}a[10000];
bool cmp(name a,name b){
	if(a.s!=b.s) return a.s>b.s;
	return a.k<b.k;
}
int main(){
	long long n,m,temp;
	cin>>n>>m;
	double p=1.5*m;
	temp=floor(p);
	for(int i=0;i<n;i++){
		cin>>a[i].k>>a[i].s;
	}
	sort(a,a+n,cmp);
	m=0;
	long long i=0;
	while(a[i].s>=a[temp-1].s){
		m++;
		i++;
	}
	i=0;
	cout<<a[m-1].s<<" "<<m<<'\n';
	while(a[i].s>=a[m-1].s){
		cout<<a[i].k<<" "<<a[i].s<<'\n';
		i++;
	}
	return 0;
}
```

## 注
你猜我玩什么游戏
