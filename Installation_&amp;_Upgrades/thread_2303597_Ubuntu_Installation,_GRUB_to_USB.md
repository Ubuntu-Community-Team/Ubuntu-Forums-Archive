---
title: "Ubuntu Installation, GRUB to USB"
date: 2015-11-20
forum: Installation &amp; Upgrades
---

### Post by sg4rb0 on 2015-11-20
I have one HDD with two volumes on a single volume group. I plan to mount / on one volume, and /home on the other. What I also want to do is install the bootloader (GRUB) to a USB drive instead of on the HDD. But during the Ubuntu installation, I can't see how it's done. Please advise.

---

### Post by Bucky Ball on 2015-11-20
Are you installing Ubuntu from USB? Then you are going to need a blank USB plugged in during install to install grub to. You realise to boot Ubuntu you are going to need to boot to the USB (which means the USB will need to be plugged in whenever you boot Ubuntu). Any specific reason for wanting this unusual setup?

Anyway, choose 'Something Else' when you get to the partitioning section of the install and you can select to install grub wherever you like.

---

### Post by grahammechanical on 2015-11-20
The installer will default to install Grub to sda but as noted above when we use the Something Else option we get a window that shows the partition layout. Underneath that window is a panel with a drop down menu that will allow us to select a different location for Grub to be installed.

Look at image #4 in this wiki page. Right at the bottom of the image it says "device for boot loader installation." That is the panel with the drop down menu.

[https://wiki.ubuntu.com/UbuntuGNOME/Installation/ManualInstallation](https://wiki.ubuntu.com/UbuntuGNOME/Installation/ManualInstallation)

Regards

---

