---
title: "installing ubuntu on machine with duel monitors"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by gnixon70 on 2006-07-28
I need some help.  I'm currently ghosting up my machine for backup purposes.  my intention is to replace this machine with an ubuntu os.  I've tested it on the live cd and everything seemed to work wonderfully except for one vital thing(at least for me).  I have an agp graphics card that has an s-video out which i have hooked to the tv in my bedroom that is hooked up to an rf modulator(okay its an old tv).  What my intention is, is to extend my desktop to that tv so I can watch tv shows that i've downloaded(its much better then watching comericials in real time.) I'm able to do this with windows with not a problem...however, when i booted the live ubuntu cd, the tv part got all wacked out with lines and distortion when it reached the ubuntu part of the boot process and would not correct after the live cd was loaded.  my hardware profile is as follows:

OS Name	Microsoft Windows XP Professional
Version	5.1.2600 Service Pack 2 Build 2600
OS Manufacturer	Microsoft Corporation

System Manufacturer	VIA Technologies, Inc.
System Model	KM266A-8237
System Type	X86-based PC
Processor	x86 Family 6 Model 8 Stepping 1 AuthenticAMD ~1394 Mhz
BIOS Version/Date	Phoenix Technologies, LTD 6.00 PG, 12/22/2005
SMBIOS Version	2.2
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"
User Name	
Time Zone	Central Daylight Time
Total Physical Memory	640.00 MB
Available Physical Memory	376.07 MB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Page File Space	1.48 GB
Page File	C:\pagefile.sys


Name	Celestica Gold Edition RADEON 7000
PNP Device ID	PCI\VEN_1002&DEV_5159&SUBSYS_000F18D4&REV_00\4&1FEB96E4&0&0008
Adapter Type	RADEON 7000 Series AGP (0x5159), ATI Technologies Inc. compatible
Adapter Description	Celestica Gold Edition RADEON 7000
Adapter RAM	64.00 MB (67,108,864 bytes)
Installed Drivers	ati2dvag.dll
Driver Version	6.14.10.6601
INF File	oem10.inf (ati2mtag_RV100 section)
Color Planes	1
Color Table Entries	4294967296
Resolution	1024 x 768 x 60 hertz
Bits/Pixel	32
Memory Address	0xD8000000-0xDFFFFFFF
I/O Port	0x0000C000-0x0000CFFF
Memory Address	0xE0020000-0xE002FFFF
IRQ Channel	IRQ 16
I/O Port	0x000003B0-0x000003BB
I/O Port	0x000003C0-0x000003DF
Memory Address	0xA0000-0xBFFFF
Driver	c:\windows\system32\drivers\ati2mtag.sys (6.14.10.6601, 1.44 MB (1,505,792 bytes), 7/10/2006 3:41 PM)
	
Name	Winvnc video hook driver
PNP Device ID	ROOT\DISPLAY\0000
Adapter Type	RADEON 7000 Series AGP (0x5159), Winvnc Video hook driver compatible
Adapter Description	Winvnc video hook driver
Adapter RAM	64.00 MB (67,108,864 bytes)
Installed Drivers	ati2dvag.dll
Driver Version	1.00.17
INF File	oem11.inf (vncdrv section)
Color Planes	1
Color Table Entries	4294967296
Resolution	1024 x 768 x 60 hertz
Bits/Pixel	32
Driver	c:\windows\system32\drivers\vncdrv.sys (1.00.17, 4.63 KB (4,736 bytes), 7/19/2006 1:36 PM)

to cut through all of this my video card is a radeon 7000 series agp adapter.

If anyone has any thoughts on how to make this work i'd be most greatfull for the help

Thanks

Greg

---

### Post by orb9220 on 2006-07-28
Well the live dosn't do mutiple outputs like that. After I installed and then
installed the nvidia drivers for my card then config the xorg.conf file.

I now have a dual monitor setup for mine. The default setup is always for one
default monitor using default drivers like windows. You will have to install the ati drivers for your RADEON 7000 card and ask for help it getting yer s-video out.

The people are quite helpful and do a forum search on   RADEON 7000 and see how others did it.

Hope this helps.

---

