# My-LeetCode
LeedCode第三题

class Solution {
    public int lengthOfLongestSubstring(String s) {
      if(s == null){
          return 0;
      }
        int result = 0;
        int start = 0;
        Map<Character,Integer> map = new HashMap<>(s.length());
        for(int i = 0 ; i < s.length() ; i++){
             char ch = s.charAt(i);
            if(map.containsKey(ch) && map.get(ch) >= start){
                start = map.get(ch) + 1;
            }else{
                result = Math.max(result , i - start + 1);
            }
            map.put(ch , i);
        }
        return result;
        
    }
}

我是看了别人写的运用窗口滑动，比较窗口的大小。
将字符串的每一个字符和其所在的位置存在一个HashMap中
首先设置窗口的起点为start = 0，start就是窗口的最左端，遍历字符串的位置就是窗口的最右端，最后不断更新i - start + 1,得到最大的窗口长度即可。
