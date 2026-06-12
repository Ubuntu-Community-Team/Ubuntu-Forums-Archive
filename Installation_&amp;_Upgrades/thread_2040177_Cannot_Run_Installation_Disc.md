---
title: "Cannot Run Installation Disc"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by Soulplayer on 2012-08-10
I use Google a lot… sometimes all day long in my thirst for technical  knowledge. I rarely ever post questions unless I am absolutely stumped.

I am.

To the best of my knowledge, my entire system should be fully up-to-date  for this task. I just purchased this refurbished computer about a month  ago from Geeks.com, and my family knows this website to be a very  reliable online store for awesome deals on electronics. It looked to be  in "like new" condition.
 
My motherboard has an AMD APU (accelerated processing unit), which  combines central, integrated graphics video, and integrated sound audio  processors all onto the same motherboard.
 
The computer came with dual-channel RAM, 4 sticks of 2-GB Kingston, and  then I replaced 2 of the sticks with 4-GB CORSAIR RAM into a  corresponding channel (for a difference of an extra 4 GB of RAM) that I  purchased from Newegg.com.
 
I also just bought a new SSD from Amazon.com and installed it into an open drive bay.
 
Upon starting to use my OEM version of Windows 7 Home Premium (64-bit), I  am almost 100% positive that I had installed all of the latest driver  updates for all of my hardware, until I ran into some issues with  installing new operating systems, which I will explain. Keep in mind  that I do not value this OS, so I do not mind replacing it during the  process of re-formatting the HDD with different operating systems. I do  not wish to multi-boot 2 different versions of Windows 7.
 
My BIOS is fully up to date.
 
 
**CHAMPION-PC Desktop Computer Specs:**
 
Case, PSU, & Cooling Units
_ Acer Aspire mid-tower
_ Acer Aspire M3 ATX (300 W)
_ Acer Aspire heat sink & fan

Motherboard, CPU, iGPU/iVPU, & iSPU/iAPU
_ Acer Aspire M3470-UC30P
_ AMD Fusion A8-3800 (Quad-Core / Turbo Core) (APU) Llano, Socket FM1 (65 W) @ 2.4/2.7 GHz
_ AMD (ATI) Radeon HD 6500D
_ Realtek ALC892 7.1+2-channel HD audio codec w/ content protection

BIOS
_ American Megatrends Inc. P01-A4 [COLOR=#008000][UP-TO-DATE][/COLOR]

RAM
_ 2 x 4-GB CORSAIR Vengeance DIMM @ 1,600 MHz, DDR3 PC3-12800 SDRAM
_ 2 x 2-GB Kingston 1Rx8 DIMM @ 1,600 MHz, DDR3 PC3-12800 SDRAM

Internal Disk Drives
_ 256-GB SAMSUNG 830 MZ-7PC256D/AM SATA/SCSI III MLC SSD [COLOR=#ff0000][COLOR=#0000ff][IN SATA-0 PORT[/COLOR][/COLOR][COLOR=#ff0000][COLOR=#0000ff] [COLOR=Red]CURRENTLY SET TO 2ND DISK PRIORITY, COMPLETELY FORMATTED][/COLOR][/COLOR][/COLOR]
_ 1-TB Seagate ST31000524AS SATA/SCSI HDD [COLOR=#ff0000][COLOR=#0000ff][IN SATA-1 PORT; [COLOR=Red]CURRENTLY SET TO 1ST DISK PRIORITY WITH OEM DISTRO OF WINDOWS 7 HOME PREMIUM][/COLOR][/COLOR][/COLOR]

Internal Optical Disc Drive
_ Pioneer DVR-219RS CD-ROM / CD-RW / DVD-ROM / DVD±R / DVD±R DL (DVD±R9) / DVD±RW (SL)/DL player/burner [COLOR=#ff0000][COLOR=#0000ff][IN SATA-2 PORT][/COLOR][/COLOR]


    **Goal:**
 
I wish to upload a new OS onto my new SSD so that I can transfer all of  my data from my HDD onto the SSD, format the HDD, transfer all of my  data back onto the HDD permanently, and then to re-format my SSD and  custom install the following 3 operating systems in order, partitioning  volume sizes accordingly:
 
[COLOR=#0000ff][bootable CD/DVD][/COLOR] Canonical Ubuntu Linux 12.04 LTS (Precise Pangolin) (x86-64) [COLOR=#008000][40 GB space][/COLOR]
[COLOR=#0000ff][bootable CD/DVD][/COLOR] Microsoft Windows 7 Ultimate (x86-64), Service Pack 1 [COLOR=#008000][60 GB space][/COLOR]
[COLOR=#0000ff][bootable USB][/COLOR] Apple (Mac) OS X v10.8 "Mountain Lion" Hackintosh (x86-64) [COLOR=#008000][80 GB space][/COLOR]
 
NOTE: Before commenting on my mention of Hackintosh, realize that  Hackintosh has nothing to do with the issue. My issue involves the  installation of Ubuntu Linux.

**Problem:**
 
IN ONE SENTENCE: I can't boot multiple operating systems onto my computer, let alone even one of them.
 
Very confusing.
 
First of all, it's a given that I always correctly edit the Boot  Priority in my BIOS menu (Del key) and correctly change the Boot Order  (F12 key). However many times I double-check this, I can't seem to  understand why my BIOS Default Settings think that I should use the RAID  SATA mode, because the computer originally came with a single hard disk  drive, and I just recently installed the solid-state drive. I read that  RAID requires at least 2 drives, usually of the same amount of storage  space?
 
My CD/DVD optical drive and Windows 7 Home Premium will both fail to  boot in the regular AHCI SATA mode and also the older IDE mode and  requests that I run Startup Repair, which fails to boot also (but this  doesn't matter). I have never set up a RAID array manually, and I can  only imagine that Windows has confused my BIOS into thinking that I am  using RAID (perhaps from faulty OEM (original equipment manufacturer)  installation?). Aside from the fact that my BIOS does not give me any  choice as to which type of RAID I can use, I assume that it maybe just  uses RAID-0? This concerns me, because if I understand RAID correctly,  then I cannot utilize my maximum capacity of data storage without an  even higher increase in data loss probability. Does this give any clue  toward a proper diagnosis?
 
I downloaded the Ubuntu Linux installation .iso disc image from the  Ubuntu website, trying both direct download and torrent download. I used  InfraRecorder to write the disc images onto a DVD (then I burned a  couple more just for tests in case of either faulty discs or faulty  images). wubi.exe starts up, but upon booting from CD/DVD drive, I see  the GRUB manager, which lists 3 options from the Linux installer. All of  them give me a black screen that ends the signal to my monitor and  forces me to hold down the power button. Installation fails, of course,  so after each attempt, I uninstall Ubuntu from my Program Files.

I should also note that after burning the DVD, wubi.exe gives me the message, "D:\wubi.exe is not a valid win32 application."  When I download wubi.exe directly from Ubuntu.com, I run it and  install, reboot my computer, and enter GNU GRUB, whereas I can choose  between either Windows 7 or Ubuntu, but Ubuntu does not load and faces  the same issue as that which I stated in the previous paragraph. I  proceed to re-format the SSD.

I don't know if it's a coincidence,  but I remember the same thing happening on my old computer, which also  has a Pioneer-brand CD/DVD optical drive, when I tried to install Ubuntu  Linux 10.04 LTS (Lucid Lynx) (32-bit).
 
I tried popping in my Windows 7 Ultimate installation disc, which I burned using Windows 7 USB/DVD Download Tool, and it  booted! The only problem there was that the installer prompted me that I  needed to install CD/DVD drive drivers to continue. It showed a menu  where driver updates would otherwise appear in a list for me to install,  but nothing appeared. So… are my drivers up to date??
 

**Solution:**
 
Please, if anyone knows an answer that does not involve a terminal  coding work-around or a temporary fix that could jeopardize the  functionality of the operating systems and therefore defeat the purpose  of even installing them altogether, then I would greatly appreciate all  of the help!
 
 
 
 
If you read through this entire post, then you're awesome. [IMG]http://www.pchelpforum.com/xf/styles/default/xenforo/clear.png[/IMG] Thank you in advance!!
 
 
Sincerely,
 
Soulplayer

:lolflag:

---

### Post by Soulplayer on 2012-08-10
Why can't my computer boot the Ubuntu Linux 12.04 AMD64 installer from DVD, which I burned using InfraRecorder?? Yes, I know how to use the BIOS. Does it have anything to do with my OEM distribution of Windows 7 not booting into AHCI mode, even after I made a fix < [http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976) > that should have taken care of that problem?? Please help. Thank you in advance.

If you want background on the issue, then here is the main thread: [http://ubuntuforums.org/showthread.php?p=12161588](http://ubuntuforums.org/showthread.php?p=12161588)


Sincerely,

Soulplayer

---

### Post by seshdroid on 2012-08-10
What happens while you boot your system? 

 Does it show a crimson screen with a list of stuff with Ubuntu 12.04 on the top and Windows at the bottom? 

 If yes then your dual boot worked fine

 else it failed and you might have to re-install just Ubuntu

It might sound silly but if you could use a USB stick to install, it might work faster.

If you have Ubuntu installed in another system then use the StartupDiskCreator (application) that comes pre-installed on it.. its easy. You'll get loads of video tutorials for it on YouTube.

---

### Post by Soulplayer on 2012-08-10
I don't get anything beyond GNU GRUB other than a blank screen and a lost signal to my monitor. I do not have a USB drive available for Ubuntu Linux. InfraRecorder should be just as good as StartupDiskCreator for this task, shouldn't it?

What concerns me more than any of this is the fact that my Windows installation disc tells me that I lack the necessary drivers for my CD/DVD optical drive, but when it shows me a menu, which would otherwise show a list of drivers to download, nothing appears.

---

### Post by oldos2er on 2012-08-10
Threads merged. Please don't start more than one thread for a given topic; it dilutes community effort. Thanks.

---

