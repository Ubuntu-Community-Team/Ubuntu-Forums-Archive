---
title: "Booting Karmic 9.10 Grub2 via XP bootloader"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rallg on 2009-08-25
Those of you who dual-boot with a previously-installed Windows XP (not Vista) know that it is possible to use XP's own boot loader, then transfer control to GRUB, where GRUB is installed within Ubuntu's own partition rather than at the hard drive root.

Ubuntu 9.10 uses the "GRUB2" boot loader, which is quite different from the original GRUB. I have tried, and it is still possible to use XP's own boot loader with GRUB2, just as with old GRUB.

The main difference is that GRUB2 does not use a "menu.lst" file. In most cases, you don't need to worry about that.

You can also boot to Grub4DOS on a USB stick, then transfer control over to GRUB2 installed on your Ubuntu partition. In this case, you will have to hand-create menu.lst on the USB.

I won't describe the details, since they are already known to those who use these methods. But I wanted to tell you that the methods still work with GRUB2. I am using Asus EEE PC 1000HA.

---

