---
title: "Using Windows Boot Manager for dual boot"
date: 2005-03-01
forum: Installation &amp; Upgrades
---

### Post by emtilt on 2005-03-01
I'd like to setup an old Win2k machine to dual boot with Ubuntu. Currently, it has one HDD with Windows, and I would like to add another HDD for Ubuntu, and then have it dual boot. I know how to do all that. But I'd like to not overwrite the Windows Boot Manager with GRUB, but instead point the WIndows Boot Manager to GRUB. I know that this is possible, but I am unsure how to go about doing it. If you could point me to a link that gives some basic info, or just give me a very brief idea of how it could be done, I would be very grateful. I don't need anything too detailed. Thanks in advance.

---

### Post by Daniel G. Taylor on 2005-03-01
This may help:

[http://bratlady.com/linux_boot.shtml](http://bratlady.com/linux_boot.shtml)

Word of caution though, as it looks like you will need to update it every time you update your boot loader, and I'm not sure if it works with grub.

---

### Post by inz on 2005-03-01
It works fine with grub, and I didn't have to update the bootsector image or boot.ini whenever I updated grub.conf in gentoo, so this is a nice option if you want to be able to reinstall windows every now and then without losing your bootloader I think. =)

---

