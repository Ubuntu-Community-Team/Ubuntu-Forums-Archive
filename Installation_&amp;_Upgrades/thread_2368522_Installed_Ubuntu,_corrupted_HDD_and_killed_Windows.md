---
title: "Installed Ubuntu, corrupted HDD and killed Windows"
date: 2017-08-11
forum: Installation &amp; Upgrades
---

### Post by SpazCool on 2017-08-11
The long and short of it is that in my attempt to have a dual boot system, I killed Windows. I'd like to get it back. The problem is that this is a second-hand laptop that came with W10 already installed. I don't have any paper documents, receipts or anything else that might prove a purchase of W10 for this machine. 

Anyone have any ideas on how to get a copy of W10 back on here?

---

### Post by oldfred on 2017-08-11
If Windows 10 was pre-installed:
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c) 

But it may only work for the OEM version. And if it does work with Windows direct download,  you may have to download lots of drivers from the OEM.

Also makes a huge difference if system is UEFI and if Ubuntu is UEFI. If Ubuntu is now BIOS on UEFI hardware, you will have to convert as Windows must be installed in UEFI mode on gpt partitioned drive.

Are you sure Windows is gone? Only the install to full drive options, which warn you in RED that you are easing Windows would have removed it.
Post this:
sudo parted -l

---

### Post by SpazCool on 2017-08-11
Thanks for the reply, here's what I got with the command:

```
Model: ATA WDC WD10S21X-24R (scsi)Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  496GB   496GB   primary   ext4            boot
 3      496GB   992GB   496GB   primary   ntfs
 2      992GB   1000GB  8501MB  extended
 5      992GB   1000GB  8501MB  logical   linux-swap(v1)





```

---

### Post by oldfred on 2017-08-11
You still show a Windows NTFS partition.
But you have boot flag on sda1, not the NTFS partition.
Grub does not use boot flag, But Windows has to have boot flag on primary NTFS partition with boot files to boot, or even to allow repair using repair flash drive of the NTFS partition.

Move boot flag back to sda2. But if grub is not booting it, it may not have all the boot files. Windows installed in BIOS boot mode normally has a small 100MB boot partition as the first NTFS partition. That has bootmgr & BCD which are required for Windows to boot. If those are missing, you can often use a Windows repair flash drive to add them to the main Windows install partition. Separate Boot partition is not required with Windows.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by arsenic23 on 2017-08-13
Don't worry about Windows 10 keys.  If you have Windows 10 and you have had it online, Microsoft has a hardware key for your system.  Even if you don't manage to get it booting again you won't loose your Windows license.  You can just download the Windows 10 installer from Microsoft, copy it to a flash drive, flag the drive bootable, and reinstall windows.  After getting online and activating you'll find that you have your license back with no issue.  This works 99.9% of the time.

---

