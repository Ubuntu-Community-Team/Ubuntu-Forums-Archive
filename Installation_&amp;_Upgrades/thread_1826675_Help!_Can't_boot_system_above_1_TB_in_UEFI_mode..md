---
title: "Help! Can't boot system above 1 TB in UEFI mode."
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by sword7 on 2011-08-16
Hello folks,

I tried to install Ubuntu 11.04 on my 3 TB hard drive but UEFI firmware can't boot that Linux partition anywhere and went Windows 7 instead.  Does anyone have any solutions for UEFI booting? I think EFI filesystem is messed up or bug in installer. 

Earlier I was able install and boot linux partition with both linux distros (Ubuntu and Fedora) before I removed them for re-install them later and created additional NTFS partition until now. :(

However, I was only able boot Ubuntu 11.04 from USB stick in UEFI mode.  I will continue to use live USB until all solutions are solved.

UPDATE: I made a data backup on one of NTFS partitions and removed it.  I  tried to install Ubuntu 11.04 below 1 TB disk space but still can't  boot it.

My system configuration is:
ASUS Maximus IV motherboard
Intel i7-2600K processor
8 GB memory modules
Hitachi 3 TB hard drive
MSI HD 6870 Hawk video card

Thanks,
Sword7

---

### Post by YesWeCan on 2011-08-17
Hi, welcome. Nice system.
Did you create a grub EFI boot loader program? [https://wiki.archlinux.org/index.php/GRUB2#GPT_specific_instructions](https://wiki.archlinux.org/index.php/GRUB2#GPT_specific_instructions)

---

### Post by ProNux on 2011-08-17
Is is safe experimenting on EFI / Dual boot?

---

### Post by sword7 on 2011-08-17
> **YesWeCan said:**
> Hi, welcome. Nice system.
Did you create a grub EFI boot loader program? [https://wiki.archlinux.org/index.php/GRUB2#GPT_specific_instructions](https://wiki.archlinux.org/index.php/GRUB2#GPT_specific_instructions)

Thanks. I will look into that.  How do I mount EFI filesystem to investigate what is wrong with UEFI linux booting. Only Windows 7 booting works fine. :(

Sword7

---

### Post by YesWeCan on 2011-08-17
I think Canonical is still "working on it". So unless you want to get your hands very dirty, I'd probably forget UEFI booting of Ubuntu for now. However, I suppose that doesn't stop you installing Ubuntu on a GPT disk partition and putting Grub on your USB stick. Then choosing either Windows or USB from the UEFI menu.

---

### Post by srs5694 on 2011-08-18
Sword7,

It's very unclear to me how your system is configured and how you're attempting to boot it. It sounds like you're saying that you did an initial Ubuntu/Fedora installation, removed it, and now can't get Ubuntu installed; however, it's unclear if you did either your initial install or the new one in BIOS mode or in UEFI mode, in what order you did your initial installations, what boot loader(s) you used, what partitioning system you used, and many other critical details.

First, some details you must understand:


[list]
[*]There's no such thing as an "EFI filesystem," at least not in the sense that you'd say "ext3 filesystem" or "FAT filesystem." "EFI" is the "Extensible Firmware Interface," the latest version of which is the Unified EFI (UEFI). This is a firmware standard for the computer, not a filesystem. To boot, though, EFI uses an EFI System Partition (ESP), which is a FAT partition on the hard disk that holds boot loader files for each OS.
[*]Most BIOS-based computers use the Master Boot Record (MBR) partitioning system. Most UEFI-based computers use the GUID Partition Table (GPT) partitioning system. Windows enforces those associations, but Linux does not, so it's possible to use GPT on a BIOS-based computer or MBR on a UEFI-based computer under Linux.
[*]MBR uses 32-bit pointers to describe its partitions, which gives it a disk size limit of 2 TiB (assuming 512-byte sectors, which are nearly universal). GPT uses 64-bit pointers, which makes its limit much higher and not worth worrying about right now.
[*]Most (perhaps all) modern UEFI implementations include a BIOS compatibility layer that enables the computer to boot OSes that work only with a BIOS, such as older versions of Windows. It's conceivable that your original dual-boot Linux installation was done in BIOS mode but that your computer now boots in UEFI mode. Which boot mode is used is an option you can set in the firmware's setup utility. Unfortunately, details of how to set these modes varies greatly from one firmware to another.
[*]In BIOS mode, three main Linux boot loaders are available: LILO, GRUB Legacy, and GRUB 2. Ubuntu uses GRUB 2 by default and Fedora uses GRUB Legacy by default.
[*]In UEFI mode, two main Linux boot loaders are available: ELILO (like LILO, but not identical) and GRUB 2 (which is similar to GRUB 2 in BIOS mode, but must be compiled with different options). Ubuntu uses GRUB 2. Fedora uses a heavily-modified GRUB Legacy to boot in UEFI mode, so in a sense that's a third option, but I didn't introduce it as such because this UEFI-enabled GRUB Legacy is not officially supported by the GRUB developers.
[/list]


Ubuntu does support installation and booting in UEFI mode; however, there are a number of serious bugs with this process that can cause problems, particularly if you're also dual-booting with Windows. Sometimes it's desirable to work to overcome those problems, and your case may be one of these, since you say you've got a 3 TB hard disk and it sounds like you want to dual-boot with Windows. With such a system, you'll need to use GPT on the disk, and therefore UEFI boot mode, at least for Windows.

I recommend you boot a Linux emergency disc (or the Ubuntu installer in its "try it now" mode, or whatever it's called) and run the following command:

```

sudo parted -l

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility. That will show us how your disk is currently partitioned. Also tell us:


[list]
[*]Is Windows currently booting? (I get the impression it is, but I just want confirmation of this.)
[*]Do you want to dual-boot with Windows, or will this be a Linux-only installation?
[*]Do you want to install Ubuntu, Fedora, or both?
[*]Do you currently see a GRUB menu when you boot, or does the computer boot directly to Windows?
[/list]


It *is* possible to boot just about any modern Linux distribution in UEFI mode; however, you may have to jump through some extra hoops to get it all working correctly.

---

