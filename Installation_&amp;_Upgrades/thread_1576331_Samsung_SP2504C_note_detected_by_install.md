---
title: "Samsung SP2504C note detected by install"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by Andykvakk on 2010-09-17
I am trying to install Ubuntu on my home-built PC, but i cannot install because Ubuntu does not see my Samsung SP2504C harddrive during install. I have tried Ubuntu Server, Ubuntu Desktop Alternate and Live CD install.

This is what happens:
1. The harddrive is visible in Gparted
2. The harddrive is visible in fdisk, fdisk -l gives this output (i have deleted all partitions on the harddrive).

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe52fe52

   Device Boot      Start         End      Blocks   Id  System

```

3. The graphical installation program does not recognize the harddrive and the alternate install does not recognize the harddrive.

I have used Ubuntu on this computer for a long time, but moved the other harddrives to another machine and want to install Ubuntu onto the 250gb harddrive. I have two Samsung S2504C, and its the same problem whith both drives on this machine and on another machine which is brand new. Is there any solution to this? The MB is an ASUS P5GD1, and i have tried both AHCI mode and IDE mode in bios. Other harddrives work, but not the SP2504C.

Output of dmesg:
```
ubuntu@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
[    0.000000] Command line: initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffb0000 - 00000000bffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffbe000 - 00000000bfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbffb0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bffb0000 (usable)
[    0.000000]  modified: 00000000bffb0000 - 00000000bffbe000 (ACPI data)
[    0.000000]  modified: 00000000bffbe000 - 00000000bfff0000 (ACPI NVS)
[    0.000000]  modified: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bffb0000
[    0.000000] Warning: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bffb0000 page 4k
[    0.000000] kernel direct mapping tables up to bffb0000 @ 10000-15000
[    0.000000] RAMDISK: 7f69d000 - 7fffede7
[    0.000000] ACPI: RSDP 00000000000fadb0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bffb0000 00034 (v01 A M I  OEMRSDT  10000513 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bffb0200 00081 (v01 A M I  OEMFACP  10000513 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bffb0400 06A7C (v01  A0045 A0045001 00000001 INTL 02002026)
[    0.000000] ACPI: FACS 00000000bffbe000 00040
[    0.000000] ACPI: APIC 00000000bffb0390 00070 (v01 A M I  OEMAPIC  10000513 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bffbe040 00046 (v01 A M I  AMI_OEM  10000513 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bffb6e80 0003C (v01 A M I  OEMMCFG  10000513 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000bffb0000
[    0.000000] Bootmem setup node 0 0000000000000000-00000000bffb0000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000002fff7] pages 18
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00bffb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a2fe64]    TEXT DATA BSS ==> [0001000000 - 0001a2fe64]
[    0.000000]   #3 [007f69d000 - 007fffede7]          RAMDISK ==> [007f69d000 - 007fffede7]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0001a30000 - 0001a3028c]              BRK ==> [0001a30000 - 0001a3028c]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff880002000000-ffff8800049fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bffb0
[    0.000000] On node 0 totalpages: 786239
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3825 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10695 pages used for memmap
[    0.000000]   DMA32 zone: 771561 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3fb80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 775386
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3081448k/3145408k available (5422k kernel code, 452k absent, 63508k reserved, 2979k data, 880k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 31457280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3211.242 MHz processor.
[    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6422.48 BogoMIPS (lpj=32112420)
[    0.010038] Security Framework initialized
[    0.010063] AppArmor: AppArmor initialized
[    0.010696] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013218] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.014398] Mount-cache hash table entries: 256
[    0.014590] Initializing cgroup subsys ns
[    0.014597] Initializing cgroup subsys cpuacct
[    0.014602] Initializing cgroup subsys memory
[    0.014611] Initializing cgroup subsys devices
[    0.014615] Initializing cgroup subsys freezer
[    0.014617] Initializing cgroup subsys net_cls
[    0.014648] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.014652] CPU: L2 cache: 2048K
[    0.014657] CPU 0/0x0 -> Node 0
[    0.014659] CPU: Physical Processor ID: 0
[    0.014661] CPU: Processor Core ID: 0
[    0.014665] mce: CPU supports 4 MCE banks
[    0.014679] CPU0: Thermal monitoring enabled (TM1)
[    0.014685] using mwait in idle threads.
[    0.014688] Performance Events: no PMU driver, software events only.
[    0.022843] ACPI: Core revision 20090903
[    0.040011] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040018] ftrace: allocating 22527 entries in 89 pages
[    0.050075] Setting APIC routing to flat
[    0.050393] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.159505] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[    0.160000] APIC calibration not consistent with PM-Timer: 460ms instead of 100ms
[    0.160000] APIC delta adjusted to PM-Timer: 1254436 (5770503)
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.020000] CPU: L2 cache: 2048K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 0
[    0.020000] CPU1: Thermal monitoring enabled (TM1)
[    0.310141] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[    0.310152] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320024] Brought up 2 CPUs
[    0.320029] Total of 2 processors activated (12845.31 BogoMIPS).
[    0.320489] CPU0 attaching sched-domain:
[    0.320495]  domain 0: span 0-1 level SIBLING
[    0.320498]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.320505]   domain 1: span 0-1 level MC
[    0.320508]    groups: 0-1 (cpu_power = 1178)
[    0.320516] CPU1 attaching sched-domain:
[    0.320518]  domain 0: span 0-1 level SIBLING
[    0.320521]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.320527]   domain 1: span 0-1 level MC
[    0.320529]    groups: 0-1 (cpu_power = 1178)
[    0.320665] devtmpfs: initialized
[    0.320665] regulator: core version 0.5
[    0.320665] Time: 10:10:21  Date: 09/17/10
[    0.320665] NET: Registered protocol family 16
[    0.320665] Trying to unpack rootfs image as initramfs...
[    0.320849] ACPI: bus type pci registered
[    0.320959] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.320964] PCI: Not using MMCONFIG.
[    0.320968] PCI: Using configuration type 1 for base access
[    0.322606] bio: create slab <bio-0> at 0
[    0.323905] ACPI: EC: Look up EC in DSDT
[    0.330629] ACPI: Executed 1 blocks of module-level executable AML code
[    0.343856] ACPI: Interpreter enabled
[    0.343865] ACPI: (supports S0 S1 S3 S4 S5)
[    0.343910] ACPI: Using IOAPIC for interrupt routing
[    0.343996] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.353110] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.360285] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.371904] ACPI Warning: Incorrect checksum in table [OEMB] - 5D, should be 51 (20090903/tbutils-314)
[    0.372092] ACPI: No dock devices found.
[    0.372325] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.372502] pci 0000:00:1b.0: reg 10 64bit mmio: [0xcfdf4000-0xcfdf7fff]
[    0.372556] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.372562] pci 0000:00:1b.0: PME# disabled
[    0.372641] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.372647] pci 0000:00:1c.0: PME# disabled
[    0.372728] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.372734] pci 0000:00:1c.1: PME# disabled
[    0.372797] pci 0000:00:1d.0: reg 20 io port: [0x9000-0x901f]
[    0.372859] pci 0000:00:1d.1: reg 20 io port: [0x9400-0x941f]
[    0.372920] pci 0000:00:1d.2: reg 20 io port: [0x9800-0x981f]
[    0.372980] pci 0000:00:1d.3: reg 20 io port: [0xa000-0xa01f]
[    0.373048] pci 0000:00:1d.7: reg 10 32bit mmio: [0xcfdff800-0xcfdffbff]
[    0.373109] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.373115] pci 0000:00:1d.7: PME# disabled
[    0.373257] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.373267] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.373274] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.373281] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 0290-029f
[    0.373313] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.373322] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.373331] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.373340] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.373349] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.373401] pci 0000:00:1f.2: reg 10 io port: [0xb800-0xb807]
[    0.373409] pci 0000:00:1f.2: reg 14 io port: [0xb400-0xb403]
[    0.373418] pci 0000:00:1f.2: reg 18 io port: [0xb000-0xb007]
[    0.373426] pci 0000:00:1f.2: reg 1c io port: [0xa800-0xa803]
[    0.373435] pci 0000:00:1f.2: reg 20 io port: [0xa400-0xa40f]
[    0.373443] pci 0000:00:1f.2: reg 24 32bit mmio: [0xcfdffc00-0xcfdfffff]
[    0.373470] pci 0000:00:1f.2: PME# supported from D3hot
[    0.373475] pci 0000:00:1f.2: PME# disabled
[    0.373530] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.373612] pci 0000:00:1c.0: bridge io port: [0xe000-0xefff]
[    0.373690] pci 0000:02:00.0: reg 10 64bit mmio: [0xcfffc000-0xcfffffff]
[    0.373702] pci 0000:02:00.0: reg 18 io port: [0xd800-0xd8ff]
[    0.373733] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xcffc0000-0xcffdffff]
[    0.373781] pci 0000:02:00.0: supports D1 D2
[    0.373785] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.373793] pci 0000:02:00.0: PME# disabled
[    0.373848] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.373854] pci 0000:00:1c.1: bridge 32bit mmio: [0xcff00000-0xcfffffff]
[    0.373918] pci 0000:01:09.0: reg 10 32bit mmio: [0xcfeef000-0xcfeeffff]
[    0.373928] pci 0000:01:09.0: reg 14 io port: [0xc800-0xc83f]
[    0.373937] pci 0000:01:09.0: reg 18 32bit mmio: [0xcfea0000-0xcfebffff]
[    0.373982] pci 0000:01:09.0: supports D1 D2
[    0.373987] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.373994] pci 0000:01:09.0: PME# disabled
[    0.374039] pci 0000:01:0b.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.374050] pci 0000:01:0b.0: reg 14 io port: [0xc000-0xc0ff]
[    0.374059] pci 0000:01:0b.0: reg 18 32bit mmio: [0xcfef0000-0xcfefffff]
[    0.374086] pci 0000:01:0b.0: reg 30 32bit mmio pref: [0xcfec0000-0xcfedffff]
[    0.374110] pci 0000:01:0b.0: supports D1 D2
[    0.374150] pci 0000:00:1e.0: transparent bridge
[    0.374156] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.374162] pci 0000:00:1e.0: bridge 32bit mmio: [0xcfe00000-0xcfefffff]
[    0.374171] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.374195] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.374414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.374582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.374655] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.379960] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.380187] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.380376] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.380563] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.380748] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.380938] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.381125] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.381315] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.381521] vgaarb: device added: PCI:0000:01:0b.0,decodes=io+mem,owns=io+mem,locks=none
[    0.381526] vgaarb: loaded
[    0.381724] SCSI subsystem initialized
[    0.381840] libata version 3.00 loaded.
[    0.381953] usbcore: registered new interface driver usbfs
[    0.381976] usbcore: registered new interface driver hub
[    0.382025] usbcore: registered new device driver usb
[    0.382233] ACPI: WMI: Mapper loaded
[    0.382237] PCI: Using ACPI for IRQ routing
[    0.382478] NetLabel: Initializing
[    0.382482] NetLabel:  domain hash size = 128
[    0.382485] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.382506] NetLabel:  unlabeled traffic allowed by default
[    0.382636] hpet clockevent registered
[    0.382642] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.382649] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.382658] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    2.730885] Switching to clocksource tsc
[    2.733372] AppArmor: AppArmor Filesystem Enabled
[    2.733410] pnp: PnP ACPI init
[    2.733449] ACPI: bus type pnp registered
[    2.742356] pnp: PnP ACPI: found 16 devices
[    2.742362] ACPI: ACPI bus type pnp unregistered
[    2.742389] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    2.742408] system 00:08: ioport range 0x290-0x297 has been reserved
[    2.742421] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    2.742427] system 00:09: ioport range 0x800-0x87f has been reserved
[    2.742432] system 00:09: ioport range 0x400-0x41f has been reserved
[    2.742437] system 00:09: ioport range 0x480-0x4bf has been reserved
[    2.742443] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    2.742448] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[    2.742454] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[    2.742460] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    2.742475] system 00:0b: iomem range 0xffc00000-0xfff7ffff has been reserved
[    2.742489] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    2.742535] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    2.742547] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    2.742559] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    2.742571] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    2.742577] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    2.742583] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
[    2.747531] pci 0000:01:0b.0: BAR 6: address space collision on of device [0xcfec0000-0xcfedffff]
[    2.747591] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    2.747597] pci 0000:00:1c.0:   IO window: 0xe000-0xefff
[    2.747605] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    2.747612] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    2.747622] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    2.747628] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    2.747636] pci 0000:00:1c.1:   MEM window: 0xcff00000-0xcfffffff
[    2.747643] pci 0000:00:1c.1:   PREFETCH window: 0x000000c0400000-0x000000c05fffff
[    2.747657] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    2.747662] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    2.747670] pci 0000:00:1e.0:   MEM window: 0xcfe00000-0xcfefffff
[    2.747677] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    2.747706]   alloc irq_desc for 16 on node -1
[    2.747711]   alloc kstat_irqs on node -1
[    2.747725] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.747734] pci 0000:00:1c.0: setting latency timer to 64
[    2.747749]   alloc irq_desc for 17 on node -1
[    2.747752]   alloc kstat_irqs on node -1
[    2.747758] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.747765] pci 0000:00:1c.1: setting latency timer to 64
[    2.747777] pci 0000:00:1e.0: setting latency timer to 64
[    2.747785] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    2.747790] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    2.747795] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    2.747799] pci_bus 0000:03: resource 1 mem: [0xc0000000-0xc01fffff]
[    2.747804] pci_bus 0000:03: resource 2 pref mem [0xc0200000-0xc03fffff]
[    2.747808] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    2.747812] pci_bus 0000:02: resource 1 mem: [0xcff00000-0xcfffffff]
[    2.747818] pci_bus 0000:02: resource 2 pref mem [0xc0400000-0xc05fffff]
[    2.747823] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    2.747828] pci_bus 0000:01: resource 1 mem: [0xcfe00000-0xcfefffff]
[    2.747832] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    2.747836] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    2.747840] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    2.747911] NET: Registered protocol family 2
[    2.748291] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.751098] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.757067] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.757844] TCP: Hash tables configured (established 524288 bind 65536)
[    2.757850] TCP reno registered
[    2.758065] NET: Registered protocol family 1
[    2.758247] pci 0000:01:09.0: Firmware left e100 interrupts enabled; disabling
[    2.758261] pci 0000:01:0b.0: Boot video device
[    2.758651] Scanning for low memory corruption every 60 seconds
[    2.758903] audit: initializing netlink socket (disabled)
[    2.758922] type=2000 audit(1284718222.750:1): initialized
[    2.769740] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.772725] VFS: Disk quotas dquot_6.5.2
[    2.772856] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.774186] fuse init (API version 7.13)
[    2.774356] msgmni has been set to 6018
[    2.774787] alg: No test for stdrng (krng)
[    2.774894] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.774900] io scheduler noop registered
[    2.774903] io scheduler anticipatory registered
[    2.774906] io scheduler deadline registered
[    2.774984] io scheduler cfq registered (default)
[    2.775231]   alloc irq_desc for 24 on node -1
[    2.775236]   alloc kstat_irqs on node -1
[    2.775254] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    2.775266] pcieport 0000:00:1c.0: setting latency timer to 64
[    2.775445]   alloc irq_desc for 25 on node -1
[    2.775449]   alloc kstat_irqs on node -1
[    2.775460] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    2.775472] pcieport 0000:00:1c.1: setting latency timer to 64
[    2.775620] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.775766] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.775957] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    2.775964] ACPI: Power Button [PWRB]
[    2.776044] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    2.776049] ACPI: Power Button [PWRF]
[    2.776936] ACPI: SSDT 00000000bffb6ec0 002FC (v01    AMI   CPU1PM 00000001 INTL 02002026)
[    2.777429] processor LNXCPU:00: registered as cooling_device0
[    2.777704] ACPI Warning: Incorrect checksum in table [SSDT] - E8, should be 8F (20090903/tbutils-314)
[    2.777713] ACPI: SSDT 00000000bffb71c0 002FC (v01    AMI   CPU2PM 00000001 INTL 02002026)
[    2.777984] processor LNXCPU:01: registered as cooling_device1
[    2.783772] Linux agpgart interface v0.103
[    2.783839] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.786327] brd: module loaded
[    2.787285] loop: module loaded
[    2.787487] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.787704] ata_piix 0000:00:1f.1: version 2.13
[    2.787737]   alloc irq_desc for 18 on node -1
[    2.787742]   alloc kstat_irqs on node -1
[    2.787756] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.787839] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.788029] scsi0 : ata_piix
[    2.788176] scsi1 : ata_piix
[    2.791023] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.791031] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.791168]   alloc irq_desc for 19 on node -1
[    2.791172]   alloc kstat_irqs on node -1
[    2.791185] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.791215] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.791291] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.791396] scsi2 : ata_piix
[    2.791798] scsi3 : ata_piix
[    2.791874] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xa400 irq 19
[    2.791879] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xa800 bmdma 0xa408 irq 19
[    2.792635] Fixed MDIO Bus: probed
[    2.792709] PPP generic driver version 2.4.2
[    2.792807] tun: Universal TUN/TAP device driver, 1.6
[    2.792811] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.792993] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.793041]   alloc irq_desc for 23 on node -1
[    2.793046]   alloc kstat_irqs on node -1
[    2.793057] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.793084] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.793090] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.793157] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.793199] ehci_hcd 0000:00:1d.7: debug port 1
[    2.797079] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.797119] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xcfdff800
[    2.830030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.830247] usb usb1: configuration #1 chosen from 1 choice
[    2.830307] hub 1-0:1.0: USB hub found
[    2.830320] hub 1-0:1.0: 8 ports detected
[    2.830434] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.830465] uhci_hcd: USB Universal Host Controller Interface driver
[    2.830524] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.830536] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.830541] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.830609] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.830642] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009000
[    2.830788] usb usb2: configuration #1 chosen from 1 choice
[    2.830837] hub 2-0:1.0: USB hub found
[    2.830848] hub 2-0:1.0: 2 ports detected
[    2.830919] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.830928] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.830933] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.830987] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.831016] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009400
[    2.831163] usb usb3: configuration #1 chosen from 1 choice
[    2.831208] hub 3-0:1.0: USB hub found
[    2.831218] hub 3-0:1.0: 2 ports detected
[    2.831292] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.831301] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.831306] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.831363] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.831405] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009800
[    2.831553] usb usb4: configuration #1 chosen from 1 choice
[    2.831600] hub 4-0:1.0: USB hub found
[    2.831610] hub 4-0:1.0: 2 ports detected
[    2.831687] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.831696] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.831701] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.831755] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.831792] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000a000
[    2.831948] usb usb5: configuration #1 chosen from 1 choice
[    2.831993] hub 5-0:1.0: USB hub found
[    2.832003] hub 5-0:1.0: 2 ports detected
[    2.832181] PNP: No PS/2 controller found. Probing ports directly.
[    2.834667] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.834677] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.834810] mice: PS/2 mouse device common for all mice
[    2.834972] rtc_cmos 00:03: RTC can wake from S4
[    2.835034] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.835063] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.835300] device-mapper: uevent: version 1.0.3
[    2.835510] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.835618] device-mapper: multipath: version 1.1.0 loaded
[    2.835623] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.835868] cpuidle: using governor ladder
[    2.835872] cpuidle: using governor menu
[    2.836581] TCP cubic registered
[    2.836812] NET: Registered protocol family 10
[    2.837547] lo: Disabled Privacy Extensions
[    2.838082] NET: Registered protocol family 17
[    2.839250] PM: Resume from disk failed.
[    2.839269] registered taskstats version 1
[    2.839622]   Magic number: 10:969:173
[    2.839670] pci_express 0000:00:1c.0:pcie01: hash matches
[    2.839727] rtc_cmos 00:03: setting system clock to 2010-09-17 10:10:23 UTC (1284718223)
[    2.839733] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.839736] EDD information not available.
[    2.994174] ata1.01: ATAPI: LG, 1&#65533;00, max UDMA/66
[    2.994216] ata1.01: limited to UDMA/33 due to 40-wire cable
[    2.994327] ata3.00: ATA-7: SAMSUNG SP2504C, VT100-33, max UDMA7
[    2.994333] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.010439] ata1.01: model number mismatch 'LG' != 'LO 8   8 DVT-RO&#65533; TR\-x160B 8   8   8   8'
[    3.010445] ata1.01: revalidation failed (errno=-19)
[    3.010451] ata1.01: limiting speed to UDMA/33:PIO3
[    3.010519] ata3.00: configured for UDMA/133
[    3.271204] usb 1-3: new high speed USB device using ehci_hcd and address 4
[    3.272150] Freeing initrd memory: 9607k freed
[    3.422846] usb 1-3: configuration #1 chosen from 1 choice
[    3.540099] usb 1-7: new high speed USB device using ehci_hcd and address 5
[    3.692531] usb 1-7: configuration #1 chosen from 1 choice
[    3.970015] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.153814] usb 2-1: configuration #1 chosen from 1 choice
[    4.430015] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    4.610830] usb 2-2: configuration #1 chosen from 1 choice
[    8.151885] ata1.01: model number mismatch 'LG' != 'LG       TVT-PO&#65533; TRT-8160P'
[    8.151890] ata1.01: revalidation failed (errno=-19)
[    8.151893] ata1.01: disabled
[    8.152051] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5
[    8.152210] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    8.152325] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    8.152393] sd 2:0:0:0: [sda] Write Protect is off
[    8.152397] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.152431] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.152623]  sda: sda1
[    8.162156] sd 2:0:0:0: [sda] Attached SCSI disk
[    8.162177] Freeing unused kernel memory: 880k freed
[    8.162623] Write protecting the kernel read-only data: 7696k
[    8.188095] udev: starting version 151
[    8.277182] sky2 driver version 1.25
[    8.277240] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.277262] sky2 0000:02:00.0: setting latency timer to 64
[    8.277301] sky2 0000:02:00.0: Yukon-2 EC chip revision 1
[    8.277399]   alloc irq_desc for 26 on node -1
[    8.277403]   alloc kstat_irqs on node -1
[    8.277424] sky2 0000:02:00.0: irq 26 for MSI/MSI-X
[    8.334463] sky2 eth0: addr 00:11:d8:14:a6:29
[    8.391977] [drm] Initialized drm 1.1.0 20060810
[    8.404576] usbcore: registered new interface driver hiddev
[    8.408650] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    8.408655] e100: Copyright(c) 1999-2006 Intel Corporation
[    8.408718] e100 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.417348] Initializing USB Mass Storage driver...
[    8.417592] scsi4 : SCSI emulation for USB Mass Storage devices
[    8.418021] usb-storage: device found at 4
[    8.418024] usb-storage: waiting for device to settle before scanning
[    8.418064] scsi5 : SCSI emulation for USB Mass Storage devices
[    8.418256] usbcore: registered new interface driver usb-storage
[    8.418261] USB Mass Storage support registered.
[    8.418543] usb-storage: device found at 5
[    8.418547] usb-storage: waiting for device to settle before scanning
[    8.419853] input: CHICONY USB NetVista Full Width Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    8.419972] generic-usb 0003:04B3:3025.0001: input,hidraw0: USB HID v1.10 Keyboard [CHICONY USB NetVista Full Width Keyboard] on usb-0000:00:1d.0-1/input0
[    8.433710] e100 0000:01:09.0: PME# disabled
[    8.434826] e100: eth1: e100_probe: addr 0xcfeef000, irq 17, MAC addr 00:02:b3:a4:3b:fc
[    8.435961] Floppy drive(s): fd0 is 1.44M
[    8.444317] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
[    8.444532] generic-usb 0003:046D:C050.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2/input0
[    8.444595] usbcore: registered new interface driver usbhid
[    8.444605] usbhid: v2.6:USB HID core driver
[    8.453766] FDC 0 is a post-1991 82077
[    8.473900] [drm] radeon defaulting to kernel modesetting.
[    8.473906] [drm] radeon kernel modesetting enabled.
[    8.473986]   alloc irq_desc for 22 on node -1
[    8.473991]   alloc kstat_irqs on node -1
[    8.474004] radeon 0000:01:0b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.477256] [drm] radeon: Initializing kernel modesetting.
[    8.479989] [drm] register mmio base: 0xCFEF0000
[    8.479993] [drm] register mmio size: 65536
[    8.481237] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[    8.481261] [drm] Generation 2 PCI interface, using max accessible memory
[    8.481268] [drm] radeon: VRAM 128M
[    8.481271] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[    8.481274] [drm] radeon: GTT 512M
[    8.481277] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[    8.481319] [drm] radeon: irq initialized.
[    8.482025] [drm] Detected VRAM RAM=128M, BAR=256M
[    8.482030] [drm] RAM width 64bits DDR
[    8.482170] [TTM] Zone  kernel: Available graphics memory: 1545968 kiB.
[    8.482197] [drm] radeon: 128M of VRAM memory ready
[    8.482201] [drm] radeon: 512M of GTT memory ready.
[    8.482228] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    8.483607] [drm] radeon: cp idle (0x02000603)
[    8.483677] [drm] Loading R200 Microcode
[    8.484113] platform radeon_cp.0: firmware: requesting radeon/R200_cp.bin
[    8.487983] [drm] radeon: ring at 0x0000000020000000
[    8.488007] [drm] ring test succeeded in 0 usecs
[    8.488219] [drm] radeon: ib pool ready.
[    8.489026] [drm] ib test succeeded in 0 usecs
[    8.489226] [drm] Default TV standard: PAL
[    8.489230] [drm] 27.000000000 MHz TV ref clk
[    8.489236] [drm] DFP table revision: 4
[    8.489328] [drm] Default TV standard: PAL
[    8.489332] [drm] 27.000000000 MHz TV ref clk
[    8.489384] [drm] Radeon Display Connectors
[    8.489389] [drm] Connector 0:
[    8.489392] [drm]   VGA
[    8.489395] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    8.489399] [drm]   Encoders:
[    8.489402] [drm]     CRT1: INTERNAL_DAC1
[    8.489405] [drm] Connector 1:
[    8.489407] [drm]   DVI-I
[    8.489409] [drm]   HPD1
[    8.489413] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    8.489416] [drm]   Encoders:
[    8.489419] [drm]     CRT2: INTERNAL_DAC2
[    8.489421] [drm]     DFP1: INTERNAL_TMDS1
[    8.489424] [drm] Connector 2:
[    8.489427] [drm]   S-video
[    8.489429] [drm]   Encoders:
[    8.489432] [drm]     TV1: INTERNAL_DAC2
[    8.684667] [drm] fb mappable at 0xD0040000
[    8.684672] [drm] vram apper at 0xD0000000
[    8.684674] [drm] size 7056000
[    8.684676] [drm] fb depth is 24
[    8.684678] [drm]    pitch is 6720
[    8.684818] fb0: radeondrmfb frame buffer device
[    8.684821] registered panic notifier
[    8.684829] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:0b.0 on minor 0
[    8.687214] vga16fb: initializing
[    8.687219] vga16fb: mapped to 0xffff8800000a0000
[    8.687226] vga16fb: not registering due to another framebuffer present
[    8.813000] Console: switching to colour frame buffer device 210x65
[    9.407847] xor: automatically using best checksumming function: generic_sse
[    9.452499]    generic_sse:  4882.000 MB/sec
[    9.452503] xor: using function: generic_sse (4882.000 MB/sec)
[    9.455445] device-mapper: dm-raid45: initialized v0.2594b
[   13.412773] usb-storage: device scan complete
[   13.412778] usb-storage: device scan complete
[   13.413493] scsi 4:0:0:0: Direct-Access     Lexar    JD FireFly       1100 PQ: 0 ANSI: 0 CCS
[   13.414036] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   13.414366] scsi 5:0:0:0: Direct-Access     Generic  USB Storage-CFC  I19A PQ: 0 ANSI: 0 CCS
[   13.415117] scsi 5:0:0:1: Direct-Access     Generic  USB Storage-MSC  I19A PQ: 0 ANSI: 0 CCS
[   13.415364] sd 4:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[   13.415859] scsi 5:0:0:2: Direct-Access     Generic  USB Storage-SMC  I19A PQ: 0 ANSI: 0 CCS
[   13.416100] sd 4:0:0:0: [sdb] Write Protect is off
[   13.416106] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   13.416110] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   13.416625] scsi 5:0:0:3: Direct-Access     Generic  USB Storage-SDC  I19A PQ: 0 ANSI: 0 CCS
[   13.417327] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   13.417570] sd 5:0:0:1: Attached scsi generic sg3 type 0
[   13.417826] sd 5:0:0:2: Attached scsi generic sg4 type 0
[   13.418071] sd 5:0:0:3: Attached scsi generic sg5 type 0
[   13.419734] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   13.419742]  sdb: sdb1
[   13.423615] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   13.423622] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   13.423732] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[   13.426095] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[   13.429226] sd 5:0:0:2: [sde] Attached SCSI removable disk
[   13.430356] sd 5:0:0:3: [sdf] Attached SCSI removable disk
[   14.281865] aufs 2-standalone.tree-20091207
[   14.298377] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   25.482395] udev: starting version 151
[   25.770526] intel_rng: FWH not detected
[   26.145160] parport_pc 00:07: reported by Plug and Play ACPI
[   26.145216] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   26.408613] ppdev: user-space parallel port driver
[   26.530188] sky2 eth0: enabling interface
[   26.542372] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.563494] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   26.680009] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.680047] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.824362] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   27.748877] lp0: using parport0 (interrupt-driven).
[   28.963344] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   28.964186] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.687317] CPU0 attaching NULL sched-domain.
[   29.687326] CPU1 attaching NULL sched-domain.
[   29.724955] CPU0 attaching sched-domain:
[   29.724961]  domain 0: span 0-1 level SIBLING
[   29.724964]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   29.724972]   domain 1: span 0-1 level MC
[   29.724975]    groups: 0-1 (cpu_power = 1178)
[   29.724982] CPU1 attaching sched-domain:
[   29.724985]  domain 0: span 0-1 level SIBLING
[   29.724987]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   29.724994]   domain 1: span 0-1 level MC
[   29.724996]    groups: 0-1 (cpu_power = 1178)
[   36.285718] CPU0 attaching NULL sched-domain.
[   36.285728] CPU1 attaching NULL sched-domain.
[   36.322640] CPU0 attaching sched-domain:
[   36.322648]  domain 0: span 0-1 level SIBLING
[   36.322653]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   36.322665]   domain 1: span 0-1 level MC
[   36.322669]    groups: 0-1 (cpu_power = 1178)
[   36.322680] CPU1 attaching sched-domain:
[   36.322685]  domain 0: span 0-1 level SIBLING
[   36.322689]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   36.322700]   domain 1: span 0-1 level MC
[   36.322705]    groups: 0-1 (cpu_power = 1178)
[   39.020027] eth0: no IPv6 routers present
[   66.802859] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   66.806688] SGI XFS Quota Management subsystem
[   66.823604] JFS: nTxBlock = 8192, nTxLock = 65536
[   66.846168] NTFS driver 2.1.29 [Flags: R/O MODULE].
[   66.883221] QNX4 filesystem 0.2.3 registered.
[   66.940804] Btrfs loaded
[   82.278454] end_request: I/O error, dev fd0, sector 0
[   94.358565] end_request: I/O error, dev fd0, sector 0
[  279.888944] end_request: I/O error, dev fd0, sector 0
[  291.971153] end_request: I/O error, dev fd0, sector 0
ubuntu@ubuntu:~$ 

```

Output of lspci:
```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
01:0b.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
ubuntu@ubuntu:~$ 

```

---

