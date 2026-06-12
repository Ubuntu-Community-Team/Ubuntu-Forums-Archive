---
title: "Can't Install On Samsung Ativ Book 9"
date: 2015-01-12
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2015-01-12
This seems impossible, I've been at it for 2 days.

The computer came with Windows 8 but I immediately wiped it and tried installing Ubuntu 14.10. I have tried the following:
- installing in CRM mode
- installing in UEFI mode
- running Boot Repair 35 times
- installing from 2 different flash drives
- installing 2 separate downloads of 14.04 and 14.10

Every time I boot up the laptop it shows me a black screen with white lettering:> All boot options are tried.
Press <F4> key to recover with factory image using Recovery
or any other keys for next boot loop iteration.

I don't see a splash screen, Grub, nothing but this in the bootup sequence.

---

### Post by Maheriano on 2015-01-12
I found this in another post and it worked perfectly:

> 1) Boot into live installer
2) sudo mount /dev/sda1 /mnt
3) cd /mnt/EFI
4) mkdir boot
5) sudo cp ubuntu/grubx64.efi boot/bootx64.efi
6) Remove UBS key and reboot

---

