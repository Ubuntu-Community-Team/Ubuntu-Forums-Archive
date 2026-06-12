---
title: "Best way to Partition Shared Drive? (dual boot, linux/XP)"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by dpatel304 on 2006-10-30
I am currently at the partition screen in ubuntu.  Just got done installing a new copy of windows.

Currently, my screen shows this:
/dev/hdd1          ntfs 50GB - windows xp
new partition #1   ext3 50GB - will be for ubuntu
new partition #2   linux-swap 1GB - swap partition
new partition #3   extended 130GB
    unallocated     unallocated


The last partition should be my shared drive.  I would like to know the best way to go about this, and what exactly to enter in for the next screen.  I am a complete newb at this, so any help would be greatly appreciated.  (I realize 50GB for each OS seems like a bit much, but I would rather have the extra breathing room, if need be.  Plus, previously I had not even come close to maxing out my HDD, so the 130GB shared should be more than enough).

Also, what would I set as my "Mount points" for each of the respective partitions.  My XP is defaulted to /media/hdd1.  I set the swap partition to "swap", and the linux partition to "/".  I'm not sure what to do for the shared partition.

---

### Post by Sef on 2006-10-30
For the alternate CD install, read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

For the Desktop CD install, read [Psychocat's Installing Ubuntu]("http://www.psychocats.net/ubuntu/installing").

---

