---
title: "Removing suse from dual boot with vista"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by rakesh_d on 2008-04-27
Hi, I had installed opensuse about 6 months ago as a dual boot with vista. After coming to know about ubuntu, I installed the latest hardy heron from vista using the wonderful wubi installer. Everything is working great and hence I would like to wipe out opensuse to save disk space. My friend who helped with the installation of opensuse says that deleting the opensuse partition would disable me from booting to vista also. 

I am new not only to ubuntu but also computers in general, and hence I request you to be a bit considerate in explaining the various jargon.

---

### Post by HunterThomson on 2008-04-27
If I were you I would un-install ubuntu with in window$ with the wubi. Then Pop in the live Ubuntu cd and boot up from it. Click the install icon on the desktop. Then in the installer, when you get to partitioning, I would click the manual partitioner. Delete the Open Suse partition and in then open space partition it like this... each one is a new partion

The partitioner is in MB

100MB Primary partition  Label it /boot  format ext3
20000MB swap partition
15000MB  Logical partition label it /   format ext3
the rest of the space make one Primary partition and label it /home format ext3

You mite want to make a logical partition that is formatted FAT32 to swap files between windows and linux.

You should not have a problem booting window$ scents it will install the grub boot loader but if you do you can install the super grub from a super grub cd you can download form here

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by rakesh_d on 2008-04-27
Thanks for your immediate reply.. I will try out your suggestion immediately after getting hold of the ubuntu cd.

---

