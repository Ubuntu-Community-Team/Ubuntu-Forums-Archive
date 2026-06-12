---
title: "GRUB while using 2 HDD"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by 7franky on 2015-10-06
Hello everyone,

I have installed Windows 8.1 & Ubuntu 14.10 on my primary HDD (1000 gb). Then I've add second HDD (500 gb) and install Ubuntu 14.04.3 on it, but now I have GRUB loaded as command line while starting laptop.
I able to go to BIOS, set first boot option as "ubuntu", save and after such actions goes into usual GRUB menu, choose my installed 14.04.3 and goes further. But again, after restarting laptop I have GRUB as command line.

Fixing with tool "Boot-Repair" helps, but only for 1 restarting of laptop - I see usual GRUB menu only once. Upon next restarting I again have GRUB as command line.

Report of this tool is here:
[http://paste.ubuntu.com/12698803/](http://paste.ubuntu.com/12698803/)

Huge thanks for any tips!

---

### Post by oldfred on 2015-10-06
I see mention of Asus, is this an Asus and what model?

Did you run any work around to get 14.10 to boot in UEFI mode before? That install is now obsolete, but all its kernels add a long list to grub menu.

Is secure boot off?

This user said he just changed boot order in UEFI.
   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)

---

### Post by 7franky on 2015-10-11
Yes, "Secure boot" was disabled in BIOS, but here was enabled "Fast boot". I remember that I've disabled this feature from Windows way, but in some strange reason it was enabled in BIOS way.
After disabling "Fast boot" GRUB initialized succesfully. Thanks for pointing! 						Resolved

---

### Post by oldfred on 2015-10-11
Glad you got it working.
Fast start up in Windows is always on hibernation to speed Windows boot.
And fast boot in UEFI/BIOS is to skip hardware intialization and assume it is all the same hardware as last boot. That also speeds up boot.

Windows requires those settings, as it boots very slow otherwise and it needs these work arounds to make it seem that Window is really booting faster. And for most users it then does boot faster until they have issues. Then repair is more difficult.

---

