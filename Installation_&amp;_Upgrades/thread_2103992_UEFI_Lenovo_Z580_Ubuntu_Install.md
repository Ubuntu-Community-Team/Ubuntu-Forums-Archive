---
title: "UEFI Lenovo Z580 Ubuntu Install"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by locuststorm on 2013-01-11
I've been trying to dual boot Ubuntu 12.10 alongside windows for some time now on my Lenovo Z580 laptop and, as much as I hate to admit it, need help doing so through UEFI. I've been using this guide ([https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")) from the Ubuntu community while attempting to install it.

After I finished going through the install process using the USB (which boots properly), I get the error from SecureBoot stating that the bootloader had failed to verify with access denied.

As such, I ran boot-repair, as recommended by the forums and the community guide, with the following result:

[http://paste.ubuntu.com/1521008/](http://paste.ubuntu.com/1521008/)

Any help that you could offer regarding this would be greatly appreciated! Please let me know if there's anything else I can provide, and I would gladly do so. 

Thank you in advance!

**Additional Information:**
UEFI partition: sda2
Ubuntu partition: sda7
bootloader partition (specified during install): sda2

---

### Post by oldfred on 2013-01-11
Welcome to the forums.

Have you from UEFI menu booted the ubuntu entry? With both secure boot off or on? And have you turned off fast boot as that may cause other issues.

Some computers will only boot the Windows entry (or Redhat).
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

    Other Lenovo's that have worked.
       Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

    
Older, so no secure boot issues.
       How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

Because some UEFI systems only boot the Windows efi files, the work around is to rename the grub file to the Windows file name. Back up entire efi partition first.
       Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)

    
And Boot-Repair under advanced options should offer to backup & rename files.
       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

---

