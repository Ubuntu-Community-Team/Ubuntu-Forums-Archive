---
title: "Ubuntu on a USB Flash Disk"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by unseend on 2008-11-08
Hey guys!

I have a little question. I need to install Ubuntu on a pc which does not have a CD-ROM device. So, I need to make Ubuntu to be able to be installed from this USB Flash disk. I've done some little search and most of the other posts were about to install Ubuntu on the USB Flash, but I want just to burn the .iso there in order to be just like the CD. What have I to do?

Thanks,
unseend

---

### Post by dpantell on 2008-11-08
Hi,

If you have another computer that has a cdrom drive (or if you already have 8.10 installed) follow these instructions:

[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/]("http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/")

You don't have to use the persistence feature if your not going to be using the USB device as a portable install (select discarded on shutdown).

---

### Post by cariboo on 2008-11-08
If you are running Intrepid there is a builtin usb boot disk creator. Go to System-->Administration-->Create a USB Boot Disk.

You don't need to burn a CDrom you can use an iso of the distribution you want to install.

Jim

---

### Post by unseend on 2008-11-09
I am running 7.10 :-/

---

### Post by C.S.Cameron on 2008-11-09
Unetbootin will install the iso to flash drive, you can then use the flash drive to install Ubuntu to a computer without CD.
If you install usb-creator it will do the same as Unetbootin.

---

### Post by gnomeInWonderland on 2008-11-11
[LIST=1]
[*]plug your flash disk on your PC
[*]cat /etc/mtab to see which device your USB flash disk is
[*]unmount your flash disk, but let it plugged
[*]enter this command : dd if=<your_iso> of=<flash disk device> bs=1024
[*]now you can boot on your flash disk
[/LIST]

:)

---

### Post by null_pointer_us on 2008-11-11
> **C.S.Cameron said:**
> Unetbootin will install the iso to flash drive, you can then use the flash drive to install Ubuntu to a computer without CD.
If you install usb-creator it will do the same as Unetbootin.

I second this. Here's a guide for Unetbootin:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Pretty slick, IMO. :)

---

### Post by unseend on 2008-11-25
Guys thanks! Hence I installed 8.10 I run now the built-in app for the LiveUSB. :D:D Thanks once again!

---

