---
title: "how can i add more space to sda2 from free space"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by jcer93705 on 2010-07-22
hey guys i made space by shrinking my window partition and so i have unallocated and would like to add to sda2 to have more space. Check out this pic. How can i do this?

---

### Post by oldfred on 2010-07-23
You end up having to move a lot of partitions around with increasing risk as you move more data.

I would suggest just making it sda3 and move /home into it or make it just a data partition for all your data (but not hidden system settings) that is in /home.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Your data partition could be linux only or NTFS to share with windows:
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

---

