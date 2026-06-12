---
title: "Kubuntu freeze"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by nimeshchandran on 2007-11-09
helo guys i installed kubuntu 7.04 on my p4 2.8 Ghz system.... the problem is whenever i boot up the system i got to wait at the splash screen showing the kubuntu logo with a liitle bit of the blue bar filled...i got to wait for about 4 minutes after which the booting process continues normally.... i can work just fine ones i log in.... but the waiting for the thing to load is frustrating... i typed in dmesg to find the messages at boot time here is the result...

> [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2
(Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.2
7-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 en
d: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 en
d: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e6000 size: 000000000001a000 en
d: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fe2fc00 en
d: 000000002ff2fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002ff2fc00 size: 0000000000000400 en
d: 000000002ff30000 type: 4
[    0.000000] copy_e820_map() start: 000000002ff30000 size: 0000000000010000 en
d: 000000002ff40000 type: 3
[    0.000000] copy_e820_map() start: 000000002ff40000 size: 00000000000b0000 en
d: 000000002fff0000 type: 4
[    0.000000] copy_e820_map() start: 000000002fff0000 size: 0000000000010000 en
d: 0000000030000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fecf0000 size: 0000000000001000 en
d: 00000000fecf1000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000080000 en
d: 00000000feda0000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ff2fc00 (usable)
[    0.000000]  BIOS-e820: 000000002ff2fc00 - 000000002ff30000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff30000 - 000000002ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ff40000 - 000000002fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fff0000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 196399) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196399
[    0.000000]   HighMem    196399 ->   196399
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196399
[    0.000000] On node 0 totalpages: 196399
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1502 pages used for memmap
[    0.000000]   Normal zone: 190801 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f
61b0
[    0.000000] ACPI: RSDT (v001 INTEL  D865GBF  0x20040622 MSFT 0x00000097) @ 0x
2ff30000
[    0.000000] ACPI: FADT (v002 INTEL  D865GBF  0x20040622 MSFT 0x00000097) @ 0x
2ff30200
[    0.000000] ACPI: MADT (v001 INTEL  D865GBF  0x20040622 MSFT 0x00000097) @ 0x
2ff30300
[    0.000000] ACPI: ASF! (v016 LEGEND I865PASF 0x00000001 MSFT 0x0100000d) @ 0x
2ff345b0
[    0.000000] ACPI: TCPA (v001 INTEL  TBLOEMID 0x00000001 MSFT 0x00000097) @ 0x
2ff34649
[    0.000000] ACPI: WDDT (v001 INTEL  OEMWDDT  0x00000001 MSFT 0x0100000d) @ 0x
2ff3467d
[    0.000000] ACPI: DSDT (v001 INTEL  D865GBF  0x00000001 MSFT 0x0100000d) @ 0x
00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cecf
0000)
[    0.000000] Detected 2793.362 MHz processor.
[   23.416306] Built 1 zonelists.  Total pages: 194865
[   23.416311] Kernel command line: root=UUID=98241a0e-d620-452d-8f3f-b729a1a652
7c ro quiet splash
[   23.416476] mapped APIC to ffffd000 (fee00000)
[   23.416480] mapped IOAPIC to ffffc000 (fec00000)
[   23.416483] Enabling fast FPU save and restore... done.
[   23.416486] Enabling unmasked SIMD FPU exception support... done.
[   23.416498] Initializing CPU#0
[   23.416574] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   23.418628] Console: colour VGA+ 80x25
[   23.419194] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.419753] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.432896] Memory: 767296k/785596k available (1992k kernel code, 17660k rese
rved, 893k data, 328k init, 0k highmem)
[   23.432907] virtual kernel memory layout:
[   23.432908]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   23.432909]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.432910]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   23.432911]     lowmem  : 0xc0000000 - 0xeff2f000   ( 767 MB)
[   23.432913]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   23.432914]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   23.432915]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   23.432918] Checking if this processor honours the WP bit even in supervisor
mode... Ok.
[   23.512426] Calibrating delay using timer specific routine.. 5590.86 BogoMIPS
 (lpj=11181738)
[   23.512470] Security Framework v1.0.0 initialized
[   23.512475] SELinux:  Disabled at boot.
[   23.512493] Mount-cache hash table entries: 512
[   23.512637] CPU: After generic identify, caps: bfebfbff 00000000 00000000 000
00000 0000041d 00000000 00000000
[   23.512647] monitor/mwait feature present.
[   23.512649] using mwait in idle threads.
[   23.512656] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.512659] CPU: L2 cache: 1024K
[   23.512662] CPU: Physical Processor ID: 0
[   23.512665] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0
000041d 00000000 00000000
[   23.512676] Compat vDSO mapped to ffffe000.
[   23.512680] Remapping vsyscall page to ffffe000
[   23.512696] Checking 'hlt' instruction... OK.
[   23.528492] SMP alternatives: switching to UP code
[   23.528832] Early unpacking initramfs... done
[   23.826996] ACPI: Core revision 20060707
[   23.827704] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found,
using machine DSDT.
[   23.829970] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[   23.829994] SMP alternatives: switching to SMP code
[   23.830136] Booting processor 1/1 eip 3000
[   23.840525] Initializing CPU#1
[   23.919772] Calibrating delay using timer specific routine.. 5586.87 BogoMIPS
 (lpj=11173746)
[   23.919783] CPU: After generic identify, caps: bfebfbff 00000000 00000000 000
00000 0000041d 00000000 00000000
[   23.919790] monitor/mwait feature present.
[   23.919798] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.919801] CPU: L2 cache: 1024K
[   23.919804] CPU: Physical Processor ID: 0
[   23.919807] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0
000041d 00000000 00000000
[   23.920093] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[   23.920139] Total of 2 processors activated (11177.74 BogoMIPS).
[   23.920271] ENABLING IO-APIC IRQs
[   23.920454] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.067548] checking TSC synchronization across 2 CPUs: passed.
[    0.003990] Brought up 2 CPUs
[    0.146055] migration_cost=119
[    0.146387] Booting paravirtualized kernel on bare hardware
[    0.146472] Time: 17:46:19  Date: 10/09/107
[    0.146506] NET: Registered protocol family 16
[    0.146610] EISA bus registered
[    0.146616] ACPI: bus type pci registered
[    0.148003] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.148006] PCI: Using configuration type 1
[    0.148008] Setting up standard PCI resources
[    0.163743] ACPI: Interpreter enabled
[    0.163747] ACPI: Using IOAPIC for interrupt routing
[    0.164174] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.164185] PCI: Probing PCI hardware (bus 00)
[    0.164812] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.164816] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[    0.165114] Boot video device is 0000:01:00.0
[    0.165287] PCI: Transparent bridge - 0000:00:1e.0
[    0.165317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.167286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.167923] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.172360] ACPI: Power Resource [URP1] (off)
[    0.172444] ACPI: Power Resource [FDDP] (off)
[    0.172529] ACPI: Power Resource [LPTP] (off)
[    0.173809] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15
)
[    0.174205] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15
)
[    0.174599] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15
)
[    0.174989] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15
)
[    0.175381] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15)
 *0, disabled.
[    0.175783] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15)
 *0, disabled.
[    0.176176] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15)
 *0, disabled.
[    0.176572] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15
)
[    0.176980] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.176994] pnp: PnP ACPI init
[    0.181116] pnp: PnP ACPI: found 14 devices
[    0.181122] PnPBIOS: Disabled by ACPI PNP
[    0.181184] PCI: Using ACPI for IRQ routing
[    0.181188] PCI: If a device doesn't work, try "pci=routeirq".  If it helps,
post a report
[    0.185042] NET: Registered protocol family 8
[    0.185045] NET: Registered protocol family 20
[    0.185899] pnp: 00:0c: ioport range 0x400-0x47f could not be reserved
[    0.185903] pnp: 00:0c: ioport range 0x680-0x6ff has been reserved
[    0.185906] pnp: 00:0c: ioport range 0x500-0x53f has been reserved
[    0.186310] PCI: Bridge: 0000:00:01.0
[    0.186313]   IO window: disabled.
[    0.186318]   MEM window: fa900000-fe9fffff
[    0.186323]   PREFETCH window: ba800000-da7fffff
[    0.186328] PCI: Bridge: 0000:00:1e.0
[    0.186331]   IO window: b000-bfff
[    0.186337]   MEM window: fea00000-feafffff
[    0.186341]   PREFETCH window: disabled.
[    0.186359] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.186394] NET: Registered protocol family 2
[    0.223710] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.223887] TCP established hash table entries: 131072 (order: 8, 1048576 byt
es)
[    0.224562] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.225052] TCP: Hash tables configured (established 131072 bind 65536)
[    0.225056] TCP reno registered
[    0.239788] checking if image is initramfs... it is
[    0.832971] Freeing initrd memory: 6993k freed
[    0.833684] audit: initializing netlink socket (disabled)
[    0.833700] audit(1194630379.564:1): initialized
[    0.833908] VFS: Disk quotas dquot_6.5.1
[    0.833931] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.833991] io scheduler noop registered
[    0.833995] io scheduler anticipatory registered
[    0.833998] io scheduler deadline registered
[    0.834013] io scheduler cfq registered (default)
[    0.834321] isapnp: Scanning for PnP cards...
[    1.187513] isapnp: No Plug & Play device found
[    1.217764] Real Time Clock Driver v1.12ac
[    1.217833] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
[    1.217947] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.218743] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.218942] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ
 16
[    1.219247] 0000:02:03.0: ttyS1 at I/O 0xb808 (irq = 16) is a 16450
[    1.219428] 0000:02:03.0: ttyS2 at I/O 0xb810 (irq = 16) is a 8250
[    1.219604] 0000:02:03.0: ttyS3 at I/O 0xb818 (irq = 16) is a 16450
[    1.219679] Couldn't register serial port 0000:02:03.0: -28
[    1.219759] mice: PS/2 mouse device common for all mice
[    1.220493] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[    1.220673] input: Macintosh mouse button emulation as /class/input/input0
[    1.220719] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.220724] ide: Assuming 33MHz system bus speed for PIO modes; override with
 idebus=xx
[    1.220986] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq
 1,12
[    1.223990] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.223997] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.224129] EISA: Probing bus 0 at eisa.0
[    1.224173] EISA: Detected 0 cards.
[    1.254221] TCP cubic registered
[    1.254232] NET: Registered protocol family 1
[    1.254260] Starting balanced_irq
[    1.254269] Using IPI No-Shortcut mode
[    1.254363] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.254461] ACPI: (supports S0 S1 S4 S5)
[    1.254519]   Magic number: 15:744:794
[    1.254653]   hash matches device ptyr2
[    1.254954] Freeing unused kernel memory: 328k freed
[    1.257974] Time: tsc clocksource has been installed.
[    2.487808] Capability LSM initialized
[    2.533147] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.533168] ACPI: Processor [CPU2] (supports 8 throttling states)
[    3.033802] usbcore: registered new interface driver usbfs
[    3.033835] usbcore: registered new interface driver hub
[    3.052689] usbcore: registered new device driver usb
[    3.054200] USB Universal Host Controller Interface driver v3.0
[    3.054269] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ
 17
[    3.054285] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.054291] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.054443] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus numbe
r 1
[    3.054474] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000cc00
[    3.054628] usb usb1: configuration #1 chosen from 1 choice
[    3.054676] hub 1-0:1.0: USB hub found
[    3.054685] hub 1-0:1.0: 2 ports detected
[    3.155134] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ
 16
[    3.155151] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.155158] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.155196] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus numbe
r 2
[    3.155234] uhci_hcd 0000:00:1d.1: irq 16, io base 0x0000d000
[    3.155370] usb usb2: configuration #1 chosen from 1 choice
[    3.155410] hub 2-0:1.0: USB hub found
[    3.155420] hub 2-0:1.0: 2 ports detected
[    3.192155] Floppy drive(s): fd0 is 1.44M
[    3.240875] FDC 0 is a National Semiconductor PC87306
[    3.258950] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ
 18
[    3.258968] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.258974] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.259016] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus numbe
r 3
[    3.259047] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    3.259210] usb usb3: configuration #1 chosen from 1 choice
[    3.259273] hub 3-0:1.0: USB hub found
[    3.259286] hub 3-0:1.0: 2 ports detected
[    3.362720] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ
 17
[    3.362737] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.362743] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.362785] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus numbe
r 4
[    3.362811] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000d800
[    3.362982] usb usb4: configuration #1 chosen from 1 choice
[    3.363037] hub 4-0:1.0: USB hub found
[    3.363050] hub 4-0:1.0: 2 ports detected
[    3.479716] SCSI subsystem initialized
[    3.488783] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ
 19
[    3.488804] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.488811] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.488870] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus numbe
r 5
[    3.488925] ehci_hcd 0000:00:1d.7: debug port 1
[    3.488934] PCI: cache line size of 128 is not supported by device 0000:00:1d
.7
[    3.488949] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebffc00
[    3.492840] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec
2004
[    3.492999] usb usb5: configuration #1 chosen from 1 choice
[    3.493048] hub 5-0:1.0: USB hub found
[    3.493062] hub 5-0:1.0: 8 ports detected
[    3.498402] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.517356] libata version 2.20 loaded.
[    3.594754] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.594782] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.594796] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ
 18
[    3.594826] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.594914] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000
1ffa0 irq 14
[    3.594962] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x000
1ffa8 irq 15
[    3.594986] scsi0 : ata_piix
[    3.798331] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488
397168
[    3.798337] ata1.00: ATA-7: ST3250820AV, 3.ACG, max UDMA/100
[    3.798340] ata1.00: 488397168 sectors, multi 16: LBA48
[    3.798345] ata1.00: limited to UDMA/33 due to 40-wire cable
[    3.864853] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488
397168
[    3.864858] ata1.00: configured for UDMA/33
[    3.864871] scsi1 : ata_piix
[    4.253178] usb 2-1: new full speed USB device using uhci_hcd and address 3
[    4.345224] ata2.00: ATAPI, max UDMA/33
[    4.345229] ata2.01: ATAPI, max UDMA/66
[    4.424078] usb 2-1: configuration #1 chosen from 1 choice
[    4.508965] ata2.00: configured for UDMA/33
[    4.672784] ata2.01: configured for UDMA/66
[    4.672936] scsi 0:0:0:0: Direct-Access     ATA      ST3250820AV      3.AC PQ
: 0 ANSI: 5
[   10.167730] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   10.167743] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 d
ata 36 in
[   10.167746]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeo
ut)
[   17.176487] ata2: port is slow to respond, please be patient (Status 0xd0)
[   40.159609] ata2: port failed to respond (30 secs, Status 0xd0)
[   40.159618] ata2: soft resetting port
[   40.834729] ata2.00: configured for UDMA/33
[   41.006626] ata2.01: configured for UDMA/66
[   41.006646] ata2: EH complete
[   46.501477] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   46.501487] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 d
ata 36 in
[   46.501488]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeo
ut)
[   53.494263] ata2: port is slow to respond, please be patient (Status 0xd0)
[   76.473391] ata2: port failed to respond (30 secs, Status 0xd0)
[   76.473400] ata2: soft resetting port
[   77.136526] ata2.00: configured for UDMA/33
[   77.308340] ata2.01: configured for UDMA/66
[   77.308359] ata2: EH complete
[   82.803271] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   82.803281] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 d
ata 36 in
[   82.803282]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeo
ut)
[   89.796065] ata2: port is slow to respond, please be patient (Status 0xd0)
[  112.775195] ata2: port failed to respond (30 secs, Status 0xd0)
[  112.775205] ata2: soft resetting port
[  113.430337] ata2.00: configured for UDMA/33
[  113.598154] ata2.01: configured for UDMA/66
[  113.598174] ata2: EH complete
[  119.093097] ata2.00: limiting speed to UDMA/25:PIO4
[  119.093102] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  119.093110] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 d
ata 36 in
[  119.093112]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeo
ut)
[  126.085886] ata2: port is slow to respond, please be patient (Status 0xd0)
[  149.065014] ata2: port failed to respond (30 secs, Status 0xd0)
[  149.065023] ata2: soft resetting port
[  149.720159] ata2.00: configured for UDMA/25
[  149.887983] ata2.01: configured for UDMA/66
[  149.888017] ata2: EH complete
[  149.889352] scsi 1:0:1:0: CD-ROM            SONY     DVD RW DRU-820A  1.0b PQ
: 0 ANSI: 5
[  149.889595] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[  149.889618] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ
 18
[  149.889648] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  149.889709] ata3: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e802 bmdma 0x000
1dc00 irq 18
[  149.889757] ata4: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x000
1dc08 irq 18
[  149.889773] scsi2 : ata_piix
[  150.058158] ATA: abnormal status 0x7F on port 0x0001ec07
[  150.058175] scsi3 : ata_piix
[  150.225892] ATA: abnormal status 0x7F on port 0x0001e407
[  150.240163] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[  150.240189] sda: Write Protect is off
[  150.240193] sda: Mode Sense: 00 3a 00 00
[  150.240233] SCSI device sda: write cache: enabled, read cache: enabled, doesn
't support DPO or FUA
[  150.240353] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[  150.240378] sda: Write Protect is off
[  150.240383] sda: Mode Sense: 00 3a 00 00
[  150.240420] SCSI device sda: write cache: enabled, read cache: enabled, doesn
't support DPO or FUA
[  150.240433]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda1
3 sda14 >
[  150.372974] sd 0:0:0:0: Attached scsi disk sda
[  150.378852] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  150.378884] sr 1:0:1:0: Attached scsi generic sg1 type 5
[  150.382139] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda
tray
[  150.382152] Uniform CD-ROM driver Revision: 3.20
[  150.384100] sr 1:0:1:0: Attached scsi CD-ROM sr0
[  150.997458] Attempting manual resume
[  150.997463] swsusp: Resume From Partition 8:13
[  150.997465] PM: Checking swsusp image.
[  150.997764] PM: Resume from disk failed.
[  151.032076] kjournald starting.  Commit interval 5 seconds
[  151.032085] EXT3-fs: mounted filesystem with ordered data mode.
[  160.437070] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  160.440497] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  160.484359] Linux agpgart interface v0.102 (c) Dave Jones
[  160.488445] agpgart: Detected an Intel 865 Chipset.
[  160.499800] agpgart: AGP aperture is 256M @ 0xe0000000
[  160.603224] iTCO_vendor_support: vendor-support=0
[  160.653793] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  160.661987] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x
0460)
[  160.667204] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  160.691504] intel_rng: Firmware space is locked read-only. If you can't or
[  160.691508] intel_rng: don't want to disable this in firmware setup, and if
[  160.691510] intel_rng: you are certain that your system has a functional
[  160.691512] intel_rng: RNG, try using the 'no_fwh_detect' option.
[  161.206115] parport: PnPBIOS parport detected.
[  161.206170] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  161.425920] input: PC Speaker as /class/input/input2
[  161.538184] nvidia: module license 'NVIDIA' taints kernel.
[  161.584102] eth0: register 'cdc_ether' at usb-0000:00:1d.1-1, CDC Ethernet De
vice, 00:17:ee:6b:03:20
[  161.584119] usbcore: registered new interface driver cdc_ether
[  161.794088] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ
 17
[  161.794309] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26
 23:21:15 PST 2007
[  161.912763] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[  162.066159] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ
 20
[  162.066200] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  162.391654] intel8x0_measure_ac97_clock: measured 59283 usecs
[  162.391658] intel8x0: clocking to 48000
[  162.521766] fuse init (API version 7.8)
[  162.535583] lp0: using parport0 (interrupt-driven).
[  162.571817] Adding 891568k swap on /dev/disk/by-uuid/33cdc1a7-7731-4fe5-8a36-
59de362976b8.  Priority:-1 extents:1 across:891568k
[  162.962662] EXT3 FS on sda14, internal journal
[  163.053819] NET: Registered protocol family 17
[  163.785333] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  163.845350] NTFS volume version 3.1.
[  163.951683] NET: Registered protocol family 10
[  163.951832] lo: Disabled Privacy Extensions
[  169.341970] input: Power Button (FF) as /class/input/input4
[  169.342014] ACPI: Power Button (FF) [PWRF]
[  169.342110] input: Sleep Button (CM) as /class/input/input5
[  169.342145] ACPI: Sleep Button (CM) [SLPB]
[  169.563190] Using specific hotkey driver
[  169.627131] ibm_acpi: ec object not found
[  169.692223] No dock devices found.
[  169.768332] pcc_acpi: loading...
[  172.588657] serial8250: too much work for irq16
[  172.589653] serial8250: too much work for irq16
[  174.296568] eth0: no IPv6 routers present
[  174.638850] ppdev: user-space parallel port driver
[  175.266113] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  175.266120] apm: disabled - APM is not SMP safe.
[  175.789183] Bluetooth: Core ver 2.11
[  175.789448] NET: Registered protocol family 31
[  175.789454] Bluetooth: HCI device and connection manager initialized
[  175.789462] Bluetooth: HCI socket layer initialized
[  175.823817] Bluetooth: L2CAP ver 2.8
[  175.823823] Bluetooth: L2CAP socket layer initialized
[  175.959420] Bluetooth: RFCOMM socket layer initialized
[  175.959862] Bluetooth: RFCOMM TTY layer initialized
[  175.959868] Bluetooth: RFCOMM ver 1.8
[  177.329729] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  177.329759] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  177.329834] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  189.987405] eth0: no IPv6 routers present
[ 4238.735488] NVRM: Xid (0001:00): 34
[ 7979.145173] NVRM: Xid (0001:00): 34
[ 7979.152688] NVRM: Xid (0001:00): 34
[ 7979.164787] NVRM: Xid (0001:00): 34




what can be the reason...some said its because of teh hard disk..well my hdd is 250GB seagate PATA hard disk.. i checked the partition thoroughly using seagate seatools for both windows and dos and even tried at boot time using usb booting and it returned no errors.. i checked the hdd with partition table doctor and it also returned no errors..so what should i do???

---

### Post by dabl on 2007-11-09
I don't see an obvious problem in your dmesg output.  Maybe it is some process (like fsck) that is happening during the bootup that just takes a long time.  Does it do the same thing if you boot recovery mode?  If you boot recovery mode and watch it, you should be able to observe the point where it stops and waits a long while.  :)

---

### Post by Pumalite on 2007-11-09
What are your comp specs and what iso did you use?
Also: [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x.
If you have ATI or integrated graphics you better install with Alternate CD.

---

### Post by nimeshchandran on 2007-11-09
hello guys the same problem persists in safe mode too...well about the image, i installed the kubuntu from the free cd that i got through ship-it...  the same problem exists with ubuntu 7.04... well if u notice the delay occurs from the point in dmesg [ 10.167730].... after that the error happens again and again.....

about my pc configuration...
p4 2.8GHz HT
250GB seagate PATA HDD
768 MB RAM DDR400
Intel D865GBF motherboard
GeForce 7600GS
Sony DRU820 DVD writer
LG CD writer
500w SMPS
got Windows XP SP2 in dual boot using acronis boot loader

---

### Post by griblik on 2007-11-10
I had something similar happening with a sata drive - try adding irqpoll as a boot option.

In grub, edit the boot option (there's a key to press in the grub menu - e? - it says which one at the bottom of the menu), go down to the kernel line and add "irqpoll" to the end of it. Hit B and you should boot.

HTH

G

---

### Post by nimeshchandran on 2007-11-10
hey adding irqpoll didnt help me out :(
but i worked it out..the culprit was the lg cd writer...i disconnected it and everyuthing is just fine now... thanks man for the tips.. thanks

---

### Post by kiev on 2008-05-24
kernel bug? [http://ubuntuforums.org/showthread.php?p=5031353](http://ubuntuforums.org/showthread.php?p=5031353)

---

