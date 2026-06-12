---
title: "Manual partition installation question"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by danielcork1 on 2011-08-04
Installing Ubuntu. The 'side by side' option didn't work (have windows 7 and want to run dual boot) so have to do the manual partitions option which I'm not terribly confident on.

Have watched a few tutorial videos, and think I know what I have to create (namely the Ubuntu and swap partitions, and a FAT32 if I want a common accessible folder) but 'add' is greyed out.

Do i need to 'create a new partition table'., Just worried because the dialog that comes up for that says that doing so will erase all existing partitions -- would that not wipe out Windows?

Screenshots linked below:
[https://picasaweb.google.com/lh/photo/E3FRf9HmpfWREN3Ugc-f3Q?feat=directlink](https://picasaweb.google.com/lh/photo/E3FRf9HmpfWREN3Ugc-f3Q?feat=directlink)
[https://picasaweb.google.com/lh/photo/Dxyi1dbhAyfiUlzPFSzmSg?feat=directlink](https://picasaweb.google.com/lh/photo/Dxyi1dbhAyfiUlzPFSzmSg?feat=directlink)

---

### Post by Basher101 on 2011-08-04
I can't look at your screens. Somewhat my Opera is not fully supported...anyway first and best thing before installing is to free up disk space from within Windows. This ensures you will have no issues from then on. If you free up around 40% of your disk space, you will get an option during installation: Install ubuntu aside windows. This does everything else automated. I can also tell you how to free it up from within Windows if you don't know.

---

### Post by karlson on 2011-08-04
> **danielcork1 said:**
> Installing Ubuntu. The 'side by side' option didn't work (have windows 7 and want to run dual boot) so have to do the manual partitions option which I'm not terribly confident on.


Relatively easy but not the point.

> 
Have watched a few tutorial videos, and think I know what I have to create (namely the Ubuntu and swap partitions, and a FAT32 if I want a common accessible folder) but 'add' is greyed out.


Question number one you need to ask before you create anything is: Do you have any free space on the disk?  Based on what I see from the screenshots you don't so no new partitions until you shrink your Windows Partition or get a different disk.

> 
Do i need to 'create a new partition table'., Just worried because the dialog that comes up for that says that doing so will erase all existing partitions -- would that not wipe out Windows?


Yes it will.

---

### Post by Basher101 on 2011-08-04
I was able to install ubuntu on a 10 GB big partition that i freed up from within windows. Only had to do a "custom install" during the installation process and mark my 10GB partition as / and that was pretty much it. Dual boot works like a charm.

---

### Post by danielcork1 on 2011-08-05
Great, it worked perfectly. Didn't think I'd manage the manual partitions but read a few other threads here and a few vids on YouTube and it came out fine (used a 2.6gb swap, hope that's big enough -- 4gb ram?).

Anyway, solution was shrinking the hard drive via windows and then just partitioning the space. Really very easy but it seems difficult.

It does seem a little sluggish, but I might be paranoid. Not very noticeable though.

Thanks for all the help guys. Probably could have let the automatic side-by-side installer do the work once I shrunk the windows' partition, but it was fun doing it the manual way, and a learning experience!

---

### Post by Basher101 on 2011-08-05
Just as i said, shrink from within windows and install. And thats all there is to it. Mark this as [SOLVED] as you got everything answered.
Regards

---

