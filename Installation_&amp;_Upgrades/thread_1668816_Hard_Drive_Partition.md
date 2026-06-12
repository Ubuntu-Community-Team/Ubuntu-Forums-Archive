---
title: "Hard Drive Partition"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by Badams130 on 2011-01-16
When i went to create a partition for Ubuntu using the Disk Management tool, i discovered there were three partitions: 
the C: Drive (Boot, Page File, Crash Dump, Primary Partition); 
a 9.01GB partition thats 100% free (Primary Partition); and 
a 1.46GB partition (Active, Recovery Partition). 

The last two dont have any letters assigned to them (theres no D: Drive or E: Drive). Is it safe to create another partition for Ubuntu, i dont wanna ruin my harddrive :-|

FYI, I'm Running Windows 7 64-bit.

---

### Post by Quackers on 2011-01-16
Welcome to UF.
The maximum number of primary partitions on any single disc is 4. If you have 3, it is safe to create another. The 4th partition would be better as an extended partition, as this can hold many logical partitions, which are fine for Linux systems.
It is usually better to create partitions for Linux systems with something like gparted (NOT Windows!)
In your circumstances it is likely that the whole hard disc is used by the 3 partitions currently in use. Therefore it will be necessary to shrink your C: partition to create some unallocated space for the 4th partition to be created in. This should be done from the Windows disk management screen (by right-clicking the C: drive and selecting "shrink").
However this should only be done AFTER defragmenting the C: drive - preferrably twice.

---

### Post by Badams130 on 2011-01-16
Thanks for clearing that up =D

---

### Post by Quackers on 2011-01-17
You're welcome :-)
Have fun, but take care!

---

