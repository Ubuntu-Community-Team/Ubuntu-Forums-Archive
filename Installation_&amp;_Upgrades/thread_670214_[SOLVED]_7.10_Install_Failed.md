---
title: "[SOLVED] 7.10 Install Failed"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by galeg on 2008-01-17
Attempted twice to install 7.10 to secondary HD (E:) from CD download, but in each case installation froze at "Scanning Mirror". After 2nd failure totally creamed HD ready for another installation attempt tomorrow. Am also considering a wait for 8.04 unless somebody has a possible solution.

---

### Post by forestpixie on 2008-01-17
I had a similar problem installing for someone else - disconnected from the net once it reached that part. Install then carried on without any problems as such, you might though afterwards have a problem with your sources.list.

That is easily fixed and there are many, probably hundreds, of threads here dealing with that problem.

This should help with the sources.list once you need to deal with it - [http://ubuntuforums.org/showthread.php?t=659314](http://ubuntuforums.org/showthread.php?t=659314)

---

### Post by PmDematagoda on 2008-01-17
The apparent freeze that you face when the install is "Scanning the mirrors" is not a freeze at all, it would take some time(about 10-20 minutes at times) to finish that process. So if you had waited for some time then the installation would have finished successfully.

---

### Post by forestpixie on 2008-01-17
yea totally agree with you on that point and we both are aware, but someone just turned up wouldn't be - but if you ask me it's quicker to lett the sources get commented out and edit the file :)

I waited 25 mins - which is longer than the rest of the install process, and tbh I think it's just a little bit ridiculous that it works that way.

That said - it's better than installing windows, then getting the updates and restarting and getting some more and restarting and getting some more.....

Perhaps there should be a 'if you've got this far it's not frozen but busy' type of warning 

:D

---

### Post by galeg on 2008-01-17
Thanks all, I will go and wash the car while I wait.

---

### Post by forestpixie on 2008-01-17
check your sources.list once it's finished and rebooted - for justin case's sake 

cat /etc/apt/sources.list

if you've got nearly all lines starting with #  - you'll need to edit it

Good luck - see you on the other side

and if all goes swimmingly can you mark thread as solved

---

### Post by galeg on 2008-01-17
Thanks all for the replys.
From what I read it sounds like the install attempts to connect to the web at this point. If that is the case it will not connect because I do not appear to have been asked for a logon / Psw, and if I do not send to the ISP, the ISP server just ignores me, so I will need to rely on the installattion to have a timeout (in Australia the big ISPs will only respond to receiving an ID / Psw being received, they do not send a anything to you).
Can somebody please confirm
1. The installation is attempting to connect to the net at this point
2. What the installation timeout is approx if it does not receive a response
Thanks

---

### Post by Partyboi2 on 2008-01-18
This might work
[http://blogs.developerfusion.com/blogs/thushan/archive/2007/10/25/3398.aspx](http://blogs.developerfusion.com/blogs/thushan/archive/2007/10/25/3398.aspx)
Here is a bug report relating to the problem
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095)
When ever I have run into this problem when I am installing Gusty, I have left it and 20-30min later it has timed out and finished the install (with internet connection) Some people the time seems to be shorter and for others the time seems to be longer. Some have left it on over night or gone to work to return and find that it has completed the install.

---

### Post by galeg on 2008-01-18
Thanks all, again.

Will start install tonight, Friday, which gives me all of Saturday for a timeout, or all of Sunday to rebuild secondary HD.

---

### Post by galeg on 2008-01-18
Ubuntu has appeared to install correctly, passing the "Scanning the Mirror" message after about 30 minutes.

Next problem
When the system reboots, I do not receive any options to select Linux, the system just automatically goes straight to MS XP.
Carefully checked the install (actually did a complete reinstall to check) and answered "Yes" to Grub Boot Loader to Master Boot Record" question.
On booting the box there are 2 options displayed for a few seconds during the start of the boot:
F2 - Set Up (for BIOS)
F12 - Boot Menu
If I am quick enough and select F12, I receive the following message
"Digital Input"
"2: Cannot display this video mode"

Anybody have any suggestions where to from here.

Thanks

---

### Post by PmDematagoda on 2008-01-18
Post the complete specifications of your PC. Also, please post how our monitor is connected to the VGA card.

---

### Post by galeg on 2008-01-18
Morning
Information as requested

Monitor Connection
-----------------------
Digital onboard port via cable to digital monitor

System
-----------
OS Name	Microsoft Windows XP Home Edition
Version	5.1.2600 Service Pack 2 Build 2600
OS Manufacturer	Microsoft Corporation
System Name	D21ZXC1S
System Manufacturer	Dell Inc.
System Model	Dimension 4700
System Type	X86-based PC
Processor	x86 Family 15 Model 4 Stepping 1 GenuineIntel ~3192 Mhz
BIOS Version/Date	Dell Inc. A05, 23/11/2004
SMBIOS Version	2.3
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume4
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"
Total Physical Memory	2,048.00 MB
Available Physical Memory	1.42 GB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Page File Space	3.85 GB
Page File	C:\pagefile.sys

Video
---------
Name	RADEON X300 Series
PNP Device ID	PCI\VEN_1002&DEV_5B60&SUBSYS_03021002&REV_00\4&166AB6CD&0&0008
Adapter Type	RADEON X300 SE (0x5B60), ATI Technologies Inc. compatible
Adapter Description	RADEON X300 Series
Adapter RAM	128.00 MB (134,217,728 bytes)
Installed Drivers	ati2dvag.dll
Driver Version	6.14.10.6476
INF File	oem0.inf (ati2mtag_RV370 section)
Color Planes	1
Color Table Entries	4294967296
Resolution	1280 x 1024 x 60 hertz
Bits/Pixel	32
Memory Address	0xD0000000-0xD7FFFFFF
I/O Port	0x0000DC00-0x0000DCFF
Memory Address	0xDFDE0000-0xDFDEFFFF
IRQ Channel	IRQ 16
I/O Port	0x000003B0-0x000003BB
I/O Port	0x000003C0-0x000003DF
Memory Address	0xA0000-0xBFFFF
Driver	c:\windows\system32\drivers\ati2mtag.sys (6.14.10.6476, 769.00 KB (787,456 bytes), 1/01/1980 2:00 AM)

Hope the above assists

---

### Post by galeg on 2008-01-19
Problem solved, and ubuntu now operational.
To resolve the problem, I went back to basics and started with the hardware.
During the analysis, the following was noted and fixed.
1. Secondary drive was identified and accessed by XP
2. Secondary drive was identified and allowed ubuntu to install to it
3. Secondary drive was not recognised by BIOS
4. Secondary drive was switched to be slave, NOT cable select 
5. Secondary drive set as cable select
6. Reinstalled ubuntu
7. F12 - Boot Menu allowed access, and although ubuntu is not mentioned (listed as Boot to Secondary Drive) this allowed ubuntu to successfully boot.

Thanks to all the assistance and interest from the forum members.

Grant

---

