---
title: "Partition planning in conjunction with upgrade from (Xubuntu) Dapper to Feisty"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by jis on 2007-09-07
There are two hard drives - 10GB and 6GB - in my computer.
I have Xubuntu Dapper installed. /home partition is currently the 6GB drive. I want to have bigger /home partition and maybe different file system (ext3, currently xfs) for it so how would you move it to the other drive so that you could retain my personal data and settings when installing Xubuntu Feisty from CD? Is there some performance gain, if I have swap partition and / on different drive? (Actually I don't know which drive is faster.) ..Or maybe is it better to occupy the whole 10GB drive for /home? What is the fastest reliable file system for / ?

---

### Post by dabl on 2007-09-07
Well, assuming life must go on with just those 2 drives, the 6GB drive is sufficient for your "/" and swap partitions, if you put /home on the 10GB drive.  Hopefully you can back up your data to other media, and make it easy on yourself.  You will need a swap partition -- just make a 0.5GB partition on the 6GB drive, and use that for swap, and the rest of that drive for root. You should be able to do that all with the live CD (after you've backed up your data).  I personally prefer the "Alternate Install" CD -- it gives you a little more control and visibility over the process. Good luck with Feisty!

:)

---

