---
title: "HOWTO mount a NWFS partition"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by vimas on 2006-06-27
We use Ubuntu as backup server and it holds virtual disk images containing ext3, FAT32, NTFS and NWFS. 
If we need to restore a file, we want to mount and export a disk image on our Ubuntu v5.10 backup server.  While this works fine for ext3, FAT32 and NTFS partitions, we fail to mount NWFS-386 partitions.

ncpmount is a utility that gives access to Netware filesystems on a remote server but my filesystem is local and listening on /dev/ndb0.

Any idea how I could get this solved?

---

### Post by vimas on 2006-06-27
Found sources on [http://developer.novell.com/wiki/index.php/Special:Downloads/nwfs-lw](http://developer.novell.com/wiki/index.php/Special:Downloads/nwfs-lw)

But build fails ...

---

