---
title: "cannot autostart"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by ewuntu on 2016-05-10
Howdy.
Comp. will not autostart downloaded Xenial Xerus without wubi on XP or Win7 OS.
Cannot find any setting for UEFI, Legacy or Secure Boot enable/disable in the BIOS.
The downloaded file was burnt to a DVD. If BIOS is set to boot from CD it does boot
from DVD. If set to boot from removable it does not read the USB.
Stuck. Any suggestions welcomed.

---

### Post by oldos2er on 2016-05-10
Wubi is no longer included in the 16.04 ISO; it hasn't been supported for a long time anyway.

Please tell us the make and model of your computer, and the BIOS and version if you know it.

---

### Post by ewuntu on 2016-05-10
oldos2er
comp. is DIY 10 + yrs
motherboard ASUS M2N SLI
Phoenix Award BIOS v 6.00pg revision 0903

---

### Post by Bucky Ball on 2016-05-10
CPU and amount of RAM please. The motherboard details only are not much use, sorry. ;)

---

### Post by grahammechanical on 2016-05-10
Are you expecting the Ubuntu install media to autostart in Windows? That cannot happen with 16.04 because wubi.exe is no longer included. It was incompatible with Windows 8 and it has not been developed to be compatible with Windows 8 or 10.

And because no development work is being done on wubi.exe there is no point in using wubi.exe with Windows 7. Besides, this forum is unable to offer support to Ubuntu installed using wubi.exe. There are too few users able or willing to provided that support.

Regards.

---

### Post by ewuntu on 2016-05-10
Bucky Ball
CPU AMD Athlon 64 Processor
RAM 2G

---

### Post by Impavidus on 2016-05-11
> **ewuntu said:**
> Howdy.
Comp. will not autostart downloaded Xenial Xerus without wubi on XP or Win7 OS.And indeed it should be without wubi. But you don't run Ubuntu on Windows, you run it on bare metal.
> Cannot find any setting for UEFI, Legacy or Secure Boot enable/disable in the BIOS.
(...)
If set to boot from removable it does not read the USB.
Stuck. Any suggestions welcomed.Not surprising with a 10 year old computer. Back then there was nu UEFI or secure boot, so by default you're using old fashioned bios and no secure boot. Which makes things easier. I also have an 11 year old computer now running Xubuntu Xenial Xerus which doesn't boot from usb. Many old computers cannot boot from usb, or it only works on some usb ports or with some usb drives and only some bootable usb disk creators.
> The downloaded file was burnt to a DVD. If BIOS is set to boot from CD it does boot
from DVD.So you can boot a live dvd? Then what's the problem?

---

### Post by ewuntu on 2016-05-11
[COLOR=#000000][I]Impavidus

"The downloaded file was burnt to a DVD. If BIOS is set to boot from CD it does boot[/I][/COLOR]
[COLOR=#000000][I]from DVD"

sorry that should read  "it does not boot from the DVD"

You said run on bare metal. What is that? I am not trying to run it on Windows. The comp. I am trying to install it on has XP as the OS now.  [/I][/COLOR]

---

### Post by Bucky Ball on 2016-05-12
'Bare metal' means you are installing directly to the hard drive/SSD, not installing via *Wubi* inside Windows. 

You have Ubuntu installed *alongside* Windows on its own partition (bare metal), not *inside* Windows as a Wubi install?

---

### Post by ewuntu on 2016-05-12
Bucky Ball
My intention is to install Ubuntu alone on the drive.

---

