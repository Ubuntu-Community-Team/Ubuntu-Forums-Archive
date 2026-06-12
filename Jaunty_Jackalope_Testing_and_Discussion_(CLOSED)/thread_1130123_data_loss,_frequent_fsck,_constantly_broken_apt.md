---
title: "data loss, frequent fsck, constantly broken apt"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kaliif on 2009-04-19
Hi,

Also could not resist to try Jaunty beta (64bit), but this clearly wasn't the best idea I ever had. Ever since the upgrade I've had problems with apt freezing, files corrupting on hd and settings vanishing into thin air. Almost every time I update with apt-get, it crashes, apport is trying to compose an error report an crashes too. Almost every time I reboot I'm forced to run fsck and it always finds some broken files (almost meaning one, maybe two times not). I'm not too experienced user, so help would be appreciated.

Installed Jaunty first with dist-upgrade. After a few days I started getting errors, first during updating, later just out of the blue. I ran through forums but even though I found some posts describing similar conditions as mine, no solutions followed. At first I suspected the dist-upgrade option (I have been using Ubuntu since 5.10 on several computers and in-place upgrade has worked fine only once) but after doing a clean reinstall from cd the problems persisted. Tried to install Kubuntu, no better. This morning I did a third install, clean from cd, tried ext4 instead of ext3 this time. This was the fastest: I only managed to update after install and then to install some additional packages (eclipse etc.) and again, I get errors which are not recoverable by deleting binaries in /var/cache/apt/ or dpkg --configure -a'ing or apt-get -f installing; / becomes read-only and to to something useful I'm forced to reboot and fsck. 

Even though amazingly only one file was lost this time, I'm pretty much sick of Jaunty. I was prepared for some inconveniences, but I do need to use my computer to some extent, so I'm going back to Ibex. I can't do it today, maybe not even tomorrow so if anyone has some cunning plan to debug this mess and extract some useful information, I'd be glad to help fixing these problems.

kaliif

---

### Post by ssam on 2009-04-19
can you post the output of
```
dmesg
```

are you sure the hardware is good?

can you run memcheck from the live cd, let it run for a couple of hours (or overnight), and see if it finds any errors.

check the disk. from a live cd run
```
sudo badblocks -s /dev/sda
```
change /dev/sda if that is not you main hard disk
(this does a non-destructive readonly test of the disk)

---

### Post by kaliif on 2009-04-19
dmesg looks like this:

```
[    0.555502] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.555506] pci 0000:00:1c.1: setting latency timer to 64
[    0.555514] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.555519] pci 0000:00:1c.2: setting latency timer to 64
[    0.555528] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.555532] pci 0000:00:1c.3: setting latency timer to 64
[    0.555540] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.555544] pci 0000:00:1c.4: setting latency timer to 64
[    0.555551] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.555556] pci 0000:00:1c.5: setting latency timer to 64
[    0.555563] pci 0000:00:1e.0: setting latency timer to 64
[    0.555566] bus: 00 index 0 io port: [0x00-0xffff]
[    0.555568] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.555570] bus: 01 index 0 mmio: [0x0-0x0]
[    0.555571] bus: 01 index 1 mmio: [0x0-0x0]
[    0.555573] bus: 01 index 2 mmio: [0x0-0x0]
[    0.555574] bus: 01 index 3 mmio: [0x0-0x0]
[    0.555575] bus: 02 index 0 mmio: [0x0-0x0]
[    0.555577] bus: 02 index 1 mmio: [0xf4200000-0xf42fffff]
[    0.555578] bus: 02 index 2 mmio: [0x0-0x0]
[    0.555579] bus: 02 index 3 mmio: [0x0-0x0]
[    0.555581] bus: 04 index 0 io port: [0x2000-0x2fff]
[    0.555582] bus: 04 index 1 mmio: [0xf8000000-0xfbffffff]
[    0.555584] bus: 04 index 2 mmio: [0xf0000000-0xf3ffffff]
[    0.555585] bus: 04 index 3 mmio: [0x0-0x0]
[    0.555587] bus: 06 index 0 mmio: [0x0-0x0]
[    0.555588] bus: 06 index 1 mmio: [0x0-0x0]
[    0.555589] bus: 06 index 2 mmio: [0x0-0x0]
[    0.555590] bus: 06 index 3 mmio: [0x0-0x0]
[    0.555592] bus: 07 index 0 io port: [0x3000-0x3fff]
[    0.555593] bus: 07 index 1 mmio: [0xf4300000-0xf43fffff]
[    0.555595] bus: 07 index 2 mmio: [0xf4000000-0xf40fffff]
[    0.555596] bus: 07 index 3 mmio: [0x0-0x0]
[    0.555598] bus: 08 index 0 mmio: [0x0-0x0]
[    0.555599] bus: 08 index 1 mmio: [0xf4800000-0xf48fffff]
[    0.555601] bus: 08 index 2 mmio: [0x0-0x0]
[    0.555602] bus: 08 index 3 mmio: [0x0-0x0]
[    0.555603] bus: 09 index 0 mmio: [0x0-0x0]
[    0.555604] bus: 09 index 1 mmio: [0x0-0x0]
[    0.555606] bus: 09 index 2 mmio: [0x0-0x0]
[    0.555607] bus: 09 index 3 mmio: [0x0-0x0]
[    0.555608] bus: 0a index 0 mmio: [0x0-0x0]
[    0.555610] bus: 0a index 1 mmio: [0x0-0x0]
[    0.555611] bus: 0a index 2 mmio: [0x0-0x0]
[    0.555612] bus: 0a index 3 io port: [0x00-0xffff]
[    0.555614] bus: 0a index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.555621] NET: Registered protocol family 2
[    0.588051] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.588578] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.590468] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.590983] TCP: Hash tables configured (established 262144 bind 65536)
[    0.590985] TCP reno registered
[    0.600107] NET: Registered protocol family 1
[    0.600219] checking if image is initramfs... it is
[    1.269001] Freeing initrd memory: 7748k freed
[    1.272574] Simple Boot Flag at 0x36 set to 0x1
[    1.272853] audit: initializing netlink socket (disabled)
[    1.272873] type=2000 audit(1240154482.272:1): initialized
[    1.281146] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.282271] VFS: Disk quotas dquot_6.5.1
[    1.282320] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.282799] fuse init (API version 7.10)
[    1.282866] msgmni has been set to 7712
[    1.283010] alg: No test for stdrng (krng)
[    1.283018] io scheduler noop registered
[    1.283020] io scheduler anticipatory registered
[    1.283021] io scheduler deadline registered
[    1.283056] io scheduler cfq registered (default)
[    1.283068] pci 0000:00:02.0: Boot video device
[    1.286323] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.286356] pcieport-driver 0000:00:01.0: found MSI capability
[    1.286377] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.286386] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.286398] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.286408] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.286454] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.286502] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.286534] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.286550] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.286561] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.286571] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.286641] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.286688] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.286720] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.286736] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.286749] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.286759] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.286829] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.286877] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.286909] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.286924] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.286936] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.286946] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.287016] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.287064] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.287096] pcieport-driver 0000:00:1c.3: irq 2299 for MSI/MSI-X
[    1.287111] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.287122] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.287132] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.287205] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.287252] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.287285] pcieport-driver 0000:00:1c.4: irq 2298 for MSI/MSI-X
[    1.287300] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.287311] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.287321] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.287392] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.287439] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.287471] pcieport-driver 0000:00:1c.5: irq 2297 for MSI/MSI-X
[    1.287487] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.287497] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.287508] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.287585] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.287774] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.288627] ACPI Error (psargs-0358): [\_PR_.CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND
[    1.288633] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.ADP0.ADJP] (Node ffff88013f81a160), AE_NOT_FOUND
[    1.288701] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.ADP0._PSR] (Node ffff88013f81a120), AE_NOT_FOUND
[    1.288769] ACPI Exception (ac-0135): AE_NOT_FOUND, Error reading AC Adapter state [20080926]
[    1.304302] ACPI: Battery Slot [BAT0] (battery present)
[    1.304364] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.304366] ACPI: Power Button (FF) [PWRF]
[    1.304416] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.305502] ACPI: Lid Switch [LID0]
[    1.305573] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.305579] ACPI: Power Button (CM) [PWRB]
[    1.305618] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.305626] ACPI: Sleep Button (CM) [SLPB]
[    1.306398] ACPI: SSDT BDB1ACA0, 0223 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.306837] ACPI: SSDT BDB19620, 0568 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.309653] Monitor-Mwait will be used to enter C-1 state
[    1.309655] Monitor-Mwait will be used to enter C-2 state
[    1.309666] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.309686] processor ACPI_CPU:00: registered as cooling_device0
[    1.309689] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.310420] ACPI: SSDT BDB1AA20, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
[    1.310872] ACPI: SSDT BDB1AF20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
[    1.312385] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.312401] processor ACPI_CPU:01: registered as cooling_device1
[    1.312404] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.327467] thermal LNXTHERM:01: registered as thermal_zone0
[    1.344573] ACPI: Thermal Zone [THM0] (49 C)
[    1.381211] Linux agpgart interface v0.103
[    1.381219] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.382064] brd: module loaded
[    1.382335] loop: module loaded
[    1.382389] Fixed MDIO Bus: probed
[    1.382393] PPP generic driver version 2.4.2
[    1.382443] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.382465] Driver 'sd' needs updating - please use bus_type methods
[    1.382473] Driver 'sr' needs updating - please use bus_type methods
[    1.382542] ata_piix 0000:00:1f.2: version 2.12
[    1.382553] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.382557] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.382599] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.382671] scsi0 : ata_piix
[    1.382741] scsi1 : ata_piix
[    1.382776] ata1: SATA max UDMA/133 cmd 0x18f8 ctl 0x180c bmdma 0x18e0 irq 19
[    1.382780] ata2: SATA max UDMA/133 cmd 0x18f0 ctl 0x1808 bmdma 0x18e8 irq 19
[    1.856057] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.866073] ata1.00: ATA-8: SAMSUNG HM320JI, 2SS00_01, max UDMA7
[    1.866076] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.882081] ata1.00: configured for UDMA/133
[    2.356058] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.380246] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, TM00, max UDMA/100
[    2.380254] ata2.00: applying bridge limits
[    2.412258] ata2.00: configured for UDMA/100
[    2.414742] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM320JI  2SS0 PQ: 0 ANSI: 5
[    2.414819] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.414834] sd 0:0:0:0: [sda] Write Protect is off
[    2.414836] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.414859] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.414917] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.414930] sd 0:0:0:0: [sda] Write Protect is off
[    2.414932] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.414955] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.414958]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    2.472996] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.473034] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.476848] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  TM00 PQ: 0 ANSI: 5
[    2.489470] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.489472] Uniform CD-ROM driver Revision: 3.20
[    2.489542] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.489576] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.489595] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.489599] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.489640] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.489683] scsi2 : ata_piix
[    2.489729] scsi3 : ata_piix
[    2.489767] ata3: SATA max UDMA/133 cmd 0x1c50 ctl 0x1c44 bmdma 0x1c30 irq 19
[    2.489771] ata4: SATA max UDMA/133 cmd 0x1c48 ctl 0x1c40 bmdma 0x1c38 irq 19
[    2.819139] ata3: SATA link down (SStatus 0 SControl 300)
[    3.147139] ata4: SATA link down (SStatus 0 SControl 300)
[    3.147699] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.147717] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.147734] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.147738] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.147790] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.151705] ehci_hcd 0000:00:1a.7: debug port 1
[    3.151711] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.151716] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf4b04000
[    3.165007] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.165061] usb usb1: configuration #1 chosen from 1 choice
[    3.165083] hub 1-0:1.0: USB hub found
[    3.165089] hub 1-0:1.0: 6 ports detected
[    3.165188] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.165196] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.165200] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.165238] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.169132] ehci_hcd 0000:00:1d.7: debug port 1
[    3.169138] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.169149] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4b04400
[    3.184007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.184063] usb usb2: configuration #1 chosen from 1 choice
[    3.184083] hub 2-0:1.0: USB hub found
[    3.184090] hub 2-0:1.0: 6 ports detected
[    3.184171] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.184185] uhci_hcd: USB Universal Host Controller Interface driver
[    3.184205] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.184210] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.184214] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.184254] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.184287] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    3.184353] usb usb3: configuration #1 chosen from 1 choice
[    3.184375] hub 3-0:1.0: USB hub found
[    3.184380] hub 3-0:1.0: 2 ports detected
[    3.184456] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.184462] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.184465] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.184498] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.184532] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    3.184597] usb usb4: configuration #1 chosen from 1 choice
[    3.184617] hub 4-0:1.0: USB hub found
[    3.184623] hub 4-0:1.0: 2 ports detected
[    3.184694] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.184699] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.184702] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.184737] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.184762] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    3.184828] usb usb5: configuration #1 chosen from 1 choice
[    3.184848] hub 5-0:1.0: USB hub found
[    3.184852] hub 5-0:1.0: 2 ports detected
[    3.184926] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.184932] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.184935] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.184974] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.185004] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    3.185067] usb usb6: configuration #1 chosen from 1 choice
[    3.185089] hub 6-0:1.0: USB hub found
[    3.185094] hub 6-0:1.0: 2 ports detected
[    3.185164] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.185170] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.185173] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.185209] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.185235] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    3.185300] usb usb7: configuration #1 chosen from 1 choice
[    3.185324] hub 7-0:1.0: USB hub found
[    3.185331] hub 7-0:1.0: 2 ports detected
[    3.185408] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.185413] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.185416] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.185452] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.185486] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    3.185553] usb usb8: configuration #1 chosen from 1 choice
[    3.185573] hub 8-0:1.0: USB hub found
[    3.185578] hub 8-0:1.0: 2 ports detected
[    3.185693] usbcore: registered new interface driver libusual
[    3.185719] usbcore: registered new interface driver usbserial
[    3.185729] USB Serial support registered for generic
[    3.185742] usbcore: registered new interface driver usbserial_generic
[    3.185744] usbserial: USB Serial Driver core
[    3.185780] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.189722] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.192320] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.192324] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.192326] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.192328] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.192330] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.204036] mice: PS/2 mouse device common for all mice
[    3.264089] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.264120] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.264169] device-mapper: uevent: version 1.0.3
[    3.264243] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.264301] device-mapper: multipath: version 1.0.5 loaded
[    3.264303] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.264420] cpuidle: using governor ladder
[    3.264490] cpuidle: using governor menu
[    3.264848] TCP cubic registered
[    3.264903] NET: Registered protocol family 10
[    3.265241] lo: Disabled Privacy Extensions
[    3.265490] NET: Registered protocol family 17
[    3.265511] Bluetooth: L2CAP ver 2.11
[    3.265512] Bluetooth: L2CAP socket layer initialized
[    3.265515] Bluetooth: SCO (Voice Link) ver 0.6
[    3.265516] Bluetooth: SCO socket layer initialized
[    3.265542] Bluetooth: RFCOMM socket layer initialized
[    3.265544] Marking TSC unstable due to TSC halts in idle
[    3.265549] Bluetooth: RFCOMM TTY layer initialized
[    3.265551] Bluetooth: RFCOMM ver 1.10
[    3.266279] registered taskstats version 1
[    3.266413]   Magic number: 5:827:386
[    3.266419] usb usb4: hash matches
[    3.266450] thermal cooling_device1: hash matches
[    3.266518] rtc_cmos 00:07: setting system clock to 2009-04-19 15:21:25 UTC (1240154485)
[    3.266520] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.266522] EDD information not available.
[    3.266570] Freeing unused kernel memory: 536k freed
[    3.266770] Write protecting the kernel read-only data: 6708k
[    3.299350] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.477302] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.513571] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.513603] r8169 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.513650] r8169 0000:07:00.0: setting latency timer to 64
[    3.513873] r8169 0000:07:00.0: irq 2296 for MSI/MSI-X
[    3.514429] eth0: RTL8168c/8111c at 0xffffc20000072000, 00:90:f5:8f:9c:bb, XID 3c4000c0 IRQ 2296
[    3.886650] usb 1-2: configuration #1 chosen from 1 choice
[    4.000036] Clocksource tsc unstable (delta = -68426053 ns)
[    4.087869] PM: Starting manual resume from disk
[    4.087872] PM: Resume from partition 8:5
[    4.087874] PM: Checking hibernation image.
[    4.088090] PM: Resume from disk failed.
[    4.110933] EXT4-fs: barriers enabled
[    4.125990] kjournald2 starting.  Commit interval 5 seconds
[    4.126002] EXT4-fs: delayed allocation enabled
[    4.126005] EXT4-fs: file extents enabled
[    4.126092] EXT4-fs: mballoc enabled
[    4.126096] EXT4-fs: mounted filesystem with ordered data mode.
[    4.361052] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    4.541150] usb 6-1: configuration #1 chosen from 1 choice
[    8.276707] udev: starting version 141
[    8.428077] cfg80211: Calling CRDA to update world regulatory domain
[    8.623328] cfg80211: World regulatory domain updated:
[    8.623331] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.623333] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.623335] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.623337] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.623339] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.623340] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.753918] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    8.754662] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    8.758637] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    8.815478] usbcore: registered new interface driver hiddev
[    8.828412] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input6
[    8.853175] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1/input0
[    8.853209] usbcore: registered new interface driver usbhid
[    8.853229] usbhid: v2.6:USB HID core driver
[    9.019893] iTCO_vendor_support: vendor-support=0
[    9.092066] input: PC Speaker as /devices/platform/pcspkr/input/input7
[    9.105963] sdhci: Secure Digital Host Controller Interface driver
[    9.105965] sdhci: Copyright(c) Pierre Ossman
[    9.107523] sdhci-pci 0000:08:00.0: SDHCI controller found [197b:2382] (rev 0)
[    9.107546] sdhci-pci 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.107614] sdhci-pci 0000:08:00.0: setting latency timer to 64
[    9.107661] mmc0: SDHCI controller on PCI [0000:08:00.0] using ADMA
[    9.107671] sdhci-pci 0000:08:00.2: SDHCI controller found [197b:2381] (rev 0)
[    9.107688] sdhci-pci 0000:08:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.107694] sdhci-pci 0000:08:00.2: Refusing to bind to secondary interface.
[    9.107701] sdhci-pci 0000:08:00.2: PCI INT A disabled
[    9.173260] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.173413] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[    9.173503] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.209343] acpi device:05: registered as cooling_device2
[    9.209516] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input8
[    9.210628] Linux video capture interface: v2.00
[    9.240145] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    9.358217] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.358220] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[    9.358320] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.358329] iwlagn 0000:02:00.0: setting latency timer to 64
[    9.358376] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[    9.372492] uvcvideo: Found UVC 1.00 device USB2.0 Camera (5986:0200)
[    9.381163] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.381232] iwlagn 0000:02:00.0: irq 2295 for MSI/MSI-X
[    9.381998] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input9
[    9.384403] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.385249] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.397226] usbcore: registered new interface driver uvcvideo
[    9.397262] USB Video Class driver (v0.1.0)
[    9.596973] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.597058] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.630169] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[    9.877219] lp: driver loaded but no devices found
[    9.943646] Adding 7815580k swap on /dev/sda5.  Priority:-1 extents:1 across:7815580k
[   10.234022] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000
[   10.269700] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   10.476965] EXT4 FS on sda1, internal journal on sda1:8
[   11.244231] kjournald starting.  Commit interval 5 seconds
[   11.244511] EXT3 FS on sda7, internal journal
[   11.244517] EXT3-fs: mounted filesystem with ordered data mode.
[   11.273286] EXT4-fs: barriers enabled
[   11.273650] kjournald2 starting.  Commit interval 5 seconds
[   11.273900] EXT4 FS on sda6, internal journal on sda6:8
[   11.273902] EXT4-fs: delayed allocation enabled
[   11.273903] EXT4-fs: file extents enabled
[   11.281551] EXT4-fs: mballoc enabled
[   11.281555] EXT4-fs: mounted filesystem with ordered data mode.
[   11.547835] type=1505 audit(1240154493.777:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2180
[   11.593630] type=1505 audit(1240154493.825:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2184
[   11.593738] type=1505 audit(1240154493.825:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2184
[   11.593774] type=1505 audit(1240154493.825:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2184
[   11.593810] type=1505 audit(1240154493.825:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2184
[   11.694136] type=1505 audit(1240154493.925:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2189
[   11.694277] type=1505 audit(1240154493.925:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2189
[   11.745472] type=1505 audit(1240154493.977:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2193
[   13.592529] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.592532] Bluetooth: BNEP filters: protocol multicast
[   13.632289] Bridge firewalling registered
[   15.160043] ppdev: user-space parallel port driver
[   16.707252] [drm] Initialized drm 1.1.0 20060810
[   16.716153] pci 0000:00:02.0: power state changed by ACPI to D0
[   16.716163] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.716167] pci 0000:00:02.0: setting latency timer to 64
[   16.716395] pci 0000:00:02.0: irq 2294 for MSI/MSI-X
[   16.716481] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   16.718185] [drm:i915_setparam] *ERROR* unknown parameter 4
[   18.768219] r8169: eth0: link down
[   18.768864] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.769468] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   19.259043] Registered led device: iwl-phy0:radio
[   19.259068] Registered led device: iwl-phy0:assoc
[   19.259092] Registered led device: iwl-phy0:RX
[   19.259117] Registered led device: iwl-phy0:TX
[   19.269755] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.794519] wlan0: authenticate with AP 00:14:bf:3c:47:1f
[   20.798379] wlan0: authenticated
[   20.798384] wlan0: associate with AP 00:14:bf:3c:47:1f
[   20.800482] wlan0: RX AssocResp from 00:14:bf:3c:47:1f (capab=0x401 status=0 aid=3)
[   20.800486] wlan0: associated
[   20.804876] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.854751] wlan0: disassociating by local choice (reason=3)
[   31.093028] wlan0: no IPv6 routers present
[   37.273856] wlan0: authenticate with AP 00:14:bf:3c:47:1f
[   37.275856] wlan0: authenticated
[   37.275860] wlan0: associate with AP 00:14:bf:3c:47:1f
[   37.277980] wlan0: RX ReassocResp from 00:14:bf:3c:47:1f (capab=0x401 status=0 aid=3)
[   37.277984] wlan0: associated
[   63.305361] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   85.366146] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[  115.277115] CE: hpet increasing min_delta_ns to 15000 nsec
[  829.852049] synaptic[4686]: segfault at 7f9775aac3d0 ip 00007f8efa522784 sp 00007fff029b1d90 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f8efa4d7000+bc000]
[  876.773726] synaptic[4694]: segfault at 7f7231f07234 ip 00007f723aa9c3ca sp 00007fff42f3d8c0 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f723aa62000+bc000]
[ 1058.190777] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[11292.660029] EXT4-fs error (device sda6): ext4_add_entry: bad entry in directory #17: directory entry across blocks - offset=0, inode=0, rec_len=65536, name_len=0
[12178.479066] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
```


About the hd, I'm as sure as one can be .. about the hd. But scan with smartmontools couple of days ago did not show any errors and it's new, bought it in february, run Ibex on it for about a month (worked like a charm) and then installed Jaunty which is also when the problems begun.

Kaliif

---

### Post by fuchur on 2009-04-19
Just wanted to say that I had exactly the same issue on jaunty.
Thought it was a hardware failure, but to make sure I reinstalled intrepid. So far, it seems these problems were specific to jaunty but not to the harddisk (an asus-laptop from bestbuy)

---

### Post by novafluxx on 2009-04-19
This is why I'll always do a fresh install... I hope the issues get resolved for you guys

---

### Post by Polygon on 2009-04-19
hmm

apt is segfaulting:

```
[  829.852049] synaptic[4686]: segfault at 7f9775aac3d0 ip 00007f8efa522784 sp 00007fff029b1d90 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f8efa4d7000+bc000]
[  876.773726] synaptic[4694]: segfault at 7f7231f07234 ip 00007f723aa9c3ca sp 00007fff42f3d8c0 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f723aa62000+bc000]
```


and something is going wrong with ext4:

```
[11292.660029] EXT4-fs error (device sda6): ext4_add_entry: bad entry in directory #17: directory entry across blocks - offset=0, inode=0, rec_len=65536, name_len=0
```

something major seems to be borked...

---

### Post by kaliif on 2009-04-20
The apt segaults can usually be overcome by deleting corrupt binaries in /var/cache/apt/. But when looking for how to solve this, I found that this bug has already been reported and the first report I came accross were posted in 2006. This is somewhat disturbing.

But I still can't tell if this is the thing that's breaking my files. I can't find a pattern in this, the files seem to corrupt randomly. Sometimes the files I'm working on, but also the files I've never touched on this machine. If this is indeed some Jaunty-related thing, there's going to be some pretty pissed users after 23th.

kaliif

---

### Post by ssam on 2009-04-20
this looks similar to me
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350268](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350268)

could you add a comment.

---

### Post by kaliif on 2009-04-20
Looks similar enough. Added my comment to the Launchpad.

kaliif

---

