---
title: "How to install PHP Eclipse in Ubuntu 7.04 Feisty Fawn"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by anand kirtan on 2007-09-04
Hi All,

I am noob here and totally noob for unix/linux. I am glad to find a excellent OS for my PC.

I am posting this for the noobs who will come across the same problem that i came.

1. Install Eclipse using Applications => Add/Remove

2.  Download PHP Eclipse from Source Forge.

3. Unzip and copy and paste it in plugin and features directory as usually.

When you run and try to edit PHP file, you will get an error message that tells you to look in the log.

I came across this [http://www.plog4u.org/index.php/Using_PHPEclipse_:_Installation_:_Installing_PHPEclipse](http://www.plog4u.org/index.php/Using_PHPEclipse_:_Installation_:_Installing_PHPEclipse) and follow the instructions.

A blue scrine titled "Configuring sun-java6-bin" shows, to accept it press tab and hit enter.
and press tab and highlight "Yes" hit enter.

Now PHP Eclipse runs smoothly.

If you were closed that blue screen before accepting it, try using

dpkg --configure -a

and then use again 
1. sudo apt-get install sun-java6-jre
2.  sudo nano -w /etc/eclipse/java_home
3.  Insert /usr/lib/jvm/java-6-sun on the line above /usr/lib/jvm/java-gcj
4. Close and save the file 

Many thanks for this awesome OS

Cheers,
Anand Kirtan

---

### Post by vrix on 2007-09-17
another alternative:

1. download PHP Development Tools (PDT) from eclipse website. [PDT All-in-One]("http://download.eclipse.org/tools/pdt/downloads/?release=S20070910-RC1") using Linux Link.

2. extract.

3. download the debugger from Zend: [http://www.zend.com/pdt/]("http://www.zend.com/pdt/") Choose Download Zend Executable Debugger Eclipse Plugin.

4. extract and copy to eclipse plugin and features folder.

5. click Eclipse executable. 

6. Enjoy! :)

---

