---
title: "Ubuntu installation alongside windows 10"
date: 2016-08-10
forum: Installation &amp; Upgrades
---

### Post by nimmi2 on 2016-08-10
When I am trying to install ubuntu alongside windows 10, the partition table does not show details of windows. It shows as entire hard disk is empty. I selected "something else" option for installation. How to solve this problem? Please help

---

### Post by yancek on 2016-08-10
If you have a pre-installed windows 10, then it almost certainly uses UEFI.  In that case, it would be a good idea to read the Ubuntu documentation on dual booting windows/Ubuntu with UEFI at the link below.[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Do you have any unallocated/free space on the drive on which to install Ubuntu?  If not, you need to shrink it using windows tools such as Disk Management.  After doing this, reboot windows and run chkdsk before trying to install Ubuntu.

---

### Post by ubfan1 on 2016-08-10
Also check that your machine is not using something called "dynamic partitions", which are not recognized by the Ubuntu installer.  Those type of partitions would need to be converted to 
"basic" type partitions first.

---

### Post by nimmi2 on 2016-08-21
Thank you

---

