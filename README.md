1.1.函数
函数的作用？
函数可以封装一段代码，只需定义一次，即可多次调用和执行，因为可以传入参数所以会非常灵活.
1.1.1.函数的声明和调用
函数的声明
function 函数名 () {
	//函数体 
}

函数的调用
函数名();

1.1.2.引入外部js中的函数
Common.js:
function fn() {
    console.log("表示很多代码");
    console.log("做了很多事情");
}

html代码：
<script src="common.js">
</script>
<script >
    fn();
</script>
注意，这里的引入和调用，必须分开写（写在两个script标签）。不然就没有效果。
	 而且，必须先引入，再调用。

1.1.3.函数的参数
有参数的函数的声明（声明中的参数只是一个占位符，没有实际的值，是形式参数，即形参）
function 函数名 (参数1,参数2,参数3...) {
	//函数体 
}
有参数的函数的调用（调用时传入的参数才是有真正数值的参数，是实际参数，即实参）
函数名(参数1,参数2,参数3...);
 
1.1.4.函数的返回值
在函数中通过return关键字将要返回值返回
return 要返回的值;

问题：什么时候要添加返回值？
主要看需求，看自己要处理什么逻辑。
比如：我想计算xy之间所有数之和，然后打印出来。
function getSum(x, y) {
    var sum = 0;
    for (var i = x; i <= y; i++) {
        sum += i;
    }
    console.log(sum); 
}
注意：这里的需求，仅仅是要打印任意两个数之和，所以这里可以不用返回值。

再比如：我想计算xy之间所有数之和。
function getSum(x, y) {
    var sum = 0;
    for (var i = x; i <= y; i++) {
        sum += i;
    }
    return sum;
}
注意：这里的需求仅仅是计算两个数之和，然后没了。但为什么这里要返回值呢？大家可以考虑一下，我们如果调用这个方法，将两个任意数传入之和，此方法内部求完和之和，什么都不做，也不给一个反馈，我们调用这个方法有何用呢？
一般，我们调用这个方法之后，可能要打印结果，或者要参与后续运算，所以这个方法需要将计算结果给我返回。

第二种写法（有返回值的写法），更加灵活。我们拿到结果之后，可以打印，也可以做其他事情。
但是第一种写法就比较死板了，只能将结果打印。

如何还弄不清楚，方法什么时候要有返回值，那大家可以考虑一下，系统的方法。
console.log(“abc”);此方法仅仅要处理控制台输出，所以不需要返回值。（undefined）
prompt(“请输入”);此方法目的为了接受用户输入的内容，一般我们要获取用户输入的内容，处理后续逻辑，所以prompt会将接受的结果返回。（String）

如果还弄不清楚，先搁置，方法写的多了，有经验之后，自然而然的就理解了。
1.1.5.函数高级概念
1.1.5.1.参数详解
在JS中实参的个数和形参的个数可以不一致
函数少传了参数，那么没有传的参数就会被认为值是undefined，
函数多传了参数。那么多传的参数就会被忽略

1.1.5.2.返回值详解
函数的返回值是什么，调用这个函数就相当于调用什么，如果没有返回值则为undefined
函数在执行完成return语句后便会退出函数，后面的代码不会执行

1.1.5.3.函数两种定义方式
函数声明
        function fn1() {
            //函数体
        }
函数表达式
        var fn2 = function () {
            //函数体
        };
注意变量方式的函数不能提前调用，为什么？
 
函数声明方式，会函数声明提升，会把函数的声明提升到最顶端
函数表达式方式，属于变量声明提升，会把变量声明提升，不提升赋值，所以提升时var fn2等于undefined。


1.1.5.4.递归调用 了解
程序调用自身的编程技巧称为递归（一般还要有结束的条件，不然就是死递归，浏览器会卡死）
var i = 0;
function story() {
    console.log("从前有座山，山里有座庙，庙里有个老和尚在给小和尚讲故事，故事是：");
    i++;
    if (i < 10) {//条件
        story();
    }
}
story();

1.1.5.5.回调函数 了解
函数也是一种普通的数据类型（function）
因此函数也可以被当作参数传递
被当作参数传递的函数叫做回调函数

var num = 10;
var fn = function () {
    console.log("fn");
}; 
function fn1(a) { 
    a();
} 
fn1(fn); //像这种 被当做参数传递的函数叫做 回调函数
如何理解回调函数？
将函数fn作为参数传递之后，此方法会被fn1回调。一般作为参数传递的函数，都要被回调，所以我们称作为参数传递的函数为回调函数。
注意：
这里可以将fn()传递进去么？
fn1(fn());
答案是不行的。
这个相当于调用了fn();方法，然后将方法的返回值undefined传递给了fn1的a；
1.1.6.全局变量与局部变量
作用域 ： 起作用的区域

1、什么全局变量？
在函数外部声明的变量

2、什么是局部变量？
在函数内部声明的变量

3、函数内部变量没有用var声明在外部可以使用吗？
可以，函数内部没有var声明的变量，属于隐式全局变量。但不建议使用。

4、形参是什么变量？
形参属于局部变量。
1.1.7.函数相互调用
function fn1() {
    console.log("fn1");
    fn2();//函数fn1调用函数fn2
}
fn1();
function fn2() {
    console.log("fn2");
}


1.2.对象
从宏观的角度讲，对象是对客观事物的抽象，事物的特征可以用属性表示，事物的行为可以用方法表示
从微观的角度讲，对象就是一种数据类型，通过对象可以方便地对变量和函数进行管理
初期我们甚至可以把他简单地理解为一个工具箱
1.2.1.键值对
键值对就是一种对应关系，通过键能够方便地找到值
键:值    key:value    k:v
键值对，是一种存储数据的结果，一 一对应。

优点：空间换时间，提高效率

生活中实例：
身份证---人
名称---物品
字典
Css属性
Html属性
1.2.2.对象的声明
对象：万物皆为对象，学生，电脑，自行车等等。

通过构造函数声明（更加通用）
var obj= new Object();
通过字面量声明（更加简便）
var obj= {};

对象具有属性和方法
属性 用来描述对象的特征 一般是名词 对应变量
方法 用来描述对象的行为 一般是动词 对应函数

学生有年龄、名字这些属性也有学习这种行为
小狗有年龄、名字还有汪汪叫的行为

1.2.3.属性
属性的定义
对象.属性名 = 值
属性的调用
对象.属性名
1.2.4.方法
方法的定义
对象.方法名 = function(){ //函数体 }
方法的调用
对象.方法名()

注意：单单 通过 console.log(stu);这个是不会调用的对象内部的方法的，这个只是打印出来stu的定义，包括哪些属性，方法。
1.3.其他概念
1.3.1.对象字面量
var o = {
            name : "zs",
            age : 18,
            sayHi : function() {
                console.log(this.name);
            }
        };
第二种写法：
var stu2 = {
    "name": "zs",//字符串，比较灵活
    "age": 18,
    "se-x":0,//可以包括一些其他字符，比较灵活
    "say-Hi": function () {
        console.log("大家好");
    }
};


1.3.2.对象标记法
JavaScript Object Notation（JavaScript对象标记法）是仿照JS中对象字面量的格式去书写的一串用来记录对象数据的字符串，可以用于数据传输。将来学习AJAX会详细学习。
1.3.3.访问属性的两种方式
两种方式都需要掌握：
点语法（简单）
对象.属性名

中括号（灵活）
对象[“属性名”]

var obj = {};
for (var i = 0; i < 5; i++) {
    obj["n" + i] = i; 
}
console.log(obj);
打印结果：


具体代码：
//对象是无需属性的集合，我们可以把他看成是键值对
var arr = [1, 2, 3, 4, 5];//数组其实也是对象，从var arr=new Array();可以看出。也是通过构造函数创建的数组对象
arr[0] = 20;//键值对形式：索引:值

var obj = {};
//obj.age = 18;
//第二种访问属性的形式（其实与数组类似）
//obj["age"] = 18;//1.如果是字符串必须加上双引号。
//console.log(obj);
for (var i = 0; i < 5; i++) {
    //obj[i] = i;//2.如果是 变量 ，不用加上双引号
    obj["n" + i] = i;//比较灵活，可以通过编程形式添加属性
    //obj.ni//不可行，这个代表的是obj内部属性名为nj
}
console.log(obj);

注意：
obj[“属性名”]形式访问对象属性，需要注意两点：
1.如果是字符串必须加上双引号
2.如果是 变量 ，不用加上双引号

1.3.3.1.扩展
//对象字面量
var stu = {
    name: "zs",//变量名，需要遵循命名规则
    age: 18,
    sayHi: function () {
        console.log("大家好");
    }
};
var stu2 = {
    "name": "zs",//字符串，比较灵活
    "age": 18,
    "se-x":0,//可以包括一些其他字符，比较灵活
    "say-Hi": function () {
        console.log("大家好");
    }
};
以上两种写法，大家应该是比较熟悉的了。
那我们有学习了，访问属性的两种方式，针对以上两种方式，有什么关联么？
以上第一种方式，变量名方式，只能用stu.name访问属性？
以上第二种方式，字符串方式，只能用stu2[“name”]访问属性？
不对，其实以上两种方式，对于属性的两种访问方式都可以用。
console.log(stu.name);
console.log(stu["name"]);
console.log(stu2.name);
console.log(stu2["name"]);

特殊情况：
//stu2.se-x//包含特殊字符的属性，不能以 点的方式访问属性
console.log(stu2["se-x"]);//只能通过中括号方式访问

//访问方法
//stu2.say-Hi();//不行
stu2["say-Hi"]();//先通过中括号方式，获取到属性名的字符串，然后加上小括号调用

1.3.4.遍历的两种方式
通过for可以对集合进行有序的遍历
var arr = [1, 2, 3, 4, 5];
for (var i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}

通过forin可以对集合进行有序的遍历
for(var k in arr) { 语句 }
k变量代表的是arr中的各个属性（key）和 var i = 0中的i是一个意思 名字不同而已

var obj = {
    name: "zs",
    age: 18,
    sex: 0
};
for (var k in obj) {
    //console.log(k);
    console.log(obj[k]);//这里中括号内，只能写“字符串”或者变量
	 //obj.k  不能这么写
}
注意：遍历对象，只能用forin遍历

总结：
for循环//只适用于有序的集合(数组)
forin适用于所有情况，有序集合(数组)，无序集合(对象)
1.4.补充知识点
1.4.1.WebStorm 撤销与取消撤销
Ctrl+z 撤销
Ctrl+shift+z 取消撤销

1.4.2.回调函数与函数相互调用的区别？
函数的相互调用：一个函数调用另外一个函数，就可以称之为函数的调用。
function fn1() {
    console.log("fn1");
    fn2();//函数fn1调用函数fn2
}
fn1();
function fn2() {
    console.log("fn2");
}

回调函数：此函数被作为实参传递了，才叫做回调函数。

var num = 10;
var fn = function () {
    console.log("fn");
}; 
function fn1(a) { 
    a();
} 
fn1(fn); //像这种 被当做参数传递的函数叫做 回调函数
