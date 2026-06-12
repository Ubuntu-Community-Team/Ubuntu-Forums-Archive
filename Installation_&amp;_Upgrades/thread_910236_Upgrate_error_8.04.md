---
title: "Upgrate error 8.04"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by pmarag on 2008-09-04
Hello,
I'm trying to upgrade xubuntu to 8.04 version and i get an error "Can't update xubuntu - desktop". Any ideas or other ways to upgrade? The pc is Pentium 3 with no cd-rom and no option to boot from removable drive ( like usb .

Thx

---

### Post by dstew on 2008-09-04
You can use [Unetbootin]("http://unetbootin.sourceforge.net") to do a fresh installation over the internet. This is not an upgrade, so you need to back up your data if you don't have room to make a new partition for the new installation.

---

### Post by pmarag on 2008-09-04
Thx for your advise. The pcs i want to upgrade are 9. Can i use this program and give it the source from a usb?

---

### Post by dstew on 2008-09-04
I am not sure you can do that with Unetbootin. Check their website. You can create a USB drive that will install Ubuntu. See [this Wiki]("https://help.ubuntu.com/community/Installation/FromUSBStick"). However, your system is unable to boot the installation disk. To get around the boot problem, you can use [Smart Boot Manager]("http://sourceforge.net/projects/btmgr/"). This is an operating-system-independent program that can detect and boot drives in a system where the BIOS is unable to do it. You will need to create a bootable floppy drive with Smart Boot Manager on it, boot it, and use Smart Boot Manager to boot the USB drive to install Ubuntu.

---

### Post by Crafty Kisses on 2008-09-05
> **dstew said:**
> You can use [Unetbootin]("http://unetbootin.sourceforge.net") to do a fresh installation over the internet. This is not an upgrade, so you need to back up your data if you don't have room to make a new partition for the new installation.

Nice information right there, wasn't even aware you could do that. :)

---

