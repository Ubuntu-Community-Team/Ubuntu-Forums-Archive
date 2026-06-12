---
title: "Problems on apt-get &amp; synaptic"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by guille4ty on 2008-07-10
I don't know why, but my computer keeps freezing up every time I use either apt-get or the Synaptic Package Manager, and after each I have to do a hard reboot on my system... It's not X though, since I can't even restart it. It just randomly freezes up. :confused:

Thx in advance,
guille

---

### Post by forger on 2008-07-10
type in terminal: dmesg

it should show any faults or problems..
or you could try searching the /var/log/ directory

---

### Post by guille4ty on 2008-07-10
Thanks for the quick response!
Either way, there's a few things I saw using dmesg

I'll post the whole thing first and the the warnings

```

guille4ty@Guille:~$ dmesg
[    0.000000] Linux version 2.6.22-14-rt (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP PREEMPT RT Sun Oct 14 22:53:32 GMT 2007 (Unofficial)
[    0.000000] Command line: root=UUID=d8454a46-7d8e-496b-a9c5-ca0227948b40 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ef0000 - 0000000017eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017eff000 - 0000000017f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 98032) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F8290 checksum 0
[    0.000000] ACPI: RSDP 000F8290, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 17EF8BE5, 0034 (r1 HP     3093     20040804  LTP        0)
[    0.000000] ACPI: FACP 17EFEE20, 0074 (r1 HP     3093     20040804 PTL        5F)
[    0.000000] ACPI: DSDT 17EF8C19, 6207 (r1 HP     3091     20040804 MSFT  100000E)
[    0.000000] ACPI: FACS 17EFFFC0, 0040
[    0.000000] ACPI: SSDT 17EFEE94, 00D6 (r1 PTLTD  POWERNOW 20040804  LTP        1)
[    0.000000] ACPI: APIC 17EFEF6A, 005A (r1 PTLTD       3093   20040804  LTP        0)
[    0.000000] ACPI: MCFG 17EFEFC4, 003C (r1 PTLTD    MCFG   20040804  LTP        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000017ef0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 98032) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000017ef0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->    98032
[    0.000000] On node 0 totalpages: 97935
[    0.000000]   DMA zone: 96 pages used for memmap
[    0.000000]   DMA zone: 1192 pages reserved
[    0.000000]   DMA zone: 2711 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 2201 pages used for memmap
[    0.000000]   DMA32 zone: 91735 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34376 bytes of per cpu data
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
[    0.000000] Built 1 zonelists.  Total pages: 94446
[    0.000000] Kernel command line: root=UUID=d8454a46-7d8e-496b-a9c5-ca0227948b40 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] WARNING: experimental RCU implementation.
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   10.123925] time.c: Detected 1790.828 MHz processor.
[   10.124822] Console: colour VGA+ 80x25
[   10.124843] Checking aperture...
[   10.124848] CPU 0: aperture @ 79fc000000 size 32 MB
[   10.124850] Aperture too small (32 MB)
[   10.137398] No AGP bridge found
[   10.146662] Memory: 370096k/392128k available (2343k kernel code, 21644k reserved, 1228k data, 324k init)
[   10.205770] Calibrating delay using timer specific routine.. 3583.93 BogoMIPS (lpj=1791968)
[   10.205824] Security Framework v1.0.0 initialized
[   10.205834] SELinux:  Disabled at boot.
[   10.205913] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   10.206513] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   10.206856] Mount-cache hash table entries: 256
[   10.207090] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   10.207093] CPU: L2 Cache: 512K (64 bytes/line)
[   10.207096] CPU 0/0 -> Node 0
[   10.207120] SMP alternatives: switching to UP code
[   10.207385] Freeing SMP alternatives: 19k freed
[   10.208008] Early unpacking initramfs... done
[   10.552603] ACPI: Core revision 20070126
[   10.552701] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.567807] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   10.577848] Using local APIC timer interrupts.
[   10.633616] APIC timer calibration result 12436312
[   10.633618] Detected 12.436 MHz APIC timer.
[   10.634060] Brought up 1 CPUs
[   10.634366] NET: Registered protocol family 16
[   10.634490] ACPI: bus type pci registered
[   10.634498] PCI: Using configuration type 1
[   10.635571] ACPI: EC: Look up EC in DSDT
[   10.636268] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   10.637652] ACPI: Interpreter enabled
[   10.637656] ACPI: (supports S0 S3 S4 S5)
[   10.637678] ACPI: Using IOAPIC for interrupt routing
[   10.643875] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   10.643930] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.643939] PCI: Probing PCI hardware (bus 00)
[   10.645448] PCI: Transparent bridge - 0000:00:14.4
[   10.645561] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.645755] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   10.645917] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   10.648257] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   10.648367] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   10.648475] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   10.648584] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   10.648714] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   10.648821] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   10.648929] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   10.649037] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   10.649128] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.649151] pnp: PnP ACPI init
[   10.649169] ACPI: bus type pnp registered
[   10.651867] pnp: PnP ACPI: found 10 devices
[   10.651870] ACPI: ACPI bus type pnp unregistered
[   10.651957] PCI: Using ACPI for IRQ routing
[   10.651961] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.652095] NET: Registered protocol family 8
[   10.652097] NET: Registered protocol family 20
[   10.652282] pnp: 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   10.652287] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   10.652292] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   10.652302] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   10.652306] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   10.652309] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   10.652313] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   10.652320] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   10.652325] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   10.652328] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   10.652796] PCI: Bridge: 0000:00:01.0
[   10.652799]   IO window: 9000-9fff
[   10.652804]   MEM window: c0100000-c01fffff
[   10.652807]   PREFETCH window: c8000000-cfffffff
[   10.652819] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[   10.652821]   IO window: 0000a400-0000a4ff
[   10.652828]   IO window: 0000a800-0000a8ff
[   10.652834]   PREFETCH window: 30000000-33ffffff
[   10.652841]   MEM window: 34000000-37ffffff
[   10.652846] PCI: Bridge: 0000:00:14.4
[   10.652850]   IO window: a000-afff
[   10.652857]   MEM window: c0200000-c02fffff
[   10.652863]   PREFETCH window: 30000000-33ffffff
[   10.652906] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[   10.652915] PCI: Setting latency timer of device 0000:05:09.0 to 64
[   10.652981] NET: Registered protocol family 2
[   10.658746] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   10.658949] TCP established hash table entries: 16384 (order: 8, 1179648 bytes)
[   10.660398] TCP bind hash table entries: 16384 (order: 8, 1048576 bytes)
[   10.661713] TCP: Hash tables configured (established 16384 bind 16384)
[   10.661720] TCP reno registered
[   10.663861] checking if image is initramfs... it is
[   11.331705] Freeing initrd memory: 7554k freed
[   11.341731] audit: initializing netlink socket (disabled)
[   11.341752] audit(1215725950.152:1): initialized
[   11.341980] VFS: Disk quotas dquot_6.5.1
[   11.341993] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   11.342066] io scheduler noop registered
[   11.342068] io scheduler anticipatory registered
[   11.342071] io scheduler deadline registered
[   11.342082] io scheduler cfq registered (default)
[   11.342089] PCI: MSI quirk detected. MSI deactivated.
[   12.001228] Boot video device is 0000:01:05.0
[   12.033924] Real Time Clock Driver v1.12ac
[   12.034085] Linux agpgart interface v0.102 (c) Dave Jones
[   12.034089] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.034845] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   12.034856] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   12.035637] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.035809] input: Macintosh mouse button emulation as /class/input/input0
[   12.035910] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   12.037741] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.037802] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.037980] mice: PS/2 mouse device common for all mice
[   12.038139] TCP cubic registered
[   12.038147] NET: Registered protocol family 1
[   12.038408] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   12.038418] Freeing unused kernel memory: 324k freed
[   12.068080] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.228042] AppArmor: AppArmor initialized<5>audit(1215725952.041:2):  type=1505 info="AppArmor initialized" pid=1154
[   13.235888] fuse init (API version 7.8)
[   13.240916] Failure registering capabilities with primary security module.
[   13.250223] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   13.250230] ACPI: Processor [CPU0] (supports 8 throttling states)
[   13.251834] ACPI: Thermal Zone [THRM] (88 C)
[   14.012162] usbcore: registered new interface driver usbfs
[   14.012196] usbcore: registered new interface driver hub
[   14.013418] usbcore: registered new device driver usb
[   14.019687] SCSI subsystem initialized
[   14.022446] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   14.023814] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   14.023976] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   14.024185] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   14.145747] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[   14.201891] usb usb1: configuration #1 chosen from 1 choice
[   14.201926] hub 1-0:1.0: USB hub found
[   14.201942] hub 1-0:1.0: 4 ports detected
[   14.201998] 8139too Fast Ethernet driver 0.9.28
[   14.230236] libata version 2.21 loaded.
[   14.302635] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   14.302804] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   14.302889] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[   14.302952] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[   14.302965] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.303108] usb usb2: configuration #1 chosen from 1 choice
[   14.303158] hub 2-0:1.0: USB hub found
[   14.303167] hub 2-0:1.0: 8 ports detected
[   14.404544] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   14.404713] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   14.405110] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   14.405133] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[   14.460501] usb usb3: configuration #1 chosen from 1 choice
[   14.460688] hub 3-0:1.0: USB hub found
[   14.460702] hub 3-0:1.0: 4 ports detected
[   14.562369] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   14.563403] eth0: RealTek RTL8139 at 0xffffc20000316000, 00:c0:9f:ba:40:cb, IRQ 18
[   14.563408] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   14.563452] ACPI: PCI Interrupt 0000:05:09.2[C] -> GSI 22 (level, low) -> IRQ 22
[   14.609751] usb 2-2: new high speed USB device using ehci_hcd and address 2
[   14.625721] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   14.632709] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   14.657147] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.657154] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.671897] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   14.671924] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   14.671938] ATIIXP: chipset revision 0
[   14.671941] ATIIXP: not 100% native mode: will probe irqs later
[   14.671952]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   14.671968]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   14.671978] Probing IDE interface ide0...
[   14.725433] usb 2-2: configuration #1 chosen from 1 choice
[   14.726237] hub 2-2:1.0: USB hub found
[   14.726610] hub 2-2:1.0: 4 ports detected
[   14.937774] hda: FUJITSU MHV2080AH, ATA DISK drive
[   15.450688] usb 3-3: new full speed USB device using ohci_hcd and address 2
[   15.548582] hda: selected mode 0x45
[   15.552391] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   15.622376] Probing IDE interface ide1...
[   15.636417] usb 3-3: configuration #1 chosen from 1 choice
[   15.818576] usb 2-2.1: new full speed USB device using ehci_hcd and address 5
[   15.880280] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f000063dbdc]
[   16.011733] usb 2-2.1: configuration #1 chosen from 1 choice
[   16.196103] usb 2-2.4: new low speed USB device using ehci_hcd and address 6
[   16.288219] usb 2-2.4: configuration #1 chosen from 1 choice
[   16.289592] usbcore: registered new interface driver hiddev
[   16.293194] hdc: PIONEER DVDRW DVR-K15, ATAPI CD/DVD-ROM drive
[   16.549312] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   16.748855] usb 1-1: configuration #1 chosen from 1 choice
[   16.780611] HID device not claimed by input or hiddev
[   16.783970] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   16.784153] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.2-2.4
[   16.794030] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input3
[   16.794041] input: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:13.0-1
[   16.808947] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input4
[   16.808955] input: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:13.0-1
[   16.808968] usbcore: registered new interface driver usbhid
[   16.808972] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   16.904883] hdc: selected mode 0x22
[   16.905766] ide1 at 0x170-0x177,0x376 on irq 15
[   16.932393] hda: max request size: 128KiB
[   16.932399] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[   16.936004] hda: cache flushes supported
[   16.936071]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 >
[   17.041012] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, DMA
[   17.041020] Uniform CD-ROM driver Revision: 3.20
[   17.362608] Attempting manual resume
[   17.362613] swsusp: Resume From Partition 3:7
[   17.362615] PM: Checking swsusp image.
[   17.362821] PM: Resume from disk failed.
[   17.377715] EXT3-fs: INFO: recovery required on readonly filesystem.
[   17.377722] EXT3-fs: write access will be enabled during recovery.
[   18.953272] kjournald starting.  Commit interval 5 seconds
[   18.953301] EXT3-fs: recovery complete.
[   18.953975] EXT3-fs: mounted filesystem with ordered data mode.
[   27.594960] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.639844] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.974610] input: PC Speaker as /class/input/input5
[   28.057978] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   28.636869] ieee80211_crypt: registered algorithm 'NULL'
[   28.702731] ACPI: PCI Interrupt 0000:05:09.3[A] -> GSI 17 (level, low) -> IRQ 17
[   28.715143] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   28.715149] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   28.777179] sdhci: Secure Digital Host Controller Interface driver
[   28.777185] sdhci: Copyright(c) Pierre Ossman
[   28.777251] sdhci: SDHCI controller found at 0000:05:09.4 [104c:8034] (rev 0)
[   28.777281] ACPI: PCI Interrupt 0000:05:09.4[A] -> GSI 17 (level, low) -> IRQ 17
[   28.778008] mmc0: SDHCI at 0xc0209400 irq 17 DMA
[   28.778279] mmc1: SDHCI at 0xc0209000 irq 17 DMA
[   28.778471] mmc2: SDHCI at 0xc0208400 irq 17 DMA
[   28.813557] Bluetooth: Core ver 2.11
[   28.813631] NET: Registered protocol family 31
[   28.813633] Bluetooth: HCI device and connection manager initialized
[   28.813637] Bluetooth: HCI socket layer initialized
[   28.847232] usbcore: registered new interface driver xpad
[   28.847238] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   28.878542] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[   28.878573] Yenta: Enabling burst memory read transactions
[   28.878579] Yenta: Using CSCINT to route CSC interrupts to PCI
[   28.878581] Yenta: Routing CardBus interrupts to PCI
[   28.878588] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x64
[   28.886716] Bluetooth: HCI USB driver ver 2.9
[   28.888978] usbcore: registered new interface driver hci_usb
[   28.917862] bcm43xx driver
[   29.101472] Yenta: ISA IRQ mask 0x0ee8, PCI irq 17
[   29.101479] Socket status: 30000820
[   29.101482] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   29.101490] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   29.101495] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   29.101498] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   29.104283] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[   29.130395] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   29.163044] input: SynPS/2 Synaptics TouchPad as /class/input/input6
[   29.331071] usbcore: registered new interface driver snd-usb-audio
[   29.625865] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   29.728844] MC'97 0 converters and GPIO not ready (0x1)
[   29.730825] pccard: CardBus card inserted into slot 0
[   29.731829] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   29.954128] ath_hal: module license 'Proprietary' taints kernel.
[   30.041018] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   30.219131] wlan: 0.8.4.2 (0.9.3.2)
[   30.255221] ath_pci: 0.9.4.5 (0.9.3.2)
[   30.255935] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[   30.255946] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   30.695694] ath_rate_sample: 1.2 (0.9.3.2)
[   30.696433] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   30.696439] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   30.696448] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   30.696454] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   30.696457] wifi0: mac 5.9 phy 4.3 radio 4.6
[   30.696462] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   30.696464] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   30.696466] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   30.696469] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   30.696470] wifi0: Use hw queue 8 for CAB traffic
[   30.696472] wifi0: Use hw queue 9 for beacons
[   30.719219] wifi0: Atheros 5212: mem=0x34000000, irq=17
[   31.211275] loop: module loaded
[   31.275602] lp: driver loaded but no devices found
[   31.400865] Adding 4088500k swap on /dev/hda7.  Priority:-1 extents:1 across:4088500k
[   31.759952] EXT3 FS on hda1, internal journal
[   32.084926] NET: Registered protocol family 17
[   33.703951] NET: Registered protocol family 10
[   33.704049] lo: Disabled Privacy Extensions
[   34.011506] kjournald starting.  Commit interval 5 seconds
[   34.011785] EXT3 FS on hda5, internal journal
[   34.011790] EXT3-fs: mounted filesystem with ordered data mode.
[   34.035739] kjournald starting.  Commit interval 5 seconds
[   34.036024] EXT3 FS on hda6, internal journal
[   34.036028] EXT3-fs: mounted filesystem with ordered data mode.
[   34.067876] kjournald starting.  Commit interval 5 seconds
[   34.068160] EXT3 FS on hda8, internal journal
[   34.068164] EXT3-fs: mounted filesystem with ordered data mode.
[   35.061245] No dock devices found.
[   35.073967] ACPI: AC Adapter [ACAD] (on-line)
[   35.087967] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   35.175022] ACPI: Battery Slot [BAT1] (battery present)
[   35.225317] input: Power Button (FF) as /class/input/input7
[   35.225346] ACPI: Power Button (FF) [PWRF]
[   35.225389] input: Power Button (CM) as /class/input/input8
[   35.225408] ACPI: Power Button (CM) [PWRB]
[   35.225445] input: Sleep Button (CM) as /class/input/input9
[   35.225463] ACPI: Sleep Button (CM) [SLPB]
[   35.225499] input: Lid Switch as /class/input/input10
[   35.225518] ACPI: Lid Switch [LID]
[   35.503682] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-32 processors (version 2.00.00)
[   35.503730] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[   35.503733] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[   35.503735] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[   36.333644] ppdev: user-space parallel port driver
[   36.466480] audit(1215725987.139:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5473 profile="/usr/sbin/cupsd"
[   36.886893] Failure registering capabilities with primary security module.
[   36.980372] Marking TSC unstable due to cpufreq changes
[   38.486948] [drm] Initialized drm 1.1.0 20060810
[   38.495899] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   38.496731] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   39.789140] [drm] Setting GART location based on new memory map
[   39.789452] [drm] Loading R300 Microcode
[   39.789466] [drm] writeback test succeeded in 1 usecs
[   40.560396] ath0: no IPv6 routers present

```

mainly this I found, but I don't think it affects anything much:
```

[    0.000000] Initializing CPU#0
[    0.000000] WARNING: experimental RCU implementation.

```

---

### Post by forger on 2008-07-11
You could try some of the boot options:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

i.e. pci=noacpi

Play around with a variety of them :)

---

### Post by guille4ty on 2008-07-11
Thanks, disabling ACPI worked like a charm!
=D>

---

