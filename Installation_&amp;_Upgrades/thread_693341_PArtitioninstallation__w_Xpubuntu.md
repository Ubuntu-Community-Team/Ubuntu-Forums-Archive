---
title: "PArtition/installation  w/ Xp/ubuntu"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by carress on 2008-02-10
Don't mean to flood- I think I posted this in the wrong forum already.


I have installed windows xp, and was able to partition my HD. Now in ubuntu, i think i see 2 partitions, and in windows, I see 1 C drive at 58GB, and unallocated space at 53GB.  am trying to install ubuntu now, and I'm not sure what to do. It's asking me to partition the disk, but I've already done that, and it seems to see tht it's partitioned b/c the slider for 'new partition size' is at 58.1GB- that part is orange, and everything to the right is gray. I get an error when I try the guided partition, and it brings me to the manual partition window. In the manual window, I think I see the two partitions. the first one says /dev/sda1 (or l-I'm not sure) - its type is ntfs (which makes me think it's the 'c' drive from windows), the mount point is /media/sda1 (or l?) the Format box is unchecked and uncheckable, the size is 62915MB, and 7500MB.  The secon partition says free space, nothing for type and mount point, uncheckable Format box, 57116mb as size, and no used space.

I'm thinking I need to create a new partition within the free space..actually create 3 partitions...but I'm utterly lost at this point.

I can't seem to find my situation in any documentation, and I have read a bunch of stuff in the last few days...  Is anyone willing to do some hand-holding??

---

### Post by erfahren on 2008-02-10
you're correct - everything is as it should be 

I'm not going into the reason why right now  - but make the partitions for Linux as "logical"

so do this:

out of the free space - right-click and create new - make the size 6GB - and set the mount point as root ( / ) - if you need to type that in just type it as "/" (a slash) - make it logical

take the rest of the space and subtract about 1042MB (a little more than 1GB) - make a partition - set the mount point as /home - make it logical

the leftover space of 1GB - make it a partition - swap - make it logical

that should do it

---

### Post by jesusfreak107 on 2008-02-10
Alright. freeze. backup to the beginning. Okay.
Now, you say you have a Windows drive at 58GB.
You have unallocated space at 53GB.
Linux Recognizes the sda1 (yes, 1) as some used, some free, with the partition being ntfs.
Now, you have a "free space" *partition* of 57GB. That is the one you need to install it on.  if it is not a partition, and just free space for Windows, then that means that I did not understand you at all.  But if it is a partition, then you are fine.  Now, the weird part in that is that you say that the free space partition is uncheckable. that is not supposed to be so.  First, make sure you are root, or an admin (if you are using a live CD, you *should* be).  Then go to System>Partition Editor.  If stuff is still incheckable, open a Teminal, type "sudo bash"(makes you a root user), and type "gparted"(opens the partitioning tool.)  That should bring up the Partition Editor as Root.
WARNING:
Using the previous terminal commands to open the Partition Editor gives you a powerfull weapon of mass destruction. While using the Partition Editor, make sure you know what you are doing, or you could format your Windows drive.  

That being said, you will need to take the empty space, and format it to the "ext3" format. Also, you will need some swap space. Swap is sort of like fake RAM that Linux uses when it runs out of normal RAM.  I would suggest partitioning as much to the "swap"(or "linux swap") as you have RAM (1GB RAM, 1GB swap, etc.).  Then, run the install again, and *select* the ext3 partition as the "/" section, and the swap as the swap section. try that.

---

### Post by erfahren on 2008-02-10
@jesusfreak - the reason the format box is uncheckable for the free space is because it is not yet actually a partition

I've seen that screen a few times - everythings fine

---

