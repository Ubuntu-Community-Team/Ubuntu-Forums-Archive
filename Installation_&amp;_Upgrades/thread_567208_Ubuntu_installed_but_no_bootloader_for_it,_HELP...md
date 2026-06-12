---
title: "Ubuntu installed but no bootloader for it, HELP.."
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by Ncdude on 2007-10-04
Hi all,

I have Winxp and Vista installed on a 500gb Sata drive and installed Ubuntu on 15 gigs of it as well. Now when my computer boots up the only choices I have are for Winxp or Vista not for Ubuntu. Any way to fix this and why would it not enter itself into the bootloader?

Thanks,

Scott..

---

### Post by tgalati4 on 2007-10-04
Load the Ubuntu Live CD and look for the Ubuntu partition.

Post the output of:

/boot/grub/menu.lst  or /boot/grub/grub.conf

---

### Post by maybeway36 on 2007-10-04
Also, if you have a floppy drive, then you could reinstall Ubuntu and choose to install GRUB to (fd0) which is the floppy disk.

---

