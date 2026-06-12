---
title: "duplicate UUID problem"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by moshuptrail on 2007-06-20
Long ago I cloned two partitions.  One was FAT32 and the other NTFS.
Now I am finding that the clone worked a little too well.  The partitions have duplicate UUIDs with the original source partitions!

So what's to do?

I know that uuidgen will generate a new UUID, but how can I apply it to one of the cloned partitions?  

I don't normally even mount the cloned partitions, but the duplicate UUID is confusing feisty at times.

There is a command to modify the UUID of an ext2 or ext3 partition:
tune2fs -U xxxxx

But it won't touch the FAT32 or NTFS partitions.  Any ideas?

another idea:  Could I re-clone and do it differently to get unique UUIDs?

---

