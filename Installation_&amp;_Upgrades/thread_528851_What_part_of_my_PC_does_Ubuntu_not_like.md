---
title: "What part of my PC does Ubuntu not like?"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Qwertinsky on 2007-08-18
I have had Ubuntu running on this system in the past. 

I know 6.06 ran and I am pretty sure Edgy ran.

The last few versions have been a complete failure on my system. They will seem to install using the ALT disk but when I boot it gets so far and just goes to a blank screen and locks up. Live CD's do exactly the same get seemingly most of the way through the boot process and just stop.

My system spec's are nothing too exotic:

**Motherboard:**
Manufacturer	Gigabyte Technology Co., Ltd.
Model	GA-K8N-SLi
Version	F2
Serial Number	Sat Aug 06 02:06:01 2005
Chipset Vendor	Nvidia Corp
Chipset Model	nForce4 Memory Controller
South Bridge	nForce4 PCI to ISA Bridge
SMBus	Nvidia Corp nForce4 SMBus @1C00h
SMBus	Nvidia Corp nForce4 SMBus @B000h
CPU	AMD Athlon 64 X2 4200+
Cpu Socket	Socket 939

**BIOS**
Property	Value
BIOS Version	Nvidia - 42302e31
	Award Modular BIOS v6.00PG
BIOS Date	05/11/06
BIOS Web Page	[http://www.award.com](http://www.award.com)
BIOS Vendor	Award Software International, Inc.
Version	F2
Release	05/11/2006

**CPU:**
Property	Value
Number of CPU(s)	One Physical Processor / 2 Cores / 2 Logical Processors / 64 bits
Vendor	AuthenticAMD
CPU Full Name	AMD Athlon 64 X2 4200+
CPU Name	AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
CPU Code Name	Toledo-512K
Technology	0.09µ
Platform Name	Socket 939
Type	Original OEM processor


**RAM**
Device Locator	Slot 1
Manufacturer	Corsair
Part Number	CMX512-3200C2
Serial Number	00000000
Capacity	512 MBytes
Memory Type	SDRAM DDR
Speed	PC3200 (200 MHz)
Data Width	64 bits

Device Locator	Slot 2
Manufacturer	Corsair
Part Number	CMX512-3200C2
Serial Number	00000000
Capacity	512 MBytes
Memory Type	SDRAM DDR
Speed	PC3200 (200 MHz)
Data Width	64 bits

**Video:**
DeviceID	VideoController0
Video Bios Version	Version 5.40.02.36.08 
Video Bios Date	01/25/05
Name	GeForce 6800 GT
Chip Type	GeForce 6800 GT
DAC Type	Integrated RAMDAC
Memory	256 MBytes

DeviceID	VideoController1
Video Bios Version	Version 5.40.02.36.08 
Video Bios Date	01/25/05
Name	GeForce 6800 GT
Chip Type	GeForce 6800 GT
DAC Type	Integrated RAMDAC
Memory	256 MBytes

**HDD:**
Property	Value
Vendor	Seagate
Model	ST3300831AS
Disk Family	Barracuda 7200.8 SATA NCQ
Interface	IDE SATA
Serial Number	5NF0H8S0
Revision	3.03
Size	300 GBytes

**Network:**
Card 1 (Connected)	NVIDIA nForce Networking Controller
Description	NVIDIA nForce Networking Controller - Packet Scheduler Miniport
Type	WIRED
Speed	100 Mbps

**Monitor**
Monitor Name	SyncMaster 960B/960BF,SyncMaster Magic CX915T(Digital)
Monitor ID	SAM01E5
Model	SyncMaster
Manufacturer	Samsung
Manufacturing Date	2006, Week 2
Digital Display Input	
Display Size	19" (38 cm x 30 cm)
Horizontal Frequency	30-81 kHz
Vertical Frequency	56-76 Hz
Current Resolution	1280 x 1024 @ 60Hz - Aspect Ratio 5:4
Supported Resolution	1280 x 1024 @ 60Hz - Aspect Ratio 5:4
Supported Resolution	1280 x 960 @ 60Hz - Aspect Ratio 4:3
Supported Resolution	1152 x 864 @ 75Hz - Aspect Ratio 4:3
Max dot clock (video bandwidth)	140 MHz
DPMS Mode Support	Active Off

---

### Post by Steve1961 on 2007-08-18
The only potential problem I see with your system is your x2 cpu - there seems to be a lot of people who have one of those having various issue.  the rest of your kits looks fairly standard and much the same as mine, apart from the fact that I have a single core cpu.  I recently upgraded my cpu and had a few issues re-cpu scaling, but a bios upgrade resolved those.  Might be worth considering if nothing else works, but search these forums first.

You could try hitting F6 and entering these parameters:

nosplash noapic nolapic

---

