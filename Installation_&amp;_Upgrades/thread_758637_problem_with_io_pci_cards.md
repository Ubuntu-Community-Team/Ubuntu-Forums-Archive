---
title: "problem with i/o pci cards"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by anteone on 2008-04-18
Hi everybody,
long time reader, first time writer.

I am putting ubuntu on a pc with 2 sunix 4037t i/o pci card, each one with 2 rs232 ports on.
The motherboard has one more rs232 onboard itself.

I installed proper drivers and loaded related kernel module.
My system recognize all ports and they seem to work pretty fine but..
one process that use one of the four pci serial port, once started, stops almost immediately.
It doesn't crash, it stops (let me said like if use CTRL+Z).

I found out an error in /var/log/messages but I really don't know how to overcome it.

/var/log/messages
```

Apr 18 11:29:08 Cas02poli027 syslogd 1.4.1#21ubuntu3: restart.
Apr 18 11:29:08 Cas02poli027 kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr 18 11:29:08 Cas02poli027 kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr 18 11:29:08 Cas02poli027 kernel: Symbols match kernel version 2.6.22.
Apr 18 11:29:08 Cas02poli027 kernel: No module symbols loaded - kernel modules not enabled. 
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ec13000 (usable)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000001ec13000 - 000000001ec15000 (reserved)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000001ec15000 - 000000001ed2a000 (usable)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000001ed2a000 - 000000001ede5000 (ACPI NVS)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000001ede5000 - 000000001edeb000 (usable)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000001edeb000 - 000000001edf2000 (ACPI data)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000001edf2000 - 000000001edf3000 (usable)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000001edf3000 - 000000001edff000 (ACPI data)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000001edff000 - 000000001ee00000 (usable)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 000000001ee00000 - 000000001f800000 (reserved)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] 0MB HIGHMEM available.
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] 494MB LOWMEM available.
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] found SMP MP-table at 000fe200
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Zone PFN ranges:
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]   DMA             0 ->     4096
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]   Normal       4096 ->   126464
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]   HighMem    126464 ->   126464
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000]     0:        0 ->   126464
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] DMI 2.4 present.
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: RSDT 1EDFD038, 0058 (r1 INTEL  DG33BU        19D       1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: FACP 1EDFC000, 0074 (r1 INTEL  DG33BU        19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: DSDT 1EDF8000, 3DAD (r1 INTEL  DG33BU        19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: FACS 1ED96000, 0040
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: APIC 1EDF7000, 0078 (r1 INTEL  DG33BU        19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: WDDT 1EDF6000, 0040 (r1 INTEL  DG33BU        19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: MCFG 1EDF5000, 003C (r1 INTEL  DG33BU        19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: ASF! 1EDF4000, 00A6 (r32 INTEL  DG33BU        19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: HPET 1EDF3000, 0038 (r1 INTEL  DG33BU        19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: ASPT 1EDF1000, 002C (r1 INTEL  DG33BU        19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: WDTT 1EDF0000, 02CC (r1 INTEL  DG33BU        19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: SSDT 1EDEF000, 0204 (r1 INTEL     CpuPm      19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: SSDT 1EDEE000, 00DD (r1 INTEL   Cpu0Cst      19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: SSDT 1EDED000, 00DD (r1 INTEL   Cpu1Cst      19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: SSDT 1EDEC000, 00DD (r1 INTEL   Cpu2Cst      19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: SSDT 1EDEB000, 00DD (r1 INTEL   Cpu3Cst      19D MSFT  1000013)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Processor #0 7:6 APIC version 20
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:d0800000)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Built 1 zonelists.  Total pages: 125476
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Kernel command line: root=UUID=a2c779ec-9487-4c93-9b34-1b7e86b53e33 ro quiet splash
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Initializing CPU#0
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 18 11:29:08 Cas02poli027 kernel: [    0.000000] Detected 1800.163 MHz processor.
Apr 18 11:29:08 Cas02poli027 kernel: [   17.494961] Console: colour VGA+ 80x25
Apr 18 11:29:08 Cas02poli027 kernel: [   17.495078] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.495196] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504304] Memory: 488716k/505856k available (2015k kernel code, 15592k reserved, 916k data, 364k init, 0k highmem)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504312] virtual kernel memory layout:
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504313]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504315]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504316]     vmalloc : 0xdf800000 - 0xff7fe000   ( 511 MB)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504317]     lowmem  : 0xc0000000 - 0xdee00000   ( 494 MB)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504318]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504319]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504320]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504323] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504351] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504480] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Apr 18 11:29:08 Cas02poli027 kernel: [   17.504485] hpet0: 4 64-bit timers, 14318180 Hz
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585375] Calibrating delay using timer specific routine.. 3602.87 BogoMIPS (lpj=7205756)
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585392] Security Framework v1.0.0 initialized
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585396] SELinux:  Disabled at boot.
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585406] Mount-cache hash table entries: 512
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585513] monitor/mwait feature present.
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585514] using mwait in idle threads.
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585518] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585520] CPU: L2 cache: 512K
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585530] Compat vDSO mapped to ffffe000.
Apr 18 11:29:08 Cas02poli027 kernel: [   17.585541] Checking 'hlt' instruction... OK.
Apr 18 11:29:08 Cas02poli027 kernel: [   17.601470] SMP alternatives: switching to UP code
Apr 18 11:29:08 Cas02poli027 kernel: [   17.601669] Freeing SMP alternatives: 11k freed
Apr 18 11:29:08 Cas02poli027 kernel: [   17.601904] Early unpacking initramfs... done
Apr 18 11:29:08 Cas02poli027 kernel: [   17.916174] ACPI: Core revision 20070126
Apr 18 11:29:08 Cas02poli027 kernel: [   17.916215] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 18 11:29:08 Cas02poli027 kernel: [   17.920333] CPU0: Intel(R) Celeron(R) CPU          430  @ 1.80GHz stepping 01
Apr 18 11:29:08 Cas02poli027 kernel: [   17.920355] Total of 1 processors activated (3602.87 BogoMIPS).
Apr 18 11:29:08 Cas02poli027 kernel: [   17.920494] ENABLING IO-APIC IRQs
Apr 18 11:29:08 Cas02poli027 kernel: [   17.920661] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 18 11:29:08 Cas02poli027 kernel: [   18.064669] Brought up 1 CPUs
Apr 18 11:29:08 Cas02poli027 kernel: [   18.064765] Booting paravirtualized kernel on bare hardware
Apr 18 11:29:08 Cas02poli027 kernel: [   18.064819] Time:  9:28:56  Date: 03/18/108
Apr 18 11:29:08 Cas02poli027 kernel: [   18.064837] NET: Registered protocol family 16
Apr 18 11:29:08 Cas02poli027 kernel: [   18.064910] EISA bus registered
Apr 18 11:29:08 Cas02poli027 kernel: [   18.064916] ACPI: bus type pci registered
Apr 18 11:29:08 Cas02poli027 kernel: [   18.066440] PCI: Using configuration type 1
Apr 18 11:29:08 Cas02poli027 kernel: [   18.066442] Setting up standard PCI resources
Apr 18 11:29:08 Cas02poli027 kernel: [   18.074482] ACPI: Interpreter enabled
Apr 18 11:29:08 Cas02poli027 kernel: [   18.074485] ACPI: (supports S0 S1 S4 S5)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.074498] ACPI: Using IOAPIC for interrupt routing
Apr 18 11:29:08 Cas02poli027 kernel: [   18.079434] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.080732] PCI: Transparent bridge - 0000:00:1e.0
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085072] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085164] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085250] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085335] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085422] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085507] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *9 10 11 12)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085591] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085676] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085792] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085803] pnp: PnP ACPI init
Apr 18 11:29:08 Cas02poli027 kernel: [   18.085811] ACPI: bus type pnp registered
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088352] pnp: PnP ACPI: found 13 devices
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088356] ACPI: ACPI bus type pnp unregistered
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088360] PnPBIOS: Disabled by ACPI PNP
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088405] PCI: Using ACPI for IRQ routing
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088408] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088483] NET: Registered protocol family 8
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088485] NET: Registered protocol family 20
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088549] pnp: 00:01: iomem range 0xf0000000-0xf7ffffff could not be reserved
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088552] pnp: 00:01: iomem range 0xfeb00000-0xfeb03fff has been reserved
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088555] pnp: 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088558] pnp: 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088565] pnp: 00:06: ioport range 0x500-0x53f has been reserved
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088567] pnp: 00:06: ioport range 0x400-0x47f has been reserved
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088570] pnp: 00:06: ioport range 0x680-0x6ff has been reserved
Apr 18 11:29:08 Cas02poli027 kernel: [   18.088605] Time: tsc clocksource has been installed.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.116572] Switched to high resolution mode on CPU 0
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118852] PCI: Bridge: 0000:00:01.0
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118853]   IO window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118857]   MEM window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118859]   PREFETCH window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118862] PCI: Bridge: 0000:00:1c.0
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118864]   IO window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118867]   MEM window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118870]   PREFETCH window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118875] PCI: Bridge: 0000:00:1c.1
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118877]   IO window: 2000-2fff
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118882]   MEM window: 30100000-301fffff
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118885]   PREFETCH window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118889] PCI: Bridge: 0000:00:1c.2
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118890]   IO window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118894]   MEM window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118897]   PREFETCH window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118901] PCI: Bridge: 0000:00:1c.3
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118902]   IO window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118906]   MEM window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118909]   PREFETCH window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118914] PCI: Bridge: 0000:00:1c.4
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118915]   IO window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118919]   MEM window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118922]   PREFETCH window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118926] PCI: Bridge: 0000:00:1e.0
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118929]   IO window: 1000-1fff
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118933]   MEM window: 30000000-300fffff
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118936]   PREFETCH window: disabled.
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118954] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118977] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 18 11:29:08 Cas02poli027 kernel: [   18.118998] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 20 (level, low) -> IRQ 18
Apr 18 11:29:08 Cas02poli027 kernel: [   18.119018] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 19
Apr 18 11:29:08 Cas02poli027 kernel: [   18.119040] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 20
Apr 18 11:29:08 Cas02poli027 kernel: [   18.119060] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
Apr 18 11:29:08 Cas02poli027 kernel: [   18.119086] NET: Registered protocol family 2
Apr 18 11:29:08 Cas02poli027 kernel: [   18.156533] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.156571] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.156681] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.156759] TCP: Hash tables configured (established 16384 bind 16384)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.156763] TCP reno registered
Apr 18 11:29:08 Cas02poli027 kernel: [   18.168633] checking if image is initramfs... it is
Apr 18 11:29:08 Cas02poli027 kernel: [   18.785595] Freeing initrd memory: 7347k freed
Apr 18 11:29:08 Cas02poli027 kernel: [   18.786013] audit: initializing netlink socket (disabled)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.786024] audit(1208510935.976:1): initialized
Apr 18 11:29:08 Cas02poli027 kernel: [   18.787845] VFS: Disk quotas dquot_6.5.1
Apr 18 11:29:08 Cas02poli027 kernel: [   18.787896] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.787989] io scheduler noop registered
Apr 18 11:29:08 Cas02poli027 kernel: [   18.787991] io scheduler anticipatory registered
Apr 18 11:29:08 Cas02poli027 kernel: [   18.787993] io scheduler deadline registered
Apr 18 11:29:08 Cas02poli027 kernel: [   18.788012] io scheduler cfq registered (default)
Apr 18 11:29:08 Cas02poli027 kernel: [   18.788144] assign_interrupt_mode Found MSI capability
Apr 18 11:29:08 Cas02poli027 kernel: [   18.788255] assign_interrupt_mode Found MSI capability
Apr 18 11:29:08 Cas02poli027 kernel: [   18.788394] assign_interrupt_mode Found MSI capability
Apr 18 11:29:08 Cas02poli027 kernel: [   18.788534] assign_interrupt_mode Found MSI capability
Apr 18 11:29:08 Cas02poli027 kernel: [   18.788672] assign_interrupt_mode Found MSI capability
Apr 18 11:29:08 Cas02poli027 kernel: [   18.788814] assign_interrupt_mode Found MSI capability
Apr 18 11:29:08 Cas02poli027 kernel: [   18.788974] isapnp: Scanning for PnP cards...
Apr 18 11:29:08 Cas02poli027 kernel: [   19.141657] isapnp: No Plug & Play device found
Apr 18 11:29:08 Cas02poli027 kernel: [   19.174881] Real Time Clock Driver v1.12ac
Apr 18 11:29:08 Cas02poli027 kernel: [   19.175009] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 18 11:29:08 Cas02poli027 kernel: [   19.175101] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 18 11:29:08 Cas02poli027 kernel: [   19.175991] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 18 11:29:08 Cas02poli027 kernel: [   19.176207] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 21 (level, low) -> IRQ 21
Apr 18 11:29:08 Cas02poli027 kernel: [   19.176334] 0000:07:00.0: ttyS1 at I/O 0x1020 (irq = 21) is a 16550A
Apr 18 11:29:08 Cas02poli027 kernel: [   19.176578] 0000:07:00.0: ttyS2 at I/O 0x1028 (irq = 21) is a 16550A
Apr 18 11:29:08 Cas02poli027 kernel: [   19.176716] ACPI: PCI Interrupt 0000:07:01.0[A] -> GSI 22 (level, low) -> IRQ 22
Apr 18 11:29:08 Cas02poli027 kernel: [   19.176841] 0000:07:01.0: ttyS3 at I/O 0x1000 (irq = 22) is a 16550A
Apr 18 11:29:08 Cas02poli027 kernel: [   19.176968] Couldn't register serial port 0000:07:01.0: -28
Apr 18 11:29:08 Cas02poli027 kernel: [   19.177452] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 18 11:29:08 Cas02poli027 kernel: [   19.177638] input: Macintosh mouse button emulation as /class/input/input0
Apr 18 11:29:08 Cas02poli027 kernel: [   19.177713] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Apr 18 11:29:08 Cas02poli027 kernel: [   19.180971] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 18 11:29:08 Cas02poli027 kernel: [   19.180977] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181152] mice: PS/2 mouse device common for all mice
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181257] EISA: Probing bus 0 at eisa.0
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181263] Cannot allocate resource for EISA slot 1
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181265] Cannot allocate resource for EISA slot 2
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181267] Cannot allocate resource for EISA slot 3
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181283] EISA: Detected 0 cards.
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181361] TCP cubic registered
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181377] NET: Registered protocol family 1
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181400] Using IPI No-Shortcut mode
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181555]   Magic number: 4:219:475
Apr 18 11:29:08 Cas02poli027 kernel: [   19.181756] Freeing unused kernel memory: 364k freed
Apr 18 11:29:08 Cas02poli027 kernel: [   19.218931] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 18 11:29:08 Cas02poli027 kernel: [   20.370834] AppArmor: AppArmor initialized<5>audit(1208510937.476:2):  type=1505 info="AppArmor initialized" pid=1229
Apr 18 11:29:08 Cas02poli027 kernel: [   20.376259] fuse init (API version 7.8)
Apr 18 11:29:08 Cas02poli027 kernel: [   20.380230] Failure registering capabilities with primary security module.
Apr 18 11:29:08 Cas02poli027 kernel: [   20.388722] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 18 11:29:08 Cas02poli027 kernel: [   20.388733] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Apr 18 11:29:08 Cas02poli027 kernel: [   20.388741] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Apr 18 11:29:08 Cas02poli027 kernel: [   20.388750] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Apr 18 11:29:08 Cas02poli027 kernel: [   20.919816] SCSI subsystem initialized
Apr 18 11:29:08 Cas02poli027 kernel: [   20.926929] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 18 11:29:08 Cas02poli027 kernel: [   20.927014] scsi0 : pata_marvell
Apr 18 11:29:08 Cas02poli027 kernel: [   20.927050] scsi1 : pata_marvell
Apr 18 11:29:08 Cas02poli027 kernel: [   20.927074] ata1: PATA max UDMA/100 cmd 0x00012018 ctl 0x00012026 bmdma 0x00012000 irq 17
Apr 18 11:29:08 Cas02poli027 kernel: [   20.927077] ata2: DUMMY
Apr 18 11:29:08 Cas02poli027 kernel: [   20.927099] BAR5:00:00 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:01 0D:00 0E:00 0F:00 
Apr 18 11:29:08 Cas02poli027 kernel: [   21.053700] Floppy drive(s): fd0 is 1.44M
Apr 18 11:29:08 Cas02poli027 kernel: [   21.091966] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Apr 18 11:29:08 Cas02poli027 kernel: [   21.091988] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 21 (level, low) -> IRQ 21
Apr 18 11:29:08 Cas02poli027 kernel: [   21.092075] scsi2 : ata_piix
Apr 18 11:29:08 Cas02poli027 kernel: [   21.094357] scsi3 : ata_piix
Apr 18 11:29:08 Cas02poli027 kernel: [   21.094466] ata3: SATA max UDMA/133 cmd 0x00013098 ctl 0x000130b6 bmdma 0x00013070 irq 21
Apr 18 11:29:08 Cas02poli027 kernel: [   21.094469] ata4: SATA max UDMA/133 cmd 0x00013090 ctl 0x000130b2 bmdma 0x00013078 irq 21
Apr 18 11:29:08 Cas02poli027 kernel: [   21.109406] FDC 0 is a National Semiconductor PC87306
Apr 18 11:29:08 Cas02poli027 kernel: [   21.422232] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
Apr 18 11:29:08 Cas02poli027 kernel: [   21.422256] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 21 (level, low) -> IRQ 21
Apr 18 11:29:08 Cas02poli027 kernel: [   21.422314] scsi4 : ata_piix
Apr 18 11:29:08 Cas02poli027 kernel: [   21.422364] scsi5 : ata_piix
Apr 18 11:29:08 Cas02poli027 kernel: [   21.422425] ata5: SATA max UDMA/133 cmd 0x00013088 ctl 0x000130ae bmdma 0x00013050 irq 21
Apr 18 11:29:08 Cas02poli027 kernel: [   21.422428] ata6: SATA max UDMA/133 cmd 0x00013080 ctl 0x000130aa bmdma 0x00013058 irq 21
Apr 18 11:29:08 Cas02poli027 kernel: [   21.591754] ata5.00: ATA-7: WDC WD800AAJS-22PSA0, 05.06H05, max UDMA/133
Apr 18 11:29:08 Cas02poli027 kernel: [   21.591760] ata5.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr 18 11:29:08 Cas02poli027 kernel: [   21.607940] ata5.00: configured for UDMA/133
Apr 18 11:29:08 Cas02poli027 kernel: [   21.773741] scsi 4:0:0:0: Direct-Access     ATA      WDC WD800AAJS-22 05.0 PQ: 0 ANSI: 5
Apr 18 11:29:08 Cas02poli027 kernel: [   21.774162] ACPI: PCI Interrupt 0000:07:03.0[A] -> GSI 19 (level, low) -> IRQ 20
Apr 18 11:29:08 Cas02poli027 kernel: [   21.824133] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[30004000-300047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Apr 18 11:29:08 Cas02poli027 kernel: [   21.834080] sd 4:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 18 11:29:08 Cas02poli027 kernel: [   21.834092] sd 4:0:0:0: [sda] Write Protect is off
Apr 18 11:29:08 Cas02poli027 kernel: [   21.834107] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 18 11:29:08 Cas02poli027 kernel: [   21.834157] sd 4:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 18 11:29:08 Cas02poli027 kernel: [   21.834165] sd 4:0:0:0: [sda] Write Protect is off
Apr 18 11:29:08 Cas02poli027 kernel: [   21.834178] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 18 11:29:08 Cas02poli027 kernel: [   21.834182]  sda: sda1 sda2 < sda5 >
Apr 18 11:29:08 Cas02poli027 kernel: [   21.865395] sd 4:0:0:0: [sda] Attached SCSI disk
Apr 18 11:29:08 Cas02poli027 kernel: [   21.869034] sd 4:0:0:0: Attached scsi generic sg0 type 0
Apr 18 11:29:08 Cas02poli027 kernel: [   22.051279] Attempting manual resume
Apr 18 11:29:08 Cas02poli027 kernel: [   22.090403] kjournald starting.  Commit interval 5 seconds
Apr 18 11:29:08 Cas02poli027 kernel: [   22.090415] EXT3-fs: mounted filesystem with ordered data mode.
Apr 18 11:29:08 Cas02poli027 kernel: [   27.187956] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 18 11:29:08 Cas02poli027 kernel: [   27.216260] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 18 11:29:08 Cas02poli027 kernel: [   27.251295] heci: Intel(R) AMT Management Interface - version 3.1.0.31
Apr 18 11:29:08 Cas02poli027 kernel: [   27.251298] heci: Copyright (c) 2003 - 2007 Intel Corporation.
Apr 18 11:29:08 Cas02poli027 kernel: [   27.251346] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 18 11:29:08 Cas02poli027 kernel: [   27.252256] heci: link layer has been established.
Apr 18 11:29:08 Cas02poli027 kernel: [   27.257864] Intel(R) PRO/1000 Network Driver - version 7.6.5-NAPI
Apr 18 11:29:08 Cas02poli027 kernel: [   27.257867] Copyright (c) 1999-2007 Intel Corporation.
Apr 18 11:29:08 Cas02poli027 kernel: [   27.273916] Linux agpgart interface v0.102 (c) Dave Jones
Apr 18 11:29:08 Cas02poli027 kernel: [   27.355486] heci: heci driver initialization successful.
Apr 18 11:29:08 Cas02poli027 kernel: [   27.355519] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 18 11:29:08 Cas02poli027 kernel: [   27.403029] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1c:c0:23:75:f3
Apr 18 11:29:08 Cas02poli027 kernel: [   27.472242] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Apr 18 11:29:08 Cas02poli027 kernel: [   27.472275] agpgart: Detected an Intel G33 Chipset.
Apr 18 11:29:08 Cas02poli027 kernel: [   27.472427] agpgart: Detected 7164K stolen memory.
Apr 18 11:29:08 Cas02poli027 kernel: [   27.486250] agpgart: AGP aperture is 256M @ 0x20000000
Apr 18 11:29:08 Cas02poli027 kernel: [   27.590151] 
Apr 18 11:29:08 Cas02poli027 kernel: [   27.590152] 
Apr 18 11:29:08 Cas02poli027 kernel: [   27.590154] ====================  GOLDEN Series Driver Module Install  =====================
Apr 18 11:29:08 Cas02poli027 kernel: [   27.590156] 
Apr 18 11:29:08 Cas02poli027 kernel: [   27.590157] GOLDEN Info : Loading Golden Series Board Driver Module
Apr 18 11:29:08 Cas02poli027 kernel: [   27.590159]                                                        -- Version: 1.08
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607302] ACPI: PCI interrupt for device 0000:07:00.0 disabled
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607311] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 21 (level, low) -> IRQ 21
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607315] 
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607316] GOLDEN Info : Found Golden 4037 Series 2 ports RS-232 Board,
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607318]               bus number:7, device number:0
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607319] 
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607323] ACPI: PCI interrupt for device 0000:07:01.0 disabled
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607328] ACPI: PCI Interrupt 0000:07:01.0[A] -> GSI 22 (level, low) -> IRQ 22
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607330] 
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607331] GOLDEN Info : Found Golden 4037 Series 2 ports RS-232 Board,
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607333]               bus number:7, device number:1
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607334] 
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607341] Trying to free nonexistent resource <0000000000001008-000000000000100f>
Apr 18 11:29:08 Cas02poli027 kernel: [   27.607361] ================================================================================
Apr 18 11:29:08 Cas02poli027 kernel: [   28.019025] input: PC Speaker as /class/input/input2
Apr 18 11:29:08 Cas02poli027 kernel: [   28.318259] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Apr 18 11:29:08 Cas02poli027 kernel: [   28.524636] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Apr 18 11:29:08 Cas02poli027 kernel: [   28.651886] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
Apr 18 11:29:08 Cas02poli027 kernel: [   28.725133] NET: Registered protocol family 10
Apr 18 11:29:08 Cas02poli027 kernel: [   28.725232] lo: Disabled Privacy Extensions
Apr 18 11:29:08 Cas02poli027 kernel: [   28.725302] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 18 11:29:08 Cas02poli027 kernel: [   29.047697] lp: driver loaded but no devices found
Apr 18 11:29:08 Cas02poli027 kernel: [   29.206637] Adding 1453840k swap on /dev/sda5.  Priority:-1 extents:1 across:1453840k
Apr 18 11:29:08 Cas02poli027 kernel: [   29.481990] EXT3 FS on sda1, internal journal
Apr 18 11:29:08 Cas02poli027 kernel: [   29.543495] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Apr 18 11:29:08 Cas02poli027 kernel: [   29.543500] e1000: eth0: e1000_watchdog_task: 10/100 speed: disabling TSO
Apr 18 11:29:08 Cas02poli027 kernel: [   29.543750] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 18 11:29:08 Cas02poli027 kernel: [   30.341174] No dock devices found.
Apr 18 11:29:08 Cas02poli027 kernel: [   30.496203] input: Power Button (FF) as /class/input/input4
Apr 18 11:29:08 Cas02poli027 kernel: [   30.499540] ACPI: Power Button (FF) [PWRF]
Apr 18 11:29:08 Cas02poli027 kernel: [   30.524719] input: Sleep Button (CM) as /class/input/input5
Apr 18 11:29:08 Cas02poli027 kernel: [   30.527998] ACPI: Sleep Button (CM) [SLPB]
Apr 18 11:29:08 Cas02poli027 kernel: [   31.542099] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr 18 11:29:08 Cas02poli027 kernel: [   31.542104] apm: overridden by ACPI.
Apr 18 11:29:09 Cas02poli027 kernel: [   31.821423] Failure registering capabilities with primary security module.
Apr 18 11:29:09 Cas02poli027 dhcdbd: Started up.
Apr 18 11:29:11 Cas02poli027 kernel: [   33.504820] [drm] Initialized drm 1.1.0 20060810
Apr 18 11:29:11 Cas02poli027 kernel: [   33.520180] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 18 11:29:11 Cas02poli027 kernel: [   33.522120] [drm] Initialized i915 1.6.0 20060119 on minor 0


```

here is /proc/ioports
```

0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-006f : keyboard
0070-0077 : rtc
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
03c0-03df : vga+
03f2-03f5 : floppy
03f7-03f7 : floppy DIR
03f8-03ff : serial
0400-047f : pnp 00:06
  0400-0403 : ACPI PM1a_EVT_BLK
  0404-0405 : ACPI PM1a_CNT_BLK
  0408-040b : ACPI PM_TMR
  0410-0415 : ACPI CPU throttle
  0420-042f : ACPI GPE0_BLK
  0450-0450 : ACPI PM2_CNT_BLK
0500-053f : pnp 00:06
0680-06ff : pnp 00:06
0cf8-0cff : PCI conf1
1000-1fff : PCI Bus #07
  1000-101f : 0000:07:01.0
    1000-1007 : snx_golden
    1008-100f : snx_golden
  1020-103f : 0000:07:00.0
    1020-1027 : snx_golden
    1028-102f : snx_golden
2000-2fff : PCI Bus #03
  2000-200f : 0000:03:00.0
    2000-200f : libata
  2010-2017 : 0000:03:00.0
  2018-201f : 0000:03:00.0
    2018-201f : libata
  2020-2023 : 0000:03:00.0
  2024-2027 : 0000:03:00.0
    2024-2027 : libata
3000-301f : 0000:00:1f.3
3020-303f : 0000:00:19.0
  3020-303f : e1000-ich9
3040-304f : 0000:00:1f.5
3050-305f : 0000:00:1f.5
  3050-305f : libata
3060-306f : 0000:00:1f.2
3070-307f : 0000:00:1f.2
  3070-307f : libata
3080-3087 : 0000:00:1f.5
  3080-3087 : libata
3088-308f : 0000:00:1f.5
  3088-308f : libata
3090-3097 : 0000:00:1f.2
  3090-3097 : libata
3098-309f : 0000:00:1f.2
  3098-309f : libata
30a0-30a7 : 0000:00:02.0
30a8-30ab : 0000:00:1f.5
  30a8-30ab : libata
30ac-30af : 0000:00:1f.5
  30ac-30af : libata
30b0-30b3 : 0000:00:1f.2
  30b0-30b3 : libata
30b4-30b7 : 0000:00:1f.2
  30b4-30b7 : libata

```

and lspci -vvn output
```

00:00.0 0600: 8086:29c0 (rev 02)
	Subsystem: 8086:5044
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 0300: 8086:29c2 (rev 02) (prog-if 00 [VGA])
	Subsystem: 8086:5044
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at 30300000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at 3460 [size=8]
	Region 2: Memory at 20000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at 30200000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:03.0 0780: 8086:29c4 (rev 02)
	Subsystem: 8086:5044
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at 303a5900 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [8c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000

00:19.0 0200: 8086:294c (rev 02)
	Subsystem: 8086:0001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at 30380000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at 303a4000 (32-bit, non-prefetchable) [size=4K]
	Region 2: I/O ports at 30e0 [size=32]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [e0] Vendor Specific Information

00:1a.0 0c03: 8086:2937 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 8086:5044
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 4: I/O ports at 30c0 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1a.1 0c03: 8086:2938 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 8086:5044
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at 30a0 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1a.2 0c03: 8086:2939 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 8086:5044
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 16
	Region 4: I/O ports at 3080 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1a.7 0c03: 8086:293c (rev 02) (prog-if 20 [EHCI])
	Subsystem: 8086:5044
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 16
	Region 0: Memory at 303a5400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port
	Capabilities: [98] Vendor Specific Information

00:1b.0 0403: 8086:293e (rev 02)
	Subsystem: 8086:0001
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at 303a0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express Unknown type IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
		Link: Latency L0s <64ns, L1 <1us
		Link: ASPM Disabled CommClk- ExtSynch-
		Link: Speed unknown, Width x0

00:1c.0 0604: 8086:2940 (rev 02) (prog-if 00 [Normal decode])
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 1
		Link: Latency L0s <1us, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x0
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 1, PowerLimit 10.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [90] Subsystem: 8086:2940
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.1 0604: 8086:2942 (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 30100000-301fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 2
		Link: Latency L0s <256ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 2, PowerLimit 10.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [90] Subsystem: 8086:2942
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.2 0604: 8086:2944 (rev 02) (prog-if 00 [Normal decode])
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 3
		Link: Latency L0s <1us, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x0
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 3, PowerLimit 10.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [90] Subsystem: 8086:2944
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.3 0604: 8086:2946 (rev 02) (prog-if 00 [Normal decode])
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 4
		Link: Latency L0s <1us, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x0
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 4, PowerLimit 10.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [90] Subsystem: 8086:2946
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.4 0604: 8086:2948 (rev 02) (prog-if 00 [Normal decode])
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 5
		Link: Latency L0s <1us, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x0
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 5, PowerLimit 10.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [90] Subsystem: 8086:2948
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1d.0 0c03: 8086:2934 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 8086:5044
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 22
	Region 4: I/O ports at 3060 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1d.1 0c03: 8086:2935 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 8086:5044
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at 3040 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1d.2 0c03: 8086:2936 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 8086:5044
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 3020 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1d.7 0c03: 8086:293a (rev 02) (prog-if 20 [EHCI])
	Subsystem: 8086:5044
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at 303a5000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port
	Capabilities: [98] Vendor Specific Information

00:1e.0 0604: 8086:244e (rev 92) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 30000000-300fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [50] Subsystem: 8086:5044

00:1f.0 0601: 8086:2912 (rev 02)
	Subsystem: 8086:5044
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information

00:1f.2 0101: 8086:2920 (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: 8086:5044
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at 3458 [size=8]
	Region 1: I/O ports at 3474 [size=4]
	Region 2: I/O ports at 3450 [size=8]
	Region 3: I/O ports at 3470 [size=4]
	Region 4: I/O ports at 3430 [size=16]
	Region 5: I/O ports at 3420 [size=16]
	Capabilities: [70] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] Vendor Specific Information

00:1f.3 0c05: 8086:2930 (rev 02)
	Subsystem: 8086:5044
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at 303a5800 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 3000 [size=32]

00:1f.5 0101: 8086:2926 (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: 8086:5044
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at 3448 [size=8]
	Region 1: I/O ports at 346c [size=4]
	Region 2: I/O ports at 3440 [size=8]
	Region 3: I/O ports at 3468 [size=4]
	Region 4: I/O ports at 3410 [size=16]
	Region 5: I/O ports at 3400 [size=16]
	Capabilities: [70] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] Vendor Specific Information

02:00.0 0101: 11ab:6101 (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: 11ab:6101
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 2018 [size=8]
	Region 1: I/O ports at 2024 [size=4]
	Region 2: I/O ports at 2010 [size=8]
	Region 3: I/O ports at 2020 [size=4]
	Region 4: I/O ports at 2000 [size=16]
	Region 5: Memory at 30100000 (32-bit, non-prefetchable) [size=512]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [e0] Express Legacy Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr+ NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0
		Link: Latency L0s <256ns, L1 unlimited
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1

06:00.0 0700: 1409:7168 (rev 01) (prog-if 02 [16550])
	Subsystem: 1409:4037
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at 1020 [size=32]

06:01.0 0700: 1409:7168 (rev 01) (prog-if 02 [16550])
	Subsystem: 1409:4037
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 21
	Region 0: I/O ports at 1000 [size=32]

06:03.0 0c00: 104c:8023 (prog-if 10 [OHCI])
	Subsystem: 8086:5044
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at 30004000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at 30000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+

```

please help me, thank you very much.

bye

---

