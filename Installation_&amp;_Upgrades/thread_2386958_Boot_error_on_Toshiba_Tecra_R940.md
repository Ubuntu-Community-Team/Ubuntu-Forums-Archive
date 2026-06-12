---
title: "Boot error on Toshiba Tecra R940"
date: 2018-03-12
forum: Installation &amp; Upgrades
---

### Post by mirijadesky on 2018-03-12
I recently installed ubuntu on my laptop and it is unable to boot. A breif error code pops up which says

Could not get fio for li->DeviceHandle: invalid parameter
Failed to find fs: Failed Parameter
Failed to load image \EFI\BOOT\grubx64.efi:invalid parameter
Start Image () returned Invalid Parameter
After which the laptop simply displays, insert disk into drive and press any key to continue.

---

### Post by oldfred on 2018-03-20
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Toshiba often need to boot a fallback or hard drive entry, not the ubuntu entry. That is at /EFI/Boot/bootx64.efi and Boot-Repair now copies shimx64.efi to be that file. But sometimes all the files including grubx64.efi must also be copied.

Issues are often common by brand across models, so these may apply even if not same model.

 Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
Toshiba Satellite C55-C5241  Windows vs. Ubuntu
[http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1)
Toshiba L50-A-1EH laptop - used bcd edit
[http://ubuntuforums.org/showthread.php?t=2295628](http://ubuntuforums.org/showthread.php?t=2295628)
Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)

---

