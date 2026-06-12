---
title: "Cannot reinstall GRUB Boot Loader"
date: 2019-03-11
forum: Installation &amp; Upgrades
---

### Post by luapekralc on 2019-03-11
Hi,

Had a dual-boot installation (Windows10Pro + Ubuntu 18.04) however the Ubuntu system ran out of hard drive room and would not boot. I attempted a reinstall of Ubuntu from the latest ISO n a USB, and it was successful in that Ubuntu is now running fine. BUT...I can no longer boot to windows as the Grub Boot Loader does not come up.

I have followed various intructions that all result in the same thing - a Boot record and when rebooting the PC direct boot into Ubuntu.

I am not sure how Windows is installed as I can't access it right now, but I expect that it is UEFI. So for the Boot-repair I have booted as a UEFI USB drive and attempted the Boot-repair.

Here is the latest paste: [http://paste.ubuntu.com/p/btW4fHjZgf/](http://paste.ubuntu.com/p/btW4fHjZgf/)

Any suggestions would be appreciated.

Thanks, Paul

---

### Post by yancek on 2019-03-11
Your problem is explained in the quote below from the end of the boot repair report.  You need to boot windows by using an installation DVD or recovery CD and find some way to turn that off.  Turn off fast boot and anything relating to hibernation.  No Linux system will mount a hibernated partition there for Grub will have no access to the windows boot files and there will be no entry for windows.  Additionally, you have an EFI partition but you have a Legacy install with an msdos partition so the EFI partition is not used and only has Ubuntu files.  You have Grub in the MBR of both disks.

> Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation

---

### Post by oldfred on 2019-03-11
Because Windows 10 is not dual boot friendly in BIOS/MBR configuration, I would install grub2's boot loader to sdb drive and keep a Windows boot loader to MBR of Windows sda drive.

Grub only boots working Windows, or Windows that is not hibernated. And Windows updates turn fast start up back on, setting hibernation flag, so grub will then not boot it. And you have to temporarily install Windows boot loader to MBR of sda, fix Windows and restore grub to dual boot.
But if grub is in sdb, you do not have to go thru all that. Just in BIOS change which drive to boot from.
 But still better to have systems in UEFI boot mode if newer hardware.

You cannot have Ubuntu in UEFI boot mode on same drive as Windows in BIOS boot mode.
Windows in BIOS boot mode has to have boot flag on primary NTFS partition with boot files.
UEFI requires boot flag on ESP - efi system partition and you cannot have two boot flags.
Normally UEFI uses gpt and Windows requires gpt partitioning for UEFI boot, but Ubuntu can be forced to install in UEFI mode to MBR partitioned drive.
Windows in BIOS boot mode must use MBR partitioning and it is not easy to convert a BIOS/MBR install of Windows to UEFI/gpt, without erasing drive. 

Whatever you do be sure to have good backups.

---

### Post by luapekralc on 2019-03-12
Thanks for the tips. Have decided to reinstall everything. Fingers crossed.

---

### Post by yancek on 2019-03-12
I would definitely recommend you read the Ubuntu documentation on dual booting with windows 10 at the link below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

