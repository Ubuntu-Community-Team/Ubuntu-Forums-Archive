---
title: "Problem in booting of ubuntu 6.06"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by new_fan_of_linux on 2008-05-29
Hello everyone,

I installed ubuntu 6.06 one day before but there are some problems in booting it. Every time, the booting halts at the point "Mounting root file system" in the beginning. I even tried to boot using a live CD of ubuntu 6.06 but everytime the step "Mounting root file system" is not performed with an ok tag. I have two CDs of ubuntu but the problem arises from both of them besides hard disk booting of ubuntu. Can it be due to some problem in hard disk or anything else.

Any help will be highly appreciated. I am in great need of ubuntu.

---

### Post by logos34 on 2008-05-29
Sounds like it might be a problem with menu.lst or fstab, or filesystem error.  

Type this in a terminal:

sudo fdisk -l

Find your root partition and run a filesystem check:

sudo fsck /dev/hda?

Then mount root:

sudo mkdir /mnt/ubuntu

sudo mount -t ext3 /dev/hda? /mnt/ubuntu

gksudo gedit /mnt/ubuntu/boot/grub/menu.lst

Copy and post it.

Do the same for fstab:

gksudo gedit /mnt/ubuntu/etc/fstab


If you ever get it working correctly, you might consider upgrading:
[https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197](https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197)

---

