---
title: "installer damaged windows partitions"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by thosmos on 2007-06-14
I used the manual partition editor during install to delete one primary NTFS windows partition and replace it with an ext3 partition  (it was the 3rd of a 4 partition drive). I am very familiar with partitioning and I did not alter any other partition in any way.  I then installed lilo in that same partition (rather than the MBR for the disk).  Everything seemed to go fine in terms of the linux install, but when I booted into windows, the 2nd and 4th partitions were no longer visible to Windows XP Pro.  Disk Management, sees them and says they're healthy NTFS partitions, but calls them "Unkown Partitions" and won't let me mount them.  Also, interestingly, the linux partition appears as an NTFS partition.

Has this happened before and, if so, is there a known fix?

[IMG]http://thosmos.com/misc/untitled.JPG[/IMG]

T

---

### Post by dannyboy79 on 2007-06-14
well you deleted a partition and so your partition table changed and now windows verison of the partition table is bad (that's what I think anyway). you can try to use a tool called testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
I believe it's on the **gparted live cd ** along with partimage and gparted so it's a livecd that a user should have.

I can't tell you what to think about the ubuntu parititon looking like a ntfs partition, what does sudo fdisk -l
return frmo a live cd?

---

### Post by thosmos on 2007-06-15
THANKS!  That utility worked!  Its auto-scan found the partitions and showed me that the partition table backup was bad.  The partitions now show up in windows again.  I am going to back up everything (as I should have done before the install) and recreate them just in case.  (I should also probably have deleted the partition from windows first before creating it in the linux installer.)  

This is the first time that a partition repair tool worked for me.  I've paid for them in the past and none of them worked (at least for me), and all were harder to use than this one AND it's open source.  

T

---

### Post by dannyboy79 on 2007-06-15
i am glad I could help, you should really donate even the smallest amount to testdisk as he works hard for free and as you found out, his app is awesome!! This is the kind of success stories that need to be stickied.

---

