---
title: "Swapping Linux Flavour In A Dual Boot System"
date: 2020-06-05
forum: Installation &amp; Upgrades
---

### Post by spode2 on 2020-06-05
I have a dual boot system with Lubuntu 18.04 on a SSD and Windows 7 on a HDD. 

I want to upgrade the Linux installation to Xubuntu 20.04 by replacing the Lubuntu SSD with a new drive, and installing Xubuntu onto the new drive alongside the existing Windows 7.

Will there be any problems when the Xubuntu installer sets up the dual boot system on the Windows drive, as the files will already exist?

---

### Post by Impavidus on 2020-06-06
I don't expect problems, but it depends on the details. UEFI or bios/legacy mode? Where is the bootloader installed?

---

### Post by spode2 on 2020-06-06
Thanks for the reply. I did not know UEFI was even an option with W7, but I am sure it's all BIOS. So far as I know, if you choose to have dual-boot, the bootloader is installed on the Windows drive, but it is this that I am asking about. Will the fact that it already exists cause any problem to the new install?

I was hoping to be told that there would be no change to the bootloader, and I could even swap the previous Linux drive back if I needed to.

---

### Post by yancek on 2020-06-06
UEFI is an option but it is extremely unlikely that you are using it if you have a default install of windows 7.  You seem to be saying that you plan to get a new drive and install both Xubuntu and windows 7 there.  Is that what you want?  If so, just install windows first then Xubuntu and make sure you select during the Xubuntu install to install the Grub bootloader to the MBR of the drive you want, usually /dev/sda.  If this isn't what you want and you plan on having multiple drives with multiple operating systems, you need to specify that information.

---

### Post by oldfred on 2020-06-06
Windows 7 can be UEFI, but most installs were BIOS. 
Users could install in either mode. Which depended on how installer was booted. Original installer was BIOS but could be converted to UEFI on flash drive with moving & renaming a couple of files. Updates to installer then made it UEFI compatible.

Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since release of Windows 8 in 2012. Windows 8 supported UEFI Secure Boot. Windows 7 in UEFI mode did not support Secure Boot.

So all hardware since 2012 is UEFI. So how installer is booted UEFI or BIOS/CSM/Legacy is then how system is installed.

If having Ubuntu on its own disk, some advantages to gpt partitioning, but you have to have a bios_grub partition for BIOS boot.
But all versions of Windows require MBR for BIOS boot.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by grahammechanical on 2020-06-06
If I understand the original post correctly, then the original poster has Windows 7 (possibly BIOS install) on a hard drive and Lubuntu on a SSD. He (or she) wants to remove the SSD and replace it with another SSD and install Xubuntu on it. And would also like the option of putting the Lubuntu SSD back into the machine and booting into Lubuntu.

If I was doing something like this I would have put the Grub boot loader on the SSD and then used the BIOS utility to change boot order. I do this now with 2 hard drives and when I want to plug in a USB memory stick with a Ubuntu ISO image burned to it.

I would suggest to install Xubuntu onto the new SSD the same way you installed Lubuntu on the old SSD and put the Grub boot loader on the Xubuntu SSD. Then you can switch SSDs and the Lubuntu one will boot because it still has Grub on it. You will be selecting which drives to load using the BIOS boot utility. It may be that Grub will give you an option to load Windows. I do not know if this is the case. I do not have Windows. If Grub can do that then it would be so much the better.

On the other hand if the Lubuntu Grub is on the hard disk then it will not load Xubuntu. You will have to overwrite the Lubuntu Grub with a Xubuntu Grub. And then Grub will not load Lubuntu. 

Do you have the option of running both SSDs in the machine at the same time? If so, then updating Grub (whichever one) will detect the other Linux distribution. You will have to make sure that the correct SSD has boot priority. 

Regards.

---

