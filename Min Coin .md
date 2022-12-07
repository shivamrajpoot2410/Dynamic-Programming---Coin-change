class Solution{
	public:
	int MinCoin(vector<int>nums, int amount)
	{
	    // Code here
	    int n=nums.size();
	    int dp[n+1][amount+1];
	    
	    for(int i=0; i<amount+1;i++)
	    {
	        dp[0][i]=INT_MAX - 1;
	    }
	    for(int j=0;j<n+1;j++)
	    {
	        dp[j][0]=0;
	    }
	    for(int i=1;i<n+1;i++)
	    {
	        for(int j=1;j<amount+1;j++)
	        {
	            if(nums[i-1]<=j)
	            {
	                dp[i][j]=min(dp[i-1][j], 1+dp[i][j-nums[i-1]]);
	            }
	            else
	            {
	                dp[i][j]=dp[i-1][j];
	            }
	        }
	    }
	    return dp[n][amount]!=INT_MAX-1?dp[n][amount]:-1;
	}
};
