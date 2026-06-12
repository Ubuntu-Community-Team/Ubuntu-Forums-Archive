---
title: "Multibooting with BTRFS subvolumes"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by Correnos on 2010-09-26
The setup I want to end up with is to have two linux systems installed on my BTRFS partition, with the ubuntu partition installed in /alt_root. I have installed it with debootstrap using the guide [here]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/linux-upgrade.html"), but I do not know the entry on the kernel command line to pass arguments to mount. On Arch, I know that it's ```
rootflags=subvol=alt_root
```but I am unaware of what the Ubuntu equivalent is.

EDIT: I have figured out the correct command to pass mount opts-for future reference, it is ```
roflags="-o subvol=alt_root"
``` However, when I attempt to boot the system, at some point it remounts the BTRFS filesystem without the "subvol=alt_root" and ends up running the Arch Linux init script. The ubuntu subvolume's fstab does have the "subvol=alt_root" flag set on the root mount, but I suspect that the main BTRFS volume is being mounted before ubuntu's fstab is parsed in the boot process.

---

### Post by xavv on 2010-09-28
Hi, 

I'm currently studying the BTRFS and other new FS to use ...

About what you are looking for, I think you have to patch Grub. It's him which tells on which "partition" the system has to boot.

I don't know if grub2 (grub-pc) can use BRTFS, but I heard that a patch was in progress for grub 1.97 (grub-legacy).


I hope it will help you, and if you finally find an answer about, I will be glade to read it. ;)


Thx
Xavv

---

### Post by Correnos on 2010-09-28
I have an ext2 /boot partition setup for the bootloader, and am using extlinux as a bootloader. I have included in Ubuntu's initramfs the btrfs kmod, and it is able to successfully mount the BTRFS partition. Again, the only problem is that it doesn't mount the subvolume even with the correct "roflag" passed.

---

