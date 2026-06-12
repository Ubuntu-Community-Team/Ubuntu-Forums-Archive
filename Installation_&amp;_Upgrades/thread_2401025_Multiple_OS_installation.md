---
title: "Multiple OS installation"
date: 2018-09-12
forum: Installation &amp; Upgrades
---

### Post by hennmann on 2018-09-12
I have two computers running the latest Ubuntu and one of which had Windows 7 on a smaller HHD with only one partition. I decided to install the latest version and Ubuntu gave me the option to resize my partition and install Ubuntu beside my Win 7 and give me a multiple OS bootloader and this is on my Gigabyte Mobo and other than video card driver issues the two OS work fine. Now I'm attempting to install multiple OS on my MSI 970A SLI Krait with a 1 TB Western Digital 3D NAND SSD where I set up 3 partitions, one for Win 7, one for Ubuntu and a third for more options later on. Unlike my first attempt on the Gigabyte the installation recognizes or acknowledges that I have 3 partitions one with windows including the additional small system partitions Windows sets up BUT the installation doesn't give me the option of which partition to install into, just the nag that no ROOT partition has been created. Anyway when all was said and done the whole partition scheme got deleted, my Windows boot loader is gone and I now have a none functioning system. I have come to the conclusion I need one partition with Windows installed and then be forced to create additional partitions after the fact during a Ubuntu installation? Why?? Multiple partitions are the same as multiple HHD so where is my option to manually select which partition to install and which partition to install my bootloader? What do I need to use to correct this? Another reason why I feel I shouldn't have to use the same method as I did on the single small hard drive is lets say I want Windows 7 on one partition, Win 10 on another and then Ubuntu on the 3rd?? What is required to get around this? From what I experienced in the past was it is always easier to install Windows first and then install Linux because the Windows crap will over wright the boot loader

---

### Post by TheFu on 2018-09-12
BIOS or UEFI boot?  It matters.
MBR or GPT disks?  It matters.  MBR has some limitations to make things harder.
Also, if using 32-bit Windows, that forces some limitations. Similarly, 64-bit Windows mandates other choices.

The first step to getting help is to provide lots of details, **accurate**, information.  The way to gather that is to boot an Ubuntu Live, install **boot-repair** (it will only be there while this boot is running), then run it ONLY CHOOSING the option that gathers data, do not ask it to attempt repairs.   Gathering the data will generate a URL.  Post that URL here.

Once that is posted, someone might be able to figure out what you have, what you want and what you need.

BTW, walls of text are next to impossible to read. If you edit the first post, break it up into paragraphs, it will be easier to read and people are more likely to help.

---

### Post by hennmann on 2018-09-15
Okay I will start at the beginning:
First I installed Ubuntu on my MSI  A970 SLI Krait and had a new SSD dedicated to only one OS, Ubuntu to see how everything behaves and it installed smoothly with Zero driver issues etc. Since this board was running an FX 6300 CPU I decided to install Ubuntu on my Gigabyte with an AM3 640 processor to see how it performed etc. with the only issues being drivers needed to be updated for the GT 710 Video card.

The Gigabyte mainboard computer also has a single hard drive in it as well so I installed only Win7 Pro 64 by itself and got this all working with all updates etc. and at this point decided to give multiple OS a try on one HHD.

My intention was to install Ubuntu back onto this computer after trying both OS to see how this recently acquired hardware would work with the idea that if Windows got lost it wouldn't be a big deal as I had multiple OS in the past BUT I always had Windows on one hard drive and Linux on another AFTER installing Windows first as it usually is easier this way because if installed first Windows can't MESS UP the Linux Boot loader!

Okay so with a working Win7 64 in goes the USB drive with Ubuntu and I reboot, select the USB drive to boot first and during the installation it gives me the option to run Ubuntu alongside Windows and I had no partitions set up except what Windows sets up during install such as the small system partition with the main OS partition along with a recovery partition. Also it allows me to resize  the one and only main partition with Win7 on it to make room for Ubuntu while not destroying the Win7 installation, and install a boot loader to select between the two. When all is said and done both are working fine with a properly functioning boot loader. 

Now back to the Krait with a newly updated FX8370 CPU, I decide to run multiple OS on this computer so I do a clean install of Win7 Pro 64 on a 1TB SSD and during installation I set up 3 partitions, one for Win7 Pro 64, one for Ubuntu and a third for the option of Win 10 in the future if I desire to do so.

Win7 is now installed and now I decide to attempt to add Ubuntu to one of the extra partitions and during this adventure there didn't seem to be the option of installation just into the extra partition with the installation of the boot loader to allow selective boot to Windows or Ubuntu. Remember multiple partitions can be used like multiple hard drives. 
When all was said and done Ubuntu kept complaining there was no Root Partition selected etc.

What am I doing wrong where I don't have to resize or create partitions like my first multiple OS attempt? My assumption is do I have to have only one partition, install Windows first, Install Ubuntu second requiring me to resize the single partition into two like the install on the Gigabyte creating partitions after the fact? Also if this is the case it would appear I would have to install Win7 first, Win10 second and lastly Ubuntu?? 
I have an Acer Aspire One Netbook with multiple partitions, one with Win 7 Starter, one with Win10 and a third unused partition for Ubuntu later on. In this situation Win 10 set up a boot loader so I can choose either/or. This is going to be the same scenario as my Krait perhaps or is there a procedure to install Ubuntu on an empty dedicated partition AND install 10 later on? Also I might add all 3 will be 64 bit as well.

---

### Post by Dennis N on 2018-09-15
> Win7 is now installed and now I decide to attempt to add Ubuntu to one of the extra partitions and during this adventure there didn't seem to be the option of installation just into the extra partition with the installation of the boot loader to allow selective boot to Windows or Ubuntu.

Yes there is such an option. At the installer's "Installation Type" screen, select the "Something Else" option at the bottom, which leads to the partitioning screen. here you select the desired partition and then use the change button to fill in some details in the dialog that pops-up, specifying it to be formatted ext4, mounted at /. Then you can proceed to install.

---

### Post by oldfred on 2018-09-15
Did you miss TheFu's comments on UEFI & BIOS & MBR & gpt?

You new hardware is UEFI, but has CSM support for the now 35 year old BIOS/MBR configuration.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

The Windows 7 DVD only installs in BIOS/MBR. But can be copied to a flash drive and some files moved/renamed to make it UEFI bootable.

For both Windows & Ubuntu how you boot install media UEFI or BIOS is then how it installs. And you want all installs in same boot mode.
Note that Windows in UEFI mode must have gpt partitioning. And Windows in BIOS boot mode must use MBR partition with its 4 primary partition limit.

      
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Windows 10 is not as dual boot friendly as it turns on its fast start up which is just hibernation as Windows still boots slowly. But grub only boots working Windows, so when Windows turn fast start up back on with updates (which it will do), you will not be able to boot Windows from grub.
If you keep them on separate drives with each having its own boot loader, it should work. But you are using BIOS and not taking advantage of gpt & UEFI. 

       
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by hennmann on 2018-09-16
Yes Dennis N I used this option and at the time I didnt see these options
Now my question to oldfred is why the @*&% should installation become so damn complicated?? Slap a windows DVD or USB into the drive or port, set up your partitions etc. bing bang boom you are up and running. My Gigabyte with ONE partition, one hard drive was not this complicated and this is AM3. My Krait is only AM3+ from 2015
KISS
Keep
It
Stupid
Simple

Years ago I used Mandrake, Redhat etc. and there were a number of partitioning options, drive options etc. including the boot manager now we are talking BIOS, UEFI etc. etc.
I most certainly dont have a Comp Sci degree and this is becoming a different language all together. Ask yourself and others, why do very few use Linux??

---

### Post by oldfred on 2018-09-16
Talk to Microsoft.

If you just want Ubuntu, you still have to change some settings in UEFI from "Windows" to "Other". Even if installing Windows 7 you have to make that change to turn off UEFI Secure Boot as Windows 7 does not support UEFI Secure Boot. And even with BIOS I had 5 or 6 settings I changed to make it work or work better.

But once you make those changes, and boot installer, it just installs. I now have the Ubuntu install down to 10 Minutes once ISO on hard drive and / partition on SSD.

---

### Post by C.S.Cameron on 2018-09-17
They could probably come up with a more descriptive name than "Something else".

A word like "Manual" would be my suggestion.

---

