---
title: "Mythtv problems on feisty"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by PapaDoc1 on 2007-05-21
Let me begin by saying I am more than a complete newby.  So thank you in advance for your patients.

I'm running:
7.04
mythtv 0.2
hauppaunge mce 500
nvidia 6800 gt
sound blaster z

I downloaded and followed the directions from  [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop")

I get down to the input connection and it either is hanging up or its not recoqnizing something.

Again,  I appriciate any help you can give.

---

### Post by superm1 on 2007-05-22
Hi,

The most common cause of this problem is from incorrectly choosing the card type that you are using two screens before.  Since you have a pvr-500 series card, you should have chosen "MPEG-2 Encoder Card (PVR-X50, PVR-500)".  Double check this and make sure it was the case.  If you continue to get this error, check out the command 

```
dmesg
```

For information about hardware errors.

Also you can try to launch mythtv setup from the command line so as to catch any errors in a terminal that it is giving

```
mythtv-setup
```

---

### Post by PapaDoc1 on 2007-05-22
I had the correct card installed.  I ran the commands but I don't know what it means.

```
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 000000000000a000 end: 00000000000da000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000008000 end: 000000003fff8000 type: 3
[    0.000000] copy_e820_map() start: 000000003fff8000 size: 0000000000008000 end: 0000000040000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000da000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fba70
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa0c0
[    0.000000] ACPI: RSDT (v001 AMIINT VIA_K8   0x00000010 MSFT 0x00000097) @ 0x3fff0000
[    0.000000] ACPI: FADT (v001 AMIINT VIA_K8   0x00000011 MSFT 0x00000097) @ 0x3fff0030
[    0.000000] ACPI: MADT (v001 AMIINT VIA_K8   0x00000009 MSFT 0x00000097) @ 0x3fff00c0
[    0.000000] ACPI: DSDT (v001    VIA   VIA_K8 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Detected 2000.230 MHz processor.
[   27.534263] Built 1 zonelists.  Total pages: 260081
[   27.534266] Kernel command line: root=UUID=bab6d0b9-29b8-4254-b0bc-191693d25c2d ro quiet splash
[   27.534395] mapped APIC to ffffd000 (fee00000)
[   27.534398] mapped IOAPIC to ffffc000 (fec00000)
[   27.534401] Enabling fast FPU save and restore... done.
[   27.534403] Enabling unmasked SIMD FPU exception support... done.
[   27.534413] Initializing CPU#0
[   27.534476] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   27.536100] Console: colour VGA+ 80x25
[   27.536684] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.537154] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.558536] Memory: 1028060k/1048512k available (1992k kernel code, 19688k reserved, 893k data, 328k init, 131008k highmem)
[   27.558546] virtual kernel memory layout:
[   27.558547]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   27.558548]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.558550]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.558551]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.558552]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   27.558553]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   27.558555]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   27.558557] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.638291] Calibrating delay using timer specific routine.. 4004.08 BogoMIPS (lpj=8008178)
[   27.638328] Security Framework v1.0.0 initialized
[   27.638337] SELinux:  Disabled at boot.
[   27.638351] Mount-cache hash table entries: 512
[   27.638485] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000001
[   27.638493] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   27.638495] CPU: L2 Cache: 1024K (64 bytes/line)
[   27.638498] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000001
[   27.638509] Compat vDSO mapped to ffffe000.
[   27.638513] Remapping vsyscall page to ffffe000
[   27.638523] Checking 'hlt' instruction... OK.
[   27.654397] SMP alternatives: switching to UP code
[   27.654634] Freeing SMP alternatives: 11k freed
[   27.654833] Early unpacking initramfs... done
[   27.944394] ACPI: Core revision 20060707
[   27.944830] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   27.946443] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 0a
[   27.946459] Total of 1 processors activated (4004.08 BogoMIPS).
[   27.946928] ENABLING IO-APIC IRQs
[   27.947232] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   28.093476] Brought up 1 CPUs
[   28.093678] Booting paravirtualized kernel on bare hardware
[   28.093752] Time:  0:14:42  Date: 04/23/107
[   28.093780] NET: Registered protocol family 16
[   28.093847] EISA bus registered
[   28.093851] ACPI: bus type pci registered
[   28.094538] PCI: PCI BIOS revision 2.10 entry at 0xfdab1, last bus=2
[   28.094540] PCI: Using configuration type 1
[   28.094541] Setting up standard PCI resources
[   28.105058] ACPI: Interpreter enabled
[   28.105060] ACPI: Using IOAPIC for interrupt routing
[   28.105334] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.105338] PCI: Probing PCI hardware (bus 00)
[   28.106916] Boot video device is 0000:01:00.0
[   28.107139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.127857] ACPI: Power Resource [URP1] (off)
[   28.127903] ACPI: Power Resource [URP2] (off)
[   28.127949] ACPI: Power Resource [FDDP] (off)
[   28.127993] ACPI: Power Resource [LPTP] (off)
[   28.129001] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   28.129180] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   28.129356] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   28.129537] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   28.129718] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   28.129895] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   28.130073] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   28.130250] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   28.130364] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.130370] pnp: PnP ACPI init
[   28.132644] pnp: PnP ACPI: found 10 devices
[   28.132647] PnPBIOS: Disabled by ACPI PNP
[   28.132680] PCI: Using ACPI for IRQ routing
[   28.132683] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.138329] NET: Registered protocol family 8
[   28.138331] NET: Registered protocol family 20
[   28.138729] PCI: Bridge: 0000:00:01.0
[   28.138731]   IO window: disabled.
[   28.138735]   MEM window: cbe00000-cfefffff
[   28.138738]   PREFETCH window: 9bd00000-bbcfffff
[   28.138742] PCI: Bridge: 0000:00:06.0
[   28.138743]   IO window: disabled.
[   28.138746]   MEM window: disabled.
[   28.138750]   PREFETCH window: bbd00000-cbcfffff
[   28.138762] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.138795] NET: Registered protocol family 2
[   28.169365] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.169516] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.170501] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.171069] TCP: Hash tables configured (established 131072 bind 65536)
[   28.171072] TCP reno registered
[   28.181404] checking if image is initramfs... it is
[   28.751301] Freeing initrd memory: 7007k freed
[   28.751655] audit: initializing netlink socket (disabled)
[   28.751666] audit(1179879282.296:1): initialized
[   28.751721] highmem bounce pool size: 64 pages
[   28.751790] VFS: Disk quotas dquot_6.5.1
[   28.751807] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.751854] io scheduler noop registered
[   28.751856] io scheduler anticipatory registered
[   28.751857] io scheduler deadline registered
[   28.751871] io scheduler cfq registered (default)
[   28.752121] isapnp: Scanning for PnP cards...
[   29.105439] isapnp: No Plug & Play device found
[   29.122816] Real Time Clock Driver v1.12ac
[   29.122850] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.122957] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.123356] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.123545] mice: PS/2 mouse device common for all mice
[   29.123958] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.124133] input: Macintosh mouse button emulation as /class/input/input0
[   29.124156] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.124159] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.124358] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   29.124361] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   29.124586] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.124590] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.124666] EISA: Probing bus 0 at eisa.0
[   29.124703] EISA: Detected 0 cards.
[   29.154805] TCP cubic registered
[   29.154815] NET: Registered protocol family 1
[   29.154833] Using IPI No-Shortcut mode
[   29.154884] ACPI: (supports S0 S1 S4 S5)
[   29.154919]   Magic number: 7:884:203
[   29.154955]   hash matches device ttyt1
[   29.155372] Freeing unused kernel memory: 328k freed
[   29.155460] Time: tsc clocksource has been installed.
[   29.173924] input: AT Translated Set 2 keyboard as /class/input/input1
[   30.376160] Capability LSM initialized
[   30.869596] ieee1394: Initialized config rom entry `ip1394'
[   30.870514] ACPI: PCI Interrupt 0000:00:08.2[B] -> GSI 16 (level, low) -> IRQ 16
[   30.938255] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[cfffb800-cfffbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   30.944739] r8169 Gigabit Ethernet driver 2.2LK loaded
[   30.944758] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.944880] eth0: RTL8169s/8110s at 0xf887a700, 00:0c:76:b4:aa:a3, IRQ 16
[   30.955123] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   30.955143] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 17
[   30.955153] VP_IDE: chipset revision 6
[   30.955154] VP_IDE: not 100% native mode: will probe irqs later
[   30.955164] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   30.955172]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   30.955183]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:DMA
[   30.955190] Probing IDE interface ide0...
[   30.974195] usbcore: registered new interface driver usbfs
[   30.974214] usbcore: registered new interface driver hub
[   30.974230] usbcore: registered new device driver usb
[   30.974835] USB Universal Host Controller Interface driver v3.0
[   31.009336] SCSI subsystem initialized
[   31.013205] libata version 2.20 loaded.
[   31.075805] Floppy drive(s): fd0 is 1.44M
[   31.145258] FDC 0 is a post-1991 82077
[   31.854644] hda: PIONEER DVD-RW DVR-112D, ATAPI CD/DVD-ROM drive
[   32.190454] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   32.191798] Probing IDE interface ide1...
[   32.205983] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c01510596d2]
[   32.828859] hdd: Maxtor 6Y120P0, ATA DISK drive
[   32.884921] ide1 at 0x170-0x177,0x376 on irq 15
[   32.895748] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 18
[   32.895759] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   32.895962] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   32.895990] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000bc00
[   32.896402] usb usb1: configuration #1 chosen from 1 choice
[   32.896536] hub 1-0:1.0: USB hub found
[   32.896544] hub 1-0:1.0: 2 ports detected
[   32.911593] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[   32.911601] Uniform CD-ROM driver Revision: 3.20
[   33.000556] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 18
[   33.000566] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   33.000584] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   33.000605] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000c000
[   33.000690] usb usb2: configuration #1 chosen from 1 choice
[   33.000710] hub 2-0:1.0: USB hub found
[   33.000716] hub 2-0:1.0: 2 ports detected
[   33.104301] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 18
[   33.104308] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   33.104322] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   33.104339] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000c400
[   33.104407] usb usb3: configuration #1 chosen from 1 choice
[   33.104423] hub 3-0:1.0: USB hub found
[   33.104429] hub 3-0:1.0: 2 ports detected
[   33.208123] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 18
[   33.208131] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   33.208148] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   33.208165] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000c800
[   33.208231] usb usb4: configuration #1 chosen from 1 choice
[   33.208248] hub 4-0:1.0: USB hub found
[   33.208254] hub 4-0:1.0: 2 ports detected
[   33.311996] sata_via 0000:00:0f.0: version 2.1
[   33.312013] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 17
[   33.312027] sata_via 0000:00:0f.0: routed to hard irq line 10
[   33.312076] ata1: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e402 bmdma 0x0001d800 irq 17
[   33.312100] ata2: SATA max UDMA/133 cmd 0x0001e000 ctl 0x0001dc02 bmdma 0x0001d808 irq 17
[   33.312115] scsi0 : sata_via
[   33.347203] hdd: max request size: 128KiB
[   33.347334] hdd: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63
[   33.347460] hdd: cache flushes supported
[   33.347488]  hdd: hdd1 hdd2 hdd3
[   33.515496] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   33.526044] ATA: abnormal status 0x7F on port 0x0001e807
[   33.526073] scsi1 : sata_via
[   33.548681] Attempting manual resume
[   33.548685] swsusp: Resume From Partition 22:66
[   33.548687] PM: Checking swsusp image.
[   33.548783] PM: Resume from disk failed.
[   33.580268] kjournald starting.  Commit interval 5 seconds
[   33.580279] EXT3-fs: mounted filesystem with ordered data mode.
[   33.627298] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   33.727108] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   33.737655] ATA: abnormal status 0x7F on port 0x0001e007
[   33.737822] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18
[   33.737834] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   33.737868] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   33.737903] ehci_hcd 0000:00:10.4: irq 18, io mem 0xcfffb500
[   33.737909] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.737986] usb usb5: configuration #1 chosen from 1 choice
[   33.738007] hub 5-0:1.0: USB hub found
[   33.738013] hub 5-0:1.0: 8 ports detected
[   34.158315] usb 2-2: device not accepting address 2, error -71
[   35.515824] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   35.705013] usb 3-2: configuration #1 chosen from 1 choice
[   35.951024] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   36.070804] usb 4-1: device descriptor read/64, error -71
[   36.354678] usb 4-1: configuration #1 chosen from 1 choice
[   36.593844] usb 2-2: new low speed USB device using uhci_hcd and address 4
[   36.765822] usb 2-2: configuration #1 chosen from 1 choice
[   41.202577] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.212280] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.607634] gameport: EMU10K1 is pci0000:00:08.1/gameport0, io 0xec00, speed 1193kHz
[   41.692474] Linux video capture interface: v2.00
[   41.792227] Linux agpgart interface v0.102 (c) Dave Jones
[   41.817045] agpgart: Detected AGP bridge 0
[   41.822783] agpgart: AGP aperture is 128M @ 0xd0000000
[   41.961216] ieee80211_crypt: registered algorithm 'NULL'
[   41.973395] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   41.973398] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   42.036349] ivtv:  ==================== START INIT IVTV ====================
[   42.036352] ivtv:  version 0.10.1 (tagged release) loading
[   42.036354] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
[   42.036356] ivtv:  In case of problems please include the debug info between
[   42.036358] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   42.036360] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   42.036436] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   42.036479] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 19
[   42.036490] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   42.436160] bcm43xx driver
[   42.470552] parport: PnPBIOS parport detected.
[   42.470659] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   42.496252] input: PC Speaker as /class/input/input2
[   42.526990] usbcore: registered new interface driver hiddev
[   42.599920] nvidia: module license 'NVIDIA' taints kernel.
[   42.878906] input: HOLTEK Wireless Keyboard/Mouse(2.4G) as /class/input/input3
[   42.878944] input: USB HID v1.10 Keyboard [HOLTEK Wireless Keyboard/Mouse(2.4G)] on usb-0000:00:10.3-1
[   42.878961] usbcore: registered new interface driver usbserial
[   42.878981] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   42.897864] input: HOLTEK Wireless Keyboard/Mouse(2.4G) as /class/input/input4
[   42.897944] input: USB HID v1.10 Mouse [HOLTEK Wireless Keyboard/Mouse(2.4G)] on usb-0000:00:10.3-1
[   42.987860] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   43.056108] input: Logitech USB-PS/2 Optical Mouse as /class/input/input5
[   43.056178] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.1-2
[   43.056193] usbcore: registered new interface driver usbhid
[   43.056197] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   43.056203] usbcore: registered new interface driver usbserial_generic
[   43.056206] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   43.122964] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI USB Serial Device
[   43.122996] ftdi_sio 3-2:1.0: FTDI USB Serial Device converter detected
[   43.123003] drivers/usb/serial/ftdi_sio.c: Detected FT232BM
[   43.123179] usb 3-2: FTDI USB Serial Device converter now attached to ttyUSB0
[   43.123189] usbcore: registered new interface driver ftdi_sio
[   43.123192] drivers/usb/serial/ftdi_sio.c: v1.4.3:USB FTDI Serial Converters Driver
[   43.229693] ivtv0: Encoder revision: 0x02050032
[   43.229697] ivtv0: Recommended firmware version is 0x02060039.
[   43.295908] tveeprom 0-0050: Hauppauge model 23552, rev E792, serial# 9952041
[   43.295912] tveeprom 0-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   43.295915] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   43.295917] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   43.295920] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   43.295922] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   43.295924] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[   43.295927] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   43.325093] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   43.325116] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   43.329986] tuner 0-0060: TEA5767 detected.
[   43.329988] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   43.330007] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   43.330330] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   43.394682] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   48.219306] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   48.342079] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   48.407094] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   48.407325] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   48.407579] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   48.407744] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   48.408000] ivtv0: Registered device radio0 for encoder radio
[   48.408024] tuner 0-0061: type set to 57 (Philips FQ1236A MK4)
[   48.797986] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   48.798043] ivtv:  ======================  NEXT CARD  ======================
[   48.798047] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   48.798095] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 18 (level, low) -> IRQ 20
[   48.798106] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   49.419777] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   49.633940] ivtv1: Encoder revision: 0x02050032
[   49.633943] ivtv1: Recommended firmware version is 0x02060039.
[   49.640496] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   49.640609] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   49.644929] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   49.666793] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   54.442509] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   54.546588] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   54.623642] tveeprom 1-0050: Hauppauge model 23552, rev E792, serial# 9952041
[   54.623646] tveeprom 1-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   54.623649] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   54.623651] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   54.623654] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   54.623656] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   54.623658] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
[   54.623661] ivtv1: Correcting tveeprom data: no radio present on second unit
[   54.623663] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   54.699462] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   54.699719] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   54.699990] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   54.700165] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   54.700332] tuner 1-0061: type set to 57 (Philips FQ1236A MK4)
[   55.086439] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   55.086729] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 19
[   55.091880] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   55.092121] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   55.106353] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 21
[   55.106488] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   55.110733] ivtv:  ====================  END INIT IVTV  ====================
[   55.477672] ieee80211_crypt: registered algorithm 'WEP'
[   55.644241] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 19 (level, low) -> IRQ 22
[   55.646601] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[   55.901976] fuse init (API version 7.8)
[   55.927084] lp0: using parport0 (interrupt-driven).
[   55.939979] SoftMAC: Open Authentication completed with 00:0c:41:f5:e9:4a
[   55.993944] Adding 2441872k swap on /dev/disk/by-uuid/fd4f3bcc-ddf6-4301-a360-8fcac5a35ec7.  Priority:-1 extents:1 across:2441872k
[   56.079658] EXT3 FS on hdd1, internal journal
[   56.257139] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   56.257305] SGI XFS Quota Management subsystem
[   56.297881] XFS mounting filesystem hdd3
[   56.402337] Ending clean XFS mount for filesystem: hdd3
[   56.745042] NET: Registered protocol family 17
[   60.259099] NET: Registered protocol family 10
[   60.259196] lo: Disabled Privacy Extensions
[   60.512387] Using specific hotkey driver
[   60.575932] input: Power Button (FF) as /class/input/input6
[   60.579745] ACPI: Power Button (FF) [PWRF]
[   60.609648] input: Power Button (CM) as /class/input/input7
[   60.613383] ACPI: Power Button (CM) [PWRB]
[   60.643094] input: Sleep Button (CM) as /class/input/input8
[   60.646838] ACPI: Sleep Button (CM) [SLPB]
[   60.725516] ibm_acpi: ec object not found
[   60.747813] No dock devices found.
[   60.806772] pcc_acpi: loading...
[   61.004541] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[   61.004593] ACPI: Invalid package argument
[   61.004597] ACPI Exception (acpi_processor-0270): AE_BAD_PARAMETER, Invalid _PSS data [20060707]
[   61.006807] powernow-k8:    0 : fid 0x2 (1000 MHz), vid 0x12
[   61.006809] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
[   61.006811] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0x2
[   66.066681] r8169: eth0: link down
[   66.066858] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.192225] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   67.192433] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   67.192622] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   67.497846] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[   67.500402] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[   67.502425] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!
[   68.252033] ppdev: user-space parallel port driver
[   70.471661] eth1: no IPv6 routers present
[   72.551434] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   72.551439] apm: overridden by ACPI.
[   48.024000] Time: acpi_pm clocksource has been installed.
[   52.636000] Bluetooth: Core ver 2.11
[   52.640000] NET: Registered protocol family 31
[   52.640000] Bluetooth: HCI device and connection manager initialized
[   52.640000] Bluetooth: HCI socket layer initialized
[   52.712000] Bluetooth: L2CAP ver 2.8
[   52.712000] Bluetooth: L2CAP socket layer initialized
[   52.756000] Bluetooth: RFCOMM socket layer initialized
[   52.756000] Bluetooth: RFCOMM TTY layer initialized
[   52.756000] Bluetooth: RFCOMM ver 1.8
[  983.540000] NVRM: Xid (0001:00): 6, PE0000 0438 ff7f6a59 0000f478 00000000 fff6e7dc
[  983.544000] NVRM: Xid (0001:00): 29,  L1 -> L0
[ 1954.496000] NVRM: API mismatch: the client has the version 1.0-7184, but
[ 1954.496000] NVRM: this kernel module has the version 1.0-9631.  Please
[ 1954.496000] NVRM: make sure that this kernel module and all NVIDIA driver
[ 1954.496000] NVRM: components have the same version.

```


then I ran mythtv-setup and got this
```
mythtv-setup
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-05-22 20:01:02.319 Using runtime prefix = /usr
2007-05-22 20:01:02.333 Gnome-Screensaver support enabled
2007-05-22 20:01:02.334 DPMS is active.
2007-05-22 20:01:02.372 New DB connection, total: 1
2007-05-22 20:01:02.379 Connected to database 'mythconverg' at host: localhost
2007-05-22 20:01:02.384 Total desktop dim: 1280x1024, with 1 screen[s].
2007-05-22 20:01:02.387 Using screen 0, 1280x1024 at 0,0
2007-05-22 20:01:02.398 Current Schema Version: 
2007-05-22 20:01:02.433 Newest Schema Version : 1160
2007-05-22 20:01:02.434 New DB connection, total: 2
2007-05-22 20:01:02.435 Connected to database 'mythconverg' at host: localhost
2007-05-22 20:01:02.435 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-05-22 20:01:02.437 New DB connection, total: 3
2007-05-22 20:01:02.437 Connected to database 'mythconverg' at host: localhost
2007-05-22 20:01:02.438 Told to create a NEW database schema, but the database
already has 1 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-05-22 20:01:02.438 Database Schema upgrade FAILED, unlocking.
2007-05-22 20:01:02.494 Total desktop dim: 1280x1024, with 1 screen[s].
2007-05-22 20:01:02.496 Using screen 0, 1280x1024 at 0,0
2007-05-22 20:01:02.498 Switching to square mode (G.A.N.T.)
Error: API mismatch: the NVIDIA kernel module is version 1.0.9631, but
this library is version 1.0.7184. Please be sure that your kernel
module and all NVIDIA driver files have the same driver version.
Segmentation fault (core dumped)
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.

```


Thank you for your help

---

### Post by superm1 on 2007-05-22
Okay well two big issues here.  You have a corrupted database and your nvidia drivers aren't properly installed.  Sort out the nvidia driver issue first.  You must have installed via some nonstandard method if you have two different versions like that.  The standard way is to go through Restricted Drivers Manager and enable the driver there.

As for the database, this is the easiest solution:
```
sudo apt-get remove --purge mysql-server-5.0 mythtv-database
```

Let it drop the databases.

```
sudo apt-get install mythtv-database mysql-server-5.0
```

---

### Post by PapaDoc1 on 2007-05-23
Thank you that worked. 

The channel scan only picked up the channels below 13 on both tuners.  I'm assuming that this is an error in the channel frequence table.  Is this correct?

---

### Post by superm1 on 2007-05-23
You just need to set the frequency to be cable rather than air to get the higher channels.  Its in mythtv-setup for a global option and tuner specific.

---

