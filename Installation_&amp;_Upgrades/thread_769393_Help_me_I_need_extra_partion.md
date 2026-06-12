---
title: "Help me I need extra partion"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Enthrall on 2008-04-26
So I have a dual boot of vista and ubuntu hardy. But I only have 10 gigs for ubuntu and like 320 gb for windows. I would like to make a partion that I could  use to put both windows and ubuntu files in. What would be the best way to do this? What file system should I use?

---

### Post by dstew on 2008-04-26
You can shrink the Windows partition, and make your new partition out of the unallocated space. Use the Gnome Partition Editor to shrink the partition (back up and defragment first) and create the new one. Format the new partition with a NTFS file system, because both Windows and Linux can read and write to that.

---

### Post by Pumalite on 2008-04-26
You can use ntfs. Ubuntu reads/write to ntfs.

---

### Post by raul_ on 2008-04-26
I always say that for creating/editing partitions, the GParted Live CD is the best way to go.

About the filesystem, you can use fs-driver to read/write ext3 partitions in windows, and use ntfs-3g to read/write ntfs partitions on linux. FAT is supported by both OS's , so it's up to you to chose :)

---

