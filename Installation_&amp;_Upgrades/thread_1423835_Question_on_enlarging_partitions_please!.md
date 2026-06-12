---
title: "Question on enlarging partitions please!"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by listerdl on 2010-03-07
Hi, I have a dual boot windows and ubuntu.

If the windows has outgrown the size of the partition, can I slap in the gpartition and simply increase the allocated space?

Is it as simple as that?

Im obviously worried to upset the karma of the machine.....

---

### Post by SecretCode on 2010-03-07
It can be as simple as that ... but that can also cause you to lose all of your data on both OSes! Unlikely, but still you should not resize partitions without adequate backups. I would recommend Clonezilla for the backups.

If you have unallocated space on your disk adjacent to your windows partition, resizing it will be easy. If you don't, you'll have to move another partition, shrink another partition, or (probably) both.

And you probably meant 'gparted' not gpartition! Run it from a Live CD.

---

### Post by Mark Phelps on 2010-03-08
If you're running Windows XP, you should be able to use GParted to resize the Windows XP NTFS partition without problems.

If you're running Vista -- do not do that!  Instead, use the Vista Disk Management utility to shrink the OS partition, and then use GParted to resize the Linux partition.

---

