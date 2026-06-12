---
title: "intex tv tuner card SAA713x Philips Semiconductors not working on TV time"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by ukmad on 2011-08-06
Hi i have a new TV tuner card on my ubuntu 10.04
its intex

Provider = "Philips Semiconductors"

DiskName = "SAA713x TV Card Driver

I am unable to configure this. with the old card which went bad was working fine

The current card works fine on Windows....

tvtime -v   gave me this

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/uday/.tvtime/tvtime.xml
cpuinfo: CPU Intel(R) Pentium(R) 4 CPU 3.06GHz, family 15, model 4, stepping 9.
cpuinfo: CPU measured at 3059.494MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10706000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1024x768.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is compiz and is EWMH compliant.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 80: Intel(R) Textured Video.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/uday/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'saa7134', card 'LifeView/Typhoon FlyVIDEO2000' (bus PCI:0000:01:01.0).
videoinput: Version is 527, capabilities 5010015.
videoinput: Maximum input width: 720 pixels.
tvtime: Sampling input at 720 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (57).
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.



dmesg -- gave me this 
oot=UUID=73a18c05-61d6-4d0a-9340-68ecf9da102f ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7823040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005f7f0)
[    0.000000] Memory: 1526480k/1564608k available (4673k kernel code, 36656k reserved, 2122k data, 656k init, 655304k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 3059.178 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6118.35 BogoMIPS (lpj=12236712)
[    0.004032] Security Framework initialized
[    0.004065] AppArmor: AppArmor initialized
[    0.004077] Mount-cache hash table entries: 512
[    0.004275] Initializing cgroup subsys ns
[    0.004284] Initializing cgroup subsys cpuacct
[    0.004289] Initializing cgroup subsys memory
[    0.004299] Initializing cgroup subsys devices
[    0.004302] Initializing cgroup subsys freezer
[    0.004306] Initializing cgroup subsys net_cls
[    0.004340] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004344] CPU: L2 cache: 1024K
[    0.004347] CPU: Physical Processor ID: 0
[    0.004350] CPU: Processor Core ID: 0
[    0.004354] mce: CPU supports 4 MCE banks
[    0.004369] CPU0: Thermal monitoring enabled (TM2)
[    0.004379] using mwait in idle threads.
[    0.004390] Performance Events: no PMU driver, software events only.
[    0.004399] Checking 'hlt' instruction... OK.
[    0.024230] ACPI: Core revision 20090903
[    0.032014] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032020] ftrace: allocating 21771 entries in 43 pages
[    0.036095] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036424] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076392] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.008000] CPU: L2 cache: 1024K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.164103] CPU1: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
[    0.164123] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168031] Brought up 2 CPUs
[    0.168037] Total of 2 processors activated (12237.06 BogoMIPS).
[    0.168390] CPU0 attaching sched-domain:
[    0.168396]  domain 0: span 0-1 level SIBLING
[    0.168400]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.168408]   domain 1: span 0-1 level MC
[    0.168411]    groups: 0-1 (cpu_power = 1178)
[    0.168420] CPU1 attaching sched-domain:
[    0.168423]  domain 0: span 0-1 level SIBLING
[    0.168426]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.168433]   domain 1: span 0-1 level MC
[    0.168436]    groups: 0-1 (cpu_power = 1178)
[    0.168601] devtmpfs: initialized
[    0.168601] regulator: core version 0.5
[    0.168601] Time:  9:36:24  Date: 08/06/11
[    0.168601] NET: Registered protocol family 16
[    0.168601] Trying to unpack rootfs image as initramfs...
[    0.168601] EISA bus registered
[    0.168601] ACPI: bus type pci registered
[    0.168601] PCI: MCFG configuration 0: base d0000000 segment 0 buses 0 - 255
[    0.168601] PCI: MCFG area at d0000000 reserved in E820
[    0.168601] PCI: Using MMCONFIG for extended config space
[    0.168601] PCI: Using configuration type 1 for base access
[    0.172063] bio: create slab <bio-0> at 0
[    0.173101] ACPI: EC: Look up EC in DSDT
[    0.181434] ACPI: Interpreter enabled
[    0.181450] ACPI: (supports S0 S1 S4 S5)
[    0.181491] ACPI: Using IOAPIC for interrupt routing
[    0.189727] ACPI: No dock devices found.
[    0.189889] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.190056] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0100000-0xf017ffff]
[    0.190067] pci 0000:00:02.0: reg 14 io port: [0xc000-0xc007]
[    0.190076] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.190085] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf0180000-0xf01bffff]
[    0.190204] pci 0000:00:1d.0: reg 20 io port: [0xb000-0xb01f]
[    0.190276] pci 0000:00:1d.1: reg 20 io port: [0xb400-0xb41f]
[    0.190349] pci 0000:00:1d.2: reg 20 io port: [0xb800-0xb81f]
[    0.190419] pci 0000:00:1d.3: reg 20 io port: [0xbc00-0xbc1f]
[    0.190493] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf01c0000-0xf01c03ff]
[    0.190675] pci 0000:00:1e.2: reg 10 io port: [0xc400-0xc4ff]
[    0.190688] pci 0000:00:1e.2: reg 14 io port: [0xc800-0xc83f]
[    0.190698] pci 0000:00:1e.2: reg 18 32bit mmio: [0xf01c1000-0xf01c11ff]
[    0.190708] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xf01c2000-0xf01c20ff]
[    0.190751] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.190759] pci 0000:00:1e.2: PME# disabled
[    0.190857] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.190868] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.190875] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.190881] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0800-087f
[    0.190888] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 0290-029f
[    0.190940] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.190953] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.190968] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.190982] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.190993] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.191037] pci 0000:00:1f.2: PME# supported from D3hot
[    0.191045] pci 0000:00:1f.2: PME# disabled
[    0.191108] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.191194] pci 0000:01:01.0: reg 10 32bit mmio: [0xf0000000-0xf00003ff]
[    0.191261] pci 0000:01:01.0: supports D1 D2
[    0.191321] pci 0000:01:05.0: reg 10 io port: [0xa000-0xa0ff]
[    0.191333] pci 0000:01:05.0: reg 14 32bit mmio: [0xf0001000-0xf00010ff]
[    0.191393] pci 0000:01:05.0: supports D1 D2
[    0.191397] pci 0000:01:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.191405] pci 0000:01:05.0: PME# disabled
[    0.191460] pci 0000:00:1e.0: transparent bridge
[    0.191468] pci 0000:00:1e.0: bridge io port: [0xa000-0xafff]
[    0.191475] pci 0000:00:1e.0: bridge 32bit mmio: [0xf0000000-0xf00fffff]
[    0.191493] pci_bus 0000:00: on NUMA node 0
[    0.191501] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.191754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.205569] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.205749] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.205915] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.206081] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.206255] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.206417] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.206579] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.206751] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.206947] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.206968] vgaarb: loaded
[    0.207209] SCSI subsystem initialized
[    0.207383] libata version 3.00 loaded.
[    0.207518] usbcore: registered new interface driver usbfs
[    0.207549] usbcore: registered new interface driver hub
[    0.207606] usbcore: registered new device driver usb
[    0.207893] ACPI: WMI: Mapper loaded
[    0.207897] PCI: Using ACPI for IRQ routing
[    0.208198] NetLabel: Initializing
[    0.208203] NetLabel:  domain hash size = 128
[    0.208206] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.208231] NetLabel:  unlabeled traffic allowed by default
[    0.208375] hpet clockevent registered
[    0.208381] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.208391] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.208403] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.212384] Switching to clocksource tsc
[    0.215760] AppArmor: AppArmor Filesystem Enabled
[    0.215791] pnp: PnP ACPI init
[    0.215823] ACPI: bus type pnp registered
[    0.221012] pnp: PnP ACPI: found 15 devices
[    0.221017] ACPI: ACPI bus type pnp unregistered
[    0.221026] PnPBIOS: Disabled by ACPI PNP
[    0.221048] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.221054] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.221060] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.221065] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.221084] system 00:0c: ioport range 0x400-0x4bf could not be reserved
[    0.221097] system 00:0d: iomem range 0xd0000000-0xdfffffff has been reserved
[    0.221109] system 00:0e: iomem range 0xca400-0xcbfff has been reserved
[    0.221116] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[    0.221122] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[    0.221128] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[    0.221134] system 00:0e: iomem range 0x5f7f0000-0x5f7fffff could not be reserved
[    0.221139] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.221145] system 00:0e: iomem range 0x100000-0x5f7effff could not be reserved
[    0.221151] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.221157] system 00:0e: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.221162] system 00:0e: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.221168] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.221174] system 00:0e: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.221180] system 00:0e: iomem range 0xfff00000-0xffffffff has been reserved
[    0.221185] system 00:0e: iomem range 0xe0000-0xeffff has been reserved
[    0.256098] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.256107] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.256116] pci 0000:00:1e.0:   MEM window: 0xf0000000-0xf00fffff
[    0.256122] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.256146] pci 0000:00:1e.0: setting latency timer to 64
[    0.256154] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.256159] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.256165] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.256170] pci_bus 0000:01: resource 1 mem: [0xf0000000-0xf00fffff]
[    0.256174] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.256179] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.256248] NET: Registered protocol family 2
[    0.256435] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.257065] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.257818] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.258352] TCP: Hash tables configured (established 131072 bind 65536)
[    0.258359] TCP reno registered
[    0.258593] NET: Registered protocol family 1
[    0.258633] pci 0000:00:02.0: Boot video device
[    0.259152] cpufreq-nforce2: No nForce2 chipset.
[    0.259215] Scanning for low memory corruption every 60 seconds
[    0.259433] audit: initializing netlink socket (disabled)
[    0.259452] type=2000 audit(1312623383.258:1): initialized
[    0.271499] highmem bounce pool size: 64 pages
[    0.271510] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.274524] VFS: Disk quotas dquot_6.5.2
[    0.274649] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.275872] fuse init (API version 7.13)
[    0.276051] msgmni has been set to 1703
[    0.276465] alg: No test for stdrng (krng)
[    0.276583] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.276589] io scheduler noop registered
[    0.276593] io scheduler anticipatory registered
[    0.276597] io scheduler deadline registered
[    0.276678] io scheduler cfq registered (default)
[    0.276856] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.276903] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.277079] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.277087] ACPI: Power Button [PWRB]
[    0.277191] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.277197] ACPI: Power Button [PWRF]
[    0.277661] processor LNXCPU:00: registered as cooling_device0
[    0.277933] processor LNXCPU:01: registered as cooling_device1
[    0.283485] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.283615] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.283743] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.284251] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.284468] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.286732] brd: module loaded
[    0.287484] isapnp: Scanning for PnP cards...
[    0.287716] loop: module loaded
[    0.287881] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.288057] ata_piix 0000:00:1f.2: version 2.13
[    0.288087]   alloc irq_desc for 19 on node -1
[    0.288092]   alloc kstat_irqs on node -1
[    0.288103] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.288111] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.288177] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.288299] scsi0 : ata_piix
[    0.288424] scsi1 : ata_piix
[    0.289652] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.289658] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.290321] Fixed MDIO Bus: probed
[    0.290392] PPP generic driver version 2.4.2
[    0.290475] tun: Universal TUN/TAP device driver, 1.6
[    0.290479] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.290633] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.290661]   alloc irq_desc for 23 on node -1
[    0.290665]   alloc kstat_irqs on node -1
[    0.290674] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.290694] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.290700] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.290757] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.294688] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.294711] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf01c0000
[    0.307441] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.307628] usb usb1: configuration #1 chosen from 1 choice
[    0.307679] hub 1-0:1.0: USB hub found
[    0.307694] hub 1-0:1.0: 8 ports detected
[    0.307810] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.307837] uhci_hcd: USB Universal Host Controller Interface driver
[    0.307895] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.307909] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.307915] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.307974] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.308007] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b000
[    0.308158] usb usb2: configuration #1 chosen from 1 choice
[    0.308204] hub 2-0:1.0: USB hub found
[    0.308215] hub 2-0:1.0: 2 ports detected
[    0.308293] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.308305] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.308310] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.308370] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.308409] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    0.308560] usb usb3: configuration #1 chosen from 1 choice
[    0.308608] hub 3-0:1.0: USB hub found
[    0.308619] hub 3-0:1.0: 2 ports detected
[    0.308688]   alloc irq_desc for 18 on node -1
[    0.308692]   alloc kstat_irqs on node -1
[    0.308703] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.308712] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.308717] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.308774] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.308811] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b800
[    0.308961] usb usb4: configuration #1 chosen from 1 choice
[    0.309010] hub 4-0:1.0: USB hub found
[    0.309021] hub 4-0:1.0: 2 ports detected
[    0.309089]   alloc irq_desc for 16 on node -1
[    0.309093]   alloc kstat_irqs on node -1
[    0.309100] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.309108] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.309113] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.309165] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.309202] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000bc00
[    0.309354] usb usb5: configuration #1 chosen from 1 choice
[    0.309401] hub 5-0:1.0: USB hub found
[    0.309412] hub 5-0:1.0: 2 ports detected
[    0.309576] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.316195] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.316210] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.316366] mice: PS/2 mouse device common for all mice
[    0.316536] rtc_cmos 00:03: RTC can wake from S4
[    0.316616] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.316648] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.316848] device-mapper: uevent: version 1.0.3
[    0.336952] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.351340] device-mapper: multipath: version 1.1.0 loaded
[    0.351349] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.351603] EISA: Probing bus 0 at eisa.0
[    0.351641] EISA: Detected 0 cards.
[    0.362057] cpuidle: using governor ladder
[    0.362062] cpuidle: using governor menu
[    0.362901] TCP cubic registered
[    0.363155] NET: Registered protocol family 10
[    0.363957] lo: Disabled Privacy Extensions
[    0.364550] NET: Registered protocol family 17
[    0.364639] Using IPI No-Shortcut mode
[    0.364794] PM: Resume from disk failed.
[    0.364812] registered taskstats version 1
[    0.365107]   Magic number: 7:994:625
[    0.365218] rtc_cmos 00:03: setting system clock to 2011-08-06 09:36:24 UTC (1312623384)
[    0.365224] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.365227] EDD information not available.
[    0.373941] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.487883] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-H10A, JL02, max UDMA/33
[    0.500553] Freeing initrd memory: 7766k freed
[    0.508313] ata2.00: configured for UDMA/33
[    0.535354] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    0.535362] ata1.00: ATA-8: ST3500418AS, CC38, max UDMA/133
[    0.535367] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.551585] ata1.00: configured for UDMA/133
[    0.641085] isapnp: No Plug & Play device found
[    0.641281] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
[    0.641503] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.641584] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.641597] sd 0:0:0:0: [sda] Write Protect is off
[    0.641604] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.641652] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.642005]  sda:
[    0.645421] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10A  JL02 PQ: 0 ANSI: 5
[    0.657907] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.657912] Uniform CD-ROM driver Revision: 3.20
[    0.658035] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.658105] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.662436]  sda1 sda2 < sda5 sda6 >
[    0.698342] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.698367] Freeing unused kernel memory: 656k freed
[    0.699090] Write protecting the kernel text: 4676k
[    0.699143] Write protecting the kernel read-only data: 1840k
[    0.724414] udev: starting version 151
[    0.914391] Floppy drive(s): fd0 is 1.44M
[    0.932270] FDC 0 is a post-1991 82077
[    0.944614] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.944655] 8139cp 0000:01:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.950905] 8139too Fast Ethernet driver 0.9.28
[    0.950976]   alloc irq_desc for 21 on node -1
[    0.950981]   alloc kstat_irqs on node -1
[    0.950993] 8139too 0000:01:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.953084] eth0: RealTek RTL8139 at 0xa000, 00:14:85:e2:49:89, IRQ 21
[    1.266608] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   10.197376] Adding 19529720k swap on /dev/sda6.  Priority:-1 extents:1 across:19529720k 
[   10.212979] udev: starting version 151
[   10.255537] lp: driver loaded but no devices found
[   10.466427] Linux agpgart interface v0.103
[   10.590749] intel_rng: FWH not detected
[   10.621985] agpgart-intel 0000:00:00.0: Intel 915G Chipset
[   10.622870] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   10.654990] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   10.705595] parport_pc 00:09: reported by Plug and Play ACPI
[   10.705656] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.714792] [drm] Initialized drm 1.1.0 20060810
[   10.765121] Linux video capture interface: v2.00
[   10.785200] ppdev: user-space parallel port driver
[   10.797089] lp0: using parport0 (interrupt-driven).
[   10.800617] type=1505 audit(1312603594.934:2):  operation="profile_load" pid=551 name="/sbin/dhclient3"
[   10.801410] type=1505 audit(1312603594.934:3):  operation="profile_load" pid=551 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.801848] type=1505 audit(1312603594.934:4):  operation="profile_load" pid=551 name="/usr/lib/connman/scripts/dhclient-script"
[   10.811837] psmouse serio1: ID: 10 00 64
[   10.850893] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.850902] i915 0000:00:02.0: setting latency timer to 64
[   10.876511] [drm] set up 7M of stolen space
[   10.877693] [drm] initialized overlay support
[   10.942626] saa7130/34: v4l2 driver version 0.2.15 loaded
[   10.942693]   alloc irq_desc for 20 on node -1
[   10.942698]   alloc kstat_irqs on node -1
[   10.942709] saa7134 0000:01:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   10.942719] saa7130[0]: found at 0000:01:01.0, rev: 1, irq: 20, latency: 32, mmio: 0xf0000000
[   10.942730] saa7130[0]: subsystem: 1131:0000, board: LifeView/Typhoon FlyVIDEO2000 [card=3,insmod option]
[   10.942751] saa7130[0]: board init: gpio is 4000
[   10.942755] saa7130[0]: there are different flyvideo cards with different tuners
[   10.942757] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[   10.942760] saa7130[0]: option to override the default value.
[   10.943005] input: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:1e.0/0000:01:01.0/input/input4
[   10.943189] IRQ 20/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.045062] saa7130[0]: Huh, no eeprom present (err=-5)?
[   11.045070] i2c i2c-1: Invalid 7-bit address 0x7a
[   11.053605] fb0: inteldrmfb frame buffer device
[   11.053610] registered panic notifier
[   11.053623] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.077747] vga16fb: initializing
[   11.077754] vga16fb: mapped to 0xc00a0000
[   11.077762] vga16fb: not registering due to another framebuffer present
[   11.081002]   alloc irq_desc for 17 on node -1
[   11.081008]   alloc kstat_irqs on node -1
[   11.081022] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.081104] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   11.172047] All bytes are equal. It is not a TEA5767
[   11.172242] tuner 1-0060: chip found @ 0xc0 (saa7130[0])
[   11.208066] tuner-simple 1-0060: creating new instance
[   11.208075] tuner-simple 1-0060: type set to 55 (TCL 2002MB)
[   11.220855] Console: switching to colour frame buffer device 128x48
[   11.236225] saa7130[0]: registered device video0 [v4l2]
[   11.236285] saa7130[0]: registered device vbi0
[   11.236337] saa7130[0]: registered device radio0
[   11.385297] type=1505 audit(1312603595.518:5):  operation="profile_load" pid=701 name="/usr/share/gdm/guest-session/Xsession"
[   11.388753] type=1505 audit(1312603595.522:6):  operation="profile_replace" pid=702 name="/sbin/dhclient3"
[   11.389897] type=1505 audit(1312603595.522:7):  operation="profile_replace" pid=702 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.390343] type=1505 audit(1312603595.522:8):  operation="profile_replace" pid=702 name="/usr/lib/connman/scripts/dhclient-script"
[   11.398842] saa7134 ALSA driver for DMA sound loaded
[   11.398850] saa7130[0]/alsa: LifeView/Typhoon FlyVIDEO2000 doesn't support digital audio
[   11.433068] intel8x0_measure_ac97_clock: measured 56550 usecs (2725 samples)
[   11.433075] intel8x0: clocking to 48000
[   11.464036] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   11.469552] type=1505 audit(1312603595.602:9):  operation="profile_load" pid=704 name="/usr/bin/evince"
[   11.497610] type=1505 audit(1312603595.630:10):  operation="profile_load" pid=704 name="/usr/bin/evince-previewer"
[   11.537260] type=1505 audit(1312603595.670:11):  operation="profile_load" pid=704 name="/usr/bin/evince-thumbnailer"
[   11.596331] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   17.532047] end_request: I/O error, dev fd0, sector 0
[   17.572044] end_request: I/O error, dev fd0, sector 0
[   21.924025] eth0: no IPv6 routers present
[   50.589076] __ratelimit: 9 callbacks suppressed
[   50.589083] NetworkManager[679]: segfault at c ip 0042fd29 sp bfc6a940 error 4 in libdbus-glib-1.so.2.1.0[427000+1c000]
[ 1188.482442] lo: Disabled Privacy Extensions
[ 3434.588709] lo: Disabled Privacy Extensions
[ 3548.295112] zapping[2471]: segfault at 153801c ip 03f18f95 sp bff841b8 error 6 in libc-2.11.1.so[3e0a000+153000]
[ 3579.777433] zapping[2486]: segfault at 4a3901c ip 04608f95 sp bfbb2b68 error 6 in libc-2.11.1.so[44fa000+153000]
[ 3605.937120] zapping[2514]: segfault at 43ab01c ip 021dff95 sp bfb81e38 error 6 in libc-2.11.1.so[20d1000+153000]
[ 3625.937805] zapping[2523]: segfault at 4be301c ip 010fef95 sp bfc250a8 error 6 in libc-2.11.1.so[ff0000+153000]
[ 4909.860011] lo: Disabled Privacy Extensions
[ 5037.328030] end_request: I/O error, dev fd0, sector 0
[ 5037.356045] end_request: I/O error, dev fd0, sector 0
[ 7904.597232] zapping[3233]: segfault at 283701c ip 077bef95 sp bff40308 error 6 in libc-2.11.1.so[76b0000+153000]
[11224.733230] lo: Disabled Privacy Extensions
uday@uday-desktop:~$ 

What do i do.

---

