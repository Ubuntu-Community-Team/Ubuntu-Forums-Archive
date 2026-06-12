---
title: "How to dual boot Ubuntu 12.04 with Windows 7?"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by Chris . on 2012-08-09
Hello guys!
I have Ubuntu 12.04 and i'd like to dual boot it with Windows 7.
I need to have Windows 7 burned on a disc or on a memory stick, right?

But what do i do then?
Can anyone give me a full tutorial about this, i don't wanna mess this up.
Thanks!

---

### Post by Frogs Hair on 2012-08-09
Backup important Windows files for sure . You don't have to remove Windows to dual boot and you will want to create a system repair/recovery disk make sure you have the Win 7 product key also.
 
I dual boot and have not installed on a factory partitioned hard drive, but it is covered in the community documentation. You will need to find out if your computer has a recovery partition on the hard drive before proceeding. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2012-08-09
Windows has to have a primary NTFS partition with the boot flag. Windows 7 will install to one partition if created in advance. If installing to unallocated space it will want to create two partitions, one a hidden 100MB boot/repair and the main install. The separate boot partition is primarily so you can get to the repair console even when the main partition has issues or to encrypt your main install. Better to have repair CD anyway and if not encrypting then installing to one partition works just fine.

---

### Post by Mark Phelps on 2012-08-09
In my experience, Win7 works best when installed to a partition it formatted.  So, I would suggest the following:
1) Boot from Ubuntu LiveCD (or LiveUSB) and use GParted to shrink down the partitions you have to make room for Win7.  Would recommend 50GB of space.
2) Use Gparted to create and format a new NTFS partition.  This will prevent the Win7 installer from creating TWO partitions.
3) Boot into the Win7 install DVD, select the partition you created and use the option to FORMAT it during install.  This will reformat the same partition and will avoid file system problems by doing that.

---

