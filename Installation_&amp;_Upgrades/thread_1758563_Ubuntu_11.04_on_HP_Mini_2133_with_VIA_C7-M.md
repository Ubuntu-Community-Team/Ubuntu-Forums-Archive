---
title: "Ubuntu 11.04 on HP Mini 2133 with VIA C7-M"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by sbrbot on 2011-05-14
I cannot install a brand new or upgrade to Natty Narwhal (11.04) Ubuntu or Xubuntu on my HP Mini 2133 netbook with VIA C7-M CPU and VIA chipset. Every time when I try to install it or upgrade from 10.10 it freezes somewhere during installation/upgrade process. With earlier versions of Ubuntu (9.10, 10.04, 10.10) this machine works very well.

---

### Post by Hedgehog1 on 2011-05-14
We might be able to help with a little more data about your system.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by jimnovy on 2011-05-16
I managed to get 11.04 installed on my 2133 and it freezes whenever I connect to a wireless access point.  Are you trying to install using a wireless connection?

---

### Post by sbrbot on 2011-05-16
> **jimnovy said:**
> I managed to get 11.04 installed on my 2133 and it freezes whenever I connect to a wireless access point.  Are you trying to install using a wireless connection?
Right. I think that I also managed to install it once and it froze after trying to use wireless connection!

---

### Post by jeevak on 2011-05-17
> **sbrbot said:**
> Right. I think that I also managed to install it once and it froze after trying to use wireless connection!

hey!

i seem to have the same problem. it freezes when it tries to connect to the net via the wireless!!!! i have to turn it off in order to use the "netbook"!!! kinda defeats the purpose of a netbook now doesnt it!! 
solution? 
problem with the drivers maybe?
anyone from ubuntu got a solution??

---

### Post by sbrbot on 2011-05-17
> **Hedgehog1 said:**
> We might be able to help with a little more data about your system.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Here is the RESULTS.txt fili with results of mentioned script.

---

### Post by sbrbot on 2011-05-17
Here is the output of lspci command:

```
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
07:03.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
```

---

### Post by sbrbot on 2011-05-17
Here is output of dmesg command:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-29-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #51-Ubuntu SMP Fri Apr 15 17:13:54 UTC 2011 (Ubuntu 2.6.35-29.51-generic 2.6.35.12)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037eb0000 (usable)
[    0.000000]  BIOS-e820: 0000000037eb0000 - 0000000037ebe000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037ebe000 - 0000000037ef0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037f00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x37eb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 038000000 mask FF8000000 uncachable
[    0.000000]   1 base 000000000 mask FC0000000 write-back
[    0.000000]   2 base 037F00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000037eb0000 (usable)
[    0.000000]  modified: 0000000037eb0000 - 0000000037ebe000 (ACPI data)
[    0.000000]  modified: 0000000037ebe000 - 0000000037ef0000 (ACPI NVS)
[    0.000000]  modified: 0000000037ef0000 - 0000000037f00000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 29500000 - 29f44000
[    0.000000] ACPI: RSDP 000f9ef0 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 37eb0100 00064 (v01 HPQOEM SLIC-MPC 20080820 MSFT 00000097)
[    0.000000] ACPI: FACP 37eb0290 000F4 (v04 HP     FACP2203 20080820 MSFT 00000097)
[    0.000000] ACPI: DSDT 37eb0600 0909C (v02  68VGU 68VGUF05 00000F05 INTL 20061109)
[    0.000000] ACPI: FACS 37ebe000 00040
[    0.000000] ACPI: APIC 37eb0390 00060 (v02 HP     APIC2203 20080820 MSFT 00000097)
[    0.000000] ACPI: MCFG 37eb03f0 0003C (v01 HP     OEMMCFG  20080820 MSFT 00000097)
[    0.000000] ACPI: SLIC 37eb0430 00176 (v01 HPQOEM SLIC-MPC 20080820 MSFT 00000097)
[    0.000000] ACPI: WDRT 37eb05b0 00047 (v01 HP     VT-8237S 20080820 MSFT 00000097)
[    0.000000] ACPI: OEMB 37ebe040 000F0 (v01 HP     OEMB2203 20080820 MSFT 00000097)
[    0.000000] ACPI: HPET 37eb96a0 00038 (v01 HP     VT-8237S 20080820 MSFT 00000097)
[    0.000000] ACPI: SSDT 37ebe130 002AE (v01    HP    P001PM 00000001 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00037eb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00037eb0
[    0.000000] On node 0 totalpages: 228928
[    0.000000] free_area_init_node: node 0, pgdat c0802000, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 14 pages used for memmap
[    0.000000]   HighMem zone: 1700 pages, LIFO batch:0
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfed00000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 37f00000 (gap: 37f00000:c6d00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227138
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-29-generic root=UUID=11007a0c-c08b-4840-8d7e-0a1cc61a288b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4580780 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (50 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a4adc]   TEXT DATA BSS
[    0.000000]   #3 [0029500000 - 0029f44000]         RAMDISK
[    0.000000]   #4 [00009a5000 - 00009a8144]             BRK
[    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #7 [000009fc00 - 00000fd110]   BIOS reserved
[    0.000000]   #8 [00000fd268 - 00000ff780]   BIOS reserved
[    0.000000]   #9 [00000fd110 - 00000fd268]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001701000]         BOOTMEM
[    0.000000]   #15 [0001701000 - 0001701004]         BOOTMEM
[    0.000000]   #16 [0001701040 - 0001701100]         BOOTMEM
[    0.000000]   #17 [0001701100 - 0001701154]         BOOTMEM
[    0.000000]   #18 [0001701180 - 0001704180]         BOOTMEM
[    0.000000]   #19 [0001704180 - 0001704184]         BOOTMEM
[    0.000000]   #20 [00017041c0 - 0001704220]         BOOTMEM
[    0.000000]   #21 [0001704240 - 0001704265]         BOOTMEM
[    0.000000]   #22 [0001704280 - 00017042ce]         BOOTMEM
[    0.000000]   #23 [0001704300 - 0001704488]         BOOTMEM
[    0.000000]   #24 [00017044c0 - 0001704500]         BOOTMEM
[    0.000000]   #25 [0001704500 - 0001704540]         BOOTMEM
[    0.000000]   #26 [0001704540 - 0001704580]         BOOTMEM
[    0.000000]   #27 [0001704580 - 00017045c0]         BOOTMEM
[    0.000000]   #28 [00017045c0 - 0001704600]         BOOTMEM
[    0.000000]   #29 [0001704600 - 0001704640]         BOOTMEM
[    0.000000]   #30 [0001704640 - 0001704680]         BOOTMEM
[    0.000000]   #31 [0001704680 - 00017046c0]         BOOTMEM
[    0.000000]   #32 [00017046c0 - 0001704700]         BOOTMEM
[    0.000000]   #33 [0001704700 - 0001704740]         BOOTMEM
[    0.000000]   #34 [0001704740 - 0001704780]         BOOTMEM
[    0.000000]   #35 [0001704780 - 0001704790]         BOOTMEM
[    0.000000]   #36 [00017047c0 - 00017047d0]         BOOTMEM
[    0.000000]   #37 [0001704800 - 000170486a]         BOOTMEM
[    0.000000]   #38 [0001704880 - 00017048ea]         BOOTMEM
[    0.000000]   #39 [0001800000 - 000180e000]         BOOTMEM
[    0.000000]   #40 [0001706900 - 0001706904]         BOOTMEM
[    0.000000]   #41 [0001706940 - 0001706944]         BOOTMEM
[    0.000000]   #42 [0001706980 - 0001706984]         BOOTMEM
[    0.000000]   #43 [00017069c0 - 00017069c4]         BOOTMEM
[    0.000000]   #44 [0001706a00 - 0001706ab0]         BOOTMEM
[    0.000000]   #45 [0001706ac0 - 0001706b68]         BOOTMEM
[    0.000000]   #46 [0001706b80 - 000170ab80]         BOOTMEM
[    0.000000]   #47 [000170ab80 - 000178ab80]         BOOTMEM
[    0.000000]   #48 [000178ab80 - 00017cab80]         BOOTMEM
[    0.000000]   #49 [000180e000 - 0001c6c5ac]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:00037eb0)
[    0.000000] Memory: 883796k/916160k available (4940k kernel code, 31916k reserved, 2333k data, 688k init, 6856k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc081b000 - 0xc08c7000   ( 688 kB)
[    0.000000]       .data : 0xc05d32de - 0xc081a7e8   (2333 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d32de   (4940 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1197.025 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 2394.05 BogoMIPS (lpj=4788100)
[    0.004025] pid_max: default: 32768 minimum: 301
[    0.004081] Security Framework initialized
[    0.004130] AppArmor: AppArmor initialized
[    0.004136] Yama: becoming mindful.
[    0.004297] Mount-cache hash table entries: 512
[    0.004583] Initializing cgroup subsys ns
[    0.004595] Initializing cgroup subsys cpuacct
[    0.004609] Initializing cgroup subsys memory
[    0.004632] Initializing cgroup subsys devices
[    0.004641] Initializing cgroup subsys freezer
[    0.004649] Initializing cgroup subsys net_cls
[    0.004717] Performance Events: 
[    0.006642] SMP alternatives: switching to UP code
[    0.032737] Freeing SMP alternatives: 24k freed
[    0.032783] ACPI: Core revision 20100428
[    0.056017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.056034] ftrace: allocating 21774 entries in 43 pages
[    0.060142] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.060690] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.103062] CPU0: Centaur VIA C7-M Processor 1200MHz stepping 00
[    0.104000] APIC calibration not consistent with PM-Timer: 115ms instead of 100ms
[    0.104000] APIC delta adjusted to PM-Timer: 1246872 (1446363)
[    0.104361] Brought up 1 CPUs
[    0.104371] Total of 1 processors activated (2394.05 BogoMIPS).
[    0.104713] devtmpfs: initialized
[    0.108298] regulator: core version 0.5
[    0.108362] Time: 21:33:00  Date: 05/17/11
[    0.108471] NET: Registered protocol family 16
[    0.108785] EISA bus registered
[    0.108805] ACPI: bus type pci registered
[    0.108991] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.109003] PCI: not using MMCONFIG
[    0.109347] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=7
[    0.109355] PCI: Using configuration type 1 for base access
[    0.112236] bio: create slab <bio-0> at 0
[    0.116098] ACPI: EC: Look up EC in DSDT
[    0.120043] ACPI: Executed 1 blocks of module-level executable AML code
[    0.149757] ACPI: Interpreter enabled
[    0.149772] ACPI: (supports S0 S3 S4 S5)
[    0.149834] ACPI: Using IOAPIC for interrupt routing
[    0.149980] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.153338] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.153346] PCI: Using MMCONFIG for extended config space
[    0.172759] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.172938] ACPI: Power Resource [APMF] (off)
[    0.173684] ACPI: No dock devices found.
[    0.173696] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.174133] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7f])
[    0.174996] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.175006] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.175016] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.175026] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.175037] pci_root PNP0A03:00: host bridge window [mem 0x37f00000-0xdfffffff]
[    0.175047] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfeafffff]
[    0.175103] pci 0000:00:00.0: reg 10: [mem 0xf0000000-0xf7ffffff pref]
[    0.175907] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.175918] pci 0000:00:02.0: PME# disabled
[    0.176069] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.176080] pci 0000:00:03.0: PME# disabled
[    0.176181] pci 0000:00:0f.0: reg 10: [io  0xcc00-0xcc07]
[    0.176196] pci 0000:00:0f.0: reg 14: [io  0xc880-0xc883]
[    0.176211] pci 0000:00:0f.0: reg 18: [io  0xc800-0xc807]
[    0.176226] pci 0000:00:0f.0: reg 1c: [io  0xc480-0xc483]
[    0.176241] pci 0000:00:0f.0: reg 20: [io  0xc400-0xc40f]
[    0.176256] pci 0000:00:0f.0: reg 24: [io  0xc000-0xc0ff]
[    0.176365] pci 0000:00:10.0: reg 20: [io  0xb800-0xb81f]
[    0.176408] pci 0000:00:10.0: supports D1 D2
[    0.176416] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176427] pci 0000:00:10.0: PME# disabled
[    0.176502] pci 0000:00:10.2: reg 20: [io  0xb880-0xb89f]
[    0.176544] pci 0000:00:10.2: supports D1 D2
[    0.176552] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176563] pci 0000:00:10.2: PME# disabled
[    0.176636] pci 0000:00:10.3: reg 20: [io  0xbc00-0xbc1f]
[    0.176679] pci 0000:00:10.3: supports D1 D2
[    0.176687] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176697] pci 0000:00:10.3: PME# disabled
[    0.176752] pci 0000:00:10.4: reg 10: [mem 0xfbeffc00-0xfbeffcff]
[    0.176825] pci 0000:00:10.4: supports D1 D2
[    0.176833] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176844] pci 0000:00:10.4: PME# disabled
[    0.177358] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xd7ffffff pref]
[    0.177372] pci 0000:01:00.0: reg 14: [mem 0xfc000000-0xfcffffff]
[    0.177407] pci 0000:01:00.0: reg 30: [mem 0xfbff0000-0xfbffffff pref]
[    0.177439] pci 0000:01:00.0: supports D1 D2
[    0.177499] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.177510] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.177523] pci 0000:00:01.0:   bridge window [mem 0xfbf00000-0xfcffffff]
[    0.177536] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd7ffffff pref]
[    0.177663] pci 0000:02:00.0: reg 10: [mem 0xfdffc000-0xfdffffff 64bit]
[    0.177751] pci 0000:02:00.0: supports D1 D2
[    0.184032] pci 0000:00:02.0: PCI bridge to [bus 02-04]
[    0.184043] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.184055] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfdffffff]
[    0.184070] pci 0000:00:02.0:   bridge window [mem 0xde000000-0xdfffffff 64bit pref]
[    0.184158] pci 0000:00:03.0: PCI bridge to [bus 05-06]
[    0.184169] pci 0000:00:03.0:   bridge window [io  0xe000-0xefff]
[    0.184181] pci 0000:00:03.0:   bridge window [mem 0xfe000000-0xfe9fffff]
[    0.184197] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfaffffff 64bit pref]
[    0.184329] pci 0000:07:03.0: reg 10: [mem 0xfeaf0000-0xfeafffff]
[    0.184416] pci 0000:07:03.0: PME# supported from D3hot D3cold
[    0.184426] pci 0000:07:03.0: PME# disabled
[    0.184491] pci 0000:00:13.1: PCI bridge to [bus 07-07] (subtractive decode)
[    0.184503] pci 0000:00:13.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.184516] pci 0000:00:13.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.184531] pci 0000:00:13.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.184541] pci 0000:00:13.1:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.184551] pci 0000:00:13.1:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.184561] pci 0000:00:13.1:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.184572] pci 0000:00:13.1:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.184583] pci 0000:00:13.1:   bridge window [mem 0x37f00000-0xdfffffff] (subtractive decode)
[    0.184593] pci 0000:00:13.1:   bridge window [mem 0xf0000000-0xfeafffff] (subtractive decode)
[    0.184630] pci_bus 0000:00: on NUMA node 0
[    0.184648] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.185101] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.185260] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.185571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.185705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[    0.185861] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[    0.242012] ACPI: PCI Root Bridge [PCI1] (domain 0000 [bus 80-ff])
[    0.244634] pci_root PNP0A08:00: host bridge window [mem 0xfeb00000-0xfebfffff]
[    0.244700] pci 0000:80:01.0: reg 10: [mem 0xfebfc000-0xfebfffff 64bit]
[    0.244774] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
[    0.244785] pci 0000:80:01.0: PME# disabled
[    0.244859] pci_bus 0000:80: on NUMA node 0
[    0.244872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.245771] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.246094] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.246411] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.246725] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.247040] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.247378] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.247716] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.248078] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.248230] HEST: Table is not found!
[    0.248474] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.248488] vgaarb: loaded
[    0.248927] SCSI subsystem initialized
[    0.249071] libata version 3.00 loaded.
[    0.249224] usbcore: registered new interface driver usbfs
[    0.249261] usbcore: registered new interface driver hub
[    0.249326] usbcore: registered new device driver usb
[    0.250509] ACPI: WMI: Mapper loaded
[    0.250516] PCI: Using ACPI for IRQ routing
[    0.250657] PCI: pci_cache_line_size set to 64 bytes
[    0.250851] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.250860] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.250869] reserve RAM buffer: 0000000037eb0000 - 0000000037ffffff 
[    0.251136] NetLabel: Initializing
[    0.251142] NetLabel:  domain hash size = 128
[    0.251148] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.251183] NetLabel:  unlabeled traffic allowed by default
[    0.251288] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.251301] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.251317] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.256065] Switching to clocksource tsc
[    0.280420] AppArmor: AppArmor Filesystem Enabled
[    0.280458] pnp: PnP ACPI init
[    0.280503] ACPI: bus type pnp registered
[    0.285408]   alloc irq_desc for 22 on node -1
[    0.285416]   alloc kstat_irqs on node -1
[    0.288681] pnp: PnP ACPI: found 14 devices
[    0.288689] ACPI: ACPI bus type pnp unregistered
[    0.288699] PnPBIOS: Disabled by ACPI PNP
[    0.288737] system 00:05: [io  0x03e0-0x03e7] has been reserved
[    0.288747] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.288757] system 00:05: [io  0x0500-0x0501] has been reserved
[    0.288768] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.288778] system 00:05: [io  0x0400-0x041f] has been reserved
[    0.288791] system 00:05: [mem 0xfecc0000-0xfecc0fff] could not be reserved
[    0.288803] system 00:05: [mem 0xfed02000-0xfed02fff] has been reserved
[    0.288823] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.288834] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.288853] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.288870] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.288881] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.288892] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.288903] system 00:0c: [mem 0x00100000-0x37efffff] could not be reserved
[    0.288914] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.327591] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.327601] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.327616] pci 0000:00:01.0:   bridge window [mem 0xfbf00000-0xfcffffff]
[    0.327629] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd7ffffff pref]
[    0.327645] pci 0000:00:02.0: PCI bridge to [bus 02-04]
[    0.327655] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.327668] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfdffffff]
[    0.327681] pci 0000:00:02.0:   bridge window [mem 0xde000000-0xdfffffff 64bit pref]
[    0.327696] pci 0000:00:03.0: PCI bridge to [bus 05-06]
[    0.327706] pci 0000:00:03.0:   bridge window [io  0xe000-0xefff]
[    0.327720] pci 0000:00:03.0:   bridge window [mem 0xfe000000-0xfe9fffff]
[    0.327733] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfaffffff 64bit pref]
[    0.327749] pci 0000:00:13.1: PCI bridge to [bus 07-07]
[    0.327756] pci 0000:00:13.1:   bridge window [io  disabled]
[    0.327769] pci 0000:00:13.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.327779] pci 0000:00:13.1:   bridge window [mem pref disabled]
[    0.327812] pci 0000:00:01.0: setting latency timer to 64
[    0.327836]   alloc irq_desc for 27 on node -1
[    0.327844]   alloc kstat_irqs on node -1
[    0.327862] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.327873] pci 0000:00:02.0: setting latency timer to 64
[    0.327893]   alloc irq_desc for 31 on node -1
[    0.327899]   alloc kstat_irqs on node -1
[    0.327910] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    0.327929] pci 0000:00:03.0: setting latency timer to 64
[    0.327945] pci 0000:00:13.1: setting latency timer to 64
[    0.327959] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.327968] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.327977] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.327986] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.327996] pci_bus 0000:00: resource 8 [mem 0x37f00000-0xdfffffff]
[    0.328005] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfeafffff]
[    0.328016] pci_bus 0000:01: resource 1 [mem 0xfbf00000-0xfcffffff]
[    0.328025] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd7ffffff pref]
[    0.328035] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.328045] pci_bus 0000:02: resource 1 [mem 0xfd000000-0xfdffffff]
[    0.328055] pci_bus 0000:02: resource 2 [mem 0xde000000-0xdfffffff 64bit pref]
[    0.328065] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
[    0.328074] pci_bus 0000:05: resource 1 [mem 0xfe000000-0xfe9fffff]
[    0.328084] pci_bus 0000:05: resource 2 [mem 0xf8000000-0xfaffffff 64bit pref]
[    0.328095] pci_bus 0000:07: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.328104] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
[    0.328113] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
[    0.328122] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
[    0.328131] pci_bus 0000:07: resource 7 [mem 0x000d0000-0x000dffff]
[    0.328141] pci_bus 0000:07: resource 8 [mem 0x37f00000-0xdfffffff]
[    0.328150] pci_bus 0000:07: resource 9 [mem 0xf0000000-0xfeafffff]
[    0.328161] pci_bus 0000:80: resource 4 [mem 0xfeb00000-0xfebfffff]
[    0.328280] NET: Registered protocol family 2
[    0.328458] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.329245] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.331252] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.332344] TCP: Hash tables configured (established 131072 bind 65536)
[    0.332353] TCP reno registered
[    0.332367] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.332400] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.332639] NET: Registered protocol family 1
[    0.332668] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.332719] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.332872] pci 0000:01:00.0: Boot video device
[    0.332898] PCI: CLS 32 bytes, default 64
[    0.333097] cpufreq-nforce2: No nForce2 chipset.
[    0.333214] Scanning for low memory corruption every 60 seconds
[    0.333693] audit: initializing netlink socket (disabled)
[    0.333719] type=2000 audit(1305667980.328:1): initialized
[    0.364161] Trying to unpack rootfs image as initramfs...
[    0.397270] highmem bounce pool size: 64 pages
[    0.397287] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.408444] VFS: Disk quotas dquot_6.5.2
[    0.408645] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.410444] fuse init (API version 7.14)
[    0.410726] msgmni has been set to 1712
[    1.281976] Freeing initrd memory: 10512k freed
[    1.302277] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.302288] io scheduler noop registered
[    1.302295] io scheduler deadline registered
[    1.302339] io scheduler cfq registered (default)
[    1.302676] pcieport 0000:00:02.0: setting latency timer to 64
[    1.302935] pcieport 0000:00:03.0: setting latency timer to 64
[    1.303223] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.303454] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.357617] ACPI: AC Adapter [AC0] (off-line)
[    1.357908] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/PNP0C0D:00/input/input0
[    1.358030] ACPI: Lid Switch [LID]
[    1.358176] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.358198] ACPI: Sleep Button [SLPB]
[    1.358338] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    1.358351] ACPI: Power Button [PWRB]
[    1.358497] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.358509] ACPI: Power Button [PWRF]
[    1.359846] ACPI: acpi_idle registered with cpuidle
[    1.360136] Marking TSC unstable due to TSC halts in idle
[    1.364058] Switching to clocksource hpet
[    1.369331] thermal LNXTHERM:01: registered as thermal_zone0
[    1.369355] ACPI: Thermal Zone [THRM] (33 C)
[    1.369677] ERST: Table is not found!
[    1.371025] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.373815] isapnp: Scanning for PnP cards...
[    1.425076] brd: module loaded
[    1.426656] loop: module loaded
[    1.427374] pata_acpi 0000:00:0f.0: power state changed by ACPI to D0
[    1.427401] pata_acpi 0000:00:0f.0: power state changed by ACPI to D0
[    1.427422]   alloc irq_desc for 21 on node -1
[    1.427429]   alloc kstat_irqs on node -1
[    1.427448] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.427546] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    1.428815] Fixed MDIO Bus: probed
[    1.428978] PPP generic driver version 2.4.2
[    1.429496] tun: Universal TUN/TAP device driver, 1.6
[    1.429503] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.429799] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.429887] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.429932] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    1.430072] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    1.430176] ehci_hcd 0000:00:10.4: debug port 1
[    1.431017] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfbeffc00
[    1.474729] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    1.475144] hub 1-0:1.0: USB hub found
[    1.475157] hub 1-0:1.0: 8 ports detected
[    1.475364] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.475412] uhci_hcd: USB Universal Host Controller Interface driver
[    1.475526]   alloc irq_desc for 20 on node -1
[    1.475533]   alloc kstat_irqs on node -1
[    1.475577] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.475595] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    1.475718] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    1.475783] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000b800
[    1.476184] hub 2-0:1.0: USB hub found
[    1.476197] hub 2-0:1.0: 2 ports detected
[    1.476363] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.476380] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    1.476478] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    1.476520] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b880
[    1.476860] hub 3-0:1.0: USB hub found
[    1.476871] hub 3-0:1.0: 2 ports detected
[    1.477036]   alloc irq_desc for 23 on node -1
[    1.477043]   alloc kstat_irqs on node -1
[    1.477061] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.477076] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    1.477178] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    1.477238] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000bc00
[    1.477561] hub 4-0:1.0: USB hub found
[    1.477573] hub 4-0:1.0: 2 ports detected
[    1.477878] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f12:PS2M] at 0x60,0x64 irq 1,12
[    1.482127] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.528504] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.528525] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.528606] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.528668] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.528730] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.529048] mice: PS/2 mouse device common for all mice
[    1.529479] rtc_cmos 00:07: RTC can wake from S4
[    1.529583] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.529638] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.529988] device-mapper: uevent: version 1.0.3
[    1.530325] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.530458] device-mapper: multipath: version 1.1.1 loaded
[    1.530467] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.530826] EISA: Probing bus 0 at eisa.0
[    1.530836] EISA: Cannot allocate resource for mainboard
[    1.530845] Cannot allocate resource for EISA slot 1
[    1.530852] Cannot allocate resource for EISA slot 2
[    1.530860] Cannot allocate resource for EISA slot 3
[    1.530867] Cannot allocate resource for EISA slot 4
[    1.530874] Cannot allocate resource for EISA slot 5
[    1.530882] Cannot allocate resource for EISA slot 6
[    1.530889] Cannot allocate resource for EISA slot 7
[    1.530896] Cannot allocate resource for EISA slot 8
[    1.530903] EISA: Detected 0 cards.
[    1.531108] cpuidle: using governor ladder
[    1.531271] cpuidle: using governor menu
[    1.532202] TCP cubic registered
[    1.532651] NET: Registered protocol family 10
[    1.533680] lo: Disabled Privacy Extensions
[    1.534326] NET: Registered protocol family 17
[    1.535378] longhaul: APIC detected. Longhaul is currently broken in this configuration.
[    1.535393] Using IPI No-Shortcut mode
[    1.535658] PM: Resume from disk failed.
[    1.535686] registered taskstats version 1
[    1.536366]   Magic number: 11:528:601
[    1.536632] rtc_cmos 00:07: setting system clock to 2011-05-17 21:33:01 UTC (1305667981)
[    1.536642] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.536649] EDD information not available.
[    1.755077] isapnp: No Plug & Play device found
[    1.755127] Freeing unused kernel memory: 688k freed
[    1.756357] Write protecting the kernel text: 4944k
[    1.756479] Write protecting the kernel read-only data: 1976k
[    1.778859] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.812567] udev[64]: starting version 163
[    1.820145] usb 1-8: new high speed USB device using ehci_hcd and address 2
[    1.868362] ACPI: Battery Slot [BAT1] (battery present)
[    2.537847] sata_via 0000:00:0f.0: version 2.6
[    2.537915] sata_via 0000:00:0f.0: power state changed by ACPI to D0
[    2.537941] sata_via 0000:00:0f.0: power state changed by ACPI to D0
[    2.537962] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.538038] sata_via 0000:00:0f.0: routed to hard irq line 5
[    2.553891] scsi0 : sata_via
[    2.570044] scsi1 : sata_via
[    2.574419] ata1: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 21
[    2.574431] ata2: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 21
[    2.672366]   alloc irq_desc for 24 on node -1
[    2.672376]   alloc kstat_irqs on node -1
[    2.672395] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[    2.672415] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[    2.692283] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.692301] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.692317] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.692332] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.744991] tg3.c:v3.110 (April 9, 2010)
[    2.745035]   alloc irq_desc for 16 on node -1
[    2.745043]   alloc kstat_irqs on node -1
[    2.745061] tg3 0000:07:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.748157] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    2.826657] ata1: SATA link up 1.5 Gbps (SStatus 123 SControl 300)
[    2.828703] tg3 0000:07:03.0: eth0: Tigon3 [partno(BCM95788) rev 3003] (PCI:33MHz:32-bit) MAC address 00:25:b3:5f:24:d2
[    2.828718] tg3 0000:07:03.0: eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[0])
[    2.828730] tg3 0000:07:03.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.828740] tg3 0000:07:03.0: eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
[    2.988319] ata1.00: ATA-8: ST9120817AS, 3.AHC, max UDMA/100
[    2.988331] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.004345] ata1.00: configured for UDMA/100
[    3.004583] scsi 0:0:0:0: Direct-Access     ATA      ST9120817AS      3.AH PQ: 0 ANSI: 5
[    3.005025] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.005663] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    3.005779] sd 0:0:0:0: [sda] Write Protect is off
[    3.005789] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.005840] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.006976]  sda: sda1 sda2 sda3 sda4
[    3.069708] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.208092] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.874539] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    6.294229] Adding 1983484k swap on /dev/sda4.  Priority:-1 extents:1 across:1983484k 
[    8.284674] udev[340]: starting version 163
[    8.674090] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[    9.259581] ACPI: resource vt596_smbus [io  0x0400-0x0407] conflicts with ACPI region SMA1 [??? 0x00000400-0x0000040f flags 0x31]
[    9.259594] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.424145] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.233136] Linux agpgart interface v0.103
[   10.316479] Linux video capture interface: v2.00
[   10.365329] lp: driver loaded but no devices found
[   10.440774] lis3lv02d: laptop model unknown, using default axes configuration
[   10.495279] lis3lv02d: 8 bits sensor found
[   10.588262] agpgart: Detected VIA P4M900 chipset
[   10.685693] uvcvideo: Found UVC 1.00 device CNF7070 (04f2:b107)
[   10.740265] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   10.745363] input: CNF7070 as /devices/pci0000:00/0000:00:10.4/usb1/1-8/1-8:1.0/input/input5
[   10.745577] usbcore: registered new interface driver uvcvideo
[   10.745585] USB Video Class driver (v0.1.0)
[   10.751688] cfg80211: Calling CRDA to update world regulatory domain
[   10.755149] acpi device:08: registered as cooling_device1
[   10.756997] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:07/LNXVIDEO:00/input/input6
[   10.757424] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.840354] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
[   10.840693] Registered led device: hp::hddprotect
[   10.840752] lis3lv02d driver loaded.
[   11.167825] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04711/0xa00000/0x0
[   11.168962] input: HP WMI hotkeys as /devices/virtual/input/input8
[   11.208741] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   11.885607] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   11.990240] type=1400 audit(1305660791.952:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=642 comm="apparmor_parser"
[   11.991027] type=1400 audit(1305660791.952:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
[   11.991498] type=1400 audit(1305660791.952:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=642 comm="apparmor_parser"
[   11.993915] type=1400 audit(1305660791.952:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=643 comm="apparmor_parser"
[   11.994704] type=1400 audit(1305660791.952:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=643 comm="apparmor_parser"
[   11.995179] type=1400 audit(1305660791.952:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=643 comm="apparmor_parser"
[   12.039881] HP WMI: Unknown response received
[   12.564176] cfg80211: World regulatory domain updated:
[   12.564188]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.564200]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.564210]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.564220]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.564231]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.564241]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.653390] phy0: Selected rate control algorithm 'minstrel'
[   12.655176] Registered led device: b43-phy0::tx
[   12.655228] Registered led device: b43-phy0::rx
[   12.655294] Registered led device: b43-phy0::radio
[   12.655498] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   13.197364] HDA Intel 0000:80:01.0: power state changed by ACPI to D0
[   13.197464] HDA Intel 0000:80:01.0: power state changed by ACPI to D0
[   13.197486]   alloc irq_desc for 17 on node -1
[   13.197494]   alloc kstat_irqs on node -1
[   13.197512] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.197621] HDA Intel 0000:80:01.0: setting latency timer to 64
[   13.197632] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
[   16.403021] type=1400 audit(1305660796.360:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=885 comm="apparmor_parser"
[   16.403817] type=1400 audit(1305660796.360:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=885 comm="apparmor_parser"
[   16.404974] type=1400 audit(1305660796.364:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=885 comm="apparmor_parser"
[   16.604973] type=1400 audit(1305660796.564:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=889 comm="apparmor_parser"
[   16.994322] audit_printk_skb: 6 callbacks suppressed
[   16.994334] type=1400 audit(1305660796.952:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=891 comm="apparmor_parser"
[   17.002303] type=1400 audit(1305660796.960:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=891 comm="apparmor_parser"
[   17.022976] type=1400 audit(1305660796.980:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=901 comm="apparmor_parser"
[   17.025251] type=1400 audit(1305660796.984:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=901 comm="apparmor_parser"
[   17.060486] type=1400 audit(1305660797.020:18): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=902 comm="apparmor_parser"
[   17.717890] ppdev: user-space parallel port driver
[   20.124064] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   22.960387] [drm] Initialized drm 1.1.0 20060810
[   24.652501] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[   25.972250] b43-pci-bridge 0000:02:00.0: PCI: Disallowing DAC for device
[   25.972264] b43-phy0: DMA mask fallback from 64-bit to 32-bit
[   25.994294] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.335852] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.070078] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[   62.320093] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   69.333250] wlan0: authenticate with 00:21:04:4f:b5:f0 (try 1)
[   69.336576] wlan0: authenticated
[   69.337602] wlan0: associate with 00:21:04:4f:b5:f0 (try 1)
[   69.339924] wlan0: RX AssocResp from 00:21:04:4f:b5:f0 (capab=0x431 status=0 aid=5)
[   69.339941] wlan0: associated
[   69.344478] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   69.684785] padlock: Using VIA PadLock ACE for AES algorithm.
[   78.640107] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   79.089300] Bluetooth: Core ver 2.15
[   79.089420] NET: Registered protocol family 31
[   79.089429] Bluetooth: HCI device and connection manager initialized
[   79.089441] Bluetooth: HCI socket layer initialized
[   79.219356] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   79.230547] usbcore: registered new interface driver btusb
[   79.424050] wlan0: no IPv6 routers present
[   79.536900] Bluetooth: L2CAP ver 2.14
[   79.536914] Bluetooth: L2CAP socket layer initialized
[   79.735441] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   79.735456] Bluetooth: BNEP filters: protocol multicast
[   79.816274] Bluetooth: SCO (Voice Link) ver 0.6
[   79.816289] Bluetooth: SCO socket layer initialized
[   80.138889] Bluetooth: RFCOMM TTY layer initialized
[   80.138913] Bluetooth: RFCOMM socket layer initialized
[   80.138924] Bluetooth: RFCOMM ver 1.11
[  306.630621] hci_cmd_task: hci0 command tx timeout
[  321.444533] hci_cmd_task: hci0 command tx timeout
[  385.638339] EXT4-fs (sda2): bad geometry: block count 11261696 exceeds size of device (2441216 blocks)
```

---

### Post by sbrbot on 2011-05-17
Here is output of lsmod command:
```
Module                  Size  Used by
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
btusb                  10969  2 
bluetooth              50500  11 rfcomm,sco,bnep,l2cap,btusb
padlock_aes             4935  3 
aes_i586                7280  0 
aes_generic            26875  2 padlock_aes,aes_i586
via                    37920  0 
drm                   168092  1 via
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_analog    59649  1 
snd_hda_intel          22235  4 
snd_hda_codec          87552  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
arc4                    1165  2 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
b43                   168681  0 
snd_timer              19067  2 snd_pcm,snd_seq
mac80211              231927  1 b43
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8767  0 
hp_wmi                  5223  0 
uvcvideo               55879  0 
snd                    49102  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
via_agp                 5322  1 
video                  18712  0 
hp_accel               13204  0 
lis3lv02d               8556  1 hp_accel
cfg80211              144790  2 b43,mac80211
output                  1883  1 video
videodev               43098  1 uvcvideo
soundcore                880  1 snd
psmouse                59033  0 
lp                      7342  0 
input_polldev           3491  1 lis3lv02d
v4l1_compat            13359  2 uvcvideo,videodev
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,via_agp
serio_raw               4022  0 
shpchp                 29886  0 
i2c_viapro              5777  0 
led_class               2633  2 b43,hp_accel
parport                31492  3 parport_pc,ppdev,lp
tg3                   123310  0 
ssb                    39320  1 b43
sata_via                7344  3 
```

---

### Post by byroncheng on 2011-05-26
> **jeevak said:**
> hey!

i seem to have the same problem. it freezes when it tries to connect to the net via the wireless!!!! i have to turn it off in order to use the "netbook"!!! kinda defeats the purpose of a netbook now doesnt it!! 
solution? 
problem with the drivers maybe?
anyone from ubuntu got a solution??

Ubuntu Launchpad site has a solution for the Wifi freeze problem - It's solved that problem on my Mininote (now to fix the fact that it just runs slowly)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/772923/comments/28](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/772923/comments/28)

They suggest updating the kernel to 2.6.39.0

---

### Post by gekko95 on 2011-07-07
Hi folks,

I am having exactly the same issue.  I haven't had any luck getting a stable installation on my HP 2133 since 10.04.  Versions 10.10, 11.04 and even 11.10 have all had issues for me:

- The wireless has been an issue on everything upto 11.10.  The commonly accepted fix seems to be to upgrade to kernel 2.6.39, though the ppa links are now all coming up empty.

- I put in a new SSD hard drive (not wanting to risk an install that works) and set up a clean 11.04 leaving the wireless turned off.  I then did an in-place upgrade to 11.10, which brought the kernel to version 3.03.  Wireless seems to be stable but...

Gnome 3 comes by default with this release and the HP 2133 does not have the graphics capability to run it.  My session also lacked a lot of the controls and plugins I was used to.  After working in 11.10 for a while I updated packages and then rebooted, after which the machine refused to come up.  During startup I consistently see udevd[55] runtime errors.

Another 11.04 install, in-place upgrade to 11.10 and a downgrade to gnome-panel (ie version 2) resulted in broken dependencies and another non-starter.

And in all 4 versions getting my external monitor to display correctly took more work than I usually put in to my day job.

Has anyone had any luck getting 11.04 running on an HP 2133?  If not, what would be the best netbook to buy if I want to be able to upgrade to the latest version and use all of the latest features?

I realize my post doesn't contain a lot of technical output or screenshots, please don't take this to mean I'm a noob.  I have been happily using Ubuntu for years and have several active web servers using the server flavour.  I'm getting pretty frustrated, though, with the later releases and what seems to be lack of support for legacy systems.  I've maxed out the RAM on my 2133 and invested in a decent drive, this unit should be good for at least a couple of years.

A reference to a good, supported netbook will get you good karma and I'm happy to pay a reasonable support fee for a solution that works with my existing gear.  Any takers?

S

---

### Post by simonjpo on 2011-08-07
Today, I got 11.04 working very well on my 2133. I have previously put in extra RAM up to the maximum.
The first thing I did after (this attempted) install was turn off networking at boot. 2.6.39 RC4 was no help. I wired down Oneiric 3.0 Kernel, and applied it.
Since when it's been rock solid, including wirelessly installing everything I needed to download my own demo programmes (I use this occasionally for commercial work), and rebuilding them using a fresh install of MonoDevelop; they need this because 11.04 only uses OpenCV 2.1.
The programmes are intensive and also use the camera, so they make a good load test. They ran cleanly.
I also installed my 70GB music collection, for personal use, and while Banshee struggled at times to import it all in one go, playback was fine and nothing hung.

As for the VGA port, screen cloning is possible if you include the following in an xorg.conf file :
Section "Device"
Identifier "Configured Video Device"
Option "ActiveDevice"  "LCD, CRT"
Option "SWCursor" "on"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

I can't swear to it yet, because it's only worked on 9.10, 10.04 and 10.10 before; I'll probably check it on 11.04 tomorrow after work.

What worries me is the rumour that 11.10 won't be able to support my 2133 at all.
My desktop is LTS in any case, so only goes over at 12.04.

---

### Post by speyburn on 2011-08-11
Hi,

I've installed Xubuntu to a HP 2133 laptop and im having troubles with the wifi. Every time i turn it on the computer freezes.

Now the previous links suggest that i install kernel 2.6.39-0, but since the source is down and they only provide .deb files from another source, I really don't know how on install them.

Could someone help a noobish person here? :)

---

### Post by simonjpo on 2011-08-13
Speyburn,
on the help page for the original problem, it is acknowledged that the repository is NBG anymore; a link is provided to all the Ubuntu kernel packages.
If you can find this, you're nearly there.
Download the .deb files(Debian package style)with your 2133 wifi networking disabled(right button immediately on boot until orange light) and using ethernet.
That is:
Headers-All, Headers-386 and Image-386.
Install each in that order.
Do it from the command line using sudo dpkg -i (i for 'install')and the full package name.
Best to cd into the download directory, then use tab to auto complete the package names.
This will avoid irritating name errors.
Reboot, and you should have a sweet little system, although you might find it doesn't try to update anymore since it thinks it's from the future.:)

ps-the xorg.conf file works like a charm on 11.04. Just put it in /etc/X11. (If you're lazy, and the protection won't let you import the file, run sudo nautilus to get full permissions - but be very, very careful!)

pps:- It will try to update, and it will try to revert to the broken kernel. I use 3.0 and turned updates off altogether.

---

### Post by sbrbot on 2012-05-06
Did somebody try to install Ubuntu 12.04 on HP 2133? Any luck?

---

### Post by fhuang2 on 2012-05-20
Yeap... just installed Ubuntu 12.04 (32-bit) on HP 2133.  Wi-Fi driver was recognized and proprietary drivers installed.

02:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 02)

Sound is working as well, though YouTube video is sluggish.  

Just installed Skype 2.2.0.35 and the mic does not work.  Sound recording is all garbled... I did  try Puppy Linux 5.x and got Skype mic to work before...

---

### Post by sbrbot on 2012-05-21
Thank you for your reply of installing Precise on Mini. YouTube is sluggish because of weak CPU on this machine, of course. However, it's nice to know that there's no issue with NIC like in Oneiric.

---

