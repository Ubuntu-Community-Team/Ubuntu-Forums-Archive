---
title: "Will I be able to dual boot?"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by chazperx on 2010-06-12
I am about to install Ubuntu 10x, but before I do, I need to be sure the install will offer a chance for a dual boot. Does such an offer exist? Does the program do it, or do I need to partition?
 
Thanks
 
Chaz

---

### Post by darkod on 2010-06-12
Dual boot with? Windows?
Yes, you will be able to. Partitioning is necessary either way, the only difference is the guided methods use some algorithm to decide how big to make the partitions, while using manual partitioning puts you in control to set the partitions sizes as wanted.

Also, if you don't have unallocated space to use (not belonging to any partition right now), and you have vista or 7, it's better to shrink the partition you plan to shrink using windows Disk Management, than using the side-by-side method. Reboot windows few times after the shrink to do its disk checks.
After that install in the unallocated space you created with the Use Largest Available Free space option or manual partitioning, as you wish.

---

