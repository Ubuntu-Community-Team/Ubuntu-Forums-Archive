---
title: "Resizing Ubuntu partitions"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by Tab on 2005-06-22
I've been trying to resize my partition and am running into some problems. As far as I know, QTParted should be able to do the job, however, when attempting to use it (either from Knoppix or [SystemRescueCD](http://www.sysresccd.org/)), the main ext3 partition is unresizable. Is there any way to fix this, or any other program that will work? Or is it impossible to do with the type of ext3 filesystem Ubuntu uses?

---

### Post by uidzer0org on 2005-06-22
try gparted

---

### Post by Tab on 2005-06-22
Nah, tried that even before QTParted. Same deal :\

---

### Post by mingus on 2005-06-23
[QUOTE=Tab]I've been trying to resize my partition and am running into some problems. As far as I know, QTParted should be able to do the job, however, when attempting to use it (either from Knoppix or [SystemRescueCD](http://www.sysresccd.org/)), the main ext3 partition is unresizable. Is there any way to fix this, or any other program that will work? Or is it impossible to do with the type of ext3 filesystem Ubuntu uses?[/QUOTE]

Not the filesystem.  (Ext3 is only one of several that Ubuntu can use.)

Some partitioners cannot resize, some cannot resize in certain situations, some will not resize when certain risks are detected.  And some partitions are not resizable.

Can you post back your disk partition table and fstab?

BTW, QTParted, GParted, Partman are all the same under the hood:  libparted.

---

### Post by Tab on 2005-06-23
hdb2 is the partition in question...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
**/dev/hdb2       /               ext3    defaults,errors=remount-ro,user_xattr 0       1**
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows/G  ntfs    umask=0222      0       0
/dev/hdb1       /media/windows/C  ntfs    umask=0222      0       0
/dev/sda2               /mnt/ipod               auto    noauto,user,rw 0 0

Output of fdisk -l is
> Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12161    97683201    7  HPFS/NTFS

Disk /dev/hdb: 40.9 GB, 40992473088 bytes
255 heads, 63 sectors/track, 4983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2089    16779861    7  HPFS/NTFS
**/dev/hdb2            2090        4861    22266090   83  Linux**
/dev/hdb3            4862        4983      979965    5  Extended
/dev/hdb5            4862        4983      979933+  82  Linux swap / Solaris


Output of parted /dev/hdb print:
> Disk geometry for /dev/hdb: 0.000-39093.468 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  16386.613  primary   ntfs        boot
**2      16386.614  38130.842  primary   ext3**
3      38130.842  39087.839  extended
5      38130.873  39087.839  logical   linux-swap

---

### Post by mingus on 2005-06-23
**VERY IMPORTANT:**

I did some additional checking about resizing an ext3 partition.  Parted claims to have this functionality, and at least on some occasions it works.  However, there are a number of posts on the web about parted also having problems doing so.  What is disturbing is that it is not clear why.  At one time it was a version issue, another time there was a bug reported and accepted but I don't  know if that was fixed.  There are also protective rules that may be in play (for example, sometimes a resize can be done but not if it requires changing the starting point of the partition, etc.) which are not well documented.  Theories for this problem include an inability to properly rebuild the journal, choking on file attributes, or problems matching the size of the filesystem with the partition.  

As an alternative, I found suggestions that the partition be converted from ext3 to ext2, which removes the journal, then resized, and then converted back to ext3.  The following link is from a RedHat 9 manual describing this approach.

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-filesystem-ext2-revert.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-filesystem-ext2-revert.html)

The following, while suggesting using Parted, also observes the versions and libraries issues.  It also suggests using PartitionMagic, and provides a manual procedure using fdisk and ext2resize which is the actual code that Parted is using to do the resizing.

[http://www.newsforge.com/os/03/10/07/2028234.shtml](http://www.newsforge.com/os/03/10/07/2028234.shtml)

I saw enough where I would be extremely nervous about using any Parted derivative to do this, at least not before doing a lot more research.  As it is, partitioning is a bit of a black art.

I would consider PartitionMagic.  If it indicates it cannot resize, then you're alternative will be to a procedure like RedHat's above, or to backup the partition, delete and recreate the partitions, and then restore from the backup.

You did not indicate what problem you are actually trying to solve with resizing.  There may be another approach that can get your desired result, other than resizing.  If you'd like to post that info back, there may be other suggestions possible.

---

### Post by Tab on 2005-06-23
Ah I see, thank you for the information. I may simply back up and recreate the partitions.

The reason for resizing is that I need to install FC4 alongside of Ubuntu, and so want to free about 10gb from hdb2.

---

### Post by mingus on 2005-06-23
[QUOTE=Tab]
The reason for resizing is that I need to install FC4 alongside of Ubuntu, and so want to free about 10gb from hdb2.[/QUOTE]

Right.  My only other thought would be to copy the ntfs data from hdb1 to that large hda1 and then reclaim hdb1 for FC4.

---

### Post by Tab on 2005-06-24
I wish I could, but hdb1 is where my WinXP installation resides. However, I might be able to move some things and squash that down to a bare-minimum, and then simply resize the ntfs filesystem. Then again, maybe it is time to get rid of that altogether...

Got a copy of Partition Magic, gonna try that first.

---

### Post by Tab on 2005-06-24
~_~
PartitionMagic says this regarding the ext3 volume: 
The version of the filesystem is not supported.
I can't resize.

Gonna go with moving files and resizing NTFS, I guess...

---

