---
title: "Can't get online with latest kernel"
date: 2008-07-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by thelostsoul on 2008-07-31
Okay, this is something that was kinda discussed, but I'm pretty sure it's a different issue.

I have a Linksys WUSB11 v2.6 wireless card, and I have my interfaces configured to manual properly, so it connects fine in the older 24 kernels, but not in the latest 26 one.  I am posting from the latest stable Ubuntu Studio (24 kernel), and if I use my intrepid installation, I can boot into the older kernels and it still has internet, but when I try to boot into the 26 one, there's no connection, though it does detect that I have a connection.

If I try to ping 192.168.1.1 it says host unreachable, and pinging google.com continues to try, but fails.  

This has got me pretty stumped...anyone have any ideas?

---

### Post by pressureman on 2008-07-31
Does the 26 kernel even detect your wireless card? Try running iwconfig to quickly check if the interface is present and has wireless extensions recognised. If not, you really need to paste the output of your dmesg here.

---

### Post by thelostsoul on 2008-07-31
Yes, iwconfig does detect the card, and as far as I can tell, it all looks good to me, but I'm not positive on that.

I'll boot into that kernel now and try that dmesg command now though...

---

### Post by thelostsoul on 2008-07-31
```
name@name-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"myrouternameishere"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:06:25:92:53:ED   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=45/100  Signal level=47/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

name@name-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.26-4-generic (buildd@palmer) (gcc version 4.3.1 (Ubuntu 4.3.1-5ubuntu1) ) #1 SMP Mon Jul 14 18:39:53 UTC 2008 (Ubuntu 2.6.26-4.11-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at [c00f56f0] 000f56f0
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 36 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4060 pages, LIFO batch:0
[    0.000000]   Normal zone: 1116 pages used for memmap
[    0.000000]   Normal zone: 125844 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000F7590, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 1FFF3000, 0030 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF30C0, 3C93 (r1 INTELR AWRDACPI     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: DBGP 1FFF6E00, 0034 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 1FFF6D80, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 41000 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129904
[    0.000000] Kernel command line: root=UUID=9390b02f-b8bd-413a-aa63-1d55ff6dc5d9 ro splash vga=773 
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2524.036 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 505916k/524224k available (2460k kernel code, 17792k reserved, 1113k data, 368k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc74000 - 0xfffff000   (3628 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xe0800000 - 0xff3fe000   ( 491 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.004000]       .init : 0xc0485000 - 0xc04e1000   ( 368 kB)
[    0.004000]       .data : 0xc03670f6 - 0xc047d540   (1113 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03670f6   (2460 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.084009] Calibrating delay using timer specific routine.. 5053.75 BogoMIPS (lpj=10107507)
[    0.084034] Security Framework initialized
[    0.084046] SELinux:  Disabled at boot.
[    0.084068] AppArmor: AppArmor initialized <NULL>
[    0.084076] AppArmor: Registered secondary security module capability
[    0.084081] Capability LSM initialized as secondary
[    0.084094] Mount-cache hash table entries: 512
[    0.084268] Initializing cgroup subsys ns
[    0.084277] Initializing cgroup subsys cpuacct
[    0.084282] Initializing cgroup subsys memory
[    0.084302] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.084309] CPU: L2 cache: 512K
[    0.084314] CPU: Hyper-Threading is disabled
[    0.084331] Checking 'hlt' instruction... OK.
[    0.100560] SMP alternatives: switching to UP code
[    0.110766] Freeing SMP alternatives: 18k freed
[    0.110784] ACPI: Core revision 20080321
[    0.124160] ENABLING IO-APIC IRQs
[    0.124363] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.164042] CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 07
[    0.168010] Brought up 1 CPUs
[    0.168010] Total of 1 processors activated (5053.75 BogoMIPS).
[    0.168010] CPU0 attaching sched-domain:
[    0.168010]  domain 0: span 0
[    0.168010]   groups: 0
[    0.168010] net_namespace: 660 bytes
[    0.168010] Booting paravirtualized kernel on bare hardware
[    0.168010] NET: Registered protocol family 16
[    0.168010] EISA bus registered
[    0.168010] ACPI: bus type pci registered
[    0.192012] PCI: PCI BIOS revision 2.10 entry at 0xfb160, last bus=2
[    0.192012] PCI: Using configuration type 1 for base access
[    0.192012] Setting up standard PCI resources
[    0.212013] ACPI: EC: Look up EC in DSDT
[    0.217504] ACPI: Interpreter enabled
[    0.217515] ACPI: (supports S0 S1 S3 S4 S5)
[    0.217537] ACPI: Using IOAPIC for interrupt routing
[    0.222650] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.223091] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.223093] * this clock source is slow. If you are sure your timer does not have
[    0.223094] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.223149] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.223157] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.223447] PCI: Transparent bridge - 0000:00:1e.0
[    0.223477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.223772] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.246388] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.246542] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.246689] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.246834] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.246979] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.247127] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.247274] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.247420] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.247625] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.247677] pnp: PnP ACPI init
[    0.247690] ACPI: bus type pnp registered
[    0.251893] pnp: PnP ACPI: found 15 devices
[    0.251903] ACPI: ACPI bus type pnp unregistered
[    0.251912] PnPBIOS: Disabled by ACPI PNP
[    0.252308] PCI: Using ACPI for IRQ routing
[    0.252536] NET: Registered protocol family 8
[    0.252542] NET: Registered protocol family 20
[    0.252584] NetLabel: Initializing
[    0.252589] NetLabel:  domain hash size = 128
[    0.252592] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.252609] NetLabel:  unlabeled traffic allowed by default
[    0.252662] AppArmor: AppArmor Filesystem Enabled 
[    0.252687] ACPI: RTC can wake from S4
[    0.252726] system 00:00: ioport range 0x280-0x287 has been reserved
[    0.252741] system 00:01: iomem range 0xf0000-0xf3fff could not be reserved
[    0.252747] system 00:01: iomem range 0xf4000-0xf7fff could not be reserved
[    0.252753] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
[    0.252758] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
[    0.252764] system 00:01: iomem range 0x1fff0000-0x1fffffff could not be reserved
[    0.252770] system 00:01: iomem range 0x0-0x9ffff could not be reserved
[    0.252775] system 00:01: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.252782] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.252788] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.252794] system 00:01: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.252801] system 00:01: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.252807] system 00:01: iomem range 0xe0000-0xeffff has been reserved
[    0.252818] system 00:04: ioport range 0x400-0x4bf could not be reserved
[    0.252829] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.252835] system 00:05: ioport range 0x800-0x87f has been reserved
[    0.283411] PCI: Bridge: 0000:00:01.0
[    0.283416]   IO window: disabled.
[    0.283424]   MEM window: 0xec000000-0xedffffff
[    0.283430]   PREFETCH window: 0x00000000e4000000-0x00000000ebffffff
[    0.283439] PCI: Bridge: 0000:00:1e.0
[    0.283444]   IO window: c000-cfff
[    0.283451]   MEM window: 0xee000000-0xee0fffff
[    0.283457]   PREFETCH window: disabled.
[    0.283478] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.283496] NET: Registered protocol family 2
[    0.283623] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.283857] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.283981] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.284122] TCP: Hash tables configured (established 16384 bind 16384)
[    0.284128] TCP reno registered
[    0.284228] NET: Registered protocol family 1
[    0.284374] checking if image is initramfs... it is
[    0.784053] Switched to high resolution mode on CPU 0
[    1.112410] Freeing initrd memory: 8184k freed
[    1.113231] audit: initializing netlink socket (disabled)
[    1.113262] type=2000 audit(1217516568.112:1): initialized
[    1.118200] Total HugeTLB memory allocated, 0
[    1.120569] VFS: Disk quotas dquot_6.5.1
[    1.120677] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.120802] msgmni has been set to 1004
[    1.120937] io scheduler noop registered
[    1.120943] io scheduler anticipatory registered
[    1.120947] io scheduler deadline registered
[    1.120965] io scheduler cfq registered (default)
[    1.121067] pci 0000:01:00.0: Boot video device
[    1.121422] isapnp: Scanning for PnP cards...
[    1.475614] isapnp: No Plug & Play device found
[    1.506487] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.506636] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.507516] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.509383] brd: module loaded
[    1.509471] input: Macintosh mouse button emulation as /class/input/input0
[    1.509617] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.512616] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.512626] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.512994] mice: PS/2 mouse device common for all mice
[    1.513141] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.513163] rtc0: alarms up to one month
[    1.513305] EISA: Probing bus 0 at eisa.0
[    1.513345] EISA: Detected 0 cards.
[    1.513351] cpuidle: using governor ladder
[    1.513355] cpuidle: using governor menu
[    1.513745] aufs 20080609
[    1.514277] Using IPI No-Shortcut mode
[    1.514441] registered taskstats version 1
[    1.514573] rtc_cmos 00:07: setting system clock to 2008-07-31 15:02:49 UTC (1217516569)
[    1.514581] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.514585] EDD information not available.
[    1.515136] Freeing unused kernel memory: 368k freed
[    1.546264] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.737210] fuse init (API version 7.9)
[    1.821765] uvesafb: failed to execute /sbin/v86d
[    1.821772] uvesafb: make sure that the v86d helper is installed and executable
[    1.821776] uvesafb: Getting VBE info block failed (eax=0x4f00, err=-2)
[    1.821779] uvesafb: vbe_init() failed with -22
[    1.821785] uvesafb: probe of uvesafb.0 failed with error -22
[    1.896257] ACPI: ACPI0007:00 is registered as cooling_device0
[    1.896266] ACPI: Processor [CPU0] (supports 2 throttling states)
[    1.942867] ACPI: LNXTHERM:01 is registered as thermal_zone0
[    1.964760] ACPI: Thermal Zone [THRM] (40 C)
[    3.484161] usbcore: registered new interface driver usbfs
[    3.484203] usbcore: registered new interface driver hub
[    3.484258] usbcore: registered new device driver usb
[    3.492714] USB Universal Host Controller Interface driver v3.0
[    3.492788] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.492801] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.492806] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.493104] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.493142] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[    3.493253] usb usb1: configuration #1 chosen from 1 choice
[    3.493288] hub 1-0:1.0: USB hub found
[    3.493299] hub 1-0:1.0: 2 ports detected
[    3.542417] No dock devices found.
[    3.588510] SCSI subsystem initialized
[    3.599289] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.599308] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.599313] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.599352] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.599387] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    3.599489] usb usb2: configuration #1 chosen from 1 choice
[    3.599522] hub 2-0:1.0: USB hub found
[    3.599534] hub 2-0:1.0: 2 ports detected
[    3.641200] libata version 3.00 loaded.
[    3.700196] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.700213] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.700218] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.700248] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.700282] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    3.700383] usb usb3: configuration #1 chosen from 1 choice
[    3.700417] hub 3-0:1.0: USB hub found
[    3.700427] hub 3-0:1.0: 2 ports detected
[    3.804237] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[    3.804262] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.804266] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.804297] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.808203] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    3.808219] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee100000
[    3.836025] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.848010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.848124] usb usb4: configuration #1 chosen from 1 choice
[    3.848160] hub 4-0:1.0: USB hub found
[    3.848175] hub 4-0:1.0: 6 ports detected
[    3.904049] hub 1-0:1.0: unable to enumerate USB device on port 2
[    3.953997] ata_piix 0000:00:1f.1: version 2.12
[    3.954016] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    3.954090] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.954617] scsi0 : ata_piix
[    3.955578] scsi1 : ata_piix
[    3.956597] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    3.956601] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.121189] ata1.00: ATA-5: WDC WD1200AB-00CBA1, 04.07B04, max UDMA/100
[    4.121197] ata1.00: 234441648 sectors, multi 16: LBA 
[    4.137110] ata1.00: configured for UDMA/100
[    4.308295] ata2.00: ATAPI: HL-DT-ST GCE-8400B, 1.06, max MWDMA2
[    4.308319] ata2.01: ATAPI: TOSHIBA DVD-ROM SD-M1612, 1808, max UDMA/33
[    4.324228] ata2.00: configured for MWDMA2
[    4.340324] ata2.01: configured for UDMA/33
[    4.340471] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200AB-00C 04.0 PQ: 0 ANSI: 5
[    4.341107] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8400B  1.06 PQ: 0 ANSI: 5
[    4.346469] scsi 1:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-M1612 1808 PQ: 0 ANSI: 5
[    4.382823] Driver 'sd' needs updating - please use bus_type methods
[    4.382955] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.382974] sd 0:0:0:0: [sda] Write Protect is off
[    4.382978] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.383008] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.383075] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.383092] sd 0:0:0:0: [sda] Write Protect is off
[    4.383095] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.383124] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.383129]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.407080]  sda1 sda2 sda3 sda4
[    4.432032] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.439316] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.439348] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.439374] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    4.450070] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.450079] Uniform CD-ROM driver Revision: 3.20
[    4.450194] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.458620] sr1: scsi3-mmc drive: 40x/48x cd/rw xa/form2 cdda tray
[    4.458761] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    4.840041] PM: Starting manual resume from disk
[    4.840041] PM: Resume from partition 8:3
[    4.840041] PM: Checking hibernation image.
[    4.840041] PM: Resume from disk failed.
[    4.883556] kjournald starting.  Commit interval 5 seconds
[    4.883556] EXT3-fs: mounted filesystem with ordered data mode.
[    5.008029] usb 4-5: new high speed USB device using ehci_hcd and address 4
[    5.140465] usb 4-5: configuration #1 chosen from 1 choice
[    5.140533] hub 4-5:1.0: USB hub found
[    5.140628] hub 4-5:1.0: 4 ports detected
[    5.724035] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    5.908712] usb 1-2: configuration #1 chosen from 1 choice
[    6.148032] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    6.329889] usb 2-1: configuration #1 chosen from 1 choice
[    6.332005] hub 2-1:1.0: USB hub found
[    6.332005] hub 2-1:1.0: 3 ports detected
[    6.660105] usb 4-5.1: new high speed USB device using ehci_hcd and address 6
[    6.769027] usb 4-5.1: configuration #1 chosen from 1 choice
[    6.984162] usb 4-5.2: new high speed USB device using ehci_hcd and address 7
[    7.093457] usb 4-5.2: configuration #1 chosen from 1 choice
[    7.308102] usb 4-5.3: new full speed USB device using ehci_hcd and address 8
[    7.428765] usb 4-5.3: configuration #1 chosen from 1 choice
[    7.668015] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    7.817617] usb 3-2: configuration #1 chosen from 1 choice
[    8.025585] usb 2-1.2: new full speed USB device using uhci_hcd and address 3
[    8.132003] usb 2-1.2: configuration #1 chosen from 1 choice
[    8.385518] usb 2-1.3: new full speed USB device using uhci_hcd and address 4
[    8.492003] usb 2-1.3: configuration #1 chosen from 1 choice
[   14.520089] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.606530] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[   15.128005] udevd version 124 started
[   17.559922] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.615799] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.671517] Linux agpgart interface v0.103
[   17.729460] agpgart: Detected an Intel 830M Chipset.
[   17.732544] agpgart: AGP aperture is 64M @ 0xe0000000
[   17.918660] intel_rng: FWH not detected
[   18.015242] input: Power Button (FF) as /class/input/input2
[   18.028602] iTCO_vendor_support: vendor-support=0
[   18.045149] ACPI: Power Button (FF) [PWRF]
[   18.045278] input: Power Button (CM) as /class/input/input3
[   18.070939] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   18.078751] ACPI: Power Button (CM) [PWRB]
[   18.078875] input: Sleep Button (CM) as /class/input/input4
[   18.078970] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   18.079003] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.108094] ACPI: Sleep Button (CM) [SLPB]
[   20.260810] nvidia: module license 'NVIDIA' taints kernel.
[   20.262322] Symbol init_mm is marked as UNUSED, however this module is using it.
[   20.262325] This symbol will go away in the future.
[   20.262328] Please evalute if this is the right api to use and if it really is, submit a report the linux kernel mailinglist together with submitting your code for inclusion.
[   20.781173] input: PC Speaker as /class/input/input5
[   20.975187] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[   20.975219] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   21.120063] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x6104
[   21.120124] usbcore: registered new interface driver usblp
[   21.220112] at76_usb: Atmel at76c50x USB Wireless LAN Driver 0.14beta1 loading
[   21.220155] firmware: requesting atmel_at76c503-rfmd.bin
[   21.296059] intel8x0_measure_ac97_clock: measured 54939 usecs
[   21.296067] intel8x0: clocking to 48000
[   21.342057] input: ImPS/2 Logitech Wheel Mouse as /class/input/input6
[   21.573516] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.574008] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   21.984968] usbcore: registered new interface driver hiddev
[   21.985015] usbcore: registered new interface driver libusual
[   21.997471] usbcore: registered new interface driver at76_usb
[   21.998509] hiddev96hidraw0: USB HID v1.10 Device [Western Digital External HDD] on usb-0000:00:1d.7-5.2
[   22.003337] input: Logitech USB Gaming Mouse as /class/input/input7
[   22.009218] Initializing USB Mass Storage driver...
[   22.019892] scsi2 : SCSI emulation for USB Mass Storage devices
[   22.020145] usb-storage: device found at 6
[   22.020148] usb-storage: waiting for device to settle before scanning
[   22.023485] scsi3 : SCSI emulation for USB Mass Storage devices
[   22.023590] usb-storage: device found at 7
[   22.023593] usb-storage: waiting for device to settle before scanning
[   22.028139] input,hidraw1: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.7-5.3
[   22.034140] hiddev97hidraw2: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.7-5.3
[   22.041063] input: Logitech Logitech BT Mini-Receiver as /class/input/input8
[   22.068168] input,hidraw3: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.1-1.2
[   22.077892] input: Logitech Logitech BT Mini-Receiver as /class/input/input9
[   22.077892] input,hiddev98,hidraw4: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.1-1.3
[   22.077892] usbcore: registered new interface driver usb-storage
[   22.077892] USB Mass Storage support registered.
[   22.077892] usbcore: registered new interface driver usbhid
[   22.077892] usbhid: v2.6:USB HID core driver
[   22.632907] parport_pc 00:0c: reported by Plug and Play ACPI
[   22.632967] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   22.728500] lp0: using parport0 (interrupt-driven).
[   23.032038] Bluetooth: Core ver 2.11
[   23.032698] NET: Registered protocol family 31
[   23.032703] Bluetooth: HCI device and connection manager initialized
[   23.032707] Bluetooth: HCI socket layer initialized
[   23.042260] Bluetooth: L2CAP ver 2.9
[   23.042267] Bluetooth: L2CAP socket layer initialized
[   23.052886] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   23.446419] Adding 1060280k swap on /dev/sda3.  Priority:-1 extents:1 across:1060280k
[   24.114830] EXT3 FS on sda2, internal journal
[   24.276044] usb 3-2: reset full speed USB device using uhci_hcd and address 2
[   24.387701] device-mapper: uevent: version 1.0.3
[   24.389289] device-mapper: ioctl: 4.13.0-ioctl (2007-10-18) initialised: dm-devel@redhat.com
[   24.420410] usb 3-2: device firmware changed
[   24.420448] usb 3-2: USB disconnect, address 2
[   24.422457] at76_usb: wlan0 disconnecting
[   24.422469] at76_usb: at76_usb disconnected
[   24.532054] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   24.681329] usb 3-2: configuration #1 chosen from 1 choice
[   24.686628] firmware: requesting atmel_at76c503-rfmd.bin
[   24.792311] at76_usb: firmware version 1.101.4 #84 (fcs_len 4)
[   24.792311] at76_usb: device's MAC 00:06:25:0e:ff:04, regulatory domain FCC (U.S) (id 16)
[   24.792311] at76_usb: registered wlan0
[   26.203772] type=1505 audit(1217530993.822:2): operation="profile_load" name="/bin/ping" name2="default" pid=4033
[   26.250425] type=1505 audit(1217530993.870:3): operation="profile_load" name="/sbin/klogd" name2="default" pid=4039
[   26.325868] type=1505 audit(1217530993.946:4): operation="profile_load" name="/sbin/syslog-ng" name2="default" pid=4042
[   26.384612] type=1505 audit(1217530994.006:5): operation="profile_load" name="/sbin/syslogd" name2="default" pid=4045
[   26.461321] type=1505 audit(1217530994.082:6): operation="profile_load" name="/usr/sbin/avahi-daemon" name2="default" pid=4050
[   26.702145] type=1505 audit(1217530994.322:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4054
[   26.702567] type=1505 audit(1217530994.322:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4054
[   26.772990] type=1505 audit(1217530994.394:9): operation="profile_load" name="/usr/sbin/dnsmasq" name2="default" pid=4059
[   26.838214] type=1505 audit(1217530994.458:10): operation="profile_load" name="/usr/sbin/identd" name2="default" pid=4062
[   26.895248] type=1505 audit(1217530994.514:11): operation="profile_load" name="/usr/sbin/mdnsd" name2="default" pid=4065
[   27.020365] usb-storage: device scan complete
[   27.020516] usb-storage: device scan complete
[   27.021024] scsi 2:0:0:0: Direct-Access     Maxtor   5000DV v01.00.00 0100 PQ: 0 ANSI: 0 CCS
[   27.025172] scsi 3:0:0:0: Direct-Access     WD       1600BB External  0412 PQ: 0 ANSI: 0
[   27.041035] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   27.047240] sd 3:0:0:0: [sdb] Write Protect is off
[   27.047244] sd 3:0:0:0: [sdb] Mode Sense: 33 00 00 00
[   27.047248] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   27.048354] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   27.049353] sd 3:0:0:0: [sdb] Write Protect is off
[   27.049356] sd 3:0:0:0: [sdb] Mode Sense: 33 00 00 00
[   27.049359] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   27.049363]  sdb: sdb1
[   27.062517] sd 3:0:0:0: [sdb] Attached SCSI disk
[   27.062578] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   27.063611] sd 2:0:0:0: [sdc] 320171008 512-byte hardware sectors (163928 MB)
[   27.065492] sd 2:0:0:0: [sdc] Test WP failed, assume Write Enabled
[   27.065500] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   27.066593] sd 2:0:0:0: [sdc] 320171008 512-byte hardware sectors (163928 MB)
[   27.067718] sd 2:0:0:0: [sdc] Test WP failed, assume Write Enabled
[   27.067722] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   27.067728]  sdc: sdc1
[   27.099522] sd 2:0:0:0: [sdc] Attached SCSI disk
[   27.099578] sd 2:0:0:0: Attached scsi generic sg4 type 0
[   29.804022] at76_usb: 2515: assertion dev->istate == INIT failed
[   31.046128] at76_usb: 1777: assertion dev->curr_bss == NULL failed
[   31.717509] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   35.831740] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   35.836922] __ratelimit: 18 messages suppressed
[   35.836930] type=1503 audit(1217531003.458:18): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=105 name="/etc/resolvconf/run/resolv.conf" pid=5347 profile="/usr/sbin/avahi-daemon"
[   46.134932] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   46.134932] apm: overridden by ACPI.
[   54.912446] ppdev: user-space parallel port driver
[   54.951752] type=1503 audit(1217531022.575:19): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/etc/resolvconf/run/resolv.conf" pid=5973 profile="/usr/sbin/cupsd"
[   54.951752] type=1503 audit(1217531022.575:20): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/etc/resolvconf/run/resolv.conf" pid=5973 profile="/usr/sbin/cupsd"
[   55.152004] type=1503 audit(1217531022.778:21): operation="inode_permission" requested_mask="a::" denied_mask="a::" fsuid=0 name="/dev/tty" pid=5973 profile="/usr/sbin/cupsd"
[   85.976241] type=1502 audit(1217531053.598:22): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/etc/resolvconf/run/resolv.conf" pid=6275 profile="/usr/sbin/ntpd"
[   85.977301] type=1502 audit(1217531053.598:23): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/etc/resolvconf/run/resolv.conf" pid=6275 profile="/usr/sbin/ntpd"
[  140.406305] loop: module loaded
[  140.456014] kjournald starting.  Commit interval 5 seconds
[  140.456014] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  140.456014] EXT3 FS on loop0, internal journal
[  140.456014] EXT3-fs: mounted filesystem with ordered data mode.
[  218.249235] Bluetooth: RFCOMM socket layer initialized
[  218.249565] Bluetooth: RFCOMM TTY layer initialized
[  218.249572] Bluetooth: RFCOMM ver 1.8
[  218.353180] usb 2-1.1: new full speed USB device using uhci_hcd and address 5
[  218.488243] usb 2-1.1: configuration #1 chosen from 1 choice
[  218.891477] Bluetooth: HCI USB driver ver 2.9
[  218.900624] usbcore: registered new interface driver hci_usb
[  220.658203] NET: Registered protocol family 10
[  220.659124] lo: Disabled Privacy Extensions
[  230.832011] wlan0: no IPv6 routers present
[  289.323700] gvfsd-trash[7238]: segfault at b73fbf36 ip b73fbf36 sp bf8f5d00 error 4
[  289.384062] gvfsd-trash[7254]: segfault at b7302f36 ip b7302f36 sp bfcff5a0 error 4
[  358.226135] type=1503 audit(1217531325.846:24): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/etc/selinux/config" pid=7466 profile="/usr/sbin/cupsd"
[  368.820981] type=1503 audit(1217531336.442:25): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/7476/net/" pid=7476 profile="/usr/sbin/cupsd"
[  368.821039] type=1503 audit(1217531336.442:26): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=7476 profile="/usr/sbin/cupsd"
[  368.821046] type=1503 audit(1217531336.442:27): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=7476 profile="/usr/sbin/cupsd"
[  368.821052] type=1503 audit(1217531336.442:28): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=7476 profile="/usr/sbin/cupsd"
[  368.821059] type=1503 audit(1217531336.442:29): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=7476 profile="/usr/sbin/cupsd"
[  368.821065] type=1503 audit(1217531336.442:30): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=7476 profile="/usr/sbin/cupsd"
[  368.821071] type=1503 audit(1217531336.442:31): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=7476 profile="/usr/sbin/cupsd"
[  368.821077] type=1503 audit(1217531336.442:32): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=7476 profile="/usr/sbin/cupsd"
[  368.821083] type=1503 audit(1217531336.442:33): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=7476 profile="/usr/sbin/cupsd"
[  368.821138] type=1503 audit(1217531336.442:34): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/7476/net/dev" pid=7476 profile="/usr/sbin/cupsd"
[  370.081225] ppdev0: registered pardevice
[  370.128051] ppdev0: unregistered pardevice
[  370.829259] ppdev0: registered pardevice
[  370.876163] ppdev0: unregistered pardevice
[  370.924959] ppdev0: registered pardevice
[  370.972270] ppdev0: unregistered pardevice



```

---

### Post by dannyboy79 on 2008-07-31
looks like your problem may be the wireless card firmware file according to dmesg:

[   24.420410] usb 3-2: device firmware changed
[   24.420448] usb 3-2: USB disconnect, address 2
[   24.422457] at76_usb: wlan0 disconnecting
[   24.422469] at76_usb: at76_usb disconnected
[   24.532054] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   24.681329] usb 3-2: configuration #1 chosen from 1 choice
[   24.686628] firmware: requesting atmel_at76c503-rfmd.bin
[   24.792311] at76_usb: firmware version 1.101.4 #84 (fcs_len 4)
[   24.792311] at76_usb: device's MAC 00:06:25:0e:ff:04, regulatory domain FCC (U.S) (id 16)
[   24.792311] at76_usb: registered wlan0

---

### Post by thelostsoul on 2008-07-31
hmm, I don't understand why it would work in the .24 kernels but not the .26 ones then...remember I'm posting on the .24 kernel using Ubuntu Studio right now, and it still works if I boot my Intrepid installation into the .24 kernel.

Forgive my newbieness, but I don't exactly understand why those messages mean its the firmware because it still finishes saying its registered.

What I am seeing as a potential problem is this line:
[   24.276044] usb 3-2: reset full speed USB device using uhci_hcd and address 2

Something I've always had a problem with using this network card is I can never disconnect it and reconnect it while my computer is running.  If I ever unplugged the card, I would have to shut down my computer, connect the card, then boot it up connected.  This line appears to be restarting the connection to the card (please correct me if I'm wrong...) which I'd imagine would cause the same problem...

Perhaps if there's a way to stop it from resetting?


thanks

---

### Post by cariboo on 2008-07-31
You could always stop and restart networking from the terminal eg:

```
jimk@intrepid:~$ sudo /etc/init.d/networking stop
[sudo] password for jimk: 
 * Deconfiguring network interfaces...                                   [ OK ] 
jimk@intrepid:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                            [ OK]                                      .
                                                                      
```

Jim

---

### Post by thelostsoul on 2008-07-31
Hmm, good point...I don't think it'll get me online, but it might help to see what's going on during the networking initialization process.  I'll have to try that tomorrow and post about it though...

---

### Post by psyke83 on 2008-08-01
Install the package "linux-restricted-modules-common" and reboot. You're probably missing that package (which seemed to be missing from all the alternate CDs I tested, though I haven't tried the Live CD yet).

---

### Post by thelostsoul on 2008-08-01
Yeah I read that before, it's already installed though...I upgraded, not a fresh install.  

I guess that could be an issue in itself though?  

Didn't get to try that other command today though...gonna have to tomorrow if I can...

---

### Post by Gina on 2008-08-02
I always do a fresh install (separate /home so I don't lose my settings etc.).

I see your wireless is connecting (once at least) as it has found the router MAC.  I think firmware is the most likely culprit too.

But I would suggest a fresh install and run the updates.  Go to Software Sources before the update though and check you have everything ticked as appropriate.  Also, to be sure of the latest updates set the source to Main Server rather than your local mirror.  Some mirrors are up to a week behind.

---

### Post by plun on 2008-08-02
Just a little question, are you on kernel 2.6.26-5  ?

I had trouble yesterday (after a week without updates)
to get this kernel to menu.lst

I noticed during install that debconf asked me and I choosed
to preserve the file installed already.

Maybe that a dist-upgrade is needed.:evil:

sudo update-gub didn't solve this so I must manually edit menu.lst to get latest kernel running.

---

### Post by allmywebsite1 on 2008-08-02
hiii..friends

you can see the online tv and the screen is so wide 
so you can watch properly and you feel like you are watching at home......

---

### Post by KIAaze on 2008-08-02
I also can't get online over wifi with the latest kernel (2.6.26-4).
iwconfig doesn't even list my wifi card!

Also, the **network manager seems to have disappeared** from the System->Administration menu. :(
And when I click on "configure manually" in the nm-applet, nothing happens.
I couldn't find any network-manager command either.

I rebooted into the 2.6.24-16 kernel and there my card worked without any problems.
But network-manager is still unavailable of course.

My wifi card:
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```

---

### Post by plun on 2008-08-02
> **KIAaze said:**
> I also can't get online over wifi with the latest kernel (2.6.26-4).
iwconfig doesn't even list my wifi card!

Generic Linux-image for Intrepid is **2.6.26-5**

[http://packages.ubuntu.com/intrepid/linux-image](http://packages.ubuntu.com/intrepid/linux-image)

I am not starting another discussions about the dist-upgrade command  :)

What is the output with this command


```
sudo apt-get update && sudo apt-get dist-upgrade

```  

Answer "No" and post output if you are unsure.... !


Maybe we also have servers left behind....:confused:

---

### Post by KIAaze on 2008-08-02
The linux-image metapackage wasn't installed. I suppose that's why it didn't upgrade the kernel.
Doing it right now. I'll tell you if it works.

But what about the network manager? Is it gone?

---

### Post by plun on 2008-08-02
> **KIAaze said:**
> The linux-image metapackage wasn't installed. I suppose that's why it didn't upgrade the kernel.
Doing it right now. I'll tell you if it works.

But what about the network manager? Is it gone?

OK.... no clue about NM and I switched to asacs testing ppa for
NM 0.7 a month ago. Works great.

[http://www.asoftsite.org/s9y/archives/145-NetworkManager-0.7-is-back-New-PPA.html](http://www.asoftsite.org/s9y/archives/145-NetworkManager-0.7-is-back-New-PPA.html)

---

### Post by KIAaze on 2008-08-02
Nope, wifi still not working with kernel 2.6.26.5.7.
I also have linux-restricted-modules 2.6.26.5.7.

edit:
Here's what I get with the old kernel:
```
    *-network
          description: Wireless interface
          product: AR5212/AR5213 Multiprotocol MAC/baseband processor
          vendor: Atheros Communications Inc.
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: wifi0
          version: 01
          serial: 00:14:78:8f:8b:39
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath_pci ip=192.168.2.101 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

```

$lsmod | grep ath
ath_rate_sample        14336  1
ath_pci               101024  0
wlan                  207728  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci

```
I'll check for the driver module in the new kernel at next reboot. Don't want to reboot now.

---

### Post by plun on 2008-08-02
Well, thats strange....

You can maybe try "kevdogs" sticky thread for manual config. 

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)


This can be a NM challenge.....

---

### Post by Gina on 2008-08-02
Wasn't it that a package was missing? - gnome-admin-tools or something like that - can't quite remember and I can't seem to find the thread now.

EDIT...  Found it!> You have to install the gnome-network-admin package. 

---

### Post by KIAaze on 2008-08-02
Ah, thanks, that was the package. :)
I thought if ubuntu-desktop was installed it would be installed. Apparently that's not necessarily the case...

Still haven't rebooted, but I doubt this will change anything for the other kernel since it's supposed to just be a GUI.

---

### Post by plun on 2008-08-03
> **KIAaze said:**
> Ah, thanks, that was the package. :)
I thought if ubuntu-desktop was installed it would be installed. Apparently that's not necessarily the case...

Still haven't rebooted, but I doubt this will change anything for the other kernel since it's supposed to just be a GUI.

Updated kernel should be available

[https://lists.ubuntu.com/archives/intrepid-changes/2008-August/004533.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-August/004533.html)


And if a reboot fails, just choose another kernel from the GRUB menu..:)

---

### Post by KIAaze on 2008-08-03
The ath_pci.ko module is not available in the linux-restricted-modules-2.6.26-5-generic package.
That's why it doesn't work.

I attempted to compile madwifi (which provides the module I think), but it was a failure.
I guess I'll just wait a bit.

Compile error if anyone understands it:
```
~/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':          
~/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [~/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1                                     
make[2]: *** [~/madwifi-0.9.4/net80211] Error 2                                                       
make[1]: *** [_module_~/madwifi-0.9.4] Error 2                                                        
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-5-generic'                                           
make: *** [modules] Error 2                                              

```
```
[11][~]$  locate ath_pci
/lib/linux-restricted-modules/2.6.26-3-generic/ath_pci
/lib/linux-restricted-modules/2.6.26-3-generic/ath_pci/ath_pci.mod.o
/lib/linux-restricted-modules/2.6.26-3-generic/ath_pci/if_ath.o
/lib/linux-restricted-modules/2.6.26-3-generic/ath_pci/if_ath_pci.o
/lib/linux-restricted-modules/2.6.26-4-generic/ath_pci
/lib/linux-restricted-modules/2.6.26-4-generic/ath_pci/ath_pci.mod.o
/lib/linux-restricted-modules/2.6.26-4-generic/ath_pci/if_ath.o
/lib/linux-restricted-modules/2.6.26-4-generic/ath_pci/if_ath_pci.o
/lib/linux-restricted-modules/2.6.26-5-generic/ath_pci
/lib/linux-restricted-modules/2.6.26-5-generic/ath_pci/ath_pci.mod.o
/lib/linux-restricted-modules/2.6.26-5-generic/ath_pci/if_ath.o
/lib/linux-restricted-modules/2.6.26-5-generic/ath_pci/if_ath_pci.o
/lib/modules/2.6.24-16-generic/madwifi/ath_pci.ko
/usr/share/linux-restricted-modules/2.6.26-3-generic/modules.alias.override/ath_pci
/usr/share/linux-restricted-modules/2.6.26-4-generic/modules.alias.override/ath_pci
/usr/share/linux-restricted-modules/2.6.26-5-generic/modules.alias.override/ath_pci

```

---

### Post by plun on 2008-08-03
Well, maybe you needs the kernel source ?

```
sudo apt-get install linux-source-2.6.26
```


Madwifi and kernel 2.6.26...:confused:


Also file a bug >  [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Seems to be clear that it is.

---

### Post by KIAaze on 2008-08-06
Bug finally filed: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/255547](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/255547)

---

