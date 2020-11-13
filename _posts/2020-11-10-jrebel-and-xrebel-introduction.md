---
layout: post
title: Intellij IDEA集成JProfiler性能分析
categories: Java
description: Intellij IDEA集成JProfiler性能分析
keywords:  Intellij,IDEA,JProfiler,性能分析
---

Jenkins是当前非常流行的一款持续集成工具，可以帮助把更新后的代码自动部署到服务器上运行。

### 一. 插件&软件安装

1. 插件在IDEA上直接下载Preferences–>plugins–>Browse repositories。
![](/images/posts/other/1604971412833.jpg)
2. JProfiler软件安装，[官网下载](https://www.ej-technologies.com/download/jprofiler/files)

![](/images/posts/other/1604971709654.jpg)

### 二. 配置IDEA运行环境
1. JProflier激活
    * JProfiler11 序列号
    > L-J11-Everyone#speedzodiac-327a9wrs5dxvz#463a59
    > 
    >A-J11-Everyone#admin-3v7hg353d6idd5#9b4
    ![](/images/posts/other/2018042515023882.png)
2. Preferences–>Tools–>JProflier–>JProflier executable选择JProfile安装可执行文件。
![](/images/posts/other/QQ20201110-093306.png)

### 三. IDEA中启动JProflier

1. 选择要分析的项目，点击JProfiler图标启动。
 ![](/images/posts/other/1604972954014.png)
2. 启动完成会自动弹出JProfiler窗口，在里面就可以监控自己的代码性能了。
![](/images/posts/other/20201110095319.png)
![](/images/posts/other/QQ20201110-095418.png)

### 四. JProflier功能介绍



### 五. 配置JRebel和JProfiler同时运行
有些人在IDEA中配置了JRebel热部署，要想JRebel和JProfiler同时运行，就要改手动管理JProfiler session了。

**第一步，配置启动参数**
- 方式1：
在要分析的tomcat启动脚本catalina.bat中增加一行。
> set CATALINA_OPTS=-agentpath:D:\service\jprofiler9\bin\windows-x64\jprofilerti.dll=port=8849,nowait,id=80,config=C:\Users\Administrator\.jprofiler9\config.xml %CATALINA_OPTS%
- 方式2：
在IDEA Run/Debug Configurations窗口JRebel Debug中配置Environment Variables属性。
> CATALINA_OPTS=-agentpath:D:\service\jprofiler9\bin\windows-x64\jprofilerti.dll\=port\=8849,nowait,id\=81,config\=C:\Users\Administrator\.jprofiler9\config.xml

![](/images/posts/other/20201110095319.png)

**第二步，启动JRebel**
![](/images/posts/other/QQ20201110-095418.png)

**第三步，看到控制台如下信息，说明JRebel和JProfiler都启动了**
![](/images/posts/other/QQ20201110-095418.png)