---
title: "ISO-USB-Stick Version 20.10--- screen freeze after ramp up"
date: 2020-12-05
forum: Installation &amp; Upgrades
---

### Post by nexusquax on 2020-12-05
Hi,

because of problems with my xubuntu 18.04 internal mic (unplugged!?) 
my idea was to swing over to xubuntu 20.10.
With  "try xubuntu" I would have checked the performance and whether the internal mic will work?!
but
my problems started with ramping up the ISO-USB 20.10 version.
During the ramp up I just can see the install-screen afterwards the screen freezes.
No more keyboard, no more mouse...nothing, just a hard switch off ends the drama.
Same problem in the nomodeset mode.
Same problem with the 20.04 version.
By the way my dualboot with xubuntu 18.04 and win10 works like a glance!!

My brand new notebook:
Omen 17-cb0204.
I already did a bios update.

Any idea?
Thanks a lot and sorry for my terrible English.

cheers
harry

---

### Post by grahammechanical on 2020-12-05
A wild guess. Check in the UEFI settings if there are USB speed settings. I have a very old machine. It has two speed settings - High speed and full speed. Over the years three USB standards have developed. USB 1; USB2; USB3. The latest motherboard needs to be backwards compatible with all the standards. The USB stick itself will be made to one of those standards. It does not matter how fast the USB can transfer data it will only transfer data at the speed the USB drive is designed to push the data out.

Just giving some thoughts of why data transfer from a memory stick might not be as fast as we expect it to be.

Regards

---

### Post by nexusquax on 2020-12-06
thanks a lot for your idea, 
but I had no problems to manage the 18.04 ISO-USB xubuntu version "try xubuntu" and "install xubuntu" by my usb-stick.
It worked perfekt after I added the nomodeset in the bootup menue.

When the ramp starts there some errors in the first lines, maybe this could be a problem?
In the first line are written:
ACPI Bios error Couldn't resolve symbol ????!!
Initramfs Unpacking failed Decoding failed???!!

cheers

---

### Post by CelticWarrior on 2020-12-06
> [COLOR=#000000]It worked perfekt after I added the nomodeset in the bootup menue[/COLOR]
It didn't because it couldn't.
You knew to know your hardware, namely that it has a Nvidia graphics card. This implies you need to disable Secure Boot and install Nvidia drivers.
With 20.04 you can just select the option for third-party drivers, codecs, firmware, etc. and the installer will do it automatically but you must disable Secure Boot in UEFI first. That should be all.

---

### Post by nexusquax on 2020-12-06
Thank you mate,

I disabled the secure boot all the time when I dealed with dualboot installation.
Where shall/can  I select the third-party drivers and so on, when the screen freezes?
regards

---

### Post by CelticWarrior on 2020-12-06
That is selected during the installation process. If you didn't select it then you can now search for the recommended drivers in Additional Drivers.

---

