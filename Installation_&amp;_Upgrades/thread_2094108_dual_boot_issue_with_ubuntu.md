---
title: "dual boot issue with ubuntu"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by stpalli on 2012-12-12
[http://paste.ubuntu.com/1428543/](http://paste.ubuntu.com/1428543/)       

      system: lenovo thinkpad x230, preinstalled with windows 8
      
      symptom: i installed ubuntu on it and then tried booting into       windows 8 but could not. i ran a boot-repair and that did not work       either.
      
      quick help would be greatly appreciated.
      
      thanks a lot,
      shashi

---

### Post by debodas on 2012-12-12
Are you using GRUB?
If not I'd install GRUB to /dev/sda

---

### Post by oldfred on 2012-12-13
Welcome to the forums.

With UEFI you do not install grub to the MBR. You actually have the new gpt partitioning not the very old MBR(msdos) partitioning.

The default boot entries that grub2's os-prober creates do not work. They are the BIOS type entries and you have to have an efi type entry.
Boot-Repair added new entries and those should chain to the Windows efi partition.

Have you turned fast boot off? That often causes issues.

Can you boot Windows directly from UEFI menu.

It looks like with your UEFI menu you have many options. You have 19 or Ubuntu set as first and 18 or Windows as second.

BootOrder: ```
0019,0018,0000,0001,0002,0003,0007,0008,0009,000A,000B,000C,000D,000E,000F,0011,0010,0012
Boot0000  Setup
Boot0001  Boot Menu
Boot0002  Diagnostic Splash Screen
Boot0003  Lenovo Diagnostics
Boot0004  Startup Interrupt Menu
Boot0005  ME Configuration Menu
Boot0006  Rescue and Recovery
Boot0007* USB CD
Boot0008* USB FDD
Boot0009* ATAPI CD0
Boot000A* ATA HDD0
Boot000B* ATA HDD1
Boot000C* ATA HDD2
Boot000D* USB HDD
Boot000E* PCI LAN
Boot000F* ATAPI CD1
Boot0010  Other CD
Boot0011* ATA HDD3
Boot0012  Other HDD
Boot0013* IDER BOOT CDROM
Boot0014* IDER BOOT Floppy
Boot0015* ATA HDD
Boot0016* ATAPI CD:
Boot0017* PCI LAN
Boot0018* Windows Boot Manager
Boot0019* ubuntu
```

How did you shrink Windows? Did you use Windows MMC to shrink itself. And reboot so it runs chkdsk? Not sure which of the boot choices for rescue or repair are the standard Windows. Do not run the Lenovo repair as that will probably restore system to as purchased.

Older
       How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

---

### Post by CorruptDNA on 2012-12-13
maybe u installed ubuntu on the drive where windows was and accidentally formatted it :o

---

