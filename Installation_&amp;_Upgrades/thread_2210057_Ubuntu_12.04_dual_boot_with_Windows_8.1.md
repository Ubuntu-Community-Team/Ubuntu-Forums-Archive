---
title: "Ubuntu 12.04 dual boot with Windows 8.1"
date: 2014-03-08
forum: Installation &amp; Upgrades
---

### Post by ahpitre on 2014-03-08
I have a new laptop with Windows 8.1. Laptop uses UEFI and GPT. I disabled Smart Boot. Ubuntu 13.10 always failed (booted from live CD, but a message "cannot find root", followed by messages about some missing files (couldn't see it completely as it goes away real fast). The installation GRUB menu then appears. I tried running each option (test UBUNTU from live CD, Install Ubuntu, Check Disk for errors), but, screen goes black, and nothing happens.

I then decided to try installing Ubuntu 12.04. It installed successfully, but, GRUB didn't install correctly, and the computer still boots to Windows 8.1 by using the default Windows boot-loader. In Windows, there is no option to add the Ubuntu partition. If I restart the Laptop and hit the F9 key, I see the Boot menu, and Ubuntu appears as the 2nd option, I select, hit Enter and UBUNTU boots successfully. Following advice on UBUNTU Forums, I installed (in UBUNTU) the Boot Repair Disk. Ran the repair option, but got a message that GRUB wasn't succesfully repaired and that having UBUNTU so far away from the beggining of the drive might be causing this issue. The Hard Disk is a 750GB drive, has 4 small partitions at the beginning 250MB, 100MB, etc., which are default Windows 8.1 recovery partitions, the 5th partition is the Windows NTFS partition, then partition #6 is where UBUNTU is installed. Windows partition is about 550GB, Ubuntu parition is 100GB. So, Ubuntu is about 578GB away from the beginning of the HDD.

Boot-repair-disk generated the file located in [http://paste.ubuntu.com/7052620/](http://paste.ubuntu.com/7052620/). Basically I need a way to repair GRUB so I can boot Windows 8.1 or UBUNTU.

Also, if anyone can recommend a Graphical boot program I will appreciate it. In the past I used GAG which was graphical bootloader that allows to password protect certain options. For example, I only use UBUNTU, so I password protected, but Windows was the default with time options (so it boots after X amount of seconds) with no password. I used GAG 3 years ago in a WIndows 7/Ubuntu 11 dual boot (w/o UEFI or GPT). Not sure if GAG is still available or if it works with UEFI/GPT drives.

---

### Post by oldfred on 2014-03-08
Somehow you have grub legacy in the MBR. Not even sure it works with gpt partitioned drives. And it was last the standard with Ubuntu 9.04, but is still in repository. Did you force Boot-Repair to install grub legacy in BIOS mode?
>  Wrong GRUB version detected.


You need to totally purge grub, and grub2 and reinstall grub-efi for UEFI boot. Boot-Repair can help you with that.
It does look like Boot-Repair has updated to grub-efi. But do not boot in BIOS mode and grub legacy may be causing conflicts. Also not sure what it did with gpt drive. It normally installs part of grub right after MBR, but that space does not exist with gpt. Grub2 is smart enough to know space does not exist and needs a bios_grub partition to install in BIOS mode.

You also have many entries in UEFI like this.
 Boot0004* Internal Hard Disk or Solid State Disk	RC
Too much UEFI data can cause UEFI issues and total bricking of a computer if UEFI gets too full.


 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

Generally 13.10 should be better for your system, but you may need boot parameters to get video to work or you end up with black screen. But sometimes black screen is just video set low and you can use f-key to may it brighter.  You would not need nomodeset, but it shows how to add boot parameters to grub menu. try some of the options in the post by ubfan1.
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

