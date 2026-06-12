---
title: "Grub error 18 from usb boot"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by jdm bb6 on 2007-05-29
I am in classand we are having an issue with booting from a usb drive. We keep getting errors no matter how much we change within the bios.

USB boot enabled. Internal SATA drive disable and only PATASecondary Master/slave active for cd/DVD drives.

Fails on both IOMEGA 250GB and LaCie 80GB.Only one Lacie booted and the cd/DVD drives were onthe PATA Primary master/slave. Otherwise identical Intel 865 motherboard.

new server edition 

Need help asap guys please, thanks in advanced.
Deric

---

### Post by confused57 on 2007-05-29
Here's an explanation of error 18 & possible solutions:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

You may need to create a separate small  /boot partition(approx 100 Mb) at the very beginning of the hard drive.

---

