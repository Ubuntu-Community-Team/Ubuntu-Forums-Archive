---
title: "Dual Booting Windows 10 and Ubuntu"
date: 2018-08-28
forum: Installation &amp; Upgrades
---

### Post by tabs467 on 2018-08-28
I have tried quite a few different combinations of partitions from online tutorials on the "Something Else" menu when trying to install Ubuntu and so far none of them seem to work. Each one results in the following error message when the installation program tries to install the GRUB2 Package: "The 'grub-efi-amd64-signed' package failed to install into / target/. Without the GRUB boot loader, the installed system will not boot."

I have tried using both RUFUS and Universal USB Installer to put the disc image of Ubuntu onto a pen drive which I have been using to try and install the operating system. 

My BIOS mode is Legacy.

The partitions I set up when installing Ubuntu:
[LIST]
[*]21GB, Primary, Beginning of this space, Ext4, Mount Point: "/"
[*]33GB, Logical, Beginning of this space, swap area
[*]46GB, Primary, Beginning of this space, Ext4, Mount Point: "/home"
[/LIST]

The partitions I have before I attempt installation:
[LIST]
[*]100MB, NTFS, Healthy (System, Active, Primary Partition)
[*]830.72GB, NTFS, Healthy (Boot, Page File, Crash Dump, Primary Partition)
[*]100.69GB, Unallocated
[/LIST]

I am beyond confused as to which partitions I should use, especially since I can only use up to four primary partitions (I already have two used for Windows 10). Does anyone have any suggestions as to which partitions to use?

---

### Post by oldfred on 2018-08-29
It seems you must have a newer UEFI system, but have Windows installed in the now 35 year old BIOS/MBR configuration.
With BIOS boot, Windows only works from MBR(msdos) partitions.
With UEFI, Windows only can have gpt partitions.
So you cannot change partitioning unless you want to reinstall Windows.

And then you need to install Ubuntu in same boot mode as Windows. Or in your case you need to install in BIOS boot mode. Ubuntu now only needs one partition which can be either primary or a logical partition inside an extended partition. The advantage of extended partition is then you can create many more partitions if desired. But newer gpt partitioning used with UEFI has a limit of 128 partitions.

How you boot install media, is then how it installs. And USB boot, does not default to legacy setting in UEFI, it still offers both modes. So boot in BIOS boot mode. Your UEFI system will show two boot options for Ubuntu flash drive. One is UEFI:flash and other just flash where flash is name or label of flash drive. You want the one that is just flash.

While more for UEFI boot, it shows boot screens. You want the purple one.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
If Windows 10, only use Windows to shrink NTFS partition and reboot immediately to let it run chkdsk. And have good backups.
Also make a Windows repair disk as Windows 10 in BIOS mode will need to be directly booted on occassion. Grub only boots working Windows. So then you have to temporarily  install Windows boot loader to MBR, fix Windows and then restore grub boot loader to MBR. 
Windows 10 works better with UEFI as then you can always directly boot from UEFI boot menu.

---

