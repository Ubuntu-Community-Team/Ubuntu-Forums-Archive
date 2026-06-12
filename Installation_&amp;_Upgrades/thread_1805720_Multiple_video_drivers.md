---
title: "Multiple video drivers?"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by TheShader on 2011-07-16
Hello I've installed Lubuntu to a USB stick. (Not live USB, a full install on it) I'm mostly using it in the computers at my school. I installed the proprietary nvidia drivers on it and it works perfect on the pc's with nvidia graphics. However, I get problems to getting it work on my laptop with Intel graphics.

I don't know how the graphics drivers actually work on a Linux distro. Is there a possible way of installing multiple video drivers (like nvidia, ati and some open source mesa drivers) and select them from GRUB? Maybe installing several kernels and installing the drivers for those kernels separately should work? But how?

Thanks

---

### Post by TheShader on 2011-07-16
*bump*

---

### Post by TheShader on 2011-07-17
*bump*

---

### Post by MAFoElffen on 2011-07-17
> **TheShader said:**
> Hello I've installed Lubuntu to a USB stick. (Not live USB, a full install on it) I'm mostly using it in the computers at my school. I installed the proprietary nvidia drivers on it and it works perfect on the pc's with nvidia graphics. However, I get problems to getting it work on my laptop with Intel graphics.

I don't know how the graphics drivers actually work on a Linux distro. Is there a possible way of installing multiple video drivers (like nvidia, ati and some open source mesa drivers) and select them from GRUB? Maybe installing several kernels and installing the drivers for those kernels separately should work? But how?

Thanks
Sort of yes... That one is really going to need an explanation!!!

First a short explaination of graphics in linux and unix-  The boot loader (grub, grub2, lilo) loads.  The boot loader displays a menu that not only lets you boot multiple OS'es, but gives you the ability to load the same OS with different startup options via a kernel boot line...  Thsi is what is going to give you the ability you want.  Once the kernel boots, xorg, the graphics layer can start...

If you pick a proprietary driver, it's going to pick that driver each time (not what you want).  If you let Xorg pick one of it's own opensource drivers (many)... but you need to create some menu-items with different kernel startup options to help it start with different graphics cards- fro it to be able to do that.  Those menu items, you can create in /etc/grub.d/40_custom.

What you can do is copy and paste the first menu item of /boot/grub/grub.cfg following 10_linux... and use it as an example in 40_custom to have many items with different kernel boot options.  After you make changes to this file, you have to run update-grub to pickup those changes.

I hope this info helped.

---

### Post by TheShader on 2011-07-17
Thanks for the reply! So to sum up with, I can't go with the proprietary drivers anyway, because once they are installed the system will only boot with them, am I right? But if I install the free drivers, I will be able to select?

---

### Post by MAFoElffen on 2011-07-19
> **TheShader said:**
> Thanks for the reply! So to sum up with, I can't go with the proprietary drivers anyway, because once they are installed the system will only boot with them, am I right? But if I install the free drivers, I will be able to select?
Yes... again "sort of.."  

Yes on if you install a proprietary, that last driver installed will be the one that comes up each time.

If you don't install any, then Xorg will start an Xsession and during it's upstart, it goes through some video hardware checks and figures out which driver to try to use...  It has over 20 opensource drivers including NVidia, Radeon, VESA and a generic VGA driver.

The other part of this is first tries to boot in a VESA mode.  Not all video hardware will automatically display in a VESA mode without some type of modeset passed to it.  The graphics modeset you can pass in a kernel boot line.  That's where can pass it in menuitems of 40_custom... to help that video hardware to boot graphically.

Common modesets for different video hardware are:
NVidia --> nomodeset
Radeon --> radeon.mode=1
Intel --> i850.mode=1
some others --> forcevesa

---

