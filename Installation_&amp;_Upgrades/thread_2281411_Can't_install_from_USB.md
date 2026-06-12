---
title: "Can't install from USB"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by laura17 on 2015-06-06
Hello everyone, 
I have been trying to install the latest edition of Linux Mint alongside Windows 7 on my older computer via torrent, [[http://www.linuxmint.com/edition.php?id=172](http://www.linuxmint.com/edition.php?id=172)]....but couldn't even get to live mode. keep getting stuck on the same thing every time! 

```
Code: Select all
random nonblocking pool is initialized
```

Any idea why this keeps happening? I have had Mint before on this computer, and it installed just fine. 

_Specs:_ 

OS Name    Microsoft Windows 7 Home Premium
Version    6.1.7601 Service Pack 1 Build 7601
Other OS Description     Not Available
OS Manufacturer    Microsoft Corporation
System Name    LAURA-PC

System Manufacturer    Gateway
System Model    GT5694
System Type    x64-based PC
Processor    AMD Phenom(tm) 9100e Quad-Core Processor, 1800 Mhz, 4 Core(s), 4 Logical Processor(s)
BIOS Version/Date    American Megatrends Inc. 7B3P081G, 5/5/2008
SMBIOS Version    2.5
Windows Directory    C:\Windows
System Directory    C:\Windows\system32
Boot Device    \Device\HarddiskVolume1
Locale    United States
Hardware Abstraction Layer    Version = "6.1.7601.17514"
User Name    Laura-PC\Laura
Time Zone    Eastern Daylight Time
Installed Physical Memory (RAM)    8.00 GB
Total Physical Memory    7.75 GB
Available Physical Memory    5.47 GB
Total Virtual Memory    15.5 GB
Available Virtual Memory    12.9 GB
Page File Space    7.75 GB
Page File    C:\pagefile.sys

_Display:_
Name    AMD Radeon HD 5570
PNP Device ID    PCI\VEN_1002&DEV_68D9&SUBSYS_20091787&REV_00\4&25574E2E&0&0010
Adapter Type    AMD Radeon Graphics Processor (0x68D9), Advanced Micro Devices, Inc. compatible
Adapter Description    AMD Radeon HD 5570
Adapter RAM    1.00 GB (1,073,741,824 bytes)
Installed Drivers    aticfx64.dll,aticfx64.dll,aticfx64.dll,aticfx32,aticfx32,aticfx32,atiumd64.dll,atidxx64.dll,atidxx64.dll,atiumdag,atidxx32,atidxx32,atiumdva,atiumd6a.cap,atitmm64.dll
Driver Version    14.501.1003.0
INF File    oem46.inf (ati2mtag_Evergreen section)
Color Planes    Not Available
Color Table Entries    4294967296
Resolution    1920 x 1080 x 60 hertz
Bits/Pixel    32
Memory Address    0xD0000000-0xDFFFFFFF
Memory Address    0xFE8E0000-0xFE8FFFFF
I/O Port    0x0000C000-0x0000CFFF
IRQ Channel    IRQ 4294967293
I/O Port    0x000003B0-0x000003BB
I/O Port    0x000003C0-0x000003DF
Memory Address    0xA0000-0xBFFFF
Driver    c:\windows\system32\drivers\atikmpag.sys (8.14.1.6413, 575.50 KB (589,312 bytes), 11/20/2014 9:08 PM)

---

### Post by egeezer on 2015-06-06
After you downloaded the iso file from torrent, how did you write the iso to your USB drive?

---

### Post by laura17 on 2015-06-09
> **egeezer said:**
> After you downloaded the iso file from torrent, how did you write the iso to your USB drive?
1. Downloaded Rufus 

2. Inserted USB drive, chose File Format  FAT32, where it says FreeDOS, clicked the drop down arrow and chose the  Linux Mint ISO file, then start.

---

### Post by shantiq on 2015-06-10
always found using unetbootin   which is in repo    ```
sudo apt-get install unetbootin
```
and then creating a live USB [takes under 10 mn] is a failsafe way here   ...   maybe try that?

---

### Post by sudodus on 2015-06-10
I have read good reports about Rufus.

Unetbootin works well in Ubuntu, when installed via  the developer's ppa. The version in the Ubuntu repositories is not up to  date in order to install from the versions 12.04 LTS and 14.04 LTS to  15.04. 
[URL="https://launchpad.net/%7Egezakovacs/+archive/ubuntu/ppa"]
https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa[/URL] 

```
sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get install unetbootin
```

See more details in [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

