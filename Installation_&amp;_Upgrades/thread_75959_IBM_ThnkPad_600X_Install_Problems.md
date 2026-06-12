---
title: "IBM ThnkPad 600X Install Problems"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by w9cw on 2005-10-14
I burned install and live Breezy Badger ISO's.  Installed it on my desktop, and all worked fine with either - as usual, but not with my IBM ThinkPad 600X.  I would really like to use 5.10 on the 600X, as it's my "road warrior" laptop.  The live CD-ROM doesn't load, but the install CD-ROM goes through the install process completely without a hitch. But, when you boot, Ubuntu loads, but stops at the Ubuntu banner and never loads the desktop.  I know the old 600X can be flaky with Linux, but any ideas?  I have upgraded the BIOS to the latest version.

---

### Post by waffen on 2005-10-14
Try to edit this file:

gedit /boot/grub/menu.lst 

add this lines:

pci=noacpi
acpi=off
apm=on

If you couldn start the Ubuntu, in the grub window if possible make this change with the "e" command to edit the ini line. 

I have the same laptop and in my Hoary distro, I need this change for run Ubuntu.

Mario

---

