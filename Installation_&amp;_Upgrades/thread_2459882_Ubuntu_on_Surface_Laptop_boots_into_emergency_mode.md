---
title: "Ubuntu on Surface Laptop boots into emergency mode"
date: 2021-03-28
forum: Installation &amp; Upgrades
---

### Post by aayla-secura on 2021-03-28
I installed Ubuntu 20.04 (well, Xubuntu technically) onto a USB drive. Basically I

[LIST]
[*]booted into the live Ubuntu USB drive from my PC 
[*]plugged in a second USB drive 
[*]created a 1G FAT32 EFI partition ([FONT=courier new]boot[/FONT] and [FONT=courier new]esp[/FONT] flags) and another ext4 for the root fs 
[*]started the installed with [FONT=courier new]ubiquity -b[/FONT] in order to skip installing a bootloader (since that failed at first) 
[*]chrooted into it 
[*]installed [FONT=courier new]grub-efi-amd64-signed[/FONT] and [FONT=courier new]shim-signed[/FONT] 
[*]installed grub with [FONT=courier new]grub-install --target=x86_64-efi --recheck --removable --efi-directory=/boot/efi --boot-directory=/boot --no-nvram --uefi-secure-boot[/FONT] 
[/LIST]
finally, I plugged the drive with the installed Ubuntu into a Surface Laptop and the GRUB menu loaded fine, but when I booted into Ubuntu it went into emergency mode, and I can't proceed to load the system normally. No other errors in the journal log. Any ideas?

[SIZE=4]_**EDIT:**_[/SIZE]

Oh, I found the error actually: it was failing to mount the EFI partition cause the UUID in [FONT=courier new]fstab[/FONT] was wrong... Fixing that now it boots normally.

---

