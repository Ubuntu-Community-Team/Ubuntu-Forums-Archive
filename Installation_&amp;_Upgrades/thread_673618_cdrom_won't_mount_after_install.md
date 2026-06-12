---
title: "cdrom won't mount after install"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by slack42 on 2008-01-20
Hi, I just did a install of Gutsy on a Dell C610. It has a bay where I can change it to either a cdrom drive or a floppy drive. I did the install no problem using the cdrom drive but now when I put a cd in the drive I get the "special device /dev/scd0 does not exist" message. 

I've done a lot of searching to try and solve this problem and here are some of the things I've done. First I looked in my /etc/fstab and the line for the cdrom is

/dev/scd0    /media/cdrom0      udf,iso9660 user,noauto,exec   0   0

That is how it is on another laptop I have so it looks right to me. When I check /dev there is in no scd0 in there and I saw where someone suggested using /dev/sr0 but that doesn't exist for me either. so I tried creating scd0 manually with.

sudo mknod  scd0 b 11 0

I got the major and minor numbers from my other laptop. And then I changed the group to cdrom and gave it the same permissions as on my laptop. And I also created a symbolic link to /media/cdrom0. 

But when I try to access the drive I get the message that it is not a valid block device, so I'm not sure I did something wrong when I created the node. I also saw on another forum where some suggested seeing if the sr_mod was loaded and when I checked it wasn't and so I did.

sudo modprobe sr_mod

But that didn't work either. I also saw on another forum that someone added  acpi=off when there kernel loads but I haven't tried that because I don't know where to do that. Would it be in the grub menu.lst file? And if so how would it look?

I'm guessing that the fact that my drive is one that is interchangeable is a part of the reason it's not working. But I don't understand why the drive worked when I did the install and now all of a sudden it decides to not work. I can't think of anything else to try and I have yet to find anything that will work for me from searching google.

Any suggestions would be appreciated.

---

### Post by enigma_0Z on 2008-01-20
Can you post the output from the following commands after receiving the "special device does not exist" error:

```
dmesg
```
```
ls /dev/sc*
```
[code[ls /dev/sr*[/code]
```
lshw
```

Dmesg will probably be the most useful, and if it's hot-pluggable, it may be getting a different device node than /dev/scd0

---

### Post by slack42 on 2008-01-20
Thanks for the response, here is the info you asked for.




```


dmesg

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffd3000 (usable)
[    0.000000]  BIOS-e820: 000000001ffd3000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131027) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131027
[    0.000000]   HighMem    131027 ->   131027
[    0.000000] early_node_map[1] active PFN ranges

 0xc02f7de6   (2015 kB)
[   73.345512] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   73.345643] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   73.425678] Calibrating delay using timer specific routine.. 1994.98 BogoMIPS (lpj=3989975)
[   73.425785] Security Framework v1.0.0 initialized
[   73.425828] SELinux:  Disabled at boot.
[   73.425886] Mount-cache hash table entries: 512
[   73.426143] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   73.426164] CPU: L1 I cache: 16K, L1 D cache: 16K
[   73.426217] CPU: L2 cache: 512K
[   73.426250] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   73.426268] Compat vDSO mapped to ffffe000.
[   73.426316] Checking 'hlt' instruction... OK.
[   73.441826] SMP alternatives: switching to UP code
[   73.442089] Freeing SMP alternatives: 11k freed
[   73.442565] Early unpacking initramfs... done
[   74.066055] ACPI: Core revision 20070126
[   74.066256] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   74.069235] ACPI: setting ELCR to 0200 (from 0800)
[   75.107273] CPU0: Intel Mobile Intel(R) Pentium(R) III CPU - M  1000MHz stepping 04
[   75.107378] SMP motherboard not detected.
[   75.107410] Local APIC not detected. Using dummy APIC emulation.
[   75.107527] Brought up 1 CPUs
[   75.107835] Booting paravirtualized kernel on bare hardware
[   75.107966] Time:  3:08:19  Date: 00/21/108
[   75.108054] NET: Registered protocol family 16
[   75.108308] EISA bus registered
[   75.108355] ACPI: bus type pci registered
[   75.133371] PCI: PCI BIOS revision 2.10 entry at 0xfbfee, last bus=2
[   75.133406] PCI: Using configuration type 1
[   75.133438] Setting up standard PCI resources
[   75.137453] ACPI: EC: Look up EC in DSDT
[   75.149677] ACPI: Interpreter enabled
[   75.149717] ACPI: (supports S0 S1 S3 S4 S5)
[   75.149889] ACPI: Using PIC for interrupt routing
[   75.175945] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   75.176014] PCI: Probing PCI hardware (bus 00)
[   75.176282] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   75.176318] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   75.176774] PCI: Transparent bridge - 0000:00:1e.0
[   75.176985] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   75.177183] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   75.177216] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   75.198651] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[   75.198983] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[   75.199309] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[   75.199635] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[   75.200013] ACPI: Power Resource [PADA] (on)
[   75.200057] Linux Plug and Play Support v0.97 (c) Adam Belay
[   75.200106] pnp: PnP ACPI init
[   75.200151] ACPI: bus type pnp registered
[   75.263433] pnp: PnP ACPI: found 17 devices
[   75.263469] ACPI: ACPI bus type pnp unregistered
[   75.263507] PnPBIOS: Disabled by ACPI PNP
[   75.263645] PCI: Using ACPI for IRQ routing
[   75.263678] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   75.267199] NET: Registered protocol family 8
[   75.267232] NET: Registered protocol family 20
[   75.267399] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
[   75.267436] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   75.267472] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
[   75.267508] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   75.267549] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   75.267584] pnp: 00:02: ioport range 0x800-0x805 has been reserved
[   75.267619] pnp: 00:02: ioport range 0x808-0x80f has been reserved
[   75.267660] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[   75.267694] pnp: 00:03: ioport range 0x810-0x85f has been reserved
[   75.267729] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[   75.267763] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[   75.267797] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
[   75.267832] pnp: 00:03: ioport range 0x8e0-0x8ff has been reserved
[   75.267873] pnp: 00:04: ioport range 0xf000-0xf0fe has been reserved
[   75.267908] pnp: 00:04: ioport range 0xf100-0xf1fe has been reserved
[   75.267943] pnp: 00:04: ioport range 0xf200-0xf2fe has been reserved
[   75.267977] pnp: 00:04: ioport range 0xf400-0xf4fe has been reserved
[   75.268012] pnp: 00:04: ioport range 0xf500-0xf5fe has been reserved
[   75.268047] pnp: 00:04: ioport range 0xf600-0xf6fe has been reserved
[   75.268082] pnp: 00:04: ioport range 0xf800-0xf8fe has been reserved
[   75.268118] pnp: 00:04: ioport range 0xf900-0xf9fe has been reserved
[   75.268153] pnp: 00:04: iomem range 0xfa000000-0xfbffffff has been reserved
[   75.268197] pnp: 00:09: ioport range 0x900-0x91f has been reserved
[   75.268232] pnp: 00:09: ioport range 0x3f0-0x3f1 has been reserved
[   75.268274] pnp: 00:0f: ioport range 0xbf40-0xbf5f has been reserved
[   75.268309] pnp: 00:0f: ioport range 0xbf20-0xbf3f has been reserved
[   75.268349] pnp: 00:10: iomem range 0xfebffc00-0xfebfffff has been reserved
[   75.269046] Time: tsc clocksource has been installed.
[   75.298971] PCI: Bridge: 0000:00:01.0
[   75.299004]   IO window: c000-cfff
[   75.299037]   MEM window: fc000000-fdffffff
[   75.299070]   PREFETCH window: e0000000-e7ffffff
[   75.299116] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[   75.299149]   IO window: 0000e000-0000e0ff
[   75.299182]   IO window: 0000e400-0000e4ff
[   75.299215]   PREFETCH window: 30000000-33ffffff
[   75.299249]   MEM window: f4000000-f7ffffff
[   75.299282] PCI: Bus 7, cardbus bridge: 0000:02:01.1
[   75.299314]   IO window: 0000e800-0000e8ff
[   75.299347]   IO window: 0000fc00-0000fcff
[   75.299381]   PREFETCH window: 34000000-37ffffff
[   75.299415]   MEM window: 3c000000-3fffffff
[   75.299448] PCI: Bridge: 0000:00:1e.0
[   75.299480]   IO window: e000-ffff
[   75.299514]   MEM window: f4000000-fbffffff
[   75.299548]   PREFETCH window: 30000000-39ffffff
[   75.299594] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   75.299611] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[   75.299970] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   75.300005] PCI: setting IRQ 11 as level-triggered
[   75.300011] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   75.300105] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
[   75.300140] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   75.300246] NET: Registered protocol family 2
[   75.337088] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   75.337211] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   75.337735] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   75.338168] TCP: Hash tables configured (established 16384 bind 16384)
[   75.338204] TCP reno registered
[   75.349365] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   75.888873]  it is
[   76.533112] Freeing initrd memory: 7070k freed
[   76.533954] audit: initializing netlink socket (disabled)
[   76.534020] audit(1200884898.892:1): initialized
[   76.538631] VFS: Disk quotas dquot_6.5.1
[   76.538795] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   76.539052] io scheduler noop registered
[   76.539087] io scheduler anticipatory registered
[   76.539119] io scheduler deadline registered
[   76.539190] io scheduler cfq registered (default)
[   76.539275] Boot video device is 0000:01:00.0
[   76.539607] isapnp: Scanning for PnP cards...
[   76.892401] isapnp: No Plug & Play device found
[   76.947423] Real Time Clock Driver v1.12ac
[   76.947665] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   76.947827] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   76.949247] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   76.950000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   76.950038] PCI: setting IRQ 5 as level-triggered
[   76.950044] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   76.950133] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   76.951313] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   76.951771] input: Macintosh mouse button emulation as /class/input/input0
[   76.951972] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   76.957741] serio: i8042 KBD port at 0x60,0x64 irq 1
[   76.957786] serio: i8042 AUX port at 0x60,0x64 irq 12
[   76.958156] mice: PS/2 mouse device common for all mice
[   76.958400] EISA: Probing bus 0 at eisa.0
[   76.958465] EISA: Detected 0 cards.
[   76.958712] TCP cubic registered
[   76.959865] NET: Registered protocol family 1
[   76.959947] Using IPI No-Shortcut mode
[   76.960275]   Magic number: 8:924:108
[   76.961007] Freeing unused kernel memory: 364k freed
[   76.992451] input: AT Translated Set 2 keyboard as /class/input/input1
[   77.286285] AppArmor: AppArmor initialized<5>audit(1200884899.892:2):  type=1505 info="AppArmor initialized" pid=1181
[   77.304673] fuse init (API version 7.8)
[   77.316985] Failure registering capabilities with primary security module.
[   77.340638] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   77.354596] ACPI: Thermal Zone [THM] (58 C)
[   78.314522] usbcore: registered new interface driver usbfs
[   78.314619] usbcore: registered new interface driver hub
[   78.314692] usbcore: registered new device driver usb
[   78.317479] USB Universal Host Controller Interface driver v3.0
[   78.318051] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   78.318088] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   78.318182] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   78.318189] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   78.318494] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   78.318566] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[   78.318839] usb usb1: configuration #1 chosen from 1 choice
[   78.318921] hub 1-0:1.0: USB hub found
[   78.318961] hub 1-0:1.0: 2 ports detected
[   78.435874] SCSI subsystem initialized
[   78.454795] libata version 2.21 loaded.
[   78.466197] ata_piix 0000:00:1f.1: version 2.11
[   78.466223] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   78.466277] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   78.466415] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   78.466620] scsi0 : ata_piix
[   78.466739] scsi1 : ata_piix
[   78.468161] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[   78.468206] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[   78.633408] ata1.00: ATA-6: ST960815A, 3.ALD, max UDMA/100
[   78.633455] ata1.00: 117210240 sectors, multi 8: LBA48 
[   78.648199] ata1.00: configured for UDMA/100
[   78.805879] scsi 0:0:0:0: Direct-Access     ATA      ST960815A        3.AL PQ: 0 ANSI: 5
[   78.806876] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   78.806913] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   78.807001] 3c59x: Donald Becker and others.
[   78.807038] 0000:02:00.0: 3Com PCI 3c905C Tornado at e0814c00.
[   78.874681] Floppy drive(s): fd0 is 1.44M
[   78.938386] FDC 0 is a post-1991 82077
[   79.017290] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   79.017356] sd 0:0:0:0: [sda] Write Protect is off
[   79.017390] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   79.017423] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   79.017562] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   79.017613] sd 0:0:0:0: [sda] Write Protect is off
[   79.017647] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   79.017680] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   79.017725]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   79.097375] sd 0:0:0:0: [sda] Attached SCSI disk
[   79.106643] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.776000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.780000] Time: acpi_pm clocksource has been installed.
[    4.924000] Attempting manual resume
[    4.924000] swsusp: Resume From Partition 8:3
[    4.924000] PM: Checking swsusp image.
[    4.924000] PM: Resume from disk failed.
[    4.972000] kjournald starting.  Commit interval 5 seconds
[    4.972000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.420000] Clocksource tsc unstable (delta = -81911936 ns)
[   16.168000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.188000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.204000] iTCO_vendor_support: vendor-support=0
[   16.208000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   16.208000] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x0860)
[   16.208000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.256000] intel_rng: FWH not detected
[   16.328000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.420000] agpgart: Detected an Intel 830M Chipset.
[   16.436000] agpgart: AGP aperture is 256M @ 0xd0000000
[   17.152000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:00e3]
[   17.152000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.152000] Yenta: Routing CardBus interrupts to PCI
[   17.152000] Yenta TI: socket 0000:02:01.0, mfunc 0x01261222, devctl 0x64
[   17.384000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
[   17.384000] Socket status: 30000006
[   17.384000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   17.384000] cs: IO port probe 0xe000-0xffff: clean.
[   17.384000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   17.384000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x39ffffff
[   17.384000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:00e3]
[   17.384000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.384000] Yenta: Routing CardBus interrupts to PCI
[   17.384000] Yenta TI: socket 0000:02:01.1, mfunc 0x01261222, devctl 0x64
[   17.616000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
[   17.616000] Socket status: 30000006
[   17.616000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   17.616000] cs: IO port probe 0xe000-0xffff: clean.
[   17.616000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   17.616000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x39ffffff
[   18.604000] input: PC Speaker as /class/input/input2
[   19.088000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   19.088000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   19.436000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   19.436000] cs: IO port probe 0x100-0x3af: excluding 0x378-0x37f
[   19.440000] cs: IO port probe 0x3e0-0x4ff: clean.
[   19.440000] cs: IO port probe 0x820-0x8ff: clean.
[   19.440000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.440000] cs: IO port probe 0xa00-0xaff: clean.
[   19.440000] parport_pc 00:0e: reported by Plug and Play ACPI
[   19.440000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   19.564000] cs: IO port probe 0x100-0x3af: clean.
[   19.564000] cs: IO port probe 0x3e0-0x4ff: clean.
[   19.564000] cs: IO port probe 0x820-0x8ff: clean.
[   19.564000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.564000] cs: IO port probe 0xa00-0xaff: clean.
[   19.844000] intel8x0_measure_ac97_clock: measured 55360 usecs
[   19.844000] intel8x0: clocking to 48000
[   20.416000] lp0: using parport0 (interrupt-driven).
[   20.480000] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k
[   20.816000] EXT3 FS on sda2, internal journal
[   21.696000] kjournald starting.  Commit interval 5 seconds
[   21.696000] EXT3 FS on sda1, internal journal
[   21.696000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.716000] kjournald starting.  Commit interval 5 seconds
[   21.716000] EXT3 FS on sda5, internal journal
[   21.716000] EXT3-fs: mounted filesystem with ordered data mode.
[   24.424000] ACPI: ACPI Dock Station Driver 
[   24.584000] ACPI: AC Adapter [AC] (on-line)
[   24.936000] ACPI: Battery Slot [BAT0] (battery present)
[   24.936000] ACPI: Battery Slot [BAT1] (battery absent)
[   25.044000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.128000] input: Lid Switch as /class/input/input4
[   25.128000] ACPI: Lid Switch [LID]
[   25.144000] input: Power Button (CM) as /class/input/input5
[   25.144000] ACPI: Power Button (CM) [PBTN]
[   25.152000] input: Sleep Button (CM) as /class/input/input6
[   25.152000] ACPI: Sleep Button (CM) [SBTN]
[   27.152000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   27.152000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   27.788000] eth0:  setting full-duplex.
[   28.648000] NET: Registered protocol family 10
[   28.652000] lo: Disabled Privacy Extensions
[   29.052000] ppdev: user-space parallel port driver
[   29.236000] audit(1200884927.533:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4991 profile="/usr/sbin/cupsd"
[   29.352000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   29.352000] apm: overridden by ACPI.
[   29.708000] Failure registering capabilities with primary security module.
[   29.920000] Bluetooth: Core ver 2.11
[   29.920000] NET: Registered protocol family 31
[   29.920000] Bluetooth: HCI device and connection manager initialized
[   29.920000] Bluetooth: HCI socket layer initialized
[   29.944000] Bluetooth: L2CAP ver 2.8
[   29.944000] Bluetooth: L2CAP socket layer initialized
[   30.008000] Bluetooth: RFCOMM socket layer initialized
[   30.008000] Bluetooth: RFCOMM TTY layer initialized
[   30.008000] Bluetooth: RFCOMM ver 1.8
[   31.664000] [drm] Initialized drm 1.1.0 20060810
[   31.680000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   31.684000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   34.088000] NET: Registered protocol family 17
[   34.116000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   34.116000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   34.116000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   35.460000] [drm] Setting GART location based on new memory map
[   35.460000] [drm] writeback test succeeded in 1 usecs
[   46.116000] eth0: no IPv6 routers present
[   87.276000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[   87.276000] ata2: (ACPI event)
[   87.276000] ata2: soft resetting port
[   87.432000] ata2: EH complete
[  154.640000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[  154.640000] ata2: (ACPI event)
[  154.640000] ata2: soft resetting port
[  154.796000] ata2: EH complete
[  159.584000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[  159.584000] ata2: (ACPI event)
[  159.584000] ata2: soft resetting port
[  159.740000] ata2: EH complete
[  230.408000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[  230.408000] ata2: (ACPI event)
[  230.408000] ata2: soft resetting port
[  230.564000] ata2: EH complete
[  585.836000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[  585.836000] ata2: (ACPI event)
[  590.876000] ata2: port is slow to respond, please be patient (Status 0xb4)
[  595.860000] ata2: device not ready (errno=-16), forcing hardreset
[  595.860000] ata2: soft resetting port
[  596.016000] ata2: EH complete
[  609.764000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[  609.764000] ata2: (ACPI event)
[  609.764000] ata2: soft resetting port
[  609.920000] ata2: EH complete
[  621.100000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[  621.100000] ata2: (ACPI event)
[  621.100000] ata2: soft resetting port
[  621.256000] ata2: EH complete
[ 2812.432000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2812.432000] ata2: (ACPI event)
[ 2812.432000] ata2: soft resetting port
[ 2812.588000] ata2: EH complete
[ 2816.664000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2816.664000] ata2: (ACPI event)
[ 2816.664000] ata2: soft resetting port
[ 2816.820000] ata2: EH complete

```

```


ls /dev/sc*

ls: /dev/sc*: No such file or directory

```


```


lshw

WARNING: you should run this program as super-user.
pat-laptop                
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: Mobile Intel(R) Pentium(R) III CPU - M  1000MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.4
          size: 997MHz
          capacity: 997MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82830 830 Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon Mobility M6 LY
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master vga_palette cap_list
                configuration: latency=32 mingnt=8
        *-usb
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 78
                serial: 00:0b:db:a5:db:dd
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=3c59x ip=192.168.0.103 latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic bus_master
             configuration: driver=Intel ICH Modem latency=0 module=snd_intel8x0m

```

---

### Post by slack42 on 2008-01-22
I got the cdrom working. I had put a new hard drive in the laptop and installed Ubuntu on it and I had also did a BIOS upgrade. So I took the old hard drive witch still had Windows on it and I thought I could boot into it and flash the BIOS again using the hard drive installer from Dell. I was thinking tha maybe something went wrong when I did the initial BIOS upgrade.

When I got into Windows it didn't see the cdrom either so I thought I would plug in the floppy module to see if it would see that. And what do you know it did, so I figured why not plug in the cdrom drive back in and see what happens. And Windows saw it and I was even able to put in a CD and have it recognized. 

So I guess that in the end all I had to really do was reload the cdrom drive and I could have avoided a lot these problems. As it usually is with these kinds of things the simplest answer was the solution, I should have tried this before but it just didn't dawn on me to try the other module. 

I now have the hard drive with Ubuntu back in and it's working great again. Sorry If I wasted any of your time and I thank you for trying to help.

---

