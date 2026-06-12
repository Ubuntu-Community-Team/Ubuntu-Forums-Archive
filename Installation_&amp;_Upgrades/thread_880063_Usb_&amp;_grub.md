---
title: "Usb &amp; grub"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by riles32807 on 2008-08-04
Not quite an installation problem, but here's my situation.

I've installed Ubuntu to a USB drive.  I'd like to set it up so that when the USB drive is plugged in, Ubuntu loads, when it isn't, Windows loads.  In the past I've been able to do this through the BIOS on other computers, however this BIOS resets the boot order if the USB drive isn't found.

I was wondering if I could do this with GRUB?  It seems like it should, but I think GRUB was installed to the USB drive, so if the drive isn't found GRUB fails with 'error 21'.  Is there a way to move GRUB to the Windows partition?  I've already changed the menu to load Windows by default (I know, I'd love to be 100% linux but that's not an option due to work reasons).

Thank for any help.

---

### Post by logos34 on 2008-08-05
no, the error means that grub (the tiny 446 byte stage1, to be exact) is on the MBR of the internal (windows) disk...what's happening is that at boot it's looking for menu.lst on / (->USB) but can't find it when it's unplugged.  

Either reinstall grub (see link below) to the mbr of the external disk (and toggle the Bios boot order for the OS) or make a /boot partition on the windows disk.

---

### Post by riles32807 on 2008-08-13
> **logos34 said:**
> no, the error means that grub (the tiny 446 byte stage1, to be exact) is on the MBR of the internal (windows) disk...what's happening is that at boot it's looking for menu.lst on / (->USB) but can't find it when it's unplugged. 

Ok that's what I thought was happening. 

> **logos34 said:**
> Either reinstall grub (see link below) to the mbr of the external disk (and toggle the Bios boot order for the OS) or make a /boot partition on the windows disk.

I'll try making a /boot partition on the windows disk.  Thanks for the help, I'll be back if I have any more questions. =)

---

