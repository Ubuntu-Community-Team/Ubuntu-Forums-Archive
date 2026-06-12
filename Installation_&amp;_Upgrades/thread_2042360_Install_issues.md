---
title: "Install issues"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by jpsil on 2012-08-14
Hey all, 

I am having some issues with installing Ubuntu on my laptop.  I recently reinstalled windows after screwing up the MBR and GRUB.  I currently am able to boot into Windows 7 Home Premium and into Backtrack 5 R2.  The problem is that neither the ubuntu installer nor gparted can see the individual partitions on my drive.  It is all listed as one unallocated space.  When I open the "ubuntu explorer" on the live cd I can see the other partitions and can even mount and explore inside of them.  I did an fdisk -lu just for kicks and it sees all of the partitions.  Here is the output from the fdisk:

root@ubuntu:~# fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27877510

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    24578047    12288000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    24578048   478479952   226950952+   7  HPFS/NTFS
/dev/sda3       478488576   790430120   155970772+   7  HPFS/NTFS
/dev/sda4       790430130   976784129    93177000    f  W95 Ext'd (LBA)
/dev/sda5       790430193   895286384    52428096   83  Linux
/dev/sda6       895287296   934418431    19565568   83  Linux
/dev/sda7       934426624   936220655      897016   82  Linux swap / Solaris
/dev/sda8       936224768   974993407    19384320   83  Linux
/dev/sda9       974995456   976773103      888824   82  Linux swap / Solaris



sda 1 is the recovery for windows.
sda2 is the windows 7 partition.
sda3 is a data partition for windows.
sda4 is ?.
One if the Linux partitions and the swap partitions must belong to Backtrack.

Any help would be greatly appreciated.

--Jpsil

---

### Post by jpsil on 2012-08-15
Any ideas?

---

