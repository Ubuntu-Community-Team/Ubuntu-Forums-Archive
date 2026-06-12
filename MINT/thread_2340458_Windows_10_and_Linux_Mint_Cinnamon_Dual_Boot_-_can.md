---
title: "Windows 10 and Linux Mint Cinnamon Dual Boot - cannot boot"
date: 2016-10-18
forum: MINT
---

### Post by mylestogobeforeisleep on 2016-10-18
Hello,

As the title says, I am trying to dual boot Windows 10 and Linux Mint Cinnamon. I have successfully installed linux mint in uefi mode onto a separate partition, but the bootloader does not recognize that the bootable partition exists. I have tried running the boot-repair utility but it still is not booting into linux mint. It also does not appear when I do an F2 or F12 on startup to see bootable devices.

I have spent many hours on this already so any help would be greatly appreciated. Hopefully I can learn something from this.

Thank you in advance!!

The output from boot-repair can be seen here:
[http://paste2.org/yNttz5Yh](http://paste2.org/yNttz5Yh)

About my laptop:
         Operating System: Windows 10 Home 64-bit (10.0, Build 14393) (14393.rs1_release_inmarket.161004-2338)
                 Language: English (Regional Setting: English)
      System Manufacturer: Acer
             System Model: Aspire E5-575G
                     BIOS: V1.04
                Processor: Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz (4 CPUs), ~2.6GHz
                   Memory: 16384MB RAM
      Available OS Memory: 16258MB RAM
                Page File: 5102MB used, 13587MB available
              Windows Dir: C:\WINDOWS
          DirectX Version: DirectX 12
      DX Setup Parameters: Not found
         User DPI Setting: Using System DPI
       System DPI Setting: 120 DPI (125 percent)
          DWM DPI Scaling: UnKnown
                 Miracast: Available, with HDCP
Microsoft Graphics Hybrid: Supported
---------------
Display Devices
---------------
          Card name: Intel(R) HD Graphics 520
       Manufacturer: Intel Corporation
          Chip type: Intel(R) HD Graphics Family

---

### Post by oldfred on 2016-10-19
It looks like you installed grub to the ESP's boot sector for a BIOS boot. You may need to fix that. 

But all Acer's have a unique requirement of setting a UEFI supervisory password to open more options, and in UEFI drilling down to /EFI/ubuntu and setting trust on ubuntu/grub's .efi boot files.
Also make sure you have newest UEFI from Acer. Some older threads mention downgrading to an older UEFI, but newer threads say Acer fixed it and newest UEFI works. May depend on what version of UEFI you have.

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912) 
    
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    [URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL] This is for NTFS as it keeps backup partition boot sector. Not sure if FAT32 also has backup or not.
 PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery) 

The only other way I know to fix it, would be fully backup, delete FAT32 partition. Then create new FAT32 partition with boot flag and restore EFI boot files. UEFI entries may need updating as it knows GUID of partition and recreating it may change those. Full cold reboot may add entries or you have to use efibootmgr to add all the entries.

---

### Post by mylestogobeforeisleep on 2016-10-28
@oldfred thank you so much! I thought nobody had replied since I never got notified, but randomly logged in this morning and saw your reply. Thanks you for such a detailed response! I will take a look this weekend and see if I can figure out a way to fix it.

---

### Post by mylestogobeforeisleep on 2016-11-17
Just wanted to give a quick update. I followed the steps in this link and it worked like a charm:
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[URL="http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot"]http://askubuntu.com/questions/62741...-not-dual-boot

[/URL]
I'm posting this from my linux mint partition so it worked great! Thank you oldfred!

---

### Post by oldfred on 2016-11-17
Glad you got it working.

You can change to solved.

---

