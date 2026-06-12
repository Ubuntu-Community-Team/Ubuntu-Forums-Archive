---
title: "formatting new drive"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by jasonsexton on 2007-03-14
I am running 64bit Ubuntu 6.10 on an AMD 64.  I have purchased an additional hard drive for storage only.  I have connected the drive to the motherboard and need to know  what the best procedure for initializing, formatting and mapping the drive for easy accessability.  I have installed gparted and I can see the drive but don't know what to do next.

---

### Post by Kateikyoushi on 2007-03-14
There is really nothing to it, just decide how many partitions you would like and their size. Then create partition(s) on the drive, format it, I recommend ext3 and then add it to fstab. If you need help with the latter show us the output of the next command.

```
sudo fdisk -l
```

---

