---
title: "Installing Ubuntu on UEFI, and GPT enabled ultrabook"
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by kamesh419 on 2013-07-16
I have two specific questions regarding installing Ubuntu on UEFI and GPT enabled ultrabook. 

1) When installing Ubuntu, should we explicitly choose "device for boot loader installation" as /dev/sda or /dev/sda3 (EFI partition)?

2) How would I uninstall or install another distro on the same partition. Previously, we just used to reformat it. Now because the keys are stored in EFI partition, how do we remove them.

Thanks and regards

---

### Post by oldfred on 2013-07-16
With BIOS we never installed grub2's boot loader to a partition, only to a drive's MBR. 
But with UEFI you do install grub2's boot loader to the efi partition and to no other place. With UEFI it seems to automatically install to the efi partition regardless of what you select so generally with UEFI there is no issue. 
But you must be installing in UEFI mode not BIOS/CSM mode which then would need a boot loader in the gpt drive's protective MBR.

Each install has a separate folder in the efi partition. One user wanted separate folders for each of his Ubuntu installs (Ubuntu & Kubuntu etc) & filed a bug report, but you can still boot from one working grub.
If totally removing an install you can delete the folder in the efi partition. But you may also have to go into UEFI Shell or efibootmgr and remove UEFI entries as it also saves some boot info.
 [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)

---

### Post by kamesh419 on 2013-07-17
Thanks a lot Oldfred. Your replies were very helpful. I need one more small clarification. Please let me know.

> If totally removing an install you can delete the folder in the efi partition. But you may also have to go into UEFI Shell or efibootmgr and remove UEFI entries as it also saves some boot info.

1) How can one remove the folders in the efi partition? Just by mouting them in Ubuntu?

2) How can one go into the UEFI shell or efibootmgr and remove UEFI entries? Does it depend on my UEFI provider?

---

### Post by oldfred on 2013-07-17
You can just use any system that will mount and show files & folders in the efi partition to delete them. May be best to fully backup efi partition before any major changes.

Some UEFI provides have UEFI shell, but you may be able to download from Intel and use that one if your UEFI does not have it.
       [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)
EFI/boot/bootx64.efi.efi" ---> Brings up 'EFI shell environment' with command prompt.
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)


 [http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it).
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

