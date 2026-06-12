---
title: "LVM issue with multiple disks...."
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by tabmow99 on 2010-11-11
Hi all,
    I have a system that has three 2TB drives in it, and i want to use LVM and put all the space together (it's just a backup server).   So I used Ubuntu 10.10 alternate disk to install with LVM.   When I did this, it chooses one of the three disks to install to, so the resulting install had LVM using one disk, with all the space allocated to / basically. 

Is there a way to install using the alternate disk that would use all 3 disks in one big space? Since I wasn't clear on the install option, i did try this:


[LIST]
[*]fdisk the two other drives (to create lvm partitions)
[*]pvcreate them
[*]vgextend the orig volume group
[*]lvextend it
[/LIST]
But once i did all that, lvdisplay shows the "LV Size" as being 6TB, but if i do a "df -h", it is still only 2TB.   Rebooting did nothing.

Any ideas or suggestions what i could do?
Thanks very much.

---

### Post by dino99 on 2010-11-11
watch the LVM installation guide

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

or here:
[https://wiki.edubuntu.org/Lvm](https://wiki.edubuntu.org/Lvm)

---

### Post by tabmow99 on 2010-11-23
Thanks!
I used this page: [https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

which came from one of your linked pages and the system works great now.
Thanks again.

---

