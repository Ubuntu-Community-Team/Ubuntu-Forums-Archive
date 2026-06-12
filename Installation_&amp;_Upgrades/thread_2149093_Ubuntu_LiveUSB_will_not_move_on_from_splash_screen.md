---
title: "Ubuntu LiveUSB will not move on from splash screen"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by lolPotato on 2013-05-27
Hi

On My old computers, I have used linux a lot and am fairly good at it.

Recently, I decided to build a custom build pc, Here are the specs
In Win em series case
Asus fm1a75-m pro r2 motherboard with UEFI:frown:
amd a4 apu 2.5ghz dual core.
Samsung 100gb enterprise ssd
1tb seagate hard drive

I am however, suspicious of the UEFI bios.
Here's what I have disabled
-Secureboot
-Fastboot
What I have changed:
-Chose startup os to 'Other OS'

Help would be greatly appreciated.

Thanks,
lolPotato

---

### Post by ubfan1 on 2013-05-27
Here's the starting point:  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
If you can disable UEFI in the settings, you are back to familiar territory.  If not, just use gpt partition tables on your disks, make a small (250M) FAT partition with the boot flag for the EFI files, and hopefully any Ubuntu 64 bit install after 12.04.2 should work for you.

---

