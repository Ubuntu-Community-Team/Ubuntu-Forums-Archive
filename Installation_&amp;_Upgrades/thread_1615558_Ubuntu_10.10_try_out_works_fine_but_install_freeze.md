---
title: "Ubuntu 10.10 try out works fine but install freezes? HELP!"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by jonnyboyca on 2010-11-07
I have downloaded and burned the ISO 3 different times on 2 machines and still won't work. I have a 3 year old Gateway old laptop that was running 10.04 just fine. Did a clean wipe and trying to install 10.10 and when I get to the screen 'Preparing to install ubuntu' I click forward and it freezes. The weird thing is if i boot up from the same cd and run it as "Try Ubuntu" it loads up completely fine. Is this a problem with the cd or ? So confused. Thanks
:-k

---

### Post by Jechem on 2010-11-07
try running the live cd first and choose the install icon if it still freezes up.

---

### Post by jonnyboyca on 2010-11-07
tried that.. it just freezes at the same spot... i selected download updates.. deselected it.. nothing.. it just shows the "thinking" circle and nothing happens...

---

### Post by P4man on 2010-11-07
sounds like a problem with the drive (or partitions/filesystem). Try a live session and run disk utility.

---

### Post by jonnyboyca on 2010-11-07
i can get into live and disk utility but when i try to format or delete partitions it says daemon prohibited

---

### Post by P4man on 2010-11-07
Perhaps try this; open a terminal and swapoff first:

```
sudo swapoff -a
```

A live session will use any swap partition it finds on the hdd, and you cant delete partitions that are being used.

If that doesnt help, can you post the output of

```
dmesg
```

```
sudo fdisk -l
```

---

### Post by jonnyboyca on 2010-11-07
dmesg:

[    0.112922] system 00:04: [io  0x1000-0x107f] has been reserved
[    0.112925] system 00:04: [io  0x1180-0x11bf] has been reserved
[    0.112931] system 00:04: [mem 0xfec10000-0xfec1ffff] has been reserved
[    0.112935] system 00:04: [mem 0xe0000000-0xefffffff] could not be reserved
[    0.149481] pci 0000:00:1e.0: BAR 15: assigned [mem 0x50000000-0x53ffffff pref]
[    0.149488] pci 0000:00:1e.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.149492] pci 0000:00:1f.1: BAR 5: assigned [mem 0x54000000-0x540003ff]
[    0.149500] pci 0000:00:1f.1: BAR 5: set to [mem 0x54000000-0x540003ff] (PCI address [0x54000000-0x540003ff]
[    0.149506] pci 0000:02:07.0: BAR 15: assigned [mem 0x50000000-0x53ffffff pref]
[    0.149511] pci 0000:02:07.0: BAR 16: assigned [mem 0x58000000-0x5bffffff]
[    0.149514] pci 0000:02:07.0: BAR 0: assigned [mem 0xe020a000-0xe020afff]
[    0.149521] pci 0000:02:07.0: BAR 0: set to [mem 0xe020a000-0xe020afff] (PCI address [0xe020a000-0xe020afff]
[    0.149525] pci 0000:02:07.0: BAR 13: assigned [io  0x3000-0x30ff]
[    0.149529] pci 0000:02:07.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.149533] pci 0000:02:07.0: CardBus bridge to [bus 03-06]
[    0.149536] pci 0000:02:07.0:   bridge window [io  0x3000-0x30ff]
[    0.149541] pci 0000:02:07.0:   bridge window [io  0x3400-0x34ff]
[    0.149547] pci 0000:02:07.0:   bridge window [mem 0x50000000-0x53ffffff pref]
[    0.149552] pci 0000:02:07.0:   bridge window [mem 0x58000000-0x5bffffff]
[    0.149558] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.149563] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.149570] pci 0000:00:1e.0:   bridge window [mem 0xe0200000-0xe02fffff]
[    0.149575] pci 0000:00:1e.0:   bridge window [mem 0x50000000-0x53ffffff pref]
[    0.149594] pci 0000:00:1e.0: setting latency timer to 64
[    0.149604] pci 0000:02:07.0: enabling device (0000 -> 0003)
[    0.149613]   alloc irq_desc for 19 on node -1
[    0.149616]   alloc kstat_irqs on node -1
[    0.149626] pci 0000:02:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.149632] pci 0000:02:07.0: setting latency timer to 64
[    0.149637] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.149641] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.149644] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.149648] pci_bus 0000:02: resource 1 [mem 0xe0200000-0xe02fffff]
[    0.149651] pci_bus 0000:02: resource 2 [mem 0x50000000-0x53ffffff pref]
[    0.149655] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.149658] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.149662] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.149665] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.149668] pci_bus 0000:03: resource 2 [mem 0x50000000-0x53ffffff pref]
[    0.149672] pci_bus 0000:03: resource 3 [mem 0x58000000-0x5bffffff]
[    0.149730] NET: Registered protocol family 2
[    0.149827] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.150170] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.151953] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.153058] TCP: Hash tables configured (established 131072 bind 65536)
[    0.153063] TCP reno registered
[    0.153072] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.153112] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.153322] NET: Registered protocol family 1
[    0.153361] pci 0000:00:02.0: Boot video device
[    0.153570] PCI: CLS 64 bytes, default 64
[    0.153731] Simple Boot Flag at 0x36 set to 0x1
[    0.153929] cpufreq-nforce2: No nForce2 chipset.
[    0.153972] Scanning for low memory corruption every 60 seconds
[    0.154017] Corrupted low memory at c0006a50 (6a50 phys) = 00000008
[    0.154067] ------------[ cut here ]------------
[    0.154081] WARNING: at /build/buildd/linux-2.6.35/arch/x86/kernel/check.c:134 check_for_bios_corruption+0xcb/0xe0()
[    0.154085] Hardware name: GateWay M210 and 3500 Series
[    0.154087] Memory corruption detected in low memory
[    0.154090] Modules linked in:
[    0.154096] Pid: 6, comm: events/0 Not tainted 2.6.35-22-generic #33-Ubuntu
[    0.154099] Call Trace:
[    0.154113]  [<c014ac52>] warn_slowpath_common+0x72/0xa0
[    0.154118]  [<c012d4cb>] ? check_for_bios_corruption+0xcb/0xe0
[    0.154123]  [<c012d4cb>] ? check_for_bios_corruption+0xcb/0xe0
[    0.154127]  [<c014ad23>] warn_slowpath_fmt+0x33/0x40
[    0.154132]  [<c012d4cb>] check_for_bios_corruption+0xcb/0xe0
[    0.154137]  [<c012d4ed>] check_corruption+0xd/0x30
[    0.154146]  [<c0161a4e>] run_workqueue+0x8e/0x150
[    0.154151]  [<c012d4e0>] ? check_corruption+0x0/0x30
[    0.154155]  [<c0161b94>] worker_thread+0x84/0xe0
[    0.154162]  [<c0165e10>] ? autoremove_wake_function+0x0/0x50
[    0.154167]  [<c0161b10>] ? worker_thread+0x0/0xe0
[    0.154171]  [<c01659e4>] kthread+0x74/0x80
[    0.154175]  [<c0165970>] ? kthread+0x0/0x80
[    0.154181]  [<c010363e>] kernel_thread_helper+0x6/0x10
[    0.154193] ---[ end trace 5a5d197966b56a2e ]---
[    0.154369] audit: initializing netlink socket (disabled)
[    0.154390] type=2000 audit(1289099123.152:1): initialized
[    0.168811] Trying to unpack rootfs image as initramfs...
[    3.255433] highmem bounce pool size: 64 pages
[    3.255442] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.257450] VFS: Disk quotas dquot_6.5.2
[    3.257528] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.258383] fuse init (API version 7.14)
[    3.258501] msgmni has been set to 1702
[    3.258848] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.258852] io scheduler noop registered
[    3.258855] io scheduler deadline registered
[    3.258873] io scheduler cfq registered (default)
[    3.259047] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.259076] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.259624] ACPI: AC Adapter [AC] (on-line)
[    3.259719] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    3.260187] ACPI: Lid Switch [LID0]
[    3.260251] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    3.260258] ACPI: Sleep Button [SLPB]
[    3.260321] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    3.260326] ACPI: Power Button [PWRB]
[    3.260390] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    3.260395] ACPI: Power Button [PWRF]
[    3.260561] ACPI: acpi_idle registered with cpuidle
[    3.260701] Marking TSC unstable due to TSC halts in idle
[    3.268107] Switching to clocksource acpi_pm
[    3.269367] thermal LNXTHERM:01: registered as thermal_zone0
[    3.269381] ACPI: Thermal Zone [THRM] (56 C)
[    3.269491] ERST: Table is not found!
[    3.269729] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.270188]   alloc irq_desc for 17 on node -1
[    3.270191]   alloc kstat_irqs on node -1
[    3.270203] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.270211] serial 0000:00:1f.6: PCI INT B disabled
[    3.271709] brd: module loaded
[    3.276641] loop: module loaded
[    3.277004] ata_piix 0000:00:1f.1: version 2.13
[    3.277030]   alloc irq_desc for 18 on node -1
[    3.277033]   alloc kstat_irqs on node -1
[    3.277045] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.277106] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.277393] scsi0 : ata_piix
[    3.277800] isapnp: Scanning for PnP cards...
[    3.286535] scsi1 : ata_piix
[    3.287955] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.287959] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.288508] Fixed MDIO Bus: probed
[    3.288561] PPP generic driver version 2.4.2
[    3.288666] tun: Universal TUN/TAP device driver, 1.6
[    3.288668] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.288787] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.288820]   alloc irq_desc for 23 on node -1
[    3.288823]   alloc kstat_irqs on node -1
[    3.288834] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.288860] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.288864] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.288909] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.288946] ehci_hcd 0000:00:1d.7: debug port 1
[    3.292843] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    3.298371] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe0100000
[    3.349961] ACPI: Battery Slot [BAT0] (battery present)
[    3.364081] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.364351] hub 1-0:1.0: USB hub found
[    3.364360] hub 1-0:1.0: 6 ports detected
[    3.364473] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.364504] uhci_hcd: USB Universal Host Controller Interface driver
[    3.364586]   alloc irq_desc for 16 on node -1
[    3.364590]   alloc kstat_irqs on node -1
[    3.364602] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.364617] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.364622] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.364686] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.364734] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001820
[    3.364895] hub 2-0:1.0: USB hub found
[    3.364902] hub 2-0:1.0: 2 ports detected
[    3.364982] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.364990] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.364994] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.365044] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.365077] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    3.365228] hub 3-0:1.0: USB hub found
[    3.365234] hub 3-0:1.0: 2 ports detected
[    3.365294] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.365301] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.365305] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.365344] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.365379] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.365537] hub 4-0:1.0: USB hub found
[    3.365542] hub 4-0:1.0: 2 ports detected
[    3.365685] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.372377] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.372398] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.372653] mice: PS/2 mouse device common for all mice
[    3.372903] rtc_cmos 00:01: RTC can wake from S4
[    3.372971] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    3.372996] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    3.373197] device-mapper: uevent: version 1.0.3
[    3.375805] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    3.380085] device-mapper: multipath: version 1.1.1 loaded
[    3.380093] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.380425] EISA: Probing bus 0 at eisa.0
[    3.380437] Cannot allocate resource for EISA slot 1
[    3.380442] Cannot allocate resource for EISA slot 2
[    3.380445] Cannot allocate resource for EISA slot 3
[    3.380467] EISA: Detected 0 cards.
[    3.386703] cpuidle: using governor ladder
[    3.386782] cpuidle: using governor menu
[    3.387232] TCP cubic registered
[    3.387435] NET: Registered protocol family 10
[    3.387931] lo: Disabled Privacy Extensions
[    3.388242] NET: Registered protocol family 17
[    3.388616] Using IPI No-Shortcut mode
[    3.388769] PM: Resume from disk failed.
[    3.388786] registered taskstats version 1
[    3.389043]   Magic number: 2:384:57
[    3.389189] rtc_cmos 00:01: setting system clock to 2010-11-07 03:05:26 UTC (1289099126)
[    3.389193] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.389196] EDD information not available.
[    3.395544] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.460737] ata2.00: ATAPI: HL-DT-ST DVD-RW GWA-4080N, 0G03, max UDMA/33
[    3.460871] ata1.00: ATA-6: ST9808210A, 3.04, max UDMA/100
[    3.460875] ata1.00: 156301488 sectors, multi 16: LBA48 
[    3.476409] ata2.00: configured for UDMA/33
[    3.476684] ata1.00: configured for UDMA/100
[    4.126976] isapnp: No Plug & Play device found
[    4.127195] scsi 0:0:0:0: Direct-Access     ATA      ST9808210A       3.04 PQ: 0 ANSI: 5
[    4.127464] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.127672] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    4.127741] sd 0:0:0:0: [sda] Write Protect is off
[    4.127745] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.127775] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.127968]  sda:
[    4.131328] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4080N 0G03 PQ: 0 ANSI: 5
[    4.135525] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.135534] Uniform CD-ROM driver Revision: 3.20
[    4.135747] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.135867] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.145482] Freeing initrd memory: 11144k freed
[    4.157146]  sda1 sda2 < sda5 >
[    4.185031] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.185058] Freeing unused kernel memory: 684k freed
[    4.185725] Write protecting the kernel text: 4932k
[    4.185773] Write protecting the kernel read-only data: 1976k
[    4.212201] udev[75]: starting version 163
[    4.484037] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    4.484363] acpi device:03: registered as cooling_device1
[    4.484495] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[    4.484586] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[    4.501001] Linux agpgart interface v0.103
[    4.524130] firewire_ohci 0000:02:07.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.524264] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[    4.525299] agpgart-intel 0000:00:00.0: detected 32636K stolen memory
[    4.528195] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    4.565429] [drm] Initialized drm 1.1.0 20060810
[    4.580129] firewire_ohci: Added fw-ohci device 0000:02:07.2, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    4.580370] b44 0000:02:08.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.600091] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[    4.600098] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    4.600104] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[    4.606672] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.606678] i915 0000:00:02.0: setting latency timer to 64
[    4.612196] [drm] set up 31M of stolen space
[    4.740208] ssb: Sonics Silicon Backplane found on PCI device 0000:02:08.0
[    4.740237] b44: b44.c:v2.0
[    4.746228] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    4.746644] [drm] initialized overlay support
[    5.008862] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:03:25:17:25:f9
[    5.080150] firewire_core: created device fw0: GUID 00032521410030ea, S400
[    5.536186] Skipping EDID probe due to cached edid
[    5.921657] Console: switching to colour frame buffer device 160x48
[    5.927140] fb0: inteldrmfb frame buffer device
[    5.927143] drm: registered panic notifier
[    5.927156] Slow work thread pool: Starting up
[    5.927223] Slow work thread pool: Ready
[    5.927234] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.084290] Skipping EDID probe due to cached edid
[    7.248806] Btrfs loaded
[    7.254933] xor: automatically using best checksumming function: pIII_sse
[    7.272009]    pIII_sse  :  4142.000 MB/sec
[    7.272012] xor: using function: pIII_sse (4142.000 MB/sec)
[    7.284603] device-mapper: dm-raid45: initialized v0.2594b
[    7.500142] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    7.500148] EXT4-fs (sda1): write access will be enabled during recovery
[    7.537751] EXT4-fs warning (device sda1): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    7.537757] EXT4-fs warning (device sda1): ext4_clear_journal_err: Marking fs in need of filesystem check.
[    7.537775] BUG: unable to handle kernel paging request at 01745000
[    7.537781] IP: [<c036228a>] __percpu_counter_sum+0x2a/0x70
[    7.537794] *pde = 00000000 
[    7.537798] Oops: 0000 [#1] SMP 
[    7.537801] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.1/host0/uevent
[    7.537806] Modules linked in: dm_raid45 xor btrfs zlib_deflate crc32c libcrc32c i915 drm_kms_helper drm b44 firewire_ohci intel_agp ssb i2c_algo_bit video firewire_core crc_itu_t mii output agpgart
[    7.537827] 
[    7.537833] Pid: 349, comm: exe Tainted: G        W   2.6.35-22-generic #33-Ubuntu 3520GZ/GateWay M210 and 3500 Series
[    7.537837] EIP: 0060:[<c036228a>] EFLAGS: 00010293 CPU: 0
[    7.537842] EIP is at __percpu_counter_sum+0x2a/0x70
[    7.537845] EAX: 00000000 EBX: 00000000 ECX: 01745000 EDX: 00000000
[    7.537849] ESI: 00000000 EDI: f6b1c494 EBP: f6963d6c ESP: f6963d60
[    7.537852]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[    7.537856] Process exe (pid: 349, ti=f6962000 task=f6b43f70 task.ti=f6962000)
[    7.537859] Stack:
[    7.537861]  f6b36a00 0087748b 00000000 f6963da0 c02ad8b6 c1485400 f6963d88 c05c6468
[    7.537869] <0> 00000001 c1485400 00877487 00000000 f6ea20e0 f6b36a00 f6b1c800 c1485400
[    7.537877] <0> f6963dd8 c02ada83 f6b36a00 c05e91b5 c0730c54 c073dd3e f6b1c800 f6963dd8
[    7.537887] Call Trace:
[    7.537897]  [<c02ad8b6>] ? ext4_commit_super+0xd6/0x1d0
[    7.537905]  [<c05c6468>] ? printk+0x2d/0x35
[    7.537910]  [<c02ada83>] ? ext4_clear_journal_err+0xa3/0xd0
[    7.537918]  [<c02d7ffc>] ? jbd2_journal_load+0x6c/0xd0
[    7.537922]  [<c02ad669>] ? ext4_msg+0x49/0x50
[    7.537927]  [<c02b0cff>] ? ext4_load_journal+0x14f/0x2e0
[    7.537933]  [<c02b219d>] ? ext4_fill_super+0x11fd/0x1a40
[    7.537940]  [<c03585b5>] ? vsnprintf+0xb5/0x430
[    7.537946]  [<c021b552>] ? get_sb_bdev+0x162/0x1a0
[    7.537951]  [<c02b0fa0>] ? ext4_fill_super+0x0/0x1a40
[    7.537956]  [<c02ac1d6>] ? ext4_get_sb+0x26/0x30
[    7.537961]  [<c02b0fa0>] ? ext4_fill_super+0x0/0x1a40
[    7.537965]  [<c021aee4>] ? vfs_kern_mount+0x74/0x1c0
[    7.537972]  [<c022f493>] ? get_fs_type+0x33/0xb0
[    7.537976]  [<c021b08e>] ? do_kern_mount+0x3e/0xe0
[    7.537981]  [<c023260c>] ? do_mount+0x1dc/0x220
[    7.537985]  [<c02326bb>] ? sys_mount+0x6b/0xa0
[    7.537991]  [<c05c90a4>] ? syscall_call+0x7/0xb
[    7.537993] Code: 00 55 89 e5 57 89 c7 56 53 e8 f3 68 26 00 8b 5f 04 b8 ff ff ff ff 8b 77 08 eb 1c 8d b6 00 00 00 00 8b 0c 85 80 56 81 c0 8b 57 14 <8b> 14 0a 89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 6c 93 5d c0 ba 
[    7.538038] EIP: [<c036228a>] __percpu_counter_sum+0x2a/0x70 SS:ESP 0068:f6963d60
[    7.538045] CR2: 0000000001745000
[    7.538050] ---[ end trace 5a5d197966b56a30 ]---
[    8.696929] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.696938] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.696945] Info fld=0x56ae6, ILI
[    8.696947] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.696958] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.696970] end_request: I/O error, dev sr0, sector 1420184
[    8.696974] Buffer I/O error on device sr0, logical block 177523
[    8.702100] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.702105] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.702110] Info fld=0x56ae6, ILI
[    8.702113] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.702119] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.702130] end_request: I/O error, dev sr0, sector 1420184
[    8.702133] Buffer I/O error on device sr0, logical block 177523
[    8.705579] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.705584] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.705589] Info fld=0x56ae6, ILI
[    8.705591] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.705598] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.705609] end_request: I/O error, dev sr0, sector 1420184
[    8.705612] Buffer I/O error on device sr0, logical block 177523
[    8.710442] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.710447] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.710452] Info fld=0x56ae6, ILI
[    8.710454] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.710461] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.710472] end_request: I/O error, dev sr0, sector 1420184
[    8.710475] Buffer I/O error on device sr0, logical block 177523
[    8.713561] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.713565] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.713571] Info fld=0x56ae6, ILI
[    8.713573] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.713580] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.713591] end_request: I/O error, dev sr0, sector 1420184
[    8.713594] Buffer I/O error on device sr0, logical block 177523
[    8.716830] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.716835] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.716840] Info fld=0x56ae6, ILI
[    8.716842] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.716849] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.716860] end_request: I/O error, dev sr0, sector 1420184
[    8.716863] Buffer I/O error on device sr0, logical block 177523
[    8.721419] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.721424] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.721429] Info fld=0x56ae6, ILI
[    8.721432] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.721438] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.721449] end_request: I/O error, dev sr0, sector 1420184
[    8.721452] Buffer I/O error on device sr0, logical block 177523
[    8.818165] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.818170] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.818176] Info fld=0x56ae6, ILI
[    8.818179] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.818185] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.818196] end_request: I/O error, dev sr0, sector 1420184
[    8.818200] Buffer I/O error on device sr0, logical block 177523
[    8.823355] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.823360] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.823365] Info fld=0x56ae6, ILI
[    8.823368] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.823374] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.823385] end_request: I/O error, dev sr0, sector 1420184
[    8.823388] Buffer I/O error on device sr0, logical block 177523
[    8.826884] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.826888] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.826894] Info fld=0x56ae6, ILI
[    8.826896] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    8.826903] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
[    8.826914] end_request: I/O error, dev sr0, sector 1420184
[    8.826917] Buffer I/O error on device sr0, logical block 177523
[    9.588542] ISO 9660 Extensions: Microsoft Joliet Level 3
[    9.664753] ISO 9660 Extensions: RRIP_1991A
[    9.827268] aufs 2-standalone.tree-35-rcN-20100705
[    9.919172] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   67.322323] Adding 3227644k swap on /dev/sda5.  Priority:-1 extents:1 across:3227644k 
[   69.115626] udev[1162]: starting version 163
[   74.502808] intel_rng: FWH not detected
[   74.588690] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   75.106040] lib80211: common routines for IEEE802.11 drivers
[   75.106045] lib80211_crypt: registered algorithm 'NULL'
[   75.661471] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008/0x0
[   75.697840] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   76.175171] tifm_7xx1 0000:02:07.3: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   76.176986] yenta_cardbus 0000:02:07.0: CardBus bridge found [161f:203e]
[   76.177001] yenta_cardbus 0000:02:07.0: Enabling burst memory read transactions
[   76.177007] yenta_cardbus 0000:02:07.0: Using CSCINT to route CSC interrupts to PCI
[   76.177010] yenta_cardbus 0000:02:07.0: Routing CardBus interrupts to PCI
[   76.177016] yenta_cardbus 0000:02:07.0: TI: mfunc 0x00001002, devctl 0x64
[   76.196844] tifm_core: MMC/SD card detected in socket 0:3
[   76.197344] cfg80211: Calling CRDA to update world regulatory domain
[   76.408785] yenta_cardbus 0000:02:07.0: ISA IRQ mask 0x0cf8, PCI irq 19
[   76.408791] yenta_cardbus 0000:02:07.0: Socket status: 30000006
[   76.408797] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   76.408812] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   76.408817] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: excluding 0x3000-0x30ff 0x3400-0x34ff
[   76.414736] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge window: [mem 0xe0200000-0xe02fffff]
[   76.414741] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0200000-0xe02fffff: excluding 0xe0200000-0xe020ffff
[   76.414760] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge window: [mem 0x50000000-0x53ffffff pref]
[   76.414764] pcmcia_socket pcmcia_socket0: cs: memory probe 0x50000000-0x53ffffff: excluding 0x50000000-0x53ffffff
[   76.504077] libipw: 802.11 data/management/control stack, git-1.1.13
[   76.504082] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   76.909303] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   76.909308] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   76.909459] ipw2200 0000:02:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   76.909635] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   78.083211] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   78.084949] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   78.085665] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   78.086262] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   78.086916] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   78.086991] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   78.087065] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   78.087142] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   78.743369] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   79.105538] cfg80211: World regulatory domain updated:
[   79.105545]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   79.105550]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   79.105554]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   79.105558]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   79.105561]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   79.105565]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   79.620124] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   79.620173] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   80.620035] intel8x0_measure_ac97_clock: measured 53828 usecs (2594 samples)
[   80.620041] intel8x0: clocking to 48000
[   80.816856] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   82.360255] lp: driver loaded but no devices found
[   83.065962] ppdev: user-space parallel port driver
[   91.392020] eth1: no IPv6 routers present
[  355.485510] lib80211_crypt: registered algorithm 'WEP'
[  478.149754] JFS: nTxBlock = 8192, nTxLock = 65536
[  478.527462] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  478.534106] SGI XFS Quota Management subsystem
[  480.444380] NTFS driver 2.1.29 [Flags: R/O MODULE].
[  480.692501] QNX4 filesystem 0.2.3 registered.

---------------------------------------------------------------------------

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000da60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

---

### Post by P4man on 2010-11-07
Please use [code] tags for such long outputs.

You have some serious issues there. A kernel oops and IO errors. If you still have a 10.04 cd, can you try booting that? If that gives the same problem, then its pretty sure a hardware issue. If 10.04 works, we may need to poke around in the bios

---

