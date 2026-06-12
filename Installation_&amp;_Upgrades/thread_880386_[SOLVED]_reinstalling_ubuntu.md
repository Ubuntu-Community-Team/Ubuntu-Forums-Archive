---
title: "[SOLVED] reinstalling ubuntu"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2008-08-04
I have a hard disk with three partitions. two of them are for windows. Is it possible to install ubuntu on the third partition without resizing anything? Furthermore I have the ALTERNATE INSTALLATION version. Is it possible to install ubuntu on a specified partition with this version of the installation CD?

---

### Post by dileepm on 2008-08-05
You may install ubuntu on your third partition but check the minimum hard disk/partition space requred in the requirements section of Ubuntu before you proceed.

---

### Post by coffeecat on 2008-08-05
Don't forget that the third partition will have to be reformatted into two partitions - one for / and one for swap. Depending on what you've got already, this might give you four primary partitions which will give you no flexibility in the future - you are limited to four primary partitions. Bearing in mind dileepm's comment about minimum space requirements, it might be a good idea to reformat the third partition as an extended partition and then create logical swap and ext3 partitions within that for Ubuntu. Don't forget that Linux can boot up from a logical partition.

It is a long time since I've used the alternative CD, but I'm fairly sure you can choose and create your own partitioning setup like this in it. If not, you could download the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php"), prepare your partitions with it, and then install from the alternate CD.

---

