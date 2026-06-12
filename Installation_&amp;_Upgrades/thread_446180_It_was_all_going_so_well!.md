---
title: "It was all going so well!"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by blop on 2007-05-16
HEY ALL!

really really really need some help...

have just been setting up my Toshiba p200-155 with a fresh install of Kubuntu 7.04. it installed fine picked up most of the hardware ok and i was even able to get the nvidia drivers on to it fairly easily.....but then my luck ran out.

my sound card is being a bit quite......as in no sound at all..

i did some searching and i came up with this guide which i worked through but it did not help much. i can tell i have a sound card and it seems to of given it a driver but it doesnt work

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_alsamixer](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_alsamixer)

any help appreciated! :)

---

### Post by blop on 2007-05-16
bump

---

### Post by blop on 2007-05-17
bump o matic

please help!

---

### Post by blop on 2007-05-17
pppppplllllllleeeeeeaaaaaassssseeeeeee help

---

### Post by dkulchenko on 2007-05-17
STOP bumping your post. It is very annoying. If someone comes along who knows, they will answer.

---

### Post by bapoumba on 2007-05-17
@ dkulchenko: there is so much traffic here, that bumping once or twice a day is fine :)
@ blop: please go back to your first post and edit the thread title to something more appropriate, with your sound card specs. "Problem installing xxx" for ex.

---

### Post by digitalbenji on 2007-05-17
I had a similar problem to this.  The soundcard was installed, showed up in lspci and dmesg, and the sound daemon was running.  Then I checked the volume settings on the software panel.  Boom, one of the volume sliders was all the way down.

Take a look at the mixer, and see if this isn't the cause.

If that doesn't help, please post the contents of a dmesg and an lspci

Thanks

---

### Post by blop on 2007-05-17
cheers for the help..

i did try and be as sure as i was that is was not a volume issue before i posted im fairly confident he says..

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by blop on 2007-05-17
dmesg

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fd80000 end: 000000007fe80000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fe80000 size: 0000000000080000 end: 000000007ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000007ff00000 size: 0000000000100000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe80000 (usable)
[    0.000000]  BIOS-e820: 000000007fe80000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7670
[    0.000000] Entering add_active_range(0, 0, 523904) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523904
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523904
[    0.000000] On node 0 totalpages: 523904
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292227 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f75e0
[    0.000000] ACPI: RSDT (v001 TOSCPL TOSCPL00 0x06040000  LTP 0x00000000) @ 0x7fe877a8
[    0.000000] ACPI: FADT (v001 TOSCPL CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7fe8fc78
[    0.000000] ACPI: SLIC (v001 TOSCPL TOSCPL00 0x06040000 LOHR 0x00000000) @ 0x7fe8fcec
[    0.000000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7fe8fe62
[    0.000000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7fe8feca
[    0.000000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7fe8ff02
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x7fe8ffd8
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x7fe8ff70
[    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20050624) @ 0x7fe88ec0
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20050624) @ 0x7fe8882e
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Tst 0x00003000 INTL 0x20050624) @ 0x7fe87d88
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu1Tst 0x00003000 INTL 0x20050624) @ 0x7fe87ce2
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x7fe877fc
[    0.000000] ACPI: DSDT (v001 TOSCPL CALISTGA 0x06040000 INTL 0x20060608) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Detected 1729.215 MHz processor.
[   28.114551] Built 1 zonelists.  Total pages: 519811
[   28.114555] Kernel command line: root=UUID=4ff31e88-d55d-431b-920a-9827aa844be8 ro quiet splash
[   28.114695] mapped APIC to ffffd000 (fee00000)
[   28.114697] mapped IOAPIC to ffffc000 (fec00000)
[   28.114700] Enabling fast FPU save and restore... done.
[   28.114702] Enabling unmasked SIMD FPU exception support... done.
[   28.114710] Initializing CPU#0
[   28.114783] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   28.118314] Console: colour VGA+ 80x25
[   28.118647] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.118965] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.192986] Memory: 2066276k/2095616k available (1992k kernel code, 27932k reserved, 893k data, 328k init, 1178112k highmem)
[   28.192995] virtual kernel memory layout:
[   28.192996]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.192997]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.192998]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   28.192999]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.193001]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   28.193002]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   28.193003]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   28.193006] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.193180] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   28.193186] hpet0: 3 64-bit timers, 14318180 Hz
[   28.194192] Using HPET for base-timer
[   28.273150] Calibrating delay using timer specific routine.. 3462.09 BogoMIPS (lpj=6924197)
[   28.273193] Security Framework v1.0.0 initialized
[   28.273201] SELinux:  Disabled at boot.
[   28.273216] Mount-cache hash table entries: 512
[   28.273358] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   28.273366] monitor/mwait feature present.
[   28.273367] using mwait in idle threads.
[   28.273371] CPU: L1 I cache: 32K, L1 D cache: 32K
[   28.273374] CPU: L2 cache: 2048K
[   28.273376] CPU: Physical Processor ID: 0
[   28.273378] CPU: Processor Core ID: 0
[   28.273379] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   28.273389] Compat vDSO mapped to ffffe000.
[   28.273394] Remapping vsyscall page to ffffe000
[   28.273406] Checking 'hlt' instruction... OK.
[   28.289252] SMP alternatives: switching to UP code
[   28.289625] Early unpacking initramfs... done
[   28.605858] ACPI: Core revision 20060707
[   28.606147] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   28.615467] CPU0: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz stepping 02
[   28.615485] SMP alternatives: switching to SMP code
[   28.615569] Booting processor 1/1 eip 3000
[   28.626001] Initializing CPU#1
[   28.704968] Calibrating delay using timer specific routine.. 3458.14 BogoMIPS (lpj=6916285)
[   28.704974] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   28.704979] monitor/mwait feature present.
[   28.704982] CPU: L1 I cache: 32K, L1 D cache: 32K
[   28.704984] CPU: L2 cache: 2048K
[   28.704986] CPU: Physical Processor ID: 0
[   28.704987] CPU: Processor Core ID: 1
[   28.704989] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   28.705421] CPU1: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz stepping 02
[   28.705443] Total of 2 processors activated (6920.24 BogoMIPS).
[   28.705643] ENABLING IO-APIC IRQs
[   28.705845] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.852908] checking TSC synchronization across 2 CPUs: passed.
[    0.003998] Brought up 2 CPUs
[    0.114546] migration_cost=36
[    0.114803] Booting paravirtualized kernel on bare hardware
[    0.114902] Time: 17:47:23  Date: 04/17/107
[    0.114930] NET: Registered protocol family 16
[    0.115012] EISA bus registered
[    0.115019] ACPI: bus type pci registered
[    0.115135] PCI: BIOS BUG #81[49435000] found
[    0.115205] PCI: Using configuration type 1
[    0.115207] Setting up standard PCI resources
[    0.124841] ACPI: Interpreter enabled
[    0.124843] ACPI: Using IOAPIC for interrupt routing
[    0.125300] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.125304] PCI: Probing PCI hardware (bus 00)
[    0.126691] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.126695] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.126953] Boot video device is 0000:01:00.0
[    0.128039] PCI: Transparent bridge - 0000:00:1e.0
[    0.128113] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#06) (try 'pci=assign-busses')
[    0.128115] Please report the result to linux-kernel to fix this permanently
[    0.128196] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.134707] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.135516] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.135760] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.136098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.136916] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.137648] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.137884] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.138127] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.138362] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.138596] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.138831] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.139067] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.139301] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.188619] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.188628] pnp: PnP ACPI init
[    0.220072] pnp: PnP ACPI: found 10 devices
[    0.220075] PnPBIOS: Disabled by ACPI PNP
[    0.220112] PCI: Using ACPI for IRQ routing
[    0.220115] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.220234] NET: Registered protocol family 8
[    0.220236] NET: Registered protocol family 20
[    0.220460] pnp: 00:01: ioport range 0xfe00-0xfe7f has been reserved
[    0.220463] pnp: 00:01: ioport range 0xfe80-0xfeff has been reserved
[    0.220466] pnp: 00:01: ioport range 0xff00-0xff7f has been reserved
[    0.220748] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
[    0.220821] PCI: Bridge: 0000:00:01.0
[    0.220823]   IO window: 2000-2fff
[    0.220827]   MEM window: dc000000-ddffffff
[    0.220831]   PREFETCH window: c0000000-cfffffff
[    0.220835] PCI: Bridge: 0000:00:1c.0
[    0.220838]   IO window: 3000-3fff
[    0.220844]   MEM window: d6000000-d7ffffff
[    0.220849]   PREFETCH window: d0000000-d1ffffff
[    0.220856] PCI: Bridge: 0000:00:1c.1
[    0.220859]   IO window: 4000-4fff
[    0.220865]   MEM window: d8000000-d9ffffff
[    0.220870]   PREFETCH window: d2000000-d3ffffff
[    0.220876] PCI: Bridge: 0000:00:1c.2
[    0.220879]   IO window: 5000-5fff
[    0.220886]   MEM window: da000000-dbffffff
[    0.220891]   PREFETCH window: d4000000-d5ffffff
[    0.220903] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[    0.220905]   IO window: 00006000-000060ff
[    0.220910]   IO window: 00006400-000064ff
[    0.220916]   PREFETCH window: 88000000-8bffffff
[    0.220921]   MEM window: 8c000000-8fffffff
[    0.220927] PCI: Bridge: 0000:00:1e.0
[    0.220930]   IO window: 6000-6fff
[    0.220936]   MEM window: de000000-de0fffff
[    0.220941]   PREFETCH window: 88000000-8bffffff
[    0.220958] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.220963] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.220988] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    0.220994] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.221018] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    0.221024] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.221049] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.221055] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.221069] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.221086] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.221118] NET: Registered protocol family 2

---

### Post by blop on 2007-05-17
[    0.267927] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.268031] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.268504] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.268762] TCP: Hash tables configured (established 131072 bind 65536)
[    0.268765] TCP reno registered
[    0.283993] checking if image is initramfs... it is
[    0.906644] Freeing initrd memory: 7002k freed
[    0.906835] Simple Boot Flag at 0x36 set to 0x1
[    0.907309] audit: initializing netlink socket (disabled)
[    0.907323] audit(1179424043.644:1): initialized
[    0.907422] highmem bounce pool size: 64 pages
[    0.907511] VFS: Disk quotas dquot_6.5.1
[    0.907530] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.907580] io scheduler noop registered
[    0.907582] io scheduler anticipatory registered
[    0.907584] io scheduler deadline registered
[    0.907595] io scheduler cfq registered (default)
[    0.907854] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.907896] assign_interrupt_mode Found MSI capability
[    0.907899] Allocate Port Service[0000:00:01.0:pcie00]
[    0.907994] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.908055] assign_interrupt_mode Found MSI capability
[    0.908057] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.908093] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.908222] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.908282] assign_interrupt_mode Found MSI capability
[    0.908285] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.908319] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.908447] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.908507] assign_interrupt_mode Found MSI capability
[    0.908510] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.908541] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.908733] isapnp: Scanning for PnP cards...
[    1.263121] isapnp: No Plug & Play device found
[    1.284444] Real Time Clock Driver v1.12ac
[    1.284502] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.285120] mice: PS/2 mouse device common for all mice
[    1.285691] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.285843] input: Macintosh mouse button emulation as /class/input/input0
[    1.285879] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.285882] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.286182] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.286403] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.286479] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.286482] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.286485] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.286487] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.286490] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.286601] EISA: Probing bus 0 at eisa.0
[    1.286608] Cannot allocate resource for EISA slot 1
[    1.286611] Cannot allocate resource for EISA slot 2
[    1.286613] Cannot allocate resource for EISA slot 3
[    1.286615] Cannot allocate resource for EISA slot 4
[    1.286617] Cannot allocate resource for EISA slot 5
[    1.286619] Cannot allocate resource for EISA slot 6
[    1.286629] EISA: Detected 0 cards.
[    1.289068] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.316718] TCP cubic registered
[    1.316727] NET: Registered protocol family 1
[    1.316750] Starting balanced_irq
[    1.316760] Using IPI No-Shortcut mode
[    1.316859] ACPI: (supports S0 S3 S4 S5)
[    1.316905]   Magic number: 7:310:795
[    1.316975]   hash matches device ptyr3
[    1.317201] Freeing unused kernel memory: 328k freed
[    1.319445] Time: tsc clocksource has been installed.
[    2.521117] Capability LSM initialized
[    2.559287] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.559519] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.559867] Monitor-Mwait will be used to enter C-1 state
[    2.559871] Monitor-Mwait will be used to enter C-2 state
[    2.559873] Monitor-Mwait will be used to enter C-3 state
[    2.559879] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.560375] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.560570] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.560977] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.124000] Time: hpet clocksource has been installed.
[    3.456000] usbcore: registered new interface driver usbfs
[    3.456000] usbcore: registered new interface driver hub
[    3.456000] usbcore: registered new device driver usb
[    3.456000] USB Universal Host Controller Interface driver v3.0
[    3.456000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.456000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.456000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.456000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.456000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001800
[    3.456000] usb usb1: configuration #1 chosen from 1 choice
[    3.456000] hub 1-0:1.0: USB hub found
[    3.456000] hub 1-0:1.0: 2 ports detected
[    3.484000] SCSI subsystem initialized
[    3.488000] libata version 2.20 loaded.
[    3.544000] ieee1394: Initialized config rom entry `ip1394'
[    3.560000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.560000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.560000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.560000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.560000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[    3.560000] usb usb2: configuration #1 chosen from 1 choice
[    3.560000] hub 2-0:1.0: USB hub found
[    3.560000] hub 2-0:1.0: 2 ports detected
[    3.664000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.664000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.664000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.664000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.664000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    3.664000] usb usb3: configuration #1 chosen from 1 choice
[    3.664000] hub 3-0:1.0: USB hub found
[    3.664000] hub 3-0:1.0: 2 ports detected
[    3.768000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.768000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.768000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.768000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.768000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    3.768000] usb usb4: configuration #1 chosen from 1 choice
[    3.768000] hub 4-0:1.0: USB hub found
[    3.768000] hub 4-0:1.0: 2 ports detected
[    3.872000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.872000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.028000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.028000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.028000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.028000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15

---

### Post by blop on 2007-05-17
[    4.028000] scsi0 : ata_piix
[    4.192000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    4.192000] ata1.00: ATA-7: TOSHIBA MK1637GSX, DL030M, max UDMA/100
[    4.192000] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.200000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    4.200000] ata1.00: configured for UDMA/100
[    4.200000] scsi1 : ata_piix
[    4.520000] ata2.00: ATAPI, max UDMA/33
[    4.684000] ata2.00: configured for UDMA/33
[    4.684000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL03 PQ: 0 ANSI: 5
[    4.688000] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WT03 PQ: 0 ANSI: 5
[    4.688000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    4.688000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.688000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.688000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.688000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.688000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.688000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xde304000
[    4.692000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.692000] usb usb5: configuration #1 chosen from 1 choice
[    4.692000] hub 5-0:1.0: USB hub found
[    4.692000] hub 5-0:1.0: 8 ports detected
[    4.796000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    4.796000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[    4.796000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[    4.796000] eth0: RTL8101e at 0xf88b4000, 00:16:d4:f6:3f:ab, IRQ 18
[    4.800000] ACPI: PCI Interrupt 0000:06:04.1[B] -> GSI 17 (level, low) -> IRQ 17
[    4.852000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[de005000-de0057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.860000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    4.860000] sda: Write Protect is off
[    4.860000] sda: Mode Sense: 00 3a 00 00
[    4.860000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.860000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    4.860000] sda: Write Protect is off
[    4.860000] sda: Mode Sense: 00 3a 00 00
[    4.860000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.860000]  sda: sda1 sda2 sda3
[    4.912000] sd 0:0:0:0: Attached scsi disk sda
[    4.916000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.916000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.932000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.932000] Uniform CD-ROM driver Revision: 3.20
[    4.932000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.116000] Attempting manual resume
[    5.116000] swsusp: Resume From Partition 8:1
[    5.116000] PM: Checking swsusp image.
[    5.120000] PM: Resume from disk failed.
[    5.144000] kjournald starting.  Commit interval 5 seconds
[    5.144000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.188000] usb 5-6: new high speed USB device using ehci_hcd and address 2
[    5.332000] usb 5-6: configuration #1 chosen from 1 choice
[    6.124000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f74bd400277]
[   13.300000] r8169: eth0: link up
[   13.300000] r8169: eth0: link up
[   14.128000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.180000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.184000] agpgart: Detected an Intel 945GM Chipset.
[   14.200000] agpgart: AGP aperture is 256M @ 0x0
[   14.220000] intel_rng: FWH not detected
[   14.252000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.292000] iTCO_vendor_support: vendor-support=0
[   14.292000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   14.292000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   14.292000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.416000] Yenta: CardBus bridge found at 0000:06:04.0 [1179:ff00]
[   14.416000] Yenta: Enabling burst memory read transactions
[   14.416000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   14.416000] Yenta: Routing CardBus interrupts to PCI
[   14.416000] Yenta TI: socket 0000:06:04.0, mfunc 0x10aa1b22, devctl 0x64
[   14.596000] NET: Registered protocol family 17
[   14.628000] ieee80211_crypt: registered algorithm 'NULL'
[   14.636000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.636000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.648000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   14.648000] Socket status: 30000006
[   14.648000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   14.648000] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
[   14.648000] cs: IO port probe 0x6000-0x6fff: clean.
[   14.648000] pcmcia: parent PCI bridge Memory window: 0xde000000 - 0xde0fffff
[   14.648000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   14.648000] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.652000] sdhci: Secure Digital Host Controller Interface driver
[   14.652000] sdhci: Copyright(c) Pierre Ossman
[   14.652000] sdhci: SDHCI controller found at 0000:06:04.3 [104c:803c] (rev 0)
[   14.652000] ACPI: PCI Interrupt 0000:06:04.3[C] -> GSI 18 (level, low) -> IRQ 18
[   14.652000] mmc0: SDHCI at 0xde005800 irq 18 DMA
[   14.752000] nvidia: module license 'NVIDIA' taints kernel.
[   15.008000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.008000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   15.008000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   15.012000] Linux video capture interface: v2.00
[   15.068000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   15.068000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   15.068000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   15.068000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   15.072000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   15.132000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04713/0x204000
[   15.132000] synaptics: Toshiba Satellite P200 detected, limiting rate to 40pps.
[   15.152000] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   15.152000] usbcore: registered new interface driver uvcvideo
[   15.152000] USB Video Class driver (v0.1.0)
[   15.164000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   15.336000] cs: IO port probe 0x100-0x3af: clean.
[   15.340000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.340000] cs: IO port probe 0x820-0x8ff: clean.
[   15.340000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.340000] cs: IO port probe 0xa00-0xaff: clean.
[   15.388000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   15.388000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.596000] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
[   16.356000] si3054: cannot initialize. EXT MID = 0000
[   16.512000] fuse init (API version 7.8)
[   16.584000] lp: driver loaded but no devices found
[   16.628000] Adding 2048276k swap on /dev/disk/by-uuid/aaf22fe7-5a46-424a-94e2-8249be5e93cf.  Priority:-1 extents:1 across:2048276k
[   17.012000] EXT3 FS on sda2, internal journal
[   17.068000] ipw3945: Max thermal spin reached
[   17.068000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   17.168000] NET: Registered protocol family 10
[   17.168000] lo: Disabled Privacy Extensions
[   22.776000] input: Power Button (FF) as /class/input/input3
[   22.776000] ACPI: Power Button (FF) [PWRF]
[   22.776000] input: Lid Switch as /class/input/input4
[   22.776000] ACPI: Lid Switch [LID0]
[   22.776000] input: Power Button (CM) as /class/input/input5
[   22.776000] ACPI: Power Button (CM) [PWRB]
[   22.820000] ACPI: AC Adapter [ACAD] (on-line)
[   22.908000] No dock devices found.
[   22.984000] ACPI: Battery Slot [BAT1] (battery present)
[   22.988000] ibm_acpi: ec object not found
[   23.016000] Using specific hotkey driver
[   23.048000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   23.048000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   23.092000] pcc_acpi: loading...
[   24.756000] ppdev: user-space parallel port driver
[   25.388000] apm: BIOS not found.
[   25.852000] /dev/vmmon[5235]: Module vmmon: registered with major=10 minor=165
[   25.852000] /dev/vmmon[5235]: Module vmmon: initialized
[   25.956000] /dev/vmnet: open called by PID 5263 (vmnet-bridge)
[   25.956000] /dev/vmnet: hub 0 does not exist, allocating memory.
[   25.956000] /dev/vmnet: port on hub 0 successfully opened
[   25.956000] bridge-eth0: enabling the bridge
[   25.960000] bridge-eth0: up
[   25.960000] bridge-eth0: already up
[   25.960000] bridge-eth0: attached
[   25.980000] /dev/vmnet: open called by PID 5269 (vmnet-netifup)
[   25.980000] /dev/vmnet: hub 1 does not exist, allocating memory.
[   25.980000] /dev/vmnet: port on hub 1 successfully opened
[   25.984000] /dev/vmnet: open called by PID 5277 (vmnet-netifup)
[   25.984000] /dev/vmnet: hub 8 does not exist, allocating memory.
[   25.984000] /dev/vmnet: port on hub 8 successfully opened
[   26.036000] /dev/vmnet: open called by PID 5289 (vmnet-natd)
[   26.036000] /dev/vmnet: port on hub 8 successfully opened
[   26.264000] /dev/vmnet: open called by PID 5297 (vmnet-dhcpd)
[   26.264000] /dev/vmnet: port on hub 1 successfully opened
[   26.264000] /dev/vmnet: open called by PID 5301 (vmnet-dhcpd)
[   26.264000] /dev/vmnet: port on hub 8 successfully opened
[   26.388000] Bluetooth: Core ver 2.11
[   26.388000] NET: Registered protocol family 31
[   26.388000] Bluetooth: HCI device and connection manager initialized
[   26.388000] Bluetooth: HCI socket layer initialized
[   26.416000] Bluetooth: L2CAP ver 2.8
[   26.416000] Bluetooth: L2CAP socket layer initialized
[   26.532000] Bluetooth: RFCOMM socket layer initialized
[   26.532000] Bluetooth: RFCOMM TTY layer initialized
[   26.532000] Bluetooth: RFCOMM ver 1.8
[   36.772000] vmnet1: no IPv6 routers present
[   36.920000] vmnet8: no IPv6 routers present
[   39.332000] eth0: no IPv6 routers present
[   77.568000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
[   78.328000] ipw3945: Radio Frequency Kill Switch is On:
[   78.328000] Kill switch must be turned off for wireless networking to work.

---

### Post by blop on 2007-05-17
bump

---

### Post by digitalbenji on 2007-05-17
Hi,
   In lspci it looks like it recognizes the audio card just fine, which I think means that its got the drivers all set to go.  Try going into the control panel for sound configuration, I forget exactly where it is, but it lets you select which sound architecture to use for which type of media, and see if changing around from ARTs to OSS and such makes it so you can hear sound.  If not, let me know.

Thanks,

---

### Post by digitalbenji on 2007-05-18
In Edgy this is found in System -> Preferences -> Sound

Try using all the different engines and using the Test button to see if you can get any sound.

---

### Post by blop on 2007-05-20
Well i was having a bunch of issues with kubuntu so i did a complete reinstall of ubuntu 7.04 so far it has been less buggy.....less pretty :(.......but a lot less buggy. Installing nvidia drivers was super easy....and i now have beryl working.....but i lost superkaramba.

One thing that is the same is no sound.. :( Although the volume dial on the front of the laptop now actually works correctly before it would only cycle between 0-10% now it does the full range.

Have tried all the sound devices there is six including autodetect.....not a snip from any of them.

Thank you for your continued help!

---

### Post by quickwitt on 2007-05-20
I had a similar problem with Feisty on my Toshiba U205. I used Synaptic to remove all of ALSA, rebooted and reinstalled ALSA and the ALSA mixer GUI.  Then under Sound Preferences confirmed that everything was pointed to ALSA and my device was set to Intel HDA. Everything now works.

---

### Post by blop on 2007-05-20
I opted to do a reinstall within synaptic, instead of a remove reboot reinstallation.....

sadly did not work :(

---

### Post by mostholy on 2007-05-20
try the recompile as detailed here:
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)
The default is muted so you'll need to fix that and perhaps a reboot to find sound functional.

Cheers

---

### Post by blop on 2007-05-21
thanks for the help...

i actually found that link from a post....i did it but now no sound card is detected in System>Admin>Sound. It realises their is a card i think:

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

But im not sure how i get to use it....any help apprecated!!

---

### Post by digitalbenji on 2007-05-22
Are you certain your speakers work?  Are you certain that you don't have a hardware mute on?

---

### Post by blop on 2007-05-22
hi thanks for the reply....

laptop has speakers and headphone out.....both are dead as a dodo....and both work on windows vista....so im sure

i did not have a hardware mute on as i did some looking in alsa mixer...and everything looked ok.

i dont have a sound card setup now after i followed the instructions in the post advising me to do a an install of a recompile of alsa.

---

### Post by digitalbenji on 2007-05-22
Hmm, that's pretty strange.  I would recommend popping in the Feisty LiveCD, or any other distro that has a LiveCD, and see if you can play sound from there.  If you can, you know the problem is just a software misconfiguration or error along those lines.  Let me know if you can hear sound from a LiveCD.

---

### Post by blop on 2007-05-24
I have found out there is a bunch of bug reports referring the problem i and others are experiencing with HDA INTEL sound cards and ubuntu. I was the ubuntu IRC and someone mentioned it was an issue with this kernel some conflict or other....

so i may have to wait for the devs to sort it,...

---

### Post by arijarot on 2007-06-08
> **blop said:**
> I have found out there is a bunch of bug reports referring the problem i and others are experiencing with HDA INTEL sound cards and ubuntu. I was the ubuntu IRC and someone mentioned it was an issue with this kernel some conflict or other....

so i may have to wait for the devs to sort it,...

this site [http://www.linlap.com/wiki/Toshiba+Satellite+P200](http://www.linlap.com/wiki/Toshiba+Satellite+P200) says to use the "snd-hda-intel **driver**" for sound. I don't know if this will help to try it...

---

### Post by DonLorenzo on 2007-06-13
I have a Toshiba P200-ST2071.
This worked for me.

edit the file: /etc/modprobe.d/alsa-base
append to the file:
options snd-hda-intel model=3stack

reboot
you should/may have sound at this point.

Others have reported good results with "model=auto"

---

### Post by Seti on 2007-06-13
And you're sure that  you played around with the alsamixer settings?

```

alsamixer

```

And nothing in there did it??

---

### Post by blop on 2007-07-14
> **DonLorenzo said:**
> I have a Toshiba P200-ST2071.
This worked for me.

edit the file: /etc/modprobe.d/alsa-base
append to the file:
options snd-hda-intel model=3stack

reboot
you should/may have sound at this point.

Others have reported good results with "model=auto"

this did work.... thanks!!

---

