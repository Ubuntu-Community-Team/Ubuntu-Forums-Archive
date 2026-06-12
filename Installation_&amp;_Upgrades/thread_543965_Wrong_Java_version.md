---
title: "Wrong Java version"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by nexula on 2007-09-05
I have just installed sun-java6-xx using **apt-get install** and everything seemed to go fine, except when I write **java -version** then I get **java version "1.4.2"**.
Can anyone tell me why the version is still 1.4.2 and how I can fix it so that it points to the new java version I have just installed.
Thanx..

---

### Post by wolfen69 on 2007-09-05
you have the correct version of java. it will always come up as 1.4.2 or like mine, 1.6.0  but i do not know why it does this. java seems to work well for me, so i don't worry about it.

---

### Post by Pumalite on 2007-09-05
Have you tried: sudo aptitude show sun-java6-xx, and see what it shows?

---

### Post by merlin666 on 2007-09-05
Apparently many java apps will not understand java 6 anyway and will force you to go back to java 1.5. It's also available for amd64 at

[http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0_07-oth-JPR&SiteId=JSC&TransactionId=noreg](http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0_07-oth-JPR&SiteId=JSC&TransactionId=noreg)

---

### Post by nexula on 2007-09-06
> **Pumalite said:**
> Have you tried: sudo aptitude show sun-java6-xx, and see what it shows?

I tried this and the output was as follows:
Package: sun-java6-jdk
State: installed
Automatically installed: no
Version: 6-00-2ubuntu2
Priority: optional
Section: multiverse/devel
Maintainer: Matthias Klose <doko@ubuntu.com>
Uncompressed Size: 32.0M
Depends: sun-java6-jre (= 6-00-2ubuntu2), libc6, libx11-6
PreDepends: debconf (>= 0.5) | debconf-2.0
Suggests: sun-java6-demo, sun-java6-doc, sun-java6-source
Provides: java-compiler, java2-compiler
Description: Sun Java(TM) Development Kit (JDK) 6
 The JDK(TM) is a development environment for building applications, applets, and components using the Java
 programming language. 
 
 The JDK includes tools useful for developing and testing programs written in the Java programming language and
 running on the Java Platform. 
 
 NOTE: You must accept Sun's EULA prior to successfully installing this package


I know it works fine cause when I go to the directory where it is installed I am able to compile
 and run java applications, but I think it should have updated the "pointer" (java + javac) files 
enabling me to compile and run java applications from anywhere in my file structure.
G

---

### Post by Pumalite on 2007-09-06
Well, we know now that is installed and installed right. It might be a question of path. Investigate that.

---

### Post by Dogmeat Jack on 2007-09-07
Found the answer:
[http://forum.java.sun.com/thread.jspa?threadID=5191319&messageID=9756412]("http://forum.java.sun.com/thread.jspa?threadID=5191319&messageID=9756412")
basicly run :
```
sudo update-alternatives --config java
```
and select your preferred Java versio

---

### Post by Pumalite on 2007-09-07
Good for you! And thank you for posting the answer to the problem.

---

### Post by leifjonny on 2007-09-08
thanx

---

### Post by nexula on 2007-09-10
> **Dogmeat Jack said:**
> Found the answer:
[http://forum.java.sun.com/thread.jspa?threadID=5191319&messageID=9756412]("http://forum.java.sun.com/thread.jspa?threadID=5191319&messageID=9756412")
basicly run :
```
sudo update-alternatives --config java
```
and select your preferred Java versio


I tried your solution and it was just what I was looking for. 
Thank you for your excellent answer!!!!   :)

---

### Post by Splinterhood on 2007-09-17
I Checked my Version Here:
[http://www.javatester.org/version.html](http://www.javatester.org/version.html)
and here:
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) (Where it told me I was not up to date; I installed from the Feisty Synaptic)

---

