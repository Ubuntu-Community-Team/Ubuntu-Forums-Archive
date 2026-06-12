---
title: "Mixing File Systems"
date: 2006-04-28
forum: Installation &amp; Upgrades
---

### Post by Sef on 2006-04-28
When using more than one distro is it ok to mix file systems: Feather Linux on ext3, Ubuntu on reiserfs, and Alt Linux on XFS?

---

### Post by manicka on 2006-04-28
They are all different partitions so it shouldn't be a problem. It's no different to running ntfs and fat32 partitions as well.

---

### Post by Sef on 2006-04-28
Thank you.  I thought it would be ok, but wanted to check first.

---

### Post by Nzer24 on 2008-01-06
Yes, but what about mixing filesystems within one distribution on different partitions? Ex. /boot = ext3, /home = reiserfs, etc.

---

### Post by gruss on 2008-01-06
I'm far from a pro but I have and ext2 /home, ext3 /root, fat32  and NTFS all playing nice together. I dont see why what you want to do wouldnt work

---

### Post by kellemes on 2008-01-06
Works fine..
I have a triple boot with ext2, ext3, reiser, NTFS and FAT32.

For some reason though.. The Ubuntu installer can't handle ext2 formatted /boot-partitions, it just dies.

---

