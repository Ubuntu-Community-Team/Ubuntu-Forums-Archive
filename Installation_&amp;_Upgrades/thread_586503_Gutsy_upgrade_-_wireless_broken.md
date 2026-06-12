---
title: "Gutsy upgrade - wireless broken"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by cgfoz on 2007-10-22
Just upgraded to Gutsy from Feisty and now I'm having wireless problems.

My laptop is a HP dv2000. It looks like the wireless device is not being recognised at all.

Any suggestions? Device info below

Thanks
Chris

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

dmesg
(I think the key message is ADDRCONF(NETDEV_UP): eth0: link is not read)
```
[    2.852000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.856000] Time: acpi_pm clocksource has been installed.
[    2.856000] ACPI: Thermal Zone [TZS0] (52 C)
[    2.864000] ACPI: Thermal Zone [TZS1] (52 C)
[    3.276000] usbcore: registered new interface driver usbfs
[    3.276000] usbcore: registered new interface driver hub
[    3.276000] usbcore: registered new device driver usb
[    3.276000] USB Universal Host Controller Interface driver v3.0
[    3.276000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    3.276000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.276000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.276000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.276000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[    3.276000] usb usb1: configuration #1 chosen from 1 choice
[    3.276000] hub 1-0:1.0: USB hub found
[    3.276000] hub 1-0:1.0: 2 ports detected
[    3.380000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.380000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.380000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.380000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.380000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    3.380000] usb usb2: configuration #1 chosen from 1 choice
[    3.380000] hub 2-0:1.0: USB hub found
[    3.380000] hub 2-0:1.0: 2 ports detected
[    3.380000] SCSI subsystem initialized
[    3.384000] libata version 2.21 loaded.
[    3.432000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[    3.432000] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.484000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 21
[    3.484000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.484000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.484000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.484000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001840
[    3.484000] usb usb3: configuration #1 chosen from 1 choice
[    3.484000] hub 3-0:1.0: USB hub found
[    3.484000] hub 3-0:1.0: 2 ports detected
[    3.588000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.588000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.588000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.588000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.588000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    3.588000] usb usb4: configuration #1 chosen from 1 choice
[    3.588000] hub 4-0:1.0: USB hub found
[    3.588000] hub 4-0:1.0: 2 ports detected
[    3.692000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    3.692000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.692000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.692000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.692000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.692000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.692000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd6404000
[    3.724000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.724000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.724000] usb usb5: configuration #1 chosen from 1 choice
[    3.724000] hub 5-0:1.0: USB hub found
[    3.724000] hub 5-0:1.0: 8 ports detected
[    3.828000] ata_piix 0000:00:1f.1: version 2.11
[    3.828000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    3.828000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.828000] scsi0 : ata_piix
[    3.828000] scsi1 : ata_piix
[    3.828000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011880 irq 14
[    3.828000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011888 irq 15
[    4.060000] Clocksource tsc unstable (delta = -239774609 ns)
[    4.172000] ata1.00: ATAPI: SONY     DVD RW DW-G520A, GPSD, max MWDMA2
[    4.340000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[    4.368000] ata1.00: configured for MWDMA2
[    4.368000] ata2: port disabled. ignoring.
[    4.368000] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DW-G520A  GPSD PQ: 0 ANSI: 5
[    4.368000] ahci 0000:00:1f.2: version 2.2
[    4.368000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    4.388000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.388000] Uniform CD-ROM driver Revision: 3.20
[    4.388000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.392000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.480000] usb 5-5: configuration #1 chosen from 1 choice
[    4.720000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    4.896000] usb 2-1: configuration #1 chosen from 1 choice
[    4.908000] usbcore: registered new interface driver hiddev
[    4.920000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    4.920000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
[    4.920000] usbcore: registered new interface driver usbhid
[    4.920000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.372000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[    5.372000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    5.372000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.372000] scsi2 : ahci
[    5.372000] scsi3 : ahci
[    5.372000] scsi4 : ahci
[    5.372000] scsi5 : ahci
[    5.372000] ata3: SATA max UDMA/133 cmd 0xf8854500 ctl 0x00000000 bmdma 0x00000000 irq 19
[    5.372000] ata4: SATA max UDMA/133 cmd 0xf8854580 ctl 0x00000000 bmdma 0x00000000 irq 19
[    5.372000] ata5: SATA max UDMA/133 cmd 0xf8854600 ctl 0x00000000 bmdma 0x00000000 irq 19
[    5.372000] ata6: SATA max UDMA/133 cmd 0xf8854680 ctl 0x00000000 bmdma 0x00000000 irq 19
[    5.856000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.856000] ata3.00: ATA-7: WDC WD1200BEVS-60LAT0, 01.06M01, max UDMA/100
[    5.856000] ata3.00: 234441648 sectors, multi 16: LBA48 
[    5.856000] ata3.00: configured for UDMA/100
[    6.168000] ata4: SATA link down (SStatus 0 SControl 0)
[    6.480000] ata5: SATA link down (SStatus 0 SControl 300)
[    6.792000] ata6: SATA link down (SStatus 0 SControl 0)
[    6.792000] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-6 01.0 PQ: 0 ANSI: 5
[    6.792000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    6.792000] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 20 (level, low) -> IRQ 22
[    6.820000] e100: eth0: e100_probe: addr 0xd6100000, irq 22, MAC addr 00:16:D3:12:BD:81
[    6.820000] ACPI: PCI Interrupt 0000:08:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[    6.872000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d6101000-d61017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.884000] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.884000] sd 2:0:0:0: [sda] Write Protect is off
[    6.884000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.884000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.884000] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.884000] sd 2:0:0:0: [sda] Write Protect is off
[    6.884000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.884000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.884000]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    6.968000] sd 2:0:0:0: [sda] Attached SCSI disk
[    7.272000] Attempting manual resume
[    7.272000] swsusp: Resume From Partition 8:5
[    7.272000] PM: Checking swsusp image.
[    7.272000] PM: Resume from disk failed.
[    7.276000] swsusp: Basic memory bitmaps created
[    7.284000] swsusp: Basic memory bitmaps freed
[    7.304000] kjournald starting.  Commit interval 5 seconds
[    7.304000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.148000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[06e40a000fbc5043]
[   19.172000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.220000] Netfilter messages via NETLINK v0.30.
[   19.236000] nf_conntrack version 0.5.0 (8180 buckets, 65440 max)
[   20.856000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.016000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.020000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.572000] iTCO_vendor_support: vendor-support=0
[   21.588000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   21.588000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   21.588000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.616000] intel_rng: FWH not detected
[   21.996000] sdhci: Secure Digital Host Controller Interface driver
[   21.996000] sdhci: Copyright(c) Pierre Ossman
[   21.996000] sdhci: SDHCI controller found at 0000:08:09.1 [1180:0822] (rev 19)
[   21.996000] ACPI: PCI Interrupt 0000:08:09.1[B] -> GSI 18 (level, low) -> IRQ 18
[   21.996000] mmc0: SDHCI at 0xd6101800 irq 18 DMA
[   22.156000] nvidia: module license 'NVIDIA' taints kernel.
[   22.652000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.652000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   22.652000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   22.844000] Real Time Clock Driver v1.12ac
[   23.112000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   23.140000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   24.824000] lp: driver loaded but no devices found
[   24.948000] Adding 2096440k swap on /dev/sda5.  Priority:-1 extents:1 across:2096440k
[   25.452000] EXT3 FS on sda2, internal journal
[   34.968000] APIC error on CPU0: 00(40)
[   44.160000] ACPI: AC Adapter [ADP1] (on-line)
[   44.276000] ACPI: Battery Slot [BAT0] (battery present)
[   44.292000] No dock devices found.
[   44.368000] input: Power Button (FF) as /class/input/input4
[   44.372000] ACPI: Power Button (FF) [PWRF]
[   44.412000] input: Lid Switch as /class/input/input5
[   44.416000] ACPI: Lid Switch [LID0]
[   44.456000] input: Sleep Button (CM) as /class/input/input6
[   44.460000] ACPI: Sleep Button (CM) [SLPB]
[   44.500000] input: Power Button (CM) as /class/input/input7
[   44.504000] ACPI: Power Button (CM) [PWRB]
[   44.632000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   44.632000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   47.164000] ppdev: user-space parallel port driver
[   75.040000] apm: BIOS not found.
[   78.104000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   78.256000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   78.272000] NFSD: starting 90-second grace period
[   91.316000] Capability LSM initialized
[  126.132000] NET: Registered protocol family 10
[  126.132000] lo: Disabled Privacy Extensions
[  126.132000] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by cgfoz on 2007-10-22
Okay, looks like the upgrade installs two kernel versions:

2.6.22-14-generic and  2.6.22-14-i386

and was putting the i386 one at the top of the loading list in grub, which was causing the problems. 

When I chose the generic everything was fine

---

### Post by amphib1 on 2007-10-25
Hope this helps, worked for me... Assuming you have a cat5 lan connection. Otherwise you'll have to copy the files.

I went to System- admin- Synaptic package manager.  The browsed down to the most recent linux-restricted-modules and made sure it was checked for install.

Then went to System- Admin-  Restricted driver manager and made sure I enabled the Atheros HAL.

Restarted the computer

Then went to System- Admin- Network Tools and clicked down to Ath0, then it picked it up.

Dont know exactly what I was doing, but it worked.

-J

---

