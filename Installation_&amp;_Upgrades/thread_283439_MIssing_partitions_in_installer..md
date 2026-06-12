---
title: "MIssing partitions in installer."
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by manradjan on 2006-10-24
Hi,

I'm trying to install Ubuntu 6.06 and I'm having troubles with partitioning my hard drive. When I choose manual partioning in the installer, it doesn't show my partitions correctly. 
This is my disklayout:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7296    58605088+   7  HPFS/NTFS
/dev/hda2            7297       14593    58613152+   f  W95 Ext'd (LBA)
/dev/hda3           13415       14593     9470286    b  W95 FAT32
/dev/hda5            7297        7303       56196   83  Linux
/dev/hda6            7304        7366      506016   82  Linux swap / Solaris
/dev/hda7            7367       13414    48580528+  83  Linux

It displays this harddrive as unallocated diskspace. The strange thing is that my other harddrive, hdb shows up correctly (it has 4 linux partitions with data). I selected manual partitioning because I want to keep my windows install, but use the Linux partitions from another linux install. If I ignore this, and continue with the next step, I can choose my hda* partitions while connecting them to a mountpoint, but after that, it gives an error about no root filesystem being available.
Anyone knows how to solve this? Thanks in advance!

---

### Post by galego on 2006-10-24
sorry if im not helping at all, but hda1 you listed as HPFS/NTFS, however you dont have any Windows NT or DOS. i think (THINK being used very loosly) that may be why Ubuntu is not recognizing it.  and as far as givin you the error, i would understand as you have not specified a root and also hda5 and hda7 may not be ext3 file systems. (you did not specify) Ubuntu defaults to use ext3 file systems.

---

### Post by bulldog on 2006-10-24
When you mount an existing linux partition empty or not,Ubuntu will not over write it.

The best thing to do is to delete the partition and create it back again.
Then you can set it as / partition.

---

