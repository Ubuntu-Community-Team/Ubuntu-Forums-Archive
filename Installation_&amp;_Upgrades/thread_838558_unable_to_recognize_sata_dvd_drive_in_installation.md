---
title: "unable to recognize sata dvd drive in installation of 8.04 server"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by jonschin on 2008-06-23
I ordered a new computer and would like to play around with the server edition however because my new computer has a sata dvd drive when it tries to find the cd rom drive it can not find it.  I then tried to set it up using a usb flash drive.  I got to the same spot and could go no further.  I am by no means an expert but i am also not completely green, aka i am not afraid of diving into files and playing around with them to try and get the installation to work.  The problem is that i do not know which file i would need to change, if any, for the installation to not want to look for a cd rom anymore.

---

### Post by Pumalite on 2008-06-23
Try editing the boot line and adding all_generic_ide at the end.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by jonschin on 2008-06-23
its not a problem with the grub boot loader.  The problem is with the installation disk.  I want to try changing something in the installation usb

---

### Post by jonschin on 2008-07-19
I dont know why this is true but the server installation does not work, however the desktop installation works.

---

