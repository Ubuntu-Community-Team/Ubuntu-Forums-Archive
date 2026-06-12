---
title: "Java not working even after installing Java"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by sunseeker888 on 2010-08-19
HI Guys

Problem with Java after installed

I have done this procedures several times, it worked. I have just wiped windows 7 completely from my desktop, as I have finally managed to get multiheads working after 1 year. Ubuntu 10.04 works like a charm, and it has addressed most of the multiheads issues, although It did take 5 hours to sort out the xorg.conf. but it was worthy.

I installed the 64 bits version on both a laptop, and my PC, because my pc has 12 Gb DDR3, and laptop 8GB

Java is working on the laptop, but it's not working on pc.



I have uploaded 2 short youtude video to show the Problem. As you will see the how, the website shows how it should like on the macbookair, but this ain't happening on the PC. The laptop with Ubuntu is working fine, but I have left it my GF place.


I have tried everything, but do not know how to sort this out or what's the problemw 

here's what I did.

sudo aptitude install sun-java6-jre sun-java6-plugin equiv


badboy@supermax:~$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1)
OpenJDK 64-Bit Server VM (build 16.0-b13, mixed mode)
badboy@supermax:~





It looks like the applet is not starting. I have firewall and Clam av anti-virus



Working on Macbookair, that's how it supposed to work

[http://www.youtube.com/watch?v=nsjpyZ4b1Hw](http://www.youtube.com/watch?v=nsjpyZ4b1Hw)



Not working on Pc

Blank screen 
[http://www.youtube.com/watch?v=nL5q-FI0ShM](http://www.youtube.com/watch?v=nL5q-FI0ShM)

[http://www.youtube.com/watch?v=yMXYoo-D5xU](http://www.youtube.com/watch?v=yMXYoo-D5xU)



Needs some brains here chaps. Thanks in advance.

---

### Post by anieruddha on 2010-08-19
Hi,

I had face similar issue. I am mentioning what I did

1. First remove the installed java
2. download the appropriate jdk from sun/oracle site.
3. Copy that bin file to /opt directory. (I find /opt more manageable)
4. Run the file "./jdkXXXXX.bin" will do. It will extract the jdk in current directory
5. Change the directory Permissions to 755
6. Go to /usr/local directory.
7. Create soft link using "ln -s /opt/jdkXXX jdk"
8. Now create the system variable '$JAVA_HOME' by editing your $HOME/.profile file.
9. Add the $JAVA_HOME/bin to your $PATH.
 Hope this will work for you.

---

### Post by lykeion on 2010-08-19
There's probably hundreds of posts with "java problem" here at the forums. 
To try to solve a java problem one must first define what java is.

It could be:
1) the java browser plugin
2) the programming language java

Clearly OP (original poster) is claiming to have problems with 1) not 2) 
so solving his problem would not involve any downloading and installation of the Java JDK (like post ^^ suggests).

First OP should **make sure JavaScript is enabled** (this could be a reason to the blank web page)
In Firefox > Edit > Preferences > Content > Make sure "Enable JavaScript" is ticked

If that doesn't do it, try to remove the IcedTea java plugin (like OP seems to have installed), 
and install the Sun Java plugin instead (because some web pages with java applets only work with this plugin).

Installing Sun Java Plugin on Ubuntu Lucid involves
* remove IcedTea plugin
* enable the partner repository
* install Sun Java plugin
* restart your browser
* check if it is properly installed

Applications > Accessories > Terminal
```
sudo apt-get remove icedtea6-plugin icedtea-6-jre-cacao
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-plugin sun-java6-fonts
```
Restart your browser
Browse to [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
and check if plugin is properly installed

EDIT:
Just noticed that you've also posted this earlier
[http://ubuntuforums.org/showthread.php?t=1556260](http://ubuntuforums.org/showthread.php?t=1556260)

Please don't create multiple threads on the same subject.

---

### Post by sunseeker888 on 2010-08-19
> **lykeion said:**
> There's probably hundreds of posts with "java problem" here at the forums. 
To try to solve a java problem one must first define what java is.

It could be:
1) the java browser plugin
2) the programming language java

Clearly OP (original poster) is claiming to have problems with 1) not 2) 
so solving his problem would not involve any downloading and installation of the Java JDK (like post ^^ suggests).

First OP should **make sure JavaScript is enabled** (this could be a reason to the blank web page)
In Firefox > Edit > Preferences > Content > Make sure "Enable JavaScript" is ticked

If that doesn't do it, try to remove the IcedTea java plugin (like OP seems to have installed), 
and install the Sun Java plugin instead (because some web pages with java applets only work with this plugin).

Installing Sun Java Plugin on Ubuntu Lucid involves
* remove IcedTea plugin
* enable the partner repository
* install Sun Java plugin
* restart your browser
* check if it is properly installed

Applications > Accessories > Terminal
```
sudo apt-get remove icedtea6-plugin icedtea-6-jre-cacao
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-plugin sun-java6-fonts
```
Restart your browser
Browse to [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
and check if plugin is properly installed

EDIT:
Just noticed that you've also posted this earlier
[http://ubuntuforums.org/showthread.php?t=1556260](http://ubuntuforums.org/showthread.php?t=1556260)

Please don't create multiple threads on the same subject.



Thanks it's working now. Finally saying goodbye to Windows. Sorry about the duplication, I thought I asked on the wrong thread, hence the duplicates. My apologise

---

### Post by sunseeker888 on 2010-08-19
> **anieruddha said:**
> Hi,

I had face similar issue. I am mentioning what I did

1. First remove the installed java
2. download the appropriate jdk from sun/oracle site.
3. Copy that bin file to /opt directory. (I find /opt more manageable)
4. Run the file "./jdkXXXXX.bin" will do. It will extract the jdk in current directory
5. Change the directory Permissions to 755
6. Go to /usr/local directory.
7. Create soft link using "ln -s /opt/jdkXXX jdk"
8. Now create the system variable '$JAVA_HOME' by editing your $HOME/.profile file.
9. Add the $JAVA_HOME/bin to your $PATH.
 Hope this will work for you.




Thank you. I really needed that websites to work. Really appreciate your help. Working now.

---

### Post by ratcheer on 2010-08-19
Please use the Thread tools link to mark your problem as Solved. Thanks.

Tim

---

