---
title: "Install Java Runtime"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by nguyencongdieu on 2008-07-24
Hi, 
Could you please help me to fix this error:
I am installing Java than I have to perform "dpkg --configure -a" 
After running dpkg --configure -a I encountered: synaptic: no process killed
dieunc@hanhchinh-01-desktop:~$ apt-get install libc6

You can see:
dieunc@hanhchinh-01-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
dieunc@hanhchinh-01-desktop:~$ sudo dpkg --configure -a
[sudo] password for dieunc: 
Setting up java-common (0.28ubuntu3) ...

Setting up hal (0.5.11~rc2-1ubuntu8.2) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Hardware abstraction layer hald                                     /usr/sbin/hald already running.
                                                                         [ OK ]

Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Please help me!

---

### Post by appier on 2008-07-25
I am pretty new at Ubuntu.  However, I have installed java on a couple of machines in my classroom because I needed it in order to get through the Watchguard Authentication Applet to get access to the internet.  If someone with more experience would like to elaborate and correct me--please do.

First, have you tried to install it the "easy way" using Applications --> Add/Remove, then select Java Runtime Environment...?

Second, if that doesn't work, try installing it using the instructions given on the java website at [http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80) for the "Linux (self-extracting file)" carefully following the instructions at [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting) .

The key to success with the manual install is finding where your profile folder for Firefox is located and creating a symbolic link back to your java installation location.

---

### Post by stealth17 on 2008-07-25
How do I add the java path as an environment variable? Here is the message I get when I try to run mvpod on Hardy

> 
ERROR!
Java executable not found in /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
Please add java to your PATH environment variable, or specify it in file /home/stealth17/mvpod/mvpod.properties

---

### Post by stchman on 2008-07-25
To install Java use the following:

32 bit (use SUN Java)
```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

64 bit (use Icedtea openJDK)
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

---

