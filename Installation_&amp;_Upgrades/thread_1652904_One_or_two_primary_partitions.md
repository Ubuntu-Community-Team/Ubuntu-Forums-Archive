---
title: "One or two primary partitions?"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by rumboogy on 2010-12-25
I am somewhat new to Linux and am trying to install Ubuntu into a single primary partition (and multiple logical partitions).  I did this before with PC Linux OS but can't seem to get it to work with Ubuntu.  I do the install and all looks good but then when I try to boot using BootIt NG it says the partition is not bootable.  

I was able to boot into Ubuntu when I installed it in two primary partitions (one for swap and the other for everything else).

Any thoughts?

---

### Post by zvacet on 2010-12-27
Why don´t you try to install Ubuntu and partition it with it own partition tool.You should be able (in fact you mst be able) to install Ubuntu on one partition.If you don´t want to have swap use manual way for partitioning.

---

### Post by dino99 on 2010-12-27
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by rumboogy on 2011-01-18
> **zvacet said:**
> Why don´t you try to install Ubuntu and partition it with it own partition tool.You should be able (in fact you mst be able) to install Ubuntu on one partition.If you don´t want to have swap use manual way for partitioning.


You are right.  I fixed the problem by creating the partitions from within the Ubuntu installer rather than outside.  I started off by opening a location on the disk where I wanted Ubuntu to reside.  Then during the install process I selected that location and created the swap and root partitions as logical partitions.  All was well from there on.

Thanks.

---

### Post by rumboogy on 2011-01-31
[SOLVED] 

OK, I was wrong.  It was not really solved in the last post but now it is.   The answer is that you have to keep the partitions in the MBR's partition table in the same order during and after the install.  The partition names in Linux (sda1, sda2, etc.) imply their order in the MBR.  If you change the order then after the install it won't work anymore.  Now that I understand this I can reliably install Linux in a single partition.

---

