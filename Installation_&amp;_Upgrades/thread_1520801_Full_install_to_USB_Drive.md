---
title: "Full install to USB Drive?"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by d-shade on 2010-06-30
I was wondering if this is even possible.
I am trying to install ubuntu netbook remix to my 4gb usb drive.

I am mainly going to use it on my netbook so I can mess with my htc hero.
Is there any tutorial on how to set this up if it is possible?
Or would it be better to use the liveUSB method with 3gb of persistence.

It really doesn't matter if the life of the USB drive gets shorter doing it the first method. I just want the customization I had when I had ubuntu installed on my spare desktop.

---

### Post by kerry_s on 2010-06-30
i'd go with the live usb & slide the persistence to the max.

if you do the install, make sure you select advanced & point the boot loader to install on the usb.

---

### Post by sgosnell on 2010-06-30
It's easy.  Connect the USB drive, then boot from the liveCD (or flash drive, whatever you use for it).  Select install, then choose the USB drive you want to install to.  It's probably sdb or sdc, depending on how your system detects the drives.  You should be able to tell by the size of the drive.  Follow the prompts and install to the USB drive.  Have the installer put the bootloader on the USB drive, not the default sda1.  You'll need to press Esc or Shift at boot time to get the menu for the drive to boot from if you do that, but I think that's better than having grub search for the USB drive every time you boot, and you won't be able to boot from any other computer using the flash drive unless you put the bootloader on it.  IMO this is far better than using a persistent liveCD version, which is intended for installing to another drive, not for daily use.

---

### Post by d-shade on 2010-06-30
Great I got it to work!!! I guess when I installed to the usb the first time the boot wasn't there which is most likely why it didn't work.

But now it works great on my netbook, now I just need to install the android sdk.

---

