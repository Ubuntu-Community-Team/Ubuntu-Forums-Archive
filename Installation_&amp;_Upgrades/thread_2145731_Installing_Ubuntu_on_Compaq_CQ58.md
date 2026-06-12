---
title: "Installing Ubuntu on Compaq CQ58"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by James Caird on 2013-05-16
I am having trouble loading Ubuntu on this new laptop.  I've tried the 64bit versions of both 13.04 and 12.04.  The problem seems to be that the EFI in the BIOS isn't finding the Ubuntu Grub file on the CD ROM.  These have burned correctly as they will boot other machines, although not via EFI.  I have tried the EFI Help Page but the range of options on this machine are more limited than suggested and only Secure Boot can be disabled.  Legacy booting can be enabled but this is made unfunctional by the BIOS's prioritation of EFI which boots Windows 8 before reaching any Legacy alternative.  I have forced the boot sequence (F9) and it finds the CD ROM but returns the message "No bootable device -- insert boot disk and press any key".  The automated sequence tries the CD ROM 3 times before reverting to HDD boot.  Any help would be gratefully received.  Thanks.  James

---

