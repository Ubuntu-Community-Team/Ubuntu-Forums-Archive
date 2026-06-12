---
title: "Problems Installing Ubuntu in an Extra NTSF Partition"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by jamesc1979 on 2007-05-21
I'm new to Ubuntu but have installed it on a couple computers.  I have always installed Ubuntu on an existing Windows XP partition containing the XP operating system.  This time I have an existing 50 Gig partiton (NTSF) on the same drive as the XP operating system.  Ubuntu Install keeps giving me errors installing within this partition. 

I keep getting hung up on the choose partition/ drive part (Step 3-I think) 
I have no info on the drive so can reformat it if needed.  The only reason it's even a partition is because Ubuntu wouldn't recognize the unpartitioned Space.
I really don't want to cut from the XP partition any smaller and I don't want to reinstall XP either.

What should I try next?

---

### Post by Xappe on 2007-05-21
If you want to have ubuntu use all of the space that's now the ntfs partition I would remove that one with gparted and choose to manually partition the drive during the ubuntu install.

When the partitioner loads, choose to manually partition the drive. Remove the ntfs partition and create three new partitions, one for / (root) (maybe ~ 10 GB or so), one for swap (~ 1 GB should be more than enough), and one for /home  (the remaining of the unpartitioned space).

Make sure to set the mountpoints for the new partitions.

---

### Post by shen-an-doah on 2007-05-21
Your problem is that Ubuntu won't install on an NTFS filesystem. You need to format it as ext3.

---

### Post by Yoooder on 2007-05-21
NTFS support in linux is still shaky, and can be very unstable (although it has gotten much better).

As already stated, you'll need to reformat the partition to a supported filesystem (ext2, ext3, xfs, reiserfs...).

If you would like to be able to access your linux partition from Windows, you might want to use the older ext2, as there are utilities/drivers that allow it to integrate with Windows XP quite well.

---

### Post by jamesc1979 on 2007-05-21
Thanks guys.... I will give it a try tomorrow.  I'll keep you up to date.

---

