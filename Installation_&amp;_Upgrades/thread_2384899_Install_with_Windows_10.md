---
title: "Install with Windows 10"
date: 2018-02-13
forum: Installation &amp; Upgrades
---

### Post by abxrazorback on 2018-02-13
I am getting ready to install Ubuntu on a new computer.  Windows 10 is on its own drive (M.2) and I plan on installing Ubuntu on a separate drive.  I have used Ubuntu before but want to make sure my windows bootloader is not overwritten in the install process.  Is there a prompt during installation that asks where to install the boot loader, i.e. grub?
Thanks

---

### Post by ubfan1 on 2018-02-13
Our assumption here is that your new computer with Windows 10 has  Windows installed in UEFI mode -- please confirm.  If you have Windows in UEFI mode, is the Ubuntu disk an internal disk, or external (USB, eSATA, etc.)?  UEFI Ubuntu bootloaders are put onto the EFI partition in a separate directory, /EFI/ubuntu, from the Windows bootloaders, so will not overwrite.  Non volatile memory selects which bootloader to boot (in order).  Each disk may have one EFIpartition, and each EFI may have a default bootloader, in /EFI/Boot/bootx64.efi (for 64 bit architecture).  This default bootloader may be overwritten by the Ubuntu installation, but it normally is not used except on removable boot media (which had no nv memory entry for the boot, but which may be selected for booting).  If your Ubuntu disk is a permanent part of your setup, then it doesn't matter that grub gets installed to  sda (the windows disk). If your Ubuntu installation is to be removable (not present all the time), then things do tend to get messy, as there are several bugs about where/how grub gets installed.  The  simple configuration of putting grub
only on the second disk, and booting it when you  want Ubuntu, leaving the first Windows disk alone  does not seem to be in the installer's capabilities.  This is where all the advice to remove the Windows disk, then install Ubuntu onto the new disk, which is now sda, comes from.   I think the install these days puts grub into the default location too.

   You can manually  fix things if Windows is present, but that takes a little more work (but no screwdrivers needed ;^).
If you install Ubuntu to the second disk (and want to separate them)
1) Grub boots off sda, but has its config files on the Ubuntu disk (sdb?).  Copy the entire EFI partition from sda to sdb.  Now sdb will boot with grub just fine.
2) Reset the first nv ram boot entry back to windows from Ubuntu, now Windows will boot, regardless if the second disk is present.
3)Use the EFI menu (some key at power-up, function, esc, del, ...) to select boot OS/device, and select the second disk to boot Ubuntu,

---

### Post by oldfred on 2018-02-13
The installer will not create an ESP - efi system partition on any drive other than sda. Or it will add a folder into the sda drive's ESP.

So for  ubfan's suggestion of copying ESP from sda to sdb, you must partition in advance using gpt and include as one of first partitions the ESP as FAT32 with boot flag if gparted or code ef00 if using gdisk on command line.
 [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace

[/URL]
  Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or
sudo parted /dev/sda mklabel gpt 

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by abxrazorback on 2018-02-14
Thanks for the replies.  So, I think I am finding out what my other problem has been.  My current setup has Windows 10 on an NVME drive, another NVME drive for Windows data, an SSD showing up as dev/sda which is another Windows data drive and finally an SSD showing up as dev/sdb on which Ubuntu is now installed.  I have had trouble with Grub finding Windows to add to the Grub start menu.  It has also given me trouble in another distro of linux (Mint).  Is this setup going to work for dual boot or do I need to do something else?  Fdisk shows all drives with no problem.  Thanks.

---

### Post by oldfred on 2018-02-14
This has not been updated to show NVMe drives well. First part of report will miss those drives.
But rest of report will show a lot of details.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by abxrazorback on 2018-02-14
I will get that information when I get home.  Thanks

---

### Post by abxrazorback on 2018-02-14
For some reason Ubuntu is not booting.  I have decided that I will relocate my SSD for Ubuntu to sda location on the motherboard and reinstall.  I think it may have been the problem all along as grub wants to be installed on it.  I hope after doing this it will install and then find Windows 10 on the NVME drive.  Does that sound logical?  Thanks

---

### Post by oldfred on 2018-02-14
Cannot hurt.

With SATA only drives, Ubuntu's UEFI grub only installs to first drive or sda.
But with NVMe drive also it seems to know to install grub to that. Not sure what its logic really is.

---

