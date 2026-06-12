---
title: "cant boot from USB"
date: 2016-03-12
forum: Installation &amp; Upgrades
---

### Post by qball2 on 2016-03-12
Hi all
I'm trying to install Ubuntu from USB on a pavilion x2 (laptop/tablet)
Iv set up a bootable USB with unetboot with Ubuntu on it
 iv gone in to boot options with f10 and disabled secure boot
changed the boot order so  the USB boots first

but it still boots into windows after reset

or do I have to download one that will work through UEFI, by the way iv not a clue what that dose or what its for. iv just going through a few forums and seen it mentioned

thanks

---

### Post by fantab on 2016-03-12
Have you read:
[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)
[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)

Posting a few details of the desktop/laptop you are installing Ubuntu to will help the forum help you.

---

### Post by Bucky Ball on 2016-03-12
Welcome. Boot to Windows, switch off hibernation, try again. If Win is hibernating then the drive is effectively still mounted and you can't access it any other way than booting straight to it. Even though you think the machine is going off, when hibernation is on, Windows is still mounted and running. You can't install Ubuntu, or anything else, under those conditions.

---

### Post by qball2 on 2016-03-13
hi pal
   Iv turned off hibernation its no different

---

### Post by qball2 on 2016-03-13
its a HP pavilion x2 detachable laptop/tablet 2 in 1

Intel Atom atom&#8482; z8300 quad core processor. 
32GB eMMC hard drive. 
2GB ram

Microsoft Windows 10

---

### Post by HermanAB on 2016-03-13
Well, first of all, you don't need unetbootin to make an ISO image bootable anymore.  The Ubuntu ISO files have been dual mode for the last few years.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by qball2 on 2016-03-13
> **HermanAB said:**
> Well, first of all, you don't need unetbootin to make an ISO image bootable anymore.  The Ubuntu ISO files have been dual mode for the last few years.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Hi pal 
I'm guessing it must be something to do with this computer. just used that USB installer and the same thing, it just ignores the USB on boot up

---

### Post by Bucky Ball on 2016-03-13
*Thread moved to **Installation & Upgrades**.*

---

