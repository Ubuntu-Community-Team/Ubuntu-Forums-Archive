---
title: "UEFI laptop installation with dual boot"
date: 2013-09-06
forum: Installation &amp; Upgrades
---

### Post by Gareth_Owen on 2013-09-06
Hi all

I installed the ubuntu ISO to a USB stick.  I disabled secure boot, restart the laptop and boot from the USB.  

**PRIMARY QUESTION: **The grub shell comes up and no installer - how do I launch the installer?

**ADDITIONAL INFO**
My laptop has Win8 preinstalled.  I did try installing in legacy mode but naturally grub corrupted my gpt mbr (which thankfully was backed up).  Also, The EFI partition doesn't appear to be a standard fs format - it's not mountable from linux.

Best
Gareth

---

### Post by Gareth_Owen on 2013-09-06
Answer for me was as follows, where hd1 is your usb drive).  [tab] means press the tab key.

linux (hd1,msdos0)/casper/vmlinuz[tab] boot=casper
initrd (hd1,msdos0)/casper/initrd.lz
boot

Best
Gareth

---

### Post by PJ_Dawson on 2013-09-06
Are you using the 64bit iso?   If your computer uses UEFI boot you need to use the 64bit iso (if i'm not mistaken) to avoid the GPT partition table not being able to read it.

Also you can always try GParted, or booting into PartedMagic!

I know you've already fixed the issue, just trying to add helpful comments?  I don't know.

James

---

### Post by oldfred on 2013-09-06
If booting in UEFI mode from flash drive it is standard to get grub menu as it will boot UEFI.
Syslinux is BIOS boot only, so you get the standard purple accessibility screen with icons when in BIOS mode.
  
Nore links and other details in my signature.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

