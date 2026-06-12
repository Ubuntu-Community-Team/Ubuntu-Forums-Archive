---
title: "IDE Flash hard disk not mountable"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by matc on 2009-04-14
Hi everybody,

I'm trying to get a 32MB IDE flash adapter (connected as secondary master) running in ubuntu jaunty beta.
The device is properly detected in BIOS and the system can try to boot from it (there's some messed up grub on it already).

However, booting the jaunty server (2.6.28-11-server) from the primary master hard disk, the device shows errors upon detection:
```
[    2.730334] ata4.00: failed to IDENTIFY (device reports invalid type, err_mask=0x0)
[    7.890333] ata4.00: failed to IDENTIFY (device reports invalid type, err_mask=0x0)
```

As a consequence the hard disk is not assigned any dev node (e.g. /dev/sdb ) and can therefore not be partitioned/formatted/mounted in Linux. 

This happens with various mainboards with VIA and SIS chipsets...

Anybody got an idea? How can I get this to run in order to install something onto it?

---

### Post by matc on 2009-04-14
I forgot the dmesg messages...

Here they come:
```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-server (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #37-Ubuntu SMP Mon Mar 23 17:30:31 UTC 2009 (Ubuntu 2.6.28-11.37-server)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x1000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 00000000000d8000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  modified: 000000003fff0000 - 000000003fff8000 (ACPI data)
[    0.000000]  modified: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-16000
[    0.000000] RAMDISK: 378d7000 - 37fefc0c
[    0.000000] Allocated new RAMDISK: 008b4000 - 00fccc0c
[    0.000000] Move RAMDISK from 00000000378d7000 - 0000000037fefc0b to 008b4000 - 00fccc0b
[    0.000000] ACPI: RSDP 000FA140, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 3FFF0000, 002C (r1 AMIINT VIA_P6         10 MSFT       97)
[    0.000000] ACPI: FACP 3FFF0030, 0081 (r1 AMIINT VIA_P6         11 MSFT       97)
[    0.000000] ACPI: DSDT 3FFF0120, 34F2 (r1    VIA APOLLO-P     1000 INTL  2002024)
[    0.000000] ACPI: FACS 3FFF8000, 0040
[    0.000000] ACPI: APIC 3FFF00C0, 005C (r1 AMIINT VIA_P6          9 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 00000000 - 377fe000
[    0.000000]   bootmap 00013000 - 00019f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008aae2c]    TEXT DATA BSS ==> [0000100000 - 00008aae2c]
[    0.000000]   #4 [00008ab000 - 00008b4000]    INIT_PG_TABLE ==> [00008ab000 - 00008b4000]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [00008b4000 - 0000fccc0c]      NEW RAMDISK ==> [00008b4000 - 0000fccc0c]
[    0.000000]   #8 [0000013000 - 000001a000]          BOOTMAP ==> [0000013000 - 000001a000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262015
[    0.000000] free_area_init_node: node 0, pgdat c06e5480, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34530 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] PERCPU: Allocating 49152 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259967
[    0.000000] Kernel command line: root=UUID=e4c8ad23-a756-4ffc-898a-a878a6970f81 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2953.120 MHz processor.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.010000] allocated 5242240 bytes of page_cgroup
[    0.010000] please try cgroup_disable=memory option if you don't want
[    0.010000] Scanning for low memory corruption every 60 seconds
[    0.010000] Memory: 1018256k/1048512k available (4180k kernel code, 29408k reserved, 2255k data, 548k init, 139208k highmem)
[    0.010000] virtual kernel memory layout:
[    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
[    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
[    0.010000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.010000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.010000]       .init : 0xc0751000 - 0xc07da000   ( 548 kB)
[    0.010000]       .data : 0xc0515153 - 0xc0748fc0   (2255 kB)
[    0.010000]       .text : 0xc0100000 - 0xc0515153   (4180 kB)
[    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.010000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.010019] Calibrating delay loop (skipped), value calculated using timer frequency.. 5906.24 BogoMIPS (lpj=29531200)
[    0.010049] Security Framework initialized
[    0.010063] SELinux:  Disabled at boot.
[    0.010098] AppArmor: AppArmor initialized
[    0.010117] Mount-cache hash table entries: 512
[    0.010356] Initializing cgroup subsys ns
[    0.010363] Initializing cgroup subsys cpuacct
[    0.010368] Initializing cgroup subsys memory
[    0.010375] Initializing cgroup subsys freezer
[    0.010401] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.010406] CPU: L2 cache: 512K
[    0.010410] CPU: Physical Processor ID: 0
[    0.010413] CPU: Processor Core ID: 0
[    0.010435] Checking 'hlt' instruction... OK.
[    0.054278] ACPI: Core revision 20080926
[    0.056159] ACPI: Checking initramfs for custom DSDT
[    0.406820] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.506845] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[    0.510000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 5906.41 BogoMIPS (lpj=29532056)
[    0.010000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.010000] CPU: L2 cache: 512K
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.660291] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[    0.660312] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.670075] Brought up 2 CPUs
[    0.670081] Total of 2 processors activated (11812.65 BogoMIPS).
[    0.670324] CPU0 attaching sched-domain:
[    0.670328]  domain 0: span 0-1 level SIBLING
[    0.670331]   groups: 0 1
[    0.670340] CPU1 attaching sched-domain:
[    0.670343]  domain 0: span 0-1 level SIBLING
[    0.670346]   groups: 1 0
[    0.670442] net_namespace: 776 bytes
[    0.670442] Booting paravirtualized kernel on bare hardware
[    0.670522] Time: 19:32:46  Date: 04/13/09
[    0.670522] regulator: core version 0.5
[    0.670522] NET: Registered protocol family 16
[    0.670522] EISA bus registered
[    0.670522] ACPI: bus type pci registered
[    0.675161] PCI: PCI BIOS revision 2.10 entry at 0xfdb11, last bus=1
[    0.675164] PCI: Using configuration type 1 for base access
[    0.676353] ACPI: EC: Look up EC in DSDT
[    0.685541] ACPI: Interpreter enabled
[    0.685547] ACPI: (supports S0 S1 S4 S5)
[    0.685571] ACPI: Using IOAPIC for interrupt routing
[    0.690862] ACPI: No dock devices found.
[    0.690877] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.690945] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.691027] pci 0000:00:01.0: supports D1
[    0.691073] pci 0000:00:0b.0: reg 10 io port: [0xd400-0xd4ff]
[    0.691081] pci 0000:00:0b.0: reg 14 32bit mmio: [0xdfffbf00-0xdfffbfff]
[    0.691108] pci 0000:00:0b.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.691118] pci 0000:00:0b.0: supports D1 D2
[    0.691121] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
[    0.691127] pci 0000:00:0b.0: PME# disabled
[    0.691166] pci 0000:00:0f.0: reg 10 io port: [0xec00-0xec07]
[    0.691174] pci 0000:00:0f.0: reg 14 io port: [0xe800-0xe803]
[    0.691182] pci 0000:00:0f.0: reg 18 io port: [0xe400-0xe407]
[    0.691189] pci 0000:00:0f.0: reg 1c io port: [0xe000-0xe003]
[    0.691197] pci 0000:00:0f.0: reg 20 io port: [0xdc00-0xdc0f]
[    0.691204] pci 0000:00:0f.0: reg 24 io port: [0xd800-0xd8ff]
[    0.691273] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.691354] pci 0000:00:10.0: reg 20 io port: [0xc400-0xc41f]
[    0.691373] pci 0000:00:10.0: supports D1 D2
[    0.691375] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.691380] pci 0000:00:10.0: PME# disabled
[    0.691433] pci 0000:00:10.1: reg 20 io port: [0xc800-0xc81f]
[    0.691452] pci 0000:00:10.1: supports D1 D2
[    0.691455] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.691460] pci 0000:00:10.1: PME# disabled
[    0.691512] pci 0000:00:10.2: reg 20 io port: [0xcc00-0xcc1f]
[    0.691531] pci 0000:00:10.2: supports D1 D2
[    0.691534] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.691539] pci 0000:00:10.2: PME# disabled
[    0.691591] pci 0000:00:10.3: reg 20 io port: [0xd000-0xd01f]
[    0.691611] pci 0000:00:10.3: supports D1 D2
[    0.691613] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.691618] pci 0000:00:10.3: PME# disabled
[    0.691653] pci 0000:00:10.4: reg 10 32bit mmio: [0xdfffbd00-0xdfffbdff]
[    0.691691] pci 0000:00:10.4: supports D1 D2
[    0.691693] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.691698] pci 0000:00:10.4: PME# disabled
[    0.691768] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.691815] pci 0000:00:11.5: reg 10 io port: [0xc000-0xc0ff]
[    0.691855] pci 0000:00:11.5: supports D1 D2
[    0.691892] pci 0000:00:12.0: reg 10 io port: [0xbc00-0xbcff]
[    0.691900] pci 0000:00:12.0: reg 14 32bit mmio: [0xdfffbc00-0xdfffbcff]
[    0.691934] pci 0000:00:12.0: supports D1 D2
[    0.691937] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.691942] pci 0000:00:12.0: PME# disabled
[    0.691999] pci 0000:01:00.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.692006] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xcfffffff]
[    0.692013] pci 0000:01:00.0: reg 18 32bit mmio: [0xdd000000-0xddffffff]
[    0.692032] pci 0000:01:00.0: reg 30 32bit mmio: [0xdfee0000-0xdfefffff]
[    0.692083] pci 0000:00:01.0: bridge 32bit mmio: [0xdbe00000-0xdfefffff]
[    0.692089] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbbd00000-0xdbcfffff]
[    0.692098] bus 00 -> node 0
[    0.692105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.694870] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.695003] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.695132] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.695262] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.695392] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.695525] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.695656] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.695789] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.695893] ACPI: Power Resource [URP1] (off)
[    0.695933] ACPI: Power Resource [URP2] (off)
[    0.695973] ACPI: Power Resource [FDDP] (off)
[    0.696013] ACPI: Power Resource [LPTP] (off)
[    0.696113] ACPI: WMI: Mapper loaded
[    0.696218] SCSI subsystem initialized
[    0.696218] libata version 3.00 loaded.
[    0.696218] usbcore: registered new interface driver usbfs
[    0.696218] usbcore: registered new interface driver hub
[    0.696218] usbcore: registered new device driver usb
[    0.696218] PCI: Using ACPI for IRQ routing
[    0.710015] Bluetooth: Core ver 2.13
[    0.710039] NET: Registered protocol family 31
[    0.710039] Bluetooth: HCI device and connection manager initialized
[    0.710039] Bluetooth: HCI socket layer initialized
[    0.710039] NET: Registered protocol family 8
[    0.710039] NET: Registered protocol family 20
[    0.710051] NetLabel: Initializing
[    0.710053] NetLabel:  domain hash size = 128
[    0.710056] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.710073] NetLabel:  unlabeled traffic allowed by default
[    0.710190] AppArmor: AppArmor Filesystem Enabled
[    0.720014] pnp: PnP ACPI init
[    0.720030] ACPI: bus type pnp registered
[    0.723379] pnp: PnP ACPI: found 11 devices
[    0.723383] ACPI: ACPI bus type pnp unregistered
[    0.723388] PnPBIOS: Disabled by ACPI PNP
[    0.723404] system 00:01: ioport range 0x295-0x296 has been reserved
[    0.723407] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
[    0.723411] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.723414] system 00:01: ioport range 0x400-0x40f has been reserved
[    0.723417] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.723422] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.723425] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.758241] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.758244] pci 0000:00:01.0:   IO window: disabled
[    0.758251] pci 0000:00:01.0:   MEM window: 0xdbe00000-0xdfefffff
[    0.758256] pci 0000:00:01.0:   PREFETCH window: 0x000000bbd00000-0x000000dbcfffff
[    0.758272] pci 0000:00:01.0: setting latency timer to 64
[    0.758277] bus: 00 index 0 io port: [0x00-0xffff]
[    0.758280] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.758283] bus: 01 index 0 mmio: [0x0-0x0]
[    0.758286] bus: 01 index 1 mmio: [0xdbe00000-0xdfefffff]
[    0.758288] bus: 01 index 2 mmio: [0xbbd00000-0xdbcfffff]
[    0.758291] bus: 01 index 3 mmio: [0x0-0x0]
[    0.758305] NET: Registered protocol family 2
[    0.790082] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.790514] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.791525] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.792171] TCP: Hash tables configured (established 131072 bind 65536)
[    0.792176] TCP reno registered
[    0.810152] NET: Registered protocol family 1
[    0.810332] checking if image is initramfs... it is
[    1.250410] Switched to high resolution mode on CPU 1
[    1.260019] Switched to high resolution mode on CPU 0
[    1.407797] Freeing initrd memory: 7267k freed
[    1.407887] cpufreq: No nForce2 chipset.
[    1.408087] audit: initializing netlink socket (disabled)
[    1.408111] type=2000 audit(1239651166.402:1): initialized
[    1.414654] highmem bounce pool size: 64 pages
[    1.414662] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.416223] VFS: Disk quotas dquot_6.5.1
[    1.416308] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.417109] fuse init (API version 7.10)
[    1.417211] msgmni has been set to 1731
[    1.417488] alg: No test for stdrng (krng)
[    1.417516] io scheduler noop registered
[    1.417519] io scheduler anticipatory registered
[    1.417522] io scheduler deadline registered (default)
[    1.417546] io scheduler cfq registered
[    1.417561] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.417652] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    1.417679] pci 0000:01:00.0: Boot video device
[    1.421109] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.421123] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.421296] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.421300] ACPI: Power Button (FF) [PWRF]
[    1.421355] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.421358] ACPI: Power Button (CM) [PWRB]
[    1.421427] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.421435] ACPI: Sleep Button (CM) [SLPB]
[    1.421666] processor ACPI_CPU:00: registered as cooling_device0
[    1.421727] processor ACPI_CPU:01: registered as cooling_device1
[    1.423820] isapnp: Scanning for PnP cards...
[    1.780180] isapnp: No Plug & Play device found
[    1.810192] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.810287] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.810670] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.811655] brd: module loaded
[    1.812071] loop: module loaded
[    1.812183] Fixed MDIO Bus: probed
[    1.812192] PPP generic driver version 2.4.2
[    1.812268] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.812318] Driver 'sd' needs updating - please use bus_type methods
[    1.812330] Driver 'sr' needs updating - please use bus_type methods
[    1.812509] sata_via 0000:00:0f.0: version 2.4
[    1.812558] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.812614] sata_via 0000:00:0f.0: routed to hard irq line 10
[    1.812767] scsi0 : sata_via
[    1.812925] scsi1 : sata_via
[    1.812981] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 20
[    1.812984] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 20
[    2.020016] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.240017] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.251313] pata_via 0000:00:0f.1: version 0.3.3
[    2.251331] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.251553] scsi2 : pata_via
[    2.251642] scsi3 : pata_via
[    2.253538] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.253541] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.450361] ata3.00: ATA-3: SAMSUNG SV2046D, LS100, max UDMA/66
[    2.450365] ata3.00: 40142592 sectors, multi 16: LBA
[    2.490238] ata3.00: configured for UDMA/66
[    2.550238] ata3.00: configured for UDMA/66
[    2.550242] ata3: EH complete
[    2.730334] ata4.00: failed to IDENTIFY (device reports invalid type, err_mask=0x0)
[    7.890333] ata4.00: failed to IDENTIFY (device reports invalid type, err_mask=0x0)
[   13.030212] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SV2046D  LS10 PQ: 0 ANSI: 5
[   13.030348] sd 2:0:0:0: [sda] 40142592 512-byte hardware sectors: (20.5 GB/19.1 GiB)
[   13.030370] sd 2:0:0:0: [sda] Write Protect is off
[   13.030373] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.030407] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   13.030494] sd 2:0:0:0: [sda] 40142592 512-byte hardware sectors: (20.5 GB/19.1 GiB)
[   13.030513] sd 2:0:0:0: [sda] Write Protect is off
[   13.030516] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.030548] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   13.030553]  sda: sda1 sda2 < sda5 >
[   13.059819] sd 2:0:0:0: [sda] Attached SCSI disk
[   13.059891] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   13.060176] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   13.060215] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[   13.060254] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   13.060335] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[   13.060415] ehci_hcd 0000:00:10.4: irq 21, io mem 0xdfffbd00
[   13.080010] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[   13.080097] usb usb1: configuration #1 chosen from 1 choice
[   13.080135] hub 1-0:1.0: USB hub found
[   13.080149] hub 1-0:1.0: 8 ports detected
[   13.080297] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   13.080325] uhci_hcd: USB Universal Host Controller Interface driver
[   13.080383] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   13.080393] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   13.080455] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[   13.080477] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c400
[   13.080570] usb usb2: configuration #1 chosen from 1 choice
[   13.080602] hub 2-0:1.0: USB hub found
[   13.080614] hub 2-0:1.0: 2 ports detected
[   13.080721] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   13.080729] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   13.080788] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[   13.080809] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000c800
[   13.080897] usb usb3: configuration #1 chosen from 1 choice
[   13.080929] hub 3-0:1.0: USB hub found
[   13.080939] hub 3-0:1.0: 2 ports detected
[   13.081045] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   13.081052] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   13.081117] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[   13.081137] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000cc00
[   13.081237] usb usb4: configuration #1 chosen from 1 choice
[   13.081270] hub 4-0:1.0: USB hub found
[   13.081280] hub 4-0:1.0: 2 ports detected
[   13.081387] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   13.081394] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   13.081455] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[   13.081476] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d000
[   13.081566] usb usb5: configuration #1 chosen from 1 choice
[   13.081598] hub 5-0:1.0: USB hub found
[   13.081607] hub 5-0:1.0: 2 ports detected
[   13.081771] usbcore: registered new interface driver libusual
[   13.081817] usbcore: registered new interface driver usbserial
[   13.081831] USB Serial support registered for generic
[   13.081853] usbcore: registered new interface driver usbserial_generic
[   13.081856] usbserial: USB Serial Driver core
[   13.081908] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   13.081911] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   13.082045] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.090063] mice: PS/2 mouse device common for all mice
[   13.130089] rtc_cmos 00:03: RTC can wake from S4
[   13.130143] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[   13.130198] rtc0: alarms up to one year, y3k, 114 bytes nvram
[   13.130299] device-mapper: uevent: version 1.0.3
[   13.130445] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   13.130559] device-mapper: multipath: version 1.0.5 loaded
[   13.130565] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.130688] EISA: Probing bus 0 at eisa.0
[   13.130735] EISA: Detected 0 cards.
[   13.130816] cpuidle: using governor ladder
[   13.130821] cpuidle: using governor menu
[   13.131537] TCP cubic registered
[   13.131620] NET: Registered protocol family 10
[   13.132210] lo: Disabled Privacy Extensions
[   13.132695] NET: Registered protocol family 17
[   13.132721] Bluetooth: L2CAP ver 2.11
[   13.132724] Bluetooth: L2CAP socket layer initialized
[   13.132728] Bluetooth: SCO (Voice Link) ver 0.6
[   13.132731] Bluetooth: SCO socket layer initialized
[   13.132798] Bluetooth: RFCOMM socket layer initialized
[   13.132819] Bluetooth: RFCOMM TTY layer initialized
[   13.132823] Bluetooth: RFCOMM ver 1.10
[   13.132939] Using IPI No-Shortcut mode
[   13.133075] registered taskstats version 1
[   13.133221]   Magic number: 5:457:546
[   13.133269] mem null: hash matches
[   13.133288] processor ACPI_CPU:01: hash matches
[   13.133342] rtc_cmos 00:03: setting system clock to 2009-04-13 19:32:59 UTC (1239651179)
[   13.133346] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   13.133349] EDD information not available.
[   13.134000] Freeing unused kernel memory: 548k freed
[   13.134171] Write protecting the kernel text: 4184k
[   13.134292] Write protecting the kernel read-only data: 1552k
[   13.158523] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[   13.422643] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   13.422678] r8169 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.422700] r8169 0000:00:0b.0: PCI: Disallowing DAC for device
[   13.422845] r8169 0000:00:0b.0: no PCI Express capability
[   13.424244] eth0: RTL8169sb/8110sb at 0xf80c4f00, 00:08:54:55:6c:de, XID 10000000 IRQ 19
[   13.425932] FDC 0 is a post-1991 82077
[   13.485391] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   13.485513] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   13.491107] eth1: VIA Rhine II at 0xdfffbc00, 00:0b:6a:3a:c6:ff, IRQ 23.
[   13.491837] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   14.155372] PM: Starting manual resume from disk
[   14.155378] PM: Resume from partition 8:5
[   14.155380] PM: Checking hibernation image.
[   14.155729] PM: Resume from disk failed.
[   14.221657] kjournald starting.  Commit interval 5 seconds
[   14.221671] EXT3-fs: mounted filesystem with ordered data mode.
[   16.741653] udev: starting version 140
[   16.797062] udev: renamed network interface eth0 to eth2
[   16.861611] udev: renamed network interface eth1 to eth3
[   18.353360] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   18.507837] parport_pc 00:09: reported by Plug and Play ACPI
[   18.507964] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   18.763937] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.801234] Linux agpgart interface v0.103
[   18.813025] ppdev: user-space parallel port driver
[   18.846311] agpgart: Detected VIA PT800 chipset
[   18.853313] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   19.014781] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   19.014968] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   19.719543] lp0: using parport0 (interrupt-driven).
[   20.051251] Adding 634528k swap on /dev/sda5.  Priority:-1 extents:1 across:634528k
[   20.674257] EXT3 FS on sda1, internal journal
[   22.176375] type=1505 audit(1239651188.536:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1513
[   22.176644] type=1505 audit(1239651188.536:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1513
[   22.176714] type=1505 audit(1239651188.536:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1513
[   22.176771] type=1505 audit(1239651188.536:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1513
[   22.292358] type=1505 audit(1239651188.656:6): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1524
[   23.115482] r8169: eth2: link up
[   23.120149] eth3: link down
[   23.120384] ADDRCONF(NETDEV_UP): eth3: link is not ready
[   33.290008] eth2: no IPv6 routers present

```

---

