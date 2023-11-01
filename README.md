# Binary_Search_in_rotated_sorted_array leetcode question no= 33

class Solution {
public:
    int findpivitindex(vector<int>& arr) {
        int n = arr.size();
        int s=0;
        int e=n-1;
        int mid = s+ (e-s)/2;
        while(s<=e){
            if(s==e){
                return s;
            }
            else if(mid +1 <n && arr[mid]> arr[mid+1]){
                return mid;
            }
            else if(mid -1 >0 && arr[mid]<arr[mid-1]){
                return mid -1;
            }
            else if(arr[s]>arr[mid]){
                e= mid -1;
            }
            else{
                s= mid +1;
             }
             mid = s+ (e-s)/2;
        }return -1;
    }
    int binarysearch(vector<int>& arr, int s, int e, int target){
        int mid = s + (e-s)/2;
        while(s<=e){
            if(arr[mid]== target){
                return mid;
            }
            else if(arr[mid]> target){
                e = mid -1;
            }
            else{
                s= mid +1;
            }
            mid = s+ (e-s)/2;
        }return -1;
    }
    int search(vector<int>& nums,int target){
        int pivit = findpivitindex(nums);
        int n = nums.size();
        int ans = -1;
        if(target>=  nums[0] && target <= nums[pivit]){
            ans = binarysearch(nums , 0, pivit, target);
        }
        else {
            ans = binarysearch(nums, pivit + 1 , n-1 , target);
        }
        return ans;


    }

};
