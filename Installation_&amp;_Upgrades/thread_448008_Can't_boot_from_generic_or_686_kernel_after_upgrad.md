---
title: "Can't boot from generic or 686 kernel after upgrading from dapper ot edgy?"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by trytrytry on 2007-05-18
After having upgraded from dapper to edgy, I can only boot from the kernel 2.6.17-11-386. The generic one does not work for me (black screen each time I tried). I even can not boot from the old 686 kernel, which worked in dapper.

Here is part of the output from dmesg. Anyone experienced the similar problems? Thx.

[17179569.184000] Linux version 2.6.17-11-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Mar 13 23:30:30 UTC 2007 (Ubuntu 2.6.17-11.37-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 00000000cfe8ac00 (usable)
[17179569.184000]  BIOS-e820: 00000000cfe8ac00 - 00000000cfe8cc00 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000cfe8cc00 - 00000000cfe8ec00 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000cfe8ec00 - 00000000d0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000]  BIOS-e820: 0000000100000000 - 000000012c000000 (usable)
[17179569.184000] Warning only 4GB will be used.
[17179569.184000] Use a PAE enabled kernel.
[17179569.184000] 3200MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fe710
[17179569.184000] On node 0 totalpages: 1048576
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 819200 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fec30
[17179569.184000] ACPI: RSDT (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x000fcb69
[17179569.184000] ACPI: FADT (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x000fcbbd
[17179569.184000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffdbcac
[17179569.184000] ACPI: MADT (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x000fcc31
[17179569.184000] ACPI: BOOT (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x000fccbb
[17179569.184000] ACPI: ASF! (v016 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x000fcce3
[17179569.184000] ACPI: MCFG (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x000fcd4a
[17179569.184000] ACPI: HPET (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x000fcd88
[17179569.184000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x06] enabled)
[17179569.184000] Processor #6 15:4 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] enabled)
[17179569.184000] Processor #7 15:4 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: IOAPIC (id[0x09] address[0xfec80000] gsi_base[24])
[17179569.184000] IOAPIC[1]: apic_id 9, version 32, address 0xfec80000, GSI 24-47
[17179569.184000] ACPI: IOAPIC (id[0x0a] address[0xfec80800] gsi_base[48])
[17179569.184000] IOAPIC[2]: apic_id 10, version 32, address 0xfec80800, GSI 48-71
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 3 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at d1000000 (gap: d0000000:10000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=28301226-81ce-4f3b-b4ae-45ff2b17d4ac ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] mapped IOAPIC to ffffb000 (fec80000)
[17179569.184000] mapped IOAPIC to ffffa000 (fec80800)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 3361292k/4194304k available (1829k kernel code, 43868k reserved, 1041k data, 288k init, 2488872k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 3391.651 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.264000] Calibrating delay using timer specific routine.. 6787.65 BogoMIPS (lpj=13575306)
[17179569.264000] Security Framework v1.0.0 initialized
[17179569.264000] SELinux:  Disabled at boot.
[17179569.264000] Mount-cache hash table entries: 512
[17179569.264000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179569.264000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179569.264000] monitor/mwait feature present.
[17179569.264000] using mwait in idle threads.
[17179569.264000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.264000] CPU: L2 cache: 2048K
[17179569.264000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000649d 00000000 00000000
[17179569.264000] CPU: Intel(R) Xeon(TM) CPU 3.40GHz stepping 03
[17179569.264000] Checking 'hlt' instruction... OK.
[17179569.280000] SMP alternatives: switching to UP code
[17179569.280000] Freeing SMP alternatives: 0k freed
[17179569.280000] checking if image is initramfs... it is
[17179569.744000] Freeing initrd memory: 6693k freed
[17179569.744000] ACPI: Core revision 20060707
[17179569.752000] ACPI: Looking for DSDT ... not found!
[17179569.780000] ENABLING IO-APIC IRQs
[17179569.780000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[17179569.928000] NET: Registered protocol family 16
[17179569.928000] EISA bus registered
[17179569.928000] ACPI: bus type pci registered
[17179569.928000] PCI: Using MMCONFIG
[17179569.928000] Setting up standard PCI resources
[17179569.960000] ACPI: Interpreter enabled
[17179569.960000] ACPI: Using IOAPIC for interrupt routing
[17179569.964000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179569.964000] PCI: Probing PCI hardware (bus 00)
[17179569.964000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179569.980000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179569.980000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179569.980000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179569.980000] PCI: PXH quirk detected, disabling MSI for SHPC device
[17179569.980000] PCI: PXH quirk detected, disabling MSI for SHPC device
[17179569.980000] Boot video device is 0000:05:00.0
[17179569.980000] PCI: Transparent bridge - 0000:00:1e.0
[17179569.980000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.536000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179570.540000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1.PCI2._PRT]
[17179570.548000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1.PCI3._PRT]
[17179570.556000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[17179570.560000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[17179570.568000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI6._PRT]
[17179570.604000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179570.604000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179570.604000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179570.604000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179570.604000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179570.608000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179570.608000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179570.608000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179570.608000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.608000] pnp: PnP ACPI init
[17179570.636000] pnp: PnP ACPI: found 10 devices
[17179570.636000] PnPBIOS: Disabled by ACPI PNP
[17179570.636000] PCI: Using ACPI for IRQ routing
[17179570.636000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.640000] pnp: 00:01: ioport range 0x800-0x85f could not be reserved
[17179570.640000] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[17179570.640000] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[17179570.640000] PCI: Bridge: 0000:01:00.0
[17179570.640000]   IO window: disabled.
[17179570.640000]   MEM window: disabled.
[17179570.640000]   PREFETCH window: disabled.
[17179570.640000] PCI: Bridge: 0000:01:00.2
[17179570.640000]   IO window: d000-dfff
[17179570.640000]   MEM window: dfe00000-dfefffff
[17179570.640000]   PREFETCH window: disabled.
[17179570.640000] PCI: Bridge: 0000:00:02.0
[17179570.640000]   IO window: d000-dfff
[17179570.640000]   MEM window: dfe00000-dfefffff
[17179570.640000]   PREFETCH window: disabled.
[17179570.640000] PCI: Bridge: 0000:00:03.0
[17179570.640000]   IO window: disabled.
[17179570.640000]   MEM window: dfd00000-dfdfffff
[17179570.640000]   PREFETCH window: disabled.
[17179570.640000] PCI: Bridge: 0000:00:04.0
[17179570.640000]   IO window: disabled.
[17179570.640000]   MEM window: dd000000-dfcfffff
[17179570.640000]   PREFETCH window: d0000000-d7ffffff
[17179570.640000] PCI: Bridge: 0000:00:1e.0
[17179570.640000]   IO window: disabled.

---

