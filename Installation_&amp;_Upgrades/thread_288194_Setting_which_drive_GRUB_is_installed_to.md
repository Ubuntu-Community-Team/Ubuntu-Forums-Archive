---
title: "Setting which drive GRUB is installed to"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by wolrahnaes on 2006-10-29
I have a nVraid fakeraid and multiple USB external drives in my system.  When installing, all of these get lower device numbers (/dev/sdX) than the main hard drive, even though the main drive is on SATA port 1.  Both of the nvRAID drives appear separately, even when I have those ports turned off in the BIOS.

The installer does not make it clear where the bootloader is going, and based om past experience where 5.04 installed the bootloader to my USB drive I'm wary of installing with these drives attached for fear of nuking the RAID 0 where I keep all my music and videos (granted, not the most important stuff, but it would still be a pain to lose).

I installed 6.06 by physically disconnecting every hard drive except the main one for the install.  This worked, but when I plugged in the other drives again GRUB freaked out and I had to manually tweak its configuration to be able to boot.

I'm preparing to nuke and reinstall for 6.10 (the nVidia graphics driver has never worked on my 6.06 install, so it's not worth keeping and trying to uprade) so what I want to know is can I just tell the installer that my boot drive is for some retarded reason /dev/sdc and that it should put GRUB there?

edit: I should mention my drive configuration, physical plugs and how they show up under Linux.

_nForce4 Controller_
IDE1 Master: DVD+-R/W /dev/hda
IDE1 Slave: None
IDE2 Disabled
SATA1: Seagate 7200.8 250GB (OS Drive) /dev/sdc
SATA2: Seagate 7200.9 250GB (nvraid stripe) /dev/sda
SATA3: Seagate 7200.9 250GB (nvraid stripe) /dev/sdb
SATA4: None

_Silicon Image Controller_
Disabled

They show up in the correct order in Windows.

---

