---
title: "Partitions Cloned, GParted Can't See Them"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by fischerville on 2010-03-29
I haven't seen this problem anywhere else after googling.

I recently cloned my Ubuntu installation (all partitions) to another hard disk using ddrescue (per [these instructions]("http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk"), using live Karmic CD)

After removing the old hard disk, i can boot Ubuntu no problem, but ALL partition software i have used reports that my entire disk is unformatted. All my devices are fine, and mount properly, but this is what i get from cfdisk:

FATAL ERROR: Bad Primary Partition 1: Partition Ends after End-of-Disk

and gparted simply reports 189 GiB of unallocated space.

This really weirds me out, since the partitions are clearly working fine, and have been for over a month. I'm assuming this is a problem with the partition table, but i don't know how to repair it.

For the record, here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b5f63290-d917-449d-895d-fbbce4424750 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=0bc72961-923e-42bc-960b-fc4b389368dd /home           ext3    relatime        0       2
# /dev/sda6
UUID=8a79e6e9-c195-4c1e-aef9-e911de590da0 /opt            ext3    relatime        0       2
# /dev/sda5
UUID=ce441377-1405-489b-ab53-de54dcb3c2ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=126,devmode=666 0 0

---

### Post by 2hot6ft2 on 2010-03-29
> **fischerville said:**
> 
FATAL ERROR: Bad Primary Partition 1: **Partition Ends after End-of-Disk**

Sounds to me like the source disk was larger than the destination disk.

---

### Post by Skaperen on 2010-03-29
Yes, sounds like that to me, too.  One partition is going to be truncated, and zero or more will be completely gone.

To the OP: please tell what this command outputs:```
fdisk -lu /dev/sda
```

---

### Post by fischerville on 2010-03-29
Entered 

fischer@buntu:~$ fdisk -lu sda
fischer@buntu:~$

No output at all. But you're right, the source disk was larger than the target disk. I knew that my home partition (last one on disk) would be truncated, but it wasn't full and i knew all the data would fit on the new disk. I assumed it would resize the partition to fit, but obviously it didn't. 

Any way to manually resize a partition that isn't recognized by cfdisk, gparted, or...??

Otherwise, if i reversed the procedure: backed up sda to sdb, with sdb being the original source disk, might that just solve the problem?

---

### Post by fischerville on 2010-03-29
Turns out Palimpset Disk Utility (by RedHat...?) kinda-sorta recognizes my partitions, although it's a little screwy.

Bear with me for a moment...

204 GB Hard Disk (actually, it's 190...)
 -> 10 GB Filesystem (mounted to root)
 -> 241 GB Filesystem (logical partition)
    -> 3.0 GB Swap Space
    -> 31 GB Filesystem (ext3)
    -> 138 GB Filesystem (ext3)
    -> 69 GB unallocated
 -> 18446744027 GB Free (yeah, i know...)

What i'm looking for is basically

10 GB root
3 GB swap
31 GB ext3
~146 GB ext3

and that's it...

---

### Post by oldfred on 2010-03-29
I think you need sudo to run the fdisk

This works for me:
fred@fred-desktop:~$ sudo fdisk -lu

---

### Post by fischerville on 2010-03-29
aha... sudo get me a sandwich, i mean... show me my partitions.


Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x771d4660

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    19535039     9767488+  83  Linux
/dev/sda2        19535040   490223474   235344217+   5  Extended
/dev/sda5        19535103    25398764     2931831   82  Linux swap / Solaris
/dev/sda6        25398828    86799194    30700183+  83  Linux
/dev/sda7        86799258   356305634   134753188+  83  Linux

---

### Post by fischerville on 2010-03-29
Would i be able to just resize the extended partition so that the upper end is the same as the end of sda7?

---

### Post by fischerville on 2010-03-30
Ok, problem solved.  Found [this post]("http://ubuntuforums.org/showthread.php?t=352723") which describes my problem almost exactly. 

First of all, for insurance, i did the process in reverse, backed up 190GB hd to 250GB hd and tested to make sure it would boot, etc.

Second, i booted to live CD and copied fdisk's description of my partition table to text editor. Then used fdisk to delete sda2 and then manually recreate the extended and logical partitions by entering the cylinder numbers. 

Shutdown, rebooted to 190GB HD and it worked fine. Also, now GParted and cfdisk recognize the thing.

Thanks for pointing me in the right direction(s).

---

