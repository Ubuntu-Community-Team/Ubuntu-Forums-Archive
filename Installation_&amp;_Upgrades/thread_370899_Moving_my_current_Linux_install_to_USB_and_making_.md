---
title: "Moving my current Linux install to USB and making it bootable ?"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by elmerfud on 2007-02-26
I've been using Fedora for several years on my laptop.  It still works, but I want to move to Ubuntu.

I am very afraid of losing data and the many applications that I have built and installed in Fedora.

I'd like to move my current Fedora installation onto a USB drive and make it bootable, so that I could always go back and run or look at something if I need to.

My laptop will not boot a USB device.

Could I set it up like this ?

1) copy everything from my current installation to the USB drive with cp -a

2) wipe the laptop and install Ubuntu

3) create a new grub entry in Ubuntu that boots the old Fedora image now located on the USB drive ?

I'm a little foggy on step #3.  Some help would be greatly appreciated.

A typical grub entry in Fedora's grub.conf looks like this.

===============================================
title Fedora Core (2.6.19-1.2911.fc6PAE)
	root (hd0,1)
	kernel /vmlinuz-2.6.19-1.2911.fc6PAE ro root=LABEL=/12 rhgb quiet pci=assign-busses
	initrd /initrd-2.6.19-1.2911.fc6PAE.img
===============================================

Could I copy the above into the Ubuntu grub and copy the necessary vmlinuz, etc files to Ubuntu's /boot dir and then change root(hd0,1) to point to /dev/sda1 ?

Is it that simple ?

Thanks !

---

### Post by elmerfud on 2007-02-26
What if I did "kernel /vmlinuz-version ro root=/dev/sda1" ?

Thanks

---

