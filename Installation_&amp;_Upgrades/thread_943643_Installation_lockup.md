---
title: "Installation lockup"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by bbowdry on 2008-10-10
I've been having a lot of trouble reinstalling Ubuntu 8.04.1. I have tried many live CDs with it on them with no avail. With these I usually can get the screen with the Ubuntu logo. Following that my Shuttle desktop computer stops responding.

As I was writing this document I tried a Linux Identity Starter “ubuntu family 8.0.4” disk with Live CD Versions of Ubutu, kubuntu, Xubuntu, and Mythubuntu on my Acer Travelmate 4670. All of these came up in the live CD mode. I did not install any of these at this time. None of them worked on my Shuttle.

I also tried using the LXFDVD107, July 2008, Ubuntu 8.0.4. The Live CD mode came up as expected.
I also tried using the LXFDVD100, Dec 2007, Ubuntu 7.10. The Live CD mode came up as expected. 
When using the LXFDVD100 to install Ubuntu 7.10 on my Shuttle Desktop system I ended up with a screen showing (initramfs) [6..778585] ata3.00: failed to set xfermode (err_mask=0x40)
Further down on the screen was the text that this is not an 8139c+ compatible chip. Try the "8139too"*driver instead. How do I find this driver and how do I install it.
I went into windows and disabled the network card that had the 8139c driver. It had a Realtek Driver Version 5.687.0225.2008. Did this prevent the driver from loading?
When again trying to reinstall Ubuntu 8.04 I got slightly different error messages: (initramfs) [108.638919] ata3.00: revalidation failed (errno=-5)
I tried again after removing the hardware device. Still no luck. Error message was : (initramfs) [115 1523233] ata3.00: revalidation failed (errno=-5).
I had previously used this same disk to install this Distro on this machine! What do I do now?

My system information below:
Acer Travelmate 4670 (All of the Ubuntu Live 
Intel processor ..........................T2300 @ 1.66GHZ
Memory.....................................1026320 kB
OS Name...................................Microsoft Windows XP Professional
Version.......................................5.1.2600 Service Pack 3 Build 2600
OS Manufacturer........................Microsoft Corporation
System Mfg................................Acer, inc.
System Model	............................TravelMate 4670
System Type...............................X86-based PC
Processor.....................................x86 Family 6 Model 14 Stepping 8 GenuineIntel ~1666 Mhz
BIOS Version/Date.....................Acer v1.3221, 2/24/2006
SMBIOS Version........................2.4
Boot Device................................\Device\HarddiskVolume2
Locale..........................................United States
Total Physical Memory...............1,024.00 MB
Available Physical Memory........447.85 MB
Total Virtual Memory.................2.00 GB
Available Virtual Memory..........1.96 GB
Page File Space..........................2.38 GB
 
Shuttle Desktop
OS Name....................................Microsoft Windows XP Home Edition
Version........................................5.1.2600 Service Pack 3 Build 2600
OS Manufacturer........................Microsoft Corporation
System Manufacturer.................Shuttle Inc
System Model............................SB65
System Type..............................X86-based PC
Processor....................................x86 Family 15 Model 2 Stepping 9 GenuineIntel ~2806 Mhz
BIOS Version/Date....................Phoenix Technologies, LTD 6.00 PG, 8/23/2004
SMBIOS Version.......................2.2
Windows Directory....................C:\WINDOWS
System Directory.......................C:\WINDOWS\system32
Boot Device...............................\Device\HarddiskVolume1
Hardware Abstraction Layer......Version = "5.1.2600.5512 (xpsp.080413-2111)"
Total Physical Memory..............1,024.00 MB
Available Physical Memory.......1.38 GB
Total Virtual Memory.................2.00 GB
Available Virtual Memory..........1.96 GB
Page File Space..........................3.85 GB
Page File.....................................C:\pagefile.sys

[email]bbowdry@carowill.com[/email]

---

