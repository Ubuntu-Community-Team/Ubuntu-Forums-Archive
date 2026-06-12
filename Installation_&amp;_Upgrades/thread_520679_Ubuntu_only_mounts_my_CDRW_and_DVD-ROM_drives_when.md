---
title: "Ubuntu only mounts my CDRW and DVD-ROM drives when it feels like it"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by GadgetsGuy on 2007-08-08
The  title pretty much sums it up

since installing Ubuntu fresh a couple days ago I seem to be doing alot more bitching and complaining than I should be ... :(

Ubuntu only mounts my CDRW and DVD_ROM drives every so many reboots ... whenever it is in the mood to do so ...

My computer is of no good to me without my drives ...

How can I have them mount EVERY TIME I REBOOT ... what's the secret code?

I LOVE Ubuntu when it works properly ... but as of lately that has not been too much

It would be a real shame to have to abandon Ubuntu and return to that evil place called Micro$oft ...   :(

Somebody please save me from this fate!!!

---

### Post by MrObvious on 2007-08-08
What happens when you mount it manually? (sudo mount /dev/hd* or /dev/sd*)

Post a syslog please. (cat /var/log/syslog I think is the exact path)

---

### Post by GadgetsGuy on 2007-08-08
No joy with either command  :(

```
blackie@blackie:~$ sudo mount /dev/hd*
Password:
mount: can't find /dev/hd* in /etc/fstab or /etc/mtab
blackie@blackie:~$ sudo mount /dev/sd*
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

---

### Post by GadgetsGuy on 2007-08-08
here is the syslog

```
Aug  8 13:14:12 blackie kernel: [   27.901912] NET: Registered protocol family 16
Aug  8 13:14:12 blackie kernel: [   27.902054] EISA bus registered
Aug  8 13:14:12 blackie kernel: [   27.902061] ACPI: bus type pci registered
Aug  8 13:14:12 blackie kernel: [   27.902668] PCI: PCI BIOS revision 2.10 entry at 0xfd98d, last bus=2
Aug  8 13:14:12 blackie kernel: [   27.902671] PCI: Using configuration type 1
Aug  8 13:14:12 blackie kernel: [   27.902674] Setting up standard PCI resources
Aug  8 13:14:12 blackie kernel: [   27.922341] ACPI: Interpreter enabled
Aug  8 13:14:12 blackie kernel: [   27.922347] ACPI: Using IOAPIC for interrupt routing
Aug  8 13:14:12 blackie kernel: [   27.924052] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  8 13:14:12 blackie kernel: [   27.924059] PCI: Probing PCI hardware (bus 00)
Aug  8 13:14:12 blackie kernel: [   27.926003] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Aug  8 13:14:12 blackie kernel: [   27.926005] * this clock source is slow. If you are sure your timer does not have
Aug  8 13:14:12 blackie kernel: [   27.926007] * this bug, please use "acpi_pm_good" to disable the workaround
Aug  8 13:14:12 blackie kernel: [   27.926067] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Aug  8 13:14:12 blackie kernel: [   27.926072] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
Aug  8 13:14:12 blackie kernel: [   27.926399] Boot video device is 0000:01:00.0
Aug  8 13:14:12 blackie kernel: [   27.926543] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
Aug  8 13:14:12 blackie kernel: [   27.926705] PCI: Transparent bridge - 0000:00:1e.0
Aug  8 13:14:12 blackie kernel: [   27.926744] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug  8 13:14:12 blackie kernel: [   28.007449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
Aug  8 13:14:12 blackie kernel: [   28.010030] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Aug  8 13:14:12 blackie kernel: [   28.010358] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Aug  8 13:14:12 blackie kernel: [   28.010660] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Aug  8 13:14:12 blackie kernel: [   28.010962] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Aug  8 13:14:12 blackie kernel: [   28.011281] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Aug  8 13:14:12 blackie kernel: [   28.011598] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Aug  8 13:14:12 blackie kernel: [   28.011907] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Aug  8 13:14:12 blackie kernel: [   28.012218] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Aug  8 13:14:12 blackie kernel: [   28.036761] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Aug  8 13:14:12 blackie kernel: [   28.037089] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug  8 13:14:12 blackie kernel: [   28.037111] pnp: PnP ACPI init
Aug  8 13:14:12 blackie kernel: [   28.081475] pnp: PnP ACPI: found 13 devices
Aug  8 13:14:12 blackie kernel: [   28.081482] PnPBIOS: Disabled by ACPI PNP
Aug  8 13:14:12 blackie kernel: [   28.081579] PCI: Using ACPI for IRQ routing
Aug  8 13:14:12 blackie kernel: [   28.081584] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug  8 13:14:12 blackie kernel: [   28.087497] NET: Registered protocol family 8
Aug  8 13:14:12 blackie kernel: [   28.087501] NET: Registered protocol family 20
Aug  8 13:14:12 blackie kernel: [   28.088493] PCI: Bridge: 0000:00:01.0
Aug  8 13:14:12 blackie kernel: [   28.088496]   IO window: disabled.
Aug  8 13:14:12 blackie kernel: [   28.088504]   MEM window: c2000000-c3ffffff
Aug  8 13:14:12 blackie kernel: [   28.088510]   PREFETCH window: e0000000-e60fffff
Aug  8 13:14:12 blackie kernel: [   28.088517] PCI: Bridge: 0000:00:1e.0
Aug  8 13:14:12 blackie kernel: [   28.088522]   IO window: 2000-2fff
Aug  8 13:14:12 blackie kernel: [   28.088529]   MEM window: c4000000-c40fffff
Aug  8 13:14:12 blackie kernel: [   28.088535]   PREFETCH window: disabled.
Aug  8 13:14:12 blackie kernel: [   28.088558] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Aug  8 13:14:12 blackie kernel: [   28.088604] NET: Registered protocol family 2
Aug  8 13:14:12 blackie kernel: [   28.098495] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug  8 13:14:12 blackie kernel: [   28.098808] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Aug  8 13:14:12 blackie kernel: [   28.101239] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
Aug  8 13:14:12 blackie kernel: [   28.102621] TCP: Hash tables configured (established 131072 bind 65536)
Aug  8 13:14:12 blackie kernel: [   28.102629] TCP reno registered
Aug  8 13:14:12 blackie kernel: [   28.105614] checking if image is initramfs... it is
Aug  8 13:14:12 blackie kernel: [   28.961577] Freeing initrd memory: 6910k freed
Aug  8 13:14:12 blackie kernel: [   28.961893] Simple Boot Flag at 0x6c set to 0x1
Aug  8 13:14:12 blackie kernel: [   28.962255] audit: initializing netlink socket (disabled)
Aug  8 13:14:12 blackie kernel: [   28.962279] audit(1186578713.853:1): initialized
Aug  8 13:14:12 blackie kernel: [   28.962537] VFS: Disk quotas dquot_6.5.1
Aug  8 13:14:12 blackie kernel: [   28.962572] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug  8 13:14:12 blackie kernel: [   28.962649] io scheduler noop registered
Aug  8 13:14:12 blackie kernel: [   28.962654] io scheduler anticipatory registered
Aug  8 13:14:12 blackie kernel: [   28.962658] io scheduler deadline registered
Aug  8 13:14:12 blackie kernel: [   28.962712] io scheduler cfq registered (default)
Aug  8 13:14:12 blackie kernel: [   28.963233] isapnp: Scanning for PnP cards...
Aug  8 13:14:12 blackie kernel: [   29.319778] isapnp: No Plug & Play device found
Aug  8 13:14:12 blackie kernel: [   29.360108] Real Time Clock Driver v1.12ac
Aug  8 13:14:12 blackie kernel: [   29.360188] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug  8 13:14:12 blackie kernel: [   29.360340] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  8 13:14:12 blackie kernel: [   29.360592] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Aug  8 13:14:12 blackie kernel: [   29.361551] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  8 13:14:12 blackie kernel: [   29.361990] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Aug  8 13:14:12 blackie kernel: [   29.362346] mice: PS/2 mouse device common for all mice
Aug  8 13:14:12 blackie kernel: [   29.363295] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug  8 13:14:12 blackie kernel: [   29.363534] input: Macintosh mouse button emulation as /class/input/input0
Aug  8 13:14:12 blackie kernel: [   29.363596] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug  8 13:14:12 blackie kernel: [   29.363602] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug  8 13:14:12 blackie kernel: [   29.364020] PNP: No PS/2 controller found. Probing ports directly.
Aug  8 13:14:12 blackie kernel: [   29.365602] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  8 13:14:12 blackie kernel: [   29.365683] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug  8 13:14:12 blackie kernel: [   29.365795] EISA: Probing bus 0 at eisa.0
Aug  8 13:14:12 blackie kernel: [   29.365806] Cannot allocate resource for EISA slot 1
Aug  8 13:14:12 blackie kernel: [   29.365811] Cannot allocate resource for EISA slot 2
Aug  8 13:14:12 blackie kernel: [   29.365882] EISA: Detected 0 cards.
Aug  8 13:14:12 blackie kernel: [   29.395990] TCP cubic registered
Aug  8 13:14:12 blackie kernel: [   29.396002] NET: Registered protocol family 1
Aug  8 13:14:12 blackie kernel: [   29.396035] Using IPI No-Shortcut mode
Aug  8 13:14:12 blackie kernel: [   29.396128] ACPI: (supports<6>Time: tsc clocksource has been installed.
Aug  8 13:14:12 blackie kernel: [   29.396145]  S0 S1 S3 S4 S5)
Aug  8 13:14:12 blackie kernel: [   29.396206]   Magic number: 3:606:179
Aug  8 13:14:12 blackie kernel: [   29.396295]   hash matches device ttyr5
Aug  8 13:14:12 blackie kernel: [   29.397016] Freeing unused kernel memory: 328k freed
Aug  8 13:14:12 blackie kernel: [   30.704732] Capability LSM initialized
Aug  8 13:14:12 blackie kernel: [   30.764431] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug  8 13:14:12 blackie kernel: [   30.766549] ACPI: Thermal Zone [THM0] (58 C)
Aug  8 13:14:12 blackie kernel: [   31.540941] usbcore: registered new interface driver usbfs
Aug  8 13:14:12 blackie kernel: [   31.540975] usbcore: registered new interface driver hub
Aug  8 13:14:12 blackie kernel: [   31.541014] usbcore: registered new device driver usb
Aug  8 13:14:12 blackie kernel: [   31.542470] USB Universal Host Controller Interface driver v3.0
Aug  8 13:14:12 blackie kernel: [   31.542545] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug  8 13:14:12 blackie kernel: [   31.542561] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Aug  8 13:14:12 blackie kernel: [   31.542566] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug  8 13:14:12 blackie kernel: [   31.542752] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Aug  8 13:14:12 blackie kernel: [   31.542785] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Aug  8 13:14:12 blackie kernel: [   31.542940] usb usb1: configuration #1 chosen from 1 choice
Aug  8 13:14:12 blackie kernel: [   31.542981] hub 1-0:1.0: USB hub found
Aug  8 13:14:12 blackie kernel: [   31.542993] hub 1-0:1.0: 2 ports detected
Aug  8 13:14:12 blackie kernel: [   31.643843] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Aug  8 13:14:12 blackie kernel: [   31.643861] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Aug  8 13:14:12 blackie kernel: [   31.643867] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug  8 13:14:12 blackie kernel: [   31.643905] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Aug  8 13:14:12 blackie kernel: [   31.643938] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Aug  8 13:14:12 blackie kernel: [   31.644070] usb usb2: configuration #1 chosen from 1 choice
Aug  8 13:14:12 blackie kernel: [   31.644113] hub 2-0:1.0: USB hub found
Aug  8 13:14:12 blackie kernel: [   31.644124] hub 2-0:1.0: 2 ports detected
Aug  8 13:14:12 blackie kernel: [   31.659516] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
Aug  8 13:14:12 blackie kernel: [   31.659521] e100: Copyright(c) 1999-2006 Intel Corporation
Aug  8 13:14:12 blackie kernel: [   31.745883] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Aug  8 13:14:12 blackie kernel: [   31.745900] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Aug  8 13:14:12 blackie kernel: [   31.745906] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug  8 13:14:12 blackie kernel: [   31.745940] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Aug  8 13:14:12 blackie kernel: [   31.745977] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Aug  8 13:14:12 blackie kernel: [   31.746111] usb usb3: configuration #1 chosen from 1 choice
Aug  8 13:14:12 blackie kernel: [   31.746158] hub 3-0:1.0: USB hub found
Aug  8 13:14:12 blackie kernel: [   31.746171] hub 3-0:1.0: 2 ports detected
Aug  8 13:14:12 blackie kernel: [   31.794189] Floppy drive(s): fd0 is 1.44M
Aug  8 13:14:12 blackie kernel: [   31.847250] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Aug  8 13:14:12 blackie kernel: [   31.847275] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Aug  8 13:14:12 blackie kernel: [   31.847281] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug  8 13:14:12 blackie kernel: [   31.847322] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Aug  8 13:14:12 blackie kernel: [   31.847374] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Aug  8 13:14:12 blackie kernel: [   31.847388] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xc0000000
Aug  8 13:14:12 blackie kernel: [   31.848702] usb 1-2: new full speed USB device using uhci_hcd and address 2
Aug  8 13:14:12 blackie kernel: [   31.851258] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug  8 13:14:12 blackie kernel: [   31.851385] usb usb4: configuration #1 chosen from 1 choice
Aug  8 13:14:12 blackie kernel: [   31.851425] hub 4-0:1.0: USB hub found
Aug  8 13:14:12 blackie kernel: [   31.851440] hub 4-0:1.0: 6 ports detected
Aug  8 13:14:12 blackie kernel: [   31.855713] FDC 0 is a post-1991 82077
Aug  8 13:14:12 blackie kernel: [   31.962369] SCSI subsystem initialized
Aug  8 13:14:12 blackie kernel: [   31.971139] libata version 2.20 loaded.
Aug  8 13:14:12 blackie kernel: [   31.973525] ata_piix 0000:00:1f.1: version 2.10ac1
Aug  8 13:14:12 blackie kernel: [   31.973545] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Aug  8 13:14:12 blackie kernel: [   31.973555] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Aug  8 13:14:12 blackie kernel: [   31.973581] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Aug  8 13:14:12 blackie kernel: [   31.973663] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
Aug  8 13:14:12 blackie kernel: [   31.973717] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
Aug  8 13:14:12 blackie kernel: [   31.973750] scsi0 : ata_piix
Aug  8 13:14:12 blackie kernel: [   32.128380] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
Aug  8 13:14:12 blackie kernel: [   32.128386] ata1.00: ATA-5: IC35L040AVVN07-0, VA2OAF1A, max UDMA/100
Aug  8 13:14:12 blackie kernel: [   32.128391] ata1.00: 78156288 sectors, multi 16: LBA 
Aug  8 13:14:12 blackie kernel: [   32.132368] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
Aug  8 13:14:12 blackie kernel: [   32.132372] ata1.00: configured for UDMA/100
Aug  8 13:14:12 blackie kernel: [   32.132391] scsi1 : ata_piix
Aug  8 13:14:12 blackie kernel: [   32.597964] usb 1-2: new full speed USB device using uhci_hcd and address 3
Aug  8 13:14:12 blackie kernel: [   32.756174] usb 1-2: configuration #1 chosen from 1 choice
Aug  8 13:14:12 blackie kernel: [   32.759135] hub 1-2:1.0: USB hub found
Aug  8 13:14:12 blackie kernel: [   32.762070] hub 1-2:1.0: 4 ports detected
Aug  8 13:14:12 blackie kernel: [   32.765300] ata2.00: ATAPI, max UDMA/66
Aug  8 13:14:12 blackie kernel: [   32.765304] ata2.01: ATAPI, max UDMA/33
Aug  8 13:14:12 blackie kernel: [   32.765313] ata2.00: limited to UDMA/33 due to 40-wire cable
Aug  8 13:14:12 blackie kernel: [   32.936308] ata2.00: configured for UDMA/33
Aug  8 13:14:12 blackie kernel: [   33.075126] usb 2-1: new full speed USB device using uhci_hcd and address 2
Aug  8 13:14:12 blackie kernel: [   33.248771] usb 2-1: configuration #1 chosen from 1 choice
Aug  8 13:14:12 blackie kernel: [   33.268516] usbcore: registered new interface driver hiddev
Aug  8 13:14:12 blackie kernel: [   33.287079] input: Logitech USB Receiver as /class/input/input1
Aug  8 13:14:12 blackie kernel: [   33.287115] input: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1
Aug  8 13:14:12 blackie kernel: [   33.290118] input: Logitech USB Receiver as /class/input/input2
Aug  8 13:14:12 blackie kernel: [   33.290500] input,hiddev96: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
Aug  8 13:14:12 blackie kernel: [   33.290535] usbcore: registered new interface driver usbhid
Aug  8 13:14:12 blackie kernel: [   33.290541] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Aug  8 13:14:12 blackie kernel: [   62.893579] ata2.01: qc timeout (cmd 0xef)
Aug  8 13:14:12 blackie kernel: [   62.893592] ata2.01: failed to set xfermode (err_mask=0x4)
Aug  8 13:14:12 blackie kernel: [   62.893599] ata2: failed to recover some devices, retrying in 5 secs
Aug  8 13:14:12 blackie kernel: [   68.688812] ata2.00: configured for UDMA/33
Aug  8 13:14:12 blackie kernel: [   98.646088] ata2.01: qc timeout (cmd 0xef)
Aug  8 13:14:12 blackie kernel: [   98.646100] ata2.01: failed to set xfermode (err_mask=0x4)
Aug  8 13:14:12 blackie kernel: [   98.646109] ata2.01: limiting speed to UDMA/33:PIO3
Aug  8 13:14:12 blackie kernel: [   98.646112] ata2: failed to recover some devices, retrying in 5 secs
Aug  8 13:14:12 blackie kernel: [  104.441322] ata2.00: configured for UDMA/33
Aug  8 13:14:12 blackie kernel: [  134.398596] ata2.01: qc timeout (cmd 0xef)
Aug  8 13:14:12 blackie kernel: [  134.398609] ata2.01: failed to set xfermode (err_mask=0x4)
Aug  8 13:14:12 blackie kernel: [  134.398615] ata2.01: disabled
Aug  8 13:14:12 blackie kernel: [  134.398619] ata2: failed to recover some devices, retrying in 5 secs
Aug  8 13:14:12 blackie kernel: [  139.392351] ata2.00: failed to set xfermode (err_mask=0x40)
Aug  8 13:14:12 blackie kernel: [  139.392359] ata2: failed to recover some devices, retrying in 5 secs
Aug  8 13:14:12 blackie kernel: [  145.034529] ata2.00: configured for UDMA/33
Aug  8 13:14:12 blackie kernel: [  145.034722] scsi 0:0:0:0: Direct-Access     ATA      IC35L040AVVN07-0 VA2O PQ: 0 ANSI: 5
Aug  8 13:14:12 blackie kernel: [  145.042845] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8160B 0009 PQ: 0 ANSI: 5
Aug  8 13:14:12 blackie kernel: [  145.049829] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
Aug  8 13:14:12 blackie kernel: [  145.073171] e100: eth0: e100_probe: addr 0xc4010000, irq 20, MAC addr 00:09:6B:26:C3:44
Aug  8 13:14:12 blackie kernel: [  145.102141] SCSI device sda: 78156288 512-byte hdwr sectors (40016 MB)
Aug  8 13:14:12 blackie kernel: [  145.103186] sda: Write Protect is off
Aug  8 13:14:12 blackie kernel: [  145.103191] sda: Mode Sense: 00 3a 00 00
Aug  8 13:14:12 blackie kernel: [  145.104345] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  8 13:14:12 blackie kernel: [  145.104813] SCSI device sda: 78156288 512-byte hdwr sectors (40016 MB)
Aug  8 13:14:12 blackie kernel: [  145.104833] sda: Write Protect is off
Aug  8 13:14:12 blackie kernel: [  145.104837] sda: Mode Sense: 00 3a 00 00
Aug  8 13:14:12 blackie kernel: [  145.104867] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  8 13:14:12 blackie kernel: [  145.104871]  sda: sda1 sda2 sda3 < sda5 sda6 >
Aug  8 13:14:12 blackie kernel: [  145.178386] sd 0:0:0:0: Attached scsi disk sda
Aug  8 13:14:12 blackie kernel: [  145.185514] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug  8 13:14:12 blackie kernel: [  145.185672] sr 1:0:0:0: Attached scsi generic sg1 type 5
Aug  8 13:14:12 blackie kernel: [  145.213374] sr0: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
Aug  8 13:14:12 blackie kernel: [  145.213382] Uniform CD-ROM driver Revision: 3.20
Aug  8 13:14:12 blackie kernel: [  145.213704] sr 1:0:0:0: Attached scsi CD-ROM sr0
Aug  8 13:14:12 blackie kernel: [  145.582040] Attempting manual resume
Aug  8 13:14:12 blackie kernel: [  145.582045] swsusp: Resume From Partition 8:6
Aug  8 13:14:12 blackie kernel: [  145.582048] PM: Checking swsusp image.
Aug  8 13:14:12 blackie kernel: [  145.582261] PM: Resume from disk failed.
Aug  8 13:14:12 blackie kernel: [  145.617911] kjournald starting.  Commit interval 5 seconds
Aug  8 13:14:12 blackie kernel: [  145.617928] EXT3-fs: mounted filesystem with ordered data mode.
Aug  8 13:14:12 blackie kernel: [  153.563389] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Aug  8 13:14:12 blackie kernel: [  154.066550] NET: Registered protocol family 10
Aug  8 13:14:12 blackie kernel: [  154.066714] lo: Disabled Privacy Extensions
Aug  8 13:14:12 blackie kernel: [  155.979479] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  8 13:14:12 blackie kernel: [  156.000514] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  8 13:14:12 blackie kernel: [  156.208168] intel_rng: Firmware space is locked read-only. If you can't or
Aug  8 13:14:12 blackie kernel: [  156.208171] intel_rng: don't want to disable this in firmware setup, and if
Aug  8 13:14:12 blackie kernel: [  156.208173] intel_rng: you are certain that your system has a functional
Aug  8 13:14:12 blackie kernel: [  156.208175] intel_rng: RNG, try using the 'no_fwh_detect' option.
Aug  8 13:14:12 blackie kernel: [  156.708432] Linux agpgart interface v0.102 (c) Dave Jones
Aug  8 13:14:12 blackie kernel: [  156.709078] iTCO_vendor_support: vendor-support=0
Aug  8 13:14:12 blackie kernel: [  156.710571] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Aug  8 13:14:12 blackie kernel: [  156.710729] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x1060)
Aug  8 13:14:12 blackie kernel: [  156.710784] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Aug  8 13:14:12 blackie kernel: [  156.832303] input: PC Speaker as /class/input/input3
Aug  8 13:14:12 blackie kernel: [  156.922496] agpgart: Detected an Intel 845G Chipset.
Aug  8 13:14:12 blackie kernel: [  156.926563] agpgart: AGP aperture is 64M @ 0xd0000000
Aug  8 13:14:12 blackie kernel: [  157.289627] nvidia: module license 'NVIDIA' taints kernel.
Aug  8 13:14:12 blackie kernel: [  157.576173] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug  8 13:14:12 blackie kernel: [  157.576579] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
Aug  8 13:14:12 blackie kernel: [  157.932166] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
Aug  8 13:14:12 blackie kernel: [  157.932204] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Aug  8 13:14:12 blackie kernel: [  158.018816] parport: PnPBIOS parport detected.
Aug  8 13:14:12 blackie kernel: [  158.018888] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Aug  8 13:14:12 blackie kernel: [  158.243916] intel8x0_measure_ac97_clock: measured 50977 usecs
Aug  8 13:14:12 blackie kernel: [  158.243922] intel8x0: clocking to 48000
Aug  8 13:14:12 blackie kernel: [  158.485589] fuse init (API version 7.8)
Aug  8 13:14:12 blackie kernel: [  158.521291] lp0: using parport0 (interrupt-driven).
Aug  8 13:14:12 blackie kernel: [  158.567521] Adding 2008084k swap on /dev/disk/by-uuid/711a63ad-6c94-4b7f-803a-c02926b994ae.  Priority:-1 extents:1 across:2008084k
Aug  8 13:14:12 blackie kernel: [  158.776874] EXT3 FS on sda5, internal journal
Aug  8 13:14:12 blackie kernel: [  161.209824] NET: Registered protocol family 17
Aug  8 13:14:12 blackie kernel: [  164.531113] eth0: no IPv6 routers present
Aug  8 13:14:12 blackie kernel: [  165.575069] ibm_acpi: ec object not found
Aug  8 13:14:12 blackie kernel: [  165.607533] No dock devices found.
Aug  8 13:14:12 blackie kernel: [  165.720714] input: Power Button (FF) as /class/input/input4
Aug  8 13:14:12 blackie kernel: [  165.727057] ACPI: Power Button (FF) [PWRF]
Aug  8 13:14:12 blackie kernel: [  165.783772] input: Power Button (CM) as /class/input/input5
Aug  8 13:14:12 blackie kernel: [  165.790109] ACPI: Power Button (CM) [PWRB]
Aug  8 13:14:12 blackie kernel: [  165.823263] Using specific hotkey driver
Aug  8 13:14:12 blackie kernel: [  166.015746] pcc_acpi: loading...
Aug  8 13:14:13 blackie dhcdbd: Started up.
Aug  8 13:14:13 blackie NetworkManager: <information>^Istarting... 
Aug  8 13:14:13 blackie avahi-daemon[8024]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Aug  8 13:14:13 blackie avahi-daemon[8024]: Successfully dropped root privileges.
Aug  8 13:14:13 blackie avahi-daemon[8024]: avahi-daemon 0.6.17 starting up.
Aug  8 13:14:13 blackie avahi-daemon[8024]: Successfully called chroot().
Aug  8 13:14:13 blackie avahi-daemon[8024]: Successfully dropped remaining capabilities.
Aug  8 13:14:13 blackie avahi-daemon[8024]: No service found in /etc/avahi/services.
Aug  8 13:14:13 blackie avahi-daemon[8024]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.100.
Aug  8 13:14:13 blackie avahi-daemon[8024]: New relevant interface eth0.IPv4 for mDNS.
Aug  8 13:14:13 blackie avahi-daemon[8024]: Network interface enumeration completed.
Aug  8 13:14:13 blackie avahi-daemon[8024]: Registering new address record for fe80::209:6bff:fe26:c344 on eth0.*.
Aug  8 13:14:13 blackie avahi-daemon[8024]: Registering new address record for 192.168.0.100 on eth0.IPv4.
Aug  8 13:14:13 blackie avahi-daemon[8024]: Registering HINFO record with values 'I686'/'LINUX'.
Aug  8 13:14:14 blackie avahi-daemon[8024]: Server startup complete. Host name is blackie.local. Local service cookie is 3547491078.
Aug  8 13:14:15 blackie kernel: [  169.988114] ppdev: user-space parallel port driver
Aug  8 13:14:15 blackie kernel: [  170.183335] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Aug  8 13:14:15 blackie kernel: [  170.183552] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Aug  8 13:14:15 blackie kernel: [  170.183753] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Aug  8 13:14:16 blackie hpiod: 1.7.3 accepting connections at 2208... 
Aug  8 13:14:16 blackie kernel: [  171.511321] IBM machine detected. Enabling interrupts during APM calls.
Aug  8 13:14:16 blackie kernel: [  171.511724] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug  8 13:14:16 blackie kernel: [  171.511990] apm: overridden by ACPI.
Aug  8 13:14:16 blackie kernel: [  171.682185] Non-volatile memory driver v1.2
Aug  8 13:14:16 blackie kernel: [  171.711702] input: /usr/sbin/thinkpad-keys as /class/input/input6
Aug  8 13:14:17 blackie NetworkManager: <debug info>^I[1186593257.005717] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Aug  8 13:14:17 blackie anacron[8295]: Anacron 2.3 started on 2007-08-08
Aug  8 13:14:17 blackie anacron[8295]: Normal exit (0 jobs run)
Aug  8 13:14:17 blackie /usr/sbin/cron[8322]: (CRON) INFO (pidfile fd = 3)
Aug  8 13:14:17 blackie /usr/sbin/cron[8323]: (CRON) STARTUP (fork ok)
Aug  8 13:14:17 blackie /usr/sbin/cron[8323]: (CRON) INFO (Running @reboot jobs)
Aug  8 13:14:28 blackie gconfd (blackie-8474): starting (version 2.18.0.1), pid 8474 user 'blackie'
Aug  8 13:14:29 blackie gconfd (blackie-8474): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  8 13:14:29 blackie gconfd (blackie-8474): Resolved address "xml:readwrite:/home/blackie/.gconf" to a writable configuration source at position 1
Aug  8 13:14:29 blackie gconfd (blackie-8474): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  8 13:14:29 blackie gconfd (blackie-8474): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  8 13:14:29 blackie gconfd (blackie-8474): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  8 13:14:34 blackie Synergy 1.3.1: NOTE: synergys.cpp,500: started server
Aug  8 13:14:35 blackie gconfd (blackie-8474): Resolved address "xml:readwrite:/home/blackie/.gconf" to a writable configuration source at position 0
Aug  8 13:14:40 blackie NetworkManager: <information>^IUpdating allowed wireless network lists. 
Aug  8 13:14:40 blackie NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug  8 13:15:36 blackie Synergy 1.3.1: NOTE: CClientListener.cpp,127: accepted client connection
Aug  8 13:15:36 blackie Synergy 1.3.1: NOTE: CServer.cpp,277: client "copperxp" has connected
Aug  8 13:17:01 blackie /USR/SBIN/CRON[8669]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  8 13:34:11 blackie -- MARK --
Aug  8 13:54:11 blackie -- MARK --

```

---

### Post by GadgetsGuy on 2007-08-09
Bumping for an answer ...

---

### Post by p-stone on 2007-08-19
Similar issue here, I can't think what exactly I would have done different as it worked for a period of time before crapping out. The difference is that I can mount and unmount the CD/DVD manually. Also, when I press the eject button on the physical drive, if I have not unmounted it first I will get an error message that I do not have permission to eject WDEXTHD, which is my external hard drive. Any assistance would be appreciated

---

### Post by s3a on 2007-08-19
Try "sudo mount -a" to mount and then enter password as requested.
To unmount stuff, use "sudo umount -a".

I'm new to Ubuntu as well, so I'm not sure, but I hope this works for you!

P.S.
Type those commands in the terminal....obviously.

---

### Post by p-stone on 2007-08-20
s3a - I can already mount from the terminal fine. The issue I have is with having to do it manually at all. Normally you shouldn't have to put in any commands to mount or unmount a CD. Thanks for trying though.

---

### Post by s3a on 2007-08-20
What about shutting down your pc with Hibernation mode? That should preserve mount...I THINK.

---

### Post by p-stone on 2007-08-20
s3a- 
Couple problems with that. First of all, and I hate to be nit picky here, I'm looking for an actual solution, not a hack. The other big issue is that I have a habit of wanting to use more than one CD or DVD per session and I find it frustrating to have to manually unmount and mount each disk, rather than just pushing the button on the drive and swapping disks as you'd expect to. The first time after a reboot it always loads the disk properly but I really can't see myself rebooting every time I swap out a disk. Once again thanks for your efforts but I'm going to have to keep looking.

---

### Post by pt123 on 2007-09-28
If you are getting failed to set xfermode on older CD drives try this solution:
[http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)

In grub, “…at the end of this new menu item add it as an argument to the line:
```

# defoptions=quiet splash irqpoll

```


You just need to ad `irqpoll` to your grub line. So in so in /boot/grub/menu.lst I added irqpoll to the kernel line:
```

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=495b ro quiet splash irqpoll

```

---

### Post by emmanuel.brasil on 2008-03-03
Yo guys, looking for some help too. I try to google and spent some time looking for a lot of posts at some linux forums! I have one cdrom player and one dvdrw at the same PC. They both appear at nautilus at the tree but none mount form clicking at the icons. A error message appears "mount: special device /dev/hdd does not exist". The wierd is that the cd player mount automaticlly and works fine when I insert a CD in it, and also another icon appears at desktop.... the dvdrw does not. When a I insert a DVD in it, iturns a bit and nothing else happens. Ive tryed to mount it manually with the terminal command but the error message is the same!

After a while I found out that I can mount the dvdrw and use it normally when and I boot wiht any cd in the cd palyer and any dvd in the dvdrw. At this session everything works fine (k3b, vlc, mplayer ...), booting wiht the cd player empty or both of them empty is just like frustrating.

I try to find any configuration to auto mount but so far everything that I could find was allready configured as it was supposed to!

Any tip to this annoyance?

Best regards to all

---

