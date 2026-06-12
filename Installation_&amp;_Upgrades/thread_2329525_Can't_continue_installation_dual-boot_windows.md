---
title: "Can't continue installation dual-boot windows"
date: 2016-07-02
forum: Installation &amp; Upgrades
---

### Post by manvas on 2016-07-02
Greetings,
I have a problem. Once installed Windows 7 and it restarted i can't go to windows. When boot windows CD and click repair->continue it goes straight to kubuntu. Tried to fix grub, but it don't show windows at grub highlights. Tried to add it manually, but it can't find disk. Any suggestions?

/etc/grub.d/40_custom:
```
[FONT=monospace][COLOR=#000000]#!/bin/sh[/COLOR]
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Windows 7' {
set root='(hd0,2)'
#search --no-floppy --fs-uuid --set 02589CD3589CC6B7
chainloader +1
}

[/FONT]
```
boot-info:
[http://pastebin.com/hZQ2Mnf6](http://pastebin.com/hZQ2Mnf6)

---

### Post by grahammechanical on 2016-07-02
hd0,2 = first hard drive, second partition = sda2. You do not have any Windows boot files in sda2. I do not think that you do. Ubuntu is installed in EFI mode. There are Ubuntu efi boot files in sda2. Is Windows 7 installed in BIOS/Legacy/CSM mode? If so, then Ubuntu will not be able to load Windows from the Ubuntu (Grub) boot menu.

Ubuntu & Windows must be installed in the same mode. Either efi or bios. I am just guessing.

set root='(hd0,2)' is the Ubuntu partition and where the Ubuntu boot files are. Try set root='(hd0,3)' for that is the Windows partition and where the Windows boot files are.

Regards.

---

### Post by oldfred on 2016-07-03
Was Windows on a BIOS boot MBR partitioned drive, before you installed Ubuntu in UEFI boot on a gpt drive?
Your Windows shows no efi boot files in ESP - efi system partition.
And does not have the system reserved partition that is the default with all normal UEFI Windows installls. And you show all three Windows boot files in sda3 which is a more typical BIOS boot configuration of Windows booting from one NTFS partition.

Windows can only boot from gpt partitioned drive in UEFI mode.
Windows can only boot in BIOS mode from MBR(msdos) partitioned drive.
UEFI & BIOS are not compatible. Once you start booting in one mode you cannot switch modes, or in effect can only dual boot systems installed in same boot mode from grub menu.

Windows 7 default install also is normally BIOS with MBR partitioning when installing from DVD. You have to copy to flash drive and move some files around to have /EFI/Boot/bootx64.efi which is the file name used by UEFI to boot external devices.

       Convert Windows 7 install to UEFI
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)
[URL="http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx"]http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx
[/URL]
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 

[       ]("http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx")
  How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html) 
    [URL="http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx"]
[/URL]

---

