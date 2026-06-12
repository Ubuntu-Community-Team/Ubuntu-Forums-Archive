---
title: "clean install problem, gets past splash but not to login"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by boyofford on 2008-08-07
Hi, 
just thought i'd tidy up my computer and do a clean re-install of vista and re-install of ubuntu-studio on my dell 530s.
Wanted to get rid of recovery partition and try out newer 8.04.1 ubuntu-studio 64-bit.

But it has all gone horribly and stupidly wrong!:confused:
vista is working but ubuntu can only get past splash and not to login, just freezes. have tried to reinstall 8.04.1 ubuntu-studio 64bit at least ten times each time end up with this same problem,
have tried to reinstall 7.10 ubuntu-studio 64bit gutsy (which had working before i started all this and had reinstalled before no problem) but get this same strange problem!
and have even tried a standard gutsy 32-bit version and end up with same problem!!!

what am i missing in all this, hopefully something simple!

hope this is a red-herring but did upgrade the bios on this computer recently, could this be cause? :confused:

my syslog looks like this for latest re-install(32bit gutsy)
```

Aug  7 20:13:44 rich-desktop syslogd 1.4.1#21ubuntu3: restart.
Aug  7 20:13:45 rich-desktop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Aug  7 20:13:45 rich-desktop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Aug  7 20:13:45 rich-desktop kernel: Symbols match kernel version 2.6.22.
Aug  7 20:13:45 rich-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe90000 (usable)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]  BIOS-e820: 000000007fe90000 - 000000007fee3000 (ACPI NVS)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] 896MB LOWMEM available.
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] found SMP MP-table at 000f3f00
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 523920) 0 entries of 256 used
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Zone PFN ranges:
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   DMA             0 ->     4096
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   HighMem    229376 ->   523920
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]     0:        0 ->   523920
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] On node 0 totalpages: 523920
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug  7 20:13:45 rich-desktop kernel: [    0.000000]   HighMem zone: 292243 pages, LIFO batch:31
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] DMI 2.5 present.
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F97A0 checksum 0
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: RSDP 000F97A0, 0024 (r2 DELL  )
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: XSDT 7FEE3080, 005C (r1 DELL    FX09    42302E31 AWRD        0)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: FACP 7FEE7200, 00F4 (r3 DELL    FX09    42302E31 AWRD        0)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: DSDT 7FEE3200, 3FFC (r1 DELL   AWRDACPI     1000 MSFT  3000000)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: FACS 7FE90000, 0040
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: HPET 7FEE73C0, 0038 (r1 DELL    FX09    42302E31 AWRD       98)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: MCFG 7FEE7400, 003C (r1 DELL    FX09    42302E31 AWRD        0)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: SLIC 7FEE7440, 0176 (r1 DELL    FX09    42302E31 AWRD        0)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: DMY2 7FEE75C0, 0080 (r1 DELL    FX09    42302E31 AWRD        0)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: APIC 7FEE7300, 0084 (r1 DELL    FX09    42302E31 AWRD        0)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: SSDT 7FEE7CA0, 0380 (r1  PmRef    CpuPm     3000 INTL 20041203)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Built 1 zonelists.  Total pages: 519827
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Kernel command line: root=UUID=b38c49eb-85ab-4c43-8e5a-3d09df42739b ro quiet splash
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Initializing CPU#0
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug  7 20:13:45 rich-desktop kernel: [    0.000000] Detected 2992.647 MHz processor.
Aug  7 20:13:45 rich-desktop kernel: [   18.790140] Console: colour VGA+ 80x25
Aug  7 20:13:45 rich-desktop kernel: [   18.790283] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug  7 20:13:45 rich-desktop kernel: [   18.790445] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug  7 20:13:45 rich-desktop kernel: [   18.840477] Memory: 2065960k/2095680k available (2015k kernel code, 28476k reserved, 916k data, 364k init, 1178176k highmem)
Aug  7 20:13:45 rich-desktop kernel: [   18.840482] virtual kernel memory layout:
Aug  7 20:13:45 rich-desktop kernel: [   18.840483]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Aug  7 20:13:45 rich-desktop kernel: [   18.840484]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug  7 20:13:45 rich-desktop kernel: [   18.840484]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug  7 20:13:45 rich-desktop kernel: [   18.840485]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug  7 20:13:45 rich-desktop kernel: [   18.840486]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Aug  7 20:13:45 rich-desktop kernel: [   18.840486]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Aug  7 20:13:45 rich-desktop kernel: [   18.840487]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Aug  7 20:13:45 rich-desktop kernel: [   18.840489] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug  7 20:13:45 rich-desktop kernel: [   18.840512] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug  7 20:13:45 rich-desktop kernel: [   18.840596] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug  7 20:13:45 rich-desktop kernel: [   18.840600] hpet0: 4 64-bit timers, 14318180 Hz
Aug  7 20:13:45 rich-desktop kernel: [   18.921566] Calibrating delay using timer specific routine.. 5988.90 BogoMIPS (lpj=11977800)
Aug  7 20:13:45 rich-desktop kernel: [   18.921580] Security Framework v1.0.0 initialized
Aug  7 20:13:45 rich-desktop kernel: [   18.921584] SELinux:  Disabled at boot.
Aug  7 20:13:45 rich-desktop kernel: [   18.921592] Mount-cache hash table entries: 512
Aug  7 20:13:45 rich-desktop kernel: [   18.921668] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001
Aug  7 20:13:45 rich-desktop kernel: [   18.921672] monitor/mwait feature present.
Aug  7 20:13:45 rich-desktop kernel: [   18.921673] using mwait in idle threads.
Aug  7 20:13:45 rich-desktop kernel: [   18.921676] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  7 20:13:45 rich-desktop kernel: [   18.921677] CPU: L2 cache: 4096K
Aug  7 20:13:45 rich-desktop kernel: [   18.921679] CPU: Physical Processor ID: 0
Aug  7 20:13:45 rich-desktop kernel: [   18.921680] CPU: Processor Core ID: 0
Aug  7 20:13:45 rich-desktop kernel: [   18.921681] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001
Aug  7 20:13:45 rich-desktop kernel: [   18.921686] Compat vDSO mapped to ffffe000.
Aug  7 20:13:45 rich-desktop kernel: [   18.921694] Checking 'hlt' instruction... OK.
Aug  7 20:13:45 rich-desktop kernel: [   18.937639] SMP alternatives: switching to UP code
Aug  7 20:13:45 rich-desktop kernel: [   18.937917] Early unpacking initramfs... done
Aug  7 20:13:45 rich-desktop kernel: [   19.127440] ACPI: Core revision 20070126
Aug  7 20:13:45 rich-desktop kernel: [   19.127465] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug  7 20:13:45 rich-desktop kernel: [   19.183900] CPU0: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
Aug  7 20:13:45 rich-desktop kernel: [   19.183909] SMP alternatives: switching to SMP code
Aug  7 20:13:45 rich-desktop kernel: [   19.183957] Booting processor 1/1 eip 3000
Aug  7 20:13:45 rich-desktop kernel: [   19.194174] Initializing CPU#1
Aug  7 20:13:45 rich-desktop kernel: [   19.273366] Calibrating delay using timer specific routine.. 5984.98 BogoMIPS (lpj=11969974)
Aug  7 20:13:45 rich-desktop kernel: [   19.273370] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001
Aug  7 20:13:45 rich-desktop kernel: [   19.273373] monitor/mwait feature present.
Aug  7 20:13:45 rich-desktop kernel: [   19.273375] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  7 20:13:45 rich-desktop kernel: [   19.273376] CPU: L2 cache: 4096K
Aug  7 20:13:45 rich-desktop kernel: [   19.273377] CPU: Physical Processor ID: 0
Aug  7 20:13:45 rich-desktop kernel: [   19.273378] CPU: Processor Core ID: 1
Aug  7 20:13:45 rich-desktop kernel: [   19.273379] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001
Aug  7 20:13:45 rich-desktop kernel: [   19.273890] CPU1: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
Aug  7 20:13:45 rich-desktop kernel: [   19.273903] Total of 2 processors activated (11973.88 BogoMIPS).
Aug  7 20:13:45 rich-desktop kernel: [   19.274038] ENABLING IO-APIC IRQs
Aug  7 20:13:45 rich-desktop kernel: [   19.274194] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  7 20:13:45 rich-desktop kernel: [   19.669146] APIC calibration not consistent with PM Timer: 347ms instead of 100ms
Aug  7 20:13:45 rich-desktop kernel: [   19.669147] APIC delta adjusted to PM-Timer: 2078122 (7231785)
Aug  7 20:13:45 rich-desktop kernel: [   19.669204] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug  7 20:13:45 rich-desktop kernel: [   19.689203] Brought up 2 CPUs
Aug  7 20:13:45 rich-desktop kernel: [   19.745131] migration_cost=27
Aug  7 20:13:45 rich-desktop kernel: [   19.745213] Booting paravirtualized kernel on bare hardware
Aug  7 20:13:45 rich-desktop kernel: [   19.745258] Time: 20:13:34  Date: 07/07/108
Aug  7 20:13:45 rich-desktop kernel: [   19.745270] NET: Registered protocol family 16
Aug  7 20:13:45 rich-desktop kernel: [   19.745323] EISA bus registered
Aug  7 20:13:45 rich-desktop kernel: [   19.745325] ACPI: bus type pci registered
Aug  7 20:13:45 rich-desktop kernel: [   19.779058] PCI: PCI BIOS revision 3.00 entry at 0xfba00, last bus=2
Aug  7 20:13:45 rich-desktop kernel: [   19.779059] PCI: Using configuration type 1
Aug  7 20:13:45 rich-desktop kernel: [   19.779060] Setting up standard PCI resources
Aug  7 20:13:45 rich-desktop kernel: [   19.780451] ACPI: EC: Look up EC in DSDT
Aug  7 20:13:45 rich-desktop kernel: [   19.782640] ACPI: Interpreter enabled
Aug  7 20:13:45 rich-desktop kernel: [   19.782641] ACPI: (supports S0 S3 S4 S5)
Aug  7 20:13:45 rich-desktop kernel: [   19.782650] ACPI: Using IOAPIC for interrupt routing
Aug  7 20:13:45 rich-desktop kernel: [   19.785481] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  7 20:13:45 rich-desktop kernel: [   19.785487] PCI: Probing PCI hardware (bus 00)
Aug  7 20:13:45 rich-desktop kernel: [   19.786197] PCI: Transparent bridge - 0000:00:1e.0
Aug  7 20:13:45 rich-desktop kernel: [   19.786219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug  7 20:13:45 rich-desktop kernel: [   19.786316] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Aug  7 20:13:45 rich-desktop kernel: [   19.795025] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Aug  7 20:13:45 rich-desktop kernel: [   19.795088] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Aug  7 20:13:45 rich-desktop kernel: [   19.795151] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Aug  7 20:13:45 rich-desktop kernel: [   19.795213] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Aug  7 20:13:45 rich-desktop kernel: [   19.795275] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Aug  7 20:13:45 rich-desktop kernel: [   19.795337] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Aug  7 20:13:45 rich-desktop kernel: [   19.795398] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 7 9 10 11 12 14 15)
Aug  7 20:13:45 rich-desktop kernel: [   19.795460] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 *4 5 7 9 10 11 12 14 15)
Aug  7 20:13:45 rich-desktop kernel: [   19.795520] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug  7 20:13:45 rich-desktop kernel: [   19.795525] pnp: PnP ACPI init
Aug  7 20:13:45 rich-desktop kernel: [   19.795532] ACPI: bus type pnp registered
Aug  7 20:13:45 rich-desktop kernel: [   19.796613] pnp: PnP ACPI: found 12 devices
Aug  7 20:13:45 rich-desktop kernel: [   19.796614] ACPI: ACPI bus type pnp unregistered
Aug  7 20:13:45 rich-desktop kernel: [   19.796616] PnPBIOS: Disabled by ACPI PNP
Aug  7 20:13:45 rich-desktop kernel: [   19.796641] PCI: Using ACPI for IRQ routing
Aug  7 20:13:45 rich-desktop kernel: [   19.796642] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug  7 20:13:45 rich-desktop kernel: [   19.808948] NET: Registered protocol family 8
Aug  7 20:13:45 rich-desktop kernel: [   19.808949] NET: Registered protocol family 20
Aug  7 20:13:45 rich-desktop kernel: [   19.808978] pnp: 00:08: ioport range 0x400-0x4bf has been reserved
Aug  7 20:13:45 rich-desktop kernel: [   19.808981] pnp: 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
Aug  7 20:13:45 rich-desktop kernel: [   19.808984] pnp: 00:0b: iomem range 0xf0000-0xfffff could not be reserved
Aug  7 20:13:45 rich-desktop kernel: [   19.808986] pnp: 00:0b: iomem range 0x7ff00000-0x7fffffff has been reserved
Aug  7 20:13:45 rich-desktop kernel: [   19.808987] pnp: 00:0b: iomem range 0xfed00000-0xfed000ff could not be reserved
Aug  7 20:13:45 rich-desktop kernel: [   19.808989] pnp: 00:0b: iomem range 0x7fe90000-0x7fefffff could not be reserved
Aug  7 20:13:45 rich-desktop kernel: [   19.809073] Time: tsc clocksource has been installed.
Aug  7 20:13:45 rich-desktop kernel: [   19.809078] Switched to high resolution mode on CPU 0
Aug  7 20:13:45 rich-desktop kernel: [   19.809132] Switched to high resolution mode on CPU 1
Aug  7 20:13:45 rich-desktop kernel: [   19.839150] PCI: Bridge: 0000:00:01.0
Aug  7 20:13:45 rich-desktop kernel: [   19.839151]   IO window: c000-cfff
Aug  7 20:13:45 rich-desktop kernel: [   19.839154]   MEM window: f8000000-fbffffff
Aug  7 20:13:45 rich-desktop kernel: [   19.839155]   PREFETCH window: d0000000-dfffffff
Aug  7 20:13:45 rich-desktop kernel: [   19.839158] PCI: Bridge: 0000:00:1e.0
Aug  7 20:13:45 rich-desktop kernel: [   19.839159]   IO window: d000-dfff
Aug  7 20:13:45 rich-desktop kernel: [   19.839162]   MEM window: fde00000-fdefffff
Aug  7 20:13:45 rich-desktop kernel: [   19.839165]   PREFETCH window: fdd00000-fddfffff
Aug  7 20:13:45 rich-desktop kernel: [   19.839173] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug  7 20:13:45 rich-desktop kernel: [   19.839177] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug  7 20:13:45 rich-desktop kernel: [   19.839183] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Aug  7 20:13:45 rich-desktop kernel: [   19.839189] NET: Registered protocol family 2
Aug  7 20:13:45 rich-desktop kernel: [   19.889028] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug  7 20:13:45 rich-desktop kernel: [   19.889062] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Aug  7 20:13:45 rich-desktop kernel: [   19.889495] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug  7 20:13:45 rich-desktop kernel: [   19.889621] TCP: Hash tables configured (established 131072 bind 65536)
Aug  7 20:13:45 rich-desktop kernel: [   19.889623] TCP reno registered
Aug  7 20:13:45 rich-desktop kernel: [   19.905097] checking if image is initramfs... it is
Aug  7 20:13:45 rich-desktop kernel: [   20.278904] Freeing initrd memory: 7353k freed
Aug  7 20:13:45 rich-desktop kernel: [   20.279250] audit: initializing netlink socket (disabled)
Aug  7 20:13:45 rich-desktop kernel: [   20.279261] audit(1218140013.544:1): initialized
Aug  7 20:13:45 rich-desktop kernel: [   20.279314] highmem bounce pool size: 64 pages
Aug  7 20:13:45 rich-desktop kernel: [   20.280315] VFS: Disk quotas dquot_6.5.1
Aug  7 20:13:45 rich-desktop kernel: [   20.280338] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug  7 20:13:45 rich-desktop kernel: [   20.280387] io scheduler noop registered
Aug  7 20:13:45 rich-desktop kernel: [   20.280388] io scheduler anticipatory registered
Aug  7 20:13:45 rich-desktop kernel: [   20.280389] io scheduler deadline registered
Aug  7 20:13:45 rich-desktop kernel: [   20.280397] io scheduler cfq registered (default)
Aug  7 20:13:45 rich-desktop kernel: [   20.280494] Boot video device is 0000:01:00.0
Aug  7 20:13:45 rich-desktop kernel: [   20.280535] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug  7 20:13:45 rich-desktop kernel: [   20.280555] assign_interrupt_mode Found MSI capability
Aug  7 20:13:45 rich-desktop kernel: [   20.280557] Allocate Port Service[0000:00:01.0:pcie00]
Aug  7 20:13:45 rich-desktop kernel: [   20.280633] isapnp: Scanning for PnP cards...
Aug  7 20:13:45 rich-desktop kernel: [   20.633218] isapnp: No Plug & Play device found
Aug  7 20:13:45 rich-desktop kernel: [   20.643780] Real Time Clock Driver v1.12ac
Aug  7 20:13:45 rich-desktop kernel: [   20.643882] hpet_resources: 0xfed00000 is busy
Aug  7 20:13:45 rich-desktop kernel: [   20.643906] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug  7 20:13:45 rich-desktop kernel: [   20.644461] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug  7 20:13:45 rich-desktop kernel: [   20.644531] input: Macintosh mouse button emulation as /class/input/input0
Aug  7 20:13:45 rich-desktop kernel: [   20.644595] PNP: No PS/2 controller found. Probing ports directly.
Aug  7 20:13:45 rich-desktop kernel: [   20.644852] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  7 20:13:45 rich-desktop kernel: [   20.644856] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug  7 20:13:45 rich-desktop kernel: [   20.644931] mice: PS/2 mouse device common for all mice
Aug  7 20:13:45 rich-desktop kernel: [   20.645003] EISA: Probing bus 0 at eisa.0
Aug  7 20:13:45 rich-desktop kernel: [   20.645028] EISA: Detected 0 cards.
Aug  7 20:13:45 rich-desktop kernel: [   20.645088] TCP cubic registered
Aug  7 20:13:45 rich-desktop kernel: [   20.645097] NET: Registered protocol family 1
Aug  7 20:13:45 rich-desktop kernel: [   20.645112] Using IPI No-Shortcut mode
Aug  7 20:13:45 rich-desktop kernel: [   20.645205]   Magic number: 4:826:244
Aug  7 20:13:45 rich-desktop kernel: [   20.645212]   hash matches device ttyw0
Aug  7 20:13:45 rich-desktop kernel: [   20.645352] Freeing unused kernel memory: 364k freed
Aug  7 20:13:45 rich-desktop kernel: [   21.757047] AppArmor: AppArmor initialized<5>audit(1218140015.044:2):  type=1505 info="AppArmor initialized" pid=1215
Aug  7 20:13:45 rich-desktop kernel: [   21.761193] fuse init (API version 7.8)
Aug  7 20:13:45 rich-desktop kernel: [   21.763525] Failure registering capabilities with primary security module.
Aug  7 20:13:45 rich-desktop kernel: [   21.789779] ACPI: Fan [FAN] (on)
Aug  7 20:13:45 rich-desktop kernel: [   21.792021] ACPI: SSDT 7FEE7680, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
Aug  7 20:13:45 rich-desktop kernel: [   21.792169] ACPI: SSDT 7FEE7B40, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
Aug  7 20:13:45 rich-desktop kernel: [   21.792239] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug  7 20:13:45 rich-desktop kernel: [   21.792244] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug  7 20:13:45 rich-desktop kernel: [   21.792823] ACPI: Thermal Zone [THRM] (40 C)
Aug  7 20:13:45 rich-desktop kernel: [   22.008338] usbcore: registered new interface driver usbfs
Aug  7 20:13:45 rich-desktop kernel: [   22.008352] usbcore: registered new interface driver hub
Aug  7 20:13:45 rich-desktop kernel: [   22.008363] usbcore: registered new device driver usb
Aug  7 20:13:45 rich-desktop kernel: [   22.008757] USB Universal Host Controller Interface driver v3.0
Aug  7 20:13:45 rich-desktop kernel: [   22.008795] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug  7 20:13:45 rich-desktop kernel: [   22.008803] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Aug  7 20:13:45 rich-desktop kernel: [   22.008805] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Aug  7 20:13:45 rich-desktop kernel: [   22.008881] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Aug  7 20:13:45 rich-desktop kernel: [   22.008902] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fe00
Aug  7 20:13:45 rich-desktop kernel: [   22.008961] usb usb1: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   22.008975] hub 1-0:1.0: USB hub found
Aug  7 20:13:45 rich-desktop kernel: [   22.008977] hub 1-0:1.0: 2 ports detected
Aug  7 20:13:45 rich-desktop kernel: [   22.034448] SCSI subsystem initialized
Aug  7 20:13:45 rich-desktop kernel: [   22.037085] libata version 2.21 loaded.
Aug  7 20:13:45 rich-desktop kernel: [   22.087454] FDC 0 is a post-1991 82077
Aug  7 20:13:45 rich-desktop kernel: [   22.112052] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 17
Aug  7 20:13:45 rich-desktop kernel: [   22.112059] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Aug  7 20:13:45 rich-desktop kernel: [   22.112062] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Aug  7 20:13:45 rich-desktop kernel: [   22.112129] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Aug  7 20:13:45 rich-desktop kernel: [   22.112151] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000fd00
Aug  7 20:13:45 rich-desktop kernel: [   22.112313] usb usb2: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   22.112383] hub 2-0:1.0: USB hub found
Aug  7 20:13:45 rich-desktop kernel: [   22.112386] hub 2-0:1.0: 2 ports detected
Aug  7 20:13:45 rich-desktop kernel: [   22.215974] ACPI: PCI Interrupt 0000:00:1a.2[D] -> GSI 19 (level, low) -> IRQ 18
Aug  7 20:13:45 rich-desktop kernel: [   22.215978] PCI: Setting latency timer of device 0000:00:1a.2 to 64
Aug  7 20:13:45 rich-desktop kernel: [   22.215981] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Aug  7 20:13:45 rich-desktop kernel: [   22.216050] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
Aug  7 20:13:45 rich-desktop kernel: [   22.216069] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fc00
Aug  7 20:13:45 rich-desktop kernel: [   22.216278] usb usb3: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   22.216372] hub 3-0:1.0: USB hub found
Aug  7 20:13:45 rich-desktop kernel: [   22.216375] hub 3-0:1.0: 2 ports detected
Aug  7 20:13:45 rich-desktop kernel: [   22.319994] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Aug  7 20:13:45 rich-desktop kernel: [   22.319999] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Aug  7 20:13:45 rich-desktop kernel: [   22.320002] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug  7 20:13:45 rich-desktop kernel: [   22.320100] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
Aug  7 20:13:45 rich-desktop kernel: [   22.320123] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000fb00
Aug  7 20:13:45 rich-desktop kernel: [   22.320360] usb usb4: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   22.320465] hub 4-0:1.0: USB hub found
Aug  7 20:13:45 rich-desktop kernel: [   22.320469] hub 4-0:1.0: 2 ports detected
Aug  7 20:13:45 rich-desktop kernel: [   22.423953] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
Aug  7 20:13:45 rich-desktop kernel: [   22.423958] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Aug  7 20:13:45 rich-desktop kernel: [   22.423960] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug  7 20:13:45 rich-desktop kernel: [   22.424074] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
Aug  7 20:13:45 rich-desktop kernel: [   22.424096] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000fa00
Aug  7 20:13:45 rich-desktop kernel: [   22.424374] usb usb5: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   22.424500] hub 5-0:1.0: USB hub found
Aug  7 20:13:45 rich-desktop kernel: [   22.424505] hub 5-0:1.0: 2 ports detected
Aug  7 20:13:45 rich-desktop kernel: [   22.459596] usb 2-2: new low speed USB device using uhci_hcd and address 2
Aug  7 20:13:45 rich-desktop kernel: [   22.527945] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Aug  7 20:13:45 rich-desktop kernel: [   22.527951] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Aug  7 20:13:45 rich-desktop kernel: [   22.527954] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug  7 20:13:45 rich-desktop kernel: [   22.528087] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
Aug  7 20:13:45 rich-desktop kernel: [   22.528113] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000f900
Aug  7 20:13:45 rich-desktop kernel: [   22.528427] usb usb6: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   22.528574] hub 6-0:1.0: USB hub found
Aug  7 20:13:45 rich-desktop kernel: [   22.528577] hub 6-0:1.0: 2 ports detected
Aug  7 20:13:45 rich-desktop kernel: [   22.631918] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
Aug  7 20:13:45 rich-desktop kernel: [   22.631926] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Aug  7 20:13:45 rich-desktop kernel: [   22.631928] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Aug  7 20:13:45 rich-desktop kernel: [   22.633074] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
Aug  7 20:13:45 rich-desktop kernel: [   22.633104] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Aug  7 20:13:45 rich-desktop kernel: [   22.633109] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfdffe000
Aug  7 20:13:45 rich-desktop kernel: [   22.636992] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug  7 20:13:45 rich-desktop kernel: [   22.637046] usb usb7: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   22.637067] hub 7-0:1.0: USB hub found
Aug  7 20:13:45 rich-desktop kernel: [   22.637072] hub 7-0:1.0: 6 ports detected
Aug  7 20:13:45 rich-desktop kernel: [   22.645876] usb 2-2: string descriptor 0 read error: -71
Aug  7 20:13:45 rich-desktop kernel: [   22.653873] usb 2-2: string descriptor 0 read error: -71
Aug  7 20:13:45 rich-desktop kernel: [   22.653931] usb 2-2: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   22.657871] usb 2-2: can't set config #1, error -71
Aug  7 20:13:45 rich-desktop kernel: [   22.739527] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Aug  7 20:13:45 rich-desktop kernel: [   22.739539] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Aug  7 20:13:45 rich-desktop kernel: [   22.739541] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug  7 20:13:45 rich-desktop kernel: [   22.739559] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
Aug  7 20:13:45 rich-desktop kernel: [   22.739588] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Aug  7 20:13:45 rich-desktop kernel: [   22.739592] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfdffd000
Aug  7 20:13:45 rich-desktop kernel: [   22.743472] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug  7 20:13:45 rich-desktop kernel: [   22.743527] usb usb8: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   22.743545] hub 8-0:1.0: USB hub found
Aug  7 20:13:45 rich-desktop kernel: [   22.743550] hub 8-0:1.0: 6 ports detected
Aug  7 20:13:45 rich-desktop kernel: [   22.847517] ata_piix 0000:00:1f.2: version 2.11
Aug  7 20:13:45 rich-desktop kernel: [   22.847523] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Aug  7 20:13:45 rich-desktop kernel: [   22.847540] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 18
Aug  7 20:13:45 rich-desktop kernel: [   22.847564] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Aug  7 20:13:45 rich-desktop kernel: [   22.847603] scsi0 : ata_piix
Aug  7 20:13:45 rich-desktop kernel: [   22.847623] scsi1 : ata_piix
Aug  7 20:13:45 rich-desktop kernel: [   22.847676] ata1: SATA max UDMA/133 cmd 0x0001f800 ctl 0x0001f702 bmdma 0x0001f400 irq 18
Aug  7 20:13:45 rich-desktop kernel: [   22.847678] ata2: SATA max UDMA/133 cmd 0x0001f600 ctl 0x0001f502 bmdma 0x0001f408 irq 18
Aug  7 20:13:45 rich-desktop kernel: [   22.911374] usb 2-2: USB disconnect, address 2
Aug  7 20:13:45 rich-desktop kernel: [   23.052430] ata1.00: ATA-7: ST3320620AS, 3.ADG, max UDMA/133
Aug  7 20:13:45 rich-desktop kernel: [   23.052433] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Aug  7 20:13:45 rich-desktop kernel: [   23.119026] ata1.00: configured for UDMA/133
Aug  7 20:13:45 rich-desktop kernel: [   23.607130] ata2.00: ATAPI: PBDS DVD+/-RW DH-16W1S, 2D14, max UDMA/100
Aug  7 20:13:45 rich-desktop kernel: [   23.646937] usb 8-5: new high speed USB device using ehci_hcd and address 2
Aug  7 20:13:45 rich-desktop kernel: [   23.795018] ata2.00: configured for UDMA/100
Aug  7 20:13:45 rich-desktop kernel: [   23.795084] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AD PQ: 0 ANSI: 5
Aug  7 20:13:45 rich-desktop kernel: [   23.796000] scsi 1:0:0:0: CD-ROM            PBDS     DVD+-RW DH-16W1S 2D14 PQ: 0 ANSI: 5
Aug  7 20:13:45 rich-desktop kernel: [   23.796194] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
Aug  7 20:13:45 rich-desktop kernel: [   23.796208] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 18
Aug  7 20:13:45 rich-desktop kernel: [   23.796223] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Aug  7 20:13:45 rich-desktop kernel: [   23.796240] scsi2 : ata_piix
Aug  7 20:13:45 rich-desktop kernel: [   23.796312] scsi3 : ata_piix
Aug  7 20:13:45 rich-desktop kernel: [   23.796401] ata3: SATA max UDMA/133 cmd 0x0001f100 ctl 0x0001f002 bmdma 0x0001ed00 irq 18
Aug  7 20:13:45 rich-desktop kernel: [   23.796403] ata4: SATA max UDMA/133 cmd 0x0001ef00 ctl 0x0001ee02 bmdma 0x0001ed08 irq 18
Aug  7 20:13:45 rich-desktop kernel: [   23.837329] usb 8-5: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   24.074704] usb 2-2: new low speed USB device using uhci_hcd and address 3
Aug  7 20:13:45 rich-desktop kernel: [   24.131417] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Aug  7 20:13:45 rich-desktop kernel: [   24.131424] sd 0:0:0:0: [sda] Write Protect is off
Aug  7 20:13:45 rich-desktop kernel: [   24.131425] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  7 20:13:45 rich-desktop kernel: [   24.131433] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  7 20:13:45 rich-desktop kernel: [   24.131459] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Aug  7 20:13:45 rich-desktop kernel: [   24.131463] sd 0:0:0:0: [sda] Write Protect is off
Aug  7 20:13:45 rich-desktop kernel: [   24.131464] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  7 20:13:45 rich-desktop kernel: [   24.131472] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  7 20:13:45 rich-desktop kernel: [   24.131474]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
Aug  7 20:13:45 rich-desktop kernel: [   24.180081] sd 0:0:0:0: [sda] Attached SCSI disk
Aug  7 20:13:45 rich-desktop kernel: [   24.181976] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug  7 20:13:45 rich-desktop kernel: [   24.181986] sr 1:0:0:0: Attached scsi generic sg1 type 5
Aug  7 20:13:45 rich-desktop kernel: [   24.186426] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Aug  7 20:13:45 rich-desktop kernel: [   24.186427] Uniform CD-ROM driver Revision: 3.20
Aug  7 20:13:45 rich-desktop kernel: [   24.186522] sr 1:0:0:0: Attached scsi CD-ROM sr0
Aug  7 20:13:45 rich-desktop kernel: [   24.282031] usb 2-2: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   24.495744] Attempting manual resume
Aug  7 20:13:45 rich-desktop kernel: [   24.495746] swsusp: Resume From Partition 8:6
Aug  7 20:13:45 rich-desktop kernel: [   24.495747] PM: Checking swsusp image.
Aug  7 20:13:45 rich-desktop kernel: [   24.495902] PM: Resume from disk failed.
Aug  7 20:13:45 rich-desktop kernel: [   24.526432] kjournald starting.  Commit interval 5 seconds
Aug  7 20:13:45 rich-desktop kernel: [   24.526464] EXT3-fs: mounted filesystem with ordered data mode.
Aug  7 20:13:45 rich-desktop kernel: [   24.558428] usb 3-2: new low speed USB device using uhci_hcd and address 2
Aug  7 20:13:45 rich-desktop kernel: [   24.733761] usb 3-2: configuration #1 chosen from 1 choice
Aug  7 20:13:45 rich-desktop kernel: [   24.736788] usbcore: registered new interface driver hiddev
Aug  7 20:13:45 rich-desktop kernel: [   24.768882] input: Dell Dell USB Keyboard as /class/input/input1
Aug  7 20:13:45 rich-desktop kernel: [   24.768887] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.1-2
Aug  7 20:13:45 rich-desktop kernel: [   24.768897] usbcore: registered new interface driver libusual
Aug  7 20:13:45 rich-desktop kernel: [   24.781802] input: Dell Dell USB Optical Mouse as /class/input/input2
Aug  7 20:13:45 rich-desktop kernel: [   24.781816] input: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1a.2-2
Aug  7 20:13:45 rich-desktop kernel: [   24.781823] usbcore: registered new interface driver usbhid
Aug  7 20:13:45 rich-desktop kernel: [   24.781825] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug  7 20:13:45 rich-desktop kernel: [   25.108043] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug  7 20:13:45 rich-desktop kernel: [   25.108046] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug  7 20:13:45 rich-desktop kernel: [   25.153740] Initializing USB Mass Storage driver...
Aug  7 20:13:45 rich-desktop kernel: [   25.153773] scsi4 : SCSI emulation for USB Mass Storage devices
Aug  7 20:13:45 rich-desktop kernel: [   25.153797] usb-storage: device found at 2
Aug  7 20:13:45 rich-desktop kernel: [   25.153798] usb-storage: waiting for device to settle before scanning
Aug  7 20:13:45 rich-desktop kernel: [   25.153801] usbcore: registered new interface driver usb-storage
Aug  7 20:13:45 rich-desktop kernel: [   25.153803] USB Mass Storage support registered.
Aug  7 20:13:45 rich-desktop kernel: [   28.268036] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  7 20:13:45 rich-desktop kernel: [   28.316882] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  7 20:13:45 rich-desktop kernel: [   28.389592] Linux agpgart interface v0.102 (c) Dave Jones
Aug  7 20:13:45 rich-desktop kernel: [   28.442358] Intel(R) PRO/1000 Network Driver - version 7.6.5-NAPI
Aug  7 20:13:45 rich-desktop kernel: [   28.442360] Copyright (c) 1999-2007 Intel Corporation.
Aug  7 20:13:45 rich-desktop kernel: [   28.442386] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 21
Aug  7 20:13:45 rich-desktop kernel: [   28.442395] PCI: Setting latency timer of device 0000:00:19.0 to 64
Aug  7 20:13:45 rich-desktop kernel: [   28.447554] input: PC Speaker as /class/input/input3
Aug  7 20:13:45 rich-desktop kernel: [   28.488874] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:a0:94:a7:c0
Aug  7 20:13:45 rich-desktop kernel: [   28.529753] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Aug  7 20:13:45 rich-desktop kernel: [   28.633741] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Aug  7 20:13:45 rich-desktop kernel: [   28.633754] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Aug  7 20:13:45 rich-desktop kernel: [   28.840029] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Aug  7 20:13:45 rich-desktop kernel: [   29.039485] lp: driver loaded but no devices found
Aug  7 20:13:45 rich-desktop kernel: [   29.063413] Adding 2000052k swap on /dev/sda6.  Priority:-1 extents:1 across:2000052k
Aug  7 20:13:45 rich-desktop kernel: [   29.368755] EXT3 FS on sda5, internal journal
Aug  7 20:13:45 rich-desktop kernel: [   29.851676] kjournald starting.  Commit interval 5 seconds
Aug  7 20:13:45 rich-desktop kernel: [   29.851798] EXT3 FS on sda7, internal journal
Aug  7 20:13:45 rich-desktop kernel: [   29.851802] EXT3-fs: mounted filesystem with ordered data mode.
Aug  7 20:13:45 rich-desktop kernel: [   30.153298] usb-storage: device scan complete
Aug  7 20:13:45 rich-desktop kernel: [   30.157547] scsi 4:0:0:0: Direct-Access     TEAC     USB   HS-CF Card 4.08 PQ: 0 ANSI: 0
Aug  7 20:13:45 rich-desktop kernel: [   30.161173] scsi 4:0:0:1: Direct-Access     TEAC     USB   HS-xD/SM   4.08 PQ: 0 ANSI: 0
Aug  7 20:13:45 rich-desktop kernel: [   30.164672] scsi 4:0:0:2: Direct-Access     TEAC     USB   HS-MS Card 4.08 PQ: 0 ANSI: 0
Aug  7 20:13:45 rich-desktop kernel: [   30.168046] scsi 4:0:0:3: Direct-Access     TEAC     USB   HS-SD Card 4.08 PQ: 0 ANSI: 0
Aug  7 20:13:45 rich-desktop kernel: [   30.172310] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Aug  7 20:13:45 rich-desktop kernel: [   30.172337] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug  7 20:13:45 rich-desktop kernel: [   30.176675] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Aug  7 20:13:45 rich-desktop kernel: [   30.176701] sd 4:0:0:1: Attached scsi generic sg3 type 0
Aug  7 20:13:45 rich-desktop kernel: [   30.181182] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Aug  7 20:13:45 rich-desktop kernel: [   30.181213] sd 4:0:0:2: Attached scsi generic sg4 type 0
Aug  7 20:13:45 rich-desktop kernel: [   30.185169] sd 4:0:0:3: [sde] Attached SCSI removable disk
Aug  7 20:13:45 rich-desktop kernel: [   30.185195] sd 4:0:0:3: Attached scsi generic sg5 type 0
Aug  7 20:13:45 rich-desktop kernel: [   30.518896] No dock devices found.
Aug  7 20:13:45 rich-desktop kernel: [   30.602960] input: Power Button (FF) as /class/input/input4
Aug  7 20:13:45 rich-desktop kernel: [   30.603036] ACPI: Power Button (FF) [PWRF]
Aug  7 20:13:45 rich-desktop kernel: [   30.615035] input: Power Button (CM) as /class/input/input5
Aug  7 20:13:45 rich-desktop kernel: [   30.615121] ACPI: Power Button (CM) [PWRB]
Aug  7 20:13:45 rich-desktop NetworkManager: <info>  starting... 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.482403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_29c0'). 
Aug  7 20:13:45 rich-desktop kernel: [   31.485542] ppdev: user-space parallel port driver
Aug  7 20:13:45 rich-desktop kernel: [   31.570020] audit(1218136425.340:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5024 profile="/usr/sbin/cupsd"
Aug  7 20:13:45 rich-desktop kernel: [   31.610520] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug  7 20:13:45 rich-desktop kernel: [   31.610523] apm: disabled - APM is not SMP safe.
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.656210] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_29c1'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.656790] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10de_423'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.657042] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_10c0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.657228] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2937'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.657458] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.657916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.658099] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2938'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.658278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.658455] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.658631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_2105_noserial'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.658808] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_2105_noserial_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.658987] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2939'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.659178] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_2'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.659355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_2_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.659535] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_3012_noserial'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.659719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_3012_noserial_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.660142] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293c'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.660329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.660574] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.660760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293e'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.660946] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2934'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.661130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.661356] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.661667] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2935'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.662111] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.662328] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.662517] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2936'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.662863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.691858] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.692076] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293a'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.692268] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.692457] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.692643] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.692829] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.693033] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0_scsi_host'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.693219] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0_scsi_host_scsi_device_lun0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.693401] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0_scsi_host_scsi_device_lun1'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.693589] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0_scsi_host_scsi_device_lun2'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.693769] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0_scsi_host_scsi_device_lun3'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.693948] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_244e'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.694127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2916'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.694305] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2920'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.694483] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.694668] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_device_lun0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.694847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.695025] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_0_scsi_device_lun0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.695202] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2930'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.695379] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2926'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.695557] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.695736] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.695913] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.696091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.696278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.696461] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.696643] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a08'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.696826] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.697017] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.697207] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.697440] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.697679] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.697909] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.698139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0700'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.698369] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.698596] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_INT0800'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.698823] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.699050] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.699285] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.699511] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_3012_noserial_if0_logicaldev_input'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.699740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.699966] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1a_a0_94_a7_c0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'e1000-ich9'. 
Aug  7 20:13:45 rich-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug  7 20:13:45 rich-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug  7 20:13:45 rich-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Aug  7 20:13:45 rich-desktop NetworkManager: <info>  Deactivating device eth0. 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.771303] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.771565] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2920_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.771784] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.771997] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.772211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0_scsi_host_scsi_device_lun2_scsi_generic'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.772433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_if0_scsi_host_scsi_device_lun3_scsi_generic'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.772642] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293e_oss_pcm_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.772849] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293e_alsa_control__1'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.773056] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293e_oss_pcm_0_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.773262] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293e_oss_mixer__1'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.773476] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293e_alsa_capture_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.773683] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293e_alsa_playback_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.773888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_293e_alsa_capture_2'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.774093] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.774305] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.774510] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.774715] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.774919] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_2105_noserial_if0_logicaldev_input'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.775127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.775331] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.775544] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.775770] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.775975] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.776184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_2105_noserial_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.776390] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_2_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.776594] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_3012_noserial_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.776807] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.777012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.777216] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.777420] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.777624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.777828] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_644_200_000005035E9C_usbraw'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.778039] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3320620AS_9QF7F3T9'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.778244] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_07D7_0A19'). 
Aug  7 20:13:45 rich-desktop kernel: [   31.766611] Failure registering capabilities with primary security module.
Aug  7 20:13:45 rich-desktop avahi-daemon[5219]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Aug  7 20:13:45 rich-desktop avahi-daemon[5219]: Successfully dropped root privileges.
Aug  7 20:13:45 rich-desktop avahi-daemon[5219]: avahi-daemon 0.6.20 starting up.
Aug  7 20:13:45 rich-desktop avahi-daemon[5219]: Successfully called chroot().
Aug  7 20:13:45 rich-desktop avahi-daemon[5219]: Successfully dropped remaining capabilities.
Aug  7 20:13:45 rich-desktop avahi-daemon[5219]: No service file found in /etc/avahi/services.
Aug  7 20:13:45 rich-desktop avahi-daemon[5219]: Network interface enumeration completed.
Aug  7 20:13:45 rich-desktop avahi-daemon[5219]: Registering HINFO record with values 'I686'/'LINUX'.
Aug  7 20:13:45 rich-desktop avahi-daemon[5219]: Server startup complete. Host name is rich-desktop.local. Local service cookie is 3217956932.
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.881752] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_547C37147C36EFFA'). 
Aug  7 20:13:45 rich-desktop dhcdbd: Started up.
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.918357] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.922037] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_b38c49eb_85ab_4c43_8e5a_3d09df42739b'). 
Aug  7 20:13:45 rich-desktop NetworkManager: <debug> [1218136425.925198] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_5bf41a49_ec6a_4ced_80ba_bb084a3f1cdc'). 
Aug  7 20:13:45 rich-desktop hcid[5258]: Bluetooth HCI daemon
Aug  7 20:13:45 rich-desktop kernel: [   31.945303] Bluetooth: Core ver 2.11
Aug  7 20:13:45 rich-desktop kernel: [   31.945403] NET: Registered protocol family 31
Aug  7 20:13:45 rich-desktop kernel: [   31.945405] Bluetooth: HCI device and connection manager initialized
Aug  7 20:13:45 rich-desktop kernel: [   31.945408] Bluetooth: HCI socket layer initialized
Aug  7 20:13:45 rich-desktop hcid[5258]: Starting SDP server
Aug  7 20:13:46 rich-desktop kernel: [   31.967689] Bluetooth: L2CAP ver 2.8
Aug  7 20:13:46 rich-desktop kernel: [   31.967692] Bluetooth: L2CAP socket layer initialized
Aug  7 20:13:46 rich-desktop hcid[5258]: Created local server at unix:abstract=/var/run/dbus-sriTX7YYHw,guid=9d6f8ff3d4af75cb40771800489b496a
Aug  7 20:13:46 rich-desktop NetworkManager: <debug> [1218136426.007948] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8411953a_25cc_4550_bfec_7c76d993db75'). 
Aug  7 20:13:46 rich-desktop input[5270]: Bluetooth Input daemon
Aug  7 20:13:46 rich-desktop input[5270]: Registered input manager path:/org/bluez/input
Aug  7 20:13:46 rich-desktop audio[5273]: Bluetooth Audio daemon
Aug  7 20:13:46 rich-desktop audio[5273]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Aug  7 20:13:46 rich-desktop audio[5273]: Unix socket created: 5
Aug  7 20:13:46 rich-desktop kernel: [   32.016855] Bluetooth: RFCOMM socket layer initialized
Aug  7 20:13:46 rich-desktop kernel: [   32.016864] Bluetooth: RFCOMM TTY layer initialized
Aug  7 20:13:46 rich-desktop kernel: [   32.016865] Bluetooth: RFCOMM ver 1.8
Aug  7 20:13:46 rich-desktop audio[5273]: add_service_record: got record id 0x10000
Aug  7 20:13:46 rich-desktop NetworkManager: <debug> [1218136426.057432] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_TEAC_USB_HS_CF_Card_000005035E9C_0_0'). 
Aug  7 20:13:46 rich-desktop audio[5273]: add_service_record: got record id 0x10001
Aug  7 20:13:46 rich-desktop audio[5273]: Registered manager path:/org/bluez/audio
Aug  7 20:13:46 rich-desktop NetworkManager: <debug> [1218136426.072352] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_TEAC_USB_HS_xD_SM_000005035E9C_0_1'). 
Aug  7 20:13:46 rich-desktop NetworkManager: <debug> [1218136426.086476] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_TEAC_USB_HS_MS_Card_000005035E9C_0_2'). 
Aug  7 20:13:46 rich-desktop NetworkManager: <debug> [1218136426.099090] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_TEAC_USB_HS_SD_Card_000005035E9C_0_3'). 
Aug  7 20:13:46 rich-desktop NetworkManager: <debug> [1218136426.120253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Aug  7 20:13:46 rich-desktop NetworkManager: <debug> [1218136426.124149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Aug  7 20:13:46 rich-desktop NetworkManager: <debug> [1218136426.124608] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_FAN'). 
Aug  7 20:13:46 rich-desktop NetworkManager: <debug> [1218136426.124934] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_DH_16W1S'). 
Aug  7 20:13:47 rich-desktop kernel: [   33.225889] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Aug  7 20:13:47 rich-desktop kernel: [   33.225893] e1000: eth0: e1000_watchdog_task: 10/100 speed: disabling TSO
Aug  7 20:13:47 rich-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Aug  7 20:13:47 rich-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Aug  7 20:13:48 rich-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) started... 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Aug  7 20:13:48 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Aug  7 20:13:48 rich-desktop anacron[5361]: Anacron 2.3 started on 2008-08-07
Aug  7 20:13:48 rich-desktop anacron[5361]: Will run job `cron.daily' in 5 min.
Aug  7 20:13:48 rich-desktop anacron[5361]: Will run job `cron.weekly' in 10 min.
Aug  7 20:13:48 rich-desktop anacron[5361]: Will run job `cron.monthly' in 15 min.
Aug  7 20:13:48 rich-desktop anacron[5361]: Jobs will be executed sequentially
Aug  7 20:13:48 rich-desktop /usr/sbin/cron[5388]: (CRON) INFO (pidfile fd = 3)
Aug  7 20:13:48 rich-desktop /usr/sbin/cron[5389]: (CRON) STARTUP (fork ok)
Aug  7 20:13:48 rich-desktop /usr/sbin/cron[5389]: (CRON) INFO (Running @reboot jobs)
Aug  7 20:13:48 rich-desktop NetworkManager: <debug> [1218136428.888524] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Ubuntu_7_10_i386'). 
Aug  7 20:13:49 rich-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Aug  7 20:13:49 rich-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Aug  7 20:13:49 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Aug  7 20:13:50 rich-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Aug  7 20:13:50 rich-desktop kernel: [   36.322735] NET: Registered protocol family 17
Aug  7 20:13:52 rich-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug  7 20:13:52 rich-desktop dhclient: DHCPOFFER from 10.69.64.1
Aug  7 20:13:52 rich-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Aug  7 20:13:52 rich-desktop dhclient: DHCPACK from 10.69.64.1
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Joining mDNS multicast group on interface eth0.IPv4 with address 80.193.180.111.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: New relevant interface eth0.IPv4 for mDNS.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Registering new address record for 80.193.180.111 on eth0.IPv4.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Withdrawing address record for 80.193.180.111 on eth0.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Leaving mDNS multicast group on interface eth0.IPv4 with address 80.193.180.111.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Joining mDNS multicast group on interface eth0.IPv4 with address 80.193.180.111.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: New relevant interface eth0.IPv4 for mDNS.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Registering new address record for 80.193.180.111 on eth0.IPv4.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Withdrawing address record for 80.193.180.111 on eth0.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Leaving mDNS multicast group on interface eth0.IPv4 with address 80.193.180.111.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Joining mDNS multicast group on interface eth0.IPv4 with address 80.193.180.111.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: New relevant interface eth0.IPv4 for mDNS.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Registering new address record for 80.193.180.111 on eth0.IPv4.
Aug  7 20:13:52 rich-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Aug  7 20:13:52 rich-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Aug  7 20:13:52 rich-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug  7 20:13:52 rich-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Aug  7 20:13:52 rich-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>    address 80.193.180.111 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>    netmask 255.255.255.0 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>    broadcast 255.255.255.255 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>    gateway 80.193.180.1 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>    nameserver 194.168.4.100 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>    nameserver 194.168.8.100 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>    hostname 'x1-6-00-1a-a0-94-a7-c0' 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Aug  7 20:13:52 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Aug  7 20:13:52 rich-desktop dhclient: bound to 80.193.180.111 -- renewal in 139724 seconds.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Withdrawing address record for 80.193.180.111 on eth0.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Leaving mDNS multicast group on interface eth0.IPv4 with address 80.193.180.111.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Joining mDNS multicast group on interface eth0.IPv4 with address 80.193.180.111.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: New relevant interface eth0.IPv4 for mDNS.
Aug  7 20:13:52 rich-desktop avahi-daemon[5219]: Registering new address record for 80.193.180.111 on eth0.IPv4.
Aug  7 20:13:53 rich-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Aug  7 20:13:53 rich-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Aug  7 20:13:53 rich-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Aug  7 20:13:53 rich-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Aug  7 20:13:53 rich-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug  7 20:13:53 rich-desktop kernel: [   39.317144] NET: Registered protocol family 10
Aug  7 20:13:53 rich-desktop kernel: [   39.317256] lo: Disabled Privacy Extensions
Aug  7 20:13:54 rich-desktop ntpdate[5537]: step time server 91.189.94.4 offset 0.949597 sec
Aug  7 20:13:55 rich-desktop avahi-daemon[5219]: Registering new address record for fe80::21a:a0ff:fe94:a7c0 on eth0.*.
Aug  7 20:14:04 rich-desktop kernel: [   49.524441] eth0: no IPv6 routers present


```

From memory always seems to stall on same last line for each install.

I'm a bit of a noob so be gentle, probably something stupid i've done!

cheers

---

### Post by boyofford on 2008-08-08
can no one help? i can get livecd to work no probs, just problem after install.:(

---

### Post by tropdoug on 2008-08-08
Hi

sorry your not getting too many replies. I can't help with the technical stuff you posted, but I know that when I installed ubuntu alonside Vista it did not like it. I wonder if it's something to do with the hidden partition that vista creates for itself, to hold it's 'ghost image' (i think that's what they call it).

Personally I hated Vista so I simply wiped the entire disc, installed 7.10 and haven't had a day of problems since, and all the graphic and audio and presentation stuff I use I have better or equivalent alternatives from open source. Go the Penguin! 

Hope you get it sorted bro

Doug

</div>

---

### Post by boyofford on 2008-08-08
Do you mean the EISA partitition? i thought that was juzt a dell thing?
I had dual boot working before but the vista install i had before was a dell factory install which i simply shrank to make space for ubuntu.

---

### Post by boyofford on 2008-08-08
right, deleted the eisa partition, and reinstalled, and...same again, could this really be bios? livecds work mostly, but not instalations. I miss having a proper linux install!

---

### Post by boyofford on 2008-08-09
bump...help:confused:

---

