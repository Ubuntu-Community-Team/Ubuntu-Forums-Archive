---
title: "Dual upgrade from Ununtu 9.10 and Vista to 12.10 and Win8"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by nanso_ on 2012-11-23
Hi,
I'm trying to do several things at the same time.
I'm running Ubuntu 9.10 and Windows Vista Home Premium on another partition of my hard drive. I want to upgrade to Ubuntu 12.10, reduce the Ubuntu partition as it is too big, and upgrade to Windows 8 as well. 
I don't know where to start, I'd appreciate any advice.
Thank you

---

### Post by mikewhatever on 2012-11-23
Doing so many things at the same time will not work. Finish one thing first, then go to the next, etc, for example:

1. Backup!
2. Shrink the Ubuntu partition.
3. Upgrade Ubuntu.
4. Upgrade Vista.

Start with number 1.

Any questions?

---

### Post by nanso_ on 2012-12-01
Thanks for your reply, mikewhatever.
Alright, I'll take it step by step. I backed up both partitions. How do I shrink the Ubuntu drive?
Thanks

---

### Post by oldfred on 2012-12-01
How big is hard drive and how many partitions do you have?

sudo fdisk -lu
# Mount Windows partition(s) first to include it in this 
df -h

Use Windows to resize Windows, but not to create partitions or anything else. Reboot Windows a couple of times after a resize to let it run its chkdsk or other repairs to update its size.

Use gparted from Ubuntu liveCD and click on swap, right click swap off, so all partitions are unmounted.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

