---
title: "Ubuntu 18.04 installation help"
date: 2020-01-06
forum: Installation &amp; Upgrades
---

### Post by zefk on 2020-01-06
I am trying to dual boot windows 10 with [Ubuntu 18.04]("https://ubuntu.com/download/desktop"). I burned the image onto a disk. The following message occurs after making my root, home, swap, and then selecting install.

> The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as “Reserved BIOS boot area” and should be at least 1 MB in size. Note that this is not the same as a partition mounted on /boot. If you do not go back to the partitioning menu and correct this error, bootloader installation may fail later, although it may still be possible to install the boot loader to a partition.

I did some research [here]("https://askubuntu.com/questions/458947/should-i-create-the-reserved-bios-boot-area-partition/459002"), but I still do not know how to resolve it. It does not explained how to install Ubuntu in UEFI mode instead of legacy mode. I thought it has something to do with secure boot? I tried pressing F11 and enabled it, but still the same error message.

[IMG]https://www.rodsbooks.com/efi-bootloaders/hp2.jpg[/IMG]

---

### Post by CatKiller on 2020-01-06
> **zefk said:**
> I thought it has something to do with secure boot?

Nothing really to do with Secure Boot. UEFI is a completely different framework to the really old BIOS. The "Legacy mode" is still UEFI but running everything through a BIOS emulator that turns off the useful new stuff. You can only do Secure Boot with a machine that's natively UEFI: a machine that's *actually* using BIOS rather than simply pretending to use BIOS can't do Secure Boot. That's probably where your confusion came from.

Another wrinkle is that actual BIOS machines can only understand MBR partitions, which have limits like only being able to use four primary partitions. UEFI machines can also understand GPT partitions, which don't have those limits. With MBR partitions you can only have one bootloader, which sits in the MBR and chainloads any other bootloaders you might have. GPT partitions have an EFI System Partition that houses all your bootloaders together; that's what you're being asked to create with that message, since you've decided to do all your partitioning manually.

The Ubuntu installer will install in UEFI mode if you boot the install media in UEFI mode; it will install in BIOS mode if you boot the install media in BIOS mode. Since you're trying to dual boot you'll find it easiest to match whatever your Windows install does; an OEM install of Windows 10 would be installed in UEFI mode with GPT partitions, but if you installed it yourself or upgraded from another version of Windows it could be set up as anything.

There's more information on installing Ubuntu in UEFI mode [here](https://help.ubuntu.com/community/UEFI).

---

### Post by zefk on 2020-01-08
> **CatKiller said:**
> GPT partitions have an EFI System Partition that houses all your bootloaders together; that's what you're being asked to create with that message, since you've decided to do all your partitioning manually.

There's more information on installing Ubuntu in UEFI mode [here]("https://help.ubuntu.com/community/UEFI").

What you are saying is that I need to make a EFI partition? Like this....?
[IMG]https://www.intel.com/content/dam/support/us/en/images/memory-and-storage/25535_image3.png[/IMG]

 Normally, Ubuntu would set everything up for me, but for someone reason I have to do it manually. It did it for me on my HP Laptop, but maybe because it is a newer model or did I get some different Ubuntu os image back then with Ubuntu 16.04?

---

### Post by CatKiller on 2020-01-08
> **zefk said:**
> What you are saying is that I need to make a EFI partition? Like this....?

If you already have one, you don't need to make another one; all your bootloaders can live in the same one. I have no idea what your existing partitions are like.

---

### Post by zefk on 2020-01-08
> **CatKiller said:**
> If you already have one, you don't need to make another one; all your bootloaders can live in the same one. I have no idea what your existing partitions are like.

I do not have one, so this might be the problem because things are set with [COLOR=#000000]UEFI mode. Should I make it 100mb like with the image I found?[/COLOR]

---

### Post by CatKiller on 2020-01-08
> **zefk said:**
> I do not have one, so this might be the problem because things are set with UEFI mode. Should I make it 100mb like with the image I found?

From the link I gave you already:

> An ESP can be created via a recent version of GParted (the Gparted version included in the 12.04 disk is OK), and must have the following attributes:

[list=1][*]Mount point: /boot/efi (remark: no need to set this mount point when using the manual partitioning, the Ubuntu installer will detect it automatically)

[*]Size: minimum 100Mib. 200MiB recommended.

[*]Type: FAT32

[*]Other: needs a "boot" flag.[/list]

(the instructions are from 2012, that's why it mentions the 12.04 installer. It just means the one on the installer you're using.)

---

