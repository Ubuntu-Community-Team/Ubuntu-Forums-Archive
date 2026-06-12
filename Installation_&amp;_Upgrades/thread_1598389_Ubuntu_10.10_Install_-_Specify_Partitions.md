---
title: "Ubuntu 10.10 Install - Specify Partitions"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by thebarisaxkid on 2010-10-16
I am upgrading from 10.04 to 10.10 and I need help with specifying the partitions.

I chose the advanced option because I will be dual booting Windows Vista with 10.10.  

I deleted my old 10.04 partition (which included the main partition as well as the swap partition.  So now I have the dell utility partition as well as the Vista partition and a bunch of free space.

I want select the free space patition and click install but an error says no root file system is defined.  

What do I have to do?  Do I have to create a new 'swap' partition? Do I have to format the partition? If so, what format should I use?

---

### Post by lemming465 on 2010-10-17
Your scenario is more properly described as a reinstall than an upgrade; an upgrade would be if you had kept the 10.04 filesystem, booted it, and run an upgrade in place (e.g. sudo update-manager -c).

From where you are now, what you should do is pick the "manual" disk partitioning option, create an extended partition covering the disk free space if you don't have one yet, and then put root and swap logical partitions inside it.  Format root as ext4, usage /, swap as swap.

---

### Post by thebarisaxkid on 2010-10-18
k thanks

---

### Post by thebarisaxkid on 2010-10-18
k thanks

---

