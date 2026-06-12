---
title: "How do I get Java??"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by Exoskull969 on 2010-06-12
How do I get Java on Ubuntu 10.04 64 bit?

Note that I am also using chromium (:

All I want it for is to play a game called Minecraft.

Plz help!

---

### Post by Zireth ZH on 2010-06-12
you can get it on their site.. they got a linux version

---

### Post by pastalavista on 2010-06-12
Well...[here's what I found upon doing your Googling for you, no charge]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins");)

---

### Post by Exoskull969 on 2010-06-13
Im a linux newb can I have a step by step tutorial cuz im sooooo confused

---

### Post by 5BallJuggler on 2010-06-13
> **Exoskull969 said:**
> Im a linux newb can I have a step by step tutorial cuz im sooooo confused

Open the Package manager

System->Administation->Synaptic Package Manager

Type in sun-java6-jre into the search box

Click on "Apply".

Then "OK" or "Install" (Can't remember sorry) on the window that opens.

That's it done.

---

### Post by howefield on 2010-06-13
> **5BallJuggler said:**
> <*snippety snip*>.

This won't work in 10.04, where you would need to enable the partner repository first. And you might also want sun-java6-plugin.

---

### Post by 5BallJuggler on 2010-06-13
> **howefield said:**
> This won't work in 10.04, where you would need to enable the partner repository first. And you might also want sun-java6-plugin.

It's working for me in 10.04, these are the files I have

sun-java6-jre.
sun-java6-bin.
sun-java6-fonts.
sun-java6-plugin.

---

### Post by howefield on 2010-06-13
> **5BallJuggler said:**
> It's working for me in 10.04, these are the files I have.

Perhaps you upgraded to 10.04 with java already installed or you activated the partner repository, the Sun packages moved to partner with Lucid.

```
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun) Java moved to the Partner repository
```

---

### Post by ankit singh on 2010-06-13
I think even after installing sun java ,openjdk will be used as default.
run this after installing sun java
```
sudo update-java-alternatives -s java-6-sun 			 		
```

---

### Post by AgentXSmith on 2010-06-21
I just tried to use WebEx and it says I don't have Java installed but I checked my synaptic package manager and it shows it as being there.  Is there something I need to do to "activate" it?

---

### Post by ankit singh on 2010-06-22
Type these codes in terminal
```
sudo apt-get install libstdc++5
```this solves this bug
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6542512](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6542512)


and type 
```
sudo update-java-alternatives -s java-6-sun
```this code will replace openjdk to sun java

and test ur java at

[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

---

### Post by ankit singh on 2010-06-22
[http://forumubuntusoftware.info/viewtopic.php?f=68&t=4847&p=52604#p52604](http://forumubuntusoftware.info/viewtopic.php?f=68&t=4847&p=52604#p52604)

This will help you in installing java:guitar:

---

### Post by bachor on 2011-02-21
can't get Java to work in Firefox 3.6.13 Kubuntu 10.04 on LXDE desktop with Apparmor Firefox profile from Bodhi [t_hank YOU so much_]

I've had Java 1.6.0_20 version and did :

> sudo apt-get upgradeand now **NO Java version** in Java link:  [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

it goes on next page without finding what version is installed:  [http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)

 but about: plugins in Firefox:

> **Java(TM) Plug-in 1.6.0_24**

or:

> baachor@linuz:~$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) Client VM (build 19.1-b02, mixed mode, sharing)> baachor@linuz:~$ sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice
[*], or type selection number: 
 what is going on? do I have to uninstall OpenJDK like : [http://forumubuntusoftware.info/viewtopic.php?f=68&t=4847&p=52604#p52604](http://forumubuntusoftware.info/viewtopic.php?f=68&t=4847&p=52604#p52604)

 any idea ?

 thank You .)

---

### Post by ankit singh on 2011-02-22
> Press enter to keep the current choice
[*], or type selection number:                       Just type 2 at the prompt and then enter :)

or open the terminal and type this (this is direct) 
sudo update-java-alternatives -s java-6-sun

---

### Post by bachor on 2011-02-22
> **ankit singh said:**
> Just type 2 at the prompt and then enter :)

or open the terminal and type this (this is direct) 
sudo update-java-alternatives -s java-6-sun


 yes I hit Enter [to leave option 2] or tried 2 and Enter, and either way I got this error:

```
baachor@linuz:~$ sudo update-java-alternatives -s java-6-sun
update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for HtmlConverter.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
update-alternatives: error: no alternatives for javac.
update-alternatives: error: no alternatives for javadoc.
update-alternatives: error: no alternatives for javah.
update-alternatives: error: no alternatives for javap.
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for jconsole.
update-alternatives: error: no alternatives for jdb.
update-alternatives: error: no alternatives for jhat.
update-alternatives: error: no alternatives for jinfo.
update-alternatives: error: no alternatives for jmap.
update-alternatives: error: no alternatives for jps.
update-alternatives: error: no alternatives for jrunscript.
update-alternatives: error: no alternatives for jsadebugd.
update-alternatives: error: no alternatives for jstack.
update-alternatives: error: no alternatives for jstat.
update-alternatives: error: no alternatives for jstatd.
update-alternatives: error: no alternatives for native2ascii.
update-alternatives: error: no alternatives for rmic.
update-alternatives: error: no alternatives for schemagen.
update-alternatives: error: no alternatives for serialver.
update-alternatives: error: no alternatives for wsgen.
update-alternatives: error: no alternatives for wsimport.
update-alternatives: error: no alternatives for xjc.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
```

---

### Post by bachor on 2011-02-22
I want to start selling pix on Dreamstime and they only use Java for upload. yack

---

### Post by bachor on 2011-02-22
ooopps, I'm sorry but it is Firefox Apparmor profile. I just set it to "complain" ad it works. Should have thought about that earlier. Gotta have to figure out where is the problem thou.

---

