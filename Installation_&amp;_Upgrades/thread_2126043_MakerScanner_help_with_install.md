---
title: "MakerScanner help with install"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by iJonesN on 2013-03-15
I am trying to in stall MakerScanner onUbuntu 12.10 using the terminal following along the instructions andwhen I get to the step to “./configure”  the file I get “Nopackage 'opencv' found” from the terminal. I am completely new tousing a terminal interface of any kind so any help would be a great.


Here is the web site [http://makerbot.wikidot.com/makerscanner-software](http://makerbot.wikidot.com/makerscanner-software)


Here is the complete terminal code lineI get back if that helps


jonesn@jonesn-HP-Pavilion-dv2700-Notebook-PC:~$cd makerscanner-0.3.1/
jonesn@jonesn-HP-Pavilion-dv2700-Notebook-PC:~/makerscanner-0.3.1$./configure
checking for a BSD-compatibleinstall... /usr/bin/install -c
checking whether build environment issane... yes
checking for a thread-safe mkdir -p.../bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)...yes
checking for g++... g++
checking whether the C++ compilerworks... yes
checking for C++ compiler defaultoutput file name... a.out
checking for suffix of executables... 
checking whether we are crosscompiling... no
checking for suffix of object files...o
checking whether we are using the GNUC++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used bymake... GNU
checking dependency style of g++...gcc3
checking for gcc... gcc
checking whether we are using the GNU Ccompiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISOC89... none needed
checking dependency style of gcc...gcc3
checking for pkg-config.../usr/bin/pkg-config
checking pkg-config is at least version0.9.0... yes
checking for OPENCV... configure:error: Package requirements (opencv >= 2.0) were not met:
No package 'opencv' found
Consider adjusting the PKG_CONFIG_PATHenvironment variable if you
installed software in a non-standardprefix.
Alternatively, you may set theenvironment variables OPENCV_CFLAGS
and OPENCV_LIBS to avoid the need tocall pkg-config.
See the pkg-config man page for moredetails.

---

### Post by slickymaster on 2013-03-15
> **iJonesN said:**
> I am trying to in stall MakerScanner onUbuntu 12.10 using the terminal following along the instructions andwhen I get to the step to “./configure”  the file I get “Nopackage 'opencv' found” from the terminal. I am completely new tousing a terminal interface of any kind so any help would be a great.


Here is the web site [http://makerbot.wikidot.com/makerscanner-software](http://makerbot.wikidot.com/makerscanner-software)


Here is the complete terminal code lineI get back if that helps


jonesn@jonesn-HP-Pavilion-dv2700-Notebook-PC:~$cd makerscanner-0.3.1/
jonesn@jonesn-HP-Pavilion-dv2700-Notebook-PC:~/makerscanner-0.3.1$./configure
checking for a BSD-compatibleinstall... /usr/bin/install -c
checking whether build environment issane... yes
checking for a thread-safe mkdir -p.../bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)...yes
checking for g++... g++
checking whether the C++ compilerworks... yes
checking for C++ compiler defaultoutput file name... a.out
checking for suffix of executables... 
checking whether we are crosscompiling... no
checking for suffix of object files...o
checking whether we are using the GNUC++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used bymake... GNU
checking dependency style of g++...gcc3
checking for gcc... gcc
checking whether we are using the GNU Ccompiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISOC89... none needed
checking dependency style of gcc...gcc3
checking for pkg-config.../usr/bin/pkg-config
checking pkg-config is at least version0.9.0... yes
checking for OPENCV... configure:error: Package requirements (opencv >= 2.0) were not met:
[COLOR=#ff0000][SIZE=4]**No package 'opencv' found**[/SIZE][/COLOR]
Consider adjusting the PKG_CONFIG_PATHenvironment variable if you
installed software in a non-standardprefix.
Alternatively, you may set theenvironment variables OPENCV_CFLAGS
and OPENCV_LIBS to avoid the need tocall pkg-config.
See the pkg-config man page for moredetails.

You don't have OpenCV installed on your computer. You need to install the development libraries for OpenCV.

To install it, run the following commands at a terminal windows, one at a time:
```
sudo su
sudo apt-get install build-essential
sudo apt-get install libavformat-dev
sudo apt-get install ffmpeg
sudo apt-get install libcv2.3 libcvaux2.3 libhighgui2.3 python-opencv opencv-doc libcv-dev libcvaux-dev libhighgui-dev
```

---

### Post by slickymaster on 2013-03-15
One other thing, make sure you also have** wxWidgets **libraries on your computer, before trying to install MakerScanner, because it's also one of the dependencies.

Here's a tutorial on how to do it:
[http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu](http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu)

---

### Post by iJonesN on 2013-03-15
thank you thats a big help:)

---

