---
title: "raid5 volume created in dapper, not detected with gutsy live CD"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Randall on 2008-01-14
Hi,

I have an up-to-date dapper system with a raid5 volume. I created the volume a while back with mdadm and it is autodetected by the kernel when booting dapper.

I am considering upgrading to gutsy, however when I booted with the gutsy live CD the volume is not detected. Searching forums and bugs only turns up [this bug]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/133773"), but I'm not sure it is the same thing.

I'm wondering if anyone has encountered this problem and might know how to fix it. I can supply full dmesg outputs etc if that helps, some snippets below.

Cheers,
Randall.


from dapper boot:
...
[17179604.332000] raid5: automatically using best checksumming function: pIII_sse
[17179604.352000]    pIII_sse  :  3788.000 MB/sec
[17179604.352000] raid5: using function: pIII_sse (3788.000 MB/sec)
[17179604.352000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179604.352000] md: bitmap version 4.39
[17179604.352000] md: raid5 personality registered as nr 4
[17179604.540000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179604.700000] md: md0 stopped.
[17179604.732000] usbcore: registered new driver hiddev
[17179604.748000] input: Logitech Optical USB Mouse as /class/input/input1
[17179604.748000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
[17179604.748000] usbcore: registered new driver usbhid
[17179604.748000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179604.788000] md: bind<hdh1>
[17179604.796000] md: bind<hdi1>
[17179604.796000] md: bind<hdk1>
[17179604.804000] md: bind<hdl1>
[17179604.804000] md: bind<hdg1>
[17179604.804000] raid5: device hdg1 operational as raid disk 0
[17179604.804000] raid5: device hdl1 operational as raid disk 4
[17179604.804000] raid5: device hdk1 operational as raid disk 3
[17179604.804000] raid5: device hdi1 operational as raid disk 2
[17179604.804000] raid5: device hdh1 operational as raid disk 1
...


from gutsy boot:
... at the end of detecting disks...
[   67.383488] scsi 5:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-104  1.30 PQ: 0 ANSI: 5
[   67.383580] scsi 5:0:0:0: Attached scsi generic sg6 type 5
[   67.383626] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   67.383646] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 19
[   67.383687] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   67.383746] scsi6 : ata_piix
[   67.383815] scsi7 : ata_piix
[   67.383943] ata7: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e802 bmdma 0x0001dc00 irq 19
[   67.383948] ata8: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x0001dc08 irq 19
[   67.713958] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 19
[   67.713974] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   67.731858] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   67.731865] Uniform CD-ROM driver Revision: 3.20
[   67.732175] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   67.867483] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:07:e9:55:60:6a
[   68.051076] end_request: I/O error, dev fd0, sector 0
[   68.122113] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 1920 not in group (block 0)!
[   68.122121] EXT2-fs: group descriptors corrupted!
[   68.133022] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   68.133094] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[   68.424583] EXT2-fs: sde1: couldn't mount because of unsupported optional features (4000000).
[   68.491282] kjournald starting.  Commit interval 5 seconds
[   68.491294] EXT3-fs: mounted filesystem with ordered data mode.
[   68.511001] kjournald starting.  Commit interval 5 seconds
[   68.511011] EXT3-fs: mounted filesystem with ordered data mode.
...
and then it finished up mounting real ext3 paritions and finishes up...

---

### Post by Randall on 2008-01-22
OK, so I found the solution to my own problem. I'll post it for posterity.

main point: raids don't get detected without the mdadm package installed.

For the live cd, you can install the mdadm package (after setting up the network if necessary), then auto-detect the raid volume using 'sudo mdadm -A /dev/md0'. (Where /dev/md0 will be the first raid volume, /dev/md1 the second etc.) After that you can mount it as a normal partition with mount.

After installing Gutsy properly onto the hard disk, I installed the mdadm package and the raid volume was automatically detected on reboot.

---

