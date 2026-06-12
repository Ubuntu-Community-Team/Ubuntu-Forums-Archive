---
title: "Hardy - Some video issues with nvidia after Xorg loads"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by exodus_ on 2008-04-24
Good morning!

I upgraded to Hardy Heron RC a couple of days ago and it all seems to be working quite well for the most part.  However I am having a rather annoying issue with my video card that I hope someone can help me out with!

The issue is that once bootup is complete and gdm loads, or if I use startx on a virtual console, Xorg loads fine and works fine but if I try to switch to a virtual console the display goes blank and is acting as if there is so signal or the signal is out of range.  This will also happen if the display is allowed to be shut off by the power management settings or if I close the lid of the laptop.  When using the GUI I can switch to a virtual console and back to the Xorg session and it "fixes" the display issue for Xorg only.

In an effort ot fix this myself, I tried to use different settings on the console, I enabled the modules for the framebuffer (vesafb) and it also works, I can see all the bootup messages, but it still does not allow me to use virtual consoles after Xorg starts up.  Next I tried to use a generic xorg.conf that did not load the nvidia driver but instead used a generic driver.  This partially resolved the issue, but I would like to be able to use the nvidia driver.

I tried to search around for this on google/ubuntu forums/launchpad but I did not find anything helpful just a couple people with an issue that looks similar to mine and all using nvidia hardware.

Does anyone know a better search term I could use other than "nvidia issues" or "hardy virtual consoles" or does anyone know a fix or a walkthrough I could follow to help me solve this?

I'll include some information about my system here just in case it will help someone help me.

Acer Aspire 9300
AMD Turion 2.0 GHz
1GB RAM
nforce mcp51
nvidia geforce go 6100 (rev a2)

dmesg
```
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=be9e51c8-fb97-4aa4-8ac7-b123d8f4f92a ro acpi_osi=Linux vga=792
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bf10000 (usable)
[    0.000000]  BIOS-e820: 000000003bf10000 - 000000003bf1b000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bf1b000 - 000000003bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 245520) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F8240 checksum 0
[    0.000000] ACPI: RSDP 000F8240, 0024 (r3 PTLTD )
[    0.000000] ACPI: XSDT 3BF14B53, 005C (r1 ACRSYS ACRPRDCT  6040000 INNA        0)
[    0.000000] ACPI: FACP 3BF1AB21, 00F4 (r3 NVIDIA MCP51M    6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 3BF14BAF, 5F72 (r1 NVIDIA   MCP51M  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BF1BFC0, 0040
[    0.000000] ACPI: SLIC 3BF1AC89, 0176 (r1 ACRSYS ACRPRDCT  6040000 ANNI        1)
[    0.000000] ACPI: MCFG 3BF1ADFF, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 3BF1AE3B, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 3BF1AE73, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3BF1AEC3, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3BF1AEEB, 0115 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003bf10000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 245520) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003bf10000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   245520
[    0.000000] On node 0 totalpages: 245421
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1208 pages reserved
[    0.000000]   DMA zone: 2733 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3300 pages used for memmap
[    0.000000]   DMA32 zone: 238124 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 240857
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=be9e51c8-fb97-4aa4-8ac7-b123d8f4f92a ro acpi_osi=Linux vga=792
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   48.432106] time.c: Detected 2009.157 MHz processor.
[   48.432139] Console: colour dummy device 80x25
[   48.432142] console [tty0] enabled
[   48.432281] Checking aperture...
[   48.432285] CPU 0: aperture @ 8b02000000 size 32 MB
[   48.432288] Aperture too small (32 MB)
[   48.439118] No AGP bridge found
[   48.450181] Memory: 955780k/982080k available (2466k kernel code, 25904k reserved, 1309k data, 316k init)
[   48.450216] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   48.529959] Calibrating delay using timer specific routine.. 4021.63 BogoMIPS (lpj=8043270)
[   48.529994] Security Framework initialized
[   48.530001] SELinux:  Disabled at boot.
[   48.530015] AppArmor: AppArmor initialized
[   48.530021] Failure registering capabilities with primary security module.
[   48.530111] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   48.530879] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   48.531242] Mount-cache hash table entries: 256
[   48.531373] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   48.531378] CPU: L2 Cache: 512K (64 bytes/line)
[   48.531382] CPU 0/0 -> Node 0
[   48.531405] SMP alternatives: switching to UP code
[   48.531903] Freeing SMP alternatives: 24k freed
[   48.532206] Early unpacking initramfs... done
[   48.832632] ACPI: Core revision 20070126
[   48.832690] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   48.999255] Using local APIC timer interrupts.
[   49.048969] APIC timer calibration result 12557228
[   49.048971] Detected 12.557 MHz APIC timer.
[   49.049019] Brought up 1 CPUs
[   49.049131] CPU0 attaching sched-domain:
[   49.049133]  domain 0: span 01
[   49.049135]   groups: 01
[   49.049279] net_namespace: 120 bytes
[   49.049681] Time: 14:04:28  Date: 04/24/08
[   49.049711] NET: Registered protocol family 16
[   49.049872] ACPI: bus type pci registered
[   49.049937] PCI: Using configuration type 1
[   49.050803] ACPI: EC: Look up EC in DSDT
[   49.052401] ACPI: BIOS _OSI(Linux) query honored via cmdline
[   49.052671] ACPI: Interpreter enabled
[   49.052675] ACPI: (supports S0 S3 S4 S5)
[   49.052690] ACPI: Using IOAPIC for interrupt routing
[   49.053032] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   49.061395] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[   49.061404] ACPI: EC: driver started in interrupt mode
[   49.061446] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   49.062552] PCI: Transparent bridge - 0000:00:10.0
[   49.062601] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   49.062697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   49.062726] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[   49.062752] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   49.062778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   49.097077] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   49.097266] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 19 20 21 22 23) *10
[   49.097447] ACPI: PCI Interrupt Link [LNK3] (IRQs 16 17 18 19 20 21 22 23) *10
[   49.097594] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[   49.097774] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   49.097955] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   49.098137] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20 21 22 23) *10
[   49.098318] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   49.098500] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[   49.098688] ACPI: PCI Interrupt Link [LSMU] (IRQs 16 17 18 19 20 21 22 23) *11
[   49.098869] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[   49.099050] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[   49.099231] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *11
[   49.099417] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   49.099602] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   49.099784] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   49.099967] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   49.100156] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *5
[   49.100342] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0
[   49.100456] Linux Plug and Play Support v0.97 (c) Adam Belay
[   49.100483] pnp: PnP ACPI init
[   49.100493] ACPI: bus type pnp registered
[   49.103659] pnp: PnP ACPI: found 11 devices
[   49.103665] ACPI: ACPI bus type pnp unregistered
[   49.103869] PCI: Using ACPI for IRQ routing
[   49.103874] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   49.112924] NET: Registered protocol family 8
[   49.112927] NET: Registered protocol family 20
[   49.113004] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   49.113010] hpet0: 3 32-bit timers, 25000000 Hz
[   49.114061] AppArmor: AppArmor Filesystem Enabled
[   49.116890] Time: tsc clocksource has been installed.
[   49.116901] Switched to high resolution mode on CPU 0
[   49.124879] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   49.124890] system 00:02: ioport range 0x1000-0x107f has been reserved
[   49.124894] system 00:02: ioport range 0x1080-0x10ff has been reserved
[   49.124899] system 00:02: ioport range 0x1400-0x147f has been reserved
[   49.124903] system 00:02: ioport range 0x1480-0x14ff has been reserved
[   49.124907] system 00:02: ioport range 0x1800-0x187f has been reserved
[   49.124911] system 00:02: ioport range 0x1880-0x18ff has been reserved
[   49.124915] system 00:02: ioport range 0x2000-0x203f has been reserved
[   49.124922] system 00:03: ioport range 0x360-0x361 has been reserved
[   49.124926] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   49.125261] PCI: Bridge: 0000:00:02.0
[   49.125265]   IO window: disabled.
[   49.125268]   MEM window: disabled.
[   49.125271]   PREFETCH window: disabled.
[   49.125275] PCI: Bridge: 0000:00:03.0
[   49.125277]   IO window: 4000-4fff
[   49.125281]   MEM window: c4000000-c40fffff
[   49.125283]   PREFETCH window: disabled.
[   49.125287] PCI: Bridge: 0000:00:04.0
[   49.125289]   IO window: disabled.
[   49.125292]   MEM window: disabled.
[   49.125294]   PREFETCH window: disabled.
[   49.125302] PCI: Bus 5, cardbus bridge: 0000:04:06.0
[   49.125305]   IO window: 00001c00-00001cff
[   49.125309]   IO window: 00002400-000024ff
[   49.125313]   PREFETCH window: 54000000-57ffffff
[   49.125318]   MEM window: 58000000-5bffffff
[   49.125322] PCI: Bridge: 0000:00:10.0
[   49.125324]   IO window: disabled.
[   49.125328]   MEM window: c3000000-c30fffff
[   49.125331]   PREFETCH window: disabled.
[   49.125346] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   49.125352] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   49.125357] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   49.125364] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   49.125588] ACPI: PCI Interrupt Link [LNK4] enabled at IRQ 11
[   49.125600] ACPI: PCI Interrupt 0000:04:06.0[A] -> Link [LNK4] -> GSI 11 (level, low) -> IRQ 11
[   49.125654] NET: Registered protocol family 2
[   49.160882] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   49.161310] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   49.162862] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   49.163607] TCP: Hash tables configured (established 131072 bind 65536)
[   49.163614] TCP reno registered
[   49.172913] checking if image is initramfs... it is
[   49.758078] Freeing initrd memory: 7505k freed
[   49.763226] Simple Boot Flag at 0x36 set to 0x1
[   49.763764] audit: initializing netlink socket (disabled)
[   49.763777] audit(1209045868.172:1): initialized
[   49.765463] VFS: Disk quotas dquot_6.5.1
[   49.765532] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   49.765655] io scheduler noop registered
[   49.765659] io scheduler anticipatory registered
[   49.765662] io scheduler deadline registered
[   49.765752] io scheduler cfq registered (default)
[   49.765770] Boot video device is 0000:00:05.0
[   49.972057] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   49.972077] assign_interrupt_mode Found MSI capability
[   49.972100] Allocate Port Service[0000:00:02.0:pcie00]
[   49.972155] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   49.972174] assign_interrupt_mode Found MSI capability
[   49.972190] Allocate Port Service[0000:00:03.0:pcie00]
[   49.972238] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   49.972257] assign_interrupt_mode Found MSI capability
[   49.972273] Allocate Port Service[0000:00:04.0:pcie00]
[   49.995977] Real Time Clock Driver v1.12ac
[   49.996155] hpet_resources: 0xfed00000 is busy
[   49.996186] Linux agpgart interface v0.102
[   49.996190] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   49.997067] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   49.997129] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   49.997208] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   49.997521] i8042.c: Detected active multiplexing controller, rev 1.1.
[   49.997592] serio: i8042 KBD port at 0x60,0x64 irq 1
[   49.997597] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   49.997601] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   49.997604] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   49.997608] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   50.003869] mice: PS/2 mouse device common for all mice
[   50.003903] cpuidle: using governor ladder
[   50.003907] cpuidle: using governor menu
[   50.004038] NET: Registered protocol family 1
[   50.004089] registered taskstats version 1
[   50.004228]   Magic number: 4:787:81
[   50.004372] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   50.004378] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   50.004382] EDD information not available.
[   50.004402] Freeing unused kernel memory: 316k freed
[   50.007259] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   50.090231] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc20000500000, using 6144k, total 65536k
[   50.090243] vesafb: mode is 1024x768x32, linelength=4096, pages=1
[   50.090247] vesafb: scrolling: redraw
[   50.090250] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   50.090350] Console: switching to colour frame buffer device 128x48
[   50.144069] fb0: VESA VGA frame buffer device
[   50.278490] fuse init (API version 7.9)
[   50.294880] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   50.295560] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   50.298404] Marking TSC unstable due to TSC halts in idle
[   50.299274] Time: hpet clocksource has been installed.
[   50.306608] ACPI: Thermal Zone [TZS0] (53 C)
[   50.309791] ACPI: Thermal Zone [TZS1] (56 C)
[   51.034386] usbcore: registered new interface driver usbfs
[   51.034959] usbcore: registered new interface driver hub
[   51.050885] usbcore: registered new device driver usb
[   51.061348] SCSI subsystem initialized
[   51.087698] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   51.088052] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[   51.088640] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 23
[   51.089636] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   51.089642] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   51.100351] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   51.112545] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xc0004000
[   51.158170] libata version 3.00 loaded.
[   51.180251] usb usb1: configuration #1 chosen from 1 choice
[   51.191973] hub 1-0:1.0: USB hub found
[   51.203892] hub 1-0:1.0: 8 ports detected
[   51.318473] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   51.331208] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 22
[   51.345480] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   51.345486] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   51.359436] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   51.373904] ehci_hcd 0000:00:0b.1: debug port 1
[   51.388439] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   51.388451] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xc0005000
[   51.413811] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   51.429388] usb usb2: configuration #1 chosen from 1 choice
[   51.445281] hub 2-0:1.0: USB hub found
[   51.461331] hub 2-0:1.0: 8 ports detected
[   51.577782] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   51.595839] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[   51.613429] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 21 (level, high) -> IRQ 21
[   51.631876] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   51.837217] usb 2-6: new high speed USB device using ehci_hcd and address 2
[   51.993432] usb 2-6: configuration #1 chosen from 1 choice
[   52.149456] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:d3:51:23:bb
[   52.169711] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   52.190380] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   52.190704] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 20
[   52.211757] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 20 (level, high) -> IRQ 20
[   52.233178] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   52.233185] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[   52.254279] sata_nv 0000:00:0e.0: version 3.5
[   52.254285] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 20 (level, high) -> IRQ 20
[   52.275902] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   52.277064] scsi0 : sata_nv
[   52.298969] scsi1 : sata_nv
[   52.319994] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 20
[   52.341043] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 20
[   52.827854] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   52.856180] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
[   52.876743] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   52.912444] ata1.00: configured for UDMA/100
[   53.243258] ata2: SATA link down (SStatus 0 SControl 300)
[   53.274974] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[   53.300344] pata_amd 0000:00:0d.0: version 0.3.10
[   53.300389] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   53.302714] scsi2 : pata_amd
[   53.325587] scsi3 : pata_amd
[   53.347234] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[   53.368908] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[   53.870677] ata4.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, SC03, max UDMA/33
[   54.062336] ata4.00: configured for UDMA/33
[   54.084547] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D SC03 PQ: 0 ANSI: 5
[   54.114335] Driver 'sd' needs updating - please use bus_type methods
[   54.137308] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   54.160483] sd 0:0:0:0: [sda] Write Protect is off
[   54.182902] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.186966] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.211456] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   54.235190] sd 0:0:0:0: [sda] Write Protect is off
[   54.257697] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.257768] Driver 'sr' needs updating - please use bus_type methods
[   54.281125] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.304418]  sda: sda1 sda2 sda3
[   54.351572] sd 0:0:0:0: [sda] Attached SCSI disk
[   54.379932] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   54.403065] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   54.425540] sr0: scsi3-mmc drive: 16x/16x writer dvd-ram cd/rw xa/form2 cdda tray
[   54.448443] Uniform CD-ROM driver Revision: 3.20
[   54.471298] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   54.992891] Attempting manual resume
[   55.016592] swsusp: Resume From Partition 8:1
[   55.016593] PM: Checking swsusp image.
[   55.016815] PM: Resume from disk failed.
[   55.071842] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[   55.095571] ReiserFS: sda2: using ordered data mode
[   55.129282] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   55.178241] ReiserFS: sda2: checking transaction log (sda2)
[   64.341036] ReiserFS: sda2: replayed 496 transactions in 9 seconds
[   64.364886] ReiserFS: sda2: Using r5 hash to sort names
[   73.950211] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   74.022172] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   74.094060] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   74.115749] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   74.380984] nvidia: module license 'NVIDIA' taints kernel.
[   74.897030] input: Power Button (FF) as /devices/virtual/input/input2
[   74.928837] ACPI: Power Button (FF) [PWRF]
[   74.950346] input: Lid Switch as /devices/virtual/input/input3
[   74.973089] ACPI: Lid Switch [LID0]
[   75.017980] input: Sleep Button (CM) as /devices/virtual/input/input4
[   75.084617] ACPI: Sleep Button (CM) [SLPB]
[   75.119200] ACPI: WMI-Acer: Mapper loaded
[   75.155872] input: Power Button (CM) as /devices/virtual/input/input5
[   75.188466] ACPI: Power Button (CM) [PWRB]
[   75.616258] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   75.651902] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   75.675148] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/LNXVIDEO:01/input/input7
[   75.711763] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   76.954650] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 19
[   76.977615] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 19 (level, high) -> IRQ 19
[   77.000963] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   77.036005] ACPI: AC Adapter [ADP1] (on-line)
[   77.229855] ACPI: Battery Slot [BAT0] (battery present)
[   77.339263] Yenta: CardBus bridge found at 0000:04:06.0 [1025:0112]
[   77.362427] Yenta: Using CSCINT to route CSC interrupts to PCI
[   77.385238] Yenta: Routing CardBus interrupts to PCI
[   77.407675] Yenta TI: socket 0000:04:06.0, mfunc 0x013a1b22, devctl 0x64
[   77.445934] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   77.547467] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   77.570481] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 18 (level, high) -> IRQ 18
[   77.593662] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   77.697712] Yenta: ISA IRQ mask 0x04f8, PCI irq 11
[   77.720794] Socket status: 30000006
[   77.743193] Yenta: Raising subordinate bus# of parent bus (#04) from #05 to #08
[   77.765550] pcmcia: parent PCI bridge Memory window: 0xc3000000 - 0xc30fffff
[   77.809082] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   77.980655] wlan: 0.9.4
[   78.053273] ACPI: PCI Interrupt 0000:04:06.2[A] -> Link [LNK4] -> GSI 11 (level, low) -> IRQ 11
[   78.184453] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   78.261498] ath_pci: 0.9.4
[   78.285676] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 17
[   78.309884] ACPI: PCI Interrupt 0000:04:05.0[A] -> Link [LNK2] -> GSI 17 (level, high) -> IRQ 17
[   79.407570] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   79.432407] acer_acpi: Detected Acer AMW0 version 2 interface
[   79.694853] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   79.750543] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   80.000593] ath_rate_sample: 1.2 (0.9.4)
[   80.026953] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   80.053267] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   80.080426] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   80.107490] wifi0: mac 7.8 phy 4.5 radio 5.6
[   80.134256] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   80.161003] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   80.187285] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   80.213572] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   80.239461] wifi0: Use hw queue 8 for CAB traffic
[   80.264951] wifi0: Use hw queue 9 for beacons
[   80.339829] wifi0: Atheros 5212: mem=0xc3000000, irq=17
[   81.982941] loop: module loaded
[   82.095019] lp: driver loaded but no devices found
[   82.357063] Adding 1951856k swap on /dev/sda1.  Priority:-1 extents:1 across:1951856k
[   88.624555] ReiserFS: sda2: Removing [272 1992 0x0 SD]..done
[   88.624671] ReiserFS: sda2: There were 1 uncompleted unlinks/truncates. Completed
[  103.571789] ReiserFS: sda3: found reiserfs format "3.6" with standard journal
[  103.571803] ReiserFS: sda3: using ordered data mode
[  103.576372] ReiserFS: sda3: journal params: device sda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  103.577730] ReiserFS: sda3: checking transaction log (sda3)
[  103.598003] ReiserFS: sda3: Using r5 hash to sort names
[  104.043308] ip_tables: (C) 2000-2006 Netfilter Core Team
[  104.815412] No dock devices found.
[  105.129546] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (1 cpu cores) (version 2.20.00)
[  105.129583] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[  105.129586] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[  105.129587] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[  105.129589] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[  111.193642] eth0: no link during initialization.
[  111.334793] ppdev: user-space parallel port driver
[  111.432299] audit(1209045930.607:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5424 profile="/usr/sbin/cupsd" namespace="default"
[  111.812341] Bluetooth: Core ver 2.11
[  111.813054] NET: Registered protocol family 31
[  111.813058] Bluetooth: HCI device and connection manager initialized
[  111.813062] Bluetooth: HCI socket layer initialized
[  111.857174] Bluetooth: L2CAP ver 2.9
[  111.857179] Bluetooth: L2CAP socket layer initialized
[  111.921686] Bluetooth: RFCOMM socket layer initialized
[  111.922067] Bluetooth: RFCOMM TTY layer initialized
[  111.922070] Bluetooth: RFCOMM ver 1.8
[  112.918908] Clocksource tsc unstable (delta = -80792904 ns)
[  134.270957] NET: Registered protocol family 10
[  134.271482] lo: Disabled Privacy Extensions
[  134.272161] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  139.518071] NET: Registered protocol family 17
[  140.386618] ath0: no IPv6 routers present
[  142.084959] cdrom: sr0: mrw address space DMA selected
[  145.001751] ISO 9660 Extensions: Microsoft Joliet Level 3
[  145.035301] ISOFS: changing to secondary root
[  154.875832] ath0: no IPv6 routers present

```

lspci -vvnn
```

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f3] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR-

00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: c4000000-c40fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:05.0 VGA compatible controller [0300]: nVidia Corporation MCP51 PCI-X GeForce Go 6100 [10de:0247] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 10
	Region 4: I/O ports at 3040 [size=64]
	Region 5: I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at c0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at c0005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device [f025:0112]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 3080 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1) (prog-if 85 [Master SecO PriO])
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at 30b0 [size=8]
	Region 1: I/O ports at 30a4 [size=4]
	Region 2: I/O ports at 30a8 [size=8]
	Region 3: I/O ports at 30a0 [size=4]
	Region 4: I/O ports at 3090 [size=16]
	Region 5: Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=04, subordinate=08, sec-latency=64
	Memory behind bridge: c3000000-c30fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR+
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 30b8 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

04:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device [1468:0418]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at c3000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

04:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at c3010000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 54000000-57fff000 (prefetchable)
	Memory window 1: 58000000-5bfff000
	I/O window 0: 00001c00-00001cff
	I/O window 1: 00002400-000024ff


	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

04:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
	Subsystem: Acer Incorporated [ALI] Unknown device [1025:0112]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (1750ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at c3012000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```

Xorg.log
```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux capricorn 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64
Build Date: 15 April 2008  05:41:18PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 24 10:05:31 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f3 card 1025,0112 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1025,0112 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1025,0112 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1025,0112 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1025,0112 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1025,0112 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1025,0112 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1025,0112 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0247 card 1025,0112 rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 1025,0112 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 1025,0112 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1025,0112 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:3: chip 10de,0271 card 1025,0112 rev a3 class 0b,40,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1025,0112 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1025,0112 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card f025,0112 rev f1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1025,0112 rev f1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 1025,0112 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1025,0112 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 04:05:0: chip 168c,001a card 1468,0418 rev 01 class 02,00,00 hdr 00
(II) PCI: 04:06:0: chip 104c,8039 card 1c00,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 04:06:2: chip 104c,803b card 1025,0112 rev 00 class 01,80,00 hdr 80
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xc4000000 - 0xc40fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,8), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xc3000000 - 0xc30fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (4:6:0), (4,5,8), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(0:5:0) nVidia Corporation MCP51 PCI-X GeForce Go 6100 rev 162, Mem @ 0xc2000000/24, 0xd0000000/28, 0xc1000000/24
(--) PCI: (0:10:3) nVidia Corporation MCP51 PMU rev 163, Mem @ 0xc0040000/18
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xc3012000 - 0xc3012fff (0x1000) MX[B]
	[1] -1	0	0xc3000000 - 0xc300ffff (0x10000) MX[B]
	[2] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[3] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[4] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[5] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[6] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[7] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[8] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[12] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[13] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[14] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[15] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[16] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[17] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[18] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[19] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc3012000 - 0xc3012fff (0x1000) MX[B]
	[1] -1	0	0xc3000000 - 0xc300ffff (0x10000) MX[B]
	[2] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[3] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[4] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[5] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[6] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[7] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[8] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[12] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[13] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[14] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[15] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[16] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[17] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[18] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[19] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc3012000 - 0xc3012fff (0x1000) MX[B]
	[5] -1	0	0xc3000000 - 0xc300ffff (0x10000) MX[B]
	[6] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[8] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[9] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[10] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[11] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[12] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[18] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[19] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[20] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[21] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[22] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[23] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[24] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[25] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:34:02 PST 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:53:48 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:10:3) found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc3012000 - 0xc3012fff (0x1000) MX[B]
	[5] -1	0	0xc3000000 - 0xc300ffff (0x10000) MX[B]
	[6] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[8] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[9] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[10] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[11] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[12] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[18] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[19] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[20] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[21] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[22] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[23] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[24] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[25] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc3012000 - 0xc3012fff (0x1000) MX[B]
	[5] -1	0	0xc3000000 - 0xc300ffff (0x10000) MX[B]
	[6] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[8] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[9] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[10] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[11] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[12] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[21] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[22] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[23] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[24] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[25] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[26] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[27] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[28] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 6100 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.28.53.08
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 6100 at PCI:0:5:0:
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 310.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (114, 114); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc3012000 - 0xc3012fff (0x1000) MX[B]
	[5] -1	0	0xc3000000 - 0xc300ffff (0x10000) MX[B]
	[6] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[8] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[9] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[10] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[11] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[12] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[21] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[22] -1	0	0x000030a0 - 0x000030a3 (0x4) IX[B]
	[23] -1	0	0x000030a8 - 0x000030af (0x8) IX[B]
	[24] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[25] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[26] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[27] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[28] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "1440x900"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 8
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1440x900"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

uname
```

Linux capricorn 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

```

xorg.conf
```
# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation MCP51 PCI-X GeForce Go 6100"
	Driver		"nvidia"
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-72
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation MCP51 PCI-X GeForce Go 6100"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```


Thanks for any help :)

---

### Post by Peter09 on 2008-04-24
Hardy comes with envyNG in the repositories. 

Install envyNG then in a terminal type envyng -t.

This will allow you to install the nvidia drivers. From there you can use the nvidia settings tool in System->Administration

PC

---

### Post by exodus_ on 2008-04-24
> **Peter09 said:**
> Hardy comes with envyNG in the repositories. 

Install envyNG then in a terminal type envyng -t.

This will allow you to install the nvidia drivers. From there you can use the nvidia settings tool in System->Administration

PC

Thanks for the reply but I don't use envy and I already have the driver for nvidia installed and I can already use nvidia-settings.

This issue only started once I did a release upgrade to hardy (or on a clean hardy install)

---

### Post by BattlePanic on 2008-04-26
After upgrading to Hardy I ran into this problem and although I think I may have found a workable solution, I'm still a bit confused by the whole thing.

To start, here is my hardware:
Sony Vaio VGN-FS675P/H laptop w/ 1 gig of RAM
Nvidia GeForce Go 6200 Video card

Initially the upgrade was failing at the beginning, delivering a vague error message explaining that installed unofficial packages could be the cause.  Removing the nvidia-glx package seemed to allow the upgrade to work.

Now upgraded to Hardy, I rebooted but got a message from the X server that that nvidia driver wasn't working and I as a result had to operate in low resolution.  I checked in System -> Administration -> Hardware Drivers.  This configuration window told me that the Nvidia drivers were enabled but 'not in use'.

In my case, I think the issue comes down to two packages: nvidia-glx and nvidia-glx-new.  If nvidia-glx-new is installed on my system, System -> Administration -> Hardware Drivers shows that nvidia drivers and enabled and 'in use'.  The problem with this setup is that I'm unable to see anything on any of the other virtual consoles.  If I remove nvidia-glx-new and replace it with nvidia-glx things seem to and I can also view all of the virtual consoles but now the Hardware Drivers window shows that nvidia driver are enabled but 'not in use'.  Perhaps it refers only to the nvidia-glx-new drivers?

If the nvidia drivers are not currently in use then how do I find out which drivers I'm using?  I have included my X.org log file and it seems to suggest that I am using an nvidia driver and not just a vesa driver.  I could be wrong on this point though.

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux ordinator 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 26 11:23:42 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV43 [GeForce Go 6200/6400]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2590 card 104d,81b7 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2591 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,2668 card 104d,81bb rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,2658 card 104d,81b9 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 104d,81b9 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 104d,81b9 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 104d,81b9 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 104d,81b9 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2641 card 104d,81b9 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 104d,81b9 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 104d,81b9 rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0167 card 104d,81c2 rev a1 class 03,00,00 hdr 00
(II) PCI: 06:03:0: chip 104c,ac8e card 2400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 06:03:2: chip 104c,802e card 104d,818f rev 00 class 0c,00,10 hdr 80
(II) PCI: 06:03:3: chip 104c,ac8f card 104d,8190 rev 00 class 01,80,00 hdr 80
(II) PCI: 06:04:0: chip 8086,4220 card 8086,2751 rev 05 class 02,80,00 hdr 00
(II) PCI: 06:08:0: chip 8086,1068 card 104d,81d0 rev 03 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x90000000 - 0xafffffff (0x20000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,10), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xb00fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:3:0), (6,7,10), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[1] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce Go 6200/6400] rev 161, Mem @ 0xa0000000/24, 0xc0000000/28, 0x90000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[1] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[2] -1	0	0xb0005000 - 0xb0005fff (0x1000) MX[B]
	[3] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[4] -1	0	0xb0004000 - 0xb00047ff (0x800) MX[B]
	[5] -1	0	0x80004000 - 0x800043ff (0x400) MX[B]
	[6] -1	0	0x80000000 - 0x80003fff (0x4000) MX[B]
	[7] -1	0	0x90000000 - 0x90ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xa0000000 - 0xa0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[11] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[12] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[18] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[19] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[20] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[1] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[2] -1	0	0xb0005000 - 0xb0005fff (0x1000) MX[B]
	[3] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[4] -1	0	0xb0004000 - 0xb00047ff (0x800) MX[B]
	[5] -1	0	0x80004000 - 0x800043ff (0x400) MX[B]
	[6] -1	0	0x80000000 - 0x80003fff (0x4000) MX[B]
	[7] -1	0	0x90000000 - 0x90ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xa0000000 - 0xa0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[11] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[12] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[18] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[19] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[20] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[5] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[6] -1	0	0xb0005000 - 0xb0005fff (0x1000) MX[B]
	[7] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[8] -1	0	0xb0004000 - 0xb00047ff (0x800) MX[B]
	[9] -1	0	0x80004000 - 0x800043ff (0x400) MX[B]
	[10] -1	0	0x80000000 - 0x80003fff (0x4000) MX[B]
	[11] -1	0	0x90000000 - 0x90ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xa0000000 - 0xa0ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[17] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.05  Tue Jan 22 20:11:30 PST 2008
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Wacom driver level: 47-0.7.9-8 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  96.43.05  Tue Jan 22 19:38:46 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[5] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[6] -1	0	0xb0005000 - 0xb0005fff (0x1000) MX[B]
	[7] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[8] -1	0	0xb0004000 - 0xb00047ff (0x800) MX[B]
	[9] -1	0	0x80004000 - 0x800043ff (0x400) MX[B]
	[10] -1	0	0x80000000 - 0x80003fff (0x4000) MX[B]
	[11] -1	0	0x90000000 - 0x90ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xa0000000 - 0xa0ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[17] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[5] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[6] -1	0	0xb0005000 - 0xb0005fff (0x1000) MX[B]
	[7] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[8] -1	0	0xb0004000 - 0xb00047ff (0x800) MX[B]
	[9] -1	0	0x80004000 - 0x800043ff (0x400) MX[B]
	[10] -1	0	0x80000000 - 0x80003fff (0x4000) MX[B]
	[11] -1	0	0x90000000 - 0x90ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xa0000000 - 0xa0ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[20] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[21] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "UseEdidDpi" "False"
(**) NVIDIA(0): Option "DPI" "96 x 96"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 6200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.23.22
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 6200 at PCI:1:0:0:
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 310.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(**) NVIDIA(0): DPI set to (96, 96); computed from "DPI" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x90000000 - 0x90ffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xa0000000 - 0xa0ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xb0007000 - 0xb0007fff (0x1000) MX[B]
	[8] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[9] -1	0	0xb0005000 - 0xb0005fff (0x1000) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0004000 - 0xb00047ff (0x800) MX[B]
	[12] -1	0	0x80004000 - 0x800043ff (0x400) MX[B]
	[13] -1	0	0x80000000 - 0x80003fff (0x4000) MX[B]
	[14] -1	0	0x90000000 - 0x90ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xa0000000 - 0xa0ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[23] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[24] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1280x800"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "SHMConfig" "true"
(**) Option "LeftEdge" "130"
(**) Option "RightEdge" "840"
(**) Option "TopEdge" "130"
(**) Option "BottomEdge" "640"
(**) Option "HorizScrollDelta" "0"
(**) Option "FingerLow" "14"
(**) Option "FingerHigh" "15"
(**) Option "MaxTapTime" "100"
(**) Option "ClickTime" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1280x800"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
couldn't enable device 3
couldn't enable device 4
couldn't enable device 5
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1280x800"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
couldn't enable device 3
couldn't enable device 4
couldn't enable device 5
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1280x800"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
couldn't enable device 3
couldn't enable device 4
couldn't enable device 5
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1280x800"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
couldn't enable device 3
couldn't enable device 4
couldn't enable device 5
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1280x800"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
couldn't enable device 3
couldn't enable device 4
couldn't enable device 5
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1280x800"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
couldn't enable device 3
couldn't enable device 4
couldn't enable device 5
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1280x800"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
couldn't enable device 3
couldn't enable device 4
couldn't enable device 5
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

---

### Post by charly4711 on 2008-05-16
> **BattlePanic said:**
> ```
(II) NVIDIA dlloader X Driver  96.43.05  Tue Jan 22 19:38:46 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

```

This means you ARE in fact using the nvidia driver. The version number also says, you are using nvidia-glx (vs. nvidia-glx-legacy or nvidia-glx-new). No idea why the restricted module manager thinks it's not in use.
You should be able to use compiz/desktop effects, are you?

(Ahhh, and congrats that solves the blank tty issue for you. I'm stuck with nvidia-glx-new and black ttys)

---

