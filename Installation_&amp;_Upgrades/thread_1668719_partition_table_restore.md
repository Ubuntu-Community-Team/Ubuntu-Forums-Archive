---
title: "partition table restore"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by mkzet on 2011-01-16
hi all this is my first post on this forum xD

Do i have any chances to restore my windows partition table after tried to install debian and i used the entire disk instead of the free space i had alocated for this

after i figured out what i did i stoped the installation but was to late ... i answered yes at write partition table changes on disk question


i tried win7 automate recovery tool from dvd and manual install of mbr with no successful result

---

### Post by srs5694 on 2011-01-17
The chances of your recovering a fully bootable Windows system are very close to 0. There's a chance you can recover some, but probably not all, of the individual files on the disk by using [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) or some similar tool. If you use PhotoRec, you'll probably have to sift through the files one by one to identify them and give them suitable names. You'll probably need another disk on which to store the recovered files; I'm not positive, but I don't think you can recover from and store to the same partition, and given your description, I doubt if you can safely create a partition for storing the recovered files on the damaged disk.

---

