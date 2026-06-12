---
title: "Grub Issue, Command line, external drive"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Rodendack on 2006-06-20
Hello,

So, I Installed Ubuntu on an external drive... after the final reboot xp runs normally and if I disable the "inside" hd and boot using the external drive I only get a command line that says "GRUB _" and it does nothing, I waited a long time and it does nothing, what did went wrong?



my crappy pc

Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 1
           Language: Spanish (Regional Setting: Spanish)
System Manufacturer: HP Pavilion 04
               BIOS: Award Medallion BIOS v6.0
          Processor: Intel(R) Pentium(R) 4 CPU 1.60GHz, ~1.6GHz
             Memory: 512MB RAM
          Page File: 247MB used, 1002MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.0001.0904 32bit Unicode

Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 14.9 GB
Total Space: 35.5 GB
File System: NTFS
      Model: Maxtor 4D040H2

      Drive: D:
 Free Space: 13.4 GB
Total Space: 13.4 GB
File System: FAT32
      Model: TOSHIBA MK4025GAS USB Device

      Drive: G:
 Free Space: 5.3 GB
Total Space: 8.5 GB
File System: FAT32
      Model: TOSHIBA MK4025GAS USB Device

      Drive: H:
 Free Space: 3.0 GB
Total Space: 8.2 GB
File System: FAT32
      Model: TOSHIBA MK4025GAS USB Device

      Drive: I:
 Free Space: 0.8 GB
Total Space: 1.0 GB
File System: FAT32
      Model: TOSHIBA MK4025GAS USB Device

      Drive: M:
 Free Space: 2.9 GB
Total Space: 3.8 GB
File System: FAT32
      Model: TOSHIBA MK4025GAS USB Device

      Drive: E:
      Model: HP CD-Writer cd16e
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.1106 (Spanish), 8/29/2002 01:27:56, 47488 bytes

      Drive: F:
      Model: HITACHI DVD-ROM GD-8000
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.1106 (Spanish), 8/29/2002 01:27:56, 47488 bytes

      Drive: J:
      Model: Generic CD-ROM SCSI CdRom Device
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.1106 (Spanish), 8/29/2002 01:27:56, 47488 bytes

      Drive: K:
      Model: Generic CD-ROM SCSI CdRom Device
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.1106 (Spanish), 8/29/2002 01:27:56, 47488 bytes

      Drive: L:
      Model: Generic CD-ROM SCSI CdRom Device
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.1106 (Spanish), 8/29/2002 01:27:56, 47488 bytes

---

### Post by yager on 2006-06-20
Check out this thread.

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

I installed Ubuntu on my external Seagate drive and have had no problems when using this method.  It may be that Grub can't get to the files it needs in the boot directory.  Try these steps and let us know if it improves the startup.

---

### Post by Rodendack on 2006-06-21
[QUOTE=yager]Check out this thread.

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

I installed Ubuntu on my external Seagate drive and have had no problems when using this method.  It may be that Grub can't get to the files it needs in the boot directory.  Try these steps and let us know if it improves the startup.[/QUOTE]


thank you mr. bender bending rodriguez, I did a search about grub but I didn´t find that thread, I´ll try it out tomorrow ;)

---

