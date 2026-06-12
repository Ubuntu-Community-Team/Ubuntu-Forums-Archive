---
title: "[B][U]Install: some files going to wrong drive[/U][/B]"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by j_b_seguin on 2005-10-13
I'm installing to a drive with three partitions and some of the folders are going 
to the third drive. Can anyone tell me why, and how to stop it from happening.

Maxtor 72rpm 120Gb

partition 1 - /
Partition 2- Swap
Partition 3 - /home
partition 4 - /usr/local

---

### Post by Velox Letum on 2005-10-13
Typically, when one mounts /home on a different partition, when that mount point is written to, its written to the partition its mounted at...ie partition 3. If you don't want any partitions other than / and swap, then you'll need to repartition.

---

### Post by j_b_seguin on 2005-10-14
I think what I have here is the swap folders installing on the last drive, from what I've 
been reading, the swap partition should be the last partition on the drive.

(??? the swap folders are audomatically installing to the last drive instead of looking 
for the swap drive ????)  The folders definately have the look of swap folders.

---

