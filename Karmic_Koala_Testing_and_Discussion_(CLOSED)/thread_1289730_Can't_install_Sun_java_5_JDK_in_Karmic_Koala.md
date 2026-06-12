---
title: "Can't install Sun java 5 JDK in Karmic Koala"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by raptor_mig on 2009-10-12
I can't install sun-java5-jdk package in the latest Karmic Koala beta release. It gives me the next message.

$ sudo apt-get install sun-java5-jdk 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java5-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-jdk has no installation candidate


I really need the Java 5 version of the JDK for development and testing, and like me there should be a lot of users.

---

### Post by steveolyo on 2009-10-21
Get java5 from the Jaunty repository. 

Java5 should be put back in the Karmic repository. I too have a project that only works on Java5 and apparently I'm not alone.

I did see this tidbit:
[http://osdir.com/ml/ubuntu-archive/2009-09/msg00004.html]("http://osdir.com/ml/ubuntu-archive/2009-09/msg00004.html")

So to get the repo for java5 add these lines to your  /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

Steveolyo

---

### Post by steeleyuk on 2009-10-21
Can you not use Java 6?

Support can't be maintained forever on a particular version... security issues, bugs and all.

---

### Post by LittleKoy on 2009-10-22
> **steeleyuk said:**
> Can you not use Java 6?

Support can't be maintained forever on a particular version... security issues, bugs and all.

Unfortunately no. If Java 5 JDK is not there, Karmic will be taboo for many Java developers (like me).

---

### Post by raptor_mig on 2009-10-25
> **steeleyuk said:**
> Can you not use Java 6?

Support can't be maintained forever on a particular version... security issues, bugs and all.

Unfortunately I can't work with Java 6. I have develop and test all my work in Java 5.
If I can't have Java5 in Karmic I won't upgrade to it, as I'm sure many Java developers won't.

---

### Post by rickh57 on 2009-10-26
I just went to java.sun.com and downloaded [JDK 1.5.0_21]("http://java.sun.com/javase/downloads/5u21/jdk") for linux. I then installed that under Karmic (into my home folder). By pointing JAVA_HOME at the install directory, Java 5 works fine for me in compiling and executing my application, along with ant, junit, etc.

---

### Post by froggyswamp on 2009-10-26
As rickh57 said, get it from java.sun.com, I have a backup copy just in case they require subscription for such old stuff. Anyway Java 5 is already the IE6 of browsers, people should really drop it dead, Apple also upgraded long ago to Java 6.
Imho Java EE 5 can and should be used with Java (JRE) 6
Also Java 5 had lots of rendering issues as well as printing issues unresolved (on Ubuntu and Linux in general).

---

### Post by pferraro on 2009-10-26
JDK 5 will no longer be supported by Sun by the time Karmic is released. See [http://java.sun.com/javase/downloads/index_jdk5.jsp](http://java.sun.com/javase/downloads/index_jdk5.jsp)
> J2SE 5.0 is in its Java Technology End of Life (EOL) transition period. The EOL transition period began April 8th, 2008 and will complete October 30th, 2009, when J2SE 5.0 will have reached its End of Service Life (EOSL). Customers interested in learning more about Sun's Java Technology Support and EOL policy. »Read More
Customers interested in continuing to receive critical fixes, are encouraged to consider the following options:

    * Migrate to the latest Java SE release »Read More
    * Migrate to Java SE for Business 5.0 »Read More

---

