---
title: "Dual boot Windows/Ubuntu 13.10"
date: 2014-11-24
forum: Installation &amp; Upgrades
---

### Post by runxctry on 2014-11-24
Windows doesn't boot.  

Here's the boot-repair pastebin from my attempts to automatically fix this.  The computer just restarts when Windows is selected.  Before I ran boot-repair, selecting "Windows" immediately returned me to the GRUB menu.

[http://paste.ubuntu.com/9239123/](http://paste.ubuntu.com/9239123/)

DETAILS
New install of Ubuntu 13.10 with on a 1TB hard drive, and I divided the drive in half.  I included a swap partition at about the 500GB point, and the root partition at 517GB point (16GB of RAM)

It's a Z230, a very new computer with UEFI (though I don't care about it... ensured that Safeboot and UEFI boot and what not are all disabled)

---

### Post by runxctry on 2014-11-24
[Deleted]

---

### Post by runxctry on 2014-11-24
[Deleted]

---

### Post by runxctry on 2014-11-24
{Deleted}

---

### Post by grahammechanical on 2014-11-24
Did you say Ubuntu 13.10? That version only had 9 months support. Ubuntu 13.10 reached End Of Life some months ago. Why do you need 500GB for a swap partition? With 16GB of RAM it is mostly that swap will never be used. Or hardly used at all. If you intend to suspend or hibernate the OS then a swap partition of a little more than the size of RAM is all that is necessary.

So, you turned of UEFI? Was Windows installed in UEFI mode? If the machine came with Windows pre-installed and the motherboard has a EFI boot system (firmware) then it is likely that Windows was installed in EFI mode. Turning off EFI mode would stop Windows from loading, as far as I understand things.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by oldfred on 2014-11-24
You rarely install grub to a partition boot sector and never to a NTFS partition boot sector. Windows has to have its own boot code in the NTFS partition's boot sector, NTFS has a backup that you can restore with testdisk:

 sda1: ____________________________________________

       File system:       [COLOR=#ff0000]ntfs[/COLOR]
    [COLOR=#ff0000]Boot sector type:  Grub2 (v1.99-2.00)[/COLOR]
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1 
                       and looks at sector 1434020088 of the same hard drive 
                       for core.img. core.img is at this location. No errors 
                       found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

 Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

And your should just install a current version of Ubuntu. You will not be able to update an obsolete version. 
Be sure to use Something Else. Your current install is in BIOS mode so be sure to boot installer in BIOS mode and choose Something Else. Then select current / partition as new /, format as ext4. It will find current swap.

---

### Post by runxctry on 2014-11-25
> **oldfred said:**
> You rarely install grub to a partition boot sector and never to a NTFS partition boot sector. Windows has to have its own boot code in the NTFS partition's boot sector, NTFS has a backup that you can restore with testdisk: 

This information was enough for me to find in Testdisk:

Advanced -> Partition 1 -> Rebuild boot sector (from backup).

dual boot works now.

Thanks so much.

---

