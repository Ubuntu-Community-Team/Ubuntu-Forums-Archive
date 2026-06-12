---
title: "Printing GUI Does Not Launch After 14.04 Upgrade"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by mulluysavage on 2014-11-04
Upgraded from 12.04 to 14.04. Click on Printers: Wheelie pointer spins, then nothing.

phil@phil-V5-171:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 58
Stepping:              9
CPU MHz:               768.000
BogoMIPS:              4788.87
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K
NUMA node0 CPU(s):     0-3

System Information
	Manufacturer: Acer
	Product Name: V5-171
	Version: V2.15
	Serial Number: NXM3AAA00823811E473400
	UUID: CBC54907-0202-E211-B90F-B888E3A53FBD
	Wake-up Type: Power Switch
	SKU Number: V5-171_0743_V2.15
	Family: Type1Family

Base Board Information
	Manufacturer: Acer
	Product Name: Mimic             
	Version: Type2 - Board Version
	Serial Number: NBM3A110072383E93E3400
	Asset Tag: Type2 - Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Type2 - Board Chassis Location
	Type: Motherboard

Chassis Information
	Manufacturer: Acer
	Type: Notebook
	Lock: Not Present
	Version: V2.15
	Serial Number: NXM3AAA00823811E473400
	Asset Tag:                  
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0
	SKU Number: Not Specified

Processor Information
	Socket Designation: U3E1
	Type: Central Processor
	Family: Core i7
	Manufacturer: Intel(R) Corporation
	ID: A9 06 03 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 58, Stepping 9
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Multi-threading)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Core(TM) i7-3517U CPU @ 1.90GHz
	Voltage: 0.8 V
	External Clock: 100 MHz
	Max Speed: 4000 MHz
	Current Speed: 1800 MHz
	Status: Populated, Enabled
	Upgrade: Socket rPGA988B
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 2
	Core Enabled: 2
	Thread Count: 4
	Characteristics:
		64-bit capable
		Multi-Core
		Hardware Thread
		Execute Protection
		Enhanced Virtualization
		Power/Performance Control

Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 8192 MB
	Maximum Total Memory Size: 16384 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		Other
	Memory Module Voltage: Unknown
	Associated Memory Slots: 2
		0x0006
		0x0007
	Enabled Error Correcting Capabilities:
		None

Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: None
	Current Speed: Unknown
	Type: DIMM
	Installed Size: 4096 MB (Single-bank Connection)
	Enabled Size: 4096 MB (Single-bank Connection)
	Error Status: OK

Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: None
	Current Speed: Unknown
	Type: DIMM
	Installed Size: 4096 MB (Single-bank Connection)
	Enabled Size: 4096 MB (Single-bank Connection)
	Error Status: OK

Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 32 kB
	Maximum Size: 32 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Data
	Associativity: 8-way Set-associative

Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 32 kB
	Maximum Size: 32 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Instruction
	Associativity: 8-way Set-associative

Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 256 kB
	Maximum Size: 256 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Multi-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Cache Information
	Socket Designation: L3 Cache
	Configuration: Enabled, Not Socketed, Level 3
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 4096 kB
	Maximum Size: 4096 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Multi-bit ECC
	System Type: Unified
	Associativity: 16-way Set-associative

System Slot Information
	Designation: J5C1
	Type: x16 PCI Express x16
	Current Usage: Available
	Length: Other
	ID: 1
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:01.0

System Slot Information
	Designation: J6C1
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 2
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.0

System Slot Information
	Designation: J6C2
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 3
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.1

System Slot Information
	Designation: J6D2
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 4
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.2

System Slot Information
	Designation: J7C1
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 5
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.3

System Slot Information
	Designation: J7D2
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 6
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.4

System Slot Information
	Designation: J8C1
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 7
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.5

System Slot Information
	Designation: J8C2
	Type: x16 PCI Express x16
	Current Usage: Available
	Length: Other
	ID: 8
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.7

On Board Device Information
	Type: Video
	Status: Enabled
	Description: Video Graphics Controller

On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Lan Controller

OEM Strings
	String 1: String1 for Original Equipment Manufacturer
	String 2: vZcaCXPAt+w-p
	String 3: 7HR5KlVbv8MeI
	String 4: Bbo22BpkmBgSf
	String 5: String5 for Original Equipment Manufacturer

System Configuration Options
	Option 1: SMI:00B2C002
	Option 2: String2 for Type12 Equipment Manufacturer
	Option 3: DSN:S14GNEACC12929E 
	Option 4: DSN:341BA0274D3S16C11G
	Option 5: DSN:TEST42b500682006/03/01
	Option 6: String6 for Type12 Equipment Manufacturer
	Option 7: String7 for Type12 Equipment Manufacturer

Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 16 GB
	Number Of Devices: 2

---

### Post by tgalati4 on 2014-11-05
One tip that is often not mentioned anywhere, is to delete all of your printers in linux, perform the operating system upgrade, then reinstall your printers.  If you try to send print jobs to the old print queues, they will often fail.

```
sudo service cups status
lpstat -a
```

Delete the printers from here:  [http://localhost:631](http://localhost:631)

Go into Administration and delete each printer.  Then bring up the Printers dialog and reinstall the printers.  You can also install printers from the web page.

---

