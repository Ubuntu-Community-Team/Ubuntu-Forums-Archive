---
title: "problem when installing from usb"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by crazymao on 2011-05-27
so im trying to install a 64bit ubuntu on my comp with a usb, everything works nicely until in the middle of the installation i get an error saying something like "error loading drivers from cd-rom", i followed many guides online on how to install from usb but im always stuck at this error, any ideas what might be up? thanks

---

### Post by DrDim on 2011-05-27
Have you copied the initrd.gz and vmlinuz from images hd-media or from cdrom?
[[COLOR=#444444]http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/[/COLOR]]("http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/hd-media/") you can get them for hd-media here.
Also try this in your syslinux cdrom-detect/try-usb=true persistent

---

