---
title: "Ubuntu 16.04 beta 2 64 bit installation USB key not recognized in BIOS"
date: 2016-04-10
forum: Installation &amp; Upgrades
---

### Post by daloonik on 2016-04-10
I'm trying to install the 64 bit version of Ubuntu 16.04 beta 2. My machine is a HP Mini 110-3100 which is 64 bit compatible. The HP Mini is running Ubuntu 14.04 32 bit. I have tried two different USB sticks with the file ubuntu-16.04-beta2-desktop-amd64.iso installed with Universal USB Installer under Windows. However when I choose a boot device in BIOS the USB Key is not listed; only the hard drive. This isn't a problem with the USB stick as I can install the 32 bit version of Ubuntu 16.04 beta 2 on the USB stick and the HP Mini's BIOS will now recognize it and allow me to boot from the USB Key. Is this a problem with the ISO File, or is this due to the fact that the computer is running a 32 bit operating system? Will I have to choose an installation method that doesn't involve the USB Key or CD drive? Thanks.

---

### Post by sudodus on 2016-04-10
You already know how to make your computer work with a 32-bit linux system :-)

If you want to check if the problem depends on the operating system or the pendrive (a hardware mismatch), you can install exactly the same system that you know works, in exactly the same way into the other pendrive. Will it work or not?

You can also try to install Ubuntu Xenial (64-bit) into the pendrive that works with a 32-bit system. Will it work or not?

-o-

I think that even when you make it boot, you will get problems with standard Ubuntu, because it wants a stronger CPU and more RAM to work (or at least to work well). 64-bit systems need more RAM for the same task compared to 32-bit systems. You will probably have better luck with a lighter flavour of the Ubuntu family

- ***Lubuntu*** will an ultra-light desktop environment
- ***Xubuntu*** will a medium light desktop environment
- ***Ubuntu MATE*** will a medium light desktop environment

---

### Post by daloonik on 2016-04-10
All right, I'll try one of those. I thought the 64 bit version would make it run faster, but I guess that won't be the case if it requires more RAM. Thanks for the response!

---

### Post by $yl9pAR%t on 2016-04-10
I do not know how much RAM you have, but if Google Chrome browser is important to you, you should try to find a way to install 64-bit OS. Google Chrome is not supported any longer on 32-bit OS'es. When it comes to mix of 32 and 64-bit OS'es I had no problem to install Ubuntu 16.04 64-bit along with Windows Vista 32-bit and Xubuntu 14.04 32-bit.

EDIT:

If you still have Ubuntu 14.04, try to use SDC (Startup Disk Creator), besides don't bother with beta 2, download current version (less updates after install).

[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

---

