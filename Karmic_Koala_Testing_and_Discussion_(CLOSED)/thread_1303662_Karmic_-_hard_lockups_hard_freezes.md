---
title: "Karmic - hard lockups hard freezes"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frogotronic on 2009-10-28
this is a showstopper.

Here's the last two minutes of the kernel log before it seize
```

Oct 28 13:32:22 methy1 kernel: [    2.250866] usbcore: registered new interface driver usbhid
Oct 28 13:32:22 methy1 kernel: [    2.250869] usbhid: v2.6:USB HID core driver
Oct 28 13:32:22 methy1 kernel: [    2.644039] PM: Starting manual resume from disk
Oct 28 13:32:22 methy1 kernel: [    2.644043] PM: Resume from partition 8:5
Oct 28 13:32:22 methy1 kernel: [    2.644045] PM: Checking hibernation image.
Oct 28 13:32:22 methy1 kernel: [    2.644177] PM: Resume from disk failed.
Oct 28 13:32:22 methy1 kernel: [    2.672523] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Oct 28 13:32:22 methy1 kernel: [    2.672527] EXT4-fs (sda1): write access will be enabled during recovery
Oct 28 13:32:22 methy1 kernel: [    2.679971] EXT4-fs (sda1): barriers enabled
Oct 28 13:32:22 methy1 kernel: [    2.921571] kjournald2 starting: pid 483, dev sda1:8, commit interval 5 seconds
Oct 28 13:32:22 methy1 kernel: [    2.921584] EXT4-fs (sda1): delayed allocation enabled
Oct 28 13:32:22 methy1 kernel: [    2.921588] EXT4-fs: file extents enabled
Oct 28 13:32:22 methy1 kernel: [    2.928340] EXT4-fs: mballoc enabled
Oct 28 13:32:22 methy1 kernel: [    2.928354] EXT4-fs (sda1): recovery complete
Oct 28 13:32:22 methy1 kernel: [    2.928724] EXT4-fs (sda1): mounted filesystem with ordered data mode
Oct 28 13:32:22 methy1 kernel: [    3.017176] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f9929ad5a0e]
Oct 28 13:32:22 methy1 kernel: [    3.683403] type=1505 audit(1256751138.119:2): operation="profile_load" pid=506 name=/usr/share/gdm/guest-session/Xsession
Oct 28 13:32:22 methy1 kernel: [    3.685842] type=1505 audit(1256751138.121:3): operation="profile_load" pid=507 name=/sbin/dhclient3
Oct 28 13:32:22 methy1 kernel: [    3.686519] type=1505 audit(1256751138.121:4): operation="profile_load" pid=507 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Oct 28 13:32:22 methy1 kernel: [    3.686882] type=1505 audit(1256751138.121:5): operation="profile_load" pid=507 name=/usr/lib/connman/scripts/dhclient-script
Oct 28 13:32:22 methy1 kernel: [    3.725848] type=1505 audit(1256751138.161:6): operation="profile_load" pid=508 name=/usr/bin/evince
Oct 28 13:32:22 methy1 kernel: [    3.736200] type=1505 audit(1256751138.173:7): operation="profile_load" pid=508 name=/usr/bin/evince-previewer
Oct 28 13:32:22 methy1 kernel: [    3.742472] type=1505 audit(1256751138.177:8): operation="profile_load" pid=508 name=/usr/bin/evince-thumbnailer
Oct 28 13:32:22 methy1 kernel: [    3.760286] type=1505 audit(1256751138.197:9): operation="profile_load" pid=510 name=/usr/lib/cups/backend/cups-pdf
Oct 28 13:32:22 methy1 kernel: [    4.977193] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k 
Oct 28 13:32:22 methy1 kernel: [    5.045757] EXT4-fs (sda1): internal journal on sda1:8
Oct 28 13:32:22 methy1 kernel: [    5.581685] udev: starting version 147
Oct 28 13:32:22 methy1 kernel: [    8.174496] __ratelimit: 6 callbacks suppressed
Oct 28 13:32:22 methy1 kernel: [    8.174499] type=1505 audit(1256751142.610:12): operation="profile_replace" pid=868 name=/usr/share/gdm/guest-session/Xsession
Oct 28 13:32:22 methy1 kernel: [    8.176064] type=1505 audit(1256751142.610:13): operation="profile_replace" pid=869 name=/sbin/dhclient3
Oct 28 13:32:22 methy1 kernel: [    8.176748] type=1505 audit(1256751142.610:14): operation="profile_replace" pid=869 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Oct 28 13:32:22 methy1 kernel: [    8.177133] type=1505 audit(1256751142.614:15): operation="profile_replace" pid=869 name=/usr/lib/connman/scripts/dhclient-script
Oct 28 13:32:22 methy1 kernel: [    8.180511] type=1505 audit(1256751142.614:16): operation="profile_replace" pid=870 name=/usr/bin/evince
Oct 28 13:32:22 methy1 kernel: [    8.190964] type=1505 audit(1256751142.626:17): operation="profile_replace" pid=870 name=/usr/bin/evince-previewer
Oct 28 13:32:22 methy1 kernel: [    8.197232] type=1505 audit(1256751142.634:18): operation="profile_replace" pid=870 name=/usr/bin/evince-thumbnailer
Oct 28 13:32:22 methy1 kernel: [    8.205789] type=1505 audit(1256751142.642:19): operation="profile_replace" pid=872 name=/usr/lib/cups/backend/cups-pdf
Oct 28 13:32:22 methy1 kernel: [    8.206566] type=1505 audit(1256751142.642:20): operation="profile_replace" pid=872 name=/usr/sbin/cupsd
Oct 28 13:32:22 methy1 kernel: [    8.208837] type=1505 audit(1256751142.642:21): operation="profile_replace" pid=873 name=/usr/sbin/tcpdump
Oct 28 13:32:23 methy1 kernel: [    8.840272] e1000e 0000:00:19.0: irq 29 for MSI/MSI-X
Oct 28 13:32:23 methy1 kernel: [    8.896110] e1000e 0000:00:19.0: irq 29 for MSI/MSI-X
Oct 28 13:32:23 methy1 kernel: [    8.896396] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 28 13:32:24 methy1 kernel: [   10.232933] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Oct 28 13:32:24 methy1 kernel: [   10.232936] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Oct 28 13:32:24 methy1 kernel: [   10.233150] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 28 13:32:25 methy1 kernel: [   10.714277] lib80211: common routines for IEEE802.11 drivers
Oct 28 13:32:25 methy1 kernel: [   10.714280] lib80211_crypt: registered algorithm 'NULL'
Oct 28 13:32:25 methy1 kernel: [   10.959079] wl: module license 'MIXED/Proprietary' taints kernel.
Oct 28 13:32:25 methy1 kernel: [   10.959083] Disabling lock debugging due to kernel taint
Oct 28 13:32:25 methy1 kernel: [   10.960871] wl 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 28 13:32:25 methy1 kernel: [   10.960879] wl 0000:10:00.0: setting latency timer to 64
Oct 28 13:32:25 methy1 kernel: [   11.269140] lib80211_crypt: registered algorithm 'TKIP'
Oct 28 13:32:25 methy1 kernel: [   11.269917] eth1: Broadcom BCM4312 802.11 Wireless Controller 5.10.91.9
Oct 28 13:32:25 methy1 kernel: [   11.275346] udev: renamed network interface eth1 to eth2
Oct 28 13:32:26 methy1 kernel: [   11.651866] irda_init()
Oct 28 13:32:26 methy1 kernel: [   11.651875] NET: Registered protocol family 23
Oct 28 13:32:26 methy1 kernel: [   12.202360] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 28 13:32:27 methy1 kernel: [   12.727254] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Oct 28 13:32:27 methy1 kernel: [   12.727454] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Oct 28 13:32:27 methy1 kernel: [   12.727457] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Oct 28 13:32:27 methy1 kernel: [   12.727459] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Oct 28 13:32:27 methy1 kernel: [   12.895430] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Oct 28 13:32:27 methy1 kernel: [   12.895442] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 28 13:32:27 methy1 kernel: [   12.895474] HDA Intel 0000:00:1b.0: setting latency timer to 64
Oct 28 13:32:28 methy1 kernel: [   13.611991] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Oct 28 13:32:28 methy1 kernel: [   13.703150] ip6_tables: (C) 2000-2006 Netfilter Core Team
Oct 28 13:32:29 methy1 kernel: [   15.123388] ricoh-mmc: Ricoh MMC Controller disabling driver
Oct 28 13:32:29 methy1 kernel: [   15.123391] ricoh-mmc: Copyright(c) Philip Langdale
Oct 28 13:32:29 methy1 kernel: [   15.123426] ricoh-mmc: Ricoh MMC controller found at 0000:02:06.4 [1180:0843] (rev 10)
Oct 28 13:32:29 methy1 kernel: [   15.123449] ricoh-mmc: Controller is now disabled.
Oct 28 13:32:29 methy1 kernel: [   15.191780] found SMC SuperIO Chip (devid=0x7a rev=03 base=0x004e): LPC47N227
Oct 28 13:32:29 methy1 kernel: [   15.191805] smsc_superio_flat(): fir: 0x100, sir: 0x3e8, dma: 03, irq: 6, mode: 0x0e
Oct 28 13:32:29 methy1 kernel: [   15.191809] smsc_ircc_present: can't get sir_base of 0x3e8
Oct 28 13:32:29 methy1 kernel: [   15.244072] lp: driver loaded but no devices found
Oct 28 13:32:29 methy1 kernel: [   15.273853] parport_pc 00:04: reported by Plug and Play ACPI
Oct 28 13:32:29 methy1 kernel: [   15.273936] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Oct 28 13:32:29 methy1 kernel: [   15.368248] lp0: using parport0 (interrupt-driven).
Oct 28 13:32:30 methy1 kernel: [   15.748373] ppdev: user-space parallel port driver
Oct 28 13:32:30 methy1 kernel: [   15.751424] sdhci: Secure Digital Host Controller Interface driver
Oct 28 13:32:30 methy1 kernel: [   15.751427] sdhci: Copyright(c) Pierre Ossman
Oct 28 13:32:30 methy1 kernel: [   15.775194] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:30c1]
Oct 28 13:32:30 methy1 kernel: [   15.900727] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0c38, PCI irq 18
Oct 28 13:32:30 methy1 kernel: [   15.900731] yenta_cardbus 0000:02:06.0: Socket status: 30000006
Oct 28 13:32:30 methy1 kernel: [   15.900736] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
Oct 28 13:32:30 methy1 kernel: [   15.900739] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x6000-0x6fff: clean.
Oct 28 13:32:30 methy1 kernel: [   15.900974] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xd8100000 - 0xd83fffff
Oct 28 13:32:30 methy1 kernel: [   15.900977] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
Oct 28 13:32:30 methy1 kernel: [   15.901967] yenta_cardbus 0000:02:06.1: CardBus bridge found [103c:30c1]
Oct 28 13:32:30 methy1 kernel: [   16.028724] yenta_cardbus 0000:02:06.1: ISA IRQ mask 0x0000, PCI irq 19
Oct 28 13:32:30 methy1 kernel: [   16.028728] yenta_cardbus 0000:02:06.1: Socket status: 30000810
Oct 28 13:32:30 methy1 kernel: [   16.028732] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #04 to #07
Oct 28 13:32:30 methy1 kernel: [   16.028738] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
Oct 28 13:32:30 methy1 kernel: [   16.028740] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x6000-0x6fff: clean.
Oct 28 13:32:30 methy1 kernel: [   16.028969] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge Memory window: 0xd8100000 - 0xd83fffff
Oct 28 13:32:30 methy1 kernel: [   16.028972] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
Oct 28 13:32:30 methy1 kernel: [   16.123825] tpm_inf_pnp 00:05: Found C231 with ID IFX0102
Oct 28 13:32:30 methy1 kernel: [   16.123883] tpm_inf_pnp 00:05: TPM found: config base 0x560, data base 0x570, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
Oct 28 13:32:30 methy1 kernel: [   16.373233] lis3lv02d: laptop model unknown, using default axes configuration
Oct 28 13:32:30 methy1 kernel: [   16.373931] lis3lv02d: 2-byte sensor found
Oct 28 13:32:30 methy1 kernel: [   16.387022] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
Oct 28 13:32:30 methy1 kernel: [   16.387116] Registered led device: hp::hddprotect
Oct 28 13:32:30 methy1 kernel: [   16.387137] lis3lv02d driver loaded.
Oct 28 13:32:30 methy1 kernel: [   16.388713] sdhci-pci 0000:02:06.3: SDHCI controller found [1180:0822] (rev 20)
Oct 28 13:32:30 methy1 kernel: [   16.388733] sdhci-pci 0000:02:06.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 28 13:32:30 methy1 kernel: [   16.390781] Registered led device: mmc0::
Oct 28 13:32:30 methy1 kernel: [   16.391807] mmc0: SDHCI controller on PCI [0000:02:06.3] using PIO
Oct 28 13:32:30 methy1 kernel: [   16.445116] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
Oct 28 13:32:30 methy1 kernel: [   16.445121] serio: Synaptics pass-through port at isa0060/serio4/input0
Oct 28 13:32:30 methy1 kernel: [   16.487064] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
Oct 28 13:32:31 methy1 kernel: [   16.664070] pcmcia_socket pcmcia_socket1: pccard: PCMCIA card inserted into slot 1
Oct 28 13:32:31 methy1 kernel: [   16.664100] pcmcia_socket pcmcia_socket1: cs: memory probe 0xd8100000-0xd83fffff: excluding 0xd8100000-0xd812ffff
Oct 28 13:32:31 methy1 kernel: [   16.668849] pcmcia 1.0: pcmcia: registering new device pcmcia1.0
Oct 28 13:32:31 methy1 kernel: [   16.717190] scsi5 : pata_pcmcia
Oct 28 13:32:31 methy1 kernel: [   16.717258] ata6: PATA max PIO0 cmd 0x6100 ctl 0x610e irq 19
Oct 28 13:32:31 methy1 kernel: [   17.029494] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
Oct 28 13:32:31 methy1 kernel: [   17.031787] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
Oct 28 13:32:31 methy1 kernel: [   17.033144] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
Oct 28 13:32:31 methy1 kernel: [   17.033988] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
Oct 28 13:32:31 methy1 kernel: [   17.034963] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
Oct 28 13:32:31 methy1 kernel: [   17.035958] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
Oct 28 13:32:31 methy1 kernel: [   17.038296] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
Oct 28 13:32:31 methy1 kernel: [   17.039213] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Oct 28 13:32:31 methy1 kernel: [   17.040054] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Oct 28 13:32:31 methy1 kernel: [   17.041042] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Oct 28 13:32:32 methy1 kernel: [   18.392054] CE: hpet increasing min_delta_ns to 15000 nsec
Oct 28 13:32:34 methy1 kernel: [   19.160154] psmouse serio5: ID: 10 00 64
Oct 28 13:32:34 methy1 kernel: [   19.680956] [drm] Setting GART location based on new memory map
Oct 28 13:32:34 methy1 kernel: [   19.682894] [drm] Loading R500 Microcode
Oct 28 13:32:34 methy1 kernel: [   19.682945] [drm] Num pipes: 1
Oct 28 13:32:34 methy1 kernel: [   19.682955] [drm] writeback test succeeded in 1 usecs
Oct 28 13:32:35 methy1 kernel: [   20.528021] eth0: no IPv6 routers present
Oct 28 13:32:36 methy1 kernel: [   21.453039] eth2: no IPv6 routers present
Oct 28 13:32:37 methy1 kernel: [   21.959899] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input10
Oct 28 13:32:38 methy1 kernel: [   22.883442] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Oct 28 13:32:38 methy1 kernel: [   22.883445] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance
Oct 28 13:32:38 methy1 kernel: [   22.883447] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
Oct 28 13:32:38 methy1 kernel: [   22.883448] vboxdrv: the usage of hardware performance counters by
Oct 28 13:32:38 methy1 kernel: [   22.883449] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
Oct 28 13:32:38 methy1 kernel: [   22.883453] vboxdrv: Found 2 processor cores.
Oct 28 13:32:38 methy1 kernel: [   22.883565] vboxdrv: fAsync=0 offMin=0x1ae offMax=0xc9a4
Oct 28 13:32:38 methy1 kernel: [   22.883605] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Oct 28 13:32:38 methy1 kernel: [   22.883607] vboxdrv: Successfully loaded version 3.0.8 (interface 0x000e0000).
```

---

