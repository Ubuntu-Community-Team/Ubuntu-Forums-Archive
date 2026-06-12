---
title: "ubuntu intrepid Alpha 4 64bit live cd-no ide disks only sata"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by of_darkness on 2008-09-01
Just downloaded [Alpha 4]("http://www.ubuntu.com/testing/intrepid/alpha4") ubuntu live-cd and my 2 pata(ide) disks are not showing upp.
nethier in /dev/sd* or in gparted 
but listed /dev/disk

> ata-SAMSUNG_HD103UJ_S13PJ1BQ717775
ata-SAMSUNG_HD103UJ_S13PJ1BQ717775-part1
ata-SAMSUNG_HD103UJ_S13PJ1BQ717775-part2
ata-WDC_WD2500KS-00MJB0_WD-WMANK1339323
ata-WDC_WD2500KS-00MJB0_WD-WMANK1339323-part1
ata-WDC_WD2500KS-00MJB0_WD-WMANK1339323-part2
ata-WDC_WD2500KS-00MJB0_WD-WMANK1339323-part3
ata-WDC_WD2500KS-00MJB0_WD-WMANK1339323-part4
ata-WDC_WD5000AAKS-07YGA0_WD-WCAS81806883
ata-WDC_WD5000AAKS-07YGA0_WD-WCAS81806883-part1
ata-WDC_WD5000AAKS-07YGA0_WD-WCAS81806883-part2
ata-WDC_WD5000AAKS-07YGA0_WD-WCAS81806883-part3
scsi-1ATA_SAMSUNG_HD103UJ_S13PJ1BQ717775
scsi-1ATA_SAMSUNG_HD103UJ_S13PJ1BQ717775-part1
scsi-1ATA_SAMSUNG_HD103UJ_S13PJ1BQ717775-part2
scsi-1ATA_WDC_WD2500KS-00MJB0_WD-WMANK1339323
scsi-1ATA_WDC_WD2500KS-00MJB0_WD-WMANK1339323-part1
scsi-1ATA_WDC_WD2500KS-00MJB0_WD-WMANK1339323-part2
scsi-1ATA_WDC_WD2500KS-00MJB0_WD-WMANK1339323-part3
scsi-1ATA_WDC_WD2500KS-00MJB0_WD-WMANK1339323-part4
scsi-1ATA_WDC_WD5000AAKS-07YGA0_WD-WCAS81806883
scsi-1ATA_WDC_WD5000AAKS-07YGA0_WD-WCAS81806883-part1
scsi-1ATA_WDC_WD5000AAKS-07YGA0_WD-WCAS81806883-part2
scsi-1ATA_WDC_WD5000AAKS-07YGA0_WD-WCAS81806883-part3
ubuntu@ubuntu:~$ ls /dev/disk/by-uuid/
04de637a-9f28-4fcd-8727-eba15b94c588  863702bb-ba70-410c-a5e3-5fe2b2798550
04e3008b-896e-4e5e-8509-349a1ff1fec2  afa598a3-3198-4b51-8a3b-b6bca4968b54
2f4ea16b-cac0-4d26-998f-5a4759b044cb  b11f8c22-919b-43a7-94e7-3d8e926cd55a
60aa0022-6895-4bae-8407-2944ec0ddf5a  d402edd6-12c3-4e0c-ae38-a8ece2282a58
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-09-01 14:29 04de637a-9f28-4fcd-8727-eba15b94c588 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-09-01 13:52 04e3008b-896e-4e5e-8509-349a1ff1fec2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-09-01 13:52 2f4ea16b-cac0-4d26-998f-5a4759b044cb -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-09-01 13:52 60aa0022-6895-4bae-8407-2944ec0ddf5a -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-09-01 14:29 863702bb-ba70-410c-a5e3-5fe2b2798550 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-09-01 14:33 afa598a3-3198-4b51-8a3b-b6bca4968b54 -> ../../sdc3
lrwxrwxrwx 1 root root 10 2008-09-01 14:33 b11f8c22-919b-43a7-94e7-3d8e926cd55a -> ../../sdc2
lrwxrwxrwx 1 root root 10 2008-09-01 14:33 d402edd6-12c3-4e0c-ae38-a8ece2282a58 -> ../../sdc1
ubuntu@ubuntu:~$ 



dmesg:
```
[    0.640031] NetLabel: Initializing
[    0.640031] NetLabel:  domain hash size = 128
[    0.640031] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.640031] NetLabel:  unlabeled traffic allowed by default
[    0.640031] PCI-GART: No AMD northbridge found.
[    0.640031] AppArmor: AppArmor Filesystem Enabled 
[    0.640031] ACPI: RTC can wake from S4
[    0.651904] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.651912] system 00:0a: ioport range 0xa00-0xadf has been reserved
[    0.651914] system 00:0a: ioport range 0xae0-0xaef has been reserved
[    0.651918] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.651920] system 00:0b: ioport range 0x800-0x87f has been reserved
[    0.651922] system 00:0b: ioport range 0x480-0x4bf has been reserved
[    0.651924] system 00:0b: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.651928] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.651933] system 00:0d: iomem range 0xffc00000-0xffefffff could not be reserved
[    0.651937] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.651939] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.651943] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.651947] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.651949] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    0.651950] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.651952] system 00:10: iomem range 0x100000-0xcfffffff could not be reserved
[    0.652032] PCI: Bridge: 0000:00:01.0
[    0.652032]   IO window: b000-bfff
[    0.652032]   MEM window: 0xfa000000-0xfe8fffff
[    0.652032]   PREFETCH window: 0x00000000d0000000-0x00000000dfffffff
[    0.652032] PCI: Bridge: 0000:00:1c.0
[    0.652032]   IO window: disabled.
[    0.652032]   MEM window: disabled.
[    0.652032]   PREFETCH window: disabled.
[    0.652032] PCI: Bridge: 0000:00:1c.4
[    0.652032]   IO window: c000-cfff
[    0.652032]   MEM window: 0xfe900000-0xfe9fffff
[    0.652032]   PREFETCH window: disabled.
[    0.652032] PCI: Bridge: 0000:00:1c.5
[    0.652032]   IO window: d000-dfff
[    0.652032]   MEM window: 0xfea00000-0xfeafffff
[    0.652032]   PREFETCH window: disabled.
[    0.652032] PCI: Bridge: 0000:00:1e.0
[    0.652032]   IO window: e000-efff
[    0.652032]   MEM window: 0xfeb00000-0xfebfffff
[    0.652032]   PREFETCH window: 0x00000000f4000000-0x00000000f7ffffff
[    0.652032] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.652032] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.652032] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    0.652032] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.652032] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[    0.652032] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.652032] ACPI: PCI Interrupt 0000:00:1c.5[b] -> GSI 16 (level, low) -> IRQ 16
[    0.652032] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.652032] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.652032] NET: Registered protocol family 2
[    0.687570] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.688618] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.691661] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.692618] TCP: Hash tables configured (established 524288 bind 65536)
[    0.692620] TCP reno registered
[    0.703810] NET: Registered protocol family 1
[    0.703897] checking if image is initramfs... it is
[    1.152621] Switched to high resolution mode on CPU 1
[    1.155427] Switched to high resolution mode on CPU 0
[    1.360381] Freeing initrd memory: 8710k freed
[    1.360587] audit: initializing netlink socket (disabled)
[    1.360587] type=2000 audit(1220277140.356:1): initialized
[    1.371820] Total HugeTLB memory allocated, 0
[    1.371998] VFS: Disk quotas dquot_6.5.1
[    1.371998] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.371998] msgmni has been set to 15984
[    1.371998] io scheduler noop registered
[    1.371998] io scheduler anticipatory registered
[    1.371998] io scheduler deadline registered
[    1.371998] io scheduler cfq registered (default)
[    1.371998] pci 0000:01:00.0: Boot video device
[    1.371998] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    1.371998] assign_interrupt_mode Found MSI capability
[    1.371998] Allocate Port Service[0000:00:01.0:pcie00]
[    1.371998] Allocate Port Service[0000:00:01.0:pcie03]
[    1.371998] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.371998] assign_interrupt_mode Found MSI capability
[    1.371998] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.371998] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.371998] Allocate Port Service[0000:00:1c.0:pcie03]
[    1.371998] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    1.372024] assign_interrupt_mode Found MSI capability
[    1.372024] Allocate Port Service[0000:00:1c.4:pcie00]
[    1.372024] Allocate Port Service[0000:00:1c.4:pcie02]
[    1.372024] Allocate Port Service[0000:00:1c.4:pcie03]
[    1.372024] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    1.372024] assign_interrupt_mode Found MSI capability
[    1.372024] Allocate Port Service[0000:00:1c.5:pcie00]
[    1.372025] Allocate Port Service[0000:00:1c.5:pcie02]
[    1.372025] Allocate Port Service[0000:00:1c.5:pcie03]
[    1.395452] Linux agpgart interface v0.103
[    1.395452] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.395452] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.395452] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.399451] brd: module loaded
[    1.399451] input: Macintosh mouse button emulation as /class/input/input0
[    1.399451] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.399451] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.399451] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.422594] mice: PS/2 mouse device common for all mice
[    1.423451] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.423451] rtc0: alarms up to one month, y3k
[    1.423451] cpuidle: using governor ladder
[    1.423451] cpuidle: using governor menu
[    1.423451] aufs 20080609
[    1.423451] registered taskstats version 1
[    1.423451] rtc_cmos 00:03: setting system clock to 2008-09-01 13:52:21 UTC (1220277141)
[    1.423451] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.423451] EDD information not available.
[    1.423451] Freeing unused kernel memory: 408k freed
[    1.467431] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.516830] fuse init (API version 7.9)
[    1.534973] uvesafb: failed to execute /sbin/v86d
[    1.535019] uvesafb: make sure that the v86d helper is installed and executable
[    1.535057] uvesafb: Getting VBE info block failed (eax=0x4f00, err=-2)
[    1.535098] uvesafb: vbe_init() failed with -22
[    1.535136] uvesafb: probe of uvesafb.0 failed with error -22
[    1.583680] ACPI: SSDT CFFC00F0, 0277 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    1.583931] ACPI: ACPI0007:00 is registered as cooling_device0
[    1.584250] ACPI: SSDT CFFC0580, 0277 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    1.584477] ACPI: ACPI0007:01 is registered as cooling_device1
[    2.045496] usbcore: registered new interface driver usbfs
[    2.045515] usbcore: registered new interface driver hub
[    2.047461] usbcore: registered new device driver usb
[    2.047786] USB Universal Host Controller Interface driver v3.0
[    2.047786] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.047786] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    2.047786] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.047786] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.047817] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ac00
[    2.047817] usb usb1: configuration #1 chosen from 1 choice
[    2.047817] hub 1-0:1.0: USB hub found
[    2.047817] hub 1-0:1.0: 2 ports detected
[    2.119004] CPU1: Temperature above threshold, cpu clock throttled (total events = 1)
[    2.119010] CPU0: Temperature/speed normal
[    2.153836] ACPI: PCI Interrupt 0000:00:1a.1[b] -> GSI 21 (level, low) -> IRQ 21
[    2.153845] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    2.153848] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.153865] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.153891] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    2.153951] usb usb2: configuration #1 chosen from 1 choice
[    2.153971] hub 2-0:1.0: USB hub found
[    2.153976] hub 2-0:1.0: 2 ports detected
[    2.227288] No dock devices found.
[    2.237689] SCSI subsystem initialized
[    2.261810] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[    2.261810] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    2.261810] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.261810] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    2.266575] ehci_hcd 0000:00:1a.7: debug port 1
[    2.266580] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    2.266589] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    2.267438] libata version 3.00 loaded.
[    2.282412] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.282469] usb usb3: configuration #1 chosen from 1 choice
[    2.282490] hub 3-0:1.0: USB hub found
[    2.282496] hub 3-0:1.0: 4 ports detected
[    2.387655] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[    2.387655] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    2.387655] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.387655] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.387655] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a800
[    2.387655] usb usb4: configuration #1 chosen from 1 choice
[    2.387655] hub 4-0:1.0: USB hub found
[    2.387655] hub 4-0:1.0: 2 ports detected
[    2.495155] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 19
[    2.495155] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    2.495155] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.495155] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    2.495155] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a480
[    2.495155] usb usb5: configuration #1 chosen from 1 choice
[    2.495155] hub 5-0:1.0: USB hub found
[    2.495155] hub 5-0:1.0: 2 ports detected
[    2.599158] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    2.599158] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    2.599158] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.599158] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    2.599158] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a400
[    2.599158] usb usb6: configuration #1 chosen from 1 choice
[    2.599158] hub 6-0:1.0: USB hub found
[    2.599158] hub 6-0:1.0: 2 ports detected
[    2.707653] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    2.707653] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    2.707653] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.707653] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 7
[    2.707653] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000a080
[    2.707653] usb usb7: configuration #1 chosen from 1 choice
[    2.707653] hub 7-0:1.0: USB hub found
[    2.707653] hub 7-0:1.0: 2 ports detected
[    2.815658] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[    2.815658] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    2.815658] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.815658] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    2.819653] ehci_hcd 0000:00:1d.7: debug port 1
[    2.819653] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    2.819653] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    2.839653] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.839653] usb usb8: configuration #1 chosen from 1 choice
[    2.839653] hub 8-0:1.0: USB hub found
[    2.839653] hub 8-0:1.0: 8 ports detected
[    2.942736] hub 8-0:1.0: over-current change on port 7
[    2.943653] r8169 Gigabit Ethernet driver 2.2LK loaded
[    2.943653] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    2.943653] PCI: Setting latency timer of device 0000:04:00.0 to 64
[    2.943653] eth0: RTL8168b/8111b at 0xffffc20000c40000, 00:19:db:cc:a6:f6, XID 38000000 IRQ 2299
[    2.943653] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[    2.999665] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.007234] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 19
[    3.007234] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.007234] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[    3.007234] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 19 (level, low) -> IRQ 19
[    3.007234] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    3.007234] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[    3.007234] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.007234] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    3.007234] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[    3.007234] ahci 0000:03:00.0: version 3.0
[    3.007234] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.007234] ahci 0000:03:00.0: controller can't do NCQ, turning off CAP_NCQ
[    3.007234] ahci 0000:03:00.0: MV_AHCI HACK: port_map 7 -> 3
[    3.049869] hub 8-0:1.0: over-current change on port 8
[    4.011128] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 3 ports 3 Gbps 0x3 impl IDE mode
[    4.011131] ahci 0000:03:00.0: flags: 64bit stag led pmp slum part 
[    4.011137] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    4.012237] scsi0 : ahci
[    4.013316] scsi1 : ahci
[    4.014359] scsi2 : ahci
[    4.014383] ata1: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd00 irq 16
[    4.014387] ata2: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd80 irq 16
[    4.014388] ata3: DUMMY
[    4.278162] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00012efe60]
[    4.498493] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.502094] ata1.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
[    4.502094] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    4.502094] ata1.00: configured for UDMA/133
[    4.830933] ata2: SATA link down (SStatus 0 SControl 300)
[    4.830915] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    4.830915] ata_piix 0000:00:1f.2: version 2.12
[    4.830915] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 19
[    4.830915] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    4.830915] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.830915] scsi3 : ata_piix
[    4.830915] scsi4 : ata_piix
[    4.831943] ata4: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 19
[    4.831946] ata5: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 19
[    5.305266] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.322893] ata4.00: ATA-8: WDC WD5000AAKS-07YGA0, 12.01C02, max UDMA/133
[    5.322893] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.334985] ata4.00: configured for UDMA/133
[    5.839519] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.847645] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB00, max UDMA/100
[    5.863647] ata5.00: configured for UDMA/100
[    5.867483] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[    5.869302] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB00 PQ: 0 ANSI: 5
[    5.869361] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 19 (level, low) -> IRQ 19
[    5.869364] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    5.869395] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    5.870428] scsi5 : ata_piix
[    5.871470] scsi6 : ata_piix
[    5.871475] ata6: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 19
[    5.871475] ata7: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 19
[    6.343230] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.351358] ata6.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB00, max UDMA/100
[    6.367352] ata6.00: configured for UDMA/100
[    6.895477] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.907441] ata7.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    6.907441] ata7.00: 488397168 sectors, multi 16: LBA48 
[    6.915434] ata7.00: configured for UDMA/133
[    6.918935] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB00 PQ: 0 ANSI: 5
[    6.918935] scsi 6:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[    6.926231] Driver 'sd' needs updating - please use bus_type methods
[    6.926305] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    6.926317] sd 0:0:0:0: [sda] Write Protect is off
[    6.926319] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.926338] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.926379] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    6.926390] sd 0:0:0:0: [sda] Write Protect is off
[    6.926392] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.926410] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.926413]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    6.941629]  sda1 sda2
[    6.941708] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.942177] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    6.942177] sd 3:0:0:0: [sdb] Write Protect is off
[    6.942177] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.942177] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.942177] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    6.942177] sd 3:0:0:0: [sdb] Write Protect is off
[    6.942177] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.942177] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.942177]  sdb: sdb1 sdb2 sdb3
[    6.945585] sd 3:0:0:0: [sdb] Attached SCSI disk
[    6.945759] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    6.945771] sd 6:0:0:0: [sdc] Write Protect is off
[    6.945773] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.945793] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.945833] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    6.945845] sd 6:0:0:0: [sdc] Write Protect is off
[    6.945846] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.945866] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.945868]  sdc:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.949187] Uniform CD-ROM driver Revision: 3.20
[    6.949234] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.953708] sr1: scsi3-mmc drive: 32x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.953753] sr 5:0:0:0: Attached scsi CD-ROM sr1
[    6.962357]  sdc1 sdc2 sdc3 sdc4
[    6.962446] sd 6:0:0:0: [sdc] Attached SCSI disk
[    6.967969] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.967969] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    6.967969] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    6.967969] sr 5:0:0:0: Attached scsi generic sg3 type 5
[    6.967969] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    8.100381] kjournald starting.  Commit interval 5 seconds
[    8.101748] EXT3-fs: mounted filesystem with ordered data mode.
[    8.136381] kjournald starting.  Commit interval 5 seconds
[    8.136381] EXT3-fs: mounted filesystem with ordered data mode.
[    8.176381] kjournald starting.  Commit interval 5 seconds
[    8.176381] EXT3-fs: mounted filesystem with ordered data mode.
[    8.204381] kjournald starting.  Commit interval 5 seconds
[    8.204381] EXT3-fs: mounted filesystem with ordered data mode.
[    8.238647] kjournald starting.  Commit interval 5 seconds
[    8.239895] EXT3-fs: mounted filesystem with ordered data mode.
[    8.326647] kjournald starting.  Commit interval 5 seconds
[    8.328105] EXT3-fs: mounted filesystem with ordered data mode.
[    8.358647] kjournald starting.  Commit interval 5 seconds
[    8.360105] EXT3-fs: mounted filesystem with ordered data mode.
[    8.378647] kjournald starting.  Commit interval 5 seconds
[    8.378647] EXT3-fs: mounted filesystem with ordered data mode.
[    9.453514] kjournald starting.  Commit interval 5 seconds
[    9.453522] EXT3-fs: mounted filesystem with ordered data mode.
[    9.474746] kjournald starting.  Commit interval 5 seconds
[    9.477271] EXT3-fs: mounted filesystem with ordered data mode.
[    9.493900] kjournald starting.  Commit interval 5 seconds
[    9.493900] EXT3-fs: mounted filesystem with ordered data mode.
[    9.505072] kjournald starting.  Commit interval 5 seconds
[    9.505072] EXT3-fs: mounted filesystem with ordered data mode.
[    9.517072] kjournald starting.  Commit interval 5 seconds
[    9.517072] EXT3-fs: mounted filesystem with ordered data mode.
[    9.545072] kjournald starting.  Commit interval 5 seconds
[    9.545072] EXT3-fs: mounted filesystem with ordered data mode.
[    9.553073] kjournald starting.  Commit interval 5 seconds
[    9.553073] EXT3-fs: mounted filesystem with ordered data mode.
[    9.560928] kjournald starting.  Commit interval 5 seconds
[    9.560928] EXT3-fs: mounted filesystem with ordered data mode.
[    9.857627] ISO 9660 Extensions: Microsoft Joliet Level 3
[    9.882464] ISO 9660 Extensions: RRIP_1991A
[   10.152271] loop: module loaded
[   10.390917] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   58.531070] udevd version 124 started
[   59.781833] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   59.942717] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   60.096002] iTCO_vendor_support: vendor-support=0
[   60.096742] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   60.096803] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0860)
[   60.096832] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   60.856957] Linux video capture interface: v2.00
[   60.970022] input: Power Button (FF) as /class/input/input2
[   60.986002] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   60.986023] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   61.017275] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   61.030499] ACPI: Power Button (FF) [PWRF]
[   61.030593] input: Power Button (CM) as /class/input/input3
[   61.091293] ACPI: Power Button (CM) [PWRB]
[   61.134382] ivtv:  Start initialization, version 1.3.0
[   61.134382] ivtv0: Initializing card #0
[   61.134382] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   61.142262] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   61.194361] tveeprom 0-0050: Hauppauge model 48139, rev K2B7, serial# 9978285
[   61.194361] tveeprom 0-0050: tuner model is Philips FM1216ME MK5 (idx 117, type 38)
[   61.194361] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   61.194361] tveeprom 0-0050: audio processor is MSP4418 (idx 25)
[   61.194361] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   61.194361] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[   61.194361] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   61.840519] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   61.958481] input: ImExPS/2 Logitech MX Mouse as /class/input/input4
[   62.033152] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   62.041354] msp3400 0-0040: MSP4418G-B3 found @ 0x80 (ivtv i2c driver #0)
[   62.041356] msp3400 0-0040: msp3400 supports nicam and radio, mode is autodetect and autoselect
[   62.097476] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   62.113476] tda9887 0-0043: creating new instance
[   62.113476] tda9887 0-0043: tda988[5/6/7] found
[   62.113476] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   62.153635] tuner-simple 0-0061: creating new instance
[   62.153635] tuner-simple 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   62.171347] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   62.171347] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   62.171347] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   62.171347] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   62.171347] ivtv0: Registered device radio0 for encoder radio
[   62.171347] ivtv0: Registered device video16 for decoder MPG (1024 kB)
[   62.171347] ivtv0: Registered device vbi8 for decoder VBI (64 kB)
[   62.171347] ivtv0: Registered device vbi16 for decoder VOUT
[   62.171347] ivtv0: Registered device video48 for decoder YUV (1024 kB)
[   62.171347] ivtv0: Initialized card #0: Hauppauge WinTV PVR-350
[   62.171347] ivtv:  End initialization
[   63.529376] ip_tables: (C) 2000-2006 Netfilter Core Team
[   66.776158] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   66.930371] parport_pc 00:07: reported by Plug and Play ACPI
[   66.930415] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   67.022735] lp0: using parport0 (interrupt-driven).
[   67.082733] ppdev: user-space parallel port driver
[   71.855601] firmware: requesting v4l-cx2341x-enc.fw
[   72.702075] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   72.702075] firmware: requesting v4l-cx2341x-dec.fw
[   72.718076] ivtv0: Loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   72.918076] ivtv0: Encoder revision: 0x02060039
[   72.918076] ivtv0: Decoder revision: 0x02020023
[   72.972980] firmware: requesting v4l-cx2341x-init.mpg
[   73.013855] ivtv0: Loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[   74.005283] Bluetooth: Core ver 2.11
[   74.005759] NET: Registered protocol family 31
[   74.005759] Bluetooth: HCI device and connection manager initialized
[   74.005759] Bluetooth: HCI socket layer initialized
[   74.094015] Bluetooth: L2CAP ver 2.9
[   74.094016] Bluetooth: L2CAP socket layer initialized
[   74.252690] Bluetooth: RFCOMM socket layer initialized
[   74.252690] Bluetooth: RFCOMM TTY layer initialized
[   74.252690] Bluetooth: RFCOMM ver 1.8
[   79.530325] r8169: eth0: link up
[   79.530325] r8169: eth0: link up
[   80.373978] mtrr: base(0xfb000000) is not aligned on a size(0xe00000) boundary
[   81.099524] NET: Registered protocol family 17
[   92.742394] NET: Registered protocol family 10
[   92.745255] lo: Disabled Privacy Extensions
[  104.423877] eth0: no IPv6 routers present
[  186.430996] ppdev0: registered pardevice
[  186.478964] ppdev0: unregistered pardevice
[  187.311700] ppdev0: registered pardevice
[  187.357504] ppdev0: unregistered pardevice
[  187.481581] ppdev0: registered pardevice
[  187.533992] ppdev0: unregistered pardevice
[  331.522053] Machine check events logged

```
 syslog 
```
Sep  1 13:53:22 ubuntu syslogd 1.5.0#2ubuntu4: restart.
Sep  1 13:53:22 ubuntu klogd: Inspecting /boot/System.map-2.6.26-5-generic
Sep  1 13:53:22 ubuntu klogd: Loaded 31219 symbols from /boot/System.map-2.6.26-5-generic.
Sep  1 13:53:22 ubuntu klogd: Symbols match kernel version 2.6.26.
Sep  1 13:53:22 ubuntu klogd: Loaded 18366 symbols from 95 modules.
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Initializing cgroup subsys cpuset
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Initializing cgroup subsys cpu
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Linux version 2.6.26-5-generic (buildd@crested) (gcc version 4.3.1 (Ubuntu 4.3.1-8ubuntu3) ) #1 SMP Sun Aug 10 20:28:44 UTC 2008 (Ubuntu 2.6.26-5.15-generic)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash -- debian-installer/language=sv console-setup/layoutcode?=se xforcevesa
Sep  1 13:53:22 ubuntu klogd: [    0.000000] BIOS-provided physical RAM map:
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cfff0000 (ACPI NVS)
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000d0000000 (reserved)
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Entering add_active_range(0, 256, 851888) 1 entries of 3200 used
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Entering add_active_range(0, 1048576, 2293760) 2 entries of 3200 used
Sep  1 13:53:22 ubuntu klogd: [    0.000000] max_pfn_mapped = 2293760
Sep  1 13:53:22 ubuntu klogd: [    0.000000] init_memory_mapping
Sep  1 13:53:22 ubuntu klogd: [    0.000000] DMI present.
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: RSDP 000F9380, 0014 (r0 ACPIAM)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: RSDT CFFB0000, 003C (r1 080907 RSDT1802 20070809 MSFT       97)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: FACP CFFB0200, 0084 (r1 080907 FACP1802 20070809 MSFT       97)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: DSDT CFFB0440, 5564 (r1  0AAAA 0AAAA000        0 INTL 20051117)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: FACS CFFBE000, 0040
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: APIC CFFB0390, 006C (r1 080907 APIC1802 20070809 MSFT       97)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: MCFG CFFB0400, 003C (r1 080907 OEMMCFG  20070809 MSFT       97)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: OEMB CFFBE040, 0071 (r1 080907 OEMB1802 20070809 MSFT       97)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: GSCI CFFBE0C0, 2024 (r1 080907 GMCHSCI  20070809 MSFT       97)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: SSDT CFFC0A10, 082F (r1 DpgPmm    CpuPm       12 INTL 20051117)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] No NUMA configuration found
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Faking a node at 0000000000000000-0000000230000000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Entering add_active_range(0, 256, 851888) 1 entries of 3200 used
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Entering add_active_range(0, 1048576, 2293760) 2 entries of 3200 used
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Bootmem setup node 0 0000000000000000-0000000230000000
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   bootmap [0000000000017000 -  000000000005cfff] pages 46
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   early res: 0 [0-fff] BIOS data page
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   early res: 1 [6000-7fff] TRAMPOLINE
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   early res: 2 [200000-7da81b] TEXT DATA BSS
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   early res: 3 [7f77e000-7ffffad2] RAMDISK
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   early res: 4 [9dc00-fffff] BIOS reserved
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   early res: 5 [8000-11fff] PGTABLE
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  [ffffe20000000000-ffffe20002dfffff] PMD -> [ffff810001200000-ffff810003ffffff] on node 0
Sep  1 13:53:22 ubuntu klogd: [    0.000000]  [ffffe20002e00000-ffffe20008bfffff] PMD -> [ffff81000c000000-ffff8100111fffff] on node 0
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Zone PFN ranges:
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   DMA             0 ->     4096
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   DMA32        4096 ->  1048576
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   Normal    1048576 ->  2293760
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Movable zone start PFN for each node
Sep  1 13:53:22 ubuntu klogd: [    0.000000] early_node_map[3] active PFN ranges
Sep  1 13:53:22 ubuntu klogd: [    0.000000]     0:        0 ->      157
Sep  1 13:53:22 ubuntu klogd: [    0.000000]     0:      256 ->   851888
Sep  1 13:53:22 ubuntu klogd: [    0.000000]     0:  1048576 ->  2293760
Sep  1 13:53:22 ubuntu klogd: [    0.000000] On node 0 totalpages: 2096973
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   DMA zone: 64 pages used for memmap
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   DMA zone: 1611 pages reserved
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   DMA zone: 2322 pages, LIFO batch:0
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   DMA32 zone: 831472 pages, LIFO batch:31
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   Normal zone: 19456 pages used for memmap
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   Normal zone: 1225728 pages, LIFO batch:31
Sep  1 13:53:22 ubuntu klogd: [    0.000000]   Movable zone: 0 pages used for memmap
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep  1 13:53:22 ubuntu klogd: [    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: IRQ0 used by override.
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: IRQ2 used by override.
Sep  1 13:53:22 ubuntu klogd: [    0.000000] ACPI: IRQ9 used by override.
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Setting APIC routing to flat
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e3000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 00000000000e3000 - 0000000000100000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 00000000cffb0000 - 00000000cffbe000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 00000000cffbe000 - 00000000cfff0000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 00000000cfff0000 - 00000000d0000000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ee00000)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PERCPU: Allocating 45360 bytes of per cpu data
Sep  1 13:53:22 ubuntu klogd: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2059522
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Policy zone: Normal
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash -- debian-installer/language=sv console-setup/layoutcode?=se xforcevesa
Sep  1 13:53:22 ubuntu klogd: [    0.000000] Initializing CPU#0
Sep  1 13:53:22 ubuntu klogd: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Sep  1 13:53:22 ubuntu klogd: [    0.000000] TSC calibrated against PM_TIMER
Sep  1 13:53:22 ubuntu klogd: [    0.000000] time.c: Detected 2402.375 MHz processor.
Sep  1 13:53:22 ubuntu klogd: [    0.004000] Console: colour VGA+ 80x25
Sep  1 13:53:22 ubuntu klogd: [    0.004000] console [tty0] enabled
Sep  1 13:53:22 ubuntu klogd: [    0.004000] Checking aperture...
Sep  1 13:53:22 ubuntu klogd: [    0.004000] Calgary: detecting Calgary via BIOS EBDA area
Sep  1 13:53:22 ubuntu klogd: [    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Sep  1 13:53:22 ubuntu klogd: [    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Sep  1 13:53:22 ubuntu klogd: [    0.004000] Placing software IO TLB between 0x4000000 - 0x8000000
Sep  1 13:53:22 ubuntu klogd: [    0.004000] Memory: 8175596k/9175040k available (2950k kernel code, 212296k reserved, 1479k data, 408k init)
Sep  1 13:53:22 ubuntu klogd: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Sep  1 13:53:22 ubuntu klogd: [    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Sep  1 13:53:22 ubuntu klogd: [    0.084008] Calibrating delay using timer specific routine.. 4808.75 BogoMIPS (lpj=9617504)
Sep  1 13:53:22 ubuntu klogd: [    0.084030] Security Framework initialized
Sep  1 13:53:22 ubuntu klogd: [    0.084035] SELinux:  Disabled at boot.
Sep  1 13:53:22 ubuntu klogd: [    0.084047] AppArmor: AppArmor initialized <NULL>
Sep  1 13:53:22 ubuntu klogd: [    0.084051] AppArmor: Registered secondary security module capability
Sep  1 13:53:22 ubuntu klogd: [    0.084053] Capability LSM initialized as secondary
Sep  1 13:53:22 ubuntu klogd: [    0.084805] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Sep  1 13:53:22 ubuntu klogd: [    0.088509] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Sep  1 13:53:22 ubuntu klogd: [    0.090178] Mount-cache hash table entries: 256
Sep  1 13:53:22 ubuntu klogd: [    0.090332] Initializing cgroup subsys ns
Sep  1 13:53:22 ubuntu klogd: [    0.090337] Initializing cgroup subsys cpuacct
Sep  1 13:53:22 ubuntu klogd: [    0.090339] Initializing cgroup subsys memory
Sep  1 13:53:22 ubuntu klogd: [    0.090352] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  1 13:53:22 ubuntu klogd: [    0.090353] CPU: L2 cache: 4096K
Sep  1 13:53:22 ubuntu klogd: [    0.090355] CPU 0/0 -> Node 0
Sep  1 13:53:22 ubuntu klogd: [    0.090357] CPU: Physical Processor ID: 0
Sep  1 13:53:22 ubuntu klogd: [    0.090358] CPU: Processor Core ID: 0
Sep  1 13:53:22 ubuntu klogd: [    0.090364] CPU0: Thermal monitoring enabled (TM2)
Sep  1 13:53:22 ubuntu klogd: [    0.090366] using mwait in idle threads.
Sep  1 13:53:22 ubuntu klogd: [    0.091280] Early unpacking initramfs... done
Sep  1 13:53:22 ubuntu klogd: [    0.425945] ACPI: Core revision 20080321
Sep  1 13:53:22 ubuntu klogd: [    0.427640] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep  1 13:53:22 ubuntu klogd: [    0.480030] CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
Sep  1 13:53:22 ubuntu klogd: [    0.480030] Using local APIC timer interrupts.
Sep  1 13:53:22 ubuntu klogd: [    0.484030] APIC timer calibration result 16683147
Sep  1 13:53:22 ubuntu klogd: [    0.484030] Detected 16.683 MHz APIC timer.
Sep  1 13:53:22 ubuntu klogd: [    0.484030] Booting processor 1/1 ip 6000
Sep  1 13:53:22 ubuntu klogd: [    0.492030] Initializing CPU#1
Sep  1 13:53:22 ubuntu klogd: [    0.492030] Calibrating delay using timer specific routine.. 4804.79 BogoMIPS (lpj=9609587)
Sep  1 13:53:22 ubuntu klogd: [    0.492030] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  1 13:53:22 ubuntu klogd: [    0.492030] CPU: L2 cache: 4096K
Sep  1 13:53:22 ubuntu klogd: [    0.492030] CPU 1/1 -> Node 0
Sep  1 13:53:22 ubuntu klogd: [    0.492030] CPU: Physical Processor ID: 0
Sep  1 13:53:22 ubuntu klogd: [    0.492030] CPU: Processor Core ID: 1
Sep  1 13:53:22 ubuntu klogd: [    0.492030] CPU1: Thermal monitoring enabled (TM2)
Sep  1 13:53:22 ubuntu klogd: [    0.572031] CPU1: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
Sep  1 13:53:22 ubuntu klogd: [    0.572031] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Sep  1 13:53:22 ubuntu klogd: [    0.576031] Brought up 2 CPUs
Sep  1 13:53:22 ubuntu klogd: [    0.576031] Total of 2 processors activated (9613.54 BogoMIPS).
Sep  1 13:53:22 ubuntu klogd: [    0.576031] CPU0 attaching sched-domain:
Sep  1 13:53:22 ubuntu klogd: [    0.576031]  domain 0: span 0-1
Sep  1 13:53:22 ubuntu klogd: [    0.576031]   groups: 0 1
Sep  1 13:53:22 ubuntu klogd: [    0.576031]   domain 1: span 0-1
Sep  1 13:53:22 ubuntu klogd: [    0.576031]    groups: 0-1
Sep  1 13:53:22 ubuntu klogd: [    0.576031] CPU1 attaching sched-domain:
Sep  1 13:53:22 ubuntu klogd: [    0.576031]  domain 0: span 0-1
Sep  1 13:53:22 ubuntu klogd: [    0.576031]   groups: 1 0
Sep  1 13:53:22 ubuntu klogd: [    0.576031]   domain 1: span 0-1
Sep  1 13:53:22 ubuntu klogd: [    0.576031]    groups: 0-1
Sep  1 13:53:22 ubuntu klogd: [    0.576032] net_namespace: 1224 bytes
Sep  1 13:53:22 ubuntu klogd: [    0.576032] Booting paravirtualized kernel on bare hardware
Sep  1 13:53:22 ubuntu klogd: [    0.576032] NET: Registered protocol family 16
Sep  1 13:53:22 ubuntu klogd: [    0.576032] ACPI: bus type pci registered
Sep  1 13:53:22 ubuntu klogd: [    0.576032] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Sep  1 13:53:22 ubuntu klogd: [    0.576032] PCI: Not using MMCONFIG.
Sep  1 13:53:22 ubuntu klogd: [    0.576032] PCI: Using configuration type 1 for base access
Sep  1 13:53:22 ubuntu klogd: [    0.576032] ACPI: EC: Look up EC in DSDT
Sep  1 13:53:22 ubuntu klogd: [    0.583359] ACPI: Interpreter enabled
Sep  1 13:53:22 ubuntu klogd: [    0.583361] ACPI: (supports S0 S1 S3 S4 S5)
Sep  1 13:53:22 ubuntu klogd: [    0.583373] ACPI: Using IOAPIC for interrupt routing
Sep  1 13:53:22 ubuntu klogd: [    0.583421] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Sep  1 13:53:22 ubuntu klogd: [    0.586635] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Sep  1 13:53:22 ubuntu klogd: [    0.598888] PCI: Using MMCONFIG at e0000000 - efffffff
Sep  1 13:53:22 ubuntu klogd: [    0.608031] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  1 13:53:22 ubuntu klogd: [    0.608031] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Sep  1 13:53:22 ubuntu klogd: [    0.608031] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Sep  1 13:53:22 ubuntu klogd: [    0.608031] PCI: Transparent bridge - 0000:00:1e.0
Sep  1 13:53:22 ubuntu klogd: [    0.608031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  1 13:53:22 ubuntu klogd: [    0.608031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Sep  1 13:53:22 ubuntu klogd: [    0.608031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Sep  1 13:53:22 ubuntu klogd: [    0.608031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
Sep  1 13:53:22 ubuntu klogd: [    0.608031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 *14 15)
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 *10 11 12 14 15)
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 8C, should be 87 [20080321]
Sep  1 13:53:22 ubuntu klogd: [    0.612031] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  1 13:53:22 ubuntu klogd: [    0.612031] pnp: PnP ACPI init
Sep  1 13:53:22 ubuntu klogd: [    0.612031] ACPI: bus type pnp registered
Sep  1 13:53:22 ubuntu klogd: [    0.616031] pnp: PnP ACPI: found 17 devices
Sep  1 13:53:22 ubuntu klogd: [    0.616031] ACPI: ACPI bus type pnp unregistered
Sep  1 13:53:22 ubuntu klogd: [    0.620031] PCI: Using ACPI for IRQ routing
Sep  1 13:53:22 ubuntu klogd: [    0.639850] NET: Registered protocol family 8
Sep  1 13:53:22 ubuntu klogd: [    0.639852] NET: Registered protocol family 20
Sep  1 13:53:22 ubuntu klogd: [    0.640031] NetLabel: Initializing
Sep  1 13:53:22 ubuntu klogd: [    0.640031] NetLabel:  domain hash size = 128
Sep  1 13:53:22 ubuntu klogd: [    0.640031] NetLabel:  protocols = UNLABELED CIPSOv4
Sep  1 13:53:22 ubuntu klogd: [    0.640031] NetLabel:  unlabeled traffic allowed by default
Sep  1 13:53:22 ubuntu klogd: [    0.640031] PCI-GART: No AMD northbridge found.
Sep  1 13:53:22 ubuntu klogd: [    0.640031] AppArmor: AppArmor Filesystem Enabled 
Sep  1 13:53:22 ubuntu klogd: [    0.640031] ACPI: RTC can wake from S4
Sep  1 13:53:22 ubuntu klogd: [    0.651904] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651912] system 00:0a: ioport range 0xa00-0xadf has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651914] system 00:0a: ioport range 0xae0-0xaef has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651918] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651920] system 00:0b: ioport range 0x800-0x87f has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651922] system 00:0b: ioport range 0x480-0x4bf has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651924] system 00:0b: iomem range 0xfed1c000-0xfed1ffff has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651928] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651933] system 00:0d: iomem range 0xffc00000-0xffefffff could not be reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651937] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651939] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651943] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651947] system 00:10: iomem range 0x0-0x9ffff could not be reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651949] system 00:10: iomem range 0xc0000-0xcffff has been reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651950] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
Sep  1 13:53:22 ubuntu klogd: [    0.651952] system 00:10: iomem range 0x100000-0xcfffffff could not be reserved
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Bridge: 0000:00:01.0
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   IO window: b000-bfff
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   MEM window: 0xfa000000-0xfe8fffff
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   PREFETCH window: 0x00000000d0000000-0x00000000dfffffff
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Bridge: 0000:00:1c.0
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   IO window: disabled.
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   MEM window: disabled.
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   PREFETCH window: disabled.
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Bridge: 0000:00:1c.4
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   IO window: c000-cfff
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   MEM window: 0xfe900000-0xfe9fffff
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   PREFETCH window: disabled.
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Bridge: 0000:00:1c.5
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   IO window: d000-dfff
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   MEM window: 0xfea00000-0xfeafffff
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   PREFETCH window: disabled.
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Bridge: 0000:00:1e.0
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   IO window: e000-efff
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   MEM window: 0xfeb00000-0xfebfffff
Sep  1 13:53:22 ubuntu klogd: [    0.652032]   PREFETCH window: 0x00000000f4000000-0x00000000f7ffffff
Sep  1 13:53:22 ubuntu klogd: [    0.652032] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    0.652032] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    0.652032] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Sep  1 13:53:22 ubuntu klogd: [    0.652032] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Sep  1 13:53:22 ubuntu klogd: [    0.652032] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    0.652032] NET: Registered protocol family 2
Sep  1 13:53:22 ubuntu klogd: [    0.687570] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Sep  1 13:53:22 ubuntu klogd: [    0.688618] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Sep  1 13:53:22 ubuntu klogd: [    0.691661] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Sep  1 13:53:22 ubuntu klogd: [    0.692618] TCP: Hash tables configured (established 524288 bind 65536)
Sep  1 13:53:22 ubuntu klogd: [    0.692620] TCP reno registered
Sep  1 13:53:22 ubuntu klogd: [    0.703810] NET: Registered protocol family 1
Sep  1 13:53:22 ubuntu klogd: [    0.703897] checking if image is initramfs... it is
Sep  1 13:53:22 ubuntu klogd: [    1.152621] Switched to high resolution mode on CPU 1
Sep  1 13:53:22 ubuntu klogd: [    1.155427] Switched to high resolution mode on CPU 0
Sep  1 13:53:22 ubuntu klogd: [    1.360381] Freeing initrd memory: 8710k freed
Sep  1 13:53:22 ubuntu klogd: [    1.360587] audit: initializing netlink socket (disabled)
Sep  1 13:53:22 ubuntu klogd: [    1.360587] type=2000 audit(1220277140.356:1): initialized
Sep  1 13:53:22 ubuntu klogd: [    1.371820] Total HugeTLB memory allocated, 0
Sep  1 13:53:22 ubuntu klogd: [    1.371998] VFS: Disk quotas dquot_6.5.1
Sep  1 13:53:22 ubuntu klogd: [    1.371998] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Sep  1 13:53:22 ubuntu klogd: [    1.371998] msgmni has been set to 15984
Sep  1 13:53:22 ubuntu klogd: [    1.371998] io scheduler noop registered
Sep  1 13:53:22 ubuntu klogd: [    1.371998] io scheduler anticipatory registered
Sep  1 13:53:22 ubuntu klogd: [    1.371998] io scheduler deadline registered
Sep  1 13:53:22 ubuntu klogd: [    1.371998] io scheduler cfq registered (default)
Sep  1 13:53:22 ubuntu klogd: [    1.371998] pci 0000:01:00.0: Boot video device
Sep  1 13:53:22 ubuntu klogd: [    1.371998] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    1.371998] assign_interrupt_mode Found MSI capability
Sep  1 13:53:22 ubuntu klogd: [    1.371998] Allocate Port Service[0000:00:01.0:pcie00]
Sep  1 13:53:22 ubuntu klogd: [    1.371998] Allocate Port Service[0000:00:01.0:pcie03]
Sep  1 13:53:22 ubuntu klogd: [    1.371998] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    1.371998] assign_interrupt_mode Found MSI capability
Sep  1 13:53:22 ubuntu klogd: [    1.371998] Allocate Port Service[0000:00:1c.0:pcie00]
Sep  1 13:53:22 ubuntu klogd: [    1.371998] Allocate Port Service[0000:00:1c.0:pcie02]
Sep  1 13:53:22 ubuntu klogd: [    1.371998] Allocate Port Service[0000:00:1c.0:pcie03]
Sep  1 13:53:22 ubuntu klogd: [    1.371998] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Sep  1 13:53:22 ubuntu klogd: [    1.372024] assign_interrupt_mode Found MSI capability
Sep  1 13:53:22 ubuntu klogd: [    1.372024] Allocate Port Service[0000:00:1c.4:pcie00]
Sep  1 13:53:22 ubuntu klogd: [    1.372024] Allocate Port Service[0000:00:1c.4:pcie02]
Sep  1 13:53:22 ubuntu klogd: [    1.372024] Allocate Port Service[0000:00:1c.4:pcie03]
Sep  1 13:53:22 ubuntu klogd: [    1.372024] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Sep  1 13:53:22 ubuntu klogd: [    1.372024] assign_interrupt_mode Found MSI capability
Sep  1 13:53:22 ubuntu klogd: [    1.372024] Allocate Port Service[0000:00:1c.5:pcie00]
Sep  1 13:53:22 ubuntu klogd: [    1.372025] Allocate Port Service[0000:00:1c.5:pcie02]
Sep  1 13:53:22 ubuntu klogd: [    1.372025] Allocate Port Service[0000:00:1c.5:pcie03]
Sep  1 13:53:22 ubuntu klogd: [    1.395452] Linux agpgart interface v0.103
Sep  1 13:53:22 ubuntu klogd: [    1.395452] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  1 13:53:22 ubuntu klogd: [    1.395452] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  1 13:53:22 ubuntu klogd: [    1.395452] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  1 13:53:22 ubuntu klogd: [    1.399451] brd: module loaded
Sep  1 13:53:22 ubuntu klogd: [    1.399451] input: Macintosh mouse button emulation as /class/input/input0
Sep  1 13:53:22 ubuntu klogd: [    1.399451] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Sep  1 13:53:22 ubuntu klogd: [    1.399451] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  1 13:53:22 ubuntu klogd: [    1.399451] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  1 13:53:22 ubuntu klogd: [    1.422594] mice: PS/2 mouse device common for all mice
Sep  1 13:53:22 ubuntu klogd: [    1.423451] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Sep  1 13:53:22 ubuntu klogd: [    1.423451] rtc0: alarms up to one month, y3k
Sep  1 13:53:22 ubuntu klogd: [    1.423451] cpuidle: using governor ladder
Sep  1 13:53:22 ubuntu klogd: [    1.423451] cpuidle: using governor menu
Sep  1 13:53:22 ubuntu klogd: [    1.423451] aufs 20080609
Sep  1 13:53:22 ubuntu klogd: [    1.423451] registered taskstats version 1
Sep  1 13:53:22 ubuntu klogd: [    1.423451] rtc_cmos 00:03: setting system clock to 2008-09-01 13:52:21 UTC (1220277141)
Sep  1 13:53:22 ubuntu klogd: [    1.423451] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  1 13:53:22 ubuntu klogd: [    1.423451] EDD information not available.
Sep  1 13:53:22 ubuntu klogd: [    1.423451] Freeing unused kernel memory: 408k freed
Sep  1 13:53:22 ubuntu klogd: [    1.467431] input: AT Translated Set 2 keyboard as /class/input/input1
Sep  1 13:53:22 ubuntu klogd: [    1.516830] fuse init (API version 7.9)
Sep  1 13:53:22 ubuntu klogd: [    1.534973] uvesafb: failed to execute /sbin/v86d
Sep  1 13:53:22 ubuntu klogd: [    1.535019] uvesafb: make sure that the v86d helper is installed and executable
Sep  1 13:53:22 ubuntu klogd: [    1.535057] uvesafb: Getting VBE info block failed (eax=0x4f00, err=-2)
Sep  1 13:53:22 ubuntu klogd: [    1.535098] uvesafb: vbe_init() failed with -22
Sep  1 13:53:22 ubuntu klogd: [    1.535136] uvesafb: probe of uvesafb.0 failed with error -22
Sep  1 13:53:22 ubuntu klogd: [    1.583680] ACPI: SSDT CFFC00F0, 0277 (r1 DpgPmm  P001Ist       11 INTL 20051117)
Sep  1 13:53:22 ubuntu klogd: [    1.583931] ACPI: ACPI0007:00 is registered as cooling_device0
Sep  1 13:53:22 ubuntu klogd: [    1.584250] ACPI: SSDT CFFC0580, 0277 (r1 DpgPmm  P002Ist       12 INTL 20051117)
Sep  1 13:53:22 ubuntu klogd: [    1.584477] ACPI: ACPI0007:01 is registered as cooling_device1
Sep  1 13:53:22 ubuntu klogd: [    2.045496] usbcore: registered new interface driver usbfs
Sep  1 13:53:22 ubuntu klogd: [    2.045515] usbcore: registered new interface driver hub
Sep  1 13:53:22 ubuntu klogd: [    2.047461] usbcore: registered new device driver usb
Sep  1 13:53:22 ubuntu klogd: [    2.047786] USB Universal Host Controller Interface driver v3.0
Sep  1 13:53:22 ubuntu klogd: [    2.047786] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  1 13:53:22 ubuntu klogd: [    2.047786] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    2.047786] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Sep  1 13:53:22 ubuntu klogd: [    2.047786] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Sep  1 13:53:22 ubuntu klogd: [    2.047817] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ac00
Sep  1 13:53:22 ubuntu klogd: [    2.047817] usb usb1: configuration #1 chosen from 1 choice
Sep  1 13:53:22 ubuntu klogd: [    2.047817] hub 1-0:1.0: USB hub found
Sep  1 13:53:22 ubuntu klogd: [    2.047817] hub 1-0:1.0: 2 ports detected
Sep  1 13:53:22 ubuntu klogd: [    2.119004] CPU1: Temperature above threshold, cpu clock throttled (total events = 1)
Sep  1 13:53:22 ubuntu klogd: [    2.119010] CPU0: Temperature/speed normal
Sep  1 13:53:22 ubuntu klogd: [    2.153836] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
Sep  1 13:53:22 ubuntu klogd: [    2.153845] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Sep  1 13:53:22 ubuntu klogd: [    2.153848] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Sep  1 13:53:22 ubuntu klogd: [    2.153865] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Sep  1 13:53:22 ubuntu klogd: [    2.153891] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
Sep  1 13:53:22 ubuntu klogd: [    2.153951] usb usb2: configuration #1 chosen from 1 choice
Sep  1 13:53:22 ubuntu klogd: [    2.153971] hub 2-0:1.0: USB hub found
Sep  1 13:53:22 ubuntu klogd: [    2.153976] hub 2-0:1.0: 2 ports detected
Sep  1 13:53:22 ubuntu klogd: [    2.227288] No dock devices found.
Sep  1 13:53:22 ubuntu klogd: [    2.237689] SCSI subsystem initialized
Sep  1 13:53:22 ubuntu klogd: [    2.261810] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Sep  1 13:53:22 ubuntu klogd: [    2.261810] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Sep  1 13:53:22 ubuntu klogd: [    2.261810] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Sep  1 13:53:22 ubuntu klogd: [    2.261810] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
Sep  1 13:53:22 ubuntu klogd: [    2.266575] ehci_hcd 0000:00:1a.7: debug port 1
Sep  1 13:53:22 ubuntu klogd: [    2.266580] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Sep  1 13:53:22 ubuntu klogd: [    2.266589] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
Sep  1 13:53:22 ubuntu klogd: [    2.267438] libata version 3.00 loaded.
Sep  1 13:53:22 ubuntu klogd: [    2.282412] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  1 13:53:22 ubuntu klogd: [    2.282469] usb usb3: configuration #1 chosen from 1 choice
Sep  1 13:53:22 ubuntu klogd: [    2.282490] hub 3-0:1.0: USB hub found
Sep  1 13:53:22 ubuntu klogd: [    2.282496] hub 3-0:1.0: 4 ports detected
Sep  1 13:53:22 ubuntu klogd: [    2.387655] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
Sep  1 13:53:22 ubuntu klogd: [    2.387655] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    2.387655] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep  1 13:53:22 ubuntu klogd: [    2.387655] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
Sep  1 13:53:22 ubuntu klogd: [    2.387655] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a800
Sep  1 13:53:22 ubuntu klogd: [    2.387655] usb usb4: configuration #1 chosen from 1 choice
Sep  1 13:53:22 ubuntu klogd: [    2.387655] hub 4-0:1.0: USB hub found
Sep  1 13:53:22 ubuntu klogd: [    2.387655] hub 4-0:1.0: 2 ports detected
Sep  1 13:53:22 ubuntu klogd: [    2.495155] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Sep  1 13:53:22 ubuntu klogd: [    2.495155] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Sep  1 13:53:22 ubuntu klogd: [    2.495155] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep  1 13:53:22 ubuntu klogd: [    2.495155] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
Sep  1 13:53:22 ubuntu klogd: [    2.495155] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a480
Sep  1 13:53:22 ubuntu klogd: [    2.495155] usb usb5: configuration #1 chosen from 1 choice
Sep  1 13:53:22 ubuntu klogd: [    2.495155] hub 5-0:1.0: USB hub found
Sep  1 13:53:22 ubuntu klogd: [    2.495155] hub 5-0:1.0: 2 ports detected
Sep  1 13:53:22 ubuntu klogd: [    2.599158] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Sep  1 13:53:22 ubuntu klogd: [    2.599158] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Sep  1 13:53:22 ubuntu klogd: [    2.599158] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep  1 13:53:22 ubuntu klogd: [    2.599158] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
Sep  1 13:53:22 ubuntu klogd: [    2.599158] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a400
Sep  1 13:53:22 ubuntu klogd: [    2.599158] usb usb6: configuration #1 chosen from 1 choice
Sep  1 13:53:22 ubuntu klogd: [    2.599158] hub 6-0:1.0: USB hub found
Sep  1 13:53:22 ubuntu klogd: [    2.599158] hub 6-0:1.0: 2 ports detected
Sep  1 13:53:22 ubuntu klogd: [    2.707653] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
Sep  1 13:53:22 ubuntu klogd: [    2.707653] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Sep  1 13:53:22 ubuntu klogd: [    2.707653] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Sep  1 13:53:22 ubuntu klogd: [    2.707653] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 7
Sep  1 13:53:22 ubuntu klogd: [    2.707653] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000a080
Sep  1 13:53:22 ubuntu klogd: [    2.707653] usb usb7: configuration #1 chosen from 1 choice
Sep  1 13:53:22 ubuntu klogd: [    2.707653] hub 7-0:1.0: USB hub found
Sep  1 13:53:22 ubuntu klogd: [    2.707653] hub 7-0:1.0: 2 ports detected
Sep  1 13:53:22 ubuntu klogd: [    2.815658] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
Sep  1 13:53:22 ubuntu klogd: [    2.815658] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Sep  1 13:53:22 ubuntu klogd: [    2.815658] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep  1 13:53:22 ubuntu klogd: [    2.815658] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
Sep  1 13:53:22 ubuntu klogd: [    2.819653] ehci_hcd 0000:00:1d.7: debug port 1
Sep  1 13:53:22 ubuntu klogd: [    2.819653] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Sep  1 13:53:22 ubuntu klogd: [    2.819653] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
Sep  1 13:53:22 ubuntu klogd: [    2.839653] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  1 13:53:22 ubuntu klogd: [    2.839653] usb usb8: configuration #1 chosen from 1 choice
Sep  1 13:53:22 ubuntu klogd: [    2.839653] hub 8-0:1.0: USB hub found
Sep  1 13:53:22 ubuntu klogd: [    2.839653] hub 8-0:1.0: 8 ports detected
Sep  1 13:53:22 ubuntu klogd: [    2.942736] hub 8-0:1.0: over-current change on port 7
Sep  1 13:53:22 ubuntu klogd: [    2.943653] r8169 Gigabit Ethernet driver 2.2LK loaded
Sep  1 13:53:22 ubuntu klogd: [    2.943653] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Sep  1 13:53:22 ubuntu klogd: [    2.943653] PCI: Setting latency timer of device 0000:04:00.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    2.943653] eth0: RTL8168b/8111b at 0xffffc20000c40000, 00:19:db:cc:a6:f6, XID 38000000 IRQ 2299
Sep  1 13:53:22 ubuntu klogd: [    2.943653] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 18
Sep  1 13:53:22 ubuntu klogd: [    2.999665] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
Sep  1 13:53:22 ubuntu klogd: [    3.007234] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
Sep  1 13:53:22 ubuntu klogd: [    3.007234] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  1 13:53:22 ubuntu klogd: [    3.007234] PCI: Setting latency timer of device 0000:03:00.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ahci 0000:03:00.0: version 3.0
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ahci 0000:03:00.0: controller can't do NCQ, turning off CAP_NCQ
Sep  1 13:53:22 ubuntu klogd: [    3.007234] ahci 0000:03:00.0: MV_AHCI HACK: port_map 7 -> 3
Sep  1 13:53:22 ubuntu klogd: [    3.049869] hub 8-0:1.0: over-current change on port 8
Sep  1 13:53:22 ubuntu klogd: [    4.011128] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 3 ports 3 Gbps 0x3 impl IDE mode
Sep  1 13:53:22 ubuntu klogd: [    4.011131] ahci 0000:03:00.0: flags: 64bit stag led pmp slum part 
Sep  1 13:53:22 ubuntu klogd: [    4.011137] PCI: Setting latency timer of device 0000:03:00.0 to 64
Sep  1 13:53:22 ubuntu klogd: [    4.012237] scsi0 : ahci
Sep  1 13:53:22 ubuntu klogd: [    4.013316] scsi1 : ahci
Sep  1 13:53:22 ubuntu klogd: [    4.014359] scsi2 : ahci
Sep  1 13:53:22 ubuntu klogd: [    4.014383] ata1: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd00 irq 16
Sep  1 13:53:22 ubuntu klogd: [    4.014387] ata2: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd80 irq 16
Sep  1 13:53:22 ubuntu klogd: [    4.014388] ata3: DUMMY
Sep  1 13:53:22 ubuntu klogd: [    4.278162] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00012efe60]
Sep  1 13:53:22 ubuntu klogd: [    4.498493] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  1 13:53:22 ubuntu klogd: [    4.502094] ata1.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
Sep  1 13:53:22 ubuntu klogd: [    4.502094] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
Sep  1 13:53:22 ubuntu klogd: [    4.502094] ata1.00: configured for UDMA/133
Sep  1 13:53:22 ubuntu klogd: [    4.830933] ata2: SATA link down (SStatus 0 SControl 300)
Sep  1 13:53:22 ubuntu klogd: [    4.830915] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
Sep  1 13:53:22 ubuntu klogd: [    4.830915] ata_piix 0000:00:1f.2: version 2.12
Sep  1 13:53:22 ubuntu klogd: [    4.830915] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
Sep  1 13:53:22 ubuntu klogd: [    4.830915] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Sep  1 13:53:22 ubuntu klogd: [    4.830915] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep  1 13:53:22 ubuntu klogd: [    4.830915] scsi3 : ata_piix
Sep  1 13:53:22 ubuntu klogd: [    4.830915] scsi4 : ata_piix
Sep  1 13:53:22 ubuntu klogd: [    4.831943] ata4: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 19
Sep  1 13:53:22 ubuntu klogd: [    4.831946] ata5: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 19
Sep  1 13:53:22 ubuntu klogd: [    5.305266] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  1 13:53:22 ubuntu klogd: [    5.322893] ata4.00: ATA-8: WDC WD5000AAKS-07YGA0, 12.01C02, max UDMA/133
Sep  1 13:53:22 ubuntu klogd: [    5.322893] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Sep  1 13:53:22 ubuntu klogd: [    5.334985] ata4.00: configured for UDMA/133
Sep  1 13:53:22 ubuntu klogd: [    5.839519] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Sep  1 13:53:22 ubuntu klogd: [    5.847645] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB00, max UDMA/100
Sep  1 13:53:22 ubuntu klogd: [    5.863647] ata5.00: configured for UDMA/100
Sep  1 13:53:22 ubuntu klogd: [    5.867483] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
Sep  1 13:53:22 ubuntu klogd: [    5.869302] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB00 PQ: 0 ANSI: 5
Sep  1 13:53:22 ubuntu klogd: [    5.869361] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
Sep  1 13:53:22 ubuntu klogd: [    5.869364] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Sep  1 13:53:22 ubuntu klogd: [    5.869395] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Sep  1 13:53:22 ubuntu klogd: [    5.870428] scsi5 : ata_piix
Sep  1 13:53:22 ubuntu klogd: [    5.871470] scsi6 : ata_piix
Sep  1 13:53:22 ubuntu klogd: [    5.871475] ata6: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 19
Sep  1 13:53:22 ubuntu klogd: [    5.871475] ata7: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 19
Sep  1 13:53:22 ubuntu klogd: [    6.343230] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Sep  1 13:53:22 ubuntu klogd: [    6.351358] ata6.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB00, max UDMA/100
Sep  1 13:53:22 ubuntu klogd: [    6.367352] ata6.00: configured for UDMA/100
Sep  1 13:53:22 ubuntu klogd: [    6.895477] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Sep  1 13:53:22 ubuntu klogd: [    6.907441] ata7.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
Sep  1 13:53:22 ubuntu klogd: [    6.907441] ata7.00: 488397168 sectors, multi 16: LBA48 
Sep  1 13:53:22 ubuntu klogd: [    6.915434] ata7.00: configured for UDMA/133
Sep  1 13:53:22 ubuntu klogd: [    6.918935] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB00 PQ: 0 ANSI: 5
Sep  1 13:53:22 ubuntu klogd: [    6.918935] scsi 6:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
Sep  1 13:53:22 ubuntu klogd: [    6.926231] Driver 'sd' needs updating - please use bus_type methods
Sep  1 13:53:22 ubuntu klogd: [    6.926305] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
Sep  1 13:53:22 ubuntu klogd: [    6.926317] sd 0:0:0:0: [sda] Write Protect is off
Sep  1 13:53:22 ubuntu klogd: [    6.926319] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  1 13:53:22 ubuntu klogd: [    6.926338] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  1 13:53:22 ubuntu klogd: [    6.926379] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
Sep  1 13:53:22 ubuntu klogd: [    6.926390] sd 0:0:0:0: [sda] Write Protect is off
Sep  1 13:53:22 ubuntu klogd: [    6.926392] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  1 13:53:22 ubuntu klogd: [    6.926410] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  1 13:53:22 ubuntu klogd: [    6.926413]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep  1 13:53:22 ubuntu klogd: [    6.941629]  sda1 sda2
Sep  1 13:53:22 ubuntu klogd: [    6.941708] sd 0:0:0:0: [sda] Attached SCSI disk
Sep  1 13:53:22 ubuntu klogd: [    6.942177] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Sep  1 13:53:22 ubuntu klogd: [    6.942177] sd 3:0:0:0: [sdb] Write Protect is off
Sep  1 13:53:22 ubuntu klogd: [    6.942177] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep  1 13:53:22 ubuntu klogd: [    6.942177] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  1 13:53:22 ubuntu klogd: [    6.942177] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Sep  1 13:53:22 ubuntu klogd: [    6.942177] sd 3:0:0:0: [sdb] Write Protect is off
Sep  1 13:53:22 ubuntu klogd: [    6.942177] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep  1 13:53:22 ubuntu klogd: [    6.942177] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  1 13:53:22 ubuntu klogd: [    6.942177]  sdb: sdb1 sdb2 sdb3
Sep  1 13:53:22 ubuntu klogd: [    6.945585] sd 3:0:0:0: [sdb] Attached SCSI disk
Sep  1 13:53:22 ubuntu klogd: [    6.945759] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
Sep  1 13:53:22 ubuntu klogd: [    6.945771] sd 6:0:0:0: [sdc] Write Protect is off
Sep  1 13:53:22 ubuntu klogd: [    6.945773] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Sep  1 13:53:22 ubuntu klogd: [    6.945793] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  1 13:53:22 ubuntu klogd: [    6.945833] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
Sep  1 13:53:22 ubuntu klogd: [    6.945845] sd 6:0:0:0: [sdc] Write Protect is off
Sep  1 13:53:22 ubuntu klogd: [    6.945846] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Sep  1 13:53:22 ubuntu klogd: [    6.945866] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  1 13:53:22 ubuntu klogd: [    6.945868]  sdc:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep  1 13:53:22 ubuntu klogd: [    6.949187] Uniform CD-ROM driver Revision: 3.20
Sep  1 13:53:22 ubuntu klogd: [    6.949234] sr 4:0:0:0: Attached scsi CD-ROM sr0
Sep  1 13:53:22 ubuntu klogd: [    6.953708] sr1: scsi3-mmc drive: 32x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Sep  1 13:53:22 ubuntu klogd: [    6.953753] sr 5:0:0:0: Attached scsi CD-ROM sr1
Sep  1 13:53:22 ubuntu klogd: [    6.962357]  sdc1 sdc2 sdc3 sdc4
Sep  1 13:53:22 ubuntu klogd: [    6.962446] sd 6:0:0:0: [sdc] Attached SCSI disk
Sep  1 13:53:22 ubuntu klogd: [    6.967969] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  1 13:53:22 ubuntu klogd: [    6.967969] sd 3:0:0:0: Attached scsi generic sg1 type 0
Sep  1 13:53:22 ubuntu klogd: [    6.967969] sr 4:0:0:0: Attached scsi generic sg2 type 5
Sep  1 13:53:22 ubuntu klogd: [    6.967969] sr 5:0:0:0: Attached scsi generic sg3 type 5
Sep  1 13:53:22 ubuntu klogd: [    6.967969] sd 6:0:0:0: Attached scsi generic sg4 type 0
Sep  1 13:53:22 ubuntu klogd: [    8.100381] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    8.101748] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    8.136381] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    8.136381] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    8.176381] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    8.176381] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    8.204381] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    8.204381] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    8.238647] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    8.239895] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    8.326647] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    8.328105] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    8.358647] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    8.360105] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    8.378647] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    8.378647] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    9.453514] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    9.453522] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    9.474746] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    9.477271] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    9.493900] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    9.493900] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    9.505072] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    9.505072] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    9.517072] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    9.517072] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    9.545072] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    9.545072] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    9.553073] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    9.553073] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    9.560928] kjournald starting.  Commit interval 5 seconds
Sep  1 13:53:22 ubuntu klogd: [    9.560928] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 13:53:22 ubuntu klogd: [    9.857627] ISO 9660 Extensions: Microsoft Joliet Level 3
Sep  1 13:53:22 ubuntu klogd: [    9.882464] ISO 9660 Extensions: RRIP_1991A
Sep  1 13:53:22 ubuntu klogd: [   10.152271] loop: module loaded
Sep  1 13:53:22 ubuntu klogd: [   10.390917] squashfs: version 3.3 (2007/10/31) Phillip Lougher
Sep  1 13:53:22 ubuntu klogd: [   58.531070] udevd version 124 started
Sep  1 13:53:22 ubuntu klogd: [   59.781833] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  1 13:53:22 ubuntu klogd: [   59.942717] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  1 13:53:22 ubuntu klogd: [   60.096002] iTCO_vendor_support: vendor-support=0
Sep  1 13:53:22 ubuntu klogd: [   60.096742] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Sep  1 13:53:22 ubuntu klogd: [   60.096803] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0860)
Sep  1 13:53:22 ubuntu klogd: [   60.096832] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Sep  1 13:53:22 ubuntu klogd: [   60.856957] Linux video capture interface: v2.00
Sep  1 13:53:22 ubuntu klogd: [   60.970022] input: Power Button (FF) as /class/input/input2
Sep  1 13:53:22 ubuntu klogd: [   60.986002] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Sep  1 13:53:22 ubuntu klogd: [   60.986023] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Sep  1 13:53:22 ubuntu klogd: [   61.017275] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Sep  1 13:53:22 ubuntu klogd: [   61.030499] ACPI: Power Button (FF) [PWRF]
Sep  1 13:53:22 ubuntu klogd: [   61.030593] input: Power Button (CM) as /class/input/input3
Sep  1 13:53:22 ubuntu klogd: [   61.091293] ACPI: Power Button (CM) [PWRB]
Sep  1 13:53:22 ubuntu klogd: [   61.134382] ivtv:  Start initialization, version 1.3.0
Sep  1 13:53:22 ubuntu klogd: [   61.134382] ivtv0: Initializing card #0
Sep  1 13:53:22 ubuntu klogd: [   61.134382] ivtv0: Autodetected Hauppauge card (cx23415 based)
Sep  1 13:53:22 ubuntu klogd: [   61.142262] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  1 13:53:22 ubuntu klogd: [   61.194361] tveeprom 0-0050: Hauppauge model 48139, rev K2B7, serial# 9978285
Sep  1 13:53:22 ubuntu klogd: [   61.194361] tveeprom 0-0050: tuner model is Philips FM1216ME MK5 (idx 117, type 38)
Sep  1 13:53:22 ubuntu klogd: [   61.194361] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
Sep  1 13:53:22 ubuntu klogd: [   61.194361] tveeprom 0-0050: audio processor is MSP4418 (idx 25)
Sep  1 13:53:22 ubuntu klogd: [   61.194361] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
Sep  1 13:53:22 ubuntu klogd: [   61.194361] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
Sep  1 13:53:22 ubuntu klogd: [   61.194361] ivtv0: Autodetected Hauppauge WinTV PVR-350
Sep  1 13:53:22 ubuntu klogd: [   61.840519] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
Sep  1 13:53:22 ubuntu klogd: [   61.958481] input: ImExPS/2 Logitech MX Mouse as /class/input/input4
Sep  1 13:53:22 ubuntu klogd: [   62.033152] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
Sep  1 13:53:22 ubuntu klogd: [   62.041354] msp3400 0-0040: MSP4418G-B3 found @ 0x80 (ivtv i2c driver #0)
Sep  1 13:53:22 ubuntu klogd: [   62.041356] msp3400 0-0040: msp3400 supports nicam and radio, mode is autodetect and autoselect
Sep  1 13:53:22 ubuntu klogd: [   62.097476] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
Sep  1 13:53:22 ubuntu klogd: [   62.113476] tda9887 0-0043: creating new instance
Sep  1 13:53:22 ubuntu klogd: [   62.113476] tda9887 0-0043: tda988[5/6/7] found
Sep  1 13:53:22 ubuntu klogd: [   62.113476] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Sep  1 13:53:22 ubuntu klogd: [   62.153635] tuner-simple 0-0061: creating new instance
Sep  1 13:53:22 ubuntu klogd: [   62.153635] tuner-simple 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Registered device video0 for encoder MPG (4096 kB)
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Registered device video32 for encoder YUV (2048 kB)
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Registered device video24 for encoder PCM (320 kB)
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Registered device radio0 for encoder radio
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Registered device video16 for decoder MPG (1024 kB)
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Registered device vbi8 for decoder VBI (64 kB)
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Registered device vbi16 for decoder VOUT
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Registered device video48 for decoder YUV (1024 kB)
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv0: Initialized card #0: Hauppauge WinTV PVR-350
Sep  1 13:53:22 ubuntu klogd: [   62.171347] ivtv:  End initialization
Sep  1 13:53:22 ubuntu klogd: [   63.529376] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep  1 13:53:23 ubuntu klogd: [   66.776158] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: Found user 'avahi' (UID 107) and group 'avahi' (GID 119).
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: Successfully dropped root privileges.
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: avahi-daemon 0.6.23 starting up.
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: Successfully called chroot().
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: Successfully dropped remaining capabilities.
Sep  1 13:53:23 ubuntu avahi-daemon[6925]: chroot.c: open() failed: No such file or directory
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: Failed to open /etc/resolv.conf: Invalid argument
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: No service file found in /etc/avahi/services.
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: Network interface enumeration completed.
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep  1 13:53:23 ubuntu avahi-daemon[6924]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3128088163.
Sep  1 13:53:23 ubuntu klogd: [   66.930371] parport_pc 00:07: reported by Plug and Play ACPI
Sep  1 13:53:23 ubuntu klogd: [   66.930415] parport0: PC-style at 0x378, irq 7 [PCSPP]
Sep  1 13:53:23 ubuntu klogd: [   67.022735] lp0: using parport0 (interrupt-driven).
Sep  1 13:53:23 ubuntu klogd: [   67.082733] ppdev: user-space parallel port driver
Sep  1 13:53:27 ubuntu acpid: client connected from 7121[109:121] 
Sep  1 13:53:28 ubuntu klogd: [   71.855601] firmware: requesting v4l-cx2341x-enc.fw
Sep  1 13:53:28 ubuntu klogd: [   72.702075] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Sep  1 13:53:28 ubuntu klogd: [   72.702075] firmware: requesting v4l-cx2341x-dec.fw
Sep  1 13:53:28 ubuntu klogd: [   72.718076] ivtv0: Loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
Sep  1 13:53:29 ubuntu klogd: [   72.918076] ivtv0: Encoder revision: 0x02060039
Sep  1 13:53:29 ubuntu klogd: [   72.918076] ivtv0: Decoder revision: 0x02020023
Sep  1 13:53:29 ubuntu klogd: [   72.972980] firmware: requesting v4l-cx2341x-init.mpg
Sep  1 13:53:29 ubuntu klogd: [   73.013855] ivtv0: Loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
Sep  1 13:53:30 ubuntu hcid[7204]: Bluetooth HCI daemon
Sep  1 13:53:30 ubuntu klogd: [   74.005283] Bluetooth: Core ver 2.11
Sep  1 13:53:30 ubuntu klogd: [   74.005759] NET: Registered protocol family 31
Sep  1 13:53:30 ubuntu klogd: [   74.005759] Bluetooth: HCI device and connection manager initialized
Sep  1 13:53:30 ubuntu klogd: [   74.005759] Bluetooth: HCI socket layer initialized
Sep  1 13:53:30 ubuntu hcid[7204]: Parsing /etc/bluetooth/main.conf failed: No such file or directory
Sep  1 13:53:30 ubuntu hcid[7204]: Starting SDP server
Sep  1 13:53:30 ubuntu klogd: [   74.094015] Bluetooth: L2CAP ver 2.9
Sep  1 13:53:30 ubuntu klogd: [   74.094016] Bluetooth: L2CAP socket layer initialized
Sep  1 13:53:30 ubuntu hcid[7204]: Unix socket created: 11
Sep  1 13:53:30 ubuntu klogd: [   74.252690] Bluetooth: RFCOMM socket layer initialized
Sep  1 13:53:30 ubuntu hcid[7204]: Registered manager path:/org/bluez/audio
Sep  1 13:53:30 ubuntu klogd: [   74.252690] Bluetooth: RFCOMM TTY layer initialized
Sep  1 13:53:30 ubuntu klogd: [   74.252690] Bluetooth: RFCOMM ver 1.8

```

hardrives and dvd-burners (as they appear in my hardy install)
> 
scsi-1ATA_WDC_WD5000AAKS-07YGA0_WD-WCAS81806883 -> ../../sda 
scsi-1ATA_WDC_WD2500KS-00MJB0_WD-WMANK1339323 -> ../../sdb 
scsi-1ATA_ST3160021A_5JS0LPH1 -> ../../sdc 
scsi-1ATA_SAMSUNG_HD103UJ_S13PJ1BQ717775 -> ../../sde 
scsi-1ATA_Maxtor_6Y200P0_Y63L2XTE -> ../../sdd 
 
and 2 TSSTcorp CDDVDW SH-S203B (/dev/scd0 +scd1 


mother bord is a msi p35 neo

---

### Post by Nullack on 2008-09-01
Synch to the main repo for updates and see if you still replicate the bug

---

### Post by of_darkness on 2008-09-01
> **Nullack said:**
> Synch to the main repo for updates and see if you still replicate the bug

well can try to do it later when my partion rearingement is finiched.. 

but dosent changes 2 xorg nead a reboot? wich is obviusly imposimple and keeping the updates.. but i shall try..

is their any other packages bisedes xorg and casper that i nead 2 update that can be affected by this bug?

btw i reported it [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/263745](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/263745) to when awayting a response here..

---

### Post by of_darkness on 2008-09-02
> **Nullack said:**
> Synch to the main repo for updates and see if you still replicate the bug

updated the live cd but no diffrence.

---

### Post by of_darkness on 2008-09-04
the problem does not exist in my installed intrepid env. only on alpha 4 live cd(have not tested later versions)

---

