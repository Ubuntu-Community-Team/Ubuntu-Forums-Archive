---
title: "ps eye installation on ubuntu 9.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by sonyofjapan on 2011-05-01
i have a playstation eye i want to install on my ubuntu so i can chat with it on google. look everywhere but it doesnt work becuase someone doesnt put in the right commend on the website or the website doesnt exist to install. 
i found this one site ([http://kaswy.free.fr/?q=en/node/53](http://kaswy.free.fr/?q=en/node/53)) and i type in this commend after downloading:

root@donations-laptop:/usr/src# patch -p1 < ps3eyeMT-2.6.31-10-generic.patch

but show up:

can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Naur linux-source-2.6.31/drivers/media/video/gspca/ov534.c linux-ps3eyeMT/drivers/media/video/gspca/ov534.c
|--- linux-source-2.6.31/drivers/media/video/gspca/ov534.c    2009-09-10 00:13:59.000000000 +0200
|+++ linux-ps3eyeMT/drivers/media/video/gspca/ov534.c    2009-09-21 19:10:40.000000000 +0200
--------------------------
File to patch:

then i stop there
so how would i fix this up
thanks

---

### Post by mörgæs on 2011-05-01
9.04 has been out of support for the latest half year. It is a security threat to use it.

Best is to begin with a clean install of one of the supported versions:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

