---
title: "wd 3tb ubuntu 11.04 64 desktop how?"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by juggy on 2011-08-14
Hi,

i am struggling with the below install
it wont boot after i install ubuntu 11.04 64 bit desktop

I am trying to install ubuntu to use as an nas / desktop

Hardware:

AMD A8-3850
Gigabyte A75-UD4H
8GB DDR3
western digital green 3 TB

I have tried just letting the installer run through - it wont boot after it installs

i understand i may need to have a grub bios partition the only option i saw was EFI

if this is the same thing how do i allocate the rest of the partitions

The bios on my board is supposed to support 3tb
I have also tried setting the cd/dvd in bios to EFI before i let the ubuntu dvd boot

at this point i am really pulling my hair out

I have also updated the bios to the newest (F4)

Thanks,

Kevin

---

### Post by dino99 on 2011-08-15
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by juggy on 2011-08-15
> **dino99 said:**
> [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
ok thanks but can someone give me a step by step

i am really confused by that page too many scenarios

---

### Post by kylerxiii on 2011-08-20
Yes a step by step would be great I'm having the same type of issue with a: 

AMD A8 3850
ASUS F1A75-V PRO
West digital 1TB
8GB DDR3-1600 

You are the only other person on the internet i could find with the same sort of issue. Good luck to us both

---

### Post by oldfred on 2011-08-20
I do not have UEFI but hope to soon, so I have saved some info: Others that know more can add.

With 3TB you need to be using gpt partitioning not MBR(msdos). Then you have to decide if you have BIOS or UEFI. Most UEFI systems still will boot with BIOS mode. BIOS is the original PC system from the 80's, UEFI is the new system. If you want to install windows also you have to use UEFI.

If BIOS & gpt you need the bios_grub partition of 1MB (any where on drive). IF UEFI you need the efi partition as the first partition in the drive. You can create both if you want and then if you change later you have the other partition available.

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)
How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Updates - Avidanborisov created compile script
[http://ubuntuforums.org/showthread.php?t=1772310](http://ubuntuforums.org/showthread.php?t=1772310)
UEFI issues srs5694 post #58  Solutioin see above
[http://ubuntuforums.org/showthread.php?t=1719851&page=6](http://ubuntuforums.org/showthread.php?t=1719851&page=6)
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

---

### Post by igorc on 2011-10-26
Hi guys,

I have similar setup on AsRock board:

AMD A4-3400
AsRock A75M
4GB DDR3
WD green 1TB/SATA3

Wonder if you managed to install 11.04 on your A75 boards?

Thanks

---

