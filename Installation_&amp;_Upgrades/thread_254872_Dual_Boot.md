---
title: "Dual Boot?"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by ByKeLaO on 2006-09-10
](*,) Hi I have Windows XP Home installed, and under windows I have 4 logical partitions:
1 emergency recovery file partition which has not been assigned a drive letter
Drives C:\, D:\ and K:\

I would like to either install linux onto the logical partition assigned to drive K, or resize the partitions, and set up a dual-boot system.

the problem is, none of the partitions created in windows appear in linux.

Any suggestions?

---

### Post by marcelm on 2006-09-10
Make some free empty space on your harddrive. Do this with a good partition manager in windows XP. (like 15 Gb).

Don't forget to defragment AND make a CHKDSK in XP.!

Start up a Ubuntu install, and when the partition screen comes, choose manual partition. Then, in this unassigned space, make a ext3 partition and a (like 1 Gb) Swap space. Be sure to mount them properly (do not mount them on your XP partition of course.)

Install the Ubuntu on this new partition. The dual boot should function properly now. Do NOT forget to backup your valuable data in XP. I've recently made a dual boot and tried to resize a NTFS partition in gparted, the program messed up the XP installation. Resize in XP. Good luck.

---

### Post by ByKeLaO on 2006-09-11
Thank you for your fast reply. I'll try what you suggested.

---

