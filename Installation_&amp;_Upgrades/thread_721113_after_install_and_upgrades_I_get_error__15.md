---
title: "after install and upgrades I get error  15"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by Kevin Jones on 2008-03-11
Hello all
I just downloaded kubuntu and burned an iso disk. this was a good download, with the md5 sum checking as good, and I slow burned.
Installation was fine, I clicked on the upgrades icon and downloaded all the updates offered
the installation of the updates did not go well, I got a message saying that install was not complete because of some, maybe, corrupt files.
I tried to open the adept manager, but it said that there was an instance of the package manager already being used, I decided to reboot, thinking that this would at least close the package manager. I still don't know why the manager was left working
on reboot I get

error 15
In sage mode as well as ubuntu 7.10

can any one help?

Jones Kevin

---

### Post by wblancqu on 2008-03-11
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

Frequently, the error notes a missing kernel image file. Make sure that the file it is referring to exists on your boot partition.

If not, try manually editing grub boot instructions (Press e in GRUB), and put a valid kernel image in boot line. If works, update permanent in /boot/grub/menu/lst

Grtz

---

### Post by col_panik on 2008-03-11
-

---

