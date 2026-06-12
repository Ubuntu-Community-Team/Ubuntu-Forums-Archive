---
title: "Can I change an Acer ES1-331 series from UEFI to legacy boot"
date: 2017-05-31
forum: Installation &amp; Upgrades
---

### Post by Roland_Msl on 2017-05-31
I have last year installed Ubuntu 16.04 on an Acer ES1-331-P498.
I used UEFI boot mode, had to create a BIOS password.

Now it happens the 3rd time, that at starting the laptop, it has forgotten the already installed grub.
Each time, I have to tell in UEFI, that this is a wanted start file.

Now I have 2 other Acer ES1-331 series installed with legacy boot mode.

Is it simple possible to switch from UEFI to legacy mode without any further changes?

---

### Post by ubfan1 on 2017-05-31
Your Acer probably has a GPT partitioned disk, so for a legacy boot, you will need a small (1-2M) partition flagged "grub-bios".  With that partition, you should be able to install grub-pc, and have a legacy boot.  If things don't work, you will still have the UEFI boot in place, since the legacy install should not affect it.  Now you will have some unnecessary things, like a mount of the EFI partition at /boot/efi -- you can leave it or remove it. I have       gone the other way, from a legacy install to UEFI on an external disk, but did have an EFI partition in place on the disk.  I didn't even bother with any cleanup, since Win 10 is on an MSDOS disk, and cannot boot in UEFI  anyway.

---

### Post by oldfred on 2017-05-31
If you create the bios-grub partition anywhere on drive before running Boot-Repair, you can use Boot-Repair's advanced mode to uninstall grub-efi-amd64 and install grub-pc. 
Since you can boot, you can probably do that your self from inside your install, but while one grub is uninstalled you could not reboot, until other grub is correctly installed. Or have live installer handy, just in case you have to repair it.

I use gpt for all new or reformatted drives (since about 2011) using the bios_grub partition.
And I now normally include both the ESP - efi system partition (FAT32) and the bios_grub partition (unformatted) on every drive.
The only place you cannot use gpt is if Windows must boot in BIOS mode. 
My old BIOS systems booted Ubuntu using bios_grub and newer systems with UEFI hardware booted in UEFI mode using ESP.

---

### Post by Roland_Msl on 2017-06-03
Had last week got 2 Acer ES1-331 series bought at Ebay and installed Ubuntu 16.04.2 in legacy mode. Thought could just copy this bios_grub partition from this units, but there is nothing.

It's only Ext4, and an extended where the linux-swap is. How do they boot without anything like bios-grub partition?

---

### Post by oldfred on 2017-06-03
If using MBR which if you have an extended it is, core.img is in the sectors after the MBR.
If using gpt then the bios_grub is required. But it is unformatted.

You do not copy bios_grub as the code in core.img is specific to your install of grub.

Either way you may just need to reinstall grub to MBR or a total reinstall of all of grub.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Boot-Repair can help you do a full uninstall/reinstall of grub2 using its advanced options.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

