---
title: "Dual Boot Partioning ???"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by whitetimer on 2010-04-18
Hi All

Ok just doing my very first dual boot install and started with Windows 7 where i have 2 partitions and then installed ubuntu, but when i tried to do the partitions manually, i could only create / & /home i could not create a swap partition ... Would this be normal, have i to many partitions or something ... ?

Many Thanks

---

### Post by RavanH on 2010-04-18
> **whitetimer said:**
> Hi All

Ok just doing my very first dual boot install and started with Windows 7 where i have 2 partitions and then installed ubuntu, but when i tried to do the partitions manually, i could only create / & /home i could not create a swap partition ... Would this be normal, have i to many partitions or something ... ?

Many Thanks

Yes, you will have run in to the PRIMARY partition limit. One volume can only hold 4 primary partitions so if you already had 2 one there (most likely one hidden manufacturer partition and one windows partition) then you will have run out after creating a root and a home partition for Linux.

The way to go here is to create an EXTENDED partition. This will allow you to go on and create more partitions inside it. There are many pages around the web that give advise on what how and where to create partitions for Linux but I would suggest to limit it to the three you are already talking about:
1. Create one new primary partition (#3) right after the two that are already on there (do not make the windows partition too small or W7 will nag your ears off about having less than 25% free space!) to be used as root (/) sized at least 10GB (bigger if you are planning to install a huge amount of software or if you will be needing lots of /tmp space for video editing for example)
2. Create an extended partition right after that filling the remainder of your disk
3. Create a swap space at the start of the extended partition at least the same size of your PC's physical memory (needed for hibernation) or 2GB if the size if physical memory is less than that.
4. Create your /home partition right after that filling the rest of the extended partition

The idea behind placing the swap in the middle instead of at the end is that that minimalizes disk heads going back and forth spanning the complete disk area. This way, most read tracks on the disk will be relatively close to each other reducing seek times.

---

### Post by Bucky Ball on 2010-04-18
You maybe just not selecting it quite right. The swap partition is a default in the manual partitioning section which you can select from one of the drop down boxes and not the drop down box where you select the default / and /home from memory. You designate the partition swap space and the rest is taken care of. 2Gb should be plenty.

RavanH, the swap partition is the one giving problems, the others seem to be working so maybe not the primary partition problem. But having said that, yes, you can only have four. Windows needs to run on a primary partition, so yes again, make and extended and you can put lots of virtual disks (partitions) on that.

---

