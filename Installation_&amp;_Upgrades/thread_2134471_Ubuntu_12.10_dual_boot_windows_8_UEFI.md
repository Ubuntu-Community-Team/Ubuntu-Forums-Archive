---
title: "Ubuntu 12.10 dual boot windows 8 UEFI"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by mauricio288 on 2013-04-11
[COLOR=#444444][FONT=Trebuchet MS]Hello comunity, I need your help with my laptop.[/FONT][/COLOR]

[COLOR=#444444][FONT=Trebuchet MS]I'm a ubuntu user, and want to have a dual-boot instalation of Windows 8 and Ubuntu.[/FONT][/COLOR]

[COLOR=#444444][FONT=Trebuchet MS]When I install ubuntu on my Acer aspire v5-571p everything was all rigth until I wanted to enter Windows 8 again, Windows send an error about a not found file, wich is necesesary for the Windows 8 UEFI to boot.[/FONT][/COLOR]

[COLOR=#444444][FONT=Trebuchet MS]I was able to enter Ubuntu, but my Windows partition was useless, so I tried to restore to default settings, but I was unnable to do it, the Alt + F10 command was not working and because of that I had to send my laptop to Acer for a full restoration.[/FONT][/COLOR]

[COLOR=#444444][FONT=Trebuchet MS]Now that I have my laptop again, I need a step by step guide to install Ubuntu along side Windows 8 in the UEFI mode; without having a mayor risk, also, I think that Acer is not ready to work with windows 8, this is because if I try the Alt + F10 command it simply won't work.[/FONT][/COLOR]

[COLOR=#444444][FONT=Trebuchet MS]I hope that you can help me in this problem, beacuse, really I don't feel confortable using Windows 8. (I have it only for educational reasons)[/FONT][/COLOR]

---

### Post by oldfred on 2013-04-12
Often the fast boot or secure boot may prevent keys from working or you have to be extremely quick with correct key as fast boot is to by-pass UEFI and go directly to Windows to speed up booting. 
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

If you turn those off, does key then work and can you still boot Windows. Some systems will only boot Windows with secure boot on.

Backup efi partition and your Windows partition.


 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Best to backup efi partition and Windows partition first.
Only use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 


 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Others with Acer:
 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

