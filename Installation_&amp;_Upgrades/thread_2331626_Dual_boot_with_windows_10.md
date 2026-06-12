---
title: "Dual boot with windows 10"
date: 2016-07-23
forum: Installation &amp; Upgrades
---

### Post by michael2410 on 2016-07-23
Hi

I have tried to set up a dual boot with windows 10 (already on computer) and ubuntu 16.04.1. Unfortunately it did not work and all I get is an error message and the grub rescue screen. I tried to fix with grub-repair but that didn't work. I created the following document with boot-repair [http://paste.ubuntu.com/20692555/](http://paste.ubuntu.com/20692555/). Can someone help me please. I am not very good with computers!

---

### Post by oldfred on 2016-07-23
It looks like you have new UEFI hardware and booted Boot-Repair in UEFI boot mode.

But you have CSM/BIOS boot of Windows installed to sdb. And no install of Ubuntu anywhere??
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Make sure Windows fast start up is off.
And install a Windows boot loader to the MBR of sdb for BIOS boot. You Windows repair flash drive or Windows installer can do that with fixMBR, or Boot-Repair can also install a Windows type boot loader, syslinux if Windows fast start up is off, so Linux NTFS can mount (see) the NTFS partition's files to know it is bootable.
Then make sdb first in UEFI/BIOS boot order. Make sure CSM is on or UEFI is off in UEFI settings.

How you boot install media, for both Windows & Ubuntu is then how it installs. And best that both Windows and Ubuntu be in same boot mode, or both BIOS or both UEFI.

Windows only boots from MBR partitioned drives with BIOS.
Windows only boots from gpt partitioned drives with UEFI.
Ubuntu can boot from gpt partitioned drives with either UEFI or BIOS if correct supporting partitions are on drive. ESP for UEFI and/or bios_grub for BIOS.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by yancek on 2016-07-24
> Unfortunately it did not work and all I get is an error message 

Posting "it did not work" isn't very helpful.  You don't indicate what the error message was either.  Looking at your boot repair output it is clear that there is no sign at all of an Ubuntu install so I'm not sure what you did but you definitely did not install Ubuntu.  All of the partitions showing on both your drives are windows filesystems.  Did you follow some tutorial on the install?  If so, can you post a link to it.

Since you have windows installed as MBR, take a look at the detailed instructions at the link below on installing Ubuntu.  If you scroll about half way down the page, there is a step by step guide and a guide on dual booting which should be helpful.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by michael2410 on 2016-07-24
Thanks for the replies. The error message was - Error: no such device: cdd9e929-8158-486-8ef1-48ae027526ff. Entering Rescue Mode... Grub Rescue>
I tried to install following the instructions provided by the unbuntu program. I didn't follow anyone else's instructions. Windows doesn't work either. I appreciate your help but it is all too technical for me and I don't want to become a programmer. I will try and find some who can do this for me.

Thanks

Michael

---

### Post by yancek on 2016-07-24
>  Error: no such device: cdd9e929-8158-486-8ef1-48ae027526ff.

That long series of characters (numbers and lower case letters) is the UUID for a Linux partition and if you look at the top of the boot repair output you will see this message both drive sda and sdb.  That means your Ubuntu partition was on drive number 5 and partition number 6 which you don't seem to have.  If you decide to get someone else to help, it might be a good idea to have the boot repair file on a flash drive/CD or printed out to help.  Good luck.

> search.fs_uuid cdd9e929-8158-486e-8ef1-48ae027526ff root hd4,msdos6 
set prefix=($root)'/boot/grub'

---

