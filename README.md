# 移动开发个人项目天气预报App文档

1901210358-陈忠毅

## 1.功能介绍

本天气预报主要的功能如下：

1. 显示今日天气状况，包括PM2.5，湿度，空气质量；
2. 查询全国各地城市未来四天内的天气状况；
3. 手动更新天气信息，精确定位并查询当地天气状况，实现分享功能；
4. 了解查询三天之内的具体环境状况，包括天气状况、风力、湿度等；

### 1.1功能模块

![Alt](天气预报 功能.png)

### 1.2 欢迎界面

欢迎界面提供本软件的信息，其中包含定位功能，实现定位功能，跳转到主界面时显示所在地的天气状况。
	

### 1.3主界面

主界面由3个部分组成，分别是状态栏区域，今日天气区域与未来天气区域，其具体内容如下：

1. 状态栏区域 用于显示当前所在城市的名称，其中包含搜索、定位、刷新、分享等功能按钮。
2. 今日天气区域 用于显示今日的天气情况，其中包括所在城市名称、天气发布时间、今天的日期、天气状况（包含图标）、风力大小、空气质量湿度、PM2.5值等具体内容。
3. 未来天气区域 用于显示未来四天的天气状况，其中包含日期、温度、风力大小、天气状况（包含图标）等内容。

### 1.4`Activity`设计

`Activity`是一个应用组件，用户可与其提供的屏幕进行交互，以执行不同的功能操作。 每个`Activity`都会获得一个用于绘制其用户界面的窗口。窗口通常会充满屏幕，但也可小于屏幕并浮动在其他窗口之上。在本系统中主要设计了主要4个`Activity`分别是`MainActivity`,`SelectCity`,`Locamtemap`,`Share`具体功能分别如下所示：

* `MainActivity`
  1. 判断选择当前城市
  1. 获取城市编码
  1. 更新当前城市天气信息
  1. 判断选择当前城市以及是否联网。
* `SelectCity`具体功能
  1. 判断选择当前城市
  1. 判断选择当前城市编码
  1. 返回按钮响应
* `Locamtemap`具体功能
  1. 初始化地图
  1. 判断当前位置
  1. 返回按钮响应
* `Share`具体功能
  1. 分享天气信息至其他程序
  1. 返回按钮响应


### 1.5Java类设计

## 2.技术方案

### 2.1技术实现流程

1. 项目工程创建
   打开 Android Studio开发环境，创建一个空白Android Studio 的Activity项目。
2. 工程布局文件创建
   在Layout目录下，新建一个布局文件“main”，这将是此款APP的主要界面的布局。
   页面布局:在布局文件“main”中进行界面的布局，其主要有工具栏的制作、今日天气以及未来几天的天气情况的页面布局。
3. 功能的实现
   根据上述所提到的天气预报需求分析将功能逐一调试运行成功。
4. 测试与发布
   将设计完成的APP进行最后的测试工作后进行发布。

### 2.2功能实现及关键代码

* Locamtemap获取位置信息

* 城市选择功能
  城市选择功能分为两部分其中核心代码分为搜索城市的代码，热门城市选择的代码（以北京为例）。搜索城市的原理是输入城市信息，通过连接CityDB数据库，实现连接，如数据库中有城市信息则搜索成功，若无城市信息则搜索失败。主要代码如下。

### 2.3Share实现分享功能

* 分享代码：获取手机其他软件的编码，通过权限实现分享功能。
* 反馈代码：通过监听事件来得到分享的结果，反馈分享结果信息。

### 2.4布局

#### 2.4.1欢迎页面

欢迎页面有图片按钮，通过点击图片按钮进入主页面。欢迎界面的目的在于显示App的欢迎页以及获取位置信息，同步主页的天气情况，在主页面中显示当前位置的天气情况。

#### 2.4.2主页面

主页面包含今日天气、未来四天天气情况以及城市选择按钮、定位按钮、更新按钮、分享按钮。通过点击按钮来跳转到具体页面。

#### 2.4.3城市选择页面

城市选择的页面包括两个部分，第一部分是实现城市的查找，输入想要查询的城市后点击后跳转到主页面，在主页面上显示搜索城市的天气情况以及未来四天的天气状况。第二部分为热门城市的列表，点击热门城市同样实现查询功能。

#### 2.4.4位置页面

![Alt](https://i.loli.net/2020/01/14/SheiJmTbv5sl4W1.jpg)
位置页面直接采用了百度地图的SDK包和申请的API密匙（AK）。页面与百度地图的位置信息一致。

#### 2.4.5分享页面

分享页面设计了三个应用程序的分享，它们是分享到QQ、空间、QQ音乐。它同样采用了腾讯开发者平台的SDK包和APP ID。

## 3.创新点

2. 通过调用地图接口可以实现对当前位置的天气信息自动获取与展示和定时刷新功能，也可以通过移动地图界面中的位置针来获取连续位置的天气信息
3. 可以实现当前位置天气信息在多社交平台上的分享功能
4. 关注用户体验，多使用Toast及时反馈当前功能运行状况给用户
