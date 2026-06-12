---
title: "Oracle Install issue"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by Logical Dream on 2008-08-08
I downloaded " oracle-xe-univ-10.2.0.1-1.0.i386 " and wanted to install it on my ubuntu 8.04 . 

Immediately I had problem with some of libraries .  

> root@ubuntu:/home/idle/Desktop/ORACLE# ls
DBXETutorial  oracle-xe-univ-10.2.0.1-1.0.i386.rpm
root@ubuntu:/home/idle/Desktop/ORACLE# rpm -ivh oracle-xe-univ-10.2.0.1-1.0.i386.rpm
error: Failed dependencies:
	glibc >= 2.3.2 is needed by oracle-xe-univ-10.2.0.1-1.0.i386
	libaio >= 0.3.96 is needed by oracle-xe-univ-10.2.0.1-1.0.i386
	/bin/sh is needed by oracle-xe-univ-10.2.0.1-1.0.i386
root@ubuntu:/home/idle/Desktop/ORACLE# 


In SPM I found this missing libraries and I install them , in any case I log in again but again I had same error . 

Have no idea what to do next . 

I want to have it just in purpose of education , I check some official help.doc but didn't find solution .

Just for reference :

[http://otn.oracle.com](http://otn.oracle.com).

The installation docs are at [http://docs.oracle.com](http://docs.oracle.com)

The technical docs at [http://tahiti.oracle.com](http://tahiti.oracle.com)


Any suggestion  ? 

tnx

Ivan

---

### Post by Logical Dream on 2008-08-11
anyone ? :/

---

### Post by Logical Dream on 2008-08-12
maybe somebody could say " U noob , RPM ! " 
 

cheers

---

