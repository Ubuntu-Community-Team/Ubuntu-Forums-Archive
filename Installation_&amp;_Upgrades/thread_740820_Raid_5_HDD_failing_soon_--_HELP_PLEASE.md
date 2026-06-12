---
title: "Raid 5 HDD failing soon -- HELP PLEASE"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by Vati-Khan on 2008-03-31
Hi I need some help as my current Raid 5 seems to be failing soon

according to smartctl my disc /dev/sdb will fail soon - no surprise there as it has been behaving strangely anyway. has had many readerrors in the past weeks, but the raid always managed to recover 

```
cat /proc/mdstat gives

Personalities : [raid1] [raid6] [raid5] [raid4]
md1 : active raid5 sda2[0] sdc2[2] sdb2[1]
      976189568 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md0 : active raid1 sda1[0] sdc1[2] sdb1[1]
      289024 blocks [3/3] [UUU]

```

and 

```
 cat /etc/mdadm/mdadm.conf
# mdadm.conf
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
# MAILADDR bla@bla.com
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=3 UUID=2d8b0dc4:172ec6ea:58fb2bbb:6ac40426
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=20c985ae:0a43a895:6f1358d9:fab1aff6

# This file was auto-generated on Sun, 03 Feb 2008 18:23:44 +0000
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

```

so I went to get a new disc (of the same type/size...)

what should I do now as I want to replace the disc before it's failing completely (just one month of warranty left)

**can I just copy the fdisk Partitions?** - like dd -if=/dev/sdb of=/dev/sdd or should I add the new disk as hot spare?
**what about the LVM stuff (dev/md1 is an LVM partition with multiple logical lvm volumes)**
```
lvmdiskscan -l
  WARNING: only considering LVM devices
  /dev/md1   [      930,97 GB] LVM physical volume
  0 LVM physical volume whole disks
  1 LVM physical volume

```

**so please give me some kind of best practice or expert advice and the necessary commands if you know them by heart.**

any help appreciated

thx
HS

---

