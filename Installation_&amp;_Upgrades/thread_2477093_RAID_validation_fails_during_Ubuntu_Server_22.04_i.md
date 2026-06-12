---
title: "RAID validation fails during Ubuntu Server 22.04 installation"
date: 2022-07-14
forum: Installation &amp; Upgrades
---

### Post by f-bastianello on 2022-07-14
[COLOR=#232629][FONT=-apple-system]I've followed [/FONT][/COLOR][Install Ubuntu 20.04 Focal Fossa with RAID 1 on two devices]("https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices")[COLOR=#232629][FONT=-apple-system] t[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]o set up RAID 1 during the installation of Ubuntu Server 22.04, yet installation always fails with a RAID validation error (I also tried with Ubuntu 20.04). Debian, on the contrary, can configure RAID successfully and complete the setup.

[/FONT][/COLOR][IMG]https://i.stack.imgur.com/Y4rOk.jpg[/IMG]

[IMG]https://i.stack.imgur.com/wEFVI.jpg[/IMG]

[IMG]https://i.stack.imgur.com/libV1.jpg[/IMG][COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]

---

### Post by TheFu on 2022-07-15
Just for fun, I setup RAID via LVM on Ubuntu knowing that because it is on quality SSDs, that failure is extremely unlikely and backups are 1000x more important than RAID.  I didn't use mdadm.
The method is to setup LVM on 1 SSD during the install, then use LVM's lvconvert tool to create a mirror/RAID1 set.  This doesn't mirror /boot/, which is a normal, non-LVM, partition. /boot/ can be manually mirrored to another partition on a different disk and update-grub will find it. Just add that to the patch scripts used.
```
#       Convert a linear LV to a two-way RAID1 LV.
       lvconvert --type raid1 --mirrors 1 vg/lvol1

```

With LVM, we can split and merge mirrors as we like. We gain access to all the enterprise LVM features, not just RAID1.  There are lots of how-to guides for LVM.
Best of all, with the LVM method, all the RAID parts happen post-install, so we don't have to struggle with the terrible interface in the installer.

Just providing another option for consideration.

---

