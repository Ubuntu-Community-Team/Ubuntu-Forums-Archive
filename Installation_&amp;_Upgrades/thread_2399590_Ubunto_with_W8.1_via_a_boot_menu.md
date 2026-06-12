---
title: "Ubunto with W8.1 via a boot menu"
date: 2018-08-27
forum: Installation &amp; Upgrades
---

### Post by michaels-perry-4 on 2018-08-27
Hi

I run an Acer E15 E5-521 65DE laptop that runs Windows 8.1 and uses UEFI. I want to be able to dual boot via a menu (grub?) so I can select which OS to start at boot time. The hard disk is partitioned into two main sections and I wish to use space on the D:/ drive for Ubuntu. Or would I be better off using a 64GB USB SDXC memory card? What steps do I have to take to enable that and set up Ubuntu 18.04? I have an ISO of Ubuntu but the Windows 8.1 was ore-installed so I do not have an ISO for that. 
I am not familiar with settings in a UEFI system so clear steps would be much appreciated, please?

---

### Post by oldfred on 2018-08-27
You cannot use Windows formatted partitions like a d: "drive" for Ubuntu. It requires ext4 format as default or one of many other supported Linux partition. Windows partitions do not have support for ownership & permissions which is part of why Linux is more secure.

Does your system boot from memory cards? A few smaller type laptops do, many larger systems do not.

You will have two menus to boot. UEFI has its boot menu and grub will offer to boot Windows.
But grub only boots working Windows or Windows that is not hibernated nor needs chkdsk (often after abnormal shutdown). And Windows now uses fast start up which is just always on hibernation. So make sure fast start up in Windows is off.
So also make a Windows repair/recovery flash drive. You should have that anyway.

Be sure to boot install media in UEFI boot mode.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

In link below in my signature are 9 "Easy" steps to install. And for those not familiar with some of those details lots of additional info with links on details.


Acer also has an unique requirement of setting an UEFI passworks and from within UEFI drilling down to the .efi boot files and setting "trust" on booting with those files.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) 
            Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
    
Many with Acer have also had to update UEFI  from Acer.
       Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

This user posted lots of details and is an Acer e15.
       Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
[https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074](https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074)
[https://askubuntu.com/questions/886536/how-to-install-ubuntu-on-an-acer-with-preinstalled-windows-10-home](https://askubuntu.com/questions/886536/how-to-install-ubuntu-on-an-acer-with-preinstalled-windows-10-home)

---

### Post by michaels-perry-4 on 2018-08-27
My laptop has a 1TB drive partitioned into C: for Windows and D: for data. I can divide that to give another partition for Ubuntu. It boots from the C: drive and not an external device (the UEFI is not even set to boot from USB) so can I use my 64 GB SDXC card instead of changing the main HDD partitioning? I assume I will need to change some settings in the UEFI boot sequence - but how and to what? 

Is it possible to set up the machine to be able to boot either Windows 8.1 or Ubuntu 18.04 without having to fiddle about each time - I only want what was possible before this UEFI system was devised, a simple boot menu to select from. 

Thanks

---

### Post by oldfred on 2018-08-27
With UEFI both UEFI & grub have boot menus.
Are you really booting from C: drive? Windows in UEFI mode really boots from ESP - efi system partition and grub will add another folder for UEFI to boot.
Or if system not UEFI, Windows boots from a Boot partition which you normally do not see.

Grub only boots working Windows, so sometimes you have to either directly boot Windows from UEFI or boot Windows repair/recovery disk. Whether you have Ubuntu or not, you may have to manually boot from UEFI or Windows repair disk when (not if) Windows gives you issues.

---

### Post by michaels-perry-4 on 2018-09-02
All I know is that when I start my laptop, it boots directly into W8.1. What I want is either to boot to a menu so I can choose whether it boots into Ubuntu or W8.1 or else boots into one of the OSs depending on whether a USB storage device is inserted or not - see next paragraph. The laptop has a UEFI system that is normally not visible, but I can access it using F2 during start-up. 

I would prefer to have Ubuntu on an SD card (64 GB) plugged into a USB adapter so that if it is inserted I get Ubunto and if it's not then I get W8.1. That will allow it to be formated to suit Ubuntu and have the needed partitions for Swap, etc. 

The main HDD has several partitions: an OEM partition (600MB); a UEFI partition (300MB); a recovery partition (450MB); an OEM partition (15.44 GB); C: drive (250 GB) and D: drive (650MB). Windows 8.1 is on C: drive.

---

### Post by oldfred on 2018-09-02
Ubuntu does not use a swap partition, anymore. It now uses a swap file. It will use an existing swap partition if one is found.

Only some systems boot from SD cards directly. But if thru a USB adapter, you should be able to directly boot it. 
But full installs to boot from an external device in UEFI mode require a bit of preparation and reconfiguration.
You must partition external drive in advance and be sure to include an ESP - efi system partition on external drive. Issue is UEFI only boots from ESP on external with /EFI/Boot/bootx64.efi. But grub with a full install only installs to an ubuntu folder and boots from /EFI/ubuntu/shimx6.efi or grubx64.efi and has to be able to see a grub.cfg in /EFI/ubuntu. 
My work around has been to copy from /EFI/ubuntu on internal drive's ESP to external drive's ESP twice. Once to /EFI/ubuntu and again  to /EFI/Boot and rename shimx64.efi to bootx64.efi.  

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

    If using gparted to partition, be sure to change to gpt from default MBR first.

UEFI will always have a boot menu you can use. And in UEFI you can set the external drive as first in boot order and then Windows as second. If first not found, it goes to second in boot order.
Grub will also offer to boot Windows if Windows hibernation/fast start up is not on.

Only use Something Else install option. 
If you need more info, lots of details & links to more info in link below in my signature.

---

