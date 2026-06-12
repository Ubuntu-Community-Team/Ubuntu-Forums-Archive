---
title: "Hibernation/Standby not working (among other things...)"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by Hrwoye on 2007-11-25
So, Standby and Hibernation are not working on my desktop. Trying Hibernation ends up with something that looks like plain restart, and going into Standby looks like shutdown sequence, only the machine never shuts down. Fans keep spinning, screen on, just the disks turn off (I presume). Machine has to boot with ACPI=off or with ACPI 2.0 disabled in BIOS, or it won't boot at all. If I boot it with ACPI 2.0 enabled in BIOS and ACPI=off then I experience another Power Management malfunction manifesting as inability to shut down at all. With ACPI 2.0 disabled in BIOS and ACPI=off omitted at least I am able to perform a proper shut down. APM option in BIOS is enabled.

Logs show that there is even some PnPBIOS problem and suggests to boot with pnpbios=off for more stable operation. Tried it - no change.

So far I could see throughout this forum and other places that Power Management (ACPI, APM...) is an Achilles heel to Linux. I am using plain desktop 2-3 years old PC with ASUS P4V800-X mbo with P4 2.4 GHz HT processor, ATI Radeon 9200 AGP card with 128 Mb, WD SATA2 disk (SATA controller on mbo)... Nothing exotic. I even upgraded BIOS to latest version.

Is there some elegant solution to this problem that does not require a month googling, posting posts to forums, newsgroups, getting a degree and so on? I am not really asking for much, am I?

---

### Post by Pumalite on 2007-11-25
RE: Hibernation: /swap has to be equal to RAM in laptops. With 128 MB of RAM you shouldn't be running anything heavier than Feisty Xubuntu.

---

### Post by Hrwoye on 2007-11-25
> **Pumalite said:**
> RE: Hibernation: /swap has to be equal to RAM in laptops. With 128 MB of RAM you shouldn't be running anything heavier than Feisty Xubuntu.
Just to make it clear, 128 Mb is on a display adapter (ATI Radeon). 768 Mb of RAM is on motherboard. And it is not a laptop, it is a desktop computer.

---

### Post by Pumalite on 2007-11-25
Sorry,  my mistake.

---

### Post by Hrwoye on 2007-11-25
Some System Information on my computer, in case it could help someone detect the problem.

```
-------------------------
  CPU-Z version 1.41
-------------------------

Processors Map
------------------------------------------------------------------------------------

Number of processors	1
Number of threads	2

Processor 0
    -- Core 0
        -- Thread 0
        -- Thread 1


Processors Information
------------------------------------------------------------------------------------

Processor 1 (ID = 0)
Number of cores		1
Number of threads	2 (max 2)
Name			Intel Pentium 4
Codename		Northwood
Specification		Intel(R) Pentium(R) 4 CPU 2.40GHz
Package			Socket 478 mPGA (platform ID = 2h)
CPUID			F.2.9
Extended CPUID		F.2
Brand ID		9
Core Stepping		D1
Technology		0.13 um
Core Speed		2401.3 MHz (12.0 x 200.1 MHz)
Rated Bus speed		800.4 MHz
Stock frequency		2400 MHz
Instructions sets	MMX, SSE, SSE2
L1 Data cache		8 KBytes, 4-way set associative, 64-byte line size
Trace cache		12 Kuops, 8-way set associative
L2 cache		512 KBytes, 8-way set associative, 64-byte line size
FID/VID Control		no
Features		


Thread dumps
------------------------------------------------------------------------------------

CPU Thread 0
APIC ID			0
Topology		Processor ID 0, Core ID 0, Thread ID 0
Type			01001003h
Max CPUID level		00000002h
Max CPUID ext. level	80000004h

Function		eax		ebx		ecx		edx
0x00000000		0x00000002	0x756E6547	0x6C65746E	0x49656E69
0x00000001		0x00000F29	0x00020809	0x00004400	0xBFEBFBFF
0x00000002		0x665B5001	0x00000000	0x00000000	0x007B7040
0x80000000		0x80000004	0x00000000	0x00000000	0x00000000
0x80000001		0x00000000	0x00000000	0x00000000	0x00000000
0x80000002		0x20202020	0x20202020	0x20202020	0x6E492020
0x80000003		0x286C6574	0x50202952	0x69746E65	0x52286D75
0x80000004		0x20342029	0x20555043	0x30342E32	0x007A4847

Cache descriptor	Level 1 D	8 KB	2 threads	
Cache descriptor	Level 1 T	12 KB	2 threads	
Cache descriptor	Level 2 U	512 KB	2 threads	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00900
MSR 0x00000017		edx = 0x000A0000	eax = 0x00000000
MSR 0x0000002C		edx = 0x00000000	eax = 0x0C12000C
MSR 0x000001A0		edx = 0x00000000	eax = 0x000000C9

CPU Thread 1
APIC ID			1
Topology		Processor ID 0, Core ID 0, Thread ID 1
Type			01001003h
Max CPUID level		00000002h
Max CPUID ext. level	80000004h

Function		eax		ebx		ecx		edx
0x00000000		0x00000002	0x756E6547	0x6C65746E	0x49656E69
0x00000001		0x00000F29	0x01020809	0x00004400	0xBFEBFBFF
0x00000002		0x665B5001	0x00000000	0x00000000	0x007B7040
0x80000000		0x80000004	0x00000000	0x00000000	0x00000000
0x80000001		0x00000000	0x00000000	0x00000000	0x00000000
0x80000002		0x20202020	0x20202020	0x20202020	0x6E492020
0x80000003		0x286C6574	0x50202952	0x69746E65	0x52286D75
0x80000004		0x20342029	0x20555043	0x30342E32	0x007A4847

Cache descriptor	Level 1 D	8 KB	2 threads	
Cache descriptor	Level 1 T	12 KB	2 threads	
Cache descriptor	Level 2 U	512 KB	2 threads	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00800
MSR 0x00000017		edx = 0x000A0000	eax = 0x00000000
MSR 0x0000002C		edx = 0x00000000	eax = 0x0C12000C
MSR 0x000001A0		edx = 0x00000000	eax = 0x000000C9


Chipset
------------------------------------------------------------------------------

Northbridge		VIA PT800 (VT8754) rev. 82
Southbridge		VIA VT8237 rev. 00
Memory Type		DDR
Memory Size		768 MBytes
Memory Frequency	200.1 MHz (1:1)
DRAM Interleave		4-way
CAS#			2.5
RAS# to CAS#		3
RAS# Precharge		2
Cycle Time (tRAS)	6


Memory SPD
------------------------------------------------------------------------------

DIMM #1

General
Memory type		DDR
Manufacturer (ID)	Infineon (C1494E46494E454F)
Size			256 MBytes
Max bandwidth		PC3200 (200 MHz)
Part number		64D32300GU5B      
Serial number		01B2C924
Manufacturing date	Week 03/Year 04

Attributes
Number of banks		1
Data width		64 bits
Correction		None
Registered		no
Buffered		no
Nominal Voltage		2.50 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		133	166	200	
CAS#			2.0	2.5	3.0	
RAS# to CAS# delay	2	3	3	
RAS# Precharge		2	3	3	
TRAS			6	7	8	


DIMM #2

General
Memory type		DDR
Manufacturer (ID)	Infineon (C1494E46494E454F)
Size			256 MBytes
Max bandwidth		PC3200 (200 MHz)
Part number		64D32300GU5B      
Serial number		01B2C624
Manufacturing date	Week 03/Year 04

Attributes
Number of banks		1
Data width		64 bits
Correction		None
Registered		no
Buffered		no
Nominal Voltage		2.50 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		133	166	200	
CAS#			2.0	2.5	3.0	
RAS# to CAS# delay	2	3	3	
RAS# Precharge		2	3	3	
TRAS			6	7	8	


DIMM #3

General
Memory type		DDR
Manufacturer (ID)	Infineon (C1494E46494E454F)
Size			256 MBytes
Max bandwidth		PC3200 (200 MHz)
Part number		64D32300GU5B      
Serial number		01B2D111
Manufacturing date	Week 03/Year 04

Attributes
Number of banks		1
Data width		64 bits
Correction		None
Registered		no
Buffered		no
Nominal Voltage		2.50 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		133	166	200	
CAS#			2.0	2.5	3.0	
RAS# to CAS# delay	2	3	3	
RAS# Precharge		2	3	3	
TRAS			6	7	8	


Dump Module #1
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 07 0D 0A 01 40 00 04 50 50 00 82 08 00 01 
10   0E 04 1C 01 02 20 C1 60 50 75 50 3C 28 3C 28 40 
20   60 60 40 40 00 00 00 00 00 37 41 28 28 50 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FD 
40   C1 49 4E 46 49 4E 45 4F 56 36 34 44 33 32 33 30 
50   30 47 55 35 42 20 20 20 20 20 20 03 0C 04 03 01 
60   B2 C9 24 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   43 50 51 31 15 43 5A 43 34 30 35 31 51 4A 4B 20 
90   01 BE FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
A0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
B0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
C0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
D0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
E0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
F0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 


Dump Module #2
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 07 0D 0A 01 40 00 04 50 50 00 82 08 00 01 
10   0E 04 1C 01 02 20 C1 60 50 75 50 3C 28 3C 28 40 
20   60 60 40 40 00 00 00 00 00 37 41 28 28 50 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FD 
40   C1 49 4E 46 49 4E 45 4F 56 36 34 44 33 32 33 30 
50   30 47 55 35 42 20 20 20 20 20 20 03 0C 04 03 01 
60   B2 C6 24 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   43 50 51 31 15 43 5A 43 34 30 35 31 51 4A 35 20 
90   01 A8 FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
A0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
B0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
C0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
D0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
E0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
F0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 


Dump Module #3
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 07 0D 0A 01 40 00 04 50 50 00 82 08 00 01 
10   0E 04 1C 01 02 20 C1 60 50 75 50 3C 28 3C 28 40 
20   60 60 40 40 00 00 00 00 00 37 41 28 28 50 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FD 
40   C1 49 4E 46 49 4E 45 4F 56 36 34 44 33 32 33 30 
50   30 47 55 35 42 20 20 20 20 20 20 03 0C 04 03 01 
60   B2 D1 11 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   43 50 51 31 15 43 5A 43 34 30 35 31 51 48 5A 20 
90   01 CB FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
A0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
B0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
C0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
D0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
E0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
F0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 


Monitoring
------------------------------------------------------------------------------

Mainboard Model		P4V800-X (0x1F7 - 0xB6CD0A)

LPCIO
-----------------------------------------------------
Vendor			Winbond
Model			W83627THF
Vendor ID		0x5CA3
Chip ID			0x82
Revision ID		0x84
Config Mode I/O address	0x2E

Dump config mode register space, LDN = 0xB
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   FF FF FF FF FF FF FF 0B FF FF FF FF FF FF FF FF 
10   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
20   82 84 FF FE 02 00 00 FF 20 00 00 1A 58 20 00 FF 
30   01 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
40   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
50   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
60   02 90 FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
70   00 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 


Hardware monitor
-----------------------------------------------------

Winbond W83627THF hardware monitor

Voltage sensor 0	1.58 Volts [0x63] (CPU VCore)
Voltage sensor 1	12.22 Volts [0xC9] (+12V)
Voltage sensor 2	3.34 Volts [0xD1] (+3.3V)
Voltage sensor 3	5.09 Volts [0xBF] (+5V)
Temperature sensor 0	33°C (91°F) [0x21] (SYSTIN)
Temperature sensor 1	34°C (93°F) [0x44] (CPUTIN)
Temperature sensor 2	18°C (64°F) [0x1DC] (VTIN)
Fan sensor 1		2766 RPM [0x7A] (FANIN1)

Dump hardware monitor
LPC Register space, base address = 0x0290

bank 0
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   01 FF 01 FF 00 00 00 00 01 01 01 01 3C 3C 0A 0A 
10   01 FF 00 00 00 01 01 3C 42 00 FF FF 24 32 00 DF 
20   60 C6 D1 C0 FF 50 20 21 FF 7A FF F0 00 81 80 11 
30   46 54 60 40 47 08 00 7E 01 02 00 88 08 01 00 00 
40   03 DE 09 FE FF 00 00 BF 2D 03 01 44 18 95 00 A3 
50   FF FF 80 FF FF FF 00 80 90 60 FF FF 11 24 FF 05 
60   60 C6 D1 C0 FF 50 20 21 FF 7A FF F0 00 81 80 11 
70   46 54 60 40 47 08 00 7E 01 02 00 88 08 01 00 00 
80   01 FF 01 FF 00 00 00 00 01 01 01 01 3C 3C 0A 0A 
90   01 FF 00 00 00 01 01 3C 42 00 FF FF 24 32 00 DF 
A0   60 C6 D1 C0 FF 50 20 21 FF 7A FF F0 00 81 80 11 
B0   46 54 60 40 47 08 00 7E 01 02 00 88 08 01 00 00 
C0   03 00 00 FE FF 00 00 BF 2D 03 01 44 18 95 00 A3 
D0   FF FF 80 FF FF FF 00 80 90 60 FF FF 11 24 FF 05 
E0   60 C6 D1 C0 FF 50 20 21 FF 7A FF F0 00 81 80 11 
F0   46 54 60 40 47 08 00 7E 01 02 00 88 08 01 00 00 

bank 1
50   21 80 00 4B 00 50 00 FF FF FF FF FF FF FF FF FF 
bank 2
50   EE 00 00 4B 00 50 00 FF FF FF FF FF FF FF FF FF 
bank 3
50   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
bank 4
50   03 13 00 00 00 13 00 00 1B DE 09 03 11 00 FF FF 


PCI Device List
------------------------------------------------------------------------------

Host Bridge
bus 0 (0x00), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x1106
	Model ID		0x3168
	Revision ID		0x82
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x08
	Header			0x00
PCI header
	Address 0 (memory)	0xE0000000
	Subvendor ID		0x1043
	Subsystem ID		0x8105
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	PCI Capability class 0x0
		Offset		80h
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 68 31 06 00 30 22 82 00 00 06 00 08 00 00 
	10   08 00 00 E0 00 00 00 00 00 00 00 00 00 00 00 00 
	20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 05 81 
	30   00 00 00 00 80 00 00 00 00 00 00 00 00 00 00 00 
	40   00 19 88 80 82 44 10 00 13 39 88 80 82 44 00 01 
	50   A0 FE EF 88 A0 C4 30 30 EE E0 10 10 20 20 30 30 
	60   40 AA 2A E0 66 5F 40 94 72 2D 54 D0 41 74 00 00 
	70   82 C8 EC 01 20 09 50 00 01 00 00 00 00 00 02 10 
	80   00 00 00 00 00 70 88 03 02 00 00 00 06 B6 22 03 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   02 C0 35 00 09 02 00 1F 00 00 00 00 41 42 08 CF 
	B0   7F 00 11 00 27 46 46 02 69 A4 6A 06 00 20 CB 8C 
	C0   01 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 78 11 00 11 00 75 38 42 00 
	E0   00 00 00 00 00 FF 69 22 CC 77 CC 9A 96 CC 00 80 
	F0   00 00 E4 00 00 00 82 00 00 C0 20 80 00 06 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 1 (0x01), function 0 (0x00)
Common header
	Vendor ID		0x1106
	Model ID		0xB198
	Revision ID		0x00
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x01
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	Power Management Capability
		Offset		80h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 98 B1 07 01 30 02 00 00 04 06 00 00 01 00 
	10   00 00 00 00 00 00 00 00 00 01 01 00 B0 B0 20 22 
	20   50 DF A0 DF 40 BF 30 DF 00 00 00 00 00 00 00 00 
	30   00 00 00 00 80 00 00 00 00 00 00 00 00 00 0B 00 
	40   83 C7 00 44 35 72 98 B1 00 00 00 00 00 00 00 00 
	50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   01 00 02 02 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


RAID Controller
bus 0 (0x00), device 15 (0x0F), function 0 (0x00)
Common header
	Vendor ID		0x1106
	Model ID		0x3149
	Revision ID		0x80
	PI			0x00
	SubClass		0x04
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x40
	Header			0x80
PCI header
	Address 0 (port)	0x0000E800
	Address 1 (port)	0x0000E400
	Address 2 (port)	0x0000E000
	Address 3 (port)	0x0000D800
	Address 4 (port)	0x0000D400
	Address 5 (port)	0x0000D000
	Subvendor ID		0x1043
	Subsystem ID		0x80ED
	Int. Line		0x14
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		C0h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 49 31 07 00 90 02 80 00 04 01 00 40 80 00 
	10   01 E8 00 00 01 E4 00 00 01 E0 00 00 01 D8 00 00 
	20   01 D4 00 00 01 D0 00 00 00 00 00 00 43 10 ED 80 
	30   00 00 00 00 C0 00 00 00 00 00 00 00 14 01 00 00 
	40   13 03 F1 44 06 AF 00 00 10 82 05 03 00 00 00 00 
	50   00 00 00 00 00 00 04 04 00 10 10 00 05 00 30 00 
	60   11 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 01 00 01 00 00 00 00 00 
	80   00 00 00 00 00 00 00 00 00 E0 E5 02 00 00 E6 02 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   01 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   80 01 49 31 43 10 ED 80 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


IDE Controller
bus 0 (0x00), device 15 (0x0F), function 1 (0x01)
Common header
	Vendor ID		0x1106
	Model ID		0x0571
	Revision ID		0x06
	PI			0x8A
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x20
	Header			0x00
PCI header
	Address 4 (port)	0x0000FC00
	Subvendor ID		0x1043
	Subsystem ID		0x80ED
	Int. Line		0xFF
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		C0h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 71 05 07 00 90 02 06 8A 01 01 00 20 00 00 
	10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20   01 FC 00 00 00 00 00 00 00 00 00 00 43 10 ED 80 
	30   00 00 00 00 C0 00 00 00 00 00 00 00 FF 01 00 00 
	40   1B F2 09 05 18 1C C0 00 11 20 A8 A8 FF 00 B6 B6 
	50   17 17 07 07 0C 00 00 00 A8 A8 A8 A8 00 00 00 00 
	60   00 02 00 00 00 00 00 00 00 02 00 00 00 00 00 00 
	70   82 01 00 00 00 00 00 00 02 01 00 00 00 00 00 00 
	80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   01 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   06 00 71 05 43 10 ED 80 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 09 00 00 00 00 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 16 (0x10), function 0 (0x00)
Common header
	Vendor ID		0x1106
	Model ID		0x3038
	Revision ID		0x81
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x10
	Latency			0x40
	Header			0x80
PCI header
	Address 4 (port)	0x0000CC00
	Subvendor ID		0x1043
	Subsystem ID		0x80ED
	Int. Line		0x15
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		80h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 38 30 17 00 10 02 81 00 03 0C 10 40 80 00 
	10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20   01 CC 00 00 00 00 00 00 00 00 00 00 43 10 ED 80 
	30   00 00 00 00 80 00 00 00 00 00 00 00 15 01 00 00 
	40   40 12 03 00 00 00 00 00 00 0B A0 00 00 00 00 00 
	50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   01 00 C2 FF 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 16 (0x10), function 1 (0x01)
Common header
	Vendor ID		0x1106
	Model ID		0x3038
	Revision ID		0x81
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x10
	Latency			0x40
	Header			0x80
PCI header
	Address 4 (port)	0x0000DC00
	Subvendor ID		0x1043
	Subsystem ID		0x80ED
	Int. Line		0x15
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		80h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 38 30 17 00 10 02 81 00 03 0C 10 40 80 00 
	10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20   01 DC 00 00 00 00 00 00 00 00 00 00 43 10 ED 80 
	30   00 00 00 00 80 00 00 00 00 00 00 00 15 01 00 00 
	40   40 12 03 00 00 00 00 00 00 0B A0 00 00 00 00 00 
	50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   01 00 C2 FF 00 80 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 16 (0x10), function 2 (0x02)
Common header
	Vendor ID		0x1106
	Model ID		0x3038
	Revision ID		0x81
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x10
	Latency			0x40
	Header			0x80
PCI header
	Address 4 (port)	0x0000EC00
	Subvendor ID		0x1043
	Subsystem ID		0x80ED
	Int. Line		0x15
	Int. Pin		0x02
Capabilities
	Power Management Capability
		Offset		80h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 38 30 17 00 10 02 81 00 03 0C 10 40 80 00 
	10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20   01 EC 00 00 00 00 00 00 00 00 00 00 43 10 ED 80 
	30   00 00 00 00 80 00 00 00 00 00 00 00 15 02 00 00 
	40   40 12 03 00 00 00 00 00 00 0B A0 00 00 00 00 00 
	50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   01 00 C2 FF 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 


USB Controller (UHCI)
bus 0 (0x00), device 16 (0x10), function 3 (0x03)
Common header
	Vendor ID		0x1106
	Model ID		0x3038
	Revision ID		0x81
	PI			0x00
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x10
	Latency			0x40
	Header			0x80
PCI header
	Address 4 (port)	0x0000C000
	Subvendor ID		0x1043
	Subsystem ID		0x80ED
	Int. Line		0x15
	Int. Pin		0x02
Capabilities
	Power Management Capability
		Offset		80h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 38 30 17 00 10 02 81 00 03 0C 10 40 80 00 
	10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20   01 C0 00 00 00 00 00 00 00 00 00 00 43 10 ED 80 
	30   00 00 00 00 80 00 00 00 00 00 00 00 15 02 00 00 
	40   40 10 03 00 00 00 00 00 00 0B A0 00 00 00 00 00 
	50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60   10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   01 00 C2 FF 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 


USB 2.0 Controller (EHCI)
bus 0 (0x00), device 16 (0x10), function 4 (0x04)
Common header
	Vendor ID		0x1106
	Model ID		0x3104
	Revision ID		0x86
	PI			0x20
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x10
	Latency			0x40
	Header			0x80
PCI header
	Address 0 (memory)	0xDFE00000
	Subvendor ID		0x1043
	Subsystem ID		0x80ED
	Int. Line		0x15
	Int. Pin		0x03
Capabilities
	Power Management Capability
		Offset		80h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 04 31 17 00 10 02 86 20 03 0C 10 40 80 00 
	10   00 00 E0 DF 00 00 00 00 00 00 00 00 00 00 00 00 
	20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 ED 80 
	30   00 00 00 00 80 00 00 00 00 00 00 00 15 03 00 00 
	40   00 00 03 00 00 00 00 00 80 10 00 09 00 00 00 00 
	50   00 5A 00 80 00 00 00 00 04 0B 66 88 33 66 66 00 
	60   20 20 01 00 00 00 00 00 01 00 00 00 00 00 00 C0 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   01 00 C2 FF 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 86 00 00 00 00 00 00 00 00 00 


PCI to ISA Bridge
bus 0 (0x00), device 17 (0x11), function 0 (0x00)
Common header
	Vendor ID		0x1106
	Model ID		0x3227
	Revision ID		0x00
	PI			0x00
	SubClass		0x01
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x1043
	Subsystem ID		0x80ED
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	Power Management Capability
		Offset		C0h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 27 32 87 00 10 02 00 00 01 06 00 00 80 00 
	10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 ED 80 
	30   00 00 00 00 C0 00 00 00 00 00 00 00 00 00 00 00 
	40   44 00 F0 0B 00 00 00 00 8C 20 00 00 44 00 08 08 
	50   80 98 09 00 00 00 00 00 43 90 00 01 00 00 04 08 
	60   00 00 00 00 10 00 02 04 00 00 00 00 00 00 00 00 
	70   43 10 ED 80 00 00 00 00 00 00 00 00 20 00 00 00 
	80   20 84 59 00 8A 00 00 00 01 08 00 00 00 18 00 00 
	90   0B 00 37 00 B0 C5 0F 00 10 5E 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   01 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   01 04 01 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 54 09 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 01 00 00 00 00 00 00 00 00 00 


Audio device
bus 0 (0x00), device 17 (0x11), function 5 (0x05)
Common header
	Vendor ID		0x1106
	Model ID		0x3059
	Revision ID		0x60
	PI			0x00
	SubClass		0x01
	BaseClass		0x04
	Cache Line		0x00
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (port)	0x0000C400
	Subvendor ID		0x1043
	Subsystem ID		0x80B0
	Int. Line		0x16
	Int. Pin		0x03
Capabilities
	Power Management Capability
		Offset		C0h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 59 30 01 00 10 02 60 00 01 04 00 00 00 00 
	10   01 C4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 B0 80 
	30   00 00 00 00 C0 00 00 00 00 00 00 00 16 03 00 00 
	40   01 CC 00 00 00 00 00 00 00 00 00 00 3C 00 00 00 
	50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   01 00 02 06 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   01 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Ethernet Controller
bus 0 (0x00), device 18 (0x12), function 0 (0x00)
Common header
	Vendor ID		0x1106
	Model ID		0x3065
	Revision ID		0x78
	PI			0x00
	SubClass		0x00
	BaseClass		0x02
	Cache Line		0x10
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (port)	0x0000C800
	Address 1 (memory)	0xDFF00000
	Subvendor ID		0x1043
	Subsystem ID		0x80ED
	Int. Line		0x17
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		40h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   06 11 65 30 17 01 10 02 78 00 00 02 10 40 00 00 
	10   01 C8 00 00 00 00 F0 DF 00 00 00 00 00 00 00 00 
	20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 ED 80 
	30   00 00 00 00 40 00 00 00 00 00 00 00 17 01 03 08 
	40   01 00 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	50   00 00 80 04 00 00 00 00 00 00 00 00 65 30 00 03 
	60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


VGA Controller
bus 1 (0x01), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x5964
	Revision ID		0x01
	PI			0x00
	SubClass		0x00
	BaseClass		0x03
	Cache Line		0x10
	Latency			0xFF
	Header			0x80
PCI header
	Address 0 (memory)	0xD0000000
	Address 1 (port)	0x0000B000
	Address 2 (memory)	0xDFA00000
	Subvendor ID		0x1043
	Subsystem ID		0xC006
	Int. Line		0x10
	Int. Pin		0x01
Capabilities
	AGP Capability
		Offset		58h
		Version		3.0
		Status		disabled
		Max transfer	8x
		Queue lenght	1 (max 256)
	Power Management Capability
		Offset		50h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   02 10 64 59 07 01 B0 02 01 00 00 03 10 FF 80 00 
	10   08 00 00 D0 01 B0 00 00 00 00 A0 DF 00 00 00 00 
	20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 06 C0 
	30   00 00 90 DF 58 00 00 00 00 00 00 00 10 01 08 00 
	40   00 00 00 00 00 00 00 00 00 00 00 00 43 10 06 C0 
	50   01 00 02 06 00 00 00 00 02 50 30 00 1B 02 00 FF 
	60   00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Display Controller
bus 1 (0x01), device 0 (0x00), function 1 (0x01)
Common header
	Vendor ID		0x1002
	Model ID		0x5D44
	Revision ID		0x01
	PI			0x00
	SubClass		0x80
	BaseClass		0x03
	Cache Line		0x10
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xC8000000
	Address 1 (memory)	0xDF800000
	Subvendor ID		0x1043
	Subsystem ID		0xC007
	Int. Line		0xFF
	Int. Pin		0x00
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.1
Dump
	      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	00   02 10 44 5D 07 00 B0 02 01 00 80 03 10 40 00 00 
	10   08 00 00 C8 00 00 80 DF 00 00 00 00 00 00 00 00 
	20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 07 C0 
	30   00 00 00 00 50 00 00 00 00 00 00 00 FF 00 08 00 
	40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	50   01 00 02 06 00 00 00 00 02 50 30 00 1B 02 00 FF 
	60   00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


DMI
------------------------------------------------------------------------------

DMI BIOS
--------
	vendor		American Megatrends Inc.
	version		1009.006
	date		09/26/2005


DMI System Information
----------------------
	manufacturer	To Be Filled By O.E.M.
	product		To Be Filled By O.E.M.
	version		To Be Filled By O.E.M.
	serial		To Be Filled By O.E.M.
	UUID		00020003-00040005-00060007-00080009


DMI Baseboard
-------------
	vendor		ASUSTeK Computer INC.
	model		P4V800-X
	revision	Rev 1.xx
	serial		MB-1234567890


DMI System Enclosure
--------------------
	manufacturer	Chassis Manufacture
	chassis type	Desktop
	chassis serial	Chassis Serial Number


DMI Processor
-------------
	manufacturer	Intel
	model		Intel(R) Pentium(R) 4 CPU 2.40GHz
	clock speed	2400.0MHz
	FSB speed	200.0MHz
	multiplier	12.0x


DMI Memory Controller
---------------------
	correction	64-bit ECC
	Max module size	1024MBytes


DMI Memory Module
-----------------
	designation	DIMM0
	size		256MBytes (single bank)


DMI Memory Module
-----------------
	designation	DIMM1
	size		256MBytes (single bank)


DMI Memory Module
-----------------
	designation	DIMM2
	size		256MBytes (single bank)


DMI Port Connector
------------------
	designation	PS2 (internal)
	designation	PS2Mouse (external)
	port type	Mouse Port
	connector	PS/2


DMI Port Connector
------------------
	designation	PS2 (internal)
	designation	Keyboard (external)
	port type	Keyboard Port
	connector	PS/2


DMI Port Connector
------------------
	designation	LPT (internal)
	designation	LPT 1 (external)
	port type	Parallel Port ECP/EPP
	connector	DB-25 male


DMI Port Connector
------------------
	designation	COM (internal)
	designation	COM A (external)
	port type	Serial Port 16550A
	connector	DB-9 male


DMI Port Connector
------------------
	designation	Audio Mic (internal)
	designation	Audio Mic In (external)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	Line In (internal)
	designation	Audio Line In (external)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	Line Ou (internal)
	designation	Audio Line Out (external)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	LAN (internal)
	designation	LAN (external)
	port type	Network Port
	connector	RJ-45


DMI Port Connector
------------------
	designation	USB1 (internal)
	designation	USB1 (external)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB2 (internal)
	designation	USB2 (external)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB3 (internal)
	designation	USB3 (external)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB4 (internal)
	designation	USB4 (external)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB5 (internal)
	designation	USB5 (external)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB6 (internal)
	designation	USB6 (external)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB7 (internal)
	designation	USB7 (external)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	USB8 (internal)
	designation	USB8 (external)
	port type	USB
	connector	Access Bus (USB)


DMI Port Connector
------------------
	designation	AUX IN (internal)
	port type	Audio Port
	connector	On Board Sound Input From CD-ROM


DMI Port Connector
------------------
	designation	CDIN (internal)
	port type	Audio Port
	connector	On Board Sound Input From CD-ROM


DMI Port Connector
------------------
	designation	PRI IDE (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	SEC IDE (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	FLOPPY (internal)
	connector	On Board Floppy


DMI Port Connector
------------------
	designation	FRONT PNL (internal)
	connector	9 Pin Dual Inline (pin 10 cut)


DMI Port Connector
------------------
	designation	CHASSIS REAR FAN (internal)


DMI Port Connector
------------------
	designation	CPU FAN (internal)


DMI Port Connector
------------------
	designation	FRONT FAN (internal)


DMI Port Connector
------------------
	designation	FNT USB (internal)


DMI Port Connector
------------------
	designation	FP AUD (internal)


DMI Port Connector
------------------
	designation	CONFIG (internal)


DMI Port Connector
------------------
	designation	SCSI LED (internal)


DMI Port Connector
------------------
	designation	INTRUDER (internal)


DMI Port Connector
------------------
	designation	ITP (internal)


DMI Port Connector
------------------
	designation	MAIN POWER (internal)


DMI Extension Slot
------------------
	designation	AGP
	type		AGP 8x
	width		32 bits
	populated	yes


DMI Extension Slot
------------------
	designation	PCI1
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI2
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI3
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI4
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI5
	type		PCI
	width		32 bits
	populated	no


DMI Physical Memory Array
-------------------------
	location	Motherboard
	usage		System Memory
	correction	None
	max capacity	4096MBytes
	max# of devices	3


DMI Memory Device
-----------------
	designation	DIMM0
	format		DIMM
	type		SDRAM
	total width	64bits
	data width	64bits
	size		256MBytes


DMI Memory Device
-----------------
	designation	DIMM1
	format		DIMM
	type		SDRAM
	total width	64bits
	data width	64bits
	size		256MBytes


DMI Memory Device
-----------------
	designation	DIMM2
	format		DIMM
	type		SDRAM
	total width	64bits
	data width	64bits
	size		256MBytes


Software
------------------------------------------------------------------------------

Windows Version		Microsoft Windows XP Professional  Service Pack 2 (Build 2600) 
DirectX Version		9.0c


Resources
------------------------------------------------------------------------------

Memory I/O Space, BA=0x00000000E0000000
Port I/O Space, BA=0xE800
Port I/O Space, BA=0xE400
Port I/O Space, BA=0xE000
Port I/O Space, BA=0xD800
Port I/O Space, BA=0xD400
Port I/O Space, BA=0xD000
Port I/O Space, BA=0xFC00
Port I/O Space, BA=0xCC00
Port I/O Space, BA=0xDC00
Port I/O Space, BA=0xEC00
Port I/O Space, BA=0xC000
Memory I/O Space, BA=0x00000000DFE00000
Port I/O Space, BA=0xC400
Port I/O Space, BA=0xC800
Memory I/O Space, BA=0x00000000DFF00000
Memory I/O Space, BA=0x00000000D0000000
Port I/O Space, BA=0xB000
Memory I/O Space, BA=0x00000000DFA00000
Memory I/O Space, BA=0x00000000C8000000
Memory I/O Space, BA=0x00000000DF800000
Port I/O Space, BA=0x808, size=0x4
Memory I/O Space, BA=0x00000000FEE00000, size=0x1000
Port I/O Space, BA=0x400
Port I/O Space, BA=0x290
Port I/O Space, BA=0x2E
```

---

### Post by erfahren on 2007-11-25
if you are using the fglrx driver (the propritary driver enabled through the Restricted Drivers Manager) for your ATI graphics card then your not easily going to get Suspend/Hibernation to work on Gutsy at this time from what I've heard.

I won't go into details why (mainly because I barely understand it :) )

if its important to you to have suspend working I've seen it recommended that you go back to Feisty until the problem gets worked out.

I've tried numorous things to get mine to work with no luck.

I edited the /etc/default/acpi-support file as [this post](http://ubuntuforums.org/showpost.php?p=3785681&postcount=20) suggested and ended up not being able to boot (and stupid me didn't back the file up first like I usually do so had to go and edit it using nano from the command prompt).
-- just thought I'd mention that last part in case you go and try something like that.

---

### Post by Hrwoye on 2007-11-25
From my point of view this ACPI problem is much bigger than Standby/Hibernation issue alone. I have dual boot with an XP on the other disk, which is working perfectly fine, and booting Ubuntu requires changing ACPI, APIC, APM and PnP settings in BIOS every time I want to explore and learn about Linux ON Linux. That is something I am not really willing to do, that shouldn't work that way, especially not on my plain old vanilla three years old PC with mass produced parts. :(

And I'm aware what all this power issues are worse for laptop users.

---

