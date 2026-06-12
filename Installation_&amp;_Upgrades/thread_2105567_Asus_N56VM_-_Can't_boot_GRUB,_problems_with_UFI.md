---
title: "Asus N56VM - Can't boot GRUB, problems with UFI"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by Aaron7 on 2013-01-16
Hi,

I have recently installed Debian and I can only seem to boot from a Super Grub2 on USB. In the BIOS I have disabled the UEFI setting but the hard drive does not appear in the boot order - it only shows Windows Boot Loader. 

I am currently in Ubuntu Secure Remix 64bit and have tried using boot repair but I get the following error:
[http://paste.ubuntu.com/1537814/](http://paste.ubuntu.com/1537814/)

I can still access Windows normally and boot into CD's and USB's but not boot into the boot partition for Debian(sda10).

Thanks for your help,
Aaron7.

---

### Post by oldfred on 2013-01-16
You can only have one efi partition and it should be first. Remove "boot flag" from sda10.

> In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

    

Not sure if Debian can even boot in UEFI mode?
        The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

    
If you go into UEFI/BIOS and change to legacy then you may be able to boot from MBR and boot a BIOS install. Then you have to go back and change to UEFI and boot UEFI entries. 
All systems have to be either UEFI or BIOS to allow one system to boot and then chain load to boot another.

Windows only boots from gpt partitioned drives with UEFI, so unless you want to convert back to MBR(msdos) and reinstall everything, you need to have all installs in UEFI mode.

---

### Post by YannBuntu on 2013-01-16
AFAIK:

Debian stable is not compatible with EFI.
Debian testing&unstable should be (contain GRUB1.99, same as 12.04)
None is compatible with SecureBoot.

---

