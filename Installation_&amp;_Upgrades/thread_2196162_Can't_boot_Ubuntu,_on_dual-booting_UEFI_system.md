---
title: "Can't boot Ubuntu, on dual-booting UEFI system"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by henrik.enggaard on 2013-12-28
I've been following the instructions on: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and the boot-repair tool. Grub is showing, but upon booting Ubuntu the screen stays purple and the fans eventually spin down, indicating that there is nothing going on.

I have the following paste from boot-repair: [http://paste.ubuntu.com/6650492](http://paste.ubuntu.com/6650492)

It seems to be related to: [http://ubuntuforums.org/showthread.php?t=2132581](http://ubuntuforums.org/showthread.php?t=2132581)

Thanks in advance

---

### Post by oldfred on 2013-12-28
Welcome to the forums.

It looks like you originally installed in BIOS mode and Boot-Repair converted you to UEFI mode. You need to be sure to have system set to boot in UEFI mode, not CSM/BIOS/Legacy mode, every time you boot as both Windows & Ubuntu now are UEFI. You cannot easily dual boot when systems are not in same boot mode as once you start in one mode you cannot switch (or grub does not work).

It also looks like Boot-Repair did the rename. Only required if you cannot boot ubuntu entry from UEFI menu. With rename booting Windows entry boots into grub also. But you then cannot directly boot Windows from UEFI menu.
 Rename will occure if Boot-Repair sees Windows kernel issues, but may not always be required. 
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]?


 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

You show Intel i915 driver. It may need boot parameters. And a Dell thread said the i915 driver needs CSM on even if booting in UEFI mode?

Follow the procedure for adding nomodeset, but use this instead. At grub menu press e, and replace quiet splash with boot options below.

 Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor
or
 i915.i915_enable_rc6=1



 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

> Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux. 



---

