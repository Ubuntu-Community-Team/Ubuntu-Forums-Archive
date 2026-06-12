---
title: "Failure to get ubuntu to boot on Sony Vaio Pro"
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by adam-disc0tech on 2013-12-29
I just bought a sony vaio pro for my wife and in the process of setting it up with Ubuntu.  It came pre-loaded with W8.

After numerous attempts at installation, and following available  instructions, I am stuck and need help.  I am able to boot into a Live  USB every time.

I have

1.  In the BIOS: Disabled Secure Boot, Left UEFI enabled (If I change to legacy the LiveUSB hangs during kernel startup)
2.  Booted from Live USB and used the automatic / erase existing installation options
3.  Reboot, and get a message from the firmware that windows cannot be found
4.  Launched back into the Live USB and run boot-repair (output here: [http://paste.ubuntu.com/6658144/](http://paste.ubuntu.com/6658144/))
5.  Rebooted, same problem...

Can anyone help?

One note - I have no idea what this meant in the boot-repair output, so that may be the step I am missing 
*"Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!" *

Thanks in advance

---

### Post by adam-disc0tech on 2013-12-29
A couple of other things I discovered, when I install efibootmgr I can see it is obviously wrong
> 
ubuntu@ubuntu:~/Downloads$ sudo efibootmgr -v
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0006,0000,0005
Boot0000* ubuntu    HD(1,800,f3800,7b3947c4-ff3c-45ca-8043-3f58dd535668)File(\EFI\ubuntu\shimx64.efi)
Boot0005* **Windows Boot Manager**    HD(1,800,f3800,7b3947c4-ff3c-45ca-8043-3f58dd535668)File(\EFI\Boot\bootx64.efi)
Boot0006* UEFI: SanDisk U3 Cruzer Micro 8.02    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(2,0)HD(1,26,779fc2,00000000)..BO

I don't want the windows boot manager to remain, certainly not to have boot priority.  I tried both re-ordering and deleting the windows share, but both times the change did not worked, and when I rebooted via Live USB it had reverted to the original se

> Then I tried to use REFIND boot manager, I try and install the debian package and see the below:
Setting up refind (0.7.6-1) ...
Installing rEFInd on Linux....
[B]//boot/efi doesn't seem to be on a VFAT filesystem. The ESP must be
mounted at //boot or //boot/efi and it must be VFAT! Aborting!
[/B]dpkg: error processing refind (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 refind


Could it be that I need to change my EFI boot partition to VFAT?

---

### Post by oldfred on 2013-12-29
Your efi partition is FAT32 and uses the vfat driver with Linux. It also needs the boot flag when seen from parted or gparted, but it really is a long GUID to make it the ESP or efi boot partition.

UEFI has NVRAM and remembers settings, you may have to manually delete directly from UEFI with efibootmgr. But first we need to know if your system is one of the "buggy" UEFI where the vendor has modified UEFI to only boot the Windows efi file.  If you can boot ubuntu entry then you are ok. But you have to either have secure boot off and ubuntu installed in that mode, or with secure boot on have Ubuntu with the shim and signed kernels. 

Only if it will not let you boot ubuntu entry.
       buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

   Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

If you can boot ubuntu then you can do this:

 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

You probably have to delete or backup the Microsoft folder in the efi partition, or else UEFI may find it again and add it back in.

      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by adam-disc0tech on 2013-12-29
Many thanks for the response.

> **oldfred said:**
> Your efi partition is FAT32 and uses the vfat driver with Linux. It also needs the boot flag when seen from parted or gparted, but it really is a long GUID to make it the ESP or efi boot partition.

Confirmed the boot flag is set on my FAT32 boot partition

> If you can boot ubuntu entry then you are ok. But you have to either have secure boot off and ubuntu installed in that mode, or with secure boot on have Ubuntu with the shim and signed kernels. 

I cannot even get to GRUB, I can only get to ubuntu via Live USB

>  
Only if it will not let you boot ubuntu entry.
       buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

   Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi


I have no "Microsoft" directory under /EFI...

> 
   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.


I am trying to setup a ubuntu only system - no dual boot
   
> 
If you can boot ubuntu then you can do this:

 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

You probably have to delete or backup the Microsoft folder in the efi partition, or else UEFI may find it again and add it back in.


Interestingly, I successfully deleted the microsoft boot EFI record via efibootmgr, and I do not have a microsoft folder in the EFI partition, but my firmware still fails to boot to GRUB.
      
 Any ideas?

Thanks

---

### Post by oldfred on 2013-12-29
With one system, you may be booting thru grub and into boot parameter issues. With one system you do not get a grub menu by default as it assumes you want to boot just that system. You hold shift key from BIOS until menu appears or with some UEFI systems escape key works.
What video card/chip?

Or you have the buggy UEFI that is hard coded to only boot Windows.
Some other systems than these:
 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by adam-disc0tech on 2013-12-30
Cracked it!   :P  Not sure how to mark the thread as solved though...

First I found this PDF [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512), which was useful, but didn't get me anywhere - still had exactly the same problem.

One thing I noticed was that efibootmgr kept showing me a Windows Boot Manager, even if I deleted it.  After reading the analysis of the similar HP issues here - [http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619) - I realised that the BIOS was automatically recreating it and was probably looking for the string "Windows Boot Manager" on boot...

Ultimately, the fix was this:

1. Load into Live USB as "Try Ubuntu without installing"
2. Open a terminal and run sudo modprobe efivars
3. Connect to a wifi network
4. sudo apt-get install efibootmgr
5. sudo efibootmgr -v    : this showed me multiple boot managers from all my messing around, refind, ubuntu, windows
6. sudo -c -L "Windows Boot Manager" -l "  \EFI\ubuntu\shimx64.efi"    : this is the text label from my BISO created windows boot manager, and the EFI path from the ubuntu boot manager
7. Reboot

Even if I delete the non-existing Windows Boot Manager, the BIOS recreates it.

I'm not sure how many of the steps I previously did (boot-repair, installing refind) were actually necessary without further testing.  Certainly efibootmgr indicates it is NOT booting via refind.

Hope this helps others.

---

### Post by oldfred on 2013-12-30
Good to know. 
Yours is not hard coded to boot bootmgfw.efi but by the label "Windows Boot Manager". Similar buggy UEFI. Vendors are not supposed to hard code the UEFI to boot one system with UEFI as the purpose of UEFI is to allow booting many systems.

But I thought Boot-Repairs rename would have worked as it renames the Windows efi file in the Windows folder, so UEFI thinks it boots Windows when it boots shim.

---

### Post by adam-disc0tech on 2013-12-30
> **oldfred said:**
> 
But I thought Boot-Repairs rename would have worked as it renames the Windows efi file in the Windows folder, so UEFI thinks it boots Windows when it boots shim.

I guess it's possible that I've done something else wrong, somewhere in the process, which means the shim isn't loading properly via the windows path.. AND that the logic allows any path given the right Windows label....

---

### Post by Amir_Hossein_Hajiz on 2014-01-21
Hi adam-disc0tech,

I have the exact same problem, and I'm following your approach, except that step 6 doesn't work for me. When I enter "sudo -c -L "Windows Boot Manager" -l "  \EFI\ubuntu\shimx64.efi"" linux command line prints some usages of sudo command. Am I missing something?

Thanks,

---

### Post by oldfred on 2014-01-21
You have to be using efibootmgr
I think all commands start with sudo efibootmgr and then options. #6 is missing efibootmgr

 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

