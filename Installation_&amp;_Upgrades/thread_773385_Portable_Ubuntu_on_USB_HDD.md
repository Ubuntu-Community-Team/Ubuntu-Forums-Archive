---
title: "Portable Ubuntu on USB HDD??"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by uguy on 2008-04-28
I have a Dell Latitude C600 and installed Ubuntu 7.01 on a new internal HDD (i have winxp pro on the old HD) this is working fairly well, although i'm still fine-tuning some things and converting over to some critical programs.

I would like to mount the new HD in a USB enclosure, re-install the original XP HD in the laptop and run Ubuntu from the USB drive. I'm using a USB/PCMCIA adaptor (StarTech CBUSB0) on the laptop. I don't think the BIOS in this setup will support USB boot. I think i can use a boot CD/floppy to load kernal, etc and then switch to external HD ??

Furthermore, I would like to be able to use the USB HDD as a portable OS so i can use other machines when i travel... i think most newer desktops and laptops would support direct boot from the USB HDD... would i have to modify the Ubuntu installation to use on other machines??

thanks in advance for any help... or, maybe you could point me to where this question belongs :)

---

### Post by coolaj86 on 2008-04-28
Ubuntu on a usb drive:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

Booting grub on a floppy and then the usb drive:
[http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/)
(you can also do a similar process to a cd)

---

### Post by uguy on 2008-04-28
thanks for the info, although i think you're missing the point.. i already have Ubuntu on installed on HD (which i want to make into a usb drive) and i'm operating on a laptop which doesn't normally boot from USB... if all else fails, i may have to go with a thumb drive install....

---

