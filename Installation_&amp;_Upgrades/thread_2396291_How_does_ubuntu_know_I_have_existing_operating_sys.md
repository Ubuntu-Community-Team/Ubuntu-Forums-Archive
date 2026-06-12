---
title: "How does ubuntu know I have existing operating systems if it can't see my drive"
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by alekmabry24 on 2018-07-13
Hello!

I am attempting to install ubuntu onto a USB drive completely separate from my main hard drive, I don't want to boot up my computer normally and see a grub prompt if my USB is not plugged in.

I just got the classic "Force UEFI Installation?" popup:
```
This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.
```

How does ubuntu know this? It can't even see my hard drive because it is RAID storage. I don't want to force an installation if there is any chance that it will install GRUB to my main drive

---

### Post by The Cog on 2018-07-13
Not sure if it could see stuff on RAID drives. However...
The installer generally wants to install the bootloader to the partition table on the first hard drive (sda). Which you say you don't want.

Look at this set of screenshots: [https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/install-ubuntu-16-04-with-screenshots.html](https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/install-ubuntu-16-04-with-screenshots.html)
Look for the screenshot where he has clicked for an installation type of **Something else**. The following screenshot has a drop-down list for where to install the bootloader, just above the Install Now button. Make very sure you select the right device for the bootloader before continuing the install. sda is probably your main drive, but don't take that for granted - check the size etc to confirm.

How you then persuade your PC to boot from a drive other than your main drive is another problem, but I guess you can figure that one out.

---

### Post by oldfred on 2018-07-13
That works if you are doing a BIOS install. And that may be easier.
I suggest even if you really want the 35 year old BIOS configuration you still use gpt and add both an ESP & bios_grub partitions. The ESP could be used later if you want UEFI and BIOS boot from gpt requires bios_grub partition.

If you do an UEFI install the combo box on the partitioning page does not do anything. It still installs to the first ESP/drive it sees, normally sda.
I just tried again with 18.10 and installing to sdb. I even told it not to use sda's ESP, and use ESP on sdb, but it installed to sda.

You can install without grub, but then have to manually install and if USB drive use --removeable option. 
All my installs to USB drives, I backup ESP on sda, let it install to sda's ESP. Then I copy sda's ESP to USB drive twice. UEFI only boots from /EFI/Boot/bootx64.efi, so I have to copy 2nd time to /EFI/Boot and rename shimx64.efi to bootx64.efi. And that version of grub requires /EFI/ubuntu folder & grub.cfg.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by ubfan1 on 2018-07-13
Although the standard advice is to install Ubuntu in the same mode as Windows, if you have two separate boot devices, and your machine is capable of booting either mode (legacy,UEFI), (perhaps giving you the option to set a preference of a mode if both are possible), it really shouldn't matter. However, UEFI installs to a USB will install grub to the first EFI partition it finds, not what you want.  The usual suggestion is to remove the first disk, do the install, then replace the first disk.  A legacy install to the USB should use the bootloader location you provide when selecting the "something else" option.

---

### Post by The Cog on 2018-07-20
> If you do an UEFI install the combo box on the partitioning page does not do anything. It still installs to the first ESP/drive it sees, normally sda.
I just tried again with 18.10 and installing to sdb. I even told it not to use sda's ESP, and use ESP on sdb, but it installed to sda.
Ooh! I was not aware of that. I think the installer should make that more clear to the user.

---

