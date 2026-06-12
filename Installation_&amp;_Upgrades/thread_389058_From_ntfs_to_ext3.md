---
title: "From ntfs to ext3"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2007-03-20
I have just erased win2000 from a machine to just run Ubuntu. I have ntfs on two big hdd. I activated writing-rights on the ntfs-disk under Ubuntu and have moved files from one of the disks.
How do i the easiest way go from ntfs with ntfs-3g drives and make it to an ext3 partition?

I have some trouble, becourse gparted did't could format, and when it did, it didn not format everything and the disk did not get mounted after. I manage to fix it, but it's not that nice that i want it to be. For instance, I lost my UUID för the disk, so i edit fstab in classic manner, without UUID instead of /dev/hdb1. I wounder if I can find UUID for the disk, AND if there is some nice HOW-TO to go from ntfs to ext3?

Any tip would be nice.

/Azyx

---

### Post by Death_Sargent on 2007-03-20
Gparted (gnome partition manager) will convert partitions for you 

```
sudo apt-get install gparted
```

It will be under the system menu (one of the submmenus)

THIS IS NOT A RECOMENDED COURSE OF ACTION

converting partition formats is extremely dangerous for most partitions (ESPECIALLY NTFS) I recomend backing up your files and the reformating instead

---

### Post by louieb on 2007-03-20
To get the UUID 
```
ls -l /dev/disk/by-uuid/
```

---

### Post by Mr. C. on 2007-03-20
Do you have enough extra disk space to copy the files from your NTFS disk to some spare storage?  If so, you can create archives on another disk, reformat to ext3 and then unarchive.

MrC

---

