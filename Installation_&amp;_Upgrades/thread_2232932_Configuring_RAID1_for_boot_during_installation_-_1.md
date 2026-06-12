---
title: "Configuring RAID1 for boot during installation - 14.04"
date: 2014-07-05
forum: Installation &amp; Upgrades
---

### Post by alessandro-macuz on 2014-07-05
Hi folks,

My goal is to set up a RAID1 virtual disk, w/ or w/o LVM on it, from where to boot.
I thought I could configure RAID1 during the installation but I didn't see any menu/option.
Do you have to configure mdadm in another way and then start the installation of Ubuntu or I can indeed configure the RAID for boot while installing?
Moreover booting off a USB stick (I transferred the official CD onto a USB stick by using Rufus) I land always in the graphical environment while I normally prefer the text based.

Could anybody clarify?

Thanks, Alex

---

### Post by alessandro-macuz on 2014-07-05
OK, via Ctrl+Alt+F1 I have access to the console and from there I can use either fdisk or gparted (I have 2x320Gb disks).
Yet I don't know if the official procedure enables you to configure a mdadm disk at installation to boot from it.

Alex

---

