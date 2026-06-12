---
title: "Dual booting Ubuntu and Windows 10."
date: 2015-08-18
forum: Installation &amp; Upgrades
---

### Post by mjalberts13 on 2015-08-18
Hello

I have a laptop running Windows 10. I have a 256GB SSD and a 1TB HDD.
I know that the Ubuntu setup might have the option to install alongside Windows, but I tried running a Linux Mint install earlier this week and that did not give me the option.

Could someone please verify if the following process will work:

I already have my windows on the SDD so I will create 3 more partitions:
[LIST]
[*]mount point: / - ext4 file system,
[*]mount point: /home - ext4 file system and for
[*]swap
[*]I select for GRUB to be installed on the 256GB SSD
[/LIST]

Now some posts that I have read talked about linking or something akin. Is that only applicable when I want Ubuntu to have access to the HDD?
In my case I do not want Ubuntu to have access to the HDD, only the partitions that I allocated for it on the SSD.
Will Windows still have access to the HDD after the Ubuntu setup?

Kind Regards

---

### Post by grahammechanical on 2015-08-18
Windows cannot read Linux file systems. But Linux can read Windows file systems. So, Ubuntu will still be able to access that hard drive even if it is an NTFS formatted file system. Some of us who use both Windows and Linux have NTFS partitions so that data can be shared between the 2 OS.

Was this laptop purchased with Windows 10 pre-installed? Does it have BIOS or UEFI? Msdos partition table or GPT? Certain answers will explain why you do not get the install alongside option. I do not support Linux Mint. So, I go no further.

---

### Post by oldfred on 2015-08-18
Moved to Mint sub-forum.

Whether system is BIOS or UEFI you must make sure Windows fast startup is off. That is always on hibernation. The Linux NTFS driver does not mount NTFS partitions that are hibernated or need chkdsk. Best to also use Windows to shrink the Windows NTFS partition and immediately reboot so it can run chkdsk which it needs after any resize.

If system is BIOS with MBR partitions you have the 4 primary partition limit. And you cannot let Windows create partitions as it may convert to dynamic partitions.

If UEFI with gpt partitions, you need to install Ubuntu in UEFI mode also.

---

### Post by mjalberts13 on 2015-08-18
> **grahammechanical said:**
> Windows cannot read Linux file systems. But Linux can read Windows file systems. So, Ubuntu will still be able to access that hard drive even if it is an NTFS formatted file system. Some of us who use both Windows and Linux have NTFS partitions so that data can be shared between the 2 OS.

Was this laptop purchased with Windows 10 pre-installed? Does it have BIOS or UEFI? Msdos partition table or GPT? Certain answers will explain why you do not get the install alongside option. I do not support Linux Mint. So, I go no further.

I am installing Ubuntu 15.04, not Linux Mint. I was just mentioning that Mint, when I wanted to install it earlier this week, did not have the "Install alongside windows" option in the setup and that that might mean Ubuntu won't have it either.

Windows 8.1 was pre-installed, but I did a clean install of Windows 10 (I formatted both the SSD and HDD and installed windows on the SSD). 

I checked using the method here to see if my laptop uses BIOS or UEFI: [http://www.thewindowsclub.com/check-if-uefi-or-bios](http://www.thewindowsclub.com/check-if-uefi-or-bios)
My laptop uses "EFI". Is that just short for UEFI or something entirely different?

If I go into [COLOR=#070F14][FONT=Verdana]Control Panel/Administrative Tools/Computer Management/Disk Management under "File System", both the SSD and HDD are NTFS. 
[s]How do I check for [/FONT][/COLOR]Msdos partition table or GPT?[/s] nevermind, I just figured it out. Both are GPT.

---

### Post by oldfred on 2015-08-18
OK, moved back to Installation sub-forum.

UEFI is the hardware, efi was the old name as it now is almost 15 years old. But only started major use when Mac changed to Intel chips. And that was the older version of UEFI.
Your ESP partition is the efi system partition on a gpt partitioned drive. All boot files for every installed system are in that partition.
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Use Windows tools to shrink the NTFS partition to make unallocated space for Ubuntu. Reboot Windows immediately so it can run chkdsk and repair to its new size. Make sure hibernation/fast start up is off.
The Linux NTFS driver does not mount NTFS partitions needing chkdsk or hibernated to prevent damage that a chkdsk could not then fix.

Make sure you have good backups of Windows & efi partition.
Much more info in link in my signature below.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by mjalberts13 on 2015-08-18
Thanks! I got it installed and installed the GNOME desktop-environment. Ubuntu is buggy now and sometimes will not start.

Can I do a fresh install by just formatting the Ubuntu and Swap partition and installing in those partitions again?

Will grub get overwritten correctly?

---

### Post by oldfred on 2015-08-18
Only use Something Else, not any auto install option, even if it says it is just overwriting current install.
Major bug erases entire drive, fixed in very newest versions, but I do not trust that yet.
 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions. Perhaps in 15.04.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by mjalberts13 on 2015-08-19
Thanks!

---

