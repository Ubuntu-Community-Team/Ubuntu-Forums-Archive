---
title: "Move Device for Boot Loader"
date: 2020-01-03
forum: Installation &amp; Upgrades
---

### Post by dwlamb on 2020-01-03
[ATTACH=CONFIG]284741[/ATTACH] Attached is a screen shot of the Kubuntu installation process for preparing the hard drive.  Once an installation is complete, how do you move where the boot loader information is located?

I took the screen shot from a virtual machine to clarify what I am asking about.  I need to move the boot loader information on a host system/actual PC.  Inadvertently, I specified /dev/sda though the drive for my Kubuntu system is /dev/sdc.  Anything I have googled about moving the boot loader info leads to rebuilding GRUB2.  I think what I am asking about is how to relocate the GRUB2 to another device.

I need to move the boot loader information for /dev/sda is actually a drive using a removable disk tray. Swapping the drive with another and I started to get errors that my Kubuntu root directory on /dev/sdc is full.  From my experience /dev/sda can not be removed.

As well, I want to reconfigure my hardware to install SSD on SATA0 which implies /dev/sda.

Is there a way to move the boot loader information without doing a reinstall of the system?  I tried doing a fresh install with the boot loader information specified to a different /dev/sd?.  Restoring my system files from rsync did not work for the boot loader information from the backup pointed, presumably, to /dev/sda.

---

### Post by oldfred on 2020-01-04
Is this a BIOS system with BIOS version of grub?
With UEFI you choices do not matter, and Ubiquity only installs grub to ESP - efi system partition on first drive.

If booted in Ubuntu you can install grub anywhere in BIOS mode. 
If from a live installer in BIOS mode, you have to mount the / partition  (and /boot if separate).
sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

#reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

If just installing grub to a new flash drive, you have to also create your own grub.cfg.

BIOS grub also has a setting on where to reinstall grub on major update. If you need to reset that, do this:
#to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short

---

### Post by dwlamb on 2020-01-04
> **oldfred said:**
> Is this a BIOS system with BIOS version of grub?
With UEFI you choices do not matter, and Ubiquity only installs grub to ESP - efi system partition on first drive.

I don't know.  How do I tell?  I haven't altered much in the BIOS, mainly the order for boot device(s).

As for the rest of your answer, thanks!  It has been very informative and chocked full of info to try.

---

### Post by oldfred on 2020-01-04
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

This will tell you which boot mode your are in.
Check UEFI boot mode
[ -d /sys/firmware/efi ] && echo EFI || echo Legacy

Microsoft has required UEFI/gpt on all new pre-installed systems since Windows 8 released in 2012.
But users can install in either mode. Many do not know and how you boot install media UEFI or BIOS is then how it is installed.

---

### Post by dwlamb on 2020-01-05
Thanks for your help oldfred.  I was able to determine it is a BIOS of grub.  With your terminal command assistance I set the boot loader information to the right drive, reconfigured GRUB2 and rebooted.  All is well now.

Happy 2020

---

