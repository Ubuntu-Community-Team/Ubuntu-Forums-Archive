---
title: "Install does not see Vista"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by poliltimmy on 2012-11-12
The install gets to 'type of installation'. It sees no Vista install. Apire m1100. fresh Vista install. Tried Mint, tried PCLinux same results.


ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 251.1 GB, 251059544064 bytes
255 heads, 63 sectors/track, 30522 cylinders, total 490350672 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9800481f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   418668535   209333244    7  HPFS/NTFS/exFAT
/dev/sda2       418668544   490346495    35838976    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$

---

### Post by oldfred on 2012-11-12
Does gparted show any little warning icons on your two partitions?

Was drive ever RAID or gpt? Both may leave meta-data on drive that prevents use with MBR(msdos). Windows often ignores the discrepancy but Linux sees the other data and does not want to damage system so it just stops and assumes you really want RAID or gpt partitioning.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

