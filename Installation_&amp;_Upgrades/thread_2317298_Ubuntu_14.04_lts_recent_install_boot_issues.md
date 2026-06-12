---
title: "Ubuntu 14.04 lts recent install boot issues"
date: 2016-03-15
forum: Installation &amp; Upgrades
---

### Post by petatkinson on 2016-03-15
I've recently installed 14.04 lts and have been experiencing real odd boot behaviour from longer boot times. partitions not mounting to GRUB not booting at all.The following is a copy of my last boot log

```
[    0.850625] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.851145] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.851151] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.851317] mousedev: PS/2 mouse device common for all mice
[    0.851501] rtc_cmos 00:02: RTC can wake from S4
[    0.851674] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.851710] rtc_cmos 00:02: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.851726] i2c /dev entries driver
[    0.851787] device-mapper: uevent: version 1.0.3
[    0.851879] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: [email]dm-devel@redhat.com[/email]
[    0.851914] platform eisa.0: Probing EISA bus 0
[    0.851917] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.851920] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.851923] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.851925] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.851928] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.851930] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.851933] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.851935] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.851938] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.851940] platform eisa.0: EISA: Detected 0 cards
[    0.851964] cpufreq-nforce2: No nForce2 chipset.
[    0.851973] ledtrig-cpu: registered to indicate activity on CPUs
[    0.851982] PCCT header not found.
[    0.852142] TCP: cubic registered
[    0.852319] NET: Registered protocol family 10
[    0.852612] NET: Registered protocol family 17
[    0.852627] Key type dns_resolver registered
[    0.852873] Using IPI No-Shortcut mode
[    0.853032] Loading compiled-in X.509 certificates
[    0.857359] Loaded X.509 cert 'Magrathea: Glacier signing key: fa68d885db144e776ec3ba77baa5783389ea8d85'
[    0.857377] registered taskstats version 1
[    0.859661] Key type trusted registered
[    0.863573] Key type encrypted registered
[    0.863580] AppArmor: AppArmor sha1 policy hashing enabled
[    0.863585] ima: No TPM chip found, activating TPM-bypass!
[    0.863611] evm: HMAC attrs: 0x1
[    0.864036]   Magic number: 8:544:327
[    0.864131] rtc_cmos 00:02: setting system clock to 2016-03-15 11:19:46 UTC (1458040786)
[    0.864205] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.864207] EDD information not available.
[    0.864279] PM: Hibernation image not present or could not be loaded.
[    0.872436] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.051821] isapnp: No Plug & Play device found
[    1.052242] Freeing unused kernel memory: 940K (c1a66000 - c1b51000)
[    1.052302] Write protecting the kernel text: 6960k
[    1.052418] Write protecting the kernel read-only data: 3012k
[    1.052420] NX-protecting the kernel data: 5328k
[    1.065548] systemd-udevd[98]: starting version 204
[    1.095987] pata_amd 0000:00:08.0: version 0.4.1
[    1.097048] scsi host0: pata_amd
[    1.097180] scsi host1: pata_amd
[    1.097254] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.097256] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.104029] usb 3-3: new high-speed USB device number 2 using ehci-pci
[    1.132634] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.132928] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    1.140295] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    1.196056] firewire_ohci 0000:01:07.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    1.348526] usb 3-3: New USB device found, idVendor=059b, idProduct=0473
[    1.348530] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.348534] usb 3-3: Product: Iomega ScreenPlay Pro HD
[    1.348537] usb 3-3: Manufacturer: Iomega
[    1.348540] usb 3-3: SerialNumber: 110000020288
[    1.452890] ata1.00: HPA detected: current 976771055, native 976773168
[    1.452896] ata1.00: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
[    1.452900] ata1.00: 976771055 sectors, multi 16: LBA48 
[    1.452908] ata1.01: ATAPI: LITE-ON DVDRW LH-20A1H, LL06, max UDMA/66
[    1.452916] ata1: nv_mode_filter: 0x7f39f&0x7f39f->0x7f39f, BIOS=0x7f000 (0xc7c50000) ACPI=0x7f01f (15:30:0x1f)
[    1.452920] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.452929] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc7c50000) ACPI=0x1f01f (15:30:0x1f)
[    1.452931] ata1.01: limited to UDMA/33 due to 40-wire cable
[    1.468932] ata1.00: configured for UDMA/33
[    1.500230] ata1.01: configured for UDMA/33
[    1.501076] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKB-0 4E05 PQ: 0 ANSI: 5
[    1.501375] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.501399] sd 0:0:0:0: [sda] 976771055 512-byte logical blocks: (500 GB/465 GiB)
[    1.501511] sd 0:0:0:0: [sda] Write Protect is off
[    1.501515] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.501966] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.502495] scsi 0:0:1:0: CD-ROM            LITE-ON  DVDRW LH-20A1H   LL06 PQ: 0 ANSI: 5
[    1.520734] sr 0:0:1:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.520737] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.520962] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.521107] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.521189] ata2: port disabled--ignoring
[    1.522423]  sda: sda1 sda2
[    1.522783] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.648947] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:d0:91:2a:00
[    1.648951] forcedeth 0000:00:0f.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.649090] ahci 0000:00:0e.0: version 3.0
[    1.649382] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    1.649422] ahci 0000:00:0e.0: controller can do NCQ, turning on CAP_NCQ
[    1.649425] ahci 0000:00:0e.0: controller can't do PMP, turning off CAP_PMP
[    1.649481] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.649484] ahci 0000:00:0e.0: flags: 64bit ncq sntf led clo pio 
[    1.650471] scsi host2: ahci
[    1.650623] scsi host3: ahci
[    1.650768] scsi host4: ahci
[    1.650914] scsi host5: ahci
[    1.651001] ata3: SATA max UDMA/133 abar m8192@0xeb104000 port 0xeb104100 irq 20
[    1.651005] ata4: SATA max UDMA/133 abar m8192@0xeb104000 port 0xeb104180 irq 20
[    1.651007] ata5: SATA max UDMA/133 abar m8192@0xeb104000 port 0xeb104200 irq 20
[    1.651009] ata6: SATA max UDMA/133 abar m8192@0xeb104000 port 0xeb104280 irq 20
[    1.696133] firewire_core 0000:01:07.0: created device fw0: GUID 007795a100001fd0, S400
[    1.732030] tsc: Refined TSC clocksource calibration: 2533.333 MHz
[    1.760026] usb 4-7: new full-speed USB device number 2 using ohci-pci
[    1.908183] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[    1.968036] ata5: SATA link down (SStatus 0 SControl 300)
[    1.968058] ata4: SATA link down (SStatus 0 SControl 300)
[    1.968117] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.969197] ata3.00: ATA-8: ST3500418AS, CC37, max UDMA/133
[    1.969200] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.970389] ata3.00: configured for UDMA/133
[    1.970499] scsi 2:0:0:0: Direct-Access     ATA      ST3500418AS      CC37 PQ: 0 ANSI: 5
[    1.970742] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.970793] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.970818] sd 2:0:0:0: [sdb] Write Protect is off
[    1.970822] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.970860] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.972031] ata6: SATA link down (SStatus 0 SControl 300)
[    1.973037] usb 4-7: New USB device found, idVendor=046e, idProduct=5577
[    1.973042] usb 4-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.973045] usb 4-7: Product: USB Multimedia Cordless Keyboard
[    1.973049] usb 4-7: Manufacturer: BTC
[    1.985786] hidraw: raw HID events driver (C) Jiri Kosina
[    2.004110] usbcore: registered new interface driver usbhid
[    2.004113] usbhid: USB HID core driver
[    2.012431]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    2.012939] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.133322] usb-storage 3-3:1.0: USB Mass Storage device detected
[    2.133422] scsi host6: usb-storage 3-3:1.0
[    2.133547] usbcore: registered new interface driver usb-storage
[    2.138833] usbcore: registered new interface driver uas
[    2.280023] usb 4-8: new full-speed USB device number 3 using ohci-pci
[    2.502038] usb 4-8: New USB device found, idVendor=046d, idProduct=0b07
[    2.502042] usb 4-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.502046] usb 4-8: Product: Logitech BT Mini-Receiver
[    2.502049] usb 4-8: Manufacturer: Logitech
[    2.505111] hub 4-8:1.0: USB hub found
[    2.508041] hub 4-8:1.0: 3 ports detected
[    2.732087] Switched to clocksource tsc
[    2.768963] random: nonblocking pool is initialized
[    2.812020] usb 4-8.2: new full-speed USB device number 4 using ohci-pci
[    2.938034] usb 4-8.2: New USB device found, idVendor=046d, idProduct=c71e
[    2.938038] usb 4-8.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.938042] usb 4-8.2: Product: Logitech BT Mini-Receiver
[    2.938045] usb 4-8.2: Manufacturer: Logitech
[    2.938048] usb 4-8.2: SerialNumber: 001F2009B23D
[    2.960325] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-8/4-8.2/4-8.2:1.0/0003:046D:C71E.0003/input/input5
[    3.016163] hid-generic 0003:046D:C71E.0003: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-8.2/input0
[    3.032018] usb 4-8.3: new full-speed USB device number 5 using ohci-pci
[    3.157037] usb 4-8.3: New USB device found, idVendor=046d, idProduct=c71f
[    3.157042] usb 4-8.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.157045] usb 4-8.3: Product: Logitech BT Mini-Receiver
[    3.157049] usb 4-8.3: Manufacturer: Logitech
[    3.157052] usb 4-8.3: SerialNumber: 001F2009B23D
[    3.167543] scsi 6:0:0:0: Direct-Access     ST310005 28AS             CC44 PQ: 0 ANSI: 0
[    3.167836] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    3.168652] sd 6:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.171027] sd 6:0:0:0: [sdc] Write Protect is off
[    3.171032] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    3.173029] sd 6:0:0:0: [sdc] No Caching mode page found
[    3.173035] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    3.178536]  sdc: sdc1
[    3.192039] sd 6:0:0:0: [sdc] Attached SCSI disk
[    3.192326] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-8/4-8.3/4-8.3:1.0/0003:046D:C71F.0004/input/input6
[    3.238711] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[    3.248240] logitech 0003:046D:C71F.0004: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-8.3/input0
[    4.132036] floppy0: no floppy controllers found
[   11.777847] Adding 4190204k swap on /dev/sdb5.  Priority:-1 extents:1 across:4190204k FS
[   12.084847] systemd-udevd[290]: starting version 204
[   12.283400] EXT4-fs (sdb6): re-mounted. Opts: errors=remount-ro
[   12.585388] lp: driver loaded but no devices found
[   12.597159] ppdev: user-space parallel port driver
[   12.605804] parport_pc 00:04: reported by Plug and Play ACPI
[   12.605850] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.700186] lp0: using parport0 (interrupt-driven).
[   12.839080] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   12.839151] wmi: Mapper loaded
[   12.839574] i2c i2c-1: nForce2 SMBus adapter at 0x1c80
[   12.970718] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.391652] audit: type=1400 audit(1458040799.021:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=467 comm="apparmor_parser"
[   13.391661] audit: type=1400 audit(1458040799.021:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=467 comm="apparmor_parser"
[   13.392302] audit: type=1400 audit(1458040799.025:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=467 comm="apparmor_parser"
[   13.420801] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:04.0/usb4/4-7/4-7:1.0/0003:046E:5577.0001/input/input7
[   13.438796] media: Linux media interface: v0.10
[   13.463989] Linux video capture interface: v2.00
[   13.479872] [drm] Initialized drm 1.1.0 20060810
[   13.482315] topseed 0003:046E:5577.0001: input,hidraw2: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:04.0-7/input0
[   13.485526] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:04.0/usb4/4-7/4-7:1.1/0003:046E:5577.0002/input/input8
[   13.513756] audit: type=1400 audit(1458040799.145:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=505 comm="apparmor_parser"
[   13.513765] audit: type=1400 audit(1458040799.145:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=505 comm="apparmor_parser"
[   13.513771] audit: type=1400 audit(1458040799.145:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=505 comm="apparmor_parser"
[   13.514376] audit: type=1400 audit(1458040799.145:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=505 comm="apparmor_parser"
[   13.514383] audit: type=1400 audit(1458040799.145:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=505 comm="apparmor_parser"
[   13.514699] audit: type=1400 audit(1458040799.145:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=505 comm="apparmor_parser"
[   13.547810] topseed 0003:046E:5577.0002: input,hiddev0,hidraw3: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:04.0-7/input1
[   13.602007] init: cups main process (494) killed by HUP signal
[   13.602022] init: cups main process ended, respawning
[   13.743415] Bluetooth: Core ver 2.20
[   13.743434] NET: Registered protocol family 31
[   13.743437] Bluetooth: HCI device and connection manager initialized
[   13.743442] Bluetooth: HCI socket layer initialized
[   13.743445] Bluetooth: L2CAP socket layer initialized
[   13.743453] Bluetooth: SCO socket layer initialized
[   13.785536] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   13.785639] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68,autodetected], frontend(s): 2
[   13.788986] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.788989] Bluetooth: BNEP filters: protocol multicast
[   13.788993] Bluetooth: BNEP socket layer initialized
[   13.812218] Bluetooth: RFCOMM TTY layer initialized
[   13.812226] Bluetooth: RFCOMM socket layer initialized
[   13.812234] Bluetooth: RFCOMM ver 1.11
[   13.909554] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   13.909565] snd_hda_intel 0000:00:09.0: Disabling MSI
[   13.922861] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[   14.064632] init: failsafe main process (557) killed by TERM signal
[   14.181789] tda9887 2-0043: creating new instance
[   14.181793] tda9887 2-0043: tda988[5/6/7] found
[   14.182578] tuner 2-0043: Tuner 74 found with type(s) Radio TV.
[   14.201299] tuner 2-0061: Tuner -1 found with type(s) Radio TV.
[   14.210596] checking generic (e1000000 130000) vs hw (d0000000 10000000)
[   14.210600] checking generic (e1000000 130000) vs hw (e0000000 2000000)
[   14.210602] fb: switching to nouveaufb from VESA VGA
[   14.210641] Console: switching to colour dummy device 80x25
[   14.213306] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   14.214345] nouveau  [  DEVICE][0000:02:00.0] BOOT0  : 0x094280a1
[   14.214349] nouveau  [  DEVICE][0000:02:00.0] Chipset: G94 (NV94)
[   14.214351] nouveau  [  DEVICE][0000:02:00.0] Family : NV50
[   14.247246] tveeprom 2-0050: Hauppauge model 69009, rev B2D3, serial# 4031907689
[   14.247250] tveeprom 2-0050: MAC address is 00:0d:fe:52:07:69
[   14.247252] tveeprom 2-0050: tuner model is Philips FMD1216MEX (idx 133, type 78)
[   14.247255] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   14.247258] tveeprom 2-0050: audio processor is CX882 (idx 33)
[   14.247260] tveeprom 2-0050: decoder processor is CX882 (idx 25)
[   14.247262] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[   14.247264] cx88[0]: hauppauge eeprom: model=69009
[   14.340929] audit: type=1400 audit(1458040799.973:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=717 comm="apparmor_parser"
[   14.343808] nouveau  [   VBIOS][0000:02:00.0] using image from PRAMIN
[   14.343949] nouveau  [   VBIOS][0000:02:00.0] BIT signature found
[   14.343953] nouveau  [   VBIOS][0000:02:00.0] version 62.94.6e.00.00
[   14.367223] nouveau  [     PMC][0000:02:00.0] MSI interrupts enabled
[   14.367261] nouveau W[   VBIOS][0000:02:00.0] M0203T not found
[   14.367264] nouveau W[   VBIOS][0000:02:00.0] M0203E not matched!
[   14.367272] nouveau  [     PFB][0000:02:00.0] RAM type: DDR2
[   14.367275] nouveau  [     PFB][0000:02:00.0] RAM size: 1024 MiB
[   14.367277] nouveau  [     PFB][0000:02:00.0]    ZCOMP: 2048 tags
[   14.369589] nouveau  [    VOLT][0000:02:00.0] GPU voltage: 1000000uv
[   14.399335] nouveau  [  PTHERM][0000:02:00.0] FAN control: PWM
[   14.399352] nouveau  [  PTHERM][0000:02:00.0] fan management: automatic
[   14.399387] nouveau  [  PTHERM][0000:02:00.0] internal sensor: yes
[   14.419272] nouveau  [     CLK][0000:02:00.0] 0f: core 600 MHz shader 1500 MHz memory 400 MHz
[   14.419311] nouveau  [     CLK][0000:02:00.0] --: core 500 MHz shader 1250 MHz memory 199 MHz
[   14.419535] [TTM] Zone  kernel: Available graphics memory: 427056 kiB
[   14.419538] [TTM] Zone highmem: Available graphics memory: 2066964 kiB
[   14.419540] [TTM] Initializing pool allocator
[   14.419547] [TTM] Initializing DMA pool allocator
[   14.419562] nouveau  [     DRM] VRAM: 1024 MiB
[   14.419564] nouveau  [     DRM] GART: 1048576 MiB
[   14.419570] nouveau  [     DRM] TMDS table version 2.0
[   14.419572] nouveau  [     DRM] DCB version 4.0
[   14.419575] nouveau  [     DRM] DCB outp 00: 02000300 00020028
[   14.419578] nouveau  [     DRM] DCB outp 01: 01000302 00020030
[   14.419581] nouveau  [     DRM] DCB outp 02: 04011310 00020028
[   14.419583] nouveau  [     DRM] DCB outp 03: 02011312 00020030
[   14.419586] nouveau  [     DRM] DCB outp 04: 04022342 00c20020
[   14.419588] nouveau  [     DRM] DCB conn 00: 00001030
[   14.419591] nouveau  [     DRM] DCB conn 01: 00002130
[   14.419593] nouveau  [     DRM] DCB conn 02: 00010261
[   14.428601] tuner-simple 2-0061: creating new instance
[   14.428605] tuner-simple 2-0061: type set to 78 (Philips FMD1216MEX MK3 Hybrid Tuner)
[   14.430509] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   14.430511] [drm] Driver supports precise vblank timestamp query.
[   14.459226] nouveau  [     DRM] MM: using CRYPT for buffer copies
[   14.492022] Registered IR keymap rc-hauppauge
[   14.492192] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0a.0/0000:01:06.1/rc/rc0/input9
[   14.492343] rc0: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0a.0/0000:01:06.1/rc/rc0
[   14.544491] IR NEC protocol handler initialized
[   14.551371] IR Sharp protocol handler initialized
[   14.554897] IR JVC protocol handler initialized
[   14.556895] IR SANYO protocol handler initialized
[   14.557632] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   14.558756] IR RC6 protocol handler initialized
[   14.559572] lirc_dev: IR Remote Control driver registered, major 248 
[   14.560165] input: MCE IR Keyboard/Mouse (cx88xx) as /devices/virtual/input/input10
[   14.560258] IR MCE Keyboard/mouse protocol handler initialized
[   14.560821] IR Sony protocol handler initialized
[   14.567325] IR RC5(x/sz) protocol handler initialized
[   14.571733] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[   14.571736] IR LIRC bridge handler initialized
[   14.591766] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 17, latency: 32, mmio: 0xe6000000
[   14.596965] nouveau  [     DRM] allocated 1920x1080 fb: 0x70000, bo eea7b000
[   14.597910] fbcon: nouveaufb (fb0) is primary device
[   14.598046] Console: switching to colour frame buffer device 240x67
[   14.598110] nouveau 0000:02:00.0: fb0: nouveaufb frame buffer device
[   14.598113] nouveau 0000:02:00.0: registered panic notifier
[   14.598328] IR XMP protocol handler initialized
[   14.612040] [drm] Initialized nouveau 1.2.1 20120801 for 0000:02:00.0 on minor 0
[   14.981526] wm8775 2-001b: chip found @ 0x36 (cx88[0])
[   14.992262] cx88[0]/0: registered device video0 [v4l2]
[   14.992326] cx88[0]/0: registered device vbi0
[   14.992412] cx88[0]/0: registered device radio0
[   14.992717] cx88[0]/2: cx2388x 8802 Driver Manager
[   14.992829] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 17, latency: 32, mmio: 0xe8000000
[   15.090584] forcedeth 0000:00:0f.0 eth0: MSI enabled
[   15.244030] sound hdaudioC0D0: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   15.244036] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.244040] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   15.244043] sound hdaudioC0D0:    mono: mono_out=0x0
[   15.244046] sound hdaudioC0D0:    dig-out=0x1e/0x0
[   15.244049] sound hdaudioC0D0:    inputs:
[   15.244053] sound hdaudioC0D0:      Rear Mic=0x18
[   15.244057] sound hdaudioC0D0:      Front Mic=0x19
[   15.244060] sound hdaudioC0D0:      Line=0x1a
[   15.244068] sound hdaudioC0D0:      CD=0x1c
[   15.244070] sound hdaudioC0D0:    dig-in=0x1f
[   15.365309] cx88/2: cx2388x dvb driver version 1.0.0 loaded
[   15.365313] cx88/2: registering cx8802 driver, type: dvb access: shared
[   15.365317] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[   15.365319] cx88[0]/2: cx2388x based DVB/ATSC card
[   15.365321] cx8802_alloc_frontends() allocating 2 frontend(s)
[   15.454649] tuner-simple 2-0061: attaching existing instance
[   15.454654] tuner-simple 2-0061: couldn't set type to 63. Using 78 (Philips FMD1216MEX MK3 Hybrid Tuner) instead
[   15.458481] DVB: registering new adapter (cx88[0])
[   15.458488] cx88-mpeg driver manager 0000:01:06.2: DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[   15.461367] cx88-mpeg driver manager 0000:01:06.2: DVB: registering adapter 0 frontend 1 (Conexant CX22702 DVB-T)...
[   16.020038] floppy0: no floppy controllers found
[   16.020050] work still pending
[   17.119641] init: alsa-restore main process (968) terminated with status 99
[   17.322521] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:09.0/sound/card0/input11
[   17.322671] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:09.0/sound/card0/input12
[   17.322796] input: HDA NVidia Line as /devices/pci0000:00/0000:00:09.0/sound/card0/input13
[   17.322918] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:09.0/sound/card0/input14
[   17.323040] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:09.0/sound/card0/input15
[   17.323168] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:09.0/sound/card0/input16
[   17.323294] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:09.0/sound/card0/input17
[   17.323420] input: HDA NVidia HDMI/DP,pcm=3 Phantom as /devices/pci0000:00/0000:00:09.0/sound/card0/input18
[   23.040994] init: plymouth-upstart-bridge main process ended, respawning
[   23.056849] init: plymouth-upstart-bridge main process ended, respawning
[   28.472127] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472138] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472145] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472153] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472160] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472167] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472175] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472182] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472189] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472196] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472204] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472211] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472218] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472226] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472233] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472240] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472248] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472255] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472262] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472269] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472277] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472284] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472292] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472299] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472306] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472314] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472321] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472329] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472336] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472343] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472351] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472358] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472365] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472373] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472380] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472388] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472395] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472402] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472410] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472417] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472424] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472432] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472439] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472447] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472454] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472461] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472469] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472476] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472483] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472490] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.472495] cx88[0]/1: IRQ loop detected, disabling interrupts
[   28.479529] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479540] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479548] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479555] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479562] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479570] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479577] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479585] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479592] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479600] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479607] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479615] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   28.479622] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   32.076305] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[   32.111125] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[   37.099359] cx24116_load_firmware: FW version 1.26.90.0
[   37.099367] cx24116_firmware_ondemand: Firmware upload complete
[   37.246776] cx88-mpeg driver manager 0000:01:06.2: DVB: adapter 0 frontend 0 frequency 0 out of range (950000..2150000)
[   44.060712] audit_printk_skb: 150 callbacks suppressed
[   44.060716] audit: type=1400 audit(1458040829.695:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2009 comm="apparmor_parser"
[   44.060727] audit: type=1400 audit(1458040829.695:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2009 comm="apparmor_parser"
[   44.061330] audit: type=1400 audit(1458040829.695:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2009 comm="apparmor_parser"

```
I wonder is there anything really obvious from this log what might be causing this erratic behaviour.

A previous problem I experienced back in January appeared  to have been resolved so I didn't mark it solved until I was absolutely sure

[http://ubuntuforums.org/showthread.php?t=1391416&highlight=petatkinson](http://ubuntuforums.org/showthread.php?t=1391416&highlight=petatkinson)

Since Ubuntu 8.04 I've never experienced such erratic behaviour while booting

---

### Post by fantab on 2016-03-15
Post the [BootInfo Summary]("https://help.ubuntu.com/community/Boot-Info") created using [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool.

Please use [code] tags to wrap your large boot log so it becomes easy to read on the forum. 
Refer the link in my Signature for a 'how to'. You can also use [ubuntu paste]("https://paste.ubuntu.com/").

---

### Post by petatkinson on 2016-03-15
Apologies for the large boot file. 

The GRUB boot problem link should have been the following

[http://ubuntuforums.org/showthread.php?t=2312939&highlight=Ubuntu+14.04+lts+boot](http://ubuntuforums.org/showthread.php?t=2312939&highlight=Ubuntu+14.04+lts+boot)

As I said in the original post my problem is intermittent. It boots fine one day then various problems on an other. Normally I can resolve issues but I just don't know what is causing these problems.

---

### Post by petatkinson on 2016-03-16
Did anyone have a chance to examine this problem. It's a little worrying that my system has become unstable using a long term support version. Boot times are getting longer.

---

