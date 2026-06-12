---
title: "Boot Strings and 'init: rc' messages on shutdown"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by novafluxx on 2009-09-21
Am I supposed to be seeing text at all during the boot process after GRUB2? This is a fresh install of Karmic Beta with all updates (as of 10 minutes ago, and no I didn't do a partial upgrade)

Is this a known issue I shouldn't be concerned with? If I need to provide more information please let me know and also please tell me how to obtain said information.


OK this is what I'm seeing after a dmesg:

```
[    0.324988] system 00:0b: iomem range 0x100000-0xbf66d7ff could not be reserved
[    0.324991] system 00:0b: iomem range 0xbf66d800-0xbf6fffff has been reserved
[    0.324994] system 00:0b: iomem range 0xbf700000-0xbf7fffff has been reserved
[    0.324997] system 00:0b: iomem range 0xbf700000-0xbfefffff could not be reserved
[    0.325000] system 00:0b: iomem range 0xffe00000-0xffffffff has been reserved
[    0.325003] system 00:0b: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.325007] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.325010] system 00:0b: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.325013] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.325016] system 00:0b: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.325019] system 00:0b: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.325022] system 00:0b: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.325025] system 00:0b: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.325028] system 00:0b: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.325031] system 00:0b: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.359701] AppArmor: AppArmor Filesystem Enabled
[    0.359777] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.359780] pci 0000:00:1c.0:   IO window: disabled
[    0.359786] pci 0000:00:1c.0:   MEM window: disabled
[    0.359792] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.359797] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.359799] pci 0000:00:1c.1:   IO window: disabled
[    0.359806] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff
[    0.359812] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.359817] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.359821] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.359828] pci 0000:00:1c.3:   MEM window: 0xf6a00000-0xf6bfffff
[    0.359834] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.359842] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.359844] pci 0000:00:1c.5:   IO window: disabled
[    0.359851] pci 0000:00:1c.5:   MEM window: 0xf6900000-0xf69fffff
[    0.359856] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.359862] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.359864] pci 0000:00:1e.0:   IO window: disabled
[    0.359871] pci 0000:00:1e.0:   MEM window: 0xf6800000-0xf68fffff
[    0.359876] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.359891]   alloc irq_desc for 16 on node -1
[    0.359893]   alloc kstat_irqs on node -1
[    0.359898] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.359906] pci 0000:00:1c.0: setting latency timer to 64
[    0.359915]   alloc irq_desc for 17 on node -1
[    0.359917]   alloc kstat_irqs on node -1
[    0.359921] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.359928] pci 0000:00:1c.1: setting latency timer to 64
[    0.359937]   alloc irq_desc for 19 on node -1
[    0.359939]   alloc kstat_irqs on node -1
[    0.359942] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.359949] pci 0000:00:1c.3: setting latency timer to 64
[    0.359959] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.359965] pci 0000:00:1c.5: setting latency timer to 64
[    0.359975] pci 0000:00:1e.0: setting latency timer to 64
[    0.359980] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.359983] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.359986] pci_bus 0000:0c: resource 1 mem: [0xf6c00000-0xf6cfffff]
[    0.359988] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff]
[    0.359991] pci_bus 0000:0d: resource 1 mem: [0xf6a00000-0xf6bfffff]
[    0.359998] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.360001] pci_bus 0000:09: resource 1 mem: [0xf6900000-0xf69fffff]
[    0.360004] pci_bus 0000:03: resource 1 mem: [0xf6800000-0xf68fffff]
[    0.360007] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.360009] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.360043] NET: Registered protocol family 2
[    0.360136] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.360456] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.360974] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.361207] TCP: Hash tables configured (established 131072 bind 65536)
[    0.361210] TCP reno registered
[    0.361280] NET: Registered protocol family 1
[    0.361338] Trying to unpack rootfs image as initramfs...
[    0.500499] Switched to high resolution mode on CPU 1
[    0.503992] Switched to high resolution mode on CPU 0
[    0.526301] Freeing initrd memory: 6642k freed
[    0.530204] cpufreq-nforce2: No nForce2 chipset.
[    0.530248] Scanning for low memory corruption every 60 seconds
[    0.530386] audit: initializing netlink socket (disabled)
[    0.530406] type=2000 audit(1254440010.529:1): initialized
[    0.538956] highmem bounce pool size: 64 pages
[    0.538962] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.540457] VFS: Disk quotas dquot_6.5.2
[    0.540519] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.541063] fuse init (API version 7.12)
[    0.541147] msgmni has been set to 1680
[    0.541360] alg: No test for stdrng (krng)
[    0.541374] io scheduler noop registered
[    0.541376] io scheduler anticipatory registered
[    0.541378] io scheduler deadline registered (default)
[    0.541419] io scheduler cfq registered
[    0.541430] pci 0000:00:02.0: Boot video device
[    0.541729]   alloc irq_desc for 24 on node -1
[    0.541731]   alloc kstat_irqs on node -1
[    0.541744] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.541757] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.541928]   alloc irq_desc for 25 on node -1
[    0.541930]   alloc kstat_irqs on node -1
[    0.541939] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.541951] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.542124]   alloc irq_desc for 26 on node -1
[    0.542126]   alloc kstat_irqs on node -1
[    0.542135] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.542147] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.542312]   alloc irq_desc for 27 on node -1
[    0.542314]   alloc kstat_irqs on node -1
[    0.542324] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.542336] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.542447] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.542567] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.542732] ACPI: AC Adapter [AC] (on-line)
[    0.542822] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.543242] ACPI: Lid Switch [LID]
[    0.543288] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.543295] ACPI: Power Button [PBTN]
[    0.543337] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.543340] ACPI: Sleep Button [SBTN]
[    0.543986] ACPI: SSDT bf66e530 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.544633] ACPI: SSDT bf66dec6 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.544985] Monitor-Mwait will be used to enter C-1 state
[    0.545011] Monitor-Mwait will be used to enter C-2 state
[    0.545035] Monitor-Mwait will be used to enter C-3 state
[    0.545043] Marking TSC unstable due to TSC halts in idle
[    0.545062] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.545088] processor LNXCPU:00: registered as cooling_device0
[    0.545091] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.545424] ACPI: SSDT bf66e774 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.545745] ACPI: SSDT bf66e4ab 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.546212] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.546236] processor LNXCPU:01: registered as cooling_device1
[    0.546240] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.552406] thermal LNXTHERM:01: registered as thermal_zone0
[    0.552415] ACPI: Thermal Zone [THM] (60 C)
[    0.552499] isapnp: Scanning for PnP cards...
[    0.578543] ACPI: Battery Slot [BAT0] (battery present)
[    0.909064] isapnp: No Plug & Play device found
[    0.910165] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.911503] brd: module loaded
[    0.911955] loop: module loaded
[    0.912024] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.912096] ahci 0000:00:1f.2: version 3.0
[    0.912110] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.912145]   alloc irq_desc for 28 on node -1
[    0.912147]   alloc kstat_irqs on node -1
[    0.912159] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.912231] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    0.912234] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    0.912240] ahci 0000:00:1f.2: setting latency timer to 64
[    0.921064] scsi0 : ahci
[    0.921148] scsi1 : ahci
[    0.921205] scsi2 : ahci
[    0.921425] ata1: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb900 irq 28
[    0.921427] ata2: DUMMY
[    0.921430] ata3: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfba00 irq 28
[    0.921481] ata_piix 0000:00:1f.1: version 2.13
[    0.921489] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.921526] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.921599] scsi3 : ata_piix
[    0.921655] scsi4 : ata_piix
[    0.922248] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.922251] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.922459] ata5: port disabled. ignoring.
[    0.923181] Fixed MDIO Bus: probed
[    0.923215] PPP generic driver version 2.4.2
[    0.923297] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.923316]   alloc irq_desc for 22 on node -1
[    0.923318]   alloc kstat_irqs on node -1
[    0.923323] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.923334] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.923338] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.923384] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.927298] ehci_hcd 0000:00:1a.7: debug port 1
[    0.927305] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.927319] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.941013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.941083] usb usb1: configuration #1 chosen from 1 choice
[    0.941111] hub 1-0:1.0: USB hub found
[    0.941119] hub 1-0:1.0: 4 ports detected
[    0.941177]   alloc irq_desc for 20 on node -1
[    0.941179]   alloc kstat_irqs on node -1
[    0.941183] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.941193] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.941196] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.941226] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.945122] ehci_hcd 0000:00:1d.7: debug port 1
[    0.945129] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.945142] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.961014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.961087] usb usb2: configuration #1 chosen from 1 choice
[    0.961113] hub 2-0:1.0: USB hub found
[    0.961120] hub 2-0:1.0: 6 ports detected
[    0.961184] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.961204] uhci_hcd: USB Universal Host Controller Interface driver
[    0.961228] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.961234] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.961238] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.961274] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.961301] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.961377] usb usb3: configuration #1 chosen from 1 choice
[    0.961403] hub 3-0:1.0: USB hub found
[    0.961410] hub 3-0:1.0: 2 ports detected
[    0.961461]   alloc irq_desc for 21 on node -1
[    0.961463]   alloc kstat_irqs on node -1
[    0.961468] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.961475] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.961479] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.961507] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.961546] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.961624] usb usb4: configuration #1 chosen from 1 choice
[    0.961650] hub 4-0:1.0: USB hub found
[    0.961657] hub 4-0:1.0: 2 ports detected
[    0.961708] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.961715] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.961718] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.961747] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.961776] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.961854] usb usb5: configuration #1 chosen from 1 choice
[    0.961882] hub 5-0:1.0: USB hub found
[    0.961888] hub 5-0:1.0: 2 ports detected
[    0.961935] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.961942] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.961946] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.961974] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.962002] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.962080] usb usb6: configuration #1 chosen from 1 choice
[    0.962112] hub 6-0:1.0: USB hub found
[    0.962118] hub 6-0:1.0: 2 ports detected
[    0.962166] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.962172] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.962176] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.962205] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.962232] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.962317] usb usb7: configuration #1 chosen from 1 choice
[    0.962342] hub 7-0:1.0: USB hub found
[    0.962349] hub 7-0:1.0: 2 ports detected
[    0.962452] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.965571] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.965577] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.965671] mice: PS/2 mouse device common for all mice
[    0.965792] rtc_cmos 00:03: RTC can wake from S4
[    0.965824] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.965857] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.965954] device-mapper: uevent: version 1.0.3
[    0.966045] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.966132] device-mapper: multipath: version 1.1.0 loaded
[    0.966135] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.966254] EISA: Probing bus 0 at eisa.0
[    0.966262] Cannot allocate resource for EISA slot 1
[    0.966293] EISA: Detected 0 cards.
[    0.966464] cpuidle: using governor ladder
[    0.966586] cpuidle: using governor menu
[    0.967074] TCP cubic registered
[    0.967225] NET: Registered protocol family 10
[    0.967675] lo: Disabled Privacy Extensions
[    0.968024] NET: Registered protocol family 17
[    0.968041] Bluetooth: L2CAP ver 2.13
[    0.968043] Bluetooth: L2CAP socket layer initialized
[    0.968046] Bluetooth: SCO (Voice Link) ver 0.6
[    0.968047] Bluetooth: SCO socket layer initialized
[    0.968101] Bluetooth: RFCOMM TTY layer initialized
[    0.968105] Bluetooth: RFCOMM socket layer initialized
[    0.968107] Bluetooth: RFCOMM ver 1.11
[    0.968506] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.968571] Using IPI No-Shortcut mode
[    0.968626] PM: Resume from disk failed.
[    0.968639] registered taskstats version 1
[    0.968762]   Magic number: 13:568:604
[    0.968855] rtc_cmos 00:03: setting system clock to 2009-10-01 23:33:31 UTC (1254440011)
[    0.968858] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.968860] EDD information not available.
[    1.084474] ata4.00: ATAPI: TEAC   DVD+/-RW DVW28SLC, A.06, max UDMA/33
[    1.100379] ata4.00: configured for UDMA/33
[    1.240075] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.240105] ata3: SATA link down (SStatus 0 SControl 300)
[    1.240480] ata1.00: ATA-8: FUJITSU MHZ2250BH G2, 00850009, max UDMA/100
[    1.240486] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    1.241089] ata1.00: configured for UDMA/100
[    1.256224] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2250B 0085 PQ: 0 ANSI: 5
[    1.256370] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.256408] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.256451] sd 0:0:0:0: [sda] Write Protect is off
[    1.256454] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.256476] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.256595]  sda:
[    1.263128] scsi 3:0:0:0: CD-ROM            TEAC     DVD+-RW DVW28SLC A.06 PQ: 0 ANSI: 5
[    1.279108]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.281416] Uniform CD-ROM driver Revision: 3.20
[    1.281565] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.281631] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.296143]  sda5 sda6 >
[    1.320909] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.320959] Freeing unused kernel memory: 540k freed
[    1.321326] Write protecting the kernel text: 4544k
[    1.321383] Write protecting the kernel read-only data: 1832k
[    1.365051] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    1.500020] Clocksource tsc unstable (delta = -238936629 ns)
[    1.501278] usb 2-6: configuration #1 chosen from 1 choice
[    1.532272] tg3.c:v3.99 (April 20, 2009)
[    1.532301] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.532317] tg3 0000:09:00.0: setting latency timer to 64
[    1.541058] tg3 0000:09:00.0: PME# disabled
[    1.581363] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.639086] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f68ff800-f68fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.740065] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.843297] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:21:9b:da:bb:27
[    1.843301] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
[    1.843304] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.843306] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.919429] usb 3-2: configuration #1 chosen from 1 choice
[    1.922387] hub 3-2:1.0: USB hub found
[    1.924354] hub 3-2:1.0: 3 ports detected
[    2.018852] PM: Starting manual resume from disk
[    2.018855] PM: Resume from partition 8:6
[    2.018857] PM: Checking hibernation image.
[    2.019005] PM: Resume from disk failed.
[    2.079959] EXT4-fs (sda5): barriers enabled
[    2.098452] kjournald2 starting: pid 301, dev sda5:8, commit interval 5 seconds
[    2.098476] EXT4-fs (sda5): delayed allocation enabled
[    2.098483] EXT4-fs: file extents enabled
[    2.114550] EXT4-fs: mballoc enabled
[    2.114564] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.209378] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    2.341504] usb 3-2.1: configuration #1 chosen from 1 choice
[    2.417379] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    2.547509] usb 3-2.2: configuration #1 chosen from 1 choice
[    2.554813] usbcore: registered new interface driver hiddev
[    2.557843] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input5
[    2.557965] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    2.557983] usbcore: registered new interface driver usbhid
[    2.558070] usbhid: v2.6:USB HID core driver
[    2.629379] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    2.759498] usb 3-2.3: configuration #1 chosen from 1 choice
[    2.766772] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input6
[    2.766848] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    2.814601] type=1505 audit(1254440013.344:2): operation="profile_load" pid=331 name=/sbin/dhclient3
[    2.815306] type=1505 audit(1254440013.344:3): operation="profile_load" pid=331 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    2.815703] type=1505 audit(1254440013.344:4): operation="profile_load" pid=331 name=/usr/lib/connman/scripts/dhclient-script
[    2.830322] type=1505 audit(1254440013.359:5): operation="profile_load" pid=336 name=/usr/lib/cups/backend/cups-pdf
[    2.831224] type=1505 audit(1254440013.359:6): operation="profile_load" pid=336 name=/usr/sbin/cupsd
[    2.849935] type=1505 audit(1254440013.379:7): operation="profile_load" pid=337 name=/usr/sbin/tcpdump
[    2.852003] type=1505 audit(1254440013.379:8): operation="profile_load" pid=338 name=/usr/share/gdm/guest-session/Xsession
[    2.904197] type=1505 audit(1254440013.435:9): operation="profile_load" pid=340 name=/usr/bin/evince
[    2.912209] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[324fc0003a9699c1]
[    2.914722] type=1505 audit(1254440013.443:10): operation="profile_load" pid=340 name=/usr/bin/evince-previewer
[    3.765732] udev: starting version 147
[    4.779207] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    4.840269] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    4.840386] usbcore: registered new interface driver btusb
[    5.090868] lib80211: common routines for IEEE802.11 drivers
[    5.090872] lib80211_crypt: registered algorithm 'NULL'
[    5.180288] Linux agpgart interface v0.103
[    5.209818] lp: driver loaded but no devices found
[    5.266401] Linux video capture interface: v2.00
[    5.266989] input: Dell WMI hotkeys as /devices/virtual/input/input7
[    5.280022] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    5.281085] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    5.283951] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    5.485789] sdhci: Secure Digital Host Controller Interface driver
[    5.485792] sdhci: Copyright(c) Pierre Ossman
[    6.278457] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04751/0xa00000
[    6.315498] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[    6.323084] wl: module license 'MIXED/Proprietary' taints kernel.
[    6.323088] Disabling lock debugging due to kernel taint
[    6.325354] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.325368] wl 0000:0c:00.0: setting latency timer to 64
[    6.401869] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    6.402203] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    6.402799] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input9
[    6.402856] usbcore: registered new interface driver uvcvideo
[    6.402860] USB Video Class driver (v0.1.0)
[    6.524551] [drm] Initialized drm 1.1.0 20060810
[    6.547408] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.548903] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    6.548922]   alloc irq_desc for 18 on node -1
[    6.548924]   alloc kstat_irqs on node -1
[    6.548931] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    6.550993] Registered led device: mmc0::
[    6.552040] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    6.643614] lib80211_crypt: registered algorithm 'TKIP'
[    6.644031] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[    7.026529] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.026536] i915 0000:00:02.0: setting latency timer to 64
[    7.028982]   alloc irq_desc for 29 on node -1
[    7.028986]   alloc kstat_irqs on node -1
[    7.028995] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    7.131040] integrated sync not supported
[    7.145198] Adding 8281468k swap on /dev/sda6.  Priority:-1 extents:1 across:8281468k 
[    7.248136] integrated sync not supported
[    7.255089] [drm] fb0: inteldrmfb frame buffer device
[    7.267512] acpi device:37: registered as cooling_device2
[    7.269598] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:34/input/input10
[    7.269687] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    7.269756] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    7.269877] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:39/input/input11
[    7.269936] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    7.269997] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.395094] EXT4-fs (sda5): internal journal on sda5:8
[    7.515333] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    7.516006] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.603743] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[    7.706380] [drm] LVDS-8: set mode 1280x800 e
[    7.725177] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    7.725254] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    8.329800] Console: switching to colour frame buffer device 160x50
[    9.553916] __ratelimit: 3 callbacks suppressed
[    9.553920] type=1505 audit(1254454420.084:12): operation="profile_replace" pid=776 name=/sbin/dhclient3
[    9.554661] type=1505 audit(1254454420.084:13): operation="profile_replace" pid=776 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.555062] type=1505 audit(1254454420.084:14): operation="profile_replace" pid=776 name=/usr/lib/connman/scripts/dhclient-script
[    9.556892] type=1505 audit(1254454420.084:15): operation="profile_replace" pid=777 name=/usr/lib/cups/backend/cups-pdf
[    9.557769] type=1505 audit(1254454420.088:16): operation="profile_replace" pid=777 name=/usr/sbin/cupsd
[    9.560165] type=1505 audit(1254454420.088:17): operation="profile_replace" pid=778 name=/usr/sbin/tcpdump
[    9.561993] type=1505 audit(1254454420.092:18): operation="profile_replace" pid=779 name=/usr/share/gdm/guest-session/Xsession
[    9.566907] type=1505 audit(1254454420.096:19): operation="profile_replace" pid=781 name=/usr/bin/evince
[    9.577379] type=1505 audit(1254454420.108:20): operation="profile_replace" pid=781 name=/usr/bin/evince-previewer
[    9.583309] type=1505 audit(1254454420.112:21): operation="profile_replace" pid=781 name=/usr/bin/evince-thumbnailer
[   12.698244] tg3 0000:09:00.0: PME# disabled
[   12.698485]   alloc irq_desc for 30 on node -1
[   12.698487]   alloc kstat_irqs on node -1
[   12.698519] tg3 0000:09:00.0: irq 30 for MSI/MSI-X
[   12.756961] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.311968] ppdev: user-space parallel port driver
[   14.616441] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.616445] Bluetooth: BNEP filters: protocol multicast
[   14.841418] Bridge firewalling registered
[   15.939313] integrated sync not supported
[   16.072872] integrated sync not supported
[   20.570264] integrated sync not supported
[   20.697204] integrated sync not supported
[   20.833453] integrated sync not supported
[   22.732038] eth1: no IPv6 routers present
[   47.461318] integrated sync not supported
[   47.593286] integrated sync not supported
[   47.717740] integrated sync not supported
[   49.337648] integrated sync not supported
[   58.390535] UDF-fs: No VRS found
[   58.390542] UDF-fs: No partition found (1)
[   58.487845] ISO 9660 Extensions: Microsoft Joliet Level 3
[   58.545785] ISO 9660 Extensions: RRIP_1991A
```


During boot I'm getting various things like [service] [OK] etc, BEFORE Xsplash begins. Just like I would normally get if I didn't have any splash screen.

---

### Post by novafluxx on 2009-09-21
Anyone?:confused:

---

### Post by FuturePilot on 2009-09-21
The boot messages should be fixed. See [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654")

I'm still not sure what's going on with all the messages on shutdown.

---

### Post by VMC on 2009-09-21
As I recall someone else had the same issue. This is the [one]("http://ubuntuforums.org/showthread.php?t=1271420") I was thinking about. Not the same.

---

### Post by novafluxx on 2009-09-21
The boot messages aren't errors at all, it reminds me of what I used to see back when I used Debian, just messages, not errors. What one may see without USplash and XSplashh.

The messages on shutdown I'll get more detail about in a few minutes

---

### Post by novafluxx on 2009-09-21
Added info to first post.

---

### Post by FuturePilot on 2009-09-21
> **novafluxx said:**
> The boot messages aren't errors at all, it reminds me of what I used to see back when I used Debian, just messages, not errors. What one may see without USplash and XSplashh.


The udev messages were definitely not normal messages. Something was clearly wrong.

---

### Post by novafluxx on 2009-09-21
> **FuturePilot said:**
> The udev messages were definitely not normal messages. Something was clearly wrong.

Yes, but that's resolved now. I'm talking about something else entirely. This is just normal boot stuff, like one would see without a splash screen covering it up.

---

### Post by Jay_Bee on 2009-09-21
I have those shutdown messages too.

---

### Post by FuturePilot on 2009-09-21
> **novafluxx said:**
> Yes, but that's resolved now. I'm talking about something else entirely. This is just normal boot stuff, like one would see without a splash screen covering it up.

Oh, yeah I'm talking about something else. Those messages are indeed just normal boot messages. I thought something would be hiding those by now.

---

### Post by novafluxx on 2009-09-21
> **Jay_Bee said:**
> I have those shutdown messages too.

I corrected them, so thats whats I'm seeing now. Glad I'm not alone. I wonder what it is...

---

### Post by Longinus00 on 2009-09-22
I've had these messages for quite some time. What's weird is that previously, I'd have lots of these messages and it would seem to be slowing the whole shutdown process down. Lately it'll only go through a couple pairs of the messages and will shutdown faster.

One difference between my computer and yours is that I will still sometimes get usplash after these messages. I think this is because I have less of them and so they take less time. Usplash typically goes by VERY fast when this happens, sometimes finishing almost instantly.

---

### Post by novafluxx on 2009-09-22
> **Longinus00 said:**
> I've had these messages for quite some time. What's weird is that previously, I'd have lots of these messages and it would seem to be slowing the whole shutdown process down. Lately it'll only go through a couple pairs of the messages and will shutdown faster.

One difference between my computer and yours is that I will still sometimes get usplash after these messages. I think this is because I have less of them and so they take less time. Usplash typically goes by VERY fast when this happens, sometimes finishing almost instantly.

Thanks for the reply. I wonder if anyone can explain what this is...I might have to go file a bug report. That means creating a launchpad account...hmm:confused:

---

### Post by novafluxx on 2009-10-01
Still having issues on startup after GRUB...

```
[    0.324988] system 00:0b: iomem range 0x100000-0xbf66d7ff could not be reserved
[    0.324991] system 00:0b: iomem range 0xbf66d800-0xbf6fffff has been reserved
[    0.324994] system 00:0b: iomem range 0xbf700000-0xbf7fffff has been reserved
[    0.324997] system 00:0b: iomem range 0xbf700000-0xbfefffff could not be reserved
[    0.325000] system 00:0b: iomem range 0xffe00000-0xffffffff has been reserved
[    0.325003] system 00:0b: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.325007] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.325010] system 00:0b: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.325013] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.325016] system 00:0b: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.325019] system 00:0b: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.325022] system 00:0b: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.325025] system 00:0b: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.325028] system 00:0b: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.325031] system 00:0b: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.359701] AppArmor: AppArmor Filesystem Enabled
[    0.359777] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.359780] pci 0000:00:1c.0:   IO window: disabled
[    0.359786] pci 0000:00:1c.0:   MEM window: disabled
[    0.359792] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.359797] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.359799] pci 0000:00:1c.1:   IO window: disabled
[    0.359806] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff
[    0.359812] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.359817] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.359821] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.359828] pci 0000:00:1c.3:   MEM window: 0xf6a00000-0xf6bfffff
[    0.359834] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.359842] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.359844] pci 0000:00:1c.5:   IO window: disabled
[    0.359851] pci 0000:00:1c.5:   MEM window: 0xf6900000-0xf69fffff
[    0.359856] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.359862] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.359864] pci 0000:00:1e.0:   IO window: disabled
[    0.359871] pci 0000:00:1e.0:   MEM window: 0xf6800000-0xf68fffff
[    0.359876] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.359891]   alloc irq_desc for 16 on node -1
[    0.359893]   alloc kstat_irqs on node -1
[    0.359898] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.359906] pci 0000:00:1c.0: setting latency timer to 64
[    0.359915]   alloc irq_desc for 17 on node -1
[    0.359917]   alloc kstat_irqs on node -1
[    0.359921] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.359928] pci 0000:00:1c.1: setting latency timer to 64
[    0.359937]   alloc irq_desc for 19 on node -1
[    0.359939]   alloc kstat_irqs on node -1
[    0.359942] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.359949] pci 0000:00:1c.3: setting latency timer to 64
[    0.359959] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.359965] pci 0000:00:1c.5: setting latency timer to 64
[    0.359975] pci 0000:00:1e.0: setting latency timer to 64
[    0.359980] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.359983] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.359986] pci_bus 0000:0c: resource 1 mem: [0xf6c00000-0xf6cfffff]
[    0.359988] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff]
[    0.359991] pci_bus 0000:0d: resource 1 mem: [0xf6a00000-0xf6bfffff]
[    0.359998] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.360001] pci_bus 0000:09: resource 1 mem: [0xf6900000-0xf69fffff]
[    0.360004] pci_bus 0000:03: resource 1 mem: [0xf6800000-0xf68fffff]
[    0.360007] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.360009] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.360043] NET: Registered protocol family 2
[    0.360136] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.360456] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.360974] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.361207] TCP: Hash tables configured (established 131072 bind 65536)
[    0.361210] TCP reno registered
[    0.361280] NET: Registered protocol family 1
[    0.361338] Trying to unpack rootfs image as initramfs...
[    0.500499] Switched to high resolution mode on CPU 1
[    0.503992] Switched to high resolution mode on CPU 0
[    0.526301] Freeing initrd memory: 6642k freed
[    0.530204] cpufreq-nforce2: No nForce2 chipset.
[    0.530248] Scanning for low memory corruption every 60 seconds
[    0.530386] audit: initializing netlink socket (disabled)
[    0.530406] type=2000 audit(1254440010.529:1): initialized
[    0.538956] highmem bounce pool size: 64 pages
[    0.538962] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.540457] VFS: Disk quotas dquot_6.5.2
[    0.540519] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.541063] fuse init (API version 7.12)
[    0.541147] msgmni has been set to 1680
[    0.541360] alg: No test for stdrng (krng)
[    0.541374] io scheduler noop registered
[    0.541376] io scheduler anticipatory registered
[    0.541378] io scheduler deadline registered (default)
[    0.541419] io scheduler cfq registered
[    0.541430] pci 0000:00:02.0: Boot video device
[    0.541729]   alloc irq_desc for 24 on node -1
[    0.541731]   alloc kstat_irqs on node -1
[    0.541744] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.541757] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.541928]   alloc irq_desc for 25 on node -1
[    0.541930]   alloc kstat_irqs on node -1
[    0.541939] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.541951] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.542124]   alloc irq_desc for 26 on node -1
[    0.542126]   alloc kstat_irqs on node -1
[    0.542135] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.542147] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.542312]   alloc irq_desc for 27 on node -1
[    0.542314]   alloc kstat_irqs on node -1
[    0.542324] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.542336] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.542447] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.542567] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.542732] ACPI: AC Adapter [AC] (on-line)
[    0.542822] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.543242] ACPI: Lid Switch [LID]
[    0.543288] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.543295] ACPI: Power Button [PBTN]
[    0.543337] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.543340] ACPI: Sleep Button [SBTN]
[    0.543986] ACPI: SSDT bf66e530 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.544633] ACPI: SSDT bf66dec6 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.544985] Monitor-Mwait will be used to enter C-1 state
[    0.545011] Monitor-Mwait will be used to enter C-2 state
[    0.545035] Monitor-Mwait will be used to enter C-3 state
[    0.545043] Marking TSC unstable due to TSC halts in idle
[    0.545062] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.545088] processor LNXCPU:00: registered as cooling_device0
[    0.545091] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.545424] ACPI: SSDT bf66e774 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.545745] ACPI: SSDT bf66e4ab 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.546212] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.546236] processor LNXCPU:01: registered as cooling_device1
[    0.546240] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.552406] thermal LNXTHERM:01: registered as thermal_zone0
[    0.552415] ACPI: Thermal Zone [THM] (60 C)
[    0.552499] isapnp: Scanning for PnP cards...
[    0.578543] ACPI: Battery Slot [BAT0] (battery present)
[    0.909064] isapnp: No Plug & Play device found
[    0.910165] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.911503] brd: module loaded
[    0.911955] loop: module loaded
[    0.912024] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.912096] ahci 0000:00:1f.2: version 3.0
[    0.912110] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.912145]   alloc irq_desc for 28 on node -1
[    0.912147]   alloc kstat_irqs on node -1
[    0.912159] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.912231] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    0.912234] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    0.912240] ahci 0000:00:1f.2: setting latency timer to 64
[    0.921064] scsi0 : ahci
[    0.921148] scsi1 : ahci
[    0.921205] scsi2 : ahci
[    0.921425] ata1: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb900 irq 28
[    0.921427] ata2: DUMMY
[    0.921430] ata3: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfba00 irq 28
[    0.921481] ata_piix 0000:00:1f.1: version 2.13
[    0.921489] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.921526] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.921599] scsi3 : ata_piix
[    0.921655] scsi4 : ata_piix
[    0.922248] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.922251] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.922459] ata5: port disabled. ignoring.
[    0.923181] Fixed MDIO Bus: probed
[    0.923215] PPP generic driver version 2.4.2
[    0.923297] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.923316]   alloc irq_desc for 22 on node -1
[    0.923318]   alloc kstat_irqs on node -1
[    0.923323] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.923334] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.923338] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.923384] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.927298] ehci_hcd 0000:00:1a.7: debug port 1
[    0.927305] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.927319] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.941013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.941083] usb usb1: configuration #1 chosen from 1 choice
[    0.941111] hub 1-0:1.0: USB hub found
[    0.941119] hub 1-0:1.0: 4 ports detected
[    0.941177]   alloc irq_desc for 20 on node -1
[    0.941179]   alloc kstat_irqs on node -1
[    0.941183] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.941193] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.941196] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.941226] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.945122] ehci_hcd 0000:00:1d.7: debug port 1
[    0.945129] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.945142] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.961014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.961087] usb usb2: configuration #1 chosen from 1 choice
[    0.961113] hub 2-0:1.0: USB hub found
[    0.961120] hub 2-0:1.0: 6 ports detected
[    0.961184] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.961204] uhci_hcd: USB Universal Host Controller Interface driver
[    0.961228] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.961234] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.961238] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.961274] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.961301] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.961377] usb usb3: configuration #1 chosen from 1 choice
[    0.961403] hub 3-0:1.0: USB hub found
[    0.961410] hub 3-0:1.0: 2 ports detected
[    0.961461]   alloc irq_desc for 21 on node -1
[    0.961463]   alloc kstat_irqs on node -1
[    0.961468] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.961475] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.961479] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.961507] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.961546] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.961624] usb usb4: configuration #1 chosen from 1 choice
[    0.961650] hub 4-0:1.0: USB hub found
[    0.961657] hub 4-0:1.0: 2 ports detected
[    0.961708] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.961715] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.961718] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.961747] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.961776] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.961854] usb usb5: configuration #1 chosen from 1 choice
[    0.961882] hub 5-0:1.0: USB hub found
[    0.961888] hub 5-0:1.0: 2 ports detected
[    0.961935] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.961942] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.961946] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.961974] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.962002] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.962080] usb usb6: configuration #1 chosen from 1 choice
[    0.962112] hub 6-0:1.0: USB hub found
[    0.962118] hub 6-0:1.0: 2 ports detected
[    0.962166] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.962172] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.962176] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.962205] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.962232] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.962317] usb usb7: configuration #1 chosen from 1 choice
[    0.962342] hub 7-0:1.0: USB hub found
[    0.962349] hub 7-0:1.0: 2 ports detected
[    0.962452] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.965571] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.965577] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.965671] mice: PS/2 mouse device common for all mice
[    0.965792] rtc_cmos 00:03: RTC can wake from S4
[    0.965824] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.965857] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.965954] device-mapper: uevent: version 1.0.3
[    0.966045] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.966132] device-mapper: multipath: version 1.1.0 loaded
[    0.966135] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.966254] EISA: Probing bus 0 at eisa.0
[    0.966262] Cannot allocate resource for EISA slot 1
[    0.966293] EISA: Detected 0 cards.
[    0.966464] cpuidle: using governor ladder
[    0.966586] cpuidle: using governor menu
[    0.967074] TCP cubic registered
[    0.967225] NET: Registered protocol family 10
[    0.967675] lo: Disabled Privacy Extensions
[    0.968024] NET: Registered protocol family 17
[    0.968041] Bluetooth: L2CAP ver 2.13
[    0.968043] Bluetooth: L2CAP socket layer initialized
[    0.968046] Bluetooth: SCO (Voice Link) ver 0.6
[    0.968047] Bluetooth: SCO socket layer initialized
[    0.968101] Bluetooth: RFCOMM TTY layer initialized
[    0.968105] Bluetooth: RFCOMM socket layer initialized
[    0.968107] Bluetooth: RFCOMM ver 1.11
[    0.968506] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.968571] Using IPI No-Shortcut mode
[    0.968626] PM: Resume from disk failed.
[    0.968639] registered taskstats version 1
[    0.968762]   Magic number: 13:568:604
[    0.968855] rtc_cmos 00:03: setting system clock to 2009-10-01 23:33:31 UTC (1254440011)
[    0.968858] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.968860] EDD information not available.
[    1.084474] ata4.00: ATAPI: TEAC   DVD+/-RW DVW28SLC, A.06, max UDMA/33
[    1.100379] ata4.00: configured for UDMA/33
[    1.240075] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.240105] ata3: SATA link down (SStatus 0 SControl 300)
[    1.240480] ata1.00: ATA-8: FUJITSU MHZ2250BH G2, 00850009, max UDMA/100
[    1.240486] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    1.241089] ata1.00: configured for UDMA/100
[    1.256224] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2250B 0085 PQ: 0 ANSI: 5
[    1.256370] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.256408] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.256451] sd 0:0:0:0: [sda] Write Protect is off
[    1.256454] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.256476] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.256595]  sda:
[    1.263128] scsi 3:0:0:0: CD-ROM            TEAC     DVD+-RW DVW28SLC A.06 PQ: 0 ANSI: 5
[    1.279108]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.281416] Uniform CD-ROM driver Revision: 3.20
[    1.281565] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.281631] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.296143]  sda5 sda6 >
[    1.320909] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.320959] Freeing unused kernel memory: 540k freed
[    1.321326] Write protecting the kernel text: 4544k
[    1.321383] Write protecting the kernel read-only data: 1832k
[    1.365051] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    1.500020] Clocksource tsc unstable (delta = -238936629 ns)
[    1.501278] usb 2-6: configuration #1 chosen from 1 choice
[    1.532272] tg3.c:v3.99 (April 20, 2009)
[    1.532301] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.532317] tg3 0000:09:00.0: setting latency timer to 64
[    1.541058] tg3 0000:09:00.0: PME# disabled
[    1.581363] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.639086] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f68ff800-f68fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.740065] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.843297] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:21:9b:da:bb:27
[    1.843301] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
[    1.843304] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.843306] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.919429] usb 3-2: configuration #1 chosen from 1 choice
[    1.922387] hub 3-2:1.0: USB hub found
[    1.924354] hub 3-2:1.0: 3 ports detected
[    2.018852] PM: Starting manual resume from disk
[    2.018855] PM: Resume from partition 8:6
[    2.018857] PM: Checking hibernation image.
[    2.019005] PM: Resume from disk failed.
[    2.079959] EXT4-fs (sda5): barriers enabled
[    2.098452] kjournald2 starting: pid 301, dev sda5:8, commit interval 5 seconds
[    2.098476] EXT4-fs (sda5): delayed allocation enabled
[    2.098483] EXT4-fs: file extents enabled
[    2.114550] EXT4-fs: mballoc enabled
[    2.114564] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.209378] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    2.341504] usb 3-2.1: configuration #1 chosen from 1 choice
[    2.417379] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    2.547509] usb 3-2.2: configuration #1 chosen from 1 choice
[    2.554813] usbcore: registered new interface driver hiddev
[    2.557843] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input5
[    2.557965] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    2.557983] usbcore: registered new interface driver usbhid
[    2.558070] usbhid: v2.6:USB HID core driver
[    2.629379] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    2.759498] usb 3-2.3: configuration #1 chosen from 1 choice
[    2.766772] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input6
[    2.766848] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    2.814601] type=1505 audit(1254440013.344:2): operation="profile_load" pid=331 name=/sbin/dhclient3
[    2.815306] type=1505 audit(1254440013.344:3): operation="profile_load" pid=331 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    2.815703] type=1505 audit(1254440013.344:4): operation="profile_load" pid=331 name=/usr/lib/connman/scripts/dhclient-script
[    2.830322] type=1505 audit(1254440013.359:5): operation="profile_load" pid=336 name=/usr/lib/cups/backend/cups-pdf
[    2.831224] type=1505 audit(1254440013.359:6): operation="profile_load" pid=336 name=/usr/sbin/cupsd
[    2.849935] type=1505 audit(1254440013.379:7): operation="profile_load" pid=337 name=/usr/sbin/tcpdump
[    2.852003] type=1505 audit(1254440013.379:8): operation="profile_load" pid=338 name=/usr/share/gdm/guest-session/Xsession
[    2.904197] type=1505 audit(1254440013.435:9): operation="profile_load" pid=340 name=/usr/bin/evince
[    2.912209] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[324fc0003a9699c1]
[    2.914722] type=1505 audit(1254440013.443:10): operation="profile_load" pid=340 name=/usr/bin/evince-previewer
[    3.765732] udev: starting version 147
[    4.779207] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    4.840269] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    4.840386] usbcore: registered new interface driver btusb
[    5.090868] lib80211: common routines for IEEE802.11 drivers
[    5.090872] lib80211_crypt: registered algorithm 'NULL'
[    5.180288] Linux agpgart interface v0.103
[    5.209818] lp: driver loaded but no devices found
[    5.266401] Linux video capture interface: v2.00
[    5.266989] input: Dell WMI hotkeys as /devices/virtual/input/input7
[    5.280022] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    5.281085] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    5.283951] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    5.485789] sdhci: Secure Digital Host Controller Interface driver
[    5.485792] sdhci: Copyright(c) Pierre Ossman
[    6.278457] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04751/0xa00000
[    6.315498] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[    6.323084] wl: module license 'MIXED/Proprietary' taints kernel.
[    6.323088] Disabling lock debugging due to kernel taint
[    6.325354] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.325368] wl 0000:0c:00.0: setting latency timer to 64
[    6.401869] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    6.402203] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    6.402799] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input9
[    6.402856] usbcore: registered new interface driver uvcvideo
[    6.402860] USB Video Class driver (v0.1.0)
[    6.524551] [drm] Initialized drm 1.1.0 20060810
[    6.547408] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.548903] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    6.548922]   alloc irq_desc for 18 on node -1
[    6.548924]   alloc kstat_irqs on node -1
[    6.548931] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    6.550993] Registered led device: mmc0::
[    6.552040] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    6.643614] lib80211_crypt: registered algorithm 'TKIP'
[    6.644031] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[    7.026529] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.026536] i915 0000:00:02.0: setting latency timer to 64
[    7.028982]   alloc irq_desc for 29 on node -1
[    7.028986]   alloc kstat_irqs on node -1
[    7.028995] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    7.131040] integrated sync not supported
[    7.145198] Adding 8281468k swap on /dev/sda6.  Priority:-1 extents:1 across:8281468k 
[    7.248136] integrated sync not supported
[    7.255089] [drm] fb0: inteldrmfb frame buffer device
[    7.267512] acpi device:37: registered as cooling_device2
[    7.269598] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:34/input/input10
[    7.269687] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    7.269756] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    7.269877] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:39/input/input11
[    7.269936] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    7.269997] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.395094] EXT4-fs (sda5): internal journal on sda5:8
[    7.515333] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    7.516006] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.603743] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[    7.706380] [drm] LVDS-8: set mode 1280x800 e
[    7.725177] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    7.725254] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    8.329800] Console: switching to colour frame buffer device 160x50
[    9.553916] __ratelimit: 3 callbacks suppressed
[    9.553920] type=1505 audit(1254454420.084:12): operation="profile_replace" pid=776 name=/sbin/dhclient3
[    9.554661] type=1505 audit(1254454420.084:13): operation="profile_replace" pid=776 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.555062] type=1505 audit(1254454420.084:14): operation="profile_replace" pid=776 name=/usr/lib/connman/scripts/dhclient-script
[    9.556892] type=1505 audit(1254454420.084:15): operation="profile_replace" pid=777 name=/usr/lib/cups/backend/cups-pdf
[    9.557769] type=1505 audit(1254454420.088:16): operation="profile_replace" pid=777 name=/usr/sbin/cupsd
[    9.560165] type=1505 audit(1254454420.088:17): operation="profile_replace" pid=778 name=/usr/sbin/tcpdump
[    9.561993] type=1505 audit(1254454420.092:18): operation="profile_replace" pid=779 name=/usr/share/gdm/guest-session/Xsession
[    9.566907] type=1505 audit(1254454420.096:19): operation="profile_replace" pid=781 name=/usr/bin/evince
[    9.577379] type=1505 audit(1254454420.108:20): operation="profile_replace" pid=781 name=/usr/bin/evince-previewer
[    9.583309] type=1505 audit(1254454420.112:21): operation="profile_replace" pid=781 name=/usr/bin/evince-thumbnailer
[   12.698244] tg3 0000:09:00.0: PME# disabled
[   12.698485]   alloc irq_desc for 30 on node -1
[   12.698487]   alloc kstat_irqs on node -1
[   12.698519] tg3 0000:09:00.0: irq 30 for MSI/MSI-X
[   12.756961] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.311968] ppdev: user-space parallel port driver
[   14.616441] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.616445] Bluetooth: BNEP filters: protocol multicast
[   14.841418] Bridge firewalling registered
[   15.939313] integrated sync not supported
[   16.072872] integrated sync not supported
[   20.570264] integrated sync not supported
[   20.697204] integrated sync not supported
[   20.833453] integrated sync not supported
[   22.732038] eth1: no IPv6 routers present
[   47.461318] integrated sync not supported
[   47.593286] integrated sync not supported
[   47.717740] integrated sync not supported
[   49.337648] integrated sync not supported
[   58.390535] UDF-fs: No VRS found
[   58.390542] UDF-fs: No partition found (1)
[   58.487845] ISO 9660 Extensions: Microsoft Joliet Level 3
[   58.545785] ISO 9660 Extensions: RRIP_1991A
```

This is on a Dell Inspiron 1318 with no USB devices attached, just my battery and adapter. I have Bluetooth as well.

This is a picture of tty1 if it helps:
[[IMG]http://img22.imageshack.us/img22/663/20091001235331.th.jpg[/IMG]](http://img22.imageshack.us/i/20091001235331.jpg/)

---

### Post by novafluxx on 2009-10-02
Anyone...?:confused::confused::confused::confused:

---

### Post by dt_ on 2009-10-02
I also get a bunch of text that shows up before the ubuntu splash screen pops up, though it's not the same as what was shown above...

here's a picture I took:

[[IMG]http://img4.imageshack.us/img4/7553/1001092147.th.jpg[/IMG]](http://img4.imageshack.us/i/1001092147.jpg/)

also, after this finishes (~15-20 seconds), the fancy new splash screen shows up, but it takes about 25-30 seconds longer to load that! This is longer than in Jaunty! :/  What's up with that? I'm running the 64-bit version (was running 32-bit Jaunty before though)

---

### Post by dt_ on 2009-10-02
bump. anyone else getting this?

---

### Post by garba on 2009-10-02
Same problem here, I thought messages sent to the console would be hidden by the splash screen or not displayed at all, but they aren't, actually on my pc xsplash doesn't even show up at all and after a bunch of text messages about starting daemons and the like (the same you'd get booting with no splash kernel option) the gdm login screen pops up. I think it's because of the X server not getting started at an earlier time at boot. Disappointing.

---

### Post by fut21 on 2009-10-02
Make a bug repport please.

---

### Post by novafluxx on 2009-10-02
> **fut21 said:**
> Make a bug repport please.

Okay, I'll do that when I have time tonight

---

### Post by novafluxx on 2009-10-02
Apparently there are a few other threads about these issues, can we merge them?:confused:

---

### Post by FrancoNero on 2009-10-03
yeah I think at least 4 threads concerning text during boot nobody needs to see. ever

---

### Post by tsger on 2009-10-03
> **FuturePilot said:**
> ... I thought something would be hiding those by now.

Me too.  I think the new splash screen with the plain white Ubuntu logo is supposed to be hiding the boot messages.  On my system, I don't see the logo on boot-up, only on shutdown.

---

### Post by FrancoNero on 2009-10-04
I wonder if a fresh install would fix it, but I'm guessing it must be triggered by something. i get a pci/usb something error. no idea why

---

### Post by jcris on 2009-10-04
Im getting and have been getting about 20 seconds of blank screen then a few lines of loading info then another 15 seconds of ugly ubuntu splash then a fully loaded desktop.

On the plus side...When its all loaded up Im using about 92megs of Ram at idle and with Firefox and Pidgin open it only jumps to around 155Meg which is way way lower then the 250+ I was using in Jaunty. Also at shutdown its almost instant just a flash of a logo then poof.

I spose the god awefull slow bootup and the complete ugliness of the splash is a good trade  off.

---

### Post by novafluxx on 2009-10-05
> **FrancoNero said:**
> I wonder if a fresh install would fix it, but I'm guessing it must be triggered by something. i get a pci/usb something error. no idea why

I'm getting that ALSO, before I get the other boot text stuff.

There is apparently something supposed to hide these, but its apparently not working for a few of us!

A fresh install hasn't helped me at all...

---

### Post by dalonso on 2009-10-05
> **novafluxx said:**
> I'm getting that ALSO, before I get the other boot text stuff.

There is apparently something supposed to hide these, but its apparently not working for a few of us!

A fresh install hasn't helped me at all...

This was already answered in another thread, sorry but I don't remember which one.

The thing is that in the first alphas be had the following boot process:

BIOS --> usplash --> xsplash.

From the Alpha-6 and Beta-1 the usplash piece has been removed, and xsplash loads only after XOrg and all its dependencies have been loaded. In the meantime we are seeing those messages that usplash was hiding before. Developers have stated this is work-in-progress and those messages should be fixed soon.

---

### Post by novafluxx on 2009-10-05
> **dalonso said:**
> This was already answered in another thread, sorry but I don't remember which one.

The thing is that in the first alphas be had the following boot process:

BIOS --> usplash --> xsplash.

From the Alpha-6 and Beta-1 the usplash piece has been removed, and xsplash loads only after XOrg and all its dependencies have been loaded. In the meantime we are seeing those messages that usplash was hiding before. Developers have stated this is work-in-progress and those messages should be fixed soon.

We shall see! So far everything else is looking good.

---

