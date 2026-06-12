---
title: "Remove java 1.6 and enable 1.5"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by elaintarha on 2008-09-13
Hi there,

I have ubuntu 8.04 installed and 2 versions of Java. I need to remove / disable this one:

 java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

and enable this:
/Documents/JAVA/jre1.5.0_14/bin$ ./java -version
java version "1.5.0_14"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_14-b03)
Java HotSpot(TM) Server VM (build 1.5.0_14-b03, mixed mode)

So that my Firefox uses the older one. Please help me, how?

Timo

I found the solution, used synaptics and selected "all open source" and searched "jre", then removed version 6. (although the version is 1.6?, wtf)

---

