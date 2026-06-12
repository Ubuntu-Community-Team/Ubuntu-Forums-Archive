---
title: "bootloader fails after reboot after ubuntu installation"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by DreamPhysix on 2011-03-29
I installed Ubuntu 10.10 amd64 (and tried 10.04.2 as well) from Wubi under Windows 7 64-bit.  When I reboot after installing it through Windows, I go to Ubuntu and the installation completes.  Then it reboots again to finish the install of the OS.  When I boot into Ubuntu now, grub does not appear.  Instead, some initramfs stuff comes up in a console with no GUI and says some error stuff about root devices.  I read that grub updates cause problems, but the installation never finished and therefore I was never able to go into Ubuntu to lock grub packages, etc.  Please advise!  I've run into this error on multiple fresh installs

---

### Post by bcbc on 2011-03-29
when you see the grub menu, hit 'e' and check the 'root=/dev/sdXY'. 
Then press ESC, hit 'c' and enter ls (lower case LS). Then report back on what you see.

---

