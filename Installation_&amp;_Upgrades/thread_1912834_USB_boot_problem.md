---
title: "USB boot problem"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by majabl on 2012-01-21
Hi,

I'm trying to sort out an old Mesh PC for my parents, and having a few problems. The computer in question is from 2003 and currently dual boots between Ubuntu 11.04 and Windows XP. I would like to do a clean install of both operating systems for them, but switch Ubuntu for Xubuntu.

The controller for the DVD-R and CD-RW drives on this computer is shot, so booting from a live CD via one of those drives isn't an option.

So I tried an external USB DVD drive. I changed the BIOS settings on the computer to boot from USB-CD, but the computer goes straight to Grub and from there boots via the HD. It's as though the external drive is being ignored. Once booted into Ubuntu or Windows, both recognise the external drive exactly as I would expect.

With that not working I tried the same with a USB pen drive, changing the BIOS boot order, and so on. Again, straight past the USB pen drive and straight to Grub.

I've even tried turning off the HD as a boot device in BIOS and just having all of the USB options (FDD, HDD, CD), but I still get to Grub and from there can boot to Ubuntu (default) or Windows.

Please help because I am out of ideas!

(NB I've tested the Xubuntu 11.04 live CD and pen drive on other computers and both work without problem.)

---

### Post by 2F4U on 2012-01-21
There is a small chance that booting from usb has been disabled in the BIOS. Did you check that? Else, it may indeed be one of those older computers that are not able to boot from usb.

---

### Post by majabl on 2012-01-22
> **2F4U said:**
> There is a small chance that booting from usb has been disabled in the BIOS. Did you check that? Else, it may indeed be one of those older computers that are not able to boot from usb.

Hi, 2F4U, and thanks for replying.

In the BIOS all of the USB options have been activated in the boot order. I've even turned off the HD from the boot order, but switched on and left alone the computer will go to Grub and then boot Ubuntu from the HD - even though it's not actually listed as a boot device.

Is it a fair assumption to make that if the BIOS lists booting from USB as an option, then the computer ought to be able to do it?

---

