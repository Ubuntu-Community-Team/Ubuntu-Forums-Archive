---
title: "21 seconds boot delay"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by demon981 on 2008-09-24
Hello ubuntu users. I please for your help in one issue. When i start ubuntu, i have to wait for about 21 seconds at the beginning. This is what dmesg says:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003feea000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003feea000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 261856) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261856
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261856
[    0.000000] On node 0 totalpages: 261856
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F74E0 checksum 0
[    0.000000] ACPI: RSDP 000F74E0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3FEE58D8, 0044 (r1   Sony       J1 20051025 PTL         0)
[    0.000000] ACPI: APIC 3FEE9E78, 0068 (r1   Sony       J1 20051025 PTL        5F)
[    0.000000] ACPI: FACP 3FEE9EE0, 0084 (r2   Sony       J1 20051025 PTL        5F)
[    0.000000] ACPI: DSDT 3FEE636D, 3B0B (r1   Sony       J1 20051025 PTL  20030224)
[    0.000000] ACPI: FACS 3FEFAFC0, 0040
[    0.000000] ACPI: BOOT 3FEE9FD8, 0028 (r1   Sony       J1 20051025 PTL         1)
[    0.000000] ACPI: MCFG 3FEE9F9C, 003C (r1   Sony       J1 20051025 PTL        5F)
[    0.000000] ACPI: SSDT 3FEE6195, 01D4 (r1   Sony       J1 20051025 PTL  20030224)
[    0.000000] ACPI: SSDT 3FEE5D50, 0235 (r1   Sony       J1 20051025 PTL  20030224)
[    0.000000] ACPI: SSDT 3FEE5B35, 021B (r1   Sony       J1 20051025 PTL  20030224)
[    0.000000] ACPI: SSDT 3FEE591C, 0219 (r1   Sony       J1 20051025 PTL  20030224)
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
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
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259811
[    0.000000] Kernel command line: root=/dev/sda5 ro quiet vga=792
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1729.213 MHz processor.
[   21.023170] Console: colour dummy device 80x25
[   21.023174] console [tty0] enabled
[   21.023480] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.023889] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.053129] Memory: 1026296k/1047424k available (2177k kernel code, 20408k reserved, 1006k data, 368k init, 129920k highmem)
[   21.053137] virtual kernel memory layout:
[   21.053138]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   21.053140]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.053141]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.053142]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   21.053143]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   21.053145]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   21.053146]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   21.053149] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.053183] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.133187] Calibrating delay using timer specific routine.. 3462.23 BogoMIPS (lpj=6924477)
[   21.133210] Security Framework initialized
[   21.133217] SELinux:  Disabled at boot.
[   21.133231] AppArmor: AppArmor initialized
[   21.133235] Failure registering capabilities with primary security module.
[   21.133243] Mount-cache hash table entries: 512
[   21.133358] Initializing cgroup subsys ns
[   21.133363] Initializing cgroup subsys cpuacct
[   21.133373] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000 00000000
[   21.133384] CPU: L1 I cache: 32K, L1 D cache: 32K
[   21.133386] CPU: L2 cache: 2048K
[   21.133389] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000 00000000
[   21.133397] Compat vDSO mapped to ffffe000.
[   21.133409] Checking 'hlt' instruction... OK.
[   21.149547] SMP alternatives: switching to UP code
[   21.151345] Freeing SMP alternatives: 11k freed
[   21.151446] Early unpacking initramfs... done
[   21.499823] ACPI: Core revision 20070126
[   21.499879] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.509689] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[   21.509715] Total of 1 processors activated (3462.23 BogoMIPS).
[   21.509912] ENABLING IO-APIC IRQs
[   21.510100] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.657100] Brought up 1 CPUs
[   21.657127] CPU0 attaching sched-domain:
[   21.657130]  domain 0: span 01
[   21.657132]   groups: 01
[   21.657296] net_namespace: 64 bytes
[   21.657304] Booting paravirtualized kernel on bare hardware
[   21.657763] Time: 16:36:31  Date: 09/24/08
[   21.657787] NET: Registered protocol family 16
[   21.657967] EISA bus registered
[   21.657994] ACPI: bus type pci registered
[   21.658453] PCI: PCI BIOS revision 2.10 entry at 0xfd91f, last bus=8
[   21.658456] PCI: Using configuration type 1
[   21.658470] Setting up standard PCI resources
[   21.666971] ACPI: EC: Look up EC in DSDT
[   21.671296] ACPI: Interpreter enabled
[   21.671299] ACPI: (supports S0 S3 S4 S5)
[   21.671312] ACPI: Using IOAPIC for interrupt routing
[   21.671721] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   21.777165] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   21.777168] ACPI: EC: driver started in interrupt mode
[   21.777204] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.777796] Force enabled HPET at base address 0xfed00000
[   21.777802] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   21.777806] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   21.778642] PCI: Transparent bridge - 0000:00:1e.0
[   21.778719] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.779018] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   21.779149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   21.783203] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   21.783287] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[   21.783367] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[   21.783447] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   21.783528] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   21.783607] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   21.783688] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   21.783768] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   21.783878] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.783907] pnp: PnP ACPI init
[   21.783913] ACPI: bus type pnp registered
[   21.785668] pnp: PnP ACPI: found 8 devices
[   21.785671] ACPI: ACPI bus type pnp unregistered
[   21.785674] PnPBIOS: Disabled by ACPI PNP
[   21.785867] PCI: Using ACPI for IRQ routing
[   21.785870] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.817025] NET: Registered protocol family 8
[   21.817027] NET: Registered protocol family 20
[   21.817181] hpet clockevent registered
[   21.817188] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   21.817192] hpet0: 3 64-bit timers, 14318180 Hz
[   21.818225] AppArmor: AppArmor Filesystem Enabled
[   21.821018] Time: tsc clocksource has been installed.
[   21.829050] system 00:04: ioport range 0x380-0x383 has been reserved
[   21.829053] system 00:04: ioport range 0x800-0x80f has been reserved
[   21.829056] system 00:04: ioport range 0x1000-0x107f has been reserved
[   21.829058] system 00:04: ioport range 0x1180-0x11bf has been reserved
[   21.829061] system 00:04: ioport range 0x1640-0x164f has been reserved
[   21.829065] system 00:04: iomem range 0xf0008000-0xf000bfff could not be reserved
[   21.829068] system 00:04: iomem range 0xf0000000-0xf0003fff could not be reserved
[   21.829071] system 00:04: iomem range 0xf0005000-0xf0005fff could not be reserved
[   21.829074] system 00:04: iomem range 0xf0004000-0xf0004fff could not be reserved
[   21.829077] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[   21.859448] PCI: Bridge: 0000:00:01.0
[   21.859450]   IO window: disabled.
[   21.859454]   MEM window: 90000000-afffffff
[   21.859456]   PREFETCH window: c0000000-cfffffff
[   21.859467] PCI: Bus 7, cardbus bridge: 0000:06:03.0
[   21.859470]   IO window: 00002400-000024ff
[   21.859475]   IO window: 00002800-000028ff
[   21.859482]   PREFETCH window: 50000000-53ffffff
[   21.859487]   MEM window: 54000000-57ffffff
[   21.859493] PCI: Bridge: 0000:00:1e.0
[   21.859496]   IO window: 2000-2fff
[   21.859502]   MEM window: b0000000-b00fffff
[   21.859506]   PREFETCH window: disabled.
[   21.859522] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.859527] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.859539] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.859560] PCI: Enabling device 0000:06:03.0 (0000 -> 0003)
[   21.859564] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.859580] NET: Registered protocol family 2
[   21.897050] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.897265] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.897987] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.898371] TCP: Hash tables configured (established 131072 bind 65536)
[   21.898373] TCP reno registered
[   21.909139] checking if image is initramfs... it is
[   22.320894] Switched to high resolution mode on CPU 0
[   22.582385] Freeing initrd memory: 7272k freed
[   22.582599] Simple Boot Flag at 0x36 set to 0x1
[   22.582989] audit: initializing netlink socket (disabled)
[   22.583006] audit(1222274192.420:1): initialized
[   22.583173] highmem bounce pool size: 64 pages
[   22.585009] VFS: Disk quotas dquot_6.5.1
[   22.585087] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.585224] io scheduler noop registered
[   22.585227] io scheduler anticipatory registered
[   22.585229] io scheduler deadline registered
[   22.585240] io scheduler cfq registered (default)
[   22.585347] Boot video device is 0000:01:00.0
[   22.585359] PCI: Firmware left 0000:06:08.0 e100 interrupts enabled, disabling
[   22.585465] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.585494] assign_interrupt_mode Found MSI capability
[   22.585519] Allocate Port Service[0000:00:01.0:pcie00]
[   22.585738] isapnp: Scanning for PnP cards...
[   22.941054] isapnp: No Plug & Play device found
[   22.966975] Real Time Clock Driver v1.12ac
[   22.967078] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.968185] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.968254] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.968340] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.973133] i8042.c: Detected active multiplexing controller, rev 1.1.
[   22.976455] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.976459] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   22.976462] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   22.976464] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   22.976467] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   22.988663] mice: PS/2 mouse device common for all mice
[   22.988768] EISA: Probing bus 0 at eisa.0
[   22.988776] Cannot allocate resource for EISA slot 1
[   22.988779] Cannot allocate resource for EISA slot 2
[   22.988808] EISA: Detected 0 cards.
[   22.988811] cpuidle: using governor ladder
[   22.988813] cpuidle: using governor menu
[   22.988900] NET: Registered protocol family 1
[   22.988926] Using IPI No-Shortcut mode
[   22.988956] registered taskstats version 1
[   22.989052]   Magic number: 8:101:642
[   22.989133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.989135] EDD information not available.
[   22.989316] Freeing unused kernel memory: 368k freed
[   23.191397] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.204014] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 6144k, total 32768k
[   23.204018] vesafb: mode is 1024x768x32, linelength=4096, pages=1
[   23.204020] vesafb: protected mode interface info at c000:d310
[   23.204022] vesafb: pmi: set display start = c00cd346, set palette = c00cd3b0
[   23.204024] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[   23.204034] vesafb: scrolling: redraw
[   23.204036] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   23.204140] Console: switching to colour frame buffer device 128x48
[   23.245886] fb0: VESA VGA frame buffer device
[   23.378138] fuse init (API version 7.9)
[   23.395597] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   23.395602] ACPI: Processor [CPU0] (supports 8 throttling states)
[   23.395615] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.398103] ACPI: Thermal Zone [THRM] (39 C)
[   23.968311] usbcore: registered new interface driver usbfs
[   23.968335] usbcore: registered new interface driver hub
[   23.980267] usbcore: registered new device driver usb
[   23.995461] USB Universal Host Controller Interface driver v3.0
[   23.995519] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   23.995531] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.995535] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.995864] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.995894] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001800
[   23.996025] usb usb1: configuration #1 chosen from 1 choice
[   23.996048] hub 1-0:1.0: USB hub found
[   23.996054] hub 1-0:1.0: 2 ports detected
[   24.059669] SCSI subsystem initialized
[   24.096325] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   24.096337] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   24.096342] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   24.096365] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   24.096396] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001820
[   24.096511] usb usb2: configuration #1 chosen from 1 choice
[   24.096533] hub 2-0:1.0: USB hub found
[   24.096539] hub 2-0:1.0: 2 ports detected
[   24.128205] libata version 3.00 loaded.
[   24.160196] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   24.160198] e100: Copyright(c) 1999-2006 Intel Corporation
[   24.200281] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   24.200292] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   24.200297] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   24.200319] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   24.200350] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001840
[   24.200458] usb usb3: configuration #1 chosen from 1 choice
[   24.200480] hub 3-0:1.0: USB hub found
[   24.200486] hub 3-0:1.0: 2 ports detected
[   24.304217] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   24.304230] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   24.304235] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   24.304257] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   24.304288] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[   24.304395] usb usb4: configuration #1 chosen from 1 choice
[   24.304417] hub 4-0:1.0: USB hub found
[   24.304422] hub 4-0:1.0: 2 ports detected
[   24.408283] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[   24.408297] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.408301] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.408325] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   24.412251] ehci_hcd 0000:00:1d.7: debug port 1
[   24.412257] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.412264] ehci_hcd 0000:00:1d.7: irq 17, io mem 0x80004000
[   24.428088] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.428206] usb usb5: configuration #1 chosen from 1 choice
[   24.428229] hub 5-0:1.0: USB hub found
[   24.428235] hub 5-0:1.0: 8 ports detected
[   24.532244] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   24.565191] e100: eth0: e100_probe: addr 0xb0007000, irq 20, MAC addr 00:01:4a:f1:90:11
[   24.565206] ata_piix 0000:00:1f.1: version 2.12
[   24.565221] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   24.565252] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.565510] scsi0 : ata_piix
[   24.566279] scsi1 : ata_piix
[   24.566801] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[   24.566805] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[   24.815951] Clocksource tsc unstable (delta = -9102778365 ns)
[   24.820153] Time: hpet clocksource has been installed.
[   24.823098] ata1.00: ATA-6: TOSHIBA MK1031GAS, AA204A, max UDMA/100
[   24.823102] ata1.00: 195371568 sectors, multi 16: LBA48 
[   24.823126] ata1.01: ATAPI: MATSHITAUJ-841D, 1.11, max UDMA/33
[   24.824086] ata1.00: configured for UDMA/100
[   24.826383] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   24.828350] ata1.01: configured for UDMA/33
[   24.828394] ata2: port disabled. ignoring.
[   24.828523] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1031GA AA20 PQ: 0 ANSI: 5
[   24.829125] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-841D          1.11 PQ: 0 ANSI: 5
[   24.831706] ACPI: PCI Interrupt 0000:06:03.2[C] -> GSI 18 (level, low) -> IRQ 19
[   24.881489] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[b0004000-b00047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   24.896492] Driver 'sd' needs updating - please use bus_type methods
[   24.896568] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   24.896580] sd 0:0:0:0: [sda] Write Protect is off
[   24.896583] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.896598] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.896642] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   24.896651] sd 0:0:0:0: [sda] Write Protect is off
[   24.896654] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.896668] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.896672]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.903777]  sda1 sda2 sda3 < sda5 sda6 sda7 >
[   24.905335] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.912270] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.912288] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   24.917824] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   24.917828] Uniform CD-ROM driver Revision: 3.20
[   24.917871] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   24.922697] usb 3-1: configuration #1 chosen from 1 choice
[   24.972564] usbcore: registered new interface driver hiddev
[   24.986316] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input2
[   24.987080] input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1d.2-1
[   24.987095] usbcore: registered new interface driver usbhid
[   24.987099] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.058231] Attempting manual resume
[   25.058235] swsusp: Resume From Partition 8:7
[   25.058237] PM: Checking swsusp image.
[   25.058395] PM: Resume from disk failed.
[   25.072542] kjournald starting.  Commit interval 5 seconds
[   25.072552] EXT3-fs: mounted filesystem with ordered data mode.
[   25.120469] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460302015d5b]
[   27.730140] Linux agpgart interface v0.102
[   27.934080] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.978108] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.202064] input: Power Button (FF) as /devices/virtual/input/input3
[   28.217925] ACPI: Power Button (FF) [PWRF]
[   28.218016] input: Lid Switch as /devices/virtual/input/input4
[   28.221350] ACPI: Lid Switch [LID0]
[   28.221412] input: Power Button (CM) as /devices/virtual/input/input5
[   28.229930] ACPI: Power Button (CM) [PWRB]
[   28.535526] ACPI: AC Adapter [ADP1] (off-line)
[   28.586483] ACPI: Battery Slot [BAT0] (battery present)
[   29.083201] Yenta: CardBus bridge found at 0000:06:03.0 [104d:818f]
[   29.083229] Yenta: Enabling burst memory read transactions
[   29.083236] Yenta: Using CSCINT to route CSC interrupts to PCI
[   29.083238] Yenta: Routing CardBus interrupts to PCI
[   29.083244] Yenta TI: socket 0000:06:03.0, mfunc 0x01001b22, devctl 0x64
[   29.131100] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6
[   29.141589] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[   29.142108] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7
[   29.153571] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   29.314326] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   29.314332] Socket status: 30000006
[   29.314335] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   29.314340] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   29.314343] cs: IO port probe 0x2000-0x2fff: clean.
[   29.314563] pcmcia: parent PCI bridge Memory window: 0xb0000000 - 0xb00fffff
[   29.603485] nvidia: module license 'NVIDIA' taints kernel.
[   30.633035] ieee80211_crypt: registered algorithm 'NULL'
[   30.640292] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   30.640296] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   30.661829] ACPI: PCI Interrupt 0000:06:03.3[B] -> GSI 17 (level, low) -> IRQ 21
[   30.684997] tifm_core: MMC/SD card detected in socket 0:0
[   30.784981] intel_rng: FWH not detected
[   30.793057] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   30.820961] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   30.820964] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   30.821062] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 22 (level, low) -> IRQ 22
[   30.853592] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   30.921067] iTCO_vendor_support: vendor-support=0
[   30.944916] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.944991] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   30.945600] iTCO_wdt: No card detected
[   31.288891] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   31.656697] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.656725] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   32.075426] input: PS/2 Mouse as /devices/virtual/input/input9
[   32.112536] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input10
[   32.934506] ipw2200: Radio Frequency Kill Switch is On:
[   32.934509] Kill switch must be turned off for wireless networking to work.
[   33.004849] cs: IO port probe 0x100-0x3af: clean.
[   33.007169] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   33.008167] cs: IO port probe 0x820-0x8ff: clean.
[   33.008982] cs: IO port probe 0xc00-0xcf7: clean.
[   33.009975] cs: IO port probe 0xa00-0xaff: clean.
[   33.113496] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   33.113645] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.113655] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   33.113776] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   33.412897] NET: Registered protocol family 10
[   33.413098] lo: Disabled Privacy Extensions
[   33.490704] lp: driver loaded but no devices found
[   33.514308] ACPI Sony Notebook Control Driver v0.2-PP successfully installed
[   33.697933] Adding 530104k swap on /dev/sda7.  Priority:-1 extents:1 across:530104k
[   33.712880] EXT3 FS on sda5, internal journal
[   33.771776] kjournald starting.  Commit interval 5 seconds
[   33.771925] EXT3 FS on sda6, internal journal
[   33.771930] EXT3-fs: mounted filesystem with ordered data mode.
[   34.136226] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.291453] PPP generic driver version 2.4.2
[   34.311210] NET: Registered protocol family 17
[   34.332585] NET: Registered protocol family 24
[   34.689982] No dock devices found.
[   35.303889] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   35.303894] apm: overridden by ACPI.
[   36.227354] ppdev: user-space parallel port driver
[   36.413862] audit(1222263433.607:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5459 profile="/usr/sbin/cupsd" namespace="default"
[   40.928571] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   91.469903] Marking TSC unstable due to: cpufreq changes.
[  162.109076] cdrom: This disc doesn't have any tracks I recognize!
[  169.015687] UDF-fs: No VRS found
[  169.020190] ISO 9660 Extensions: Microsoft Joliet Level 3
[  169.023195] ISO 9660 Extensions: RRIP_1991A
```


Could you please tell me what is wrong?

Thanx.

---

