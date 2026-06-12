---
title: "Installing Ubuntu on Acer Aspire M5 Ultrabook"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by Crabbyman on 2013-02-04
I've been attempting to dual boot Windows 8 and Ubuntu 12.10 on my Acer Aspire M5, and haven't had any luck.

I burned the .iso to a cd, but am having problems booting from the cd.  I changed the boot order in the bios and placed the cd ahead of the windows loader.  However, when restarting and attempting to install, my computer gets stuck on the acer splash screen.

I believe secure boot is the issue, but I am unsure how to disable secure boot.  (I am not able to change the option in the bios.)

If anyone had any insight to what steps I'll need to take to install ubuntu, it would be very helpful.

---

### Post by HoneyGutClusters on 2013-02-26
I just did this to my Aspire M5-481PT. I couldn't get GRUB to boot Windows 8 and I couldn't get the Windows Bootloader to load GRUB. Basically, I used diskpart in the command prompt on my Win8 recovery disc to shrink the main partition, then used an Ubuntu live CD to create three partitions, one for /boot, one for /, and a swap partition. Once that's done, you can basically follow the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).

This basically sets up two bootloaders. Instead of having GRUB present a bootloader, I use F12 to select which bootloader to use. This is the only way I've been able to get it to work.

---

### Post by HoneyGutClusters on 2013-02-26
A few more notes:

At the Acer splash screen, press F12 to get to the bootmenu. If you're in UEFI mode and you've inserted the CD, it will present it as a boot option. If it doesn't, then it didn't find an EFI bootloader on the CD and there's either something wrong with your image or the way you burned it.

I don't know if 12.10 supports EFI (I'm pretty sure it does). I used 12.04 LTS.

Only the 64 bit version of Ubuntu supports EFI. It's the same case with Windows. If you want to use 32 bit, you'll have to switch the BIOS from UEFI to Legacy.

Hope that helps!

---

