---
title: "[SOLVED] Kubuntu 8.04 LTS boots extremely slow at &amp;quot;Reading files needed to boot&amp;quot;"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by erythrocyte on 2008-05-20
Hi!

I have a clean install of Kubuntu 8.04 (KDE 3.5.9) (32 bit) on an Intel P4 (1.7GHz), 256 MB RAM desktop system with a native 1024x768 resolution monitor. Everything was working fine, until a few days ago when I installed a couple of updates. After that, my boot-up has gone painfully slow (in excess of 4 minutes - from hitting enter at GRUB to the KDM login screen). Normally this time would be around 1-2 minutes max.

I looked around and found a couple of bugs  on launchpad [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/197228](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/197228) & [https://answers.launchpad.net/ubuntu/+question/29321](https://answers.launchpad.net/ubuntu/+question/29321) (related to clocksource=hpet). Unfortunately, adding clocksource=hpet to my kernel line hasn't helped at all.

After removing 'quiet' and 'splash' from my kernel lines, I noticed that most of the delay happens at the "Reading files needed to boot" stage. It takes nearly 2 minutes!

Attached is the default settings bootchart.

dmesg
```

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000eff0000 (usable)
[    0.000000]  BIOS-e820: 000000000eff0000 - 000000000eff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000eff3000 - 000000000f000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 239MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 61424) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    61424
[    0.000000]   HighMem     61424 ->    61424
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    61424
[    0.000000] On node 0 totalpages: 61424
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 447 pages used for memmap
[    0.000000]   Normal zone: 56881 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7570 checksum 0
[    0.000000] ACPI: RSDP 000F7570, 0014 (r0 JETWAY)
[    0.000000] ACPI: RSDT 0EFF3000, 0028 (r1 JETWAY AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 0EFF3040, 0074 (r1 JETWAY AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 0EFF30C0, 38B3 (r1 JETWAY AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 0EFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0f000000:efc00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 60945
[    0.000000] Kernel command line: root=UUID=081d11c3-243e-4f1d-b0a1-c981407284e6 ro quiet splash
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1700.135 MHz processor.
[   26.976450] Console: colour VGA+ 80x25
[   26.976459] console [tty0] enabled
[   26.976791] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.977084] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   26.987357] Memory: 231204k/245696k available (2157k kernel code, 13932k reserved, 998k data, 364k init, 0k highmem)
[   26.987372] virtual kernel memory layout:
[   26.987373]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   26.987375]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.987377]     vmalloc : 0xcf800000 - 0xff7fe000   ( 767 MB)
[   26.987379]     lowmem  : 0xc0000000 - 0xceff0000   ( 239 MB)
[   26.987381]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   26.987382]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   26.987384]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   26.987390] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.987456] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   27.067449] Calibrating delay using timer specific routine.. 3403.83 BogoMIPS (lpj=6807675)
[   27.067497] Security Framework initialized
[   27.067511] SELinux:  Disabled at boot.
[   27.067539] AppArmor: AppArmor initialized
[   27.067546] Failure registering capabilities with primary security module.
[   27.067560] Mount-cache hash table entries: 512
[   27.067832] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   27.067857] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   27.067862] CPU: L2 cache: 256K
[   27.067867] CPU: Hyper-Threading is disabled
[   27.067870] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[   27.067893] Compat vDSO mapped to ffffe000.
[   27.067922] Checking 'hlt' instruction... OK.
[   27.084146] SMP alternatives: switching to UP code
[   27.086990] Freeing SMP alternatives: 11k freed
[   27.087254] Early unpacking initramfs... done
[   27.656550] ACPI: Core revision 20070126
[   27.656669] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.658988] ACPI: setting ELCR to 0200 (from 0e20)
[   27.660881] CPU0: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[   27.660894] SMP motherboard not detected.
[   27.767212] Brought up 1 CPUs
[   27.767246] CPU0 attaching sched-domain:
[   27.767252]  domain 0: span 01
[   27.767255]   groups: 01
[   27.767685] net_namespace: 64 bytes
[   27.767701] Booting paravirtualized kernel on bare hardware
[   27.768776] Time: 15:55:54  Date: 05/20/08
[   27.768844] NET: Registered protocol family 16
[   27.769336] EISA bus registered
[   27.769388] ACPI: bus type pci registered
[   27.782169] PCI: PCI BIOS revision 2.10 entry at 0xfb3a0, last bus=1
[   27.782173] PCI: Using configuration type 1
[   27.782176] Setting up standard PCI resources
[   27.796064] ACPI: EC: Look up EC in DSDT
[   27.801169] ACPI: Interpreter enabled
[   27.801178] ACPI: (supports S0 S1 S4 S5)
[   27.801205] ACPI: Using PIC for interrupt routing
[   27.810369] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.810689] Enabling SiS 96x SMBus.
[   27.811950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.841421] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   27.841583] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   27.841743] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   27.841891] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   27.842040] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   27.842188] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   27.842336] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   27.842487] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   27.842795] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.842866] pnp: PnP ACPI init
[   27.842890] ACPI: bus type pnp registered
[   27.848944] pnp: PnP ACPI: found 14 devices
[   27.848951] ACPI: ACPI bus type pnp unregistered
[   27.848960] PnPBIOS: Disabled by ACPI PNP
[   27.849479] PCI: Using ACPI for IRQ routing
[   27.849488] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.911074] NET: Registered protocol family 8
[   27.911079] NET: Registered protocol family 20
[   27.911268] AppArmor: AppArmor Filesystem Enabled
[   27.915053] Time: tsc clocksource has been installed.
[   27.923177] system 00:00: iomem range 0xd5800-0xd7fff has been reserved
[   27.923183] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   27.923187] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   27.923191] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   27.923196] system 00:00: iomem range 0xeff0000-0xeffffff could not be reserved
[   27.923203] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   27.923207] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   27.923211] system 00:00: iomem range 0x100000-0xefeffff could not be reserved
[   27.923216] system 00:00: iomem range 0xffee0000-0xffefffff has been reserved
[   27.923220] system 00:00: iomem range 0xfffe0000-0xfffeffff has been reserved
[   27.923225] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   27.923230] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   27.923244] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   27.923249] system 00:02: ioport range 0x800-0x805 has been reserved
[   27.954155] PCI: Bridge: 0000:00:01.0
[   27.954162]   IO window: c000-cfff
[   27.954171]   MEM window: e0000000-e00fffff
[   27.954178]   PREFETCH window: d8000000-dfffffff
[   27.954225] NET: Registered protocol family 2
[   27.991202] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   27.991630] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   27.991724] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   27.991814] TCP: Hash tables configured (established 8192 bind 8192)
[   27.991818] TCP reno registered
[   28.003328] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   28.510842]  it is
[   29.096703] Freeing initrd memory: 7702k freed
[   29.097867] audit: initializing netlink socket (disabled)
[   29.097901] audit(1211298955.004:1): initialized
[   29.101888] VFS: Disk quotas dquot_6.5.1
[   29.102070] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.102466] io scheduler noop registered
[   29.102472] io scheduler anticipatory registered
[   29.102475] io scheduler deadline registered
[   29.102514] io scheduler cfq registered (default)
[   29.102619] Boot video device is 0000:01:00.0
[   29.103240] isapnp: Scanning for PnP cards...
[   29.457282] isapnp: No Plug & Play device found
[   29.573280] Real Time Clock Driver v1.12ac
[   29.573485] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.573705] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.574221] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.576115] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.577144] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.579015] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.579167] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   29.579410] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   29.579796] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.579806] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.586408] mice: PS/2 mouse device common for all mice
[   29.586699] EISA: Probing bus 0 at eisa.0
[   29.586714] Cannot allocate resource for EISA slot 1
[   29.586727] Cannot allocate resource for EISA slot 4
[   29.586747] EISA: Detected 0 cards.
[   29.586754] cpuidle: using governor ladder
[   29.586757] cpuidle: using governor menu
[   29.586961] NET: Registered protocol family 1
[   29.587025] Using IPI No-Shortcut mode
[   29.587106] registered taskstats version 1
[   29.587290]   Magic number: 8:976:942
[   29.587427]   hash matches device ptyyd
[   29.587540] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   29.587543] EDD information not available.
[   29.588417] Freeing unused kernel memory: 364k freed
[   29.605125] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   31.198865] fuse init (API version 7.9)
[   31.233739] ACPI: Fan [FAN] (on)
[   31.250117] ACPI: Thermal Zone [THRM] (40 C)
[   32.592607] usbcore: registered new interface driver usbfs
[   32.592659] usbcore: registered new interface driver hub
[   32.612548] usbcore: registered new device driver usb
[   32.618398] SCSI subsystem initialized
[   32.741379] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   32.741786] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   32.741794] PCI: setting IRQ 11 as level-triggered
[   32.741799] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   32.741831] ohci_hcd 0000:00:02.2: OHCI Host Controller
[   32.742688] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[   32.742734] ohci_hcd 0000:00:02.2: irq 11, io mem 0xe0100000
[   32.784417] USB Universal Host Controller Interface driver v3.0
[   32.798652] usb usb1: configuration #1 chosen from 1 choice
[   32.798703] hub 1-0:1.0: USB hub found
[   32.798717] hub 1-0:1.0: 3 ports detected
[   32.808081] libata version 3.00 loaded.
[   32.844869] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   32.900821] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   32.900830] PCI: setting IRQ 10 as level-triggered
[   32.900836] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   32.900867] ohci_hcd 0000:00:02.3: OHCI Host Controller
[   32.900947] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[   32.900977] ohci_hcd 0000:00:02.3: irq 10, io mem 0xe0101000
[   32.958549] usb usb2: configuration #1 chosen from 1 choice
[   32.958598] hub 2-0:1.0: USB hub found
[   32.958614] hub 2-0:1.0: 3 ports detected
[   32.966524] Floppy drive(s): fd0 is 1.44M
[   32.988076] FDC 0 is a post-1991 82077
[   33.061037] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   33.061049] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   33.061072] uhci_hcd 0000:00:09.0: UHCI Host Controller
[   33.061166] uhci_hcd 0000:00:09.0: new USB bus registered, assigned bus number 3
[   33.061209] uhci_hcd 0000:00:09.0: irq 11, io base 0x0000e000
[   33.061475] usb usb3: configuration #1 chosen from 1 choice
[   33.061523] hub 3-0:1.0: USB hub found
[   33.061534] hub 3-0:1.0: 2 ports detected
[   33.164715] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   33.164726] ACPI: PCI Interrupt 0000:00:09.1[B] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   33.164752] uhci_hcd 0000:00:09.1: UHCI Host Controller
[   33.164824] uhci_hcd 0000:00:09.1: new USB bus registered, assigned bus number 4
[   33.164861] uhci_hcd 0000:00:09.1: irq 10, io base 0x0000e400
[   33.165106] usb usb4: configuration #1 chosen from 1 choice
[   33.165161] hub 4-0:1.0: USB hub found
[   33.165173] hub 4-0:1.0: 2 ports detected
[   33.268956] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   33.268966] ACPI: PCI Interrupt 0000:00:09.2[C] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   33.268994] ehci_hcd 0000:00:09.2: EHCI Host Controller
[   33.269082] ehci_hcd 0000:00:09.2: new USB bus registered, assigned bus number 5
[   33.269167] ehci_hcd 0000:00:09.2: irq 11, io mem 0xe0102000
[   33.280087] ehci_hcd 0000:00:09.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.280384] usb usb5: configuration #1 chosen from 1 choice
[   33.280436] hub 5-0:1.0: USB hub found
[   33.280452] hub 5-0:1.0: 4 ports detected
[   33.384527] 8139cp 0000:00:0d.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   33.384540] 8139cp 0000:00:0d.0: Try the "8139too" driver instead.
[   33.388057] pata_sis 0000:00:02.5: version 0.5.2
[   33.391705] 8139too Fast Ethernet driver 0.9.28
[   33.393939] scsi0 : pata_sis
[   33.396169] scsi1 : pata_sis
[   33.397320] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14
[   33.397326] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15
[   33.717253] ata1.00: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
[   33.717263] ata1.00: 78165360 sectors, multi 16: LBA 
[   33.717309] ata1.01: ATAPI: HL-DT-ST GCE-8525B, 1.02, max UDMA/33
[   33.717333] ata1.00: limited to UDMA/33 due to 40-wire cable
[   33.733084] ata1.00: configured for UDMA/33
[   33.896212] ata1.01: configured for UDMA/33
[   34.175595] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   34.320986] usb 3-2: configuration #1 chosen from 1 choice
[   34.395881] ata2.00: ATAPI: TSSTcorpCD/DVDW SH-W162C, TS11, max UDMA/33
[   34.395926] ata2.01: ATAPI: LG       DVD-ROM DRD-8160B, 1.01, max UDMA/33
[   34.591699] ata2.00: configured for UDMA/33
[   34.755704] ata2.01: configured for UDMA/33
[   34.755999] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
[   34.756472] scsi 0:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8525B  1.02 PQ: 0 ANSI: 5
[   34.757677] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-W162C TS11 PQ: 0 ANSI: 5
[   34.758399] scsi 1:0:1:0: CD-ROM            LG       DVD-ROM DRD8160B 1.01 PQ: 0 ANSI: 5
[   34.763344] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   34.764257] eth0: RealTek RTL8139 at 0xe800, 00:08:a1:7b:bd:e0, IRQ 11
[   34.764263] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   34.838854] Driver 'sd' needs updating - please use bus_type methods
[   34.839058] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   34.839086] sd 0:0:0:0: [sda] Write Protect is off
[   34.839091] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.839128] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.839316] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   34.839337] sd 0:0:0:0: [sda] Write Protect is off
[   34.839342] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.839375] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.839385]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   34.869175]  sda1 sda2 < sda5 sda6 sda7 sda8 >
[   35.059944] sd 0:0:0:0: [sda] Attached SCSI disk
[   35.076624] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   35.076671] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   35.076704] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   35.076735] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   35.080089] sr0: scsi3-mmc drive: 40x/52x writer cd/rw xa/form2 cdda tray
[   35.080101] Uniform CD-ROM driver Revision: 3.20
[   35.080239] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   35.093124] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   35.093259] sr 1:0:0:0: Attached scsi CD-ROM sr1
[   35.095888] sr2: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   35.096031] sr 1:0:1:0: Attached scsi CD-ROM sr2
[   51.344208] Attempting manual resume
[   51.344218] swsusp: Resume From Partition 8:6
[   51.344221] PM: Checking swsusp image.
[   51.344592] PM: Resume from disk failed.
[   51.515719] kjournald starting.  Commit interval 5 seconds
[   51.515761] EXT3-fs: mounted filesystem with ordered data mode.
[  191.530937] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  191.818703] Linux agpgart interface v0.102
[  192.702326] agpgart: Detected SiS chipset - id:1616
[  192.718182] agpgart: AGP aperture is 128M @ 0xd0000000
[  193.040688] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  193.261627] input: Power Button (FF) as /devices/virtual/input/input2
[  193.269875] ACPI: Power Button (FF) [PWRF]
[  193.270070] input: Power Button (CM) as /devices/virtual/input/input3
[  193.285817] ACPI: Power Button (CM) [PWRB]
[  193.340840] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1080
[  193.514077] input: PC Speaker as /devices/platform/pcspkr/input/input4
[  195.261661] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  203.824197] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[  204.860869] parport_pc 00:0a: reported by Plug and Play ACPI
[  204.860930] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  207.460916] NET: Registered protocol family 10
[  207.461406] lo: Disabled Privacy Extensions
[  208.187272] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 5
[  208.187284] PCI: setting IRQ 5 as level-triggered
[  208.187289] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKF] -> GSI 5 (level, low) -> IRQ 5
[  208.509209] intel8x0_measure_ac97_clock: measured 54930 usecs
[  208.509217] intel8x0: clocking to 48000
[  209.796749] lp0: using parport0 (interrupt-driven).
[  209.894598] Adding 506008k swap on /dev/sda6.  Priority:-1 extents:1 across:506008k
[  211.399256] EXT3 FS on sda7, internal journal
[  211.771984] device-mapper: uevent: version 1.0.3
[  211.772054] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[  218.143764] eth0: no IPv6 routers present
[  220.216383] kjournald starting.  Commit interval 5 seconds
[  220.216688] EXT3 FS on sda8, internal journal
[  220.216699] EXT3-fs: mounted filesystem with ordered data mode.
[  221.173949] ip_tables: (C) 2000-2006 Netfilter Core Team
[  222.004362] PPP generic driver version 2.4.2
[  222.067127] NET: Registered protocol family 17
[  222.137655] NET: Registered protocol family 24
[  223.184833] No dock devices found.
[  227.325336] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  227.325347] apm: overridden by ACPI.
[  228.044205] ppdev: user-space parallel port driver
[  228.490697] audit(1211279355.006:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=16465 profile="/usr/sbin/cupsd" namespace="default"
[  253.593217] Bluetooth: Core ver 2.11
[  253.595870] NET: Registered protocol family 31
[  253.595882] Bluetooth: HCI device and connection manager initialized
[  253.595895] Bluetooth: HCI socket layer initialized
[  253.876765] Bluetooth: L2CAP ver 2.9
[  253.876777] Bluetooth: L2CAP socket layer initialized
[  254.505626] Bluetooth: RFCOMM socket layer initialized
[  254.505682] Bluetooth: RFCOMM TTY layer initialized
[  254.505685] Bluetooth: RFCOMM ver 1.8

```

dmesg | grep error
```

[   27.656669] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

```

lspci -vvnn
```

00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 650/M650 Host [1039:0650] (rev 01)
	Subsystem: Silicon Integrated Systems [SiS] 650/M650 Host [1039:0650]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 32
	Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) [1039:0001] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: e0000000-e00fffff
	Prefetchable memory behind bridge: d8000000-dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO] [1039:0961]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 0
	Region 4: I/O ports at 1080 [size=32]

00:02.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 07) (prog-if 10 [OHCI])
	Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin D routed to IRQ 11
	Region 0: Memory at e0100000 (32-bit, non-prefetchable) [size=4K]

00:02.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 07) (prog-if 10 [OHCI])
	Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at e0101000 (32-bit, non-prefetchable) [size=4K]

00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev d0) (prog-if 80 [Master])
	Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step) [1039:5513]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 128
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at 4000 [size=16]

00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
	Subsystem: Avance Logic Inc. Unknown device [4005:36db]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (13000ns min, 2750ns max)
	Interrupt: pin C routed to IRQ 5
	Region 0: I/O ports at d800 [size=256]
	Region 1: I/O ports at dc00 [size=128]
	Capabilities: <access denied>

00:09.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 62) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 4: I/O ports at e000 [size=32]
	Capabilities: <access denied>

00:09.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 62) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 10
	Region 4: I/O ports at e400 [size=32]
	Capabilities: <access denied>

00:09.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 65) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. USB 2.0 [1106:3104]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 128 bytes
	Interrupt: pin C routed to IRQ 11
	Region 0: Memory at e0102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0b.0 Communication controller [0780]: Analog Devices SM56 PCI modem [11d4:1805]
	Subsystem: Analog Devices SM56 PCI modem [11d4:1805]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (250ns min, 63750ns max)
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at e0103000 (32-bit, prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Unknown device [4554:434e]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at e800 [size=256]
	Region 1: Memory at e0104000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter [1039:6325] (prog-if 00 [VGA controller])
	Subsystem: Silicon Integrated Systems [SiS] 740 [315 graphics core] on ECS K7SOM+ motherboard [1039:6325]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 10
	BIST result: 00
	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at e0000000 (32-bit, non-prefetchable) [size=128K]
	Region 2: I/O ports at c000 [size=128]
	Capabilities: <access denied>


```

cat /etc/usplash.conf
```

# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1024
yres=768

```

uname -a
```

Linux 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```

cat /etc/X11/xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
            Modes       "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

cat /boot/grub/menu.lst
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=081d11c3-243e-4f1d-b0a1-c981407284e6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=081d11c3-243e-4f1d-b0a1-c981407284e6 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=081d11c3-243e-4f1d-b0a1-c981407284e6 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

sudo fdisk /dev/sda (edited)
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe264e264

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/sda2            1276        4865    28836675    5  Extended
/dev/sda5            1276        2550    10241406    7  HPFS/NTFS
/dev/sda6            2551        2613      506016   82  Linux swap / Solaris
/dev/sda7            2614        3828     9759456   83  Linux
/dev/sda8            3829        4865     8329671   83  Linux

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda7 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
proc /proc proc defaults 0 0
/dev/scd1 /media/cdrom0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/scd0 /media/cdrom1 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/scd2 /media/cdrom2 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,sync,dev,exec,suid 0 0
/dev/sda1 /media/sda1 vfat defaults,umask=003,uid=1000,gid=1000 0 0
/dev/sda5 /media/sda5 ntfs defaults,umask=003,uid=1000,gid=1000 0 0
/dev/sda6 none swap defaults 0 0
/dev/sda8 /media/sda8 ext3 defaults 0 0

```

df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.3G  3.2G  5.7G  36% /
varrun                117M  104K  117M   1% /var/run
varlock               117M     0  117M   0% /var/lock
udev                  117M   64K  117M   1% /dev
devshm                117M     0  117M   0% /dev/shm
lrm                   117M   38M   80M  32% /lib/modules/2.6.24-16-generic/volatile
/dev/sda1             9.8G  1.8G  8.1G  18% /media/sda1
/dev/sda5             9.8G  3.8G  6.1G  39% /media/sda5
/dev/sda8             7.9G  1.5G  6.0G  20% /media/sda8

```

Any help would be greatly appreciated! Thanks!

---

### Post by erythrocyte on 2008-05-22
This problem got resolved for me, after a reinstallation.

---

