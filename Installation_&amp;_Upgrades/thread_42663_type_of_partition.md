---
title: "type of partition"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by Tonglebeak on 2005-06-18
What should ubuntu's partition type be: Linux Ext2, or Linux Ext3?

---

### Post by GTvulse on 2005-06-18
First off, you are referring to filesystem type, not partition type...

The business of choosing a filesystem is a mix of technical need and religious commitment. That is, in the end it is a decision based on a bit of hearsay and lots of misplaced gut feeling :-)

ext2 is the oldest standing filesystem used by the Linux kernel. And it shows: it is solid and reliable. ext3 is a journaling filesystem built on top of EXT2. It has all the goodness of ext2 and adds the abitlity to do fast crash recovery with minimal data loss. It is slower than, say, reiserfs or xfs when using its default settings because in "data ordered" mode it queues both data and metadata into the journal log before writing the data into the actual filesystem. ReiserFS and XFS are a lot faster, because they only log metadata in the journal. This has a major disadvantage: you may be able to recover the filesystem after a crash, but you will probably lose the data that was written to the disk at that moment. With EXT3 you have a high chance of recovering both.

ext3 is **sloooowwww** when searching the directory tree. But if you activate the [dir_index feature](http://ubuntuforums.org/showthread.php?t=37806&highlight=tune2fs) , you will speed it up noticeably. I perceive no practical difference using  ext3 with dir_tree active or reiserfs in a 7200 RPM hard disk. If using a slower disk (like my older 4500 RPM slave disk) Reiserfs will be faster.

---

### Post by mohaham on 2005-06-18
ext2 is recommended for boot partition (If you have one)
ext3 and reiserfs for / (root) partition

---

### Post by irusun on 2005-06-18
[QUOTE=Tonglebeak]What should ubuntu's partition type be: Linux Ext2, or Linux Ext3?[/QUOTE]
Use Ext3 which is a modernized version of Ext2 and has become the new standard over the last couple of years.  It's pretty much Ext2 with journaling.

---

### Post by rider343 on 2005-06-18
I prefer reiserfs or xfs... but xfs have problems on some machines

---

### Post by byen on 2005-06-18
yup..agree with irusun....ext3!!! it is.

---

