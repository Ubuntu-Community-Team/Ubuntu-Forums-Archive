---
title: "Partitions not showing"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by Shino90 on 2007-05-12
Im trying to install Ubuntu 7.04 Feisty Fawn. The problem I have is that Ubuntu doesn't see any of the partitions I have. I have divided my drive into three parts. One part is for Windows XP, one part is for Windows Vista, and another part is unallocated, ready for Ubuntu. I made these partitions in Windows XP.

Here's a screenshot of the disk management screen in Windows Vista, clearly showing how my drive is divided:
[http://members.home.nl/jgsijen/ubuntu/schijfbeheer.png](http://members.home.nl/jgsijen/ubuntu/schijfbeheer.png)

Here's a screenshot of GParted (running off the livecd):
[http://members.home.nl/jgsijen/ubuntu/screenshot1.png](http://members.home.nl/jgsijen/ubuntu/screenshot1.png)

It thinks my entire drive is unallocated... And so does the Ubuntu installer. When I try to install, I only get two options:
[http://members.home.nl/jgsijen/ubuntu/screenshot2.png](http://members.home.nl/jgsijen/ubuntu/screenshot2.png)

The manual partitioning requires me to erase all my current partitions:
[http://members.home.nl/jgsijen/ubuntu/screenshot3.png](http://members.home.nl/jgsijen/ubuntu/screenshot3.png)

Now, the weird thing is that the FDISK command in the Terminal *does* see my partitions:
[http://members.home.nl/jgsijen/ubuntu/screenshot4.png](http://members.home.nl/jgsijen/ubuntu/screenshot4.png)

I have no clue what could be causing this. I tried installing NTFS drivers ("sudo apt-get ntfs-config" with universe enabled) but this didn't help either. I also tried rewriting the partition table to the disk using FDISK.

Any ideas?

---

### Post by Shino90 on 2007-05-15
I managed to fix my problem. Apparently one of my partitions ended out of my harddisk's range. (Not quite sure how that happened...) I got the error when trying to launch GParted through the Terminal ("sudo gparted /dev/hda") in an Ubuntu LiveCD session. I booted back into Windows Vista and shrunk the partition that was out of bounds, and that fixed it.

Thanks for helping, everyone. :lolflag:

---

