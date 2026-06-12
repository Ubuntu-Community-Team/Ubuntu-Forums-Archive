---
title: "Ubuntu Server hangs about 2200 seconds before continuing the boot process."
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by supidupi on 2008-06-16
I have got a AMD Geode LX processor with 500 MHz with 256MB RAM and I installed Ubuntu Server 8.04.
During the boot of Ubuntu Server 8.04 my box hangs for about 2200 seconds and continues with "Console: colour VGA+ 80x25".
When I used Ubuntu Server 7.10 the time till the message "Console: colour VGA+ 80x25" was shown was only about 20 seconds.

Does anybody know how to find out why the CPU needs so long to bring up the message "Console: colour VGA+ 80x25" in Ubuntu 8.04?
Does anybody have an idea where to look at to trace back this behavior to decrease the time Ubuntu needs to boot?

I attached the content of the /var/log/dmesg file.

Thank you for your help!!!



[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000efc0000 (usable)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 239MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 61376) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    61376
[    0.000000]   HighMem     61376 ->    61376
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    61376
[    0.000000] On node 0 totalpages: 61376
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 447 pages used for memmap
[    0.000000]   Normal zone: 56833 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0efc0000:f1030000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 000000000009f000
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 60897
[    0.000000] Kernel command line: root=UUID=5fd62ba6-a315-4509-bc6c-adab9d28a2d5 ro quiet splash
[    0.000000] No local APIC present or hardware disabled
[    0.000000] mapped APIC to ffffb000 (011ec000)
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 498.074 MHz processor.
[ 2156.150470] Console: colour VGA+ 80x25
[ 2156.150486] console [tty0] enabled
[ 2156.150645] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 2156.151298] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 2156.191235] Memory: 231584k/245504k available (2157k kernel code, 13340k reserved, 998k data, 364k init, 0k highmem)
[ 2156.191289] virtual kernel memory layout:
[ 2156.191297]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[ 2156.191307]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[ 2156.191317]     vmalloc : 0xcf800000 - 0xff7fe000   ( 767 MB)
[ 2156.191327]     lowmem  : 0xc0000000 - 0xcefc0000   ( 239 MB)
[ 2156.191337]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[ 2156.191347]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[ 2156.191357]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[ 2156.191383] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 2156.191520] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[ 2156.271536] Calibrating delay using timer specific routine.. 997.87 BogoMIPS (lpj=1995753)
[ 2156.271637] Security Framework initialized
[ 2156.271661] SELinux:  Disabled at boot.
[ 2156.271742] AppArmor: AppArmor initialized
[ 2156.271763] Failure registering capabilities with primary security module.
[ 2156.271805] Mount-cache hash table entries: 512
[ 2156.272183] CPU: After generic identify, caps: 0088a93d c0c0a13d 00000000 00000000 00000000 00000000 00000000 00000000
[ 2156.272231] CPU: L1 I Cache: 64K (32 bytes/line), D cache 64K (32 bytes/line)
[ 2156.272249] CPU: L2 Cache: 128K (32 bytes/line)
[ 2156.272263] CPU: After all inits, caps: 0088a93d c0c0a13d 00000000 00000000 00000000 00000000 00000000 00000000
[ 2156.272307] Compat vDSO mapped to ffffe000.
[ 2156.272341] Checking 'hlt' instruction... OK.
[ 2156.287638] SMP alternatives: switching to UP code
[ 2156.291357] Freeing SMP alternatives: 11k freed
[ 2156.291900] Early unpacking initramfs... done
[ 2158.189558] ACPI: Core revision 20070126
[ 2158.189681] ACPI Exception (tbxface-0629): AE_NO_ACPI_TABLES, While loading namespace from ACPI tables [20070126]
[ 2158.189710] ACPI: Unable to load the System Description Tables
[ 2158.189890] CPU0: AMD Geode(TM) Integrated Processor by AMD PCS stepping 02
[ 2158.189917] SMP motherboard not detected.
[ 2158.189930] Local APIC not detected. Using dummy APIC emulation.
[ 2158.190115] Brought up 1 CPUs
[ 2158.190202] CPU0 attaching sched-domain:
[ 2158.190217]  domain 0: span 01
[ 2158.190228]   groups: 01
[ 2158.190973] net_namespace: 64 bytes
[ 2158.190995] Booting paravirtualized kernel on bare hardware
[ 2158.193606] Time: 14:13:36  Date: 06/15/08
[ 2158.193694] NET: Registered protocol family 16
[ 2158.194567] EISA bus registered
[ 2158.200462] PCI: PCI BIOS revision 2.10 entry at 0xfa6d0, last bus=0
[ 2158.200479] PCI: Using configuration type 1
[ 2158.200491] Setting up standard PCI resources
[ 2158.211669] ACPI: Interpreter disabled.
[ 2158.211685] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 2158.211824] pnp: PnP ACPI: disabled
[ 2158.211841] PnPBIOS: Scanning system for PnP BIOS support...
[ 2158.212132] PnPBIOS: Found PnP BIOS installation structure at 0xc00fb030
[ 2158.212156] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb060, dseg 0xf0000
[ 2158.215158] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[ 2158.216141] PCI: Probing PCI hardware
[ 2158.216164] PCI: Probing PCI hardware (bus 00)
[ 2158.226874] PCI: Using IRQ router NatSemi [1022/2090] at 0000:00:0f.0
[ 2158.258696] NET: Registered protocol family 8
[ 2158.258710] NET: Registered protocol family 20
[ 2158.258960] AppArmor: AppArmor Filesystem Enabled
[ 2158.259129] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[ 2158.259152] system 00:07: iomem range 0xfffc0000-0xffffffff could not be reserved
[ 2158.259174] system 00:07: iomem range 0xfee00000-0xfee0ffff has been reserved
[ 2158.259196] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[ 2158.259234] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[ 2158.259256] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[ 2158.259277] system 00:08: iomem range 0xf8000-0xfbfff could not be reserved
[ 2158.259298] system 00:08: iomem range 0xfc000-0xfffff could not be reserved
[ 2158.261161] NET: Registered protocol family 2
[ 2158.262665] Time: tsc clocksource has been installed.
[ 2158.294968] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[ 2158.296189] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[ 2158.296412] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[ 2158.296645] TCP: Hash tables configured (established 8192 bind 8192)
[ 2158.296660] TCP reno registered
[ 2158.307210] checking if image is initramfs... it is
[ 2162.048570] Freeing initrd memory: 7104k freed
[ 2162.050692] audit: initializing netlink socket (disabled)
[ 2162.050732] audit(1213539219.864:1): initialized
[ 2162.061079] VFS: Disk quotas dquot_6.5.1
[ 2162.062206] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 2162.062781] io scheduler noop registered
[ 2162.062795] io scheduler anticipatory registered
[ 2162.062808] io scheduler deadline registered
[ 2162.062879] io scheduler cfq registered (default)
[ 2162.062964] Boot video device is 0000:00:01.1
[ 2162.062988] PCI: Firmware left 0000:00:0d.0 e100 interrupts enabled, disabling
[ 2162.063018] PCI: Firmware left 0000:00:0e.0 e100 interrupts enabled, disabling
[ 2162.077948] isapnp: Scanning for PnP cards...
[ 2162.434842] isapnp: No Plug & Play device found
[ 2162.576456] Real Time Clock Driver v1.12ac
[ 2162.576867] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 2162.577169] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 2162.577587] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 2162.578005] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[ 2162.578433] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[ 2162.579877] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 2162.580760] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 2162.581724] 00:11: ttyS2 at I/O 0x3e8 (irq = 11) is a 16550A
[ 2162.582663] 00:12: ttyS3 at I/O 0x2e8 (irq = 10) is a 16550A
[ 2162.586319] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 2162.586651] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 2162.587058] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[ 2162.587075] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[ 2162.587891] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 2162.601141] mice: PS/2 mouse device common for all mice
[ 2162.601625] EISA: Probing bus 0 at eisa.0
[ 2162.601653] Cannot allocate resource for EISA slot 1
[ 2162.601714] Cannot allocate resource for EISA slot 6
[ 2162.601751] EISA: Detected 0 cards.
[ 2162.601765] cpuidle: using governor ladder
[ 2162.601778] cpuidle: using governor menu
[ 2162.602499] NET: Registered protocol family 1
[ 2162.602619] Using IPI No-Shortcut mode
[ 2162.602720] registered taskstats version 1
[ 2162.603151]   Magic number: 12:777:232
[ 2162.603252]   hash matches device ttyv2
[ 2162.603490] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 2162.603504] EDD information not available.
[ 2162.603899] Freeing unused kernel memory: 364k freed
[ 2163.725754] fuse init (API version 7.9)
[ 2164.173653] thermal: Unknown symbol acpi_processor_set_thermal_limit
[ 2165.987427] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[ 2165.987447] e100: Copyright(c) 1999-2006 Intel Corporation
[ 2165.987629] PCI: setting IRQ 15 as level-triggered
[ 2165.987646] PCI: Found IRQ 15 for device 0000:00:0d.0
[ 2165.987819] PCI: Sharing IRQ 15 with 0000:00:0f.3
[ 2165.987956] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[ 2166.336309] e100: eth0: e100_probe: addr 0xeffff000, irq 15, MAC addr 00:01:05:02:65:23
[ 2166.336437] PCI: setting IRQ 7 as level-triggered
[ 2166.336453] PCI: Found IRQ 7 for device 0000:00:0e.0
[ 2166.336750] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[ 2166.644339] e100: eth1: e100_probe: addr 0xefffe000, irq 7, MAC addr 00:01:05:02:65:24
[ 2166.857071] SCSI subsystem initialized
[ 2167.166993] usbcore: registered new interface driver usbfs
[ 2167.167093] usbcore: registered new interface driver hub
[ 2167.194875] usbcore: registered new device driver usb
[ 2167.371129] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 2167.371510] PCI: Found IRQ 7 for device 0000:00:0f.4
[ 2167.371732] PCI: Sharing IRQ 7 with 0000:00:0f.5
[ 2167.371809] PCI: Setting latency timer of device 0000:00:0f.4 to 64
[ 2167.371850] ohci_hcd 0000:00:0f.4: OHCI Host Controller
[ 2167.372517] ohci_hcd 0000:00:0f.4: new USB bus registered, assigned bus number 1
[ 2167.372573] ohci_hcd 0000:00:0f.4: irq 7, io mem 0xefffd000
[ 2167.390191] libata version 3.00 loaded.
[ 2167.433231] usb usb1: configuration #1 chosen from 1 choice
[ 2167.433351] hub 1-0:1.0: USB hub found
[ 2167.433381] hub 1-0:1.0: 4 ports detected
[ 2167.535580] PCI: Found IRQ 7 for device 0000:00:0f.5
[ 2167.535780] PCI: Sharing IRQ 7 with 0000:00:0f.4
[ 2167.535881] PCI: Setting latency timer of device 0000:00:0f.5 to 64
[ 2167.535922] ehci_hcd 0000:00:0f.5: EHCI Host Controller
[ 2167.536027] ehci_hcd 0000:00:0f.5: new USB bus registered, assigned bus number 2
[ 2167.536331] ehci_hcd 0000:00:0f.5: irq 7, io mem 0xefffc000
[ 2167.546700] ehci_hcd 0000:00:0f.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 2167.547186] usb usb2: configuration #1 chosen from 1 choice
[ 2167.547304] hub 2-0:1.0: USB hub found
[ 2167.547332] hub 2-0:1.0: 4 ports detected
[ 2167.651279] pata_amd 0000:00:0f.2: version 0.3.10
[ 2167.656066] scsi0 : pata_amd
[ 2167.659157] scsi1 : pata_amd
[ 2167.659325] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfd00 irq 14
[ 2167.659344] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfd08 irq 15
[ 2167.823104] ata1.00: ATA-4: TRANSCEND, 20070418, max UDMA/66
[ 2167.823127] ata1.00: 15924384 sectors, multi 0: LBA 
[ 2167.823184] ata1.00: limited to UDMA/33 due to 40-wire cable
[ 2167.838958] ata1.00: configured for UDMA/33
[ 2167.839312] ata2: port disabled. ignoring.
[ 2167.839694] scsi 0:0:0:0: Direct-Access     ATA      TRANSCEND        2007 PQ: 0 ANSI: 5
[ 2169.317983] Driver 'sd' needs updating - please use bus_type methods
[ 2169.318266] sd 0:0:0:0: [sda] 15924384 512-byte hardware sectors (8153 MB)
[ 2169.318325] sd 0:0:0:0: [sda] Write Protect is off
[ 2169.318342] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2169.318426] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2169.318616] sd 0:0:0:0: [sda] 15924384 512-byte hardware sectors (8153 MB)
[ 2169.318668] sd 0:0:0:0: [sda] Write Protect is off
[ 2169.318685] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2169.318767] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2169.318790]  sda: sda1 sda2
[ 2169.337182] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2169.382063] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 2169.723968] Attempting manual resume
[ 2169.723984] swsusp: Resume From Partition 8:2
[ 2169.723996] PM: Checking swsusp image.
[ 2169.724878] PM: Resume from disk failed.
[ 2169.807544] kjournald starting.  Commit interval 5 seconds
[ 2169.807596] EXT3-fs: mounted filesystem with ordered data mode.
[ 2182.436709] PCI: Found IRQ 15 for device 0000:00:01.1
[ 2182.436815] PCI: Sharing IRQ 15 with 0000:00:01.2
[ 2182.437502] lxfb 0000:00:01.1: 16384 KB of video memory at 0xec000000
[ 2182.521306] AMD Geode RNG detected
[ 2182.582587] Console: switching to colour frame buffer device 80x30
[ 2182.592251] fb0: Geode LX frame buffer device
[ 2182.668636] cs5535_gpio: base=0x6100 mask=0xb003c66 major=253
[ 2183.968037] input: PC Speaker as /devices/platform/pcspkr/input/input1
[ 2184.463672] PCI: Found IRQ 15 for device 0000:00:0f.3
[ 2184.463775] PCI: Sharing IRQ 15 with 0000:00:0d.0
[ 2184.463980] PCI: Setting latency timer of device 0000:00:0f.3 to 64
[ 2184.464204] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2184.465317] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x7c,Last value=0xff80ffff
[ 2184.466502] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2184.467606] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x7e,Last value=0xff80ffff
[ 2184.468774] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2184.469899] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2184.476758] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x0,Last value=0xff80ffff
[ 2184.497075] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2184.520062] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x7c,Last value=0xff80ffff
[ 2184.545928] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2184.574131] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x7e,Last value=0xff80ffff
[ 2184.659350] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 2184.767099] Clocksource tsc unstable (delta = 88011563 ns)
[ 2184.771081] Time: pit clocksource has been installed.
[ 2185.310755] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2185.339435] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2185.368002] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x1c,Last value=0xff80ffff
[ 2185.769065] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2185.797775] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x0,Last value=0xff80ffff
[ 2185.826440] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2185.854989] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x7c,Last value=0xff80ffff
[ 2185.883657] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2185.912213] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x7e,Last value=0xff80ffff
[ 2185.940898] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2185.969458] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x3c,Last value=0xff80ffff
[ 2187.114194] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2187.142843] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2187.171409] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x1c,Last value=0xff80ffff
[ 2187.601864] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2061: AC'97 0 does not respond - RESET
[ 2187.602023] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2187.630662] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x7c,Last value=0xff80ffff
[ 2187.659343] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:87: Failure writing to cs5535 codec
[ 2187.687909] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:113: Failure reading codec reg 0x7e,Last value=0xff80ffff
[ 2187.716607] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2070: AC'97 0 access is not valid [0xffffffff], removing mixer.
[ 2188.393722] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/cs5535audio/../../alsa-kernel/pci/cs5535audio/cs5535audio.c:167: mixer failed
[ 2188.545687] cs5535audio: probe of 0000:00:0f.3 failed with error -5
[ 2188.545885] PCI: Found IRQ 15 for device 0000:00:01.2
[ 2188.545956] PCI: Sharing IRQ 15 with 0000:00:01.1
[ 2188.546145] geode-aes: GEODE AES engine enabled.
[ 2190.589746] NET: Registered protocol family 10
[ 2190.590902] lo: Disabled Privacy Extensions
[ 2195.800401] loop: module loaded
[ 2196.013750] lp: driver loaded but no devices found
[ 2197.317783] Adding 634556k swap on /dev/sda2.  Priority:-1 extents:1 across:634556k
[ 2197.494358] EXT3 FS on sda1, internal journal
[ 2198.567806] ip_tables: (C) 2000-2006 Netfilter Core Team

---

