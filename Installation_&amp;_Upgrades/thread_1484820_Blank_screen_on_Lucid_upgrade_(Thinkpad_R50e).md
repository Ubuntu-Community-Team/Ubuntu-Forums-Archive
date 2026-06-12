---
title: "Blank screen on Lucid upgrade (Thinkpad R50e)"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by pwaring on 2010-05-16
I've recently upgraded my Karmic install to Lucid on a Thinkpad R50e laptop using the Update Manager->Upgrade option. When I boot up and select any kernel from Grub, I see the usual Ubuntu splash screen (or all the scrolling text if I remove the 'splash' option), followed by a blank screen. The laptop still appears to be on (fan is working etc.) but nothing I do produces a response (Ctrl-Alt-Tab, Ctrl-Alt-F2 to get another terminal etc.), the only option is to hold down the power button until the laptop switches off.

I have tried all the following solutions found from searches from a root console with networking enabled:

[LIST]
[*]Moving xorg.conf to xorg.conf.bak
[*]dpkg-reconfigure -phigh xserver-xorg 
[*]aptitude update && aptitude upgrade
[/LIST]

I've also tried the following options in grub:

[LIST]
[*]Adding i915.modeset=1 to the kernel line in grub
[*]Adding i915.modeset=0 to the kernel line in grub
[*]Adding i915.modeset=0 xforcevesa to the kernel line in grub
[/LIST]

I have also tried connecting an external monitor, just to make sure that it wasn't the laptop screen at fault, but the results are the same. Booting into XP (the machine dual-boots) works fine.

Is there anything else which I can try? I am starting to get a bit worried now, as this is my primary development machine and I really need it to work by Monday morning...

Information about my graphics card:

```
lspci | VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

---

### Post by pwaring on 2010-05-16
After a bit more searching, I managed to find this (I didn't know that I had an '8xx' card, but I'm guessing that's what the /855GM part of the lspci output means):

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Workaround A seems to have solved the problem for me, suppose it is about time I bought a new laptop if this is always going to be a problem. :(

---

### Post by pwaring on 2010-05-16
Actually, Workaround A doesn't fix the problem, it allows me to boot, but then after 30-60 minutes Ubuntu will simply crash out into what looks like the output of dmesg and then the screen goes blank again.

---

### Post by dE_logics on 2010-05-16
Appears to be hardware problem...overheating.

How about  - 

```
tail -f /proc/acpi/thermal_zone/THM/temperature > ~/Desktop/out
```

This will create a file on your desktop showing the changes in temperature, so after the hard crash, you can view the latest temperature change.

Open /var/log, there should be 2 files dmesg and dmesg.0, post contents of the latter.

And, how about running a memtest?

---

### Post by pwaring on 2010-05-16
I'm not sure why it would be a hardware problem or overheating, everything was fine until I upgraded to Lucid last night. I have used Workaround B which seems to have fixed the problem for the moment, it does mean that I can no longer play DVDs or games but I can't afford to have a machine randomly crashing on me.

Last CPU temperature at the moment is: 51C, I have left the tail command running in case it crashes again.

/var/log/dmesg.0 contains:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6e0000 - 000000003f6f7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6f7000 - 000000003f6f9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x3f6e0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-DFFFF write-back
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f6e0000 (usable)
[    0.000000]  modified: 000000003f6e0000 - 000000003f6f7000 (ACPI data)
[    0.000000]  modified: 000000003f6f7000 - 000000003f6f9000 (ACPI NVS)
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 3785e000 - 37fef402
[    0.000000] Allocated new RAMDISK: 008de000 - 0106f402
[    0.000000] Move RAMDISK from 000000003785e000 - 0000000037fef401 to 008de000 - 0106f401
[    0.000000] ACPI: RSDP 000f6e40 00024 (v02 IBM   )
[    0.000000] ACPI: XSDT 3f6ef33d 0004C (v01 IBM    TP-1W    00002050  LTP 00000000)
[    0.000000] ACPI: FACP 3f6ef400 000F4 (v03 IBM    TP-1W    00002050 IBM  00000001)
[    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20090903/tbfadt-526)
[    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 000000000000102C/0 (20090903/tbfadt-557)
[    0.000000] ACPI: DSDT 3f6ef5e7 07865 (v01 IBM    TP-1W    00002050 MSFT 0100000E)
[    0.000000] ACPI: FACS 3f6f8000 00040
[    0.000000] ACPI: SSDT 3f6ef5b4 00033 (v01 IBM    TP-1W    00002050 MSFT 0100000E)
[    0.000000] ACPI: ECDT 3f6f6e4c 00052 (v01 IBM    TP-1W    00002050 IBM  00000001)
[    0.000000] ACPI: TCPA 3f6f6e9e 00032 (v01 IBM    TP-1W    00002050 PTL  00000001)
[    0.000000] ACPI: BOOT 3f6f6fd8 00028 (v01 IBM    TP-1W    00002050  LTP 00000001)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd128]              BRK ==> [00008da000 - 00008dd128]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008de000 - 000106f402]      NEW RAMDISK ==> [00008de000 - 000106f402]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f6e0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f6e0
[    0.000000] On node 0 totalpages: 259707
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1071000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32228 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bf800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257677
[    0.000000] Kernel command line: root=UUID=2a180ea4-21a3-414c-ab59-62121efce253 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5196160 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f6e0)
[    0.000000] Memory: 1008448k/1039232k available (4673k kernel code, 29912k reserved, 2121k data, 656k init, 129928k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1698.280 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3396.56 BogoMIPS (lpj=6793120)
[    0.004028] Security Framework initialized
[    0.004058] AppArmor: AppArmor initialized
[    0.004066] Mount-cache hash table entries: 512
[    0.004215] Initializing cgroup subsys ns
[    0.004220] Initializing cgroup subsys cpuacct
[    0.004225] Initializing cgroup subsys memory
[    0.004236] Initializing cgroup subsys devices
[    0.008005] Initializing cgroup subsys freezer
[    0.008008] Initializing cgroup subsys net_cls
[    0.008038] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008042] CPU: L2 cache: 2048K
[    0.008047] mce: CPU supports 5 MCE banks
[    0.008064] Performance Events: 
[    0.008067] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.008069] no hardware sampling interrupt available.
[    0.008072] p6 PMU driver.
[    0.008079] ... version:                0
[    0.008081] ... bit width:              32
[    0.008083] ... generic registers:      2
[    0.008086] ... value mask:             00000000ffffffff
[    0.008088] ... max period:             000000007fffffff
[    0.008091] ... fixed-purpose events:   0
[    0.008093] ... event mask:             0000000000000003
[    0.008098] Checking 'hlt' instruction... OK.
[    0.024953] SMP alternatives: switching to UP code
[    0.033003] Freeing SMP alternatives: 19k freed
[    0.033013] ACPI: Core revision 20090903
[    0.048554] ACPI: setting ELCR to 0200 (from 0800)
[    0.052009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.052015] ftrace: allocating 21771 entries in 43 pages
[    0.056092] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.056098] weird, boot CPU (#0) not listed by the BIOS.
[    0.056100] SMP motherboard not detected.
[    0.056104] Local APIC not detected. Using dummy APIC emulation.
[    0.056106] SMP disabled
[    0.056241] Brought up 1 CPUs
[    0.056244] Total of 1 processors activated (3396.56 BogoMIPS).
[    0.060059] CPU0 attaching NULL sched-domain.
[    0.060221] devtmpfs: initialized
[    0.060631] regulator: core version 0.5
[    0.060654] Time: 14:32:51  Date: 05/16/10
[    0.060707] NET: Registered protocol family 16
[    0.060846] EISA bus registered
[    0.060857] ACPI: bus type pci registered
[    0.061080] PCI: PCI BIOS revision 2.10 entry at 0xfd8c6, last bus=5
[    0.061082] PCI: Using configuration type 1 for base access
[    0.062154] bio: create slab <bio-0> at 0
[    0.064166] ACPI: EC: EC description table is found, configuring boot EC
[    0.072197] ACPI: Interpreter enabled
[    0.072204] ACPI: (supports S0 S3 S4 S5)
[    0.072229] ACPI: Using PIC for interrupt routing
[    0.077115] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.077115] ACPI: Power Resource [PUBS] (on)
[    0.077115] ACPI: No dock devices found.
[    0.077115] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.077115] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.077115] pci 0000:00:02.0: reg 14 32bit mmio: [0xd0000000-0xd007ffff]
[    0.077115] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]
[    0.077115] pci 0000:00:02.0: supports D1
[    0.077115] pci 0000:00:02.1: reg 10 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.077115] pci 0000:00:02.1: reg 14 32bit mmio: [0xd0080000-0xd00fffff]
[    0.077115] pci 0000:00:02.1: supports D1
[    0.077115] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.077115] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.077115] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.077115] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0100000-0xd01003ff]
[    0.077115] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.077115] pci 0000:00:1d.7: PME# disabled
[    0.077115] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.077115] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.077115] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.077115] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.077115] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.077115] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.077115] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.077115] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.077115] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.077115] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.077115] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.077115] pci 0000:00:1f.5: reg 18 32bit mmio: [0xd0100c00-0xd0100dff]
[    0.077115] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xd0100800-0xd01008ff]
[    0.077115] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.077115] pci 0000:00:1f.5: PME# disabled
[    0.077115] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.077115] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.080007] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.080012] pci 0000:00:1f.6: PME# disabled
[    0.080050] pci 0000:02:00.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
[    0.080067] pci 0000:02:00.0: supports D1 D2
[    0.080070] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.080074] pci 0000:02:00.0: PME# disabled
[    0.080105] pci 0000:02:02.0: reg 10 32bit mmio: [0xd0200000-0xd0200fff]
[    0.080146] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.080150] pci 0000:02:02.0: PME# disabled
[    0.080183] pci 0000:02:08.0: reg 10 32bit mmio: [0xd0201000-0xd0201fff]
[    0.080190] pci 0000:02:08.0: reg 14 io port: [0x7000-0x703f]
[    0.080223] pci 0000:02:08.0: supports D1 D2
[    0.080226] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.080230] pci 0000:02:08.0: PME# disabled
[    0.080259] pci 0000:00:1e.0: transparent bridge
[    0.080264] pci 0000:00:1e.0: bridge io port: [0x3000-0x7fff]
[    0.080269] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0200000-0xdfffffff]
[    0.080274] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.080297] pci_bus 0000:00: on NUMA node 0
[    0.080302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.080384] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.083814] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.084018] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.084205] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.084393] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.084579] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.084766] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.084934] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.085121] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.085253] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.085262] vgaarb: loaded
[    0.085398] SCSI subsystem initialized
[    0.085442] libata version 3.00 loaded.
[    0.085517] usbcore: registered new interface driver usbfs
[    0.085535] usbcore: registered new interface driver hub
[    0.085563] usbcore: registered new device driver usb
[    0.085709] ACPI: WMI: Mapper loaded
[    0.085711] PCI: Using ACPI for IRQ routing
[    0.085941] NetLabel: Initializing
[    0.085944] NetLabel:  domain hash size = 128
[    0.085946] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.085961] NetLabel:  unlabeled traffic allowed by default
[    0.085996] Switching to clocksource tsc
[    0.087996] AppArmor: AppArmor Filesystem Enabled
[    0.087996] pnp: PnP ACPI init
[    0.087996] ACPI: bus type pnp registered
[    0.088423] pnp: PnP ACPI: found 10 devices
[    0.088425] ACPI: ACPI bus type pnp unregistered
[    0.088429] PnPBIOS: Disabled by ACPI PNP
[    0.088440] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.088444] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.088448] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.088451] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    0.088455] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.088459] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.088463] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.088466] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.088470] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.088473] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.088477] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.088481] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[    0.088485] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.088493] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.088496] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.088500] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.088504] system 00:02: ioport range 0x1600-0x167f has been reserved
[    0.123203] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.123207] pci 0000:02:00.0:   IO window: 0x003000-0x0030ff
[    0.123212] pci 0000:02:00.0:   IO window: 0x003400-0x0034ff
[    0.123217] pci 0000:02:00.0:   PREFETCH window: 0xf0000000-0xf3ffffff
[    0.123222] pci 0000:02:00.0:   MEM window: 0xd4000000-0xd7ffffff
[    0.123227] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.123231] pci 0000:00:1e.0:   IO window: 0x3000-0x7fff
[    0.123237] pci 0000:00:1e.0:   MEM window: 0xd0200000-0xdfffffff
[    0.123243] pci 0000:00:1e.0:   PREFETCH window: 0xf0000000-0xf7ffffff
[    0.123258] pci 0000:00:1e.0: setting latency timer to 64
[    0.123589] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.123592] PCI: setting IRQ 11 as level-triggered
[    0.123597] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.123605] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.123608] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.123612] pci_bus 0000:02: resource 0 io:  [0x3000-0x7fff]
[    0.123615] pci_bus 0000:02: resource 1 mem: [0xd0200000-0xdfffffff]
[    0.123619] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.123622] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.123625] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.123628] pci_bus 0000:03: resource 0 io:  [0x3000-0x30ff]
[    0.123631] pci_bus 0000:03: resource 1 io:  [0x3400-0x34ff]
[    0.123635] pci_bus 0000:03: resource 2 pref mem [0xf0000000-0xf3ffffff]
[    0.123638] pci_bus 0000:03: resource 3 mem: [0xd4000000-0xd7ffffff]
[    0.123672] NET: Registered protocol family 2
[    0.123769] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.124114] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.125204] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.126023] TCP: Hash tables configured (established 131072 bind 65536)
[    0.126028] TCP reno registered
[    0.126189] NET: Registered protocol family 1
[    0.126229] pci 0000:00:02.0: Boot video device
[    0.126314] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.126452] Simple Boot Flag at 0x35 set to 0x1
[    0.126562] cpufreq-nforce2: No nForce2 chipset.
[    0.126594] Scanning for low memory corruption every 60 seconds
[    0.126761] audit: initializing netlink socket (disabled)
[    0.126786] type=2000 audit(1274020371.125:1): initialized
[    0.139050] Trying to unpack rootfs image as initramfs...
[    0.154402] highmem bounce pool size: 64 pages
[    0.154411] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.156273] VFS: Disk quotas dquot_6.5.2
[    0.156351] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.162333] fuse init (API version 7.13)
[    0.162456] msgmni has been set to 1716
[    0.162753] alg: No test for stdrng (krng)
[    0.162829] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.162833] io scheduler noop registered
[    0.162836] io scheduler anticipatory registered
[    0.162838] io scheduler deadline registered
[    0.162887] io scheduler cfq registered (default)
[    0.163035] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.163067] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.163336] ACPI: AC Adapter [AC] (on-line)
[    0.163417] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.163614] ACPI: Lid Switch [LID]
[    0.163668] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.163673] ACPI: Sleep Button [SLPB]
[    0.163734] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.163737] ACPI: Power Button [PWRF]
[    0.170327] Marking TSC unstable due to TSC halts in idle
[    0.170449] processor LNXCPU:00: registered as cooling_device0
[    0.171771] Switching to clocksource acpi_pm
[    0.173503] thermal LNXTHERM:01: registered as thermal_zone0
[    0.173513] ACPI: Thermal Zone [THM0] (62 C)
[    0.175276] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.176053] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.176060] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.176069] serial 0000:00:1f.6: PCI INT B disabled
[    0.177221] brd: module loaded
[    0.177782] loop: module loaded
[    0.177879] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.178011] ata_piix 0000:00:1f.1: version 2.13
[    0.178020] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.178359] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.178364] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.178413] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.184238] isapnp: Scanning for PnP cards...
[    0.189718] scsi0 : ata_piix
[    0.189999] scsi1 : ata_piix
[    0.191072] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.191076] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.191819] Fixed MDIO Bus: probed
[    0.191862] PPP generic driver version 2.4.2
[    0.191938] tun: Universal TUN/TAP device driver, 1.6
[    0.191940] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.192110] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.259261] ACPI: Battery Slot [BAT0] (battery present)
[    0.259409] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.259753] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.259759] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.259782] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.259787] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.259879] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.259916] ehci_hcd 0000:00:1d.7: debug port 1
[    0.263808] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.263823] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xd0100000
[    0.288074] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.288278] usb usb1: configuration #1 chosen from 1 choice
[    0.288319] hub 1-0:1.0: USB hub found
[    0.288333] hub 1-0:1.0: 6 ports detected
[    0.288420] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.288452] uhci_hcd: USB Universal Host Controller Interface driver
[    0.288746] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.288760] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.288772] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.288777] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.288840] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.288870] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[    0.288984] usb usb2: configuration #1 chosen from 1 choice
[    0.289015] hub 2-0:1.0: USB hub found
[    0.289024] hub 2-0:1.0: 2 ports detected
[    0.289229] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.289582] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.289586] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.289594] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.289598] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.289643] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.289664] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    0.289764] usb usb3: configuration #1 chosen from 1 choice
[    0.289794] hub 3-0:1.0: USB hub found
[    0.289803] hub 3-0:1.0: 2 ports detected
[    0.289854] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.289862] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.289866] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.289907] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.289927] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    0.290032] usb usb4: configuration #1 chosen from 1 choice
[    0.290066] hub 4-0:1.0: USB hub found
[    0.290074] hub 4-0:1.0: 2 ports detected
[    0.290181] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.349548] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.349560] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.349773] mice: PS/2 mouse device common for all mice
[    0.349947] rtc_cmos 00:06: RTC can wake from S4
[    0.350005] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.350029] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.350194] device-mapper: uevent: version 1.0.3
[    0.350354] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.350889] device-mapper: multipath: version 1.1.0 loaded
[    0.350893] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.351998] EISA: Probing bus 0 at eisa.0
[    0.352036] Cannot allocate resource for EISA slot 1
[    0.352041] Cannot allocate resource for EISA slot 2
[    0.352044] Cannot allocate resource for EISA slot 3
[    0.352046] Cannot allocate resource for EISA slot 4
[    0.352049] Cannot allocate resource for EISA slot 5
[    0.352051] Cannot allocate resource for EISA slot 6
[    0.352053] Cannot allocate resource for EISA slot 7
[    0.352058] EISA: Detected 0 cards.
[    0.354423] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.354997] cpuidle: using governor ladder
[    0.355067] cpuidle: using governor menu
[    0.355600] TCP cubic registered
[    0.355788] NET: Registered protocol family 10
[    0.356756] ata2.00: ATAPI: MATSHITADVD-RAM UJ-830Sx, 1.00, max UDMA/33
[    0.357059] ata1.00: ATA-6: HTS541060G9AT00, MB3IA60A, max UDMA/100
[    0.357063] ata1.00: 117210240 sectors, multi 16: LBA 
[    0.357328] lo: Disabled Privacy Extensions
[    0.357681] NET: Registered protocol family 17
[    0.357897] P-state transition latency capped at 20 uS
[    0.358207] Using IPI No-Shortcut mode
[    0.358309] PM: Resume from disk failed.
[    0.358325] registered taskstats version 1
[    0.358561]   Magic number: 10:158:536
[    0.358586] bdi 1:14: hash matches
[    0.358694] rtc_cmos 00:06: setting system clock to 2010-05-16 14:32:51 UTC (1274020371)
[    0.358698] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.358700] EDD information not available.
[    0.364896] ata2.00: configured for UDMA/33
[    0.365483] ata1.00: configured for UDMA/100
[    0.713578] Freeing initrd memory: 7749k freed
[    0.808580] isapnp: No Plug & Play device found
[    0.808869] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3I PQ: 0 ANSI: 5
[    0.809092] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    0.809151] sd 0:0:0:0: [sda] Write Protect is off
[    0.809155] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.809184] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.809406]  sda:
[    0.809639] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.811635] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-830Sx 1.00 PQ: 0 ANSI: 5
[    0.816216] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.816220] Uniform CD-ROM driver Revision: 3.20
[    0.816344] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.816402] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.825862]  sda1 sda2 sda3 sda4 < sda5 >
[    0.852750] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.852772] Freeing unused kernel memory: 656k freed
[    0.853324] Write protecting the kernel text: 4676k
[    0.853367] Write protecting the kernel read-only data: 1840k
[    0.871899] udev: starting version 151
[    0.920084] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    1.096585] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.096591] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.096845] usb 3-2: configuration #1 chosen from 1 choice
[    1.097447] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    1.097453] e100 0000:02:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    1.121025] e100 0000:02:08.0: PME# disabled
[    1.123056] e100: eth0: e100_probe: addr 0xd0201000, irq 11, MAC addr 00:0a:e4:c5:55:cd
[    1.146491] usbcore: registered new interface driver hiddev
[    1.163165] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    1.163404] generic-usb 0003:093A:2500.0001: input,hidraw0: USB HID v1.10 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.1-2/input0
[    1.163431] usbcore: registered new interface driver usbhid
[    1.163529] usbhid: v2.6:USB HID core driver
[    1.389021] kjournald starting.  Commit interval 5 seconds
[    1.389034] EXT3-fs: mounted filesystem with ordered data mode.
[   44.292585] Adding 923696k swap on /dev/sda5.  Priority:-1 extents:1 across:923696k 
[   44.345478] udev: starting version 151
[   44.522837] lp: driver loaded but no devices found
[   44.540070] intel_rng: FWH not detected
[   44.550768] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.575435] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   44.575520] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   44.761971] Linux agpgart interface v0.103
[   44.927480] Non-volatile memory driver v1.3
[   44.936042] [drm] Initialized drm 1.1.0 20060810
[   44.940984] psmouse serio1: ID: 10 00 64
[   44.941547] parport_pc 00:09: reported by Plug and Play ACPI
[   44.941586] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   44.952951] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   44.953752] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   44.968831] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   44.986608] lib80211: common routines for IEEE802.11 drivers
[   44.986614] lib80211_crypt: registered algorithm 'NULL'
[   45.001844] type=1505 audit(1274016816.141:2):  operation="profile_load" pid=551 name="/sbin/dhclient3"
[   45.002571] type=1505 audit(1274016816.141:3):  operation="profile_load" pid=551 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   45.002960] type=1505 audit(1274016816.141:4):  operation="profile_load" pid=551 name="/usr/lib/connman/scripts/dhclient-script"
[   45.004100] EXT3 FS on sda3, internal journal
[   45.032339] lp0: using parport0 (interrupt-driven).
[   45.035610] ppdev: user-space parallel port driver
[   45.055403] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   45.055408] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   45.144333] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0512]
[   45.144353] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[   45.144356] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[   45.144362] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21022, devctl 0x64
[   45.146117] i915 0000:00:02.0: power state changed by ACPI to D0
[   45.146130] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   45.146137] i915 0000:00:02.0: setting latency timer to 64
[   45.168211] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   45.168216] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   45.168269] [drm] set up 7M of stolen space
[   45.184277] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.235774] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   45.235779] thinkpad_acpi: http://ibm-acpi.sf.net/
[   45.235781] thinkpad_acpi: ThinkPad BIOS 1WET85WW (2.05 ), EC 1VHT28WW-1.04
[   45.235784] thinkpad_acpi: IBM ThinkPad R50e, model 1834U2G
[   45.235788] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
[   45.235790] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
[   45.256477] Registered led device: tpacpi::thinklight
[   45.257070] Registered led device: tpacpi::power
[   45.257642] Registered led device: tpacpi::standby
[   45.265935] thinkpad_acpi: brightness: will use unverified default: brightness_mode=3
[   45.265939] thinkpad_acpi: brightness: please report to ibm-acpi-devel@lists.sourceforge.net whether it works well or not on your ThinkPad
[   45.270240] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   45.278777] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[   45.312506] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   45.331879] [drm] initialized overlay support
[   45.607448] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input8
[   45.608250] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0478, PCI irq 11
[   45.608254] yenta_cardbus 0000:02:00.0: Socket status: 30000007
[   45.608262] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   45.608267] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: clean.
[   45.609447] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[   45.609451] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[   45.611958] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[   45.611965] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[   45.614212] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   45.614266] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[   45.626797] nf_conntrack version 0.5.0 (15895 buckets, 63580 max)
[   45.628219] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   45.628223] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   45.628225] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   45.791290] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   45.906050] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   45.947618] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   45.948461] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   45.948821] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   45.949120] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   45.949560] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   46.511451] fb0: inteldrmfb frame buffer device
[   46.511456] registered panic notifier
[   46.511468] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   46.511520] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   46.511550] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   46.520760] vga16fb: initializing
[   46.520765] vga16fb: mapped to 0xc00a0000
[   46.520771] vga16fb: not registering due to another framebuffer present
[   46.704725] Console: switching to colour frame buffer device 128x48
[   47.768048] intel8x0_measure_ac97_clock: measured 54070 usecs (2605 samples)
[   47.768054] intel8x0: clocking to 48000
[   50.764724] type=1505 audit(1274016821.905:5):  operation="profile_load" pid=948 name="/usr/share/gdm/guest-session/Xsession"
[   50.766420] type=1505 audit(1274016821.905:6):  operation="profile_replace" pid=949 name="/sbin/dhclient3"
[   50.767167] type=1505 audit(1274016821.905:7):  operation="profile_replace" pid=949 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   50.767557] type=1505 audit(1274016821.905:8):  operation="profile_replace" pid=949 name="/usr/lib/connman/scripts/dhclient-script"
[   50.771660] type=1505 audit(1274016821.909:9):  operation="profile_load" pid=950 name="/usr/bin/evince"
[   50.781307] type=1505 audit(1274016821.921:10):  operation="profile_load" pid=950 name="/usr/bin/evince-previewer"
[   50.787513] type=1505 audit(1274016821.925:11):  operation="profile_load" pid=950 name="/usr/bin/evince-thumbnailer"
[   50.913139] type=1505 audit(1274016822.053:12):  operation="profile_load" pid=952 name="/usr/bin/freshclam"
[   51.032862] type=1505 audit(1274016822.173:13):  operation="profile_load" pid=953 name="/usr/sbin/clamd"
[   51.035417] type=1505 audit(1274016822.173:14):  operation="profile_load" pid=1018 name="/usr/lib/cups/backend/cups-pdf"
[   51.154167] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   51.578218] IBM machine detected. Enabling interrupts during APM calls.
[   51.578223] apm: BIOS not found.
```

---

### Post by Duncan J Murray on 2010-06-01
Had exactly the same problem with my Dad's R50e.  I should have been warned off by the lucid iso booting into a blank screen, but I nonetheless upgraded from karmic.

I attempted workaround A, which, as you also noticed allows booting to the desktop, but doesn't do video.  I tried othef workarounds, including quite a convoluted one, but the only thing that worked was booting to .31 rather than .32 kernel.

Really annoying - I hope it gets sorted in a later kernel.  I just don't understand how things can break like this on upgrade, but then I suppose I simply shouldn't have upgraded!

Duncan

---

### Post by sancelot on 2010-06-08
what has happening if you upgrade to ubuntu maverick ?

---

### Post by Rosya on 2010-06-27
hiiii
i'm very new to ubuntu and it's my first time using Linux
i'm using R50e and i have the same problem
and i tried this

on setup i used boot editing by pressing e
and add this line to boot option  i915.modeset=1
then after finishing ubuntu installation i found the i must do this everytime i boot
so i searched and found this workaround ushing 2 commands

- echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
- sudo update-initramfs -u

and it worked for me

but i cant play videos and i cant play mp3 files .
i run update manager and i updated and no hope
so is there any solution .. and if not .. which version of Linux i must use to run in peace ?

---

### Post by Duncan J Murray on 2010-07-24
I think it's still a problem.  The only proper solution appears to use a different kernel version number.  So you could try selecting the 3rd option down on your boot-up, or waiting for Maverick in October.

Bit disappointing for an LTS release.

---

