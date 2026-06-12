---
title: "Installing Ubuntu 12.04 on a Dell Inspiron 15Z"
date: 2014-02-25
forum: Installation &amp; Upgrades
---

### Post by juan14 on 2014-02-25
Hi everyone,

I am noob in this Ubuntu universe. I want to try Ubuntu, but keeping my Windows OS, because I know I'll struggle with Ubuntu, and also because I usually work with CAD software (Solidworks and CATIA mainly), and as far as I know (forum reads on the net and some fellow designers experience) compatibility with that kind of software is an issue. I want to make it simple, and since it seems that W8 is installed in the SSD disk, I'd rather leave it there and install Ubuntu in a partition in the HDD.

My PC is a DELL Inspiron 15Z 5523, with the following configuration:
[LIST]
[*]Intel i-7 3537;
[*]Windows 8 x64;
[*]8 GB RAM;
[*]500 GB HDD;
[*]32 GB SSD;
[*]NVidia Geforce GT630 2GB.
[/LIST]

SO, I returned the PC to its original state, cleaning the HDD. I downloaded Ubuntu 12.04 and burned it in a DVD. I enter the BIOS menu and change from UEFI Secure boot ON to Legacy Secure Boot Off, and restart the computer. It then starts reading the DVD and enters the installation menu.

I have read several tutorials that should be "How to install Ubuntu for dummies", but I have problems with them. According to them, after checking that I have internet connection, it should go to the section where I can choose what type of installation I want (whether is delenting W8 and installing Ubuntu, installing Ubuntu alongside Windows etc etc). However, I don't get this step. Instead of it, the window header is the same, "Installation Type", but it presents an list that shows my current partitions.However, the list is empty and I cannot edit it, create new partitions...nothing. Below it, I have a sentece that reads "Where to install the boot charger" (sorry if I am wrong, I am translating from spanish), and the only option I have is "/dev/sda" (see below).

[ATTACH=CONFIG]250684[/ATTACH]

Since from this point on I won't effin know what I am doing, I prefer not doing anything and asking the experts before. I do not dare to press "Install now"...:(

Any ideas?

---

### Post by oldfred on 2014-02-26
If an Ultrabook, it probably has Intel SRT which uses RAID. Older installers did not see Windows but some with the newest versions seem to see Windows but grub does not install correctly as a RAID install is different.
Do you have 12.04.4? That should have all the updates like 13.10.

Some now report just changing UEFI/BIOS to AHCI works, before we had to remove the RAID meta-data from drive. But turning on Intel SRT later seemed to recreate it.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

      
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

