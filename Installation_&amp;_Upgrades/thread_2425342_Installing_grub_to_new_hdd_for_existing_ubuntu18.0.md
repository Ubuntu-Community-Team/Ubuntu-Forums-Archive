---
title: "Installing grub to new hdd for existing ubuntu18.04 amd64"
date: 2019-08-24
forum: Installation &amp; Upgrades
---

### Post by arthur_8200 on 2019-08-24
Hi,

I have had two harddisk, one with windows+grub and the other one with ubuntu.
But now I want to use only the ubuntu and therefore I need to manually install grub onto the ubuntu hdd (with ext4 root partition).

I tried some grub recovery tutorial but I had no success.

Can someone give me a hint?

Best regards,
Arthur

---

### Post by oldfred on 2019-08-24
UEFI or BIOS installs on both drives?

If UEFI you  need an ESP - efi system partition  (FAT32 with esp/boot flags).
If BIOS you can just install grub bootloader to MBR of drive if drive is MBR(msdos) partitioned.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by arthur_8200 on 2019-08-24
Thank you, oldfred!

I have had used UEFI on the old harddisk.

Do I need to use again UEFI? Or can I also use BIOS now? Actually I will use only ubuntu, so I don't need UEFI.

Best regards,
Arthur

---

### Post by oldfred on 2019-08-24
If hardware is UEFI, I suggest using it.
Some others prefer the now old BIOS configuration.

If you want to use BIOS, I then suggest using gpt and having both an ESP - efi system partition and a bios_grub partition. The bios_grub partition is required with BIOS boot on gpt drives, but is only 1 or 2MB and is unformatted. That way you can just reinstall grub's efi version of boot loader to convert to UEFI later if desired. Otherwise conversion from BIOS/MBR to UEFI/gpt is a lot more complicated. 
But either way good backups are required.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by arthur_8200 on 2019-08-25
Now I have booted from boot repair usb stick but it failed:
[http://paste.ubuntu.com/p/64w7hdtfvv/](http://paste.ubuntu.com/p/64w7hdtfvv/)

:-(

---

### Post by oldfred on 2019-08-25
I really do not know LVM nor encryption.
But your bios_grub is the size of a /boot partition usually used with LVM?
The bios_grub is normally 1 or 2MB unformatted.
But default installs of LVM using separate /boot often were too small now with multiple kernel versions. So now default is either larger or /boot is inside LVM.

       [https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

---

