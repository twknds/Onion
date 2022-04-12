자바 웹 프로그래밍 Next Step을 공부하기 위한 깃허브이다.

-------------------------------------

2022.4.12
2.3 문자열 계산기 구현

# 최초 구현 코드

## Main 코드
```java
import java.lang.String;

public class onion231 {
    private String arr;
    public static void main(String[] args){
        splits splits = new splits();
        splits.setter("//;\n1;2;3");
        //splits.setter("1,2,3");
        System.out.println(splits.add());
    }
    public onion231(String scan){
        arr = scan;
    }
}
```

## Split 코드

``` java
import java.lang.String;
import java.util.Arrays;

public class splits {
    public static String arr;
    public int add(){
        int sum=0;
        String[] answer;
        String ptrSpl = "[//\n]";
        String ptr = "[.,:";
        String[] arr2 = arr.split(ptrSpl); // "//" "\n"사이에 끼인 구분자를 색출하기 위한 split
        if( arr2.length==4) { //사이에 끼인 구분자가 존재할경우
            ptr += arr2[2] + "]";
            answer = arr2[3].split(ptr);
        }
        else{ //아닌경우 그냥 split된 arr2값을 넣으면된다
            answer = arr2;
        }
        for(int i =0;i<answer.length;i++){
            sum+=Integer.parseInt(answer[i]);
        }
        return sum;
    }
    public void setter(String arr){
        this.arr=arr;
    }
    public splits(){

    }
}
```

## Test 코드

``` java
import org.junit.Before;
import org.junit.Test;
import org.junit.jupiter.api.BeforeAll;

import static org.junit.jupiter.api.Assertions.*;

class onion231Test {
    splits splits;
    @Before
    public void Setup(){
        splits = new splits();
        splits.setter("1.2.3");
    }
    @Test
    public void test(){
        assertEquals(6,splits.add());
    }
}
```

# 리팩토링 코드

