---
title: "What happens to GRUB/my Windows installation if I format my linux drive for reinstall"
date: 2018-06-21
forum: Installation &amp; Upgrades
---

### Post by erhammon on 2018-06-21
Hi,

 I've been having lots of issues with my Ubuntu installation, and would like to just start fresh. I'm running a dual boot system, with my Windows installation on a solid state, and my Ubuntu installation on a hard drive. I'm using 16.04 LTS, and grub as my boot loader. If I were to format my linux hard drive from Windows disk managment or from a live usb, will grub be removed? Will I still be able to boot to Windows from grub? With a formatted drive, could I just go through a live USB installation process on the formatted hard drive again?

Thank you

---

### Post by oldfred on 2018-06-21
Lots of issues, but only if done wrong.

Only use Windows tools to edit NTFS partitions. And then always reboot as it wants chkdsk.
Use gparted or other Linux tools for Linux partitions.

Is system UEFI or BIOS? That will determine where boot loaders are. 
If UEFI all boot loaders are in the ESP - efi system partition.
If BIOS, best to have Windows boot loader on Windows drive and grub on Ubuntu drive and set BIOS to boot Ubuntu drive. Then if Windows has issues you can still boot Windows from BIOS.

Reset Windows to default boot first whether UEFI or BIOS. IF BIOS reinstall Windows boot loader to MBR of Windows drive and make sure it boots.

Make sure you have really good backups of both Windows & Ubuntu. You want all your data & list of installed apps as the minimum. Reinstall may offer to save data, but if you have issues, it may just keep your issues.

Only use Something Else install option. And be sure to boot installer in same boot mode as Windows is installs whether UEFI or BIOS. and if BIOS install grub to Ubuntu drive.

Post this if more questions:
sudo parted -l

---

