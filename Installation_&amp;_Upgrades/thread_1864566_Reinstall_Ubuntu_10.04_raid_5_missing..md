---
title: "Reinstall Ubuntu 10.04 raid 5 missing."
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by e-zoli on 2011-10-19
I had a working Ubuntu 11.10 with raid 5 (4* 2Tb), but I had to reinstall it, and I went with version 10.04.

Now my raid 5: "Not running, partially assemled"

If I run *sudo mdadm --assemble --scan -f *it is working again but only with 3 drivers.

After restart I had to run again* sudo mdadm --assemble --scan -f *in order to see my files.

This what I have after restart:

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
``````
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
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/RAID-5 level=raid5 metadata=1.2 num-devices=4
UUID=f326d7c7:a015ac79:e1d39d54:3d41314e name=:RAID-5

# This file was auto-generated on Tue, 18 Oct 2011 22:52:19 +0200
# by mkconf $Id$
``````
sudo sfdisk -luS

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util
sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             1 3907029167 3907029167  ee  GPT
                start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util
sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 243201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1             1 3907029167 3907029167  ee  GPT
                start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util
sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 243201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1             1 3907029167 3907029167  ee  GPT
                start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sdd2             0         -          0   0  Empty
/dev/sdd3             0         -          0   0  Empty
/dev/sdd4             0         -          0   0  Empty

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util
sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 243201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1             1 3907029167 3907029167  ee  GPT
                start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty

Disk /dev/sde: 48641 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sde1   *      2048 769345535  769343488  83  Linux
/dev/sde2     769347582 781422591   12075010   5  Extended
/dev/sde3             0         -          0   0  Empty
/dev/sde4             0         -          0   0  Empty
/dev/sde5     769347584 781422591   12075008  82  Linux swap / Solaris
```How can I solve this?
Thanks!

---

