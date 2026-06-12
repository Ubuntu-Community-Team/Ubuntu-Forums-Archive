---
title: "anyhelp? Boot Ubuntu on ACER E 13 (ES1-311-C4Q6)"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by hello5 on 2015-08-01
Hello, have recently installed the latest Ubuntu version from flash drive on an ACER E 13 (ES1-311-C4Q6) notebook, 

installed the o/s image to flash using: Linux Live USB creator -from windows

image: Ubuntu 14.04.2 LTS (64bit)

opted to format the HD before installing (removed windows,) installation works fine, however when rebooting my notebook solemnly declares - NO BOOTABLE DEVICE

have tried reinstalling, and have changed boot orders around, have reset boot order in BIOS to standard but the o/s is still not found.

I am currently using UBUNTU from the flash drive and can see the O/S files are accessible on the hard drive?

kinda out of ideas...............

THANKYOU ***

---

### Post by Vladlenin5000 on 2015-08-01
Hi and welcome.

ACER ES1-311-C4Q6 is a UEFI enabled system. This means there's a lot more to learn in order to install, particularly in dual boot scenarios - not the case - and even with Ubuntu as a single OS it often needs some parameters in BIOS/UEFI like disabling secure boot - shouldn't be needed now but some systems won't let you boot anything other than Windows with secure boot on. There are also other settings that may need to be changed.

---

### Post by hello5 on 2015-08-01
Ok thankyou I will look into BIOS further...

---

### Post by hello5 on 2015-08-01
OK have experimented with the BIOS thanks to your advice.

I have tried changing modes to LEGACY and seperately disabling SECURE BOOT in UEFI however this did'nt help.

The other obvious option I have after setting a password: To set UEFI files as trusted in the database

this has given me some success.

It takes me into the HD displaying files...

shimx64.efi
grubx64.efi
MokManager.efi

BIOS then asks for a boot description and a YES/NO value for each file. Changing these setting around I am able to reach the SHIM boot screen however none of the options here results in success...

I had thought GRUB load was needed possibly?

Will research more myself but otherwise any help from anyone would be great? ... ...

---

