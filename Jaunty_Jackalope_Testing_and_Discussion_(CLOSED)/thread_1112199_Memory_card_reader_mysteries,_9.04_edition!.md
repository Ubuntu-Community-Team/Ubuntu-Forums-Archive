---
title: "Memory card reader mysteries, 9.04 edition!"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Sunships on 2009-03-31
Hello,

I am using a Sony Vaio FS550, with a fresh 9.04 installation, and have found that the memory card reader no longer works. I was using 8.04 previously, and was able to get it to work fine with help from other kind forum-goers :)(Thread here: [http://ubuntuforums.org/showthread.php?t=750983](http://ubuntuforums.org/showthread.php?t=750983)).

I don't know if the previous problem is relevant to helping it to work this time. Before the card was clearly recognised according to dmesg, just non-functional:

```
[  284.424000] tifm_core: MemoryStick card detected in socket 0:1
[  284.464000] tifm_ms: Unknown symbol tifm_has_ms_pif
```

This time there is no mention of the card reader (dmesg output pasted below). I realise 9.04 is still in development, but am not convinced it is so completely alien that it will never support a working memory card reader. Does anyone out there know how I can get it to work? I am not entirely fluent with the command line and Linux, so please keep it simple for me if you can.

Thanks!



```
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #37-Ubuntu SMP Mon Mar 23 16:40:23 UTC 2009 (Ubuntu 2.6.28-11.37-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000004f6e0000 - 000000004f6ea000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004f6ea000 - 000000004f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004f700000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x4f6e0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000004f6e0000 (usable)
[    0.000000]  modified: 000000004f6e0000 - 000000004f6ea000 (ACPI data)
[    0.000000]  modified: 000000004f6ea000 - 000000004f700000 (ACPI NVS)
[    0.000000]  modified: 000000004f700000 - 0000000050000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bf000 - 37fef8f5
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb18f5
[    0.000000] Move RAMDISK from 00000000378bf000 - 0000000037fef8f4 to 00881000 - 00fb18f4
[    0.000000] ACPI: RSDP 000F7530, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 4F6E5A12, 0044 (r1   Sony       J0 20041219 PTL         0)
[    0.000000] ACPI: APIC 4F6E9E78, 0068 (r1   Sony       J0 20041219 PTL        5F)
[    0.000000] ACPI: FACP 4F6E9EE0, 0084 (r2   Sony       J0 20041219 PTL        5F)
[    0.000000] ACPI: DSDT 4F6E64A7, 39D1 (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: FACS 4F6FAFC0, 0040
[    0.000000] ACPI: BOOT 4F6E9FD8, 0028 (r1   Sony       J0 20041219 PTL         1)
[    0.000000] ACPI: MCFG 4F6E9F9C, 003C (r1   Sony       J0 20041219 PTL        5F)
[    0.000000] ACPI: SSDT 4F6E62CF, 01D4 (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: SSDT 4F6E5E8A, 0235 (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: SSDT 4F6E5C6F, 021B (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: SSDT 4F6E5A56, 0219 (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 386MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb18f5]      NEW RAMDISK ==> [0000881000 - 0000fb18f5]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0004f6e0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004f6e0
[    0.000000] On node 0 totalpages: 325231
[    0.000000] free_area_init_node: node 0, pgdat c06d0f00, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 774 pages used for memmap
[    0.000000]   HighMem zone: 98268 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
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
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:90000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 322689
[    0.000000] Kernel command line: root=UUID=dc62c66d-86be-4f6e-8241-e3aa29ffb360 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.924 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 6506560 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1267460k/1301376k available (4126k kernel code, 32512k reserved, 2208k data, 532k init, 396168k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a7f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a7f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004021] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.84 BogoMIPS (lpj=6383696)
[    0.004050] Security Framework initialized
[    0.004065] SELinux:  Disabled at boot.
[    0.004101] AppArmor: AppArmor initialized
[    0.004113] Mount-cache hash table entries: 512
[    0.004344] Initializing cgroup subsys ns
[    0.004352] Initializing cgroup subsys cpuacct
[    0.004355] Initializing cgroup subsys memory
[    0.004363] Initializing cgroup subsys freezer
[    0.004386] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004389] CPU: L2 cache: 2048K
[    0.004410] Checking 'hlt' instruction... OK.
[    0.020879] SMP alternatives: switching to UP code
[    0.147767] ACPI: Core revision 20080926
[    0.149909] ACPI: Checking initramfs for custom DSDT
[    0.524599] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.567463] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    0.568002] Brought up 1 CPUs
[    0.568002] Total of 1 processors activated (3191.84 BogoMIPS).
[    0.568002] CPU0 attaching NULL sched-domain.
[    0.568002] net_namespace: 776 bytes
[    0.568002] Booting paravirtualized kernel on bare hardware
[    0.568002] Time: 18:02:40  Date: 03/31/09
[    0.568002] regulator: core version 0.5
[    0.568002] NET: Registered protocol family 16
[    0.568002] EISA bus registered
[    0.568002] ACPI: bus type pci registered
[    0.568002] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.568002] PCI: MCFG area at e0000000 reserved in E820
[    0.568002] PCI: Using MMCONFIG for extended config space
[    0.568002] PCI: Using configuration type 1 for base access
[    0.568002] ACPI: EC: Look up EC in DSDT
[    0.572503] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.676086] ACPI: Interpreter enabled
[    0.676091] ACPI: (supports S0 S3 S4 S5)
[    0.676113] ACPI: Using IOAPIC for interrupt routing
[    0.682005] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.682008] ACPI: EC: driver started in interrupt mode
[    0.682141] ACPI: No dock devices found.
[    0.682151] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.682227] pci 0000:00:02.0: reg 10 32bit mmio: [0xb0080000-0xb00fffff]
[    0.682232] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.682238] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]
[    0.682243] pci 0000:00:02.0: reg 1c 32bit mmio: [0xb0040000-0xb007ffff]
[    0.682270] pci 0000:00:02.1: reg 10 32bit mmio: [0x000000-0x07ffff]
[    0.682374] pci 0000:00:1b.0: reg 10 64bit mmio: [0xb0000000-0xb0003fff]
[    0.682414] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.682419] pci 0000:00:1b.0: PME# disabled
[    0.682475] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.682536] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.682596] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.682657] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
[    0.682722] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb0004000-0xb00043ff]
[    0.682769] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.682774] pci 0000:00:1d.7: PME# disabled
[    0.682917] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.682924] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.682929] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.682954] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.682962] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.682970] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.682979] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.682987] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.683063] pci 0000:00:1f.3: reg 20 io port: [0x18a0-0x18bf]
[    0.683155] pci 0000:06:03.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.683170] pci 0000:06:03.0: supports D1 D2
[    0.683173] pci 0000:06:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.683179] pci 0000:06:03.0: PME# disabled
[    0.683239] pci 0000:06:03.2: reg 10 32bit mmio: [0xb0104000-0xb01047ff]
[    0.683251] pci 0000:06:03.2: reg 14 32bit mmio: [0xb0100000-0xb0103fff]
[    0.683310] pci 0000:06:03.2: supports D1 D2
[    0.683312] pci 0000:06:03.2: PME# supported from D0 D1 D2 D3hot
[    0.683318] pci 0000:06:03.2: PME# disabled
[    0.683376] pci 0000:06:03.3: reg 10 32bit mmio: [0xb0105000-0xb0105fff]
[    0.683443] pci 0000:06:03.3: supports D1 D2
[    0.683445] pci 0000:06:03.3: PME# supported from D0 D1 D2 D3hot
[    0.683452] pci 0000:06:03.3: PME# disabled
[    0.683519] pci 0000:06:04.0: reg 10 32bit mmio: [0xb0106000-0xb0106fff]
[    0.683588] pci 0000:06:04.0: PME# supported from D0 D3hot D3cold
[    0.683594] pci 0000:06:04.0: PME# disabled
[    0.683655] pci 0000:06:08.0: reg 10 32bit mmio: [0xb0107000-0xb0107fff]
[    0.683666] pci 0000:06:08.0: reg 14 io port: [0x2000-0x203f]
[    0.683723] pci 0000:06:08.0: supports D1 D2
[    0.683725] pci 0000:06:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.683731] pci 0000:06:08.0: PME# disabled
[    0.683791] pci 0000:00:1e.0: transparent bridge
[    0.683797] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]
[    0.683802] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0100000-0xb01fffff]
[    0.683842] bus 00 -> node 0
[    0.683851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.684311] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.689334] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.689465] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.689590] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.689713] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.689837] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.689960] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.690086] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.690214] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.690441] ACPI: WMI: Mapper loaded
[    0.690619] SCSI subsystem initialized
[    0.690660] libata version 3.00 loaded.
[    0.690711] usbcore: registered new interface driver usbfs
[    0.690729] usbcore: registered new interface driver hub
[    0.690756] usbcore: registered new device driver usb
[    0.690895] PCI: Using ACPI for IRQ routing
[    0.691008] Bluetooth: Core ver 2.13
[    0.691008] NET: Registered protocol family 31
[    0.691008] Bluetooth: HCI device and connection manager initialized
[    0.691008] Bluetooth: HCI socket layer initialized
[    0.691008] NET: Registered protocol family 8
[    0.691008] NET: Registered protocol family 20
[    0.691008] NetLabel: Initializing
[    0.691008] NetLabel:  domain hash size = 128
[    0.691008] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.691008] NetLabel:  unlabeled traffic allowed by default
[    0.691008] hpet clockevent registered
[    0.691008] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.691008] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.691008] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.696066] AppArmor: AppArmor Filesystem Enabled
[    0.696073] pnp: PnP ACPI init
[    0.696073] ACPI: bus type pnp registered
[    0.697564] pnp: PnP ACPI: found 8 devices
[    0.697567] ACPI: ACPI bus type pnp unregistered
[    0.697571] PnPBIOS: Disabled by ACPI PNP
[    0.697585] system 00:04: ioport range 0x380-0x383 has been reserved
[    0.697588] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.697591] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.697595] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.697598] system 00:04: ioport range 0x1640-0x164f has been reserved
[    0.697601] system 00:04: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.697605] system 00:04: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.697608] system 00:04: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.697612] system 00:04: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.697615] system 00:04: iomem range 0xe0000000-0xefffffff has been reserved
[    0.733555] pci 0000:06:03.0: CardBus bridge, secondary bus 0000:07
[    0.733558] pci 0000:06:03.0:   IO window: 0x002400-0x0024ff
[    0.733565] pci 0000:06:03.0:   IO window: 0x002800-0x0028ff
[    0.733572] pci 0000:06:03.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.733579] pci 0000:06:03.0:   MEM window: 0x68000000-0x6bffffff
[    0.733586] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.733590] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.733597] pci 0000:00:1e.0:   MEM window: 0xb0100000-0xb01fffff
[    0.733602] pci 0000:00:1e.0:   PREFETCH window: 0x00000060000000-0x00000063ffffff
[    0.733619] pci 0000:00:1e.0: setting latency timer to 64
[    0.733630] pci 0000:06:03.0: enabling device (0000 -> 0003)
[    0.733638] pci 0000:06:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.733647] bus: 00 index 0 io port: [0x00-0xffff]
[    0.733650] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.733653] bus: 06 index 0 io port: [0x2000-0x2fff]
[    0.733656] bus: 06 index 1 mmio: [0xb0100000-0xb01fffff]
[    0.733658] bus: 06 index 2 mmio: [0x60000000-0x63ffffff]
[    0.733661] bus: 06 index 3 io port: [0x00-0xffff]
[    0.733663] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.733666] bus: 07 index 0 io port: [0x2400-0x24ff]
[    0.733668] bus: 07 index 1 io port: [0x2800-0x28ff]
[    0.733671] bus: 07 index 2 mmio: [0x60000000-0x63ffffff]
[    0.733674] bus: 07 index 3 mmio: [0x68000000-0x6bffffff]
[    0.733683] NET: Registered protocol family 2
[    0.733805] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.734089] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.734854] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.735324] TCP: Hash tables configured (established 131072 bind 65536)
[    0.735328] TCP reno registered
[    0.735500] NET: Registered protocol family 1
[    0.735674] checking if image is initramfs... it is
[    1.192114] Switched to high resolution mode on CPU 0
[    1.500399] Freeing initrd memory: 7362k freed
[    1.500459] Simple Boot Flag at 0x36 set to 0x1
[    1.500497] cpufreq: No nForce2 chipset.
[    1.500693] audit: initializing netlink socket (disabled)
[    1.500719] type=2000 audit(1238522560.500:1): initialized
[    1.511550] highmem bounce pool size: 64 pages
[    1.511557] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.513091] VFS: Disk quotas dquot_6.5.1
[    1.513154] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.513853] fuse init (API version 7.10)
[    1.513950] msgmni has been set to 1717
[    1.514146] alg: No test for stdrng (krng)
[    1.514160] io scheduler noop registered
[    1.514162] io scheduler anticipatory registered
[    1.514164] io scheduler deadline registered
[    1.514181] io scheduler cfq registered (default)
[    1.514199] pci 0000:00:02.0: Boot video device
[    1.514427] pci 0000:06:08.0: Firmware left e100 interrupts enabled; disabling
[    1.518071] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.518082] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.520179] ACPI: AC Adapter [ADP1] (on-line)
[    1.526311] ACPI: Battery Slot [BAT0] (battery present)
[    1.526397] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.526400] ACPI: Power Button (FF) [PWRF]
[    1.526451] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.527618] ACPI: Lid Switch [LID0]
[    1.527673] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.527683] ACPI: Power Button (CM) [PWRB]
[    2.528200] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.528230] processor ACPI_CPU:00: registered as cooling_device0
[    2.528234] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.532213] thermal LNXTHERM:01: registered as thermal_zone0
[    2.535453] ACPI: Thermal Zone [THRM] (26 C)
[    2.535500] isapnp: Scanning for PnP cards...
[    2.889858] isapnp: No Plug & Play device found
[    2.891106] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.892239] brd: module loaded
[    2.892596] loop: module loaded
[    2.892683] Fixed MDIO Bus: probed
[    2.892692] PPP generic driver version 2.4.2
[    2.892756] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.892786] Driver 'sd' needs updating - please use bus_type methods
[    2.892797] Driver 'sr' needs updating - please use bus_type methods
[    2.892894] ata_piix 0000:00:1f.1: version 2.12
[    2.892915] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.892962] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.893068] scsi0 : ata_piix
[    2.893158] scsi1 : ata_piix
[    2.893942] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    2.893945] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.064575] ata1.00: ATA-5: HITACHI_DK23FA-80, 00M3A0A2, max UDMA/100
[    3.064578] ata1.00: 156301488 sectors, multi 16: LBA 
[    3.064622] ata1.01: ATAPI: MATSHITAUJ-831Da, 1.00, max UDMA/33
[    3.072522] ata1.00: configured for UDMA/100
[    3.088517] ata1.01: configured for UDMA/33
[    3.088909] ata2: port disabled. ignoring.
[    3.089051] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23FA-8 00M3 PQ: 0 ANSI: 5
[    3.089173] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    3.089194] sd 0:0:0:0: [sda] Write Protect is off
[    3.089197] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.089226] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.089294] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    3.089310] sd 0:0:0:0: [sda] Write Protect is off
[    3.089313] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.089340] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.089344]  sda: sda1 sda2 sda3 sda4
[    3.170041] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.170086] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.171881] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-831Da         1.00 PQ: 0 ANSI: 5
[    3.176084] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.176090] Uniform CD-ROM driver Revision: 3.20
[    3.176178] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    3.176222] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    3.176916] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.176946] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.176973] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.176977] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.177050] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.180966] ehci_hcd 0000:00:1d.7: debug port 1
[    3.180973] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.180990] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0004000
[    3.196009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.196109] usb usb1: configuration #1 chosen from 1 choice
[    3.196141] hub 1-0:1.0: USB hub found
[    3.196152] hub 1-0:1.0: 8 ports detected
[    3.196286] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.196305] uhci_hcd: USB Universal Host Controller Interface driver
[    3.196330] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.196338] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.196341] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.196384] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.196411] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    3.196504] usb usb2: configuration #1 chosen from 1 choice
[    3.196530] hub 2-0:1.0: USB hub found
[    3.196541] hub 2-0:1.0: 2 ports detected
[    3.196632] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.196639] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.196643] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.196685] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.196720] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    3.196798] usb usb3: configuration #1 chosen from 1 choice
[    3.196825] hub 3-0:1.0: USB hub found
[    3.196832] hub 3-0:1.0: 2 ports detected
[    3.196919] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.196925] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.196929] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.196971] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.197004] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.197087] usb usb4: configuration #1 chosen from 1 choice
[    3.197113] hub 4-0:1.0: USB hub found
[    3.197120] hub 4-0:1.0: 2 ports detected
[    3.197205] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.197211] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.197215] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.197266] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.197301] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    3.197385] usb usb5: configuration #1 chosen from 1 choice
[    3.197411] hub 5-0:1.0: USB hub found
[    3.197419] hub 5-0:1.0: 2 ports detected
[    3.197552] usbcore: registered new interface driver libusual
[    3.197592] usbcore: registered new interface driver usbserial
[    3.197604] USB Serial support registered for generic
[    3.197620] usbcore: registered new interface driver usbserial_generic
[    3.197622] usbserial: USB Serial Driver core
[    3.197668] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.200723] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.204160] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.204166] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.204169] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.204172] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.204175] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.204348] mice: PS/2 mouse device common for all mice
[    3.204520] rtc_cmos 00:05: RTC can wake from S4
[    3.204563] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.204596] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.204666] device-mapper: uevent: version 1.0.3
[    3.204786] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.204836] device-mapper: multipath: version 1.0.5 loaded
[    3.204839] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.204920] EISA: Probing bus 0 at eisa.0
[    3.204928] Cannot allocate resource for EISA slot 1
[    3.204931] Cannot allocate resource for EISA slot 2
[    3.204963] EISA: Detected 0 cards.
[    3.205028] cpuidle: using governor ladder
[    3.205080] cpuidle: using governor menu
[    3.205631] TCP cubic registered
[    3.205750] NET: Registered protocol family 10
[    3.206206] lo: Disabled Privacy Extensions
[    3.206550] NET: Registered protocol family 17
[    3.206569] Bluetooth: L2CAP ver 2.11
[    3.206571] Bluetooth: L2CAP socket layer initialized
[    3.206574] Bluetooth: SCO (Voice Link) ver 0.6
[    3.206576] Bluetooth: SCO socket layer initialized
[    3.206603] Bluetooth: RFCOMM socket layer initialized
[    3.206612] Bluetooth: RFCOMM TTY layer initialized
[    3.206614] Bluetooth: RFCOMM ver 1.10
[    3.206925] Using IPI No-Shortcut mode
[    3.207007] registered taskstats version 1
[    3.207133]   Magic number: 1:183:40
[    3.207145] bdi 7:5: hash matches
[    3.207218] rtc_cmos 00:05: setting system clock to 2009-03-31 18:02:43 UTC (1238522563)
[    3.207222] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.207224] EDD information not available.
[    3.207575] Freeing unused kernel memory: 532k freed
[    3.207704] Write protecting the kernel text: 4128k
[    3.207749] Write protecting the kernel read-only data: 1532k
[    3.406889] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.564017] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    3.708819] usb 1-3: configuration #1 chosen from 1 choice
[    3.719171] Initializing USB Mass Storage driver...
[    3.728019] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.736030] usbcore: registered new interface driver usb-storage
[    3.736034] USB Mass Storage support registered.
[    3.736104] usb-storage: device found at 3
[    3.736106] usb-storage: waiting for device to settle before scanning
[    3.931972] ohci1394 0000:06:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.981852] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[b0104000-b01047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.982216] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.989533] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    3.989536] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.991849] e100 0000:06:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.024414] e100 0000:06:08.0: PME# disabled
[    4.027336] e100: eth0: e100_probe: addr 0xb0107000, irq 20, MAC addr 00:01:4a:16:a0:83
[    4.216632] Marking TSC unstable due to TSC halts in idle
[    4.217347] usb 2-1: configuration #1 chosen from 1 choice
[    4.224730] usbcore: registered new interface driver hiddev
[    4.263543] input: HID 1241:1166 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5
[    4.263816] generic-usb 0003:1241:1166.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.0-1/input0
[    4.263836] usbcore: registered new interface driver usbhid
[    4.263839] usbhid: v2.6:USB HID core driver
[    4.688011] Clocksource tsc unstable (delta = -348214937 ns)
[    4.737033] PM: Starting manual resume from disk
[    4.737037] PM: Resume from partition 8:4
[    4.737039] PM: Checking hibernation image.
[    4.737255] PM: Resume from disk failed.
[    4.756656] EXT4-fs: barriers enabled
[    4.778335] kjournald2 starting.  Commit interval 5 seconds
[    4.778345] EXT4-fs: delayed allocation enabled
[    4.778347] EXT4-fs: file extents enabled
[    4.781368] EXT4-fs: mballoc enabled
[    4.781373] EXT4-fs: mounted filesystem with ordered data mode.
[    5.260152] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301cf2475]
[    8.737594] usb-storage: device scan complete
[    8.738947] scsi 2:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100F PQ: 0 ANSI: 4
[    8.741424] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    8.742922] sd 2:0:0:0: [sdb] Write Protect is off
[    8.742925] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[    8.742928] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.745172] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    8.746545] sd 2:0:0:0: [sdb] Write Protect is off
[    8.746548] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[    8.746551] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.746554]  sdb: sdb1
[    8.775168] sd 2:0:0:0: [sdb] Attached SCSI disk
[    8.775243] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.656192] udev: starting version 140
[   10.956301] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:07/input/input6
[   10.981354] sony-laptop: Sony Notebook Control Driver v0.6.
[   10.981457] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   10.983689] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/SNY5001:00/input/input7
[   11.008266] input: Sony Vaio Jogdial as /devices/virtual/input/input8
[   11.277148] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   11.331203] ieee80211_crypt: registered algorithm 'NULL'
[   11.336100] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   11.336104] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   11.355375] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.368359] Linux agpgart interface v0.103
[   11.417014] intel_rng: FWH not detected
[   11.462480] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   11.462485] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   11.462706] ipw2200 0000:06:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.463865] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   11.463926] ipw2200 0000:06:04.0: firmware: requesting ipw2200-bss.fw
[   11.798248] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   11.798812] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   11.801838] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   11.998270] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   12.011067] yenta_cardbus 0000:06:03.0: CardBus bridge found [104d:818f]
[   12.011094] yenta_cardbus 0000:06:03.0: Enabling burst memory read transactions
[   12.011102] yenta_cardbus 0000:06:03.0: Using CSCINT to route CSC interrupts to PCI
[   12.011105] yenta_cardbus 0000:06:03.0: Routing CardBus interrupts to PCI
[   12.011112] yenta_cardbus 0000:06:03.0: TI: mfunc 0x01001b22, devctl 0x64
[   12.103598] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input10
[   12.124712] iTCO_vendor_support: vendor-support=0
[   12.126013] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input11
[   12.129171] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.129346] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   12.129358] iTCO_wdt: No card detected
[   12.241247] yenta_cardbus 0000:06:03.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   12.241253] yenta_cardbus 0000:06:03.0: Socket status: 30000006
[   12.241257] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   12.241267] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   12.241271] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   12.241511] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   12.241515] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x63ffffff
[   12.271338] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.271417] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.608570] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.610896] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   12.611891] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.612729] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.613743] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.746634] lp: driver loaded but no devices found
[   12.812336] Adding 409648k swap on /dev/sda4.  Priority:-1 extents:1 across:409648k
[   13.354078] EXT4 FS on sda3, internal journal on sda3:8
[   14.420469] type=1505 audit(1238518974.712:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1879
[   14.496984] type=1505 audit(1238518974.788:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1883
[   14.497119] type=1505 audit(1238518974.788:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1883
[   14.497170] type=1505 audit(1238518974.788:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1883
[   14.497221] type=1505 audit(1238518974.788:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1883
[   14.678470] type=1505 audit(1238518974.968:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1888
[   14.678841] type=1505 audit(1238518974.968:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1888
[   14.713397] type=1505 audit(1238518975.004:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1892
[   17.625387] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   17.625391] vboxdrv: Successfully done.
[   17.625393] vboxdrv: Found 1 processor cores.
[   17.625513] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   17.625516] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   19.171988] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.171992] Bluetooth: BNEP filters: protocol multicast
[   19.206857] Bridge firewalling registered
[   21.246964] ppdev: user-space parallel port driver
[   22.476831] [drm] Initialized drm 1.1.0 20060810
[   22.485495] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.485503] pci 0000:00:02.0: setting latency timer to 64
[   22.485699] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   22.488461] [drm:i915_setparam] *ERROR* unknown parameter 4
[   22.488485] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   23.804072] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   24.722159] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.236024] eth1: no IPv6 routers present
[   35.261351] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   44.153168] CPU0 attaching NULL sched-domain.
[   44.164108] CPU0 attaching NULL sched-domain.
[   50.798259] ieee80211_crypt: registered algorithm 'WEP'
[   71.038739] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
[   71.041611] mtrr: no MTRR for c0000000,10000000 found
[   73.583347] [drm:i915_setparam] *ERROR* unknown parameter 4
[   73.583393] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   74.663438] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   89.408731] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   92.606701] CPU0 attaching NULL sched-domain.
[   92.621015] CPU0 attaching NULL sched-domain.
```

---

### Post by Sunships on 2009-03-31
*Bump*

---

### Post by Sunships on 2009-04-01
*Bump*

---

### Post by Vico Vicario on 2009-04-01
Apparently module is not being loaded. Try the following for some info:

1) lsmod | grep tifm

(should see some module names)

2) lspci -v

(should see card reader and module used by it)

If both commands indicate that module is not being loaded, then PCI ids might be missing from driver and is a good idea to update.

V.

---

### Post by Sunships on 2009-04-01
Hi V,

"lsmod | grep tifm" gives no output.

"lspci -v" gives the following:

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Sony Corporation Device 81b7
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Sony Corporation Device 81b8
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Sony Corporation Device 81b8
	Flags: fast devsel
	Memory at 64000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: Sony Corporation Device 81bb
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
	Subsystem: Sony Corporation Device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
	Subsystem: Sony Corporation Device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
	Subsystem: Sony Corporation Device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
	Subsystem: Sony Corporation Device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20)
	Subsystem: Sony Corporation Device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: 0000000060000000-0000000063ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
	Subsystem: Sony Corporation Device 81b9
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
	Subsystem: Sony Corporation Device 81b9
	Flags: medium devsel, IRQ 10
	I/O ports at 18a0 [size=32]
	Kernel modules: i2c-i801

06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
	Subsystem: Sony Corporation Device 818f
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at b0108000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 60000000-63fff000 (prefetchable)
	Memory window 1: 68000000-6bfff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller (prog-if 10)
	Subsystem: Sony Corporation Device 818f
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at b0104000 (32-bit, non-prefetchable) [size=2K]
	Memory at b0100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
	Subsystem: Sony Corporation Device 8190
	Flags: medium devsel, IRQ 4
	Memory at b0105000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2751
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at b0106000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 04)
	Subsystem: Sony Corporation Device 81d0
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at b0107000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

```

I guess either SMBus or CardBus is the relevant entry? Please advise on what action I should take next.

Thanks!

---

### Post by Sunships on 2009-04-01
*Bump*

---

### Post by Vico Vicario on 2009-04-01
You could try loading the modules manually:

sudo modprobe tifm_core
sudo modprobe tifm_sd
sudo modprobe tifm_7xx1

V.

---

### Post by Sunships on 2009-04-02
```


$ sudo modprobe tifm_core
FATAL: Module tifm_core not found.

$ sudo modprobe tifm_sd
FATAL: Error inserting tifm_sd (/lib/modules/2.6.28-11-generic/kernel/drivers/mmc/host/tifm_sd.ko): Unknown symbol in module, or unknown parameter (see dmesg)

$ sudo modprobe tifm_7xx1
FATAL: Module tifm_7xx1 not found.

```

Didn't work :( Do I need to install something else first?

---

### Post by Vico Vicario on 2009-04-02
Somehow you lost the modules. Try:

find /lib/modules/ -name "tifm*"
 
> /lib/modules/2.6.28-11-generic/kernel/drivers/mmc/host/tifm_sd.ko
> /lib/modules/2.6.28-11-generic/kernel/drivers/misc/tifm_7xx1.ko
> /lib/modules/2.6.28-11-generic/kernel/drivers/misc/tifm_core.ko

You **should** have the 3 modules. They are provided by the generic kernel.

If you have them, try 'sudo depmod', and then try to reload them again with the modprobe commands.

If you don't have them you will need to re-install the kernel

V.

---

### Post by Sunships on 2009-04-02
Thanks V! I'm at work right now, but will try it out when I get home.

---

### Post by Sunships on 2009-04-02
Hm,this is all I get:

```
$ find /lib/modules/ -name "tifm*"
/lib/modules/2.6.28-11-generic/kernel/drivers/mmc/host/tifm_sd.ko
```

How do I re-install the kernel? Do I have to reinstall Ubuntu from scratch?

---

### Post by Sunships on 2009-04-03
*Bumpage*

---

### Post by Sunships on 2009-04-04
So to summarise - my memory card reader doesn't work following installation of 9.04, since I lack these modules:

> /lib/modules/2.6.28-11-generic/kernel/drivers/mmc/host/tifm_sd.ko
> /lib/modules/2.6.28-11-generic/kernel/drivers/misc/tifm_7xx1.ko
> /lib/modules/2.6.28-11-generic/kernel/drivers/misc/tifm_core.ko

V's latest advice is to re-install my kernel, but I don't know how to do that. Do I need to specify that I want these modules installed as well when I do it?

---

### Post by Vico Vicario on 2009-04-04
You can reinstall with:

sudo apt-get install --reinstall linux-image-2.6.28-11-generic

Good luck,

V.

PS. If after re-installing this package you still have no modules then I will be baffled since they should be there, see [http://packages.ubuntu.com/search?searchon=contents&keywords=tifm_core.ko&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=tifm_core.ko&mode=exactfilename&suite=jaunty&arch=any)

---

### Post by Sunships on 2009-04-05
Cool, that seemed to work, 

find /lib/modules/ -name "tifm*" now gives:

```

/lib/modules/2.6.28-11-generic/kernel/drivers/mmc/host/tifm_sd.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/misc/tifm_core.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/misc/tifm_7xx1.ko

```

but the card reader still doesn't work. I tried the fix suggested by qamelian in my previous thread, but at the first stage I received a few messages warning of potential conflicts. I chose the "postpone" option, to avoid any problems, and when I got to the "make" stage I get the output shown below. When repeating the fix I don't get the option change the "postpone" decision.

```

:~/driver$ make
echo /home/sunships/driver
/home/sunships/driver
make -C /lib/modules/2.6.28-11-generic/build M=/home/sunships/driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/sunships/driver/mspro_block.o
/home/sunships/driver/mspro_block.c: In function ‘__end_request’:
/home/sunships/driver/mspro_block.c:51: error: implicit declaration of function ‘end_that_request_chunk’
/home/sunships/driver/mspro_block.c:55: error: implicit declaration of function ‘end_that_request_last’
/home/sunships/driver/mspro_block.c: At top level:
/home/sunships/driver/mspro_block.c:64: error: expected identifier or ‘(’ before ‘==’ token
/home/sunships/driver/mspro_block.c: In function ‘mspro_block_disk_release’:
/home/sunships/driver/mspro_block.c:231: error: ‘MSPRO_BLOCK_PART_SHIFT’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:231: error: (Each undeclared identifier is reported only once
/home/sunships/driver/mspro_block.c:231: error: for each function it appears in.)
/home/sunships/driver/mspro_block.c: At top level:
/home/sunships/driver/mspro_block.c:271: warning: initialisation from incompatible pointer type
/home/sunships/driver/mspro_block.c:272: warning: initialisation from incompatible pointer type
/home/sunships/driver/mspro_block.c: In function ‘mspro_block_attr_name’:
/home/sunships/driver/mspro_block.c:289: error: ‘MSPRO_BLOCK_ID_SYSINFO’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:291: error: ‘MSPRO_BLOCK_ID_MODELNAME’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:293: error: ‘MSPRO_BLOCK_ID_MBR’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:295: error: ‘MSPRO_BLOCK_ID_PBR16’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:297: error: ‘MSPRO_BLOCK_ID_PBR32’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:299: error: ‘MSPRO_BLOCK_ID_SPECFILEVALUES1’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:301: error: ‘MSPRO_BLOCK_ID_SPECFILEVALUES2’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:303: error: ‘MSPRO_BLOCK_ID_DEVINFO’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c: In function ‘mspro_block_attr_show’:
/home/sunships/driver/mspro_block.c:525: error: ‘MSPRO_BLOCK_ID_SYSINFO’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:527: error: ‘MSPRO_BLOCK_ID_MODELNAME’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:529: error: ‘MSPRO_BLOCK_ID_MBR’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:531: error: ‘MSPRO_BLOCK_ID_SPECFILEVALUES1’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:532: error: ‘MSPRO_BLOCK_ID_SPECFILEVALUES2’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:534: error: ‘MSPRO_BLOCK_ID_DEVINFO’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c: In function ‘mspro_block_init_disk’:
/home/sunships/driver/mspro_block.c:1217: error: ‘MSPRO_BLOCK_ID_DEVINFO’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:1219: error: ‘MSPRO_BLOCK_ID_SYSINFO’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c:1242: error: ‘MSPRO_BLOCK_PART_SHIFT’ undeclared (first use in this function)
/home/sunships/driver/mspro_block.c: In function ‘mspro_block_resume’:
/home/sunships/driver/mspro_block.c:1432: error: ‘MSPRO_BLOCK_ID_SYSINFO’ undeclared (first use in this function)
make[2]: *** [/home/sunships/driver/mspro_block.o] Error 1
make[1]: *** [_module_/home/sunships/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

```

---

### Post by Sunships on 2009-04-06
*Bumpity*

---

### Post by Sunships on 2009-04-08
The mystery persists! Is there anyone out there who can save me from logging in to Windows for just a meagre exchange of data with my phone?

---

### Post by knarf on 2009-04-08
It is most likely a bug in the kernel, related to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222557) or (possible dup) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159951](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159951). Try the patch mentioned in the first bug (scroll down a bit, the file has moved), maybe that works or can be adapted to the current kernel.

---

