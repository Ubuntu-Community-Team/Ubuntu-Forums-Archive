---
title: "Ubuntu/Windows 8 Will not Boot"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by joeturtle on 2013-05-11
I've been trying to get my computer to Dual Boot both Ubuntu 13.04 and Windows 8, but somehow in the process I've messed up my computer.

I'm using an Asus laptop, and from others who have computers from the same company, it seemed the best (and only) way to get Ubuntu to work correctly with UEFI is to install it with CMS enabled in the BIOS and then change over to EFI after the installation. 

I've ran boot-repair, but that has not solved my problem. All options in GRUB boot to a blank purple screen, regardless of if I have CMS enabled or not. FastBoot and SecureBoot are both diabled within my BIOS.

My Grub options are as such:
Ubuntu
Advanced Options for Ubuntu
Windows UEFI bkpbootmgfw.efi
Windows Boot UEFI loader
Windows Recovery Environment (loader) (on /dev/sda2)

The PASTE Url from Boot-Loader is [http://paste.ubuntu.com/5656284](http://paste.ubuntu.com/5656284)

Any help into being able to boot Windows and/or Ubuntu would be appreciated. Thank you.

Edit: The only way I can boot my computer is using the LiveUSB I made of ubuntu in CMS mode.

---

### Post by oldfred on 2013-05-11
It looks like you have installed the secure boot versions of grub. Have you tried turning secure boot on. Boot-Repair also have done a file rename for those systems that only boot Windows, so booting Windows from the UEFI menu should give you grub and then the bkpbootmgfw.efi should boot Windows.

If Ubuntu starts to boot but gives black screen then it is a video issue. What video card?

Some have not been able to boot Ubuntu due to video issue with some models of Asus. Or it only works in BIOS mode. Make sure you have newest UEFI/BIOS but it seems like a bug in Asus UEFI.

 Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
ASUS-K55N is just not able to boot an EFI linux, converted to BIOS with MBR partitioning - UEFI Windows 7
[http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283](http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283)
Blank screen resolved by turning secure boot off
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

---

