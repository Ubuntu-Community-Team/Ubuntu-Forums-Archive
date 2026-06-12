---
title: "System Hangs (8.04)"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by dlinear on 2008-06-04
Hello, I have run out of ideas and need community support. I have been running ubuntu since 6.06 on my home server and my recent machine upgrade has caused the system to randomly (after 2-6 hours) freeze. The screen shows the last X11 frame but the system is unusable. (ssh doesn't work either)

Recently I upgraded my server hardware (from an AMD athlon system ) to:
Intel Q9450 (quad-core 12MB Core 2)
Gigabyte GA-73PVM-S2H (with Nvidia GeoForce 7100 Video and nForce 630i chipset)

On this system I have apache, mysql, nfs, samba and a custom tvcapturing program that I wrote (captures frames from tvtime and audio)

During this upgrade I have replaced the motherboard three times due to memtest+86 failing constantly (and the machine rebooting by itself). The current motherboard has successfully passed memtest+86 for two nights so I feel comfortable the memory is okay (and the cpu cache for that matter!)

Basically I feel that the current problem is NOT a hardware one (anymore), but in fact a software one. I have run cpuburn (4 processes) for over an hour without a glitch. Additionally I have tested it with three power supplies and instead of restarting (a common sign of bad ram or PSU) the system just freezes instead, making me feel it's a linux kernel/driver issue. I would try an older kernel but I am sure most of my hardware is unsupported. 

- I have removed my additional usb card (my usb kvm does not like the nForce usb, a common but annoying problem), system still hangs
- I have disabled compiz, system still hangs
- I have swapped the tv-tuner card, system still hangs
- I have used the vesa driver with xawtv, system still hangs
- I have unplugged my iguanaIR usb device, system still hangs

I do not know what else to do. I tail -f /var/log/messages and see nothing of interest before the system crashes. Is there anything I can do to help narrow down what's wrong?

UNAME -A
> Linux commave 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux

DMESG OUTPUT
> 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-17-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 13:57:17 UTC 2008 (Ubuntu 2.6.24-17.31-generic)
[    0.000000] Command line: root=UUID=799ea51c-2ea6-4d82-ba18-20e7a40ffeee ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077000000 (usable)
[    0.000000]  BIOS-e820: 0000000077000000 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 000000007f000000 - 000000007fdf0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000d2000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 487424) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 520192, 523760) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6600 checksum 0
[    0.000000] ACPI: RSDP 000F6600, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FEF3040, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FEF3180, 52C6 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FEF1800, 0040
[    0.000000] ACPI: HPET 7FEF85C0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FEF8640, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FEF84C0, 0098 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT 7FEF8FA0, 02FC (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fdf0000
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 487424) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 520192, 523760) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fdf0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      158
[    0.000000]     0:      256 ->   487424
[    0.000000]     0:   520192 ->   523760
[    0.000000] On node 0 totalpages: 490894
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1221 pages reserved
[    0.000000]   DMA zone: 2721 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7104 pages used for memmap
[    0.000000]   DMA32 zone: 479792 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 0000000077000000 - 000000007f000000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:50100000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 482513
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=799ea51c-2ea6-4d82-ba18-20e7a40ffeee ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   17.724021] time.c: Detected 2666.665 MHz processor.
[   17.726771] Console: colour VGA+ 80x25
[   17.726774] console [tty0] enabled
[   17.726789] Checking aperture...
[   17.726797] Calgary: detecting Calgary via BIOS EBDA area
[   17.726799] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   17.750029] Memory: 1922268k/2095040k available (2488k kernel code, 41308k reserved, 1319k data, 320k init)
[   17.750074] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   17.830007] Calibrating delay using timer specific routine.. 5338.45 BogoMIPS (lpj=10676917)
[   17.830037] Security Framework initialized
[   17.830045] SELinux:  Disabled at boot.
[   17.830056] AppArmor: AppArmor initialized
[   17.830059] Failure registering capabilities with primary security module.
[   17.830196] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   17.831709] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.832429] Mount-cache hash table entries: 256
[   17.832537] Initializing cgroup subsys ns
[   17.832540] Initializing cgroup subsys cpuacct
[   17.832552] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.832553] CPU: L2 cache: 6144K
[   17.832555] CPU 0/0 -> Node 0
[   17.832556] using mwait in idle threads.
[   17.832557] CPU: Physical Processor ID: 0
[   17.832558] CPU: Processor Core ID: 0
[   17.832562] CPU0: Thermal monitoring enabled (TM2)
[   17.832574] SMP alternatives: switching to UP code
[   17.833228] Early unpacking initramfs... done
[   18.090154] ACPI: Core revision 20070126
[   18.090185] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.133660] Using local APIC timer interrupts.
[   18.171163] APIC timer calibration result 20833316
[   18.171164] Detected 20.833 MHz APIC timer.
[   18.171219] SMP alternatives: switching to SMP code
[   18.171772] Booting processor 1/4 APIC 0x1
[   18.182422] Initializing CPU#1
[   18.259167] Calibrating delay using timer specific routine.. 5333.34 BogoMIPS (lpj=10666693)
[   18.259172] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.259173] CPU: L2 cache: 6144K
[   18.259175] CPU 1/1 -> Node 0
[   18.259176] CPU: Physical Processor ID: 0
[   18.259176] CPU: Processor Core ID: 1
[   18.259181] CPU1: Thermal monitoring enabled (TM2)
[   18.259841] Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz stepping 07
[   18.259899] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   18.279969] SMP alternatives: switching to SMP code
[   18.280536] Booting processor 2/4 APIC 0x3
[   18.291167] Initializing CPU#2
[   18.371167] Calibrating delay using timer specific routine.. 5333.41 BogoMIPS (lpj=10666832)
[   18.371172] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.371173] CPU: L2 cache: 6144K
[   18.371174] CPU 2/3 -> Node 0
[   18.371175] CPU: Physical Processor ID: 0
[   18.371176] CPU: Processor Core ID: 3
[   18.371180] CPU2: Thermal monitoring enabled (TM2)
[   18.371840] Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz stepping 07
[   18.371868] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   18.391919] SMP alternatives: switching to SMP code
[   18.392324] Booting processor 3/4 APIC 0x2
[   18.402955] Initializing CPU#3
[   18.483167] Calibrating delay using timer specific routine.. 5333.40 BogoMIPS (lpj=10666818)
[   18.483171] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.483172] CPU: L2 cache: 6144K
[   18.483174] CPU 3/2 -> Node 0
[   18.483175] CPU: Physical Processor ID: 0
[   18.483176] CPU: Processor Core ID: 2
[   18.483180] CPU3: Thermal monitoring enabled (TM2)
[   18.483840] Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz stepping 07
[   18.483856] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   18.503869] Brought up 4 CPUs
[   18.503968] CPU0 attaching sched-domain:
[   18.503969]  domain 0: span 03
[   18.503970]   groups: 01 02
[   18.503972]   domain 1: span 0f
[   18.503973]    groups: 03 0c
[   18.503974]    domain 2: span 0f
[   18.503975]     groups: 0f
[   18.503977] CPU1 attaching sched-domain:
[   18.503978]  domain 0: span 03
[   18.503979]   groups: 02 01
[   18.503980]   domain 1: span 0f
[   18.503981]    groups: 03 0c
[   18.503982]    domain 2: span 0f
[   18.503983]     groups: 0f
[   18.503985] CPU2 attaching sched-domain:
[   18.503985]  domain 0: span 0c
[   18.503986]   groups: 04 08
[   18.503988]   domain 1: span 0f
[   18.503989]    groups: 0c 03
[   18.503990]    domain 2: span 0f
[   18.503991]     groups: 0f
[   18.503992] CPU3 attaching sched-domain:
[   18.503993]  domain 0: span 0c
[   18.503994]   groups: 08 04
[   18.503996]   domain 1: span 0f
[   18.503997]    groups: 0c 03
[   18.503998]    domain 2: span 0f
[   18.503999]     groups: 0f
[   18.504225] net_namespace: 120 bytes
[   18.504505] Time: 16:57:16  Date: 06/04/08
[   18.504521] NET: Registered protocol family 16
[   18.504648] ACPI: bus type pci registered
[   18.504697] PCI: Using configuration type 1
[   18.504699] mtrr: your CPUs had inconsistent fixed MTRR settings
[   18.504700] mtrr: probably your BIOS does not setup all CPUs.
[   18.504701] mtrr: corrected configuration.
[   18.505663] ACPI: EC: Look up EC in DSDT
[   18.509511] ACPI: Interpreter enabled
[   18.509513] ACPI: (supports S0 S1 S4 S5)
[   18.509531] ACPI: Using IOAPIC for interrupt routing
[   18.515571] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.516997] PCI: Transparent bridge - 0000:00:0a.0
[   18.517165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.517317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   18.552022] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[   18.552129] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.552236] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[   18.552341] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.552447] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.552552] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.552657] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.552762] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.552866] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.552972] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[   18.553078] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   18.553184] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   18.553289] ACPI: PCI Interrupt Link [LU1B] (IRQs 5 7 9 10 11 14 15) *0
[   18.553394] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 10 11 14 15) *0
[   18.553500] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[   18.553606] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[   18.553714] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.553821] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   18.553929] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.554036] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   18.554173] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   18.554300] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   18.554426] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   18.554550] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   18.554675] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   18.554799] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   18.554923] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   18.555047] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   18.555179] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[   18.555305] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[   18.555430] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
[   18.555555] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
[   18.555680] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
[   18.555805] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   18.555930] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   18.556056] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   18.556181] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   18.556306] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   18.556431] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   18.556556] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   18.556642] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.556661] pnp: PnP ACPI init
[   18.556666] ACPI: bus type pnp registered
[   18.559663] pnp: PnP ACPI: found 14 devices
[   18.559664] ACPI: ACPI bus type pnp unregistered
[   18.559819] PCI: Using ACPI for IRQ routing
[   18.559821] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.571200] NET: Registered protocol family 8
[   18.571202] NET: Registered protocol family 20
[   18.571231] PCI-GART: No AMD northbridge found.
[   18.571237] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   18.571240] hpet0: 3 32-bit timers, 25000000 Hz
[   18.572265] AppArmor: AppArmor Filesystem Enabled
[   18.575168] Time: tsc clocksource has been installed.
[   18.575174] Switched to high resolution mode on CPU 0
[   18.575880] Switched to high resolution mode on CPU 3
[   18.575888] Switched to high resolution mode on CPU 2
[   18.575914] Switched to high resolution mode on CPU 1
[   18.583155] system 00:01: ioport range 0x1000-0x107f has been reserved
[   18.583158] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   18.583160] system 00:01: ioport range 0x1400-0x147f has been reserved
[   18.583163] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   18.583165] system 00:01: ioport range 0x1800-0x187f has been reserved
[   18.583168] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   18.583170] system 00:01: iomem range 0x0-0x0 could not be reserved
[   18.583173] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   18.583176] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[   18.583178] system 00:01: iomem range 0x77000000-0x7effffff could not be reserved
[   18.583183] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   18.583185] system 00:02: ioport range 0x800-0x87f has been reserved
[   18.583188] system 00:02: ioport range 0x295-0x314 has been reserved
[   18.583190] system 00:02: ioport range 0x290-0x294 has been reserved
[   18.583192] system 00:02: ioport range 0x880-0x88f has been reserved
[   18.583201] system 00:0c: iomem range 0xd0000000-0xd1ffffff could not be reserved
[   18.583207] system 00:0d: iomem range 0xd0000-0xd3fff has been reserved
[   18.583209] system 00:0d: iomem range 0xd6800-0xd7fff has been reserved
[   18.583212] system 00:0d: iomem range 0xf0000-0xfbfff could not be reserved
[   18.583214] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   18.583217] system 00:0d: iomem range 0x7fef0000-0x7fefffff could not be reserved
[   18.583220] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[   18.583222] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   18.583225] system 00:0d: iomem range 0x100000-0x7feeffff could not be reserved
[   18.583227] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[   18.583230] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   18.583509] PCI: Bridge: 0000:00:0a.0
[   18.583510]   IO window: disabled.
[   18.583513]   MEM window: d5000000-d50fffff
[   18.583515]   PREFETCH window: d5100000-d51fffff
[   18.583517] PCI: Bridge: 0000:00:0b.0
[   18.583518]   IO window: 9000-9fff
[   18.583520]   MEM window: disabled.
[   18.583521]   PREFETCH window: disabled.
[   18.583523] PCI: Bridge: 0000:00:0c.0
[   18.583524]   IO window: b000-bfff
[   18.583526]   MEM window: disabled.
[   18.583528]   PREFETCH window: disabled.
[   18.583529] PCI: Bridge: 0000:00:0d.0
[   18.583531]   IO window: a000-afff
[   18.583532]   MEM window: disabled.
[   18.583534]   PREFETCH window: disabled.
[   18.583541] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   18.583548] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   18.583554] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   18.583560] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   18.583565] NET: Registered protocol family 2
[   18.619206] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   18.619624] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   18.620842] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   18.621275] TCP: Hash tables configured (established 262144 bind 65536)
[   18.621276] TCP reno registered
[   18.631266] checking if image is initramfs... it is
[   19.136752] Freeing initrd memory: 7515k freed
[   19.141504] audit: initializing netlink socket (disabled)
[   19.141514] audit(1212598636.336:1): initialized
[   19.144177] VFS: Disk quotas dquot_6.5.1
[   19.144247] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   19.144344] io scheduler noop registered
[   19.144346] io scheduler anticipatory registered
[   19.144347] io scheduler deadline registered
[   19.144466] io scheduler cfq registered (default)
[   19.168559] Boot video device is 0000:00:10.0
[   19.168739] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   19.168760] assign_interrupt_mode Found MSI capability
[   19.168779] Allocate Port Service[0000:00:0b.0:pcie00]
[   19.168854] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   19.168875] assign_interrupt_mode Found MSI capability
[   19.168891] Allocate Port Service[0000:00:0c.0:pcie00]
[   19.168963] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   19.168984] assign_interrupt_mode Found MSI capability
[   19.169000] Allocate Port Service[0000:00:0d.0:pcie00]
[   19.200042] Real Time Clock Driver v1.12ac
[   19.200209] hpet_resources: 0xfeff0000 is busy
[   19.200241] Linux agpgart interface v0.102
[   19.200243] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.200362] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.200899] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.201848] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.201913] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.202022] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   19.202023] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   19.202149] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.220683] mice: PS/2 mouse device common for all mice
[   19.220720] cpuidle: using governor ladder
[   19.220722] cpuidle: using governor menu
[   19.220853] NET: Registered protocol family 1
[   19.220941] registered taskstats version 1
[   19.221015]   Magic number: 12:438:994
[   19.221018]   hash matches device ttyd7
[   19.221019]   hash matches device ttyaa
[   19.221036] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   19.221037] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.221038] EDD information not available.
[   19.221046] Freeing unused kernel memory: 320k freed
[   19.240764] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.357413] fuse init (API version 7.9)
[   20.368980] ACPI: SSDT 7FEF86C0, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[   20.369188] ACPI: SSDT 7FEF8B80, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   20.369368] ACPI: SSDT 7FEF8CE0, 0152 (r1  PmRef  Cpu2Ist     3000 INTL 20040311)
[   20.369548] ACPI: SSDT 7FEF8E40, 0152 (r1  PmRef  Cpu3Ist     3000 INTL 20040311)
[   20.543225] usbcore: registered new interface driver usbfs
[   20.543241] usbcore: registered new interface driver hub
[   20.543258] usbcore: registered new device driver usb
[   20.550282] SCSI subsystem initialized
[   20.555738] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.556013] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[   20.556025] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [AUBA] -> GSI 23 (level, low) -> IRQ 23
[   20.558586] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   20.558591] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   20.558763] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 1
[   20.558776] ohci_hcd 0000:00:04.0: irq 23, io mem 0xd5207000
[   20.568940] libata version 3.00 loaded.
[   20.593135] Floppy drive(s): fd0 is 1.44M
[   20.611426] FDC 0 is a post-1991 82077
[   20.613638] usb usb1: configuration #1 chosen from 1 choice
[   20.613653] hub 1-0:1.0: USB hub found
[   20.613658] hub 1-0:1.0: 10 ports detected
[   20.720080] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   20.720089] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   20.770222] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[d5004000-d50047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   20.770616] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   20.770872] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   20.770878] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 22
[   20.770883] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   21.039016] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   21.253625] usb 1-1: configuration #1 chosen from 1 choice
[   21.288662] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:7d:d1:3d:c8
[   21.288665] forcedeth 0000:00:0f.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[   21.288965] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 21
[   21.288971] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [AUB2] -> GSI 21 (level, low) -> IRQ 21
[   21.291546] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   21.291550] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   21.291583] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[   21.291607] ehci_hcd 0000:00:04.1: debug port 1
[   21.291611] PCI: cache line size of 32 is not supported by device 0000:00:04.1
[   21.291619] ehci_hcd 0000:00:04.1: irq 21, io mem 0xd5208000
[   21.303005] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.303091] usb usb2: configuration #1 chosen from 1 choice
[   21.303109] hub 2-0:1.0: USB hub found
[   21.303113] hub 2-0:1.0: 10 ports detected
[   21.407108] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   21.407198] ahci 0000:00:0e.0: version 3.0
[   21.407445] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   21.407450] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   21.575007] usb 1-1: USB disconnect, address 2
[   22.039058] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00f2daac00001d7d]
[   22.310942] usb 2-3: new high speed USB device using ehci_hcd and address 4
[   22.410943] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   22.410947] ahci 0000:00:0e.0: flags: 64bit sntf led clo pmp pio 
[   22.410949] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   22.411385] scsi0 : ahci
[   22.411519] scsi1 : ahci
[   22.411613] scsi2 : ahci
[   22.411708] scsi3 : ahci
[   22.411759] ata1: SATA max UDMA/133 abar m8192@0xd5204000 port 0xd5204100 irq 508
[   22.411761] ata2: SATA max UDMA/133 abar m8192@0xd5204000 port 0xd5204180 irq 508
[   22.411763] ata3: SATA max UDMA/133 abar m8192@0xd5204000 port 0xd5204200 irq 508
[   22.411764] ata4: SATA max UDMA/133 abar m8192@0xd5204000 port 0xd5204280 irq 508
[   22.445316] usb 2-3: configuration #1 chosen from 1 choice
[   22.746916] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   22.961623] usb 1-1: configuration #1 chosen from 1 choice
[   23.050903] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.055103] ata1.00: ATA-6: WDC WD2500JD-22HBB0, 08.02D08, max UDMA/133
[   23.055106] ata1.00: 488397168 sectors, multi 0: LBA48 
[   23.060561] ata1.00: configured for UDMA/133
[   23.266886] usb 1-2: new low speed USB device using ohci_hcd and address 4
[   23.486622] usb 1-2: configuration #1 chosen from 1 choice
[   23.489670] usbcore: registered new interface driver libusual
[   23.494939] Initializing USB Mass Storage driver...
[   23.494994] scsi4 : SCSI emulation for USB Mass Storage devices
[   23.495032] usb-storage: device found at 4
[   23.495034] usb-storage: waiting for device to settle before scanning
[   23.495039] usbcore: registered new interface driver usb-storage
[   23.495041] USB Mass Storage support registered.
[   23.497069] usbcore: registered new interface driver hiddev
[   23.504824] input: Microsoft Microsoft Wireless Intellimouse Explorer® 1.0A as /devices/pci0000:00/0000:00:04.0/usb1/1-2/1-2:1.0/input/input2
[   23.530897] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft Wireless Intellimouse Explorer® 1.0A] on usb-0000:00:04.0-2
[   23.530910] usbcore: registered new interface driver usbhid
[   23.530912] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   23.699361] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.701472] ata2.00: ATA-7: Maxtor 6L100M0, BACE1G20, max UDMA/133
[   23.701474] ata2.00: 195813072 sectors, multi 0: LBA NCQ (depth 0/32)
[   23.704445] ata2.00: configured for UDMA/133
[   24.342827] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   24.717705] ata3.00: ATA-8: WDC WD7500AACS-00ZJB0, 01.01B01, max UDMA/133
[   24.717707] ata3.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   24.718498] ata3.00: configured for UDMA/133
[   25.034786] ata4: SATA link down (SStatus 0 SControl 300)
[   25.034860] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JD-22H 08.0 PQ: 0 ANSI: 5
[   25.034940] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6L100M0   BACE PQ: 0 ANSI: 5
[   25.035006] scsi 2:0:0:0: Direct-Access     ATA      WDC WD7500AACS-0 01.0 PQ: 0 ANSI: 5
[   25.035058] pata_amd 0000:00:08.0: version 0.3.10
[   25.035101] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   25.035388] scsi5 : pata_amd
[   25.035498] scsi6 : pata_amd
[   25.035866] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   25.035868] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   25.039701] Driver 'sd' needs updating - please use bus_type methods
[   25.039754] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.039761] sd 0:0:0:0: [sda] Write Protect is off
[   25.039762] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.039773] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.039819] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.039825] sd 0:0:0:0: [sda] Write Protect is off
[   25.039826] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.039836] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.039838]  sda: sda1
[   25.180767] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.180877] sd 1:0:0:0: [sdb] 195813072 512-byte hardware sectors (100256 MB)
[   25.180884] sd 1:0:0:0: [sdb] Write Protect is off
[   25.180886] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   25.180896] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.180923] sd 1:0:0:0: [sdb] 195813072 512-byte hardware sectors (100256 MB)
[   25.180929] sd 1:0:0:0: [sdb] Write Protect is off
[   25.180930] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   25.180939] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.180941]  sdb:<4>ata5.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   25.190945] ata5: failed to recover some devices, retrying in 5 secs
[   25.198622]  sdb1 sdb2 < sdb5 >
[   25.216333] sd 1:0:0:0: [sdb] Attached SCSI disk
[   25.216765] sd 2:0:0:0: [sdc] 1465149168 512-byte hardware sectors (750156 MB)
[   25.216772] sd 2:0:0:0: [sdc] Write Protect is off
[   25.216773] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   25.216783] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.216804] sd 2:0:0:0: [sdc] 1465149168 512-byte hardware sectors (750156 MB)
[   25.216809] sd 2:0:0:0: [sdc] Write Protect is off
[   25.216811] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   25.216821] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.216823]  sdc: sdc1
[   25.222074] sd 2:0:0:0: [sdc] Attached SCSI disk
[   25.224498] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.224515] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   25.224531] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   25.470475] Attempting manual resume
[   25.470477] swsusp: Resume From Partition 8:21
[   25.470478] PM: Checking swsusp image.
[   25.470543] PM: Resume from disk failed.
[   25.477762] EXT3-fs: INFO: recovery required on readonly filesystem.
[   25.477763] EXT3-fs: write access will be enabled during recovery.
[   26.673465] kjournald starting.  Commit interval 5 seconds
[   26.673476] EXT3-fs: sdb1: orphan cleanup on readonly fs
[   26.673480] ext3_orphan_cleanup: deleting unreferenced inode 3147251
[   26.673509] ext3_orphan_cleanup: deleting unreferenced inode 2834449
[   26.673516] ext3_orphan_cleanup: deleting unreferenced inode 2834440
[   26.673526] ext3_orphan_cleanup: deleting unreferenced inode 2834439
[   26.673529] ext3_orphan_cleanup: deleting unreferenced inode 2834438
[   26.673533] ext3_orphan_cleanup: deleting unreferenced inode 2834437
[   26.673536] ext3_orphan_cleanup: deleting unreferenced inode 2834436
[   26.673539] EXT3-fs: sdb1: 7 orphan inodes deleted
[   26.673540] EXT3-fs: recovery complete.
[   26.674837] EXT3-fs: mounted filesystem with ordered data mode.
[   28.494779] usb-storage: device scan complete
[   28.496276] scsi 4:0:0:0: Direct-Access     Maxtor 6 L250M0                PQ: 0 ANSI: 2 CCS
[   28.499890] sd 4:0:0:0: [sdd] 490234752 512-byte hardware sectors (251000 MB)
[   28.502767] sd 4:0:0:0: [sdd] Write Protect is off
[   28.502769] sd 4:0:0:0: [sdd] Mode Sense: 00 38 00 00
[   28.502770] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[   28.506889] sd 4:0:0:0: [sdd] 490234752 512-byte hardware sectors (251000 MB)
[   28.509764] sd 4:0:0:0: [sdd] Write Protect is off
[   28.509765] sd 4:0:0:0: [sdd] Mode Sense: 00 38 00 00
[   28.509767] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[   28.509769]  sdd: sdd1
[   28.535436] sd 4:0:0:0: [sdd] Attached SCSI disk
[   28.535455] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   30.350645] ata5.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   30.350648] ata5: failed to recover some devices, retrying in 5 secs
[   35.302304] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.334412] input: Power Button (FF) as /devices/virtual/input/input3
[   35.366216] ACPI: Power Button (FF) [PWRF]
[   35.366261] input: Power Button (CM) as /devices/virtual/input/input4
[   35.398193] ACPI: Power Button (CM) [PWRB]
[   35.406176] Linux video capture interface: v2.00
[   35.510476] ata5.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   35.510478] ata5: failed to recover some devices, retrying in 5 secs
[   35.702105] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   35.750836] ACPI: WMI-Acer: Mapper loaded
[   35.814497] parport_pc 00:0a: reported by Plug and Play ACPI
[   35.814540] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   35.940928] bttv: driver version 0.9.17 loaded
[   35.940930] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   36.199561] NET: Registered protocol family 10
[   36.199700] lo: Disabled Privacy Extensions
[   40.834305] ata5.00: ATAPI: SAMSUNG CD-R/RW SW-248F, R602, max UDMA/33
[   41.006212] ata5.00: configured for UDMA/33
[   41.006263] ata6: port disabled. ignoring.
[   41.007892] scsi 5:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-248F  R602 PQ: 0 ANSI: 5
[   41.007959] scsi 5:0:0:0: Attached scsi generic sg4 type 5
[   41.008049] bttv: Bt8xx card found (0).
[   41.008332] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   41.008337] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   41.008346] bttv0: Bt878 (rev 17) at 0000:01:05.0, irq: 16, latency: 32, mmio: 0xd5100000
[   41.008352] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[   41.008354] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[   41.008378] bttv0: gpio: en=00000000, out=00000000 in=00bf7707 [init]
[   41.008727] bttv0: tuner type=5
[   41.008728] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   41.009328] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   41.009933] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   41.058258] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   41.058276] tuner-simple 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   41.058278] tuner 0-0061: type set to Philips PAL_BG (FI1
[   41.058280] tuner-simple 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   41.058281] tuner 0-0061: type set to Philips PAL_BG (FI1
[   41.066888] bttv0: registered device video0
[   41.066909] bttv0: registered device vbi0
[   41.066931] bttv0: registered device radio0
[   41.066959] bttv0: PLL: 28636363 => 35468950 ..<4>Driver 'sr' needs updating - please use bus_type methods
[   41.098866]  ok
[   41.099564] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:0a.0/0000:01:05.0/input/input6
[   41.103336] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   41.103339] Uniform CD-ROM driver Revision: 3.20
[   41.103376] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   41.162914] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.163281] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   41.163283] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   41.165077] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   41.169839] bt878: AUDIO driver version 0.0.0 loaded
[   41.228187] bt878: Bt878 AUDIO function found (0).
[   41.228203] ACPI: PCI Interrupt 0000:01:05.1[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   41.228208] bt878_probe: card id=[0x6606107d], Unknown card.
[   41.228209] Exiting..
[   41.228212] ACPI: PCI interrupt for device 0000:01:05.1 disabled
[   41.228215] bt878: probe of 0000:01:05.1 failed with error -22
[   41.246012] ACPI: PCI Interrupt 0000:01:05.1[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   41.247977] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/bt87x.c:947: bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   41.791153] lp0: using parport0 (interrupt-driven).
[   41.865416] Adding 2811332k swap on /dev/sdb5.  Priority:-1 extents:1 across:2811332k
[   42.410469] EXT3 FS on sdb1, internal journal
[   46.549543] eth0: no IPv6 routers present
[   55.250781] kjournald starting.  Commit interval 5 seconds
[   55.257469] EXT3 FS on sda1, internal journal
[   55.257473] EXT3-fs: mounted filesystem with ordered data mode.
[   55.261192] kjournald starting.  Commit interval 5 seconds
[   55.269146] EXT3 FS on sdc1, internal journal
[   55.269149] EXT3-fs: mounted filesystem with ordered data mode.
[   55.628176] ip_tables: (C) 2000-2006 Netfilter Core Team
[   56.876648] RPC: Registered udp transport module.
[   56.876651] RPC: Registered tcp transport module.
[   57.494431] No dock devices found.
[   60.293316] ppdev: user-space parallel port driver
[   60.761176] audit(1212598679.042:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6311 profile="/usr/sbin/cupsd" namespace="default"
[   61.544741] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   62.033789] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   62.061661] NFSD: starting 90-second grace period
[   67.274863] Bluetooth: Core ver 2.11
[   67.274959] NET: Registered protocol family 31
[   67.274962] Bluetooth: HCI device and connection manager initialized
[   67.274967] Bluetooth: HCI socket layer initialized
[   67.377889] Bluetooth: L2CAP ver 2.9
[   67.377894] Bluetooth: L2CAP socket layer initialized
[   67.380322] Bluetooth: RFCOMM socket layer initialized
[   67.380335] Bluetooth: RFCOMM TTY layer initialized
[   67.380336] Bluetooth: RFCOMM ver 1.8
[  278.714565] nvidia: module license 'NVIDIA' taints kernel.
[  278.968743] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22

[  278.968748] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [AIGP] -> GSI 22 (level, low) -> IRQ 22
[  278.968755] PCI: Setting latency timer of device 0000:00:10.0 to 64
[  278.968899] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[  305.964026] bttv0: PLL can sleep, using XTAL (28636363).
[  313.393287] bttv0: SCERR @ 76c4c014,bits: OFLOW FDSR SCERR*
[  313.660233] bttv0: SCERR @ 76c4c014,bits: OFLOW FDSR SCERR*
[  317.397512] bttv0: SCERR @ 76c4c014,bits: OFLOW FDSR SCERR*


(PS. my network led indicator acts strangely during these system hangs. sometimes after a system hang the data indicator is blinking non-stop till a restart... I guess I will try another network card after the next crash too.)

---

### Post by hal8000 on 2008-06-04
I sympathize with you and hate these intermittant faults.

Some things you can try.
Make sure all fans, CPU heatsinks are clean, could be a sympton of overheating, and I would also run your computer with the case lid open to
see if it makes any difference.

Not sure how much power you need for a quad core but check your PSU ratings.

Strange that you have replaced the motherboard three times, I would check that memory is not overheating, again leave case lid offs to see if more air flow helps.

Finally if you have a live CD of knoppix or any other bootable CD/DVD you could try booting and leave to see if you have any instabilities.
Hope that helps.

---

### Post by dlinear on 2008-06-04
> **hal8000 said:**
> I sympathize with you and hate these intermittant faults.

Some things you can try.
Make sure all fans, CPU heatsinks are clean, could be a sympton of overheating, and I would also run your computer with the case lid open to
see if it makes any difference.

I have reapplied with thermal grease three times to the CPU and stock fan. When I did cpuburn the heatsink got quite hot but the system did not freeze. Also I have a thermometer in my case, typically it at between 87 and 97 degrees Fahrenheit.

> 
Not sure how much power you need for a quad core but check your PSU ratings.
My PSU is rated at 400W. I have a power meter between my system and the AC outlet telling me I am only using 120W. Also I am using this PSU primarily (FSP Group ZEN 400 ATX 2.2V 400W Fanless Power Supply) I would highly recommend this to anyone who does not need a gamers rig and wants to help the environment and lower ambient sounds 

> 
Strange that you have replaced the motherboard three times, I would check that memory is not overheating, again leave case lid offs to see if more air flow helps.
While I have had the case off for multiple hours I would think the opposite would happen. The case creates an air flow with cold air coming in the front and hot air exiting the rear. Removing the cover will disrupt this and likely cause more failures (not in my current situation)

> Finally if you have a live CD of knoppix or any other bootable CD/DVD you could try booting and leave to see if you have any instabilities.
I might try that next. I think before that I will test the current system under idle loads and see how long it lasts....

> Hope that helps.
Always does! :)

---

### Post by hal8000 on 2008-06-04
> **dlinear said:**
> 
My PSU is rated at 400W. I have a power meter between my system and the AC outlet telling me I am only using 120W. Also I am using this PSU primarily (FSP Group ZEN 400 ATX 2.2V 400W Fanless Power Supply) I would highly recommend this to anyone who does not need a gamers rig and wants to help the environment and lower ambient sounds 




I think this is your problem, 400W may be rather low for a quad core.
Had a quick look on google a lot of quad core users have 500 and 600W PSU's.

[http://discuss.extremetech.com/forums/thread/1004374049.aspx](http://discuss.extremetech.com/forums/thread/1004374049.aspx)

You have to remember two things:
1) Your power meter is measuring average power which is 120W. It cannot
measure small changes (microseconds) and less when all your CPU cores conduct and process information. It may be only microseconds for millions of operations, but if the current isnt there, then you will get some erratic function.

2) Your PSU rated and actual limits will differ.

I could be wrong about the power requirements, but my Intel pentium 4 2.8Ghz computer has a 650W PSU and that is what the computer shop supplied, (of course it could be all they had...)

If you can borrow a higher wattage PSU try that, your power meter will still read 120W but I'd do some digging and see what Intel recommend for your quad core.
Hope that helps.

---

### Post by dlinear on 2008-06-05
> **hal8000 said:**
> I think this is your problem, 400W may be rather low for a quad core.
Had a quick look on google a lot of quad core users have 500 and 600W PSU's.

[http://discuss.extremetech.com/forums/thread/1004374049.aspx](http://discuss.extremetech.com/forums/thread/1004374049.aspx)

You have to remember two things:
1) Your power meter is measuring average power which is 120W. It cannot
measure small changes (microseconds) and less when all your CPU cores conduct and process information. It may be only microseconds for millions of operations, but if the current isnt there, then you will get some erratic function.

2) Your PSU rated and actual limits will differ.

I could be wrong about the power requirements, but my Intel pentium 4 2.8Ghz computer has a 650W PSU and that is what the computer shop supplied, (of course it could be all they had...)

If you can borrow a higher wattage PSU try that, your power meter will still read 120W but I'd do some digging and see what Intel recommend for your quad core.
Hope that helps.

The link you posted mentions a system with a gamers video card. That is the main reason to get a better PSU (dual SLI's need 700-1000W PSU's, that's crazy). I have no video cards, I am using the onboard GPU.

The link includes a PSU recommender link. I filled it in, biased towards to much power (100 load, etc) and I was recommended a 240 Watt supply.

Pentium 4's use way to much power, the reason I had an AMD and why Intel was in minor trouble a few years back. The Q9450 is supposed to be rated at 95W meaning my PSU can supply enough power from one 12V rail (14A*12V = 162Watts) and it contains two 12V rails (14A and 13A) and supports multi-core systems. The main reason I purchased the Q9450 was because it is using 45nm technology and therefore should use less power per operation.

If it turned out to be the power supply I would be really bummed since I paid $140 for this high quality, high efficiency, fan less PSU. ...

I have already tested another 500W earlier this week on a different motherboard. The system freeze was still happening then (plus I had memory problems from that motherboard)

I noticed earlier today that my fan in the back had come unplugged. With a fanless PSU there was nothing sucking the hot air out. I suddenly threw my arms up in air thinking you had discovered the problem. I threw my program on and said a little prayer. About 30 minutes ago it the system crashed again.

I do not think the hardware itself is the problem. More likely I think there is a driver/hardware issue. Is there anyway I can enable more debugging?

---

### Post by hal8000 on 2008-06-05
> **dlinear said:**
> 

Is there anyway I can enable more debugging?


The problem you have is that your system works ok for a while before freezing.
If it happened on boot, you can press alt-F1 to bypass the splash screen and watch the boot messages- but this wont help in your case.

If you havent already tried it download a copy of Knoppix 5.1.1 on CD and boot with that. At least using differnt software and a different kernel may be the way to go here, if knoppix works ok, then you are looking at software issues, if knoppix freezes, then it would mean checking the hardwrae.

---

### Post by dlinear on 2008-06-05
> **hal8000 said:**
> The problem you have is that your system works ok for a while before freezing.
If it happened on boot, you can press alt-F1 to bypass the splash screen and watch the boot messages- but this wont help in your case.

If you havent already tried it download a copy of Knoppix 5.1.1 on CD and boot with that. At least using differnt software and a different kernel may be the way to go here, if knoppix works ok, then you are looking at software issues, if knoppix freezes, then it would mean checking the hardwrae.

Not exactly the answer I was looking for on an unbuntu forum...

It appears I am experiencing a major bug (for some) that has been going on for quite some time. Random kernel lockups caused by unknown forces.

The good news is my Q9450, motherboard, PSU, and memory appear to be working great!

The bad news is Ubuntu is broken!

[http://ubuntuforums.org/showthread.php?t=768200&highlight=hardy+freeze]("http://ubuntuforums.org/showthread.php?t=768200&highlight=hardy+freeze")

---

