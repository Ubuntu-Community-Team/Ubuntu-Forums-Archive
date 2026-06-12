---
title: "Unable to Boot After Boot-Repair-Disk"
date: 2013-08-08
forum: Installation &amp; Upgrades
---

### Post by BlindSoothsayer on 2013-08-08
Hello everyone!

I decided to try installing Ubuntu 12.04.2 to dual boot with Windows 7 on a custom-built desktop.  I have the Windows system files and the boot files on a SSD (/dev/sda).  On a HDD (/dev/sdb), I have several partitions.  The first (/dev/sdb1) is data, the second (/dev/sdb3) is where I installed Ubuntu, the third (/dev/sdb4) is a swap partition, and the final partition (/dev/sdb2) is a backup of the Windows system files from the SSD.  I also have all Windows files and data backed up on an external hard drive from before the attempted Ubuntu installation.

The motherboard is a Gigabyte  GA-990FXA-UD3 ATX AM3+, which has dual UEFI BIOS.

When attempting to install Ubuntu, I received the following error message:

```

Executing 'grub-install /dev/sda' failed.

This is a fatal error.

```

At this point I chose to continue without a bootloader.  After that, I was still able to boot into Windows 7, but not Ubuntu.

Then I booted onto a boot-repair-disk.  I ran it with the default options.  It says the boot was successfully repaired, then this:

```
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!
```

However, in my BIOS I only have the following options:

```

Windows Boot Manager
P0:  ATAPI iHAS 124 W
P1:  SanDisk SDSSDP064G

```

P0 is the DVD reader/writer.  P1 is the SSD, which does not successfully load anything.  I also have an option to override boot onto the HDD, which also does nothing.  Windows Boot Manager brings up the GRUB menu, which has the following options:

```

Ubuntu, with Linux 3.5.0-23-generic
Ubuntu, with Linux 3.5.0-23-generic (recovery mode)
Windows UEFI bkpbootmgfw.efi
Windows Boot UEFI loader
EFI/Acronis/bootwiz.efi

```

Acronis is the software I used to backup the Windows files onto the HDD.  The first Ubuntu option brings up the Ubuntu logo screen, with the five dots alternating between red and white.  It hangs here indefinitely.  The recovery mode option seems to work okay.  Any of the final three options brings up:

```

error: no such device: ACF3-1C79
error: file not found.

Press any key to continue...

```

From the boot info script, it looks like ACF3-1C79 is the UUID of /dev/sda1.  Is there any way I will be able to dual boot Ubuntu and Windows 7 on this system?  If not, is there at least a way I can restore functionality to Windows 7?  Any help or advice would be greatly appreciated.  [Here is the full boot info script]("http://paste.ubuntu.com/5961044/") from the boot-repair-disk.

---

### Post by oldfred on 2013-08-08
You show both Ubuntu & Windows boot efi files in sda1.

It does look you have run the rename function with boot-repair, I might undo that.
renamed file
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 
Original

 /EFI/Microsoft/Boot/bootmgfw.efi 
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

What it has done:

 [http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply

But either way your UEFI menu should have entries for both ubuntu & windows. A few were modified to only boot Windows and that was the reason for the rename function to let UEFI think it is booting Windows but really booting grub2's shim file.

---

### Post by BlindSoothsayer on 2013-08-08
Thank you for the quick reply!

I was able to undo and rename the files back to their original names as you suggested.  It now boots straight into Windows with no problem.  Is there any hope of getting Ubuntu functioning?  [Here is the boot info script from the undo operation.]("http://paste.ubuntu.com/5961415/")

---

### Post by oldfred on 2013-08-08
You still have ubuntu in the efi partition. UEFI should show that as a boot option. With secure boot off does it show more options?

But you may have one of the few sytems that only boot Windows. I might try updating UEFI as many vendors found UEFI issues and have corrected those also. 

If not then the rename should work as UEFI thinks it is booting Windows, but you also may need the secure boot version of Ubuntu with the signed kernel. You can boot Boot-Repair in secure boot mode and tick the signed box and it will run the update to install the signed kernels.

 Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.


 One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

 One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

 


Boot-Repair seemed to not be able to query UEFI, so you may not have the UEFI shell. But see if you have any of this:

 [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)
EFI/boot/bootx64.efi.efi" ---> Brings up 'EFI shell environment' with command prompt.
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by BlindSoothsayer on 2013-08-08
I've searched through my BIOS and do not see a SecureBoot option.  I have tried booting in UEFI mode and "Legacy" mode and both go straight to Windows.  I will try updating my UEFI in the next few days.

---

### Post by oldfred on 2013-08-08
Only systems with Windows 8 pre-installed currently have the secure boot option implemented with UEFI. If you built system yourself, it is unlikely that secure boot is an option yet.

---

### Post by BlindSoothsayer on 2013-08-10
Gigabyte says that I will void the motherboard warranty if I alter the BIOS.  Also, I just found on their website that they don't list any 'nix in the supported OSs.  I don't think I'll be able to get Ubuntu working on this system.  I have Ubuntu on my laptop.  Thanks for the help anyways oldfred.

---

### Post by oldfred on 2013-08-11
That is a standard answer and you do not modify UEFI/BIOS. But you download upgrades from Gigabyte and change UEFI settings to make it work. 
Some motherboards have settings that do not seem related that create issues.
And some vendors do not post they work with Linux but still do if the comply with standards like UEFI is. But better to have a board that at least has been tested with Linux.

---

