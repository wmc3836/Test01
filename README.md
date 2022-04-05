# Test01
判断句子是否符合要求的语法结构
package day03;

import java.util.*;

public class Main {
    static Set<String> setA = new HashSet<>();
    static Set<String> setB = new HashSet<>();;
    static Set<String> setC = new HashSet<>();
    public static void main(String[] args){
        //获取开始时间
        long startTime = System.currentTimeMillis();

        Scanner sc = new Scanner(System.in);
        int numsA = sc.nextInt();//主语个数
        int numsB = sc.nextInt();//谓语个数
        int numsC = sc.nextInt();//宾语个数
        for(int i = 0; i < numsA;i++){
            setA.add(sc.next());
        }
        for(int i = 0; i < numsB;i++){
            setB.add(sc.next());
        }
        for(int i = 0; i < numsC;i++){
            setC.add(sc.next());
        }
        int n = sc.nextInt();//句子个数
        String[] strs = new String[n];
        for(int i = 0;i < n;i++){
            Scanner s = new Scanner(System.in);
            strs[i] = s.nextLine();
        }

        for(int i = 0;i < n;i++){
            System.out.println(isAvalible(strs[i]));
        }
        //获取结束时间
        long endTime = System.currentTimeMillis();
        System.out.println("程序运行时间： "+(endTime-startTime)+"ms");
    }
    public static String isAvalible(String str){
        String[] chs = str.split(" ");
        int len = chs.length;
        int[] used = new int[3];
        for(int i = 0;i < chs.length;i++){
            //第一个不是主语的情况,直接返回 No
            if(!setA.contains(chs[i]) && i == 0) return "No";
            else if(setA.contains(chs[i])){//是主语
                if(used[1] == 0)
                    continue;
                else
                    return "No";
            }
            else if(setB.contains(chs[i])){
                if(used[1] == 0){
                    used[1] = 1;
                    continue;
                }else{
                    return "No";
                }
            }else{
                if(used[1] == 1){
                    continue;
                }
                else
                    return "No";
            }
        }
        return used[1] == 1 ? "Yes" : "No";
    }
}
