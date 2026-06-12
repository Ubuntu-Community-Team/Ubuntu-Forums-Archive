---
title: "installation on raid 0"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Nosnik on 2007-10-19
Just installed ubuntu 7.10 on a software raid 0, but i can't install any of the boot loaders grub/lilo onto the raid partion. Does anyone have an idea?

by standard it tryes to install itself on hd0, and just gets an error when i change it to md1 (the raid partion)

---

### Post by LinuxNewb_22 on 2007-10-23
try making your /boot partition a RAID 1 array and the rest of your partitions RAID 0. That's what worked for me.

---

