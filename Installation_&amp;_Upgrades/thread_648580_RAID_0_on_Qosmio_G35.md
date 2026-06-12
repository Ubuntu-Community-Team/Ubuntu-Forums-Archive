---
title: "RAID 0 on Qosmio G35"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by Portending Ennui on 2007-12-23
Hello all,

I am wondering how to use RAID 0 to dual-boot XP-pro and Ubuntu with v7.10 Gutsy.  I could do this with an older build in Sept. of '06m and upon trying again I cannot.

First off, some system information, with relevant bits bold...

```

Toshiba Qosmio G35-AV600.

Mainboard :	TOSHIBA Portable PC
Chipset :	Intel i945PM
Processor :	Intel Core Duo T2400 @ 1833 MHz
Physical Memory :	1024 MB (2 x 512 DDR2-SDRAM )
Video Card :	Nvidia Corp Quadro NVS 110M / **GeForce Go 7300**
**Hard Disk :	TOSHIBA (159 GB)**
[B]Disk Controller :	Intel Corporation 82801G (ICH7 Family) Ultra ATA Storage Controller 

             Disk Type :	Hard Disk 
             Peripheral Type :	SCSI 
             Manufacturer :	TOSHIBA  
             Model :	RAID LD0         
             Free Space :	93% 
[/B]
Hard Disk :	WDC (80 GB)
DVD-Rom Drive :	MATSHITA DVD-RAM UJ-846S
DVD-Rom Drive :	KM1374V QQB412X SCSI CdRom Device
Monitor Type :	Toshiba TOSHIBA Inte - 17 inches
Network Card :	Intel Corporation PRO/1000 PL Network Connection
Network Card :	Intel Corporation PRO/Wireless 3945ABG
Operating System :	Microsoft Windows XP Professional 5.01.2600 Service Pack 2
DirectX :	Version 9.0c  (July 2007)

```

Now then, the setup...

2 physical 80GB Toshiba SATA HDD's in a RAID 0 if you couldn't tell from above.  I'm using a 130GB partition for XP Pro.  What I want top do is use the rest for Ubuntu.  Data loss is not an issue as I run nightly backups with a NAS unit, so RAID 0 for performance is the way I want to go.  My Notebook uses FakeRAID, or that is my understanding...  I'm a linux dabbler, I play around with it but am not a heavy user, but I am not afraid of the CL or learning new things, even if it means some data loss, and I will do whatever I can for this to work.

Last Year it worked flawlessly on install.  Recognized my RAID 0 array as 1 disk, installed and dual-booted with XP fine.  I think this was v6.06 or some such.  With the gutsy cd, my drives are recognized, but as two separate 80GB drives, which leads me to believe the support for it (RAID 0 with my controller) was taken out.  What I need to know is how to put it back in.  So, if anyone could guide me in the right direction, I would greatly appreciate it.  I ask of your geeky goodness, and If you ever have problems with any Windows Server Products, I will give you some of my geeky goodness! :lolflag:  I wouldn't be here if I haven't heard everywhere that Ubuntu has the best community, and I hope maybe some of you can help me out.

---

### Post by Portending Ennui on 2007-12-26
Anyone?

---

### Post by squid636 on 2008-01-27
I don't know how to fix your problem since I am a noob to Ubuntu but since we both have the same laptop if you run into any more problems let me know.  I might of already been down that road and can help.  I have recently dumped windows on all of my home computers.

---

### Post by slaguth on 2008-01-28
I was just investigating RAID myself and found this tidbit in one of the howtos:

> Under Linux, which has built-in softRAID functionality that pre-dates these devices, the hardware is normally seen for what it is -- multiple hard drives and a multi-channel IDE/SATA controller. Hence, fakeRAID.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

The howto in question deals with installing FakeRaid, which I think is supposed to help with the problem you described.

Hope this helps.

---

