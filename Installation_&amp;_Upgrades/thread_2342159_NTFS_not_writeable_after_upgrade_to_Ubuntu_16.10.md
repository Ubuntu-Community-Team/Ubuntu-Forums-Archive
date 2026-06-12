---
title: "NTFS not writeable after upgrade to Ubuntu 16.10"
date: 2016-11-04
forum: Installation &amp; Upgrades
---

### Post by TobyGK on 2016-11-04
After upgrading to Ubuntu 16.10 from 16.04 I can't write to any of my ntfs partitions. ntfs configuration tool tells me they are are writable and the properties - permissions tells me all users can 'create and delete files'. I can see all the partitions, read files and copy files from ntfs, but not write to ntfs. GParted shows them as locked (key icon).

I've tried uninstalling NTFS Configuration tool, installing and making all writable again. The ntfs configuration tool seem convinced I can read and write, but still I can only read.

Could it be a problem with the latest version of Nautilus?

---

### Post by TobyGK on 2016-11-04
OK, also now tried changing owner from root to user as admin using fstab. Properties - Permissions still say all users can 'Create and delete files', and I'm now the owner as well and can immediately try and change permissions. However, if I do attempt to change permissions (just as an experiment) there's an error message 'Error setting permissions: read only file system'. Yet ntfs configuration tool still insists that all the ntfs volumes are writable. What am I missing here? Has no one else come across this yet?

---

### Post by Impavidus on 2016-11-05
It's a read-only file system. Even if you have write permissions, it won't work, as the file system is mounted read-only. Maybe the file system is in an unclean state? It used to be that it refused to mount automatically, suggesting manually mounting read-only. Maybe that changed.

Boot Windows and run filesystem checks on the ntfs partitions. Make sure you shutdown Windows completely, unmounting all file systems. Linux can't mount ntfs partitions if Windows is (semi-)hibernated.

---

### Post by TobyGK on 2016-11-06
Phew, thanks for the reminder! Up and running again. Yes, I do have a dual (well sadly quad, really) boot machine.

I'm very familiar with that problem, but Windows must have reset the 'fast start-up' itself during a recent upgrade that coincided with my Ubuntu upgrade. Good old Windows.

Many thanks again.

---

### Post by slickymaster on 2016-11-06
*Thread moved to **Installation & Upgrades**.*

---

