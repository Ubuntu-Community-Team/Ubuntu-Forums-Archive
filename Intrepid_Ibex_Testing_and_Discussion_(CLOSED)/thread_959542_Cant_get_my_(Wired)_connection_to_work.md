---
title: "Cant get my (Wired) connection to work"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Spanklord on 2008-10-26
i upgraded to 8.10 from 8.04 and suddenly my network card wasnt detected anymore 

i got a m2npv-vm motherboard wich has nforce 430 chipset on it 

if i type in lshw -C network i get something back with logic name pan0 wich i dont know where it came from but anyways . anybody got an idea ?


im not to expirienced with ubuntu. and i dual boot with xp so i have to switch over every time to post something or to get some new info. so bare with me plz

this is what dmesg gave me

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3fef0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3f67f000 - 3fedf4f6
[    0.000000] Allocated new RAMDISK: 005c4000 - 00e244f6
[    0.000000] Move RAMDISK from 000000003f67f000 - 000000003fedf4f5 to 005c4000 - 00e244f5
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F7640, 0024 (r2 Nvidia)
[    0.000000] ACPI: XSDT 3FEF3100, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEF9D80, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FEF3280, 6AC0 (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 3FEF0000, 0040
[    0.000000] ACPI: HPET 3FEF9F80, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 3FEFA000, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FEF9EC0, 007C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00005c4000 - 0000e244f6]      NEW RAMDISK ==> [00005c4000 - 0000e244f6]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f5ab0] 000f5ab0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003fef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fef0
[    0.000000] On node 0 totalpages: 261775
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32210 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259473
[    0.000000] Kernel command line: root=UUID=8C009C61009C5454 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2204.557 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1023216k/1047488k available (2572k kernel code, 23600k reserved, 1160k data, 424k init, 129984k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4409.11 BogoMIPS (lpj=8818228)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(2) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017441] ACPI: Core revision 20080609
[    0.019282] ACPI: Checking initramfs for custom DSDT
[    0.352362] ENABLING IO-APIC IRQs
[    0.352585] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.392973] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.396024] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4409.22 BogoMIPS (lpj=8818451)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.480159] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.480184] Brought up 2 CPUs
[    0.480187] Total of 2 processors activated (8818.33 BogoMIPS).
[    0.480229] CPU0 attaching sched-domain:
[    0.480231]  domain 0: span 0-1 level CPU
[    0.480234]   groups: 0 1
[    0.480239] CPU1 attaching sched-domain:
[    0.480241]  domain 0: span 0-1 level CPU
[    0.480244]   groups: 1 0
[    0.480301] net_namespace: 840 bytes
[    0.480301] Booting paravirtualized kernel on bare hardware
[    0.480301] Time: 21:31:54  Date: 10/26/08
[    0.480301] NET: Registered protocol family 16
[    0.480306] EISA bus registered
[    0.480306] ACPI: bus type pci registered
[    0.480306] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.480306] PCI: MCFG area at e0000000 reserved in E820
[    0.480306] PCI: Using MMCONFIG for extended config space
[    0.480306] PCI: Using configuration type 1 for base access
[    0.481007] ACPI: EC: Look up EC in DSDT
[    0.494619] ACPI: Interpreter enabled
[    0.494623] ACPI: (supports S0 S1 S3 S4 S5)
[    0.494639] ACPI: Using IOAPIC for interrupt routing
[    0.504197] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.508108] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508111] pci 0000:00:04.0: PME# disabled
[    0.508313] PCI: 0000:00:0a.1 reg 20 io port: [4c00, 4c3f]
[    0.508319] PCI: 0000:00:0a.1 reg 24 io port: [4c40, 4c7f]
[    0.508337] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.508343] pci 0000:00:0a.1: PME# disabled
[    0.508398] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.508423] pci 0000:00:0b.0: supports D1
[    0.508425] pci 0000:00:0b.0: supports D2
[    0.508427] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508431] pci 0000:00:0b.0: PME# disabled
[    0.508452] PCI: 0000:00:0b.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    0.508478] pci 0000:00:0b.1: supports D1
[    0.508480] pci 0000:00:0b.1: supports D2
[    0.508482] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508486] pci 0000:00:0b.1: PME# disabled
[    0.508518] PCI: 0000:00:0d.0 reg 20 io port: [f400, f40f]
[    0.508554] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.508559] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.508564] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.508569] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.508573] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]
[    0.508578] PCI: 0000:00:0e.0 reg 24 32bit mmio: [fe02d000, fe02dfff]
[    0.508614] PCI: 0000:00:0f.0 reg 10 io port: [9e0, 9e7]
[    0.508619] PCI: 0000:00:0f.0 reg 14 io port: [be0, be3]
[    0.508623] PCI: 0000:00:0f.0 reg 18 io port: [960, 967]
[    0.508627] PCI: 0000:00:0f.0 reg 1c io port: [b60, b63]
[    0.508632] PCI: 0000:00:0f.0 reg 20 io port: [cc00, cc0f]
[    0.508637] PCI: 0000:00:0f.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
[    0.508702] PCI: 0000:00:10.1 reg 10 32bit mmio: [fe024000, fe027fff]
[    0.508731] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.508734] pci 0000:00:10.1: PME# disabled
[    0.508759] PCI: 0000:00:14.0 reg 10 32bit mmio: [fe02b000, fe02bfff]
[    0.508764] PCI: 0000:00:14.0 reg 14 io port: [c800, c807]
[    0.508784] pci 0000:00:14.0: supports D1
[    0.508786] pci 0000:00:14.0: supports D2
[    0.508788] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508792] pci 0000:00:14.0: PME# disabled
[    0.508877] PCI: 0000:01:00.0 reg 10 32bit mmio: [fa000000, faffffff]
[    0.508881] PCI: 0000:01:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.508891] PCI: 0000:01:00.0 reg 1c 64bit mmio: [f8000000, f9ffffff]
[    0.508896] PCI: 0000:01:00.0 reg 24 io port: [ac00, ac7f]
[    0.508901] PCI: 0000:01:00.0 reg 30 32bit mmio: [fbfe0000, fbffffff]
[    0.508945] PCI: bridge 0000:00:04.0 io port: [a000, afff]
[    0.508948] PCI: bridge 0000:00:04.0 32bit mmio: [f8000000, fbffffff]
[    0.508951] PCI: bridge 0000:00:04.0 64bit mmio pref: [d0000000, dfffffff]
[    0.508983] PCI: 0000:02:05.0 reg 10 32bit mmio: [fdeff000, fdeff7ff]
[    0.508989] PCI: 0000:02:05.0 reg 14 32bit mmio: [fdef8000, fdefbfff]
[    0.509020] pci 0000:02:05.0: supports D1
[    0.509021] pci 0000:02:05.0: supports D2
[    0.509023] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot
[    0.509027] pci 0000:02:05.0: PME# disabled
[    0.509055] pci 0000:00:10.0: transparent bridge
[    0.509058] PCI: bridge 0000:00:10.0 io port: [b000, bfff]
[    0.509061] PCI: bridge 0000:00:10.0 32bit mmio: [fde00000, fdefffff]
[    0.509065] PCI: bridge 0000:00:10.0 32bit mmio pref: [fdd00000, fddfffff]
[    0.509071] bus 00 -> node 0
[    0.509078] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.509536] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.582947] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.582947] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.584177] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.584385] ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
[    0.584592] ACPI: PCI Interrupt Link [LNK5] (IRQs *5 7 9 10 11 14 15)
[    0.584798] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.585005] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.585212] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.585420] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.585627] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.585836] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[    0.586043] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.586252] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.586459] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.586667] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.586876] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[    0.587083] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.587289] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.587498] ACPI: PCI Interrupt Link [LSID] (IRQs *5 7 9 10 11 14 15)
[    0.587706] ACPI: PCI Interrupt Link [LFID] (IRQs *5 7 9 10 11 14 15)
[    0.587963] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.588222] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.588472] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.588722] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.588972] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.589221] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.589471] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.589721] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.589971] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.590222] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.590474] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.590725] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.590982] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.591233] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.591484] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.591736] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.591987] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.592246] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.592499] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.592750] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.593001] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.593072] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.593072] pnp: PnP ACPI init
[    0.593072] ACPI: bus type pnp registered
[    0.600301] pnp: PnP ACPI: found 15 devices
[    0.600301] ACPI: ACPI bus type pnp unregistered
[    0.600301] PnPBIOS: Disabled by ACPI PNP
[    0.600301] PCI: Using ACPI for IRQ routing
[    0.608041] NET: Registered protocol family 8
[    0.608044] NET: Registered protocol family 20
[    0.608067] NetLabel: Initializing
[    0.608068] NetLabel:  domain hash size = 128
[    0.608070] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.608084] NetLabel:  unlabeled traffic allowed by default
[    0.608092] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[    0.608097] hpet0: 3 32-bit timers, 25000000 Hz
[    0.609653] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.609655]    actual entries 65620
[    0.609789] AppArmor: AppArmor Filesystem Enabled
[    0.609819] ACPI: RTC can wake from S4
[    0.612045] Switched to high resolution mode on CPU 0
[    0.612198] Switched to high resolution mode on CPU 1
[    0.616033] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.616036] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.616039] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.616042] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.616045] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.616048] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.616050] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.616053] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.616060] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.616063] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.616066] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.616079] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.616085] system 00:0e: iomem range 0xf0000-0xf3fff could not be reserved
[    0.616088] system 00:0e: iomem range 0xf4000-0xf7fff could not be reserved
[    0.616091] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[    0.616094] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[    0.616097] system 00:0e: iomem range 0xfefff000-0xfefff0ff could not be reserved
[    0.616100] system 00:0e: iomem range 0x3fef0000-0x3fefffff could not be reserved
[    0.616103] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.616106] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.616110] system 00:0e: iomem range 0x100000-0x3feeffff could not be reserved
[    0.616113] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.616116] system 00:0e: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.616119] system 00:0e: iomem range 0xfefff000-0xfeffffff could not be reserved
[    0.616122] system 00:0e: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.616126] system 00:0e: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.616129] system 00:0e: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.651465] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.651469] pci 0000:00:04.0:   IO window: 0xa000-0xafff
[    0.651472] pci 0000:00:04.0:   MEM window: 0xf8000000-0xfbffffff
[    0.651476] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.651480] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.651483] pci 0000:00:10.0:   IO window: 0xb000-0xbfff
[    0.651487] pci 0000:00:10.0:   MEM window: 0xfde00000-0xfdefffff
[    0.651490] pci 0000:00:10.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.651501] pci 0000:00:04.0: setting latency timer to 64
[    0.651506] pci 0000:00:10.0: setting latency timer to 64
[    0.651509] bus: 00 index 0 io port: [0, ffff]
[    0.651511] bus: 00 index 1 mmio: [0, ffffffff]
[    0.651513] bus: 01 index 0 io port: [a000, afff]
[    0.651515] bus: 01 index 1 mmio: [f8000000, fbffffff]
[    0.651517] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.651519] bus: 01 index 3 mmio: [0, 0]
[    0.651522] bus: 02 index 0 io port: [b000, bfff]
[    0.651524] bus: 02 index 1 mmio: [fde00000, fdefffff]
[    0.651526] bus: 02 index 2 mmio: [fdd00000, fddfffff]
[    0.651528] bus: 02 index 3 io port: [0, ffff]
[    0.651530] bus: 02 index 4 mmio: [0, ffffffff]
[    0.651542] NET: Registered protocol family 2
[    0.664058] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.664334] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.664983] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.665309] TCP: Hash tables configured (established 131072 bind 65536)
[    0.665312] TCP reno registered
[    0.672086] NET: Registered protocol family 1
[    0.672205] checking if image is initramfs... it is
[    1.355512] Freeing initrd memory: 8577k freed
[    1.356800] audit: initializing netlink socket (disabled)
[    1.356818] type=2000 audit(1225056715.356:1): initialized
[    1.362322] highmem bounce pool size: 64 pages
[    1.362328] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.364939] VFS: Disk quotas dquot_6.5.1
[    1.365041] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.365136] msgmni has been set to 1761
[    1.365247] io scheduler noop registered
[    1.365250] io scheduler anticipatory registered
[    1.365252] io scheduler deadline registered
[    1.365263] io scheduler cfq registered (default)
[    1.365278] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.365313] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.365336] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.381056] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.381067] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.381077] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.381088] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.381109] pci 0000:01:00.0: Boot video device
[    1.381229] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.381253] pcieport-driver 0000:00:04.0: found MSI capability
[    1.381273] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.381326] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.381715] isapnp: Scanning for PnP cards...
[    1.734510] isapnp: No Plug & Play device found
[    1.773284] hpet_resources: 0xfefff000 is busy
[    1.773391] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.773542] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.773724] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.774366] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.774681] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.776850] brd: module loaded
[    1.776933] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.777078] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.777081] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.777238] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.781141] mice: PS/2 mouse device common for all mice
[    1.781288] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.781321] rtc0: alarms up to one year, y3k, hpet irqs
[    1.781486] EISA: Probing bus 0 at eisa.0
[    1.781499] Cannot allocate resource for EISA slot 2
[    1.781503] Cannot allocate resource for EISA slot 4
[    1.781516] EISA: Detected 0 cards.
[    1.781519] cpuidle: using governor ladder
[    1.781521] cpuidle: using governor menu
[    1.781992] TCP cubic registered
[    1.782017] Using IPI No-Shortcut mode
[    1.782233] registered taskstats version 1
[    1.782372]   Magic number: 12:684:551
[    1.782517] pci_link PNP0C0F:02: hash matches
[    1.782569] rtc_cmos 00:05: setting system clock to 2008-10-26 21:31:56 UTC (1225056716)
[    1.782572] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.782574] EDD information not available.
[    1.782846] Freeing unused kernel memory: 424k freed
[    1.782904] Write protecting the kernel text: 2576k
[    1.782942] Write protecting the kernel read-only data: 936k
[    1.799005] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.923047] fuse init (API version 7.9)
[    2.000200] fan PNP0C0B:00: registered as cooling_device0
[    2.000207] ACPI: Fan [FAN] (on)
[    2.016218] processor ACPI0007:00: registered as cooling_device1
[    2.016293] processor ACPI0007:01: registered as cooling_device2
[    2.018999] thermal LNXTHERM:01: registered as thermal_zone0
[    2.019506] ACPI: Thermal Zone [THRM] (40 C)
[    2.629085] usbcore: registered new interface driver usbfs
[    2.629108] usbcore: registered new interface driver hub
[    2.629160] usbcore: registered new device driver usb
[    2.641088] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.641580] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    2.641593] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    2.641606] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.641609] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.641662] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.641688] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xfe02f000
[    2.688250] No dock devices found.
[    2.702170] usb usb1: configuration #1 chosen from 1 choice
[    2.702199] hub 1-0:1.0: USB hub found
[    2.702210] hub 1-0:1.0: 8 ports detected
[    2.710035] SCSI subsystem initialized
[    2.784552] libata version 3.00 loaded.
[    2.913546] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    2.913560] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    2.913574] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.913577] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.913703] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    2.913733] ehci_hcd 0000:00:0b.1: debug port 1
[    2.913737] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    2.913756] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xfe02e000
[    3.084021] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    3.096023] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.096185] usb usb2: configuration #1 chosen from 1 choice
[    3.096211] hub 2-0:1.0: USB hub found
[    3.096221] hub 2-0:1.0: 8 ports detected
[    3.152025] hub 1-0:1.0: unable to enumerate USB device on port 1
[    3.304345] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.304784] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    3.304796] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 21 (level, low) -> IRQ 21
[    3.304801] forcedeth 0000:00:14.0: setting latency timer to 64
[    3.304827] nv_probe: set workaround bit for reversed mac addr
[    3.824481] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:17:31:c4:8a:b3
[    3.824486] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[    3.825039] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    3.825050] ohci1394 0000:02:05.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    3.874779] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.878014] pata_amd 0000:00:0d.0: version 0.3.10
[    3.878073] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.878444] scsi0 : pata_amd
[    3.878547] scsi1 : pata_amd
[    3.879500] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    3.879503] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    4.049187] ata1.00: ATA-5: WDC WD600BB-00CAA1, 17.07W17, max UDMA/100
[    4.049191] ata1.00: 117231408 sectors, multi 1: LBA 
[    4.049357] ata1.01: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/133
[    4.049359] ata1.01: 80293248 sectors, multi 1: LBA 
[    4.049372] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6c7c000) ACPI=0x3f01f (20:15:0x1f)
[    4.049377] ata1: nv_mode_filter: 0x7f39f&0x7f01f->0x7f01f, BIOS=0x7f000 (0xc6c7c000) ACPI=0x7f01f (20:15:0x1f)
[    4.065125] ata1.00: configured for UDMA/100
[    4.080401] ata1.01: configured for UDMA/133
[    4.120026] usb 1-1: new full speed USB device using ohci_hcd and address 3
[    4.334413] usb 1-1: configuration #1 chosen from 1 choice
[    4.524347] ata2.00: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-105S 0122, E1.22, max UDMA/33
[    4.524362] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc6c7c000) ACPI=0x701f (60:600:0x13)
[    4.544279] ata2.00: configured for UDMA/33
[    4.544383] scsi 0:0:0:0: Direct-Access     ATA      WDC WD600BB-00CA 17.0 PQ: 0 ANSI: 5
[    4.544522] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[    4.545897] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-ROM DVD-105  1.22 PQ: 0 ANSI: 5
[    4.546564] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    4.546575] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    4.546609] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    4.546621] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    4.547010] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[    4.547013] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
[    4.547030] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    4.547037] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    4.551148] sata_nv 0000:00:0e.0: version 3.5
[    4.551164] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    4.551167] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    4.551215] sata_nv 0000:00:0e.0: setting latency timer to 64
[    4.551994] scsi2 : sata_nv
[    4.552308] scsi3 : sata_nv
[    4.552517] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20
[    4.552521] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20
[    4.559281] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.559317] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[    4.559351] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    4.572501] Driver 'sd' needs updating - please use bus_type methods
[    4.572633] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[    4.572652] sd 0:0:0:0: [sda] Write Protect is off
[    4.572654] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.572683] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.572750] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[    4.572765] sd 0:0:0:0: [sda] Write Protect is off
[    4.572768] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.572795] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.572799]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.594474]  sda1
[    4.594604] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.595219] sd 0:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[    4.595244] sd 0:0:1:0: [sdb] Write Protect is off
[    4.595247] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.595287] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.595365] sd 0:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[    4.595386] sd 0:0:1:0: [sdb] Write Protect is off
[    4.595389] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.595428] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.595432]  sdb: sdb1
[    4.602638] sd 0:0:1:0: [sdb] Attached SCSI disk
[    4.605482] sr0: scsi3-mmc drive: 16x/40x cd/rw xa/form2 cdda tray
[    4.605487] Uniform CD-ROM driver Revision: 3.20
[    4.605574] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.641022] usb 1-2: new full speed USB device using ohci_hcd and address 4
[    4.882469] ata3: SATA link down (SStatus 0 SControl 300)
[    4.899176] usb 1-2: configuration #1 chosen from 1 choice
[    5.145132] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000b7b646]
[    5.204021] usb 1-4: new low speed USB device using ohci_hcd and address 5
[    5.210442] ata4: SATA link down (SStatus 0 SControl 300)
[    5.210493] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
[    5.210497] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    5.210550] sata_nv 0000:00:0f.0: setting latency timer to 64
[    5.210700] scsi4 : sata_nv
[    5.210798] scsi5 : sata_nv
[    5.211011] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 23
[    5.211014] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 23
[    5.240552] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[    5.402182] usb 1-4: configuration #1 chosen from 1 choice
[    5.406075] usbcore: registered new interface driver hiddev
[    5.418116] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.3/input/input2
[    5.418495] input,hidraw0: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:0b.0-2
[    5.423294] input: USB Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input3
[    5.424156] input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:0b.0-4
[    5.424174] usbcore: registered new interface driver usbhid
[    5.424178] usbhid: v2.6:USB HID core driver
[    5.538446] ata5: SATA link down (SStatus 0 SControl 300)
[    5.866443] ata6: SATA link down (SStatus 0 SControl 300)
[    6.165153] loop: module loaded
[    6.192547] kjournald starting.  Commit interval 5 seconds
[    6.192558] EXT3-fs: mounted filesystem with ordered data mode.
[   13.638041] udevd version 124 started
[   14.077627] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.103969] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.201113] ACPI: I/O resource nForce2_smbus [0x4c00-0x4c3f] conflicts with ACPI region SM00 [0x4c00-0x4c05]
[   14.201117] ACPI: Device needs an ACPI driver
[   14.201161] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   14.201178] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   14.236336] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   14.256047] ACPI: Power Button (FF) [PWRF]
[   14.256136] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   14.288390] ACPI: Power Button (CM) [PWRB]
[   15.340934] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   15.340940] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   15.340957] HDA Intel 0000:00:10.1: setting latency timer to 64
[   15.345713] parport_pc 00:0b: reported by Plug and Play ACPI
[   15.345741] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   15.380763] Linux agpgart interface v0.103
[   15.569615] nvidia: module license 'NVIDIA' taints kernel.
[   15.927790] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   15.927804] nvidia 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   15.927811] nvidia 0000:01:00.0: setting latency timer to 64
[   15.928124] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   15.963144] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   15.976600] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[   16.025951] Linux video capture interface: v2.00
[   16.079752] gspca: main v2.2.0 registered
[   16.082288] gspca: probing 041e:401d
[   16.277779] usbcore: registered new interface driver snd-usb-audio
[   16.694294] gspca: probe ok
[   16.694321] usbcore: registered new interface driver spca505
[   16.694325] spca505: registered
[   17.604862] lp0: using parport0 (interrupt-driven).
[   18.300107] EXT3 FS on loop0, internal journal
[   28.769633] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   28.939794] type=1505 audit(1225053143.447:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4643
[   29.119154] type=1505 audit(1225053143.627:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4648
[   29.119385] type=1505 audit(1225053143.627:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4648
[   29.279614] ip_tables: (C) 2000-2006 Netfilter Core Team
[   29.705971] ACPI: WMI: Mapper loaded
[   30.128396] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   30.128427] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   30.128456] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   31.106879] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   31.248425] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   31.248432] apm: disabled - APM is not SMP safe.
[   31.482134] ppdev: user-space parallel port driver
[   33.943745] Bluetooth: Core ver 2.13
[   33.943833] NET: Registered protocol family 31
[   33.943837] Bluetooth: HCI device and connection manager initialized
[   33.943844] Bluetooth: HCI socket layer initialized
[   33.958811] Bluetooth: L2CAP ver 2.11
[   33.958819] Bluetooth: L2CAP socket layer initialized
[   33.978693] Bluetooth: RFCOMM socket layer initialized
[   33.978826] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.978830] Bluetooth: BNEP filters: protocol multicast
[   33.988735] Bluetooth: RFCOMM TTY layer initialized
[   33.988743] Bluetooth: RFCOMM ver 1.10
[   34.023933] Bridge firewalling registered
[   34.024285] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   34.062064] Bluetooth: SCO (Voice Link) ver 0.6
[   34.062072] Bluetooth: SCO socket layer initialized
[   38.246400] NET: Registered protocol family 17
[   85.777970] NET: Registered protocol family 10
[   85.778421] lo: Disabled Privacy Extensions
[  159.551146] type=1503 audit(1225053274.059:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6328/net/" pid=6328 profile="/usr/sbin/cupsd"
[  159.553744] type=1503 audit(1225053274.063:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6328 profile="/usr/sbin/cupsd"
[  159.555783] type=1503 audit(1225053274.063:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6328 profile="/usr/sbin/cupsd"
[  159.557902] type=1503 audit(1225053274.067:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6328 profile="/usr/sbin/cupsd"
[  159.559941] type=1503 audit(1225053274.067:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6328 profile="/usr/sbin/cupsd"
[  159.561975] type=1503 audit(1225053274.071:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6328 profile="/usr/sbin/cupsd"
[  159.564155] type=1503 audit(1225053274.075:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6328 profile="/usr/sbin/cupsd"
[  159.566236] type=1503 audit(1225053274.075:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6328 profile="/usr/sbin/cupsd"
[  159.568041] type=1503 audit(1225053274.079:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6328 profile="/usr/sbin/cupsd"
[  159.568167] type=1503 audit(1225053274.079:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6328/net/dev" pid=6328 profile="/usr/sbin/cupsd"
[  159.824355] ppdev0: registered pardevice
[  159.876236] ppdev0: unregistered pardevice
[  160.168038] ppdev0: registered pardevice
[  160.216137] ppdev0: unregistered pardevice
[  160.246386] ppdev0: registered pardevice
[  160.292029] ppdev0: unregistered pardevice

```

---

### Post by gilgongo on 2008-10-26
Is there anything in dmesg that indicated the card has a problem?

---

### Post by Spanklord on 2008-10-26
added more info

---

