---
title: "USB Install"
date: 2015-07-11
forum: Installation &amp; Upgrades
---

### Post by ben161 on 2015-07-11
I have a successful USB install.  I started by using UUI, booting that and then installing to another USB the actual installation.  This uses the standard installer where you have four options.  I chose the guided install of LVM with Encryption.

Now I'm facing issues.  I can't boot on a machine using UEFI.  I've researched UEFI and Secure Boot.  The way to boot from USB in Windows 8, is to hold the shift key and click on restart.  This then provides the option to boot from USB.  When I do this it doesn't recognize the USB and just reboots back to windows, which says to me that perhaps my installation on the USB is not right.  The fact that Ubuntu installs can use a Microsoft generic key for UEFI boots tells me that this should not be the problem.  Hence I'm digging around on other potential problems such as:
[LIST=1]
[*]MBR vs GPT vs LVM.  I read on some forums that LVM might negate the ability to boot using UEFI and that GPT might be required.  Is this true?
[*]File system.  From what I have managed to research, whilst ext4 may be superior to FAT32, I should be using FAT32 on the boot partition to ensure the USB has compatibility with all EFI based systems including Mac.  The standard Ubuntu doesn't seem to provide this option unless going for a manual install.
[/LIST]

Appreciate some advice and any pointers to UEFI and USB installs discussions that answer the above.  I have looked and thus far come up empty.

Cheers.

Ben.

---

### Post by oldfred on 2015-07-11
How you boot installer UEFI or CSM/BIOS is then how it installs.

I do not know LVM, but some have posted Boot-Repair's Summary report and it shows, efi, boot & LVM partitions on a gpt partitioned drive. The efi partition is FAT32 with a boot flag which makes it the ESP or efi system partition.

It seems you may have booted installer in CSM mode, so it installed in CSM mode and you can only then boot it in BIOS mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by ben161 on 2015-07-18
Thanks Fred.  I will try to diagnose with Boot-Repair and also research about installing via CSM as I didn't know this was an option.  I did try using Rufus to create the BIOS and UEFI compatible boot layout, but it didn't work.  Bloody confusing:-(

---

### Post by Vladlenin5000 on 2015-07-19
With Rufus you should select the "GPT for UEFI only".
In some translations they forget the underlined part of "UEFI/_CSM_" in "MBR partition for BIOS or UEFI/CSM" which is the same as saying "old way, old BIOS or lagacy mode only". In said translations it looks like a universal solution.

---

