---
title: "Can't get past the partitioning part of the installation of Ubuntu &quot;Warty&quot;"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by herofryar on 2005-03-23
Hello everyone,

This is my first posting on these forums, wish it would have been to how much I like Ubuntu but I am afraid I am having siome trouble getting it installed.

I've had a lot of spare old components laying around the house for sometime and have decided to put these together to have a PC that I can install linux on to play with before deciding whether to put it on my everyday PC or not.

The specification of the PC is as follows:

Intel Celeron 266Mhz Processor
230MB RAM
2 x 3.2GB Hard Drives (1 x Fujitsu and 1 x Quantum)
16MB Savage 4 Pro AGP Video Card

When I try to install Ubuntu it gets to the partitioning stage and then starts to be funny, the PC will either freeze when I tell to delete any exisiting partitions or after it has formatted the ext3 partition. I haven't been able to get past this stage.

Any pointers?

---

### Post by sunscape on 2005-03-23
Try pressing F1 (i think) during installation, and enter noapic nolapic. There is a provide example of what it should look like. If i remember correctly, you can just copy it directly.

---

### Post by wylfing on 2005-03-23
If I read it right that you want to spread your directory structure across two HDs, you might want to boot with the Live CD, set up the partitions with cfdisk, and then try installing warty.

---

### Post by herofryar on 2005-03-24
[QUOTE=wylfing]If I read it right that you want to spread your directory structure across two HDs, you might want to boot with the Live CD, set up the partitions with cfdisk, and then try installing warty.[/QUOTE]

No, not neccessarily anyway. I am just trying to get Ubuntu to install which I can not do at the moment. IF I can just get it working with just one hard drive then I would be happy.

---

