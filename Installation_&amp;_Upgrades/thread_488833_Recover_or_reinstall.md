---
title: "Recover or reinstall?"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by Turner.kj on 2007-06-30
I was playing around by trying to install different packages and now my speaker on my laptop do not work.   Is there a way to go back to the original install configuration without doing a complete install?

If I need to do a reinstall, what is the best way for a dual boot?

---

### Post by Pumalite on 2007-06-30
Depends on what you are dual booting with. Give us more info.

---

### Post by sci-fi guy on 2007-06-30
I just know the reinstall method.  I suggest you wait to find out if recovery is possible, but if not...

If you are dual-booting with windows, open Disk Manager (in Windows-and I forget how, Google it) delete your non-windows partition(s) (the swap will be downgraded to free space, delete this also until it is designated as Unallocated), and run the LiveCD. While reinstalling, under the partitioning options there will be a selection to use the largest contiguous(sp?) free space on the drive. Select it and continue the install. I also recommend that you set up /home as a separate partition to prevent losing data in the future.

---

