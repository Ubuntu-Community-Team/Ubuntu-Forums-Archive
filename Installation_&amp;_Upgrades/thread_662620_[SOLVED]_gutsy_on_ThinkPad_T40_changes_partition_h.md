---
title: "[SOLVED] gutsy on ThinkPad T40 changes partition hdd parameter"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by pkn on 2008-01-09
Hi,

I've got an ThinkPad T40 (centrino 1,5GHz, Radeon 7500, 40GB HDD). Windows XP is installed on a 20GB Partition, the remaining space  is unused. I installed ubuntu 7.10 alternate with guided partitioning (use free space). Grub was installed on MBR, but Windows won't boot anymore. Blue Screen -> unmountable boot volume.  XP Recovery console was not able to read the windows partition and to fixboot / fixmbr. I had to delete the linux partitions first and then I could restore Windows MBR.

I did some tests what might go wrong during ubuntu installation and here is what I noticed:

I booted Ubuntu 7.10 Desktop and started the installation routing. Before partitioning I check the partition table. It shows up like this:

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x69737369

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       41610    20971408+   7  HPFS/NTFS

```

Right after the guided partitioner created two new partitions, the table looks like this:

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2611    20971408+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2612        4764    17293972+  83  Linux
/dev/sda3            4765        4864      803250    5  Extended
/dev/sda5            4765        4864      803218+  82  Linux swap / Solaris
root@ubuntu:~#

```

Now the hdd has 255 heads, hence less cylinders. This change makes the windows partition unusable.

I wonder if this issue is connected with a wrong identification of the hdd. 
The T40 has an ATA drive, but it is detected as sda. Within Knoppix it is detected as hda.

I was thinking about creating the partitions within Knoppix and then install ubuntu and hope it does not alter the partition table...

any help on this one?

regards,
Andreas

---

### Post by pkn on 2008-01-10
Hi,

I could identify the issue which causes the problem:

The 40GB harddisk ist detected as 34GB within Windows. Linux detects 40GB and rewrites the partition table this way. As a result Windows locks up, because the partition table refers to an 'supposed to be not existing' harddisk space.

I'll check the BIOS, as soon the admin tells me the password....

regards,
Andreas

---

### Post by pkn on 2008-01-11
One more on this - it's the IBM Predesktop Area - a hidden partition which holds some recovery files. However recent linux kernels detect and access the full disk space, which results in pretty serious situations.

This article explains the stuff:

[http://www.thinkwiki.org/wiki/Hidden_Protected_Area](http://www.thinkwiki.org/wiki/Hidden_Protected_Area)

The bug has already been reported here:

[https://bugs.launchpad.net/ubuntu/+bug/25451](https://bugs.launchpad.net/ubuntu/+bug/25451)

regards,
Andreas

---

