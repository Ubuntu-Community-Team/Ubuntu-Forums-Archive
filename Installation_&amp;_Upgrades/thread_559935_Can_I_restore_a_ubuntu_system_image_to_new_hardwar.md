---
title: "Can I restore a ubuntu system image to new hardware?"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by nelsonm on 2007-09-25
Hi,
I want to restore a backed up ubuntu os drive image onto another computer. Will i have problems running the restored ubuntu system drive image to a new and different computer?

I know that Microsoft systems often will not even boot up when restored to a new and different computer because the os has already been configured for that hardware.

Will Ubuntu adjust or will i have to just start with a new install and try to port over the desktop preferences?

regards,

---

### Post by ddrichardson on 2007-09-25
No I've done it and had no problems, except for a little hardware tweaking.

---

### Post by zero-9376 on 2007-09-25
you will probably have to make some changes to configuration files for grub, fstab, xorg and maybe your network. i did this a while ago and it worked very easily.

grub - uses uuid of partitions which will probably be different on the new pc
fstab - as above
xorg -for me i just changed ati to nvidia
network - your primary card will probably be eth1 now not eth0, network manager might be able to deal with this though

---

