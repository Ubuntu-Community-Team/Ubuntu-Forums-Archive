---
title: "'nm_hal_deinit failed' When I shutdown the Fesity"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by HolyJoe on 2007-06-08
I got 'nm_hal_deinit failed' error when I shutdown the Fesity.

---

### Post by HolyJoe on 2007-06-08
my ```
lspci -vv
``` output is:
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: IBM Unknown device 0575
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: c0000000-c7ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: b0200000-b02fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=03, subordinate=0a, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: b2000000-b3ffffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000c80fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Unknown device 0565
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Unknown device 0565
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Unknown device 0565
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 21
	Region 4: I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Unknown device 0565
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 22
	Region 4: I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: IBM Unknown device 0566
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 22
	Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=0b, subordinate=0e, sec-latency=64
	I/O behind bridge: 00005000-00008fff
	Memory behind bridge: b4000000-bfffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d7ffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: IBM Unknown device 0567
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 1c00 [size=256]
	Region 1: I/O ports at 1880 [size=64]
	Region 2: Memory at b0000800 (32-bit, non-prefetchable) [size=512]
	Region 3: Memory at b0000400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: IBM Unknown device 0576
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 2400 [size=256]
	Region 1: I/O ports at 2000 [size=128]
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: IBM Unknown device 0568
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
	Subsystem: IBM Unknown device 056a
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 18c0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: IBM Unknown device 056b
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 11
	Region 4: I/O ports at 18e0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300] (prog-if 00 [VGA])
	Subsystem: IBM Unknown device 056e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at c0000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 3000 [size=256]
	Region 2: Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at b0120000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
	Subsystem: IBM Unknown device 0577
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at b0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
	Subsystem: IBM Unknown device 056c
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at b4000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0b, secondary=0c, subordinate=0d, sec-latency=176
	Memory window 0: d0000000-d3fff000 (prefetchable)
	Memory window 1: b8000000-bbfff000
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

0b:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
	Subsystem: Intel Corporation Unknown device 2712
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (750ns min, 6000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at b4001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>


---

### Post by HolyJoe on 2007-06-08
```
dmesg
``` output is:
> [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed May 23 01:46:23 UTC 2007 (Ubuntu 2.6.20-16.28-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d2000 size: 0000000000002000 end: 00000000000d4000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fdd0000 end: 000000003fed0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fed0000 size: 0000000000015000 end: 000000003fee5000 type: 3
[    0.000000] copy_e820_map() start: 000000003fee5000 size: 000000000001b000 end: 000000003ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000003ff00000 size: 0000000000100000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0008000 size: 0000000000004000 end: 00000000f000c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fed0000 (usable)
[    0.000000]  BIOS-e820: 000000003fed0000 - 000000003fee5000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fee5000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 261840) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261840
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261840
[    0.000000] On node 0 totalpages: 261840
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32211 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f6c00
[    0.000000] ACPI: XSDT (v001 IBM    TP-1Y    0x00001290  LTP 0x00000000) @ 0x3fed6fe7
[    0.000000] ACPI: FADT (v003 IBM    TP-1Y    0x00001290 IBM  0x00000001) @ 0x3fed7100
[    0.000000] ACPI: SSDT (v001 IBM    TP-1Y    0x00001290 MSFT 0x0100000e) @ 0x3fed72b4
[    0.000000] ACPI: ECDT (v001 IBM    TP-1Y    0x00001290 IBM  0x00000001) @ 0x3fee4dfc
[    0.000000] ACPI: TCPA (v001 IBM    TP-1Y    0x00001290 PTL  0x00000001) @ 0x3fee4e4e
[    0.000000] ACPI: MADT (v001 IBM    TP-1Y    0x00001290 IBM  0x00000001) @ 0x3fee4e80
[    0.000000] ACPI: MCFG (v001 IBM    TP-1Y    0x00001290 IBM  0x00000001) @ 0x3fee4eda
[    0.000000] ACPI: BOOT (v001 IBM    TP-1Y    0x00001290  LTP 0x00000001) @ 0x3fee4fd8
[    0.000000] ACPI: DSDT (v001 IBM    TP-1Y    0x00001290 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 798.113 MHz processor.
[    2.775109] Built 1 zonelists.  Total pages: 259795
[    2.775116] Kernel command line: root=UUID=814471c6-bd31-4f3a-9dec-c12858f8125e ro quiet splash
[    2.775439] mapped APIC to ffffd000 (fee00000)
[    2.775444] mapped IOAPIC to ffffc000 (fec00000)
[    2.775449] Enabling fast FPU save and restore... done.
[    2.775455] Enabling unmasked SIMD FPU exception support... done.
[    2.775468] Initializing CPU#0
[    2.775548] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    2.776863] Console: colour VGA+ 80x25
[    2.777297] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    2.778007] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    2.838135] Memory: 1027160k/1047360k available (1992k kernel code, 19464k reserved, 896k data, 328k init, 129856k highmem)
[    2.838155] virtual kernel memory layout:
[    2.838157]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    2.838160]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    2.838163]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    2.838165]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    2.838168]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    2.838171]       .data : 0xc02f2354 - 0xc03d26d4   ( 896 kB)
[    2.838173]       .text : 0xc0100000 - 0xc02f2354   (1992 kB)
[    2.838181] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    2.915551] Calibrating delay using timer specific routine.. 1598.11 BogoMIPS (lpj=3196236)
[    2.915623] Security Framework v1.0.0 initialized
[    2.915633] SELinux:  Disabled at boot.
[    2.915663] Mount-cache hash table entries: 512
[    2.915887] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[    2.915907] CPU: L1 I cache: 32K, L1 D cache: 32K
[    2.915913] CPU: L2 cache: 2048K
[    2.915918] CPU: After all inits, caps: afe9fbff 00000000 00000000 00002040 00000180 00000000 00000000
[    2.915935] Compat vDSO mapped to ffffe000.
[    2.915942] Remapping vsyscall page to ffffe000
[    2.915960] Checking 'hlt' instruction... OK.
[    2.931722] SMP alternatives: switching to UP code
[    2.932021] Freeing SMP alternatives: 11k freed
[    2.932348] Early unpacking initramfs... done
[    3.643717] ACPI: Core revision 20060707
[    3.644055] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    3.667020] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    3.667059] Total of 1 processors activated (1598.11 BogoMIPS).
[    3.667256] ENABLING IO-APIC IRQs
[    3.667483] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    3.811572] Brought up 1 CPUs
[    3.811976] Booting paravirtualized kernel on bare hardware
[    3.812080] Time: 22:55:50  Date: 05/08/107
[    3.812122] NET: Registered protocol family 16
[    3.812244] EISA bus registered
[    3.812251] ACPI: bus type pci registered
[    3.812361] PCI: PCI BIOS revision 2.10 entry at 0xfd8f7, last bus=14
[    3.812366] PCI: Using configuration type 1
[    3.812369] Setting up standard PCI resources
[    3.835092] ACPI: Interpreter enabled
[    3.835097] ACPI: Using IOAPIC for interrupt routing
[    3.836748] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    3.837980] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    3.839211] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    3.840465] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    3.841693] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    3.842920] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    3.844161] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    3.845389] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    3.846145] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    3.846152] PCI: Probing PCI hardware (bus 00)
[    3.849454] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    3.849462] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    3.849718] Boot video device is 0000:01:00.0
[    3.850360] PCI: Transparent bridge - 0000:00:1e.0
[    3.850523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    3.861049] ACPI: Power Resource [PUBS] (on)
[    3.862721] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    3.863432] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    3.863920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    3.864428] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    3.868913] Linux Plug and Play Support v0.97 (c) Adam Belay
[    3.868932] pnp: PnP ACPI init
[    3.877638] pnp: PnP ACPI: found 13 devices
[    3.877645] PnPBIOS: Disabled by ACPI PNP
[    3.877713] PCI: Using ACPI for IRQ routing
[    3.877719] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    3.909344] NET: Registered protocol family 8
[    3.909348] NET: Registered protocol family 20
[    3.910755] PCI: Bridge: 0000:00:01.0
[    3.910760]   IO window: 3000-3fff
[    3.910766]   MEM window: b0100000-b01fffff
[    3.910772]   PREFETCH window: c0000000-c7ffffff
[    3.910778] PCI: Bridge: 0000:00:1c.0
[    3.910782]   IO window: disabled.
[    3.910790]   MEM window: b0200000-b02fffff
[    3.910796]   PREFETCH window: disabled.
[    3.910804] PCI: Bridge: 0000:00:1c.2
[    3.910810]   IO window: 4000-4fff
[    3.910818]   MEM window: b2000000-b3ffffff
[    3.910826]   PREFETCH window: c8000000-c80fffff
[    3.910838] PCI: Bus 12, cardbus bridge: 0000:0b:00.0
[    3.910842]   IO window: 00005000-000050ff
[    3.910850]   IO window: 00005400-000054ff
[    3.910859]   PREFETCH window: d0000000-d3ffffff
[    3.910867]   MEM window: b8000000-bbffffff
[    3.910874] PCI: Bridge: 0000:00:1e.0
[    3.910880]   IO window: 5000-8fff
[    3.910888]   MEM window: b4000000-bfffffff
[    3.910896]   PREFETCH window: d0000000-d7ffffff
[    3.910918] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.910927] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    3.910955] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 17
[    3.910965] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    3.910993] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 18
[    3.911003] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    3.911020] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    3.911041] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.911078] NET: Registered protocol family 2
[    3.943598] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    3.943768] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    3.945260] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    3.946012] TCP: Hash tables configured (established 131072 bind 65536)
[    3.946017] TCP reno registered
[    3.955740] checking if image is initramfs... it is
[    5.317666] Freeing initrd memory: 6774k freed
[    5.317960] Simple Boot Flag at 0x35 set to 0x1
[    5.318308] audit: initializing netlink socket (disabled)
[    5.318327] audit(1181343351.616:1): initialized
[    5.318450] highmem bounce pool size: 64 pages
[    5.318549] VFS: Disk quotas dquot_6.5.1
[    5.318579] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.318657] io scheduler noop registered
[    5.318663] io scheduler anticipatory registered
[    5.318667] io scheduler deadline registered
[    5.318683] io scheduler cfq registered (default)
[    5.319018] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    5.319062] assign_interrupt_mode Found MSI capability
[    5.319068] Allocate Port Service[0000:00:01.0:pcie00]
[    5.319196] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    5.319258] assign_interrupt_mode Found MSI capability
[    5.319263] Allocate Port Service[0000:00:1c.0:pcie00]
[    5.319324] Allocate Port Service[0000:00:1c.0:pcie02]
[    5.319495] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    5.319557] assign_interrupt_mode Found MSI capability
[    5.319562] Allocate Port Service[0000:00:1c.2:pcie00]
[    5.319622] Allocate Port Service[0000:00:1c.2:pcie02]
[    5.319870] isapnp: Scanning for PnP cards...
[    5.675197] isapnp: No Plug & Play device found
[    5.716864] Real Time Clock Driver v1.12ac
[    5.716955] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    5.717232] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    5.719024] pnp: Device 00:09 activated.
[    5.719235] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    5.719617] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 23 (level, low) -> IRQ 19
[    5.719630] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[    5.719739] mice: PS/2 mouse device common for all mice
[    5.720665] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    5.721030] input: Macintosh mouse button emulation as /class/input/input0
[    5.721090] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    5.721097] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    5.721415] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    5.729119] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.729126] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.729307] EISA: Probing bus 0 at eisa.0
[    5.729318] Cannot allocate resource for EISA slot 1
[    5.729324] Cannot allocate resource for EISA slot 2
[    5.729329] Cannot allocate resource for EISA slot 3
[    5.729334] Cannot allocate resource for EISA slot 4
[    5.729338] Cannot allocate resource for EISA slot 5
[    5.729343] Cannot allocate resource for EISA slot 6
[    5.729348] Cannot allocate resource for EISA slot 7
[    5.729353] Cannot allocate resource for EISA slot 8
[    5.729357] EISA: Detected 0 cards.
[    5.759520] TCP cubic registered
[    5.759534] NET: Registered protocol family 1
[    5.759568] Using IPI No-Shortcut mode
[    5.759670] ACPI: (supports S0 S3 S4 S5)
[    5.759755]   Magic number: 11:824:956
[    5.759826]   hash matches device ptyzd
[    5.760146] Freeing unused kernel memory: 328k freed
[    5.762285] input: AT Translated Set 2 keyboard as /class/input/input1
[    5.763435] Time: tsc clocksource has been installed.
[    7.240583] Capability LSM initialized
[    7.315344] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    7.315355] ACPI: Processor [CPU] (supports 8 throttling states)
[    7.318383] ACPI: Thermal Zone [THM0] (35 C)
[    8.027058] usbcore: registered new interface driver usbfs
[    8.027093] usbcore: registered new interface driver hub
[    8.027128] usbcore: registered new device driver usb
[    8.028741] USB Universal Host Controller Interface driver v3.0
[    8.028800] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.028816] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    8.028824] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    8.029010] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    8.029049] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[    8.029209] usb usb1: configuration #1 chosen from 1 choice
[    8.029250] hub 1-0:1.0: USB hub found
[    8.029260] hub 1-0:1.0: 2 ports detected
[    8.131520] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 20
[    8.131539] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    8.131546] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    8.131583] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    8.131623] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[    8.131781] usb usb2: configuration #1 chosen from 1 choice
[    8.131832] hub 2-0:1.0: USB hub found
[    8.131842] hub 2-0:1.0: 2 ports detected
[    8.228266] SCSI subsystem initialized
[    8.238720] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[    8.238737] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    8.238745] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    8.238783] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    8.238820] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001840
[    8.238984] usb usb3: configuration #1 chosen from 1 choice
[    8.239028] hub 3-0:1.0: USB hub found
[    8.239038] hub 3-0:1.0: 2 ports detected
[    8.239192] libata version 2.20 loaded.
[    8.339504] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 22
[    8.339523] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    8.339530] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    8.339567] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    8.339606] uhci_hcd 0000:00:1d.3: irq 22, io base 0x00001860
[    8.339762] usb usb4: configuration #1 chosen from 1 choice
[    8.339805] hub 4-0:1.0: USB hub found
[    8.339819] hub 4-0:1.0: 2 ports detected
[    8.445128] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 22
[    8.445148] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    8.445155] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    8.445198] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    8.445251] ehci_hcd 0000:00:1d.7: debug port 1
[    8.445260] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    8.445273] ehci_hcd 0000:00:1d.7: irq 22, io mem 0xb0000000
[    8.449166] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    8.449300] usb usb5: configuration #1 chosen from 1 choice
[    8.449346] hub 5-0:1.0: USB hub found
[    8.449357] hub 5-0:1.0: 8 ports detected
[    8.475346] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    8.551774] tg3.c:v3.72 (January 8, 2007)
[    8.551804] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.551822] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    8.594560] eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:16:41:15:9f:f5
[    8.594574] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[    8.594581] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    8.594862] ata_piix 0000:00:1f.2: version 2.10ac1
[    8.594871] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    5.852000] Time: acpi_pm clocksource has been installed.
[    5.864000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.864000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118c0 irq 14
[    5.864000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118c8 irq 15
[    5.864000] scsi0 : ata_piix
[    6.028000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    6.028000] ata1.00: ATA-6: HTS541060G9AT00, MB3IA60A, max UDMA/100
[    6.028000] ata1.00: 117210240 sectors, multi 16: LBA 
[    6.028000] ata1.00: applying bridge limits
[    6.036000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    6.036000] ata1.00: configured for UDMA/100
[    6.036000] scsi1 : ata_piix
[    6.356000] ata2.00: ATAPI, max UDMA/33
[    6.412000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    6.520000] ata2.00: configured for UDMA/33
[    6.520000] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3I PQ: 0 ANSI: 5
[    6.524000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4242N 0J05 PQ: 0 ANSI: 5
[    6.560000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    6.560000] sda: Write Protect is off
[    6.560000] sda: Mode Sense: 00 3a 00 00
[    6.560000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.560000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    6.560000] sda: Write Protect is off
[    6.560000] sda: Mode Sense: 00 3a 00 00
[    6.560000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.560000]  sda: sda1 sda2 <<6>usb 2-2: configuration #1 chosen from 1 choice
[    6.596000]  sda5 sda6 sda7 >
[    6.636000] sd 0:0:0:0: Attached scsi disk sda
[    6.644000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.644000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    6.664000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    6.664000] Uniform CD-ROM driver Revision: 3.20
[    6.664000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.824000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    6.912000] Attempting manual resume
[    6.912000] swsusp: Resume From Partition 8:7
[    6.912000] PM: Checking swsusp image.
[    6.912000] PM: Resume from disk failed.
[    6.956000] kjournald starting.  Commit interval 5 seconds
[    6.956000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.000000] usb 3-2: configuration #1 chosen from 1 choice
[    7.004000] usbcore: registered new interface driver hiddev
[    7.016000] input: USB Mouse as /class/input/input2
[    7.016000] input: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:1d.1-2
[    7.016000] usbcore: registered new interface driver usbhid
[    7.016000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   20.200000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.224000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.196000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.648000] agpgart: Detected an Intel 915GM Chipset.
[   21.672000] agpgart: AGP aperture is 256M @ 0x0
[   22.144000] iTCO_vendor_support: vendor-support=0
[   22.160000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   22.160000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   22.160000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   22.184000] intel_rng: FWH not detected
[   22.284000] input: PC Speaker as /class/input/input3
[   23.288000] Yenta: CardBus bridge found at 0000:0b:00.0 [1014:056c]
[   23.336000] ieee80211_crypt: registered algorithm 'NULL'
[   23.340000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   23.340000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   23.400000] parport: PnPBIOS parport detected.
[   23.400000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   23.416000] Yenta: ISA IRQ mask 0x0c38, PCI irq 16
[   23.416000] Socket status: 30000006
[   23.416000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x8fff
[   23.416000] cs: IO port probe 0x5000-0x8fff: clean.
[   23.416000] pcmcia: parent PCI bridge Memory window: 0xb4000000 - 0xbfffffff
[   23.416000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd7ffffff
[   23.468000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   23.468000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.468000] ACPI: PCI Interrupt 0000:0b:02.0[A] -> GSI 21 (level, low) -> IRQ 23
[   23.468000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.588000] irda_init()
[   23.588000] NET: Registered protocol family 23
[   23.832000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   23.832000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 22 (level, low) -> IRQ 18
[   23.832000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   23.872000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   23.888000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[   23.892000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   23.892000] nsc-ircc, chip->init
[   23.892000] nsc-ircc, Found chip at base=0x02e
[   23.892000] nsc-ircc, driver loaded (Dag Brattli)
[   23.892000] nsc_ircc_open(), can't get iobase of 0x2f8
[   23.892000] nsc-ircc, Found chip at base=0x02e
[   23.892000] nsc-ircc, driver loaded (Dag Brattli)
[   23.892000] nsc_ircc_open(), can't get iobase of 0x2f8
[   23.892000] pnp: Device 00:0b disabled.
[   23.988000] cs: IO port probe 0x100-0x3af: clean.
[   23.992000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   23.992000] cs: IO port probe 0x820-0x8ff: clean.
[   23.992000] cs: IO port probe 0xc00-0xcf7: clean.
[   23.992000] cs: IO port probe 0xa00-0xaff: clean.
[   24.652000] intel8x0_measure_ac97_clock: measured 55421 usecs
[   24.652000] intel8x0: clocking to 48000
[   24.856000] fuse init (API version 7.8)
[   24.900000] lp0: using parport0 (interrupt-driven).
[   24.944000] Adding 883532k swap on /dev/disk/by-uuid/93d31811-691e-4ff8-867e-ce9a3aa303c4.  Priority:-1 extents:1 across:883532k
[   25.108000] EXT3 FS on sda6, internal journal
[   25.408000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   25.492000] NTFS volume version 3.0.
[   25.528000] NTFS volume version 3.1.
[   26.472000] input: Power Button (FF) as /class/input/input5
[   26.476000] ACPI: Power Button (FF) [PWRF]
[   26.560000] input: Lid Switch as /class/input/input6
[   26.560000] ACPI: Lid Switch [LID]
[   26.600000] input: Sleep Button (CM) as /class/input/input7
[   26.600000] ACPI: Sleep Button (CM) [SLPB]
[   26.680000] ACPI: AC Adapter [AC] (on-line)
[   26.788000] Using specific hotkey driver
[   26.896000] ibm_acpi: ThinkPad EC firmware 1YHT29WW-1.06
[   26.896000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   26.896000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   26.908000] ibm_acpi: fan_init: initial fan status is unknown, assuming it is in auto mode
[   26.940000] ACPI: Battery Slot [BAT0] (battery present)
[   26.968000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   27.012000] ACPI: ACPI Dock Station Driver 
[   27.196000] pcc_acpi: loading...
[   28.376000] ttyS1: LSR safety check engaged!
[   28.880000] PM: Writing back config space on device 0000:02:00.0 at offset c (was d7ef0000, writing 0)
[   30.824000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   30.828000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   30.828000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   30.868000] NET: Registered protocol family 10
[   30.868000] lo: Disabled Privacy Extensions
[   30.868000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.868000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   30.888000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.056000] ppdev: user-space parallel port driver
[   33.392000] [fglrx] total      GART = 130023424
[   33.392000] [fglrx] free       GART = 114032640
[   33.392000] [fglrx] max single GART = 114032640
[   33.392000] [fglrx] total      LFB  = 66977792
[   33.392000] [fglrx] free       LFB  = 55439360
[   33.392000] [fglrx] max single LFB  = 55439360
[   33.392000] [fglrx] total      Inv  = 0
[   33.392000] [fglrx] free       Inv  = 0
[   33.392000] [fglrx] max single Inv  = 0
[   33.392000] [fglrx] total      TIM  = 0
[   34.172000] IBM machine detected. Enabling interrupts during APM calls.
[   34.172000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   34.172000] apm: overridden by ACPI.
[   34.648000] Non-volatile memory driver v1.2
[   34.704000] input: /usr/sbin/thinkpad-keys as /class/input/input8
[   34.868000] Bluetooth: Core ver 2.11
[   34.868000] NET: Registered protocol family 31
[   34.868000] Bluetooth: HCI device and connection manager initialized
[   34.868000] Bluetooth: HCI socket layer initialized
[   34.888000] Bluetooth: L2CAP ver 2.8
[   34.888000] Bluetooth: L2CAP socket layer initialized
[   35.068000] Bluetooth: RFCOMM socket layer initialized
[   35.068000] Bluetooth: RFCOMM TTY layer initialized
[   35.068000] Bluetooth: RFCOMM ver 1.8
[   57.084000] NET: Registered protocol family 17
[   57.108000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   57.464000] ieee80211_crypt: registered algorithm 'CCMP'
[   57.796000] ieee80211_crypt: registered algorithm 'TKIP'
[   64.340000] CCMP: replay detected: STA=00:19:5b:db:8a:1a previous PN 000000000000 received PN 000000000000
[   72.740000] eth1: no IPv6 routers present

---

### Post by HolyJoe on 2007-06-08
my ```
lshal
``` output part-1 is:
> Dumping 109 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.bus = 'unknown'  (string)
  info.callouts.add = {'hal-storage-cleanup-all-mountpoints'} (string list)
  info.capabilities = {'cpufreq_control'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'b'} (string list)
  power_management.acpi.linux.version = '20060707'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.can_suspend_to_disk = true  (bool)
  power_management.can_suspend_to_ram = true  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.quirk.s3_bios = true  (bool)
  power_management.quirk.s3_mode = true  (bool)
  power_management.quirk.vbe_post = true  (bool)
  power_management.quirk.vbestate_restore = true  (bool)
  power_management.type = 'acpi'  (string)
  smbios.bios.release_date = '08/21/2006'  (string)
  smbios.bios.vendor = 'IBM'  (string)
  smbios.bios.version = '1YET65WW (1.29 )'  (string)
  smbios.chassis.manufacturer = 'IBM'  (string)
  smbios.chassis.type = 'Notebook'  (string)
  smbios.system.manufacturer = 'IBM'  (string)
  smbios.system.product = '2668AZ3'  (string)
  smbios.system.serial = 'L3XNWXT'  (string)
  smbios.system.uuid = 'E8077E81-4806-11CB-9B09-9CF4A56E1AD0'  (string)
  smbios.system.version = 'ThinkPad T43'  (string)
  system.chassis.manufacturer = 'IBM'  (string)
  system.chassis.type = 'Notebook'  (string)
  system.firmware.release_date = '08/21/2006'  (string)
  system.firmware.vendor = 'IBM'  (string)
  system.firmware.version = '1YET65WW (1.29 )'  (string)
  system.formfactor = 'laptop'  (string)
  system.hardware.product = '2668AZ3'  (string)
  system.hardware.serial = 'L3XNWXT'  (string)
  system.hardware.uuid = 'E8077E81-4806-11CB-9B09-9CF4A56E1AD0'  (string)
  system.hardware.vendor = 'IBM'  (string)
  system.hardware.version = 'ThinkPad T43'  (string)
  system.kernel.machine = 'i686'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.20-16-generic'  (string)
  system.product = '2668AZ3 ThinkPad T43'  (string)
  system.vendor = 'IBM'  (string)

---

### Post by HolyJoe on 2007-06-08
my ```
lshal
``` output part-2 is:
> udi = '/org/freedesktop/Hal/devices/platform_bluetooth'
  info.bus = 'platform'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (bluetooth)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_bluetooth'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/bluetooth'  (string)
  platform.id = 'bluetooth'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'
  info.addons = {'hald-addon-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '/usr/sbin/thinkpad-keys'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'  (string)
  input.device = '/dev/input/event8'  (string)
  input.product = '/usr/sbin/thinkpad-keys'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input8/event8'  (string)

udi = '/org/freedesktop/Hal/devices/acpi_AC'
  ac_adapter.present = true  (bool)
  info.capabilities = {'ac_adapter'} (string list)
  info.category = 'ac_adapter'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AC Adapter'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_AC'  (string)
  linux.acpi_path = '/proc/acpi/ac_adapter/AC'  (string)
  linux.acpi_type = 3  (0x3)  (int)
  linux.hotplug_type = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_CPU'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Intel(R) Pentium(R) M processor 1.86GHz'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = true  (bool)
  processor.number = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_BAT0'
  battery.alarm.design = 2592  (0xa20)  (int)
  battery.alarm.unit = 'mWh'  (string)
  battery.charge_level.capacity_state = 'ok'  (string)
  battery.charge_level.current = 50600  (0xc5a8)  (int)
  battery.charge_level.design = 51840  (0xca80)  (int)
  battery.charge_level.granularity_1 = 1  (0x1)  (int)
  battery.charge_level.granularity_2 = 1  (0x1)  (int)
  battery.charge_level.last_full = 51840  (0xca80)  (int)
  battery.charge_level.low = 200  (0xc8)  (int)
  battery.charge_level.percentage = 97  (0x61)  (int)
  battery.charge_level.rate = 0  (0x0)  (int)
  battery.charge_level.unit = 'mWh'  (string)
  battery.charge_level.warning = 2592  (0xa20)  (int)
  battery.is_rechargeable = true  (bool)
  battery.model = 'IBM-92P1089'  (string)
  battery.present = true  (bool)
  battery.rechargeable.is_charging = false  (bool)
  battery.rechargeable.is_discharging = false  (bool)
  battery.reporting.current = 50600  (0xc5a8)  (int)
  battery.reporting.design = 51840  (0xca80)  (int)
  battery.reporting.granularity_1 = 1  (0x1)  (int)
  battery.reporting.granularity_2 = 1  (0x1)  (int)
  battery.reporting.last_full = 51840  (0xca80)  (int)
  battery.reporting.low = 200  (0xc8)  (int)
  battery.reporting.rate = 0  (0x0)  (int)
  battery.reporting.technology = 'LION'  (string)
  battery.reporting.unit = 'mWh'  (string)
  battery.reporting.warning = 2592  (0xa20)  (int)
  battery.serial = '8871'  (string)
  battery.technology = 'lithium-ion'  (string)
  battery.type = 'primary'  (string)
  battery.vendor = 'SONY'  (string)
  battery.voltage.current = 12343  (0x3037)  (int)
  battery.voltage.design = 10800  (0x2a30)  (int)
  battery.voltage.unit = 'mV'  (string)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  info.is_recalled = true  (bool)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Battery Bay'  (string)
  info.recall.vendor = 'LENOVO'  (string)
  info.recall.website_url = 'http://www.lenovo.com/batteryprogram'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_BAT0'  (string)
  linux.acpi_path = '/proc/acpi/battery/BAT0'  (string)
  linux.acpi_type = 0  (0x0)  (int)
  linux.hotplug_type = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  alsa.device_file = '/dev/snd/timer'  (string)
  alsa.type = 'timer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'  (string)
  linux.device_file = '/dev/snd/timer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/timer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'  (string)
  linux.device_file = '/dev/sequencer2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/sequencer2'  (string)
  oss.device_file = '/dev/sequencer2'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'  (string)
  linux.device_file = '/dev/sequencer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/sequencer'  (string)
  oss.device_file = '/dev/sequencer'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  alsa.device_file = '/dev/snd/seq'  (string)
  alsa.type = 'sequencer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'  (string)
  linux.device_file = '/dev/snd/seq'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/seq'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'
  button.has_state = false  (bool)
  button.type = 'sleep'  (string)
  info.addons = {'hald-addon-keyboard'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Sleep Button (CM)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'  (string)
  input.device = '/dev/input/event7'  (string)
  input.product = 'Sleep Button (CM)'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input7/event7'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  button.has_state = true  (bool)
  button.state.value = false  (bool)
  button.type = 'lid'  (string)
  info.addons = {'hald-addon-keyboard'} (string list)
  info.capabilities = {'input', 'input.switch', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Lid Switch'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event6'  (string)
  input.product = 'Lid Switch'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input6/event6'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons = {'hald-addon-keyboard'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button (FF)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event5'  (string)
  input.product = 'Power Button (FF)'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input5/event5'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.brightness_in_hardware = true  (bool)
  laptop_panel.num_levels = 8  (0x8)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/class/backlight/ibm'  (string)
  org.freedesktop.Hal.Device.LaptopPanel.method_argnames = {'brightness_value', ''} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_execpaths = {'hal-system-lcd-set-brightness', 'hal-system-lcd-get-brightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_names = {'SetBrightness', 'GetBrightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_signatures = {'i', ''} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_NSC1100'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (NSC1100)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_NSC1100'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'  (string)
  pnp.id = 'NSC1100'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_IBM0071'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'IBM infrared communications device'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_IBM0071'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'  (string)
  pnp.description = 'IBM infrared communications device'  (string)
  pnp.id = 'IBM0071'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0400'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'parport_pc'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Standard LPT printer port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0400'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'  (string)
  pnp.description = 'Standard LPT printer port'  (string)
  pnp.id = 'PNP0400'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/class/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.physical_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_IBM0057'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'i8042 aux'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (IBM0057)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_IBM0057'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.id = 'IBM0057'  (string)


---

### Post by HolyJoe on 2007-06-08
my ```
lshal
``` output part-3 is:
> udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'i8042 kbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.id = 'PNP0303'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT Real-Time Clock'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:06'  (string)
  pnp.description = 'AT Real-Time Clock'  (string)
  pnp.id = 'PNP0b00'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.description = 'Math Coprocessor'  (string)
  pnp.id = 'PNP0c04'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
  pnp.description = 'AT-style speaker sound'  (string)
  pnp.id = 'PNP0800'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:03'  (string)
  pnp.description = 'AT DMA Controller'  (string)
  pnp.id = 'PNP0200'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0a08)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:01'  (string)
  pnp.id = 'PNP0a08'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'System Board'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:00'  (string)
  pnp.description = 'System Board'  (string)
  pnp.id = 'PNP0c01'  (string)

udi = '/org/freedesktop/Hal/devices/platform_vesafb_0'
  info.bus = 'platform'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (vesafb.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_vesafb_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/vesafb.0'  (string)
  platform.id = 'vesafb.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.bus = 'platform'  (string)
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_1'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_1'  (string)
  linux.device_file = '/dev/ttyS1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/class/tty/ttyS1'  (string)
  serial.device = '/dev/ttyS1'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  serial.physical_device = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  serial.port = 1  (0x1)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  info.bus = 'platform'  (string)
  info.linux.driver = 'pcspkr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr'  (string)
  platform.id = 'pcspkr'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  info.product = 'PC Speaker'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  input.physical_device = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  input.product = 'PC Speaker'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'
  info.bus = 'platform'  (string)
  info.linux.driver = 'iTCO_wdt'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (iTCO_wdt)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/iTCO_wdt'  (string)
  platform.id = 'iTCO_wdt'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.bus = 'platform'  (string)
  info.linux.driver = 'i8042'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.bus = 'serio'  (string)
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'TPPS/2 IBM TrackPoint'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.physical_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'TPPS/2 IBM TrackPoint'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input4/event4'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.bus = 'serio'  (string)
  info.linux.driver = 'atkbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
  serio.id = 'serio0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.addons = {'hald-addon-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  info.product = 'AT Translated Set 2 keyboard'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'  (string)
  input.device = '/dev/input/event1'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.physical_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.product = 'AT Translated Set 2 keyboard'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  info.bus = 'platform'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (eisa.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_eisa_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/eisa.0'  (string)
  platform.id = 'eisa.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_dock_0'
  info.bus = 'platform'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (dock.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_dock_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/dock.0'  (string)
  platform.id = 'dock.0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266a'
  info.bus = 'pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266a'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 5  (0x5)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller'  (string)
  pci.product_id = 9834  (0x266a)  (int)
  pci.subsys_product_id = 1387  (0x56b)  (int)
  pci.subsys_vendor = 'IBM'  (string)
  pci.subsys_vendor_id = 4116  (0x1014)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2653'
  info.bus = 'pci'  (string)
  info.linux.driver = 'ata_piix'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FBM (ICH6M) SATA Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2653'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 128  (0x80)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.product = '82801FBM (ICH6M) SATA Controller'  (string)
  pci.product_id = 9811  (0x2653)  (int)
  pci.subsys_product_id = 1386  (0x56a)  (int)
  pci.subsys_vendor = 'IBM'  (string)
  pci.subsys_vendor_id = 4116  (0x1014)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2653'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0_scsi_device_lun0'
  info.bus = 'scsi'  (string)
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 1  (0x1)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'RW/DVD GCC-4242N'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'HL-DT-ST'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4242N'
  block.device = '/dev/scd0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4242N'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'RW/DVD GCC-4242N'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_RW/DVD_GCC_4242N'  (string)
  info.vendor = 'HL-DT-ST'  (string)
  linux.fstab.mountpoint = '/media/cdrom0'  (string)
  linux.fstab.options = 'user,noauto'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'scsi'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = false  (bool)
  storage.cdrom.dvdplusrdl = false  (bool)
  storage.cdrom.dvdplusrw = false  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = false  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrw = false  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 4234  (0x108a)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 4234  (0x108a)  (int)
  storage.cdrom.write_speeds = {'4234', '2822', '1764', '706'} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = '0J05'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'RW/DVD GCC-4242N'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0_scsi_device_lun0'  (string)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0_scsi_device_lun0'  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'HL-DT-ST'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_0_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/class/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2653'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_scsi_device_lun0'
  info.bus = 'scsi'  (string)
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 0  (0x0)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'HTS541060G9AT00'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_scsi_device_lun0'  (string)
  info.product = 'HTS541060G9AT00'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'scsi'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = 'MB3I'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'HTS541060G9AT00'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_scsi_device_lun0'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_scsi_device_lun0'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 60011642880  (0xdf8f90000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = '1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  storage.size = 60011642880  (0xdf8f90000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_93d31811_691e_4ff8_867e_ce9a3aa303c4'
  block.device = '/dev/sda7'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 7  (0x7)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.product = 'Volume (swap)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_93d31811_691e_4ff8_867e_ce9a3aa303c4'  (string)
  linux.fstab.mountpoint = 'none'  (string)
  linux.fstab.options = 'sw'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda/sda7'  (string)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'swap'  (string)
  volume.fsusage = 'other'  (string)
  volume.fsversion = '2'  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 1767087  (0x1af6af)  (int)
  volume.partition.media_size = 60011642880  (0xdf8f90000)  (uint64)
  volume.partition.number = 7  (0x7)  (int)
  volume.partition.start = 59106894336  (0xdc30ba200)  (uint64)
  volume.size = 904748544  (0x35ed5e00)  (uint64)
  volume.uuid = '93d31811-691e-4ff8-867e-ce9a3aa303c4'  (string)


---

### Post by HolyJoe on 2007-06-08
my ```
lshal
``` output part-4 is:
> 
udi = '/org/freedesktop/Hal/devices/volume_uuid_814471c6_bd31_4f3a_9dec_c12858f8125e'
  block.device = '/dev/sda6'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 6  (0x6)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.product = 'Volume (ext3)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_814471c6_bd31_4f3a_9dec_c12858f8125e'  (string)
  linux.fstab.mountpoint = '/'  (string)
  linux.fstab.options = 'defaults,errors=remount-ro'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda/sda6'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext3'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'acl', 'user_xattr', 'data='} (string list)
  volume.mount_point = '/'  (string)
  volume.num_blocks = 27326502  (0x1a0f826)  (int)
  volume.partition.media_size = 60011642880  (0xdf8f90000)  (uint64)
  volume.partition.number = 6  (0x6)  (int)
  volume.partition.start = 45115693056  (0xa811ad800)  (uint64)
  volume.size = 13991169024  (0x341f04c00)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '814471c6-bd31-4f3a-9dec-c12858f8125e'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_48DE09B5AA58A9A4'
  block.device = '/dev/sda5'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 5  (0x5)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.product = 'Local Disk'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_48DE09B5AA58A9A4'  (string)
  linux.fstab.mountpoint = '/media/sda5'  (string)
  linux.fstab.options = 'defaults,nls=utf8,umask=007,gid=46'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda/sda5'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '3.1'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = true  (bool)
  volume.is_partition = true  (bool)
  volume.label = 'Local Disk'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'locale=', 'utf8'} (string list)
  volume.mount_point = '/media/sda5'  (string)
  volume.num_blocks = 47144097  (0x2cf5ca1)  (int)
  volume.partition.media_size = 60011642880  (0xdf8f90000)  (uint64)
  volume.partition.number = 5  (0x5)  (int)
  volume.partition.start = 20971593216  (0x4e2011e00)  (uint64)
  volume.size = 24137777664  (0x59eb94200)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '48DE09B5AA58A9A4'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  block.device = '/dev/sda2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.product = 'Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda/sda2'  (string)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = ''  (string)
  volume.fsusage = ''  (string)
  volume.fsversion = ''  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 2  (0x2)  (int)
  volume.partition.media_size = 60011642880  (0xdf8f90000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.start = 20971592704  (0x4e2011c00)  (uint64)
  volume.size = 1024  (0x400)  (uint64)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_449C9DA49C9D9152'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_HTS541060G9AT00_MPB3LAXGGA31TG'  (string)
  info.product = 'Volume (ntfs)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_449C9DA49C9D9152'  (string)
  linux.fstab.mountpoint = '/media/sda1'  (string)
  linux.fstab.options = 'defaults,nls=utf8,umask=007,gid=46'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda/sda1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '3.0'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = true  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'locale=', 'utf8'} (string list)
  volume.mount_point = '/media/sda1'  (string)
  volume.num_blocks = 40960017  (0x2710011)  (int)
  volume.partition.flags = {'boot'} (string list)
  volume.partition.label = ''  (string)
  volume.partition.media_size = 60011642880  (0xdf8f90000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.partition.type = '0x07'  (string)
  volume.partition.uuid = ''  (string)
  volume.size = 20971528704  (0x4e2002200)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '449C9DA49C9D9152'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2653_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/class/scsi_generic/sg0'  (string)
  scsi_generic.device = '/dev/sg0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2641'
  info.bus = 'pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FBM (ICH6M) LPC Interface Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2641'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.product = '82801FBM (ICH6M) LPC Interface Bridge'  (string)
  pci.product_id = 9793  (0x2641)  (int)
  pci.subsys_product_id = 1384  (0x568)  (int)
  pci.subsys_vendor = 'IBM'  (string)
  pci.subsys_vendor_id = 4116  (0x1014)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_266d'
  info.bus = 'pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266d'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.3'  (string)
  pci.device_class = 7  (0x7)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.3'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller'  (string)
  pci.product_id = 9837  (0x266d)  (int)
  pci.subsys_product_id = 1398  (0x576)  (int)
  pci.subsys_vendor = 'IBM'  (string)
  pci.subsys_vendor_id = 4116  (0x1014)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e'
  info.bus = 'pci'  (string)
  info.linux.driver = 'Intel ICH'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.2'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.2'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller'  (string)
  pci.product_id = 9838  (0x266e)  (int)
  pci.subsys_product_id = 1383  (0x567)  (int)
  pci.subsys_vendor = 'IBM'  (string)
  pci.subsys_vendor_id = 4116  (0x1014)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_4'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 4  (0x4)  (int)
  alsa.device_file = '/dev/snd/pcmC0D4p'  (string)
  alsa.device_id = 'Intel ICH6 - IEC958'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'playback'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 - IEC958 ALSA Playback Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_4'  (string)
  linux.device_file = '/dev/snd/pcmC0D4p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D4p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_3'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 3  (0x3)  (int)
  alsa.device_file = '/dev/snd/pcmC0D3c'  (string)
  alsa.device_id = 'Intel ICH6 - ADC2'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 - ADC2 ALSA Capture Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_3'  (string)
  linux.device_file = '/dev/snd/pcmC0D3c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D3c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_2'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 2  (0x2)  (int)
  alsa.device_file = '/dev/snd/pcmC0D2c'  (string)
  alsa.device_id = 'Intel ICH6 - MIC2 ADC'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 - MIC2 ADC ALSA Capture Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_2'  (string)
  linux.device_file = '/dev/snd/pcmC0D2c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D2c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 1  (0x1)  (int)
  alsa.device_file = '/dev/snd/pcmC0D1c'  (string)
  alsa.device_id = 'Intel ICH6 - MIC ADC'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 - MIC ADC ALSA Capture Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_1'  (string)
  linux.device_file = '/dev/snd/pcmC0D1c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D1c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0p'  (string)
  alsa.device_id = 'Intel ICH6'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'playback'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 ALSA Playback Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D0p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0c'  (string)
  alsa.device_id = 'Intel ICH6'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 ALSA Capture Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D0c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_mixer__1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 OSS Control Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/mixer'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'Intel ICH6 with AD1981B'  (string)
  oss.device_file = '/dev/mixer'  (string)
  oss.device_id = 'Intel ICH6'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 OSS PCM Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'Intel ICH6 with AD1981B'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'Intel ICH6'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_control__1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'control'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 with AD1981B ALSA Control Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 OSS PCM Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'Intel ICH6 with AD1981B'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'Intel ICH6'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 OSS PCM Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_1'  (string)
  linux.device_file = '/dev/adsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/adsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'Intel ICH6 with AD1981B'  (string)
  oss.device = 1  (0x1)  (int)
  oss.device_file = '/dev/adsp'  (string)
  oss.device_id = 'Intel ICH6'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2448'
  info.bus = 'pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801 Mobile PCI Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.product = '82801 Mobile PCI Bridge'  (string)
  pci.product_id = 9288  (0x2448)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_4220'
  info.bus = 'pci'  (string)
  info.linux.driver = 'ipw2200'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'PRO/Wireless 2200BG Network Connection'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_4220'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:0b:02.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:0b:02.0'  (string)
  pci.product = 'PRO/Wireless 2200BG Network Connection'  (string)
  pci.product_id = 16928  (0x4220)  (int)
  pci.subsys_product_id = 10002  (0x2712)  (int)
  pci.subsys_vendor = 'Intel Corporation'  (string)
  pci.subsys_vendor_id = 32902  (0x8086)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_16_6f_1b_8f_a0'
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_4220'  (string)
  info.product = 'WLAN Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_16_6f_1b_8f_a0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/class/net/eth1'  (string)
  net.80211.mac_address = 96353357728  (0x166f1b8fa0)  (uint64)
  net.address = '00:16:6f:1b:8f:a0'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth1'  (string)
  net.linux.ifindex = 3  (0x3)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_8086_4220'  (string)
  net.physical_device = '/org/freedesktop/Hal/devices/pci_8086_4220'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1180_476'
  info.bus = 'pci'  (string)
  info.linux.driver = 'yenta_cardbus'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2448'  (string)
  info.product = 'RL5c476 II'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1180_476'  (string)
  info.vendor = 'Ricoh Co Ltd'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:0b:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 7  (0x7)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:0b:00.0'  (string)
  pci.product = 'RL5c476 II'  (string)
  pci.product_id = 1142  (0x476)  (int)
  pci.subsys_product_id = 1388  (0x56c)  (int)
  pci.subsys_vendor = 'IBM'  (string)
  pci.subsys_vendor_id = 4116  (0x1014)  (int)
  pci.vendor = 'Ricoh Co Ltd'  (string)
  pci.vendor_id = 4480  (0x1180)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_265c'
  info.bus = 'pci'  (string)
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_265c'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller'  (string)
  pci.product_id = 9820  (0x265c)  (int)
  pci.subsys_product_id = 1382  (0x566)  (int)
  pci.subsys_vendor = 'IBM'  (string)
  pci.subsys_vendor_id = 4116  (0x1014)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_265c'  (string)
  info.product = 'EHCI Host Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'  (string)
  info.vendor = 'Linux 2.6.20-16-generic ehci_hcd'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5'  (string)
  usb_device.bus_number = 5  (0x5)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 1  (0x1)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 8  (0x8)  (int)
  usb_device.product = 'EHCI Host Controller'  (string)
  usb_device.product_id = 0  (0x0)  (int)
  usb_device.serial = '0000:00:1d.7'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.speed_bcd = 294912  (0x48000)  (int)
  usb_device.vendor = 'Linux 2.6.20-16-generic ehci_hcd'  (string)
  usb_device.vendor_id = 0  (0x0)  (int)
  usb_device.version = 2.0 (2) (double)
  usb_device.version_bcd = 512  (0x200)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'  (string)
  linux.device_file = '/dev/bus/usb/005/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/class/usb_device/usbdev5.1'  (string)
  usbraw.device = '/dev/bus/usb/005/001'  (string)


---

