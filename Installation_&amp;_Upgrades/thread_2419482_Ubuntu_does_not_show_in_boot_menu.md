---
title: "Ubuntu does not show in boot menu"
date: 2019-05-22
forum: Installation &amp; Upgrades
---

### Post by upeksha1996 on 2019-05-22
I have two hard drives an 1 had windows 10 and i installed ubuntu to the next hard drive. It said that installation successful but in the boot menu Ubuntu hard drive is not there. I tried re installing but it says it already exsting. I tried installing boot loader and do recommended repair. It gave the following error[INDENT]GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.
[/INDENT]
I generated the bootinfo summary below

[INDENT]Boot repair url: [http://paste.ubuntu.com/p/82QfFvsy22/](http://paste.ubuntu.com/p/82QfFvsy22/)[/INDENT]
Appreciate if anyone could help

---

### Post by oldfred on 2019-05-22
UEFI and BIOS are not compatible.

You have new UEFI hardware, but have Windows installed in the old BIOS boot mode.
Microsoft has required vendors to install Windows in UEFI/gpt boot mode since release of Windows 8 in 2012. So most computers now are UEFI.
But UEFI has CSM - Compatiblity module to emulate BIOS for those who really wanted BIOS boot.
Windows in BIOS mode only boots from MBR partitioned drives.
Windows in UEFI boot mode only boots from gpt partitioned drives, do not easy to convert. Usually you have to backup data, erase drive & reinstall.

You installed Ubuntu in UEFI boot mode.
Grub will only boot other installs in same boot mode, so it cannot boot Windows in BIOS mode.

You can continue since separate drives, but can then only dual boot by directly using UEFI boot menu, not grub. You may have to turn on/off UEFI/legacy boot settings in UEFI, but most newer systems recognize system you are booting and use correct mode. Grub also only boots working Windows.
You can convert Ubuntu to BIOS boot, by adding a tiny 1 or 2MB unformatted partition with bios_grub flag on sdb. Just shrink ESP by several MB. And install correct version of grub.
Or you can totally reinstall Windows to take advantage of UEFI with gpt partitioning. May not be worth effort though.

If converting Ubuntu you must add bios_grub partition, and boot Ubuntu live installer in BIOS mode. Then directly install grub-pc (BIOS) and uninstall grub-efi-amd64 (UEFI). Often easier using Boot-Repair

---

