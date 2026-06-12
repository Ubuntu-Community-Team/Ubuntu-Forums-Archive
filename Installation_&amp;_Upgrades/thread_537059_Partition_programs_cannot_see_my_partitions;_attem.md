---
title: "Partition programs cannot see my partitions; attempting to reinstall"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by apathos on 2007-08-28
I tried to create a separate /home partition (using psychocat's instructions) AFTER I had installed 7.04.  I deviated from his instructions, and mostly intentionally ended up wiping my partitions that had Ubuntu on them (I dual-boot XP and Ubuntu).

After fixing a GRUB error, I now have Windows booting fine like it always did, and Ubuntu is gone.  But when I try to install ubuntu, the partitioner program sees my hard drive, but tells me the whole disk is unallocated.  It is a single ~250GB HDD, with Windows installed in the front of it (unsure of size should be 60-80GB), and a second partition for windows restore (4GB).  Both the Live CD partitioner and GParted tell me the whole 250GB is unallocated.

How do I get the partition programs to see the existing partitions?

---

### Post by merlinus on 2007-08-28
You might use gparted live cd to wipe the old ubuntu partitions clean, and then recreate and format them as ext3.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Also, be sure to delete windows temp and other unneeded files, backup data, set vitual paging to zero (set it back afterwards) and defrag several times.

Then resize your xp parttiion.

-merlin

---

### Post by apathos on 2007-08-28
I appreciate the attempt, but that doesn't help me.  I tried it anyway, just to be sure.

When I boot GParted and get to the graphical UI, when I click the device and select 'new partition', it tells me it has to make a new label for the drive, and doing so will erase all data on this disk.  I already erased ubuntu, I'd rather not reinstall windows.

Why will my computer boot Windows, but no program can see the partitions...anywhere?  There's just nothing there in GParted, like it's a brand new HDD.

Even if someone can point me in a right direction, it would sure help.

---

### Post by Pumalite on 2007-08-28
Use rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) to investigate your system and your drive in particular. Or partition with Acronis.

---

### Post by apathos on 2007-08-29
Pumalite, that did the trick.  I used the SytemRescue CD, and it was able to see my partitions and mount them, using Ranish partition manager (the graphical interface would lock up after a few seconds, so I had to do it with Ranish).  Once I got the partitions mounted, I was able to reformat the partitions and square it away, and finished my install last night.  Thanks for the help!

I'm not sure if anyone will see this, but it'd be nice to know why Ranish could fix this, but GParted couldn't.  Maybe I'll learn someday.

---

### Post by MrGarde on 2007-10-18
I am having the exact same problem.
Gparted and the installation program, are both convinced that my hard drive is all "unallocated space", which is certainly isn't. 

Reassuring to see that someone else got it fixed. 

So, I've burned the rescue CD, and I understand that I have to reformat my ext3 partition (using Ranish?). But I'm a beginner and I dont understand how to do this. I've tried booting it, but all I could see was an (older) version of gparted that also didn't identify my the partitions correctly.

Could you give some hints?

---

### Post by Pumalite on 2007-10-18
[http://www.sysresccd.org/Online-Manual-EN](http://www.sysresccd.org/Online-Manual-EN)

---

