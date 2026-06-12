---
title: "How do I remove one OS from a triple-boot PC and re-use the freed space?"
date: 2014-06-07
forum: Installation &amp; Upgrades
---

### Post by andrew.t.sullivan on 2014-06-07
Hello

I have a Lenovo G505s laptop with Windows 8.1 Update 1, openSuse 13.10 and Ubuntu 14.04 installed, which all work fine.  However, I rarely use openSuse nowadays and would like to get rid of it and use the freed-up disck space for Ubuntu. What's the safest way of doing this?

Thanks in advance

Andrew

---

### Post by oldfred on 2014-06-07
Are systems installed with UEFI or BIOS?

If UEFI all systems have separate folders in efi partition and you only have to select a different one if your current default is the system you are deleting. You can houseclean out UEFI & efi folder entries at any time.

If BIOS you have to make sure the MBR of the hard drive has the boot loader for a system you are keeping.

Then you can delete partitions with gparted and resize or make new data partitions.

       An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)
But it does not edit partitions, just makes sure you can boot.

---

### Post by andrew.t.sullivan on 2014-06-07
Many thanks for your prompt reply.  The laptop is an UEFI machine.

Just to make sure I understand...  I can use OS-Uninstaller from Ubuntu to get rid of the openSuse installation (both the root and Home partitions), then use Gparted to resize the Ubuntu data partition?

Thanks again

Andrew

> **oldfred said:**
> Are systems installed with UEFI or BIOS?

If UEFI all systems have separate folders in efi partition and you only have to select a different one if your current default is the system you are deleting. You can houseclean out UEFI & efi folder entries at any time.

If BIOS you have to make sure the MBR of the hard drive has the boot loader for a system you are keeping.

Then you can delete partitions with gparted and resize or make new data partitions.

       An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)
But it does not edit partitions, just makes sure you can boot.

---

### Post by oldfred on 2014-06-07
If UEFI, you really do not need the OS uninstaller.

Your efi partition should have a folder that is openSuse. You can delete that folder. And UEFI has its own NVRAM and remembers entries and you have to remove that also.

       # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
 [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

