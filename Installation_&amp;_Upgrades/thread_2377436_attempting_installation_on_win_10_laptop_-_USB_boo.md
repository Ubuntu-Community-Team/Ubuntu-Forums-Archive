---
title: "attempting installation on win 10 laptop - USB boots to black screen"
date: 2017-11-13
forum: Installation &amp; Upgrades
---

### Post by mishamtrop on 2017-11-13
Hi all,
I'm a new user and I'm trying to install Ubuntu-16.04.3 alongside windows on my laptop (Toshiba Satellite U-940-100, Windows 10 updated from windows 8). I'm following the instructions fro installing from a USB stick from the wiki page.
I can select the USB from the boot menu, but it only leads me to a black screen with a cursor (static underscore character) in the top left corner.

I've tried the following to solve the issue:
-created the USB with either Rufus or Unetbootin
-used a couple of different USB sticks (SanDisk ULTRA USB 3.0 16GB and an older 4GB USB 2.0)
-disabled secure boot in the BIOS; I don't see other relevant boot options in BIOS
-verified the .iso with an md5 checksum

All of this does not make a difference. I'll appreciate any kind of help

---

### Post by tilllt on 2017-11-13
Dunno if it works for you, i had the same issue, booted into recovery mode, updated software and could boot normal then.

---

### Post by mishamtrop on 2017-11-13
thanks, but I don't understand what you mean by update software?

---

### Post by oldfred on 2017-11-13
If from Windows 8 pre-installed then system is UEFI.
Are you booting Ubuntu live installer in UEFI mode. It should offer to boot in both UEFI and BIOS/CSM/Legacy but may just have name or label of flash drive for the BIOS boot mode.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

Have you backed up Windows & all your data?
Did you use Windows to shrink the NTFS partition & reboot immediately so it can run chkdsk?

Then if video issues, often nomodeset may help, but normally Intel video just works.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Many with Toshiba have had to run Boot-Repair and/or manually move some boot files around to use a fallback or hard drive UEFI boot, not the ubuntu entry which should normally work.

See also link in my signature for lots of details.

---

