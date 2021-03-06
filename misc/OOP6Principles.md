# 面向对象六大原则(SOLID+)

## 基本概念
功能：比如一个ImageLoader，负责实现图片加载，但是要支持缓存；那么这个ImageLoader就是我们讨论的功能；

依赖：上述ImageLoader功能，需要支持缓存，但是缓存其实也是一个很大的功能，而且会有多种策略，那么ImageLoader就不应该把缓存功能紧耦合，而是作为一个外部的依赖；

使用者：上述ImageLoader作为一个功能，可以打包成一个库，那么用这个库的APP就是使用者；

使用者的需求是经常变化的，因为他们的业务会随着迭代而不断调整，那么ImageLoader这个功能好的实现就是无论使用者的需求怎么变化，都无需改变ImageLoader这一功能的实现。但是对于缓存这一核心特性，也应该做到按需定制，而无需改变ImageLoader的实现代码；

## 单一职责原则(S)
非常直观的，一个类越简单，就越难有bug，50行代码基本不可能有bug，即便出了bug，也很容易分析出来，甚至都不用调试。

所以，尽可能的拆分，尽可能地简化一个类的职责，并且聚焦于这个单一的职责。一个类只聚焦于自己的职责时，需要修改一个功能，那么被修改的类也就会尽可能的少了。

## 开闭原则(O)
抽象来说，就是“对扩展开放，对修改封闭”。具体点，就是功能的修改、增加，尽可能通过增加新的类（扩展）来实现，而不是修改已有的类。

但是如何达到这个效果？就是尽量把可能会变动的地方抽象出来，使用接口进行依赖，具体的实现通过依赖注入来耦合。这样，修改功能就是增加新的实现，在使用者的代码里面注入新的实现。使用者的需求变了，代码的修改是不可避免的，但是功能的框架，如果能不修改，那就降低了引入bug的可能性。

## 里氏替换原则(L)
所有引用基类的地方必须能透明地使用其子类的对象。满足此条件时，对依赖的声明（成员、参数）都通过抽象基类来完成，则使用新的实现类时，只需替换注入/传递的参数即可，功能实现无需改变。更进一步，使用接口声明依赖，能一定程度上避免继承引入的问题。

## 接口隔离原则(I)
客户端不应该依赖它不需要的接口；一个类对另一个类的依赖应该建立在最小的接口上。根据接口隔离原则，当一个接口太大时，我们需要将它分割成一些更细小的接口，使用该接口的客户端仅需知道与之相关的方法即可，可以达到屏蔽其他接口可见性的效果。

## 依赖倒置原则(D)
模块间的依赖通过抽象发生，抽象即抽象类或者接口；使用接口更佳，而且接口内不要定义任何数据；

## 迪米特法则（最小知识原则）
一个类应该对自己依赖（使用）的其他类知道得最少，所谓知道，就是使用。可以类比接口隔离原则，依赖尽可能少的接口，每个接口又仅仅包含确实和自己的功能相关的方法。
