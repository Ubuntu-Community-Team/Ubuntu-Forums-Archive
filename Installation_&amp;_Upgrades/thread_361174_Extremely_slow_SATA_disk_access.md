---
title: "Extremely slow SATA disk access"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by cliveflint on 2007-02-14
Hi,

I have a server with Ubuntu server 6.06 on it running VMWare server 1.01. The machine has an Intel Dual core cpu with 4Gb ram.

My issue is with the sata disks running very slow. I am getting very slow await times on the sata disks on the motherboard of greater than 300ms which means about 3 accesses per second!

I've tried newer kernels which have speeded up the SIL 3132 disks but the on board devices have not got any faster.

I have some knowledge of linux but will need any changes fully explained.

Cheers

Clive

[FONT=Courier New][SIZE=2]```
Linux 2.6.18.1-custom (ubuntu)  13/02/07

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          15.43    0.00   16.39   16.11    0.00   52.07

Device:rrqm/s wrqm/s   r/s    w/s    rsec/s   wsec/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await   svctm   %util
sda    0.83   30.26   2.11    5.26    58.64   288.65    29.32   144.32    47.10      2.32  313.92    9.47    6.98
sdb    1.09   57.45   6.84    4.66   335.57   501.34   167.78   250.67    72.75      1.33  115.39    8.97   10.32
sdc    0.82   30.26   2.12    5.26    55.40   288.56    27.70   144.28    46.61      2.31  313.05    9.47    6.99
sdd    1.18   57.46   7.14    4.66   356.24   501.34   178.12   250.67    72.64      1.32  111.67    8.73   10.30
md0    0.00    0.00   5.84   35.41   113.70   283.25    56.85   141.63     9.62      0.00    0.00    0.00    0.00
md1    0.00    0.00  16.22   61.73   691.65   493.86   345.83   246.93    15.21      0.00    0.00    0.00    0.00
sde   91.86    0.16  27.17    0.12 12053.11     2.31  6026.56     1.16   441.81      0.14    5.08    4.89   13.35
sdf   92.18    0.16  27.23    0.12 12093.91     2.31  6046.96     1.16   442.32      0.14    5.05    4.84   13.25
sdg  180.39 1503.42  18.57   87.94  1592.08 12747.84   796.04  6373.92   134.63      3.03   28.36    4.28   45.59
sdh  181.75 1504.13  18.76   88.76  1604.47 12759.35   802.23  6379.68   133.60      2.95   27.36    4.22   45.43
sdi  179.89 1506.60  18.59   84.46  1588.23 12749.28   794.11  6374.64   139.14      4.02   38.90    4.61   47.46
md3    0.00    0.00 238.42    0.27 24146.95     2.18 12073.48     1.09   101.17      0.00    0.00    0.00    0.00
md2    0.00    0.00   5.27 3029.66   170.64 24237.24    85.32 12118.62     8.04      0.00    0.00    0.00    0.00
```
[/SIZE][/FONT]

Please help!

---

### Post by cliveflint on 2007-02-14
[    0.000000] Bootdata ok (command line is root=/dev/md0 ro quiet splash)
[    0.000000] Linux version 2.6.18.1-custom1 (root@ubuntu) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Tue Feb 13 21:52:11 GMT 2007
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7fd8000 (usable)
[    0.000000]  BIOS-e820: 00000000d7fd8000 - 00000000d7fe0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d7fe0000 - 00000000d8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000127fff000 (usable)
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v002 HP                                    ) @ 0x00000000000f4f10
[    0.000000] ACPI: XSDT (v001 HP     W02      0x00000002 <D2>^D 0x0000162e) @ 0x00000000d7fd82e8
[    0.000000] ACPI: FADT (v003 HP     W02      0x00000002 <D2>^D 0x0000162e) @ 0x00000000d7fd8368
[    0.000000] ACPI: SPCR (v001 HP     SPCRRBSU 0x00000001 <D2>^D 0x0000162e) @ 0x00000000d7fd8140
[    0.000000] ACPI: MCFG (v001 HP     ProLiant 0x00000001  0x00000000) @ 0x00000000d7fd81c0
[    0.000000] ACPI: HPET (v001 HP     D20      0x00000002 <D2>^D 0x0000162e) @ 0x00000000d7fd8200
[    0.000000] ACPI: MADT (v001 HP     00000083 0x00000002  0x00000000) @ 0x00000000d7fd8240
[    0.000000] ACPI: DSDT (v001 HP         DSDT 0x00000001 INTL 0x20030228) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000127fff000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000127fff000
[    0.000000] On node 0 totalpages: 1030972
[    0.000000]   DMA zone: 3052 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 866320 pages, LIFO batch:31
[    0.000000]   Normal zone: 161600 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec80000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 10, version 32, address 0xfec80000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] ACPI: HPET id: 0x10228201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at dc000000 (gap: d8000000:26c00000)
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] Built 1 zonelists.  Total pages: 1030972
[    0.000000] Kernel command line: root=/dev/md0 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 14.318180 MHz WALL HPET GTOD HPET/TSC timer.
[    0.000000] time.c: Detected 3200.252 MHz processor.
[   55.079578] Console: colour VGA+ 80x25
[   55.081673] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   55.085226] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   55.085617] Checking aperture...
[   55.085732] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   55.124483] Placing software IO TLB between 0x166a000 - 0x566a000
[   55.162821] Memory: 4045048k/4849660k available (1936k kernel code, 148700k reserved, 817k data, 180k init)
[   55.305699] Calibrating delay using timer specific routine.. 6405.51 BogoMIPS (lpj=32027587)
[   55.305763] Security Framework v1.0.0 initialized
[   55.305767] SELinux:  Disabled at boot.
[   55.305795] Mount-cache hash table entries: 256
[   55.305947] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   55.305950] CPU: L2 cache: 2048K
[   55.305952] using mwait in idle threads.
[   55.305954] CPU: Physical Processor ID: 0
[   55.305956] CPU: Processor Core ID: 0
[   55.305966] CPU0: Thermal monitoring enabled (TM1)
[   55.305979] SMP alternatives: switching to UP code
[   55.306111] ACPI: Core revision 20060707
[   55.407723] Using local APIC timer interrupts.
[   55.438878] result 12500920
[   55.438880] Detected 12.500 MHz APIC timer.
[   55.445499] SMP alternatives: switching to SMP code
[   55.445526] Booting processor 1/2 APIC 0x1
[   55.456013] Initializing CPU#1
[   55.604768] Calibrating delay using timer specific routine.. 6400.36 BogoMIPS (lpj=32001804)
[   55.604779] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   55.604781] CPU: L2 cache: 2048K
[   55.604784] CPU: Physical Processor ID: 0
[   55.604786] CPU: Processor Core ID: 1
[   55.604796] CPU1: Thermal monitoring enabled (TM1)
[   55.605168]               Intel(R) Pentium(R) D CPU 3.20GHz stepping 02
[   55.614745] Brought up 2 CPUs
[   55.614777] testing NMI watchdog ... OK.
[   55.994933] migration_cost=1000
[   55.995075] checking if image is initramfs... it is
[   56.444188] Freeing initrd memory: 6301k freed
[   56.447811] NET: Registered protocol family 16
[   56.447902] ACPI: bus type pci registered
[   56.447909] PCI: Using configuration type 1
[   56.449464] ACPI: Interpreter enabled
[   56.449466] ACPI: Using IOAPIC for interrupt routing
[   56.450011] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   56.450014] PCI: Probing PCI hardware (bus 00)
[   56.450038] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   56.451425] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[   56.451547] PCI: PXH quirk detected, disabling MSI for SHPC device
[   56.452708] PCI: Transparent bridge - 0000:00:1e.0
[   56.452777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   56.455530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IP2P._PRT]
[   56.455799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.ICHE._PRT]
[   56.456013] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IPE4._PRT]
[   56.456221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IPE5._PRT]
[   56.456429] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PTA0._PRT]
[   56.456583] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PTA0.PCXA._PRT]
[   56.457927] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 *10 11)
[   56.458123] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 *11)
[   56.458313] ACPI: PCI Interrupt Link [LNKC] (IRQs *5 7 10 11)
[   56.458505] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 10 11)
[   56.458698] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 7 10 *11)
[   56.458890] ACPI: PCI Interrupt Link [LNKF] (IRQs *5 7 10 11)
[   56.459080] ACPI: PCI Interrupt Link [LNKG] (IRQs *5 7 10 11)
[   56.459272] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7 10 11)
[   56.459397] Linux Plug and Play Support v0.97 (c) Adam Belay
[   56.459410] pnp: PnP ACPI init
[   56.461214] pnp: PnP ACPI: found 10 devices
[   56.461282] PCI: Using ACPI for IRQ routing
[   56.461285] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   56.461391] hpet0: at MMIO 0xfed00000 (virtual 0xffffffffff5fe000), IRQs 2, 8, 0
[   56.461397] hpet0: 3 64-bit timers, 14318180 Hz
[   56.462419] PCI-GART: No AMD northbridge found.
[   56.462582] pnp: 00:01: ioport range 0x408-0x40f has been reserved
[   56.462585] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   56.462874] PCI: Bridge: 0000:09:00.0
[   56.462876]   IO window: disabled.
[   56.462881]   MEM window: fdf00000-fdffffff
[   56.462884]   PREFETCH window: disabled.
[   56.462888] PCI: Bridge: 0000:00:01.0
[   56.462889]   IO window: disabled.
[   56.462893]   MEM window: fdf00000-fdffffff
[   56.462896]   PREFETCH window: disabled.
[   56.462899] PCI: Bridge: 0000:00:1c.0
[   56.462900]   IO window: disabled.
[   56.462905]   MEM window: disabled.
[   56.462908]   PREFETCH window: disabled.
[   56.462912] PCI: Bridge: 0000:00:1c.4
[   56.462914]   IO window: disabled.
[   56.462918]   MEM window: fdd00000-fddfffff
[   56.462922]   PREFETCH window: disabled.
[   56.462927] PCI: Bridge: 0000:00:1c.5
[   56.462930]   IO window: 4000-4fff
[   56.462935]   MEM window: fde00000-fdefffff
[   56.462939]   PREFETCH window: e0000000-e00fffff
[   56.462945] PCI: Bridge: 0000:00:1e.0
[   56.462948]   IO window: 2000-3fff
[   56.462953]   MEM window: fdc00000-fdcfffff
[   56.462957]   PREFETCH window: d8000000-dfffffff
[   56.462972] GSI 16 sharing vector 0xA9 and IRQ 16
[   56.462974] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[   56.462980] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   56.462994] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   56.463012] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   56.463029] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   56.463047] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   56.463057] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   56.463100] NET: Registered protocol family 2
[   56.561912] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   56.562382] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   56.564417] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   56.564862] TCP: Hash tables configured (established 262144 bind 65536)
[   56.564864] TCP reno registered
[   56.566131] audit: initializing netlink socket (disabled)
[   56.566145] audit(1171405876.470:1): initialized
[   56.566346] VFS: Disk quotas dquot_6.5.1
[   56.566370] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   56.566417] Initializing Cryptographic API
[   56.566421] io scheduler noop registered
[   56.566431] io scheduler anticipatory registered
[   56.566441] io scheduler deadline registered (default)
[   56.566466] io scheduler cfq registered
[   56.587451] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   56.587488] assign_interrupt_mode Found MSI capability
[   56.587545] Allocate Port Service[0000:00:01.0:pcie00]
[   56.587596] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   56.587600] pcie_portdrv_probe->Dev[27d0:8086] has invalid IRQ. Check vendor BIOS
[   56.587638] assign_interrupt_mode Found MSI capability
[   56.587677] Allocate Port Service[0000:00:1c.0:pcie00]
[   56.587721] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   56.587725] pcie_portdrv_probe->Dev[27e0:8086] has invalid IRQ. Check vendor BIOS
[   56.587762] assign_interrupt_mode Found MSI capability
[   56.587801] Allocate Port Service[0000:00:1c.4:pcie00]
[   56.587848] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   56.587851] pcie_portdrv_probe->Dev[27e2:8086] has invalid IRQ. Check vendor BIOS
[   56.587889] assign_interrupt_mode Found MSI capability
[   56.587927] Allocate Port Service[0000:00:1c.5:pcie00]
[   56.612868] Real Time Clock Driver v1.12ac
[   56.612967] hpet_resources: 0xfed00000 is busy
[   56.612980] Linux agpgart interface v0.101 (c) Dave Jones
[   56.612983] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   56.613112] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   56.613228] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   56.613743] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   56.614522] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   56.614711] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[   56.616958] serio: i8042 AUX port at 0x60,0x64 irq 12
[   56.617122] serio: i8042 KBD port at 0x60,0x64 irq 1
[   56.617216] mice: PS/2 mouse device common for all mice
[   56.617315] TCP bic registered
[   56.617337] NET: Registered protocol family 1
[   56.617343] NET: Registered protocol family 8
[   56.617345] NET: Registered protocol family 20
[   56.617634] ACPI: (supports S0 S4 S5)
[   56.617710] Freeing unused kernel memory: 180k freed
[   56.947772] vga16fb: initializing
[   56.947776] vga16fb: mapped to 0xffff8100000a0000
[   56.947822] fb0: VGA16 VGA frame buffer device
[   56.977757] ACPI Exception (acpi_processor-0681): AE_NOT_FOUND, Processor Device is not present [20060707]
[   56.977763] ACPI: Getting cpuindex for acpiid 0x2
[   56.977812] ACPI Exception (acpi_processor-0681): AE_NOT_FOUND, Processor Device is not present [20060707]
[   56.977816] ACPI: Getting cpuindex for acpiid 0x3
[   56.977862] ACPI Exception (acpi_processor-0681): AE_NOT_FOUND, Processor Device is not present [20060707]
[   56.977866] ACPI: Getting cpuindex for acpiid 0x4
[   56.977912] ACPI Exception (acpi_processor-0681): AE_NOT_FOUND, Processor Device is not present [20060707]
[   56.977917] ACPI: Getting cpuindex for acpiid 0x5
[   56.977966] ACPI Exception (acpi_processor-0681): AE_NOT_FOUND, Processor Device is not present [20060707]
[   56.977970] ACPI: Getting cpuindex for acpiid 0x2
[   56.978015] ACPI Exception (acpi_processor-0681): AE_NOT_FOUND, Processor Device is not present [20060707]
[   56.978019] ACPI: Getting cpuindex for acpiid 0x3
[   56.978681] ACPI: Thermal Zone [THM0] (8 C)
[   57.546793] SCSI subsystem initialized
[   57.549481] libata version 2.00 loaded.
[   57.550470] ata_piix 0000:00:1f.2: version 2.00
[   57.550476] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   57.550500] GSI 17 sharing vector 0xD9 and IRQ 17
[   57.550503] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 20 (level, low) -> IRQ 217
[   57.550519] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   57.550567] ata1: SATA max UDMA/133 cmd 0x1080 ctl 0x108A bmdma 0x10A0 irq 217
[   57.550600] ata2: SATA max UDMA/133 cmd 0x1090 ctl 0x109A bmdma 0x10A8 irq 217
[   57.550611] scsi0 : ata_piix
[   57.709768] ata1.00: ATA-7, max UDMA/100, 156301488 sectors: LBA48
[   57.709772] ata1.00: ata1: dev 0 multi count 8
[   57.711143] ata1.01: ATA-7, max UDMA/100, 488397168 sectors: LBA48
[   57.711146] ata1.01: ata1: dev 1 multi count 8
[   57.713457] ata1.00: configured for UDMA/100
[   57.715737] ata1.01: configured for UDMA/100
[   57.715747] scsi1 : ata_piix
[   57.869272] ata2.00: ATA-7, max UDMA/100, 156301488 sectors: LBA48
[   57.869275] ata2.00: ata2: dev 0 multi count 8
[   57.870647] ata2.01: ATA-7, max UDMA/100, 488397168 sectors: LBA48
[   57.870649] ata2.01: ata2: dev 1 multi count 8
[   57.872955] ata2.00: configured for UDMA/100
[   57.875249] ata2.01: configured for UDMA/100
[   57.875337]   Vendor: ATA       Model: Maxtor 6L080M0    Rev: BACE
[   57.875351]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   57.875447]   Vendor: ATA       Model: Maxtor 6L250S0    Rev: BACE
[   57.875460]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   57.875556]   Vendor: ATA       Model: Maxtor 6L080M0    Rev: BACE
[   57.875570]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   57.875664]   Vendor: ATA       Model: Maxtor 6L250S0    Rev: BACE
[   57.875677]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   57.885500] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   57.885515] sda: Write Protect is off
[   57.885518] sda: Mode Sense: 00 3a 00 00
[   57.885539] SCSI device sda: drive cache: write through
[   57.885593] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   57.885605] sda: Write Protect is off
[   57.885607] sda: Mode Sense: 00 3a 00 00
[   57.885628] SCSI device sda: drive cache: write through
[   57.885632]  sda: sda1 sda2
[   57.924717] sd 0:0:0:0: Attached scsi disk sda
[   57.926313] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   57.926328] sdb: Write Protect is off
[   57.926331] sdb: Mode Sense: 00 3a 00 00
[   57.926352] SCSI device sdb: drive cache: write through
[   57.926402] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   57.926414] sdb: Write Protect is off
[   57.926417] sdb: Mode Sense: 00 3a 00 00
[   57.926437] SCSI device sdb: drive cache: write through
[   57.926439]  sdb: sdb1
[   57.947971] sd 0:0:1:0: Attached scsi disk sdb
[   57.949661] SCSI device sdc: 156301488 512-byte hdwr sectors (80026 MB)
[   57.949675] sdc: Write Protect is off
[   57.949677] sdc: Mode Sense: 00 3a 00 00
[   57.949698] SCSI device sdc: drive cache: write through
[   57.949744] SCSI device sdc: 156301488 512-byte hdwr sectors (80026 MB)
[   57.949756] sdc: Write Protect is off
[   57.949758] sdc: Mode Sense: 00 3a 00 00
[   57.949778] SCSI device sdc: drive cache: write through
[   57.949781]  sdc: sdc1 sdc2
[   57.994457] sd 1:0:0:0: Attached scsi disk sdc
[   57.995793] SCSI device sdd: 488397168 512-byte hdwr sectors (250059 MB)
[   57.995811] sdd: Write Protect is off
[   57.995814] sdd: Mode Sense: 00 3a 00 00
[   57.995836] SCSI device sdd: drive cache: write through
[   57.995887] SCSI device sdd: 488397168 512-byte hdwr sectors (250059 MB)
[   57.995899] sdd: Write Protect is off
[   57.995901] sdd: Mode Sense: 00 3a 00 00
[   57.995921] SCSI device sdd: drive cache: write through
[   57.995924]  sdd: sdd1
[   58.014519] sd 1:0:1:0: Attached scsi disk sdd
[   58.181923] usbcore: registered new driver usbfs
[   58.181945] usbcore: registered new driver hub
[   58.183819] GSI 18 sharing vector 0xE1 and IRQ 18
[   58.183823] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 225
[   58.184494] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   58.184500] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   58.184794] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   58.184829] ehci_hcd 0000:00:1d.7: debug port 1
[   58.184834] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   58.184845] ehci_hcd 0000:00:1d.7: irq 225, io mem 0xfdbf0000
[   58.188706] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   58.188794] usb usb1: configuration #1 chosen from 1 choice
[   58.188818] hub 1-0:1.0: USB hub found
[   58.188825] hub 1-0:1.0: 8 ports detected
[   58.189720] USB Universal Host Controller Interface driver v3.0
[   58.203513] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   58.296646] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 225
[   58.296654] GSI 19 sharing vector 0xE9 and IRQ 19
[   58.296660] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   58.296662] ACPI: PCI Interrupt 0000:0a:02.2[C] -> GSI 26 (level, low) -> IRQ 233
[   58.296669] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   58.297049] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   58.297080] uhci_hcd 0000:00:1d.0: irq 225, io base 0x00001000
[   58.297198] usb usb2: configuration #1 chosen from 1 choice
[   58.297226] hub 2-0:1.0: USB hub found
[   58.297234] hub 2-0:1.0: 2 ports detected
[   58.297336] ehci_hcd 0000:0a:02.2: EHCI Host Controller
[   58.406272] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 225
[   58.406282] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   58.406285] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   58.406309] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   58.406331] uhci_hcd 0000:00:1d.1: irq 225, io base 0x00001020
[   58.406419] usb usb3: configuration #1 chosen from 1 choice
[   58.406440] hub 3-0:1.0: USB hub found
[   58.406446] hub 3-0:1.0: 2 ports detected
[   58.515933] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 225
[   58.515942] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   58.515946] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   58.515966] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   58.515998] uhci_hcd 0000:00:1d.2: irq 225, io base 0x00001040
[   58.516091] usb usb4: configuration #1 chosen from 1 choice
[   58.516115] hub 4-0:1.0: USB hub found
[   58.516120] hub 4-0:1.0: 2 ports detected
[   58.575674] usb 1-5: new high speed USB device using ehci_hcd and address 2
[   58.625594] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 21 (level, low) -> IRQ 225
[   58.625601] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   58.625604] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   58.625624] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   58.625646] uhci_hcd 0000:00:1d.3: irq 225, io base 0x00001060
[   58.625736] usb usb5: configuration #1 chosen from 1 choice
[   58.625761] hub 5-0:1.0: USB hub found
[   58.625767] hub 5-0:1.0: 2 ports detected
[   58.728250] usb 1-5: configuration #1 chosen from 1 choice
[   58.735496] ehci_hcd 0000:0a:02.2: new USB bus registered, assigned bus number 6
[   58.765100] ehci_hcd 0000:0a:02.2: irq 233, io mem 0xfdfd0000
[   58.765108] ehci_hcd 0000:0a:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   58.765195] usb usb6: configuration #1 chosen from 1 choice
[   58.765219] hub 6-0:1.0: USB hub found
[   58.765226] hub 6-0:1.0: 5 ports detected
[   58.874837] GSI 20 sharing vector 0x32 and IRQ 20
[   58.874841] ACPI: PCI Interrupt 0000:01:04.4[B] -> GSI 23 (level, low) -> IRQ 50
[   58.874849] uhci_hcd 0000:01:04.4: UHCI Host Controller
[   58.874877] uhci_hcd 0000:01:04.4: new USB bus registered, assigned bus number 7
[   58.874889] uhci_hcd 0000:01:04.4: port count misdetected? forcing to 2 ports
[   58.875656] uhci_hcd 0000:01:04.4: irq 50, io base 0x00003800
[   58.875872] usb usb7: configuration #1 chosen from 1 choice
[   58.875893] hub 7-0:1.0: USB hub found
[   58.875899] hub 7-0:1.0: 2 ports detected
[   58.890838] Initializing USB Mass Storage driver...
[   58.984658] ACPI: PCI Interrupt 0000:0a:02.0[A] -> GSI 26 (level, low) -> IRQ 233
[   58.985328] ohci_hcd 0000:0a:02.0: OHCI Host Controller
[   58.985378] ohci_hcd 0000:0a:02.0: new USB bus registered, assigned bus number 8
[   58.985393] ohci_hcd 0000:0a:02.0: irq 233, io mem 0xfdff0000
[   59.004384] usb 1-6: new high speed USB device using ehci_hcd and address 3
[   59.074284] usb usb8: configuration #1 chosen from 1 choice
[   59.074315] hub 8-0:1.0: USB hub found
[   59.074325] hub 8-0:1.0: 3 ports detected
[   59.166889] usb 1-6: configuration #1 chosen from 1 choice
[   59.183898] GSI 21 sharing vector 0x3A and IRQ 21
[   59.183902] ACPI: PCI Interrupt 0000:0a:02.1[B] -> GSI 27 (level, low) -> IRQ 58
[   59.184539] ohci_hcd 0000:0a:02.1: OHCI Host Controller
[   59.184591] ohci_hcd 0000:0a:02.1: new USB bus registered, assigned bus number 9
[   59.184609] ohci_hcd 0000:0a:02.1: irq 58, io mem 0xfdfe0000
[   59.273661] usb usb9: configuration #1 chosen from 1 choice
[   59.273689] hub 9-0:1.0: USB hub found
[   59.273697] hub 9-0:1.0: 2 ports detected
[   59.482992] scsi2 : SCSI emulation for USB Mass Storage devices
[   59.483058] usb-storage: device found at 2
[   59.483061] usb-storage: waiting for device to settle before scanning
[   59.762046] usb 6-2: new high speed USB device using ehci_hcd and address 2
[   59.915651] usb 6-2: configuration #1 chosen from 1 choice
[   60.190731] usb 7-1: new full speed USB device using uhci_hcd and address 2
[   60.349838] usb 7-1: configuration #1 chosen from 1 choice
[   60.629389] usb 7-2: new full speed USB device using uhci_hcd and address 3
[   60.788035] usb 7-2: configuration #1 chosen from 1 choice
[   60.790162] hub 7-2:1.0: USB hub found
[   60.793439] hub 7-2:1.0: 7 ports detected
[   60.921998] scsi3 : SCSI emulation for USB Mass Storage devices
[   60.922182] usb-storage: device found at 3
[   60.922184] usb-storage: waiting for device to settle before scanning
[   60.922213] scsi4 : SCSI emulation for USB Mass Storage devices
[   60.922370] usb-storage: device found at 2
[   60.922372] usb-storage: waiting for device to settle before scanning
[   60.936654] usbcore: registered new driver usb-storage
[   60.936658] USB Mass Storage support registered.
[   60.936751] usbcore: registered new driver hiddev
[   60.941090] input: HP Virtual Keyboard as /class/input/input0
[   60.941104] input: USB HID v1.01 Keyboard [HP Virtual Keyboard] on usb-0000:01:04.4-1
[   60.945344] input: HP Virtual Keyboard as /class/input/input1
[   60.945367] input: USB HID v1.01 Mouse [HP Virtual Keyboard] on usb-0000:01:04.4-1
[   60.945378] usbcore: registered new driver usbhid
[   60.945381] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   60.971418] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   60.971422] md: bitmap version 4.39
[   60.972064] md: raid1 personality registered for level 1
[   61.052960] md: md0 stopped.
[   61.053540] md: bind<sdc1>
[   61.053669] md: bind<sda1>
[   61.058132] raid1: raid set md0 active with 2 out of 2 mirrors
[   61.069399] md: md1 stopped.
[   61.070036] md: bind<sdd1>
[   61.070174] md: bind<sdb1>
[   61.074560] raid1: raid set md1 active with 2 out of 2 mirrors
[   61.088132] Attempting manual resume
[   61.118717] kjournald starting.  Commit interval 5 seconds
[   61.118724] EXT3-fs: mounted filesystem with ordered data mode.
[   64.141340] ts: Compaq touchscreen protocol output
[   64.200265] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   64.200290] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   64.200312] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   64.200333] sd 1:0:1:0: Attached scsi generic sg3 type 0
[   64.604350] parport: PnPBIOS parport detected.
[   64.604386] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   64.677336] lp0: using parport0 (interrupt-driven).
[   64.937046] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   64.950425] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   65.125686] sata_sil24 0000:06:00.0: version 0.3
[   65.125714] GSI 22 sharing vector 0x42 and IRQ 22
[   65.125717] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 66
[   65.127008] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   65.129548] ata3: SATA max UDMA/100 cmd 0xFFFFC20000020000 ctl 0x0 bmdma 0x0 irq 66
[   65.129858] ata4: SATA max UDMA/100 cmd 0xFFFFC20000022000 ctl 0x0 bmdma 0x0 irq 66
[   65.129872] scsi5 : sata_sil24
[   65.564346] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   65.564461] input: PC Speaker as /class/input/input2
[   65.564877] ata3.00: ATA-7, max UDMA/133, 488397168 sectors: LBA48 NCQ (depth 31/32)
[   65.564880] ata3.00: ata3: dev 0 multi count 16
[   65.565504] ata3.00: configured for UDMA/100
[   65.565518] scsi6 : sata_sil24
[   65.609835] Adding 2955952k swap on /dev/sda2.  Priority:-1 extents:1 across:2955952k
[   65.645292] Adding 2955952k swap on /dev/sdc2.  Priority:-2 extents:1 across:2955952k
[   65.743385]   Vendor: LaCie     Model: BigDisk           Rev:
[   65.743400]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   65.750640] SCSI device sde: 976794336 512-byte hdwr sectors (500119 MB)
[   65.751814] sde: Write Protect is off
[   65.751818] sde: Mode Sense: 10 00 00 00
[   65.751820] sde: assuming drive cache: write through
[   65.753360] SCSI device sde: 976794336 512-byte hdwr sectors (500119 MB)
[   65.754424] sde: Write Protect is off
[   65.754427] sde: Mode Sense: 10 00 00 00
[   65.754429] sde: assuming drive cache: write through
[   65.754500]  sde: sde1
[   65.763393] sd 2:0:0:0: Attached scsi disk sde
[   65.763442] sd 2:0:0:0: Attached scsi generic sg4 type 0
[   65.776024] usb-storage: device scan complete
[   66.003003] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   66.009836] ata4.00: ATA-7, max UDMA/133, 488397168 sectors: LBA48
[   66.009840] ata4.00: ata4: dev 0 multi count 16
[   66.010394] ata4.00: configured for UDMA/100
[   66.012923]   Vendor: ATA       Model: WDC WD2500JS-00N  Rev: 10.0
[   66.012937]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   66.015486] SCSI device sdf: 488397168 512-byte hdwr sectors (250059 MB)
[   66.015513] sdf: Write Protect is off
[   66.015516] sdf: Mode Sense: 00 3a 00 00
[   66.017304] SCSI device sdf: drive cache: write back
[   66.017764] SCSI device sdf: 488397168 512-byte hdwr sectors (250059 MB)
[   66.017778] sdf: Write Protect is off
[   66.017780] sdf: Mode Sense: 00 3a 00 00
[   66.017801] SCSI device sdf: drive cache: write back
[   66.017805]  sdf: unknown partition table
[   66.040472] sd 5:0:0:0: Attached scsi disk sdf
[   66.040522] sd 5:0:0:0: Attached scsi generic sg5 type 0
[   66.041253]   Vendor: ATA       Model: WDC WD2500JS-00M  Rev: 02.0
[   66.041266]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   66.041712] SCSI device sdg: 488397168 512-byte hdwr sectors (250059 MB)
[   66.041725] sdg: Write Protect is off
[   66.041728] sdg: Mode Sense: 00 3a 00 00
[   66.041749] SCSI device sdg: drive cache: write back
[   66.041798] SCSI device sdg: 488397168 512-byte hdwr sectors (250059 MB)
[   66.041811] sdg: Write Protect is off
[   66.041813] sdg: Mode Sense: 00 3a 00 00
[   66.041833] SCSI device sdg: drive cache: write back
[   66.041836]  sdg: sdg1
[   66.048016] sd 6:0:0:0: Attached scsi disk sdg
[   66.048052] sd 6:0:0:0: Attached scsi generic sg6 type 0
[   66.048193] tg3.c:v3.65 (August 07, 2006)
[   66.048215] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[   66.048225] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   66.068663] eth0: Tigon3 [partno(N/A) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:17:a4:36:dd:3f
[   66.068671] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[   66.068674] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   66.131643] EXT3 FS on md0, internal journal
[   67.168435]   Vendor: LaCie     Model: BigDisk           Rev:
[   67.168449]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   67.169368] SCSI device sdh: 976794336 512-byte hdwr sectors (500119 MB)
[   67.170285] sdh: Write Protect is off
[   67.170288] sdh: Mode Sense: 10 00 00 00
[   67.170290] sdh: assuming drive cache: write through
[   67.171156] SCSI device sdh: 976794336 512-byte hdwr sectors (500119 MB)
[   67.172154] sdh: Write Protect is off
[   67.172156] sdh: Mode Sense: 10 00 00 00
[   67.172158] sdh: assuming drive cache: write through
[   67.172216]  sdh:<5>  Vendor: LaCie     Model: BigDisk           Rev:
[   67.177387]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   67.178348] SCSI device sdi: 980469504 512-byte hdwr sectors (502000 MB)
[   67.179341] sdi: Write Protect is off
[   67.179344] sdi: Mode Sense: 10 00 00 00
[   67.179345] sdi: assuming drive cache: write through
[   67.180215] SCSI device sdi: 980469504 512-byte hdwr sectors (502000 MB)
[   67.181214] sdi: Write Protect is off
[   67.181216] sdi: Mode Sense: 10 00 00 00
[   67.181217] sdi: assuming drive cache: write through
[   67.181278]  sdi: sdh1
[   67.182432] sd 3:0:0:0: Attached scsi disk sdh
[   67.182477] sd 3:0:0:0: Attached scsi generic sg7 type 0
[   67.182733] usb-storage: device scan complete
[   67.203874]  sdi1
[   67.203952] sd 4:0:0:0: Attached scsi disk sdi
[   67.204010] sd 4:0:0:0: Attached scsi generic sg8 type 0
[   67.204276] usb-storage: device scan complete
[   67.998547] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   67.998550] tg3: eth0: Flow control is on for TX and on for RX.
[   71.607973] md: md3 stopped.
[   71.769843] md: bind<sdg1>
[   71.769965] md: bind<sdf>
[   71.825513] raid1: raid set md3 active with 2 out of 2 mirrors
[   71.825790] md: md2 stopped.
[   71.831468] md: bind<sde1>
[   71.832078] md: bind<sdi1>
[   71.832591] md: bind<sdh1>
[   71.854191] raid5: automatically using best checksumming function: generic_sse
[   71.894306]    generic_sse:  4859.200 MB/sec
[   71.894308] raid5: using function: generic_sse (4859.200 MB/sec)
[   72.063798] raid6: int64x1   1495 MB/s
[   72.233262] raid6: int64x2   1944 MB/s
[   72.402753] raid6: int64x4   2354 MB/s
[   72.572224] raid6: int64x8   1827 MB/s
[   72.741699] raid6: sse2x1    2396 MB/s
[   72.911162] raid6: sse2x2    3333 MB/s
[   73.080649] raid6: sse2x4    3067 MB/s
[   73.080651] raid6: using algorithm sse2x2 (3333 MB/s)
[   73.080654] md: raid6 personality registered for level 6
[   73.080656] md: raid5 personality registered for level 5
[   73.080658] md: raid4 personality registered for level 4
[   73.080777] raid5: device sdh1 operational as raid disk 0
[   73.080780] raid5: device sdi1 operational as raid disk 2
[   73.080782] raid5: device sde1 operational as raid disk 1
[   73.081121] raid5: allocated 3212kB for md2
[   73.081124] raid5: raid level 5 set md2 active with 3 out of 3 devices, algorithm 2
[   73.081125] RAID5 conf printout:
[   73.081127]  --- rd:3 wd:3 fd:0
[   73.081129]  disk 0, o:1, dev:sdh1
[   73.081130]  disk 1, o:1, dev:sde1
[   73.081132]  disk 2, o:1, dev:sdi1
[   73.165918] device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: [email]dm-devel@redhat.com[/email]
[   74.240186] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.240283] device-mapper: ioctl: error adding target to table
[   74.240511] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.240591] device-mapper: ioctl: error adding target to table
[   74.240797] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.240874] device-mapper: ioctl: error adding target to table
[   74.241079] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.241155] device-mapper: ioctl: error adding target to table
[   74.241361] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.241437] device-mapper: ioctl: error adding target to table
[   74.241643] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.241719] device-mapper: ioctl: error adding target to table
[   74.241921] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.241997] device-mapper: ioctl: error adding target to table
[   74.242203] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.242279] device-mapper: ioctl: error adding target to table
[   74.242481] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.242558] device-mapper: ioctl: error adding target to table
[   74.242761] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.242838] device-mapper: ioctl: error adding target to table
[   74.243044] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.243120] device-mapper: ioctl: error adding target to table
[   74.243324] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.243400] device-mapper: ioctl: error adding target to table
[   74.243622] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.243713] device-mapper: ioctl: error adding target to table
[   74.243901] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.243977] device-mapper: ioctl: error adding target to table
[   74.244180] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.244257] device-mapper: ioctl: error adding target to table
[   74.244461] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.244538] device-mapper: ioctl: error adding target to table
[   74.244738] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.244815] device-mapper: ioctl: error adding target to table
[   74.245020] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.245096] device-mapper: ioctl: error adding target to table
[   74.245299] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.245375] device-mapper: ioctl: error adding target to table
[   74.245579] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.245656] device-mapper: ioctl: error adding target to table
[   74.245858] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.245935] device-mapper: ioctl: error adding target to table
[   74.246139] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.246216] device-mapper: ioctl: error adding target to table
[   74.246417] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.246494] device-mapper: ioctl: error adding target to table
[   74.246708] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   74.246785] device-mapper: ioctl: error adding target to table
[   74.386681] kjournald starting.  Commit interval 5 seconds
[   74.435085] EXT3 FS on md1, internal journal

---

### Post by cliveflint on 2007-02-14
[   74.435090] EXT3-fs: mounted filesystem with ordered data mode.
[   74.494981] kjournald starting.  Commit interval 5 seconds
[   74.496714] EXT3 FS on md2, internal journal
[   74.496718] EXT3-fs: mounted filesystem with ordered data mode.
[   74.527002] kjournald starting.  Commit interval 5 seconds
[   74.554240] EXT3 FS on md3, internal journal
[   74.554244] EXT3-fs: mounted filesystem with ordered data mode.
[   78.672601] NET: Registered protocol family 10
[   78.672716] lo: Disabled Privacy Extensions
[   78.672832] IPv6 over IPv4 tunneling driver
[   89.570750] eth0: no IPv6 routers present
[  217.744083] vmmon: module license 'unspecified' taints kernel.
[  217.744637] /dev/vmmon[6863]: Module vmmon: registered with major=10 minor=165
[  217.744649] /dev/vmmon[6863]: Module vmmon: initialized
[  217.766696] /dev/vmmon[6869]: Module vmmon: unloaded
[  254.398721] /dev/vmmon[7211]: Module vmmon: registered with major=10 minor=165
[  254.398735] /dev/vmmon[7211]: Module vmmon: initialized
[  255.284211] /dev/vmnet: open called by PID 7238 (vmnet-bridge)
[  255.284220] /dev/vmnet: hub 0 does not exist, allocating memory.
[  255.284231] /dev/vmnet: port on hub 0 successfully opened
[  255.284331] bridge-eth0: enabling the bridge
[  255.284336] bridge-eth0: up
[  255.284338] bridge-eth0: already up
[  255.284340] bridge-eth0: attached
[  255.303508] /dev/vmnet: open called by PID 7250 (vmnet-natd)
[  255.303518] /dev/vmnet: hub 8 does not exist, allocating memory.
[  255.303532] /dev/vmnet: port on hub 8 successfully opened
[  255.648043] ppdev: user-space parallel port driver
[  256.990945] /dev/vmnet: open called by PID 7275 (vmware-vmx)
[  256.990976] device eth0 entered promiscuous mode
[  256.990984] audit(1171406077.792:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  256.990987] bridge-eth0: enabled promiscuous mode
[  256.990990] /dev/vmnet: port on hub 0 successfully opened
[  257.060764] /dev/vmmon[7287]: host clock rate change request 0 -> 19
[  264.423392] /dev/vmmon[7287]: host clock rate change request 19 -> 83
[  265.286781] /dev/vmnet: open called by PID 7301 (vmnet-netifup)
[  265.286795] /dev/vmnet: port on hub 8 successfully opened
[  265.288061] /dev/vmnet: open called by PID 7302 (vmnet-netifup)
[  265.288071] /dev/vmnet: hub 1 does not exist, allocating memory.
[  265.288084] /dev/vmnet: port on hub 1 successfully opened
[  265.506590] /dev/vmnet: open called by PID 7328 (vmnet-dhcpd)
[  265.506609] /dev/vmnet: port on hub 1 successfully opened
[  265.506808] /dev/vmnet: open called by PID 7327 (vmnet-dhcpd)
[  265.506818] /dev/vmnet: port on hub 8 successfully opened
[  272.618502] device eth0 left promiscuous mode
[  272.618515] audit(1171406093.462:3): dev=eth0 prom=0 old_prom=256 auid=4294967295
[  272.618520] bridge-eth0: disabled promiscuous mode
[  272.618793] /dev/vmnet: open called by PID 7287 (vmware-vmx)
[  272.618813] device eth0 entered promiscuous mode
[  272.618818] audit(1171406093.462:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
[  272.618820] bridge-eth0: enabled promiscuous mode
[  272.618822] /dev/vmnet: port on hub 0 successfully opened
[  275.341814] vmnet1: no IPv6 routers present
[  275.939976] vmnet8: no IPv6 routers present
[  281.885572] /dev/vmnet: open called by PID 7404 (vmware-vmx)
[  281.885590] /dev/vmnet: port on hub 0 successfully opened
[  306.956172] /dev/vmnet: open called by PID 7461 (vmware-vmx)
[  306.956184] /dev/vmnet: port on hub 0 successfully opened
[  322.037809] /dev/vmnet: open called by PID 7502 (vmware-vmx)
[  322.037824] /dev/vmnet: port on hub 0 successfully opened
[  329.583729] /dev/vmmon[7514]: host clock rate change request 83 -> 100
[  331.317219] /dev/vmmon[7514]: host clock rate change request 100 -> 200
[  342.928968] /dev/vmmon[7514]: host clock rate change request 200 -> 201
[  343.310341] /dev/vmnet: open called by PID 7514 (vmware-vmx)
[  343.310355] /dev/vmnet: port on hub 0 successfully opened
[  357.743009] /dev/vmmon[7514]: host clock rate change request 201 -> 200
[  390.357108] /dev/vmnet: open called by PID 7514 (vmware-vmx)
[  390.357120] /dev/vmnet: port on hub 0 successfully opened
[  393.729190] /dev/vmmon[7514]: host clock rate change request 200 -> 201
[  403.698934] /dev/vmmon[7514]: host clock rate change request 201 -> 200
[  404.920042] /dev/vmmon[7514]: host clock rate change request 200 -> 100
[  404.969657] /dev/vmmon[7502]: host clock rate change request 100 -> 83
[  404.979912] vmmon: Had to deallocate locked 18889 pages from vm driver ffff81003ec1a000
[  404.988261] vmmon: Had to deallocate AWE 3338 pages from vm driver ffff81003ec1a000

---

### Post by cliveflint on 2007-02-14
root@ubuntu:~# lspci
0000:00:00.0 Host bridge: Intel Corporation E7230 Memory Controller Hub (rev 81)
0000:00:01.0 PCI bridge: Intel Corporation E7230 PCI Express Root Port (rev 81)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
0000:00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:01:03.0 VGA compatible controller: ATI Technologies Inc: Unknown device 515e (rev 02)
0000:01:04.0 System peripheral: Compaq Computer Corporation Integrated Lights Out Controller (rev 03)
0000:01:04.2 System peripheral: Compaq Computer Corporation Integrated Lights Out  Processor (rev 03)
0000:01:04.4 USB Controller: Hewlett-Packard Company: Unknown device 3300
0000:05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
0000:06:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
0000:09:00.0 PCI bridge: Intel Corporation 6702PXH PCI Express-to-PCI Bridge A (rev 09)
0000:0a:02.0 USB Controller: NEC Corporation USB (rev 43)
0000:0a:02.1 USB Controller: NEC Corporation USB (rev 43)
0000:0a:02.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

root@ubuntu:~# lsmod
Module                  Size  Used by
ppdev                  11400  0
vmnet                  43304  17
vmmon                 147448  14
ipv6                  286496  28
dm_mod                 62024  0
raid456               123424  1
xor                     7440  1 raid456
serio_raw               9220  0
pcspkr                  4864  0
tg3                   109828  0
sata_sil24             18308  4
shpchp                 40880  0
pci_hotplug            35604  1 shpchp
psmouse                42508  0
parport_pc             39792  1
lp                     15040  0
parport                42764  3 ppdev,parport_pc,lp
sg                     39600  0
tsdev                  10240  0
evdev                  12800  0
ext3                  139920  4
jbd                    64360  1 ext3
mbcache                11656  1 ext3
raid1                  25344  3
md_mod                 82584  6 raid456,raid1
usbhid                 45856  0
usb_storage            76224  3
ohci_hcd               22916  0
uhci_hcd               26904  0
ehci_hcd               34696  0
usbcore               144060  6
usbhid,usb_storage,ohci_hcd,uhci_hcd,ehci_hcd
sd_mod                 23552  19
ata_piix               17416  10
libata                107168  2 sata_sil24,ata_piix
scsi_mod              154520  4 sg,usb_storage,sd_mod,libata
thermal                17420  0
processor              34952  1 thermal
fan                     6920  0
vga16fb                14232  0
cfbcopyarea             5248  1 vga16fb
vgastate               10240  1 vga16fb
cfbimgblt               4352  1 vga16fb
cfbfillrect             5760  1 vga16fb

---

### Post by cliveflint on 2007-02-15
Can anyone help? I'm not the only one having these issues.

---

