---
title: "Xubuntu 7.04 install cannot recognise scsi disks"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by akoong on 2007-05-10
I have an old Digital Celebris XL5133DP that I have successfully installed with Ubuntu 6.06. 

I tried installing Xubuntu 7.04 on it using the alternate CD distro. At the disk partitioning stage, it could not recognise the SCSI disks. Only the IDE disk was recognised. When I was installing Ubuntu 6.06 both the SCSI and IDE disks were recognised.

I have provided the dmesg output below.

I would to try Xubuntu as it is suppose to be lighter hardware resource.

Would appreciate any help on this.

********************************
dmesg output:

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f5990 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000a000000 (usable)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff5990 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 160MB LOWMEM available.
[17179569.184000] found SMP MP-table at 0009fc30
[17179569.184000] On node 0 totalpages: 40960
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 36864 pages, LIFO batch:7
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI not present.
[17179569.184000] Intel MultiProcessor Specification v1.1
[17179569.184000]     Virtual Wire compatibility mode.
[17179569.184000] Default MP configuration #5
[17179569.184000] Processor #0 5:2 APIC version 16
[17179569.184000] Processor #1 5:2 APIC version 16
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] I/O APIC #2 Version 16 at 0xFEC00000.
[17179569.184000] ISA/PCI bus type with no IRQ information... falling back to ELCR
[17179569.184000] Using ELCR to identify PCI interrupts
[17179569.184000] Processors: 1
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0a000000:f4c00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash acpi=off
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 166.698 MHz processor.
[  123.967415] Using tsc for high-res timesource
[  123.969154] Console: colour VGA+ 80x25
[  123.975035] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[  123.981156] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[  124.058795] Memory: 151912k/163840k available (1976k kernel code, 11392k reserved, 606k data, 288k init, 0k highmem)
[  124.058872] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  124.138246] Calibrating delay using timer specific routine.. 334.30 BogoMIPS (lpj=668613)
[  124.138794] Security Framework v1.0.0 initialized
[  124.138900] SELinux:  Disabled at boot.
[  124.139135] Mount-cache hash table entries: 512
[  124.141251] CPU: After generic identify, caps: 000003bf 00000000 00000000 00000000 00000000 00000000 00000000
[  124.141352] CPU: After vendor identify, caps: 000003bf 00000000 00000000 00000000 00000000 00000000 00000000
[  124.141438] Intel Pentium with F0 0F bug - workaround enabled.
[  124.141489] CPU: After all inits, caps: 000003bf 00000000 00000000 00000000 00000000 00000000 00000000
[  124.141819] mtrr: v2.0 (20020519)
[  124.141848] CPU: Intel Pentium 75 - 200 stepping 0c
[  124.141914] Checking 'hlt' instruction... OK.
[  124.156288] checking if image is initramfs... it is
[  134.242518] Freeing initrd memory: 6617k freed
[  134.452346] ExtINT not setup in hardware but reported by MP table
[  134.452436] ENABLING IO-APIC IRQs
[  134.452868] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[  134.604979] NET: Registered protocol family 16
[  134.605753] EISA bus registered
[  134.607884] PCI: PCI BIOS revision 2.10 entry at 0xfbedf, last bus=0
[  134.607986] PCI: Using configuration type 2
[  134.613971] ACPI: Subsystem revision 20051216
[  134.614009] ACPI: Interpreter disabled.
[  134.614064] Linux Plug and Play Support v0.97 (c) Adam Belay
[  134.614235] pnp: PnP ACPI: disabled
[  134.614285] PnPBIOS: Scanning system for PnP BIOS support...
[  134.614564] PnPBIOS: Found PnP BIOS installation structure at 0xc00f5f90
[  134.614629] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb10c, dseg 0xf0000[  134.630969] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[  134.631311] PCI: Probing PCI hardware
[  134.631363] PCI: Probing PCI hardware (bus 00)
[  134.633191] Boot video device is 0000:00:08.0
[  134.638454] PCI BIOS passed nonexistent PCI bus 0!
[  134.638510] PCI BIOS passed nonexistent PCI bus 0!
[  134.638551] PCI BIOS passed nonexistent PCI bus 0!
[  134.641075] pnp: 00:01: ioport range 0x26e-0x26f has been reserved
[  134.661134] audit: initializing netlink socket (disabled)
[  134.661300] audit(1178788906.805:1): initialized
[  134.663391] VFS: Disk quotas dquot_6.5.1
[  134.663877] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  134.664977] Initializing Cryptographic API
[  134.665058] io scheduler noop registered
[  134.665163] io scheduler anticipatory registered
[  134.665249] io scheduler deadline registered
[  134.665425] io scheduler cfq registered
[  134.668882] isapnp: Scanning for PnP cards...
[  134.779373] pnp: SB audio device quirk - increasing port range
[  134.781205] isapnp: Card 'Creative ViBRA16C PnP'
[  134.781253] isapnp: 1 Plug & Play card detected total
[  135.271930] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[  135.276432] serio: i8042 AUX port at 0x60,0x64 irq 12
[  135.277659] serio: i8042 KBD port at 0x60,0x64 irq 1
[  135.278693] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[  135.280167] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  135.281410] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  135.334582] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  135.337275] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  135.352613] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  135.353778] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  135.353842] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  135.356731] mice: PS/2 mouse device common for all mice
[  135.359749] EISA: Probing bus 0 at eisa.0
[  135.360034] EISA: Detected 0 cards.
[  135.360724] NET: Registered protocol family 2
[  135.386330] input: AT Translated Set 2 keyboard as /class/input/input0
[  135.404485] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[  135.407278] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[  135.408432] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[  135.409490] TCP: Hash tables configured (established 8192 bind 8192)
[  135.409534] TCP reno registered
[  135.410821] TCP bic registered
[  135.410941] NET: Registered protocol family 1
[  135.411047] NET: Registered protocol family 8
[  135.411085] NET: Registered protocol family 20
[  135.411395] Using IPI Shortcut mode
[  135.411989] Freeing unused kernel memory: 288k freed
[  136.403990] vga16fb: initializing
[  136.404082] vga16fb: mapped to 0xc00a0000
[  136.540355] Console: switching to colour frame buffer device 80x25
[  136.540468] fb0: VGA16 VGA frame buffer device
[  137.962746] Capability LSM initialized
[  147.596256] SCSI subsystem initialized
[  147.656426] sym0: <810> rev 0x2 at pci 0000:00:01.0 irq 11
[  147.659551] sym0: No NVRAM, ID 7, Fast-10, SE, parity checking
[  147.667334] sym0: SCSI BUS has been reset.
[  147.667458] scsi0 : sym-2.2.2
[  150.672471]  target0:0:0: FAST-10 SCSI 10.0 MB/s ST (100 ns, offset 8)
[  150.674601]   Vendor: IBM OEM   Model: DCHS04Z           Rev: 2626
[  150.674721]   Type:   Direct-Access                      ANSI SCSI revision: 02
[  150.674830]  target0:0:0: tagged command queuing enabled, command queue depth 16.
[  150.675157]  target0:0:0: Beginning Domain Validation
[  150.675785]  target0:0:0: asynchronous.
[  150.680135]  target0:0:0: FAST-10 SCSI 10.0 MB/s ST (100 ns, offset 8)
[  150.682969]  target0:0:0: Domain Validation skipping write tests
[  150.683022]  target0:0:0: Ending Domain Validation
[  150.693317]   Vendor: CONNER    Model: CFP1060S 1.05GB   Rev: 2035
[  150.693444]   Type:   Direct-Access                      ANSI SCSI revision: 02
[  150.693535]  target0:0:1: tagged command queuing enabled, command queue depth 16.
[  150.693857]  target0:0:1: Beginning Domain Validation
[  150.694801]  target0:0:1: asynchronous.
[  150.699320]  target0:0:1: FAST-10 SCSI 10.0 MB/s ST (100 ns, offset 8)
[  150.702097]  target0:0:1: Domain Validation skipping write tests
[  150.702150]  target0:0:1: Ending Domain Validation
[  152.362026] Driver 'sd' needs updating - please use bus_type methods
[  152.530530] SCSI device sda: 8888543 512-byte hdwr sectors (4551 MB)
[  152.588262] SCSI device sda: drive cache: write through
[  152.655497] SCSI device sda: 8888543 512-byte hdwr sectors (4551 MB)
[  152.713185] SCSI device sda: drive cache: write through
[  152.713247]  sda: sda1
[  152.727128] sd 0:0:0:0: Attached scsi disk sda
[  152.752454] SCSI device sdb: 2074880 512-byte hdwr sectors (1062 MB)
[  152.755985] SCSI device sdb: drive cache: write through
[  152.763569] SCSI device sdb: 2074880 512-byte hdwr sectors (1062 MB)
[  152.766896] SCSI device sdb: drive cache: write through
[  152.766957]  sdb: sdb1 < sdb5 >
[  152.782840] sd 0:0:1:0: Attached scsi disk sdb
[  154.161429] Probing IDE interface ide0...
[  154.575223] hda: WDC WD200EB-00BHF0, ATA DISK drive
[  155.023103] hdb: MATSHITA CD-RW CW-7586, ATAPI CD/DVD-ROM drive
[  155.078825] Probing IDE interface ide1...
[  155.638991] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[  155.773332] hda: max request size: 128KiB
[  155.911229] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63[  155.911317] hda: cache flushes not supported
[  155.913710]  hda: hda1
[  155.938213] hdb: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache
[  155.938316] Uniform CD-ROM driver Revision: 3.20
[  157.008448] Attempting manual resume
[  157.229234] EXT3-fs: mounted filesystem with ordered data mode.
[  157.234481] kjournald starting.  Commit interval 5 seconds
[  195.914736] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  195.933412] sd 0:0:1:0: Attached scsi generic sg1 type 0
[  263.665433] Linux agpgart interface v0.101 (c) Dave Jones
[  264.286701] nvidia: module license 'NVIDIA' taints kernel.
[  264.385982] NVRM: The NVIDIA RIVA TNT2 Model 64/Model 64 Pro GPU installed in this system is
[  264.386035] NVRM:  supported through the NVIDIA Legacy drivers. Please
[  264.386066] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[  264.386097] NVRM:  information.  The 1.0-8762 NVIDIA driver will ignore
[  264.386128] NVRM:  this GPU.  Continuing probe...
[  264.386210] NVRM: No NVIDIA graphics adapter found!
[  265.258989] input: PS/2 Generic Mouse as /class/input/input1
[  269.341118] input: PC Speaker as /class/input/input2
[  269.488446] Floppy drive(s): fd0 is 1.44M
[  269.505284] FDC 0 is a National Semiconductor PC87306
[  269.581882] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
[  269.585247] NVRM: cpu does not support PAT, aborting..
[  271.440428] parport: PnPBIOS parport detected.
[  271.440601] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  271.709845] Real Time Clock Driver v1.12
[  272.570318] de2104x PCI Ethernet driver v0.7 (Mar 17, 2004)
[  272.605028] de0: SROM leaf offset 65, default media 10baseT auto
[  272.605087] de0:   media block #0: BNC
[  272.605122] de0:   media block #1: AUI
[  272.605158] de0:   media block #2: 10baseT-FD
[  272.605194] de0:   media block #3: 10baseT-HD
[  272.608173] eth0: 21041 at 0xca886e80, 00:00:f8:1e:2c:8f, IRQ 10
[  274.705396] ts: Compaq touchscreen protocol output
[  275.907019] pnp: Device 01:01.01 activated.
[  275.924038] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x200, speed 693kHz
[  278.109756] eth0: enabling interface
[  278.154221] eth0: set link 10baseT auto
[  278.154252] eth0:    mode 0x7ffc0040, sia 0x10c4,0xffffef01,0xffffffff,0xffff0008
[  278.154286] eth0:    set mode 0x7ffc0040, set sia 0xef01,0xffff,0x8
[  279.380682] NET: Registered protocol family 17
[  279.904123] eth0: link up, media 10baseT auto
[  280.160690] lp0: using parport0 (interrupt-driven).
[  281.356290] Adding 1037252k swap on /dev/sdb5.  Priority:-1 extents:1 across:1037252k
[  281.870838] EXT3 FS on sda1, internal journal
[  283.706650] NET: Registered protocol family 10
[  283.708674] lo: Disabled Privacy Extensions
[  283.711547] IPv6 over IPv4 tunneling driver
[  285.214358] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  285.214421] md: bitmap version 4.39
[  289.037540] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  291.379286] cdrom: open failed.
[  293.834515] NTFS driver 2.1.25 [Flags: R/O MODULE].
[  294.144292] NTFS volume version 3.0.
[  294.533151] eth0: no IPv6 routers present
[  332.761804] ppdev: user-space parallel port driver
[  335.187256] apm: BIOS version 1.1 Flags 0x03 (Driver version 1.16ac)
[  360.226761] hdb: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  360.226869] hdb: drive_cmd: error=0x04 { AbortedCommand }
[  360.226914] ide: failed opcode was: 0xec
[  384.197098] Bluetooth: Core ver 2.8
[  384.197172] NET: Registered protocol family 31
[  384.197205] Bluetooth: HCI device and connection manager initialized
[  384.197351] Bluetooth: HCI socket layer initialized
[  384.446931] Bluetooth: L2CAP ver 2.8
[  384.446997] Bluetooth: L2CAP socket layer initialized
[  384.635232] Bluetooth: RFCOMM socket layer initialized
[  384.635559] Bluetooth: RFCOMM TTY layer initialized
[  384.635605] Bluetooth: RFCOMM ver 1.7
[ 4153.722107] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!

---

### Post by wilbert on 2007-05-15
I've got a simular problem.

I've upgrade from kubuntu 6.10 to 7.04 and lost all my scsi drives. Tried several things. 

Following configuration:

amd 3000 mhz cpu, 1 gig ram
ide 80 Gb
4 times scsi (seagate) 50 Gb with 2 partitions of 25 Gb FAT32
AHA-28940-U2W PCI SCSI adapter

2.6.17-15 generic kernel

I'm running XP and Kubuntu from the IDE drive. In XP and 6.10 everything works fine.
In /dev/ there are sda, sdb etc but the devices sda1,sdb1 etc are missing.

Whenever I boot with kernel 2.6.17-11 everything works fine

lsmod shows that aic7xxx is loaded.

Part of the dmesg result:

[ 62.376456] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[ 62.376459] <Adaptec 2940 Ultra2 SCSI adapter (OEM)>
[ 62.376460] aic7890/91: Ultra2 Wide Channel A, SCSI Id=7, 32/253 SCBs
[ 62.376462]
[ 62.377778] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 62.379005] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[ 62.379139] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5040
[ 62.381467] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 21
[ 62.381473] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LAUI] -> GSI 21 (lev
el, low) -> IRQ 17
[ 62.381496] PCI: Setting latency timer of device 0000:00:06.0 to 64
[ 62.635530] scsi 0:0:1:0: Direct-Access SEAGATE SX150176LC BA12 PQ
: 0 ANSI: 2
[ 62.635548] target0:0:1: Beginning Domain Validation
[ 62.640638] target0:0:1: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 15)
[ 62.641677] (scsi0:A:1:0): parity error detected in Data-in phase. SEQADDR(0x
1a7) SCSIRATE(0x93)
[ 62.641699] (scsi0:A:1:0): parity error detected in Data-in phase. SEQADDR(0x
84) SCSIRATE(0x93)
[ 62.643692] (scsi0:A:1:0): parity error detected in Data-in phase. SEQADDR(0x
1a8) SCSIRATE(0x93)
[ 62.644328] target0:0:1: Domain Validation detected failure, dropping back
[ 62.644880] target0:0:1: FAST-40 WIDE SCSI 66.0 MB/s ST (30.3 ns, offset 15)
[ 62.645895] (scsi0:A:1:0): parity error detected in Data-in phase. SEQADDR(0x
1a8) SCSIRATE(0x94)
[ 62.645959] (scsi0:A:1:0): parity error detected in Data-in phase. SEQADDR(0x
1a8) SCSIRATE(0x94)
[ 62.647938] (scsi0:A:1:0): parity error detected in Data-in phase. SEQADDR(0x
6f) SCSIRATE(0x94)
[ 62.648598] target0:0:1: Domain Validation detected failure, dropping back
[ 62.649104] target0:0:1: FAST-20 WIDE SCSI 40.0 MB/s ST (50 ns, offset 15)
[ 62.650138] (scsi0:A:1:0): parity error detected in Data-in phase. SEQADDR(0x
1a8) SCSIRATE(0x95)
[ 62.650160] (scsi0:A:1:0): parity error detected in Data-in phase. SEQADDR(0x
1a8) SCSIRATE(0x95)


(I had to cut the message short it makes a lot of smilies and it want be posted, so if you miss anything?)

Anybody any suggestions?

---

### Post by ergosteur on 2008-07-01
Hello
I have the same problem when trying to install xubuntu 8.04 on my Poweredge 1400SC (Adaptec AIC-7890) with 5x Maxtor Atlas 10k. The CD boots, gives the errors, the drops to busybox.

---

