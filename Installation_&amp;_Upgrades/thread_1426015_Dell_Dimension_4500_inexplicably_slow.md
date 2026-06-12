---
title: "Dell Dimension 4500 inexplicably slow"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by Bryan Pace on 2010-03-09
I’m trying to boot Ubuntu on a somewhat upgraded Dell Dimension 4500.

It runs fine on that machine in VirtualBox on Windows XP SP3.  Even the compositing window manager is usable when the virtual machine is full-screen, which surprised me.

If I try to run it directly on the hardware, it’s glacially slow.  It’s about 30 times slower than in the virtual machine.  At first I thought nothing was happening, but it’s just extremely slow.  There isn’t a particular stage that can be singled out; everything is equally affected.

The initial options screen comes up without delay.  It becomes slow immediately upon loading the kernel, either when starting a live session from the CD or installing to hard disk.  From the text start-up menu, it’s immediately after:

[INDENT][FONT="Courier New"]Loading /casper/vmlinuz...
Loading /casper/initrd.lz... ready[/FONT][/INDENT]

I can only conclude there’s something in the kernel that doesn’t like my hardware.  I’ve tried all the options from the Other Options menu.  It’s an ageing desktop machine and has no support for a power-saving CPU state.  The only vaguely relevant BIOS options are support for pre-plug and play and pre-USB operating systems, and turning off that support makes no difference.

As there’s no error message or other indication and Ubuntu can’t be started in a usable state, is there any way I can get more information on the problem?  I don’t even have enough to search the web for a possible solution.  Better yet, is this a known problem with a solution?

---

### Post by Bryan Pace on 2010-03-12
I’m still no further on.  To give you an idea, here are the times it takes to unpack the root filing system image at the start of the boot process.  In VirtualBox, it takes less than three seconds.  Running directly on the same hardware, it takes over four minutes and forty seconds.

I’ve now let a live session fully boot up from the CD and captured the results from [FONT="Courier New"]sudo lshw[/FONT].  Here’s the start of it.

```

ubuntu
    description: Mini Tower Computer
    product: DIM4500
    vendor: Dell Computer Corporation
    serial: &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=mini-tower uuid=&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;-&#9608;&#9608;&#9608;&#9608;-&#9608;&#9608;&#9608;&#9608;-&#9608;&#9608;&#9608;&#9608;-&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;
  *-core
       description: Motherboard
       product: D845EPT2
       vendor: Intel Corporation
       physical id: 0
       version: AAA83422-107
       serial: &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 1
          version: A04 (09/10/2002)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.9
          slot: X1
          size: 3066MHz
          capacity: 3066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: None
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: None
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f4000000-f7ffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:fa900000-fe9fffff memory:d2600000-f26fffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G73 [GeForce 7600 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:fd000000-fdffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:fe9e0000-fe9fffff(prefetchable)

```

I note that Linux is detecting that the CPU offers hyper-threading.  The motherboard chipset and BIOS don’t support this.  I’ve tried adding [FONT="Courier New"]noht[/FONT] to the kernel boot options, but that doesn’t help.

I’d like to think I’m reasonably technically competent, but know very little about Linux.  My perception has always been that you’d be ok with Linux, if it came pre-installed on a system.  The manufacturer will have ensured that the hardware and operating system match up.  Anything else, and you’re likely to have major headaches.  My current experience isn’t doing anything to dispel this.

Would it have been better if I’d put this thread in either Absolute Beginner Talk or Hardware & Laptops?

---

### Post by Bryan Pace on 2010-03-13
Right, here’s the start of *kern.log*.

```

Mar 13 20:43:47 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar 13 20:43:47 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 13 20:43:47 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 13 20:43:47 ubuntu kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Mar 13 20:43:47 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Mar 13 20:43:47 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff40000 (usable)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  BIOS-e820: 000000003ff40000 - 000000003ff50000 (ACPI data)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  BIOS-e820: 000000003ff50000 - 0000000040000000 (ACPI NVS)
Mar 13 20:43:47 ubuntu kernel: [    0.000000] DMI 2.3 present.
Mar 13 20:43:47 ubuntu kernel: [    0.000000] last_pfn = 0x3ff40 max_arch_pfn = 0x100000
Mar 13 20:43:47 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Mar 13 20:43:47 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   A0000-DFFFF uncachable
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   E0000-FFFFF write-back
Mar 13 20:43:47 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   1 disabled
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   2 disabled
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   3 disabled
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   4 disabled
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   5 disabled
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   6 disabled
Mar 13 20:43:47 ubuntu kernel: [    0.000000]   7 disabled
Mar 13 20:43:47 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 13 20:43:47 ubuntu kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Mar 13 20:43:47 ubuntu kernel: [    0.000000] Scanning 1 areas for low memory corruption
Mar 13 20:43:47 ubuntu kernel: [    0.000000] modified physical RAM map:
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000003ff40000 (usable)
Mar 13 20:43:47 ubuntu kernel: [    0.000000]  modified: 000000003ff40000 - 000000003ff50000 (ACPI data)
Mar 13 20:43:48 ubuntu kernel: [    0.000000]  modified: 000000003ff50000 - 0000000040000000 (ACPI NVS)
Mar 13 20:43:48 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Mar 13 20:43:48 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Mar 13 20:43:48 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Mar 13 20:43:48 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Mar 13 20:43:48 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Mar 13 20:43:48 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Mar 13 20:43:48 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Mar 13 20:43:48 ubuntu kernel: [    0.000000] RAMDISK: 3f992000 - 3ff0f098
Mar 13 20:43:48 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
Mar 13 20:43:48 ubuntu kernel: [    0.000000] Move RAMDISK from 000000003f992000 - 000000003ff0f097 to 008ad000 - 00e2a097
Mar 13 20:43:48 ubuntu kernel: [    0.000000] ACPI: RSDP 000f6cc0 00014 (v00 ACPIAM)
Mar 13 20:43:48 ubuntu kernel: [    0.000000] ACPI: RSDT 3ff40000 0002C (v01 A M I  OEMRSDT  09000210 MSFT 00000097)
Mar 13 20:43:48 ubuntu kernel: [    0.000000] ACPI: FACP 3ff40200 00081 (v02 A M I  OEMFACP  09000210 MSFT 00000097)
Mar 13 20:43:48 ubuntu kernel: [    0.000000] ACPI: DSDT 3ff40400 039D5 (v01   DELL DIM 4500 0000010A MSFT 0100000D)
Mar 13 20:43:48 ubuntu kernel: [    0.000000] ACPI: FACS 3ff50000 00040
Mar 13 20:43:48 ubuntu kernel: [    0.000000] ACPI: APIC 3ff40300 00054 (v01 A M I  OEMAPIC  09000210 MSFT 00000097)
Mar 13 20:43:48 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 13 20:43:48 ubuntu kernel: [    0.000000] 135MB HIGHMEM available.
Mar 13 20:43:48 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Mar 13 20:43:48 ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   #5 [00008a9000 - 00008ac200]              BRK ==> [00008a9000 - 00008ac200]
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Mar 13 20:43:48 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003ff40
Mar 13 20:43:48 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 13 20:43:48 ubuntu kernel: [    0.000000] early_node_map[3] active PFN ranges
Mar 13 20:43:48 ubuntu kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Mar 13 20:43:48 ubuntu kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Mar 13 20:43:48 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0003ff40
Mar 13 20:43:48 ubuntu kernel: [    0.000000] On node 0 totalpages: 261851
Mar 13 20:43:48 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   HighMem zone: 271 pages used for memmap
Mar 13 20:43:48 ubuntu kernel: [    0.000000]   HighMem zone: 34355 pages, LIFO batch:7
Mar 13 20:43:48 ubuntu kernel: [    0.000000] Using APIC driver default
Mar 13 20:43:48 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 13 20:43:49 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 13 20:43:49 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Mar 13 20:43:49 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Mar 13 20:43:49 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 13 20:43:49 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 13 20:43:49 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 13 20:43:49 ubuntu kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Mar 13 20:43:49 ubuntu kernel: [    0.000000] nr_irqs_gsi: 24
Mar 13 20:43:49 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Mar 13 20:43:49 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 13 20:43:49 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Mar 13 20:43:49 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:c0000000)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Mar 13 20:43:49 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages at c1805000, static data 35612 bytes
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259804
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz --
Mar 13 20:43:49 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 13 20:43:49 ubuntu kernel: [    0.000000] allocated 5239040 bytes of page_cgroup
Mar 13 20:43:49 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003ff40)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Memory: 1019400k/1047808k available (4565k kernel code, 27692k reserved, 2143k data, 540k init, 138504k highmem)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Mar 13 20:43:49 ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Mar 13 20:43:49 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 13 20:43:49 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Mar 13 20:43:49 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Mar 13 20:43:49 ubuntu kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Mar 13 20:43:49 ubuntu kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Mar 13 20:43:49 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 13 20:43:49 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Mar 13 20:43:49 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Mar 13 20:43:49 ubuntu kernel: [    0.000000] Detected 3056.273 MHz processor.
Mar 13 20:43:49 ubuntu kernel: [    0.002705] Console: colour VGA+ 80x25
Mar 13 20:43:49 ubuntu kernel: [    0.002925] console [tty0] enabled
Mar 13 20:43:49 ubuntu kernel: [    0.004129] Calibrating delay loop (skipped), value calculated using timer frequency.. 6112.54 BogoMIPS (lpj=12225092)
Mar 13 20:43:49 ubuntu kernel: [    0.005850] Security Framework initialized
Mar 13 20:43:49 ubuntu kernel: [    0.007686] AppArmor: AppArmor initialized
Mar 13 20:43:49 ubuntu kernel: [    0.008350] Mount-cache hash table entries: 512
Mar 13 20:43:49 ubuntu kernel: [    0.014557] Initializing cgroup subsys ns
Mar 13 20:43:49 ubuntu kernel: [    0.015096] Initializing cgroup subsys cpuacct
Mar 13 20:43:49 ubuntu kernel: [    0.015836] Initializing cgroup subsys memory
Mar 13 20:43:49 ubuntu kernel: [    0.016414] Initializing cgroup subsys freezer
Mar 13 20:43:49 ubuntu kernel: [    0.016970] Initializing cgroup subsys net_cls
Mar 13 20:43:49 ubuntu kernel: [    0.018463] CPU: Trace cache: 12K uops, L1 D cache: 8K
Mar 13 20:43:49 ubuntu kernel: [    0.019219] CPU: L2 cache: 512K
Mar 13 20:43:49 ubuntu kernel: [    0.020128] CPU: Unsupported number of siblings 2
Mar 13 20:43:49 ubuntu kernel: [    0.020697] mce: CPU supports 4 MCE banks
Mar 13 20:43:49 ubuntu kernel: [    0.021429] CPU0: Thermal monitoring enabled (TM1)
Mar 13 20:43:49 ubuntu kernel: [    0.022209] Performance Counters: no PMU driver, software counters only.
Mar 13 20:43:49 ubuntu kernel: [    0.023084] Checking 'hlt' instruction... OK.
Mar 13 20:43:49 ubuntu kernel: [    0.040107] SMP alternatives: switching to UP code
Mar 13 20:43:49 ubuntu kernel: [    0.192277] Freeing SMP alternatives: 19k freed
Mar 13 20:43:49 ubuntu kernel: [    0.193103] ACPI: Core revision 20090521
Mar 13 20:43:49 ubuntu kernel: [    0.351860] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 13 20:43:50 ubuntu kernel: [    0.392432] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
Mar 13 20:43:50 ubuntu kernel: [    0.396960] Brought up 1 CPUs
Mar 13 20:43:50 ubuntu kernel: [    0.397423] Total of 1 processors activated (6112.54 BogoMIPS).
Mar 13 20:43:50 ubuntu kernel: [    0.398807] CPU0 attaching NULL sched-domain.
Mar 13 20:43:50 ubuntu kernel: [    0.412434] Booting paravirtualized kernel on bare hardware
Mar 13 20:43:50 ubuntu kernel: [    0.428821] regulator: core version 0.5
Mar 13 20:43:50 ubuntu kernel: [    0.429657] Time: 20:33:28  Date: 03/13/10
Mar 13 20:43:50 ubuntu kernel: [    0.432790] NET: Registered protocol family 16
Mar 13 20:43:50 ubuntu kernel: [    0.441113] EISA bus registered
Mar 13 20:43:50 ubuntu kernel: [    0.441795] ACPI: bus type pci registered
Mar 13 20:43:50 ubuntu kernel: [    0.449412] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
Mar 13 20:43:50 ubuntu kernel: [    0.450076] PCI: Using configuration type 1 for base access
Mar 13 20:43:50 ubuntu kernel: [    0.533353] bio: create slab <bio-0> at 0
Mar 13 20:43:50 ubuntu kernel: [    0.576984] ACPI: EC: Look up EC in DSDT
Mar 13 20:43:50 ubuntu kernel: [    0.964301] ACPI: Interpreter enabled
Mar 13 20:43:50 ubuntu kernel: [    0.964906] ACPI: (supports S0 S1 S3 S4 S5)
Mar 13 20:43:50 ubuntu kernel: [    0.967566] ACPI: Using IOAPIC for interrupt routing
Mar 13 20:43:50 ubuntu kernel: [    1.334234] ACPI: Power Resource [URP1] (off)
Mar 13 20:43:50 ubuntu kernel: [    1.337184] ACPI: Power Resource [FDDP] (off)
Mar 13 20:43:50 ubuntu kernel: [    1.339980] ACPI: Power Resource [LPTP] (off)
Mar 13 20:43:50 ubuntu kernel: [    1.349449] ACPI: No dock devices found.
Mar 13 20:43:50 ubuntu kernel: [    1.356219] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 13 20:43:50 ubuntu kernel: [    1.358521] pci 0000:00:00.0: reg 10 32bit mmio: [0xf4000000-0xf7ffffff]
Mar 13 20:43:50 ubuntu kernel: [    1.361613] pci 0000:00:1d.0: reg 20 io port: [0xe800-0xe81f]
Mar 13 20:43:50 ubuntu kernel: [    1.362826] pci 0000:00:1d.1: reg 20 io port: [0xe880-0xe89f]
Mar 13 20:43:50 ubuntu kernel: [    1.364169] pci 0000:00:1d.2: reg 20 io port: [0xec00-0xec1f]
Mar 13 20:43:50 ubuntu kernel: [    1.365467] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfebffc00-0xfebfffff]
Mar 13 20:43:50 ubuntu kernel: [    1.366515] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Mar 13 20:43:50 ubuntu kernel: [    1.367215] pci 0000:00:1d.7: PME# disabled
Mar 13 20:43:50 ubuntu kernel: [    1.368888] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Mar 13 20:43:50 ubuntu kernel: [    1.369081] * this clock source is slow. If you are sure your timer does not have
Mar 13 20:43:50 ubuntu kernel: [    1.369291] * this bug, please use "acpi_pm_good" to disable the workaround
Mar 13 20:43:50 ubuntu kernel: [    1.371663] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Mar 13 20:43:50 ubuntu kernel: [    1.372181] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
Mar 13 20:43:50 ubuntu kernel: [    1.373395] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
Mar 13 20:43:50 ubuntu kernel: [    1.373758] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
Mar 13 20:43:50 ubuntu kernel: [    1.374118] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
Mar 13 20:43:50 ubuntu kernel: [    1.374481] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
Mar 13 20:43:50 ubuntu kernel: [    1.374848] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
Mar 13 20:43:50 ubuntu kernel: [    1.375224] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
Mar 13 20:43:50 ubuntu kernel: [    1.377022] pci 0000:00:1f.3: reg 20 io port: [0xe000-0xe01f]
Mar 13 20:43:50 ubuntu kernel: [    1.378148] pci 0000:00:1f.5: reg 10 io port: [0xe400-0xe4ff]
Mar 13 20:43:50 ubuntu kernel: [    1.378523] pci 0000:00:1f.5: reg 14 io port: [0xe080-0xe0bf]
Mar 13 20:43:50 ubuntu kernel: [    1.378905] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfebff800-0xfebff9ff]
Mar 13 20:43:50 ubuntu kernel: [    1.379313] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfebff400-0xfebff4ff]
Mar 13 20:43:50 ubuntu kernel: [    1.380215] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Mar 13 20:43:50 ubuntu kernel: [    1.380911] pci 0000:00:1f.5: PME# disabled
Mar 13 20:43:50 ubuntu kernel: [    1.382362] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
Mar 13 20:43:50 ubuntu kernel: [    1.382772] pci 0000:01:00.0: reg 14 32bit mmio: [0xe0000000-0xefffffff]
Mar 13 20:43:50 ubuntu kernel: [    1.383180] pci 0000:01:00.0: reg 18 32bit mmio: [0xfc000000-0xfcffffff]
Mar 13 20:43:50 ubuntu kernel: [    1.383778] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe9e0000-0xfe9fffff]
Mar 13 20:43:50 ubuntu kernel: [    1.385327] pci 0000:00:01.0: bridge 32bit mmio: [0xfa900000-0xfe9fffff]
Mar 13 20:43:50 ubuntu kernel: [    1.385689] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd2600000-0xf26fffff]
Mar 13 20:43:50 ubuntu kernel: [    1.386746] pci 0000:02:01.0: reg 10 io port: [0xd800-0xd8ff]
Mar 13 20:43:50 ubuntu kernel: [    1.387133] pci 0000:02:01.0: reg 14 32bit mmio: [0xfeaffc00-0xfeaffcff]
Mar 13 20:43:50 ubuntu kernel: [    1.387793] pci 0000:02:01.0: reg 30 32bit mmio: [0xfeac0000-0xfeadffff]
Mar 13 20:43:50 ubuntu kernel: [    1.388394] pci 0000:02:01.0: supports D1 D2
Mar 13 20:43:50 ubuntu kernel: [    1.388637] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
Mar 13 20:43:51 ubuntu kernel: [    1.389349] pci 0000:02:01.0: PME# disabled
Mar 13 20:43:51 ubuntu kernel: [    1.390598] pci 0000:00:1e.0: transparent bridge
Mar 13 20:43:51 ubuntu kernel: [    1.391234] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
Mar 13 20:43:51 ubuntu kernel: [    1.391561] pci 0000:00:1e.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
Mar 13 20:43:51 ubuntu kernel: [    1.392200] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xf2700000-0xf27fffff]
Mar 13 20:43:51 ubuntu kernel: [    1.392692] pci_bus 0000:00: on NUMA node 0
Mar 13 20:43:51 ubuntu kernel: [    1.392994] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 13 20:43:51 ubuntu kernel: [    1.398417] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Mar 13 20:43:51 ubuntu kernel: [    1.524859] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Mar 13 20:43:51 ubuntu kernel: [    1.536797] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11 12 14 15)
Mar 13 20:43:51 ubuntu kernel: [    1.548746] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Mar 13 20:43:51 ubuntu kernel: [    1.560678] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Mar 13 20:43:51 ubuntu kernel: [    1.572603] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Mar 13 20:43:51 ubuntu kernel: [    1.585029] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Mar 13 20:43:51 ubuntu kernel: [    1.597462] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Mar 13 20:43:51 ubuntu kernel: [    1.609568] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Mar 13 20:43:51 ubuntu kernel: [    1.624810] SCSI subsystem initialized
Mar 13 20:43:51 ubuntu kernel: [    1.629036] libata version 3.00 loaded.
Mar 13 20:43:51 ubuntu kernel: [    1.633769] usbcore: registered new interface driver usbfs
Mar 13 20:43:51 ubuntu kernel: [    1.635385] usbcore: registered new interface driver hub
Mar 13 20:43:51 ubuntu kernel: [    1.637766] usbcore: registered new device driver usb
Mar 13 20:43:51 ubuntu kernel: [    1.647154] ACPI: WMI: Mapper loaded
Mar 13 20:43:51 ubuntu kernel: [    1.647613] PCI: Using ACPI for IRQ routing
Mar 13 20:43:51 ubuntu kernel: [    1.655744] Bluetooth: Core ver 2.15
Mar 13 20:43:51 ubuntu kernel: [    1.657626] NET: Registered protocol family 31
Mar 13 20:43:51 ubuntu kernel: [    1.658140] Bluetooth: HCI device and connection manager initialized
Mar 13 20:43:51 ubuntu kernel: [    1.658799] Bluetooth: HCI socket layer initialized
Mar 13 20:43:51 ubuntu kernel: [    1.659343] NetLabel: Initializing
Mar 13 20:43:51 ubuntu kernel: [    1.660104] NetLabel:  domain hash size = 128
Mar 13 20:43:51 ubuntu kernel: [    1.660613] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 13 20:43:51 ubuntu kernel: [    1.661965] NetLabel:  unlabeled traffic allowed by default
Mar 13 20:43:51 ubuntu kernel: [    1.763897] pnp: PnP ACPI init
Mar 13 20:43:51 ubuntu kernel: [    1.764743] ACPI: bus type pnp registered
Mar 13 20:43:51 ubuntu kernel: [    1.992328] pnp: PnP ACPI: found 13 devices
Mar 13 20:43:51 ubuntu kernel: [    1.992840] ACPI: ACPI bus type pnp unregistered
Mar 13 20:43:51 ubuntu kernel: [    1.993409] PnPBIOS: Disabled by ACPI PNP
Mar 13 20:43:51 ubuntu kernel: [    1.994434] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Mar 13 20:43:51 ubuntu kernel: [    1.995402] system 00:0b: ioport range 0x400-0x47f has been reserved
Mar 13 20:43:51 ubuntu kernel: [    1.996285] system 00:0b: ioport range 0x680-0x6ff has been reserved
Mar 13 20:43:51 ubuntu kernel: [    1.997042] system 00:0b: ioport range 0x480-0x4bf has been reserved
Mar 13 20:43:51 ubuntu kernel: [    1.997838] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 13 20:43:51 ubuntu kernel: [    1.998714] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Mar 13 20:43:51 ubuntu kernel: [    1.999706] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Mar 13 20:43:51 ubuntu kernel: [    2.000607] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved
Mar 13 20:43:51 ubuntu kernel: [    2.001415] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Mar 13 20:43:51 ubuntu kernel: [    2.002222] system 00:0c: iomem range 0x100000-0x3fffffff could not be reserved
Mar 13 20:43:51 ubuntu kernel: [    2.048372] AppArmor: AppArmor Filesystem Enabled
Mar 13 20:43:51 ubuntu kernel: [    2.049632] pci 0000:02:01.0: BAR 6: address space collision on of device [0xfeac0000-0xfeadffff]
Mar 13 20:43:51 ubuntu kernel: [    2.050856] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Mar 13 20:43:52 ubuntu kernel: [    2.051501] pci 0000:00:01.0:   IO window: disabled
Mar 13 20:43:52 ubuntu kernel: [    2.052291] pci 0000:00:01.0:   MEM window: 0xfa900000-0xfe9fffff
Mar 13 20:43:52 ubuntu kernel: [    2.053015] pci 0000:00:01.0:   PREFETCH window: 0xd2600000-0xf26fffff
Mar 13 20:43:52 ubuntu kernel: [    2.053800] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Mar 13 20:43:52 ubuntu kernel: [    2.054489] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
Mar 13 20:43:52 ubuntu kernel: [    2.055182] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff
Mar 13 20:43:52 ubuntu kernel: [    2.055918] pci 0000:00:1e.0:   PREFETCH window: 0xf2700000-0xf27fffff
Mar 13 20:43:52 ubuntu kernel: [    2.056941] pci 0000:00:1e.0: setting latency timer to 64
Mar 13 20:43:52 ubuntu kernel: [    2.057248] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Mar 13 20:43:52 ubuntu kernel: [    2.057555] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Mar 13 20:43:52 ubuntu kernel: [    2.057887] pci_bus 0000:01: resource 1 mem: [0xfa900000-0xfe9fffff]
Mar 13 20:43:52 ubuntu kernel: [    2.058224] pci_bus 0000:01: resource 2 pref mem [0xd2600000-0xf26fffff]
Mar 13 20:43:52 ubuntu kernel: [    2.058560] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
Mar 13 20:43:52 ubuntu kernel: [    2.058876] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
Mar 13 20:43:52 ubuntu kernel: [    2.059207] pci_bus 0000:02: resource 2 pref mem [0xf2700000-0xf27fffff]
Mar 13 20:43:52 ubuntu kernel: [    2.059540] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
Mar 13 20:43:52 ubuntu kernel: [    2.059849] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
Mar 13 20:43:52 ubuntu kernel: [    2.062025] NET: Registered protocol family 2
Mar 13 20:43:52 ubuntu kernel: [    2.069097] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 13 20:43:52 ubuntu kernel: [    2.091606] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 13 20:43:52 ubuntu kernel: [    2.170839] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 13 20:43:52 ubuntu kernel: [    2.221847] TCP: Hash tables configured (established 131072 bind 65536)
Mar 13 20:43:52 ubuntu kernel: [    2.222520] TCP reno registered
Mar 13 20:43:52 ubuntu kernel: [    2.227760] NET: Registered protocol family 1
Mar 13 20:43:52 ubuntu kernel: [    2.231094] Trying to unpack rootfs image as initramfs...
Mar 13 20:43:52 ubuntu kernel: [    2.548306] Switched to high resolution mode on CPU 0
Mar 13 20:43:52 ubuntu kernel: [  286.106078] Freeing initrd memory: 5620k freed

```

Having thought about it some more, the performance feels as if part of the CPU cache is disabled.

---

