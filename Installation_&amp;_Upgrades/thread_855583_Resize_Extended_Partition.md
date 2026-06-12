---
title: "Resize Extended Partition"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Akash Singhal on 2008-07-10
I have Ubuntu on an extended partition and Windows on a primary partition.
I want to reduce the size of the extended partition and merge that space with the primary partition. I even deleted the extended partition but that free space was of no use.. I was unable to merge that with the primary partition. 
What should I do..I presently have Gparted installed in my extended partition.
Thanks in advance

---

### Post by Pumalite on 2008-07-10
Get Gparted Live CD and work on your partitions:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by SkonesMickLoud on 2008-07-10
Is your unallocated space in front of (in a gui, this would be to the left) the partition you want to add it to?

If so, no can do.  Partitions can only be grown from the end, not from the beginning.

---

### Post by logos34 on 2008-07-10
> **SkonesMickLoud said:**
> Partitions can only be grown from the end, not from the beginning.

Not true.  Gparted (>0.2.6) can handle it.  The version on the gutsy live cd is 0.3.5.  (latest Gparted live cd 0.3.7)

---

### Post by kahping on 2008-07-15
> **logos34 said:**
> Not true.  Gparted (>0.2.6) can handle it.  The version on the gutsy live cd is 0.3.5.  (latest Gparted live cd 0.3.7)

Indeed it can be done, but a word of caution: it can be very slow depending on the partition size :(

I'm resizing my /home partition from Hardy LiveCD as i type this and it's taking about 6hrs do resize a 74GB partition to 104GB. If you resize to the front of the partition, it looks like Gparted will move the partition first then resize

Individually performing a partition move first, _then_ growing it from the end may end up faster but I haven't tried this

*sigh* 3.5hrs to go. can't even cancel for fear of losing my files :(

---

### Post by sandysandy on 2008-07-15
post a snapshot from gparted showing the partitions.

regards

---

### Post by kahping on 2008-07-15
Here's a screen capture

---

