---
title: "Can't change XP partition"
date: 2006-05-23
forum: Installation &amp; Upgrades
---

### Post by SteveHoffmanUK on 2006-05-23
Newbie here. Trying to set up dual boot using the technique recommended at the Psychocats website ([http://www.psychocats.net/ubuntu/partitioning.html)](http://www.psychocats.net/ubuntu/partitioning.html)), whereby you have a small NTFS partition for XP, but other partitions are ext-3, using the Wire32 program to allow XP to read ext3 files.

I must be doing something wrong because I can't seem to do any partitioning. When I instal XP, it gives you the option of setting the size of the XP partition, saying it must be at least 8MB but it's preset to almost the whole disk (39GB), and I can't insert a different number. I've tried everything I can think of -- backspace, upwards arrow, downwards arrow, delete -- but the preset remains: I can only add digits at the end. 

I have also tried to change this large NTFS partition using the live Dapper disk, but it won't let me change the size.

Any suggestions on how to proceed? I'm able to mess around at this point because I have to reload XP anyway, so I can't do any damage to Windoze, and, yes, I have backed up all my files!

---

### Post by aysiu on 2006-05-23
XP itself will always want the whole disk, so you will have to install it to the whole disk and then resize it afterwards.

Generally, this isn't a problem. Theoretically, GParted, QTParted, and the Ubuntu text-mode installer can all resize NTFS.

Sometimes, though, the option is greyed out for whatever reason.

The only reliable partitioner I've found is [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142). Unfortunately, using it involves downloading an entirely different Linux distro.

---

### Post by SteveHoffmanUK on 2006-05-23
Many thanks, aysiu.

I'll try Ubuntu text-mode and see whether that will work.

What I will NOT do is install a completely different distro  :rolleyes:  I'm not a masochist.

---

### Post by aysiu on 2006-05-23
[QUOTE=SteveHoffmanUK]
What I will NOT do is install a completely different distro  :rolleyes:  I'm not a masochist.[/QUOTE] Just to clarify, to use DiskDrake, you would have to download and burn a completely different distro. You would **not** have to install that distro.

---

### Post by SteveHoffmanUK on 2006-05-23
Aysiu wrote:

> Just to clarify, to use DiskDrake, you would have to download and burn a completely different distro. You would not have to install that distro.

Thanks for the clarification. I note your answer to S{yndrome}in another thread and now understand that DiskDrake is a partitioner that is included in another distro, so you have to burn a CD of that distro in order to be able to run DiskDrake but you can then opt out and install Ubuntu once you've used DD.

---

### Post by aysiu on 2006-05-23
[QUOTE=SteveHoffmanUK]so you have to burn a CD of that distro in order to be able to run DiskDrake but you can then opt out and install Ubuntu once you've used DD.[/QUOTE] Exactly.

---

