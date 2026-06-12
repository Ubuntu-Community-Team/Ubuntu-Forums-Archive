---
title: "Lubuntu won't start on 7 yr old Toshiba laptop"
date: 2018-06-14
forum: Installation &amp; Upgrades
---

### Post by sol33t303 on 2018-06-14
My friend has lent me his 7 yr old Toshiba laptop to install linux on it. When I try and boot into my USB with Lubuntu however it shows "do_IRQ: 1.55 No irq handler for vector" and below that "Problem loading UEFI:db x.509 certificate (-65)". This is after getting to grub and trying out Lubuntu without installing. I also tried manjaro and Linux Mint, however they don't work either. Manjaro just shows a blank screen and Mint gets stuck at "starting version 250"  (or something close to that, I can't remember the specific number). My friend is new to Linux so I want to create a dualboot with Windows 8.

---

### Post by ajgreeny on 2018-06-14
How did you create the live USB disk which you're using?

The error message you saw > Problem loading UEFI:db x.509 certificate (-65) suggests that you are trying to install in UEFI mode which is unlikely to be the computer's firmware type, as I suspect a 7 year old machine used MBR.

Have a read through the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which may help you figure out which mode you used, and which you really need to use.

---

### Post by sol33t303 on 2018-06-14
After setting in the laptops bios to boot  in bios mode that error seems to have been fixed (though if the laptop dosn't support UEFI why would they have the option to boot in UEFI mode in the bios?). However the other error is still there. I created the live USB disk using dd on my PC.

---

### Post by ubfan1 on 2018-06-14
Did you ever run the media check/memory check from the install media?  dd can't work around bad blocks like a filesystem can, so there might be a problem with the media.  UEFI has been around since the 90s, not that every UEFI machine had Windows installed in UEFI mode.  My 7 yr old Lenovo came with Win7 on a msdos partitioned disk, so legacy mode, but will boot a UEFI disk just fine (no secure boot though, just UEFI).

---

