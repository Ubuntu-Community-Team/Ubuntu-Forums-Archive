---
title: "Ubuntu 8.08 won't start on Asus EEEPC (SD card)"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by weblordpepe on 2008-05-31
Hi there boys & girls. I am having difficulty with the following setup:

Asus EEE PC, with Ubuntu 8.08 and GRUB installed on the SD card.

What happens, is I throw in the SD card, boot from it with GRUB, and Ubuntu starts to load. It freezes on 'Initializing USB mass storage driver...' (*I can see this because I am booting with Recovery Mode*)

If I leave it there for a good 2 or 3 minutes, it continues to the login prompt.

After logging in, it freezes at a blank tan page. Nothing happens from that point on.
I will paste my dmesg below, and bold things I think are of interest. Can anyone please provide help? This is a standard Ubuntu 8.08 going onto a 16GB SD Card in its cardreader:

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f780000 (usable)
[    0.000000]  BIOS-e820: 000000001f780000 - 000000001f790000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f790000 - 000000001f7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f7d0000 - 000000001f7de000 (reserved)
[    0.000000]  BIOS-e820: 000000001f7e0000 - 000000001f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 128896) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128896
[    0.000000]   HighMem    128896 ->   128896
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128896
[    0.000000] On node 0 totalpages: 128896
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 975 pages used for memmap
[    0.000000]   Normal zone: 123825 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00FBE60 checksum 0
[    0.000000] ACPI: RSDP 000FBE60, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1F780000, 0034 (r1 A M I  OEMRSDT   1000804 MSFT       97)
[    0.000000] ACPI: FACP 1F780200, 0081 (r1 A M I  OEMFACP   1000804 MSFT       97)
[    0.000000] ACPI: DSDT 1F780400, 5F2B (r1  A0797 A0797000        0 INTL 20051117)
[    0.000000] ACPI: FACS 1F790000, 0040
[    0.000000] ACPI: APIC 1F780390, 0068 (r1 A M I  OEMAPIC   1000804 MSFT       97)
[    0.000000] ACPI: OEMB 1F790040, 0046 (r1 A M I  AMI_OEM   1000804 MSFT       97)
[    0.000000] ACPI: MCFG 1F786330, 003C (r1 A M I  OEMMCFG   1000804 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:df600000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127889
[    0.000000] Kernel command line: root=UUID=c9cce3b4-615c-42b4-8a44-e5b86a0dbc6a ro single
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 630.088 MHz processor.
[   17.971184] Console: colour VGA+ 80x25
[   17.971193] console [tty0] enabled
[   17.975887] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.976510] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.003577] Memory: 498724k/515584k available (2157k kernel code, 16192k reserved, 998k data, 364k init, 0k highmem)
[   18.003729] virtual kernel memory layout:
[   18.003732]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   18.003735]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.003739]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   18.003742]     lowmem  : 0xc0000000 - 0xdf780000   ( 503 MB)
[   18.003745]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   18.003749]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   18.003752]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   18.004410] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.004648] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   18.084791] Calibrating delay using timer specific routine.. 1261.75 BogoMIPS (lpj=2523507)
[   18.085006] Security Framework initialized
[   18.085099] SELinux:  Disabled at boot.
[   18.085212] AppArmor: AppArmor initialized
[   18.085301] Failure registering capabilities with primary security module.
[   18.085408] Mount-cache hash table entries: 512
[   18.085782] CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   18.085814] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.085937] CPU: L2 cache: 512K
[   18.086015] CPU: After all inits, caps: afe9fbbf 00000000 00000000 00002040 00000000 00000000 00000000 00000000
[   18.086036] Compat vDSO mapped to ffffe000.
[   18.086139] Checking 'hlt' instruction... OK.
[   18.101763] SMP alternatives: switching to UP code
[   18.106609] Freeing SMP alternatives: 11k freed
[   18.106971] Early unpacking initramfs... done
[   19.121567] ACPI: Core revision 20070126
[   19.121828] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.322866] CPU0: Intel(R) Celeron(R) M processor          900MHz stepping 06
[   19.323070] Total of 1 processors activated (1261.75 BogoMIPS).
[   19.323331] ENABLING IO-APIC IRQs
[   19.323639] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.468795] Brought up 1 CPUs
[   19.468919] CPU0 attaching sched-domain:
[   19.468926]  domain 0: span 01
[   19.468931]   groups: 01
[   19.469365] net_namespace: 64 bytes
[   19.469468] Booting paravirtualized kernel on bare hardware
[   19.470812] Time: 11:20:11  Date: 06/01/08
[   19.470959] NET: Registered protocol family 16
[   19.471581] EISA bus registered
[   19.471696] ACPI: bus type pci registered
[   19.472306] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   19.472403] PCI: Using configuration type 1
[   19.472483] Setting up standard PCI resources
[   19.495811] ACPI: EC: Look up EC in DSDT
[   19.524928] ACPI: Interpreter enabled
[   19.525019] ACPI: (supports S0 S1 S3 S4 S5)
[   19.525299] ACPI: Using IOAPIC for interrupt routing
[   19.542205] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[   19.542305] ACPI: EC: driver started in poll mode
[   19.542701] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.543818] Force enabled HPET at base address 0xfed00000
[   19.543832] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   19.543926] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   19.544887] PCI: Transparent bridge - 0000:00:1e.0
[   19.545037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.545454] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   19.545682] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   19.545900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   19.557638] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   19.558462] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   19.559265] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   19.560077] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   19.560894] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   19.561798] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   19.562698] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   19.563601] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   19.564444] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.564623] pnp: PnP ACPI init
[   19.564746] ACPI: bus type pnp registered
[   19.570073] pnp: PnP ACPI: found 13 devices
[   19.570161] ACPI: ACPI bus type pnp unregistered
[   19.570249] PnPBIOS: Disabled by ACPI PNP
[   19.570980] PCI: Using ACPI for IRQ routing
[   19.571071] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.592701] NET: Registered protocol family 8
[   19.592786] NET: Registered protocol family 20
[   19.593288] hpet clockevent registered
[   19.593299] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   19.593517] hpet0: 3 64-bit timers, 14318180 Hz
[   19.594688] AppArmor: AppArmor Filesystem Enabled
[   19.596679] Time: tsc clocksource has been installed.
[   19.604788] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   19.604912] system 00:08: ioport range 0x380-0x383 has been reserved
[   19.605006] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   19.605098] system 00:08: ioport range 0x800-0x87f has been reserved
[   19.605189] system 00:08: ioport range 0x480-0x4bf has been reserved
[   19.605282] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   19.605376] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   19.605472] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   19.605603] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   19.605699] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   19.605830] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[   19.605932] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   19.606037] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   19.606129] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   19.606223] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   19.606318] system 00:0c: iomem range 0x100000-0x1f7fffff could not be reserved
[   19.606441] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   19.637646] PCI: Bridge: 0000:00:1c.0
[   19.637729]   IO window: disabled.
[   19.637812]   MEM window: disabled.
[   19.637891]   PREFETCH window: disabled.
[   19.637977] PCI: Bridge: 0000:00:1c.1
[   19.638053]   IO window: disabled.
[   19.638134]   MEM window: fbf00000-fbffffff
[   19.638217]   PREFETCH window: disabled.
[   19.638300] PCI: Bridge: 0000:00:1c.2
[   19.638377]   IO window: disabled.
[   19.638458]   MEM window: f8000000-fbefffff
[   19.638543]   PREFETCH window: f0000000-f6ffffff
[   19.638630] PCI: Bridge: 0000:00:1e.0
[   19.638707]   IO window: disabled.
[   19.638787]   MEM window: disabled.
[   19.638867]   PREFETCH window: disabled.
[   19.638998] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.639160] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.639189] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   19.639349] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.639378] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.639537] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   19.639555] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.639591] NET: Registered protocol family 2
[   19.676836] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   19.677438] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   19.677823] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   19.678175] TCP: Hash tables configured (established 16384 bind 16384)
[   19.678267] TCP reno registered
[   19.689011] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   20.649169]  it is
[   21.676813] Freeing initrd memory: 7648k freed
[   21.678350] audit: initializing netlink socket (disabled)
[   21.678470] audit(1212319212.364:1): initialized
[   21.684091] VFS: Disk quotas dquot_6.5.1
[   21.684409] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.684886] io scheduler noop registered
[   21.684970] io scheduler anticipatory registered
[   21.685052] io scheduler deadline registered
[   21.685172] io scheduler cfq registered (default)
[   21.685279] Boot video device is 0000:00:02.0
[   21.685658] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.685722] assign_interrupt_mode Found MSI capability
[   21.685865] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.685977] Allocate Port Service[0000:00:1c.0:pcie02]
[   21.686149] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.686210] assign_interrupt_mode Found MSI capability
[   21.686343] Allocate Port Service[0000:00:1c.1:pcie00]
[   21.686446] Allocate Port Service[0000:00:1c.1:pcie02]
[   21.686617] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.686677] assign_interrupt_mode Found MSI capability
[   21.686808] Allocate Port Service[0000:00:1c.2:pcie00]
[   21.686911] Allocate Port Service[0000:00:1c.2:pcie02]
[   21.687588] isapnp: Scanning for PnP cards...
[   22.041880] isapnp: No Plug & Play device found
[   22.143674] Real Time Clock Driver v1.12ac
[   22.144014] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.147609] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.147953] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.148404] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.180693] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.180790] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.192415] mice: PS/2 mouse device common for all mice
[   22.192808] EISA: Probing bus 0 at eisa.0
[   22.192935] EISA: Detected 0 cards.
[   22.193015] cpuidle: using governor ladder
[   22.193095] cpuidle: using governor menu
[   22.193390] NET: Registered protocol family 1
[   22.193533] Using IPI No-Shortcut mode
[   22.193693] registered taskstats version 1
[   22.193993]   Magic number: 12:509:326
[   22.194113]   hash matches device ttyyf
[   22.194391] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.194481] EDD information not available.
[   22.194929] Freeing unused kernel memory: 364k freed
[   22.228287] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.730323] fuse init (API version 7.9)
[   22.797670] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   22.797905] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.802387] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   22.808027] ACPI: Thermal Zone [TZ00] (23 C)
[   24.735962] usbcore: registered new interface driver usbfs
[   24.736106] usbcore: registered new interface driver hub
[   24.747933] usbcore: registered new device driver usb
[   24.768426] USB Universal Host Controller Interface driver v3.0
[   24.768666] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   24.768838] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.768848] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.769598] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   24.769771] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e400
[   24.770198] usb usb1: configuration #1 chosen from 1 choice
[   24.770350] hub 1-0:1.0: USB hub found
[   24.770440] hub 1-0:1.0: 2 ports detected
[   24.872068] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   24.872252] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   24.872265] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   24.872409] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   24.872575] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000e480
[   24.872945] usb usb2: configuration #1 chosen from 1 choice
[   24.873089] hub 2-0:1.0: USB hub found
[   24.873179] hub 2-0:1.0: 2 ports detected
[   24.976034] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   24.976221] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   24.976231] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   24.976374] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   24.976538] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   24.976911] usb usb3: configuration #1 chosen from 1 choice
[   24.977054] hub 3-0:1.0: USB hub found
[   24.977146] hub 3-0:1.0: 2 ports detected
[   25.080032] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   25.080225] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   25.080235] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   25.080402] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   25.080568] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e880
[   25.080950] usb usb4: configuration #1 chosen from 1 choice
[   25.081102] hub 4-0:1.0: USB hub found
[   25.081191] hub 4-0:1.0: 2 ports detected
[   25.172821] SCSI subsystem initialized
[   25.194340] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   25.194536] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.194545] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.194695] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   25.198751] ehci_hcd 0000:00:1d.7: debug port 1
[   25.198839] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   25.198855] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf7eb7c00
[   25.211762] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.212187] usb usb5: configuration #1 chosen from 1 choice
[   25.212334] hub 5-0:1.0: USB hub found
[   25.212426] hub 5-0:1.0: 8 ports detected
[   25.307769] libata version 3.00 loaded.
[   25.344425] ahci 0000:00:1f.2: version 3.0
[   25.344478] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   25.344655] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   25.344752] ahci: probe of 0000:00:1f.2 failed with error -22
[   25.460713] ata_piix 0000:00:1f.2: version 2.12
[   25.460730] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   25.460990] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   25.461217] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[B][   25.485003] scsi0 : ata_piix
[   25.519711] scsi1 : ata_piix
[   25.523213] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   25.523310] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   25.591731] usb 5-5: new high speed USB device using ehci_hcd and address 2
[   25.725295] usb 5-5: configuration #1 chosen from 1 choice
[   25.848090] ata2.00: ATA-4: SILICONMOTION SM223AC, , max UDMA/66
[   25.848195] ata2.00: 7815024 sectors, multi 0: LBA 
[   25.848315] ata2.00: limited to UDMA/33 due to 40-wire cable
[   25.864056] ata2.00: configured for UDMA/33
[   25.864494] scsi 1:0:0:0: Direct-Access     ATA      SILICONMOTION SM n/a  PQ: 0 ANSI: 5
[   26.839591] Driver 'sd' needs updating - please use bus_type methods
[   26.839891] sd 1:0:0:0: [sda] 7815024 512-byte hardware sectors (4001 MB)
[   26.840009] sd 1:0:0:0: [sda] Write Protect is off
[   26.840095] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.840139] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   26.840381] sd 1:0:0:0: [sda] 7815024 512-byte hardware sectors (4001 MB)
[   26.840495] sd 1:0:0:0: [sda] Write Protect is off
[   26.840580] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.840621] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   26.840754]  sda: sda1 sda2 sda3 sda4
[   26.842086] sd 1:0:0:0: [sda] Attached SCSI disk
[   26.859656] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   26.884943] usbcore: registered new interface driver libusual
[   26.897986] Initializing USB Mass Storage driver...
[   26.906002] scsi2 : SCSI emulation for USB Mass Storage devices
[   26.912135] usbcore: registered new interface driver usb-storage
[   26.912240] USB Mass Storage support registered.
[   26.912538] usb-storage: device found at 2
[   26.912544] usb-storage: waiting for device to settle before scanning
[   27.091434] Clocksource tsc unstable (delta = -70191854508 ns)
[   27.095423] Time: hpet clocksource has been installed.
[   27.186458] usb-storage: device scan complete
[   27.186934] scsi 2:0:0:0: Direct-Access     USB2.0   CardReader SD0   0100 PQ: 0 ANSI: 0
[   27.430592] sd 2:0:0:0: [sdb] 31388672 512-byte hardware sectors (16071 MB)
[   27.431088] sd 2:0:0:0: [sdb] Write Protect is off
[   27.431178] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   27.431190] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   27.432837] sd 2:0:0:0: [sdb] 31388672 512-byte hardware sectors (16071 MB)
[   27.433323] sd 2:0:0:0: [sdb] Write Protect is off
[   27.433410] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   27.433421] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   27.433513]  sdb: sdb1 sdb2
[   27.434914] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   27.435106] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   27.617841] Attempting manual resume
[   27.617925] swsusp: Resume From Partition 8:18
[   27.617930] PM: Checking swsusp image.
[   27.618807] PM: Resume from disk failed.[/B]
[   36.127137] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.192086] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.376439] Linux agpgart interface v0.102
[   36.433648] agpgart: Detected an Intel 915GM Chipset.
[   36.434137] agpgart: Detected 7932K stolen memory.
[   36.690949] iTCO_vendor_support: vendor-support=0
[   36.752235] agpgart: AGP aperture is 256M @ 0xd0000000
[   36.752478] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   36.752799] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[   36.752988] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   37.770716] intel_rng: FWH not detected
[   38.582943] input: Power Button (FF) as /devices/virtual/input/input2
[   38.598072] ACPI: Power Button (FF) [PWRF]
[   38.598466] input: Lid Switch as /devices/virtual/input/input3
[   38.605634] ACPI: Lid Switch [LID]
[   38.605945] input: Sleep Button (CM) as /devices/virtual/input/input4
[   38.618540] ACPI: Sleep Button (CM) [SLPB]
[   38.618913] input: Power Button (CM) as /devices/virtual/input/input5
[   38.630524] ACPI: Power Button (CM) [PWRB]
[   41.459410] ACPI: AC Adapter [AC0] (off-line)
[   41.591034] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   41.601929] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   44.005503] Attansic(R) L2 Ethernet Network Driver - version 1.0.40.2
[   44.005610] Copyright (c) 2006 Attansic Corporation.
[   44.006891] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   44.007077] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   44.112820] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.113040] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   44.204886] ACPI: Battery Slot [BAT0] (battery present)
[   45.105594] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   48.102777] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04753/0x200000
[   48.187898] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   52.171978] lp: driver loaded but no devices found
[   52.667235] Adding 144576k swap on /dev/sdb2.  Priority:-1 extents:1 across:144576k
[   52.760721] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[   53.794087] ip_tables: (C) 2000-2006 Netfilter Core Team
[   55.123172] No dock devices found.
[   57.431537] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   57.431550] apm: overridden by ACPI.
[   57.629720] ppdev: user-space parallel port driver
[   57.681975] audit(1212319332.426:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5306 profile="/usr/sbin/cupsd" namespace="default"
[   59.309744] Bluetooth: Core ver 2.11
[   59.314201] NET: Registered protocol family 31
[   59.314212] Bluetooth: HCI device and connection manager initialized
[   59.314225] Bluetooth: HCI socket layer initialized
[   59.393054] Bluetooth: L2CAP ver 2.9
[   59.393065] Bluetooth: L2CAP socket layer initialized
[   59.541631] Bluetooth: RFCOMM socket layer initialized
[   59.542652] Bluetooth: RFCOMM TTY layer initialized
[   59.542664] Bluetooth: RFCOMM ver 1.8
[   62.535615] [drm] Initialized drm 1.1.0 20060810
[   62.546363] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   62.546385] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   62.548791] [drm] Initialized i915 1.6.0 20060119 on minor 0
[B][   68.892844] gnome-keyring-d[5836]: segfault at 00000014 eip 080759c7 esp bffe2e00 error 6
[   70.263854] gnome-keyring-d[5942]: segfault at 00000014 eip 080759c7 esp b7a36dc0 error 6[/B]
[   70.898394] NET: Registered protocol family 10
[   70.899837] lo: Disabled Privacy Extensions
[   70.901540] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by weblordpepe on 2008-05-31
Bump! :(

---

### Post by prshah on 2008-06-03
> **weblordpepe said:**
> 
Asus EEE PC, with Ubuntu 8.08 and GRUB installed on the SD card.

[code][   27.617925] swsusp: Resume From Partition 8:18
[   27.617930] PM: Checking swsusp image.
[   27.618807] PM: Resume from disk failed.[/B]

[B][   68.892844] gnome-keyring-d[5836]: segfault at 00000014 eip 080759c7 esp bffe2e00 error 6
[   70.263854] gnome-keyring-d[5942]: segfault at 00000014 eip 080759c7 esp b7a36dc0 error 6[/B]


Known bug.. see [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434) for details and fix (Comment #58 by nyamap) (slightly convoluted, but easy for someone whose played around with the recovery console!).

---

