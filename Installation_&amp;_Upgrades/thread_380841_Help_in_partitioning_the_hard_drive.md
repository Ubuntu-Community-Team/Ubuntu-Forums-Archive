---
title: "Help in partitioning the hard drive"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by Raein on 2007-03-10
Hello,

i am confuse in partitioning a hard drive, I have a sata disk in which kubuntu edgy are installed and PATA disk where windows xp reside.

Since i search i found out this site [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and it's very useful.

Now i wanna do is to partition the sata drive and create a fat32 and leave the PATA as is. So i am having a problem where do i place the Fat 32 

1. before the ext3 and swap partition (will it affect the grub loader?)
2. after ext3 and before the swap partition
3. after ext3 and swap partition

So, that's it. i hope to get a reply soon thanks

---

### Post by pxwpxw on 2007-03-10
Hi,

It should not affect the grub loader where you put the fat32 partition, but
I have similar, with fat32 at the end of the drive, after all the others.

It would be a good idea to do partitioning, then restart and check that XP can see the fat32, before continuing to install.

---

### Post by tintix on 2007-03-10
Usually Linux can boot from any partition - it doesn't matter if it residers in the end of hard drive (after all other partitions) or in the start of the hard drive (before all other partitions).
So, it would be better, if you create the fat32 partition in your windoze (to make sure that it will see the fat32) - go contro pannel => administrative tools => disc management (you shuold find the partitoner somewhere there). And then unstall ubuntu. :) And if there won't be radical changes in your HDD's partitions unless you gonna reinstall ubuntu or reform the partitions, you should make the fat32 partition as the first one, and install linux after it. 
You gonna create an ext3 partition for your ubuntu? Well, I prefer XFS - it's faster than ext3 and more reliable thean ReserFS. So, if you wanna switch to XFS do following:
 - create your swap like ususlly;
 - before creating the XFS partition, you need a small ext3 partition (about 40MB - there's enough place for 3 kernel images and few GRUB themes) - it's because Linux can't boot from an XFS partition. So after crating the small ext3 - it has to be mounted as "/boot".
 - then create a XFS partition and mount it like usual as "/". :guitar:

---

