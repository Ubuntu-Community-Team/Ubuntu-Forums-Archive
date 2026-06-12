---
title: "Having troubles with install"
date: 2016-02-01
forum: Installation &amp; Upgrades
---

### Post by drbentow on 2016-02-01
So trying to go back to Linux on my custom PC due to windows 10 being stupid. I use to have it on it back when I had a different mobo and graphics card. Now when I go try and install it I'm getting these lines of code first 


[  0.036021] [Firmware Bug]: AMD-Vi: IOAPIC[0] not in IVRS table


[  0.036071] [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found


[  0.036119] AMD-Vi: Disabling interrupt remapping.


so after them three lines come up for like 5sec its clears then a whole bunch on lines scroll up then goes completely black then my monitor says no single found even though my computer is still on.


Any advice or help please

---

### Post by grahammechanical on 2016-02-01
When precisely are you seeing those messages? When trying to run the Ubuntu live session? During the installation of Ubuntu? After installation during the loading of Ubuntu?

I am not clear at what point and in what process those messages are appearing. A quick web search informs me that they reference AMD hardware virtualization. Are you trying to install Ubuntu in a VM? You could try going into the BIOS/UEFI and disabling it

[URL="http://www.amd.com/en-us/solutions/servers/virtualization"]http://www.amd.com/en-us/solutions/servers/virtualization

[/URL]

---

### Post by oldfred on 2016-02-02
What motherboard & graphics card?
You may need motherboard boot parameters and video card boot parameters.

Are you booting in UEFI or BIOS boot mode. New motherboards have both.
 
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by kansasnoob on 2016-02-02
What version of Ubuntu are you trying to install?

---

### Post by mushistereck on 2016-06-02
I have a similar problem

8.836583] [Firmware Bug] : AMD-V1:IOAPIC[0] not in IVRS table
8.836583] [Firmware Bug] : AMD-V1: no southbridge IOAPIC found
8.836614] AMD-V1:grin:isabling interrupt remapping

When I boot from the DVD I get the purple screen then the above message,  then a black screen and nothing happens. I need to load 16.04 with Win 7  as dual boot. Win is already installed.



OS Name    Microsoft Windows 7 Home Premium
Version    6.1.7600 Build 7600
Other OS Description     Not Available
OS Manufacturer    Microsoft Corporation
System Name    RON-PC
System Manufacturer    MSI
System Model    MS-7721
System Type    x64-based PC
Processor    AMD A4-4000 APU with Radeon(tm) HD Graphics, 3000 Mhz, 2 Core(s), 2 Logical Processor(s)
BIOS Version/Date    American Megatrends Inc. V30.1, 6/12/2013
SMBIOS Version    2.8
Windows Directory    C:\Windows
System Directory    C:\Windows\system32
Boot Device    \Device\HarddiskVolume1
Locale    Australia
Hardware Abstraction Layer    Version = "6.1.7600.16385"
User Name    Ron-pc\Ron
Time Zone    E. Australia Standard Time
Installed Physical Memory (RAM)    16.0 GB
Total Physical Memory    15.2 GB
Available Physical Memory    13.2 GB
Total Virtual Memory    30.4 GB
Available Virtual Memory    28.2 GB
Page File Space    15.2 GB
Page File    C:\pagefile.sys

Name    AMD Radeon HD 7480D
PNP Device ID    PCI\VEN_1002&DEV_9993&SUBSYS_77211462&REV_00\3&267  A616A&0&08
Adapter Type    AMD Radeon HD 7480D (0x9993), Advanced Micro Devices, Inc. compatible
Adapter Description    AMD Radeon HD 7480D
Adapter RAM    768.00 MB (805,306,368 bytes)
Installed Drivers    aticfx64.dll,aticfx64.dll,aticfx64.dll,aticfx32,at   icfx32,aticfx32,atiumd64.dll,atidxx64.dll,atidxx64   .dll,atiumdag,atidxx32,atidxx32,atiumdva,atiumd6a.  cap,atitmm64.dll
Driver Version    13.250.0.0
INF File    oem1.inf (ati2mtag_Trinity_Desktop section)
Color Planes    Not Available
Color Table Entries    4294967296
Resolution    1440 x 900 x 60 hertz
Bits/Pixel    32
Memory Address    0xC0000000-0xFFFFFFFF
I/O Port    0x0000F000-0x0000F0FF
Memory Address    0xFEB00000-0xFEB3FFFF
IRQ Channel    IRQ 4294967294
I/O Port    0x000003B0-0x000003DF
I/O Port    0x000003C0-0x000003DF
Memory Address    0xA0000-0xBFFFF
Driver    c:\windows\system32\drivers\atikmpag.sys (8.14.1.6354, 609.50 KB (624,128 bytes), 17/11/2013 12:14 PM

---

