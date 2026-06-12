---
title: "Grub2 &amp; Windows 10"
date: 2021-09-15
forum: Installation &amp; Upgrades
---

### Post by allen2 on 2021-09-15
The setup was working, but a HDD broke, then it was giving boot errors.   So I tried to re-install Ubuntu (needed to update it anyway), and now I can't get it right. 

[https://paste.ubuntu.com/p/xnsD62nkyJ/](https://paste.ubuntu.com/p/xnsD62nkyJ/)

Windows XP is not compatible with my hardware, just remains from repurposing the hold hard drive.  I don't want to delete the partition yet though as I still have the old compatible hardware.

Preference:  I'd like to get Ubuntu and Windows 10 boot information all onto the same 1TB SSD drive since both are installed to the SSD.  (Hopefully less configuration that way if something another HDD decides to die).

---

### Post by oldfred on 2021-09-15
You have booted live installer in old BIOS/Legacy/CSM mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

As Boot-Repair says reboot in UEFI mode.
Depending on what tool you used to create Ubuntu live installer, it may be BIOS only?
Rufus, for example makes either BIOS only or UEFI only installers. Others make installer that is both, but then in UEFI boot of flash drive, you have to select the UEFI:label entry not one that is just  label as that is the BIOS version.

Both sda & sdb are gpt partitioned.
Windows only boots in UEFI mode from gpt.
Best if Ubuntu is UEFI from gpt also, although Ubuntu does let you install in BIOS mode to gpt drive.

You do show grub installed to gpt's protective MBR in sda & an old Windows BIOS boot loader in sdb.
Those should not ever be used, and will not be used as long as you always boot in UEFI boot mode. Trying to boot in BIOS mode from either drive will fail with some sort of error message.

---

### Post by allen2 on 2021-09-15
Thanks, I was able to get it working from your post.  I disabled CSM in the motherboard, found out that Ubuntu was not booting from the UEFI option (like I thought it was), so I had to use the install disk for the boot-repair.  I had experimented with adding a windows 10 option to grub, but it wasn't configured right.  I had to purge grub, then grub reinstall autodectected windows 10 properly.

---

