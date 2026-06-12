---
title: "New 8.04 Install ?'s on Acer 5420 Dual Boot"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by MrKenmore on 2008-07-30
Hi everyone.  I just bought an Acer Extensa 5420 laptop.  It has Vista on it right now.  I'd like to do a dual boot with Kubuntu 8.04.  The partitions are as follows:

10 GB Hidden Recovery Partition
51 GB Vista Partition
51 GB "Data" Partition

My thinking is to make use of the 51 GB data partition for 8.04.  Does this make sense?  Will I potentially mess up the MBR?

Thanks for any help.

---

### Post by tuxxy on 2008-07-30
Shouldnt do

---

### Post by MrKenmore on 2008-07-30
Any suggestions?  My other thought was to wipe out the entire HD and do a dual boot with XP and Kubuntu.  BTW-I have already made the backup DVD's.

---

### Post by MrKenmore on 2008-08-04
FYI - did the install and everything went smooth.  I used the following for partitioning:

10 GB Recovery Partition
30 GB Vista

The rest was free space.  I deleted all the other partitions in Vista.

I then set up 1 GB swap, 20 GB root and the rest as a FAT32 data partition for both to use.  All of these were logical partitions.

Thats basically it.  Grub installed fine and everything works with regard to dual booting.  Wireless card and sound don't work yet.  Still working on it.

---

