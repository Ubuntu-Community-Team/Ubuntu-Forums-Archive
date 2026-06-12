---
title: "Dual boot - Installing Ubuntu on a blank partition?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by hungryhungry123 on 2007-04-21
Hi, I currently have XP installed on my machine but would like to make it a dual boot system, I wonder if osomeone out there can help me.

I have 2 hard drives :  

First is 250gb, single partition, with XP installed.

Second is 120gb, with 2 partitions : one of 100gb which I use for data/storage, and another of 20gb which is empty.  All are NTFS file system.


How could I go about installing ubuntu to this blank partition?  The automated installer seems to want to use a whole drive to install to.  I'm also aware that I need a swap partition as well as the root partition, so do I need to create a small swap partition within the 20gb empty partition? If so, how would I go about this?  I'd also like to have it so that XP boots by default, not Ubuntu.

I'm pretty sure im just missing the obvious here, but any help would be much appreciated! Thanks!

---

### Post by hungryhungry123 on 2007-04-22
Anyone?  I've thought about it a little more, if I delete the empty partition so it shows as "free space" then tell Ubuntu to install to "largest continuous free space", will that work?  I'm scared that it will overwrite my XP or data files...

---

### Post by Harkainos on 2007-04-22
You could also manually decide where Ubuntu installs. It has its own partitioner and would be able to format a partition and install there.

---

### Post by pepsi_max2k on 2007-04-22
If the manual partition bit in your installer isn't recognizing current partitions, see [http://ubuntuforums.org/showthread.php?t=413745](http://ubuntuforums.org/showthread.php?t=413745)

---

