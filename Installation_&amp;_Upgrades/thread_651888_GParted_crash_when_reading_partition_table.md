---
title: "GParted crash when reading partition table"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by ascendant on 2007-12-28
The last post in [this ]("http://ubuntuforums.org/showthread.php?t=519130&page=3") thread is my problem.

I am using the desktop i386 7.10 live CD to install Ubuntu, and the installer shows no partitions on the disk.  Here is the output of fdisk -l

```
Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bf1b490

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *         395        7183    54532642+   7  HPFS/NTFS
/dev/hdd2               2        9712    78003607+   5  Extended
/dev/hdd3            9713        9729      136552+  83  Linux
/dev/hdd5               2         263     2104483+   7  HPFS/NTFS
/dev/hdd6             264         394     1052226   83  Linux
/dev/hdd7            7184        8097     7341673+  83  Linux
/dev/hdd8            8098        9712    12972456   83  Linux

Partition table entries are not in disk order
```
The partitions are physically on the disk as so:
[COLOR="Lime"][[/COLOR][COLOR="Blue"](logical)[/COLOR] linux swap] - extended partition starts with this logical partition
[[COLOR="Blue"](logical)[/COLOR] windows swap]
[[COLOR="Red"](primary)[/COLOR] windows]
[[COLOR="Blue"](logical)[/COLOR] /]
[[COLOR="Blue"](logical)[/COLOR] /home[COLOR="Lime"]][/COLOR] - extended partition ends here
[[COLOR="Red"](primary)[/COLOR] /boot] (even though fdisk says windows has the boot flag, it's actually on this partition:confused:)
GParted shows no partitions and crashes with a segfault when I refresh. It notes "Can't have overlapping partitions."

It seems that to get Ubuntu to install, I need to do one of a few things: 
Re-order the partitions on the hard drive to put all of the logical partitions in a contiguous space.  I think it would be too easy to lose partitions this way.
Edit some part of the partition table so that there are two extended partitions - one for the first pair and one for the second.
Take the easy way out and convert the two swap partitions to primary.  I'd still be within the limit of 4 primary partitions, but why do this when I can learn something cool in the second option?

So, does anyone know of a tool that lets me do the second option? Can I even have two extended partitions?
If anyone is curious, I used Acronis Disk Director to set up the layout.  I used the Ranish Partition Manager (on the UBCD) to set the boot flag.  It complained that the partitions overlapped too, but the setup works fine.

---

### Post by ascendant on 2007-12-29
I re-ordered the partitions so that all of the logical partitions were at the beginning of the drive.  
You cannot have more than one extended partition.  
Your extended partition counts as one of your four primary partitions.

---

