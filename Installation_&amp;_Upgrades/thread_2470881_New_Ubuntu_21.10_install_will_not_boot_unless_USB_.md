---
title: "New Ubuntu 21.10 install will not boot unless USB install stick is inserted"
date: 2022-01-14
forum: Installation &amp; Upgrades
---

### Post by Richard-S on 2022-01-14
On an Acer Aspire TC 1660 with an SSD, I have installed Ubuntu 21.10. Unless I put the USB installer stick in the USB slot, the screen tells me there is no bootable medium. When I put the USB stick in and restart, it boots up into the new installed system just fine.

Richard

---

### Post by MAFoElffen on 2022-01-15
It sounds like (somehow), it installed the Grub bootloader to the USB stick?

I would redo the USB thumb drive with the install media, and reinstall, insuring that the boot loader is installed to the internal drive.

---

### Post by Richard-S on 2022-01-16
That solved the problem.

Thank you.

Richard

---

### Post by MAFoElffen on 2022-01-16
Happy that this is solved for you.

Happy Ubuntu Journey...

---

