[EN](./android_code_location.md) | [ZH](./android_code_location-zh.md)
# Android 关键代码定位

AndroidManifest.xml文件

- 软件包名
- apk主活动，隐藏程序没有主Activity

Application在 java层启动最早，

## 顺序分析

最常见也是最有用的方法就是，我们顺着程序的逻辑依次查看程序的代码来进行分析，但是当程序代码量特别大时候，这一方法的效率就比较低下，需要其他方法来辅助。

## 字符串定位法

所谓字符串定位法就是通过在程序程序运行过程中出现的字符串来定位相应的函数。字符串有可能被直接硬编码在程序中，也有可能通过字符串id来索引。这一方法故去使用比较方便，但现在的话，有可能字符串会被分开或者说首先被加密，在运行的过程中被动态解密。

我们可能关注的字符串可能有

- 程序报错信息
- 服务
- 广播

## 敏感API定位

所谓敏感API定位法，意思就是我们根据程序的执行行为来判断程序可能调用了哪些函数。这一方法需要我们对于Android中的API比较熟悉。一般来说，我们可能会关注以下方面

- 控件的事件函数
    - onclick
    - show
    - Toast
- 网络函数
    - HttpGet
    - HttpPost
    - HttpUriRequest
    - socket
- 发送短信
- 打电话
- 定位
- 等等


## log信息

所谓log信息就是Android程序在运行时输出的字符串信息，这部分信息不会在我们的界面上体现，因而我们需要使用其它辅助工具来分析，比如说，我们可以使用ddms来辅助分析。对于log信息来说，我们可以从两个方面考虑

- 利用程序本身产生的log信息
- 自己对代码反编译，插入log信息，并重打包来进行分析。

## 栈跟踪

我们可以用ddms提供的方法调用链的信息来判断程序目前的调用关系如何。

## 钩子

- xposed
- cydia

## monitor

- 运行log，程序运行产生的，系统运行产生的
- 线程跟踪
- 方法调用链

## 动态调试