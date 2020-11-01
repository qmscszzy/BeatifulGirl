# BeatifulGirl

### A special gift

``` cpp

#include<bits/stdc++.h>
using namespace std;
struct e{
	int to;
	int next;
}eg[100001];
int head[100001];
int xx,yy;
int m,n;
int tot;
int nu;
int df[100001],lo[100001];
int Co[100001];
int co;
int ans;
stack <int> s;
void add(int x,int y)
{
	eg[++tot].next=head[x];
	head[x]=tot;
	eg[tot].to=y;	
}
int Tj(int t)
{
	df[t]=lo[t]=++nu;
	s.push(t);
	for(int i=head[t];i;i=eg[i].next)
	    {
	    	if(!df[eg[i].to])
		       {
		    	Tj(eg[i].to);	
		    	lo[t]=min(lo[t],lo[eg[i].to]);	
		       }
		    else
		       if(!Co[eg[i].to])
		          lo[t]=min(lo[t],df[eg[i].to]);
	    }
	if(lo[t]==df[t])
	   {
	   	Co[t]=++co;
	   	if(s.top()!=t)
	   	ans++;
	   	while(s.top()!=t)
	   	      {
	   	      	Co[s.top()]=co;
	   	      	printf("%d ",s.top());
	   	      	s.pop();
	   	      }
	   	      printf("%d\n",s.top());
	   	      s.pop();
	   }
	
	
	
}
int main()
{
	scanf("%d%d",&n,&m);
	for(int i=1;i<=m;i++)
	    {
	    	scanf("%d%d",&xx,&yy);
	    	add(xx,yy);
	    }
	Tj(1);
	printf("%d",ans);
}

```
