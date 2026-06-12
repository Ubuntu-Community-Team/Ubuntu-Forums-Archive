---
title: "No boot loader is installed in the MBR of /dev/sda"
date: 2016-08-14
forum: MINT
---

### Post by Billy_Congo on 2016-08-14
[HTML]http://paste2.org/Ma36g9L7[/HTML]

Dell Inspiron 5558 with Windows 8.1. Left it in dual boot mode. Installed Ubuntu 12.04, 14.04, 16.04 with no problem. Wanted to get rid of Windows 8.1. Installed Linux Mint 18 (sarah) but deleted all partitions. Won't boot. Updated BIOS. Tried to fix MBR. Got corrupted. Looked at other posts with similar title, but they had grub installed in boot partition.

---

### Post by ajgreeny on 2016-08-14
Moved to **Linux Mint**.

I am no expert in UEFI but I think you have fallen foul of the problems of installation in UEFI mode, details of which are shown in [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) and [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you installed in legacy BIOS you will need a small dedicated BIOS boot partition with a recommended size of at least 1 MiB. This partition can be created via GParted or other partitioning tools, or via the command line. It must be identified with a bios_grub flag. The necessary GPT modules are automatically included during installation when GRUB 2 detects a GPT scheme.

---

### Post by Dennis N on 2016-08-14
There is no operating system on your disk (sda), only swap partition and the EFI system partition. You need to redo the installation. The report also says "this live-session is not in EFI-mode.." Assuming you plan to install in UEFI mode, be sure you installation media is booted in UEFI mode.

---

### Post by oldfred on 2016-08-14
How you boot install media, UEFI or CSM/Legacy/BIOS is then how it installs.
If drive is gpt, you can install most Linux in either UEFI or BIOS boot mode.
But UEFI must have the ESP - efi system partition  which is the FAT32 formatted partition with boot flag. 
And with BIOS and gpt partitioning you must have the bios_grub partition.

When I manually partition all new drives, I only use gpt and always include both the ESP & the bios_grub, even on my larger flash drives. Then without major re-partitioning I can install in either UEFI or BIOS boot mode.

---

### Post by Billy_Congo on 2016-08-14
I tried to install in UEFI mode, but Linux Mint says "[COLOR=#111111][FONT=Ubuntu]This machines's firmware has started this installer in UEFI mode but it looks like there maybe existing operating systems already installed using BIOS compatibility mode, If you continue to install Debian in UEFI mode,it might be difficult to reboot into any BIOS-mode operating system."[/FONT][/COLOR]

---

### Post by Billy_Congo on 2016-08-14
So I installed Linux Mint in legacy mode, let it erase the entire disk, and then ran boot repair. I let it do it's thing, and while it did complain about the usb drive, it fixed the hard drive, and now everything is working.

---

