---
title: "Ubuntu not booting automatically"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by bolus on 2010-11-10
Hi There,

I'm trying to install ubuntu 10.10 on my mini-pc homeserver. Installation goes fine, but when I reboot it says "no boot device found". I checked the bios, it's set to boot from hdd, so that should be fine. When I press F10 during post, I can enter the boot menu, where only my hdd is listed. When I press enter it boots just fine. I tried using 1 partition only, tried multiple partitions, but it makes no difference. I didn't change anything to the bootloader configurations during install, just used standard settings, which is install bootloader to sda/hda. 

Does anybody know why it's not booting automatically?

---

### Post by P4man on 2010-11-10
Weird.

Perhaps you can look in the bios, if there is an option to set which drive to boot from. In most bioses you have one place to define boot order (hdd, cd, usb etc), that one you set correctly apparently, but usually there is another one where you determine the order for various harddrives. Perhaps its set to your usb stick (which some bioses identify as a hdd) ? 

Another thought would be to disable raid in the bios if its enabled, experiment with sata/ide/achi settings.

---

### Post by bolus on 2010-11-10
Ok, so the problem should be in the bios? I mean, this could not be a problem with the bootloader?

---

### Post by P4man on 2010-11-10
Sounds like a bios setting/issue to me, since manually selecting the drive boots fine, it doesnt sound like anything is wrong with the bootloader. 

The error message "no boot device found" also isnt one from grub, afaik.

---

### Post by bolus on 2010-11-10
You're right it's from the motherboard so that's why I share the same thought, but to make it even more weird... I tried installing win XP, it boots just fine.
 
So my conclusion is the motherboard checks the master boot record, didn't find a bootloader (allthough grub is there) and returns an error. Maybe I need to flash the bios to a later version, because this is a strange problem.

---

