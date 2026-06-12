---
title: "[SOLVED] Advice on partition setup for multi-boot system"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by Patb on 2008-04-16
Hi. How should I set up my home partition? 

I am setting up a triple-boot desktop system designed basically for one user.  I have two hard drives.  Here is my current (tentative) partition setup:
```
pat@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55d4193d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406   83  Linux
/dev/sda2            1276        4865    28836675    5  Extended
/dev/sda5            1276        1912     5116671   83  Linux
/dev/sda6            1913        2549     5116671   83  Linux
/dev/sda7            2550        3059     4096543+  83  Linux
/dev/sda8            3060        3569     4096543+  83  Linux
/dev/sda9            3570        4079     4096543+  83  Linux
/dev/sda10           4080        4525     3582463+  83  Linux
/dev/sda11           4526        4865     2731018+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a22ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2866    23021113+  83  Linux
/dev/sdb3            2867        9553    53713327+  83  Linux
```
/dev/sda1 is for a full Ubuntu OS.
sda2 is for a minimal Ubuntu OS.
sda 3 is for another Linux distribution (to play around with).

/dev/sdb1 and sdb2 are for documents and data respectively.  I do not wish to tamper with those.  

My question is whether it is wise to have three separate home partions (sda5 for Ubuntu, sda6 for minimal Ubuntu, and sda7 for the 'other') or combine them on one larger partition.  On the one hand, I could set up different partitions as they are now, each with the same primary user "pat".  That way, there would be no chance of confusion about user settings for different OS's. However it may lead to space related problems later on if one home partition needs more space.  

On the other hand, I could merge the current sda5, 6 and 7 into one larger partition and set up different primary users for each OS.  If I later decide to experiment with some other Linux distribution (eg DSL or Puppy), would there be any disadvantage in using the one home partition for the different distributions?  

Which way should I jump?  Any comments appreciated.  (With advance apologies for the fact that I cannot seem to get my feeble brain around this :confused:).

Cheers, Pat.

---

### Post by Pumalite on 2008-04-16
This might help:
[http://ubuntuforums.org/showthread.php?t=577990](http://ubuntuforums.org/showthread.php?t=577990)

---

### Post by Patb on 2008-04-17
Thanks, Pumalite.  I hadn't come across that informative link.  It confirms that using one home partition with one user name will likely lead to confusion between different OS's.*  And I am disinclined to use one home partition and a different user name for myself for each OS (I might forget who I am! :)).  So I think my best option is to stick to the current plan and have a separate small home partition for each OS.  

If I seem to have missed anything, I would appreciate feedback.  

Cheers, Pat.

_* PS: Edit_:  I did experiment doing exactly this and sure enough there was significant confusion between Gutsy and Hardy when each "adopted" a home user set by the other.  I ended up using a different home partition for each OS, each with the same primary user "pat".  I imagine it would be equally okay (albeit a little confusing as I have explained) to have just one home partition with different user names, one for each OS, within.

---

