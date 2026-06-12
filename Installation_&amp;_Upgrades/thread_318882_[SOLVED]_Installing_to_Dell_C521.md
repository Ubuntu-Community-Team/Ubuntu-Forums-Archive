---
title: "[SOLVED] Installing to Dell C521"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by Hopalong on 2006-12-14
the Dell comes with a partition for the installed Windows XP and a logical one for the rest of the disk. Partition Magic says that one or more of these is not movable. I've managed to put a 5 gig one (F) into the logical. I've downloaded a disk (Ubuntu 6.10): it had one RAR .ISO file.  I've burned that on to a bootable CD. Now what?  The CD will boot - into RDOS, but there's no sign of Linux.](*,)

16th Dec. Some progress. Took an 'alternate' distro of 6.06 and have now got a successful 'live disk'. Two questions now: how do I convert this into a hard disk installation in a partition (the partition's there - 5GB - as F). Two I need to boot with noapic; what's this all about?  :???:

---

### Post by Sef on 2006-12-15
> Partition Magic says that one or more of these is not movable.

PM and Linux tend not to get along well.   If you want to partition before installing, then use [GParted]("http://gparted.sourceforge.net/livecd.php").  An older version is on the install disk.  

1) > it had one RAR .ISO file. I've burned that on to a bootable CD. Now what? The CD will boot - into RDOS, but there's no sign of Linux.


Did you burn it to the disk as an .iso?

2) Did you do an md5sum of the download?

---

