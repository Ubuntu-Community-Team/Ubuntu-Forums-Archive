---
title: "Zero disk space"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by grockle on 2010-05-03
Trying to install 10.04, installer reports zero disk space.

I have;

150gigs windows partition

100gigs unused partition.

What do i have to do to get the installer to find the unused disk space ?.

cheers
grockle

---

### Post by zvacet on 2010-05-04
During install delete unused partition and on free space make Ubuntu partition.It is good to make separate home,because that way your settings&files will be safe if you decide in future to reinstall,make fresh install...So,on that unallocated space make root partition mountpoint / and format it as ext4.Give it ~10GB.Except few GB for swap you can give rest of free space to home mountpoint /home ext4.

---

