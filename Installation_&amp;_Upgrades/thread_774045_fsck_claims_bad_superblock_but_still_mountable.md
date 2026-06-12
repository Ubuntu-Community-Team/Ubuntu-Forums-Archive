---
title: "fsck claims bad superblock but still mountable?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Maverickprowls on 2008-04-29
Have just installed HH, and now whilst booting my system I am dropped into the maintenance shell when fsck exits with error 8, saying that my reiserFS partitions have bad superblocks.  

This is what the log looks like:
> Log of fsck -C3 -R -A -a 
Tue Apr 29 13:22:33 2008

fsck 1.40.8 (13-Mar-2008)

reiserfs_open: the reiserfs superblock cannot be found on /dev/sdb1.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

Failed to open the device '/dev/sdb6': No such file or directory


Failed to open the device '/dev/hda1': No such file or directory



reiserfs_open: the reiserfs superblock cannot be found on /dev/sdb5.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

fsck died with exit status 8

Tue Apr 29 13:22:33 2008
----------------

Oddly enough, however, if I CTRL-D to exit the maintenance shell and continue to boot as normal, I am able to mount these partitions manually (i.e. by clicking on them) once my system has booted.

I have tried running fsck with the options specified in the log, but this also exits with an error message saying it does not recognise the switch "e".  I must confess to being a little lost here as I'm not used to working in the nuts and bolts of my system like this.

---

### Post by Pumalite on 2008-04-29
Maybe your fstab has the wrong UUID's?

---

### Post by Maverickprowls on 2008-04-29
Many thanks, your answer pointed me in the right direction.  I haven't updated the UUIDs of my partitions, largely because I never used them in the first place, but I certainly see the sense in them now.  

I looked at output of *mount* and discovered that the device designations of my drives had changed.  (i.e. what had previously been /dev/sdb1 had become /dev/sdc1 and so forth.)  I've altered **fstab** temporarily to reflect these changes, and I'm going to go through the process of adding UUIDs to **fstab** a little later once I'm confident what I'm doing.

Incidentally, for those looking to discover the UUIDs of their partitions, try ```
sudo vol_id /dev/sdXX
```or do as I did ```
sudo vol_id /dev/sdXX > dev_sdXX.txt
``` You can then copy and paste the UUIDs straight into **fstab**

---

