---
title: "no boot device available dual boot dell xps8500"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by yang-hongk on 2014-09-30
Dear All,

I am using a dell XPS8500 machine with Ubuntu 12.04 and pre-installed Windows 8. It worked well until yesterday. When I rebooted the machine, I got the following error message:
```
No boot device available
Strike the F1 key to retry boot, F2 to run the setup utility
SATA 0: Installed
SATA 1: Installed
SATA 2: None
SATA 3: None
MSATA1: None
```

I used a usb drive running [Linux Secure Remix]("https://help.ubuntu.com/community/LinuxSecureRemix") and tried to fix this problem using Boot-Repair. I chose the option of Recommended repair but it does not work. The log file is in [http://paste.ubuntu.com/8464103/](http://paste.ubuntu.com/8464103/).

BIOS Option:
```
Boot Mode: UEFI
Load Legacy OPROM: Disabled
Secure Boot: Disabled or Enabled (tried both)
```

Any help is appreciated.

---

### Post by oldfred on 2014-10-02
If system is new enough to have Windows 8 pre-installed, then 14.04 may have been better as that included all the Dell Sputnik additions you need for system to run well.

You show that at some time you had used Boot-Repair to rename the Windows efi file:
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

I did not think Dell needed that rename, but the actual Windows boot file bootmgfw.efi is really grub or shim and you then can only boot Windows from grub menu not from UEFI. That is one of several fixes for HP, Sony and a few others that have modified UEFI to only boot Windows. But Dell's typically have not needed it.

Best to undo the rename and see if you can directly boot Windows from UEFI menu. Then we can work on booting Ubuntu.

      
 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

This says you may need to have legacy on even if booting in UEFI mode. May apply to all Dell with Intel.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

The now newer 14.04 should be even easier:
      
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

You also are now missing an essential but I guess not that essential till you need it, Windows  system reserved partition.
       Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

            Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

---

