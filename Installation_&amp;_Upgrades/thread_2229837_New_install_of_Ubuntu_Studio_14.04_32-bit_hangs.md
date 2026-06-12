---
title: "New install of Ubuntu Studio 14.04 32-bit hangs"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by Justin_Streiner on 2014-06-15
I installed Ubuntu Studio 14.04 32-bit on a machine with a pair of 1 TB drives built as a RAID1 mirrored pair through the machine's BIOS, however when I boot the machine without the live DVD loaded, it hangs at the point when GRUB would take over.  I wiped both of the drives clean before I started the installation.

When I installed US, I had to choose the option to set up LVM.  Without it, the installation would fail at the point where I select a time zone, with an error pop-up that just says "??? ???".

I chose LVM, and the installation completed.  When I rebooted without the live DVD, the machine hung as described above.

When I rebooted with the live DVD, a "sudo fdisk -l" showed this:

```
ubuntu-studio@ubuntu-studio:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6eb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953519615   976508929    5  Extended
/dev/sda5          501760  1953519615   976508928   8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6eb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      499711      248832   83  Linux
/dev/sdb2          501758  1953519615   976508929    5  Extended
/dev/sdb5          501760  1953519615   976508928   8e  Linux LVM

Disk /dev/mapper/isw_cadjeebehd_Volume0: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6eb9

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cadjeebehd_Volume0p1   *        2048      499711      248832   83  Linux
/dev/mapper/isw_cadjeebehd_Volume0p2          501758  1953519615   976508929    5  Extended
/dev/mapper/isw_cadjeebehd_Volume0p5          501760  1953519615   976508928   8e  Linux LVM

Disk /dev/mapper/isw_cadjeebehd_Volume0p1: 254 MB, 254803968 bytes
255 heads, 63 sectors/track, 30 cylinders, total 497664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cadjeebehd_Volume0p1 doesn't contain a valid partition table
fdisk: unable to read /dev/mapper/isw_cadjeebehd_Volume0p2: Inappropriate ioctl for device

```

At this point I'm just looking for recommendations on the right to fix this.  I can start mucking about in fdisk, but if there's a cleaner/safer solution, I'd rather try that first.  Worst case, I can wipe the disks out and rebuild it without enabling RAID through the machine's BIOS, though I don't know if that will make LVM any happier.

---

