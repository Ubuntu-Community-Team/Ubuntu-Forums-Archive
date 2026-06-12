---
title: "Some more specific questions about multi boot with Windows 10"
date: 2019-03-17
forum: Installation &amp; Upgrades
---

### Post by aajax on 2019-03-17
I've been using Ubuntu for quite a while now.  Most recent version is 16.04 LTS.  All of my past experience involved BIOS type computers.  What's new is UEFI.  It's been a real chore but I've finally figured out how to get Windows 10 to multi-boot in what I'd call single volume mode.  Because the Windows 10 installer is so crude, I've had to go back to the XP and before days to do it.  It seems that the Windows 10 installer refuses to use an existing EFI system partition (ESP).  This is what I'd call the boot partition but for some reason Microsoft seems to want to call the system that it, the ESP, boots the boot partition.  To try and avoid confusion I'll use the term ESP to refer to the partition that UEFI boots to.  Interestingly the UEFI on my computer refers to it as a Windows Boot Manager.  Wouldn't you think Microsoft might call that partition the boot partition?  Apparently, NOT so!

Anyway the ESP can be revised and updated using a Windows supplied program called BCDedit.  Is it possible that Ubuntu also has such a program?  If so, might it be called Grub2?  If not, what is it called?  It would also be nice to know if the System Rescue CD can be used to do this.

On my past Ubuntu multi boot systems (i.e., only Ubuntu with NO Windows installed) that use BIOS/MBR I've chosen to install a mini Debian system on a separate partition that is used as a boot manager.  This way none of the Ubuntu systems, that are actually being used to do work, depend on any of the other such Ubuntu systems to boot.  In that, they can be independently restored with no affect on each other.  From what I've learned so far it looks like the ESP needs to perform the job done by my Debian Boot Manager.  While the ESP cannot be booted into and used to update itself, BCDedit can be used from another Windows system or even WinPE as well as the Windows installation program to do this.  Therefore, like my Debian Boot Manager it is fairly independent.

What I don't know is whether or not the Ubuntu installation program is a bit more elegant than the Windows equivalent.  If the Ubuntu installer is able to add what, I think, UEFI (and of course Windows) calls a Windows Boot Loader entry into an existing ESP then that would be great.  For those of you familiar with Windows that is what is done using the BCDboot program which like BCDedit can be run from WinPE or a running instance of Windows (including the Windows installation program).  Is it possible that the Ubuntu installation program can do this?  If NOT, another possibility would be that the Ubuntu installation program can be restricted to installing into a single operational partition (like it can on a BIOS/MBR computer) and then the ESP can be subsequently edited to create a Windows Boot Loader entry that refers to the Ubuntu system.  In that, sort of like what was called chain loading in BIOS/MBR terminology.

---

### Post by oldfred on 2019-03-17
Do not know Windows issues. Best to ask about those on a Windows forum, although many do dual boot.

Ubuntu uses efibootmgr to manage UEFI boot entries. Grub uses that to install its entry, but you can recreate a Widows boot entry, delete old entries and make other changes. But some brands do not like anything else editing UEFI entries & seem to revert, possibly Windows redoing its version? 
Often UEFI updates have resolved many issues.
See
man efibootmgr

Do not confuse Ubuntu's /boot partition which must be Linux format with an ESP which is FAT32 formatted.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

You can backup & restore the ESP as it just is a partition, not an MBR like the old BIOS/MBR configuration. And ESP is somewhat like having multiple MBR as you can have multiple boot files in ESP. But ESP is more equivalent to the MBR as it is where boot starts, not Windows Boot partition nor Ubuntu's /boot partition with more boot files.

Lots more info on UEFI booting & configuration and many useful links in link in my signature below.

---

### Post by yancek on 2019-03-17
With the advent of UEFI, a separate partition formatted vfat is required to host EFI files for the different operating systems on the drive/computer.  It has EFI boot files but the operating system, be it windows or Ubuntu, will have other boot files necessary to boot on the system partition.  You can also have a separate boot partition, this is in addition to the EFI and system partitions.  Separate boot partitions are usually not needed.  I don't believe microsoft had anything to do with naming the partition EFI as they had little participation in the entire creation of UEFI, more the hardware manufacturer responsibility - Intel, AMD and computer manufacturers.

bcdedit has been the boot manager for windows since the release of vista.  Major changes have been made to it in order to use UEFI.

So as indicated above, comparable software is the Linux efibootmgr but you still need Grub or another bootloader.  Grub can boot another OS (including windows) installed UEFI by chainloading it.  According to the neosmart site at the link below, microsoft has written their software for UEFI in such a way that it will not boot a windows install earlier than vista or a non-windows install.

[https://neosmart.net/wiki/easybcd/uefi/](https://neosmart.net/wiki/easybcd/uefi/)

---

### Post by aajax on 2019-03-20
I found [this article]("https://help.ubuntu.com/community/UEFI") which I think is very helpful.  However, I wouldn't say it answers my questions.  Looks like I just have to try it and see what I get.

Based on following some of the references herein, I now have the idea that efibootmgr is quite different than bdcedit and for that matter anything that Windows has to offer.  It looks to me like efibootmgr is actually being used to alter the firmware/nvram whereas bcdedit alters data stored in the EFI System Partition.  I was able to use SysRescCD to run efibootmgr on my computer which at present has NO linux software installed.  It appears to list all of the things I can find by selecting F2 during power on and entering what I'd call the UEFI editor.  Those entries include USB drives, the DVD drive, network adapters, and then there is one entry labeled "Windows Boot Manager" (WBM).  WBM is associated with the EFI System Partition.  I only know of 2 ways, at present, to inspect the EFI System Partition.  The only one that seems useful is to use BCDedit.  The other is to assign a drive letter (i.e., mount) the volume and then I can browse the file system and inspect files using some kind of hex editor but that isn't telling me much of anything.  This begs the question is there a Linux method to inspect the EFI System Partition in a manner similar to BCDedit?

What I'd sort of like to know is what will change in the EFI System Partition if I should follow the procedure outlined in the above referenced article to install Ubuntu.

---

### Post by Dennis N on 2019-03-20
>  What I'd sort of like to know is what will change in the EFI System Partition if I should follow the procedure outlined in the above referenced article to install Ubuntu. 
Ubuntu puts it's bootloader files in a separate folder on the EFI system partition, so it is isolated from any other boot files that might be there. Besides the added folder, nothing will be changed.

---

### Post by oldfred on 2019-03-20
Windows BCD uses a Windows registry type structure that you cannot normally read from Linux.
       [http://unix.stackexchange.com/questions/17433/windows-boot-configuration-data-bcd-viewer-for-linux](http://unix.stackexchange.com/questions/17433/windows-boot-configuration-data-bcd-viewer-for-linux)

       
 UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated 

But other than what Windows does to UEFI, Ubuntu is separate and will boot separately from UEFI & ESP - efi system partition. Only some UEFI do not fully follow UEFI standards and then create issues. 

Arch often has good explanations, many apply to all Linux.
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

---

