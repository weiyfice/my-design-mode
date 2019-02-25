# 整理14种常用设计模式
```
来源:http://www.runoob.com/design-pattern
```

## 基础
### 设计模式的类型
```
设计模式可以分为三大类：创建型模式（Creational Patterns）、结构型模式（Structural Patterns）、行为型模式（Behavioral Patterns）。当然，还有另一类设计模式：J2EE 设计模式。
详情见：http://www.runoob.com/design-pattern/design-pattern-intro.html
```
### 设计模式实践的关系
<img class="magplus" title="设计模式之间的关系" src="http://www.runoob.com/wp-content/uploads/2014/08/the-relationship-between-design-patterns.jpg" alt="设计模式之间的关系" width="700" height="840">

### 设计模式的六大原则
```
1、开闭原则（Open Close Principle）

开闭原则的意思是：对扩展开放，对修改关闭。在程序需要进行拓展的时候，不能去修改原有的代码，实现一个热插拔的效果。简言之，是为了使程序的扩展性好，易于维护和升级。想要达到这样的效果，我们需要使用接口和抽象类，后面的具体设计中我们会提到这点。

2、里氏代换原则（Liskov Substitution Principle）

里氏代换原则是面向对象设计的基本原则之一。 里氏代换原则中说，任何基类可以出现的地方，子类一定可以出现。LSP 是继承复用的基石，只有当派生类可以替换掉基类，且软件单位的功能不受到影响时，基类才能真正被复用，而派生类也能够在基类的基础上增加新的行为。里氏代换原则是对开闭原则的补充。实现开闭原则的关键步骤就是抽象化，而基类与子类的继承关系就是抽象化的具体实现，所以里氏代换原则是对实现抽象化的具体步骤的规范。

3、依赖倒转原则（Dependence Inversion Principle）

这个原则是开闭原则的基础，具体内容：针对接口编程，依赖于抽象而不依赖于具体。

4、接口隔离原则（Interface Segregation Principle）

这个原则的意思是：使用多个隔离的接口，比使用单个接口要好。它还有另外一个意思是：降低类之间的耦合度。由此可见，其实设计模式就是从大型软件架构出发、便于升级和维护的软件设计思想，它强调降低依赖，降低耦合。

5、迪米特法则，又称最少知道原则（Demeter Principle）

最少知道原则是指：一个实体应当尽量少地与其他实体之间发生相互作用，使得系统功能模块相对独立。

6、合成复用原则（Composite Reuse Principle）

合成复用原则是指：尽量使用合成/聚合的方式，而不是使用继承。
```

## 模式详解
### 1.策略模式(Strategy)
```
定义个策略接口，不同的实现类提供不同的具体策略算法，通过context方法确定方法执行时具体执行那个子类的方法，属于行为型模式
混合使用(https://blog.csdn.net/pengpegV5yaya/article/details/25189253)
优点： 1、算法可以自由切换。 2、避免使用多重条件判断。 3、扩展性良好。
缺点： 1、策略类会增多。 2、所有策略类都需要对外暴露。
注意事项：如果一个系统的策略多于四个，就需要考虑使用混合模式，解决策略类膨胀的问题
```
- 示例图片<br/>
<img src="http://www.runoob.com/wp-content/uploads/2014/08/strategy_pattern_uml_diagram.jpg" />

### 2.简单工厂模式( Simple Factory )
```
定义一个用以创建对象的工厂, 根据不同的条件[传参/反射]生成不同的对象，属于创建型模式

- 优点：工厂类是整个模式的关键.包含了必要的逻辑判断,根据外界给定的信息,决定究竟应该创建哪个具体类的对象.通过使用工厂类,外界仅仅需要负责“消费”对象就可以了。而不必管这些对象究竟如何创建及如何组织的。
- 缺点：由于工厂类集中了所有实例的创建逻辑，违反了高内聚责任分配原则，将全部创建逻辑集中到了一个工厂类中；它所能创建的类只能是事先考虑到的，如果需要添加新的类，则就需要改变工厂类了。当系统中的具体产品类不断增多时候，可能会出现要求工厂类根据不同条件创建不同实例的需求．这种对条件的判断和对具体产品类型的判断交错在一起，很难避免模块功能的蔓延，对系统的维护和扩展非常不利；
```

### 3.工厂模式( Factory )
```
针对每一种产品提供一个工厂类，通过不同的工厂实例来创建不同的产品实例。简单工厂是一种产品，工厂是多种产品
```

### 4.抽象工厂模式( Abstract Factory )
```
https://blog.csdn.net/hguisu/article/details/7505909
应对产品族概念而生，属于创建型模式

区别
简单工厂 ： 用来生产同一等级结构中的任意产品。（对于增加新的产品，无能为力）
工厂方法 ：用来生产同一等级结构中的固定产品。（支持增加任意产品）
抽象工厂 ：用来生产不同产品族的全部产品。（对于增加新的产品，无能为力；支持增加产品族）

1）还没有工厂时代：假如还没有工业革命，如果一个客户要一款宝马车,一般的做法是客户去创建一款宝马车，然后拿来用。
2）简单工厂模式：后来出现工业革命。用户不用去创建车。因为客户有一个工厂来帮他创建.想要什么车，这个工厂就可以建。比如想要宝马车。工厂就创建这个系列的车。即工厂可以创建产品。
3）工厂方法模式时代：为了满足客户，车品牌越来越多，如宝马、比亚迪等，一个工厂无法创建所有的车型。于是由单独分出来多个具体的工厂。每个具体工厂创建一种系列。即具体工厂类只能创建一个具体产品。但是轿车工厂还是个抽象。你需要指定某个具体的工厂才能生产车出来。
4）抽象工厂模式时代：随着客户的要求越来越高，轿车必须配置空调。于是这个工厂开始生产轿车和需要的空调。

最终是客户只要对轿车的销售员说：我要宝马空调车，销售员就直接给他宝马空调车了。而不用自己去创建车.
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/abstractfactory_pattern_uml_diagram.jpg" alt="抽象工厂模式的 UML 图">

### 5.装饰者模式( Decorator )
```
动态的给一个对象添加一些额外的功能，属于结构型模式
优点：装饰类和被装饰类可以独立发展，不会相互耦合，装饰模式是继承的一个替代模式，装饰模式可以动态扩展一个实现类的功能。
缺点：多层装饰比较复杂。
使用场景： 1、扩展一个类的功能。 2、动态增加功能，动态撤销。
注意事项：可代替继承。

其他：下图，RedShapeDecorator extends ShapeDecorator
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/decorator_pattern_uml_diagram.jpg" alt="装饰器模式的 UML 图"/>

### 6.代理模式( Proxy )
```
封装被代理对象并限制外界对被代理对象的访问，属于结构型模式
关键代码：实现与被代理类组合。
优点： 1、职责清晰。 2、高扩展性。 3、智能化。
缺点： 1、由于在客户端和真实主题之间增加了代理对象，因此有些类型的代理模式可能会造成请求的处理速度变慢。 2、实现代理模式需要额外的工作，有些代理模式的实现非常复杂。
注意事项：
1、和适配器模式的区别：适配器模式主要改变所考虑对象的接口，而代理模式不能改变所代理类的接口。
2、和装饰器模式的区别：装饰器模式为了增强功能，而代理模式是为了加以控制。
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/proxy_pattern_uml_diagram.jpg" alt="代理模式的 UML 图">

### 7.模板方法模式( Template )
```
1.定义一个操作的算法骨架, 并将一些步骤延迟到子类中
2.一个抽象类公开定义了执行它的方法的方式/模板。它的子类可以按需要重写方法实现，但调用将以抽象类中定义的方式进行。属于行为型模式。

优点： 1、封装不变部分，扩展可变部分。 2、提取公共代码，便于维护。 3、行为由父类控制，子类实现。
缺点：每一个不同的实现都需要一个子类来实现，导致类的个数增加，使得系统更加庞大。
使用场景： 1、有多个子类共有的方法，且逻辑相同。 2、重要的、复杂的方法，可以考虑作为模板方法。
注意事项：为防止恶意操作，一般模板方法都加上 final 关键词，否则扩展类就可以自己实现模板方法。
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/template_pattern_uml_diagram.jpg" alt="模板模式的 UML 图">

### 8.外观模式( Facade )
```
为系统向外界提供一个统一的接口、隐藏系统的复杂性（对使用者来说，只关系需要的结果，不关心怎么实现的）；属于结构型模式
简单理解：电脑开机关机
启动电脑（按一下电源键）：启动CPU、启动内存、启动硬盘
关闭电脑（按一下电源键）：关闭硬盘、关闭内存、关闭CPU
优点： 1、减少系统相互依赖。 2、提高灵活性。 3、提高了安全性。
缺点：不符合开闭原则，如果要改东西很麻烦，继承重写都不合适。
使用场景： 1、为复杂的模块或子系统提供外界访问的模块。 2、子系统相对独立。 3、预防低水平人员带来的风险。
注意事项：在层次化结构中，可以使用外观模式定义系统中每一层的入口。
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/facade_pattern_uml_diagram.jpg" alt="外观模式的 UML 图">


### 9.适配器模式( Adapter )
```
将一个类的接口转换成客户希望的另一个接口。属于结构型模式
简单理解：用于现有业务维护，整合业务逻辑，根据传入的参数来执行具体某个业务
优点： 1、可以让任何两个没有关联的类一起运行。 2、提高了类的复用。 3、增加了类的透明度。 4、灵活性好。
缺点：
1、过多地使用适配器，会让系统非常零乱，不易整体进行把握。比如，明明看到调用的是 A 接口，其实内部被适配成了 B 接口的实现。因此如果不是很有必要，可以不使用适配器，而是直接对系统进行重构。
2.由于 JAVA 至多继承一个类，所以至多只能适配一个适配者类，而且目标类必须是抽象类。

使用场景：有动机地修改一个正常运行的系统的接口，这时应该考虑使用适配器模式。

注意事项：适配器不是在详细设计时添加的，而是解决正在服役的项目的问题。
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/adapter_pattern_uml_diagram.jpg" alt="适配器模式的 UML 图">

### 10.桥接模式( Bridge )
```
将抽象部分与实现部分分离，使它们都可以独立的变化。属于结构型模式

优点： 1、抽象和实现的分离。 2、优秀的扩展能力。 3、实现细节对客户透明。

缺点：桥接模式的引入会增加系统的理解与设计难度，由于聚合关联关系建立在抽象层，要求开发者针对抽象进行设计与编程。

使用场景： 1、如果一个系统需要在构件的抽象化角色和具体化角色之间增加更多的灵活性，避免在两个层次之间建立静态的继承联系，通过桥接模式可以使它们在抽象层建立一个关联关系。 2、对于那些不希望使用继承或因为多层次继承导致系统类的个数急剧增加的系统，桥接模式尤为适用。 3、一个类存在两个独立变化的维度，且这两个维度都需要进行扩展。

注意事项：对于两个独立变化的维度，使用桥接模式再适合不过了。
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/bridge_pattern_uml_diagram.jpg" alt="桥接模式的 UML 图">

### 11.建造者模式( Builder )
```
使用多个简单的对象一步一步构建成一个复杂的对象。属于创建型模式

优点： 1、建造者独立，易扩展。 2、便于控制细节风险。
缺点： 1、产品必须有共同点，范围有限制。 2、如内部变化复杂，会有很多的建造类。
注意事项：与工厂模式的区别是：建造者模式更加关注与零件装配的顺序。
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/builder_pattern_uml_diagram.jpg" alt="建造者模式的 UML 图">

### 12.观察者模式( Observer )
```
定义了一种一对多的依赖关系,让多个观察者对象同时监听某一主题对象,在它的状态发生变化时,会通知所有的观察者。观察者模式属于行为型模式。

优点： 1、观察者和被观察者是抽象耦合的。 2、建立一套触发机制。

缺点：
    1、观察者太多时，通知观察者会耗时比较久
    2、如果在观察者和观察目标之间有循环依赖的话，观察目标会触发它们之间进行循环调用，可能导致系统崩溃。
    3、观察者模式仅仅只是知道观察目标发生了变化。
注意事项：
    1、JAVA 中已经有了对观察者模式的支持类。
    2、避免循环引用。
    3、如果顺序执行，某一观察者错误会导致系统卡壳，一般采用异步方式。
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/observer_pattern_uml_diagram.jpg" alt="观察者模式的 UML 图">

### 13.单例模式( Singleton )
```
保证一个类仅有一个实例,并提供一个访问它的全局控制点.
优点：
1、在内存里只有一个实例，减少了内存的开销，尤其是频繁的创建和销毁实例（比如管理学院首页页面缓存）。
2、避免对资源的多重占用（比如写文件操作）。
   缺点：没有接口，不能继承，与单一职责原则冲突，一个类应该只关心内部逻辑，而不关心外面怎么样来实例化。
单例模式的几种实现方式
1.懒汉式，线程不安全
   这种方式是最基本的实现方式，这种实现最大的问题就是不支持多线程。因为没有加锁 synchronized，所以严格意义上它并不算单例模式。
这种方式 lazy loading 很明显，不要求线程安全，在多线程不能正常工作
2.懒汉式，线程安全
	这种方式具备很好的 lazy loading，能够在多线程中很好的工作，但是，效率很低，99% 情况下不需要同步。
	优点：第一次调用才初始化，避免内存浪费。
	缺点：必须加锁 synchronized 才能保证单例，但加锁会影响效率。
getInstance() 的性能对应用程序不是很关键（该方法使用不太频繁）。
3、饿汉式
	优点：没有加锁，执行效率会提高。
	缺点：类加载时就初始化，浪费内存。
4、双检锁/双重校验锁（DCL，即 double-checked locking）
	这种方式采用双锁机制，安全且在多线程情况下能保持高性能。
getInstance() 的性能对应用程序很关键。
5、登记式/静态内部类
	这种方式能达到双检锁方式一样的功效，但实现更简单。对静态域使用延迟初始化，应使用这种方式而不是双检锁方式。这种方式只适用于静态域的情况，双检锁方式可在实例域需要延迟初始化时使用。
6、枚举
	这种实现方式还没有被广泛采用，但这是实现单例模式的最佳方法。它更简洁，自动支持序列化机制，绝对防止多次实例化。

经验之谈：一般情况下，不建议使用第 1 种和第 2 种懒汉方式，建议使用第 3 种饿汉方式。只有在要明确实现 lazy loading 效果时，才会使用第 5 种登记方式。如果涉及到反序列化创建对象时，可以尝试使用第 6 种枚举方式。如果有其他特殊的需求，可以考虑使用第 4 种双检锁方式。
```

### 14.命令模式( Command )
```
将一个请求封装成为一个对象, 使可以用不同的请求对客户进行参数化
优点：
1、降低了系统耦合度。
2、新的命令可以很容易添加到系统中去。
缺点：使用命令模式可能会导致某些系统有过多的具体命令类。
```
<img src="http://www.runoob.com/wp-content/uploads/2014/08/command_pattern_uml_diagram.jpg" alt="命令模式的 UML 图">