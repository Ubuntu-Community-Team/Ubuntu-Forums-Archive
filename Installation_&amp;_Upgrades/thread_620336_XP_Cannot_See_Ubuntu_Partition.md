---
title: "XP Cannot See Ubuntu Partition?"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by A4orce84 on 2007-11-22
Hey Everyone,

So I just got done installing Ubuntu and am wondering why XP cannot see Ubuntu. Here is my setup:


c: ---> Physical 160 gig drive that holds Windows XP
d: -->  Physical 100 gig that I just loaded Ubuntu on

Before XP was able to see both the C: and D: Drives....now XP is only seeing the C: after Ubuntu installed and partitioned itself on to D: Drive.


Does Ubuntu use some crazy file system that XP cannot detect, and is there a way to force XP to see it? 

Thanks in advance everyone! =)

--Asif

---

### Post by scrooge_74 on 2007-11-22
XP can't see a ext3 format drive, but Ubuntu can read and write ntfs partitions.  

To be able to see the linux drive from xP you need to install:

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

