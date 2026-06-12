---
title: "Problem in installation 11.04."
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by bobthe on 2011-09-15
Before I was getting error messages in the partition part of the installation of Ubuntu 11.04. After noticing that I had 4 partitions, and that I can't have more than that, I went onto my Windows 7 and deleted HP_Tools partition (I learned its not needed at all). And I allocated free space of around 50GB for Ubuntu. I figured now that I have 4 partitions including one for Ubuntu, the free space will be shown and I'd be able to partition correctly. 

But now, I'm having a problem with the installation itself. After the 2nd step in the installation: Preparing to Install Ubuntu in which I have to click on Download updated while installing...
After I click on forward, nothing happens. It just gets stuck there for no reason. I've waited for over 15-20 minutes. And its not doing anything. It was before I deleted the HP_Tools partition. But after calling HP, i learned from them that deleting the HP_Tools partition is fine especially when you need to install Linux on the 4th partition.

I even burned the image onto another disc and I'm getting the same issue. I've been trying to do this on my new laptop for the past 2 days. I've installed Ubuntu on many machines before and never had a problem like this.

Please let me know what I should do. I really need to dualboot with Ubuntu and Win7 as I'm a CS major and going to college in a few days. I want to deal with this mess ASAP. 

I've tried to install it many times, but everytime it gets stuck on that same step when i click on forward. 

Someone please help me!!!!

---

### Post by Hakunka-Matata on 2011-09-15
Hi, Welcome:

If you can boot into the LiveCD and choose "try without installing";
open a terminal:
```
sudo sfdisk -luS
```
post the results

---

### Post by bobthe on 2011-09-15
Sorry for the late reply, but here you go:


Disk /dev/sda: 77825 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63      2047       1985  42  SFS
/dev/sda2   *      2048    409599     407552  42  SFS
/dev/sda3        409600 1117050879 1116641280  42  SFS
/dev/sda4     1117050880 1250261679  133210800  42  SFS

Disk /dev/sdc: 1020 cylinders, 247 heads, 62 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   *      8064  15634431   15626368   c  W95 FAT32 (LBA)
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty

---

### Post by Hakunka-Matata on 2011-09-15
bobthe: your sda drive has converted to dynamic disk type.  It's something windows does when you attempt to make a fifth partition.  That must be fixed, reverted back to 'basic' disk type.

Here's one thread about the situation: [http://ubuntuforums.org/showthread.php?t=1819577&highlight=convert+dynamic+disk](http://ubuntuforums.org/showthread.php?t=1819577&highlight=convert+dynamic+disk)

---

### Post by mörgæs on 2011-09-15
PLEASE DON'T YELL IN THE THREAD TITLE LIKE 'PLEASE HELP URGENT!!!', though you of course would like a fast answer. I have moderated.

---

