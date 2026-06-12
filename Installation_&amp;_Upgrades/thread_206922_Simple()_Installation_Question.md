---
title: "Simple(?) Installation Question"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by albatross83 on 2006-06-30
My system is setup with a RAID Array on an add-in card with an XP install.  I added another hard drive on the motherboard's integrated ATA controller to which I wish to install Ubuntu.  I do not want any multiboot options; I simply wish to install Ubuntu to the new drive and I'll raise its boot priority in the BIOS when I want to use it.  XP and Ubuntu can each exist in their own little worlds.

After booting from the Live Desktop CD, the drive assignment is as follows:

hda (Drive 1 of RAID Array w/XP)
hdc (Drive 2 of RAID Array w/XP)
hdh New Empty Drive

I let Ubuntu format hdh, and it proceeded to install.  When I tried to reboot, nothing happened, so I went into the BIOS and raised the boot priority for the RAID Add-In card, only to find that Ubuntu had overwritten the MBR on the RAID, and GRUB was trying to load.  I've since fixed that in the XP recovery console.

So I went back to the live CD, and I can't find any way to configure where Ubuntu installs GRUB.  I'd just like to re-install Ubuntu, but have it install the boot loader to the same drive (/dev/hdh) as it installs the rest of the OS.  So how do I do it?

Thanks in advance.

---

### Post by elglas on 2006-07-01
on the non-live cd install cd, (just what I used) it will give you a bootloader option asking if you want to install the boot loader (grub) to the MBR, select no, and point it to /dev/hdh (your linux drive) now you should be able to set what you boot with your bios pirority

if you have some strange error when trying to boot XP, try specifying no (/dev/hdh) drive in bios (set device to type none and you should be good

cheers

Mike

---

### Post by albatross83 on 2006-07-01
Ah ok, thanks!

---

