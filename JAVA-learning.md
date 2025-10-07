<div style="text-align:center;">
    <h1 style="font-family: 'STSong', 'SimSun', serif; font-weight: normal;">JAVA-learning</h1>
    <p style="font-family:  serif;">Jerry</p>
</div>

## 小技巧

1. 快速生成代码
   - `main`: 快速生成` public static void main(String[] args) {} `方法。
   - `sout`: 快速生成`System.out.println()`;。
   - `num.fori`: 对数组或集合`num` 快速生成 `for (int i = 0; i < num.length; i++) {}`循环。
   - `coll.for`: 对集合 `coll` 快速生成增强 for 循环 `for(String s:coll){}`。
2. 代码导航与查看
   - `Alt+Insert` (或 `Alt+Ins`): 在类中快速生成构造方法、`getter/setter`，`Tostring`，`equals`，`Hashcode`等。
   - `Ctrl+P`: 在调用方法或构造函数的括号内，查看需要传入的参数类型和信息。
   - `Ctrl+Click`: 跳转到变量或方法的定义处（进入源码）。
   - `Ctrl+Alt+左右箭头`: 在上次和下次光标位置之间快速切换，便于源码阅读。
   - `Ctrl+F12`: 查看当前类中所有的方法和成员变量的结构。
   - `Ctrl+N`: 在整个项目中按名称查找类。
   - `Alt+7`: 查看当前类的完整结构图（方法、字段等）。

| 场景                               | 需要重写的方法                     | 目的                               |
| :--------------------------------- | :--------------------------------- | ---------------------------------- |
| 哈希集合（HashSet）                | `equals() `和 `hashCode()`         | 正确判断元素是否重复               |
| 自然排序（TreeSet）                | `compareTo()`（来自 `Comparable`） | 定义对象的默认排序规则             |
| 自定义排序（TreeSet，Arrays.sort） | `compare()`（来自 `Comparator`）   | 提供临时的、外部的或备用的排序规则 |
| 打印对象/字符串拼接                | `toString()`                       | 提供有意义的字符串表示，便于调试   |
| 对象克隆                           | `clone()`                          | 提升可见性并实现深/浅克隆          |







![步骤一:项目](https://s21.ax1x.com/2025/09/07/pV25HSK.png)
![步骤二：模块](https://s21.ax1x.com/2025/09/07/pV25qyD.png)
![步骤三：包类似文件夹](https://s21.ax1x.com/2025/09/07/pV25XeH.png)



不要在外面创建文件夹，再打开文件夹，不然目录结构会很诡异，你直接在这个idea新建项目就好了      

接下来就是我们创建的文件即java文件(类)


```java
public class Main {
    public static void main(String[] args) {
        System.out.print("Hello and welcome!");
    }
}
```

对于java来说，万物皆可以看做class，因此他和cpp最大区别，就是他使用的不是int main()
在这段代码里public class 后面所加的类必须和文件名相同即Main.java
这里的`public static void main(String[] args)`就等价于 `int main()`

---

\t 这个会自动将字符串补齐八格，而字符串连接需要使用加号
    `System.out.print()`： 打印内容，但不在结尾换行。下一个输出会紧接在这次输出的后面。
    `System.out.println()`： 打印内容，并在结尾自动添加一个换行符。**下一个输出会从新的一行开始**。

```java
public class Main {
    public static void main(String[] args) {
        System.out.print("Hello and welcome!"+"this\t is java");
    }
}
//输出如Hello and welcome!this     is java
```

对于浮点数据类型也有所不同
**float类型后面要加个F,比如下方,double不需要**
**long类型后面加个L**
并且java里面没有bool，而是用boolean代替bool,值是true或false

```java
public class Main {
    public static void main(String[] args) {
        float a= 1.2F;
        System.out.println(a);  
    }
}
//输出为1.2
```

对于数据读取，python使用a=input("某些提示语"),cpp使用cin>>,而java比较复杂
>​      这里`nextInt()用于读取整数，对应的还有nextDouble(),next()用于读取字符串`但他们都有一个共同特点，就是遇到空格或者回车就自动中断读取内容，对此`nextLine()`读取字符串遇到回车才终止，但是`next()`的方法有一个好处，就是他对于开头的空白符会选择忽略，直到非空白符出现才开始录入，这对于连续录入中间的空格回车来说，是不会影响下一个的`next()`的读取的（会忽略），而`nextline()`则不是，他会直接读入回车和空格作为空字符
>
>​	但是这里的next()遇到空格和回车都会停止读入，只是在下一个next读取时会忽略空格回车，而nextline遇到空格会继续读，只有遇到回车符才会停止。
```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner src=new Scanner(System.in);
        System.out.println("请输入一个数字。");
        int number=src.nextInt();
        System.out.println(number);
    }
}

//输入111
//输出111
```


对于字符串加减
```java
public class Main {
    public static void main(String[] args) {
        float a= 1.2F;
        System.out.println("abc" + a + 1 + true );
    }
}

//输出abc1.21a
```

在java中的与或使用的是&&和||,没错均为两个这才能达到c的短路效果即只有一个不满足不会判断后者，直接结束，如果有一个满足就不看后面的

使用的是else if不是elif

switch(语句变量){
    case 值1:
        xxx
        break;
    default:
        xxxx
        break;
}

```java
public class ModernSwitchDemo {
    public static void main(String[] args) {
        int day = 3;

        // 直接将 switch 表达式的结果赋值给变量
        String dayName = switch (day) {
            case 1 -> "星期一";
            case 2 -> "星期二";
            case 3 -> "星期三";
            case 4 -> "星期四";
            case 5 -> "星期五";
            case 6 -> {
                System.out.println("今天是周六，要加班！");
                // 使用 yield 返回值
                yield "星期六";
            }
            case 7 -> "星期日";
            default -> "无效的日期";
        };

        System.out.println(dayName); // 输出: 星期三
    }
}
//这里的->就默认了break
```
---
数组定义方式也和c不一样，左边有方括号，右边有new  xxx[]{}
```java
int[] arr1=new int[]{1,2,3};
int[] arr2={4,5,6};
String[] arr3=new String[]{"abc","def"};
String[] arr4={"wafaf"};
```
动态定义数组
```java
int[] arr5=new int[5];

```
在java中将函数称作方法
不用def，而是 `public static void(可替换) 方法名(){}`的形式
==在包里的（一个文件夹）里的不同类可以互相调用==

random随机数的生成,使用Random
```java
Random sc=new Random();
result=sc.nextInt(10);
//表示生成0-9随机数
```

在java中类的位置和c不同，c是类一般在main函数外面，两者是独立的，但是java中一般是以文件名作为public 类名称，并且只允许出现这一个public 类，但是可以有其他的class类（不是public），而且main函数一定位于class类内部，可以调用这个类

使用this类指代成员变量

构造方法
使用public 加类名(){}进行定义，初始化会自动调用


---
字符串创建方法(可利用字符数组转换为字符串)
```java
char[] ch={'a','b','c'};
String str=new String(ch);
//会将字符数组变成字符串
byte[] bytes={97,98,99};
String str=new String(bytes);
//先根据ascii码转换成字符再变字符串
```
[![pVW2csH.png](https://s21.ax1x.com/2025/09/13/pVW2csH.png)](https://imgse.com/i/pVW2csH)

对于字符串直接比较比如 `a==b` 比较的是地址,而使用`a.equal(b)`只比较值，而`a.equalsIgnoreCase()`比较的是忽略大小写的值
对于cpp的字符串索引直接用s[i]。但是java使用s.charAt(i)表示索引

`substring(a,b)`表示从第a个字符开始不包含第b个，左闭右开，
`substring(a)`表示从第a个开始到结尾最后一个（包含在内）
例如`string.substring(0,3)`即第0与1与2个字符
`replace("","")`前面为被替换内容，后者为替换成的内容，此处前面输入的为自动查找，只要符合都会被替换

```java
package practice;

import java.util.Scanner;

public class prc_02 {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        String str=sc.next();
        String result=new StringBuilder().append(str).reverse().toString();
        System.out.println(str.equals(result));

    }
}

```
上方代码出现的StringBuilder对应的就是cpp数据结构里面的string，具有很多封装好的函数
`append()` `reverse()` `toString()`这些就是你想的那些用法，拼接，翻转，转换为字符串。cpp的string更像是把这两者融合一起，既有形式又有封装的方法，所以貌似没有tostring的必要，也不像java两个分离出来
对于字符串还有转换成字符数组的方式toCharArray()
```java
public class StringJoinerDemo2 {
    public static void main(String[] args) {

        StringJoiner sj = new StringJoiner(", ", "[", "]");

        sj.add("aaa").add("bbb").add("ccc");

        int len = sj.length();
        System.out.println(len);

        System.out.println(sj); // 输出：[aaa, bbb, ccc]
        String str = sj.toString();
        System.out.println(str); // 输出：[aaa, bbb, ccc]
    }
}
```
上方的代码使用了`StringJoiner()`它最主要的用法就是在各个字符间添加分割符，如果只填一个字符就是作为分隔符，如果是`StringJoiner("[",",","]")`那么第一个是前缀，第二个是分隔符，第三个是后缀。
我觉得这个更偏向于stringbuilder的补充用法
他的`add()`对应`append()` 

接下来新的一个数据结构arraylist，很大程度上极其类似cpp的vector

[![pV7JTn1.png](https://s21.ax1x.com/2025/10/06/pV7JTn1.png)](https://imgse.com/i/pV7JTn1)

```java
import java.util.ArrayList;
import java.util.List;

public class ArrayListSimpleExample {

    public static void main(String[] args) {
        
        ArrayList<String> fruits = new ArrayList<>();

        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Orange");

        int listSize = fruits.size();

        String secondFruit = fruits.get(1);

        String oldFruit = fruits.set(2, "Grape");

        String removedByIndex = fruits.remove(0);

        boolean isRemoved = fruits.remove("Grape");
        
        ArrayList<String> fruits2 = new ArrayList<>();
        fruits2.add("Banana");
        fruits2.add("Orange");
        
        fruits.addAll(fruits2);
    }
}
```
上方代码的`add()`实现添加功能，`get`则为索引对应内容，`set`会覆盖对应索引内容，`remove`可移除对应索引或者内容

`addAll()`可以一次添加多个数据

![pVhby6A.png](https://s21.ax1x.com/2025/09/19/pVhby6A.png)
但它与cpp定义的时候有不同的地方

==这里的右侧注意了,是基本数据类型包装的类（对象)不是所谓的123这种数据，而是一个封装好的对象，当方法需要传入对象但实际内容是int时，你用的就是`Integer`==

---
### 静态
关于static的用法：
- 首先是静态变量，在定义`static public int a=10`时意味着这个变量将会是整个类共享的，不管你定义多少个对象，他的值均相同，并且如果使用它的时候不需要new一个对象，可以直接通过类名调用
  [![pV4XkIx.png](https://s21.ax1x.com/2025/09/22/pV4XkIx.png)](https://imgse.com/i/pV4XkIx)

- 然后是静态方法
  静态方法往往是可以直接使用静态方法静态变量，但不是说不能使用非静态方法比如`public void transport()`这种，他需要先初始化对象然后通过对象调用,main本身也是静态方法，当然如果静态变量和静态方法就是main所在类的话，直接用就行（默认有this），非静态方法与变量（不管是否为当前类均需初始化才能调用）


```java
// 其他类
class Utility {
    // 静态方法
    public static void staticHelper() {
        System.out.println("这是Utility类的静态方法");
    }
    
    // 实例方法
    public void instanceHelper() {
        System.out.println("这是Utility类的实例方法");
    }
}

// 主类
public class MainExample {
    // 当前类的静态方法
    public static void myStaticMethod() {
        System.out.println("这是MainExample类的静态方法");
    }
    
    // 当前类的实例方法
    public void myInstanceMethod() {
        System.out.println("这是MainExample类的实例方法");
    }
    
    public static void main(String[] args) {
        // 1. 调用当前类的静态方法 - 直接使用
        myStaticMethod();
        
        // 2. 调用其他类的静态方法 - 类名.方法名
        Utility.staticHelper();
        
        // 3. 调用当前类的实例方法 - 先new再使用
        MainExample obj = new MainExample();
        obj.myInstanceMethod();
        
        // 4. 调用其他类的实例方法 - 先new再使用
        Utility util = new Utility();
        util.instanceHelper();

```
---

### 继承
`public class Student extends Person{}`使用`extends`表示继承，前者为子类，后者为父类，一个类只能继承一个父类，但可以多层继承，父类还有自己的父类，并且每个没有继承的类默认继承object类

子类继承父类后不再需要之前的静态或者非静态的调用方法，直接使用即可

当使用父类或者间接父类的方法时，不是直接按照一条链找过去的，而是使用虚方法表



使用时会查询常用的虚方法表进行调用
[![pV59hvV.png](https://s21.ax1x.com/2025/09/23/pV59hvV.png)](https://imgse.com/i/pV59hvV)
[![pV59IDU.png](https://s21.ax1x.com/2025/09/23/pV59IDU.png)](https://imgse.com/i/pV59IDU)

- 继承中成员变量的访问采取就近原则

```java
public class Test {
    public static void main(String[] args) {
        Zi z = new Zi();
        z.ziShow();
    }
}

class Ye {
    String name = "Ye";
}

class Fu extends Ye {
    String name = "Fu";
}

class Zi extends Fu {
    String name = "Zi";

    public void ziShow() {
        String name = "ziShow";
        
        System.out.println(name);       // 输出: ziShow

        System.out.println(this.name);  // 输出: Zi

        System.out.println(super.name); // 输出: Fu
    }
}
```

- 对于空参构造如何调用有参构造

```java

public class prc_04 {
    String name;
    int age;
    String school;
    public prc_04(){
        this(0,null,"tsinghua");
    }

    public prc_04(int age, String name, String school) {
        this.age = age;
        this.name = name;
        this.school = school;
    }

    public static void main(String[] args) {
        prc_04 stu=new prc_04();
        System.out.println(stu.school);
    }
}
//输出tsinghua
```
[![pV5sumd.png](https://s21.ax1x.com/2025/09/24/pV5sumd.png)](https://imgse.com/i/pV5sumd)
[![pV5sVSO.png](https://s21.ax1x.com/2025/09/24/pV5sVSO.png)](https://imgse.com/i/pV5sVSO)
这里子类构造使用super有参构造从而传递给我们的this.xxxx



---






## 多态

[![pV5sOHA.png](https://s21.ax1x.com/2025/09/24/pV5sOHA.png)](https://imgse.com/i/pV5sOHA)

简而言之就是左边为父类，右边为子类，用父类new一个子类。
**成员变量用父类，成员方法用子类，在方法变化时，只需变化初始化的一行代码便于维护**

```java
// 1. 定义一个抽象的父类 "Animal"
abstract class Animal {
    // 定义一个所有子类都必须实现（重写）的抽象方法
    public abstract void makeSound();
    public abstract void eat();
}

// 2. 让具体的动物类继承 Animal 并重写方法
class Dog extends Animal {
    @Override
    public void makeSound() { System.out.println("狗在汪汪叫"); }
    @Override
    public void eat() { System.out.println("狗在啃骨头"); }
}

class Cat extends Animal {
    @Override
    public void makeSound() { System.out.println("猫在喵喵叫"); }
    @Override
    public void eat() { System.out.println("猫在吃鱼"); }
}

// 3. 饲养员只需要一个通用的喂养方法
class Feeder {
    // 这个方法可以接收任何 Animal 的子类对象！
    public void feed(Animal animal) {
        animal.makeSound();
        animal.eat();
    }
}

// 4. 主程序
public class ZooTest {
    public static void main(String[] args) {
        Feeder feeder = new Feeder();
        
        // 使用多态：父类引用指向子类对象
        Animal dog = new Dog();
        Animal cat = new Cat();
        
        System.out.println("--- 喂狗 ---");
        feeder.feed(dog); // 传入 Dog 对象，自动调用 Dog 的方法
        
        System.out.println("\n--- 喂猫 ---");
        feeder.feed(cat); // 传入 Cat 对象，自动调用 Cat 的方法
    }
}






```
但是这也有弊端，**他编译的时候是看左侧父类是否存在对应的量或者方法，如果没有则不能调用，这也意味着子类的独有方法无法调用**



左侧接口右侧使用接口的类依然可以实现多态

---
final修饰的方法不能重写与被继承，修饰常量，必须且只能赋值一次
如果是引用数据类型，那么地址不能改，内容可以改，类似于指针常量

静态代码块
```java
public class APP{
    static{

    }

}
//这段static代码只执行一次，在其他的main函数初始化各种这个类的时候只调用一次，适合用于初始化信息。
```

#### 抽象方法

父类不确定具体的方法体，全部交给子类自己重新定义，这就是抽象方法，一个含有抽象方法的类称为抽象类，抽象类不一定有抽象方法

抽象类无法被作为对象初始化，不存在 new 一个抽象类

抽象方法最大的好处就是他能够统一方法名称格式，有利于管理代码

*子类继承时需要且必须重写所有抽象方法*

```java
package practice3;

public abstract class animal {
    public void drink(){
        System.out.println("喝水");

    }
    public abstract void shout();
//此处为抽象方法
}




package practice3;

public class dog extends animal{

    @Override
    public void shout() {
        System.out.println("wolf");
    }
}

```

这里还有一个类似的使用了抽象方法的，但他不是作为父类，而是接口(interface)

一个对象可以同时实现多个接口

```java
public interface inter{
    int a=10;
    //成员变量默认全部采取public static final无法二次修改
    void method();
    //方法全部采取public abstract的抽象方法
}

public class cat extends animal implements inter{
    //使用implements来达成类似继承的作用
    public void method{
        System.out.println("method");
    }
    
}
```

对于接口来说还有其他方法，他不需要子类重新定义

- 一个是`public default void show(){}`这是可以正常定义方法体的，并且子类相当于直接继承了这个方法
- 另一个是`public static void show(){}`这两者都不需要子类再次重新定义就可以使用，后者必须使用接口名才能调用比如`inter.show()`才可以

接下来如果接口有些只自己用的就使用`private`修饰方法即可

```java
package practice3;

public interface inter1 {
    public void method1();    
    public void method2();   
    public void method3();    
    public void method4();
    public void method5();   
    public void method6();
    
}


package practice3;

public abstract class interadapter implements inter1{
    @Override
    public void method1() {

    }

    @Override
    public void method2() {

    }

    @Override
    public void method3() {

    }

    @Override
    public void method4() {

    }

    @Override
    public void method5() {

    }

    @Override
    public void method6() {

    }
}


package practice3;

public class test extends interadapter{
    @Override
    public void method2() {
        System.out.println("只重新定义这一个方法");
    }
}

```

之前在抽象类方法提到必须全部重新定义，接口除了前面提到的几个不需要，那么有没有办法当我只使用某个的时候，其他的抽象类不定义呢

可以的->

上方代码通过一个*适配器设计模式*，先使用接口（继承父类一样的）然后重新定义所有抽象类，但此时的他的方法已经不是抽象类，接下来再继承就不要全部重定义了。



#### 内部类

```java
package com.itheima.a01innerclassdemo1;

public class Car {
    String carName;
    int carAge;
    String carColor;

    public void show(Car this) {
        
        System.out.println(this.carName);
        Engine e = new Engine();
        //外部类无法直接访问内部类
        System.out.println(e.engineName);
    }

    class Engine {
        String engineName;
        int engineAge;

        public void show() {
            System.out.println(engineName);
            System.out.println(carName);
        }
    }
}
```

```java
package practice3;

public class outer {
    private int a =10;
    public class inner{
        private int a=20;
        public void show(){
            int a=30;
            System.out.println(outer.this.a);
     //这里的this像是每个类的特有物，每个类都有自己的this
            System.out.println(this.a);
            System.out.println(a);
        }
    }


}
package practice3;

public class test1 {
    public static void main(String[] args) {
        outer.inner out=new outer().new inner();
        //注意这里的定义方式
        out.show();
    }
}

```

#### 匿名类

```java
public class Student implements Swim{
    public void swim(){
        system.out.println("重写游泳的方法");
    }
}

//这里是使用匿名类之前的原本的模样
//类名是Student，使用的是swim接口

new swim(){
    public void swim(){
        system.out.println("重写游泳的方法");
    }
}
//这就是匿名类
```

怎么理解这个`new swim(){}`，这么去理解，相当于new了一个无名类然后(implements/extends)这里的swim，后面大括号的内容都是该无名类的内容



```java
public interface Swim{
	public abstract void swim();   }

Swim s=new Swim(){
    public void swim(){
        system.out.println("重写游泳的方法");
    }
}
//左侧是接口，右侧是使用接口的匿名类，一个标准的多态

s.swim();


//甚至可以直接这样
new Swim(){
    public void swim(){
        system.out.println("重写游泳的方法");
    }    
}.swim();
```



[![pVIL37R.png](https://s21.ax1x.com/2025/09/27/pVIL37R.png)](https://imgse.com/i/pVIL37R)

[![pVIvmVJ.md.png](https://s21.ax1x.com/2025/09/28/pVIvmVJ.md.png)](https://imgse.com/i/pVIvmVJ)

[![pVopYlt.png](https://s21.ax1x.com/2025/09/28/pVopYlt.png)](https://imgse.com/i/pVopYlt)



---





### 各种api

| Math类常见用法 |                 |
| :------------: | :-------------: |
|      abs       |                 |
|      ceil      |    向上取整     |
|     floor      |    向下取整     |
|     round      |    四舍五入     |
|      max       |                 |
|    pow(a,b)    |    a的b次幂     |
|    random()    | 返回[0.0,1.0)的 |



|                           system类                           |              用法              |
| :----------------------------------------------------------: | :----------------------------: |
|                        system.exit()                         |                                |
|                  system.currentTimeMillis()                  | 返回当前系统的时间（毫秒形式） |
| system.arraycopy(数据源数组，起始索引，目的地数组，起始索引，拷贝个数) |                                |



```java
    public static void main(String[] args) throws IOException {

        System.out.println(Runtime.getRuntime().availableProcessors());
        System.out.println(Runtime.getRuntime().maxMemory()/1024/1024);
        System.out.println(Runtime.getRuntime().totalMemory()/1024/1024);
        System.out.println(Runtime.getRuntime().freeMemory()/1024/1024);
        Runtime.getRuntime().exec("shutdown -a");
        Runtime.getRuntime().exit(0);
```

- 这里的runtime构造为私有需要通过`getRuntime`来获取

- 这里的exec后面("")可加入cmd命令

`a.equals(b)`会调用a的equals方法，然后这个方法里面的参数是b

sout内部如果是一个自定义类，并且没有重载`toString()`方法，他会先调用`object` 的`toString()`处理然后再输出，输出  类名加@加哈希值，所以一般如果想要打出内部变量值，需要在自定义类对object的`toString()`进行重载



####  object的clone方法

```java
package practice5;

public class player implements Cloneable{
    //这里必须实现这个接口该类的对象才可以使用clone
    String name;

    public player(String name) {
        this.name = name;
    }

    @Override
    public player clone() {
        try {
            return (player) super.clone();
        } catch (CloneNotSupportedException e) {
            throw new AssertionError();
        }
    }
    //这里的clone在object里是直接使用native即底层的c语言实现的
    //属于protected类型，这就意味着，如果不重写，其他包的类如果想使用player.clone()是不行的，所以这里重写为public
}



package practice5;

public class test {
    player pl1=new player("xjj");
    player pl2=(player) pl1.clone();
}

```

- 上方这段代码实现的是浅克隆，也就是将基本类型值复制，引用类型地址复制，如果原类变化，这里的克隆过的会跟随着一起改变

还有一个是深克隆，基本类型的值会被复制，引用类型则会新建一个一样的，但地址不同

["F:\java_test\gson-2.6.2.jar"][1]

[1]: F:\java_test\gson-2.6.2.jar	" 写好的jar"





1. 在当前项目创建lib目录
2. 接下来在这个目录下粘贴这个jar
3. 然后对其设置为添加为库

然后就可以写下

```java
public class pracetice1 {
    public static void main(String[] args) {
        int[] data={1,2,3,4};
        Player pl1= new Player("sss",data);
        Gson gson =new Gson();
        String s=gson.toJson(pl1);
        System.out.println(s);
        Player pl2=gson.fromJson(s,Player.class);
        System.out.println(pl2);
        //这里如果对pl2的tostring方法进行重写
        //就能得到如下两个输出
        //{"name":"sss","data":[1,2,3,4]}
		//name:sss,  data:[1,2,3,4]
    }

}
```



#### object的equal方法

```java
    @Override
    public boolean equals(Object o) {
        if (o == null || getClass() != o.getClass()) return false;
        Player player = (Player) o;
        return Objects.equals(name, player.name) && Objects.deepEquals(data, player.data);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, Arrays.hashCode(data));
    }
}

```

当你对新定义的类写下equal后就会显示根据向导重写equal方法，如上

而object的`equal()`方法原本是对地址进行比较，而不是对属性值进行比较





接下来与objects的方法进行区分，首先你要知道之前说的各类的顶级父类是object

各种方法的覆写也是object，这里objects就是相当于多给了几个方法



objects的equal方法

`Objects.equals(pl1,pl2)`他就是在object的基础上先判断是否非空，然后非空再调用pl1.equals(pl2)，所以覆写仍然会生效

`Objects.isNull(pl1)` `Objects.nonNull(pl1)`





[![pVTWOnx.png](https://s21.ax1x.com/2025/10/03/pVTWOnx.png)](https://imgse.com/i/pVTWOnx)



这个biginteger最大的用法就是它能够生成比long还要大的数据



[![pVTfPgA.png](https://s21.ax1x.com/2025/10/03/pVTfPgA.png)](https://imgse.com/i/pVTfPgA)







---





### 正则表达式

[![pVTfK3j.png](https://s21.ax1x.com/2025/10/03/pVTfK3j.png)](https://imgse.com/i/pVTfK3j)









[![pVTf4KI.png](https://s21.ax1x.com/2025/10/03/pVTf4KI.png)](https://imgse.com/i/pVTf4KI)





[![pVTfqPg.md.png](https://s21.ax1x.com/2025/10/03/pVTfqPg.md.png)](https://imgse.com/i/pVTfqPg)







再补充一个（?i）表示忽略大小写





```java
System.out.println("23dF".matches("[a-zA-Z0-9]{4}")); // true
System.out.println("23_F".matches("[a-zA-Z0-9]{4}")); // false
System.out.println("23dF".matches("[\\w&&[^_]]{4}")); // true
System.out.println("23_F".matches("[\\w&&[^_]]{4}")); // false
String regex="\\w+@[\\w&&[^_]]{2,6}(\\.[a-zA-Z]{2,3}){1,2}"
    
    static String regex = "[1-9]\\d{5}(18|19|20)\\d{2}(0[1-9]|1[0-2])(0[1-9]|[12][0-9]|3[01])\\d{3}(\\d|(?i)x)";

```

在这里两个\\\就是一个\\，相当于对转义字符进行转义

注意这里的\\\ .和直接一个. 前者为符号，后者表示任意字符



#### 爬虫

```java
public class WebCrawler {

    public static void main(String[] args) {
        String str="Java从95年以来就xxxxxx,Java11,,Java9,,,javaXXXXX";
        Pattern p=Pattern.compile("Java\\d{0,2}");
        //这里的Pattern.compile()相当于pattern的构造函数
        Matcher m=p.matcher(str);
		//这里的matcher也是构造函数
        while(m.find()){
            String s=m.group();
            //这里开始爬取数据
            System.out.println(s);
        }
    }

}
```

这里就是简单的爬取正则表达式对应的内容





```java

public class WebCrawler {

    public static void main(String[] args) {
        String str="Java从95年以来就xxxxxx,java11,,JAVA8,Java17也即将登上舞台";

        Pattern p1=Pattern.compile("Java(?=8|11|17)");
        Pattern p2=Pattern.compile("((?i)java)(?:8|11|17)");
        Pattern p3=Pattern.compile("((?i)java)(?!8|11|17)");
        Matcher m1=p1.matcher(str);
        Matcher m2=p2.matcher(str);
        Matcher m3=p3.matcher(str);
        while(m1.find()){
            String s=m1.group();
            System.out.println(s);

        }
        System.out.println("------------------");

        while(m2.find()){
            String s=m2.group();
            System.out.println(s);

        }
        System.out.println("------------------");
        while(m3.find()){
            String s=m3.group();
            System.out.println(s);
        }
    }

}


//Java
//------------------
//java11
//JAVA8
//Java17
//------------------
//Java
//输入如上
```

这里在原有基础上对于相应内容的索引前面还可以有几种加法

1. 加上?=表示这后面的内容也要搜索，但搜索完后，要去掉
2. 加上?:表示后面的内容搜索并且也要留下（和不加的效果一样）
3. 加上?!表示后面的内容不参与搜索，搜索完如果有后面内容的要删掉



```java
        String s2="abbbbbbbbbbbbbbbbbbbbbaaaa";
        Pattern p4=Pattern.compile("ab+?");
        Matcher m4=p4.matcher(s2);
        while(m4.find()){
            System.out.println(m4.group());
        }
//这里在正常的后面加上问号就是非贪婪爬取输出ab
//正常情况没有？就是贪婪爬取会爬取尽可能多的b
```



```java
public static void main(String[] args) {
 	String s2="abbbbbbbbbbbbbbbbbbbbbaaaa";
	String s3=s2.replaceAll("b+?","1");	
    String[] s4=s3.split("1+")
    System.out.println(s3);
   
} 

    public String[] split(String regex) {
        return split(regex, 0, false);
    }
    

	public String replaceAll(String regex, String replacement) {
        return Pattern.compile(regex).matcher(this).replaceAll(replacement);
    }

//这里是两个string的函数可用于正则化表达式
//第一个replaceall，将前者替换为后者
//第二个是split按照给定的正则化表达式分割返回字符串数组

```

捕获分组

`String regex="((.)\\2*).+\\1";`

表示什么意思呢，这里的`\\`加上数字表示提取第几个分组出来再用一遍

这里分组的序号看的是第几个左括号，*表示0到n个，

在正则表达式外面的捕获分组要使用$

```java
public class Web2 {
    public static void main(String[] args) {
        String s1="abc123abc";
        String s2="def456def";
        String s3="sfa11sfa";
        String s4="aaaa2141aaaa";
        String regex="((.)\\2*).+\\1";
        System.out.println(s4.replaceAll("(.)\\1+", "$1"));
        //这里的\\提取分组必须和分组内部的东西一致而不是任意字符
        //$1表示的就是正则表达式中的第一个分组
    }
}

```

> 关于时间类的api太繁琐了我没记，到时候用到你可以看视频或者直接去查api文档





[![pV79xVf.png](https://s21.ax1x.com/2025/10/04/pV79xVf.png)](https://imgse.com/i/pV79xVf)

注意进制转换后返回的是字符串，这里的`parseInt()`相当于`atoi()`

```java
        int n = 123;
        System.out.println("n = " + n);
        System.out.println(Integer.toBinaryString(n)); // 二进制
        System.out.println(Integer.toOctalString(n));  // 八进制
        System.out.println(Integer.toHexString(n));    // 十六进制（小写）
        System.out.println(Integer.parseInt("123"));  
```





#### Array的各种api



[![pV7kz9O.png](https://s21.ax1x.com/2025/10/05/pV7kz9O.png)](https://imgse.com/i/pV7kz9O)



```java
public class ArraysUsageDemo {
    public static void main(String[] args) {
        int[] arr = {5, 2, 8, 3};

        // toString(数组)
        String s = Arrays.toString(arr); // s == "[5, 2, 8, 3]"

        // sort(数组) - 必须对二分查找前先排序
        Arrays.sort(arr);                 // arr == {2,3,5,8}

        // binarySearch(数组, 查找的元素)
        int idx = Arrays.binarySearch(arr, 5); // idx == 2 (找到时返回索引)

        // copyOf(原数组, 新数组长度)
        int[] copy = Arrays.copyOf(arr, 6); // copy == {2,3,5,8,0,0}（长度扩大，尾部补 0）

        // copyOfRange(原数组, 起始索引, 结束索引) 结束索引为 exclusive(左闭右开)
        int[] range = Arrays.copyOfRange(arr, 1, 3); // range == {3,5}

        // fill(数组, 元素)
        int[] filled = new int[5];
        Arrays.fill(filled, 7); // filled == {7,7,7,7,7}

        // sort(对象数组) 与 sort(对象数组, 排序规则)
 		
    }
}


public class array {

    public static void main(String[] args) {
        Integer[] arr={2,3,1,5};
        Arrays.sort(arr, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o1-o2;
            }
        });
    }
}


```

- 其他的都好理解，主要就是一个这里的  **sort规则的重写**

  首先是这里使用的是一个comparator的接口，并且这个接口需要接受的数据类型不能是基本数据而是<T>一个对象（类）所以当你想的是int时，你得用`Integer`才行(一个封装了基本数据类型的对象)**我之前的截图中有提到**

  在各种数据计算上`Integer`就可以看成int只是类型为一个类而已  

- 然后怎么理解这里返回值o1-o2呢他是怎么根据这个排序的呢，sort函数的底层

​		  采取的是一个`TimSort()`一种混合排序方式





>TimSort 之所以被称为**混合排序**，是因为它并非单一地使用一种排序思想，而是巧妙地将两种经典的排序算法结合在一起，在不同场景下发挥各自的优势：
>
>1. **插入排序 (Insertion Sort)**
>   - **优点**：在处理**小规模**或**基本有序**的数组时，效率极高，甚至快于复杂的 O(n log n) 算法。
>   - **在 TimSort 中的应用**：当 TimSort 发现一个天然的有序片段（run）太短时（例如，少于 32 个元素），它会使用**二分插入排序**（`binarySort`）来高效地将这个小片段扩展到合适的长度。它把处理小规模数据的任务交给了最擅长做这件事的插入排序。
>2. **归并排序 (Merge Sort)**
>   - **优点**：在处理大规模数据时，性能稳定在 O(n log n)，并且是**稳定排序**，非常适合合并两个已经排好序的大数组。
>   - **在 TimSort 中的应用**：在创建了一系列排好序的 run 之后，TimSort 的核心任务就是将这些 run **合并**起来。这个合并过程借鉴了归并排序的思想，高效、稳定地将一个个 run 合并，直到整个数组完全有序。
>
>**混合的精髓：** TimSort 就像一个聪明的项目经理。它先用“小分队”（插入排序）快速搞定零散的小任务，然后让“主力军”（归并排序）来高效地整合所有小分队的成果，最终完成整个大项目。这种分工合作让它在各种数据模式下都表现出色。



>`compare(o1, o2)` 的返回值有三种情况：
>
>- **返回负数**：表示 `o1` **应该排在** `o2` **前面**。
>- **返回正数**：表示 `o1` **应该排在** `o2` **后面**。
>- **返回 0**：表示 `o1` 和 `o2` 在排序上是**相等的**

具体怎么用的有点复杂，反正记住o1-o2是升序，反过来是降序就完了







[![pV7ZdKg.png](https://s21.ax1x.com/2025/10/05/pV7ZdKg.png)](https://imgse.com/i/pV7ZdKg)

如何使用lambda表达式简化匿名内部类函数的书写



```java
//在上面我们书写了arrays.sort的comparator接口的匿名内部类
//是这样的
public class array2 {
    public static void main(String[] args) {
        String[] arr={"aaaa","aaa","aa","a"};

        Arrays.sort(arr, new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return o1.length() - o2.length();
            }
        });
    }
}

//那么这个时候想用lambda简化，先判断是不是，有且仅有一个抽象方法的接口，发现确实，然后接下来开始简化，我们需要的是重写的方法，而怎么实现的不重要因此只保留重写方法
public class array2 {
    public static void main(String[] args) {
        String[] arr={"aaaa","aaa","aa","a"};

        Arrays.sort(arr, (String o1, String o2)-> {
                return o1.length() - o2.length();
            });
    }
}
//因为他知道这里用的是接口的这个方法（只有一个），因此就默认这是新的类的重写的对应的方法
//由于只有一行，而且类是相同的（由arr就可以判断出来应当是string类）
public class array2 {
    public static void main(String[] args) {
        String[] arr={"aaaa","aaa","aa","a"};

        Arrays.sort(arr, (o1, o2)-> o1.length() - o2.length()
        );
    }
}
//这是在此基础上去掉数据类型，去掉大括号return和分号的结果但只有方法内部只有一行的时候可以这么省

```





- 为什么lambda表达式要求接口只能有一个抽象类方法。

  比如这个sort他不是知道里面调用的是comparator的compare方法吗，那么我如果有多个抽象类方法，也不影响他只调用特定方法啊



>是的，`sort` 方法的**调用端**是知道的。但问题出在**创建端**。
>
>```
>Arrays.sort(arr, (o1, o2) -> o1 - o2);
>```
>
>这行代码分为两步：
>
>1. **创建实例**：Java 首先需要根据 `(o1, o2) -> o1 - o2` 创建一个 `Comparator` 接口的实例。
>2. **传递实例**：然后把这个创建好的实例传递给 `sort` 方法。
>
>**关键在于第一步**。在创建实例的时候，Java 必须明确这个 Lambda 对应的是哪个方法。如果 `Comparator` 有多个抽象方法，第一步就会因为歧义而失败，根本走不到第二步。

`@FunctionalInterface`这是个小技巧，看源码看到这个就意味着这是一个只有一个抽象方法的接口，可以使用lambda函数

## 数据结构



#### collection

[![pV7J9FU.png](https://s21.ax1x.com/2025/10/06/pV7J9FU.png)](https://imgse.com/i/pV7J9FU)

[![pV7JCYF.png](https://s21.ax1x.com/2025/10/06/pV7JCYF.png)](https://imgse.com/i/pV7JCYF)

```java
public class CollectionDemo {
    public static void main(String[] args) {
        // 使用 Collection 引用指向 ArrayList 实例
        Collection<String> coll = new ArrayList<>();

        // add(E e)
        coll.add("apple");
        coll.add("banana");
        coll.add("orange");
        coll.add("banana"); // ArrayList 允许重复

        // size(), isEmpty()
        System.out.println("size = " + coll.size());       // 4
        System.out.println("isEmpty = " + coll.isEmpty()); // false

        // contains(Object obj)
        System.out.println("contains 'banana' ? " + coll.contains("banana"));
        //注意这里的contains判断是否包含使用的是逐个遍历的equals方法，所以如果使用的是自定义的类作为成员，要先			定义下equals方法

        // 遍历集合（Iterator 或 foreach）
        System.out.println("elements:");
        for (String s : coll) {
            System.out.println(" - " + s);
        }

        // remove(E e)
        coll.remove("banana"); // 只移除第一个匹配项（对 List），对 Set 则移除该元素
        System.out.println("after remove 'banana', size = " + coll.size());

        // clear()
        coll.clear();
        System.out.println("after clear, isEmpty = " + coll.isEmpty());

```



第一种遍历方法

```java
public class Iterator_test {
    public static void main(String[] args) {
        Collection<String> coll=new ArrayList<>();
        coll.add("aaa");
        coll.add("bbb");
        coll.add("ccc");
        Iterator<String> it=coll.iterator();
            //此时it已经指向第一个元素
        while(it.hasNext()){
            String str=it.next();
		//这里的hasNext()是判断此处是否有元素
		//next则是提取出这个元素返回，并且后移一位
            if("bbb".equals(str)){
                it.remove();
                //在迭代器迭代的过程中不可以使用collection的方法去删除，只能用迭代器的remove去做
                //从迭代器指向的 collection 中移除迭代器返回的最后一个元素
                continue;
            }
            System.out.println(str);
        }
    }

}

```

第二个和第三个迭代方法

```java
public class Iterator_test {
    public static void main(String[] args) {
        Collection<String> coll=new ArrayList<>();
        coll.add("aaa");
        coll.add("bbb");
        coll.add("ccc");
        for (String s : coll) {
            System.out.println(s);
        }
        //第二种增强for使用coll.for即可
        coll.forEach((s) ->System.out.println(s)
        );
        //第三种使用forEach
        //这方法的底层原理是逐个遍历对该元素调用consumer的accept
    }

}

```







[![pV7JMfe.png](https://s21.ax1x.com/2025/10/06/pV7JMfe.png)](https://imgse.com/i/pV7JMfe)

可以用普通的for和get索引组合进行遍历

这是list的不同于collection的方法

```java
public class Iterator_test {
    public static void main(String[] args) {
        List<String>list=new ArrayList<>();

        list.add("aaa");
        list.add("aab");
        list.add("aac");
        ListIterator<String> it2=list.listIterator();
        while(it2.hasNext()){
            String str2=it2.next();
            if("aab".equals(str2)){
                it2.add("aae");
                //注意这里的add是list迭代器才有的，而普通的collection迭代器只有删除功能
            }
            System.out.println(str2);
        }
        for (String s : list) {
            System.out.println(s);
        }

    }

}
//aaa
//aab
//aac

//aaa
//aab
//aae
//aac

```

为什么这里的多态选择了list而不是之前的collection涉及到另一个和多态相关的知识点

- 因为这里的多态调用方法时会选择子类的重写方法，但还有一点很重要，只有这个方法是在父类有定义的才能调用

  这就意味着子类的其他新的方法是不能调用的，所以使用collection后，即便右侧是arraylist也不能调用list相关的方法

[![pV7JatS.png](https://s21.ax1x.com/2025/10/06/pV7JatS.png)](https://imgse.com/i/pV7JatS)



#### 泛型

[![pV7sZnS.png](https://s21.ax1x.com/2025/10/07/pV7sZnS.png)](https://imgse.com/i/pV7sZnS)

为什么说是伪泛型，因为当存到这里的数组里时，java还是会把他当成object类型存储，但取出来时会做一个string类型的强转，这也是为什么各种`<>`不能填写int而必须填写integer的原因，因为只有这样才能将其转换为object类

[![pV7sm7Q.png](https://s21.ax1x.com/2025/10/07/pV7sm7Q.png)](https://imgse.com/i/pV7sm7Q)

[![pV7sukj.png](https://s21.ax1x.com/2025/10/07/pV7sukj.png)](https://imgse.com/i/pV7sukj)

[![image.png](https://i.postimg.cc/T3ZFtq6t/image.png)](https://postimg.cc/k2vT4SDS)

这里以接口为例

==泛型的用处是很大的，当你重写抽象方法时如果不使用泛型指定具体类型，一般来说方法传入的是object类型，但如果你需要传入的是指定的自定义类型，就必须在使用接口时指定具体类型即泛型，或者你不需要具体的类型的话可以不写<E>（用object）或者两个都写上<E>通过这个来实现泛型（感觉不如方式1常用）==

```java
public class test {
    public static void main(String[] args) {
        MyArrayList1 list1=new MyArrayList1();
        list1.add(111);
        MyArrayList2<String>list2=new MyArrayList2<>();
        list2.add("aaa");
    }

}

public class MyArrayList1 implements List<Integer> {
    @Override
    public int size() {
        return 0;
    }

    @Override
    public boolean isEmpty() {
        return false;
    }

    @Override
    public boolean contains(Object o) {
        return false;
    }

    @Override
    public Iterator<Integer> iterator() {
        return null;
    }
    //方法太多就省略了
}


public class MyArrayList2<E> implements List<E> {
//这个就是类延续泛型
    @Override
    public int size() {
        return 0;
    }

    @Override
    public boolean isEmpty() {
        return false;
    }

    @Override
    public boolean contains(Object o) {
        return false;
    }

    @Override
    public Iterator<E> iterator() {
        return null;
    }
```

区分泛型最好的办法就是看他在不在`<>`尖括号里面，如果在的话就是泛型，

- 泛型是没有继承性的，也就是说相比于之前传递子类或者使用接口的类是没有问题的，但是传递继承的子类是没法填到父类的泛型里面的。

- 此时泛型里面写什么就只能传什么类型的类

  但是使用泛型通配符可以解决一部分问题

```java
        List<? extends Number> list1 = new ArrayList<Integer>();
        List<? super Integer> list2 = new ArrayList<Number>();
```

- 这里的在`<>`里面写? extends E表示E以及E的所有子类都可以填在里面

- ? super表示E及E的所有父类都可以填在里面

  但是**数据是具备继承性的**，什么意思？

  ```java
  ArrayList<Ye> list1 = new ArrayList<>();
  //这里右侧就不能填写Fu，只能写Ye或者不写
  //但是这里加入数据，是都可以加的后面两个是ye的子类所以可以正常加入，但是初始化的时候是不存在继承的
  list1.add(new Ye());
  list1.add(new Fu());
  list1.add(new Zi());
  ```

  

  #### 红黑树（set各类的底层实现）

  [![image.png](https://i.postimg.cc/sfY0j1LM/image.png)](https://postimg.cc/hhG0M4cn)

[![image.png](https://i.postimg.cc/5tkWmjJ0/image.png)](https://postimg.cc/94Tkmmr5)

平衡二叉树，红黑树都是基于二叉查找树（左小于根小于右）形成的，并且平衡的特征是左右子树的高度差不能大于1，如果超过了要进行左旋右旋处理。

> 平衡二叉树情况太多，到时候自己去查或者看之前代码



#### Hashset

[![image.png](https://i.postimg.cc/X71nN2Zf/image.png)](https://postimg.cc/nCmy0GGr)

哈希表的特征成功融合了数组，链表，红黑树三者进行数据存储，当表中长度乘以加载因子的内容被用了时会自动扩充长度为当前两倍，当哈希表中的链表长度超过一个阈值（默认为 8）并且哈希表的总容量大于一定值（默认为 64），会将链表转化为红黑树提高查找效率

但需要注意的是如果存入的是自定义类，需要对`equals`和`hashcode`方法进行重写，改为对于类的各个元素的比较，不然这两者底层比较的和加载的根据是地址值

[![image.png](https://i.postimg.cc/85zyCbfr/image.png)](https://postimg.cc/JyS36Zq1)

`LinkedHashSet`就是在哈希表的基础上加了双向链表用于给加入数据的顺序排序，变成有序排列

- 需要注意的是两者都是不会有重复的数据（在重写`equals`方法后）

```java
public class TestHashset {
    public static void main(String[] args) {
        HashSet<Student> hs=new HashSet<>();
        hs.add(new Student("xjj",111));
        hs.add(new Student("pamks",11));
        System.out.println(hs);

    }

public class Student implements Comparable<Student>{
    public String name;
    public int score;

    @Override
    public boolean equals(Object o) {
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return score == student.score && Objects.equals(name, student.name);
    }

    public Student(String name, int score) {
        this.name = name;
        this.score = score;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getScore() {
        return score;
    }

    public void setScore(int score) {
        this.score = score;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", score=" + score +
                '}';
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, score);
    }

    @Override
    public int compareTo(Student o) {
        System.out.println("===========");
        System.out.println("this.score="+this.score);
        System.out.println("o.score="+o.score);
        return this.score-o.score;
    }
}

```





#### Treeset



[![image.png](https://i.postimg.cc/hGxWk5C1/image.png)](https://postimg.cc/3yKcpnQk)

`Treeset`的排序方式如图，当然这是默认的排序方式，他的底层是红黑树，当你乱序加入后他会调用`Comparable`的接口`compareTo`的方法按照红黑树的比较大小的方式进行比较并排序，因此如果你想要放入自定义类需要重写这个方法

- 这也意味着一点，只要是放入treeset的对象全部都实现过这个接口并且重写过方法，因此我去随便找了几个比如string和integer，发现确实他们本来就实现过了所以你不用重写，但是你如果是自定义的话就要重新实现

>All elements inserted into
>     * the set must implement the {@link Comparable} interface.
>          * Furthermore, all such elements must be <i>mutually
>          * comparable</i>: {@code e1.compareTo(e2)} must not throw a
>               * {@code ClassCastException} for any elements {@code e1} and
>               * {@code e2} in the set.

```java
public class TreeSetTest {

    public static void main(String[] args) {
        TreeSet<Student>ts=new TreeSet<>();
        ts.add(new Student("xjj",123));
        ts.add(new Student("pmsjl",199));
        ts.add(new Student("sjl",99));
        System.out.println(ts);
    }
}


public class Student implements Comparable<Student>{
    //这里使用泛型的好处就体现了，我可以明确表示传入compareTo的变量是student类型
    public String name;
    public int score;

    @Override
    public boolean equals(Object o) {
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return score == student.score && Objects.equals(name, student.name);
    }

    public Student(String name, int score) {
        this.name = name;
        this.score = score;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getScore() {
        return score;
    }

    public void setScore(int score) {
        this.score = score;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", score=" + score +
                '}';
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, score);
    }

    @Override
    public int compareTo(Student o) {
        System.out.println("===========");
        System.out.println("this.score="+this.score);
        System.out.println("o.score="+o.score);
        return this.score-o.score;
    }
}

//这是输出
//===========
//this.score=123
//o.score=123
//===========
//this.score=199
//o.score=123
//===========
//this.score=99
//o.score=123
//[Student{name='sjl', score=99}, Student{name='xjj', score=123}, Student{name='pmsjl', score=199}]
```

- 需要注意的是这里的`compareTo()`方法里`this`是要添加的变量，`o`是已经添加的待比较的变量

  因此当你返回`this-o`的时候大于0则将加入的放入红黑树右侧，反之则在左侧



上面是第一种比较方法，往往一般都用这种，在自定义中使用Comparable接口进行重写方法

但还有一些情况是涉及无法使用第一种的，比如我的变量是string类型，那么就意味着源码已经重写过compareto了，这时候想要改变排列逻辑怎么做$\to$你需要做的就是在构造时传入comparator

```java
public class TreeSetTest2 {
    public static void main(String[] args) {
        String s1="ab";
        String s2="df";
        String s3="ascasd";
        String s4="e";
        TreeSet<String>ts=new TreeSet<>((o1, o2)-> {
                int i=o1.length()-o2.length();
                return i==0?o1.compareTo(o2):i;
				//这里o1.compareTo(o2)，与string重写方法的逻辑是一致的
            //这里o1是待添加元素，o2是待比较的元素
        });
        ts.add(s1);
        ts.add(s2);
        ts.add(s3);
        ts.add(s4);
        System.out.println(ts);

    }
}

//[e, ab, df, ascasd]
```

这里就是在构造时传入接口，然后重写方法，根据匿名内部类和lambda表达式，对形式为接口的内容进行简化，就是他看上去是传入接口，但实际后面是调用该接口的唯一抽象方法，这里用lambda后就会将方法先放到一个实例化该接口的类里面，然后调用这个方法。

[![image.png](https://i.postimg.cc/x8b0t3k1/image.png)](https://postimg.cc/0KPRNmdT)

未完待续