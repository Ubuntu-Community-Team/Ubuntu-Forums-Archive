---
title: "Any way to install Lubuntu without a Live CD/USB."
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by cg2916 on 2011-07-15
I want to install Lubuntu, but I have no CDs and Live USB's don't work. Is there anything WUBI-like to install Lubuntu?

---

### Post by lincoln32 on 2011-07-15
Not that comes to mind but I have used plpbt at [http://www.plop.at/en/bootmanagerdl.html](http://www.plop.at/en/bootmanagerdl.html) to boot from machines the did have a usb option to boot from. wubi is troublesome and fails often.;)

---

### Post by azertyh on 2011-07-16
hello,
use [unetbootin]("http://unetbootin.sourceforge.net/").
yes, you use it usually to create a live USB, but you can install an OS in a new partition from an existing OS by choosing hard disk instead of USB drive.

---

### Post by wojox on 2011-07-16
> **cg2916 said:**
>  Live USB's don't work.

Why doesn't the Live USB work?

---

### Post by Rubi1200 on 2011-07-16
You can install Wubi in the regular way and then add the Lubuntu desktop I believe to achieve what you want:

> You can install your favorite distro from within Wubi (see the advanced  settings) and then once you are in Ubuntu, you can install the other  desktop environments as normal packages. Each desktop environment is  available as a single package (e.g. kubuntu-desktop). You will not have  to reboot to change the desktop, simply log-off and choose the desktop  environment in the options at login.   
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by varunendra on 2011-07-16
> **cg2916 said:**
> I want to install Lubuntu, but I have no CDs and Live USB's don't work. Is there anything WUBI-like to install Lubuntu?

If you really want 'WUBI-like' and 'Lubuntu' then I think it is best to try what Rubi suggested. But if you want a proper installation in its own partition, then I'm afraid you must have either support for USB-booting or a working CD/DVD drive. I have a few PCs around which can not boot from a USB flash drive, but boot fine from a USB hard drive.

> **lincoln32 said:**
> Not that comes to mind but I have used plpbt at [http://www.plop.at/en/bootmanagerdl.html](http://www.plop.at/en/bootmanagerdl.html) to boot from machines the did have a usb option to boot from. wubi is troublesome and fails often.;)
I think the general tutorials available on net about using Plop to boot a USB (for a computers which has USB ports, but no option in BIOS to boot from USB) involves a CD to boot initially from, that's a problem for the OP :). Although Plop has the capability to boot from network, but firstly this needs a separate computer to serve the network booting, and secondly I think it may need some extra efforts to get it to boot the live OS located on a USB device. But I've never used plop myself so don't know how it works, and of course it is a potential option if the OP has no other choice.

> **azertyh said:**
> hello,
use [unetbootin]("http://unetbootin.sourceforge.net/").
yes, you use it usually to create a live USB, but you can install an OS in a new partition from an existing OS by choosing hard disk instead of USB drive.
Wouldn't it install Lubuntu in Live mode? I think WUBI is better than Live mode in terms of functionality. However, this method can be extended further to use that same live installation to make a proper installation on a separate partition.

@cg2916,

If you prefer a proper installation, the BIOS has the option to boot from USB, and you have a USB hard drive, then using a live USB hard drive is the best and most convenient option.

---

