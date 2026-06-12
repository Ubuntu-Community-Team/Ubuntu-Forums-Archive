---
title: "Installing on IT8212 controller"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by Frankk on 2005-10-18
I want to instrall Ubuntu 5.10 on a drive connected to ITE 8212F RAID controller.

Since it seems that installer doesn't see my hard drive connected to the controller i was thinking to this solution and I'd like to hear from someone if it could work or if it is just fantasy.


I already have Ubuntu on another PC. I found the kernel patch to support the RAID controller I have.

-I could apply the patches on the other ubuntu box (same kernel version) and compile both the kernel with the driver compiled directly in the kernel and the module alone. Then can copy the module and the kernel in a floppy.
-Then boot the install cd on the machine with the raid controller, insmod the module compiled on the other ubuntu bux mount the drive (or see if at this point the installer see it) and install ubuntu.
-Once the installer tells me to reboot i could just mount the / partition, copy my kernel compiled with the driver for the controller in /boot of the new hd and modify /boot/grub/menu.lst accordingly.
-Then the system should reboot and grub should load the new kernel with raid controller support.

Please tell me if this can work or not, or if there is an easyer method of installing on HD connected to this raid controller.

---

