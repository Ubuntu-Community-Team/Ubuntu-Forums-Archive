---
title: "Two errors arising from Lucid Lucy 10.04 upgrade"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2010-05-04
1. On startup I get Error mounting /proc/bus/usb and on skipping that I get the same for SDA1.

*Solution still needed*

2. The skype drop down menu is not reversing the text to White on black. The options are not showing as the background is also black with the text black.

*I have solved this by switching off negative in the accessibility section of Compiz Config manager in the control center under Look and feel.*

I would very much like some help on item 1 above.

Robin

---

### Post by tgalati4 on 2010-05-04
Describe your hardware.  Laptop or desktop.  What kind of processor?  How much memory.  Post the relevant entries from:

dmesg | more

Also:

lsusb -v

and 

lspci -v

---

### Post by Robbyx on 2010-05-04
> **tgalati4 said:**
> Describe your hardware.  

desktop.  

Intel Pentium processor? 4805 (LGA 775 Smithfield)

> How much memory. 3.4Gb per the system monitor 

> Post the relevant entries from:

dmesg | more

```
[    0.234508] pci 0000:00:1c.4:   PREFETCH window: 0xfc700000-0xfc8fffff
[    0.234513] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.234516] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.234519] pci 0000:00:1e.0:   MEM window: 0xfa000000-0xfbffffff
[    0.234523] pci 0000:00:1e.0:   PREFETCH window: 0xfc900000-0xfc9fffff
[    0.234534]   alloc irq_desc for 16 on node -1
[    0.234536]   alloc kstat_irqs on node -1
[    0.234541] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.234545] pci 0000:00:01.0: setting latency timer to 64
[    0.234552] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.234556] pci 0000:00:1c.0: setting latency timer to 64
[    0.234562]   alloc irq_desc for 19 on node -1
[    0.234563]   alloc kstat_irqs on node -1
[    0.234566] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.234569] pci 0000:00:1c.3: setting latency timer to 64
[    0.234575] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.234579] pci 0000:00:1c.4: setting latency timer to 64
[    0.234584] pci 0000:00:1e.0: setting latency timer to 64
[    0.234587] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.234589] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.234591] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.234593] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xf6ffffff]
[    0.234595] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.234597] pci_bus 0000:02: resource 0 io:  [0x9000-0x9fff]
[    0.234599] pci_bus 0000:02: resource 1 mem: [0xfc100000-0xfc2fffff]
[    0.234601] pci_bus 0000:02: resource 2 pref mem [0xfc300000-0xfc4fffff]
[    0.234603] pci_bus 0000:03: resource 0 io:  [0xb000-0xbfff]
[    0.234605] pci_bus 0000:03: resource 1 mem: [0xf7000000-0xf7ffffff]
[    0.234607] pci_bus 0000:03: resource 2 pref mem [0xfc500000-0xfc6fffff]
[    0.234609] pci_bus 0000:04: resource 0 io:  [0xc000-0xcfff]
[    0.234611] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xf9ffffff]
[    0.234613] pci_bus 0000:04: resource 2 pref mem [0xfc700000-0xfc8fffff]
[    0.234615] pci_bus 0000:05: resource 0 io:  [0xd000-0xdfff]
[    0.234617] pci_bus 0000:05: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.234618] pci_bus 0000:05: resource 2 pref mem [0xfc900000-0xfc9fffff]
[    0.234620] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.234622] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.234652] NET: Registered protocol family 2
[    0.234731] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.234976] TCP established hash table entries: 131072 (order: 8, 1048576 byt
es)
[    0.235348] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.235517] TCP: Hash tables configured (established 131072 bind 65536)
[    0.235519] TCP reno registered
[    0.235571] NET: Registered protocol family 1
[    0.235695] pci 0000:01:00.0: Boot video device
[    0.235837] cpufreq-nforce2: No nForce2 chipset.
[    0.235859] Scanning for low memory corruption every 60 seconds
[    0.235938] audit: initializing netlink socket (disabled)
[    0.235944] type=2000 audit(1272997256.235:1): initialized
[    0.243488] highmem bounce pool size: 64 pages
[    0.243492] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.244638] VFS: Disk quotas dquot_6.5.2
[    0.244684] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.245112] fuse init (API version 7.13)
[    0.245176] msgmni has been set to 1651
[    0.245331] alg: No test for stdrng (krng)
[    0.245373] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 2
53)
[    0.245376] io scheduler noop registered
[    0.245377] io scheduler anticipatory registered
[    0.245378] io scheduler deadline registered
[    0.245407] io scheduler cfq registered (default)
[    0.245510]   alloc irq_desc for 24 on node -1
[    0.245512]   alloc kstat_irqs on node -1
[    0.245518] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.245523] pcieport 0000:00:01.0: setting latency timer to 64
[    0.245598]   alloc irq_desc for 25 on node -1
[    0.245600]   alloc kstat_irqs on node -1
[    0.245605] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.245611] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.245703]   alloc irq_desc for 26 on node -1
[    0.245704]   alloc kstat_irqs on node -1
[    0.245709] pcieport 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.245715] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.245806]   alloc irq_desc for 27 on node -1
[    0.245807]   alloc kstat_irqs on node -1
[    0.245812] pcieport 0000:00:1c.4: irq 27 for MSI/MSI-X
[    0.245818] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.245883] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.245954] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.246027] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:0
0/input/input0
[    0.246030] ACPI: Power Button [PWRB]
[    0.246077] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/inp
ut1
[    0.246079] ACPI: Power Button [PWRF]
[    0.246312] processor LNXCPU:00: registered as cooling_device0
[    0.246451] ACPI: SSDT dfee8300 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 2004
0311)
[    0.246738] processor LNXCPU:01: registered as cooling_device1
[    0.249328] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.249412] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.249703] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.250532] brd: module loaded
[    0.250879] loop: module loaded
[    0.250935] input: Macintosh mouse button emulation as /devices/virtual/input
/input2
[    0.250991] ata_piix 0000:00:1f.2: version 2.13
[    0.251003] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.251006] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.251037] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.251123] scsi0 : ata_piix
[    0.251404] scsi1 : ata_piix
[    0.251823] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.251826] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.251841] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.251845] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.251871] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.251929] scsi2 : ata_piix
[    0.252178] scsi3 : ata_piix
[    0.252185] isapnp: Scanning for PnP cards...
[    0.252597] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[    0.252601] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[    0.252648] pata_acpi 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 1
9
[    0.252668] pata_acpi 0000:03:00.0: setting latency timer to 64
[    0.252678] pata_acpi 0000:03:00.0: PCI INT A disabled
[    0.252901] Fixed MDIO Bus: probed
[    0.252926] PPP generic driver version 2.4.2
[    0.252951] tun: Universal TUN/TAP device driver, 1.6
[    0.252952] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.253014] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.253026]   alloc irq_desc for 18 on node -1
[    0.253028]   alloc kstat_irqs on node -1
[    0.253031] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.253039] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.253041] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.253067] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus numbe
r 1
[    0.256967] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.256980] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc005000
[    0.287747] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.287826] usb usb1: configuration #1 chosen from 1 choice
[    0.287849] hub 1-0:1.0: USB hub found
[    0.287856] hub 1-0:1.0: 6 ports detected
[    0.287902]   alloc irq_desc for 23 on node -1
[    0.287904]   alloc kstat_irqs on node -1
[    0.287907] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.287917] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.287919] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.287943] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus numbe
r 2
[    0.291850] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.291862] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc004000
[    0.311706] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.311770] usb usb2: configuration #1 chosen from 1 choice
[    0.311790] hub 2-0:1.0: USB hub found
[    0.311796] hub 2-0:1.0: 6 ports detected
[    0.311843] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.311858] uhci_hcd: USB Universal Host Controller Interface driver
[    0.311888] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.311894] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.311896] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.311923] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus numbe
r 3
[    0.311949] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    0.312016] usb usb3: configuration #1 chosen from 1 choice
[    0.312035] hub 3-0:1.0: USB hub found
[    0.312040] hub 3-0:1.0: 2 ports detected
[    0.312072]   alloc irq_desc for 21 on node -1
[    0.312074]   alloc kstat_irqs on node -1
[    0.312077] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.312082] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.312084] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.312108] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus numbe
r 4
[    0.312132] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e100
[    0.312196] usb usb4: configuration #1 chosen from 1 choice
[    0.312214] hub 4-0:1.0: USB hub found
[    0.312219] hub 4-0:1.0: 2 ports detected
[    0.312250] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.312255] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.312257] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.312281] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus numbe
r 5
[    0.312300] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e500
[    0.312360] usb usb5: configuration #1 chosen from 1 choice
[    0.312378] hub 5-0:1.0: USB hub found
[    0.312383] hub 5-0:1.0: 2 ports detected
[    0.312416] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.312421] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.312423] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.312445] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus numbe
r 6
[    0.312464] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e200
[    0.312525] usb usb6: configuration #1 chosen from 1 choice
[    0.312544] hub 6-0:1.0: USB hub found
[    0.312550] hub 6-0:1.0: 2 ports detected
[    0.312583] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.312587] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.312589] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.312611] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus numbe
r 7
[    0.312630] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e300
[    0.312694] usb usb7: configuration #1 chosen from 1 choice
[    0.312712] hub 7-0:1.0: USB hub found
[    0.312717] hub 7-0:1.0: 2 ports detected
[    0.312751] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.312756] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.312758] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.312780] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus numbe
r 8
[    0.312799] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[    0.312862] usb usb8: configuration #1 chosen from 1 choice
[    0.312882] hub 8-0:1.0: USB hub found
[    0.312886] hub 8-0:1.0: 2 ports detected
[    0.312957] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.312958] PNP: PS/2 appears to have AUX port disabled, if this is incorrect
 please boot with i8042.nopnp
[    0.313105] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.313163] mice: PS/2 mouse device common for all mice
[    0.313254] rtc_cmos 00:04: RTC can wake from S4
[    0.313281] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.313303] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.313377] device-mapper: uevent: version 1.0.3
[    0.316964] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-d
evel@redhat.com
[    0.325709] device-mapper: multipath: version 1.1.0 loaded
[    0.325711] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.328178] EISA: Probing bus 0 at eisa.0
[    0.328201] EISA: Detected 0 cards.
[    0.330919] input: AT Translated Set 2 keyboard as /devices/platform/i8042/se
rio0/input/input3
[    0.339350] Freeing initrd memory: 7780k freed
[    0.341530] cpuidle: using governor ladder
[    0.341533] cpuidle: using governor menu
[    0.341914] TCP cubic registered
[    0.342030] NET: Registered protocol family 10
[    0.342387] lo: Disabled Privacy Extensions
[    0.342641] NET: Registered protocol family 17
[    0.345186] Using IPI No-Shortcut mode
[    0.345270] PM: Resume from disk failed.
[    0.345283] registered taskstats version 1
[    0.345640]   Magic number: 10:473:341
[    0.345702] rtc_cmos 00:04: setting system clock to 2010-05-04 18:20:56 UTC (
1272997256)
[    0.345704] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.345706] EDD information not available.
[    0.590238] ata1: SATA link down (SStatus 0 SControl 300)
[    0.599686] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.606364] isapnp: No Plug & Play device found
[    0.670150] ata2: SATA link down (SStatus 0 SControl 300)
[    0.798139] ata3: SATA link down (SStatus 0 SControl 300)
[    0.827635] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.859773] ata4.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    0.859777] ata4.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[    0.859780] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.863341] usb 1-1: configuration #1 chosen from 1 choice
[    0.867900] ata4.00: configured for UDMA/133
[    0.868001] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ
: 0 ANSI: 5
[    0.868113] sd 3:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 
GiB)
[    0.868121] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    0.868148] sd 3:0:0:0: [sda] Write Protect is off
[    0.868150] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.868168] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[    0.868267]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    0.926998] sd 3:0:0:0: [sda] Attached SCSI disk
[    0.927008] Freeing unused kernel memory: 656k freed
[    0.927204] Write protecting the kernel text: 4676k
[    0.927235] Write protecting the kernel read-only data: 1840k
[    0.938670] udev: starting version 151
[    0.997024] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IR
Q 19
[    0.997054] pata_jmicron 0000:03:00.0: setting latency timer to 64
[    1.008211] 3ware Storage Controller device driver for Linux v1.26.02.002.
[    1.008234]   alloc irq_desc for 20 on node -1
[    1.008236]   alloc kstat_irqs on node -1
[    1.008240] 3w-xxxx 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.010175] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.010187] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.010220] r8169 0000:04:00.0: setting latency timer to 64
[    1.010272]   alloc irq_desc for 28 on node -1
[    1.010273]   alloc kstat_irqs on node -1
[    1.010284] r8169 0000:04:00.0: irq 28 for MSI/MSI-X
[    1.010769] eth0: RTL8168b/8111b at 0xf8078000, 00:1d:7d:0a:01:3e, XID 180000
00 IRQ 28
[    1.014657] scsi4 : pata_jmicron
[    1.022243] Floppy drive(s): fd0 is 1.44M
[    1.029601] scsi6 : pata_jmicron
[    1.030128] ata5: PATA max UDMA/100 cmd 0xb000 ctl 0xb100 bmdma 0xb400 irq 19
[    1.030131] ata6: PATA max UDMA/100 cmd 0xb200 ctl 0xb300 bmdma 0xb408 irq 19
[    1.041750] FDC 0 is a post-1991 82077
[    1.208546] ata5.00: ATAPI: PIONEER DVD-RW  DVR-111D, 1.23, max UDMA/66
[    1.208971] ata5.01: ATA-6: ExcelStor Technology J340, V22OA63A, max UDMA/100
[    1.208974] ata5.01: 80418240 sectors, multi 16: LBA48 
[    1.224563] ata5.00: configured for UDMA/66
[    1.248914] ata5.01: configured for UDMA/100
[    1.260013] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    1.261988] scsi 4:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.23 PQ
: 0 ANSI: 5
[    1.274979] kjournald starting.  Commit interval 5 seconds
[    1.274990] EXT3-fs: mounted filesystem with writeback data mode.
[    1.285473] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.285476] Uniform CD-ROM driver Revision: 3.20
[    1.285554] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.285599] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.285685] scsi 4:0:1:0: Direct-Access     ATA      ExcelStor Techno V22O PQ
: 0 ANSI: 5
[    1.285769] sd 4:0:1:0: [sdb] 80418240 512-byte logical blocks: (41.1 GB/38.3
 GiB)
[    1.285772] sd 4:0:1:0: Attached scsi generic sg2 type 0
[    1.285905] sd 4:0:1:0: [sdb] Write Protect is off
[    1.285907] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.285927] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[    1.286021]  sdb: sdb1 sdb2 < sdb5 >
[    1.307898] sd 4:0:1:0: [sdb] Attached SCSI disk
[    1.506222] usb 4-2: configuration #1 chosen from 1 choice
[    1.748015] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.898380] usb 5-1: configuration #1 chosen from 1 choice
[    1.901354] hub 5-1:1.0: USB hub found
[    1.903328] hub 5-1:1.0: 4 ports detected
[    2.201332] usb 5-1.3: new low speed USB device using uhci_hcd and address 3
[    2.356410] usb 5-1.3: configuration #1 chosen from 1 choice
[    2.449331] usb 5-1.4: new full speed USB device using uhci_hcd and address 4
[    2.584384] usb 5-1.4: configuration #1 chosen from 1 choice
[    2.879760] Adding 5976172k swap on /dev/sda4.  Priority:-1 extents:1 across:
5976172k 
[    3.057053] udev: starting version 151
[    4.319977] lp: driver loaded but no devices found
[    4.440662] parport_pc 00:09: reported by Plug and Play ACPI
[    4.440703] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    4.536150] lp0: using parport0 (interrupt-driven).
[    4.543494] type=1505 audit(1272997260.694:2):  operation="profile_load" pid=
506 name="/usr/sbin/ntpd"
[    4.650015] it87: Found IT8718F chip at 0x290, revision 5
[    4.650024] it87: in3 is VCC (+5V)
[    4.664018] ppdev: user-space parallel port driver
[    4.813007] Linux agpgart interface v0.103
[    4.827385] vga16fb: initializing
[    4.827388] vga16fb: mapped to 0xc00a0000
[    4.827482] fb0: VGA16 VGA frame buffer device
[    5.258051] r8169: eth0: link up
[    5.258057] r8169: eth0: link up
[    5.630686] nvidia: module license 'NVIDIA' taints kernel.
[    5.630689] Disabling lock debugging due to kernel taint
[    6.244352] Linux video capture interface: v2.00
[    6.244457] usbcore: registered new interface driver hiddev
[    6.369806] Initializing USB Mass Storage driver...
[    6.369884] usbcore: registered new interface driver usb-storage
[    6.370203] USB Mass Storage support registered.
[    6.488361] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.488369] nvidia 0000:01:00.0: setting latency timer to 64
[    6.488372] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+me
m,decodes=none:owns=io+mem
[    6.488486] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 1
1 21:41:46 PST 2010
[    6.626525] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[    6.640383] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:1a.7
/usb1/1-1/1-1:1.0/input/input4
[    6.640443] usbcore: registered new interface driver uvcvideo
[    6.640445] USB Video Class driver (v0.1.0)
[    6.749056] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.837011]   alloc irq_desc for 22 on node -1
[    6.837013]   alloc kstat_irqs on node -1
[    6.837017] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 2
2
[    6.837040] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.866239] Console: switching to colour frame buffer device 80x30
[    7.057626] usbcore: registered new interface driver snd-usb-audio
[    7.291496] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/inp
ut/input5
[    7.419298] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    7.420713] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please 
use
[    7.420715] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module 
option or
[    7.420716] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[    7.484010] scsi5 : 3ware Storage Controller
[    7.484073] 3w-xxxx: scsi5: Found a 3ware Storage Controller at 0xd000, IRQ: 
20.
[    7.485066] scsi 5:0:0:0: Direct-Access     3ware    Logical Disk 0   1.2  PQ
: 0 ANSI: 0
[    7.488684] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    7.489055] sd 5:0:0:0: [sdc] 488395120 512-byte logical blocks: (250 GB/232 
GiB)
[    7.489069] sd 5:0:0:0: [sdc] Write Protect is off
[    7.489071] sd 5:0:0:0: [sdc] Mode Sense: 00 00 00 00
[    7.489372] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: disabled, sup
ports DPO and FUA
[    7.490025]  sdc: sdc1
[    7.497149] sd 5:0:0:0: [sdc] Attached SCSI disk
[    7.559826] 3w-xxxx: scsi5: Unknown scsi opcode: 0x85
[    7.559870] 3w-xxxx: scsi5: Unknown scsi opcode: 0x85
[    7.559883] 3w-xxxx: scsi5: Unknown scsi opcode: 0x85
[    7.767287] generic-usb 0003:051D:0002.0001: hiddev96,hidraw0: USB HID v1.10 
Device [American Power Conversion Back-UPS CS 500 FW:808.q5.I USB FW:q5] on usb-
0000:00:1a.1-2/input0
[    7.783548] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/000
0:00:1a.2/usb5/5-1/5-1.3/5-1.3:1.0/input/input6
[    7.783614] generic-usb 0003:046D:C051.0002: input,hidraw1: USB HID v1.10 Mou
se [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.2-1.3/input0
[    7.787402] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00
:1a.2/usb5/5-1/5-1.4/5-1.4:1.3/input/input7
[    7.787472] generic-usb 0003:0D8C:000C.0003: input,hidraw2: USB HID v1.00 Dev
ice [C-Media USB Headphone Set  ] on usb-0000:00:1a.2-1.4/input3
[    7.787489] usbcore: registered new interface driver usbhid
[    7.787491] usbhid: v2.6:USB HID core driver
[   12.700373] EXT3 FS on sda1, internal journal
[   12.904230] kjournald starting.  Commit interval 5 seconds
[   12.904470] EXT3 FS on sda2, internal journal
[   12.904474] EXT3-fs: mounted filesystem with ordered data mode.
[   13.592243] REISERFS (device sda5): found reiserfs format "3.6" with standard
 journal
[   13.592250] REISERFS (device sda5): using ordered data mode
[   13.595234] REISERFS (device sda5): journal params: device sda5, size 8192, j
ournal first block 18, max trans len 1024, max batch 900, max commit age 30, max
 trans age 30
[   13.595392] REISERFS (device sda5): checking transaction log (sda5)
[   13.644764] REISERFS (device sda5): Using r5 hash to sort names
[   13.696414] REISERFS (device sda6): found reiserfs format "3.6" with standard
 journal
[   13.696422] REISERFS (device sda6): using ordered data mode
[   13.706160] REISERFS (device sda6): journal params: device sda6, size 8192, j
ournal first block 18, max trans len 1024, max batch 900, max commit age 30, max
 trans age 30
[   13.706338] REISERFS (device sda6): checking transaction log (sda6)
[   13.750671] REISERFS (device sda6): Using r5 hash to sort names
[   16.056003] eth0: no IPv6 routers present
[   35.722716] type=1505 audit(1272997292.238:3):  operation="profile_load" pid=
1465 name="/usr/share/gdm/guest-session/Xsession"
[   36.038815] type=1505 audit(1272997292.554:4):  operation="profile_load" pid=
1468 name="/sbin/dhclient3"
[   36.039338] type=1505 audit(1272997292.554:5):  operation="profile_load" pid=
1468 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   36.039609] type=1505 audit(1272997292.554:6):  operation="profile_load" pid=
1468 name="/usr/lib/connman/scripts/dhclient-script"
[   36.207569] type=1505 audit(1272997292.722:7):  operation="profile_load" pid=
1469 name="/usr/bin/evince"
[   36.214013] type=1505 audit(1272997292.730:8):  operation="profile_load" pid=
1469 name="/usr/bin/evince-previewer"
[   36.218007] type=1505 audit(1272997292.734:9):  operation="profile_load" pid=
1469 name="/usr/bin/evince-thumbnailer"
[   36.423038] type=1505 audit(1272997292.938:10):  operation="profile_load" pid
=1472 name="/usr/lib/cups/backend/cups-pdf"
[   36.423689] type=1505 audit(1272997292.938:11):  operation="profile_load" pid
=1472 name="/usr/sbin/cupsd"
[   36.735216] type=1505 audit(1272997293.250:12):  operation="profile_load" pid
=1474 name="/usr/sbin/mysqld-akonadi"
[   39.379233] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   39.379235] apm: disabled - APM is not SMP safe.
[   50.063964] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   50.063966] vboxdrv: Successfully done.
[   50.063968] vboxdrv: Found 2 processor cores.
[   50.064031] vboxdrv: fAsync=0 offMin=0x190 offMax=0x7b8
[   50.064070] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'
.
[   50.064071] vboxdrv: Successfully loaded version 3.1.6 (interface 0x00100001)
.
[   50.429669] 3w-xxxx: scsi5: Unknown scsi opcode: 0x85
[   50.429684] 3w-xxxx: scsi5: Unknown scsi opcode: 0x85
[  166.084643] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

```

Also:

> lsusb -v

```
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                 24576000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  6
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            400000
        dwFrameInterval( 2)            500000
        dwFrameInterval( 3)            666666
        dwFrameInterval( 4)           1000000
        dwFrameInterval( 5)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            46
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            800
        wHeight                           600
        dwMinBitRate                 38400000
        dwMaxBitRate                192000000
        dwMaxVideoFrameBufferSize      960000
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  5
        dwFrameInterval( 0)            400000
        dwFrameInterval( 1)            500000
        dwFrameInterval( 2)            666666
        dwFrameInterval( 3)           1000000
        dwFrameInterval( 4)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            960
        wHeight                           720
        dwMinBitRate                 55296000
        dwMaxBitRate                110592000
        dwMaxVideoFrameBufferSize     1382400
        dwDefaultFrameInterval        1000000
        bFrameIntervalType                  2
        dwFrameInterval( 0)           1000000
        dwFrameInterval( 1)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         8
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1600
        wHeight                          1200
        dwMinBitRate                153600000
        dwMaxBitRate                153600000
        dwMaxVideoFrameBufferSize     3840000
        dwDefaultFrameInterval        2000000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            39
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               8
        wWidth( 0)                        160
        wHeight( 0)                       120
        wWidth( 1)                        176
        wHeight( 1)                       144
        wWidth( 2)                        320
        wHeight( 2)                       240
        wWidth( 3)                        352
        wHeight( 3)                       288
        wWidth( 4)                        640
        wHeight( 4)                       480
        wWidth( 5)                        800
        wHeight( 5)                       600
        wWidth( 6)                        960
        wHeight( 6)                       720
        wWidth( 7)                       1600
        wHeight( 7)                      1200
        bNumCompressionPatterns             8
        bCompression( 0)                    5
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x00c0  1x 192 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0180  1x 384 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0280  1x 640 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0320  1x 800 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x03b0  1x 944 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0a80  2x 640 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       8
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0b20  2x 800 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       9
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0be0  2x 992 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting      10
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting      11
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13fc  3x 1020 bytes
        bInterval               1
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         2
      bInterfaceCount         2
      bFunctionClass          1 Audio
      bFunctionSubClass       2 Streaming
      bFunctionProtocol       0 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           38
        bInCollection           1
        baInterfaceNr( 0)       3
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             1
        wChannelConfig     0x0000
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          1
        bSourceID               5
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 5
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x03
          Mute
          Volume
        iFeature                0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           3
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0024  1x 36 bytes
        bInterval               4
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.32-21-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1a.7
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```

and 

> lspci -v

```
rob@rob-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5000
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f4000000-f6ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e100 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e500 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fc005000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fc100000-fc2fffff
	Prefetchable memory behind bridge: 00000000fc300000-00000000fc4fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f7000000-f7ffffff
	Prefetchable memory behind bridge: 00000000fc500000-00000000fc6fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000fc700000-00000000fc8fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at e200 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e300 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fc004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000fc900000-00000000fc9fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5001
	Flags: medium devsel, IRQ 11
	Memory at fc006000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at e700 [size=8]
	I/O ports at e800 [size=4]
	I/O ports at e900 [size=8]
	I/O ports at ea00 [size=4]
	I/O ports at eb00 [size=16]
	I/O ports at ec00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)
	Subsystem: LeadTek Research Inc. Device 2a52
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f5000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at a000 [size=128]
	[virtual] Expansion ROM at f6000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidia, nvidiafb, nouveau

03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b000
	Flags: bus master, fast devsel, latency 0, IRQ 19
	I/O ports at b000 [size=8]
	I/O ports at b100 [size=4]
	I/O ports at b200 [size=8]
	I/O ports at b300 [size=4]
	I/O ports at b400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 28
	I/O ports at c000 [size=256]
	Memory at f9000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at fc700000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:00.0 RAID bus controller: 3ware Inc 7xxx/8xxx-series PATA/SATA-RAID (rev 01)
	Subsystem: 3ware Inc 7xxx/8xxx-series PATA/SATA-RAID
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
	I/O ports at d000 [size=16]
	Memory at fbc00000 (32-bit, non-prefetchable) [size=16]
	Memory at fb000000 (32-bit, non-prefetchable) [size=8M]
	[virtual] Expansion ROM at fc900000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: 3w-xxxx
	Kernel modules: 3w-xxxx

05:01.0 Communication controller: Intel Corporation 536EP Data Fax Modem
	Subsystem: Intel Corporation Device 1000
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at fb800000 (32-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>

```

Robin

---

### Post by Robbyx on 2010-05-05
I hope that I will get a response soon.

---

### Post by tgalati4 on 2010-05-05
Not much you can do about skype.  It is a proprietary, closed-source program.  So you can't go in and change anything in the code, other than the provided preferences.  The style widgets are fixed and may clash with whatever desktop modifications that you have made.

On my Intrepid machine, I don't show anything in /proc/bus/usb.  Even with a USB flash disk plugged in and mounted, there are no entries in /proc/bus/usb.  It is owned by root and is created when you cold boot.

I didn't see any errors.  It looks like you have 6 USB2 ports and 4 USB one ports (I presume this is an older hub that is plugged in?)

So is /dev/sda1 an external USB drive?

What is the output of:

sudo fdisk -l

What kind of device is SDA1?

Try unplugging your USB hub and wait for boot up, then plug it in.

Lucid uses DeviceKit to enumerate devices and it is supposedly much faster than HAL, the old hardware abstraction layer.  You might need to file a bug against DeviceKit.

What specifically is not working?  Your USB ports are all enumerated.  Presumably they all work.

---

### Post by Robbyx on 2010-05-05
Thank you for your help.

> **tgalati4 said:**
> Not much you can do about skype.  It is a proprietary, closed-source program.  So you can't go in and change anything in the code, other than the provided preferences.  The style widgets are fixed and may clash with whatever desktop modifications that you have made.

I have just installed Lucid  and taking their standard desktop I am getting the black on black.  I thought I had cured it but it is still there in some drop down menus in skype.
> 
On my Intrepid machine, I don't show anything in /proc/bus/usb. 

On this machine I also do not have such a directory. I just have input and pci.

> 
 Even with a USB flash disk plugged in and mounted, there are no entries in /proc/bus/usb.  It is owned by root and is created when you cold boot.

I didn't see any errors.  It looks like you have 6 USB2 ports and 4 USB one ports (I presume this is an older hub that is plugged in?)

So is /dev/sda1 an external USB drive?

What is the output of:

sudo fdisk -l

```
rob@rob-desktop:~$ sudo fdisk -l
[sudo] password for rob: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3725    29921031   83  Linux
/dev/sda2            3726        7647    31503465   83  Linux
/dev/sda3            7648       60057   420983325    5  Extended
/dev/sda4           60058       60801     5976180   82  Linux swap / Solaris
/dev/sda5            7648       21000   107257941   83  Linux
/dev/sda6           21001       60057   313725321   83  Linux

Disk /dev/sdb: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e433e42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sdb2            2551        5004    19711755    f  W95 Ext'd (LBA)
/dev/sdb5            2551        5004    19711723+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 250.1 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   fd  Linux raid autodetect
rob@rob-desktop:~$ 


```

What kind of device is SDA1?[/QUOTE]

It is the boot partition for ubuntu, ext3 



> Try unplugging your USB hub and wait for boot up, then plug it in.

Lucid uses DeviceKit to enumerate devices and it is supposedly much faster than HAL, the old hardware abstraction layer.  You might need to file a bug against DeviceKit.

What specifically is not working?  Your USB ports are all enumerated.  Presumably they all work.

Everything seems to work ok, but I am getting the error messages to which I referred,  so I thought they should be resolved.

Robin

---

### Post by tgalati4 on 2010-05-06
Well, DeviceKit replaced HAL for device enumeration.  HAL looks for /proc/bus/pci;
/proc/bus/usb; and /proc/bus/input.  It's possible that USB enumeration got changed, but the kernel is still trying to mount /proc/bus/usb but it's not there.  So perhaps file a bug for this against DeviceKit.  It's possible that a bug has already been filed, so an update patch should trickle down to fix it.

I'm not sure what the mount error for /dev/sda1 is all about.  It's your boot partition.  As long as your machine boots, it's a nuisance error but obviously not critical.  Without a context for the error, it's hard to troubleshoot this one.  If it doesn't show up in:

dmesg | grep error

Then it really doesn't effect your system.  You will have to provide the exact wording of the error and when it occurs.

For the skype nuisance, you can put a post up on the skype forum and maybe someone will fix it.  Search the skype forums first, because someone may have already discovered the problem.  The skype folks have been slow to release updates for Linux.  Seems like the Windows version gets all of the attention.

---

