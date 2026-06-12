---
title: "Asus netbook dual boot"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by lalitha niharika on 2013-08-13
[COLOR=#333333][FONT=Verdana][FONT=Lucida Grande]I bought a new Asus netbook with preloaded MS DOS. I prepared a linux bootable usb drive and installed it. During installation, I made 3 partition - 1.ext4 with linux, 2.swap, 3.free space for windows. After finishing that, my system got stuck at settings. When I on the system, only settings open and nothing else happens. When I insert windows bootable usb, its not loading and asks to connect proper bootable drive. After googling, I could understand that I have deleted EFI system unknowingly while partitioning. When i click on launch EFI shell, it says file not found. I dont know what exactly EFI is. Could it be the reason for which, I am unable to boot windows and open linux? Please help me to rectify problems and dual boot my system and to make screen to choose between linux, windows appear. As I cannot understand complicated things, please explain me in simple terms...[/FONT]
[/FONT][/COLOR]
[Lalitha niharika]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=79037")Level 1
[IMG]http://forums.linuxmint.com/images/ranks/1.gif[/IMG] [COLOR=#000000]Posts:[/COLOR] 12[COLOR=#000000]Joined:[/COLOR] Sat Feb 18, 2012 11:55 pm
[LIST]
[*]
[*]
[/LIST]
[RIGHT][COLOR=#333333][FONT=Verdana][/FONT][/COLOR][/RIGHT]

---

### Post by varunendra on 2013-08-13
> **lalitha niharika said:**
> When i click on launch EFI shell, it says file not found. I dont know what exactly EFI is. Could it be the reason for which, I am unable to boot windows and open linux?

Since the netbook came with MS DOS, EFI must have been turned off by default. It means even though your netbook supports UEFI, it was originally disabled in the "settings".

It sounds like the EFI has been turned on somehow after installation.

Since you are able to access netbook "settings", try to locate the EFI settings in it and try disabling it (disable or set it to "Legacy" mode). See if that helps booting the installed Ubuntu or the live USB.

If possible, boot another system from the same USB drive to make sure that the live USB is actually bootable and not corrupt itself.

Once you are able to boot an OS, live or installed, we can troubleshoot other issues if required.

**PS:**
Leaving an empty partition for windows means you are intending to install Windows 'AFTER' installing Ubuntu. Not a good Idea. Doing so will overwrite Grub (the Linux boot program) and you will need to repair it later in order to be able to boot both windows and Ubuntu.

It is recommended to install Windows first, Ubuntu later. That way, the dual booting will be taken care of automatically.

---

