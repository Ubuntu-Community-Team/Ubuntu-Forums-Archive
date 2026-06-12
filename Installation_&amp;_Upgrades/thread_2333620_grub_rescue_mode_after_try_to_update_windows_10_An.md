---
title: "grub rescue mode after try to update windows 10 Anniversary"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by alladdin on 2016-08-11
Hello

I try today to update windows 10 and when my laptop restart i cannot select what OS i want to choose
I try boot-repair-disk and it failed to repair my problem 
Here is the link, i hope someone can help me.
[http://paste.ubuntu.com/23037796/](http://paste.ubuntu.com/23037796/)

---

### Post by yancek on 2016-08-11
It appears that your windows update has re-written the partition table and not included the Ubuntu partition.  Look at the start and end point for sda4 and sda4 below:

> /dev/sda4       185556990   234440703    24441857    5  Extended
/dev/sda5       226291712   234440703     4074496   82  Linux swap / Solaris

Your Ubuntu would be between the start of sda4 and the start of sda5, the swap partition.  That should be about 30GB.  You should be able to use testdisk to repair the partition table.  Available for download at their site below.  Before beginning, read the Step By Step tutorial which is at a link on this same page.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

