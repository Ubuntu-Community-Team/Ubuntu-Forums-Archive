---
title: "ReiserFS to ext4"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by rykel on 2010-01-16
Hi,

Now that even Google is moving to ext4, I am more convinced than ever about the power of ext4!

I have an existing system with all my data on a ReiserFS hard disk, and would like a safe upgrade to ext4. I do NOT have any external hard disk or other partition.

Please advise?

---

### Post by falconindy on 2010-01-17
> **rykel said:**
> Hi,

Now that even Google is moving to ext4, I am more convinced than ever about the power of ext4!

I have an existing system with all my data on a ReiserFS hard disk, and would like a safe upgrade to ext4. I do NOT have any external hard disk or other partition.

Please advise?
Depending on the size of the hard drive and how much data you want to backup, you could do the following...

1) Resize your filesystem using resize_reiserfs to free enough room so that you can backup your data.
2) Use parted, fdisk or gparted to shrink the partition (be sure not to shrink the partition more than the shrank the FS!)
3) Format this new partition and move your data there.
4) Reformat the old root Ext4, and move your data back
5) Delete the temporary partition
6) Expand the new Ext4 partition to fill the disk

Of course, it would be far easier to either:
1) buy some extra storage to do an external backup or...
2) backup mission critical online somewhere (something like dropbox gives 2gb free) and reformat/reinstall

---

