---
title: "Unable to mount raid."
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2020-04-26
I just did a clean install of ubuntu 20.04  on my system (I used to have 16.04).
My system has 4 harddrives:
/dev/sdb contains the system software (/boot and /).
/dev/sda contains the home directory of the only user.
/dev/md0 is a raid, with physical drives /dev/sdc and /dev/sdd.

I can no longer mount the raid device.   Where is the information stored that tells the OS that /dev/sdc and /dev/sdd are a raid?
Since installation, I booted from a clone of /dev/sdb before the upgrade, and the raid mounts properly.

---

### Post by TheFu on 2020-04-26
Start by posting the output from **sudo fdisk -l** please.

Really hope you have partitions for the RAID devices. Makes things easier when a new disk is needed. It is a best practice to always use partitions.

Also, seeing some **mdadm  --examine** command output (w/ the exact command used) would help the next person help you.

---

### Post by lvm on 2020-04-26
Copying /etc/mdadm/mdadm.conf from the old system should probably help. If not, provide the contents of /proc/mdstat file.

---

### Post by asb3 on 2020-04-26
I di copy  /etc/mdadm/mdadm.conf to the new system:
> cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Mon, 10 Aug 2015 11:10:10 -0400
# by mkconf $Id$
****************************************************************************************************************************************
> cat /proc/mdstat
Personalities : 
unused devices: <none>
*******************************************************************************************************************************************
mdadm was not installed.
I installed it.

I set up the raid five years ago and I don't remember the command I used.
*************************************************************************************************************************************
> sudo fdisk -l
[sudo] password for asb: 
Disk /dev/loop0: 54.97 MiB, 57614336 bytes, 112528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 242.43 MiB, 254193664 bytes, 496472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 240.82 MiB, 252493824 bytes, 493152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 27.9 MiB, 28405760 bytes, 55480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 223.58 GiB, 240057409536 bytes, 468862128 sectors
Disk model: INTEL SSDSC2CT24
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000dabe3

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 468860927 468359170 223.3G  5 Extended
/dev/sda5       501760 468860927 468359168 223.3G 8e Linux LVM


Disk /dev/sdb: 59.64 GiB, 64023257088 bytes, 125045424 sectors
Disk model: SanDisk SDSSDHP0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd9b722b8

Device     Boot   Start       End   Sectors  Size Id Type
/dev/sdb1  *       2048   1050623   1048576  512M  b W95 FAT32
/dev/sdb2       1052670 125044735 123992066 59.1G  5 Extended
/dev/sdb5       1052672 125044735 123992064 59.1G 8e Linux LVM


Disk /dev/mapper/ubuntu-root: 191.65 GiB, 205764165632 bytes, 401883136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu-swap_1: 31.71 GiB, 34032582656 bytes, 66469888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/vgubuntu-root: 58.17 GiB, 62453186560 bytes, 121978880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/vgubuntu-swap_1: 980 MiB, 1027604480 bytes, 2007040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdc: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Hitachi HDS72202
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F2B51AA8-F71D-11E4-8D46-B8AC6F1C635D

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 3907028991 3907026944  1.8T Linux filesystem


Disk /dev/sdd: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Hitachi HDS72202
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000c326c

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 3907028991 3907026944  1.8T 83 Linux

---

### Post by asb3 on 2020-04-26
After installing mdadm I rebooted, and the raid was properly mounted.

---

### Post by TheFu on 2020-04-26
Very happy it was something simple that was going to be discovered quickly.  i've hit a few of those with fresh 20.04 installs the last few days too.

---

