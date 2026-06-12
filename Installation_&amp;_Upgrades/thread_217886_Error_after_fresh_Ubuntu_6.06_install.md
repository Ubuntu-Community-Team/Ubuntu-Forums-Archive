---
title: "Error after fresh Ubuntu 6.06 install"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by xordae on 2006-07-17
A standard install.. the MD5 checksum was okay, the only thing custom was that I picked XFS as my file system. 
I got this error at the end of the installation process, at about 96%. Sorry for the bad image quality. 
You can make out python and gtkui in the text.

[http://img3.freeimagehosting.net/image.php?1da7c08625.jpg](http://img3.freeimagehosting.net/image.php?1da7c08625.jpg)

Any help is appreciated, I really am pretty much a linux newbie.

---

### Post by stuh505 on 2006-07-17
When I chose ntfs as my file system, the installer also crashed but it didn't  even give me an error message like it did for you.  It also corrupted my windows partition...if you have one, you might want to check it..

---

### Post by xordae on 2006-07-17
I installed Ubuntu over my old Dapper flight on hdb1. Windoze has always been NTFS and hda1, so I figure it left it alone. Although it ripped my Grub in the process, and I just about got my master boot record restored to run Win. Do you think it might be a problem with the file system that I chose? It looks more like a gtk ui thing.

---

### Post by xordae on 2006-07-18
Okay, the guys at Launchpad had several of these bug reports! It seems the solution is to let the partitioner work in auto mode, no selecting of custom file systems and that jazz, sadly. Seems ext3 would be the only option there. I'll try it out later again.

---

### Post by deanjm1963 on 2006-07-18
> **stuh505 said:**
> When I chose ntfs as my file system, the installer also crashed but it didn't  even give me an error message like it did for you.  It also corrupted my windows partition...if you have one, you might want to check it..

You can't install linux on NTFS

---

