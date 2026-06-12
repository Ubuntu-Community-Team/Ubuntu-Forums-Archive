---
title: "boot up issues"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by rballard on 2008-11-08
I have just upgraded to Intrepid Ibex from ubuntu 8.04 and now when I turn on my pc. the screen scrolls through lines of I/O  sr0 error messesges for several minutes. any suggestions?

---

### Post by Cannaregio on 2008-11-08
If you manage to log in through -say- [COLOR="Blue"]CTRL+ALT+F3[/COLOR] use the command
```
dmesg
```
and post here the results.

---

### Post by ubu123 on 2008-11-10
I have this problem too.  Taking the cd out of the drive seems to stop it.  I didn't have this problem with Hardy, only with Intrepid.
Here's the output of dmesg:
```
[    0.020588] SMP alternatives: switching to UP code
[    0.028035] Freeing SMP alternatives: 11k freed
[    0.028041] ACPI: Core revision 20080609
[    0.029411] ACPI: Checking initramfs for custom DSDT
[    0.384164] ACPI: setting ELCR to 0200 (from 0800)
[    0.385604] weird, boot CPU (#0) not listedby the BIOS.
[    0.385608] SMP motherboard not detected.
[    0.385611] Local APIC not detected. Using dummy APIC emulation.
[    0.385614] SMP disabled
[    0.385698] Brought up 1 CPUs
[    0.385701] Total of 1 processors activated (5315.58 BogoMIPS).
[    0.385717] CPU0 attaching sched-domain:
[    0.385721]  domain 0: span 0 level CPU
[    0.385724]   groups: 0
[    0.386054] net_namespace: 840 bytes
[    0.386070] Booting paravirtualized kernel on bare hardware
[    0.386317] Time: 17:54:39  Date: 11/10/08
[    0.386368] NET: Registered protocol family 16
[    0.386825] EISA bus registered
[    0.386853] ACPI: bus type pci registered
[    0.438616] PCI: PCI BIOS revision 2.10 entry at 0xfcfae, last bus=2
[    0.438620] PCI: Using configuration type 1 for base access
[    0.440548] ACPI: EC: Look up EC in DSDT
[    0.445574] ACPI: Interpreter enabled
[    0.445580] ACPI: (supports S0 S1 S3 S4 S5)
[    0.445601] ACPI: Using PIC for interrupt routing
[    0.455263] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.455369] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e7ffffff]
[    0.455504] PCI: 0000:00:1d.0 reg 20 io port: [bf80, bf9f]
[    0.455557] PCI: 0000:00:1d.1 reg 20 io port: [bf40, bf5f]
[    0.455609] PCI: 0000:00:1d.2 reg 20 io port: [bf20, bf3f]
[    0.455670] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f4fffc00, f4ffffff]
[    0.455723] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.455729] pci 0000:00:1d.7: PME# disabled
[    0.455770] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.455772] * this clock source is slow. If you are sure your timer does not have
[    0.455774] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.455816] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.455825] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.455829] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.455850] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
[    0.455858] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
[    0.455865] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
[    0.455872] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
[    0.455879] PCI: 0000:00:1f.1 reg 20 io port: [bfa0, bfaf]
[    0.455886] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.455928] PCI: 0000:00:1f.5 reg 10 io port: [b800, b8ff]
[    0.455935] PCI: 0000:00:1f.5 reg 14 io port: [bc40, bc7f]
[    0.455942] PCI: 0000:00:1f.5 reg 18 32bit mmio: [f4fff800, f4fff9ff]
[    0.455949] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [f4fff400, f4fff4ff]
[    0.455976] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.455981] pci 0000:00:1f.5: PME# disabled
[    0.456007] PCI: 0000:00:1f.6 reg 10 io port: [b400, b4ff]
[    0.456014] PCI: 0000:00:1f.6 reg 14 io port: [b080, b0ff]
[    0.456068] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.456073] pci 0000:00:1f.6: PME# disabled
[    0.456108] PCI: 0000:01:00.0 reg 10 32bit mmio: [e8000000, efffffff]
[    0.456115] PCI: 0000:01:00.0 reg 14 io port: [c000, c0ff]
[    0.456121] PCI: 0000:01:00.0 reg 18 32bit mmio: [fcff0000, fcffffff]
[    0.456138] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.456154] pci 0000:01:00.0: supports D1
[    0.456156] pci 0000:01:00.0: supports D2
[    0.456188] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.456193] PCI: bridge 0000:00:01.0 32bit mmio: [fc000000, fdffffff]
[    0.456198] PCI: bridge 0000:00:01.0 32bit mmio pref: [e8000000, efffffff]
[    0.456234] PCI: 0000:02:01.0 reg 10 32bit mmio: [faffe000, faffffff]
[    0.456273] pci 0000:02:01.0: supports D1
[    0.456275] pci 0000:02:01.0: supports D2
[    0.456278] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.456282] pci 0000:02:01.0: PME# disabled
[    0.456309] PCI: 0000:02:02.0 reg 10 32bit mmio: [faffc000, faffdfff]
[    0.456349] pci 0000:02:02.0: supports D1
[    0.456351] pci 0000:02:02.0: supports D2
[    0.456353] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.456358] pci 0000:02:02.0: PME# disabled
[    0.456388] PCI: 0000:02:04.0 reg 10 32bit mmio: [0, fff]
[    0.456403] pci 0000:02:04.0: supports D1
[    0.456405] pci 0000:02:04.0: supports D2
[    0.456407] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.456412] pci 0000:02:04.0: PME# disabled
[    0.456443] PCI: 0000:02:04.1 reg 10 32bit mmio: [faffb800, faffbfff]
[    0.456451] PCI: 0000:02:04.1 reg 14 32bit mmio: [faff4000, faff7fff]
[    0.456490] pci 0000:02:04.1: supports D1
[    0.456492] pci 0000:02:04.1: supports D2
[    0.456494] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot
[    0.456499] pci 0000:02:04.1: PME# disabled
[    0.456540] pci 0000:00:1e.0: transparent bridge
[    0.456544] PCI: bridge 0000:00:1e.0 io port: [d000, efff]
[    0.456549] PCI: bridge 0000:00:1e.0 32bit mmio: [f6000000, fbffffff]
[    0.456580] bus 00 -> node 0
[    0.456591] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.456966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.457080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.466508] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.466684] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.466856] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.467028] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.467200] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.467377] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.467613] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.467669] pnp: PnP ACPI init
[    0.467687] ACPI: bus type pnp registered
[    0.481742] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.481747] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.481880] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.481885] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.481888] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.483406] pnp: PnP ACPI: found 11 devices
[    0.483410] ACPI: ACPI bus type pnp unregistered
[    0.483416] PnPBIOS: Disabled by ACPI PNP
[    0.483979] PCI: Using ACPI for IRQ routing
[    0.484160] NET: Registered protocol family 8
[    0.484160] NET: Registered protocol family 20
[    0.484160] NetLabel: Initializing
[    0.484160] NetLabel:  domain hash size = 128
[    0.484160] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.484167] NetLabel:  unlabeled traffic allowed by default
[    0.484481] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.484483]    actual entries 65620
[    0.484737] AppArmor: AppArmor Filesystem Enabled
[    0.484776] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.484776] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.484776] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.484776] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.484776] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.484776] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
[    0.484776] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
[    0.484776] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.484776] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.484776] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.484776] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.484776] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.484776] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.484776] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.520428] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.520433] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.520439] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.520444] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.520459] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[    0.520463] pci 0000:02:04.0:   IO window: 0x00d000-0x00d0ff
[    0.520468] pci 0000:02:04.0:   IO window: 0x00d400-0x00d4ff
[    0.520473] pci 0000:02:04.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.520477] pci 0000:02:04.0:   MEM window: 0x38000000-0x3bffffff
[    0.520482] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.520486] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.520493] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.520498] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000033ffffff
[    0.520521] pci 0000:00:1e.0: setting latency timer to 64
[    0.520530] pci 0000:02:04.0: enabling device (0000 -> 0003)
[    0.520822] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.520827] PCI: setting IRQ 11 as level-triggered
[    0.520832] pci 0000:02:04.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.520840] bus: 00 index 0 io port: [0, ffff]
[    0.520843] bus: 00 index 1 mmio: [0, ffffffff]
[    0.520845] bus: 01 index 0 io port: [c000, cfff]
[    0.520848] bus: 01 index 1 mmio: [fc000000, fdffffff]
[    0.520850] bus: 01 index 2 mmio: [e8000000, efffffff]
[    0.520853] bus: 01 index 3 mmio: [0, 0]
[    0.520855] bus: 02 index 0 io port: [d000, efff]
[    0.520858] bus: 02 index 1 mmio: [f6000000, fbffffff]
[    0.520861] bus: 02 index 2 mmio: [30000000, 33ffffff]
[    0.520863] bus: 02 index 3 io port: [0, ffff]
[    0.520866] bus: 02 index 4 mmio: [0, ffffffff]
[    0.520868] bus: 03 index 0 io port: [d000, d0ff]
[    0.520871] bus: 03 index 1 io port: [d400, d4ff]
[    0.520874] bus: 03 index 2 mmio: [30000000, 33ffffff]
[    0.520877] bus: 03 index 3 mmio: [38000000, 3bffffff]
[    0.520896] NET: Registered protocol family 2
[    0.521115] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.521430] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.521546] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.521655] TCP: Hash tables configured (established 16384 bind 16384)
[    0.521658] TCP reno registered
[    0.521792] NET: Registered protocol family 1
[    0.521960] checking if image is initramfs... it is
[    1.024094] Switched to high resolution mode on CPU 0
[    1.272322] Freeing initrd memory: 7969k freed
[    1.273230] audit: initializing netlink socket (disabled)
[    1.273264] type=2000 audit(1226339680.272:1): initialized
[    1.278436] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.281535] VFS: Disk quotas dquot_6.5.1
[    1.281682] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.281835] msgmni has been set to 1003
[    1.282019] io scheduler noop registered
[    1.282022] io scheduler anticipatory registered
[    1.282025] io scheduler deadline registered
[    1.282045] io scheduler cfq registered (default)
[    1.282140] pci 0000:01:00.0: Boot video device
[    1.282653] isapnp: Scanning for PnP cards...
[    1.635635] isapnp: No Plug & Play device found
[    1.698704] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.699952] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[    1.699957] PCI: setting IRQ 7 as level-triggered
[    1.699963] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    1.699972] serial 0000:00:1f.6: PCI INT B disabled
[    1.702358] brd: module loaded
[    1.702467] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.702648] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.702856] i8042.c: Warning: Keylock active.
[    1.705306] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.705325] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.706240] mice: PS/2 mouse device common for all mice
[    1.706483] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.706504] rtc0: alarms up to one day
[    1.706731] EISA: Probing bus 0 at eisa.0
[    1.706758] EISA: Detected 0 cards.
[    1.706773] cpuidle: using governor ladder
[    1.706776] cpuidle: using governor menu
[    1.707451] TCP cubic registered
[    1.707494] Using IPI No-Shortcut mode
[    1.707920] registered taskstats version 1
[    1.708110]   Magic number: 0:476:946
[    1.708141] tty ttya1: hash matches
[    1.708236] tty tty3: hash matches
[    1.708295] rtc_cmos 00:06: setting system clock to 2008-11-10 17:54:41 UTC (1226339681)
[    1.708299] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.708301] EDD information not available.
[    1.708954] Freeing unused kernel memory: 424k freed
[    1.709014] Write protecting the kernel text: 2576k
[    1.709050] Write protecting the kernel read-only data: 936k
[    1.711096] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.930990] fuse init (API version 7.9)
[    2.089094] processor ACPI0007:00: registered as cooling_device0
[    2.089100] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.094221] thermal LNXTHERM:01: registered as thermal_zone0
[    2.097442] ACPI: Thermal Zone [THM] (29 C)
[    2.759932] usbcore: registered new interface driver usbfs
[    2.759970] usbcore: registered new interface driver hub
[    2.760094] usbcore: registered new device driver usb
[    2.779835] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    2.779843] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    2.779860] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.779865] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.779955] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.783878] ehci_hcd 0000:00:1d.7: debug port 1
[    2.783886] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.783897] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    2.799290] USB Universal Host Controller Interface driver v3.0
[    2.821400] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.821662] usb usb1: configuration #1 chosen from 1 choice
[    2.821702] hub 1-0:1.0: USB hub found
[    2.821720] hub 1-0:1.0: 6 ports detected
[    2.872637] No dock devices found.
[    2.921725] SCSI subsystem initialized
[    2.926375] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.926394] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.926399] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.926438] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.926475] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    2.926636] usb usb2: configuration #1 chosen from 1 choice
[    2.926672] hub 2-0:1.0: USB hub found
[    2.926686] hub 2-0:1.0: 2 ports detected
[    3.004191] libata version 3.00 loaded.
[    3.028802] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.028809] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.028821] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.028826] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.028873] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.028903] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    3.029068] usb usb3: configuration #1 chosen from 1 choice
[    3.029105] hub 3-0:1.0: USB hub found
[    3.029118] hub 3-0:1.0: 2 ports detected
[    3.132739] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    3.132746] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.132757] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.132762] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.132804] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.132834] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    3.132992] usb usb4: configuration #1 chosen from 1 choice
[    3.133035] hub 4-0:1.0: USB hub found
[    3.133056] hub 4-0:1.0: 2 ports detected
[    3.237312] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.240753] ata_piix 0000:00:1f.1: version 2.12
[    3.240762] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.240769] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.240828] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.241031] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    3.245541] ohci1394 0000:02:04.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.295375] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffb800-faffbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.297165] scsi0 : ata_piix
[    3.300508] scsi1 : ata_piix
[    3.300782] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    3.300786] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    3.464403] ata1.00: ATAPI: QSI CD-RW/DVD-ROM SBW242U, UD25, max UDMA/33
[    3.480340] ata1.00: configured for UDMA/33
[    3.644539] ata2.00: ATA-5: HITACHI_DK23FB-40, 00M1A0C1, max UDMA/100
[    3.644545] ata2.00: 78140160 sectors, multi 8: LBA 
[    3.652420] ata2.00: configured for UDMA/100
[    3.653065] scsi 0:0:0:0: CD-ROM            QSI      CDRW/DVD SBW242U UD25 PQ: 0 ANSI: 5
[    3.653286] scsi 1:0:0:0: Direct-Access     ATA      HITACHI_DK23FB-4 00M1 PQ: 0 ANSI: 5
[    3.653431] b44 0000:02:01.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    3.712213] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[    3.715983] b44.c:v2.0
[    3.736617] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:b5:49:fb
[    3.983978] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.984086] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    4.021492] Driver 'sr' needs updating - please use bus_type methods
[    4.031748] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    4.031756] Uniform CD-ROM driver Revision: 3.20
[    4.031904] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.039910] Driver 'sd' needs updating - please use bus_type methods
[    4.040197] sd 1:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.040259] sd 1:0:0:0: [sda] Write Protect is off
[    4.040263] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.040376] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.040538] sd 1:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.040586] sd 1:0:0:0: [sda] Write Protect is off
[    4.040591] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.040683] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.040692]  sda: sda1 sda2 sda3
[    4.102938] sd 1:0:0:0: [sda] Attached SCSI disk
[    4.431279] PM: Starting manual resume from disk
[    4.431285] PM: Resume from partition 8:3
[    4.431287] PM: Checking hibernation image.
[    4.431516] PM: Resume from disk failed.
[    4.459212] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.459218] EXT3-fs: write access will be enabled during recovery.
[    4.572210] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[424fc000268a9c81]
[    7.917794] kjournald starting.  Commit interval 5 seconds
[    7.917828] EXT3-fs: recovery complete.
[    7.920217] EXT3-fs: mounted filesystem with ordered data mode.
[   14.597916] udevd version 124 started
[   15.254369] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.341782] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.406984] Linux agpgart interface v0.103
[   15.458419] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   15.468813] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   15.543250] iTCO_vendor_support: vendor-support=0
[   15.594709] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   15.594848] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
[   15.595088] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.734384] intel_rng: FWH not detected
[   15.814398] ACPI: AC Adapter [AC] (off-line)
[   16.209607] ACPI: Battery Slot [BAT0] (battery present)
[   16.209735] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[   16.210086] ACPI: Lid Switch [LID]
[   16.210159] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   16.220064] ACPI: Power Button (CM) [PBTN]
[   16.220348] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   16.236080] ACPI: Sleep Button (CM) [SBTN]
[   16.495228] Yenta: CardBus bridge found at 0000:02:04.0 [1028:0149]
[   16.495249] Yenta: Using CSCINT to route CSC interrupts to PCI
[   16.495251] Yenta: Routing CardBus interrupts to PCI
[   16.495257] Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64
[   16.724723] Yenta: ISA IRQ mask 0x0478, PCI irq 11
[   16.724728] Socket status: 30000086
[   16.724732] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   16.724740] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   16.724744] cs: IO port probe 0xd000-0xefff: clean.
[   16.725226] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   16.725230] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   17.198766] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/device:1c/input/input5
[   17.208089] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   17.208944] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:20/input/input6
[   17.224076] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   17.224394] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:24/input/input7
[   17.240070] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   17.870368] b43legacy-phy0: Broadcom 4306 WLAN found
[   17.908055] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   17.908079] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   17.937002] b43legacy-phy0 debug: Radio initialized
[   17.938686] phy0: Selected rate control algorithm 'pid'
[   18.012921] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   18.425965] Broadcom 43xx-legacy driver loaded [ Features: PLRID, Firmware-ID: FW10 ]
[   18.786827] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[   18.786857] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   19.109874] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[   19.150750] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   19.179664] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.612060] intel8x0_measure_ac97_clock: measured 55198 usecs
[   19.612065] intel8x0: clocking to 48000
[   20.909064] cs: IO port probe 0x100-0x3af: clean.
[   20.910145] cs: IO port probe 0x3e0-0x4ff: clean.
[   20.910605] cs: IO port probe 0x820-0x8ff: clean.
[   20.910665] cs: IO port probe 0xc00-0xcf7: clean.
[   20.911221] cs: IO port probe 0xa00-0xaff: clean.
[   21.847550] lp: driver loaded but no devices found
[   22.204308] Adding 128512k swap on /dev/sda3.  Priority:-1 extents:1 across:128512k
[   22.245893] EXT3 FS on sda2, internal journal
[   22.732425] type=1505 audit(1226357702.282:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3959
[   22.945353] type=1505 audit(1226357702.494:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3964
[   22.945825] type=1505 audit(1226357702.494:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3964
[   23.090496] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.787065] ACPI: WMI: Mapper loaded
[   25.007132] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   25.072144] apm: BIOS not found.
[   25.239471] ppdev: user-space parallel port driver
[   27.017589] Bluetooth: Core ver 2.13
[   27.020264] NET: Registered protocol family 31
[   27.020283] Bluetooth: HCI device and connection manager initialized
[   27.020288] Bluetooth: HCI socket layer initialized
[   27.043321] Bluetooth: L2CAP ver 2.11
[   27.043330] Bluetooth: L2CAP socket layer initialized
[   27.060448] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.060457] Bluetooth: BNEP filters: protocol multicast
[   27.090452] Bridge firewalling registered
[   27.091534] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   27.107402] Bluetooth: SCO (Voice Link) ver 0.6
[   27.107411] Bluetooth: SCO socket layer initialized
[   27.173895] Bluetooth: RFCOMM socket layer initialized
[   27.174236] Bluetooth: RFCOMM TTY layer initialized
[   27.174244] Bluetooth: RFCOMM ver 1.10
[   29.218025] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   29.218047] pci 0000:01:00.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[   29.488847] [drm] Initialized drm 1.1.0 20060810
[   29.516566] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   29.698631] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   29.698673] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   29.698712] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   29.927161] [drm] Setting GART location based on new memory map
[   29.927177] [drm] Loading R100 Microcode
[   29.927222] [drm] writeback test succeeded in 1 usecs
[   31.330031] input: b43legacy-phy0 as /devices/virtual/input/input10
[   31.667622] firmware: requesting b43legacy/ucode4.fw
[   31.725949] firmware: requesting b43legacy/pcm4.fw
[   31.749262] firmware: requesting b43legacy/b0g0initvals2.fw
[   31.876055] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   31.942482] b43legacy-phy0 debug: Chip initialized
[   31.943850] b43legacy-phy0 debug: 30-bit DMA initialized
[   31.947431] Registered led device: b43legacy-phy0:tx
[   31.947803] Registered led device: b43legacy-phy0:rx
[   31.948066] Registered led device: b43legacy-phy0:radio
[   31.948110] b43legacy-phy0 debug: Wireless interface started
[   31.964316] b43legacy-phy0 debug: Adding Interface type 2
[   32.063798] NET: Registered protocol family 17
[   32.756084] wlan0: authenticate with AP 00:12:17:13:b2:8c
[   32.757612] wlan0: authenticated
[   32.757622] wlan0: associate with AP 00:12:17:13:b2:8c
[   32.759780] wlan0: RX AssocResp from 00:12:17:13:b2:8c (capab=0x401 status=0 aid=9)
[   32.759787] wlan0: associated
[   32.786421] wlan0: disassociating by local choice (reason=3)
[   46.851096] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   46.851108] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   46.851113] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   46.851119] end_request: I/O error, dev sr0, sector 1431184
[   46.851127] Buffer I/O error on device sr0, logical block 178898
[   52.581080] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   52.581093] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   52.581098] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   52.581105] end_request: I/O error, dev sr0, sector 1431184
[   52.581114] Buffer I/O error on device sr0, logical block 178898
[   57.852967] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   57.852978] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   57.852983] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   57.852989] end_request: I/O error, dev sr0, sector 1431184
[   57.852998] Buffer I/O error on device sr0, logical block 178898
[   63.143873] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   63.143885] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   63.143891] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   63.143897] end_request: I/O error, dev sr0, sector 1431184
[   63.143907] Buffer I/O error on device sr0, logical block 178898
[   68.474837] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   68.474849] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   68.474855] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   68.474861] end_request: I/O error, dev sr0, sector 1431184
[   68.474869] Buffer I/O error on device sr0, logical block 178898
[   73.742630] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   73.742641] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   73.742647] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   73.742653] end_request: I/O error, dev sr0, sector 1431184
[   73.742660] Buffer I/O error on device sr0, logical block 178898
[   76.023948] wlan0: authenticate with AP 00:1e:2a:7a:6c:7c
[   76.026979] wlan0: authenticated
[   76.026998] wlan0: associate with AP 00:1e:2a:7a:6c:7c
[   76.030254] wlan0: RX AssocResp from 00:1e:2a:7a:6c:7c (capab=0x411 status=0 aid=1)
[   76.030271] wlan0: associated
[   76.581203] padlock: VIA PadLock not detected.
[   79.021598] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   79.021609] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   79.021615] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   79.021621] end_request: I/O error, dev sr0, sector 1431184
[   79.021628] Buffer I/O error on device sr0, logical block 178898
[   84.639430] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   84.639441] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   84.639447] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   84.639453] end_request: I/O error, dev sr0, sector 1431184
[   84.639461] Buffer I/O error on device sr0, logical block 178898
[   89.942290] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   89.942301] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   89.942306] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[   89.942312] end_request: I/O error, dev sr0, sector 1431184
[   89.942321] Buffer I/O error on device sr0, logical block 178898
[   90.632740] UDF-fs: No VRS found
[   90.655370] ISO 9660 Extensions: Microsoft Joliet Level 3
[   90.774635] ISO 9660 Extensions: RRIP_1991A
[   97.574912] NET: Registered protocol family 10
[   97.577632] lo: Disabled Privacy Extensions
[   97.580320] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  107.732037] wlan0: no IPv6 routers present
[  144.905573] type=1503 audit(1226357823.596:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5836/net/" pid=5836 profile="/usr/sbin/cupsd"
[  145.931252] type=1503 audit(1226357824.620:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5840/net/" pid=5840 profile="/usr/sbin/cupsd"
[  145.934157] type=1503 audit(1226357824.624:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5840 profile="/usr/sbin/cupsd"
[  145.936434] type=1503 audit(1226357824.628:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5840 profile="/usr/sbin/cupsd"
[  145.938746] type=1503 audit(1226357824.628:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5840 profile="/usr/sbin/cupsd"
[  145.941007] type=1503 audit(1226357824.632:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5840 profile="/usr/sbin/cupsd"
[  145.943266] type=1503 audit(1226357824.632:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5840 profile="/usr/sbin/cupsd"
[  145.946222] type=1503 audit(1226357824.636:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5840 profile="/usr/sbin/cupsd"
[  145.948673] type=1503 audit(1226357824.640:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5840 profile="/usr/sbin/cupsd"

```

---

### Post by Cannaregio on 2008-11-13
Can't see much, apart from some minor common unix printing system daemon error messages in ubu123 dmesg. 
Did the OP refer to those in his original post?
Why d'you have a cd inside the drive at all, ubu123?

---

