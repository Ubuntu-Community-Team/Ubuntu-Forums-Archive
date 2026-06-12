---
title: "Config help for grub, Linux and Windows on different disks"
date: 2015-10-04
forum: Installation &amp; Upgrades
---

### Post by Joakim_Nordell on 2015-10-04
I would like to configure grub so I can pick my Ubunto or Windows 7 from a boot menu.
The two different OS installations are on separate disks, sda and sdb. It seems to me that the BIOS / EFI environment variables are updated after the Linux install so that windows cannot be selected as a boot option from the BIOS boot menu. Disk sdb was physically disconnected during the Linux install, so there should not be any updates written to that disk.
I would like to describe the system in some config files to grub and then get a confirmation from update-grub or so that it has detected the possible boot options. I am visually impaired / blind and therefor dependent on screen reading software. This software is usually started after the OS it selves. If the system start half the way and then present some trubble, I will not even be able to read them. I was recently in such a situation and would like to avoid it now.
Below is a listing of the different drives on my system.
Is it really correct that the bootable flag should be active for sdb2? Isn't that old legacy stuf?
How can I make such configuration and which files should I edit?


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   488397167   244198583+  ee  GPT

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2   *      206848   351649791   175721472    7  HPFS/NTFS/exFAT

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   781422767   390710360    7  HPFS/NTFS/exFAT

--
Joakim

---

### Post by oldfred on 2015-10-04
You are showing gpt partitioning on sda. If that is Windows it only can be UEFI boot. But if Ubuntu it could be either UEFI or CSM which really is the old BIOS. 

But your sdb is MBR or msdos partitioned which for Windows can only be a BIOS boot install.

With Windows BIOS installs, it normally installs a hidden 100MB boot partition and the main install. Then main install often does not have all the boot files and will not boot on its own. We often suggest to copy boot files to main install just as a backup. Many users do not know the 100MB boot partition is essential as Windows does not normally show it. But if you have boot files in both partitions grub will find both sets as it looks for files, not boot flag. Windows has to have boot flag on partition with boot files to know which partition to boot.

But is system is UEFI and operating system is installed in UEFI boot mode, boot flag must be on the ESP - efi system partition for all systems.

And if you install one system in BIOS mode and another system in UEFI boot mode, you can only boot from UEFI boot tab, or one time boot key's boot menu. 

Do not know if UEFI or BIOS works with a screen reader?

---

