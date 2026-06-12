---
title: "Help pls!"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by Meowmix on 2007-06-15
hello there, i am extreamly new to ubuntu, and i am having several problems,.... i started of by installing that 7.04 one useing live cd, when booting of it i contiunually got bugger I/O errors, but i was able to install it onto a 40gb shared partion (with windows vista). once the installation had completed it was unable to boot into the os only grub luckly i was still able to get into vista / xp (xp is on a seperate 160gb)  i decided to use the other ubuntu that was on the website the 6.04 one or somthing using alternate cd, this time i didnt get contiunal errors and was able to get into the os, very, very slowly...... i was looking for help on the internet and i was unable to find any that fixed the problem other then 'dmesg' into a a console ill show you what it said...

"'[17179570.308000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.452000] NET: Registered protocol family 16
[17179570.452000] EISA bus registered
[17179570.452000] ACPI: bus type pci registered
[17179570.468000] PCI: PCI BIOS revision 2.10 entry at 0xfb3d0, last bus=1
[17179570.468000] PCI: Using configuration type 1
[17179570.472000] ACPI: Subsystem revision 20051216
[17179570.480000] ACPI: Interpreter enabled
[17179570.480000] ACPI: Using IOAPIC for interrupt routing
[17179570.484000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.484000] PCI: Probing PCI hardware (bus 00)
[17179570.484000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.484000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179570.484000] Boot video device is 0000:01:00.0
[17179570.488000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.516000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 14 15
)
[17179570.516000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 14 15)
 *0, disabled.
[17179570.516000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15
)
[17179570.516000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15)
 *0, disabled.
[17179570.516000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 14 15
)
[17179570.516000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 14 15
)
[17179570.516000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 14 15
)
[17179570.520000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 14 15
)
[17179570.524000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.524000] pnp: PnP ACPI init
[17179570.528000] pnp: PnP ACPI: found 11 devices
[17179570.528000] PnPBIOS: Disabled by ACPI PNP
[17179570.528000] PCI: Using ACPI for IRQ routing
[17179570.528000] PCI: If a device doesn't work, try "pci=routeirq".  If it help
s, post a report
[17179570.560000] PCI: Bridge: 0000:00:01.0
[17179570.560000]   IO window: disabled.
[17179570.560000]   MEM window: e8000000-eaffffff
[17179570.560000]   PREFETCH window: d0000000-dfffffff
[17179570.564000] audit: initializing netlink socket (disabled)
[17179570.564000] audit(1181946418.564:1): initialized
[17179570.564000] highmem bounce pool size: 64 pages
[17179570.564000] VFS: Disk quotas dquot_6.5.1
[17179570.564000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.564000] Initializing Cryptographic API
[17179570.564000] io scheduler noop registered
[17179570.564000] io scheduler anticipatory registered
[17179570.564000] io scheduler deadline registered
[17179570.564000] io scheduler cfq registered
[17179570.564000] isapnp: Scanning for PnP cards...
[17179570.916000] isapnp: No Plug & Play device found
[17179570.968000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179570.968000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.996000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.996000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.000000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shar
ing enabled
[17179572.000000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.000000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.004000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.004000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.008000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b
locksize
[17179572.008000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.008000] ide: Assuming 33MHz system bus speed for PIO modes; override w
ith idebus=xx
[17179572.008000] mice: PS/2 mouse device common for all mice
[17179572.008000] EISA: Probing bus 0 at eisa.0
[17179572.012000] Cannot allocate resource for EISA slot 1
[17179572.012000] Cannot allocate resource for EISA slot 4
[17179572.012000] EISA: Detected 0 cards.
[17179572.012000] NET: Registered protocol family 2
[17179572.040000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.064000] IP route cache hash table entries: 65536 (order: 6, 262144 byt
es)
[17179572.064000] TCP established hash table entries: 262144 (order: 8, 1048576
bytes)
[17179572.064000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.064000] TCP: Hash tables configured (established 262144 bind 65536)
[17179572.064000] TCP reno registered
[17179572.064000] TCP bic registered
[17179572.064000] NET: Registered protocol family 1
[17179572.064000] NET: Registered protocol family 8
[17179572.064000] NET: Registered protocol family 20
[17179572.064000] Using IPI Shortcut mode
[17179572.064000] ACPI wakeup devices:
[17179572.064000] FUTS PCI0 USB0 USB1 USB2 USB3 AMR0 UAR1 UAR2 PS2K
[17179572.064000] ACPI: (supports S0 S3 S4 S5)
[17179572.064000] Freeing unused kernel memory: 288k freed
[17179572.136000] vga16fb: initializing
[17179572.136000] vga16fb: mapped to 0xc00a0000
[17179572.400000] Console: switching to colour frame buffer device 80x25
[17179572.400000] fb0: VGA16 VGA frame buffer device
[17179573.428000] Capability LSM initialized
[17179573.680000] ACPI: Fan [FAN] (on)
[17179573.688000] ACPI: Thermal Zone [THRM] (28 C)
[17179574.760000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179574.760000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) ->
IRQ 169
[17179574.760000] SIS5513: chipset revision 1
[17179574.760000] SIS5513: not 100% native mode: will probe irqs later
[17179574.760000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179574.760000]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb
:DMA
[17179574.760000]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd
:DMA
[17179574.760000] Probing IDE interface ide0...
[17179575.052000] hda: ST3160815A, ATA DISK drive
[17179575.332000] hdb: MAXTOR 4K040H2, ATA DISK drive
[17179575.388000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.412000] Probing IDE interface ide1...
[17179576.148000] hdc: HL-DT-ST RW/DVD GCC-4521B, ATAPI CD/DVD-ROM drive
[17179576.932000] hdd: LITE-ON DVDRW SHW-1635S, ATAPI CD/DVD-ROM drive
[17179576.988000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.008000] hda: max request size: 1024KiB
[17179577.052000] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/
255/63, UDMA(100)
[17179577.080000] hda: cache flushes supported
[17179577.080000]  hda: hda1
[17179577.104000] hdb: max request size: 128KiB
[17179577.104000] hdb: 78198750 sectors (40037 MB) w/2000KiB Cache, CHS=65535/16
/63, UDMA(100)
[17179577.104000] hdb: cache flushes supported
[17179577.104000]  hdb: hdb1 hdb2 hdb3 < hdb5 >
[17179577.136000] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.136000] Uniform CD-ROM driver Revision: 3.20
[17179577.140000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA
(33)
[17179581.388000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179581.388000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=72
[17179581.388000] ide: failed opcode was: unknown
[17179581.388000] end_request: I/O error, dev hdb, sector 72
[17179581.388000] Buffer I/O error on device hdb, logical block 36
[17179585.632000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179585.632000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=74
[17179585.632000] ide: failed opcode was: unknown
[17179585.632000] end_request: I/O error, dev hdb, sector 74
[17179585.632000] Buffer I/O error on device hdb, logical block 37
[17179589.872000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179589.872000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=76
[17179589.872000] ide: failed opcode was: unknown
[17179589.872000] end_request: I/O error, dev hdb, sector 76
[17179589.872000] Buffer I/O error on device hdb, logical block 38
[17179594.148000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179594.148000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=78
[17179594.148000] ide: failed opcode was: unknown
[17179594.148000] end_request: I/O error, dev hdb, sector 78
[17179594.148000] Buffer I/O error on device hdb, logical block 39
[17179598.388000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179598.388000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=80
[17179598.388000] ide: failed opcode was: unknown
[17179598.388000] end_request: I/O error, dev hdb, sector 80
[17179598.388000] Buffer I/O error on device hdb, logical block 40
[17179602.628000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179602.628000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=82
[17179602.628000] ide: failed opcode was: unknown
[17179602.628000] end_request: I/O error, dev hdb, sector 82
[17179602.628000] Buffer I/O error on device hdb, logical block 41
[17179606.872000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179606.872000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=84
[17179606.872000] ide: failed opcode was: unknown
[17179606.872000] end_request: I/O error, dev hdb, sector 84
[17179606.872000] Buffer I/O error on device hdb, logical block 42
[17179611.112000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179611.112000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=86
[17179611.112000] ide: failed opcode was: unknown
[17179611.112000] end_request: I/O error, dev hdb, sector 86
[17179611.112000] Buffer I/O error on device hdb, logical block 43
[17179615.352000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179615.352000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=88
[17179615.352000] ide: failed opcode was: unknown
[17179615.352000] end_request: I/O error, dev hdb, sector 88
[17179615.352000] Buffer I/O error on device hdb, logical block 44
[17179619.592000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179619.592000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=90
[17179619.592000] ide: failed opcode was: unknown
[17179619.592000] end_request: I/O error, dev hdb, sector 90
[17179619.592000] Buffer I/O error on device hdb, logical block 45
[17179623.856000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179623.856000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=92
[17179623.856000] ide: failed opcode was: unknown
[17179623.856000] end_request: I/O error, dev hdb, sector 92
[17179623.856000] Buffer I/O error on device hdb, logical block 46
[17179628.100000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179628.100000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=94
[17179628.100000] ide: failed opcode was: unknown
[17179628.100000] end_request: I/O error, dev hdb, sector 94
[17179628.100000] Buffer I/O error on device hdb, logical block 47
[17179632.340000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179632.340000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=96
[17179632.340000] ide: failed opcode was: unknown
[17179632.340000] end_request: I/O error, dev hdb, sector 96
[17179632.340000] Buffer I/O error on device hdb, logical block 48
[17179636.580000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179636.580000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=98
[17179636.580000] ide: failed opcode was: unknown
[17179636.580000] end_request: I/O error, dev hdb, sector 98
[17179636.580000] Buffer I/O error on device hdb, logical block 49
[17179640.820000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179640.820000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=100
[17179640.820000] ide: failed opcode was: unknown
[17179640.820000] end_request: I/O error, dev hdb, sector 100
[17179640.820000] Buffer I/O error on device hdb, logical block 50
[17179645.064000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179645.064000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=102
[17179645.064000] ide: failed opcode was: unknown
[17179645.064000] end_request: I/O error, dev hdb, sector 102
[17179645.064000] Buffer I/O error on device hdb, logical block 51
[17179649.104000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179649.104000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=104
[17179649.104000] ide: failed opcode was: unknown
[17179649.104000] end_request: I/O error, dev hdb, sector 104
[17179649.104000] Buffer I/O error on device hdb, logical block 52
[17179653.140000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179653.140000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=106
[17179653.140000] ide: failed opcode was: unknown
[17179653.140000] end_request: I/O error, dev hdb, sector 106
[17179653.140000] Buffer I/O error on device hdb, logical block 53
[17179657.180000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179657.180000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=108
[17179657.180000] ide: failed opcode was: unknown
[17179657.180000] end_request: I/O error, dev hdb, sector 108
[17179657.180000] Buffer I/O error on device hdb, logical block 54
[17179661.220000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179661.220000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=110
[17179661.220000] ide: failed opcode was: unknown
[17179661.220000] end_request: I/O error, dev hdb, sector 110
[17179661.220000] Buffer I/O error on device hdb, logical block 55
[17179665.260000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179665.260000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=112
[17179665.260000] ide: failed opcode was: unknown
[17179665.260000] end_request: I/O error, dev hdb, sector 112
[17179665.260000] Buffer I/O error on device hdb, logical block 56
[17179669.300000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179669.300000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=114
[17179669.300000] ide: failed opcode was: unknown
[17179669.300000] end_request: I/O error, dev hdb, sector 114
[17179669.300000] Buffer I/O error on device hdb, logical block 57
[17179673.336000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179673.336000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=116
[17179673.336000] ide: failed opcode was: unknown
[17179673.336000] end_request: I/O error, dev hdb, sector 116
[17179673.336000] Buffer I/O error on device hdb, logical block 58
[17179677.376000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179677.376000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=118
[17179677.376000] ide: failed opcode was: unknown
[17179677.376000] end_request: I/O error, dev hdb, sector 118
[17179677.376000] Buffer I/O error on device hdb, logical block 59
[17179681.416000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179681.416000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=120
[17179681.416000] ide: failed opcode was: unknown
[17179681.416000] end_request: I/O error, dev hdb, sector 120
[17179681.416000] Buffer I/O error on device hdb, logical block 60
[17179685.468000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179685.468000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=122
[17179685.468000] ide: failed opcode was: unknown
[17179685.468000] end_request: I/O error, dev hdb, sector 122
[17179685.468000] Buffer I/O error on device hdb, logical block 61
[17179689.504000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179689.504000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=124
[17179689.504000] ide: failed opcode was: unknown
[17179689.504000] end_request: I/O error, dev hdb, sector 124
[17179689.504000] Buffer I/O error on device hdb, logical block 62
[17179693.544000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179693.544000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=126
[17179693.544000] ide: failed opcode was: unknown
[17179693.544000] end_request: I/O error, dev hdb, sector 126
[17179693.544000] Buffer I/O error on device hdb, logical block 63
[17179697.584000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179697.584000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=128
[17179697.584000] ide: failed opcode was: unknown
[17179697.584000] end_request: I/O error, dev hdb, sector 128
[17179697.584000] Buffer I/O error on device hdb, logical block 64
[17179701.624000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179701.624000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=130
[17179701.624000] ide: failed opcode was: unknown
[17179701.624000] end_request: I/O error, dev hdb, sector 130
[17179701.624000] Buffer I/O error on device hdb, logical block 65
[17179705.664000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179705.664000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=132
[17179705.664000] ide: failed opcode was: unknown
[17179705.664000] end_request: I/O error, dev hdb, sector 132
[17179705.664000] Buffer I/O error on device hdb, logical block 66
[17179709.860000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179709.860000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=131
[17179709.860000] ide: failed opcode was: unknown
[17179709.860000] end_request: I/O error, dev hdb, sector 131
[17179709.860000] Buffer I/O error on device hdb1, logical block 17
[17179713.988000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179713.988000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=131
[17179713.988000] ide: failed opcode was: unknown
[17179713.988000] end_request: I/O error, dev hdb, sector 131
[17179713.988000] Buffer I/O error on device hdb1, logical block 17
[17179718.048000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179718.048000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=131
[17179718.048000] ide: failed opcode was: unknown
[17179718.048000] end_request: I/O error, dev hdb, sector 131
[17179718.048000] Buffer I/O error on device hdb1, logical block 17
[17179722.088000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179722.088000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=131
[17179722.088000] ide: failed opcode was: unknown
[17179722.088000] end_request: I/O error, dev hdb, sector 131
[17179722.088000] Buffer I/O error on device hdb1, logical block 17
[17179726.128000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179726.128000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=131
[17179726.128000] ide: failed opcode was: unknown
[17179726.128000] end_request: I/O error, dev hdb, sector 131
[17179726.128000] Buffer I/O error on device hdb1, logical block 17
[17179730.168000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179730.168000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=131
[17179730.168000] ide: failed opcode was: unknown
[17179730.168000] end_request: I/O error, dev hdb, sector 131
[17179730.168000] Buffer I/O error on device hdb1, logical block 17
[17179734.204000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179734.204000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=132,
 sector=131
[17179734.208000] ide: failed opcode was: unknown
[17179734.208000] end_request: I/O error, dev hdb, sector 131
[17179734.208000] Buffer I/O error on device hdb1, logical block 17
[17179734.296000] usbcore: registered new driver usbfs
[17179734.296000] usbcore: registered new driver hub
[17179734.296000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI)
Driver (PCI)
[17179734.300000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) ->
IRQ 177
[17179734.300000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179734.328000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus nu
mber 1
[17179734.328000] ohci_hcd 0000:00:03.0: irq 177, io mem 0xeb013000
[17179734.384000] hub 1-0:1.0: USB hub found
[17179734.384000] hub 1-0:1.0: 3 ports detected
[17179734.488000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) ->
IRQ 185
[17179734.488000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179734.516000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus nu
mber 2
[17179734.516000] ohci_hcd 0000:00:03.1: irq 185, io mem 0xeb010000
[17179734.572000] hub 2-0:1.0: USB hub found
[17179734.572000] hub 2-0:1.0: 3 ports detected
[17179734.676000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) ->

[
^ i had to delete some to make it fit...

I belive there is some thing wrong with the maxator drive which is the one with ubuntu on it.. could this problem have some thing to do with the other half of the drive is ntfs and belongs to vista? i am prepared to remove vista aslong as i will be able to still boot to xp and if it will fix my problem... any help at all will be apriciated, thank you ;);)

---

### Post by confused57 on 2007-06-15
You could try adding "acpi=off", without quotes,  to your kernel line, boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), and edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
menu.lst is short for menu.list

Then try adding the acpi=off to the kernel line in your first entry to boot Ubuntu, quit & save. Reboot & see if this helps.

Here is a list of Knoppix Cheatcodes, which will give you some idea of what this does:
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

I'm not the best at reading dmesg errors, but looked like there might be some dma errors...see if the acpi=off helps, then you might try something like "nodma" or it could possibly be an option in your bios for enabling dma or disabling dma?

---

### Post by Meowmix on 2007-06-16
i tried what you said... but it only seemed to make it long (it was probably just me being paranoid)... is there anything else i can do? pls i really like ubuntu only this is stopping me from using it :( i also noticed gaim auto closes when ever i try to use it auto close's ](*,)](*,)

will giving ubuntu the hole disk solve the problem ? pls ? ill try any thing, thanks for helping :)

---

### Post by tommcd on 2007-06-16
As per this section of your dmesg:
--------------------------------------------------------------------------------------------------------
[17179570.524000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.524000] pnp: PnP ACPI init
[17179570.528000] pnp: PnP ACPI: found 11 devices
[17179570.528000] PnPBIOS: Disabled by ACPI PNP
[17179570.528000] PCI: Using ACPI for IRQ routing
[17179570.528000] PCI: If a device doesn't work, try "pci=routeirq". If it help
---------------------------------------------------------------------------------------------------------------
You could also try "pci=routeirq" if acpi=off does not help. Or try pnpbios=off since you seem to have some errors about that also. What kind of computer is it? motherboard? chiset?

---

### Post by Meowmix on 2007-06-16
Hi, i have an Acer Asipre T-310 which should have a Acer E61ML mainboard or at least simular and have a SiS 661 chipset  (around 4 years+) the bios are pheonix so changing almost anything there is hard / impossible i forgot to mention, whn i turned it on today i started running errors on a black screen which was differnt to when i used to just hide them 	#-o and when the gnome thing loads saying "HAL!" couldnt be loaded.... maby linux and me just arnt ment to be :(

Just some more specs if it will help

1.256 ram
40 gb hard drive, 50% vista / 50% Ubuntu
160 gb hard drive. Windows XP
1 Lite-On dvd burner
1 inbuilt (?) cd burner
Nvida 6600 Grahpics
1 Floppy disk (pulled out cabls because i read it can oftenly cause a problem)

---

### Post by Pumalite on 2007-06-16
> **Meowmix said:**
> Hi, i have an Acer Asipre T-310 which should have a Acer E61ML mainboard or at least simular and have a SiS 661 chipset  (around 4 years+) the bios are pheonix so changing almost anything there is hard / impossible i forgot to mention, whn i turned it on today i started running errors on a black screen which was differnt to when i used to just hide them 	#-o and when the gnome thing loads saying "HAL!" couldnt be loaded.... maby linux and me just arnt ment to be :(

Just some more specs if it will help

1.256 ram
40 gb hard drive, 50% vista / 50% Ubuntu
160 gb hard drive. Windows XP
1 Lite-On dvd burner
1 inbuilt (?) cd burner
Nvida 6600 Grahpics
1 Floppy disk (pulled out cabls because i read it can oftenly cause a problem)

How did you make the partition in the 40GB drive?. Vista doesn't like anyone living with her. If you insist, then you have to make the partition from Vista. Even then I'd say you have trouble. Give the entire 40GB to Ubuntu and I'd bet your problems are solved.

---

### Post by tommcd on 2007-06-16
Did you try adding the kernel options to this line in /boot/grub/menu.lst (acpi=off, noapic, pci=routeirq, pnpbios=off:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)
Try each one at a time. 
So if I understand you correctly, you installed ubuntu ok, you get the grub menu on boot up, but you just can't boot ubuntu. Is that correct?
If all else fails, and you really want ubuntu (and I hope you do!), then disconnect the other hard drive, install ubuntu from the alternate CD, and see if that helps. Also, if you have a printer or usb drive or anything hooked up, then disconnect them before you install.
Sorry you are having such a problem. Your system 'should' work ok. 
If you just can't get ubuntu going, please consider zenwalk:
[http://zenwalk.org/](http://zenwalk.org/)
It is light and fast, and made for low end computers. I'm on it now. I would be interested to see if you had better luck with zenwalk.
Keep at it, don't give up.

---

### Post by Meowmix on 2007-06-16
i originally partioned my 40 gb down to around 18 gb  with 17 gb free space then, i did a manual partion to create the ext3 and the swap it still sounds promising to give Ubuntu the hole drive.. i just have one small problem...  grub is connected to the vista boot loader which connects me to XP i fear that if i remove vista then i will no longer be able to get into xp, i need help telling grub to boot from the xp drive (hda)  and also removing the vista boot loader from the MBR of hda, thanks and again any help is appreciated :D

RE: tommcd, when i first tried to install ubuntu i used 7.04 live cd (with I/O buffer errors) and then when installed i got to grub and it didnt boot (or at least it took so long i gave up).... i was told that the alternate cd of 6.06 would often fix these problems which i tried, this version it seems hid the errors and when booting (after grub) the "mounting root file system" took ages then i check the dmesg and found a hole lot of buffer I/O errors (as posted above). does zenwalk work with beryl and xgl? i hate to say it but it is one of the main reasons i am determind to get ubuntu :P thanks for your help. *** also Ubuntu is installed on the drive thats getting the errors along with vista my other drive only has windows xp

i should also mention, when booting there is a time where it turns to a black screen saying "Entering runlevel 2" the is where i am visual encountered by Buffer I/O errors as a posed to before where i think they were just running in the background and slowing down my boot process

---

### Post by Pumalite on 2007-06-16
> **Meowmix said:**
> i originally partioned my 40 gb down to around 18 gb  with 17 gb free space then, i did a manual partion to create the ext3 and the swap it still sounds promising to give Ubuntu the hole drive.. i just have one small problem...  grub is connected to the vista boot loader which connects me to XP i fear that if i remove vista then i will no longer be able to get into xp, i need help telling grub to boot from the xp drive (hda)  and also removing the vista boot loader from the MBR of hda, thanks and again any help is appreciated :D

RE: tommcd, when i first tried to install ubuntu i used 7.04 live cd (with I/O buffer errors) and then when installed i got to grub and it didnt boot (or at least it took so long i gave up).... i was told that the alternate cd of 6.06 would often fix these problems which i tried, this version it seems hid the errors and when booting (after grub) the "mounting root file system" took ages then i check the dmesg and found a hole lot of buffer I/O errors (as posted above). does zenwalk work with beryl and xgl? i hate to say it but it is one of the main reasons i am determind to get ubuntu :P thanks for your help. *** also Ubuntu is installed on the drive thats getting the errors along with vista my other drive only has windows xp

i should also mention, when booting there is a time where it turns to a black screen saying "Entering runlevel 2" the is where i am visual encountered by Buffer I/O errors as a posed to before where i think they were just running in the background and slowing down my boot process

Your best bet is to start again, and this time, if you want to keep Vista, do the partitioning FROM Vista. Then install Ubuntu.

---

### Post by Meowmix on 2007-06-16
i cann't partion to ext3 and swap from vista can i?! if you mean creating a free space partion for ext3 and swap i did so, and started again twice :confused: ](*,)

---

### Post by confused57 on 2007-06-16
> **Meowmix said:**
> i cann't partion to ext3 and swap from vista can i?! if you mean creating a free space partion for ext3 and swap i did so, and started again twice :confused: ](*,)
Since you have a separate hard drive for Ubuntu, partitioning with Vista doesn't apply for making your ext3 & swap partitions...using the Vista partitioner is recommended for resizing the Vista partition.

Added:  Did you happen to try the kernel boot options that were suggested:
pci=routeirq
pnpbios=off

You might also try:
noirqpoll
[http://ubuntuforums.org/showthread.php?p=2798818](http://ubuntuforums.org/showthread.php?p=2798818)

I don't know if it would help to turn off PlugNPlay in your bios.

---

### Post by Meowmix on 2007-06-17
yes, i tried all of the suggested boot commands but they didn't help, today i unistalled vista and tried to give ubuntu the hole disk, but even loading the disk comes up with hda I/O errors since all of the errors seem to be on the one drive i will try removing the troubling drive....

WoooHoo! it worked! YAY

Ok, it is up and run right now but it still seems to be a bit slow while booting up.. is there any way that i find a log or some thing (like the dmsg thing i used before but forgot how to use) that will be able to tell me if there are any more errors?

Nevermind, i found out how to do it and it seemed to just be registering new devices :D thank you every one for helping!

---

