---
title: "Install using usb cdrom but with no bios support"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by [Knuckles] on 2007-08-24
I'm trying to install ubuntu on and old celeron 600mhz laptop (compaq presario 1200) but the built-in cdrom doesn't work anymore and usb booting (to an external cdrom drive) is not supported by the bios.

Is there a way to use some bootloader (installed to a floppy or to the hd) to boot off the usb cdrom? 
I've been searching and haven't found a way to do this anywere.

Thanks

---

### Post by logos34 on 2007-08-24
> usb booting (to an external cdrom drive) is not supported by the bios.

Is there a way to use some bootloader (installed to a floppy or to the hd) to boot off the usb cdrom? 

There is something called a Smart Boot Manager (SBM) floppy, but it doesn't support usb devices, it's only good for booting an internal cdrom in cases where the bios can't.  

If you have windows installed on it try this howto:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

or Plan B: take the hard disk out and plug it into another machine and install, then put it back into your presario and hope it works.

---

### Post by pgar23 on 2007-08-25
> **'[Knuckles] said:**
> I'm trying to install ubuntu on and old celeron 600mhz laptop (compaq presario 1200) but the built-in cdrom doesn't work anymore and usb booting (to an external cdrom drive) is not supported by the bios.

Is there a way to use some bootloader (installed to a floppy or to the hd) to boot off the usb cdrom? 
I've been searching and haven't found a way to do this anywere.

Thanks

Also, u might want to go to your motherboard manufacturer website and try downloading the updated version of your bios. I remember my BIOS didnt support usb booting, but once i updated the BIOS, the revision supported usb boots.

---

