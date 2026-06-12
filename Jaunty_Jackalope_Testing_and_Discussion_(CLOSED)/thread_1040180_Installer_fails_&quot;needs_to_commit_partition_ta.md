---
title: "Installer fails &quot;needs to commit partition table change&quot;"
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-01-15
Today's build 20090115 fails.  On manual partitioning, installer says it needs to "commit changes to the partition table" and will not do it because there is a partition mounted other than the one it is installing to.  Installer shouldn't change any other partition!

What's the change the installer wants to do?  I didn't ask for a resize, or a move, or a new, or a delete.  Just a format and mount point /.

Format shouldn't change the partition table?  gparted can format a partition with other partitions mounted, what's the problem with the installer doing the same?

Mount point shouldn't change the partition table?  Especially any other partition than the one being installed to?

Previous CD Live did not have this problem.  The build is oversize, won't fit on a CD, so I'm booting the CD image from another partition and of course that partition is mounted.

Appreciate a fix so I can test the new build.  

Launchpad bug is #313452.

Thanks, Jerry

---

### Post by Archmage on 2009-01-15
I think it would work if you us a USB-stick or DVD. But I think that a CD should also work, because they seems to be only slightly larger than the normal CD. Try overburning.

---

### Post by jerrylamos on 2009-01-15
> **Archmage said:**
> I think it would work if you us a USB-stick or DVD. But I think that a CD should also work, because they seems to be only slightly larger than the normal CD. Try overburning.

An Alpha a couple generations ago re-wrote the partition tables on both hard drives when it was supposed to be just installing in an existing partition.  Lost everything.  Yes, it was a test system, and I did have backups.  That took a while but didn't lose any valuable data.

What assurance is there that the current installer isn't trying to do the same thing, re-write the whole partition table when all it is supposed to do is format an existing partition and set a mount point?

Thanks, Jerry

---

