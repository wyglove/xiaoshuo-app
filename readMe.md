# 使用app源码编译自己的 小说APP

---

> 目前为主，专业版继续赠送app源码，安装[专业版小说插件](http://addon.discuz.com/?@jameson_read.plugin)的用户,请联系 
> [![](http://wpa.qq.com/pa?p=2:2867557054:51)](http://wpa.qq.com/msgrd?v=3&uin=2867557054&site=qq&menu=yes) 索要源码
> 

**下载演示app **


![](http://xf512.com/html/images/demo.png)


> 如果你还没有安装[小说阅读器插件，请去这个地址安装http://addon.discuz.com/?@jameson_read.plugin](http://addon.discuz.com/?@jameson_read.plugin)，去这个地址查看帮助文档[xf512.com/doc.php?name=jamesonread](http://xf512.com/doc.php?name=jamesonread)

----

## 零:上传接口文件

将源码中接口文件夹下的xifeng文件夹，上传到 你安装插件的网站根目录下，然后到后台-插件-小说阅读器-手机版-拉到底部，看是否出现了app相关的选项，如果有，则全部填写，不要留空，如果没有，说明你上传的位置不对

![](http://xf512.com/html/images/api12.jpg)


## 一：准备所需的资源
- apicloud 工具 下载地址 [http://apicloudspace.b0.upaiyun.com/studio-win/APICloud-Studio_v1.5.0.zip](http://apicloudspace.b0.upaiyun.com/studio-win/APICloud-Studio_v1.5.0.zip)
- 注册 apicloud 帐号，注册地址 [http://www.apicloud.com/signup](http://www.apicloud.com/signup)
- 准备三张 宽高为 1080\*1920 的png图片，作为app第一次启动时展示给用户的引导界面，并分别命名为 **s1.png**   **s2.png**   **s3.png**
- 准备一张 宽高为 1080*1920 的png图片，作为每次启动时都要显示的闪屏图片
- 准备一张 宽高为 200*200   的png图片，作为app的桌面图标

## 二：登录apicloud网站

登录地址为 [http://www.apicloud.com/signin](http://www.apicloud.com/signin),用你之前注册的帐号密码登录，登录后 点击 **创建应用** 按钮
![](http://xf512.com/html/images/api1.jpg)
在弹出的对话框中 选择 **Native**，然后填写app名字和介绍
![](http://xf512.com/html/images/api2.jpg) 
点击创建。

创建后即自动进入了本app的详细设置页面，开始进行如下设置
- 端设置
> 点击左侧 **端设置**

![](http://xf512.com/html/images/api3.jpg)

- 创建安卓证书
> 点击左侧 **证书**

![](http://xf512.com/html/images/api4.jpg)

   证书信息随意填写


- 添加使用到的模块，下面是用到的模块名称

	smsVerify
	fileBrowser
	webBrowser
	speechRecognizer
	FNScanner
	audio
	UISearchBar
	personalCenter
	UILoading
	dialogBox
	qq
	wx
	bookReader
	fs
	welcomePage

> 点击左侧 **模块**，然后在右侧再点击**模块库**，再在搜索框中分别输入如下模块名称搜索，搜索出来了，点击模块的右上角** +** 号

![](http://xf512.com/html/images/api5.jpg)



- 复制 此app的ID，并记录下来
点击左上角 **概览**，复制 app 的ID，并记录下。

![](http://xf512.com/html/images/api6.jpg)


## 三：打开 apicloud 工具，同步源码

- 打开你下载安装的 apicloud软件，用你的apicloud 帐号密码登录，登录后按下图操作

![](http://xf512.com/html/images/api7.jpg)

然后检出含有 你 app ID 的那个项目

![](http://xf512.com/html/images/api8.png)

检出后，点击 **我的app项目**,然后按照下图，打开项目所在的本地文件夹
![](http://xf512.com/html/images/api9.png)

打开后，删除除了 config.xml、.project、.svn 外的所有文件和文件夹

![](http://xf512.com/html/images/api10.jpg)


然后复制我们赠送的app源码中源代码文件夹下，除了config.xml外的所有文件和文件夹，粘贴到这里。

![](http://xf512.com/html/images/api11.jpg)


- 开始替换你的资源
1. 打开 **config.xml**，点击 **源码**，切换到源码模式
![](http://xf512.com/html/images/api14.jpg) 
将此处的代码复制到 </widget>前面
```
<feature name="wx">
    <param name="urlScheme" value="wxc276b178b0f82200"/>
    <param name="apiKey" value="wxc276b178b0f82200"/>
    <param name="apiSecret" value="7c15dbd4750f2b95d69c8ea9a01b9d5b"/>
</feature>
<feature name="qq">
    <param name="urlScheme" value="tencent1105596557"/>
    <param name="apiKey" value="1105596557"/>
</feature>
<feature name="smsVerify">
    <param name="android_app_key" value="169aa091179f3"/>
    <param name="android_app_secret" value="5c8d14b5601bb21209f04fff8542a791"/>
</feature>
```
> wx、qq、smsVerify 字段中，分别是 QQ登录、微信登录、手机注册发送验证码所需的appkey和seecret，你需要分别去微信开放平台和QQ开放平台以及mob去申请自己的key。

- [微信的申请教程地址http://docs.apicloud.com/Client-API/Open-SDK/wx](http://docs.apicloud.com/Client-API/Open-SDK/wx)
- [QQ的申请地址](http://docs.apicloud.com/Client-API/Open-SDK/qq)
- [smsVerify的申请地址](http://docs.apicloud.com/Client-API/Open-SDK/smsVerify)

2. 复制你准备好的 s1.png s2.png s3.png，覆盖到项目文件夹下 image 文件夹中

3. 打开**index.html**文件，将里面的 http://demo.xf512.com/xifeng/ 替换为你的 xifeng 文件夹所在网址，比如 你将接口文件夹 xifeng上传到了 www.abc.com 的根目录下，则这里填写 http://www.abc.com/xifeng/

4. 打开 book 文件夹下 **faxian.html**文件夹， 找到约 92 行左右，将 **http://xf512.com/**替换为你的网址，将后面的两处 **西风工作室** 改成你的网站名称，这里的名称将显示在app发现页面，用户点击后就会打开你填写的网址

![](http://xf512.com/html/images/api15.jpg)

- 开始同步
回到 apicloud 工具中，在 项目文件夹上右键--云端同步--提交，然后在弹出的对话框中确认

![](http://xf512.com/html/images/api16.jpg)

## 四：编译成app
这就是最后一步了，提交同步后，打开 apicloud网站开发控制台 [http://www.apicloud.com/console](http://www.apicloud.com/console)

进入你的应用详情界面
![](http://xf512.com/html/images/api17.jpg)


点击左侧云编译，右侧填写应用名称、选中android平台、选择正式版，然后点击底部的提交按钮

![](http://xf512.com/html/images/api18.jpg)

等待编译结束，然后点击下载你的安装包就可以了

![](http://xf512.com/html/images/api19.jpg)
---
![](http://xf512.com/html/images/api20.jpg)

## 效果预览
**下载演示app **
![](http://demo.xf512.com/xifeng/demo.png)

###首页
----
![](http://xf512.com/html/images/app2.png)

### 书架
---
![](http://xf512.com/html/images/app3.png)

### 书库
----
![](http://xf512.com/html/images/app4.png)

### 发现

----

![](http://xf512.com/html/images/app5.png)

### 图书详情

----
![](http://xf512.com/html/images/app6.png)

### 阅读界面

----

![](http://xf512.com/html/images/app7.png)


### 登录界面

----

![](http://xf512.com/html/images/app8.png)
