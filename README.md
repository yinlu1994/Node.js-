# Node.js-
## 学习前
* 浏览器大战：没有竞争就没有发展,IE6(感觉自己非常厉害后就不玩了)->2002 Mozilla推出Firefox->2003 Apple推出webKit内核的Safari 仅限Mac->Google推出基于WebKit内核的Chrome 跨平台->Google推出高性能JavaScript引擎V8 开源->webKit成为手机的主流IE6再见。
* 2009 一个外国人推出基于JavaScript 语言和V8引擎的开源web服务器项目，命名为Node.js
* V8引擎：https://blog.csdn.net/swimming_in_it_/article/details/78869549
  * V8引擎是一个JavaScript引擎实现
  * 渲染引擎：能够将HTML/CSS/JavaScript文本及相应的资源文件转换成图像结果。渲染引擎的主要作用是将资源文件转化为用户可见的结果。在浏览器的发展过程中，不同的厂商开发了不同的渲染引擎，如
    * Tridend(IE)
    * Gecko(FF)
    * WebKit(Safari,Chrome,Andriod浏览器)WebKit是由苹果2005年发起的一个开源项目，引起了众多公司的重视
      * Webkit结构：从下向上：操作系统+第三方库（图形库，网络库，视频库···）+webcore(Html解析器，css解析器，Dom···，javascriptcore(谷歌替换成v8))+嵌入式接口
  * JavaScript；解释性语言，与编译型语言不同的是它需要一遍执行一边解析，源代码-→抽象语法树-→字节码-→JIT-→本地代码(V8引擎没有中间字节码)
  * WebKit:Html渲染+JavaScript解析
  * Chrome中webkit和V8的关系：Html渲染（Webkit加封装）+JavaScript解析(V8)
* 现实中的问题：
  * 服务器程序：web应用程序架构的瓶颈；
    * 要支持更多的用户，每个连接都会生成一个新线程->更多的用户->更多的成本（内存，服务器，费用）
    >> 线程与进程：线程：一个程序同时执行多个任务，每个任务称为一个线程，共享数据使用相同的地址空间，更轻量级，线程间通信-cpu切换地址花费小，是程序执行的最小单位，多线程程序一个线程死掉整个进程就会死掉；进程：每个进程拥有一套自己的变量，有独立的地址空间，代价高，操作系统将每个时间片分配给每个进程，并给人一种并行处理的感觉，它是资源分配的最小单位，多进程程序更加健壮。
    >> 多线程非常有用：例如：一个浏览器可以同时下载几幅图片；一个web服务器需要同时处理几个并发请求
    * 客户的请求->服务器之间的共享
    
* Node.js的优势：
  * 借助JavaScript天生的事件驱动机制加V8高性能引擎，使编写高性能Web服务轻而易举。
  * 在Node环境下，通过模块化的JavaScript代码，加上函数式编程，并且无需考虑浏览器兼容性问题，直接使用最新的ECMAScript 6标准，可以完全满足工程上的需求。
## npm
* npm是Node.js的包管理工具（package manager），因为我们在Node.js上开发时，会用到很多别人写的JavaScript代码。如果我们要使用别人写的某个包，每次都根据名称搜索一下官方网站，下载代码，解压，再使用，非常繁琐。于是一个集中管理的工具应运而生：大家都把自己开发的模块打包后放到npm官网上，如果要使用，直接通过npm安装就可以直接用，不用管代码存在哪，应该从哪下载。
* 在Node.js安装的时候顺带装好了。我们在命令提示符或者终端输入npm -v
## 开始Node.js
* 用Sublime Text文本编辑器，第一行总是写上'use strict';是因为我们总是以严格模式运行JavaScript代码，避免各种潜在陷阱。
* 直接输入命令node进入交互模式，相当于启动了Node解释器，但是等待你一行一行地输入源代码，每输入一行就执行一行。
* 直接运行node hello.js文件相当于启动了Node解释器，然后一次性把hello.js文件的源代码给执行了，你是没有机会以交互的方式输入源代码的。
* IDE:Visual Studio Code
* hello.js(注意反斜杠)
```(javascript)
'use strict';
var name = 'world';
var s = `Hello, ${name}`;
console.log(s);
```
* 模块名就是文件名（去掉js）
## 引入模块操作
