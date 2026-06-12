---
title: "Hardy Upgrade Issues"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by stalinheredia on 2008-04-25
Hello guys, I just finished today upgrading my computer to hardy and after it was upgraded my computer became very very very slow, the icon became smaller, compiz still works but i had to disable it cause my computer is almost unoperable. I went to the dive drivers and found out that the HAL and the wireless drive are not being used (with the proprietary software), i'm not sure if that is part of the problem, i also disable them and enable them back, reseted the computer but still very very slow. I need some help to fix this issues......thanx before hand........

---

### Post by hermes0710 on 2008-04-25
> **stalinheredia said:**
> ..i also disable them and enable them back..

Are they "in use" after this?

If i were you i would delete all configuration files from the home folder...

(You can try to add a new user, then logout and login as the new user. Do you still have the same issues?)

About the drivers stuff could you post the dmesg output?

---

### Post by stalinheredia on 2008-04-29
> **hermes0710 said:**
> Are they "in use" after this?

If i were you i would delete all configuration files from the home folder...

(You can try to add a new user, then logout and login as the new user. Do you still have the same issues?)

About the drivers stuff could you post the dmesg output?
Thanx  hermes, but they are not in use....it seems like the drivers are not being used....
my dmesg is this:
> [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077e70000 (usable)
[    0.000000]  BIOS-e820: 0000000077e70000 - 0000000077e84000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077e84000 - 0000000077e86000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077e86000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 1022MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7380
[    0.000000] Entering add_active_range(0, 0, 491120) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   491120
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   491120
[    0.000000] On node 0 totalpages: 491120
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2044 pages used for memmap
[    0.000000]   HighMem zone: 259700 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F72E0 checksum 0
[    0.000000] ACPI: RSDP 000F72E0, 0024 (r2 TOSCPL)
[    0.000000] ACPI: XSDT 77E7B89D, 0064 (r1 TOSCPL TOSCPL00  6040000  LTP        0)
[    0.000000] ACPI: FACP 77E83939, 00F4 (r3 TOSCPL Herring   6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 77E7B901, 8038 (r1 TOSCPL    SB600  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 77E85FC0, 0040
[    0.000000] ACPI: TCPA 77E83AA1, 0032 (r2 TOSCPL           6040000 PTEC        0)
[    0.000000] ACPI: SLIC 77E83AD3, 0176 (r1 TOSCPL TOSCPL00  6040000 LOHR        0)
[    0.000000] ACPI: SSDT 77E83C49, 01C4 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 77E83E0D, 0054 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 77E83E61, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 77E83E9D, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: ASF! 77E83ED5, 012B (r32    DMA AMDTBL    6040000 PTL         1)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x43538310 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 487284
[    0.000000] Kernel command line: vga=791 root=UUID=4dc7b8ed-54b0-43fa-86b1-3e872e0c3512 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1795.643 MHz processor.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 1935916k/1964480k available (2015k kernel code, 27200k reserved, 915k data, 364k init, 1046976k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.000000] hpet0: 4 32-bit timers, 14318180 Hz
[    0.084000] Calibrating delay using timer specific routine.. 3667.32 BogoMIPS (lpj=7334659)
[    0.084000] Security Framework v1.0.0 initialized
[    0.084000] SELinux:  Disabled at boot.
[    0.084000] Mount-cache hash table entries: 512
[    0.084000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.084000] CPU 0(2) -> Core 0
[    0.084000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.084000] Compat vDSO mapped to ffffe000.
[    0.084000] Checking 'hlt' instruction... OK.
[    0.100000] SMP alternatives: switching to UP code
[    0.100000] Early unpacking initramfs... done
[    0.436000] ACPI: Core revision 20070126
[    0.436000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.444000] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.448000] SMP alternatives: switching to SMP code
[    0.448000] Booting processor 1/1 eip 3000
[    0.456000] Initializing CPU#1
[    0.536000] Calibrating delay using timer specific routine.. 3591.02 BogoMIPS (lpj=7182051)
[    0.536000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.536000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.536000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.536000] CPU 1(2) -> Core 1
[    0.536000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.536000] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.536000] Total of 2 processors activated (7258.35 BogoMIPS).
[    0.536000] ENABLING IO-APIC IRQs
[    0.536000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.536000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.536000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[    0.536000] ...trying to set up timer as Virtual Wire IRQ... works.
[    0.580000] Brought up 2 CPUs
[    0.636000] migration_cost=4000
[    0.636000] Booting paravirtualized kernel on bare hardware
[    0.636000] Time:  0:45:45  Date: 03/30/108
[    0.636000] NET: Registered protocol family 16
[    0.636000] EISA bus registered
[    0.636000] ACPI: bus type pci registered
[    0.636000] PCI: PCI BIOS revision 3.00 entry at 0xfddd6, last bus=27
[    0.636000] PCI: Using configuration type 1
[    0.636000] Setting up standard PCI resources
[    0.636000] ACPI: EC: Look up EC in DSDT
[    0.640000] ACPI: EC: GPE=0x13, ports=0x66, 0x62
[    0.648000] ACPI: System BIOS is requesting _OSI(Linux)
[    0.648000] ACPI: Please test with "acpi_osi=!Linux"
[    0.648000] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[    0.652000] ACPI: Interpreter enabled
[    0.652000] ACPI: (supports S0 S3 S4 S5)
[    0.652000] ACPI: Using IOAPIC for interrupt routing
[    0.700000] ACPI: EC: GPE=0x13, ports=0x66, 0x62
[    0.700000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.700000] PCI: Probing PCI hardware (bus 00)
[    0.700000] PCI: Transparent bridge - 0000:00:14.4
[    0.700000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.700000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.700000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.700000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.700000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB5_._PRT]
[    0.700000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.700000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.704000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.704000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.704000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.704000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.704000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.704000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.704000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.704000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.704000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.704000] pnp: PnP ACPI init
[    0.708000] ACPI: bus type pnp registered
[    0.732000] pnp: PnP ACPI: found 11 devices
[    0.732000] ACPI: ACPI bus type pnp unregistered
[    0.732000] PnPBIOS: Disabled by ACPI PNP
[    0.732000] PCI: Using ACPI for IRQ routing
[    0.732000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.732000] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[    0.732000] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[    0.812000] NET: Registered protocol family 8
[    0.812000] NET: Registered protocol family 20
[    0.812000] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.812000] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.812000] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.812000] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[    0.812000] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[    0.812000] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.812000] pnp: 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.812000] pnp: 00:09: iomem range 0x0-0x0 could not be reserved
[    0.816000] Time: hpet clocksource has been installed.
[    0.844000] PCI: Bridge: 0000:00:01.0
[    0.844000]   IO window: 9000-9fff
[    0.844000]   MEM window: f8000000-f81fffff
[    0.844000]   PREFETCH window: f0000000-f7ffffff
[    0.844000] PCI: Bridge: 0000:00:05.0
[    0.844000]   IO window: disabled.
[    0.844000]   MEM window: disabled.
[    0.844000]   PREFETCH window: disabled.
[    0.844000] PCI: Bridge: 0000:00:06.0
[    0.844000]   IO window: a000-afff
[    0.844000]   MEM window: f8300000-f83fffff
[    0.844000]   PREFETCH window: 8c000000-8c0fffff
[    0.844000] PCI: Bridge: 0000:00:07.0
[    0.844000]   IO window: disabled.
[    0.844000]   MEM window: f8200000-f82fffff
[    0.844000]   PREFETCH window: disabled.
[    0.844000] PCI: Bus 27, cardbus bridge: 0000:1a:04.0
[    0.844000]   IO window: 00002000-000020ff
[    0.844000]   IO window: 00002400-000024ff
[    0.844000]   PREFETCH window: 88000000-8bffffff
[    0.844000]   MEM window: 90000000-93ffffff
[    0.844000] PCI: Bridge: 0000:00:14.4
[    0.844000]   IO window: 2000-2fff
[    0.844000]   MEM window: f8400000-f84fffff
[    0.844000]   PREFETCH window: 88000000-8bffffff
[    0.844000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    0.844000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.844000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.844000] ACPI: PCI Interrupt 0000:1a:04.0[A] -> GSI 20 (level, low) -> IRQ 16
[    0.844000] NET: Registered protocol family 2
[    0.892000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.892000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.892000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.892000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.892000] TCP reno registered
[    0.908000] checking if image is initramfs... it is
[    1.544000] Freeing initrd memory: 7115k freed
[    1.544000] audit: initializing netlink socket (disabled)
[    1.544000] audit(1209516344.316:1): initialized
[    1.544000] highmem bounce pool size: 64 pages
[    1.544000] VFS: Disk quotas dquot_6.5.1
[    1.544000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.544000] io scheduler noop registered
[    1.544000] io scheduler anticipatory registered
[    1.544000] io scheduler deadline registered
[    1.544000] io scheduler cfq registered (default)
[    1.544000] PCI: MSI quirk detected. MSI deactivated.
[    1.544000] Boot video device is 0000:01:05.0
[    1.544000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    1.544000] assign_interrupt_mode Found MSI capability
[    1.544000] Allocate Port Service[0000:00:05.0:pcie00]
[    1.544000] Allocate Port Service[0000:00:05.0:pcie02]
[    1.544000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    1.544000] assign_interrupt_mode Found MSI capability
[    1.544000] Allocate Port Service[0000:00:06.0:pcie00]
[    1.544000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    1.544000] assign_interrupt_mode Found MSI capability
[    1.544000] Allocate Port Service[0000:00:07.0:pcie00]
[    1.544000] isapnp: Scanning for PnP cards...
[    1.900000] isapnp: No Plug & Play device found
[    1.928000] Real Time Clock Driver v1.12ac
[    1.928000] hpet_resources: 0xfed00000 is busy
[    1.928000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.932000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.932000] input: Macintosh mouse button emulation as /class/input/input0
[    1.932000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.976000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.976000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.976000] mice: PS/2 mouse device common for all mice
[    1.980000] EISA: Probing bus 0 at eisa.0
[    1.980000] Cannot allocate resource for EISA slot 1
[    1.980000] Cannot allocate resource for EISA slot 2
[    1.980000] Cannot allocate resource for EISA slot 8
[    1.980000] EISA: Detected 0 cards.
[    1.980000] TCP cubic registered
[    1.980000] NET: Registered protocol family 1
[    1.980000] Using IPI No-Shortcut mode
[    1.980000]   Magic number: 4:474:760
[    1.980000] Freeing unused kernel memory: 364k freed
[    2.004000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.084000] vesafb: framebuffer at 0xf0000000, mapped to 0xf8880000, using 3072k, total 16384k
[    2.084000] vesafb: mode is 1024x768x16, linelength=2048, pages=9
[    2.084000] vesafb: protected mode interface info at c000:9fa4
[    2.084000] vesafb: pmi: set display start = c00ca02e, set palette = c00ca0ec
[    2.084000] vesafb: scrolling: redraw
[    2.084000] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    2.084000] Console: switching to colour frame buffer device 128x48
[    2.136000] fb0: VESA VGA frame buffer device
[    3.324000] AppArmor: AppArmor initialized<5>audit(1209516346.316:2):  type=1505 info="AppArmor initialized" pid=1272
[    3.336000] fuse init (API version 7.8)
[    3.340000] Failure registering capabilities with primary security module.
[    3.372000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.976000] usbcore: registered new interface driver usbfs
[    3.976000] usbcore: registered new interface driver hub
[    3.976000] usbcore: registered new device driver usb
[    3.976000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.976000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 17
[    3.976000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.976000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.976000] ohci_hcd 0000:00:13.0: irq 17, io mem 0xf8704000
[    3.980000] SCSI subsystem initialized
[    3.984000] libata version 2.21 loaded.
[    3.992000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.992000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.044000] usb usb1: configuration #1 chosen from 1 choice
[    4.044000] hub 1-0:1.0: USB hub found
[    4.044000] hub 1-0:1.0: 2 ports detected
[    4.148000] ahci 0000:00:12.0: version 2.2
[    4.148000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[    4.148000] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    5.152000] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    5.152000] ahci 0000:00:12.0: flags: ncq ilck pm led clo pmp pio slum part 
[    5.152000] scsi0 : ahci
[    5.152000] scsi1 : ahci
[    5.152000] scsi2 : ahci
[    5.152000] scsi3 : ahci
[    5.152000] ata1: SATA max UDMA/133 cmd 0xf8bd4100 ctl 0x00000000 bmdma 0x00000000 irq 18
[    5.152000] ata2: SATA max UDMA/133 cmd 0xf8bd4180 ctl 0x00000000 bmdma 0x00000000 irq 18
[    5.152000] ata3: SATA max UDMA/133 cmd 0xf8bd4200 ctl 0x00000000 bmdma 0x00000000 irq 18
[    5.152000] ata4: SATA max UDMA/133 cmd 0xf8bd4280 ctl 0x00000000 bmdma 0x00000000 irq 18
[    5.636000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.636000] ata1.00: ATA-8: FUJITSU MHX2250BT, 0040000C, max UDMA/100
[    5.636000] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.636000] ata1.00: configured for UDMA/100
[    5.948000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.260000] ata3: SATA link down (SStatus 0 SControl 300)
[    6.572000] ata4: SATA link down (SStatus 0 SControl 300)
[    6.572000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHX2250B 0040 PQ: 0 ANSI: 5
[    6.572000] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[    6.572000] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    6.576000] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 2
[    6.576000] ehci_hcd 0000:00:13.5: debug port 1
[    6.576000] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf8709400
[    6.576000] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.576000] usb usb2: configuration #1 chosen from 1 choice
[    6.576000] hub 2-0:1.0: USB hub found
[    6.576000] hub 2-0:1.0: 10 ports detected
[    6.580000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    6.580000] sd 0:0:0:0: [sda] Write Protect is off
[    6.580000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.580000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.580000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    6.580000] sd 0:0:0:0: [sda] Write Protect is off
[    6.580000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.580000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.580000]  sda: sda1 sda2 <<6>ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 20
[    6.680000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    6.680000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    6.680000] ohci_hcd 0000:00:13.1: irq 20, io mem 0xf8705000
[    6.684000]  sda5 >
[    6.684000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.688000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.736000] usb usb3: configuration #1 chosen from 1 choice
[    6.736000] hub 3-0:1.0: USB hub found
[    6.736000] hub 3-0:1.0: 2 ports detected
[    6.840000] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 21
[    6.840000] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    6.840000] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    6.840000] ohci_hcd 0000:00:13.2: irq 21, io mem 0xf8706000
[    6.896000] usb usb4: configuration #1 chosen from 1 choice
[    6.896000] hub 4-0:1.0: USB hub found
[    6.896000] hub 4-0:1.0: 2 ports detected
[    6.920000] usb 2-8: new high speed USB device using ehci_hcd and address 2
[    6.940000] Attempting manual resume
[    6.940000] swsusp: Resume From Partition 8:5
[    6.940000] PM: Checking swsusp image.
[    6.960000] PM: Resume from disk failed.
[    7.000000] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 20
[    7.000000] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    7.000000] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    7.000000] ohci_hcd 0000:00:13.3: irq 20, io mem 0xf8707000
[    7.004000] kjournald starting.  Commit interval 5 seconds
[    7.004000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.056000] usb usb5: configuration #1 chosen from 1 choice
[    7.056000] hub 5-0:1.0: USB hub found
[    7.056000] hub 5-0:1.0: 2 ports detected
[    7.064000] usb 2-8: configuration #1 chosen from 1 choice
[    7.160000] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 21
[    7.160000] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    7.160000] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    7.160000] ohci_hcd 0000:00:13.4: irq 21, io mem 0xf8708000
[    7.216000] usb usb6: configuration #1 chosen from 1 choice
[    7.216000] hub 6-0:1.0: USB hub found
[    7.216000] hub 6-0:1.0: 2 ports detected
[    7.320000] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[    7.320000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[    7.320000] SB600_PATA: chipset revision 0
[    7.320000] SB600_PATA: not 100% native mode: will probe irqs later
[    7.320000]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[    7.320000] Probing IDE interface ide0...
[    8.056000] hda: PIONEER DVD-RW DVR-K17LF, ATAPI CD/DVD-ROM drive
[    8.392000] hda: selected mode 0x42
[    8.392000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    8.408000] ACPI: PCI Interrupt 0000:1a:04.1[B] -> GSI 21 (level, low) -> IRQ 22
[    8.456000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8406000-f84067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    8.456000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    8.456000] ACPI: PCI Interrupt 0000:0e:00.0[A] -> GSI 18 (level, low) -> IRQ 21
[    8.456000] PCI: Setting latency timer of device 0000:0e:00.0 to 64
[    8.456000] eth0: RTL8101e at 0xf887c000, 00:16:d4:ff:f0:54, XID 34000000 IRQ 21
[    9.728000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f75c0405790]
[   19.416000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.728000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.728000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.836000] Yenta: CardBus bridge found at 0000:1a:04.0 [1179:ff00]
[   19.836000] Yenta: Enabling burst memory read transactions
[   19.836000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   19.836000] Yenta: Routing CardBus interrupts to PCI
[   19.836000] Yenta TI: socket 0000:1a:04.0, mfunc 0x10a01b22, devctl 0x64
[   19.848000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   20.068000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   20.068000] Socket status: 30000006
[   20.068000] Yenta: Raising subordinate bus# of parent bus (#1a) from #1b to #1e
[   20.068000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   20.068000] cs: IO port probe 0x2000-0x2fff: clean.
[   20.068000] pcmcia: parent PCI bridge Memory window: 0xf8400000 - 0xf84fffff
[   20.068000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   20.212000] sdhci: Secure Digital Host Controller Interface driver
[   20.212000] sdhci: Copyright(c) Pierre Ossman
[   20.212000] sdhci: SDHCI controller found at 0000:1a:04.3 [104c:803c] (rev 0)
[   20.212000] ACPI: PCI Interrupt 0000:1a:04.3[C] -> GSI 22 (level, low) -> IRQ 18
[   20.212000] mmc0: SDHCI at 0xf8406800 irq 18 DMA
[   20.408000] ACPI: PCI Interrupt 0000:1a:04.2[C] -> GSI 22 (level, low) -> IRQ 18
[   20.432000] tifm_core: MMC/SD card detected in socket 0:1
[   20.448000] input: PC Speaker as /class/input/input2
[   20.520000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(33)
[   20.520000] Uniform CD-ROM driver Revision: 3.20
[   20.524000] Linux video capture interface: v2.00
[   20.608000] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   20.608000] usbcore: registered new interface driver uvcvideo
[   20.608000] USB Video Class driver (v0.1.0)
[   20.724000] cs: IO port probe 0x100-0x3af: clean.
[   20.724000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.728000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   20.728000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   20.728000] cs: IO port probe 0xa00-0xaff: clean.
[   20.768000] mmcblk0: mmc1:d555 SU04G 3979776KiB 
[   20.768000]  mmcblk0: p1
[   20.912000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   21.172000] input: PS/2 Mouse as /class/input/input3
[   21.208000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   22.212000] si3054: cannot initialize. EXT MID = 0000
[   22.404000] lp: driver loaded but no devices found
[   22.580000] ndiswrapper version 1.49 loaded (smp=yes, preempt=no)
[   22.708000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   22.708000] ACPI: PCI Interrupt 0000:14:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   22.708000] ndiswrapper (ZwClose:2227): closing handle 0xdf874e28 not implemented
[   22.708000] PCI: Setting latency timer of device 0000:14:00.0 to 64
[   23.120000] ndiswrapper: using IRQ 19
[   23.324000] wlan0: ethernet device 00:1b:9e:1f:1a:13 using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   23.328000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   23.328000] usbcore: registered new interface driver ndiswrapper
[   23.420000] Adding 5695000k swap on /dev/sda5.  Priority:-1 extents:1 across:5695000k
[   23.480000] ACPI: AC Adapter [ACAD] (on-line)
[   24.024000] EXT3 FS on sda1, internal journal
[   24.252000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   25.764000] audit(1209516370.035:3):  type=1505 operation="profile_load" info="failed to unpack profile" name="/usr/lib/cups/backend/cups-pdf" pid=4384
[   25.936000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.712000] ACPI: Battery Slot [BAT1] (battery absent)
[   26.732000] No dock devices found.
[   26.784000] input: Power Button (FF) as /class/input/input5
[   26.784000] ACPI: Power Button (FF) [PWRF]
[   26.784000] input: Lid Switch as /class/input/input6
[   26.784000] ACPI: Lid Switch [LID]
[   26.784000] input: Power Button (CM) as /class/input/input7
[   26.784000] ACPI: Power Button (CM) [PWRB]
[   26.968000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   26.968000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   27.308000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (version 2.00.00)
[   27.308000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[   27.308000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15
[   27.308000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   29.276000] r8169: eth0: link down
[   31.296000] [fglrx] Maximum main memory to use for locked dma buffers: 1776 MBytes.
[   31.296000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   31.300000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 21
[   31.492000] Failure registering capabilities with primary security module.
[   31.768000] ppdev: user-space parallel port driver
[   32.036000] apm: BIOS not found.
[   32.580000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   32.580000] vboxdrv: Successfully done.
[   33.172000] Bluetooth: Core ver 2.11
[   33.172000] NET: Registered protocol family 31
[   33.172000] Bluetooth: HCI device and connection manager initialized
[   33.172000] Bluetooth: HCI socket layer initialized
[   33.188000] Bluetooth: L2CAP ver 2.8
[   33.188000] Bluetooth: L2CAP socket layer initialized
[   33.272000] Bluetooth: RFCOMM socket layer initialized
[   33.272000] Bluetooth: RFCOMM TTY layer initialized
[   33.272000] Bluetooth: RFCOMM ver 1.8
[   33.412000] [fglrx:firegl_init_pcie] *ERROR* Invalid GART type 0.
[   35.000000] Clocksource tsc unstable (delta = -208476563 ns)
[   40.840000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   62.692000] NET: Registered protocol family 10
[   62.692000] lo: Disabled Privacy Extensions
[   62.692000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   62.692000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.856000] NET: Registered protocol family 17
[  241.528000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  260.100000] wlan0: no IPv6 routers present

---

### Post by stalinheredia on 2008-05-06
Please please anybody else, ubuntu is the only system i have on my laptop and I realy need to fix this issues. please somebody helpppp............

---

### Post by md5hash on 2008-05-06
i always receive this message when upgrading.. 

```
Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

Failed to fetch 
http://ph.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz 
Connection failed [IP: 91.189.88.45 80] 



Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

```

---

