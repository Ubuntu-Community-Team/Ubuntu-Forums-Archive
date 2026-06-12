---
title: "dapper-install corrupts luks-partition"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by tschaboo on 2006-06-01
when installing dapper from the live-cd i chose "manual partitioning" and didn't do any changes there, since i already had a partition reserved for dapper. in the screen afterwards i deselected all filesystems except

/dev/hda1 - /boot - no reformat - ext2
/dev/hda5 - swap - reformat - swap
/dev/hda7 - / - reformat - ext3

when booting into the new installation i saw fsck complaining something about superblocks on /dev/hda9 and started fixing (!?!) the partition. i ran towards the reset-button of my pc knowing that it's a LUKS-partition and fsck can't know what to do! ]

back in breezy - after correct cryptsetup-mapping - fsck confirmed errors:

```
root@breezy:~# fsck -f /dev/mapper/crypt-hda9
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Pass 1: Checking inodes, blocks, and sizes
Inode 12673 is in use, but has dtime set.  Fix<y>? no


Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Inode 12673 (...) has invalid mode (00).
Clear<y>? yes

Pass 5: Checking group summary information
Free inodes count wrong for group #0 (16374, counted=16373).
Fix<y>? no

Free inodes count wrong (9617329, counted=9617328).
Fix<y>? no


/dev/mapper/crypt-hda9: ***** FILE SYSTEM WAS MODIFIED *****

/dev/mapper/crypt-hda9: ********** WARNING: Filesystem still has errors **********

/dev/mapper/crypt-hda9: 79/9617408 files (36.7% non-contiguous), 2948805/19221635 blocks

```

it seem's like the filesystem could be repaired (of course, i answered with "yes" in fsck later) although i don't know if any files are corrupt!

back in breezy i could also see that there are the partitions in fstab that i'm 100% sure i removed the mountpoints and the partitions themselves in the screen after partitioning when installing!

```
root@breezy:~# cat /mnt/hda7/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext2    defaults        0       2
/dev/hda8       /media/hda8     ext3    defaults        0       2
/dev/hda9       /media/hda9     ext3    defaults        0       2
/dev/hdb1       /media/hdb1     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

that was not the only problem i ran into installing dapper until the first boot (this [bug]("https://launchpad.net/bugs/41925") was never fixed and i had to use vga=771 at live-cd-boot to get my TFT working (was saying "unsupported input" even with VGA-failsafe-option enabled) but this one seems to be **really** serious!

---

### Post by tschaboo on 2006-06-02
since i could reproduce the problem by trying to install a second time, i filed a [bug report]("https://launchpad.net/distros/ubuntu/+bug/48137")

would be nice if someone would look at this problem.

---

