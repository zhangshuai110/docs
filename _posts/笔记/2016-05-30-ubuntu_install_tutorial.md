---
layout: post
title: ubuntu使用笔记
category: 笔记
tags: ubuntu 笔记
keywords: ubuntu linux 
description: 这个文件是在李浩同学写的基础上写的。也正是由于这个文档才使我萌生了写文档的念头。
---

# 源
## 修改源命令
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak #备份
sudo gedit /etc/apt/sources.list #修改
sudo apt-get update #更新列表
## 源地址
deb http://mirrors.ustc.edu.cn/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.ustc.edu.cn/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.ustc.edu.cn/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.ustc.edu.cn/ubuntu/ trusty-proposed main restricted universe multiverse 
deb http://mirrors.ustc.edu.cn/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.ustc.edu.cn/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.ustc.edu.cn/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.ustc.edu.cn/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.ustc.edu.cn/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.ustc.edu.cn/ubuntu/ trusty-backports main restricted universe multiverse

deb http://mirrors.163.com/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ trusty-backports main restricted universe multiverse
#系统配置
##Remmina升级
https://github.com/FreeRDP/Remmina/wiki

```
sudo apt-add-repository ppa:remmina-ppa-team/remmina-next
sudo apt-get update
sudo apt-get install remmina remmina-plugin-rdp libfreerdp-plugins-standard
```
##Oh my Zsh!
http://ohmyz.sh/
安装：

+ 安装zsh
    `sudo apt-get install zsh`
+ Oh my zsh!
```
自动安装
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh

手动安装(tuijian)
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```
+ 设置别名
```
alias cls='clear'
alias ll='ls -l'
alias la='ls -a'
alias vi='vim'
alias javac="javac -J-Dfile.encoding=utf8"
alias grep="grep --color=auto"
alias -s html=mate   # 在命令行直接输入后缀为 html 的文件名，会在 TextMate 中打开
alias -s rb=mate     # 在命令行直接输入 ruby 文件，会在 TextMate 中打开
alias -s py=vi       # 在命令行直接输入 python 文件，会用 vim 中打开，以下类似
alias -s js=vi
alias -s c=vi
alias -s java=vi
alias -s txt=vi
alias -s gz='tar -xzvf'
alias -s tgz='tar -xzvf'
alias -s zip='unzip'
alias -s bz2='tar -xjvf'
```
+ 配置
  查看当前版本shell：
  ~$ echo $SHELL/bin/bash
	/bin/bash/bin/bash
  替换bash为zsh：
  ~$ chsh -s /bin/zsh
    zsh 的配置主要集中在用户当前目录的.zshrc里，用 vim 或你喜欢的其他编辑器打开.zshrc，调整主题
    `ZSH_THEME="random"`

    如果是 Linux，去下载 autojump 的最新版本，比如：
    https://github.com/wting/autojump

## the fuck
`wget -O - https://raw.githubusercontent.com/nvbn/thefuck/master/install.sh | sh - && $0`

##  open in the terminal 在窗口中打开命令窗口
You have to install the Install nautilus-open-terminalnautilus-open-terminal package from the universe repositories:
`sudo apt-get install nautilus-open-terminal`
Then:（必须执行这样）
`nautilus -q`
In order to restart Nautilus

#基本应用
##用Ubuntu做日常开发电脑的系统是一种怎样的体验？
http://www.zhihu.com/question/30816866
## 搜狗输入法
http://pinyin.sogou.com/linux/?r=pinyin
##金山WPS
    http://archive.ubuntukylin.com:10006/ubuntukylin/pool/main/w/wps-office/wps-office_9.1.3_amd64.deb

    安装之前确认 `sudo apt-get install openjdk-7-jdk`

## texlive， texstudio
分享一下安装和配置经验。需要手动安装
1、材料准备
 texlive的安装包：可以百度下

2、安装texlive 2013
这个安装比较简单，我用的是ubuntu12.04.4。 具体步骤是，mount一下你下载的iso文件。
sudo mkdir /media/texlive
sudo mount texlive2013-20130530.iso  /media/texlive

然后进入到 /media/texlive目录下，执行：

./install-tl
提示输入的时候，输入I （大写的i，会看到提示的）

安装完成后，可以向/etc/profile文件的最后一行添加如下代码，注意，我的系统是64位的，你要看看你自己的系统是不是在这个目录下有latex命令。

export PATH=/usr/local/texlive/2013/bin/x86_64-linux:$PATH

如果你想使用帮助的话，还可以向～/.bashrc中添加下面两行：

export MANPATH=/usr/local/texlive/2013/texmf-dist/doc/man:$MANPATH
export INFOPATH=/usr/local/texlive/2013/texmf-dist/doc/info:$INFOPATH

到这里，我一般会重启一下。

测试一下上面的配置是否正确：
which latex

如果找到了latex，那就可以继续了，找不到的话，你需要重新看一下自己是不是没有配置好环境PATH

3、搞定中文字体

先写一个简单的测试tex文件。起名为test.tex

\documentclass[UTF8]{ctexart}
\begin{document}
我爱中国！
\end{document}

然后执行如下命令编译：

xelatex test.tex

等一会，你会遇到一个错误，大致如下：

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!
! fontspec error: "font-not-found"
!
! The font "SimSun" cannot be found.
!
! See the fontspec documentation for further information.
!
! For immediate help type H <return>.
!...............................................

下面就要解决这个问题，错误里说了，"font-not-found"!

先执行如下命令：

cd /etc/fonts/conf.d
sudo ln -s /usr/local/texlive/2013/texmf-dist/tex/latex/ctex/fontset/ctex-xecjk-winfonts 09-texlive.conf

上面的命令是为了让系统可以使用texlive的字体

在做如下操作：

cd /usr/share/fonts
sudo mkdir WinFonts

然后将下载的字体解压后，拷贝到新建的目录WinFonts下，然后执行如下命令：

sudo chmod 644 *.ttf
sudo mkfontscale
sudo mkfontdir
sudo fc-cache -fsv

执行成功后，在做如下操作：

cd  /usr/local/texlive/2013/texmf-dist/tex/latex/ctex/fontset/

在进入目录后，ls，你会看到一个文件ctex-xecjk-winfonts.def

用编辑器打开，内容大致如下：

% ctex-xecjk-winfonts.def: Windows 的 xeCJK 字体设置，默认为六种中易字体
% vim:ft=tex

\setCJKmainfont[BoldFont={SimHei},ItalicFont={[SIMKAI.TTF]}]
  {SimSun}
\setCJKsansfont{SimHei}
\setCJKmonofont{[SIMFANG.TTF]}

\setCJKfamilyfont{zhsong}{SimSun}
\setCJKfamilyfont{zhhei}{SimHei}
\setCJKfamilyfont{zhkai}{[SIMKAI.TTF]}
\setCJKfamilyfont{zhfs}{[SIMFANG.TTF]}
% \setCJKfamilyfont{zhli}{LiSu}
% \setCJKfamilyfont{zhyou}{YouYuan}

\newcommand*{\songti}{\CJKfamily{zhsong}} % 宋体
\newcommand*{\heiti}{\CJKfamily{zhhei}}   % 黑体
\newcommand*{\kaishu}{\CJKfamily{zhkai}}  % 楷书
\newcommand*{\fangsong}{\CJKfamily{zhfs}} % 仿宋
% \newcommand*{\lishu}{\CJKfamily{zhli}}    % 隶书
% \newcommand*{\youyuan}{\CJKfamily{zhyou}} % 幼圆

\endinput

下面，打开新的终端，执行如下命令:

fc-list :lang=zh-cn

输出大约如下：

FangSong,仿宋:style=Regular,...
KaiTi,楷体:style=Regular,...
SimSun,宋体:style=Regular
SimHei,黑体:style=Regular...

下面需要做的就是将ctex-xecjk-winfonts.def中的字体名字改成上面四行的行首的内容。
如果你用vim,可以在vim里执行如下命令：

:%s/\[SIMFANG.TTF\]/FangSong/g
:%s/\[SIMKAI.TTF\]/KaiTi/g

重新执行一下，那个编译命令吧：

xelatex test.tex

！！！字体设置https://www.tug.org/texlive/doc/texlive-zh-cn/texlive-zh-cn.pdf
#开发应用
   + 搜狗输入法（中文输入法）
     http://jingyan.baidu.com/article/f3ad7d0ff8731609c3345b3b.html

## liverelod
   一、简单的安装方法

http://chedanji.com/sublime-text3-livereload/
## How to disable unity online search feature?
http://www.unixmen.com/disable-unity-online-search-feature-ubuntu-14-10/
## How to Improve Laptop Battery Life and Usage in Linux Using TLP
http://www.unixmen.com/how-to-improve-laptop-battery-life-and-usage-in-linux-using-tlp/
##  Top Things To Do After Installing Ubuntu 15.04
http://www.unixmen.com/top-things-to-do-after-installing-ubuntu-15-04/
## Webstorm
 `sudo apt-get install openjdk-7-jdk`
 安装openjdk webstorm的依赖关系


WebStorm注册码

User Name:

EMBRACE

License Key:

```
===== LICENSE BEGIN =====
24718-12042010
00001h6wzKLpfo3gmjJ8xoTPw5mQvY
YA8vwka9tH!vibaUKS4FIDIkUfy!!f
3C"rQCIRbShpSlDcFT1xmJi5h0yQS6
===== LICENSE END =====
```



PhpStorm注册码

User Name:

EMBRACE

 License Key:

===== LICENSE BEGIN =====
43136-12042010
00002UsvSON704l"dILe1PVx3y4"B3
49AU6oSDJrsjE8nMOQh"8HTDJHIUUh
gd1BebYc5U"6OxDbVsALB4Eb10PW8"
===== LICENSE END =====
```
## nodejs 安装
+ 下载node-v4.2.4.tar.gz
```
#  tar xvf node-v0.10.28.tar.gz
#  cd node-v0.10.28
#  ./configure
# make
# sudo make install
# sudo cp /usr/local/bin/node /usr/sbin/
# node -v
```
## 使用淘宝镜npm
镜像使用方法（三种办法任意一种都能解决问题，建议使用第三种，将配置写死，下次用的时候配置还在）:
+ 通过config命令
npm config set registry https://registry.npm.taobao.org
npm info underscore （如果上面配置正确这个命令会有字符串response）
+ 命令行指定
npm --registry https://registry.npm.taobao.org info underscore
+ 编辑 ~/.npmrc 加入下面内容
registry = https://registry.npm.taobao.org
## 安装grunt
    npm install -g grunt-cli
## 使用淘宝镜像的方法
```
alias cnpm="npm --registry=https://registry.npm.taobao.org \
--cache=$HOME/.npm/.cache/cnpm \
--disturl=https://npm.taobao.org/dist \
--userconfig=$HOME/.cnpmrc"
```
or
```
 echo '\n#alias for cnpm\nalias cnpm="npm --registry=https://registry.npm.taobao.org \
  --cache=$HOME/.npm/.cache/cnpm \
  --disturl=https://npm.taobao.org/dist \
  --userconfig=$HOME/.cnpmrc"' >> ~/.zshrc && source ~/.zshrc
```
## google浏览器安装
+ 下载安装包
一、通过直接下载安装Google Chrome浏览器deb包。
打开Ubuntu终端，以下为32位版本，使用下面的命令。
wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb
以下为64位版本，使用下面的命令。

wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

+ 安装
32 位安装命令:
sudo dpkg -i google-chrome-stable_current_i386.deb
64 位安装命令:
sudo dpkg -i google-chrome-stable_current_amd64.deb
+ 错误处理：
sudo apt-get -f install
然后就可以使用了

## 修改host表
+ 修改hosts
sudo gedit /etc/hosts
+ 添加解析记录（ . ）
完整案例：127.0.0.1 localhost.localdomain localhost
简洁记录：127.0.0.1 localhost
+ 保存后重启网络
sudo /etc/init.d/networking restart

## 安装sublime txt3
+ 添加sublime text 3的仓库
sudo add-apt-repository ppa:webupd8team/sublime-text-3
回车，出现很多信息。但是我们看看图片最后字知道，这地方在等待我们确认是否添加这个仓库，按enter键继续，按crtl+c取消。
此时，按ENTER继续，建立信任数据库。
+ 更新软件库
sudo apt-get update
+ 安装Sublime Text 3
sudo apt-get install sublime-text-installer
+ 下面是sublime text 3的安装命令，与3稍有不同：
sudo add-apt-repository ppa:webupd8team/sublime-text-3  
sudo apt-get update  
sudo apt-get install sublime-text-dev
#安装Package Control
使用Ctrl+`快捷键或者通过View->Show Console菜单打开命令行，粘贴如下代码：
        ```
        import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
      ```
## Sublime Text 3 免费使用方法

Sublime Text 2的时候还有一直免费试用的，不过到3 可就木有那么好了。官方报价是70 美刀，恩，有能力的一定要支持正版。没能力的就借助下面的东东免费使用吧！（你懂的，低调、低调）。
+ 将上面要求下载的sublime_text_3.zip(文章后面有下载链接)  文件解压，最终得到两个文件。将注册机（sublime text v2.x.keygen-lz0.exe）放在 Sublime Text 3的安装目录 （sublime_text.exe同级目录）：
Sublime Text 3注册机
+ 打开sublime text v2.x.keygen-lz0.exe，按照图示，点击“Patch Key”，选择“sublime_text.exe”文件并点击“是（yes）”即可。
Sublime Text 3注册机
+ 填写Name信息或者使用默认的，点击“Generate”就注册信息了。复制License信息后，打开sublime_text.exe，help-License信息，粘贴即可。
Sublime Text 3注册成功！
 这个经过测试，可以使用，如下：
第一个--first licence key :

========================================

—– BEGIN LICENSE —–

Michael Barnes

Single User License
EA7E-821385
8A353C41 872A0D5C DF9B2950 AFF6F667
C458EA6D 8EA3C286 98D1D650 131A97AB
AA919AEC EF20E143 B361B1E7 4C8B7F04
B085E65E 2F5F5360 8489D422 FB8FC1AA
93F6323C FD7F7544 3F39C318 D95E6480
FCCC7561 8A4A1741 68FA4223 ADCEDE07
200C25BE DBBC4855 C4CFB774 C5EC138C
0FEC1CEF D9DCECEC D3A5DAD1 01316C36
—— END LICENSE ——
========================================

第二个--second licence key :

========================================
—– BEGIN LICENSE —–
Nicolas Hennion
Single User License
EA7E-866075
8A01AA83 1D668D24 4484AEBC 3B04512C
827B0DE5 69E9B07A A39ACCC0 F95F5410
729D5639 4C37CECB B2522FB3 8D37FDC1
72899363 BBA441AC A5F47F08 6CD3B3FE
CEFB3783 B2E1BA96 71AAF7B4 AFB61B1D
0CC513E7 52FF2333 9F726D2C CDE53B4A
810C0D4F E1F419A3 CDA0832B 8440565A
35BF00F6 4CA9F869 ED10E245 469C233E
—— END LICENSE ——
========================================
第三个--third licence key :
========================================
—– BEGIN LICENSE —–
Anthony Sansone
Single User License
EA7E-878563
28B9A648 42B99D8A F2E3E9E0 16DE076E
E218B3DC F3606379 C33C1526 E8B58964

B2CB3F63 BDF901BE D31424D2 082891B5

F7058694 55FA46D8 EFC11878 0868F093

B17CAFE7 63A78881 86B78E38 0F146238

BAE22DBB D4EC71A1 0EC2E701 C7F9C648

5CF29CA3 1CB14285 19A46991 E9A98676

14FD4777 2D8A0AB6 A444EE0D CA009B54

—— END LICENSE ——

========================================

第四个--fourth licence key :

========================================

—– BEGIN LICENSE —–

Alexey Plutalov

Single User License

EA7E-860776

3DC19CC1 134CDF23 504DC871 2DE5CE55

585DC8A6 253BB0D9 637C87A2 D8D0BA85

AAE574AD BA7D6DA9 2B9773F2 324C5DEF

17830A4E FBCF9D1D 182406E9 F883EA87

E585BBA1 2538C270 E2E857C2 194283CA

7234FF9E D0392F93 1D16E021 F1914917

63909E12 203C0169 3F08FFC8 86D06EA8

73DDAEF0 AC559F30 A6A67947 B60104C6

—— END LICENSE ——

========================================

注意：----- BEGIN LICENSE ----- 和------ END LICENSE ------ 都要复制粘贴进去。
+ submit中文输入法
保存下面的代码到文件sublime_imfix.c(位于~目录)
```
#include <gtk/gtkimcontext.h>
void gtk_im_context_set_client_window (GtkIMContext *context,
         GdkWindow    *window)
{
 GtkIMContextClass *klass;
 g_return_if_fail (GTK_IS_IM_CONTEXT (context));
 klass = GTK_IM_CONTEXT_GET_CLASS (context);
 if (klass->set_client_window)
   klass->set_client_window (context, window);
 g_object_set_data(G_OBJECT(context),"window",window);
 if(!GDK_IS_WINDOW (window))
   return;
 int width = gdk_window_get_width(window);
 int height = gdk_window_get_height(window);
 if(width != 0 && height !=0)
   gtk_im_context_focus_in(context);
}

cd ~

gcc -shared -o libsublime-imfix.so sublime_imfix.c  `pkg-config --libs --cflags gtk+-2.0` -fPIC
```
然后将libsublime-imfix.so拷贝到sublime_text所在文件夹
需要安装gtk+-2.0，命令如下：
sudo apt-get install gtk+-2.0
sudo mv libsublime-imfix.so /opt/sublime_text/
修改文件/usr/bin/subl的内容
sudo gedit /usr/bin/subl
将
```
#!/bin/sh
exec /opt/sublime_text/sublime_text "$@"
```
修改为
```
#!/bin/sh
LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so exec /opt/sublime_text/sublime_text "$@"
```
此时，在命令中执行 subl 将可以使用搜狗for linux的中文输入
为了使用鼠标右键打开文件时能够使用中文输入，还需要修改文件sublime_text.desktop的内容。
命令
sudo gedit /usr/share/applications/sublime-text.desktop
将[Desktop Entry]中的字符串
Exec=/opt/sublime_text/sublime_text %F
修改为
Exec=bash -c "LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so exec /opt/sublime_text/sublime_text %F"
将[Desktop Action Window]中的字符串
Exec=/opt/sublime_text/sublime_text -n
修改为
Exec=bash -c "LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so exec /opt/sublime_text/sublime_text -n"
将[Desktop Action Document]中的字符串
Exec=/opt/sublime_text/sublime_text --command new_file
修改为
Exec=bash -c "LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so exec /opt/sublime_text/sublime_text --command new_file"
注意：
修改时请注意双引号"",否则会导致不能打开带有空格文件名的文件。
此处仅修改了/usr/share/applications/sublime-text.desktop，但可以正常使用了。
opt/sublime_text/目录下的sublime-text.desktop可以修改，也可不修改。
## 中文乱码
+ 安装插件 ConvertToUTF8
## 快速打开文件 添加别名
  使用以下命令在shell终端中以窗口形式打开一个文件夹
  nautilus  dirname
  可以用 alias 命令来给nautilus命令重新起名字，容易记住
  alias opendir='nautilus'
  完成之后就可以用 opendir 命令来进行与 nautilus 命令相同的操作
  opendir dirname
  但是这样操作只能在本次打开的shell终端中有用，下次启动shell终端命令失效，
  可以将命令写入配置文件中
  $ vi ~/.bashrc
  打开配置文件后将 alias opendir='nautilus' 添加到配置文件中，如下图
  #export PATH=$PATH:/opt/usr/local/arm/4.3.2/bin
  alias sm='luit -encoding gbk telnet newsmth.net'
  alias xyj='luit -encoding gbk telnet 220.181.69.180 6666'
  alias openpdf='xdg-open'
  alias opendir='nautilus'
  增加ssh
  alias ssh113='ssh -i /home/zhangshuai/Documents/sshKey/sshKey dev@11.11.164.113'
  这样在下次启动shell时命令还能使用
## zsh中的配置
+ zsh配置主要在用户当前目录的.zshrc文件中

## 添加右键
+ 转到下面的目录
```
~/.local/share/nautilus/scripts/
```
+ 增加文件，内容如下：
```
#!/bin/bash
exec gedit $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
```


## 常用命令
+ 删除文件夹
rm -rf raml_hc

## 安装jdk
+ 删除原有JDK
sudo apt-get purge openjdk*
+ 添加 PPA 源
sudo add-apt-repository ppa:webupd8team/java
+ 更新下源数据库
sudo apt-get update
+ 安装 Oracle Java 7
sudo apt-get install oracle-java7-installer


## 安装eclipse
+ 解压eclipse
cd /opt/ && sudo tar -zxvf ~/下载/eclipse-*.tar.gz
+ 安装
执行eclipse-inst

## 安装mysql5.6
+ 下载MySQL5.6源码包
+ 安装mysql客户端
sudo apt-get install mysql-client-5.6
+ 安装mysql服务端
sudo apt-get install mysql-server-5.6

## 使用命令安装deb
如果ubuntu要安装新软件，已有deb安装包（例如：iptux.deb），但是无法登录到桌面环境。那该怎么安装？答案是：使用dpkg命令。
dpkg命令常用格式如下：
sudo dpkg -I iptux.deb#查看iptux.deb软件包的详细信息，包括软件名称、版本以及大小等（其中-I等价于--info）
sudo dpkg -c iptux.deb#查看iptux.deb软件包中包含的文件结构（其中-c等价于--contents）
sudo dpkg -i iptux.deb#安装iptux.deb软件包（其中-i等价于--install）
sudo dpkg -l iptux#查看iptux软件包的信息（软件名称可通过dpkg -I命令查看，其中-l等价于--list）
sudo dpkg -L iptux#查看iptux软件包安装的所有文件（软件名称可通过dpkg -I命令查看，其中-L等价于--listfiles）
sudo dpkg -s iptux#查看iptux软件包的详细信息（软件名称可通过dpkg -I命令查看，其中-s等价于--status）
sudo dpkg -r iptux#卸载iptux软件包（软件名称可通过dpkg -I命令查看，其中-r等价于--remove）
注：dpkg命令无法自动解决依赖关系。如果安装的deb包存在依赖包，则应避免使用此命令，或者按照依赖关系顺序安装依赖包。

## 卸载virtualbox
sudo apt-get remove virtualbox

## 创建快捷方式
-快捷方式位置 sudo gedit /usr/share/applications/sublime-text.desktop
```
[Desktop Entry]
Encoding=UTF-8
Name=eclipse
Comment=Eclipse IDE
Exec=/home/zhangshuai/eclipse/jee-mars2/eclipse/eclipse
Icon=/home/zhangshuai/eclipse/jee-mars2/eclipse/icon.xpm
Terminal=false
StartupNotify=true
Type=Application
Categories=Application;Development;

```
+ 如果路径中有空格，可以按下面的方式写：
Exec=/home/zhangshuai/MyEclipse/'MyEclipse 10'/myeclipse
也可以按下面的方式写：
Exec='/home/zhangshuai/MyEclipse/MyEclipse 10/myeclipse'

对上面的命令中的几条稍作解释：
Exec代表应用程序的位置【视实际情况修改】
Icon代表应用程序图标的位置【视实际情况修改】
Terminal的值为false表示启动时不启动命令行窗口，值为true表示启动命令行窗口【建议为false】
Categories这里的内容决定创建出的起动器在应用程序菜单中的位置，按照上面的写法创建的起动器将出现在应用程序－Internet中，以此类推，如果想在应用程序－办公中创建起动器，上述最后一行应该写成：Categories=Application;Office;

## 安装jdk8
+ 下载 http://www.oracle.com/technetwork/cn/java/javase/downloads/index.html
+ 解压 tar zvxf jdk-8u20-linux-x64.tar.gz
+ 创建jvm文件
  sudo mkdir /usr/lib/jvm
+ 移动文件
  sudo mv jdk1.8.0_20 /usr/lib/jvm
+ 配置环境变量
  （也有在~/.bashrc修改的，区别是：
    /etc/profile的设置方法对所有登陆用户都有效
    ~/.bashrc只对当前用户有效
    ）
    - sudo vi ~/.profile
    - 添加下面记录
    export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_20
    export JRE_HOME=${JAVA_HOME}/jre
    export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
    export PATH=${JAVA_HOME}/bin:$PATH
+ 使立即生效
  source ~/.profile
# 设置为默认
输入sudo update-alternatives --display java可查看信息默认的jdk信息，刚开始因为没有，提示错误：no alternatives for java
sudo update-alternatives --install /usr/bin/java java  你JDK的路径/java  300(优先级)
sudo update-alternatives --install /usr/bin/javac javac  你JDK的路径/javac  300(优先级)
若有多个版本，需要修改默认的，则输入
sudo update-alternatives --config java
sudo update-alternatives --config javac
将会提示：要维持当前值[*]请安回车键或者输入选择的编号
输入自己设置的优先级的编号(300)，按回车就可以了
再输入display查看，确定默认版本信息
# 查看 linux 进程
2. ps 命令用于查看当前正在运行的进程。
grep 是搜索
例如： ps -ef | grep java
表示查看所有进程里 CMD 是 java 的进程信息
ps -aux | grep java
-aux 显示所有状态
ps
3. kill 命令用于终止进程
例如： kill -9 [PIDnpm install -g sails-generate-eslintrc]
-9 表示强迫进程立即停止
通常用 ps 查看进程 PID ，用 kill 命令终止进程



# atom 安装的插件
linter-eslint
linter-jscs
# 朝晖开发的sails插件
npm install -g sails-generate-eslintrc
当中sails中增加新类时，sails-generate-eslintrc

# 安装rpm文件
rpm -ivh xxx.rpm
# 禁用触摸板
安装pointing device，在软件界面中禁用；

#安装jq工具
sudo apt-get install jq

#sublimt
在Preferences/setting-user中添加下面语句：
{
  "ignored_packages":
  [
    "Vintage"
  ],
  #设置tab为两个空格
  "tab_size": 2,
  #设置tab自动转换为空格
  "translate_tabs_to_spaces": true,
  #显示空格和制表符
  "draw_white_space": "all",
}


#一个好用的meld的比较工具 安装方式
sudo apt-get install meld

# 安装firefox
命令：tar -xvf Firefox-latest.tar.bz2
得到一个Firefox文件夹。然后更改一下用户的执行权限，
命令：cd firefox
sudo chmod 755 *
为了便于管理（当然根据个人的习惯），将此文件夹移到/opt文件夹下面，
命令：sudo mv firefox /opt
此时你若直接运行文件夹中的firefox的话， 弹出的仍然是旧版本的Firefox，所以为了方便使用，还需要更改一下/usr/bin/firefox的指向，先备份该文件，
命令：sudo mv /usr/bin/firefox /usr/bin/firefox-old
然后创建新文件：
命令： sudo ln -s /opt/firefox/firefox /usr/bin/firefox
执行成功后，注销一下，重新登录后，就尽情享用新的4.0版本吧，哈

# 安装docker
  安装Docker使用apt-get命令:
  $ apt-get install docker.io
  启动服务和守护进程
  $ service docker.io status
  $ service docker.io start
## 上面的安装方法有问题，看下面的链接
  http://dockone.io/question/492
## Linux下安装QQ地址
  http://www.ubuntukylin.com/application/show.php?lang=cn&id=279#&slider1=3
