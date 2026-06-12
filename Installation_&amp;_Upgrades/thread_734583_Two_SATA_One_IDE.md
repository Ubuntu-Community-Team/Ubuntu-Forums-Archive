---
title: "Two SATA/ One IDE"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by EvilRick on 2008-03-24
Here's the hardware

ASUS K8V-SE Deluxe (Using the VIA SATA)

Two 80GB SATA
One 80GB IDE

- I have the two 80GB SATAs partitioned with 2GB Primary and 78GB Primary

- Primary on 1st is swap for Ubuntu 7.10 and Primary on 2nd is pagefile.sys and 'TEMP' for Windows XP

- The 78GB Primary partitions are set up with Windows XP on the 1st disk and Ubuntu on the 2nd

-- It looks something like this with Disk Management

Disk 0 | 2GB (Healthy, unknown) |   78GB (NTFS Windows XP)  |
Disk 1 | 2GB (NTFS SWAP)           |  78GB (Healthy, unknown)   |

- I disconnected the IDE during the Ubuntu install

Here is the problem . . .

GRUB seemed to install okay, it said it was installing to (hd0) and when the PC boots, I get the GRUB menu.  I can select Windows XP and it boots into XP.  If I select Ubuntu, it shows "Loading, please wait . . ." and then nothing.  No CTRL+ALT+F1-12 will do anything.  I tried editing the menu.lst to see if it was the whole SATA drive order thing and nada, still no boot.  It's showing that it wants to boot from (hd 1,1) which I think is correct.
It doesn't matter if the IDE is reconnected or not.

Does the IDE throw the order out of whack?

If I've left something out, let me know.

Thanks.

EDIT - Here's the 'sudo fdisk -l' with IDE disconnected.  I also noticed in the BIOS that when I disconnect the IDE, it changes the first boot drive to the 2nd SATA.  ???

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a1d92ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         262        9729    76051710    7  HPFS/NTFS
/dev/sda2               1         261     2096451   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x320a1743

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         261     2096451    7  HPFS/NTFS
/dev/sdb2             262        9729    76051710   83  Linux

```

---

### Post by EvilRick on 2008-03-24
Strange.  In the menu I chose the "recovery" option and it booted right into Ubuntu.  I looked at the 'menu.lst' file and saw that there was no difference in the partitions from the recovery option and the normal, so I rebooted and waited about 5 minutes and if finally booted into Ubuntu.  The time it's taking to boot is a bit disturbing, but I'm in now so I can troubleshoot the long time.

I guess you can count this as "CLOSED".

---

