---
title: "Ubuntu grub doesn't read Win 7 Ultimate 64bit..."
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by tiom33 on 2012-06-24
First, I installed "Windows7 Ultimate K 64bit" on my laptop.
While installing, I partitioned the harddrive as three parts:

c drive (60GB) - For Win7
d drive (60GB) - For Ubuntu
e drive (180GB) - Storage
( No "system reserved" partition. )

Then, to make a dual-boot system, I tried to install Ubuntu 12.04 64bit.

But the Ubuntu installer doesn't read any OS installed previously..
On Terminal, fdisk knows there's three partitions.
But gparted(&the installer) does not.
So It doesnt offer 'install alongside'  option.


What should I do?

---

### Post by darkod on 2012-06-24
First, delete the D: partition. If you created it in windows it would be NTFS and linux doesn't install on NTFS.

If the disk has been used in raid before and still has meta data remains, the ubuntu installer might ignore it.

Also, if there is some error or corruption in the partition table it might not recognize windows (and the partitions).

Can you post the fdisk results?

---

### Post by tiom33 on 2012-06-24
Thank you for your response!

Here's fdisk results.
------------------------------------------------------------------
root@ubuntu:~# fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa0e93598

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   122882047    61440000    7  HPFS/NTFS/exFAT
/dev/sda2       245762112   625137663   189687776    7  HPFS/NTFS/exFAT
------------------------------------------------------------

There's someting like "GPT" and "GNU"...
And no partition between C and E... Maybe it's because I unallocated it just before.

---

### Post by darkod on 2012-06-24
I think the disk was used with GPT partition table before, and then you tried to convert it to MSDOS table with windows.

But windows doesn't delete the backup gpt table, so linux is detecting it.

Beofre doing anything else, boot with the ubuntu cd in live mode and try using fixparts on the disk. If I am right, that should offer you to remove the backup gpt table, and all should be fine after that. Fixparts instructions are here:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by tiom33 on 2012-06-24
You're right! I installed Ubuntu only on my laptop last week and used it 
for a week.
I'll try it as soon as I understand the tutorial on your link!

---

### Post by tiom33 on 2012-06-24
It worked perfect!!
Thank you for your help.

---

