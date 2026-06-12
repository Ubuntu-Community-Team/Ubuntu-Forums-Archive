---
title: "Grtub2 - error you need to load the linux kernel first"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by veda_sticks on 2008-06-16
I recently upgraded to grub2 3 or 4 days ago, found out how to get it to put windows in the grub menu and everything was fine, booting into windows or linux worked perfectly everytime.

Now today i switch on my machine and after selecting the kernel i want to use,

Error - you need to load the linux kernel first.

After pressing a key i get back to the grub2 menu.

I can get into windows but not linux.

---

### Post by Pumalite on 2008-06-16
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by lsatenstein on 2009-11-01
With 9.10, I am getting this message for all loadable files except UBUNTU and Windows XP.

My config  /dev/hda  UBUNTU, Memtest
           /dev/hdb  XP, Fedora , Fedora Memtest

Tried to find documentation for the new grub, and have not been too successful.

I am using 64bit Desktop Version  4 gigs memory

---

