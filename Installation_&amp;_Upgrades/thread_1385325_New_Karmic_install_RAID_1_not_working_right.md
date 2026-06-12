---
title: "New Karmic install RAID 1 not working right"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by Robinmontreal on 2010-01-19
Hello all.. i just installed Karmic(64 bit) from CD, i installed with RAID 1.  After the first reboot, it complained that one disk was bad. It booted just fine... now i cannot tell which disk it is?

It's a simple install everything on / and 2 disks each 160 gig  sda1 and sdb1  but on Karmic, the raid info is different rather than see... (on another server)

md0 : active raid1 sdb1[1] sda1[0]
      154296192 blocks [2/2] [UU]

i see...

md0 : active raid1 dm-1[1]
      154296192 blocks [2/1] [_U]

What the heck? how do i tell which is what disk? I read somewhere that the raid name dm-1 is an alias to something else?

mdadm -D gives me

root@mx1:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Mon Jan 18 10:44:40 2010
     Raid Level : raid1
     Array Size : 154296192 (147.15 GiB 158.00 GB)
  Used Dev Size : 154296192 (147.15 GiB 158.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jan 19 12:35:40 2010
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 3b578ca2:eb30c314:fc0993d1:a94844e7
         Events : 0.8386

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1     252        1        1      active sync   /dev/block/252:1

mdadm.conf is simple...

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
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=3b578ca2:eb30c314:fc0993d1:a94844e7

# This file was auto-generated on Mon, 18 Jan 2010 10:49:26 -0500
# by mkconf $Id$

How do i tell which disk died? and how to tell mdadm to rebuild after i replace...?

Thanks...
Have a good one!
Rob
Montreal, Canada

---

### Post by Swab on 2010-01-20
Good question, anyone?

I guess you could unplug one of the disks, if it boots then you unplugged the bad one?

If you do cat /proc/partitions is it showing the partitions from both drives, or just the one?

---

### Post by Swab on 2010-01-20
And to recover I think you can do something like

mdadm /dev/md0 -a /dev/sda1

Where /dev/sda1 is the partition you created on the replacement disk.

---

### Post by goodmood on 2010-03-02
I have the same problem. Unfortunately system got no /dev/sd[ab][N] devices. Only /dev/sda & /dev/sdb AND no /dev/dm-1 or /dev/dm-0...
Another one detail. System stand on fakeRaid controller and got
ls -la /dev/mapper/*
crw-rw---- 1 root root  10, 60 2010-03-01 19:36 /dev/mapper/control
brw-rw---- 1 root disk 252,  0 2010-03-01 19:36 /dev/mapper/isw_icbaihidi_LEKHA_0
brw-rw---- 1 root disk 252,  1 2010-03-01 19:36 /dev/mapper/isw_icbaihidi_LEKHA_01

Question is how to repair RAID1 array.... :-(

---

