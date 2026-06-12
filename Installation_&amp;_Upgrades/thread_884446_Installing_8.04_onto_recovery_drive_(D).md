---
title: "Installing 8.04 onto recovery drive (D:)"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by symuha on 2008-08-09
Hey guys. I've been playing around with the Ubuntu 8.04 Live CD and I really like it. I don't want to replace Vista with it, but I do want to install it so I can dual-boot. My primary drive is having problems where it will only shrink about 1 GB so I wanted to install on my recovery drive, which I'm not really using. So how would I go about formatting and then installing onto it? Also, how would I choose which drive to boot into on startup? Thanks for any help.

---

### Post by Partyboi2 on 2008-08-09
You could use gparted on the live cd (System>Admin>Partition Editor) and delete the D partition. (Make sure you delete the right one) then run the ubuntu installer and choose to use the unallocated space to install ubuntu.
Ubuntu uses [[COLOR=Blue]grub[/COLOR]]("http://en.wikipedia.org/wiki/GNU_GRUB"), so when you boot your computer after ubuntu is installed you will get a menu screen where you can select which operating system you want to load. See below.

Edit: Here is a howto to install vista/ubuntu dual boot.
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by symuha on 2008-08-09
Nevermind, thanks for the reply but I just used Wubi :)

---

