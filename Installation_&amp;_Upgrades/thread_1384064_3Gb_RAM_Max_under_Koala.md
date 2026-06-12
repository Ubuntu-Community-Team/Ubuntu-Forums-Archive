---
title: "3Gb RAM Max under Koala"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by sambo1972 on 2010-01-18
Hi All,

Newbie here and really need help. Upgraded my laptop from 2Gb to 4Gb RAM and ubuntu doesn't detect it. I've read all the posts on this issue and I have:

1) installed a PAE kernel and made it the boot option. Output from uname -a is:

Linux tensor 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux

2) removed all the non PAE kernels (a post I found mentioned this if the PAE kernel doesn't sort it out after a reboot)

3) tried to install the linux server image & headers but this didn't work. I later found articles discussing how you couldn't do this under Koala anyway.

Facts:

1) Fresh install of Koala on a Toshiba P100 Satellite A6A PSP028017
2) 4Gb is detected in the BIOS
3) 32 bit installation - can't go to 64 bit due to development tool requirements
3) looking through the output of dmesg (all 0.000000 entries listed below) I can see that HIGHMEM is 2180Mb  and LOWMEM is 889Mb

So what can I do? If something in my hardware configuration is preventing this I don't know how to track it down.

Thanks all,

Sam

-----------------------------------------------------------------------
dmesg extract :

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic-pae (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 (Ubuntu 2.6.31-17.54-generic-pae)
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
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfe90000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe90000 - 00000000bfe9c000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfe9c000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfe90 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BFF00000 mask FFFF00000 uncachable
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
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 00000000000e4000 (reserved)
[    0.000000]  modified: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfe90000 (usable)
[    0.000000]  modified: 00000000bfe90000 - 00000000bfe9c000 (ACPI data)
[    0.000000]  modified: 00000000bfe9c000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  modified: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000
[    0.000000] RAMDISK: 3789e000 - 37fefd96
[    0.000000] Allocated new RAMDISK: 008b5000 - 01006d96
[    0.000000] Move RAMDISK from 000000003789e000 - 0000000037fefd95 to 008b5000 - 01006d95
[    0.000000] ACPI: RSDP 000f75d0 00024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT bfe91fb4 00074 (v01 TOSQCI TOSQCI00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfe9bc2a 000F4 (v03 TOSQCI TOSQCI00 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfe9305c 08B5A (v01 TOSQCI   Denver 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS bfe9cfc0 00040
[    0.000000] ACPI: APIC bfe9bd1e 00068 (v01 TOSQCI TOSQCI00 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET bfe9bd86 00038 (v01 TOSQCI TOSQCI00 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfe9bdbe 0003C (v01 TOSQCI TOSQCI00 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bfe9bdfa 00068 (v01 PTLTD       APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfe9be62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfe9be8a 00176 (v01 TOSQCI TOSQCI00 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT bfe925b4 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT bfe9250e 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT bfe92028 004E6 (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2180MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00009000 - 0000ff40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad9a0]    TEXT DATA BSS ==> [0000100000 - 00008ad9a0]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b413c]              BRK ==> [00008ae000 - 00008b413c]
[    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #7 [00008b5000 - 0001006d96]      NEW RAMDISK ==> [00008b5000 - 0001006d96]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00f7690] f7690
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x000bfe90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfe90
[    0.000000] On node 0 totalpages: 785963
[    0.000000] free_area_init_node: node 0, pgdat c078bd40, node_mem_map c1007000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4362 pages used for memmap
[    0.000000]   HighMem zone: 553864 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2817000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779821
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic-pae root=UUID=27882a03-417f-4cf7-82d1-afe06a108de9 ro splash quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15721280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:000bfe90)
[    0.000000] Memory: 3086716k/3144256k available (4590k kernel code, 56320k reserved, 2147k data, 544k init, 2232904k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc0795000 - 0xc081d000   ( 544 kB)
[    0.000000]       .data : 0xc057b894 - 0xc07947e8   (2147 kB)
[    0.000000]       .text : 0xc0100000 - 0xc057b894   (4590 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2006.263 MHz processor.
```

---

### Post by Ji Ruo on 2010-01-27
Most of your post is over my head to be honest... but how much ram is showing up with ```
sudo lshw
```Check to see if it's 4GB.

Because you are using 32bit Linux there should be 3GB available for applications, and 1GB reserved for the kernel. That's the first thing I thought when I saw your thread title.

---

### Post by sambo1972 on 2010-01-27
Thanks for replying mate.

The output of lshw shows 4Gb like you said. I am running 32 bit ubuntu so maybe what you've said about the kernel using 1Gb is the cause here.

Any idea how to verify what the kernel's RAM reservation is?

Thanks

Sam

---

### Post by presence1960 on 2010-01-28
why not install 64 bit Ubuntu? it will run better than a PAE enabled kernel anyway. It will also recognize your RAM.

---

### Post by Ji Ruo on 2010-01-28
Unfortunately I have no idea. It shouldn't be too hard to find out though - just do some searching. Try googling or even use [www.google.com/linux](www.google.com/linux)

Searching the forums might help as well.

HTH

---

### Post by sambo1972 on 2010-01-28
Thanks all.

@prescence1960 - that's probably the only solution in the long term but right now this is a working machine and I don't know how my dev tools are going to handle 64 bit.

What a hassle!

---

### Post by presence1960 on 2010-01-28
> **sambo1972 said:**
> Thanks all.

@prescence1960 - that's probably the only solution in the long term but right now this is a working machine and I don't know how my dev tools are going to handle 64 bit.

What a hassle!

I hear you. I threw that out there because if you go to PAE you will experience performance loss. I just don't think that is worth it to recognize all 4 GB of RAM. Unless you are doing multiple resource intensive tasks simultaneously 3 GB of RAM is plenty.

---

### Post by sanderj on 2010-02-08
If this is still an issue, you can run the attached python script to report about your system.


> sudo python check-my-hardware.py

---

