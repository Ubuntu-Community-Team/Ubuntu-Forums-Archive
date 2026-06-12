---
title: "kernal panic need help with reviewing boot msg"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by X51r-user on 2008-11-16
hi all,

  I need some help, i have installed a new kernal 2.6.24-21 from 2.6.24-19 but there seems to be problems during please could you review me kernal messages below and provide some advice.

```

Nov  2 05:30:21 phillip-laptop kernel: Loaded 27897 symbols from /boot/System.map-2.6.24-21-generic.
Nov  2 05:30:21 phillip-laptop kernel: Symbols match kernel version 2.6.24.
Nov  2 05:30:21 phillip-laptop kernel: Loaded 22741 symbols from 109 modules.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fa8000 (usable)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fa8000 - 0000000077fb0000 (ACPI NVS)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fb0000 - 0000000077fbe000 (ACPI data)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fbe000 - 0000000077ff0000 (ACPI NVS)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077ff0000 - 0000000078000000 (reserved)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] 1023MB HIGHMEM available.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] 896MB LOWMEM available.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] found SMP MP-table at 000ff780
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 491432) 0 entries of 256 used
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Zone PFN ranges:
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   DMA             0 ->     4096
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   HighMem    229376 ->   491432
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Movable zone start PFN for each node
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]     0:        0 ->   491432
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] On node 0 totalpages: 491432
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   HighMem zone: 2047 pages used for memmap
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   HighMem zone: 260009 pages, LIFO batch:31
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] DMI 2.4 present.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7F50 checksum 0
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: RSDP 000F7F50, 0024 (r2 ACPIAM)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: XSDT 77FB0100, 0054 (r1 _ASUS_ Notebook  7000731 MSFT       97)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: FACP 77FB0290, 00F4 (r3 A.M.I  OEMFACP   7000731 MSFT       97)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: DSDT 77FB0630, 77A4 (r1  T12R0 T12R0000        0 INTL 20051117)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: FACS 77FBE000, 0040
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: APIC 77FB0390, 005C (r1 A.M.I  OEMAPIC   7000731 MSFT       97)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: MCFG 77FB03F0, 003C (r1 A.M.I  OEMMCFG   7000731 MSFT       97)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: SLIC 77FB0430, 0176 (r1 _ASUS_ Notebook  7000731 MSFT       97)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: BOOT 77FB0600, 0028 (r1 A.M.I  OEMBOOT   7000731 MSFT       97)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: OEMB 77FBE040, 005B (r1 A.M.I  AMI_OEM   7000731 MSFT       97)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Processor #0 6:14 APIC version 20
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Processor #1 6:14 APIC version 20
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:86e00000)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487593
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Kernel command line: root=UUID=3c071645-e73d-42b0-95ae-d796b29b38b3 ro splash vga=792
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Initializing CPU#0
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov  2 05:30:21 phillip-laptop kernel: [    0.000000] Detected 1862.157 MHz processor.
Nov  2 05:30:21 phillip-laptop kernel: [   33.783531] Console: colour dummy device 80x25
Nov  2 05:30:21 phillip-laptop kernel: [   33.783536] console [tty0] enabled
Nov  2 05:30:21 phillip-laptop kernel: [   33.784605] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  2 05:30:21 phillip-laptop kernel: [   33.785315] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  2 05:30:21 phillip-laptop kernel: [   33.897577] Memory: 1935620k/1965728k available (2177k kernel code, 28936k reserved, 1005k data, 368k init, 1048224k highmem)
Nov  2 05:30:21 phillip-laptop kernel: [   33.897600] virtual kernel memory layout:
Nov  2 05:30:21 phillip-laptop kernel: [   33.897601]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Nov  2 05:30:21 phillip-laptop kernel: [   33.897602]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  2 05:30:21 phillip-laptop kernel: [   33.897604]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov  2 05:30:21 phillip-laptop kernel: [   33.897605]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov  2 05:30:21 phillip-laptop kernel: [   33.897606]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Nov  2 05:30:21 phillip-laptop kernel: [   33.897607]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
Nov  2 05:30:21 phillip-laptop kernel: [   33.897608]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
Nov  2 05:30:21 phillip-laptop kernel: [   33.897629] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov  2 05:30:21 phillip-laptop kernel: [   33.897699] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Nov  2 05:30:21 phillip-laptop kernel: [   33.977607] Calibrating delay using timer specific routine.. 3728.24 BogoMIPS (lpj=7456496)
Nov  2 05:30:21 phillip-laptop kernel: [   33.977658] Security Framework initialized
Nov  2 05:30:21 phillip-laptop kernel: [   33.977674] SELinux:  Disabled at boot.
Nov  2 05:30:21 phillip-laptop kernel: [   33.977699] AppArmor: AppArmor initialized
Nov  2 05:30:21 phillip-laptop kernel: [   33.977705] Failure registering capabilities with primary security module.
Nov  2 05:30:21 phillip-laptop kernel: [   33.977719] Mount-cache hash table entries: 512
Nov  2 05:30:21 phillip-laptop kernel: [   33.977907] Initializing cgroup subsys ns
Nov  2 05:30:21 phillip-laptop kernel: [   33.977920] Initializing cgroup subsys cpuacct
Nov  2 05:30:21 phillip-laptop kernel: [   33.977938] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
Nov  2 05:30:21 phillip-laptop kernel: [   33.977946] monitor/mwait feature present.
Nov  2 05:30:21 phillip-laptop kernel: [   33.977950] using mwait in idle threads.
Nov  2 05:30:21 phillip-laptop kernel: [   33.977956] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov  2 05:30:21 phillip-laptop kernel: [   33.977961] CPU: L2 cache: 1024K
Nov  2 05:30:21 phillip-laptop kernel: [   33.977966] CPU: Physical Processor ID: 0
Nov  2 05:30:21 phillip-laptop kernel: [   33.977969] CPU: Processor Core ID: 0
Nov  2 05:30:21 phillip-laptop kernel: [   33.977974] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
Nov  2 05:30:21 phillip-laptop kernel: [   33.977986] Compat vDSO mapped to ffffe000.
Nov  2 05:30:21 phillip-laptop kernel: [   33.978006] Checking 'hlt' instruction... OK.
Nov  2 05:30:21 phillip-laptop kernel: [   33.994003] SMP alternatives: switching to UP code
Nov  2 05:30:21 phillip-laptop kernel: [   33.995867] Early unpacking initramfs... done
Nov  2 05:30:21 phillip-laptop kernel: [   34.337197] ACPI: Core revision 20070126
Nov  2 05:30:21 phillip-laptop kernel: [   34.337275] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov  2 05:30:21 phillip-laptop kernel: [   34.342497] CPU0: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
Nov  2 05:30:21 phillip-laptop kernel: [   34.342522] SMP alternatives: switching to SMP code
Nov  2 05:30:21 phillip-laptop kernel: [   34.343281] Booting processor 1/1 eip 3000
Nov  2 05:30:21 phillip-laptop kernel: [   34.353449] Initializing CPU#1
Nov  2 05:30:21 phillip-laptop kernel: [   34.432874] Calibrating delay using timer specific routine.. 3724.56 BogoMIPS (lpj=7449135)
Nov  2 05:30:21 phillip-laptop kernel: [   34.432882] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
Nov  2 05:30:21 phillip-laptop kernel: [   34.432888] monitor/mwait feature present.
Nov  2 05:30:21 phillip-laptop kernel: [   34.432892] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov  2 05:30:21 phillip-laptop kernel: [   34.432893] CPU: L2 cache: 1024K
Nov  2 05:30:21 phillip-laptop kernel: [   34.432896] CPU: Physical Processor ID: 0
Nov  2 05:30:21 phillip-laptop kernel: [   34.432897] CPU: Processor Core ID: 1
Nov  2 05:30:21 phillip-laptop kernel: [   34.432899] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
Nov  2 05:30:21 phillip-laptop kernel: [   34.433428] CPU1: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
Nov  2 05:30:21 phillip-laptop kernel: [   34.433470] Total of 2 processors activated (7452.81 BogoMIPS).
Nov  2 05:30:21 phillip-laptop kernel: [   34.433649] ENABLING IO-APIC IRQs
Nov  2 05:30:21 phillip-laptop kernel: [   34.433840] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov  2 05:30:21 phillip-laptop kernel: [   34.580779] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov  2 05:30:21 phillip-laptop kernel: [   34.600772] Brought up 2 CPUs
Nov  2 05:30:21 phillip-laptop kernel: [   34.600798] CPU0 attaching sched-domain:
Nov  2 05:30:21 phillip-laptop kernel: [   34.600801]  domain 0: span 03
Nov  2 05:30:21 phillip-laptop kernel: [   34.600803]   groups: 01 02
Nov  2 05:30:21 phillip-laptop kernel: [   34.600806] CPU1 attaching sched-domain:
Nov  2 05:30:21 phillip-laptop kernel: [   34.600808]  domain 0: span 03
Nov  2 05:30:21 phillip-laptop kernel: [   34.600810]   groups: 02 01
Nov  2 05:30:21 phillip-laptop kernel: [   34.601099] net_namespace: 64 bytes
Nov  2 05:30:21 phillip-laptop kernel: [   34.601113] Booting paravirtualized kernel on bare hardware
Nov  2 05:30:21 phillip-laptop kernel: [   34.601565] Time:  5:29:52  Date: 11/02/08
Nov  2 05:30:21 phillip-laptop kernel: [   34.601601] NET: Registered protocol family 16
Nov  2 05:30:21 phillip-laptop kernel: [   34.601837] EISA bus registered
Nov  2 05:30:21 phillip-laptop kernel: [   34.601845] ACPI: bus type pci registered
Nov  2 05:30:21 phillip-laptop kernel: [   34.602130] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=9
Nov  2 05:30:21 phillip-laptop kernel: [   34.602135] PCI: Using configuration type 1
Nov  2 05:30:21 phillip-laptop kernel: [   34.602154] Setting up standard PCI resources
Nov  2 05:30:21 phillip-laptop kernel: [   34.602642] mtrr: your CPUs had inconsistent variable MTRR settings
Nov  2 05:30:21 phillip-laptop kernel: [   34.602647] mtrr: probably your BIOS does not setup all CPUs.
Nov  2 05:30:21 phillip-laptop kernel: [   34.602651] mtrr: corrected configuration.
Nov  2 05:30:21 phillip-laptop kernel: [   34.606992] ACPI: EC: Look up EC in DSDT
Nov  2 05:30:21 phillip-laptop kernel: [   34.652681] ACPI: Interpreter enabled
Nov  2 05:30:21 phillip-laptop kernel: [   34.652688] ACPI: (supports S0 S1 S3 S4 S5)
Nov  2 05:30:21 phillip-laptop kernel: [   34.652710] ACPI: Using IOAPIC for interrupt routing
Nov  2 05:30:21 phillip-laptop kernel: [   34.660302] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
Nov  2 05:30:21 phillip-laptop kernel: [   34.660308] ACPI: EC: driver started in poll mode
Nov  2 05:30:21 phillip-laptop kernel: [   34.660444] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  2 05:30:21 phillip-laptop kernel: [   34.660764] pci 0000:00:12.0: set SATA to AHCI mode
Nov  2 05:30:21 phillip-laptop kernel: [   34.662587] PCI: Transparent bridge - 0000:00:14.4
Nov  2 05:30:21 phillip-laptop kernel: [   34.662691] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov  2 05:30:21 phillip-laptop kernel: [   34.662836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Nov  2 05:30:21 phillip-laptop kernel: [   34.662994] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
Nov  2 05:30:21 phillip-laptop kernel: [   34.663115] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
Nov  2 05:30:21 phillip-laptop kernel: [   34.663231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Nov  2 05:30:21 phillip-laptop kernel: [   34.663362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Nov  2 05:30:21 phillip-laptop kernel: [   34.663520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
Nov  2 05:30:21 phillip-laptop kernel: [   34.668903] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *11 12)
Nov  2 05:30:21 phillip-laptop kernel: [   34.669062] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 12)
Nov  2 05:30:21 phillip-laptop kernel: [   34.669217] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 12)
Nov  2 05:30:21 phillip-laptop kernel: [   34.669371] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 12) *10
Nov  2 05:30:21 phillip-laptop kernel: [   34.669526] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 12)
Nov  2 05:30:21 phillip-laptop kernel: [   34.669679] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 12)
Nov  2 05:30:21 phillip-laptop kernel: [   34.669832] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 12)
Nov  2 05:30:21 phillip-laptop kernel: [   34.669986] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 12)
Nov  2 05:30:21 phillip-laptop kernel: [   34.670150] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  2 05:30:21 phillip-laptop kernel: [   34.670189] pnp: PnP ACPI init
Nov  2 05:30:21 phillip-laptop kernel: [   34.670199] ACPI: bus type pnp registered
Nov  2 05:30:21 phillip-laptop kernel: [   34.672614] pnp: PnP ACPI: found 12 devices
Nov  2 05:30:21 phillip-laptop kernel: [   34.672620] ACPI: ACPI bus type pnp unregistered
Nov  2 05:30:21 phillip-laptop kernel: [   34.672627] PnPBIOS: Disabled by ACPI PNP
Nov  2 05:30:21 phillip-laptop kernel: [   34.672960] PCI: Using ACPI for IRQ routing
Nov  2 05:30:21 phillip-laptop kernel: [   34.672966] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov  2 05:30:21 phillip-laptop kernel: [   34.720584] NET: Registered protocol family 8
Nov  2 05:30:21 phillip-laptop kernel: [   34.720589] NET: Registered protocol family 20
Nov  2 05:30:21 phillip-laptop kernel: [   34.720664] AppArmor: AppArmor Filesystem Enabled
Nov  2 05:30:21 phillip-laptop kernel: [   34.724426] Time: tsc clocksource has been installed.
Nov  2 05:30:21 phillip-laptop kernel: [   34.736587] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736596] system 00:05: ioport range 0x40b-0x40b has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736601] system 00:05: ioport range 0x4d6-0x4d6 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736606] system 00:05: ioport range 0xc00-0xc01 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736611] system 00:05: ioport range 0xc14-0xc14 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736616] system 00:05: ioport range 0xc50-0xc51 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736621] system 00:05: ioport range 0xc52-0xc52 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736627] system 00:05: ioport range 0xc6c-0xc6c has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736632] system 00:05: ioport range 0xc6f-0xc6f has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736637] system 00:05: ioport range 0xcd0-0xcd1 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736642] system 00:05: ioport range 0xcd2-0xcd3 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736647] system 00:05: ioport range 0xcd4-0xcd5 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736652] system 00:05: ioport range 0xcd6-0xcd7 has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736657] system 00:05: ioport range 0xcd8-0xcdf has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736662] system 00:05: ioport range 0x800-0x89f has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736668] system 00:05: ioport range 0xb00-0xb1f could not be reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736673] system 00:05: ioport range 0x900-0x90f has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736678] system 00:05: ioport range 0x910-0x91f has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736683] system 00:05: ioport range 0xfe00-0xfefe has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736688] system 00:05: ioport range 0x4000-0x40fe has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736694] system 00:05: iomem range 0xfed20000-0xfed3ffff has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736700] system 00:05: iomem range 0xfed45000-0xfed89fff has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736706] system 00:05: iomem range 0xffb80000-0xffbfffff could not be reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736712] system 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736723] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736729] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736738] system 00:09: ioport range 0x25c-0x25c has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736743] system 00:09: ioport range 0x25d-0x25d has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736748] system 00:09: ioport range 0x25e-0x25e has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736753] system 00:09: ioport range 0x25f-0x25f has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736761] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736770] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736775] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736781] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736786] system 00:0b: iomem range 0x100000-0x77ffffff could not be reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.736793] system 00:0b: iomem range 0x0-0x0 could not be reserved
Nov  2 05:30:21 phillip-laptop kernel: [   34.767249] PCI: Bridge: 0000:00:01.0
Nov  2 05:30:21 phillip-laptop kernel: [   34.767255]   IO window: 7000-7fff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767260]   MEM window: f8800000-f88fffff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767265]   PREFETCH window: 8ff00000-afefffff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767271] PCI: Bridge: 0000:00:04.0
Nov  2 05:30:21 phillip-laptop kernel: [   34.767274]   IO window: disabled.
Nov  2 05:30:21 phillip-laptop kernel: [   34.767279]   MEM window: f8900000-f89fffff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767284]   PREFETCH window: disabled.
Nov  2 05:30:21 phillip-laptop kernel: [   34.767289] PCI: Bridge: 0000:00:05.0
Nov  2 05:30:21 phillip-laptop kernel: [   34.767293]   IO window: 8000-9fff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767299]   MEM window: f8a00000-fc9fffff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767304]   PREFETCH window: aff00000-cfefffff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767309] PCI: Bridge: 0000:00:06.0
Nov  2 05:30:21 phillip-laptop kernel: [   34.767312]   IO window: disabled.
Nov  2 05:30:21 phillip-laptop kernel: [   34.767317]   MEM window: disabled.
Nov  2 05:30:21 phillip-laptop kernel: [   34.767321]   PREFETCH window: disabled.
Nov  2 05:30:21 phillip-laptop kernel: [   34.767327] PCI: Bridge: 0000:00:07.0
Nov  2 05:30:21 phillip-laptop kernel: [   34.767330]   IO window: disabled.
Nov  2 05:30:21 phillip-laptop kernel: [   34.767335]   MEM window: disabled.
Nov  2 05:30:21 phillip-laptop kernel: [   34.767339]   PREFETCH window: disabled.
Nov  2 05:30:21 phillip-laptop kernel: [   34.767353] PCI: Bus 9, cardbus bridge: 0000:08:01.0
Nov  2 05:30:21 phillip-laptop kernel: [   34.767357]   IO window: 0000a000-0000a0ff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767365]   IO window: 0000a400-0000a4ff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767372]   PREFETCH window: d0000000-d3ffffff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767380]   MEM window: 80000000-83ffffff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767388] PCI: Bridge: 0000:00:14.4
Nov  2 05:30:21 phillip-laptop kernel: [   34.767393]   IO window: a000-bfff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767401]   MEM window: fca00000-feafffff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767408]   PREFETCH window: cff00000-dfefffff
Nov  2 05:30:21 phillip-laptop kernel: [   34.767437] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov  2 05:30:21 phillip-laptop kernel: [   34.767448] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov  2 05:30:21 phillip-laptop kernel: [   34.767459] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov  2 05:30:21 phillip-laptop kernel: [   34.767469] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov  2 05:30:21 phillip-laptop kernel: [   34.767501] ACPI: PCI Interrupt 0000:08:01.0[A] -> GSI 21 (level, low) -> IRQ 16
Nov  2 05:30:21 phillip-laptop kernel: [   34.767522] NET: Registered protocol family 2
Nov  2 05:30:21 phillip-laptop kernel: [   34.812367] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  2 05:30:21 phillip-laptop kernel: [   34.812661] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov  2 05:30:21 phillip-laptop kernel: [   34.814040] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  2 05:30:21 phillip-laptop kernel: [   34.815025] TCP: Hash tables configured (established 131072 bind 65536)
Nov  2 05:30:21 phillip-laptop kernel: [   34.815034] TCP reno registered
Nov  2 05:30:21 phillip-laptop kernel: [   34.824503] checking if image is initramfs... it is
Nov  2 05:30:21 phillip-laptop kernel: [   35.263715] Switched to high resolution mode on CPU 1
Nov  2 05:30:21 phillip-laptop kernel: [   35.267559] Switched to high resolution mode on CPU 0
Nov  2 05:30:21 phillip-laptop kernel: [   35.510206] Freeing initrd memory: 8588k freed
Nov  2 05:30:21 phillip-laptop kernel: [   35.510526] Simple Boot Flag at 0xff set to 0x1
Nov  2 05:30:21 phillip-laptop kernel: [   35.511406] audit: initializing netlink socket (disabled)
Nov  2 05:30:21 phillip-laptop kernel: [   35.511432] audit(1225603792.488:1): initialized
Nov  2 05:30:21 phillip-laptop kernel: [   35.511716] highmem bounce pool size: 64 pages
Nov  2 05:30:21 phillip-laptop kernel: [   35.514020] VFS: Disk quotas dquot_6.5.1
Nov  2 05:30:21 phillip-laptop kernel: [   35.514122] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  2 05:30:21 phillip-laptop kernel: [   35.514288] io scheduler noop registered
Nov  2 05:30:21 phillip-laptop kernel: [   35.514293] io scheduler anticipatory registered
Nov  2 05:30:21 phillip-laptop kernel: [   35.514297] io scheduler deadline registered
Nov  2 05:30:21 phillip-laptop kernel: [   35.514310] io scheduler cfq registered (default)
Nov  2 05:30:21 phillip-laptop kernel: [   35.514407] Boot video device is 0000:01:05.0
Nov  2 05:30:21 phillip-laptop kernel: [   35.514562] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov  2 05:30:21 phillip-laptop kernel: [   35.514599] assign_interrupt_mode Found MSI capability
Nov  2 05:30:21 phillip-laptop kernel: [   35.514642] Allocate Port Service[0000:00:04.0:pcie00]
Nov  2 05:30:21 phillip-laptop kernel: [   35.514740] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov  2 05:30:21 phillip-laptop kernel: [   35.514775] assign_interrupt_mode Found MSI capability
Nov  2 05:30:21 phillip-laptop kernel: [   35.514810] Allocate Port Service[0000:00:05.0:pcie00]
Nov  2 05:30:21 phillip-laptop kernel: [   35.514849] Allocate Port Service[0000:00:05.0:pcie02]
Nov  2 05:30:21 phillip-laptop kernel: [   35.514940] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov  2 05:30:21 phillip-laptop kernel: [   35.514975] assign_interrupt_mode Found MSI capability
Nov  2 05:30:21 phillip-laptop kernel: [   35.515010] Allocate Port Service[0000:00:06.0:pcie00]
Nov  2 05:30:21 phillip-laptop kernel: [   35.515101] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov  2 05:30:21 phillip-laptop kernel: [   35.515136] assign_interrupt_mode Found MSI capability
Nov  2 05:30:21 phillip-laptop kernel: [   35.515171] Allocate Port Service[0000:00:07.0:pcie00]
Nov  2 05:30:21 phillip-laptop kernel: [   35.515450] isapnp: Scanning for PnP cards...
Nov  2 05:30:21 phillip-laptop kernel: [   35.869020] isapnp: No Plug & Play device found
Nov  2 05:30:21 phillip-laptop kernel: [   35.901773] Real Time Clock Driver v1.12ac
Nov  2 05:30:21 phillip-laptop kernel: [   35.901945] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov  2 05:30:21 phillip-laptop kernel: [   35.903397] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov  2 05:30:21 phillip-laptop kernel: [   35.903483] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov  2 05:30:21 phillip-laptop kernel: [   35.903593] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov  2 05:30:21 phillip-laptop kernel: [   35.906022] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov  2 05:30:21 phillip-laptop kernel: [   35.906679] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  2 05:30:21 phillip-laptop kernel: [   35.906686] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov  2 05:30:21 phillip-laptop kernel: [   35.906691] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov  2 05:30:21 phillip-laptop kernel: [   35.906695] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov  2 05:30:21 phillip-laptop kernel: [   35.906700] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov  2 05:30:21 phillip-laptop kernel: [   35.923518] mice: PS/2 mouse device common for all mice
Nov  2 05:30:21 phillip-laptop kernel: [   35.923674] EISA: Probing bus 0 at eisa.0
Nov  2 05:30:21 phillip-laptop kernel: [   35.923700] Cannot allocate resource for EISA slot 4
Nov  2 05:30:21 phillip-laptop kernel: [   35.923713] Cannot allocate resource for EISA slot 7
Nov  2 05:30:21 phillip-laptop kernel: [   35.923717] Cannot allocate resource for EISA slot 8
Nov  2 05:30:21 phillip-laptop kernel: [   35.923721] EISA: Detected 0 cards.
Nov  2 05:30:21 phillip-laptop kernel: [   35.923727] cpuidle: using governor ladder
Nov  2 05:30:21 phillip-laptop kernel: [   35.923730] cpuidle: using governor menu
Nov  2 05:30:21 phillip-laptop kernel: [   35.923835] NET: Registered protocol family 1
Nov  2 05:30:21 phillip-laptop kernel: [   35.923870] Using IPI No-Shortcut mode
Nov  2 05:30:21 phillip-laptop kernel: [   35.923909] registered taskstats version 1
Nov  2 05:30:21 phillip-laptop kernel: [   35.924044]   Magic number: 0:633:465
Nov  2 05:30:21 phillip-laptop kernel: [   35.924195] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov  2 05:30:21 phillip-laptop kernel: [   35.924200] EDD information not available.
Nov  2 05:30:21 phillip-laptop kernel: [   35.924582] Freeing unused kernel memory: 368k freed
Nov  2 05:30:21 phillip-laptop kernel: [   35.924612] Write protecting the kernel read-only data: 801k
Nov  2 05:30:21 phillip-laptop kernel: [   35.955540] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov  2 05:30:21 phillip-laptop kernel: [   36.132640] vesafb: framebuffer at 0x90000000, mapped to 0xf8880000, using 4608k, total 16384k
Nov  2 05:30:21 phillip-laptop kernel: [   36.132656] vesafb: mode is 1024x768x24, linelength=3072, pages=6
Nov  2 05:30:21 phillip-laptop kernel: [   36.132661] vesafb: protected mode interface info at c000:516e
Nov  2 05:30:21 phillip-laptop kernel: [   36.132665] vesafb: pmi: set display start = c00c51dc, set palette = c00c5216
Nov  2 05:30:21 phillip-laptop kernel: [   36.132670] vesafb: pmi: ports = 7810 7816 7854 7838 783c 785c 7800 7804 78b0 78b2 78b4 
Nov  2 05:30:21 phillip-laptop kernel: [   36.132681] vesafb: scrolling: redraw
Nov  2 05:30:21 phillip-laptop kernel: [   36.132685] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Nov  2 05:30:21 phillip-laptop kernel: [   36.132815] Console: switching to colour frame buffer device 128x48
Nov  2 05:30:21 phillip-laptop kernel: [   36.138980] fb0: VESA VGA frame buffer device
Nov  2 05:30:21 phillip-laptop kernel: [   37.270406] fuse init (API version 7.9)
Nov  2 05:30:21 phillip-laptop kernel: [   37.290415] ACPI: SSDT 77FBE2A0, 0D1C (r1    AMI   CPU1PM        1 INTL 20051117)
Nov  2 05:30:21 phillip-laptop kernel: [   37.291788] ACPI: CPU0 (power states: C1[C1] C2[C2])
Nov  2 05:30:21 phillip-laptop kernel: [   37.291898] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov  2 05:30:21 phillip-laptop kernel: [   37.292122] ACPI: SSDT 77FBEFC0, 0D1C (r1    AMI   CPU2PM        1 INTL 20051117)
Nov  2 05:30:21 phillip-laptop kernel: [   37.293453] ACPI: CPU1 (power states: C1[C1] C2[C2])
Nov  2 05:30:21 phillip-laptop kernel: [   37.294869] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov  2 05:30:21 phillip-laptop kernel: [   37.297042] ACPI: Thermal Zone [THRM] (52 C)
Nov  2 05:30:21 phillip-laptop kernel: [   37.646261] usbcore: registered new interface driver usbfs
Nov  2 05:30:21 phillip-laptop kernel: [   37.646388] usbcore: registered new interface driver hub
Nov  2 05:30:21 phillip-laptop kernel: [   37.647229] usbcore: registered new device driver usb
Nov  2 05:30:21 phillip-laptop kernel: [   37.656541] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov  2 05:30:21 phillip-laptop kernel: [   37.656614] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 17
Nov  2 05:30:21 phillip-laptop kernel: [   37.656781] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov  2 05:30:21 phillip-laptop kernel: [   37.657278] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Nov  2 05:30:21 phillip-laptop kernel: [   37.661201] ohci_hcd 0000:00:13.0: irq 17, io mem 0xfebfe000
Nov  2 05:30:21 phillip-laptop kernel: [   37.693584] SCSI subsystem initialized
Nov  2 05:30:21 phillip-laptop kernel: [   37.711567] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov  2 05:30:21 phillip-laptop kernel: [   37.715887] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov  2 05:30:21 phillip-laptop kernel: [   37.724501] usb usb1: configuration #1 chosen from 1 choice
Nov  2 05:30:21 phillip-laptop kernel: [   37.724647] libata version 3.00 loaded.
Nov  2 05:30:21 phillip-laptop kernel: [   37.728545] hub 1-0:1.0: USB hub found
Nov  2 05:30:21 phillip-laptop kernel: [   37.732607] hub 1-0:1.0: 2 ports detected
Nov  2 05:30:21 phillip-laptop kernel: [   37.815636] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Nov  2 05:30:21 phillip-laptop kernel: [   37.840286] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 18
Nov  2 05:30:21 phillip-laptop kernel: [   37.844679] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov  2 05:30:21 phillip-laptop kernel: [   37.848925] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Nov  2 05:30:21 phillip-laptop kernel: [   37.853056] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfebfd000
Nov  2 05:30:21 phillip-laptop kernel: [   37.916169] usb usb2: configuration #1 chosen from 1 choice
Nov  2 05:30:21 phillip-laptop kernel: [   37.920296] hub 2-0:1.0: USB hub found
Nov  2 05:30:21 phillip-laptop kernel: [   37.924489] hub 2-0:1.0: 2 ports detected
Nov  2 05:30:21 phillip-laptop kernel: [   38.031978] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 19
Nov  2 05:30:21 phillip-laptop kernel: [   38.036390] ohci_hcd 0000:00:13.2: OHCI Host Controller
Nov  2 05:30:21 phillip-laptop kernel: [   38.040774] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Nov  2 05:30:21 phillip-laptop kernel: [   38.045219] ohci_hcd 0000:00:13.2: irq 19, io mem 0xfebfc000
Nov  2 05:30:21 phillip-laptop kernel: [   38.110846] usb usb3: configuration #1 chosen from 1 choice
Nov  2 05:30:21 phillip-laptop kernel: [   38.115336] hub 3-0:1.0: USB hub found
Nov  2 05:30:21 phillip-laptop kernel: [   38.119672] hub 3-0:1.0: 2 ports detected
Nov  2 05:30:21 phillip-laptop kernel: [   38.230639] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 18
Nov  2 05:30:21 phillip-laptop kernel: [   38.235109] ohci_hcd 0000:00:13.3: OHCI Host Controller
Nov  2 05:30:21 phillip-laptop kernel: [   38.239544] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Nov  2 05:30:21 phillip-laptop kernel: [   38.244010] ohci_hcd 0000:00:13.3: irq 18, io mem 0xfebfb000
Nov  2 05:30:21 phillip-laptop kernel: [   38.307498] usb usb4: configuration #1 chosen from 1 choice
Nov  2 05:30:21 phillip-laptop kernel: [   38.311727] hub 4-0:1.0: USB hub found
Nov  2 05:30:21 phillip-laptop kernel: [   38.315863] hub 4-0:1.0: 2 ports detected
Nov  2 05:30:21 phillip-laptop kernel: [   38.422288] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 19
Nov  2 05:30:21 phillip-laptop kernel: [   38.426506] ohci_hcd 0000:00:13.4: OHCI Host Controller
Nov  2 05:30:21 phillip-laptop kernel: [   38.430650] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Nov  2 05:30:21 phillip-laptop kernel: [   38.434861] ohci_hcd 0000:00:13.4: irq 19, io mem 0xfebfa000
Nov  2 05:30:21 phillip-laptop kernel: [   38.498139] usb usb5: configuration #1 chosen from 1 choice
Nov  2 05:30:21 phillip-laptop kernel: [   38.502269] hub 5-0:1.0: USB hub found
Nov  2 05:30:21 phillip-laptop kernel: [   38.506335] hub 5-0:1.0: 2 ports detected
Nov  2 05:30:21 phillip-laptop kernel: [   38.614200] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 20
Nov  2 05:30:21 phillip-laptop kernel: [   38.618557] ehci_hcd 0000:00:13.5: EHCI Host Controller
Nov  2 05:30:21 phillip-laptop kernel: [   38.622774] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Nov  2 05:30:21 phillip-laptop kernel: [   38.627427] ehci_hcd 0000:00:13.5: debug port 1
Nov  2 05:30:21 phillip-laptop kernel: [   38.632316] ehci_hcd 0000:00:13.5: irq 20, io mem 0xfebff800
Nov  2 05:30:21 phillip-laptop kernel: [   38.649775] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  2 05:30:21 phillip-laptop kernel: [   38.654390] usb usb6: configuration #1 chosen from 1 choice
Nov  2 05:30:21 phillip-laptop kernel: [   38.659222] hub 6-0:1.0: USB hub found
Nov  2 05:30:21 phillip-laptop kernel: [   38.663704] hub 6-0:1.0: 10 ports detected
Nov  2 05:30:21 phillip-laptop kernel: [   38.769756] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Nov  2 05:30:21 phillip-laptop kernel: [   38.774186] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
Nov  2 05:30:21 phillip-laptop kernel: [   38.778555] SB600_PATA: not 100% native mode: will probe irqs later
Nov  2 05:30:21 phillip-laptop kernel: [   38.783143]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:DMA
Nov  2 05:30:21 phillip-laptop kernel: [   38.787919] Probing IDE interface ide0...
Nov  2 05:30:21 phillip-laptop kernel: [   39.576623] hdb: HL-DT-ST DVDRAM GSA-T20N, ATAPI CD/DVD-ROM drive
Nov  2 05:30:21 phillip-laptop kernel: [   39.859744] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Nov  2 05:30:21 phillip-laptop kernel: [   39.860558] hdb: UDMA/33 mode selected
Nov  2 05:30:21 phillip-laptop kernel: [   39.865188] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov  2 05:30:21 phillip-laptop kernel: [   39.872583] 8139cp 0000:08:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Nov  2 05:30:21 phillip-laptop kernel: [   39.876969] 8139cp 0000:08:07.0: Try the "8139too" driver instead.
Nov  2 05:30:21 phillip-laptop kernel: [   39.881464] ahci 0000:00:12.0: version 3.0
Nov  2 05:30:21 phillip-laptop kernel: [   39.881506] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 21
Nov  2 05:30:21 phillip-laptop kernel: [   39.886150] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Nov  2 05:30:21 phillip-laptop kernel: [   39.890586] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Nov  2 05:30:21 phillip-laptop kernel: [   39.894975] 8139too Fast Ethernet driver 0.9.28
Nov  2 05:30:21 phillip-laptop kernel: [   40.898027] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Nov  2 05:30:21 phillip-laptop kernel: [   40.902492] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pio 
Nov  2 05:30:21 phillip-laptop kernel: [   40.907451] scsi0 : ahci
Nov  2 05:30:21 phillip-laptop kernel: [   40.912348] scsi1 : ahci
Nov  2 05:30:21 phillip-laptop kernel: [   40.916822] scsi2 : ahci
Nov  2 05:30:21 phillip-laptop kernel: [   40.921199] scsi3 : ahci
Nov  2 05:30:21 phillip-laptop kernel: [   40.925532] ata1: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 21
Nov  2 05:30:21 phillip-laptop kernel: [   40.929833] ata2: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 21
Nov  2 05:30:21 phillip-laptop kernel: [   40.934040] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 21
Nov  2 05:30:21 phillip-laptop kernel: [   40.938197] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 21
Nov  2 05:30:21 phillip-laptop kernel: [   41.418106] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  2 05:30:21 phillip-laptop kernel: [   41.423233] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
Nov  2 05:30:21 phillip-laptop kernel: [   41.427362] ata1.00: 234441648 sectors, multi 0: LBA48 NCQ (depth 31/32)
Nov  2 05:30:21 phillip-laptop kernel: [   41.432586] ata1.00: configured for UDMA/100
Nov  2 05:30:21 phillip-laptop kernel: [   41.744550] ata2: SATA link down (SStatus 0 SControl 300)
Nov  2 05:30:21 phillip-laptop kernel: [   42.060014] ata3: SATA link down (SStatus 0 SControl 300)
Nov  2 05:30:21 phillip-laptop kernel: [   42.376477] ata4: SATA link down (SStatus 0 SControl 300)
Nov  2 05:30:21 phillip-laptop kernel: [   42.380602] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
Nov  2 05:30:21 phillip-laptop kernel: [   42.384863] ACPI: PCI Interrupt 0000:08:07.0[A] -> GSI 20 (level, low) -> IRQ 22
Nov  2 05:30:21 phillip-laptop kernel: [   42.390174] eth0: RealTek RTL8139 at 0xb800, 00:1d:60:49:6c:65, IRQ 22
Nov  2 05:30:21 phillip-laptop kernel: [   42.394215] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Nov  2 05:30:21 phillip-laptop kernel: [   42.411783] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Nov  2 05:30:21 phillip-laptop kernel: [   42.416167] Uniform CD-ROM driver Revision: 3.20
Nov  2 05:30:21 phillip-laptop kernel: [   42.420211] Driver 'sd' needs updating - please use bus_type methods
Nov  2 05:30:21 phillip-laptop kernel: [   42.425096] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov  2 05:30:21 phillip-laptop kernel: [   42.429459] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 05:30:21 phillip-laptop kernel: [   42.433804] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 05:30:21 phillip-laptop kernel: [   42.433855] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 05:30:21 phillip-laptop kernel: [   42.438054] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov  2 05:30:21 phillip-laptop kernel: [   42.442229] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 05:30:21 phillip-laptop kernel: [   42.446297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 05:30:21 phillip-laptop kernel: [   42.446324] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 05:30:21 phillip-laptop kernel: [   42.450453]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
Nov  2 05:30:21 phillip-laptop kernel: [   42.916378] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  2 05:30:21 phillip-laptop kernel: [   42.926367] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov  2 05:30:21 phillip-laptop kernel: [   43.391964] Attempting manual resume
Nov  2 05:30:21 phillip-laptop kernel: [   43.395978] swsusp: Resume From Partition 8:6
Nov  2 05:30:21 phillip-laptop kernel: [   43.395979] PM: Checking swsusp image.
Nov  2 05:30:21 phillip-laptop kernel: [   43.396135] PM: Resume from disk failed.
Nov  2 05:30:21 phillip-laptop kernel: [   43.444475] kjournald starting.  Commit interval 5 seconds
Nov  2 05:30:21 phillip-laptop kernel: [   43.444493] EXT3-fs: mounted filesystem with ordered data mode.
Nov  2 05:30:21 phillip-laptop kernel: [   52.763038] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov  2 05:30:21 phillip-laptop kernel: [   52.845378] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Nov  2 05:30:21 phillip-laptop kernel: [   53.553440] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  2 05:30:21 phillip-laptop kernel: [   53.589125] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  2 05:30:21 phillip-laptop kernel: [   53.644510] Linux agpgart interface v0.102
Nov  2 05:30:21 phillip-laptop kernel: [   53.816801] input: Power Button (FF) as /devices/virtual/input/input2
Nov  2 05:30:21 phillip-laptop kernel: [   53.844011] ACPI: Power Button (FF) [PWRF]
Nov  2 05:30:21 phillip-laptop kernel: [   53.847666] input: Lid Switch as /devices/virtual/input/input3
Nov  2 05:30:21 phillip-laptop kernel: [   53.853734] ACPI: Lid Switch [LID]
Nov  2 05:30:21 phillip-laptop kernel: [   53.857364] input: Power Button (CM) as /devices/virtual/input/input4
Nov  2 05:30:21 phillip-laptop kernel: [   53.883947] ACPI: Power Button (CM) [PWRB]
Nov  2 05:30:21 phillip-laptop kernel: [   53.887584] input: Sleep Button (CM) as /devices/virtual/input/input5
Nov  2 05:30:21 phillip-laptop kernel: [   53.899899] ACPI: Sleep Button (CM) [SLPB]
Nov  2 05:30:21 phillip-laptop kernel: [   54.152397] asus-laptop: Asus Laptop Support version 0.42
Nov  2 05:30:21 phillip-laptop kernel: [   54.156187] asus-laptop: BSTS called, 0x22 returned
Nov  2 05:30:21 phillip-laptop kernel: [   54.159545] asus-laptop:   X51R model detected
Nov  2 05:30:21 phillip-laptop kernel: [   54.393739] ACPI: AC Adapter [AC0] (on-line)
Nov  2 05:30:21 phillip-laptop kernel: [   54.573993] ACPI: Battery Slot [BAT0] (battery present)
Nov  2 05:30:21 phillip-laptop kernel: [   54.626754] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6
Nov  2 05:30:21 phillip-laptop kernel: [   54.658634] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov  2 05:30:21 phillip-laptop kernel: [   55.150991] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Nov  2 05:30:21 phillip-laptop kernel: [   55.353254] Yenta: CardBus bridge found at 0000:08:01.0 [1043:1627]
Nov  2 05:30:21 phillip-laptop kernel: [   55.393184] input: PC Speaker as /devices/platform/pcspkr/input/input7
Nov  2 05:30:21 phillip-laptop kernel: [   55.483067] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
Nov  2 05:30:21 phillip-laptop kernel: [   55.486422] Socket status: 30000006
Nov  2 05:30:21 phillip-laptop kernel: [   55.489708] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
Nov  2 05:30:21 phillip-laptop kernel: [   55.493141] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
Nov  2 05:30:21 phillip-laptop kernel: [   55.496706] cs: IO port probe 0xa000-0xbfff: clean.
Nov  2 05:30:21 phillip-laptop kernel: [   55.500837] pcmcia: parent PCI bridge Memory window: 0xfca00000 - 0xfeafffff
Nov  2 05:30:21 phillip-laptop kernel: [   55.505035] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xdfefffff
Nov  2 05:30:21 phillip-laptop kernel: [   55.674429] sdhci: Secure Digital Host Controller Interface driver
Nov  2 05:30:21 phillip-laptop kernel: [   55.678104] sdhci: Copyright(c) Pierre Ossman
Nov  2 05:30:21 phillip-laptop kernel: [   55.681802] sdhci: SDHCI controller found at 0000:08:01.1 [1180:0822] (rev 17)
Nov  2 05:30:21 phillip-laptop kernel: [   55.685757] ACPI: PCI Interrupt 0000:08:01.1[C] -> GSI 23 (level, low) -> IRQ 23
Nov  2 05:30:21 phillip-laptop kernel: [   55.689726] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Nov  2 05:30:21 phillip-laptop kernel: [   55.694332] mmc0: SDHCI at 0xfeaffc00 irq 23 DMA
Nov  2 05:30:21 phillip-laptop kernel: [   56.076872] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
Nov  2 05:30:21 phillip-laptop kernel: [   56.356374] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
Nov  2 05:30:21 phillip-laptop kernel: [   56.400388] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Nov  2 05:30:21 phillip-laptop kernel: [   57.277746] cs: IO port probe 0x100-0x3af: clean.
Nov  2 05:30:21 phillip-laptop kernel: [   57.284220] cs: IO port probe 0x3e0-0x4ff: clean.
Nov  2 05:30:21 phillip-laptop kernel: [   57.289310] cs: IO port probe 0x820-0x8ff: clean.
Nov  2 05:30:21 phillip-laptop kernel: [   57.293768] cs: IO port probe 0xc00-0xcf7: clean.
Nov  2 05:30:21 phillip-laptop kernel: [   57.298681] cs: IO port probe 0xa00-0xaff: clean.
Nov  2 05:30:21 phillip-laptop kernel: [   58.285512] lp: driver loaded but no devices found
Nov  2 05:30:21 phillip-laptop kernel: [   58.360042] ath_hal: module license 'Proprietary' taints kernel.
Nov  2 05:30:21 phillip-laptop kernel: [   58.368426] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
Nov  2 05:30:21 phillip-laptop kernel: [   58.485693] wlan: trunk
Nov  2 05:30:21 phillip-laptop kernel: [   58.537726] ath_pci: trunk
Nov  2 05:30:21 phillip-laptop kernel: [   58.542450] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Nov  2 05:30:21 phillip-laptop kernel: [   58.546952] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov  2 05:30:21 phillip-laptop kernel: [   59.038999] MadWifi: ath_attach: Switching rfkill capability off
Nov  2 05:30:21 phillip-laptop kernel: [   59.090263] ath_rate_sample: 1.2 (trunk)
Nov  2 05:30:21 phillip-laptop kernel: [   59.095043] MadWifi: ath_attach: Switching per-packet transmit power control off
Nov  2 05:30:21 phillip-laptop kernel: [   59.099706] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Nov  2 05:30:21 phillip-laptop kernel: [   59.104746] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov  2 05:30:21 phillip-laptop kernel: [   59.109205] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Nov  2 05:30:21 phillip-laptop kernel: [   59.113584] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
Nov  2 05:30:21 phillip-laptop kernel: [   59.117881] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
Nov  2 05:30:21 phillip-laptop kernel: [   59.122125] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
Nov  2 05:30:21 phillip-laptop kernel: [   59.126353] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
Nov  2 05:30:21 phillip-laptop kernel: [   59.130552] wifi0: ath_announce: Use hw queue 8 for CAB traffic
Nov  2 05:30:21 phillip-laptop kernel: [   59.134693] wifi0: ath_announce: Use hw queue 9 for beacons
Nov  2 05:30:21 phillip-laptop kernel: [   59.157718] ath_pci: wifi0: Atheros 5424/2424: mem=0xf89f0000, irq=17
Nov  2 05:30:21 phillip-laptop kernel: [   59.265006] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFB) is beyond end of object [20070126]
Nov  2 05:30:21 phillip-laptop kernel: [   59.269592] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PSS] (Node f7c49b88), AE_AML_PACKAGE_LIMIT
Nov  2 05:30:21 phillip-laptop kernel: [   59.273919] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Nov  2 05:30:21 phillip-laptop kernel: [   59.278405] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFB) is beyond end of object [20070126]
Nov  2 05:30:21 phillip-laptop kernel: [   59.282742] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PSS] (Node f7c49d98), AE_AML_PACKAGE_LIMIT
Nov  2 05:30:21 phillip-laptop kernel: [   59.287153] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Nov  2 05:30:21 phillip-laptop kernel: [   59.433840] Adding 872480k swap on /dev/sda6.  Priority:-1 extents:1 across:872480k
Nov  2 05:30:21 phillip-laptop kernel: [   59.987665] EXT3 FS on sda4, internal journal
Nov  2 05:30:21 phillip-laptop kernel: [   61.450473] NET: Registered protocol family 10
Nov  2 05:30:21 phillip-laptop kernel: [   61.450861] lo: Disabled Privacy Extensions
Nov  2 05:30:21 phillip-laptop kernel: [   61.509541] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov  2 05:30:21 phillip-laptop kernel: [   62.492573] No dock devices found.
Nov  2 05:30:21 phillip-laptop kernel: [   63.922427] ppdev: user-space parallel port driver
Nov  2 05:30:22 phillip-laptop kernel: [   64.110515] audit(1225603822.014:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5416 profile="/usr/sbin/cupsd" namespace="default"
Nov  2 05:30:22 phillip-laptop kernel: [   64.415870] apm: BIOS not found.


```

thanks...

Update to msgs

```

Nov 16 06:45:59 phillip-laptop kernel: Loaded 27897 symbols from /boot/System.map-2.6.24-21-generic.
Nov 16 06:45:59 phillip-laptop kernel: Symbols match kernel version 2.6.24.
Nov 16 06:46:00 phillip-laptop kernel: Loaded 22660 symbols from 107 modules.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fa8000 (usable)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fa8000 - 0000000077fb0000 (ACPI NVS)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fb0000 - 0000000077fbe000 (ACPI data)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fbe000 - 0000000077ff0000 (ACPI NVS)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077ff0000 - 0000000078000000 (reserved)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] 1023MB HIGHMEM available.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] 896MB LOWMEM available.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] found SMP MP-table at 000ff780
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 491432) 0 entries of 256 used
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Zone PFN ranges:
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   DMA             0 ->     4096
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   HighMem    229376 ->   491432
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Movable zone start PFN for each node
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]     0:        0 ->   491432
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] On node 0 totalpages: 491432
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   HighMem zone: 2047 pages used for memmap
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   HighMem zone: 260009 pages, LIFO batch:31
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] DMI 2.4 present.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7F50 checksum 0
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: RSDP 000F7F50, 0024 (r2 ACPIAM)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: XSDT 77FB0100, 0054 (r1 _ASUS_ Notebook  7000731 MSFT       97)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: FACP 77FB0290, 00F4 (r3 A.M.I  OEMFACP   7000731 MSFT       97)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: DSDT 77FB0630, 77A4 (r1  T12R0 T12R0000        0 INTL 20051117)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: FACS 77FBE000, 0040
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: APIC 77FB0390, 005C (r1 A.M.I  OEMAPIC   7000731 MSFT       97)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: MCFG 77FB03F0, 003C (r1 A.M.I  OEMMCFG   7000731 MSFT       97)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: SLIC 77FB0430, 0176 (r1 _ASUS_ Notebook  7000731 MSFT       97)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: BOOT 77FB0600, 0028 (r1 A.M.I  OEMBOOT   7000731 MSFT       97)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: OEMB 77FBE040, 005B (r1 A.M.I  AMI_OEM   7000731 MSFT       97)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Processor #0 6:14 APIC version 20
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Processor #1 6:14 APIC version 20
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:86e00000)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487593
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Kernel command line: root=UUID=3c071645-e73d-42b0-95ae-d796b29b38b3 ro splash vga=792
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Initializing CPU#0
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 16 06:46:00 phillip-laptop kernel: [    0.000000] Detected 1862.201 MHz processor.
Nov 16 06:46:00 phillip-laptop kernel: [   22.773534] Console: colour dummy device 80x25
Nov 16 06:46:00 phillip-laptop kernel: [   22.773539] console [tty0] enabled
Nov 16 06:46:00 phillip-laptop kernel: [   22.774581] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 16 06:46:00 phillip-laptop kernel: [   22.775299] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 16 06:46:00 phillip-laptop kernel: [   22.887606] Memory: 1935620k/1965728k available (2177k kernel code, 28936k reserved, 1005k data, 368k init, 1048224k highmem)
Nov 16 06:46:00 phillip-laptop kernel: [   22.887629] virtual kernel memory layout:
Nov 16 06:46:00 phillip-laptop kernel: [   22.887630]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Nov 16 06:46:00 phillip-laptop kernel: [   22.887631]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 16 06:46:00 phillip-laptop kernel: [   22.887632]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov 16 06:46:00 phillip-laptop kernel: [   22.887633]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov 16 06:46:00 phillip-laptop kernel: [   22.887635]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Nov 16 06:46:00 phillip-laptop kernel: [   22.887636]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
Nov 16 06:46:00 phillip-laptop kernel: [   22.887637]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
Nov 16 06:46:00 phillip-laptop kernel: [   22.887658] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 16 06:46:00 phillip-laptop kernel: [   22.887727] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Nov 16 06:46:00 phillip-laptop kernel: [   22.967634] Calibrating delay using timer specific routine.. 3728.23 BogoMIPS (lpj=7456463)
Nov 16 06:46:00 phillip-laptop kernel: [   22.967686] Security Framework initialized
Nov 16 06:46:00 phillip-laptop kernel: [   22.967702] SELinux:  Disabled at boot.
Nov 16 06:46:00 phillip-laptop kernel: [   22.967727] AppArmor: AppArmor initialized
Nov 16 06:46:00 phillip-laptop kernel: [   22.967733] Failure registering capabilities with primary security module.
Nov 16 06:46:00 phillip-laptop kernel: [   22.967746] Mount-cache hash table entries: 512
Nov 16 06:46:00 phillip-laptop kernel: [   22.967933] Initializing cgroup subsys ns
Nov 16 06:46:00 phillip-laptop kernel: [   22.967947] Initializing cgroup subsys cpuacct
Nov 16 06:46:00 phillip-laptop kernel: [   22.967965] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
Nov 16 06:46:00 phillip-laptop kernel: [   22.967973] monitor/mwait feature present.
Nov 16 06:46:00 phillip-laptop kernel: [   22.967977] using mwait in idle threads.
Nov 16 06:46:00 phillip-laptop kernel: [   22.967984] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 16 06:46:00 phillip-laptop kernel: [   22.967988] CPU: L2 cache: 1024K
Nov 16 06:46:00 phillip-laptop kernel: [   22.967993] CPU: Physical Processor ID: 0
Nov 16 06:46:00 phillip-laptop kernel: [   22.967997] CPU: Processor Core ID: 0
Nov 16 06:46:00 phillip-laptop kernel: [   22.968001] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
Nov 16 06:46:00 phillip-laptop kernel: [   22.968014] Compat vDSO mapped to ffffe000.
Nov 16 06:46:00 phillip-laptop kernel: [   22.968033] Checking 'hlt' instruction... OK.
Nov 16 06:46:00 phillip-laptop kernel: [   22.984030] SMP alternatives: switching to UP code
Nov 16 06:46:00 phillip-laptop kernel: [   22.985895] Early unpacking initramfs... done
Nov 16 06:46:00 phillip-laptop kernel: [   23.327013] ACPI: Core revision 20070126
Nov 16 06:46:00 phillip-laptop kernel: [   23.327109] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 16 06:46:00 phillip-laptop kernel: [   23.332338] CPU0: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
Nov 16 06:46:00 phillip-laptop kernel: [   23.332362] SMP alternatives: switching to SMP code
Nov 16 06:46:00 phillip-laptop kernel: [   23.333121] Booting processor 1/1 eip 3000
Nov 16 06:46:00 phillip-laptop kernel: [   23.343289] Initializing CPU#1
Nov 16 06:46:00 phillip-laptop kernel: [   23.422901] Calibrating delay using timer specific routine.. 3724.58 BogoMIPS (lpj=7449173)
Nov 16 06:46:00 phillip-laptop kernel: [   23.422910] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
Nov 16 06:46:00 phillip-laptop kernel: [   23.422915] monitor/mwait feature present.
Nov 16 06:46:00 phillip-laptop kernel: [   23.422919] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 16 06:46:00 phillip-laptop kernel: [   23.422921] CPU: L2 cache: 1024K
Nov 16 06:46:00 phillip-laptop kernel: [   23.422923] CPU: Physical Processor ID: 0
Nov 16 06:46:00 phillip-laptop kernel: [   23.422924] CPU: Processor Core ID: 1
Nov 16 06:46:00 phillip-laptop kernel: [   23.422926] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
Nov 16 06:46:00 phillip-laptop kernel: [   23.423478] CPU1: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
Nov 16 06:46:00 phillip-laptop kernel: [   23.423521] Total of 2 processors activated (7452.81 BogoMIPS).
Nov 16 06:46:00 phillip-laptop kernel: [   23.423697] ENABLING IO-APIC IRQs
Nov 16 06:46:00 phillip-laptop kernel: [   23.423887] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 16 06:46:00 phillip-laptop kernel: [   23.570806] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov 16 06:46:00 phillip-laptop kernel: [   23.590796] Brought up 2 CPUs
Nov 16 06:46:00 phillip-laptop kernel: [   23.590823] CPU0 attaching sched-domain:
Nov 16 06:46:00 phillip-laptop kernel: [   23.590826]  domain 0: span 03
Nov 16 06:46:00 phillip-laptop kernel: [   23.590828]   groups: 01 02
Nov 16 06:46:00 phillip-laptop kernel: [   23.590831] CPU1 attaching sched-domain:
Nov 16 06:46:00 phillip-laptop kernel: [   23.590832]  domain 0: span 03
Nov 16 06:46:00 phillip-laptop kernel: [   23.590834]   groups: 02 01
Nov 16 06:46:00 phillip-laptop kernel: [   23.591120] net_namespace: 64 bytes
Nov 16 06:46:00 phillip-laptop kernel: [   23.591134] Booting paravirtualized kernel on bare hardware
Nov 16 06:46:00 phillip-laptop kernel: [   23.591586] Time:  6:45:33  Date: 11/16/08
Nov 16 06:46:00 phillip-laptop kernel: [   23.591622] NET: Registered protocol family 16
Nov 16 06:46:00 phillip-laptop kernel: [   23.591897] EISA bus registered
Nov 16 06:46:00 phillip-laptop kernel: [   23.591904] ACPI: bus type pci registered
Nov 16 06:46:00 phillip-laptop kernel: [   23.592193] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=9
Nov 16 06:46:00 phillip-laptop kernel: [   23.592201] PCI: Using configuration type 1
Nov 16 06:46:00 phillip-laptop kernel: [   23.592220] Setting up standard PCI resources
Nov 16 06:46:00 phillip-laptop kernel: [   23.592716] mtrr: your CPUs had inconsistent variable MTRR settings
Nov 16 06:46:00 phillip-laptop kernel: [   23.592721] mtrr: probably your BIOS does not setup all CPUs.
Nov 16 06:46:00 phillip-laptop kernel: [   23.592725] mtrr: corrected configuration.
Nov 16 06:46:00 phillip-laptop kernel: [   23.597049] ACPI: EC: Look up EC in DSDT
Nov 16 06:46:00 phillip-laptop kernel: [   23.642710] ACPI: Interpreter enabled
Nov 16 06:46:00 phillip-laptop kernel: [   23.642717] ACPI: (supports S0 S1 S3 S4 S5)
Nov 16 06:46:00 phillip-laptop kernel: [   23.642738] ACPI: Using IOAPIC for interrupt routing
Nov 16 06:46:00 phillip-laptop kernel: [   23.650361] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
Nov 16 06:46:00 phillip-laptop kernel: [   23.650369] ACPI: EC: driver started in poll mode
Nov 16 06:46:00 phillip-laptop kernel: [   23.650509] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 16 06:46:00 phillip-laptop kernel: [   23.650825] pci 0000:00:12.0: set SATA to AHCI mode
Nov 16 06:46:00 phillip-laptop kernel: [   23.652684] PCI: Transparent bridge - 0000:00:14.4
Nov 16 06:46:00 phillip-laptop kernel: [   23.652791] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 16 06:46:00 phillip-laptop kernel: [   23.652935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Nov 16 06:46:00 phillip-laptop kernel: [   23.653089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
Nov 16 06:46:00 phillip-laptop kernel: [   23.653209] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
Nov 16 06:46:00 phillip-laptop kernel: [   23.653326] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Nov 16 06:46:00 phillip-laptop kernel: [   23.653458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Nov 16 06:46:00 phillip-laptop kernel: [   23.653616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
Nov 16 06:46:00 phillip-laptop kernel: [   23.659029] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *11 12)
Nov 16 06:46:00 phillip-laptop kernel: [   23.659189] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 12)
Nov 16 06:46:00 phillip-laptop kernel: [   23.659344] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 12)
Nov 16 06:46:00 phillip-laptop kernel: [   23.659498] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 12) *10
Nov 16 06:46:00 phillip-laptop kernel: [   23.659653] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 12)
Nov 16 06:46:00 phillip-laptop kernel: [   23.659806] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 12)
Nov 16 06:46:00 phillip-laptop kernel: [   23.659959] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 12)
Nov 16 06:46:00 phillip-laptop kernel: [   23.660113] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 12)
Nov 16 06:46:00 phillip-laptop kernel: [   23.660269] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 16 06:46:00 phillip-laptop kernel: [   23.660310] pnp: PnP ACPI init
Nov 16 06:46:00 phillip-laptop kernel: [   23.660319] ACPI: bus type pnp registered
Nov 16 06:46:00 phillip-laptop kernel: [   23.662775] pnp: PnP ACPI: found 12 devices
Nov 16 06:46:00 phillip-laptop kernel: [   23.662781] ACPI: ACPI bus type pnp unregistered
Nov 16 06:46:00 phillip-laptop kernel: [   23.662787] PnPBIOS: Disabled by ACPI PNP
Nov 16 06:46:00 phillip-laptop kernel: [   23.663087] PCI: Using ACPI for IRQ routing
Nov 16 06:46:00 phillip-laptop kernel: [   23.663092] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 16 06:46:00 phillip-laptop kernel: [   23.706619] NET: Registered protocol family 8
Nov 16 06:46:00 phillip-laptop kernel: [   23.706624] NET: Registered protocol family 20
Nov 16 06:46:00 phillip-laptop kernel: [   23.706702] AppArmor: AppArmor Filesystem Enabled
Nov 16 06:46:00 phillip-laptop kernel: [   23.710460] Time: tsc clocksource has been installed.
Nov 16 06:46:00 phillip-laptop kernel: [   23.722620] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722629] system 00:05: ioport range 0x40b-0x40b has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722634] system 00:05: ioport range 0x4d6-0x4d6 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722640] system 00:05: ioport range 0xc00-0xc01 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722645] system 00:05: ioport range 0xc14-0xc14 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722650] system 00:05: ioport range 0xc50-0xc51 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722655] system 00:05: ioport range 0xc52-0xc52 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722660] system 00:05: ioport range 0xc6c-0xc6c has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722665] system 00:05: ioport range 0xc6f-0xc6f has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722670] system 00:05: ioport range 0xcd0-0xcd1 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722676] system 00:05: ioport range 0xcd2-0xcd3 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722681] system 00:05: ioport range 0xcd4-0xcd5 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722686] system 00:05: ioport range 0xcd6-0xcd7 has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722691] system 00:05: ioport range 0xcd8-0xcdf has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722696] system 00:05: ioport range 0x800-0x89f has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722701] system 00:05: ioport range 0xb00-0xb1f could not be reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722707] system 00:05: ioport range 0x900-0x90f has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722712] system 00:05: ioport range 0x910-0x91f has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722717] system 00:05: ioport range 0xfe00-0xfefe has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722722] system 00:05: ioport range 0x4000-0x40fe has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722729] system 00:05: iomem range 0xfed20000-0xfed3ffff has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722734] system 00:05: iomem range 0xfed45000-0xfed89fff has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722740] system 00:05: iomem range 0xffb80000-0xffbfffff could not be reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722747] system 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722758] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722764] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722773] system 00:09: ioport range 0x25c-0x25c has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722778] system 00:09: ioport range 0x25d-0x25d has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722783] system 00:09: ioport range 0x25e-0x25e has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722788] system 00:09: ioport range 0x25f-0x25f has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722797] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722806] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722811] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722816] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722822] system 00:0b: iomem range 0x100000-0x77ffffff could not be reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.722828] system 00:0b: iomem range 0x0-0x0 could not be reserved
Nov 16 06:46:00 phillip-laptop kernel: [   23.753301] PCI: Bridge: 0000:00:01.0
Nov 16 06:46:00 phillip-laptop kernel: [   23.753306]   IO window: 7000-7fff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753311]   MEM window: f8800000-f88fffff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753316]   PREFETCH window: 8ff00000-afefffff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753322] PCI: Bridge: 0000:00:04.0
Nov 16 06:46:00 phillip-laptop kernel: [   23.753325]   IO window: disabled.
Nov 16 06:46:00 phillip-laptop kernel: [   23.753330]   MEM window: f8900000-f89fffff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753335]   PREFETCH window: disabled.
Nov 16 06:46:00 phillip-laptop kernel: [   23.753340] PCI: Bridge: 0000:00:05.0
Nov 16 06:46:00 phillip-laptop kernel: [   23.753344]   IO window: 8000-9fff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753350]   MEM window: f8a00000-fc9fffff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753355]   PREFETCH window: aff00000-cfefffff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753360] PCI: Bridge: 0000:00:06.0
Nov 16 06:46:00 phillip-laptop kernel: [   23.753363]   IO window: disabled.
Nov 16 06:46:00 phillip-laptop kernel: [   23.753368]   MEM window: disabled.
Nov 16 06:46:00 phillip-laptop kernel: [   23.753372]   PREFETCH window: disabled.
Nov 16 06:46:00 phillip-laptop kernel: [   23.753378] PCI: Bridge: 0000:00:07.0
Nov 16 06:46:00 phillip-laptop kernel: [   23.753381]   IO window: disabled.
Nov 16 06:46:00 phillip-laptop kernel: [   23.753386]   MEM window: disabled.
Nov 16 06:46:00 phillip-laptop kernel: [   23.753390]   PREFETCH window: disabled.
Nov 16 06:46:00 phillip-laptop kernel: [   23.753404] PCI: Bus 9, cardbus bridge: 0000:08:01.0
Nov 16 06:46:00 phillip-laptop kernel: [   23.753409]   IO window: 0000a000-0000a0ff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753416]   IO window: 0000a400-0000a4ff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753424]   PREFETCH window: d0000000-d3ffffff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753432]   MEM window: 80000000-83ffffff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753439] PCI: Bridge: 0000:00:14.4
Nov 16 06:46:00 phillip-laptop kernel: [   23.753444]   IO window: a000-bfff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753452]   MEM window: fca00000-feafffff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753459]   PREFETCH window: cff00000-dfefffff
Nov 16 06:46:00 phillip-laptop kernel: [   23.753489] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 16 06:46:00 phillip-laptop kernel: [   23.753500] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov 16 06:46:00 phillip-laptop kernel: [   23.753510] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 16 06:46:00 phillip-laptop kernel: [   23.753521] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 16 06:46:00 phillip-laptop kernel: [   23.753551] ACPI: PCI Interrupt 0000:08:01.0[A] -> GSI 21 (level, low) -> IRQ 16
Nov 16 06:46:00 phillip-laptop kernel: [   23.753572] NET: Registered protocol family 2
Nov 16 06:46:00 phillip-laptop kernel: [   23.798550] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 16 06:46:00 phillip-laptop kernel: [   23.798858] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 16 06:46:00 phillip-laptop kernel: [   23.800228] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 16 06:46:00 phillip-laptop kernel: [   23.801210] TCP: Hash tables configured (established 131072 bind 65536)
Nov 16 06:46:00 phillip-laptop kernel: [   23.801220] TCP reno registered
Nov 16 06:46:00 phillip-laptop kernel: [   23.810671] checking if image is initramfs... it is
Nov 16 06:46:00 phillip-laptop kernel: [   24.253609] Switched to high resolution mode on CPU 0
Nov 16 06:46:00 phillip-laptop kernel: [   24.253731] Switched to high resolution mode on CPU 1
Nov 16 06:46:00 phillip-laptop kernel: [   24.496114] Freeing initrd memory: 8588k freed
Nov 16 06:46:00 phillip-laptop kernel: [   24.496430] Simple Boot Flag at 0xff set to 0x1
Nov 16 06:46:00 phillip-laptop kernel: [   24.497373] audit: initializing netlink socket (disabled)
Nov 16 06:46:00 phillip-laptop kernel: [   24.497400] audit(1226817933.484:1): initialized
Nov 16 06:46:00 phillip-laptop kernel: [   24.497684] highmem bounce pool size: 64 pages
Nov 16 06:46:00 phillip-laptop kernel: [   24.499931] VFS: Disk quotas dquot_6.5.1
Nov 16 06:46:00 phillip-laptop kernel: [   24.500025] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 16 06:46:00 phillip-laptop kernel: [   24.500196] io scheduler noop registered
Nov 16 06:46:00 phillip-laptop kernel: [   24.500201] io scheduler anticipatory registered
Nov 16 06:46:00 phillip-laptop kernel: [   24.500206] io scheduler deadline registered
Nov 16 06:46:00 phillip-laptop kernel: [   24.500221] io scheduler cfq registered (default)
Nov 16 06:46:00 phillip-laptop kernel: [   24.500314] Boot video device is 0000:01:05.0
Nov 16 06:46:00 phillip-laptop kernel: [   24.500466] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 16 06:46:00 phillip-laptop kernel: [   24.500502] assign_interrupt_mode Found MSI capability
Nov 16 06:46:00 phillip-laptop kernel: [   24.500545] Allocate Port Service[0000:00:04.0:pcie00]
Nov 16 06:46:00 phillip-laptop kernel: [   24.500637] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov 16 06:46:00 phillip-laptop kernel: [   24.500672] assign_interrupt_mode Found MSI capability
Nov 16 06:46:00 phillip-laptop kernel: [   24.500707] Allocate Port Service[0000:00:05.0:pcie00]
Nov 16 06:46:00 phillip-laptop kernel: [   24.500745] Allocate Port Service[0000:00:05.0:pcie02]
Nov 16 06:46:00 phillip-laptop kernel: [   24.500827] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 16 06:46:00 phillip-laptop kernel: [   24.500862] assign_interrupt_mode Found MSI capability
Nov 16 06:46:00 phillip-laptop kernel: [   24.500897] Allocate Port Service[0000:00:06.0:pcie00]
Nov 16 06:46:00 phillip-laptop kernel: [   24.500979] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 16 06:46:00 phillip-laptop kernel: [   24.501014] assign_interrupt_mode Found MSI capability
Nov 16 06:46:00 phillip-laptop kernel: [   24.501049] Allocate Port Service[0000:00:07.0:pcie00]
Nov 16 06:46:00 phillip-laptop kernel: [   24.501356] isapnp: Scanning for PnP cards...
Nov 16 06:46:00 phillip-laptop kernel: [   24.855288] isapnp: No Plug & Play device found
Nov 16 06:46:00 phillip-laptop kernel: [   24.886288] Real Time Clock Driver v1.12ac
Nov 16 06:46:00 phillip-laptop kernel: [   24.886460] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 16 06:46:00 phillip-laptop kernel: [   24.887894] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 16 06:46:00 phillip-laptop kernel: [   24.887981] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 16 06:46:00 phillip-laptop kernel: [   24.888093] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov 16 06:46:00 phillip-laptop kernel: [   24.890053] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov 16 06:46:00 phillip-laptop kernel: [   24.890868] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 16 06:46:00 phillip-laptop kernel: [   24.890875] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 16 06:46:00 phillip-laptop kernel: [   24.890880] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 16 06:46:00 phillip-laptop kernel: [   24.890885] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 16 06:46:00 phillip-laptop kernel: [   24.890889] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 16 06:46:00 phillip-laptop kernel: [   24.904671] mice: PS/2 mouse device common for all mice
Nov 16 06:46:00 phillip-laptop kernel: [   24.904817] EISA: Probing bus 0 at eisa.0
Nov 16 06:46:00 phillip-laptop kernel: [   24.904842] Cannot allocate resource for EISA slot 4
Nov 16 06:46:00 phillip-laptop kernel: [   24.904856] Cannot allocate resource for EISA slot 7
Nov 16 06:46:00 phillip-laptop kernel: [   24.904860] Cannot allocate resource for EISA slot 8
Nov 16 06:46:00 phillip-laptop kernel: [   24.904864] EISA: Detected 0 cards.
Nov 16 06:46:00 phillip-laptop kernel: [   24.904869] cpuidle: using governor ladder
Nov 16 06:46:00 phillip-laptop kernel: [   24.904873] cpuidle: using governor menu
Nov 16 06:46:00 phillip-laptop kernel: [   24.904984] NET: Registered protocol family 1
Nov 16 06:46:00 phillip-laptop kernel: [   24.905017] Using IPI No-Shortcut mode
Nov 16 06:46:00 phillip-laptop kernel: [   24.905056] registered taskstats version 1
Nov 16 06:46:00 phillip-laptop kernel: [   24.905192]   Magic number: 0:104:772
Nov 16 06:46:00 phillip-laptop kernel: [   24.905304]   hash matches device ptyp8
Nov 16 06:46:00 phillip-laptop kernel: [   24.905348] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 16 06:46:00 phillip-laptop kernel: [   24.905353] EDD information not available.
Nov 16 06:46:00 phillip-laptop kernel: [   24.905737] Freeing unused kernel memory: 368k freed
Nov 16 06:46:00 phillip-laptop kernel: [   24.905768] Write protecting the kernel read-only data: 801k
Nov 16 06:46:00 phillip-laptop kernel: [   24.948410] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 16 06:46:00 phillip-laptop kernel: [   25.115514] vesafb: framebuffer at 0x90000000, mapped to 0xf8880000, using 4608k, total 16384k
Nov 16 06:46:00 phillip-laptop kernel: [   25.115529] vesafb: mode is 1024x768x24, linelength=3072, pages=6
Nov 16 06:46:00 phillip-laptop kernel: [   25.115534] vesafb: protected mode interface info at c000:516e
Nov 16 06:46:00 phillip-laptop kernel: [   25.115538] vesafb: pmi: set display start = c00c51dc, set palette = c00c5216
Nov 16 06:46:00 phillip-laptop kernel: [   25.115543] vesafb: pmi: ports = 7810 7816 7854 7838 783c 785c 7800 7804 78b0 78b2 78b4 
Nov 16 06:46:00 phillip-laptop kernel: [   25.115554] vesafb: scrolling: redraw
Nov 16 06:46:00 phillip-laptop kernel: [   25.115558] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Nov 16 06:46:00 phillip-laptop kernel: [   25.115692] Console: switching to colour frame buffer device 128x48
Nov 16 06:46:00 phillip-laptop kernel: [   25.121861] fb0: VESA VGA frame buffer device
Nov 16 06:46:00 phillip-laptop kernel: [   26.281763] fuse init (API version 7.9)
Nov 16 06:46:00 phillip-laptop kernel: [   26.302158] ACPI: SSDT 77FBE2A0, 0D1C (r1    AMI   CPU1PM        1 INTL 20051117)
Nov 16 06:46:00 phillip-laptop kernel: [   26.303410] ACPI: CPU0 (power states: C1[C1] C2[C2])
Nov 16 06:46:00 phillip-laptop kernel: [   26.303416] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov 16 06:46:00 phillip-laptop kernel: [   26.303476] ACPI: SSDT 77FBEFC0, 0D1C (r1    AMI   CPU2PM        1 INTL 20051117)
Nov 16 06:46:00 phillip-laptop kernel: [   26.304686] ACPI: CPU1 (power states: C1[C1] C2[C2])
Nov 16 06:46:00 phillip-laptop kernel: [   26.306018] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov 16 06:46:00 phillip-laptop kernel: [   26.308093] ACPI: Thermal Zone [THRM] (54 C)
Nov 16 06:46:00 phillip-laptop kernel: [   26.706808] SCSI subsystem initialized
Nov 16 06:46:00 phillip-laptop kernel: [   26.727013] usbcore: registered new interface driver usbfs
Nov 16 06:46:00 phillip-laptop kernel: [   26.727045] usbcore: registered new interface driver hub
Nov 16 06:46:00 phillip-laptop kernel: [   26.727492] libata version 3.00 loaded.
Nov 16 06:46:00 phillip-laptop kernel: [   26.729733] usbcore: registered new device driver usb
Nov 16 06:46:00 phillip-laptop kernel: [   26.730057] ahci 0000:00:12.0: version 3.0
Nov 16 06:46:00 phillip-laptop kernel: [   26.730094] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
Nov 16 06:46:00 phillip-laptop kernel: [   26.730123] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Nov 16 06:46:00 phillip-laptop kernel: [   26.730125] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Nov 16 06:46:00 phillip-laptop kernel: [   26.731402] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 16 06:46:00 phillip-laptop kernel: [   26.788545] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 16 06:46:00 phillip-laptop kernel: [   26.788555] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 16 06:46:00 phillip-laptop kernel: [   26.821775] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Nov 16 06:46:00 phillip-laptop kernel: [   27.731807] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Nov 16 06:46:00 phillip-laptop kernel: [   27.731816] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pio 
Nov 16 06:46:00 phillip-laptop kernel: [   27.732299] scsi0 : ahci
Nov 16 06:46:00 phillip-laptop kernel: [   27.732640] scsi1 : ahci
Nov 16 06:46:00 phillip-laptop kernel: [   27.732812] scsi2 : ahci
Nov 16 06:46:00 phillip-laptop kernel: [   27.732960] scsi3 : ahci
Nov 16 06:46:00 phillip-laptop kernel: [   27.733057] ata1: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 17
Nov 16 06:46:00 phillip-laptop kernel: [   27.733062] ata2: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 17
Nov 16 06:46:00 phillip-laptop kernel: [   27.733066] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 17
Nov 16 06:46:00 phillip-laptop kernel: [   27.733070] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 17
Nov 16 06:46:00 phillip-laptop kernel: [   28.206975] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 16 06:46:00 phillip-laptop kernel: [   28.207915] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
Nov 16 06:46:00 phillip-laptop kernel: [   28.207919] ata1.00: 234441648 sectors, multi 0: LBA48 NCQ (depth 31/32)
Nov 16 06:46:00 phillip-laptop kernel: [   28.209029] ata1.00: configured for UDMA/100
Nov 16 06:46:00 phillip-laptop kernel: [   28.518448] ata2: SATA link down (SStatus 0 SControl 300)
Nov 16 06:46:00 phillip-laptop kernel: [   28.829926] ata3: SATA link down (SStatus 0 SControl 300)
Nov 16 06:46:00 phillip-laptop kernel: [   29.141405] ata4: SATA link down (SStatus 0 SControl 300)
Nov 16 06:46:00 phillip-laptop kernel: [   29.141612] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
Nov 16 06:46:00 phillip-laptop kernel: [   29.142129] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 18
Nov 16 06:46:00 phillip-laptop kernel: [   29.142149] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 16 06:46:00 phillip-laptop kernel: [   29.142526] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Nov 16 06:46:00 phillip-laptop kernel: [   29.142551] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfebfe000
Nov 16 06:46:00 phillip-laptop kernel: [   29.150774] Driver 'sd' needs updating - please use bus_type methods
Nov 16 06:46:00 phillip-laptop kernel: [   29.150888] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov 16 06:46:00 phillip-laptop kernel: [   29.150903] sd 0:0:0:0: [sda] Write Protect is off
Nov 16 06:46:00 phillip-laptop kernel: [   29.150906] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 16 06:46:00 phillip-laptop kernel: [   29.150923] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 16 06:46:00 phillip-laptop kernel: [   29.150979] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov 16 06:46:00 phillip-laptop kernel: [   29.150989] sd 0:0:0:0: [sda] Write Protect is off
Nov 16 06:46:00 phillip-laptop kernel: [   29.150991] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 16 06:46:00 phillip-laptop kernel: [   29.151007] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 16 06:46:00 phillip-laptop kernel: [   29.151011]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
Nov 16 06:46:00 phillip-laptop kernel: [   29.201479] hub 1-0:1.0: USB hub found
Nov 16 06:46:00 phillip-laptop kernel: [   29.201490] hub 1-0:1.0: 2 ports detected
Nov 16 06:46:00 phillip-laptop kernel: [   29.305247] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 19
Nov 16 06:46:00 phillip-laptop kernel: [   29.305274] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 16 06:46:00 phillip-laptop kernel: [   29.305311] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Nov 16 06:46:00 phillip-laptop kernel: [   29.305333] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfebfd000
Nov 16 06:46:00 phillip-laptop kernel: [   29.365130] usb usb2: configuration #1 chosen from 1 choice
Nov 16 06:46:00 phillip-laptop kernel: [   29.365157] hub 2-0:1.0: USB hub found
Nov 16 06:46:00 phillip-laptop kernel: [   29.365167] hub 2-0:1.0: 2 ports detected
Nov 16 06:46:00 phillip-laptop kernel: [   29.468958] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 20
Nov 16 06:46:00 phillip-laptop kernel: [   29.468982] ohci_hcd 0000:00:13.2: OHCI Host Controller
Nov 16 06:46:00 phillip-laptop kernel: [   29.469012] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Nov 16 06:46:00 phillip-laptop kernel: [   29.469034] ohci_hcd 0000:00:13.2: irq 20, io mem 0xfebfc000
Nov 16 06:46:00 phillip-laptop kernel: [   29.528845] usb usb3: configuration #1 chosen from 1 choice
Nov 16 06:46:00 phillip-laptop kernel: [   29.528870] hub 3-0:1.0: USB hub found
Nov 16 06:46:00 phillip-laptop kernel: [   29.528881] hub 3-0:1.0: 2 ports detected
Nov 16 06:46:00 phillip-laptop kernel: [   29.558001]  sda1 sda2 sda3 < sda5 sda6 > sda4
Nov 16 06:46:00 phillip-laptop kernel: [   29.591899] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 16 06:46:00 phillip-laptop kernel: [   29.597070] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 16 06:46:00 phillip-laptop kernel: [   29.632754] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 19
Nov 16 06:46:00 phillip-laptop kernel: [   29.632787] ohci_hcd 0000:00:13.3: OHCI Host Controller
Nov 16 06:46:00 phillip-laptop kernel: [   29.632825] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Nov 16 06:46:00 phillip-laptop kernel: [   29.632846] ohci_hcd 0000:00:13.3: irq 19, io mem 0xfebfb000
Nov 16 06:46:00 phillip-laptop kernel: [   29.692644] usb usb4: configuration #1 chosen from 1 choice
Nov 16 06:46:00 phillip-laptop kernel: [   29.692685] hub 4-0:1.0: USB hub found
Nov 16 06:46:00 phillip-laptop kernel: [   29.692698] hub 4-0:1.0: 2 ports detected
Nov 16 06:46:00 phillip-laptop kernel: [   29.796443] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 20
Nov 16 06:46:00 phillip-laptop kernel: [   29.796477] ohci_hcd 0000:00:13.4: OHCI Host Controller
Nov 16 06:46:00 phillip-laptop kernel: [   29.796507] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Nov 16 06:46:00 phillip-laptop kernel: [   29.796525] ohci_hcd 0000:00:13.4: irq 20, io mem 0xfebfa000
Nov 16 06:46:00 phillip-laptop kernel: [   29.856353] usb usb5: configuration #1 chosen from 1 choice
Nov 16 06:46:00 phillip-laptop kernel: [   29.856382] hub 5-0:1.0: USB hub found
Nov 16 06:46:00 phillip-laptop kernel: [   29.856391] hub 5-0:1.0: 2 ports detected
Nov 16 06:46:00 phillip-laptop kernel: [   29.960222] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Nov 16 06:46:00 phillip-laptop kernel: [   29.960238] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
Nov 16 06:46:00 phillip-laptop kernel: [   29.960251] SB600_PATA: not 100% native mode: will probe irqs later
Nov 16 06:46:00 phillip-laptop kernel: [   29.960262]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:DMA
Nov 16 06:46:00 phillip-laptop kernel: [   29.960275] Probing IDE interface ide0...
Nov 16 06:46:00 phillip-laptop kernel: [   30.747112] hdb: HL-DT-ST DVDRAM GSA-T20N, ATAPI CD/DVD-ROM drive
Nov 16 06:46:00 phillip-laptop kernel: [   31.026246] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Nov 16 06:46:00 phillip-laptop kernel: [   31.027062] hdb: UDMA/33 mode selected
Nov 16 06:46:00 phillip-laptop kernel: [   31.027515] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov 16 06:46:00 phillip-laptop kernel: [   31.030590] 8139cp 0000:08:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Nov 16 06:46:00 phillip-laptop kernel: [   31.030593] 8139cp 0000:08:07.0: Try the "8139too" driver instead.
Nov 16 06:46:00 phillip-laptop kernel: [   31.032617] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 21
Nov 16 06:46:00 phillip-laptop kernel: [   31.032637] ehci_hcd 0000:00:13.5: EHCI Host Controller
Nov 16 06:46:00 phillip-laptop kernel: [   31.032679] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Nov 16 06:46:00 phillip-laptop kernel: [   31.032734] ehci_hcd 0000:00:13.5: debug port 1
Nov 16 06:46:00 phillip-laptop kernel: [   31.032750] ehci_hcd 0000:00:13.5: irq 21, io mem 0xfebff800
Nov 16 06:46:00 phillip-laptop kernel: [   31.032815] 8139too Fast Ethernet driver 0.9.28
Nov 16 06:46:00 phillip-laptop kernel: [   31.043216] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 16 06:46:00 phillip-laptop kernel: [   31.043346] usb usb6: configuration #1 chosen from 1 choice
Nov 16 06:46:00 phillip-laptop kernel: [   31.043372] hub 6-0:1.0: USB hub found
Nov 16 06:46:00 phillip-laptop kernel: [   31.043379] hub 6-0:1.0: 10 ports detected
Nov 16 06:46:00 phillip-laptop kernel: [   31.146440] ACPI: PCI Interrupt 0000:08:07.0[A] -> GSI 20 (level, low) -> IRQ 22
Nov 16 06:46:00 phillip-laptop kernel: [   31.147583] eth0: RealTek RTL8139 at 0xb800, 00:1d:60:49:6c:65, IRQ 22
Nov 16 06:46:00 phillip-laptop kernel: [   31.147586] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Nov 16 06:46:00 phillip-laptop kernel: [   31.167180] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Nov 16 06:46:00 phillip-laptop kernel: [   31.167191] Uniform CD-ROM driver Revision: 3.20
Nov 16 06:46:00 phillip-laptop kernel: [   31.305489] Attempting manual resume
Nov 16 06:46:00 phillip-laptop kernel: [   31.305494] swsusp: Resume From Partition 8:6
Nov 16 06:46:00 phillip-laptop kernel: [   31.305496] PM: Checking swsusp image.
Nov 16 06:46:00 phillip-laptop kernel: [   31.305643] PM: Resume from disk failed.
Nov 16 06:46:00 phillip-laptop kernel: [   31.355545] kjournald starting.  Commit interval 5 seconds
Nov 16 06:46:00 phillip-laptop kernel: [   31.355568] EXT3-fs: mounted filesystem with ordered data mode.
Nov 16 06:46:00 phillip-laptop kernel: [   41.135033] input: PC Speaker as /devices/platform/pcspkr/input/input2
Nov 16 06:46:00 phillip-laptop kernel: [   41.306226] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 16 06:46:00 phillip-laptop kernel: [   41.357112] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 16 06:46:00 phillip-laptop kernel: [   41.436984] Linux agpgart interface v0.102
Nov 16 06:46:00 phillip-laptop kernel: [   41.475062] input: Power Button (FF) as /devices/virtual/input/input3
Nov 16 06:46:00 phillip-laptop kernel: [   41.540702] ACPI: Power Button (FF) [PWRF]
Nov 16 06:46:00 phillip-laptop kernel: [   41.544389] input: Lid Switch as /devices/virtual/input/input4
Nov 16 06:46:00 phillip-laptop kernel: [   41.574356] ACPI: Lid Switch [LID]
Nov 16 06:46:00 phillip-laptop kernel: [   41.577995] input: Power Button (CM) as /devices/virtual/input/input5
Nov 16 06:46:00 phillip-laptop kernel: [   41.592671] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Nov 16 06:46:00 phillip-laptop kernel: [   41.628589] ACPI: Power Button (CM) [PWRB]
Nov 16 06:46:00 phillip-laptop kernel: [   41.632288] input: Sleep Button (CM) as /devices/virtual/input/input6
Nov 16 06:46:00 phillip-laptop kernel: [   41.680447] ACPI: Sleep Button (CM) [SLPB]
Nov 16 06:46:00 phillip-laptop kernel: [   41.877222] asus-laptop: Asus Laptop Support version 0.42
Nov 16 06:46:00 phillip-laptop kernel: [   41.881181] asus-laptop: BSTS called, 0x22 returned
Nov 16 06:46:00 phillip-laptop kernel: [   41.884862] asus-laptop:   X51R model detected
Nov 16 06:46:00 phillip-laptop kernel: [   42.248497] Yenta: CardBus bridge found at 0000:08:01.0 [1043:1627]
Nov 16 06:46:00 phillip-laptop kernel: [   42.380145] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
Nov 16 06:46:00 phillip-laptop kernel: [   42.383646] Socket status: 30000006
Nov 16 06:46:00 phillip-laptop kernel: [   42.387480] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
Nov 16 06:46:00 phillip-laptop kernel: [   42.391131] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
Nov 16 06:46:00 phillip-laptop kernel: [   42.395996] cs: IO port probe 0xa000-0xbfff: clean.
Nov 16 06:46:00 phillip-laptop kernel: [   42.400197] pcmcia: parent PCI bridge Memory window: 0xfca00000 - 0xfeafffff
Nov 16 06:46:00 phillip-laptop kernel: [   42.403815] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xdfefffff
Nov 16 06:46:00 phillip-laptop kernel: [   42.569153] sdhci: Secure Digital Host Controller Interface driver
Nov 16 06:46:00 phillip-laptop kernel: [   42.572841] sdhci: Copyright(c) Pierre Ossman
Nov 16 06:46:00 phillip-laptop kernel: [   42.576508] sdhci: SDHCI controller found at 0000:08:01.1 [1180:0822] (rev 17)
Nov 16 06:46:00 phillip-laptop kernel: [   42.580324] ACPI: PCI Interrupt 0000:08:01.1[C] -> GSI 23 (level, low) -> IRQ 23
Nov 16 06:46:00 phillip-laptop kernel: [   42.584479] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Nov 16 06:46:00 phillip-laptop kernel: [   42.599829] mmc0: SDHCI at 0xfeaffc00 irq 23 DMA
Nov 16 06:46:00 phillip-laptop kernel: [   42.734694] ACPI: Battery Slot [BAT0] (battery present)
Nov 16 06:46:00 phillip-laptop kernel: [   42.738857] ACPI: AC Adapter [AC0] (on-line)
Nov 16 06:46:00 phillip-laptop kernel: [   42.747265] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input7
Nov 16 06:46:00 phillip-laptop kernel: [   42.798693] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov 16 06:46:00 phillip-laptop kernel: [   42.961543] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
Nov 16 06:46:00 phillip-laptop kernel: [   43.281808] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
Nov 16 06:46:00 phillip-laptop kernel: [   43.325073] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Nov 16 06:46:00 phillip-laptop kernel: [   44.101620] cs: IO port probe 0x100-0x3af: clean.
Nov 16 06:46:00 phillip-laptop kernel: [   44.107993] cs: IO port probe 0x3e0-0x4ff: clean.
Nov 16 06:46:00 phillip-laptop kernel: [   44.112977] cs: IO port probe 0x820-0x8ff: clean.
Nov 16 06:46:00 phillip-laptop kernel: [   44.117304] cs: IO port probe 0xc00-0xcf7: clean.
Nov 16 06:46:00 phillip-laptop kernel: [   44.122026] cs: IO port probe 0xa00-0xaff: clean.
Nov 16 06:46:00 phillip-laptop kernel: [   44.972581] lp: driver loaded but no devices found
Nov 16 06:46:00 phillip-laptop kernel: [   45.039621] ath_hal: module license 'Proprietary' taints kernel.
Nov 16 06:46:00 phillip-laptop kernel: [   45.046914] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
Nov 16 06:46:00 phillip-laptop kernel: [   45.152986] wlan: trunk
Nov 16 06:46:00 phillip-laptop kernel: [   45.206244] ath_pci: trunk
Nov 16 06:46:00 phillip-laptop kernel: [   45.211024] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 18
Nov 16 06:46:00 phillip-laptop kernel: [   45.215596] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov 16 06:46:00 phillip-laptop kernel: [   45.707604] MadWifi: ath_attach: Switching rfkill capability off
Nov 16 06:46:00 phillip-laptop kernel: [   45.747740] ath_rate_sample: 1.2 (trunk)
Nov 16 06:46:00 phillip-laptop kernel: [   45.752654] MadWifi: ath_attach: Switching per-packet transmit power control off
Nov 16 06:46:00 phillip-laptop kernel: [   45.757244] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Nov 16 06:46:00 phillip-laptop kernel: [   45.762314] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov 16 06:46:00 phillip-laptop kernel: [   45.766792] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Nov 16 06:46:00 phillip-laptop kernel: [   45.766813] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
Nov 16 06:46:00 phillip-laptop kernel: [   45.766816] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
Nov 16 06:46:00 phillip-laptop kernel: [   45.766818] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
Nov 16 06:46:00 phillip-laptop kernel: [   45.766820] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
Nov 16 06:46:00 phillip-laptop kernel: [   45.766822] wifi0: ath_announce: Use hw queue 8 for CAB traffic
Nov 16 06:46:00 phillip-laptop kernel: [   45.766824] wifi0: ath_announce: Use hw queue 9 for beacons
Nov 16 06:46:00 phillip-laptop kernel: [   45.797152] ath_pci: wifi0: Atheros 5424/2424: mem=0xf89f0000, irq=18
Nov 16 06:46:00 phillip-laptop kernel: [   45.881019] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFB) is beyond end of object [20070126]
Nov 16 06:46:00 phillip-laptop kernel: [   45.885640] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PSS] (Node f7d2d1f8), AE_AML_PACKAGE_LIMIT
Nov 16 06:46:00 phillip-laptop kernel: [   45.889999] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Nov 16 06:46:00 phillip-laptop kernel: [   45.894520] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFB) is beyond end of object [20070126]
Nov 16 06:46:00 phillip-laptop kernel: [   45.898871] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PSS] (Node f7c49b88), AE_AML_PACKAGE_LIMIT
Nov 16 06:46:00 phillip-laptop kernel: [   45.903323] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Nov 16 06:46:00 phillip-laptop kernel: [   46.035619] Adding 872480k swap on /dev/sda6.  Priority:-1 extents:1 across:872480k
Nov 16 06:46:00 phillip-laptop kernel: [   46.572144] EXT3 FS on sda4, internal journal
Nov 16 06:46:00 phillip-laptop kernel: [   47.984711] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 16 06:46:00 phillip-laptop kernel: [   48.028624] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Nov 16 06:46:00 phillip-laptop kernel: [   48.137452] NET: Registered protocol family 10
Nov 16 06:46:00 phillip-laptop kernel: [   48.137824] lo: Disabled Privacy Extensions
Nov 16 06:46:00 phillip-laptop kernel: [   48.157543] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 16 06:46:00 phillip-laptop kernel: [   49.159257] No dock devices found.
Nov 16 06:46:00 phillip-laptop NetworkManager: <info>  starting... 
Nov 16 06:46:00 phillip-laptop avahi-daemon[5224]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov 16 06:46:00 phillip-laptop avahi-daemon[5224]: Successfully dropped root privileges.
Nov 16 06:46:00 phillip-laptop avahi-daemon[5224]: avahi-daemon 0.6.22 starting up.
Nov 16 06:46:00 phillip-laptop avahi-daemon[5224]: Successfully called chroot().
Nov 16 06:46:00 phillip-laptop avahi-daemon[5224]: Successfully dropped remaining capabilities.
Nov 16 06:46:00 phillip-laptop avahi-daemon[5224]: No service file found in /etc/avahi/services.
Nov 16 06:46:00 phillip-laptop avahi-daemon[5224]: Network interface enumeration completed.
Nov 16 06:46:00 phillip-laptop avahi-daemon[5224]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 16 06:46:00 phillip-laptop avahi-daemon[5224]: Server startup complete. Host name is phillip-laptop.local. Local service cookie is 684864958.
Nov 16 06:46:00 phillip-laptop kernel: [   50.693536] ppdev: user-space parallel port driver
Nov 16 06:46:01 phillip-laptop kernel: [   50.890028] audit(1226817961.052:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5257 profile="/usr/sbin/cupsd" namespace="default"
Nov 16 06:46:01 phillip-laptop kernel: [   51.182629] apm: BIOS not found.
Nov 16 06:46:01 phillip-laptop atieventsd[5294]: ATI External Events Daemon started... 
Nov 16 06:46:01 phillip-laptop atieventsd[5294]: Event daemon control socket created 
Nov 16 06:46:01 phillip-laptop atieventsd[5294]: acpid connection established 
Nov 16 06:46:05 phillip-laptop avgscan[5311]: Starting AVG Anti-Virus in daemon mode. 
Nov 16 06:46:05 phillip-laptop avgscan[5311]: AVG Anti-Virus Daemon started.
Nov 16 06:46:05 phillip-laptop avgscan[5311]: Starting AVG Anti-Virus on-access scanner. 
Nov 16 06:46:05 phillip-laptop avgscan[5311]: AVG Anti-Virus on-access scanner started
Nov 16 06:46:05 phillip-laptop avgscan[5313]: ERROR: registration to Dazuko failed
Nov 16 06:46:05 phillip-laptop avgscan[5313]: AVG Anti-Virus on-access failed to start.
Nov 16 06:47:20 phillip-laptop syslogd 1.5.0#1ubuntu1: restart.
Nov 16 06:47:20 phillip-laptop kernel: Inspecting /boot/System.map-2.6.24-21-generic
Nov 16 06:47:20 phillip-laptop kernel: Loaded 27897 symbols from /boot/System.map-2.6.24-21-generic.
Nov 16 06:47:20 phillip-laptop kernel: Symbols match kernel version 2.6.24.
Nov 16 06:47:20 phillip-laptop kernel: Loaded 22660 symbols from 107 modules.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fa8000 (usable)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fa8000 - 0000000077fb0000 (ACPI NVS)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fb0000 - 0000000077fbe000 (ACPI data)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fbe000 - 0000000077ff0000 (ACPI NVS)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077ff0000 - 0000000078000000 (reserved)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] 1023MB HIGHMEM available.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] 896MB LOWMEM available.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] found SMP MP-table at 000ff780
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 491432) 0 entries of 256 used
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Zone PFN ranges:
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   DMA             0 ->     4096
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   HighMem    229376 ->   491432
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Movable zone start PFN for each node
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]     0:        0 ->   491432
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] On node 0 totalpages: 491432
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   HighMem zone: 2047 pages used for memmap
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   HighMem zone: 260009 pages, LIFO batch:31
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] DMI 2.4 present.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7F50 checksum 0
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: RSDP 000F7F50, 0024 (r2 ACPIAM)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: XSDT 77FB0100, 0054 (r1 _ASUS_ Notebook  7000731 MSFT       97)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: FACP 77FB0290, 00F4 (r3 A.M.I  OEMFACP   7000731 MSFT       97)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: DSDT 77FB0630, 77A4 (r1  T12R0 T12R0000        0 INTL 20051117)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: FACS 77FBE000, 0040
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: APIC 77FB0390, 005C (r1 A.M.I  OEMAPIC   7000731 MSFT       97)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: MCFG 77FB03F0, 003C (r1 A.M.I  OEMMCFG   7000731 MSFT       97)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: SLIC 77FB0430, 0176 (r1 _ASUS_ Notebook  7000731 MSFT       97)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: BOOT 77FB0600, 0028 (r1 A.M.I  OEMBOOT   7000731 MSFT       97)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: OEMB 77FBE040, 005B (r1 A.M.I  AMI_OEM   7000731 MSFT       97)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Processor #0 6:14 APIC version 20
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Processor #1 6:14 APIC version 20
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:86e00000)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487593
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Kernel command line: root=UUID=3c071645-e73d-42b0-95ae-d796b29b38b3 ro splash vga=792
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Initializing CPU#0
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 16 06:47:20 phillip-laptop kernel: [    0.000000] Detected 1862.288 MHz processor.
Nov 16 06:47:20 phillip-laptop kernel: [   22.826822] Console: colour dummy device 80x25
Nov 16 06:47:20 phillip-laptop kernel: [   22.826827] console [tty0] enabled
Nov 16 06:47:20 phillip-laptop kernel: [   22.827850] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 16 06:47:20 phillip-laptop kernel: [   22.828577] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 16 06:47:20 phillip-laptop kernel: [   22.940857] Memory: 1935620k/1965728k available (2177k kernel code, 28936k reserved, 1005k data, 368k init, 1048224k highmem)
Nov 16 06:47:20 phillip-laptop kernel: [   22.940880] virtual kernel memory layout:
Nov 16 06:47:20 phillip-laptop kernel: [   22.940881]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Nov 16 06:47:20 phillip-laptop kernel: [   22.940882]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 16 06:47:20 phillip-laptop kernel: [   22.940884]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov 16 06:47:20 phillip-laptop kernel: [   22.940885]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov 16 06:47:20 phillip-laptop kernel: [   22.940886]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Nov 16 06:47:20 phillip-laptop kernel: [   22.940887]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
Nov 16 06:47:20 phillip-laptop kernel: [   22.940888]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
Nov 16 06:47:20 phillip-laptop kernel: [   22.940909] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 16 06:47:20 phillip-laptop kernel: [   22.940978] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Nov 16 06:47:20 phillip-laptop kernel: [   23.020885] Calibrating delay using timer specific routine.. 3728.21 BogoMIPS (lpj=7456422)
Nov 16 06:47:20 phillip-laptop kernel: [   23.020935] Security Framework initialized
Nov 16 06:47:20 phillip-laptop kernel: [   23.020952] SELinux:  Disabled at boot.
Nov 16 06:47:20 phillip-laptop kernel: [   23.020976] AppArmor: AppArmor initialized
Nov 16 06:47:20 phillip-laptop kernel: [   23.020982] Failure registering capabilities with primary security module.
Nov 16 06:47:20 phillip-laptop kernel: [   23.020996] Mount-cache hash table entries: 512
Nov 16 06:47:20 phillip-laptop kernel: [   23.021183] Initializing cgroup subsys ns
Nov 16 06:47:20 phillip-laptop kernel: [   23.021197] Initializing cgroup subsys cpuacct
Nov 16 06:47:20 phillip-laptop kernel: [   23.021215] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
Nov 16 06:47:20 phillip-laptop kernel: [   23.021223] monitor/mwait feature present.
Nov 16 06:47:20 phillip-laptop kernel: [   23.021226] using mwait in idle threads.
Nov 16 06:47:20 phillip-laptop kernel: [   23.021233] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 16 06:47:20 phillip-laptop kernel: [   23.021238] CPU: L2 cache: 1024K
Nov 16 06:47:20 phillip-laptop kernel: [   23.021243] CPU: Physical Processor ID: 0
Nov 16 06:47:20 phillip-laptop kernel: [   23.021246] CPU: Processor Core ID: 0
Nov 16 06:47:20 phillip-laptop kernel: [   23.021250] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
Nov 16 06:47:20 phillip-laptop kernel: [   23.021263] Compat vDSO mapped to ffffe000.
Nov 16 06:47:20 phillip-laptop kernel: [   23.021283] Checking 'hlt' instruction... OK.
Nov 16 06:47:20 phillip-laptop kernel: [   23.037280] SMP alternatives: switching to UP code
Nov 16 06:47:20 phillip-laptop kernel: [   23.039144] Early unpacking initramfs... done
Nov 16 06:47:20 phillip-laptop kernel: [   23.380200] ACPI: Core revision 20070126
Nov 16 06:47:20 phillip-laptop kernel: [   23.380278] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 16 06:47:20 phillip-laptop kernel: [   23.385819] CPU0: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
Nov 16 06:47:20 phillip-laptop kernel: [   23.385844] SMP alternatives: switching to SMP code
Nov 16 06:47:20 phillip-laptop kernel: [   23.386604] Booting processor 1/1 eip 3000
Nov 16 06:47:20 phillip-laptop kernel: [   23.396773] Initializing CPU#1
Nov 16 06:47:20 phillip-laptop kernel: [   23.476152] Calibrating delay using timer specific routine.. 3724.52 BogoMIPS (lpj=7449052)
Nov 16 06:47:20 phillip-laptop kernel: [   23.476160] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
Nov 16 06:47:20 phillip-laptop kernel: [   23.476166] monitor/mwait feature present.
Nov 16 06:47:20 phillip-laptop kernel: [   23.476170] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 16 06:47:20 phillip-laptop kernel: [   23.476172] CPU: L2 cache: 1024K
Nov 16 06:47:20 phillip-laptop kernel: [   23.476174] CPU: Physical Processor ID: 0
Nov 16 06:47:20 phillip-laptop kernel: [   23.476175] CPU: Processor Core ID: 1
Nov 16 06:47:20 phillip-laptop kernel: [   23.476177] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
Nov 16 06:47:20 phillip-laptop kernel: [   23.476653] CPU1: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
Nov 16 06:47:20 phillip-laptop kernel: [   23.476696] Total of 2 processors activated (7452.73 BogoMIPS).
Nov 16 06:47:20 phillip-laptop kernel: [   23.476871] ENABLING IO-APIC IRQs
Nov 16 06:47:20 phillip-laptop kernel: [   23.477061] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 16 06:47:20 phillip-laptop kernel: [   23.624057] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov 16 06:47:20 phillip-laptop kernel: [   23.644047] Brought up 2 CPUs
Nov 16 06:47:20 phillip-laptop kernel: [   23.644074] CPU0 attaching sched-domain:
Nov 16 06:47:20 phillip-laptop kernel: [   23.644077]  domain 0: span 03
Nov 16 06:47:20 phillip-laptop kernel: [   23.644078]   groups: 01 02
Nov 16 06:47:20 phillip-laptop kernel: [   23.644082] CPU1 attaching sched-domain:
Nov 16 06:47:20 phillip-laptop kernel: [   23.644083]  domain 0: span 03
Nov 16 06:47:20 phillip-laptop kernel: [   23.644085]   groups: 02 01
Nov 16 06:47:20 phillip-laptop kernel: [   23.644372] net_namespace: 64 bytes
Nov 16 06:47:20 phillip-laptop kernel: [   23.644385] Booting paravirtualized kernel on bare hardware
Nov 16 06:47:20 phillip-laptop kernel: [   23.644838] Time:  6:46:53  Date: 11/16/08
Nov 16 06:47:20 phillip-laptop kernel: [   23.644875] NET: Registered protocol family 16
Nov 16 06:47:20 phillip-laptop kernel: [   23.645162] EISA bus registered
Nov 16 06:47:20 phillip-laptop kernel: [   23.645170] ACPI: bus type pci registered
Nov 16 06:47:20 phillip-laptop kernel: [   23.645461] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=9
Nov 16 06:47:20 phillip-laptop kernel: [   23.645469] PCI: Using configuration type 1
Nov 16 06:47:20 phillip-laptop kernel: [   23.645488] Setting up standard PCI resources
Nov 16 06:47:20 phillip-laptop kernel: [   23.645985] mtrr: your CPUs had inconsistent variable MTRR settings
Nov 16 06:47:20 phillip-laptop kernel: [   23.645990] mtrr: probably your BIOS does not setup all CPUs.
Nov 16 06:47:20 phillip-laptop kernel: [   23.645994] mtrr: corrected configuration.
Nov 16 06:47:20 phillip-laptop kernel: [   23.650331] ACPI: EC: Look up EC in DSDT
Nov 16 06:47:20 phillip-laptop kernel: [   23.695958] ACPI: Interpreter enabled
Nov 16 06:47:20 phillip-laptop kernel: [   23.695964] ACPI: (supports S0 S1 S3 S4 S5)
Nov 16 06:47:20 phillip-laptop kernel: [   23.695986] ACPI: Using IOAPIC for interrupt routing
Nov 16 06:47:20 phillip-laptop kernel: [   23.703595] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
Nov 16 06:47:20 phillip-laptop kernel: [   23.703603] ACPI: EC: driver started in poll mode
Nov 16 06:47:20 phillip-laptop kernel: [   23.703741] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 16 06:47:20 phillip-laptop kernel: [   23.704057] pci 0000:00:12.0: set SATA to AHCI mode
Nov 16 06:47:20 phillip-laptop kernel: [   23.705907] PCI: Transparent bridge - 0000:00:14.4
Nov 16 06:47:20 phillip-laptop kernel: [   23.706015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 16 06:47:20 phillip-laptop kernel: [   23.706155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Nov 16 06:47:20 phillip-laptop kernel: [   23.706309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
Nov 16 06:47:20 phillip-laptop kernel: [   23.706430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
Nov 16 06:47:20 phillip-laptop kernel: [   23.706546] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Nov 16 06:47:20 phillip-laptop kernel: [   23.706678] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Nov 16 06:47:20 phillip-laptop kernel: [   23.706836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
Nov 16 06:47:20 phillip-laptop kernel: [   23.712243] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *11 12)
Nov 16 06:47:20 phillip-laptop kernel: [   23.712403] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 12)
Nov 16 06:47:20 phillip-laptop kernel: [   23.712558] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 12)
Nov 16 06:47:20 phillip-laptop kernel: [   23.712711] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 12) *10
Nov 16 06:47:20 phillip-laptop kernel: [   23.712866] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 12)
Nov 16 06:47:20 phillip-laptop kernel: [   23.713019] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 12)
Nov 16 06:47:20 phillip-laptop kernel: [   23.713172] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 12)
Nov 16 06:47:20 phillip-laptop kernel: [   23.713326] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 12)
Nov 16 06:47:20 phillip-laptop kernel: [   23.713479] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 16 06:47:20 phillip-laptop kernel: [   23.713520] pnp: PnP ACPI init
Nov 16 06:47:20 phillip-laptop kernel: [   23.713531] ACPI: bus type pnp registered
Nov 16 06:47:20 phillip-laptop kernel: [   23.715994] pnp: PnP ACPI: found 12 devices
Nov 16 06:47:20 phillip-laptop kernel: [   23.716000] ACPI: ACPI bus type pnp unregistered
Nov 16 06:47:20 phillip-laptop kernel: [   23.716006] PnPBIOS: Disabled by ACPI PNP
Nov 16 06:47:20 phillip-laptop kernel: [   23.716297] PCI: Using ACPI for IRQ routing
Nov 16 06:47:20 phillip-laptop kernel: [   23.716303] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 16 06:47:20 phillip-laptop kernel: [   23.759866] NET: Registered protocol family 8
Nov 16 06:47:20 phillip-laptop kernel: [   23.759870] NET: Registered protocol family 20
Nov 16 06:47:20 phillip-laptop kernel: [   23.759944] AppArmor: AppArmor Filesystem Enabled
Nov 16 06:47:20 phillip-laptop kernel: [   23.763706] Time: tsc clocksource has been installed.
Nov 16 06:47:20 phillip-laptop kernel: [   23.775867] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775877] system 00:05: ioport range 0x40b-0x40b has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775882] system 00:05: ioport range 0x4d6-0x4d6 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775887] system 00:05: ioport range 0xc00-0xc01 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775892] system 00:05: ioport range 0xc14-0xc14 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775897] system 00:05: ioport range 0xc50-0xc51 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775902] system 00:05: ioport range 0xc52-0xc52 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775907] system 00:05: ioport range 0xc6c-0xc6c has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775912] system 00:05: ioport range 0xc6f-0xc6f has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775918] system 00:05: ioport range 0xcd0-0xcd1 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775923] system 00:05: ioport range 0xcd2-0xcd3 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775928] system 00:05: ioport range 0xcd4-0xcd5 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775933] system 00:05: ioport range 0xcd6-0xcd7 has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775938] system 00:05: ioport range 0xcd8-0xcdf has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775943] system 00:05: ioport range 0x800-0x89f has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775949] system 00:05: ioport range 0xb00-0xb1f could not be reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775954] system 00:05: ioport range 0x900-0x90f has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775959] system 00:05: ioport range 0x910-0x91f has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775964] system 00:05: ioport range 0xfe00-0xfefe has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775970] system 00:05: ioport range 0x4000-0x40fe has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775975] system 00:05: iomem range 0xfed20000-0xfed3ffff has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775981] system 00:05: iomem range 0xfed45000-0xfed89fff has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775987] system 00:05: iomem range 0xffb80000-0xffbfffff could not be reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.775993] system 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776004] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776010] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776019] system 00:09: ioport range 0x25c-0x25c has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776024] system 00:09: ioport range 0x25d-0x25d has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776029] system 00:09: ioport range 0x25e-0x25e has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776034] system 00:09: ioport range 0x25f-0x25f has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776043] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776052] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776057] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776063] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776068] system 00:0b: iomem range 0x100000-0x77ffffff could not be reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.776074] system 00:0b: iomem range 0x0-0x0 could not be reserved
Nov 16 06:47:20 phillip-laptop kernel: [   23.806555] PCI: Bridge: 0000:00:01.0
Nov 16 06:47:20 phillip-laptop kernel: [   23.806560]   IO window: 7000-7fff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806565]   MEM window: f8800000-f88fffff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806570]   PREFETCH window: 8ff00000-afefffff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806576] PCI: Bridge: 0000:00:04.0
Nov 16 06:47:20 phillip-laptop kernel: [   23.806579]   IO window: disabled.
Nov 16 06:47:20 phillip-laptop kernel: [   23.806584]   MEM window: f8900000-f89fffff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806589]   PREFETCH window: disabled.
Nov 16 06:47:20 phillip-laptop kernel: [   23.806594] PCI: Bridge: 0000:00:05.0
Nov 16 06:47:20 phillip-laptop kernel: [   23.806598]   IO window: 8000-9fff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806604]   MEM window: f8a00000-fc9fffff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806609]   PREFETCH window: aff00000-cfefffff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806614] PCI: Bridge: 0000:00:06.0
Nov 16 06:47:20 phillip-laptop kernel: [   23.806617]   IO window: disabled.
Nov 16 06:47:20 phillip-laptop kernel: [   23.806622]   MEM window: disabled.
Nov 16 06:47:20 phillip-laptop kernel: [   23.806626]   PREFETCH window: disabled.
Nov 16 06:47:20 phillip-laptop kernel: [   23.806632] PCI: Bridge: 0000:00:07.0
Nov 16 06:47:20 phillip-laptop kernel: [   23.806635]   IO window: disabled.
Nov 16 06:47:20 phillip-laptop kernel: [   23.806640]   MEM window: disabled.
Nov 16 06:47:20 phillip-laptop kernel: [   23.806644]   PREFETCH window: disabled.
Nov 16 06:47:20 phillip-laptop kernel: [   23.806657] PCI: Bus 9, cardbus bridge: 0000:08:01.0
Nov 16 06:47:20 phillip-laptop kernel: [   23.806662]   IO window: 0000a000-0000a0ff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806669]   IO window: 0000a400-0000a4ff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806677]   PREFETCH window: d0000000-d3ffffff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806685]   MEM window: 80000000-83ffffff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806692] PCI: Bridge: 0000:00:14.4
Nov 16 06:47:20 phillip-laptop kernel: [   23.806697]   IO window: a000-bfff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806706]   MEM window: fca00000-feafffff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806712]   PREFETCH window: cff00000-dfefffff
Nov 16 06:47:20 phillip-laptop kernel: [   23.806741] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 16 06:47:20 phillip-laptop kernel: [   23.806752] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov 16 06:47:20 phillip-laptop kernel: [   23.806762] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 16 06:47:20 phillip-laptop kernel: [   23.806773] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 16 06:47:20 phillip-laptop kernel: [   23.806804] ACPI: PCI Interrupt 0000:08:01.0[A] -> GSI 21 (level, low) -> IRQ 16
Nov 16 06:47:20 phillip-laptop kernel: [   23.806825] NET: Registered protocol family 2
Nov 16 06:47:20 phillip-laptop kernel: [   23.851787] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 16 06:47:20 phillip-laptop kernel: [   23.852103] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 16 06:47:20 phillip-laptop kernel: [   23.853483] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 16 06:47:20 phillip-laptop kernel: [   23.854467] TCP: Hash tables configured (established 131072 bind 65536)
Nov 16 06:47:20 phillip-laptop kernel: [   23.854478] TCP reno registered
Nov 16 06:47:20 phillip-laptop kernel: [   23.863924] checking if image is initramfs... it is
Nov 16 06:47:20 phillip-laptop kernel: [   24.306838] Switched to high resolution mode on CPU 0
Nov 16 06:47:20 phillip-laptop kernel: [   24.306962] Switched to high resolution mode on CPU 1
Nov 16 06:47:20 phillip-laptop kernel: [   24.549354] Freeing initrd memory: 8588k freed
Nov 16 06:47:20 phillip-laptop kernel: [   24.549662] Simple Boot Flag at 0xff set to 0x1
Nov 16 06:47:20 phillip-laptop kernel: [   24.550541] audit: initializing netlink socket (disabled)
Nov 16 06:47:20 phillip-laptop kernel: [   24.550566] audit(1226818013.484:1): initialized
Nov 16 06:47:20 phillip-laptop kernel: [   24.550852] highmem bounce pool size: 64 pages
Nov 16 06:47:20 phillip-laptop kernel: [   24.553182] VFS: Disk quotas dquot_6.5.1
Nov 16 06:47:20 phillip-laptop kernel: [   24.553289] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 16 06:47:20 phillip-laptop kernel: [   24.553457] io scheduler noop registered
Nov 16 06:47:20 phillip-laptop kernel: [   24.553462] io scheduler anticipatory registered
Nov 16 06:47:20 phillip-laptop kernel: [   24.553466] io scheduler deadline registered
Nov 16 06:47:20 phillip-laptop kernel: [   24.553481] io scheduler cfq registered (default)
Nov 16 06:47:20 phillip-laptop kernel: [   24.553566] Boot video device is 0000:01:05.0
Nov 16 06:47:20 phillip-laptop kernel: [   24.553708] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 16 06:47:20 phillip-laptop kernel: [   24.553744] assign_interrupt_mode Found MSI capability
Nov 16 06:47:20 phillip-laptop kernel: [   24.553786] Allocate Port Service[0000:00:04.0:pcie00]
Nov 16 06:47:20 phillip-laptop kernel: [   24.553876] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov 16 06:47:20 phillip-laptop kernel: [   24.553911] assign_interrupt_mode Found MSI capability
Nov 16 06:47:20 phillip-laptop kernel: [   24.553947] Allocate Port Service[0000:00:05.0:pcie00]
Nov 16 06:47:20 phillip-laptop kernel: [   24.553992] Allocate Port Service[0000:00:05.0:pcie02]
Nov 16 06:47:20 phillip-laptop kernel: [   24.554092] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 16 06:47:20 phillip-laptop kernel: [   24.554128] assign_interrupt_mode Found MSI capability
Nov 16 06:47:20 phillip-laptop kernel: [   24.554165] Allocate Port Service[0000:00:06.0:pcie00]
Nov 16 06:47:20 phillip-laptop kernel: [   24.554248] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 16 06:47:20 phillip-laptop kernel: [   24.554283] assign_interrupt_mode Found MSI capability
Nov 16 06:47:20 phillip-laptop kernel: [   24.554318] Allocate Port Service[0000:00:07.0:pcie00]
Nov 16 06:47:20 phillip-laptop kernel: [   24.554605] isapnp: Scanning for PnP cards...
Nov 16 06:47:20 phillip-laptop kernel: [   24.908153] isapnp: No Plug & Play device found
Nov 16 06:47:20 phillip-laptop kernel: [   24.938734] Real Time Clock Driver v1.12ac
Nov 16 06:47:20 phillip-laptop kernel: [   24.938913] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 16 06:47:20 phillip-laptop kernel: [   24.940378] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 16 06:47:20 phillip-laptop kernel: [   24.940459] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 16 06:47:20 phillip-laptop kernel: [   24.940573] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov 16 06:47:20 phillip-laptop kernel: [   24.943012] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov 16 06:47:20 phillip-laptop kernel: [   24.943670] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 16 06:47:20 phillip-laptop kernel: [   24.943678] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 16 06:47:20 phillip-laptop kernel: [   24.943683] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 16 06:47:20 phillip-laptop kernel: [   24.943688] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 16 06:47:20 phillip-laptop kernel: [   24.943692] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 16 06:47:20 phillip-laptop kernel: [   24.962875] mice: PS/2 mouse device common for all mice
Nov 16 06:47:20 phillip-laptop kernel: [   24.963020] EISA: Probing bus 0 at eisa.0
Nov 16 06:47:20 phillip-laptop kernel: [   24.963046] Cannot allocate resource for EISA slot 4
Nov 16 06:47:20 phillip-laptop kernel: [   24.963059] Cannot allocate resource for EISA slot 7
Nov 16 06:47:20 phillip-laptop kernel: [   24.963063] Cannot allocate resource for EISA slot 8
Nov 16 06:47:20 phillip-laptop kernel: [   24.963067] EISA: Detected 0 cards.
Nov 16 06:47:20 phillip-laptop kernel: [   24.963073] cpuidle: using governor ladder
Nov 16 06:47:20 phillip-laptop kernel: [   24.963077] cpuidle: using governor menu
Nov 16 06:47:20 phillip-laptop kernel: [   24.963181] NET: Registered protocol family 1
Nov 16 06:47:20 phillip-laptop kernel: [   24.963214] Using IPI No-Shortcut mode
Nov 16 06:47:20 phillip-laptop kernel: [   24.963253] registered taskstats version 1
Nov 16 06:47:20 phillip-laptop kernel: [   24.963390]   Magic number: 0:104:772
Nov 16 06:47:20 phillip-laptop kernel: [   24.963501]   hash matches device ptyp8
Nov 16 06:47:20 phillip-laptop kernel: [   24.963544] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 16 06:47:20 phillip-laptop kernel: [   24.963548] EDD information not available.
Nov 16 06:47:20 phillip-laptop kernel: [   24.963925] Freeing unused kernel memory: 368k freed
Nov 16 06:47:20 phillip-laptop kernel: [   24.963956] Write protecting the kernel read-only data: 801k
Nov 16 06:47:20 phillip-laptop kernel: [   24.996202] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 16 06:47:20 phillip-laptop kernel: [   25.160839] vesafb: framebuffer at 0x90000000, mapped to 0xf8880000, using 4608k, total 16384k
Nov 16 06:47:20 phillip-laptop kernel: [   25.160853] vesafb: mode is 1024x768x24, linelength=3072, pages=6
Nov 16 06:47:20 phillip-laptop kernel: [   25.160858] vesafb: protected mode interface info at c000:516e
Nov 16 06:47:20 phillip-laptop kernel: [   25.160863] vesafb: pmi: set display start = c00c51dc, set palette = c00c5216
Nov 16 06:47:20 phillip-laptop kernel: [   25.160867] vesafb: pmi: ports = 7810 7816 7854 7838 783c 785c 7800 7804 78b0 78b2 78b4 
Nov 16 06:47:20 phillip-laptop kernel: [   25.160879] vesafb: scrolling: redraw
Nov 16 06:47:20 phillip-laptop kernel: [   25.160883] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Nov 16 06:47:20 phillip-laptop kernel: [   25.161020] Console: switching to colour frame buffer device 128x48
Nov 16 06:47:20 phillip-laptop kernel: [   25.167189] fb0: VESA VGA frame buffer device
Nov 16 06:47:20 phillip-laptop kernel: [   26.335507] fuse init (API version 7.9)
Nov 16 06:47:20 phillip-laptop kernel: [   26.355508] ACPI: SSDT 77FBE2A0, 0D1C (r1    AMI   CPU1PM        1 INTL 20051117)
Nov 16 06:47:20 phillip-laptop kernel: [   26.356870] ACPI: CPU0 (power states: C1[C1] C2[C2])
Nov 16 06:47:20 phillip-laptop kernel: [   26.356980] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov 16 06:47:20 phillip-laptop kernel: [   26.357150] ACPI: SSDT 77FBEFC0, 0D1C (r1    AMI   CPU2PM        1 INTL 20051117)
Nov 16 06:47:20 phillip-laptop kernel: [   26.358467] ACPI: CPU1 (power states: C1[C1] C2[C2])
Nov 16 06:47:20 phillip-laptop kernel: [   26.359953] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov 16 06:47:20 phillip-laptop kernel: [   26.362088] ACPI: Thermal Zone [THRM] (54 C)
Nov 16 06:47:20 phillip-laptop kernel: [   26.767648] usbcore: registered new interface driver usbfs
Nov 16 06:47:20 phillip-laptop kernel: [   26.767774] usbcore: registered new interface driver hub
Nov 16 06:47:20 phillip-laptop kernel: [   26.768126] SCSI subsystem initialized
Nov 16 06:47:20 phillip-laptop kernel: [   26.775918] usbcore: registered new device driver usb
Nov 16 06:47:20 phillip-laptop kernel: [   26.777399] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 16 06:47:20 phillip-laptop kernel: [   26.777442] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 17
Nov 16 06:47:20 phillip-laptop kernel: [   26.777576] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 16 06:47:20 phillip-laptop kernel: [   26.781627] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Nov 16 06:47:20 phillip-laptop kernel: [   26.785735] ohci_hcd 0000:00:13.0: irq 17, io mem 0xfebfe000
Nov 16 06:47:20 phillip-laptop kernel: [   26.816334] libata version 3.00 loaded.
Nov 16 06:47:20 phillip-laptop kernel: [   26.816587] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 16 06:47:20 phillip-laptop kernel: [   26.820458] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 16 06:47:20 phillip-laptop kernel: [   26.847848] usb usb1: configuration #1 chosen from 1 choice
Nov 16 06:47:20 phillip-laptop kernel: [   26.851933] hub 1-0:1.0: USB hub found
Nov 16 06:47:20 phillip-laptop kernel: [   26.856041] hub 1-0:1.0: 2 ports detected
Nov 16 06:47:20 phillip-laptop kernel: [   26.949519] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Nov 16 06:47:20 phillip-laptop kernel: [   26.963672] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 18
Nov 16 06:47:20 phillip-laptop kernel: [   26.968250] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 16 06:47:20 phillip-laptop kernel: [   26.972676] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Nov 16 06:47:20 phillip-laptop kernel: [   26.977117] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfebfd000
Nov 16 06:47:20 phillip-laptop kernel: [   27.039525] usb usb2: configuration #1 chosen from 1 choice
Nov 16 06:47:20 phillip-laptop kernel: [   27.043929] hub 2-0:1.0: USB hub found
Nov 16 06:47:20 phillip-laptop kernel: [   27.048232] hub 2-0:1.0: 2 ports detected
Nov 16 06:47:20 phillip-laptop kernel: [   27.155349] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 19
Nov 16 06:47:20 phillip-laptop kernel: [   27.159698] ohci_hcd 0000:00:13.2: OHCI Host Controller
Nov 16 06:47:20 phillip-laptop kernel: [   27.164008] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Nov 16 06:47:20 phillip-laptop kernel: [   27.168327] ohci_hcd 0000:00:13.2: irq 19, io mem 0xfebfc000
Nov 16 06:47:20 phillip-laptop kernel: [   27.231245] usb usb3: configuration #1 chosen from 1 choice
Nov 16 06:47:20 phillip-laptop kernel: [   27.235797] hub 3-0:1.0: USB hub found
Nov 16 06:47:20 phillip-laptop kernel: [   27.240145] hub 3-0:1.0: 2 ports detected
Nov 16 06:47:20 phillip-laptop kernel: [   27.347037] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 18
Nov 16 06:47:20 phillip-laptop kernel: [   27.351167] ohci_hcd 0000:00:13.3: OHCI Host Controller
Nov 16 06:47:20 phillip-laptop kernel: [   27.355217] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Nov 16 06:47:20 phillip-laptop kernel: [   27.359299] ohci_hcd 0000:00:13.3: irq 18, io mem 0xfebfb000
Nov 16 06:47:20 phillip-laptop kernel: [   27.421869] usb usb4: configuration #1 chosen from 1 choice
Nov 16 06:47:20 phillip-laptop kernel: [   27.426011] hub 4-0:1.0: USB hub found
Nov 16 06:47:20 phillip-laptop kernel: [   27.430095] hub 4-0:1.0: 2 ports detected
Nov 16 06:47:20 phillip-laptop kernel: [   27.538698] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 19
Nov 16 06:47:20 phillip-laptop kernel: [   27.542877] ohci_hcd 0000:00:13.4: OHCI Host Controller
Nov 16 06:47:20 phillip-laptop kernel: [   27.546975] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Nov 16 06:47:20 phillip-laptop kernel: [   27.551064] ohci_hcd 0000:00:13.4: irq 19, io mem 0xfebfa000
Nov 16 06:47:20 phillip-laptop kernel: [   27.613557] usb usb5: configuration #1 chosen from 1 choice
Nov 16 06:47:20 phillip-laptop kernel: [   27.617620] hub 5-0:1.0: USB hub found
Nov 16 06:47:20 phillip-laptop kernel: [   27.621657] hub 5-0:1.0: 2 ports detected
Nov 16 06:47:20 phillip-laptop kernel: [   27.730436] ahci 0000:00:12.0: version 3.0
Nov 16 06:47:20 phillip-laptop kernel: [   27.730481] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 20
Nov 16 06:47:20 phillip-laptop kernel: [   27.734655] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Nov 16 06:47:20 phillip-laptop kernel: [   27.738910] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Nov 16 06:47:20 phillip-laptop kernel: [   28.744676] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Nov 16 06:47:20 phillip-laptop kernel: [   28.748885] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pio 
Nov 16 06:47:20 phillip-laptop kernel: [   28.753558] scsi0 : ahci
Nov 16 06:47:20 phillip-laptop kernel: [   28.757841] scsi1 : ahci
Nov 16 06:47:20 phillip-laptop kernel: [   28.762169] scsi2 : ahci
Nov 16 06:47:20 phillip-laptop kernel: [   28.766344] scsi3 : ahci
Nov 16 06:47:20 phillip-laptop kernel: [   28.770559] ata1: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 20
Nov 16 06:47:20 phillip-laptop kernel: [   28.774696] ata2: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 20
Nov 16 06:47:20 phillip-laptop kernel: [   28.778736] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 20
Nov 16 06:47:20 phillip-laptop kernel: [   28.782714] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 20
Nov 16 06:47:20 phillip-laptop kernel: [   29.258806] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 16 06:47:20 phillip-laptop kernel: [   29.263670] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
Nov 16 06:47:20 phillip-laptop kernel: [   29.267582] ata1.00: 234441648 sectors, multi 0: LBA48 NCQ (depth 31/32)
Nov 16 06:47:20 phillip-laptop kernel: [   29.272580] ata1.00: configured for UDMA/100
Nov 16 06:47:20 phillip-laptop kernel: [   29.586267] ata2: SATA link down (SStatus 0 SControl 300)
Nov 16 06:47:20 phillip-laptop kernel: [   29.897763] ata3: SATA link down (SStatus 0 SControl 300)
Nov 16 06:47:20 phillip-laptop kernel: [   30.209257] ata4: SATA link down (SStatus 0 SControl 300)
Nov 16 06:47:20 phillip-laptop kernel: [   30.213233] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
Nov 16 06:47:20 phillip-laptop kernel: [   30.217683] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 21
Nov 16 06:47:20 phillip-laptop kernel: [   30.221695] ehci_hcd 0000:00:13.5: EHCI Host Controller
Nov 16 06:47:20 phillip-laptop kernel: [   30.225606] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Nov 16 06:47:20 phillip-laptop kernel: [   30.229844] ehci_hcd 0000:00:13.5: debug port 1
Nov 16 06:47:20 phillip-laptop kernel: [   30.233867] ehci_hcd 0000:00:13.5: irq 21, io mem 0xfebff800
Nov 16 06:47:20 phillip-laptop kernel: [   30.238022] Driver 'sd' needs updating - please use bus_type methods
Nov 16 06:47:20 phillip-laptop kernel: [   30.242097] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov 16 06:47:20 phillip-laptop kernel: [   30.246042] sd 0:0:0:0: [sda] Write Protect is off
Nov 16 06:47:20 phillip-laptop kernel: [   30.249817] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 16 06:47:20 phillip-laptop kernel: [   30.249832] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 16 06:47:20 phillip-laptop kernel: [   30.249840] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 16 06:47:20 phillip-laptop kernel: [   30.249904] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov 16 06:47:20 phillip-laptop kernel: [   30.249914] sd 0:0:0:0: [sda] Write Protect is off
Nov 16 06:47:20 phillip-laptop kernel: [   30.249916] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 16 06:47:20 phillip-laptop kernel: [   30.249931] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 16 06:47:20 phillip-laptop kernel: [   30.249935]  sda:<6>usb usb6: configuration #1 chosen from 1 choice
Nov 16 06:47:20 phillip-laptop kernel: [   30.273593] hub 6-0:1.0: USB hub found
Nov 16 06:47:20 phillip-laptop kernel: [   30.277491] hub 6-0:1.0: 10 ports detected
Nov 16 06:47:20 phillip-laptop kernel: [   30.385108] 8139cp 0000:08:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Nov 16 06:47:20 phillip-laptop kernel: [   30.389157] 8139cp 0000:08:07.0: Try the "8139too" driver instead.
Nov 16 06:47:20 phillip-laptop kernel: [   30.393175] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Nov 16 06:47:20 phillip-laptop kernel: [   30.397697] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
Nov 16 06:47:20 phillip-laptop kernel: [   30.401827] SB600_PATA: not 100% native mode: will probe irqs later
Nov 16 06:47:20 phillip-laptop kernel: [   30.405962]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:DMA
Nov 16 06:47:20 phillip-laptop kernel: [   30.410306] Probing IDE interface ide0...
Nov 16 06:47:20 phillip-laptop kernel: [   30.416295] 8139too Fast Ethernet driver 0.9.28
Nov 16 06:47:20 phillip-laptop kernel: [   30.654609]  sda1 sda2 sda3 < sda5 sda6 > sda4
Nov 16 06:47:20 phillip-laptop kernel: [   30.703622] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 16 06:47:20 phillip-laptop kernel: [   30.713376] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 16 06:47:20 phillip-laptop kernel: [   31.196105] hdb: HL-DT-ST DVDRAM GSA-T20N, ATAPI CD/DVD-ROM drive
Nov 16 06:47:20 phillip-laptop kernel: [   31.479187] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Nov 16 06:47:20 phillip-laptop kernel: [   31.479999] hdb: UDMA/33 mode selected
Nov 16 06:47:20 phillip-laptop kernel: [   31.484291] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov 16 06:47:20 phillip-laptop kernel: [   31.491555] ACPI: PCI Interrupt 0000:08:07.0[A] -> GSI 20 (level, low) -> IRQ 22
Nov 16 06:47:20 phillip-laptop kernel: [   31.497537] eth0: RealTek RTL8139 at 0xb800, 00:1d:60:49:6c:65, IRQ 22
Nov 16 06:47:20 phillip-laptop kernel: [   31.501624] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Nov 16 06:47:20 phillip-laptop kernel: [   31.517866] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Nov 16 06:47:20 phillip-laptop kernel: [   31.522014] Uniform CD-ROM driver Revision: 3.20
Nov 16 06:47:20 phillip-laptop kernel: [   31.616441] Attempting manual resume
Nov 16 06:47:20 phillip-laptop kernel: [   31.620714] swsusp: Resume From Partition 8:6
Nov 16 06:47:20 phillip-laptop kernel: [   31.620716] PM: Checking swsusp image.
Nov 16 06:47:20 phillip-laptop kernel: [   31.620869] PM: Resume from disk failed.
Nov 16 06:47:20 phillip-laptop kernel: [   31.645251] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov 16 06:47:20 phillip-laptop kernel: [   31.649605] EXT3-fs: write access will be enabled during recovery.
Nov 16 06:47:20 phillip-laptop kernel: [   31.713707] kjournald starting.  Commit interval 5 seconds
Nov 16 06:47:20 phillip-laptop kernel: [   31.713728] EXT3-fs: recovery complete.
Nov 16 06:47:20 phillip-laptop kernel: [   31.714323] EXT3-fs: mounted filesystem with ordered data mode.
Nov 16 06:47:20 phillip-laptop kernel: [   42.131601] Linux agpgart interface v0.102
Nov 16 06:47:20 phillip-laptop kernel: [   42.221874] input: PC Speaker as /devices/platform/pcspkr/input/input2
Nov 16 06:47:20 phillip-laptop kernel: [   42.266196] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 16 06:47:20 phillip-laptop kernel: [   42.470471] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 16 06:47:20 phillip-laptop kernel: [   42.622210] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Nov 16 06:47:20 phillip-laptop kernel: [   42.720372] input: Power Button (FF) as /devices/virtual/input/input3
Nov 16 06:47:20 phillip-laptop kernel: [   42.773841] ACPI: Power Button (FF) [PWRF]
Nov 16 06:47:20 phillip-laptop kernel: [   42.777830] input: Lid Switch as /devices/virtual/input/input4
Nov 16 06:47:20 phillip-laptop kernel: [   42.807955] ACPI: Lid Switch [LID]
Nov 16 06:47:20 phillip-laptop kernel: [   42.811761] input: Power Button (CM) as /devices/virtual/input/input5
Nov 16 06:47:20 phillip-laptop kernel: [   42.876697] ACPI: Power Button (CM) [PWRB]
Nov 16 06:47:20 phillip-laptop kernel: [   42.880436] input: Sleep Button (CM) as /devices/virtual/input/input6
Nov 16 06:47:20 phillip-laptop kernel: [   42.936590] ACPI: Sleep Button (CM) [SLPB]
Nov 16 06:47:20 phillip-laptop kernel: [   42.940684] asus-laptop: Asus Laptop Support version 0.42
Nov 16 06:47:20 phillip-laptop kernel: [   42.944546] asus-laptop: BSTS called, 0x22 returned
Nov 16 06:47:20 phillip-laptop kernel: [   42.948215] asus-laptop:   X51R model detected
Nov 16 06:47:20 phillip-laptop kernel: [   43.307508] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
Nov 16 06:47:20 phillip-laptop kernel: [   43.312167] Yenta: CardBus bridge found at 0000:08:01.0 [1043:1627]
Nov 16 06:47:20 phillip-laptop kernel: [   43.360592] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Nov 16 06:47:20 phillip-laptop kernel: [   43.444561] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
Nov 16 06:47:20 phillip-laptop kernel: [   43.448337] Socket status: 30000006
Nov 16 06:47:20 phillip-laptop kernel: [   43.452503] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
Nov 16 06:47:20 phillip-laptop kernel: [   43.456332] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
Nov 16 06:47:20 phillip-laptop kernel: [   43.460323] cs: IO port probe 0xa000-0xbfff: clean.
Nov 16 06:47:20 phillip-laptop kernel: [   43.464647] pcmcia: parent PCI bridge Memory window: 0xfca00000 - 0xfeafffff
Nov 16 06:47:20 phillip-laptop kernel: [   43.468905] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xdfefffff
Nov 16 06:47:20 phillip-laptop kernel: [   43.583498] ACPI: Battery Slot [BAT0] (battery present)
Nov 16 06:47:20 phillip-laptop kernel: [   43.614265] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input8
Nov 16 06:47:20 phillip-laptop kernel: [   43.644576] sdhci: Secure Digital Host Controller Interface driver
Nov 16 06:47:20 phillip-laptop kernel: [   43.648432] sdhci: Copyright(c) Pierre Ossman
Nov 16 06:47:20 phillip-laptop kernel: [   43.652348] sdhci: SDHCI controller found at 0000:08:01.1 [1180:0822] (rev 17)
Nov 16 06:47:20 phillip-laptop kernel: [   43.656429] ACPI: PCI Interrupt 0000:08:01.1[C] -> GSI 23 (level, low) -> IRQ 23
Nov 16 06:47:20 phillip-laptop kernel: [   43.660890] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Nov 16 06:47:20 phillip-laptop kernel: [   43.666051] mmc0: SDHCI at 0xfeaffc00 irq 23 DMA
Nov 16 06:47:20 phillip-laptop kernel: [   43.693949] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov 16 06:47:20 phillip-laptop kernel: [   43.699761] ACPI: AC Adapter [AC0] (on-line)
Nov 16 06:47:20 phillip-laptop kernel: [   44.047009] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
Nov 16 06:47:20 phillip-laptop kernel: [   44.987456] cs: IO port probe 0x100-0x3af: clean.
Nov 16 06:47:20 phillip-laptop kernel: [   44.993850] cs: IO port probe 0x3e0-0x4ff: clean.
Nov 16 06:47:20 phillip-laptop kernel: [   44.998933] cs: IO port probe 0x820-0x8ff: clean.
Nov 16 06:47:20 phillip-laptop kernel: [   45.003422] cs: IO port probe 0xc00-0xcf7: clean.
Nov 16 06:47:20 phillip-laptop kernel: [   45.008347] cs: IO port probe 0xa00-0xaff: clean.
Nov 16 06:47:20 phillip-laptop kernel: [   45.947131] lp: driver loaded but no devices found
Nov 16 06:47:20 phillip-laptop kernel: [   46.014251] ath_hal: module license 'Proprietary' taints kernel.
Nov 16 06:47:20 phillip-laptop kernel: [   46.024318] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
Nov 16 06:47:20 phillip-laptop kernel: [   46.139706] wlan: trunk
Nov 16 06:47:20 phillip-laptop kernel: [   46.191937] ath_pci: trunk
Nov 16 06:47:20 phillip-laptop kernel: [   46.196752] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Nov 16 06:47:20 phillip-laptop kernel: [   46.201432] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov 16 06:47:20 phillip-laptop kernel: [   46.693506] MadWifi: ath_attach: Switching rfkill capability off
Nov 16 06:47:20 phillip-laptop kernel: [   46.733421] ath_rate_sample: 1.2 (trunk)
Nov 16 06:47:20 phillip-laptop kernel: [   46.738408] MadWifi: ath_attach: Switching per-packet transmit power control off
Nov 16 06:47:20 phillip-laptop kernel: [   46.743145] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Nov 16 06:47:20 phillip-laptop kernel: [   46.748360] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov 16 06:47:20 phillip-laptop kernel: [   46.752937] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Nov 16 06:47:20 phillip-laptop kernel: [   46.757441] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
Nov 16 06:47:20 phillip-laptop kernel: [   46.761868] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
Nov 16 06:47:20 phillip-laptop kernel: [   46.766241] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
Nov 16 06:47:20 phillip-laptop kernel: [   46.770578] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
Nov 16 06:47:20 phillip-laptop kernel: [   46.774867] wifi0: ath_announce: Use hw queue 8 for CAB traffic
Nov 16 06:47:20 phillip-laptop kernel: [   46.779136] wifi0: ath_announce: Use hw queue 9 for beacons
Nov 16 06:47:20 phillip-laptop kernel: [   46.801386] ath_pci: wifi0: Atheros 5424/2424: mem=0xf89f0000, irq=17
Nov 16 06:47:20 phillip-laptop kernel: [   46.888882] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFB) is beyond end of object [20070126]
Nov 16 06:47:20 phillip-laptop kernel: [   46.893575] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PSS] (Node f7c49b88), AE_AML_PACKAGE_LIMIT
Nov 16 06:47:20 phillip-laptop kernel: [   46.897975] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Nov 16 06:47:20 phillip-laptop kernel: [   46.902541] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFB) is beyond end of object [20070126]
Nov 16 06:47:20 phillip-laptop kernel: [   46.906873] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PSS] (Node f7c49d98), AE_AML_PACKAGE_LIMIT
Nov 16 06:47:20 phillip-laptop kernel: [   46.906924] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Nov 16 06:47:20 phillip-laptop kernel: [   47.043511] Adding 872480k swap on /dev/sda6.  Priority:-1 extents:1 across:872480k
Nov 16 06:47:20 phillip-laptop kernel: [   47.597242] EXT3 FS on sda4, internal journal
Nov 16 06:47:20 phillip-laptop kernel: [   48.848359] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 16 06:47:20 phillip-laptop kernel: [   48.891193] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Nov 16 06:47:20 phillip-laptop kernel: [   49.001097] NET: Registered protocol family 10
Nov 16 06:47:20 phillip-laptop kernel: [   49.001469] lo: Disabled Privacy Extensions
Nov 16 06:47:20 phillip-laptop kernel: [   49.019965] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 16 06:47:20 phillip-laptop kernel: [   49.972225] No dock devices found.
Nov 16 06:47:21 phillip-laptop NetworkManager: <info>  starting... 
Nov 16 06:47:21 phillip-laptop avahi-daemon[5254]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov 16 06:47:21 phillip-laptop avahi-daemon[5254]: Successfully dropped root privileges.
Nov 16 06:47:21 phillip-laptop avahi-daemon[5254]: avahi-daemon 0.6.22 starting up.
Nov 16 06:47:21 phillip-laptop avahi-daemon[5254]: Successfully called chroot().
Nov 16 06:47:21 phillip-laptop avahi-daemon[5254]: Successfully dropped remaining capabilities.
Nov 16 06:47:21 phillip-laptop avahi-daemon[5254]: No service file found in /etc/avahi/services.
Nov 16 06:47:21 phillip-laptop avahi-daemon[5254]: Network interface enumeration completed.
Nov 16 06:47:21 phillip-laptop avahi-daemon[5254]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 16 06:47:21 phillip-laptop avahi-daemon[5254]: Server startup complete. Host name is phillip-laptop.local. Local service cookie is 2054049646.
Nov 16 06:47:21 phillip-laptop kernel: [   51.324275] ppdev: user-space parallel port driver
Nov 16 06:47:21 phillip-laptop kernel: [   51.542887] audit(1226818041.742:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5287 profile="/usr/sbin/cupsd" namespace="default"
Nov 16 06:47:22 phillip-laptop kernel: [   51.835581] apm: BIOS not found.
Nov 16 06:47:22 phillip-laptop atieventsd[5324]: ATI External Events Daemon started... 
Nov 16 06:47:22 phillip-laptop atieventsd[5324]: Event daemon control socket created 
Nov 16 06:47:22 phillip-laptop atieventsd[5324]: acpid connection established 
Nov 16 06:47:25 phillip-laptop avgscan[5341]: Starting AVG Anti-Virus in daemon mode. 
Nov 16 06:47:25 phillip-laptop avgscan[5341]: AVG Anti-Virus Daemon started.
Nov 16 06:47:25 phillip-laptop avgscan[5341]: Starting AVG Anti-Virus on-access scanner. 
Nov 16 06:47:25 phillip-laptop avgscan[5341]: AVG Anti-Virus on-access scanner started
Nov 16 06:47:25 phillip-laptop avgscan[5343]: ERROR: registration to Dazuko failed
Nov 16 06:47:25 phillip-laptop avgscan[5343]: AVG Anti-Virus on-access failed to start.
Nov 16 06:48:35 phillip-laptop syslogd 1.5.0#1ubuntu1: restart.
Nov 16 06:48:35 phillip-laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Nov 16 06:48:35 phillip-laptop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Nov 16 06:48:35 phillip-laptop kernel: Symbols match kernel version 2.6.24.
Nov 16 06:48:35 phillip-laptop kernel: Loaded 28367 symbols from 108 modules.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fa8000 (usable)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fa8000 - 0000000077fb0000 (ACPI NVS)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fb0000 - 0000000077fbe000 (ACPI data)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077fbe000 - 0000000077ff0000 (ACPI NVS)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 0000000077ff0000 - 0000000078000000 (reserved)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] 1023MB HIGHMEM available.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] 896MB LOWMEM available.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] found SMP MP-table at 000ff780
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 491432) 0 entries of 256 used
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Zone PFN ranges:
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   DMA             0 ->     4096
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   HighMem    229376 ->   491432
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Movable zone start PFN for each node
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]     0:        0 ->   491432
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] On node 0 totalpages: 491432
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   HighMem zone: 2047 pages used for memmap
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   HighMem zone: 260009 pages, LIFO batch:31
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] DMI 2.4 present.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7F50 checksum 0
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: RSDP 000F7F50, 0024 (r2 ACPIAM)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: XSDT 77FB0100, 0054 (r1 _ASUS_ Notebook  7000731 MSFT       97)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: FACP 77FB0290, 00F4 (r3 A.M.I  OEMFACP   7000731 MSFT       97)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: DSDT 77FB0630, 77A4 (r1  T12R0 T12R0000        0 INTL 20051117)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: FACS 77FBE000, 0040
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: APIC 77FB0390, 005C (r1 A.M.I  OEMAPIC   7000731 MSFT       97)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: MCFG 77FB03F0, 003C (r1 A.M.I  OEMMCFG   7000731 MSFT       97)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: SLIC 77FB0430, 0176 (r1 _ASUS_ Notebook  7000731 MSFT       97)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: BOOT 77FB0600, 0028 (r1 A.M.I  OEMBOOT   7000731 MSFT       97)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: OEMB 77FBE040, 005B (r1 A.M.I  AMI_OEM   7000731 MSFT       97)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Processor #0 6:14 APIC version 20
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Processor #1 6:14 APIC version 20
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:86e00000)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487593
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Kernel command line: root=UUID=3c071645-e73d-42b0-95ae-d796b29b38b3 ro splash vga=792
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Initializing CPU#0
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 16 06:48:35 phillip-laptop kernel: [    0.000000] Detected 1862.249 MHz processor.
Nov 16 06:48:35 phillip-laptop kernel: [   23.365192] Console: colour dummy device 80x25
Nov 16 06:48:35 phillip-laptop kernel: [   23.365197] console [tty0] enabled
Nov 16 06:48:35 phillip-laptop kernel: [   23.366271] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 16 06:48:35 phillip-laptop kernel: [   23.366988] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 16 06:48:35 phillip-laptop kernel: [   23.479385] Memory: 1935620k/1965728k available (2177k kernel code, 28932k reserved, 1006k data, 368k init, 1048224k highmem)
Nov 16 06:48:35 phillip-laptop kernel: [   23.479408] virtual kernel memory layout:
Nov 16 06:48:35 phillip-laptop kernel: [   23.479409]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Nov 16 06:48:35 phillip-laptop kernel: [   23.479410]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 16 06:48:35 phillip-laptop kernel: [   23.479411]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov 16 06:48:35 phillip-laptop kernel: [   23.479413]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov 16 06:48:35 phillip-laptop kernel: [   23.479414]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Nov 16 06:48:35 phillip-laptop kernel: [   23.479415]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Nov 16 06:48:35 phillip-laptop kernel: [   23.479416]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Nov 16 06:48:35 phillip-laptop kernel: [   23.479437] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 16 06:48:35 phillip-laptop kernel: [   23.479509] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Nov 16 06:48:35 phillip-laptop kernel: [   23.559417] Calibrating delay using timer specific routine.. 3728.22 BogoMIPS (lpj=7456453)
Nov 16 06:48:35 phillip-laptop kernel: [   23.559467] Security Framework initialized
Nov 16 06:48:35 phillip-laptop kernel: [   23.559484] SELinux:  Disabled at boot.
Nov 16 06:48:35 phillip-laptop kernel: [   23.559509] AppArmor: AppArmor initialized
Nov 16 06:48:35 phillip-laptop kernel: [   23.559516] Failure registering capabilities with primary security module.
Nov 16 06:48:35 phillip-laptop kernel: [   23.559528] Mount-cache hash table entries: 512
Nov 16 06:48:35 phillip-laptop kernel: [   23.559711] Initializing cgroup subsys ns
Nov 16 06:48:35 phillip-laptop kernel: [   23.559722] Initializing cgroup subsys cpuacct
Nov 16 06:48:35 phillip-laptop kernel: [   23.559739] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
Nov 16 06:48:35 phillip-laptop kernel: [   23.559748] monitor/mwait feature present.
Nov 16 06:48:35 phillip-laptop kernel: [   23.559752] using mwait in idle threads.
Nov 16 06:48:35 phillip-laptop kernel: [   23.559758] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 16 06:48:35 phillip-laptop kernel: [   23.559762] CPU: L2 cache: 1024K
Nov 16 06:48:35 phillip-laptop kernel: [   23.559768] CPU: Physical Processor ID: 0
Nov 16 06:48:35 phillip-laptop kernel: [   23.559771] CPU: Processor Core ID: 0
Nov 16 06:48:35 phillip-laptop kernel: [   23.559775] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000 00000000
Nov 16 06:48:35 phillip-laptop kernel: [   23.559788] Compat vDSO mapped to ffffe000.
Nov 16 06:48:35 phillip-laptop kernel: [   23.559807] Checking 'hlt' instruction... OK.
Nov 16 06:48:35 phillip-laptop kernel: [   23.575810] SMP alternatives: switching to UP code
Nov 16 06:48:35 phillip-laptop kernel: [   23.577673] Early unpacking initramfs... done
Nov 16 06:48:35 phillip-laptop kernel: [   23.917790] ACPI: Core revision 20070126
Nov 16 06:48:35 phillip-laptop kernel: [   23.917871] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 16 06:48:35 phillip-laptop kernel: [   23.923095] CPU0: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
Nov 16 06:48:35 phillip-laptop kernel: [   23.923119] SMP alternatives: switching to SMP code
Nov 16 06:48:35 phillip-laptop kernel: [   23.923873] Booting processor 1/1 eip 3000
Nov 16 06:48:35 phillip-laptop kernel: [   23.934040] Initializing CPU#1
Nov 16 06:48:35 phillip-laptop kernel: [   24.010691] Calibrating delay using timer specific routine.. 3724.56 BogoMIPS (lpj=7449128)
Nov 16 06:48:35 phillip-laptop kernel: [   24.010699] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
Nov 16 06:48:35 phillip-laptop kernel: [   24.010704] monitor/mwait feature present.
Nov 16 06:48:35 phillip-laptop kernel: [   24.010708] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 16 06:48:35 phillip-laptop kernel: [   24.010709] CPU: L2 cache: 1024K
Nov 16 06:48:35 phillip-laptop kernel: [   24.010712] CPU: Physical Processor ID: 0
Nov 16 06:48:35 phillip-laptop kernel: [   24.010713] CPU: Processor Core ID: 1
Nov 16 06:48:35 phillip-laptop kernel: [   24.010715] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000 00000000
Nov 16 06:48:35 phillip-laptop kernel: [   24.011244] CPU1: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
Nov 16 06:48:35 phillip-laptop kernel: [   24.011287] Total of 2 processors activated (7452.79 BogoMIPS).
Nov 16 06:48:35 phillip-laptop kernel: [   24.011467] ENABLING IO-APIC IRQs
Nov 16 06:48:35 phillip-laptop kernel: [   24.011657] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 16 06:48:35 phillip-laptop kernel: [   24.158596] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov 16 06:48:35 phillip-laptop kernel: [   24.178590] Brought up 2 CPUs
Nov 16 06:48:35 phillip-laptop kernel: [   24.178617] CPU0 attaching sched-domain:
Nov 16 06:48:35 phillip-laptop kernel: [   24.178620]  domain 0: span 03
Nov 16 06:48:35 phillip-laptop kernel: [   24.178622]   groups: 01 02
Nov 16 06:48:35 phillip-laptop kernel: [   24.178625] CPU1 attaching sched-domain:
Nov 16 06:48:35 phillip-laptop kernel: [   24.178627]  domain 0: span 03
Nov 16 06:48:35 phillip-laptop kernel: [   24.178628]   groups: 02 01
Nov 16 06:48:35 phillip-laptop kernel: [   24.178920] net_namespace: 64 bytes
Nov 16 06:48:35 phillip-laptop kernel: [   24.178933] Booting paravirtualized kernel on bare hardware
Nov 16 06:48:35 phillip-laptop kernel: [   24.179401] Time:  6:48:08  Date: 11/16/08
Nov 16 06:48:35 phillip-laptop kernel: [   24.179432] NET: Registered protocol family 16
Nov 16 06:48:35 phillip-laptop kernel: [   24.179697] EISA bus registered
Nov 16 06:48:35 phillip-laptop kernel: [   24.179705] ACPI: bus type pci registered
Nov 16 06:48:35 phillip-laptop kernel: [   24.180000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=9
Nov 16 06:48:35 phillip-laptop kernel: [   24.180009] PCI: Using configuration type 1
Nov 16 06:48:35 phillip-laptop kernel: [   24.180028] Setting up standard PCI resources
Nov 16 06:48:35 phillip-laptop kernel: [   24.180516] mtrr: your CPUs had inconsistent variable MTRR settings
Nov 16 06:48:35 phillip-laptop kernel: [   24.180521] mtrr: probably your BIOS does not setup all CPUs.
Nov 16 06:48:35 phillip-laptop kernel: [   24.180525] mtrr: corrected configuration.
Nov 16 06:48:35 phillip-laptop kernel: [   24.184700] ACPI: EC: Look up EC in DSDT
Nov 16 06:48:35 phillip-laptop kernel: [   24.230489] ACPI: Interpreter enabled
Nov 16 06:48:35 phillip-laptop kernel: [   24.230495] ACPI: (supports S0 S1 S3 S4 S5)
Nov 16 06:48:35 phillip-laptop kernel: [   24.230517] ACPI: Using IOAPIC for interrupt routing
Nov 16 06:48:35 phillip-laptop kernel: [   24.237785] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
Nov 16 06:48:35 phillip-laptop kernel: [   24.237793] ACPI: EC: driver started in poll mode
Nov 16 06:48:35 phillip-laptop kernel: [   24.237926] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 16 06:48:35 phillip-laptop kernel: [   24.238238] pci 0000:00:12.0: set SATA to AHCI mode
Nov 16 06:48:35 phillip-laptop kernel: [   24.240093] PCI: Transparent bridge - 0000:00:14.4
Nov 16 06:48:35 phillip-laptop kernel: [   24.240203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 16 06:48:35 phillip-laptop kernel: [   24.240341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Nov 16 06:48:35 phillip-laptop kernel: [   24.240488] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
Nov 16 06:48:35 phillip-laptop kernel: [   24.240599] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
Nov 16 06:48:35 phillip-laptop kernel: [   24.240707] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Nov 16 06:48:35 phillip-laptop kernel: [   24.240830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Nov 16 06:48:35 phillip-laptop kernel: [   24.240980] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
Nov 16 06:48:35 phillip-laptop kernel: [   24.246151] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *11 12)
Nov 16 06:48:35 phillip-laptop kernel: [   24.246296] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 12)
Nov 16 06:48:35 phillip-laptop kernel: [   24.246437] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 12)
Nov 16 06:48:35 phillip-laptop kernel: [   24.246583] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 12) *10
Nov 16 06:48:35 phillip-laptop kernel: [   24.246725] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 12)
Nov 16 06:48:35 phillip-laptop kernel: [   24.246866] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 12)
Nov 16 06:48:35 phillip-laptop kernel: [   24.247006] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 12)
Nov 16 06:48:35 phillip-laptop kernel: [   24.247147] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 12)
Nov 16 06:48:35 phillip-laptop kernel: [   24.247300] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 16 06:48:35 phillip-laptop kernel: [   24.247342] pnp: PnP ACPI init
Nov 16 06:48:35 phillip-laptop kernel: [   24.247352] ACPI: bus type pnp registered
Nov 16 06:48:35 phillip-laptop kernel: [   24.249671] pnp: PnP ACPI: found 12 devices
Nov 16 06:48:35 phillip-laptop kernel: [   24.249676] ACPI: ACPI bus type pnp unregistered
Nov 16 06:48:35 phillip-laptop kernel: [   24.249682] PnPBIOS: Disabled by ACPI PNP
Nov 16 06:48:35 phillip-laptop kernel: [   24.250003] PCI: Using ACPI for IRQ routing
Nov 16 06:48:35 phillip-laptop kernel: [   24.250008] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 16 06:48:35 phillip-laptop kernel: [   24.306379] NET: Registered protocol family 8
Nov 16 06:48:35 phillip-laptop kernel: [   24.306384] NET: Registered protocol family 20
Nov 16 06:48:35 phillip-laptop kernel: [   24.306462] AppArmor: AppArmor Filesystem Enabled
Nov 16 06:48:35 phillip-laptop kernel: [   24.310225] Time: tsc clocksource has been installed.
Nov 16 06:48:35 phillip-laptop kernel: [   24.326384] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326394] system 00:05: ioport range 0x40b-0x40b has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326399] system 00:05: ioport range 0x4d6-0x4d6 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326404] system 00:05: ioport range 0xc00-0xc01 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326409] system 00:05: ioport range 0xc14-0xc14 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326414] system 00:05: ioport range 0xc50-0xc51 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326419] system 00:05: ioport range 0xc52-0xc52 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326424] system 00:05: ioport range 0xc6c-0xc6c has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326429] system 00:05: ioport range 0xc6f-0xc6f has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326434] system 00:05: ioport range 0xcd0-0xcd1 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326439] system 00:05: ioport range 0xcd2-0xcd3 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326444] system 00:05: ioport range 0xcd4-0xcd5 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326450] system 00:05: ioport range 0xcd6-0xcd7 has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326455] system 00:05: ioport range 0xcd8-0xcdf has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326460] system 00:05: ioport range 0x800-0x89f has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326465] system 00:05: ioport range 0xb00-0xb1f could not be reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326470] system 00:05: ioport range 0x900-0x90f has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326476] system 00:05: ioport range 0x910-0x91f has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326481] system 00:05: ioport range 0xfe00-0xfefe has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326486] system 00:05: ioport range 0x4000-0x40fe has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326492] system 00:05: iomem range 0xfed20000-0xfed3ffff has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326497] system 00:05: iomem range 0xfed45000-0xfed89fff has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326503] system 00:05: iomem range 0xffb80000-0xffbfffff could not be reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326509] system 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326521] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326527] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326536] system 00:09: ioport range 0x25c-0x25c has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326542] system 00:09: ioport range 0x25d-0x25d has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326547] system 00:09: ioport range 0x25e-0x25e has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326552] system 00:09: ioport range 0x25f-0x25f has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326561] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326570] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326575] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326581] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326586] system 00:0b: iomem range 0x100000-0x77ffffff could not be reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.326592] system 00:0b: iomem range 0x0-0x0 could not be reserved
Nov 16 06:48:35 phillip-laptop kernel: [   24.357112] PCI: Bridge: 0000:00:01.0
Nov 16 06:48:35 phillip-laptop kernel: [   24.357117]   IO window: 7000-7fff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357122]   MEM window: f8800000-f88fffff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357127]   PREFETCH window: 8ff00000-afefffff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357133] PCI: Bridge: 0000:00:04.0
Nov 16 06:48:35 phillip-laptop kernel: [   24.357136]   IO window: disabled.
Nov 16 06:48:35 phillip-laptop kernel: [   24.357141]   MEM window: f8900000-f89fffff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357146]   PREFETCH window: disabled.
Nov 16 06:48:35 phillip-laptop kernel: [   24.357151] PCI: Bridge: 0000:00:05.0
Nov 16 06:48:35 phillip-laptop kernel: [   24.357155]   IO window: 8000-9fff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357160]   MEM window: f8a00000-fc9fffff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357165]   PREFETCH window: aff00000-cfefffff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357171] PCI: Bridge: 0000:00:06.0
Nov 16 06:48:35 phillip-laptop kernel: [   24.357174]   IO window: disabled.
Nov 16 06:48:35 phillip-laptop kernel: [   24.357179]   MEM window: disabled.
Nov 16 06:48:35 phillip-laptop kernel: [   24.357183]   PREFETCH window: disabled.
Nov 16 06:48:35 phillip-laptop kernel: [   24.357189] PCI: Bridge: 0000:00:07.0
Nov 16 06:48:35 phillip-laptop kernel: [   24.357192]   IO window: disabled.
Nov 16 06:48:35 phillip-laptop kernel: [   24.357197]   MEM window: disabled.
Nov 16 06:48:35 phillip-laptop kernel: [   24.357201]   PREFETCH window: disabled.
Nov 16 06:48:35 phillip-laptop kernel: [   24.357218] PCI: Bus 9, cardbus bridge: 0000:08:01.0
Nov 16 06:48:35 phillip-laptop kernel: [   24.357222]   IO window: 0000a000-0000a0ff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357230]   IO window: 0000a400-0000a4ff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357237]   PREFETCH window: d0000000-d3ffffff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357245]   MEM window: 80000000-83ffffff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357253] PCI: Bridge: 0000:00:14.4
Nov 16 06:48:35 phillip-laptop kernel: [   24.357258]   IO window: a000-bfff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357266]   MEM window: fca00000-feafffff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357273]   PREFETCH window: cff00000-dfefffff
Nov 16 06:48:35 phillip-laptop kernel: [   24.357301] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 16 06:48:35 phillip-laptop kernel: [   24.357312] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov 16 06:48:35 phillip-laptop kernel: [   24.357323] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 16 06:48:35 phillip-laptop kernel: [   24.357333] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 16 06:48:35 phillip-laptop kernel: [   24.357364] ACPI: PCI Interrupt 0000:08:01.0[A] -> GSI 21 (level, low) -> IRQ 16
Nov 16 06:48:35 phillip-laptop kernel: [   24.357386] NET: Registered protocol family 2
Nov 16 06:48:35 phillip-laptop kernel: [   24.402302] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 16 06:48:35 phillip-laptop kernel: [   24.402615] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 16 06:48:35 phillip-laptop kernel: [   24.404021] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 16 06:48:35 phillip-laptop kernel: [   24.405017] TCP: Hash tables configured (established 131072 bind 65536)
Nov 16 06:48:35 phillip-laptop kernel: [   24.405028] TCP reno registered
Nov 16 06:48:35 phillip-laptop kernel: [   24.414431] checking if image is initramfs... it is
Nov 16 06:48:35 phillip-laptop kernel: [   24.857353] Switched to high resolution mode on CPU 0
Nov 16 06:48:35 phillip-laptop kernel: [   24.857476] Switched to high resolution mode on CPU 1
Nov 16 06:48:35 phillip-laptop kernel: [   25.099689] Freeing initrd memory: 8586k freed
Nov 16 06:48:35 phillip-laptop kernel: [   25.099994] Simple Boot Flag at 0xff set to 0x1
Nov 16 06:48:35 phillip-laptop kernel: [   25.100865] audit: initializing netlink socket (disabled)
Nov 16 06:48:35 phillip-laptop kernel: [   25.100890] audit(1226818088.492:1): initialized
Nov 16 06:48:35 phillip-laptop kernel: [   25.101202] highmem bounce pool size: 64 pages
Nov 16 06:48:35 phillip-laptop kernel: [   25.103490] VFS: Disk quotas dquot_6.5.1
Nov 16 06:48:35 phillip-laptop kernel: [   25.103588] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 16 06:48:35 phillip-laptop kernel: [   25.103751] io scheduler noop registered
Nov 16 06:48:35 phillip-laptop kernel: [   25.103756] io scheduler anticipatory registered
Nov 16 06:48:35 phillip-laptop kernel: [   25.103760] io scheduler deadline registered
Nov 16 06:48:35 phillip-laptop kernel: [   25.103772] io scheduler cfq registered (default)
Nov 16 06:48:35 phillip-laptop kernel: [   25.103859] Boot video device is 0000:01:05.0
Nov 16 06:48:35 phillip-laptop kernel: [   25.104016] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 16 06:48:35 phillip-laptop kernel: [   25.104052] assign_interrupt_mode Found MSI capability
Nov 16 06:48:35 phillip-laptop kernel: [   25.104095] Allocate Port Service[0000:00:04.0:pcie00]
Nov 16 06:48:35 phillip-laptop kernel: [   25.104191] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov 16 06:48:35 phillip-laptop kernel: [   25.104227] assign_interrupt_mode Found MSI capability
Nov 16 06:48:35 phillip-laptop kernel: [   25.104262] Allocate Port Service[0000:00:05.0:pcie00]
Nov 16 06:48:35 phillip-laptop kernel: [   25.104302] Allocate Port Service[0000:00:05.0:pcie02]
Nov 16 06:48:35 phillip-laptop kernel: [   25.104389] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 16 06:48:35 phillip-laptop kernel: [   25.104425] assign_interrupt_mode Found MSI capability
Nov 16 06:48:35 phillip-laptop kernel: [   25.104460] Allocate Port Service[0000:00:06.0:pcie00]
Nov 16 06:48:35 phillip-laptop kernel: [   25.104551] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 16 06:48:35 phillip-laptop kernel: [   25.104587] assign_interrupt_mode Found MSI capability
Nov 16 06:48:35 phillip-laptop kernel: [   25.104626] Allocate Port Service[0000:00:07.0:pcie00]
Nov 16 06:48:35 phillip-laptop kernel: [   25.104935] isapnp: Scanning for PnP cards...
Nov 16 06:48:35 phillip-laptop kernel: [   25.458488] isapnp: No Plug & Play device found
Nov 16 06:48:35 phillip-laptop kernel: [   25.489253] Real Time Clock Driver v1.12ac
Nov 16 06:48:35 phillip-laptop kernel: [   25.489419] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 16 06:48:35 phillip-laptop kernel: [   25.490905] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 16 06:48:35 phillip-laptop kernel: [   25.490988] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 16 06:48:35 phillip-laptop kernel: [   25.491104] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov 16 06:48:35 phillip-laptop kernel: [   25.493229] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov 16 06:48:35 phillip-laptop kernel: [   25.493895] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 16 06:48:35 phillip-laptop kernel: [   25.493904] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 16 06:48:35 phillip-laptop kernel: [   25.493909] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 16 06:48:35 phillip-laptop kernel: [   25.493914] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 16 06:48:35 phillip-laptop kernel: [   25.493918] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 16 06:48:35 phillip-laptop kernel: [   25.513335] mice: PS/2 mouse device common for all mice
Nov 16 06:48:35 phillip-laptop kernel: [   25.513483] EISA: Probing bus 0 at eisa.0
Nov 16 06:48:35 phillip-laptop kernel: [   25.513508] Cannot allocate resource for EISA slot 4
Nov 16 06:48:35 phillip-laptop kernel: [   25.513521] Cannot allocate resource for EISA slot 7
Nov 16 06:48:35 phillip-laptop kernel: [   25.513526] Cannot allocate resource for EISA slot 8
Nov 16 06:48:35 phillip-laptop kernel: [   25.513529] EISA: Detected 0 cards.
Nov 16 06:48:35 phillip-laptop kernel: [   25.513535] cpuidle: using governor ladder
Nov 16 06:48:35 phillip-laptop kernel: [   25.513538] cpuidle: using governor menu
Nov 16 06:48:35 phillip-laptop kernel: [   25.513643] NET: Registered protocol family 1
Nov 16 06:48:35 phillip-laptop kernel: [   25.513678] Using IPI No-Shortcut mode
Nov 16 06:48:35 phillip-laptop kernel: [   25.513719] registered taskstats version 1
Nov 16 06:48:35 phillip-laptop kernel: [   25.513856]   Magic number: 0:654:822
Nov 16 06:48:35 phillip-laptop kernel: [   25.513954]   hash matches device ptyt2
Nov 16 06:48:35 phillip-laptop kernel: [   25.514011] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 16 06:48:35 phillip-laptop kernel: [   25.514015] EDD information not available.
Nov 16 06:48:35 phillip-laptop kernel: [   25.514392] Freeing unused kernel memory: 368k freed
Nov 16 06:48:35 phillip-laptop kernel: [   25.545456] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 16 06:48:35 phillip-laptop kernel: [   25.722302] vesafb: framebuffer at 0x90000000, mapped to 0xf8880000, using 4608k, total 16384k
Nov 16 06:48:35 phillip-laptop kernel: [   25.722316] vesafb: mode is 1024x768x24, linelength=3072, pages=6
Nov 16 06:48:35 phillip-laptop kernel: [   25.722321] vesafb: protected mode interface info at c000:516e
Nov 16 06:48:35 phillip-laptop kernel: [   25.722326] vesafb: pmi: set display start = c00c51dc, set palette = c00c5216
Nov 16 06:48:35 phillip-laptop kernel: [   25.722330] vesafb: pmi: ports = 7810 7816 7854 7838 783c 785c 7800 7804 78b0 78b2 78b4 
Nov 16 06:48:35 phillip-laptop kernel: [   25.722342] vesafb: scrolling: redraw
Nov 16 06:48:35 phillip-laptop kernel: [   25.722346] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Nov 16 06:48:35 phillip-laptop kernel: [   25.722484] Console: switching to colour frame buffer device 128x48
Nov 16 06:48:35 phillip-laptop kernel: [   25.728645] fb0: VESA VGA frame buffer device
Nov 16 06:48:35 phillip-laptop kernel: [   26.876411] fuse init (API version 7.9)
Nov 16 06:48:35 phillip-laptop kernel: [   26.895933] ACPI: SSDT 77FBE2A0, 0D1C (r1    AMI   CPU1PM        1 INTL 20051117)
Nov 16 06:48:35 phillip-laptop kernel: [   26.897153] ACPI: CPU0 (power states: C1[C1] C2[C2])
Nov 16 06:48:35 phillip-laptop kernel: [   26.897159] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov 16 06:48:35 phillip-laptop kernel: [   26.897212] ACPI: SSDT 77FBEFC0, 0D1C (r1    AMI   CPU2PM        1 INTL 20051117)
Nov 16 06:48:35 phillip-laptop kernel: [   26.898390] ACPI: CPU1 (power states: C1[C1] C2[C2])
Nov 16 06:48:35 phillip-laptop kernel: [   26.899655] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov 16 06:48:35 phillip-laptop kernel: [   26.901102] ACPI: Thermal Zone [THRM] (54 C)
Nov 16 06:48:35 phillip-laptop kernel: [   27.303258] SCSI subsystem initialized
Nov 16 06:48:35 phillip-laptop kernel: [   27.328268] usbcore: registered new interface driver usbfs
Nov 16 06:48:35 phillip-laptop kernel: [   27.328305] usbcore: registered new interface driver hub
Nov 16 06:48:35 phillip-laptop kernel: [   27.328712] libata version 3.00 loaded.
Nov 16 06:48:35 phillip-laptop kernel: [   27.330915] usbcore: registered new device driver usb
Nov 16 06:48:35 phillip-laptop kernel: [   27.331240] ahci 0000:00:12.0: version 3.0
Nov 16 06:48:35 phillip-laptop kernel: [   27.331288] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
Nov 16 06:48:35 phillip-laptop kernel: [   27.331316] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Nov 16 06:48:35 phillip-laptop kernel: [   27.331319] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Nov 16 06:48:35 phillip-laptop kernel: [   27.342564] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 16 06:48:35 phillip-laptop kernel: [   27.342689] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 16 06:48:35 phillip-laptop kernel: [   27.346497] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 16 06:48:35 phillip-laptop kernel: [   27.396751] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Nov 16 06:48:35 phillip-laptop kernel: [   28.331673] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Nov 16 06:48:35 phillip-laptop kernel: [   28.331682] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pio 
Nov 16 06:48:35 phillip-laptop kernel: [   28.332154] scsi0 : ahci
Nov 16 06:48:35 phillip-laptop kernel: [   28.332488] scsi1 : ahci
Nov 16 06:48:35 phillip-laptop kernel: [   28.332656] scsi2 : ahci
Nov 16 06:48:35 phillip-laptop kernel: [   28.332799] scsi3 : ahci
Nov 16 06:48:35 phillip-laptop kernel: [   28.332890] ata1: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 17
Nov 16 06:48:35 phillip-laptop kernel: [   28.332895] ata2: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 17
Nov 16 06:48:35 phillip-laptop kernel: [   28.332898] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 17
Nov 16 06:48:35 phillip-laptop kernel: [   28.332903] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 17
Nov 16 06:48:35 phillip-laptop kernel: [   28.806852] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 16 06:48:35 phillip-laptop kernel: [   28.807790] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
Nov 16 06:48:35 phillip-laptop kernel: [   28.807794] ata1.00: 234441648 sectors, multi 0: LBA48 NCQ (depth 31/32)
Nov 16 06:48:35 phillip-laptop kernel: [   28.808895] ata1.00: configured for UDMA/100
Nov 16 06:48:35 phillip-laptop kernel: [   29.118337] ata2: SATA link down (SStatus 0 SControl 300)
Nov 16 06:48:35 phillip-laptop kernel: [   29.429822] ata3: SATA link down (SStatus 0 SControl 300)
Nov 16 06:48:35 phillip-laptop kernel: [   29.741310] ata4: SATA link down (SStatus 0 SControl 300)
Nov 16 06:48:35 phillip-laptop kernel: [   29.741508] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
Nov 16 06:48:35 phillip-laptop kernel: [   29.742038] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 18
Nov 16 06:48:35 phillip-laptop kernel: [   29.742057] ehci_hcd 0000:00:13.5: EHCI Host Controller
Nov 16 06:48:35 phillip-laptop kernel: [   29.742421] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
Nov 16 06:48:35 phillip-laptop kernel: [   29.742473] ehci_hcd 0000:00:13.5: debug port 1
Nov 16 06:48:35 phillip-laptop kernel: [   29.742488] ehci_hcd 0000:00:13.5: irq 18, io mem 0xfebff800
Nov 16 06:48:35 phillip-laptop kernel: [   29.751056] Driver 'sd' needs updating - please use bus_type methods
Nov 16 06:48:35 phillip-laptop kernel: [   29.751154] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov 16 06:48:35 phillip-laptop kernel: [   29.751168] sd 0:0:0:0: [sda] Write Protect is off
Nov 16 06:48:35 phillip-laptop kernel: [   29.751171] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 16 06:48:35 phillip-laptop kernel: [   29.751188] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 16 06:48:35 phillip-laptop kernel: [   29.751237] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov 16 06:48:35 phillip-laptop kernel: [   29.751247] sd 0:0:0:0: [sda] Write Protect is off
Nov 16 06:48:35 phillip-laptop kernel: [   29.751250] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 16 06:48:35 phillip-laptop kernel: [   29.751266] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 16 06:48:35 phillip-laptop kernel: [   29.751269]  sda:<6>ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 16 06:48:35 phillip-laptop kernel: [   29.754436] usb usb1: configuration #1 chosen from 1 choice
Nov 16 06:48:35 phillip-laptop kernel: [   29.754462] hub 1-0:1.0: USB hub found
Nov 16 06:48:35 phillip-laptop kernel: [   29.754469] hub 1-0:1.0: 10 ports detected
Nov 16 06:48:35 phillip-laptop kernel: [   29.858374] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 19
Nov 16 06:48:35 phillip-laptop kernel: [   29.858398] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 16 06:48:35 phillip-laptop kernel: [   29.858440] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
Nov 16 06:48:35 phillip-laptop kernel: [   29.858463] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfebfe000
Nov 16 06:48:35 phillip-laptop kernel: [   29.917129] usb usb2: configuration #1 chosen from 1 choice
Nov 16 06:48:35 phillip-laptop kernel: [   29.917158] hub 2-0:1.0: USB hub found
Nov 16 06:48:35 phillip-laptop kernel: [   29.917168] hub 2-0:1.0: 2 ports detected
Nov 16 06:48:35 phillip-laptop kernel: [   30.016968] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 20
Nov 16 06:48:35 phillip-laptop kernel: [   30.016998] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 16 06:48:35 phillip-laptop kernel: [   30.017026] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
Nov 16 06:48:35 phillip-laptop kernel: [   30.017046] ohci_hcd 0000:00:13.1: irq 20, io mem 0xfebfd000
Nov 16 06:48:35 phillip-laptop kernel: [   30.077840] usb usb3: configuration #1 chosen from 1 choice
Nov 16 06:48:35 phillip-laptop kernel: [   30.077867] hub 3-0:1.0: USB hub found
Nov 16 06:48:35 phillip-laptop kernel: [   30.077878] hub 3-0:1.0: 2 ports detected
Nov 16 06:48:35 phillip-laptop kernel: [   30.165592]  sda1 sda2 sda3 <<6>ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 21
Nov 16 06:48:35 phillip-laptop kernel: [   30.181748] ohci_hcd 0000:00:13.2: OHCI Host Controller
Nov 16 06:48:35 phillip-laptop kernel: [   30.181774] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
Nov 16 06:48:35 phillip-laptop kernel: [   30.181795] ohci_hcd 0000:00:13.2: irq 21, io mem 0xfebfc000
Nov 16 06:48:35 phillip-laptop kernel: [   30.188681]  sda5 sda6 > sda4
Nov 16 06:48:35 phillip-laptop kernel: [   30.210574] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 16 06:48:35 phillip-laptop kernel: [   30.215555] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 16 06:48:35 phillip-laptop kernel: [   30.241609] usb usb4: configuration #1 chosen from 1 choice
Nov 16 06:48:35 phillip-laptop kernel: [   30.241650] hub 4-0:1.0: USB hub found
Nov 16 06:48:35 phillip-laptop kernel: [   30.241661] hub 4-0:1.0: 2 ports detected
Nov 16 06:48:35 phillip-laptop kernel: [   30.345481] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 20
Nov 16 06:48:35 phillip-laptop kernel: [   30.345518] ohci_hcd 0000:00:13.3: OHCI Host Controller
Nov 16 06:48:35 phillip-laptop kernel: [   30.345549] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
Nov 16 06:48:35 phillip-laptop kernel: [   30.345577] ohci_hcd 0000:00:13.3: irq 20, io mem 0xfebfb000
Nov 16 06:48:35 phillip-laptop kernel: [   30.404358] usb usb5: configuration #1 chosen from 1 choice
Nov 16 06:48:35 phillip-laptop kernel: [   30.404391] hub 5-0:1.0: USB hub found
Nov 16 06:48:35 phillip-laptop kernel: [   30.404402] hub 5-0:1.0: 2 ports detected
Nov 16 06:48:35 phillip-laptop kernel: [   30.504213] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 21
Nov 16 06:48:35 phillip-laptop kernel: [   30.504243] ohci_hcd 0000:00:13.4: OHCI Host Controller
Nov 16 06:48:35 phillip-laptop kernel: [   30.504280] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
Nov 16 06:48:35 phillip-laptop kernel: [   30.504299] ohci_hcd 0000:00:13.4: irq 21, io mem 0xfebfa000
Nov 16 06:48:35 phillip-laptop kernel: [   30.564069] usb usb6: configuration #1 chosen from 1 choice
Nov 16 06:48:35 phillip-laptop kernel: [   30.564109] hub 6-0:1.0: USB hub found
Nov 16 06:48:35 phillip-laptop kernel: [   30.564122] hub 6-0:1.0: 2 ports detected
Nov 16 06:48:35 phillip-laptop kernel: [   30.669044] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Nov 16 06:48:35 phillip-laptop kernel: [   30.669064] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
Nov 16 06:48:35 phillip-laptop kernel: [   30.669078] SB600_PATA: not 100% native mode: will probe irqs later
Nov 16 06:48:35 phillip-laptop kernel: [   30.669091]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:DMA
Nov 16 06:48:35 phillip-laptop kernel: [   30.669106] Probing IDE interface ide0...
Nov 16 06:48:35 phillip-laptop kernel: [   31.454884] hdb: HL-DT-ST DVDRAM GSA-T20N, ATAPI CD/DVD-ROM drive
Nov 16 06:48:35 phillip-laptop kernel: [   31.734025] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Nov 16 06:48:35 phillip-laptop kernel: [   31.734837] hdb: UDMA/33 mode selected
Nov 16 06:48:35 phillip-laptop kernel: [   31.735292] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov 16 06:48:35 phillip-laptop kernel: [   31.738530] 8139cp 0000:08:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Nov 16 06:48:35 phillip-laptop kernel: [   31.738534] 8139cp 0000:08:07.0: Try the "8139too" driver instead.
Nov 16 06:48:35 phillip-laptop kernel: [   31.740456] 8139too Fast Ethernet driver 0.9.28
Nov 16 06:48:35 phillip-laptop kernel: [   31.740533] ACPI: PCI Interrupt 0000:08:07.0[A] -> GSI 20 (level, low) -> IRQ 22
Nov 16 06:48:35 phillip-laptop kernel: [   31.741681] eth0: RealTek RTL8139 at 0xb800, 00:1d:60:49:6c:65, IRQ 22
Nov 16 06:48:35 phillip-laptop kernel: [   31.741684] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Nov 16 06:48:35 phillip-laptop kernel: [   31.759889] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Nov 16 06:48:35 phillip-laptop kernel: [   31.759899] Uniform CD-ROM driver Revision: 3.20
Nov 16 06:48:35 phillip-laptop kernel: [   31.896031] Attempting manual resume
Nov 16 06:48:35 phillip-laptop kernel: [   31.896036] swsusp: Resume From Partition 8:6
Nov 16 06:48:35 phillip-laptop kernel: [   31.896038] PM: Checking swsusp image.
Nov 16 06:48:35 phillip-laptop kernel: [   31.896189] PM: Resume from disk failed.
Nov 16 06:48:35 phillip-laptop kernel: [   31.911428] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov 16 06:48:35 phillip-laptop kernel: [   31.911435] EXT3-fs: write access will be enabled during recovery.
Nov 16 06:48:35 phillip-laptop kernel: [   31.967711] kjournald starting.  Commit interval 5 seconds
Nov 16 06:48:35 phillip-laptop kernel: [   31.967730] EXT3-fs: recovery complete.
Nov 16 06:48:35 phillip-laptop kernel: [   31.968323] EXT3-fs: mounted filesystem with ordered data mode.
Nov 16 06:48:35 phillip-laptop kernel: [   41.869913] input: PC Speaker as /devices/platform/pcspkr/input/input2
Nov 16 06:48:35 phillip-laptop kernel: [   42.033066] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 16 06:48:35 phillip-laptop kernel: [   42.098132] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 16 06:48:35 phillip-laptop kernel: [   42.141945] Linux agpgart interface v0.102
Nov 16 06:48:35 phillip-laptop kernel: [   42.307173] input: Power Button (FF) as /devices/virtual/input/input3
Nov 16 06:48:35 phillip-laptop kernel: [   42.345578] ACPI: Power Button (FF) [PWRF]
Nov 16 06:48:35 phillip-laptop kernel: [   42.345716] input: Lid Switch as /devices/virtual/input/input4
Nov 16 06:48:35 phillip-laptop kernel: [   42.357623] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Nov 16 06:48:35 phillip-laptop kernel: [   42.363879] ACPI: Lid Switch [LID]
Nov 16 06:48:35 phillip-laptop kernel: [   42.363950] input: Power Button (CM) as /devices/virtual/input/input5
Nov 16 06:48:35 phillip-laptop kernel: [   42.425444] ACPI: Power Button (CM) [PWRB]
Nov 16 06:48:35 phillip-laptop kernel: [   42.425512] input: Sleep Button (CM) as /devices/virtual/input/input6
Nov 16 06:48:35 phillip-laptop kernel: [   42.477431] ACPI: Sleep Button (CM) [SLPB]
Nov 16 06:48:35 phillip-laptop kernel: [   42.744899] asus-laptop: Asus Laptop Support version 0.42
Nov 16 06:48:35 phillip-laptop kernel: [   42.745118] asus-laptop: BSTS called, 0x22 returned
Nov 16 06:48:35 phillip-laptop kernel: [   42.745165] asus-laptop:   X51R model detected
Nov 16 06:48:35 phillip-laptop kernel: [   43.139049] ACPI: AC Adapter [AC0] (on-line)
Nov 16 06:48:35 phillip-laptop kernel: [   43.329728] ACPI: Battery Slot [BAT0] (battery present)
Nov 16 06:48:35 phillip-laptop kernel: [   43.391630] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input7
Nov 16 06:48:35 phillip-laptop kernel: [   43.418599] Yenta: CardBus bridge found at 0000:08:01.0 [1043:1627]
Nov 16 06:48:35 phillip-laptop kernel: [   43.446818] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov 16 06:48:35 phillip-laptop kernel: [   43.562251] sdhci: Secure Digital Host Controller Interface driver
Nov 16 06:48:35 phillip-laptop kernel: [   43.562257] sdhci: Copyright(c) Pierre Ossman
Nov 16 06:48:35 phillip-laptop kernel: [   43.564385] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
Nov 16 06:48:35 phillip-laptop kernel: [   43.564391] Socket status: 30000006
Nov 16 06:48:35 phillip-laptop kernel: [   43.564394] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
Nov 16 06:48:35 phillip-laptop kernel: [   43.564400] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
Nov 16 06:48:35 phillip-laptop kernel: [   43.564403] cs: IO port probe 0xa000-0xbfff: clean.
Nov 16 06:48:35 phillip-laptop kernel: [   43.564958] pcmcia: parent PCI bridge Memory window: 0xfca00000 - 0xfeafffff
Nov 16 06:48:35 phillip-laptop kernel: [   43.564960] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xdfefffff
Nov 16 06:48:35 phillip-laptop kernel: [   43.566808] sdhci: SDHCI controller found at 0000:08:01.1 [1180:0822] (rev 17)
Nov 16 06:48:35 phillip-laptop kernel: [   43.566850] ACPI: PCI Interrupt 0000:08:01.1[C] -> GSI 23 (level, low) -> IRQ 23
Nov 16 06:48:35 phillip-laptop kernel: [   43.566881] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Nov 16 06:48:35 phillip-laptop kernel: [   43.566938] mmc0: SDHCI at 0xfeaffc00 irq 23 DMA
Nov 16 06:48:35 phillip-laptop kernel: [   43.670068] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 16 06:48:35 phillip-laptop kernel: [   43.704830] [fglrx]   vendor: 1002 device: 5a62 count: 1
Nov 16 06:48:35 phillip-laptop kernel: [   43.704927] [fglrx] Maximum main memory to use for locked dma buffers: 1777 MBytes.
Nov 16 06:48:35 phillip-laptop kernel: [   43.705560] [fglrx] PAT is enabled successfully!
Nov 16 06:48:35 phillip-laptop kernel: [   43.705592] [fglrx] module loaded - fglrx 8.50.3 [Jun  2 2008] with 1 minors
Nov 16 06:48:35 phillip-laptop kernel: [   43.715276] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
Nov 16 06:48:35 phillip-laptop kernel: [   43.765270] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Nov 16 06:48:35 phillip-laptop kernel: [   44.101808] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
Nov 16 06:48:35 phillip-laptop kernel: [   44.587170] cs: IO port probe 0x100-0x3af: clean.
Nov 16 06:48:35 phillip-laptop kernel: [   44.589447] cs: IO port probe 0x3e0-0x4ff: clean.
Nov 16 06:48:35 phillip-laptop kernel: [   44.590412] cs: IO port probe 0x820-0x8ff: clean.
Nov 16 06:48:35 phillip-laptop kernel: [   44.590779] cs: IO port probe 0xc00-0xcf7: clean.
Nov 16 06:48:35 phillip-laptop kernel: [   44.591593] cs: IO port probe 0xa00-0xaff: clean.
Nov 16 06:48:35 phillip-laptop kernel: [   45.635279] lp: driver loaded but no devices found
Nov 16 06:48:35 phillip-laptop kernel: [   45.725725] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
Nov 16 06:48:35 phillip-laptop kernel: [   45.989022] wlan: trunk
Nov 16 06:48:35 phillip-laptop kernel: [   46.148956] ath_pci: trunk
Nov 16 06:48:35 phillip-laptop kernel: [   46.149071] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 19
Nov 16 06:48:35 phillip-laptop kernel: [   46.149087] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov 16 06:48:35 phillip-laptop kernel: [   46.641258] MadWifi: ath_attach: Switching rfkill capability off
Nov 16 06:48:35 phillip-laptop kernel: [   46.709132] ath_rate_sample: 1.2 (trunk)
Nov 16 06:48:35 phillip-laptop kernel: [   46.709332] MadWifi: ath_attach: Switching per-packet transmit power control off
Nov 16 06:48:35 phillip-laptop kernel: [   46.709742] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Nov 16 06:48:35 phillip-laptop kernel: [   46.709749] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov 16 06:48:35 phillip-laptop kernel: [   46.709759] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Nov 16 06:48:35 phillip-laptop kernel: [   46.709771] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
Nov 16 06:48:35 phillip-laptop kernel: [   46.709774] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
Nov 16 06:48:35 phillip-laptop kernel: [   46.709776] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
Nov 16 06:48:35 phillip-laptop kernel: [   46.709779] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
Nov 16 06:48:35 phillip-laptop kernel: [   46.709781] wifi0: ath_announce: Use hw queue 8 for CAB traffic
Nov 16 06:48:35 phillip-laptop kernel: [   46.709783] wifi0: ath_announce: Use hw queue 9 for beacons
Nov 16 06:48:35 phillip-laptop kernel: [   46.742409] ath_pci: wifi0: Atheros 5424/2424: mem=0xf89f0000, irq=19
Nov 16 06:48:35 phillip-laptop kernel: [   46.819690] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFB) is beyond end of object [20070126]
Nov 16 06:48:35 phillip-laptop kernel: [   46.819713] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PSS] (Node f7c49b88), AE_AML_PACKAGE_LIMIT
Nov 16 06:48:35 phillip-laptop kernel: [   46.819761] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Nov 16 06:48:35 phillip-laptop kernel: [   46.819965] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFB) is beyond end of object [20070126]
Nov 16 06:48:35 phillip-laptop kernel: [   46.819984] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PSS] (Node f7c49d98), AE_AML_PACKAGE_LIMIT
Nov 16 06:48:35 phillip-laptop kernel: [   46.820033] ACPI Exception (processor_perflib-0234): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20070126]
Nov 16 06:48:35 phillip-laptop kernel: [   47.002554] Adding 872480k swap on /dev/sda6.  Priority:-1 extents:1 across:872480k
Nov 16 06:48:35 phillip-laptop kernel: [   47.566200] EXT3 FS on sda4, internal journal
Nov 16 06:48:35 phillip-laptop kernel: [   48.869365] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 16 06:48:35 phillip-laptop kernel: [   48.953167] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Nov 16 06:48:35 phillip-laptop kernel: [   49.093094] NET: Registered protocol family 10
Nov 16 06:48:35 phillip-laptop kernel: [   49.093476] lo: Disabled Privacy Extensions
Nov 16 06:48:35 phillip-laptop kernel: [   49.159587] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 16 06:48:35 phillip-laptop kernel: [   50.158825] No dock devices found.
Nov 16 06:48:35 phillip-laptop NetworkManager: <info>  starting... 
Nov 16 06:48:36 phillip-laptop avahi-daemon[5257]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov 16 06:48:36 phillip-laptop avahi-daemon[5257]: Successfully dropped root privileges.
Nov 16 06:48:36 phillip-laptop avahi-daemon[5257]: avahi-daemon 0.6.22 starting up.
Nov 16 06:48:36 phillip-laptop avahi-daemon[5257]: Successfully called chroot().
Nov 16 06:48:36 phillip-laptop avahi-daemon[5257]: Successfully dropped remaining capabilities.
Nov 16 06:48:36 phillip-laptop avahi-daemon[5257]: No service file found in /etc/avahi/services.
Nov 16 06:48:36 phillip-laptop avahi-daemon[5257]: Network interface enumeration completed.
Nov 16 06:48:36 phillip-laptop avahi-daemon[5257]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 16 06:48:36 phillip-laptop avahi-daemon[5257]: Server startup complete. Host name is phillip-laptop.local. Local service cookie is 3847901260.
Nov 16 06:48:36 phillip-laptop kernel: [   51.684244] ppdev: user-space parallel port driver
Nov 16 06:48:36 phillip-laptop kernel: [   51.874766] audit(1226818116.484:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5290 profile="/usr/sbin/cupsd" namespace="default"
Nov 16 06:48:36 phillip-laptop kernel: [   52.165984] apm: BIOS not found.
Nov 16 06:48:36 phillip-laptop atieventsd[5327]: ATI External Events Daemon started... 
Nov 16 06:48:36 phillip-laptop atieventsd[5327]: Event daemon control socket created 
Nov 16 06:48:36 phillip-laptop atieventsd[5327]: acpid connection established 
Nov 16 06:48:40 phillip-laptop avgscan[5344]: Starting AVG Anti-Virus in daemon mode. 
Nov 16 06:48:40 phillip-laptop avgscan[5344]: AVG Anti-Virus Daemon started.
Nov 16 06:48:40 phillip-laptop avgscan[5344]: Starting AVG Anti-Virus on-access scanner. 
Nov 16 06:48:40 phillip-laptop avgscan[5344]: AVG Anti-Virus on-access scanner started
Nov 16 06:48:40 phillip-laptop avgscan[5346]: ERROR: registration to Dazuko failed
Nov 16 06:48:40 phillip-laptop avgscan[5346]: AVG Anti-Virus on-access failed to start.
Nov 16 06:48:44 phillip-laptop dhcdbd: Started up.
Nov 16 06:48:46 phillip-laptop kernel: [   61.538207] eth0: link down
Nov 16 06:48:46 phillip-laptop kernel: [   61.542406] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  Deactivating device eth0. 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  ath0: Device is fully-supported using driver 'ath_pci'. 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  ath0: driver does not support SSID scans (scan_capa 0x00). 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'ath0'. 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  Deactivating device ath0. 
Nov 16 06:48:46 phillip-laptop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Nov 16 06:48:47 phillip-laptop gdm[5976]: WARNING: Didn't understand `' (expected true or false) 
Nov 16 06:48:48 phillip-laptop kernel: [   63.733281] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 20
Nov 16 06:48:48 phillip-laptop anacron[6025]: Anacron 2.3 started on 2008-11-16
Nov 16 06:48:48 phillip-laptop anacron[6025]: Normal exit (0 jobs run)
Nov 16 06:48:48 phillip-laptop /usr/sbin/cron[6056]: (CRON) INFO (pidfile fd = 3)
Nov 16 06:48:48 phillip-laptop /usr/sbin/cron[6057]: (CRON) STARTUP (fork ok)
Nov 16 06:48:48 phillip-laptop /usr/sbin/cron[6057]: (CRON) INFO (Running @reboot jobs)
Nov 16 06:48:50 phillip-laptop kernel: [   65.525121] [fglrx] GART Table is not in FRAME_BUFFER range 
Nov 16 06:48:50 phillip-laptop kernel: [   65.528323] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Nov 16 06:48:50 phillip-laptop kernel: [   65.528333] [fglrx] Reserved FB block: Unshared offset:7ff5000, size:b000 
Nov 16 06:48:57 phillip-laptop kernel: [   73.050710] hda-intel: Invalid position buffer, using LPIB read method instead.
Nov 16 06:49:16 phillip-laptop kernel: [   91.921089] glxinfo[6311]: segfault at b7f20000 eip b793de28 esp bfcb5b30 error 6
Nov 16 06:49:21 phillip-laptop anacron[6427]: Anacron 2.3 started on 2008-11-16
Nov 16 06:49:21 phillip-laptop anacron[6427]: Normal exit (0 jobs run)
Nov 16 06:49:21 phillip-laptop kernel: [   96.632530] CPU0 attaching NULL sched-domain.
Nov 16 06:49:21 phillip-laptop kernel: [   96.632545] CPU1 attaching NULL sched-domain.
Nov 16 06:49:21 phillip-laptop kernel: [   96.648284] CPU0 attaching sched-domain:
Nov 16 06:49:21 phillip-laptop kernel: [   96.648296]  domain 0: span 03
Nov 16 06:49:21 phillip-laptop kernel: [   96.648301]   groups: 01 02
Nov 16 06:49:21 phillip-laptop kernel: [   96.648312] CPU1 attaching sched-domain:
Nov 16 06:49:21 phillip-laptop kernel: [   96.648316]  domain 0: span 03
Nov 16 06:49:21 phillip-laptop kernel: [   96.648319]   groups: 02 01
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'ath0'. 
Nov 16 06:49:31 phillip-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Will activate connection 'ath0/Tortilla de Patatas'. 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Device ath0 activation scheduled... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) started... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0/wireless): access point 'Tortilla de Patatas' is encrypted, but NO valid key exists.  New key needed. 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'Tortilla de Patatas'. 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) New wireless user key for network 'Tortilla de Patatas' received. 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Nov 16 06:49:31 phillip-laptop NetworkManager: <info>  Activation (ath0/wireless): access point 'Tortilla de Patatas' is encrypted, and a key exists.  No new key needed. 
Nov 16 06:49:32 phillip-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Nov 16 06:49:32 phillip-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=2) 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
Nov 16 06:49:33 phillip-laptop kernel: [  108.418341] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Nov 16 06:49:33 phillip-laptop kernel: [  108.566030] NET: Registered protocol family 17
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: response was '0' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 546f7274696c6c612064652050617461746173' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 16 06:49:33 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Nov 16 06:49:34 phillip-laptop avahi-daemon[5257]: Registering new address record for fe80::215:afff:fe3d:3adb on ath0.*.
Nov 16 06:49:36 phillip-laptop NetworkManager: <info>  Supplicant state changed: 1 
Nov 16 06:49:36 phillip-laptop NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Tortilla de Patatas'. 
Nov 16 06:49:36 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 16 06:49:36 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Nov 16 06:49:37 phillip-laptop NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
Nov 16 06:49:37 phillip-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 16 06:49:37 phillip-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath0 
Nov 16 06:49:37 phillip-laptop dhclient: wifi0: unknown hardware address type 801

```

---

