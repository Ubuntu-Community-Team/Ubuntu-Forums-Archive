---
title: "Hard Disk not enough space during update/upgrade."
date: 2013-07-30
forum: Installation &amp; Upgrades
---

### Post by termvrl on 2013-07-30
Hi all,
i have installed Ubuntu desktop with 20gb HDD.
but when i do update and upgrade, prompt an error, not enough space/hard disk is full.
when i do "df -H" no free space.

what is min requirement for the HDD.
i thought 20gb is more than enough.

---

### Post by VMC on 2013-07-30
20 gb iwould be enough, if everything else is correct.

From a terminal type the following so we can see what's partitioned:

```
sudo blkid
```

Then we can go from there.

---

### Post by Bucky Ball on 2013-07-30
*Thread moved to **Installation & Upgrades**.*

No idea why this was posted in ***Absolute Beginners***. Please post in the appropriate section, it will increase you chances of getting help.

Short answer: make more room. This problem is unresolvable and means you have no 'headroom' left on the disk; the install needs to chuck a heap on there to install which it then 'cleans'/deletes later and leaves the space free again. You don't have the room to manipulate the data. There is no alternative but to resize or clean install on another partition.

This is assuming you have been using this install for awhile and you really have no space left (run Gparted and find out). This is a common problem with the upgrade option. Clean install generally less problematic.

---

### Post by termvrl on 2013-07-30
Hi all,
Thanks for the reply.
I will do a fresh install and provide more space.

---

### Post by Bucky Ball on 2013-07-30
Probably best. Remember, if you have existing /home and /swap partitions you can use these with the new install rather than creating new ones. When you get to the partitioning section, choose 'Something Else' and partition manually. Mark /home and /swap to be used but NOT TO FORMAT! Designate where you want the OS to be installed (the / partition) and fire away.

Goes without saying you should backup anything you don't want to lose (precautionary as if done correctly you shouldn't lose anything from a separate /home) before attempting. 

PS: If you are intending to do a fresh install over the OS you are trying to upgrade you won't need to resize that partition as you are deleting the old and replacing with the new (which will use less space). 20Gb should be plenty for a regular Ubuntu install (with the /home on a separate partition, that is). If your /home is a directory on the same partition as / then you better make that partition big. I'm presuming this is the scenario and why you ran out of space. ;)

---

