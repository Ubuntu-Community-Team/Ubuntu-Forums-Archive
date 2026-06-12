---
title: "Questions before manual upgrade to 14.04 on Dual boot XP/Ubuntu."
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by benawhile on 2014-04-23
I have a Windows XP /Ubuntu 12.04 32 bit dual boot system with partitions I created manually. (see screenshot). I don't have a separate home partition and don't use the home folder except when I can't stop ubuntu from defaulting certain things to it. /dev/sda2 was created just in case I wanted anther windows os.
My computer is a home build MSI K9VGM-V Mobo. 7 years old but everything works fine. 80G HD. 2 x 1G RAM in two slots. 

I want to do a fresh install of 14.04 retaining the dual boot. I intend using a usb drive as I have no DVD burner. The BIOS has a USB-ZIP and USB-CD ROM option in the boot order list.

I have 6G unallocated space. I want to add it to the NTFS data partition. Can I resize the ntfs data partition during reinstall to add the unallocated space to it?

 Is there enough space in /dev/sda6 for 14.04?
I want to upgrade the RAM to 2 x 2GB and install the 64 bit Ubuntu version. must I change the swap partition, and to what size?

I have seen this warning in oldfred's UEFI page:
"Do not attempt to reinstall Ubuntu except with Something Else" Is this just for UEFI? One post in askubuntu says to "install alongside windows" but another says to use "something else". Which should I do?

 Does the grub reinstall into the same place automatically or do I have to reinstall it? If I have to reinstall it is the current partition big enough?

There is a warning about grub here: Is it relevant to my case?
 [http://ubuntuguide.org/wiki/Ubuntu:All#Installing_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:All#Installing_Ubuntu)
 *&#8243;there is an option to install the boot loader to /dev/sda, which really installs the Grub2 boot loader to both the MBR (Master Boot Record) as well as the partition into which (K)Ubuntu will be installed. Pay careful attention during this step if your system uses a boot partition, uses multiple OS (more than 2), or chainloads bootloaders. For systems with such a boot partition, it is best NOT to overwrite the MBR. In this case, the boot loader should only be installed to the partition in which the (K)Ubuntu OS itself will be installed. &#8243;*

I am confused by this as my grub doesn't look like it's in the OS partition.
 N.B. I don't seem to have a partition that is simply named /dev/sda. But I altered some names to enable storing files to the shared ntfs partition instead of the home folder. I can't remember exactly what I did except that I edited &#8243;fstab&#8243;. 

 Will 64 bit make a difference to printer and webcam compatibility (HP Deskjet F 4180 and Logitech C170 webcam)? In general is there any risk that upgrades of ubuntu don't carry the same drivers?

I couldn't find a formal guide for a fresh install of Ubuntu into a dual boot system. Is there one? One with screen shots would be nice, but all I can find is for setting up for a new dual boot system. That's why I have had to trawl the forums and &#8243;askubuntu&#8243; and post this question to help fill in the knowledge gaps. When I am finished I would be willing to contribute to a central source of info with my own experiences.


  [ATTACH=CONFIG]252427[/ATTACH]

---

