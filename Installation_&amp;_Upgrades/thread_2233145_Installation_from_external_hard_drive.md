---
title: "Installation from external hard drive?"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by Noah_Campbell on 2014-07-06
All i have is an external hard drive and i was wondering if i could just install with the same installation as a USB Stick. Is this possible?

---

### Post by Mark Phelps on 2014-07-06
Yes -- you can use the USB stick to install to the external drive -- but to be safe, have any internal drives disconnected when you do the installation, to prevent GRUB from being accidentally installed to the internal drive.

---

### Post by Noah_Campbell on 2014-07-06
May i use this [https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick) instead of the grub method?

---

### Post by mc4man on 2014-07-06
> **Noah_Campbell said:**
> All i have is an external hard drive and i was wondering if i could just install with the same installation as a USB Stick. Is this possible?
If you mean 'can I use an external hdd to install **from**', I don't see why not. 
(as long as the external has no current bootable partitions & if using Startup Disk Creator no ext.* partitions
Just create a small 1.5 Gb FAT partition & use that in U-S-C

---

### Post by yancek on 2014-07-06
I'm not sure what you are trying to do?  Do you mean you do not have a flash drive and want to boot to install from an external hard drive?  You can boot the iso file if you have a system with Grub2 and most any Ubuntu derivative using a loopback entry in the grub.cfg file.  You haven't given any information on what operating system you have available to not much point in trying to give more detail.

---

### Post by sudodus on 2014-07-07
> **Noah_Campbell said:**
> All i have is an external hard drive and i was wondering if i could just install with the same installation as a USB Stick. Is this possible?

> **Noah_Campbell said:**
> May i use this [https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick) instead of the grub method?

You can use a HDD drive instead of a USB drive and vice versa, so yes you can do what you ask.

But if you have important files stored on the drive, you should careful, so that they will not be damaged or removed in the process.

The Startup Disk Creator (alias usb-creator-gtk and usb-creator-kde) as well as Unetbootin want a FAT32 file system. If you have an NTFS file system on the external HDD, you will have problems.

See also this link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

