---
title: "Ubuntu not showing partitions"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by jaytu on 2006-10-08
Hi,

I am trying to install Ubuntu from the live CD and use with XP as dual boot. My hard drive is partitioned as follows:

40g
- 5g Free Space (fat32) Primary
- 23g Data (ntfs) Primary
- 12g WinXP (ntfs) Primary Active

When I get to the partitioning section in the installation it shows this hard drive as one 'unallocated 40g' hard drive and not with above partitions. I would like to install Unbuntu on the free space (4500 + 500 for swap file).

Am I doing something wrong ????

Any help would be much appreciated... Thanks

---

### Post by srunni on 2006-10-08
Are you doing a manual partition or using the "resize" option?

---

### Post by jaytu on 2006-10-08
I am not given a resize option... so am trying the manual partition...

---

### Post by jaytu on 2006-10-11
I got it to work...

The problem seemed to be that I had XP installed at the end of the drive (the drive was pretty untidy). So I did a complete format of the drive and put XP at the start of the drive. I didn't seem to ahve any problems with Ubuntu seeing the partitions then... Install went smoothly. 

I now have the following partitions setup 
WINXP - NTFS - Primary
Ubuntu - EXT3 - Primary
/Home - EXT3 - Logical
/Swap - Swap 

Hope this might help others !!!!

---

