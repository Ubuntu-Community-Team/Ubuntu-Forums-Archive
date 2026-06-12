---
title: "Messed up rEFInd Boot Manager"
date: 2013-11-04
forum: Installation &amp; Upgrades
---

### Post by Herbalist on 2013-11-04
I recently replaced linux mint with xubuntu,
i'm using the rEFInd boot manager installed from windows 8 to switch between OSs,the problem is that after i removed mint,i can still view an entry in rEFInd,
the green linux mint icon is there and the line under it says : " Boot EFI\Linuxmint\grubx64.efi from System
and i got another 4 new ubuntu icons after i installed xubuntu
the first says "Boot EFI\ubuntu\grubx64.efi from system"
the second "Boot EFI\ubuntu\shmix64.efi from system"
the tird "Boot boot\vmlinuz-3.11.0-12-generic.efi.signed from 14 GiB ext4 volume"
the fourth "Boot boot \vmlinuz-3.11.0-12-generic from 14 GiB ext4 volume"

How can i remove all the unnecessary entries and just leave Xubunt and windows 8

---

### Post by oldfred on 2013-11-05
I do not know how to refresh rEFInd. But UEFI also has memory and needs entries deleted and that may let you then update rEFInd.

       # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)


 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

