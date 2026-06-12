---
title: "[SOLVED] Installed and trying to boot on another pc"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by Diabolis on 2008-03-19
After installing successfully ubuntu into a removable hard drive through computer A, I tried to boot computer B with it. I reinstalled grub and everything went well, rebooted and the grub menu looked fine. So I picked the newly installed ubuntu and it seemed to boot as normal, but It froze halfway. I did a hard boot and tried again, but then grub returned error 21.

I already fixed my grub. I supposed that you can't install an operating system in computer A, remove the hard drive and try to boot with it in computer B. I'm guessing that its because when you install an operating system lots of configurations are made and some of them must be hardware specific. I know you can make bootable usb sticks to accomplish this.

I just wonder how a bootable usb handles those "hardware specific configurations" or whatever doesn't let you do it by installing in computer A and the trying to boot into other pcs.

---

### Post by ajgreeny on 2008-03-19
> I'm guessing that its because when you install an operating system lots of configurations are made and some of them must be hardware specific.Yup, you're correct, and there is no way round it as far as I know with a normal install.

> I just wonder how a bootable usb handles those "hardware specific configurations" or whatever doesn't let you do it by installing in computer A and the trying to boot into other pcs.This is because the bootable usb is not a proper install but the same as a live CD, so it picks drivers for hardware etc when booting, rather than trying to use the driver you have on a normal install.

---

### Post by Diabolis on 2008-03-19
So a live-cd uses generic drivers? I don't think thats possible because if it did, people wouldn't have so many problems installing drivers and everyone would be happy keeping the generics. Maybe the live-cd communicates directly to the hardware, kind of like an assembly language?

---

### Post by Peter09 on 2008-03-19
Generic drivers often do not have the full capabilities of the device specific drivers.

PC

---

### Post by Diabolis on 2008-03-19
> Generic drivers often do not have the full capabilities of the device specific drivers.
So, are you saying: Yes, a live-cd uses generic drivers just to provide the minimum functionalities?

---

### Post by ajgreeny on 2008-03-19
Depends what you mean by "generic drivers".  The live CD uses only open source drivers but it does, for example, include OS drivers specifically for ati, intel and nvidia graphic cards, as well as the "generic" vesa driver.  I don't know if this answers your query, but I hope it helps you understand why you had your problem with the external disk install.  Do a google search on "ubuntu on a usb drive" and you'll find a lot of info.

---

### Post by Diabolis on 2008-03-19
Yeah, thank you. This is pretty interesting. So it is actually pretty simple, for example talking about video cards. You don't know which one is going to have a pc, so the live-cd comes with intel, ati, nvidia and vesa no big deal. 

This means that drivers for hardware are very small? 
Because there are other linux distros that probably work the same way, but they don't have a 700mb cd some of them use 200mb or maybe less.

---

