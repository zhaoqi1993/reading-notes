## 总览
#1.精华
#2.语法
#3.对象
* 对象字面量
* 检索
* 更新
* 删除
* 引用
* 原型
* 反射（确定对象有什么属性）
* 枚举
* 减少全局变量影响
#4.函数
* 函数对象
* 函数字面量
* 调用
* 参数
* 返回
* 异常
* 扩充类型的功能
* 递归
* 作用域
* 闭包
* 回调 
* 模块化
* 级联
* 柯里化
* 记忆
#5.继承
* 伪类
* 对象说明符
* 原型
* 函数化
* 部件
#6.数组
* 数组字面量
* 长度
* 删除
* 枚举
* 容易混淆的地方
* 方法
* 指定初始值
#7.正则表达式
#8.对象方法  
* Array
	* array.contact(item)
	* array.join(separator)
	* array.pop()
	* array.push(item)
	* array.reverse()
	* array.shift()
	* array.slice(start,end)
	* array.sort(comparefn)
	* array.splice(start,deleteCount,item)
	* array.unshift(item)
* Function
	* function.apply(thisArg,argArray)
* Number
	* number.toExponentia(fractionDigits)
	* number.toFixed(fractionDigits)
	* number.toPrecision(precision)
	* number.toString(radix)
* Object
	* object.hasOwnProperty(name)
* RegExp
* String
	* string.chartAt(pos)
	* string.charCodeAt(pos)
	* string.concat(string...)
	* string.indexOf(searchString,position)
	* string.lastIndexOf(searchstring,position)
	* string.localeCompare(that)
	* string.match(regexp)
	* string.replace(searchValue,replaceValue)
	* string.search(regexp)
	* string.slice(start,end)
	* string.split(separator,limit)
	* string.substring(start,end)
	* string.toLowerCase()
	* string.toUpperCase()
	* string.fromCharCode(char...)
***
##精华
* js是web唯一的编程语言
* js的特点
	* 弱类型：没有类型错误，变量不限制类型
	* 对象字面量表示
	* 原型继承
	* （垃圾）全局对象

## 语法
* 空白
	* 善用空白，便于理解
* 注释
	* 用 // 注释
* 标识符
	* 不能用保留字
* 数字
	* 64位浮点数 1和1.0相同
	* 100 = 1e2
	* NaN：不等于任何值包括他自己
		* isNaN（number）检测是否为NaN
	* Infinity 表示无限大
	* Math对象，包含所有的数学方法
* 字符串
	* 一对单引号或者双引号中
	* 16位，没有字符类型
	* \ 表示转义字符
	* 字符串一旦创建不能修改
		* + 连接字符串并创建一个新的字符串
		* 字符且字符顺序完全相同的字符串被认为是相同字符串
* 语句
	* ``<script>``提供一个被编译且立即执行的编译单元
	* 函数内部私有变量
	* 前置标签  switch for while do
	* js一般从上到下执行
	* 代码块不新建作用域，变量应该定义到函数头部
	* 语句类型
		* if
			* 真假条件：false null 0 '' NaN undifined
		* switch
			* case
		* while
		* for
		* do
		* try
		* catch
			* 定义一个新变量e来接收抛出的异常对象
		* throw
			* 把控制流跳到catch从句中
		* return
			* 从函数提前返回
			* 没有返回值则返回undifined
			* return false会覆盖默认行为
		* break
			* 跳出循环或者switch
* 表达式
	* ？expression1:expression2
	* 基本类型
		* 数字，字符串，布尔值，null,undefined,对象
	* 运算符优先级
		* 属性提取和调用函数>一元操作符>二元操作符(乘除>加减)>不等式>等式>逻辑与>逻辑或>?:
			* +为加法运算，保证操作数都是数字
			* 第一个操作数为假,&&的值为第一个操作数的值，否则为第二个
			* 第一个操作数为真，||的值为第一个操作数的值，否则为第二个
* 字面量
	* 直接创建对象或者数组，把内部元素直接写好
	* 对象字面量
	* 数组字面量
* 函数

##对象
* 特点
	* 名值对
	* 无类型 
	* 原型链特性
* 对象字面量
	* 包围在一对花括号中的0个或多个key/value（直接创建的对象)
	* 属性名最好都用引号引起来，不要用保留字
	* 一个属性的值可以是一个对象（嵌套）
* 检索
	* 两种方法：object['name'],obj.name
	* 用||填充默认值
		* var mod = obl.name||'zhangsan'
	* 用&&避免从undefined的成员属性中取值
		* obj.a && obj.a.b
* 更新
	* 直接用赋值语句更新
	* obj.name='zhangsan'如果obj本身没有name属性，则会给obj添加name属性，且值为'zhangsan'
* 引用
	* 对象通过引用来传递
	* a=b=c=obj
		* a,b,c都指向同一个对象obj
* 原型
	* 所有对象字面量创建的对象都连接到Object.prototype上
	* 更新obj时，obj的原型是不受影响的
	* 原型被更改，所有继承自原型的对象都会做出相应改变
	* 委托
		* 检索值的时候，逐级向上，知道Object.prototype
* 反射
	* 检查对象并确定对象有什么属性
		* typeof obj.name
	* 原型链中的任何属性都会产生值
		* 1.加一个判断条件，忽略值为函数的属性
		* 2.用hasOwnProperty()
			* 这个方法不会检查原型链
* 枚举
	* for-in
		* 会列出所有属性
		* 建议用hasOwnProperty()过滤，或者用 typeof过滤
		* for-in中，属性名出现的顺序是不确定的
	* 自定义一个属性列表，查找对象中对应这个列表的属性
* 删除
	* delete obj.name
	* obj中的属性会覆盖原型中的同名属性，删除obj中的属性可能会将原型链中的属性显露出来
* 较少全局变量的污染
	* 只用一个对象来存储所有需要的外部变量，这个对象就是唯一的全局变量

##函数
* 函数对象
	* 函数是对象，凡是对象的特点函数都有
	* 函数对象隐藏链接到Function.prototype上
	* 函数创建时有两个隐藏属性：上下文和代码
	* 函数对象的prototype属性，prototype:obj{constructor:该函数}
* 函数字面量
	* 保留字function
	* 函数名（如果没有，为匿名函数）
	* 参数
		* 参数定义为函数中的变量，由实参将其初始化
	* 函数体
* 调用
	* 调用一个函数会暂停当前函数执行，控制权交给新函数
	* 调用符号：()
	* 除了形参，每个函数还有this,arguments
		* 实参数大于形参数，超过的会被被忽略
		* 实参数小于形参数，缺失的会被定为undifined
		* 参数没有类型检查
	* 调用类型
		* 方法调用
			* 函数为一个对象的方法，通过对象调用函数
			* this绑定在该对象上
		* 函数调用
			* 直接调用，并不属于某个对象
			* this绑定在全局对象
				* var that=this;在内部函数中，可以通过that访问到外部函数所在的对象
		* 构造器调用
			* new
			* 背地里创建一个链接到该函数prototype成员的新对象，this绑定在这个对象上
			* 给构造函数的实例增加方法fun，构造函数.prototype.fun = function{...}
		* apply() 
			* 函数的一个方法
			* fun.apply(this要绑定的对象，参数)
* 参数
	* arguments
		* 包含所有传递给函数的参数
		* arguments有length属性，没有任何数组方法
* 返回
	* return执行时，函数立即返回
	* 没有指定返回值，返回undifined
	* 函数调用时有new前缀，返回值不是对象，则返回this，这个this指向新对象
* 异常
	* throw
		* 中断函数执行，抛出一个exception对象，包含name，message属性，把函数流转到catch
	* 一个try只能有一个catch
* 扩充类型的功能
	* 给Object.prototype添加方法，所有的实例对象都包含该功能
* 递归
* 作用域
	* JS不支持块块级作用域
	* JS只有函数作用域，函数内定义的变量只能函数内部访问
* 闭包
	* 内部函数可以访问它被创建时所处的上下文环境
	* 内部函数可以访问定义它的外部函数的参数和变量（this和arguments除外）
	* 用函数的方法，通过返回一个有方法的对象，因为闭包的原因，这些方法可以访问函数作用域内的私有变量
	* 内部函数如果需要，外部函数的变量会一直保留
	* 内部函数访问外部函数的实际变量而无需复制
		* 区分变量i和构造时的变量i
* 回调 
	* 参考AJAX
* 模块
	* 用函数和闭包来构造模块
	* 定义了私有变量和函数的函数；利用闭包创建可以访问私有变量和函数的特权函数；最后返回这个特权函数
	* 用模块来产生安全对象
		* 特权函数不用this或that
		* 除非调用特权函数， 否则无法修改私有变量；如果特权函数被替换，替换的函数不能访问私有成员
			* 持久性对象
* 级联
	* 参考jquery的链式用法
* 柯里化
	* 把函数与传递给它 的参数相结合，产生一个新的函数
* 记忆
	* 用一个数组或者对象来保存中结果；并将这个数组或者对象放到闭包中

##继承
* 伪类
	* 构造器函数有prototype对象，用于存放继承特征
	* 扩充原型对象
		* 扩充构造器函数的prototype
	* 伪类继承
		* 把A构造函数的prototype赋值为构造函数B的一个实例
			* 此时，A的实例也拥有B中定义的属性和方法
	* Function('function_name',function(argument){..}）
		* Function方式定义 函数
	* 尽可能的不要用构造器函数
		* 忘记new前缀就悲剧了
* 对象说明符
	* 给构造器函数传递参数的时候传入一个对象说明符 var myObj= maker({name:zhang,age:23...})
		* 不用考虑参数的顺序
		* 可以和JSON配合，将方法和数据联系起来
* 原型
	* 先构建一个对象
	* 通过var new_obj = Object.create(构建好的对象）构造一个新的实例
	* 在new_obj上添加属性和方法，定制成一个新的实例
* 函数化
	* 用闭包的思想构造对象
	* 代码模板
		*  var constructor = function(spec,my){  var that,其他私有实例变量；my=my||{};that = 一个新对象;给that添加特权方法；return that}
			*  spec对象包含构造新实例所需要的所有信息（传入的参数）
			*  My是构造器提供的共享秘密的容器。其他构造器可以分享my里的内容，或者是把自己可分享的内容放入其中
			*  扩充that;
				* 建议先定义函数，再把函数名用来扩充that
* 部件 

## 数组
* 数组字面量
	* js中，数组也是对象
	* 数组的属性名为'0','1'...
		* 也可以用对象字面量创建数组，但是继承自Object.prototype
		* 常规的数组字面量创建数组，继承自Array.prototype
	* 数组有length属性
	* 数组可以包含任何混合类型的值
* 长度
	* 如果用大于当前length的数字作为下标来存储元素，length值会被增大，不会发生越界错误
	* []会把其中的表达式转换成字符串
	* length属性的值是数组最大整数属性名加1
	* 设置更大的length不会给数组分配更多的空间，length设小将会导致所有下标大于等于新length的属性被删除
* 删除
	* splice方法
	* delete方法，删除对象元素的方法，会在数组留下一个空洞，
		* 排在被删除元素之后的元素保留着最初的属性，不会向前移动
* 枚举
	* for(var i=0;i<array.length;i++){...}
		* 不要用for-in
* 容易混淆的地方
	* 区分什么时候用数组，什么时候用对象
* 扩展方法
	* 在Array.prototype上扩展方法
	* 给单个数组扩展方法
		* 相当于给对象扩展
* 指定初始值
	* JS数组没有预置值
	* 访问一个不存在的元素，得到undefined；
	* JS处理二维数组 
		* 元素为数组的数组
		* 通过for来解决，类似C中的多维数组

## 方法
* Array
	* array.concat(item)
		* 包含对array的浅复制，吧一个或多个item附加在后面
	* array.join(separator)
		* 把数组array中的元素用一个分隔符（默认是，）连接成一个字符串
			* 先把每个元素构造成一个字符串，然后用分隔符链接
	* array.pop()
		* 移除array中最后一个元素并返回
	* array.push(item...)
		* 把一个或者多个item附加到数组的尾部，并返回array的新长度
			* 如果item是一个数组，会把它当作单个元素添加到数组中
	* array.reverse()
		* 反转array里 元素的顺序
	* array.shift()
		* 移除数组的第一个元素并返回该元素
			* 如果数组是空的，返回undefined
			* 比pop慢
	* array.slice(start,end)
		* 对array中的一段做浅复制并返回
		* end参数可选，默认为array.length，从1计数
			* start从0计数
		* 如果参数中任何一个是负数，array.length会和他相加，试图变成非负数
		* start大于array.length，得到空数组
	* array.sort(comparefn)
		* 字符串排序
		* 默认排序函数把元素都视为字符串
	* array.splice(start,deleteCount,item...)
		* 从array中移除一个或者多个元素，并用item替换，返回包含被移除元素的数组
	* array.unshift(item)
		* 把item插入到数组的开始部分，并返回array新的length
* Function
	* function.apply(thisArg,argArray)
* Number
	* number.toExponentia(fractionDigits)
		* 把Number转化成科学计数法表示的字符串，fractionDigits表示小数点后面的位数
	* number.toFixed(fractionDigits)
		* 把number转化成十进制数形式的字符串
			* fractionDigits表示小数点后数字的位数
	* number.toPrecision(precision)
		* number转换成十进制数字形式的字符串
		* precision表示有效数字位数
	* number.toString(radix)
		* number转换成一个字符串
		* radix表示基数，默认为10
* Object
	* object.hasOwnProperty(name)
* RegExp
* String
	* string.chartAt(pos)
		* 返回string中pos处的字符
			* 如果pos不在范围内，返回空字符串
			* js中只有字符串
	* string.charCodeAt(pos)
		* 和charAt(pos)一样，只是返回pos处字符对应的编码
			* 不再范围内，返回NaN
	* string.concat(string...)
		* 不如+
	* string.indexOf(searchString,position)
		* 在string中查找另一个字符串searchString，并返回第一个匹配字符的位置，否则返回-1
		* pos可以设定从string的某个位置开始寻找
	* string.lastIndexOf(searchstring,position)
		* 和indexOf（）相同，只不过从后向前找
	* string.localeCompare(that)
	* string.match(regexp)
	* string.replace(searchValue,replaceValue)
		* 字符串查找和替换
		* searchValue是字符串，只会替换第一个匹配的地方；如果是带有g标识的正则，替换所有匹配
		* replaceValue是字符串，$;是函数
	* string.search(regexp)
		* 和indexOf()类似，接收一个正则且忽略其g标识；找到返回首次出现位置，没找到返回-1
	* string.slice(start,end)
		* 和array.slice(start,end)类似
	* string.split(separator,limit)
		* 把string分割成片段创建一个数组并返回
		* 可选参数limit显示被分割的片段的数量
	* string.toLowerCase()
		* string中所有字母转化成小写并返回转化后的string
	* string.toUpperCase()
		* 返回一个新的字符串，string中所有的字符转换成大写
	* string.fromCharCode(char...)