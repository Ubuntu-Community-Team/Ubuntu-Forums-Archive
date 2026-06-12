---
title: "UEFI installed questions"
date: 2016-09-26
forum: Installation &amp; Upgrades
---

### Post by kahraman.og on 2016-09-26
Hello,

I have some question that I can not find them. I will be happy if you can help me here:

1- When we start HDD with "Fallback path" mode. UEFI firmware directly finds \EFI\BOOT\BOOTx64.EFI file on the harddrive. This will start a bootloader (shell). My question here is: Which partititon will load? And where is the config files of this shell?

2- I read that ESP can contain kernel images. Why it contains kernel images? We don't put the images on different partitions?

3- I read that ESP can contain driver files. Why it contains the driver files. To open the shell \EFI\BOOT\BOOTx64.EFI with better features or to open the operatinG system with better options. I mean we will not install some driver anymore, if they are already on ESP directory?

4- I installed UBuntu 16.04 64 bit on my UEFI-based Laptop which has GPT partitioned HDD. But I see that there are files inside /boot/grub directory. Why we still use grub? THe new grub is not the executable: \EFI\Ubuntu\grubx64.efi ?

Thanks in advance

---

### Post by oldfred on 2016-09-26
The /EFI/Boot/bootx64.efi is just UEFI default drive boot entry. It can be any valid file which may or may not be complete. With Windows systems it usually is just a copy of Windows bootmgfw.efi.
With Ubuntu installer it is a smaller configuration of grub's files that just needs what is required to boot installer. With a full install the version of grub is hard coded to find /EFI/ubuntu/grub.cfg to chainload using a configfile to find the rest of grub in your install.

More info:
 UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition) 

[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

