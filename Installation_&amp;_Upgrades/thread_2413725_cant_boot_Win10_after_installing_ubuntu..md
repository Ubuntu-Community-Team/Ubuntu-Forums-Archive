---
title: "cant boot Win10 after installing ubuntu."
date: 2019-03-01
forum: Installation &amp; Upgrades
---

### Post by heavendeng9494 on 2019-03-01
[http://paste.ubuntu.com/p/PBQhWjr3BP/](http://paste.ubuntu.com/p/PBQhWjr3BP/)

disk info is shown on the above link.
I've tried update-grub, didn't have the win10 boot option though.

help!!!!!

---

### Post by yancek on 2019-03-02
> I've tried update-grub, didn't have the win10 boot option though.

Your boot repair output shows you have an EFI system on a GPT drive and you have the Ubuntu EFI boot files on the EFI partition.  There are no windows efi boot files and the windows boot files usually shown in boot repair on the system partition are not shown so updating grub isn't going to help.  The EFI partition should be marked as 'boot' or 'active' which you can do from GParted on the Ubuntu install media.  If that doesn't help you will need to get the windows boot files some other way such as a windows install DVD or recovery disk.

Were you able to use/boot windows before installing Ubuntu?

---

