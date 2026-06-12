---
title: "TV Tuner (HVR 950Q)- need help"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by rflores2323 on 2010-02-10
I just bought this tv tuner and want to use it for OTR digital cable.  Can anyone tell me what I need to install to get this working with tvtime??? I thought the drivers were already installed on 9.10 and it would work out the box.

Here is my output 


```






































































































































































































































































































































































































































































































































































































































































































[    1.530544] PNP: No PS/2 controller found. Probing ports directly.
[    1.531944] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.531960] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.532156] mice: PS/2 mouse device common for all mice
[    1.532368] rtc_cmos 00:06: RTC can wake from S4
[    1.532466] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.532534] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.532768] device-mapper: uevent: version 1.0.3
[    1.533016] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.533384] device-mapper: multipath: version 1.1.0 loaded
[    1.533391] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.533699] EISA: Probing bus 0 at eisa.0
[    1.533719] Cannot allocate resource for EISA slot 4
[    1.533737] EISA: Detected 0 cards.
[    1.534203] cpuidle: using governor ladder
[    1.534209] cpuidle: using governor menu
[    1.535360] TCP cubic registered
[    1.535719] NET: Registered protocol family 10
[    1.536717] lo: Disabled Privacy Extensions
[    1.537413] NET: Registered protocol family 17
[    1.537461] Bluetooth: L2CAP ver 2.13
[    1.537466] Bluetooth: L2CAP socket layer initialized
[    1.537472] Bluetooth: SCO (Voice Link) ver 0.6
[    1.537476] Bluetooth: SCO socket layer initialized
[    1.537586] Bluetooth: RFCOMM TTY layer initialized
[    1.537597] Bluetooth: RFCOMM socket layer initialized
[    1.537603] Bluetooth: RFCOMM ver 1.11
[    1.537694] Using IPI No-Shortcut mode
[    1.537860] PM: Resume from disk failed.
[    1.537886] registered taskstats version 1
[    1.538150]   Magic number: 14:518:154
[    1.538182] bdi 1:6: hash matches
[    1.538251] acpi device:21: hash matches
[    1.538351] rtc_cmos 00:06: setting system clock to 2010-02-11 01:09:13 UTC (1265850553)
[    1.538359] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.538364] EDD information not available.
[    1.780032] ata3: SATA link down (SStatus 0 SControl 300)
[    1.780072] ata1: SATA link down (SStatus 0 SControl 300)
[    1.780127] ata4: SATA link down (SStatus 0 SControl 300)
[    1.780157] ata5: SATA link down (SStatus 0 SControl 300)
[    1.780185] ata6: SATA link down (SStatus 0 SControl 300)
[    1.785530] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.918169] usb 1-1: configuration #1 chosen from 1 choice
[    1.944027] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.944878] ata2.00: ATA-8: Hitachi HTS545032B9A300, PB3OC60F, max UDMA/133
[    1.944886] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.945953] ata2.00: configured for UDMA/133
[    1.946191] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54503 PB3O PQ: 0 ANSI: 5
[    1.946492] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.946606] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.946764] sd 1:0:0:0: [sda] Write Protect is off
[    1.946771] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.946853] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.947248]  sda: sda1 sda2 < sda5 >
[    2.002144] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.002191] Freeing unused kernel memory: 540k freed
[    2.002673] Write protecting the kernel text: 4568k
[    2.002751] Write protecting the kernel read-only data: 1836k
[    2.144029] usb 1-3: new high speed USB device using ehci_hcd and address 4
[    2.321334] usb 1-3: configuration #1 chosen from 1 choice
[    2.324189] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.325649] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    2.325670] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    2.325688] forcedeth 0000:00:0a.0: setting latency timer to 64
[    2.396589] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 90:fb:a6:2c:b2:1f
[    2.396604] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    2.421795] Initializing USB Mass Storage driver...
[    2.422266] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.422521] usb-storage: device found at 2
[    2.422528] usb-storage: waiting for device to settle before scanning
[    2.422640] scsi7 : SCSI emulation for USB Mass Storage devices
[    2.422936] usb-storage: device found at 4
[    2.422942] usb-storage: waiting for device to settle before scanning
[    2.422977] usbcore: registered new interface driver usb-storage
[    2.422985] USB Mass Storage support registered.
[    2.717040] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    2.940157] usb 2-2: configuration #1 chosen from 1 choice
[    3.244029] usb 2-6: new low speed USB device using ohci_hcd and address 3
[    3.459091] usb 2-6: configuration #1 chosen from 1 choice
[    3.476884] usbcore: registered new interface driver hiddev
[    3.483429] input: Chicony 2.4G Multimedia Wireless Kit as /devices/pci0000:00/0000:00:04.0/usb2/2-6/2-6:1.0/input/input3
[    3.483582] generic-usb 0003:04F2:0963.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony 2.4G Multimedia Wireless Kit] on usb-0000:00:04.0-6/input0
[    3.499994] input: Chicony 2.4G Multimedia Wireless Kit as /devices/pci0000:00/0000:00:04.0/usb2/2-6/2-6:1.1/input/input4
[    3.500302] generic-usb 0003:04F2:0963.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Chicony 2.4G Multimedia Wireless Kit] on usb-0000:00:04.0-6/input1
[    3.500343] usbcore: registered new interface driver usbhid
[    3.500351] usbhid: v2.6:USB HID core driver
[    3.829873] PM: Starting manual resume from disk
[    3.829884] PM: Resume from partition 8:5
[    3.829889] PM: Checking hibernation image.
[    3.830084] PM: Resume from disk failed.
[    3.859026] EXT4-fs (sda1): barriers enabled
[    3.877217] kjournald2 starting: pid 370, dev sda1:8, commit interval 5 seconds
[    3.877251] EXT4-fs (sda1): delayed allocation enabled
[    3.877262] EXT4-fs: file extents enabled
[    3.940297] EXT4-fs: mballoc enabled
[    3.940350] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.643063] type=1505 audit(1265850556.602:2): operation="profile_load" pid=393 name=/usr/share/gdm/guest-session/Xsession
[    4.648027] type=1505 audit(1265850556.606:3): operation="profile_load" pid=394 name=/sbin/dhclient3
[    4.648656] type=1505 audit(1265850556.606:4): operation="profile_load" pid=394 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.648990] type=1505 audit(1265850556.606:5): operation="profile_load" pid=394 name=/usr/lib/connman/scripts/dhclient-script
[    4.689081] type=1505 audit(1265850556.650:6): operation="profile_load" pid=395 name=/usr/bin/evince
[    4.701335] type=1505 audit(1265850556.662:7): operation="profile_load" pid=395 name=/usr/bin/evince-previewer
[    4.707065] type=1505 audit(1265850556.666:8): operation="profile_load" pid=395 name=/usr/bin/evince-thumbnailer
[    4.725842] type=1505 audit(1265850556.686:9): operation="profile_load" pid=397 name=/usr/lib/cups/backend/cups-pdf
[    4.726592] type=1505 audit(1265850556.686:10): operation="profile_load" pid=397 name=/usr/sbin/cupsd
[    5.953621] Adding 4522256k swap on /dev/sda5.  Priority:-1 extents:1 across:4522256k 
[    6.489223] EXT4-fs (sda1): internal journal on sda1:8
[    7.420800] usb-storage: device scan complete
[    7.421677] usb-storage: device scan complete
[    7.422879] scsi 6:0:0:0: Direct-Access     WD       10EADS External  1.75 PQ: 0 ANSI: 4
[    7.424044] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    7.424154] scsi 7:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100F PQ: 0 ANSI: 4
[    7.424880] sd 6:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    7.425385] sd 7:0:0:0: Attached scsi generic sg2 type 0
[    7.425720] sd 6:0:0:0: [sdb] Write Protect is off
[    7.425728] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    7.425734] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.427343] sd 7:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    7.427712] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.427723]  sdb:
[    7.428839] sd 7:0:0:0: [sdc] Write Protect is off
[    7.428847] sd 7:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[    7.428852] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    7.433066] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    7.433081]  sdc: sdc1
[    7.442116]  sdb1
[    7.442978] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    7.442988] sd 7:0:0:0: [sdc] Attached SCSI disk
[    7.445214] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.445225] sd 6:0:0:0: [sdb] Attached SCSI disk
[    7.582635] udev: starting version 147
[    8.726236] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.884649] cfg80211: Calling CRDA to update world regulatory domain
[    8.955312] ACPI: I/O resource nForce2_smbus [0x4d00-0x4d3f] conflicts with ACPI region IP2_ [0x4d00-0x4d04]
[    8.955323] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.955330] nForce2_smbus 0000:00:03.2: Error probing SMB1.
[    8.955339] ACPI: I/O resource nForce2_smbus [0x4e00-0x4e3f] conflicts with ACPI region SM00 [0x4e00-0x4e3f]
[    8.955345] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.955351] nForce2_smbus 0000:00:03.2: Error probing SMB2.
[    8.966630] lp: driver loaded but no devices found
[    9.061806] lirc_dev: IR Remote Control driver registered, major 61 
[    9.121341] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[    9.121350] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[    9.134616] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.145404] acer-wmi: Acer Laptop ACPI-WMI Extras
[    9.145430] acer-wmi: No or unsupported WMI interface, unable to load
[    9.301055] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[    9.305341] Linux agpgart interface v0.103
[    9.483609] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 19
[    9.483626]   alloc irq_desc for 19 on node -1
[    9.483634]   alloc kstat_irqs on node -1
[    9.483654] ath9k 0000:05:00.0: PCI INT A -> Link[LN4A] -> GSI 19 (level, low) -> IRQ 19
[    9.483677] ath9k 0000:05:00.0: setting latency timer to 64
[    9.518565] lirc_dev: lirc_register_driver: sample_rate: 0
[    9.524567] lirc_mceusb[2]: Philips eHome Infrared Transceiver on usb2:2
[    9.524683] usbcore: registered new interface driver lirc_mceusb
[    9.910794] ath: EEPROM regdomain: 0x65
[    9.910801] ath: EEPROM indicates we should expect a direct regpair map
[    9.910809] ath: Country alpha2 being used: 00
[    9.910813] ath: Regpair used: 0x65
[    9.994957] cfg80211: World regulatory domain updated:
[    9.994966]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.994974]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.994980]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.994987]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.994993]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.994999]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.404075] nvidia: module license 'NVIDIA' taints kernel.
[   11.404087] Disabling lock debugging due to kernel taint
[   11.641767] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.643755] Registered led device: ath9k-phy0::radio
[   11.643809] Registered led device: ath9k-phy0::assoc
[   11.643861] Registered led device: ath9k-phy0::tx
[   11.643915] Registered led device: ath9k-phy0::rx
[   11.643967] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf85a0000, irq=19
[   11.667789] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 22
[   11.667809] nvidia 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 22 (level, low) -> IRQ 22
[   11.667832] nvidia 0000:03:00.0: setting latency timer to 64
[   11.668650] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   11.973574] __ratelimit: 3 callbacks suppressed
[   11.973583] type=1505 audit(1265850563.933:12): operation="profile_replace" pid=825 name=/usr/share/gdm/guest-session/Xsession
[   11.977333] type=1505 audit(1265850563.937:13): operation="profile_replace" pid=826 name=/sbin/dhclient3
[   11.977961] type=1505 audit(1265850563.937:14): operation="profile_replace" pid=826 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   11.978322] type=1505 audit(1265850563.937:15): operation="profile_replace" pid=826 name=/usr/lib/connman/scripts/dhclient-script
[   11.986519] type=1505 audit(1265850563.945:16): operation="profile_replace" pid=827 name=/usr/bin/evince
[   11.995911] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   11.997080] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   11.997093] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   11.997163] HDA Intel 0000:00:08.0: setting latency timer to 64
[   11.997739] type=1505 audit(1265850563.957:17): operation="profile_replace" pid=827 name=/usr/bin/evince-previewer
[   12.003670] type=1505 audit(1265850563.961:18): operation="profile_replace" pid=827 name=/usr/bin/evince-thumbnailer
[   12.015350] type=1505 audit(1265850563.973:19): operation="profile_replace" pid=829 name=/usr/lib/cups/backend/cups-pdf
[   12.016089] type=1505 audit(1265850563.977:20): operation="profile_replace" pid=829 name=/usr/sbin/cupsd
[   12.020878] type=1505 audit(1265850563.981:21): operation="profile_replace" pid=830 name=/usr/sbin/tcpdump
[   12.920028] hda_codec: ALC662 rev1: BIOS auto-probing.
[   13.000175] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input5
[   16.444923] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.520133] ppdev: user-space parallel port driver
[   22.747391] CPU0 attaching NULL sched-domain.
[   22.747405] CPU1 attaching NULL sched-domain.
[   22.747411] CPU2 attaching NULL sched-domain.
[   22.747416] CPU3 attaching NULL sched-domain.
[   22.757129] CPU0 attaching sched-domain:
[   22.757137]  domain 0: span 0,2 level SIBLING
[   22.757143]   groups: 0 2
[   22.757152]   domain 1: span 0-3 level MC
[   22.757158]    groups: 0,2 (__cpu_power = 2048) 1,3 (__cpu_power = 2048)
[   22.757173] CPU1 attaching sched-domain:
[   22.757177]  domain 0: span 1,3 level SIBLING
[   22.757183]   groups: 1 3
[   22.757191]   domain 1: span 0-3 level MC
[   22.757196]    groups: 1,3 (__cpu_power = 2048) 0,2 (__cpu_power = 2048)
[   22.757210] CPU2 attaching sched-domain:
[   22.757215]  domain 0: span 0,2 level SIBLING
[   22.757220]   groups: 2 0
[   22.757228]   domain 1: span 0-3 level MC
[   22.757233]    groups: 0,2 (__cpu_power = 2048) 1,3 (__cpu_power = 2048)
[   22.757246] CPU3 attaching sched-domain:
[   22.757251]  domain 0: span 1,3 level SIBLING
[   22.757257]   groups: 3 1
[   22.757265]   domain 1: span 0-3 level MC
[   22.757270]    groups: 1,3 (__cpu_power = 2048) 0,2 (__cpu_power = 2048)
[   26.532014] eth0: no IPv6 routers present
[   31.011626] CPU0 attaching NULL sched-domain.
[   31.011640] CPU1 attaching NULL sched-domain.
[   31.011646] CPU2 attaching NULL sched-domain.
[   31.011652] CPU3 attaching NULL sched-domain.
[   31.029159] CPU0 attaching sched-domain:
[   31.029168]  domain 0: span 0,2 level SIBLING
[   31.029175]   groups: 0 2
[   31.029185]   domain 1: span 0-3 level CPU
[   31.029190]    groups: 0,2 1,3
[   31.029202] CPU1 attaching sched-domain:
[   31.029207]  domain 0: span 1,3 level SIBLING
[   31.029212]   groups: 1 3
[   31.029220]   domain 1: span 0-3 level CPU
[   31.029225]    groups: 1,3 0,2
[   31.029235] CPU2 attaching sched-domain:
[   31.029240]  domain 0: span 0,2 level SIBLING
[   31.029245]   groups: 2 0
[   31.029253]   domain 1: span 0-3 level CPU
[   31.029258]    groups: 0,2 1,3
[   31.029268] CPU3 attaching sched-domain:
[   31.029273]  domain 0: span 1,3 level SIBLING
[   31.029278]   groups: 3 1
[   31.029286]   domain 1: span 0-3 level CPU
[   31.029291]    groups: 1,3 0,2
[   85.664881] usb 2-6: USB disconnect, address 3
[   90.888052] usb 2-4: new low speed USB device using ohci_hcd and address 4
[   91.102709] usb 2-4: configuration #1 chosen from 1 choice
[   91.113367] input: Chicony 2.4G Multimedia Wireless Kit as /devices/pci0000:00/0000:00:04.0/usb2/2-4/2-4:1.0/input/input6
[   91.113639] generic-usb 0003:04F2:0963.0003: input,hidraw0: USB HID v1.11 Keyboard [Chicony 2.4G Multimedia Wireless Kit] on usb-0000:00:04.0-4/input0
[   91.130133] input: Chicony 2.4G Multimedia Wireless Kit as /devices/pci0000:00/0000:00:04.0/usb2/2-4/2-4:1.1/input/input7
[   91.130576] generic-usb 0003:04F2:0963.0004: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Chicony 2.4G Multimedia Wireless Kit] on usb-0000:00:04.0-4/input1
[   95.072035] usb 1-6: new high speed USB device using ehci_hcd and address 7
[   95.226721] usb 1-6: configuration #1 chosen from 1 choice
[   95.333310] Linux video capture interface: v2.00
[   95.493647] au0828 driver loaded
[   95.856136] au0828: i2c bus registered
[   96.115227] tveeprom 3-0050: Hauppauge model 72001, rev B3F0, serial# 7440872
[   96.115238] tveeprom 3-0050: MAC address is 00-0D-FE-71-89-E8
[   96.115245] tveeprom 3-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[   96.115252] tveeprom 3-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   96.115259] tveeprom 3-0050: audio processor is AU8522 (idx 44)
[   96.115265] tveeprom 3-0050: decoder processor is AU8522 (idx 42)
[   96.115271] tveeprom 3-0050: has no radio, has IR receiver, has no IR transmitter
[   96.115277] hauppauge_eeprom: hauppauge eeprom: model=72001
[   96.138667] au8522 3-0047: creating new instance
[   96.138676] au8522_decoder creating new instance...
[   96.152679] tuner 3-0061: chip found @ 0xc2 (au0828)
[   96.194232] xc5000 3-0061: creating new instance
[   96.200086] xc5000: Successfully identified at address 0x61
[   96.200094] xc5000: Firmware has not been loaded previously
[   96.200673] au8522 3-0047: attaching existing instance
[   96.209934] xc5000 3-0061: attaching existing instance
[   96.222333] xc5000: Successfully identified at address 0x61
[   96.222341] xc5000: Firmware has not been loaded previously
[   96.222352] DVB: registering new adapter (au0828)
[   96.222362] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[   96.223039] Registered device AU0828 [Hauppauge HVR950Q]
[   96.797142] usbcore: registered new interface driver snd-usb-audio
[   96.797181] usbcore: registered new interface driver au0828
[  565.616662] usb 1-6: USB disconnect, address 7
[  565.617340] au8522 3-0047: destroying instance
[  565.617399] xc5000 3-0061: destroying instance
[  787.456062] usb 1-6: new high speed USB device using ehci_hcd and address 8
[  787.611102] usb 1-6: configuration #1 chosen from 1 choice
[  787.972190] au0828: i2c bus registered
[  788.243631] tveeprom 3-0050: Hauppauge model 72001, rev B3F0, serial# 7440872
[  788.243642] tveeprom 3-0050: MAC address is 00-0D-FE-71-89-E8
[  788.243650] tveeprom 3-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[  788.243657] tveeprom 3-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[  788.243664] tveeprom 3-0050: audio processor is AU8522 (idx 44)
[  788.243670] tveeprom 3-0050: decoder processor is AU8522 (idx 42)
[  788.243676] tveeprom 3-0050: has no radio, has IR receiver, has no IR transmitter
[  788.243682] hauppauge_eeprom: hauppauge eeprom: model=72001
[  788.247035] au8522 3-0047: creating new instance
[  788.247042] au8522_decoder creating new instance...
[  788.254572] tuner 3-0061: chip found @ 0xc2 (au0828)
[  788.254826] xc5000 3-0061: creating new instance
[  788.261235] xc5000: Successfully identified at address 0x61
[  788.261243] xc5000: Firmware has not been loaded previously
[  788.261777] au8522 3-0047: attaching existing instance
[  788.274268] xc5000 3-0061: attaching existing instance
[  788.278978] xc5000: Successfully identified at address 0x61
[  788.278985] xc5000: Firmware has not been loaded previously
[  788.278993] DVB: registering new adapter (au0828)
[  788.279003] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[  788.279681] Registered device AU0828 [Hauppauge HVR950Q]
[ 1080.060315] type=1505 audit(1265851632.624:22): operation="profile_load" pid=4860 name=/usr/sbin/mysqld
[ 1080.365498] type=1503 audit(1265851632.928:23): operation="open" pid=4887 parent=4886 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 1080.411078] type=1503 audit(1265851632.972:24): operation="open" pid=4901 parent=4900 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 1080.717739] type=1503 audit(1265851633.280:25): operation="open" pid=5015 parent=4907 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 1081.473880] type=1503 audit(1265851634.036:26): operation="open" pid=5032 parent=5031 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 1081.579085] type=1503 audit(1265851634.140:27): operation="open" pid=5044 parent=5043 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 1123.519708] type=1505 audit(1265851676.080:28): operation="profile_load" pid=5779 name=/usr/sbin/ntpd
[ 1621.605084] usb 1-6: USB disconnect, address 8
[ 1621.605774] au8522 3-0047: destroying instance
[ 1621.605830] xc5000 3-0061: destroying instance
[ 1847.490801] nautilus[1809]: segfault at 7780ad0 ip 07780ad0 sp bfde83ac error 4 in libtheora.so.0.3.4[7994000+54000]
[ 1849.113046] usb 1-3: reset high speed USB device using ehci_hcd and address 4
[ 2034.328037] usb 1-6: new high speed USB device using ehci_hcd and address 9
[ 2034.483570] usb 1-6: configuration #1 chosen from 1 choice
[ 2034.844129] au0828: i2c bus registered
[ 2035.113225] tveeprom 3-0050: Hauppauge model 72001, rev B3F0, serial# 7440872
[ 2035.113239] tveeprom 3-0050: MAC address is 00-0D-FE-71-89-E8
[ 2035.113248] tveeprom 3-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[ 2035.113259] tveeprom 3-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 2035.113269] tveeprom 3-0050: audio processor is AU8522 (idx 44)
[ 2035.113277] tveeprom 3-0050: decoder processor is AU8522 (idx 42)
[ 2035.113286] tveeprom 3-0050: has no radio, has IR receiver, has no IR transmitter
[ 2035.113295] hauppauge_eeprom: hauppauge eeprom: model=72001
[ 2035.300343] au8522 3-0047: creating new instance
[ 2035.300350] au8522_decoder creating new instance...
[ 2035.307239] tuner 3-0061: chip found @ 0xc2 (au0828)
[ 2035.307478] xc5000 3-0061: creating new instance
[ 2035.313582] xc5000: Successfully identified at address 0x61
[ 2035.313590] xc5000: Firmware has not been loaded previously
[ 2035.314125] au8522 3-0047: attaching existing instance
[ 2035.324308] xc5000 3-0061: attaching existing instance
[ 2035.330213] xc5000: Successfully identified at address 0x61
[ 2035.330223] xc5000: Firmware has not been loaded previously
[ 2035.330235] DVB: registering new adapter (au0828)
[ 2035.330246] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[ 2035.331163] Registered device AU0828 [Hauppauge HVR950Q]
[ 3649.100033] usb 1-3: reset high speed USB device using ehci_hcd and address 4
[ 4068.593382] usb 1-6: USB disconnect, address 9
[ 4068.594086] au8522 3-0047: destroying instance
[ 4068.594142] xc5000 3-0061: destroying instance
[ 4072.568048] usb 1-6: new high speed USB device using ehci_hcd and address 10
[ 4072.723424] usb 1-6: configuration #1 chosen from 1 choice
[ 4073.084130] au0828: i2c bus registered
[ 4073.358980] tveeprom 3-0050: Hauppauge model 72001, rev B3F0, serial# 7440872
[ 4073.358990] tveeprom 3-0050: MAC address is 00-0D-FE-71-89-E8
[ 4073.358998] tveeprom 3-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[ 4073.359005] tveeprom 3-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 4073.359012] tveeprom 3-0050: audio processor is AU8522 (idx 44)
[ 4073.359018] tveeprom 3-0050: decoder processor is AU8522 (idx 42)
[ 4073.359024] tveeprom 3-0050: has no radio, has IR receiver, has no IR transmitter
[ 4073.359030] hauppauge_eeprom: hauppauge eeprom: model=72001
[ 4073.363008] au8522 3-0047: creating new instance
[ 4073.363013] au8522_decoder creating new instance...
[ 4073.370109] tuner 3-0061: chip found @ 0xc2 (au0828)
[ 4073.370346] xc5000 3-0061: creating new instance
[ 4073.375095] xc5000: Successfully identified at address 0x61
[ 4073.375102] xc5000: Firmware has not been loaded previously
[ 4073.375641] au8522 3-0047: attaching existing instance
[ 4073.383070] xc5000 3-0061: attaching existing instance
[ 4073.387842] xc5000: Successfully identified at address 0x61
[ 4073.387848] xc5000: Firmware has not been loaded previously
[ 4073.387855] DVB: registering new adapter (au0828)
[ 4073.387864] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[ 4073.388857] Registered device AU0828 [Hauppauge HVR950Q]
[ 4816.567587] usb 1-6: USB disconnect, address 10
[ 4816.568547] au8522 3-0047: destroying instance
[ 4816.568638] xc5000 3-0061: destroying instance
[ 5446.993340] usb 1-6: new high speed USB device using ehci_hcd and address 11
[ 5447.157229] usb 1-6: configuration #1 chosen from 1 choice
[ 5447.516829] au0828: i2c bus registered
[ 5447.786306] tveeprom 3-0050: Hauppauge model 72001, rev B3F0, serial# 7440872
[ 5447.786317] tveeprom 3-0050: MAC address is 00-0D-FE-71-89-E8
[ 5447.786324] tveeprom 3-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[ 5447.786332] tveeprom 3-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 5447.786338] tveeprom 3-0050: audio processor is AU8522 (idx 44)
[ 5447.786344] tveeprom 3-0050: decoder processor is AU8522 (idx 42)
[ 5447.786351] tveeprom 3-0050: has no radio, has IR receiver, has no IR transmitter
[ 5447.786357] hauppauge_eeprom: hauppauge eeprom: model=72001
[ 5448.031314] au8522 3-0047: creating new instance
[ 5448.031321] au8522_decoder creating new instance...
[ 5448.056282] tuner 3-0061: chip found @ 0xc2 (au0828)
[ 5448.056522] xc5000 3-0061: creating new instance
[ 5448.062296] xc5000: Successfully identified at address 0x61
[ 5448.062304] xc5000: Firmware has not been loaded previously
[ 5448.062893] au8522 3-0047: attaching existing instance
[ 5448.072744] xc5000 3-0061: attaching existing instance
[ 5448.077673] xc5000: Successfully identified at address 0x61
[ 5448.077682] xc5000: Firmware has not been loaded previously
[ 5448.077691] DVB: registering new adapter (au0828)
[ 5448.077700] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[ 5448.078463] Registered device AU0828 [Hauppauge HVR950Q]
[ 5469.302972] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[ 5469.302986] usb 1-6: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[ 5469.536436] xc5000: firmware read 12401 bytes.
[ 5469.536443] xc5000: firmware uploading...
[ 5476.636023] xc5000: firmware upload complete...
[ 5480.130747] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[ 5480.130765] usb 1-6: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[ 5480.153095] xc5000: firmware read 12401 bytes.
[ 5480.153104] xc5000: firmware uploading...
[ 5487.272025] xc5000: firmware upload complete...
[ 5887.091192] me-tv[13187]: segfault at ffffff88 ip 080749c7 sp bff89d10 error 4 in me-tv[8048000+9d000]
[ 7249.088039] usb 1-3: reset high speed USB device using ehci_hcd and address 4
[11733.480779] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[11733.480793] usb 1-6: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[11733.850049] xc5000: firmware read 12401 bytes.
[11733.850057] xc5000: firmware uploading...
[11742.544045] xc5000: firmware upload complete...
[12546.307287] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[12546.307303] usb 1-6: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[12546.421868] xc5000: firmware read 12401 bytes.
[12546.421875] xc5000: firmware uploading...
[12555.080065] xc5000: firmware upload complete...
[12636.896692] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[12636.896707] usb 1-6: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[12636.907415] xc5000: firmware read 12401 bytes.
[12636.907423] xc5000: firmware uploading...
[12645.700055] xc5000: firmware upload complete...
xbmc@xbmc-desktop:~$ 


```




























































































































































































































































































































































































































































































































































68] device-mapper: uevent: version 1.0.3

---

