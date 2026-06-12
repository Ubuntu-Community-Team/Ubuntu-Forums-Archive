---
title: "ubuntu installation on unallocated partition"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by cyb3r_defender on 2011-10-06
hi,
I had a dynamic disk and as I found ubuntu cannot get installed on dynamic disk , so i converted the disk to basic.
I already have 4 primary basic partitions + unallocated 59 GB partition reserved for ubuntu from before.

and now I neither can format this partition in ubuntu installation nor create new partition in windows , because widows says it must convert to dynamic , and I don't want it dynamic.

is there any solutions for this?
[IMG]http://i52.tinypic.com/fmnaiq.jpg[/IMG]

---

### Post by Quackers on 2011-10-06
The maximum number of primary partitions on any MBR partitioned disc is four.
If you try to create another Windows will insist on changing your partitions to dynamic disks.
You MUST delete a primary partition first. Then you can either create an extended partition in which you can have as many LOGICAL partitions as you want, or the Ubuntu installer will automatically create one for you.

---

