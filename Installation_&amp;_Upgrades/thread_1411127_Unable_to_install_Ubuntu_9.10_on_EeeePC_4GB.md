---
title: "Unable to install Ubuntu 9.10 on EeeePC 4GB"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by manolomanolo on 2010-02-19
Hi to all.

I have downloaded the desktop version of ubuntu 9.10 for PC (not the netbook version) but I am unable to install it on the EeeePC.

I created a live cd using UNetBootin and also "USB Startup disk creator". The Live USB is created correctly (at least it is what those program say) but the installation is without success.

I have tried different BIOS settings. Between them:

Boot -> Hard Disk Drives:
1st drive: hdd:... [it's the hard disk]
2nd drive: USB:USB2.0 CardReal [it's my SD card]
3rd drive: SanDisk Cruzer [it's my pen drive]

Boot -> Boot Device Priority
1st Boot Device: Removable device
2nd boot Device: Disabled

Please note I cannot see any explicit reference to SD card or USB pen drive in the boot device priority despite I have tried to make both a "live bootable" using those programs.

In this case, the netbook is not able to find any "boot device" so I can only restart to BIOS and try other settings.
In case of choosing SanDisk Cruzer as "1st drive" I can also see it into the Boot Devices and select it as first boot device. In this case the installation starts: I am able to select the language and also select "install ubuntu" but then I get an error message:

Busy box v1.13.3 [...]

(initramfs) /init: line 1: can't open udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci[...]

and some other stuff.

I have also tried to download the ISO image from different mirrors and rebuild the live usb. I have also tried to select "**check cd for error**" or something similar from the installation boot menu and finally selected "**try ubuntu without installing**" or something but no success anyway: I always get the same error.

Any suggestion please?

Thanks.

---

### Post by darkod on 2010-02-19
Did you try with the SD card removed? I remember one case where ubuntu was not installing correctly with SD card in the netbook.

And where do you plan to install it? Onto the SD card? 4GB is pretty small for ubuntu, even for xubuntu. I'm not sure it can work but I don't have much experience with the netbooks with small SSDs.

---

### Post by manolomanolo on 2010-02-19
Wow! Awesome!

Removing the SD card made the job!

Now I am installing Ubuntu 9.10 on that EeePC !!!

No, I am not goinh to install it on the SD card but on the hard drive and use the SD card as external storage.

Thanks for your support!!!

---

