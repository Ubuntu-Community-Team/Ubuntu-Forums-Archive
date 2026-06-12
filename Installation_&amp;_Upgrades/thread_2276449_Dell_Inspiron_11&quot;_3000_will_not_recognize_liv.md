---
title: "Dell Inspiron 11&quot; 3000 will not recognize liveusb"
date: 2015-05-02
forum: Installation &amp; Upgrades
---

### Post by roaddog27 on 2015-05-02
I have a dell 11" inspiron 3000 series computer that came preinstalled with windows 8.1.  I'm trying to replace windows completely with ubuntu via a live usb flash drive created with pendrivelinux.  In the bios menus, booting from usb isn't even an option, when choosing the boot order there's only one option which is the windows boot loader.

Why am I not able to select alternative boot sources?  I've tried to boot via usb in both eufi and legacy boot mode, and with secure boot on and off with no success.  Any advice will be greatly appreciated.

---

### Post by kagashe on 2015-05-03
> Why am I not able to select alternative boot sources? 

Is the ISO 64 Bit?
Did  you check the ISO by md5sum?(md5 Calculator application is available free on Windows store)
Perhaps it is not UEFI Bootable USB Stick. I think Pendrivelinux is an old site to help you make one.

You can use the following guide:
[How To Create A UEFI Bootable Ubuntu USB Drive Using Windows]("http://linux.about.com/od/howtos/ss/How-To-Create-A-UEFI-Bootable-Ubuntu-USB-Drive-Using-Windows.htm")

Kamalakar

---

