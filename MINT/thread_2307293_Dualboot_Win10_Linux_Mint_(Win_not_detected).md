---
title: "Dualboot Win10/ Linux Mint (Win not detected)"
date: 2015-12-23
forum: MINT
---

### Post by skinny3 on 2015-12-23
Hi,
I just created this account to get some feedback on my situation:

I'd like to dualboot Windows 10 alongside Linux Mint, but installed Windows10 just a day ago with the result that GRUB was gone. Using a live usb, i could get back to my linux system in the end, recovering GRUB by reinstalling it via terminal. I encountered the problem that it just would not detect Windows10 so i gave Boot Repair a go resulting in the exact same issue.
Short story: I have Windows not being detected by GRUB.

Here is my log from Boot Repair:
[http://paste2.org/vYL95g9k](http://paste2.org/vYL95g9k)

I already tried manually changing the grub cfg without any obvious results.

Best Regards and gladful for any help,
skinny

---

### Post by oldfred on 2015-12-23
Moved to Mint sub-forum.
Mint also has its own forum.
[http://forums.linuxmint.com/](http://forums.linuxmint.com/)

Windows only boots from Primary NTFS formatted partition with the boot flag. 
You now have main Windows install in logical partition, so must have another NTFS partition to boot from.
And Windows boot files are in a FAT32 partition. Did that boot before or was there another Windows install in a primary partition?
Your FAT32 also shows the old DOS boot files.

Boot-Repair also says this:
>  BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.


But all your installs are BIOS. And Windows only boots in BIOS mode from MBR partitioned drives. And Windows only boots in UEFI mode from gpt partitioned drives.
Since installs are all BIOS/MBR, you need to always boot repair disks in BIOS/CSM/Legacy boot mode to avoid confusion. 

It looks like sda1 has only 20MB in almost 1GB. So you could shrink it by 100MB and create a new 100MB NTFS formatted partition with the boot flag. You have available primary partitions. And then copy Windows boot files from sda1 to new sda3.

---

### Post by skinny3 on 2015-12-23
Im not really familiar with all the stuff concerning UEFI/BIOS so that I probably need very precise instructions to resolve that. (I basically started working around this topic today)

> [COLOR=#000000]But all your installs are BIOS. And Windows only boots in BIOS mode from MBR partitioned drives. And Windows only boots in UEFI mode from gpt partitioned drives.[/COLOR]
[COLOR=#000000]Since installs are all BIOS/MBR, you need to always boot repair disks in BIOS/CSM/Legacy boot mode to avoid confusion. [/COLOR]
How to boot in Legacy Mode? At the moment, I got a Linux Mint system on a pendrive which is the same I used to run Boot Repair.

I do not really know what the FAT 32 sda1 is, could it have to with a HDD? Its 1000MiB but I never established this partition....

Edit, I figured it out now. It contains Freedos, that's why it says Windows. This system was preinstalled on the laptop.

---

### Post by oldfred on 2015-12-23
When you installed Windows it should have created 2 NTFS partitions, a 100MB boot and main install. Did you delete the 100MB boot partition?

From your UEFI menu you have two options to boot live installer. One should clearly be UEFI:flashdrive and other flashdrive which then is BIOS/CSM/Legacy.

 UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by skinny3 on 2015-12-26
I did not delete anything as far as I can tell. I installed Windows using unetbootin to boot the image from my stick. But obviously this seems to have gone wrong. I feel like the easiest solution would be installing Windows again after formating the partition that it is on at the moment and then try to fix GRUB with Boot Repair? What do you think?

---

### Post by oldfred on 2015-12-26
That should work.
Are you installing Windows to a primary NTFS partition that has boot flag?

---

