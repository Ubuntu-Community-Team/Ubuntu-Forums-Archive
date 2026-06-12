---
title: "java and phpmyadmin will not install using apt-get"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by scantoria on 2007-08-09
The server is a Ubuntu 6.06 LAMP
when I use the apt-get to install phpmyadmin and java I get the response listed below. Am I doing something wrong? What is this synaptic package manager and how do I use it.

I have removed the comments for the universe and multiverse in the sources.list and still did not work.

// phpmyphp install
scantoria@HEOPS-L-S01:/etc/apt$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-jdk
scantoria@HEOPS-L-S01:/etc/apt

// java install
scantoria@HEOPS-L-S01:/etc/apt$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-jdk
scantoria@HEOPS-L-S01:/etc/apt

Please help...

Steve

---

### Post by ruibernardo on 2007-08-09
> **scantoria said:**
> 
// phpmyphp install
scantoria@HEOPS-L-S01:/etc/apt$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-jdk
scantoria@HEOPS-L-S01:/etc/apt

Hi scantoria, 

it's hard to install a phpmyphp package with that command :)

> **scantoria said:**
> 
// java install
scantoria@HEOPS-L-S01:/etc/apt$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-jdk
scantoria@HEOPS-L-S01:/etc/apt



To install Java in Dapper, check this: [https://help.ubuntu.com/community/Java#head-8b8bf24df0b607c184a5dbfec1501ec8158e03f3](https://help.ubuntu.com/community/Java#head-8b8bf24df0b607c184a5dbfec1501ec8158e03f3)

---

