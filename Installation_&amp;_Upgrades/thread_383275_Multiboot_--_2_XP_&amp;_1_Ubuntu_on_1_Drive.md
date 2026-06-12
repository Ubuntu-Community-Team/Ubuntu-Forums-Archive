---
title: "Multiboot -- 2 XP &amp; 1 Ubuntu on 1 Drive"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by bernie_sklk on 2007-03-13
I have a single 80 GB Drive with 2 separate installations of XP on two separate partitions. I have a 3rd Partition that I would like to install Ubuntu, but I'm not entirely sure how. I  tried to use the partitioning tool at installation, but it told me I had too many primary partitions.

Is this type of installation possible? How do I set up my partitions to make this happen?

Thanks in advance for the help and guidance!

---

### Post by buuntuu! on 2007-03-13
if you have got only the two xp partitions and the third one there should be no problem installing, as a hd can have up to four primary partitions. 
in the install-menu check "manually edit partition table" and then select your third partition for the ubuntu install. make it an extended partition as you can subdivide it into several logical partitions (you need at least two, one for root and one for swap)
sounds difficult, but is quite easy, here a little introduction on the principles of hd [partitioning]("http://en.wikipedia.org/wiki/Partition_(computing)")
and here [psychocats]("http://www.psychocats.net/ubuntu/") guide to installing ubuntu.
have fun

---

### Post by desheikh on 2007-03-13
Hi,

The reason you got that error is that a hard drive can only support 4 primary partitions.
If you want more you need to convert one of you partitions into a logical partition and go on from there. Just search on google for an explanation of the two types if your confused.

This is how i generally keep my dual boot setup
hda1 - winxp
hda2 - fat32
hda3 - fat32
hda4 - logical partition
   hda5 - ubuntu
   hda6 - swap

Multibooting wont be a problem as long ubuntu is the last os you install. The grub bootloader will detect all your bootable partitions.

Hope that helps,
Ali

---

### Post by bernie_sklk on 2007-03-23
Ok. I've been able to partition my drive. I had to use partition magic (Windows and Ubuntu wouldn't let me do it) to add my two additional partitions at the end of the drive. So, I have the following partitions

mbr
1st Windows install (primary)
2nd Windows install (extended)
swap (extended)
ext3 (extended)

The intended linux partitions were formatted using Partition Magic.

When I start the Ubuntu installer and go to the manual partition tool and try to tell it I want the "/" on ext3 (hda7) and "swap" on swap (hda6), it tells me I haven't specified a root mount. I'm obviously missing something. Any suggestions?

---

