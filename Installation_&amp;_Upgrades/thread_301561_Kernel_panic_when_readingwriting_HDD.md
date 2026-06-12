---
title: "Kernel panic when reading/writing HDD"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by rdnk on 2006-11-17
Hello. I bought a new motherboard (Asrock K7NF2-Raid) and changed it to already working Ubuntu server. Everything seems to be working fine, except it throws a kernel panic or just hangs everytime I start to read/write to any of the hard disks. 

So far I've tried:
- another hdd
- another hdd cable
- knoppix (hangs there too)

I've also tried to disable onboard usb, sound, serialport and even underclock the processor. Below I'll post information regarding the system. I don't know where to look anymore, except that the mb might be broken. Where the problem could be?

**uname:**
```
Linux runonlaulaja 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686 GNU/Linux
```
[B]
lspci:[/B]
```

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
0000:00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
0000:00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
```

**dmesg:**
```
[42949372.960000] Linux version 2.6.15-23-server (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Tue May 23 15:10:35 UTC 2006
[42949372.960000] BIOS-provided physical RAM map:
[42949372.960000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[42949372.960000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[42949372.960000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[42949372.960000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[42949372.960000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[42949372.960000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[42949372.960000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[42949372.960000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[42949372.960000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[42949372.960000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[42949372.960000] 127MB HIGHMEM available.
[42949372.960000] 896MB LOWMEM available.
[42949372.960000] On node 0 totalpages: 262064
[42949372.960000]   DMA zone: 4096 pages, LIFO batch:0
[42949372.960000]   DMA32 zone: 0 pages, LIFO batch:0
[42949372.960000]   Normal zone: 225280 pages, LIFO batch:31
[42949372.960000]   HighMem zone: 32688 pages, LIFO batch:7
[42949372.960000] DMI 2.3 present.
[42949372.960000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f8ec0
[42949372.960000] ACPI: RSDT (v001 A M I  OEMRSDT  0x07000631 MSFT 0x00000097) @ 0x3ffb0000
[42949372.960000] ACPI: FADT (v002 A M I  OEMFACP  0x07000631 MSFT 0x00000097) @ 0x3ffb0200
[42949372.960000] ACPI: MADT (v001 A M I  OEMAPIC  0x07000631 MSFT 0x00000097) @ 0x3ffb0390
[42949372.960000] ACPI: OEMB (v001 A M I  NVD_CRB  0x07000631 MSFT 0x00000097) @ 0x3ffc0040
[42949372.960000] ACPI: DSDT (v001  K7NF2 K7NF2112 0x00000112 INTL 0x02002026) @ 0x00000000
[42949372.960000] ACPI: PM-Timer IO Port: 0x4008
[42949372.960000] ACPI: Local APIC address 0xfee00000
[42949372.960000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[42949372.960000] Processor #0 6:10 APIC version 16
[42949372.960000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[42949372.960000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[42949372.960000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[42949372.960000] ACPI: IRQ9 used by override.
[42949372.960000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[42949372.960000] Using ACPI (MADT) for SMP configuration information
[42949372.960000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[42949372.960000] Built 1 zonelists
[42949372.960000] Kernel command line: root=/dev/hda1 ro vga=791 quiet splash
[42949372.960000] mapped APIC to ffffd000 (fee00000)
[42949372.960000] mapped IOAPIC to ffffc000 (fec00000)
[42949372.960000] Initializing CPU#0
[42949372.960000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[42949372.960000] Detected 1300.001 MHz processor.
[42949372.960000] Using pmtmr for high-res timesource
[42949372.960000] Console: colour dummy device 80x25
[42949373.900000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[42949373.900000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[42949373.950000] Memory: 1027980k/1048256k available (2077k kernel code, 19560k reserved, 618k data, 332k init, 130752k highmem)
[42949373.950000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[42949374.100000] Calibrating delay using timer specific routine.. 2602.66 BogoMIPS (lpj=13013323)
[42949374.100000] Security Framework v1.0.0 initialized
[42949374.100000] SELinux:  Disabled at boot.
[42949374.100000] Mount-cache hash table entries: 512
[42949374.100000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[42949374.100000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[42949374.100000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[42949374.100000] CPU: L2 Cache: 512K (64 bytes/line)
[42949374.100000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000020 00000000 00000000 00000000
[42949374.100000] mtrr: v2.0 (20020519)
[42949374.100000] Enabling fast FPU save and restore... done.
[42949374.100000] Enabling unmasked SIMD FPU exception support... done.
[42949374.100000] Checking 'hlt' instruction... OK.
[42949374.140000] checking if image is initramfs... it is
[42949374.960000] Freeing initrd memory: 6781k freed
[42949374.980000] ACPI: Looking for DSDT ... not found!
[42949374.980000] CPU0: AMD Athlon(tm) XP 1800+ stepping 00
[42949374.980000] Total of 1 processors activated (2602.66 BogoMIPS).
[42949374.980000] ENABLING IO-APIC IRQs
[42949374.980000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[42949375.190000] Brought up 1 CPUs
[42949375.190000] NET: Registered protocol family 16
[42949375.190000] EISA bus registered
[42949375.190000] ACPI: bus type pci registered
[42949375.190000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[42949375.190000] PCI: Using configuration type 1
[42949375.190000] ACPI: Subsystem revision 20051216
[42949375.190000] ACPI: Interpreter enabled
[42949375.190000] ACPI: Using IOAPIC for interrupt routing
[42949375.200000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[42949375.200000] PCI: Probing PCI hardware (bus 00)
[42949375.200000] Boot video device is 0000:01:00.0
[42949375.200000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[42949375.220000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[42949375.230000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[42949375.240000] ACPI: PCI Interrupt Link [LNKA] (IRQs 16) *0, disabled.
[42949375.240000] ACPI: PCI Interrupt Link [LNKB] (IRQs 17) *0, disabled.
[42949375.240000] ACPI: PCI Interrupt Link [LNKC] (IRQs 18) *0, disabled.
[42949375.240000] ACPI: PCI Interrupt Link [LNKD] (IRQs 19) *10
[42949375.240000] ACPI: PCI Interrupt Link [LNKE] (IRQs 16) *11
[42949375.240000] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *0, disabled.
[42949375.240000] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *0, disabled.
[42949375.240000] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *0, disabled.
[42949375.240000] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *5
[42949375.240000] ACPI: PCI Interrupt Link [LAPU] (IRQs 20 21 22) *0, disabled.
[42949375.240000] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *11
[42949375.240000] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[42949375.240000] ACPI: PCI Interrupt Link [LKSM] (IRQs 23) *3
[42949375.240000] ACPI: PCI Interrupt Link [LFWR] (IRQs 20 21 22) *0, disabled.
[42949375.250000] ACPI: PCI Interrupt Link [LETH] (IRQs 20 21 22) *0, disabled.
[42949375.250000] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22) *0
[42949375.250000] ACPI: PCI Interrupt Link [LSHD] (IRQs 20 21 22) *0, disabled.
[42949375.250000] Linux Plug and Play Support v0.97 (c) Adam Belay
[42949375.250000] pnp: PnP ACPI init
[42949375.260000] pnp: PnP ACPI: found 13 devices
[42949375.260000] PnPBIOS: Disabled by ACPI PNP
[42949375.260000] PCI: Using ACPI for IRQ routing
[42949375.260000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[42949375.270000] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved
[42949375.270000] pnp: 00:0b: ioport range 0x295-0x296 has been reserved
[42949375.270000] PCI: Bridge: 0000:00:08.0
[42949375.270000]   IO window: disabled.
[42949375.270000]   MEM window: disabled.
[42949375.270000]   PREFETCH window: disabled.
[42949375.270000] PCI: Bridge: 0000:00:1e.0
[42949375.270000]   IO window: disabled.
[42949375.270000]   MEM window: fca00000-feafffff
[42949375.270000]   PREFETCH window: e4800000-f48fffff
[42949375.270000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[42949375.280000] audit: initializing netlink socket (disabled)
[42949375.280000] audit(1163775175.270:1): initialized
[42949375.280000] highmem bounce pool size: 64 pages
[42949375.280000] VFS: Disk quotas dquot_6.5.1
[42949375.280000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[42949375.280000] Initializing Cryptographic API
[42949375.280000] io scheduler noop registered
[42949375.280000] io scheduler anticipatory registered
[42949375.280000] io scheduler deadline registered
[42949375.280000] io scheduler cfq registered
[42949375.280000] isapnp: Scanning for PnP cards...
[42949375.630000] isapnp: No Plug & Play device found
[42949375.660000] Real Time Clock Driver v1.12
[42949375.660000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f12:PS2M] at 0x60,0x64 irq 1,12
[42949375.660000] serio: i8042 AUX port at 0x60,0x64 irq 12
[42949375.660000] serio: i8042 KBD port at 0x60,0x64 irq 1
[42949375.660000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[42949375.660000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949375.660000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949375.660000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[42949375.660000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[42949375.660000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[42949375.660000] mice: PS/2 mouse device common for all mice
[42949375.660000] EISA: Probing bus 0 at eisa.0
[42949375.660000] Cannot allocate resource for EISA slot 4
[42949375.660000] EISA: Detected 0 cards.
[42949375.660000] NET: Registered protocol family 2
[42949375.690000] input: AT Translated Set 2 keyboard as /class/input/input0
[42949375.750000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[42949375.750000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[42949375.750000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[42949375.750000] TCP: Hash tables configured (established 262144 bind 65536)
[42949375.750000] TCP reno registered
[42949375.750000] TCP bic registered
[42949375.750000] NET: Registered protocol family 1
[42949375.750000] NET: Registered protocol family 8
[42949375.750000] NET: Registered protocol family 20
[42949375.750000] Using IPI No-Shortcut mode
[42949375.750000] ACPI wakeup devices: 
[42949375.750000] PCI0 PS2K PS2M UAR1  MAC AC97  MDM USB0 USB1 USB2 PCI1 
[42949375.750000] ACPI: (supports S0 S1 S3 S4 S5)
[42949375.750000] Freeing unused kernel memory: 332k freed
[42949375.820000] vesafb: framebuffer at 0xe8000000, mapped to 0xf8880000, using 3072k, total 65536k
[42949375.820000] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[42949375.820000] vesafb: protected mode interface info at c000:f060
[42949375.820000] vesafb: scrolling: redraw
[42949375.820000] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[42949375.820000] vesafb: Mode is VGA compatible
[42949375.860000] Console: switching to colour frame buffer device 128x48
[42949375.860000] fb0: VESA VGA frame buffer device
[42949375.870000] Capability LSM initialized
[42949376.520000] SCSI subsystem initialized
[42949376.520000] ACPI: bus type scsi registered
[42949376.520000] libata version 1.20 loaded.
[42949376.530000] NFORCE2-U400R: IDE controller at PCI slot 0000:00:09.0
[42949376.530000] NFORCE2-U400R: chipset revision 163
[42949376.530000] NFORCE2-U400R: not 100% native mode: will probe irqs later
[42949376.530000] NFORCE2-U400R: BIOS didn't set cable bits correctly. Enabling workaround.
[42949376.530000] NFORCE2-U400R: 0000:00:09.0 (rev a3) UDMA133 controller
[42949376.530000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[42949376.530000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:DMA
[42949376.530000] Probing IDE interface ide0...
[42949376.840000] hda: Maxtor 4R080L0, ATA DISK drive
[42949377.560000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[42949377.570000] Probing IDE interface ide1...
[42949378.660000] hdd: CREATIVE CD5233E, ATAPI CD/DVD-ROM drive
[42949378.720000] ide1 at 0x170-0x177,0x376 on irq 15
[42949378.740000] hda: max request size: 128KiB
[42949378.740000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[42949378.740000] hda: cache flushes supported
[42949378.740000]  hda: hda1 hda2 < hda5 >
[42949378.780000] hdd: ATAPI 56X CD-ROM drive, 128kB Cache, DMA
[42949378.780000] Uniform CD-ROM driver Revision: 3.20
[42949379.020000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.
[42949379.020000] **** SET: Misaligned resource pointer: df8c83e2 Type 07 Len 0
[42949379.020000] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 22
[42949379.020000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LKLN] -> GSI 22 (level, high) -> IRQ 177
[42949379.020000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[42949379.550000] eth0: forcedeth.c: subsystem: 01849:0900 bound to 0000:00:04.0
[42949379.600000] Attempting manual resume
[42949379.650000] kjournald starting.  Commit interval 5 seconds
[42949379.650000] EXT3-fs: mounted filesystem with ordered data mode.
[42949383.740000] eth1: no link during initialization.
[42949384.740000] Linux agpgart interface v0.101 (c) Dave Jones
[42949384.770000] agpgart: Detected NVIDIA nForce2 chipset
[42949384.770000] agpgart: AGP aperture is 64M @ 0xf8000000
[42949384.780000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4300
[42949384.780000]  : Error requesting region 4300 .. 4307 for SMB2
[42949384.780000] nForce2_smbus 0000:00:01.1: Error probing SMB2.
[42949385.060000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[42949385.150000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[42949385.280000] input: PC Speaker as /class/input/input1
[42949385.750000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[42949385.830000] parport: PnPBIOS parport detected.
[42949385.830000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[42949385.980000] **** SET: Misaligned resource pointer: f7d7eb22 Type 07 Len 0
[42949385.980000] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 21
[42949385.980000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LAUI] -> GSI 21 (level, high) -> IRQ 185
[42949385.980000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[42949386.020000] ts: Compaq touchscreen protocol output
[42949386.300000] intel8x0_measure_ac97_clock: measured 51642 usecs
[42949386.300000] intel8x0: clocking to 47366
[42949387.120000] lp0: using parport0 (interrupt-driven).
[42949387.340000] Adding 3028212k swap on /dev/hda5.  Priority:-1 extents:1 across:3028212k
[42949387.470000] EXT3 FS on hda1, internal journal
[42949387.770000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[42949387.770000] md: bitmap version 4.39
[42949388.480000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[42949389.600000] cdrom: open failed.
```

---

### Post by rdnk on 2006-11-17
It turned out my new motherboard (Asrock K7NF2-Raid) was activating dual channel mode on memory slots 1 & 3 no matter what brands or sizes of memory I put there. Kernel panics were propably caused by two different incompatible memory modules working in dual channel.

---

