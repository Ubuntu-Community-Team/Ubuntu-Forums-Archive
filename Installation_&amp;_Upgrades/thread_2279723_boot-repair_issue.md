---
title: "boot-repair issue"
date: 2015-05-25
forum: Installation &amp; Upgrades
---

### Post by Tyler_J._Peckenpau on 2015-05-25
I think I fixed this. Seems to be OK.
------------------------------------------------

Hello, 

First, I am an absolute beginner. I've used Ubuntu before in a work environment, but never at home. I decided I wanted to set it up. I originally split my primary drive (128GB SSD) into separate partitions and ran both Windows 7 and Ubuntu on that. I decided to get a separate drive for Ubuntu and I deleted the Ubuntu partition on the first drive and changed it to be one partition again.

I now have the new drive, and I have install Ubuntu on it, but I am not able to get the boot-menu to show up so that I can choose an OS. If I manually enter the BIOS and select the drive, Ubuntu boots fine.

I suspect that what I really need to do is to make sdb first in boot  priority, but it doesn't show up as an option in the hierarchy, although  it does show up as a device I can boot to in the boot menu. I realize  this is a Ubuntu forum and not support for my BIOS, but maybe I'm wrong  about what needs to be done, or maybe someone is willing to help anyway.


```
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 0210
    Release Date: 03/12/2012
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 8192 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6
```

I've tried running boot-repair (I've been running it via a USB-drive bootable install), but at the moment it doesn't seem to want to run all the way through. I have gotten a few different errors and tried to follow the steps to correct them (most notably, it asked me to set up a separate boot partition which I have done). I keep getting a message that says ``Filesystem repair requires to unmount partitions. Please close all your programs. Then close this window.'' I do as requested and close it, but it pops up again and again.

[ATTACH=CONFIG]262202[/ATTACH]


Below is information on my drives, etc., from boot-repair.

[http://paste.ubuntu.com/11353337/](http://paste.ubuntu.com/11353337/)

sda = the original (Windows) SSD
sdb = the new (Ubunutu) SSD
sdc = a mechanical data drive
sdd = (Ubuntu) bootable USB drive

Let me know what other info is needed. Any suggestions are greatly appreciated.

---

### Post by ubfan1 on 2015-05-25
So you have a UEFI machine running in compatibility mode, OK.  Your sdb SSD is set up with gpt partitioning, with a grub-bios partition,OK.  I'm confused by SSD sda's syslinux boot -- I thought syslinux needed a FAT partition to boot, and you have only ntfs filessystems on sda.  If your BIOS really does not allow directly booting off sdb, maybe you could just switch the two disks's hardware connections?  I have had success getting a second hard disk to boot when it could not run grub directly, by using a USB device I could put earlier in the boot order, and have it run the software off the second hdd.

---

### Post by oldfred on 2015-05-25
There are several Windows type boot loaders including syslinux & lilo. They normally have there own boot code & menus in a partition but the MBR works just like Windows in finding the boot flag and jumping to more boot code in the partition boot sector or PBR. But if you just install the part of those boot loaders to the MBR it will boot Windows if boot flag is on a Windows partition and Windows has its correct code in PBR.
Boot-Repair normally installs syslinux as the Windows boot loader if repairing a Windows drive.

Best not to run Boot-Repair's auto fix with multiple drives and multiple installs. The default in Boot-Repair is to install one grub to all MBRs. But it has advanced mode to choose an install and choose a drive to load boot loader.

---

