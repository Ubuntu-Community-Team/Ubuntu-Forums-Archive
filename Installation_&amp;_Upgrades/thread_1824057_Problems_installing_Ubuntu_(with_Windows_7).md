---
title: "Problems installing Ubuntu (with Windows 7)"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by lavindc on 2011-08-13
After installing a new Windows 7, I tried installing Ubuntu 11.04. I had partitioned the HD during the Windows install. 
However, before the Ubuntu install I'm told that there is no detected OS installed. I ignored the message and installed Ubuntu on the partition I had for it. Unfortunately, then GRUB didn't work, and I would load into Windows every time I started up. 

After reformatting and remaking all the partitions and re installing both OSes a few times (with disks and USB) I decided to just install wubi, only to find after reboot that when I tried to load Ubuntu from wubi I got an error message that there is an internal problem with windows - take the install disk and repair the system (which I also tried).

Basically, I'm saying that I've spent all day trying to install Ubuntu, never sen these problems before and am baffled. What do I need to do to get this to work?

---

### Post by Rubi1200 on 2011-08-13
Hi and welcome to the forums :-)

Please post the results of the boot info script so we can see what is going on. There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by lavindc on 2011-08-25
[LEFT]Here are the results. Thanks.

 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda3 has 
                       950695935 sectors, but according to the info from 
                       fdisk, it has 2024437759 sectors.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 starts 
                       at sector 951164928. But according to the info from 
                       fdisk, sda4 starts at sector 2024906752.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992 2,024,906,751 2,024,437,760 Data partition (Windows/Linux)
/dev/sda4   2,024,906,752 2,639,304,703   614,397,952 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BCE6-2F10                              vfat       
/dev/sda3        765EEA2C5EE9E4B9                       ntfs       
/dev/sda4        6C06DD6C06DD37B2                       ntfs       Ubuntu

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

[/LEFT]

---

### Post by oldfred on 2011-08-25
With a 3TB drive and gpt partitions you have a new system using UEFI to boot not BIOS. Boot script does not yet parse efi partitions to see what is there but your windows should be like the links below:

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.
Post #76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
efi\Microsoft\Boot\bootmgfw.efi

I do not think wubi works with UEFI as it is trying to modify BIOS based windows boot.

Grub2 seems to have some issues with UEFI.
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Updates - Avidanborisov created compile script
[http://ubuntuforums.org/showthread.php?t=1772310](http://ubuntuforums.org/showthread.php?t=1772310)

[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)
How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

A few have had dual booting work, it seems to depend on how well the UEFI and grub work together. Some suggest just backing up the window EFI partition, installing grub & then copying the windows efi entries back.

---

### Post by srs5694 on 2011-08-25
In broad outline, I recommend you do the following:


[list=1]
[*]Using whatever tool is convenient and familiar, shrink your existing partitions to make room for Linux. (Maybe you've already done that -- there seems to be a gap between the end of /dev/sda4 and the end of the disk.)
[*]Back up the contents of your EFI System Partition (ESP), aka /dev/sda1. The Ubuntu installer has the inexcusable habit of trashing it.
[*]Install Ubuntu. If you tell it that /dev/sda1 is your ESP (IIRC, Ubuntu's installer calls it an "EFI boot partition" or some similar not-quite-correct term), it'll install OK but trash the ESP, rendering Linux bootable (probably) but Windows unbootable. If you *don't* identify your ESP as such, Ubuntu won't install a boot loader and you won't be able to boot. I suspect that's what happened to you.
[*]Repair the damage or incomplete boot loader installation:

[list]
[*]If Ubuntu boots but not Windows, restore the files from your ESP backup, but don't delete the Ubuntu files. You should then be able to boot either OS by selecting your choice from your firmware, and running update-grub should enable GRUB to chainload to Windows, so if you set Ubuntu/GRUB as the default in the firmware, you should be able to more easily select your boot OS.
[*]If Windows boots but Ubuntu doesn't, install an EFI-capable Linux boot loader. The grub-efi package is one such; however, you may need to edit your /etc/fstab file to mount /dev/sda1 at /boot/efi before it will work correctly. Personally, I've had more luck with [ELILO](http://elilo.sourceforge.net/) on UEFI-based systems; however, this will require more reconfiguration, and ELILO can't chainload to Windows. Thus, you might need to install [rEFIt](http://refit.sourceforge.net) in addition to ELILO; rEFIt presents a boot menu to select Windows vs. Linux, and ELILO boots Linux. There's a refit package in Ubuntu, but you must copy some files, including the 64-bit executable, to the ESP. Of course, installing all this Linux software if Ubuntu doesn't boot can be tricky; you'll need to use the Ubuntu install disc in its "live CD" mode.
[/list]

[/list]


I can provide more details if necessary; as I say, that's a broad outline.

Unfortunately, Ubuntu's UEFI support is pretty poor at the moment. No doubt things will improve in the future -- with any luck, as early as the 11.10 release in about two months.

---

