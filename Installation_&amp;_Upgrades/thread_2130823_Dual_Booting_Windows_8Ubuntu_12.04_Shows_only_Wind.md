---
title: "Dual Booting Windows 8/Ubuntu 12.04 Shows only Windows 8"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by JackCooper on 2013-03-30
I was following [this]("https://help.ubuntu.com/community/UEFI") guide (Quick And Easy Way)  and [this]("http://www.intowindows.com/dual-boot-windows-8-and-ubuntu/") guide.  My computer always boots straight to Windows 8.  Secure Boot is off and I have used Boot Repair twice.  Boot repair says to make the bios boot on sda2/EFI/ubuntu/grubx64.efi but I don't see that in the boot options (only from HDD, CD, Windows 8 etc.)  Here's the output of bootrepair:  [http://paste.ubuntu.com/5657132](http://paste.ubuntu.com/5657132)  Any help would be appreciated.

---

### Post by JackCooper on 2013-03-30
Update:  I have enabled the bios, before I was only looking at the boot options from the Windows 8 UEFI advanced settings menu.  I can now boot into either OS, though I have to enter the BIOS and choose an option (all of them are of exactly the same name, though the second one gets me to grub).  This should work for now, though I have to always go through the bios any time I want to get to ubuntu.

---

### Post by oldfred on 2013-03-30
If you select ubuntu from UEFI menu, do you get grub menu.

Then on grub menu does this entry (you only see menuentry) boot Windows?

 menuentry "[COLOR=#ff0000]Windows UEFI bootmgfw.efi[/COLOR]" {
search --fs-uuid --no-floppy --set=root 1CC2-0664
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

---

