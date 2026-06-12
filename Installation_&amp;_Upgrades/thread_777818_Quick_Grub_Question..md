---
title: "Quick Grub Question."
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by jesusfreak107 on 2008-05-01
how do I use GRUB to boot off of a USB device that has an iso file on it?

Thanks.
:guitar:

---

### Post by Pumalite on 2008-05-01
Maybe this helps:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

1. Make flash drive bootable with syslinux
2. Download the vmlinuz and intrid.gz from the ubuntu archives (not the cd ones - this is why people can't mount the flash drive as CD)
3. get the isolinux.cfg from the cd and rename it syslinux.cfg
4. get a copy of an iso you want to install. dont extract or rename the iso.
5. drag those files into a flash drive
6. boot from it and the install shall go normally without needing to mount anything

---

