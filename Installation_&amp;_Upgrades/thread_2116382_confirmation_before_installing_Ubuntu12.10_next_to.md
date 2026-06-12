---
title: "confirmation before installing Ubuntu12.10 next to preinstalled Windows8 on UEFI"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by ATEGEV on 2013-02-15
[COLOR=#000000][FONT=Arial]Last few days I spend my time with reading all sorts of posts  of what could go wrong when trying to install Ubuntu 12.10 next to Windows 8.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]They’re all about the same problem, but when this much information is to be gathered, certainly for someone like me,  who comes with a software engineering background, not system engineering,  it’s difficult to keep the overview.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I [/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][COLOR=#000000][FONT=Arial]like to have a clear view about the path I need te follow, before starting[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Arial]. Ilike to avoid to mess up the system.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
I want to install Ubuntu on my brand new Dell XPS12 (i7, 8GB RAM, 256 GB SSD), but because I sometimes need to check if the software I developed works in Windows too, I want to keep the existing installation.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
So this is what I think I have to do to install Ubuntu 12.10 alongside the by Dell preinstalled Windows 8, after reading lot of different sources. Please confirm and correct where necessary.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Then I will try it, and if I succeed, I’ll create a sort of walkthrough and  the post it on this forum, and put it on a blog of mine (mostly about  Java development) that is under construction.
[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I would like to have dual boot with UEFI, because this is the more advanced booting style.[/FONT][/COLOR]


[LIST=1]
[*][COLOR=#000000][FONT=Arial]download Ubuntu 12.10 64bit version and burn a USB stick with it (this pc has no CD nor RJ45)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Open Windows Disk Management
This is a snapshot of the partitions like I bought it from Dell
[/FONT][/COLOR][IMG]https://lh3.googleusercontent.com/MH8qCq9zMGEFjwkMmdH0LIGIy4NOvicWabst1SHJtASlTGzUqosyetGeieJX8ghxy1ibazcCDhnuUMYNbFxthCPTd8T7FjF3rAftRb0YqzhJ2pXTtfQg5_zXuA[/IMG]
[*][COLOR=#000000][FONT=Arial]Shrink the C: partition to 96 GB (tis frees about 130 GB, most will be done in Ubuntu)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Save and restart WIndows to see if everything goes as before.[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Run Ubuntu booting from disk. Check if the free space is available.[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Is it correct that I don’t have to disable SecureBoot because I’m installing Ubuntu12.10 64bit?[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Reboot with USB device connected. I don’t know if I can create the needed partitions for Ubuntu with the Ubuntu installer or if I have to choose Try Ubuntu and create the partitions with GPT fdisk. Please confirm?[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]This one I doubt also: is it correct that I don’t have to create another EFI partition, and that I can share the one that is already installed for Windows also for Ubuntu?[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]These are the partitions I think that needs to be created:[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]a swap partition of 10 GB (I have 8 GB RAM, and disk is SSD)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]a root (/) partition for the rest available space[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]do you advise to have a /home partition? If yes how large?[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]are there other partitions that I forget but that needs to be created?[/FONT][/COLOR]
[/LIST]
 
[*][COLOR=#000000][FONT=Arial]The EFI partition will be set automatically to boot/efi[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Then continue installation and I think that’s it.[/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial]Please excuse me if I ask things that are trivial, I have no system engineering background and I haven’t had a lot the chance yet to work with Linux. But I am convinced of the power of open source.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]T[/FONT][/COLOR][COLOR=#000000][FONT=Arial]hank you very much with your help.[/FONT][/COLOR]

---

### Post by oldfred on 2013-02-15
Basically ok. A few suggestions. 
You need to turn fast boot off and to install with most system you do need to turn secure boot off. Ubuntu is using the Windows key but most systems still have some issues. Those that do work are then able to boot both systems with secure boot on or off.

I would suggest you do full backups of efi partition and your main Windows install.

You can only have one efi partition and per UEFI specs it is supposed to be used by all systems. But Windows and some vendors have violated specs or just not implemented them correctly. Some systems just work, some have issues and some do not seem to work at all.

I normally create partitions in advance with gparted, but you still have to use Something Else or manual partitioning to choose which partition is which and what format. The installer may work a bit faster is swap already exists as it will use that also if found. Now you can create partitions during the install so it does not really matter much. I normally suggest / (root) be only 25GB with either /home and/or data partitions for all you files.

I would strongly suggest another NTFS shared data partition for any data you want in both systems. Windows does not like too much activity in its system partition, and the Linux NTFS driver exposes all the normally hidden files & folders which can lead to accidents. Best to set Windows system as read-only from Ubuntu.

Be sure to boot flash drive in UEFI mode not BIOS/legacy/CSM mode. Then Ubuntu will install in UEFI mode. Otherwise it installs in BIOS mode. Some with nVidia or other video systems need nomodeset boot option and some system also need other options if you have issues booting live Flash or after install.

You will need Boot-Repair. Grub has a bug and does not create correct chain load entries to boot Windows.

       > As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

     Some Brands like Samsumg and maybe Toshiba have issues. These users have installed in Dell.
       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by ATEGEV on 2013-03-13
Hi, it took a while since I posted my original request (other priorities at work and also vacation ...), but I'm finaly ready to install Ubuntu in dual boot.

Fred, thanks for your advice, especially about the partitioning.

I first had no intention to create a shared NTFS partition (and use cloud drives or external hard drives to store shared data), but I am reconsidering this now.

If I want to create a shared NTFS partition, must I create it with Windows Disk Managment or with Ubuntu?

---

### Post by oldfred on 2013-03-13
Normally we do not suggest using Windows to create partitions. With MBR(msdos) if you have the 4 primary partition limit it converts to dynamic partitioning which is somewhat like LVM in Linux. But dynamic is not compatible with Linux and may even cause issues with Windows.
Not sure now with gpt partitions if Windows would still try to create dynamic or not. With gpt the new limit on partitions is 128 and that is just the default. It can be changed to even be more if desired.

Or I still suggest using gparted to create the NTFS partition. Windows should read that just fine.

---

### Post by dmk_kirkland on 2013-03-13
Not sure about UEFI, but with the BIOS systems you had to uninstall Dell's Datasafe utility. Apparently it overwrote data in GRUB everytime you boot into Windows. I'm not sure what Dell does in the case of UEFI, but keep that in mind.

Usual repair was:
1 - boot windows, uninstall Dell Datasafe
2 - reboot and repair GRUB.

Cheers,
Dave

---

