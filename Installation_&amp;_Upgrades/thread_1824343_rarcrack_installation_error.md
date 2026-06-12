---
title: "rarcrack installation error"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by papaapa on 2011-08-13
Hello!

I get this error when i command "make" on rarcrack which i downloaded from official site.

gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
/bin/sh: xml2-config: not found
In file included from rarcrack.c:21:0:
rarcrack.h:25:48: fatal error: libxml/xmlmemory.h: No such file or directory
compilation terminated.
make: *** [all] Error 1

Can someone help me please ?

Thank you!

---

### Post by raja.genupula on 2011-08-13
hey go with this 

[http://ubuntuforums.org/showthread.php?t=1341782](http://ubuntuforums.org/showthread.php?t=1341782)

---

### Post by papaapa on 2011-08-14
sudo apt-get install libxml2
[sudo] password for dalya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxml2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dalya@dalya:~$ sudo apt-get install libxml2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libxml2-dev

---

### Post by dino99 on 2011-08-14
which distro is used ?
libxml2-dev is in repo

sudo apt-get xml-core

---

### Post by papaapa on 2011-08-14
> **dino99 said:**
> which distro is used ?
libxml2-dev is in repo

sudo apt-get xml-core

I use Ubuntu 11.04. I did not change anything from repos or something.

sudo apt-get xml-core
E: Invalid operation xml-core

sudo apt-get install xml-core
[sudo] password for dalya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xml-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by papaapa on 2011-08-15
Any ideas ? :(

---

### Post by b1kkur1 on 2012-03-26
sudo apt-get install libxml2-dev libxslt-dev

---

