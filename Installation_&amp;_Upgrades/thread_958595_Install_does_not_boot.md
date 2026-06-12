---
title: "Install does not boot"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by Nvidiot on 2008-10-25
I'm trying to install Ubuntu 8.04 with the alternate cd (the regular cd does not work properly). The machine has 5 drives (4x1TB SATA and 1x60GB PATA). I'm installing it on the PATA drive, which shows as /dev/sde in the installer. The install completes, asks me to remove the cd (which I do) and reboot. Once I reboot the system just sits there after the usual bios screens.

Hardware in use:
Gigabyte GA-MA74GM-S2H
4x Hitachi 1TB SATA
1x Seagate 60GB PATA <- trying to install on that

---

### Post by Nvidiot on 2008-10-25
Fixed it by booting into rescue mode, editing /boot/grub/device.map so hd0 points to /dev/sde and reinstalling grub on /dev/sde

---

