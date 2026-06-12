---
title: "Installing 16.04.1 on Lenovo T460p, Can't write GRUB boot loader to disk"
date: 2016-12-10
forum: Installation &amp; Upgrades
---

### Post by yongtao on 2016-12-10
Hi,

I'm trying to install Ubuntu 16.04.1 server on my brand new Lenovo T460p laptop, and it failed at "Install the GRUB boot loader on a hard disk" step. I'm guessing it has something to do with the BIOS settings. I tried all kinds of changes to the BIOS settings (e.g. enable legacy boot) to no avail. :( Any magic switch that I need to flip in the BIOS in order to get it working? Do I need to disable "Intel AMT"?

Thanks!
Yongtao

---

### Post by ubfan1 on 2016-12-10
Are you dual-booting with Windows?  With Windows in UEFI mode, you should install Ubuntu in UEFI mode.  Usually, grub will just be installed into the existing EFI partition, in another directory, /EFI/ubuntu, but that assumes there is enough spare room for it.  How much room is free in your EFI partition?  It's just a FAT filesystem, and you will need 4 or 5 meg, so usually, there's plenty of spare room.  Next, maybe the EFI filesystem has problems. Can you mount it, see files, create files normally?  Try chkdsk or dosfsck to fix it.

---

### Post by yongtao on 2016-12-10
Thanks ubfan1 for the quick reply.

No I'm not dual-booting. I've already deleted all the partitions I can find. And now the entire disk is under LVM. I've manually created 2 partitions, one for swap, and one for root (ext4 filesystem). I had this configuration on other (non-laptop) machines and they work fine.

Thanks.
Yongtao

---

### Post by ubfan1 on 2016-12-10
I don't use LVM, but don't you usually keep a /boot partition outside of the (encrypted?) volume?  Maybe that's why the installer can't find where to install grub, but you say you've done this before, so....

---

### Post by oldfred on 2016-12-10
If LVM, you have both the ESP - efi system partition and a /boot outside of the LVM.
If BIOS and gpt partitioned you need the bios_grub partition.
Only with BIOS/MBR configuration do you have just /boot & LVM as two physical partitions and whatever logical LVM partitions inside the LVM.

How you boot install media UEFI or BIOS is then how it installs.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by yongtao on 2016-12-10
I switched to UEFI in BIOS, and created a separate EFI partition outside of LVM, and now the boot loader is installed correctly! Thank you all.

-Yongtao

---

