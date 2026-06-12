---
title: "My HDD is not detected"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by agracey on 2007-01-17
I just built a computer and am trying to install ubuntu on to it. I can boot into the Live CD but then the installer doesn't recognise my SATA HDD(s), I have installed SUSE (SLED 10) but would rather have ubuntu. To install suse I had to use the safe mode with the following kernel parameters:

idewait=50 i8042.nomux psmouse.proto=bare irqpoll pci=nommconf apm=off acpi=off mce=off barrier=off ide=nodma

I tried to boot ubuntu with these and it didn't load. SUSE recognises my drive with only the previous parameters. Are there any additional parameters that I should know about.

Here is the low down on my box

AMD 64-bit X2 4200
sapphire crossfire xpress 3200
gigabyte geforce 7900 GS
M-audio Delta-44
IDE CD
2 SATA HDD
usb mouse
usb keyboard
dual moniters

---

### Post by Lucardo Mamones on 2007-01-17
are you using the motherboard raid? 

check in the bios if you have an option to change the SATA mode from RAID to IDE. 

Did the trick for me.

---

