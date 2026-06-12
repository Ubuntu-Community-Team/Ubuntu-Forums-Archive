---
title: "Install 12 LTS on a used disk"
date: 2015-08-06
forum: Installation &amp; Upgrades
---

### Post by SAM9030 on 2015-08-06
I'm trying to install 12 LTS on a previously used disk.  I am unable to delete the partitions with the install CD/USB.  I thought there was a command to jump to a screen to execute commands to fdisk etc. Can some one point me in the right direction?

---

### Post by mörgæs on 2015-08-06
Only in a few rare instances there is a reason for using 12.* . The general recommendation is the later releases like 14.04.3 or 15.04.

If you want a disk completely erased you could run it over with Killdisk or Dareks Boot and Nuke.

---

### Post by yancek on 2015-08-06
You should have GParted on the install disk so try that and make sure none of the partitions you want to delete are mounted.  There is an option to umount partitions in GParted.

---

