---
title: "Reboot and install proper boot device?"
date: 2017-03-14
forum: Installation &amp; Upgrades
---

### Post by helloworld90 on 2017-03-14
I installed Ubuntu on my Toshiba laptop but when I go to the BIOS and select boot from the hard drive I get the message
"reboot and select proper boot device." How do I fixed this? the operating system I used to have was Windows 8 if that matters.

---

### Post by ubfan1 on 2017-03-14
Did you install in legacy or UEFI mode?  Your machine that came with Windows 8 used  GPT partitioning on its disk, so if in legacy, you need a 2M grub-bios flagged empty partition, or if in UEFI you need aa 500M EFI FAT partition in addition to the root, swap partitions

---

### Post by oldfred on 2017-03-14
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

What model Toshiba? Issues often common by brand, so other models may be similar.

       
 Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
           
 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)

---

