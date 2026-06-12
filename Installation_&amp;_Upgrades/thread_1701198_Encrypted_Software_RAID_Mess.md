---
title: "Encrypted Software RAID Mess"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by ta2 on 2011-03-06
Here's my system:

1x160GB drive
4x2TB drive

I want to install the OS on the 160GB drive with full disk encryption. I also want software RAID5 on the 4 2TB drives, and on top of that I also want full disk encryption (as a data drive, there should be no waste such as super-user reserved space).

Currently I have my 160GB drive set up properly (I think). It has an unencrypted boot partition, then asks for the encyption password before it can boot the OS. I also have the 4x2TB drives correctly configured in software RAID5, but I need to set up full-disk encryption on that. Unfortunately I think there are some serious problems somewhere:

I can't use cfdisk:

> FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder
                            Press any key to exit cfdiskHere's the output of fdisk -l:

> Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000103a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006ac51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093921

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       19458   156039169    5  Extended
/dev/sda5              32       19458   156039168   83  Linux

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c0785

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002f078

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/dm-0: 159.8 GB, 159783055360 bytes
255 heads, 63 sectors/track, 19425 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 157.8 GB, 157793910784 bytes
255 heads, 63 sectors/track, 19184 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 1988 MB, 1988100096 bytes
255 heads, 63 sectors/track, 241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/md127: 6001.2 GB, 6001183948800 bytes
2 heads, 4 sectors/track, 1465132800 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x08040000

Disk /dev/md127 doesn't contain a valid partition table


---

### Post by YesWeCan on 2011-03-06
Would you please post the outputs of:
cat /proc/mdstat
sudo mdadm --detail /dev/md127
sudo blkid
cat /etc/mdadm/mdadm.conf

---

### Post by ta2 on 2011-03-06
> **YesWeCan said:**
> Would you please post the outputs of:
cat /proc/mdstat
sudo mdadm --detail /dev/md127
sudo blkid
cat /etc/mdadm/mdadm.conf

**cat /proc/mdstat**
> Personalities : [raid6] [raid5] [raid4] 
md127 : active raid5 sde1[0] sdb1[4] sdc1[2] sdd1[1]
      5860531200 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

unused devices: <none>

**mdadm --detail /dev/md127**
> /dev/md127:
        Version : 1.2
  Creation Time : Sat Mar  5 18:33:14 2011
     Raid Level : raid5
     Array Size : 5860531200 (5589.04 GiB 6001.18 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Sun Mar  6 07:47:47 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : :New RAID Array
           UUID : 8778299d:352d5e1c:9f8b3cf2:0276cc5b
         Events : 18812

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       49        1      active sync   /dev/sdd1
       2       8       33        2      active sync   /dev/sdc1
       4       8       17        3      active sync   /dev/sdb1
[B]
blkid[/B]
> /dev/sda1: UUID="616365df-7c3b-486f-9c04-f6842f732f53" TYPE="ext2" 
/dev/sda5: UUID="fcf53170-17ae-431d-ac73-104ccffc2459" TYPE="crypto_LUKS" 
/dev/sdb1: UUID="8778299d-352d-5e1c-9f8b-3cf20276cc5b" LABEL=":New RAID Array" TYPE="linux_raid_member" 
/dev/sdc1: UUID="8778299d-352d-5e1c-9f8b-3cf20276cc5b" LABEL=":New RAID Array" TYPE="linux_raid_member" 
/dev/sdd1: UUID="8778299d-352d-5e1c-9f8b-3cf20276cc5b" LABEL=":New RAID Array" TYPE="linux_raid_member" 
/dev/sde1: UUID="8778299d-352d-5e1c-9f8b-3cf20276cc5b" LABEL=":New RAID Array" TYPE="linux_raid_member" 
/dev/mapper/sdf5_crypt: UUID="FEVGIE-Q0sr-1man-Ftoi-13BY-hx0g-4rEHNs" TYPE="LVM2_member" 
/dev/mapper/ariel-root: UUID="1886d322-2b91-4496-81a8-d6862c37174d" TYPE="ext4" 
/dev/mapper/ariel-swap_1: UUID="cb215be8-7c45-452e-83d8-8038128e75bf" TYPE="swap" 
/dev/md127: UUID="2e6c2dc4-96f4-431d-9386-c7aab806ecbe" TYPE="crypto_LUKS"

**cat /etc/mdadm/mdadm.conf **
> # mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sat, 05 Mar 2011 18:26:22 +0000
# by mkconf 3.1.4-1+8efb9d1

Thanks!

---

### Post by YesWeCan on 2011-03-06
I'd put an ARRAY statement in mdadm.conf for good measure but apart from that it looks ok.

What is the problem, exactly? What was the cfdisk command that gave you the error?

---

### Post by ta2 on 2011-03-06
> **YesWeCan said:**
> I'd put an ARRAY statement in mdadm.conf for good measure but apart from that it looks ok.

What is the problem, exactly? What was the cfdisk command that gave you the error?

Simply "cfdisk" by itself. I was following [this tutorial]("https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt") until this part:

> Disk partitions are created using: 
 # cfdisk
This will display a graphical interface for creating disk partitions. 


---

