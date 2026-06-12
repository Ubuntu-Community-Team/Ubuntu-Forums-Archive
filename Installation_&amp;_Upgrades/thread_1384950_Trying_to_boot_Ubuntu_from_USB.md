---
title: "Trying to boot Ubuntu from USB"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by 95lcecil94 on 2010-01-19
Hello, I've been trying to boot Ubuntu from a USB flash drive, but has so far been unsuccessful.

I've tried creating a bootable drive with both UNetbootin and USB Startup Disk Creator.

Changing the boot order in my BIOS to this does no good.

Removable Device
Hard Disk
CD-ROM (might be called DVD, but whatever)
Network

It just continues to boot from the HDD anyway.

Pressing escape prior to booting will give me the option to choose the USB drive, but it still skips it.

What could I possibly be doing wrong?

---

### Post by PRC09 on 2010-01-19
In the bios(on mine it is under integrated peripherals) make sure your usb controllers are enabled because even if they are not you can still set the boot from removable device option(Advanced Bios Features) but of course the machine cant see them.Also on some machines you have to go for a complete shut down for the setting change to take effect,the reboot doesnt change the setting altho it says it has.Hope this is of some help....If not post back your machine make and specs and someone should be able to help....

---

### Post by 95lcecil94 on 2010-01-19
> **PRC09 said:**
> In the bios(on mine it is under integrated peripherals) make sure your usb controllers are enabled because even if they are not you can still set the boot from removable device option(Advanced Bios Features) but of course the machine cant see them.Also on some machines you have to go for a complete shut down for the setting change to take effect,the reboot doesnt change the setting altho it says it has.Hope this is of some help....If not post back your machine make and specs and someone should be able to help....
Thanks, I'll try it now.

EDIT: It worked! Thanks! A simple shut down was the solution, although, it still didn't boot from the USB stick, when having "Removable Device" set as first priority. Pressing escape right before it starts booting lets me choose a boot device, and choosing the USB device worked, it didn't before. though.

---

### Post by presence1960 on 2010-01-19
When you boot with the flash disk go into BIOS and look under Hard Disk Boot Order. On my machine any flash disk under 4 GB shows up in there. Just move the flash disk to the top of the order, save changes to CMOS and continue booting

---

