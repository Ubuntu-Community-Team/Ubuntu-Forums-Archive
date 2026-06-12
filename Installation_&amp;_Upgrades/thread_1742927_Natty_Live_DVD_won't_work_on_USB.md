---
title: "Natty Live DVD won't work on USB"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by linuxone on 2011-04-29
Hi,

I used the Ubuntu Startup Disc Creator to copy the Natty Live DVD to an 8 GB USB stick. I need the USB boot disc because my Notebook doesn't have a DVD drive and I need an bootable Live medium to repair my failed grub installation. (solved - see some topics below)

I did boot from USB and tried to repair the grub installation within a terminal. (mount encrypted partition, mount proc/dev/sys -> then chroot)

Unfortunately I cannot do any of these simple steps. "mkdir /media/sda" failes due to write permission, mount fails due to less space. Neither Firefox can't be used. FF reports a problem (missing security rules) and won't open any web page - but a ping to the Internet was successfull.

Repeating all steps, exactly same syntax, after booting Live-CD from USB, everything is working fine. Firefox has network access, mkdir, mount and chroot does work correctly. Finally I could solve my grub problem only by using the Live-CD but NOT using the DVD.

Is this a problem of the USB disc creator or contains the DVD ISO content some errors?

Thomas

---

