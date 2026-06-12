---
title: "Installing from LiveCD to USB stick"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by gubemton on 2007-11-12
I'm not looking to get the LiveCD iso bootable on a USB stick.

What I want to do is boot from the LiveCD and install Ubuntu on the USB stick.

The USB's MBR will have grub and the system itself will not be affected.

If I plug the USB stick during bootup it should load Ubuntu and run a non-live (i.e., regular) version of Ubuntu. I should be able to treat the stick as if it were a local hard disk.

My questions are:
1. Is it possible?
2. If it is possible, could the system's BIOS be an issue (for example, not booting from USB)?
3. Will this degrade the life of the USB stick (and would using a persistent LiveUSB installation be better)?
4. How do I go about doing this (i.e., should I just follow the instructions on how to install to a USB HDD)?

Answers to any of these questions will be appreciated.



Basically, I want Ubuntu to load from a USB stick, but I don't want it to be the iso.

---

### Post by az on 2007-11-12
1 - Sure.  Just boot the live cd, pick install and when it asks where you want to install it, tell it to use the usb drive.  Whether it is a solid-state drive or a spinning disk makes no difference.
2-   yes, if your bios cannot boot from usb, then you cannot boot from usb.  There are some tools which allow you to boot from usb (smart boot manager - it's included on the disk in the /install folder.  You make a floppy out of that image and boot the floppy.  SBM then will scan your hardware that *it* can boot from.)
3-  No.  Why would it?  It's normal use.
4-  See 1.  Treat the usb drive as you would any other drive, external or not.  You may want to click the advanced tab and install grub to that (usb stick) drive instead of the default one...

Edit:  The only reason the live-cd-to-usb thing is complicated is because the live cd is built for a cd.  

A cd boots by emulating a floppy.  To do that, you need the isolinux.  To make a floppy bootable, you need syslinux.  To make a usb drive bootable, you either need to use grub or some other bootloader.  You can use syslinux on that too.  In fact, if you are running the live session and it is already configured to use isolinux, converting it to syslinux is simpler, but it is not the only way to go.

---

