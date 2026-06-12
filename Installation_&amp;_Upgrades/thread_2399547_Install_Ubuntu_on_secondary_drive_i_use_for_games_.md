---
title: "Install Ubuntu on secondary drive i use for games i play on Windows 10"
date: 2018-08-26
forum: Installation &amp; Upgrades
---

### Post by rediixx on 2018-08-26
Hi, as the title says i want to install Ubuntu on my second HDD that i already use for some games i play on Windows 10, i want to know if its possible and if thats the case can someone tell me how? Do i just create a partition on that HDD and then install it normally or theres another step i need to do? Please help

---

### Post by oldfred on 2018-08-26
With two drives often easiest to disconnect all but Ubuntu drive. 

If Windows 8 or 10 and you have NTFS partition you still must have Windows fast start up off on Windows drive as that adds the hibernation flag to all NTFS partitions.
Best to use Windows to shrink NTFS & reboot immediately and run chkdsk on that partition. But do not create any partitions with Windows.

Is Windows installed in UEFI or BIOS boot mode? 
You want Ubuntu in same boot mode. How you boot install media UEFI or BIOS is then how it installs. And drives should be gpt if using UEFI. If not installing Windows, drive can be gpt for Ubuntu in either UEFI or BIOS boot mode, but you must have extra supporting partition(s). And ESP - efi system partition if UEFI and/or bios_grub if installing in BIOS boot mode.

Post this:
sudo parted -l

---

