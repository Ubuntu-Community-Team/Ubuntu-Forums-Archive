---
title: "Can't boot Windows 8.1 after installing ubuntu 13.10"
date: 2014-02-20
forum: Installation &amp; Upgrades
---

### Post by ruben7 on 2014-02-20
I've been trying to get both operative systems to boot but it seems like I can only boot Ubuntu. I messed around with all Windows auto-repair options and nothing fixes the problem, used Boot-repair several times, Secure Boot and Fast Boot are disabled. My laptop came pre-installed with Windows 8.

Here's my Boot-info URL: [http://paste.ubuntu.com/6967169/](http://paste.ubuntu.com/6967169/)

Thanks in advance for any help I can get.

---

### Post by oldfred on 2014-02-20
You only can have one efi partition per hard drive.
Use gparted and right click on sda4 and remove boot flag.

It looks like you originally installed Ubuntu in BIOS boot mode as you have grub in protective MBR. But fstab now has efi entry so Boot-Repair converted to UEFI boot.

After changing boot flag so you only have one efi partition, UEFI should let you boot either Windows or ubuntu entry in UEFI menu.

Did you run the buggy UEFI backup & rename. Best not to or undo it if you have until we know you cannot boot ubuntu entry in UEFI. Some vendors modify UEFI to only boot Windows and the rename is a work around.
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

