---
title: "[SOLVED] Java Circular Dependencies"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by ApologetixFan on 2008-05-17
Hey y'all! What a great operating system, Ubuntu, eh?

I am trying to install java on my system. Every time I try to install a package, it shows a dependency on another package which won't install because of a dependency on another package, which won't install because of a dependency on the first package. What gives? How can i get this installed if I can't install because of another package which won't install because of the first package? KWIM?

Thanks a bunch.

---

### Post by mahuyar on 2008-05-18
Be more descriptive.  Which java package are you trying to install?  Are you trying to install through Symnaptic?  Make sure you have multiverse repository checked as well.

---

### Post by ApologetixFan on 2008-05-18
> **mahuyar said:**
> Be more descriptive.  Which java package are you trying to install?  Are you trying to install through Symnaptic?  Make sure you have multiverse repository checked as well.

Thanks for your response. I am trying to install the openjdk packages. Tho, I would install sun's java if I could find where to download it. I am trying to get NetZero installed, so I don't have a connection to the internet yet. Whether I double-click to use the GUI or use dpkg, it keeps telling me about the dependency failures.

---

### Post by mahuyar on 2008-05-18
> **ApologetixFan said:**
> Thanks for your response. I am trying to install the openjdk packages. Tho, I would install sun's java if I could find where to download it. I am trying to get NetZero installed, so I don't have a connection to the internet yet. Whether I double-click to use the GUI or use dpkg, it keeps telling me about the dependency failures.

Sun's java package name is sun-java6-jdk.  It's in the multiverse repository.  But without a live connection, I'm not sure what we can do atm.

---

### Post by ApologetixFan on 2008-05-20
This seems silly. Another "circular reference". I need to be connected to the internet to get the packages that allow me to connect to the internet in the first place. But I cannot get the packages because I am not connected to the internet. So I need to connect to the internet to get the packages that allow me to connect to the internet. :confused:

Can't somebody help me? :(

---

### Post by kami_iwinaru on 2008-05-20
try sudo apt-get install ubuntu-restricted-extras in the terminal

im not sure if you need to be connected to the internet or not, but it should work if you dont

---

### Post by mahuyar on 2008-05-20
> **ApologetixFan said:**
> This seems silly. Another "circular reference". I need to be connected to the internet to get the packages that allow me to connect to the internet in the first place. But I cannot get the packages because I am not connected to the internet. So I need to connect to the internet to get the packages that allow me to connect to the internet. :confused:

Can't somebody help me? :(

Are you saying you need those java packages to get connected to the net?  I'm assuming that you need java to install Netzero package, which will eventually get you netborne.
The best bet I could come up right now is that you go to a computer with a live connection and download the Java JRE from [www.java.com](www.java.com).

---

### Post by dstew on 2008-05-20
To install with all the dependencies, but with no internet, use [nonetdebs]("http://nonetdebs.unixpod.com/").

---

### Post by BigRedButton on 2011-12-29
I am also having an issue installing the openjdk packages. I installed the Sun Java packages just fine so it's not a huge deal, but I am having the same circular dependency issues with installing the package openjdk6-jre. It depends on openjdk6-jre-headless, which depends on openjdk6-jre-lib, unfortunately openjdk6-jre-lib also depends on openjdk6-jre-headless, so neither will install.

---

