---
title: "Cannot allocate resource region --- if bridge 0000:00:1c.0"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by kentl on 2007-11-03
I've installed a command-line Gutsy using the alternate desktop download on a Acer Aspire 1640Z laptop. During boot I get errors which I hope someone can help me with.

This is the output of logfile.txt created using **dmesg** | cat >logfile.txt. It contains the messages during boot which report errors. (found approximately 4 screen scrolls down)
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000e4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe80000 (usable)
[    0.000000]  BIOS-e820: 000000003fe80000 - 000000003fe8b000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fe8b000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 261760) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261760
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261760
[    0.000000] On node 0 totalpages: 261760
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32131 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6BD0 checksum 0
[    0.000000] ACPI: RSDP 000F6BD0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3FE84FA4, 0044 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3FE8AE88, 0074 (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: DSDT 3FE8581E, 566A (r1 INTEL  ALVISO    6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FE9BFC0, 0040
[    0.000000] ACPI: APIC 3FE8AEFC, 0068 (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: HPET 3FE8AF64, 0038 (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: MCFG 3FE8AF9C, 003C (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: BOOT 3FE8AFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3FE853D9, 0235 (r1  PmRef  Cpu0Ist     3000 INTL 20030224)
[    0.000000] ACPI: SSDT 3FE85201, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030224)
[    0.000000] ACPI: SSDT 3FE84FE8, 0219 (r1  PmRef    CpuPm     3000 INTL 20030224)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 259715
[    0.000000] Kernel command line: root=UUID=dbeac422-d68e-46db-96fb-74de42f5227a ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1733.473 MHz processor.
[   19.871002] Console: colour VGA+ 80x25
[   19.871309] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   19.871719] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.906888] Memory: 1026552k/1047040k available (2015k kernel code, 19768k reserved, 916k data, 364k init, 129536k highmem)
[   19.906898] virtual kernel memory layout:
[   19.906899]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   19.906900]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.906901]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   19.906903]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   19.906904]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   19.906905]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   19.906906]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   19.906910] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.906945] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.907087] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   19.907092] hpet0: 3 64-bit timers, 14318180 Hz
[   19.988003] Calibrating delay using timer specific routine.. 3470.20 BogoMIPS (lpj=6940400)
[   19.988024] Security Framework v1.0.0 initialized
[   19.988031] SELinux:  Disabled at boot.
[   19.988044] Mount-cache hash table entries: 512
[   19.988162] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[   19.988173] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.988176] CPU: L2 cache: 2048K
[   19.988178] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[   19.988187] Compat vDSO mapped to ffffe000.
[   19.988197] Checking 'hlt' instruction... OK.
[   20.004073] SMP alternatives: switching to UP code
[   20.004236] Freeing SMP alternatives: 11k freed
[   20.004482] Early unpacking initramfs... done
[   20.310877] ACPI: Core revision 20070126
[   20.310942] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.341180] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[   20.341203] Total of 1 processors activated (3470.20 BogoMIPS).
[   20.341391] ENABLING IO-APIC IRQs
[   20.341583] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.487376] Brought up 1 CPUs
[   20.487478] Booting paravirtualized kernel on bare hardware
[   20.487544] Time: 20:35:16  Date: 10/03/107
[   20.487564] NET: Registered protocol family 16
[   20.487635] EISA bus registered
[   20.487640] ACPI: bus type pci registered
[   20.488152] PCI: PCI BIOS revision 2.10 entry at 0xfd7ce, last bus=7
[   20.488154] PCI: Using configuration type 1
[   20.488156] Setting up standard PCI resources
[   20.493000] ACPI: EC: Look up EC in DSDT
[   20.493526] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   20.577871] ACPI: Interpreter enabled
[   20.577874] ACPI: (supports S0 S3 S4 S5)
[   20.577889] ACPI: Using IOAPIC for interrupt routing
[   20.581414] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   20.581460] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.581469] PCI: Probing PCI hardware (bus 00)
[   20.582082] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   20.582086] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   20.582819] PCI: Transparent bridge - 0000:00:1e.0
[   20.582948] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.583256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   20.583381] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   20.583499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   20.583617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   20.583824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   20.589826] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   20.589915] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   20.590001] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   20.590086] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   20.590171] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   20.590256] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   20.590342] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   20.590427] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   20.590515] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.590524] pnp: PnP ACPI init
[   20.590532] ACPI: bus type pnp registered
[   20.591830] pnp: PnP ACPI: found 9 devices
[   20.591832] ACPI: ACPI bus type pnp unregistered
[   20.591836] PnPBIOS: Disabled by ACPI PNP
[   20.591870] PCI: Using ACPI for IRQ routing
[   20.591873] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.591877] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   20.591921] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   20.591962] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   20.592002] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   20.592043] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   20.592083] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   20.592124] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   20.592164] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   20.592205] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   20.608998] NET: Registered protocol family 8
[   20.609000] NET: Registered protocol family 20
[   20.609044] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   20.609047] pnp: 00:01: iomem range 0xf0000000-0xf0003fff could not be reserved
[   20.609050] pnp: 00:01: iomem range 0xf0004000-0xf0004fff could not be reserved
[   20.609054] pnp: 00:01: iomem range 0xf0005000-0xf0005fff could not be reserved
[   20.611180] Time: tsc clocksource has been installed.
[   20.611192] Switched to high resolution mode on CPU 0
[   20.639287] PCI: Bridge: 0000:00:01.0
[   20.639289]   IO window: 2000-2fff
[   20.639293]   MEM window: d4100000-d41fffff
[   20.639296]   PREFETCH window: d8000000-dbffffff
[   20.639300] PCI: Bridge: 0000:00:1c.0
[   20.639301]   IO window: disabled.
[   20.639306]   MEM window: disabled.
[   20.639310]   PREFETCH window: disabled.
[   20.639316] PCI: Bridge: 0000:00:1c.1
[   20.639317]   IO window: disabled.
[   20.639322]   MEM window: disabled.
[   20.639327]   PREFETCH window: disabled.
[   20.639332] PCI: Bridge: 0000:00:1c.2
[   20.639333]   IO window: disabled.
[   20.639339]   MEM window: disabled.
[   20.639343]   PREFETCH window: disabled.
[   20.639350] PCI: Bus 7, cardbus bridge: 0000:06:01.0
[   20.639352]   IO window: 00003400-000034ff
[   20.639358]   IO window: 00003800-000038ff
[   20.639363]   PREFETCH window: 50000000-53ffffff
[   20.639368]   MEM window: 54000000-57ffffff
[   20.639373] PCI: Bridge: 0000:00:1e.0
[   20.639376]   IO window: 3000-3fff
[   20.639382]   MEM window: d4200000-d42fffff
[   20.639387]   PREFETCH window: 50000000-53ffffff
[   20.639402] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.639407] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.639427] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.639434] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.639454] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   20.639461] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.639483] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.639490] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.639503] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.639519] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 18 (level, low) -> IRQ 18
[   20.639532] NET: Registered protocol family 2
[   20.679094] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.679154] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   20.680385] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   20.680949] TCP: Hash tables configured (established 131072 bind 65536)
[   20.680953] TCP reno registered
[   20.691211] checking if image is initramfs... it is
[   21.294248] Freeing initrd memory: 6902k freed
[   21.294408] Simple Boot Flag at 0x36 set to 0x1
[   21.294667] audit: initializing netlink socket (disabled)
[   21.294681] audit(1194122116.008:1): initialized
[   21.294752] highmem bounce pool size: 64 pages
[   21.296457] VFS: Disk quotas dquot_6.5.1
[   21.296503] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.296595] io scheduler noop registered
[   21.296598] io scheduler anticipatory registered
[   21.296600] io scheduler deadline registered
[   21.296614] io scheduler cfq registered (default)
[   21.296708] Boot video device is 0000:01:00.0
[   21.296784] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.296813] assign_interrupt_mode Found MSI capability
[   21.296816] Allocate Port Service[0000:00:01.0:pcie00]
[   21.296881] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.296932] assign_interrupt_mode Found MSI capability
[   21.296935] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.296965] Allocate Port Service[0000:00:1c.0:pcie02]
[   21.297052] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.297103] assign_interrupt_mode Found MSI capability
[   21.297105] Allocate Port Service[0000:00:1c.1:pcie00]
[   21.297131] Allocate Port Service[0000:00:1c.1:pcie02]
[   21.297221] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.297272] assign_interrupt_mode Found MSI capability
[   21.297274] Allocate Port Service[0000:00:1c.2:pcie00]
[   21.297301] Allocate Port Service[0000:00:1c.2:pcie02]
[   21.297444] isapnp: Scanning for PnP cards...
[   21.651020] isapnp: No Plug & Play device found
[   21.673670] Real Time Clock Driver v1.12ac
[   21.673915] hpet_resources: 0xfed00000 is busy
[   21.673945] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.675040] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.675219] input: Macintosh mouse button emulation as /class/input/input0
[   21.675289] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   21.679036] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.679041] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.679184] mice: PS/2 mouse device common for all mice
[   21.679272] EISA: Probing bus 0 at eisa.0
[   21.679279] Cannot allocate resource for EISA slot 1
[   21.679281] Cannot allocate resource for EISA slot 2
[   21.679283] Cannot allocate resource for EISA slot 3
[   21.679303] EISA: Detected 0 cards.
[   21.679395] TCP cubic registered
[   21.679408] NET: Registered protocol family 1
[   21.679430] Using IPI No-Shortcut mode
[   21.679581]   Magic number: 15:406:598
[   21.679629]   hash matches device ptyd2
[   21.679880] Freeing unused kernel memory: 364k freed
[   21.738213] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.817530] AppArmor: AppArmor initialized<5>audit(1194122116.508:2):  type=1505 info="AppArmor initialized" pid=1083
[   21.822421] fuse init (API version 7.8)
[   21.825983] Failure registering capabilities with primary security module.
[   21.836164] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   21.836169] ACPI: Processor [CPU0] (supports 8 throttling states)
[   21.836180] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.840106] ACPI: Thermal Zone [THRM] (46 C)
[   22.253891] usbcore: registered new interface driver usbfs
[   22.253913] usbcore: registered new interface driver hub
[   22.253931] usbcore: registered new device driver usb
[   22.254643] USB Universal Host Controller Interface driver v3.0
[   22.254706] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   22.254717] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.254721] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.254889] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.254919] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001800
[   22.255024] usb usb1: configuration #1 chosen from 1 choice
[   22.255048] hub 1-0:1.0: USB hub found
[   22.255053] hub 1-0:1.0: 2 ports detected
[   22.316493] SCSI subsystem initialized
[   22.321420] libata version 2.21 loaded.
[   22.357102] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   22.357116] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.357120] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.357141] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.357173] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[   22.357267] usb usb2: configuration #1 chosen from 1 choice
[   22.357290] hub 2-0:1.0: USB hub found
[   22.357296] hub 2-0:1.0: 2 ports detected
[   22.376180] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   22.460953] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   22.460965] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.460970] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.460995] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.461029] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   22.461120] usb usb3: configuration #1 chosen from 1 choice
[   22.461145] hub 3-0:1.0: USB hub found
[   22.461151] hub 3-0:1.0: 2 ports detected
[    2.460000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.464000] Time: hpet clocksource has been installed.
[    2.464000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    2.464000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    2.464000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.464000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.464000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    2.464000] usb usb4: configuration #1 chosen from 1 choice
[    2.464000] hub 4-0:1.0: USB hub found
[    2.464000] hub 4-0:1.0: 2 ports detected
[    2.500000] Clocksource tsc unstable (delta = -116476003 ns)
[    2.568000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    2.568000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    2.568000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.568000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.568000] ehci_hcd 0000:00:1d.7: debug port 1
[    2.568000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    2.568000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd4000000
[    2.572000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.572000] usb usb5: configuration #1 chosen from 1 choice
[    2.572000] hub 5-0:1.0: USB hub found
[    2.572000] hub 5-0:1.0: 8 ports detected
[    2.676000] ata_piix 0000:00:1f.1: version 2.11
[    2.676000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    2.676000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    2.676000] scsi0 : ata_piix
[    2.676000] scsi1 : ata_piix
[    2.676000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011880 irq 14
[    2.676000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011888 irq 15
[    3.508000] ata1.00: ATA-6: TOSHIBA MK8032GAX, AD001A, max UDMA/100
[    3.508000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    3.508000] ata1.01: ATAPI: Slimtype DVDRW SSW-8015S, HRS2, max UDMA/66
[    3.516000] ata1.00: configured for UDMA/100
[    3.688000] ata1.01: configured for UDMA/66
[    3.688000] ata2: port disabled. ignoring.
[    3.688000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8032GA AD00 PQ: 0 ANSI: 5
[    3.688000] scsi 0:0:1:0: CD-ROM            Slimtype DVDRW SSW-8015S  HRS2 PQ: 0 ANSI: 5
[    3.692000] 8139cp 0000:06:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.692000] 8139cp 0000:06:08.0: Try the "8139too" driver instead.
[    3.692000] 8139too Fast Ethernet driver 0.9.28
[    3.692000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.692000] eth0: RealTek RTL8139 at 0xf884c000, 00:16:36:2f:bf:a0, IRQ 16
[    3.692000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.708000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.708000] sd 0:0:0:0: [sda] Write Protect is off
[    3.708000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.708000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.708000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.708000] sd 0:0:0:0: [sda] Write Protect is off
[    3.708000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.708000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.708000]  sda: sda1 sda2 < sda5 >
[    3.768000] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.772000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.772000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    3.784000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.784000] Uniform CD-ROM driver Revision: 3.20
[    3.784000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    3.984000] Attempting manual resume
[    3.984000] swsusp: Resume From Partition 8:5
[    3.984000] PM: Checking swsusp image.
[    3.984000] PM: Resume from disk failed.
[    4.032000] kjournald starting.  Commit interval 5 seconds
[    4.032000] EXT3-fs: mounted filesystem with ordered data mode.
[    9.416000] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   10.236000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.264000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.280000] Linux agpgart interface v0.102 (c) Dave Jones
[   10.900000] intel_rng: FWH not detected
[   10.952000] Yenta: CardBus bridge found at 0000:06:01.0 [1025:009e]
[   10.952000] Yenta: Enabling burst memory read transactions
[   10.952000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   10.952000] Yenta: Routing CardBus interrupts to PCI
[   10.952000] Yenta TI: socket 0000:06:01.0, mfunc 0x01111112, devctl 0x66
[   11.188000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   11.188000] Socket status: 30000007
[   11.188000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #08
[   11.188000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   11.188000] cs: IO port probe 0x3000-0x3fff: clean.
[   11.188000] pcmcia: parent PCI bridge Memory window: 0xd4200000 - 0xd42fffff
[   11.188000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   11.392000] iTCO_vendor_support: vendor-support=0
[   11.400000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   11.400000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   11.400000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.512000] ieee80211_crypt: registered algorithm 'NULL'
[   11.548000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   11.548000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   11.708000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.728000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[   11.728000] [fglrx] ASYNCIO init succeed!
[   11.728000] [fglrx] PAT is enabled successfully!
[   11.728000] [fglrx] module loaded - fglrx 8.42.3 [Oct 19 2007] on minor 0
[   11.760000] NET: Registered protocol family 17
[   11.780000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   11.780000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   11.780000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 17 (level, low) -> IRQ 17
[   11.780000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   11.956000] ipw2200: Radio Frequency Kill Switch is On:
[   11.956000] Kill switch must be turned off for wireless networking to work.
[   11.956000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   12.232000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.232000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   12.264000] cs: IO port probe 0x100-0x3af: clean.
[   12.264000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   12.264000] cs: IO port probe 0x820-0x8ff: clean.
[   12.264000] cs: IO port probe 0xc00-0xcf7: clean.
[   12.264000] cs: IO port probe 0xa00-0xaff: clean.
[   12.532000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   12.568000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   13.076000] loop: module loaded
[   13.116000] lp: driver loaded but no devices found
[   13.404000] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   13.664000] EXT3 FS on sda1, internal journal
[   15.032000] NET: Registered protocol family 10
[   15.032000] lo: Disabled Privacy Extensions
[   15.944000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.976000] ACPI: Battery Slot [BAT1] (battery present)
[   15.992000] No dock devices found.
[   16.072000] input: Power Button (FF) as /class/input/input3
[   16.072000] ACPI: Power Button (FF) [PWRF]
[   16.116000] input: Lid Switch as /class/input/input4
[   16.116000] ACPI: Lid Switch [LID]
[   16.156000] input: Power Button (CM) as /class/input/input5
[   16.160000] ACPI: Power Button (CM) [PWRB]
[   16.200000] input: Sleep Button (CM) as /class/input/input6
[   16.204000] ACPI: Sleep Button (CM) [SLPB]
[   16.216000] ACPI: AC Adapter [ACAD] (on-line)
[   25.852000] eth1: no IPv6 routers present

```

The lines from above reporting errors which I'm concerned about are:
```

[   20.591870] PCI: Using ACPI for IRQ routing
[   20.591873] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.591877] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   20.591921] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   20.591962] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   20.592002] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   20.592043] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   20.592083] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   20.592124] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   20.592164] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   20.592205] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2

```

**lspci** gives this output:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by RedSquirrel on 2007-11-06
I haven't had this issue, but did you try adding:

```
pci=routeirq
```

to your kernel options?

By the way, I'm not sure about gutsy, but I know on feisty that there was an issue with ATI X**** graphics cards. There was a sticky on the Absolute Beginner Talk section about this. I'm not sure if it's still there, so you might have to search the forums a bit.

---

### Post by kentl on 2007-11-06
It just adds some errors I'm afraid. But thanks for trying to help! And I'll try searching for the thread you mentioned. (and btw, this is part of my effort to try Fluxbox which you've helped me with as well, things go slow due to work and stuff) :-)

---

### Post by RedSquirrel on 2007-11-07
Sometimes doing things slowly and carefully is the best approach. Good luck. :)

---

### Post by kentl on 2007-11-08
Thanks, I'm taking the Feisty route now, and the error doesn't appear using it.

---

### Post by grinias on 2007-11-08
Booting with 
```

pci=routeirq

```
was the solution for me. During the last week I had problems with ACPI on my Acer TM 4101,
although I had updated Feisty to Gutsy once the Candidate Release came out.
Booting with 
```
acpi=off 
``` was not an acceptable solution for me, since I was left without 
sound and network!!!

Thanx "RedSquirrel"!!!

---

### Post by grinias on 2007-11-09
...and the problem persists... After going at home and using my adsl connection (instead of ethernet LAN of university) the kernel problem came back...
Tracing back the whole procedure, the problem appeared once I upgraded to 2.6.22-14.46 at home using the ADSL connection. I recall now that after upgrading,
my laptop rebooted. When it came back, probably the sound and ethernet cards did not work, but I did not notice it, since I was preparing a presentation for the next day. 
I use a usb adsl (instead of ethernet) cable to connect at home.
The next time I booted, I had to use acpi=off as kernel option. The (very strange) problem dissapears when I use the ethernet card and I can boot normally in that case.

---

