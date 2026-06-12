---
title: "Ubuntu 9.04 doesn't detect my SSD, works fine in 8.10"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aceat64 on 2009-04-09
If I try upgrading to 9.04 the kernel can't see my Intel X25-M. However, it can see and use every other drive in my system. I have tried plugging the drive into each of the 6 slots on my motherboard, same results every time. Under 8.10 the drive is detected fine.

My motherboard is an evga 680i SLI, it's using the sata_nv kernel driver. 

Here's the output from lspci for my SATA controller.
```
00:0e.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Device [10de:c55e]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin C routed to IRQ 21
	Region 0: I/O ports at c000 [size=8]
	Region 1: I/O ports at bc00 [size=4]
	Region 2: I/O ports at b800 [size=8]
	Region 3: I/O ports at b400 [size=4]
	Region 4: I/O ports at b000 [size=16]
	Region 5: Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: sata_nv
	Kernel modules: ata_generic, sata_nv, pata_acpi
```

Please note, there is no place in my bios to run the drive in "legacy" or "compatibility" modes, as this motherboard does not support AHCI, I believe this means it is always in "legacy" mode.

When I get some free time I plan on compiling various kernel version to try and narrow down at which version the drive stops being recognized. Any help in getting this resolved would be greatly appreciated.

---

### Post by frodon on 2009-04-09
Moved to jaunty testing and discussion forum.

---

