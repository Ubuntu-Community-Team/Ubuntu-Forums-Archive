---
title: "My USB has died - no mouse and USB modem anymore"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by sander marechal on 2005-03-30
Hello all,

For some reason I do not understand my USB has died under Ubuntu. That means no mouse and no internet access for me (I have an USB modem). I have no clue what could have caused this. All I did yesterday was install a small script to enable numlock on startup (see [this guide entry](http://www.ubuntuguide.org/#onnumlockgnome)).

I have posted my kern.log below and highlighted the parts I think are relevant, though I could be wrong (total linux newbie here... sorry).

Please help!

> 
Mar 30 23:00:08 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Mar 30 23:00:08 localhost kernel: Inspecting /boot/System.map-2.6.8.1-5-386
Mar 30 23:00:09 localhost kernel: Loaded 28212 symbols from /boot/System.map-2.6.8.1-5-386.
Mar 30 23:00:09 localhost kernel: Symbols match kernel version 2.6.8.
Mar 30 23:00:09 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Mar 30 23:00:09 localhost kernel: Linux version 2.6.8.1-5-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Mon Mar 14 21:44:04 UTC 2005
Mar 30 23:00:09 localhost kernel: BIOS-provided physical RAM map:
Mar 30 23:00:09 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Mar 30 23:00:09 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Mar 30 23:00:09 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 30 23:00:09 localhost kernel:  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
Mar 30 23:00:09 localhost kernel:  BIOS-e820: 0000000007ff0000 - 0000000007ff3000 (ACPI NVS)
Mar 30 23:00:09 localhost kernel:  BIOS-e820: 0000000007ff3000 - 0000000008000000 (ACPI data)
Mar 30 23:00:09 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Mar 30 23:00:09 localhost kernel: 127MB LOWMEM available.
Mar 30 23:00:09 localhost kernel: On node 0 totalpages: 32752
Mar 30 23:00:09 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Mar 30 23:00:09 localhost kernel:   Normal zone: 28656 pages, LIFO batch:6
Mar 30 23:00:09 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Mar 30 23:00:09 localhost kernel: DMI 2.0 present.
Mar 30 23:00:09 localhost kernel: ACPI disabled because your bios is from 00 and too old
Mar 30 23:00:09 localhost kernel: You can enable it with acpi=force
Mar 30 23:00:09 localhost kernel: Built 1 zonelists
Mar 30 23:00:09 localhost kernel: Kernel command line: root=/dev/hde3 ro quiet splash
Mar 30 23:00:09 localhost kernel: Local APIC disabled by BIOS -- reenabling.
Mar 30 23:00:09 localhost kernel: Found and enabled local APIC!
Mar 30 23:00:09 localhost kernel: Initializing CPU#0
Mar 30 23:00:09 localhost kernel: PID hash table entries: 512 (order 9: 4096 bytes)
Mar 30 23:00:09 localhost kernel: Detected 601.371 MHz processor.
Mar 30 23:00:09 localhost kernel: Using tsc for high-res timesource
Mar 30 23:00:09 localhost kernel: Console: colour VGA+ 80x25
Mar 30 23:00:09 localhost kernel: Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 30 23:00:09 localhost kernel: Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Mar 30 23:00:09 localhost kernel: Memory: 122604k/131008k available (1337k kernel code, 7856k reserved, 731k data, 204k init, 0k highmem)
Mar 30 23:00:09 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Mar 30 23:00:09 localhost kernel: Calibrating delay loop... 1183.74 BogoMIPS
Mar 30 23:00:09 localhost kernel: Security Scaffold v1.0.0 initialized
Mar 30 23:00:09 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Mar 30 23:00:09 localhost kernel: CPU: After generic identify, caps: 0387fbff 00000000 00000000 00000000
Mar 30 23:00:09 localhost kernel: CPU: After vendor identify, caps:  0387fbff 00000000 00000000 00000000
Mar 30 23:00:09 localhost kernel: CPU: L1 I cache: 16K, L1 D cache: 16K
Mar 30 23:00:09 localhost kernel: CPU: L2 cache: 256K
Mar 30 23:00:09 localhost kernel: CPU serial number disabled.
Mar 30 23:00:09 localhost kernel: CPU: After all inits, caps:        0383fbff 00000000 00000000 00000040
Mar 30 23:00:09 localhost kernel: CPU: Intel Pentium III (Coppermine) stepping 01
Mar 30 23:00:09 localhost kernel: Enabling fast FPU save and restore... done.
Mar 30 23:00:09 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Mar 30 23:00:09 localhost kernel: Checking 'hlt' instruction... OK.
Mar 30 23:00:09 localhost kernel: Checking for popad bug... OK.
Mar 30 23:00:09 localhost kernel: enabled ExtINT on CPU#0
Mar 30 23:00:09 localhost kernel: ESR value before enabling vector: 00000000
Mar 30 23:00:09 localhost kernel: ESR value after enabling vector: 00000000
Mar 30 23:00:09 localhost kernel: Using local APIC timer interrupts.
Mar 30 23:00:09 localhost kernel: calibrating APIC timer ...
Mar 30 23:00:09 localhost kernel: ..... CPU clock speed is 601.0263 MHz.
Mar 30 23:00:09 localhost kernel: ..... host bus clock speed is 133.0614 MHz.
Mar 30 23:00:09 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Mar 30 23:00:09 localhost kernel: Freeing initrd memory: 4136k freed
Mar 30 23:00:09 localhost kernel: NET: Registered protocol family 16
Mar 30 23:00:09 localhost kernel: EISA bus registered
Mar 30 23:00:09 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfb0a0, last bus=1
Mar 30 23:00:09 localhost kernel: PCI: Using configuration type 1
Mar 30 23:00:09 localhost kernel: mtrr: v2.0 (20020519)
Mar 30 23:00:09 localhost kernel: ACPI: Subsystem revision 20040816
Mar 30 23:00:09 localhost kernel: ACPI: Interpreter disabled.
Mar 30 23:00:09 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 30 23:00:09 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Mar 30 23:00:09 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fbcd0
Mar 30 23:00:09 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbcf8, dseg 0xf0000
Mar 30 23:00:09 localhost kernel: PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
Mar 30 23:00:09 localhost kernel: PCI: Probing PCI hardware
Mar 30 23:00:09 localhost kernel: PCI: Probing PCI hardware (bus 00)
Mar 30 23:00:09 localhost kernel: PCI: Using IRQ router VIA [1106/0596] at 0000:00:07.0
Mar 30 23:00:09 localhost kernel: VFS: Disk quotas dquot_6.5.1
Mar 30 23:00:09 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 30 23:00:09 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Mar 30 23:00:09 localhost kernel: devfs: boot_options: 0x0
Mar 30 23:00:09 localhost kernel: Initializing Cryptographic API
Mar 30 23:00:09 localhost kernel: Activating ISA DMA hang workarounds.
Mar 30 23:00:09 localhost kernel: isapnp: Scanning for PnP cards...
Mar 30 23:00:09 localhost kernel: isapnp: No Plug & Play device found
Mar 30 23:00:09 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Mar 30 23:00:09 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 30 23:00:09 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Mar 30 23:00:09 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 30 23:00:09 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 30 23:00:09 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Mar 30 23:00:09 localhost kernel: EISA: Probing bus 0 at eisa0
Mar 30 23:00:09 localhost kernel: EISA: Detected 0 cards.
Mar 30 23:00:09 localhost kernel: NET: Registered protocol family 2
Mar 30 23:00:09 localhost kernel: IP: routing cache hash table of 512 buckets, 4Kbytes
Mar 30 23:00:09 localhost kernel: TCP: Hash tables configured (established 8192 bind 16384)
Mar 30 23:00:09 localhost kernel: NET: Registered protocol family 8
Mar 30 23:00:09 localhost kernel: NET: Registered protocol family 20
Mar 30 23:00:09 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Mar 30 23:00:09 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H
|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Mar 30 23:00:09 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Mar 30 23:00:09 localhost kernel: Freeing unused kernel memory: 204k freed
Mar 30 23:00:09 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Mar 30 23:00:09 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Mar 30 23:00:09 localhost kernel: NET: Registered protocol family 1
Mar 30 23:00:09 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Mar 30 23:00:09 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Mar 30 23:00:09 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:07.1
Mar 30 23:00:09 localhost kernel: VP_IDE: chipset revision 6
Mar 30 23:00:09 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Mar 30 23:00:09 localhost kernel: VP_IDE: VIA vt82c596b (rev 12) IDE UDMA66 controller on pci0000:00:07.1
Mar 30 23:00:09 localhost kernel:     ide0: BM-DMA at 0xa000-0xa007, BIOS settings: hda:DMA, hdb:DMA
Mar 30 23:00:09 localhost kernel:     ide1: BM-DMA at 0xa008-0xa00f, BIOS settings: hdc:DMA, hdd:DMA
Mar 30 23:00:09 localhost kernel: hda: Maxtor 53073U6, ATA DISK drive
Mar 30 23:00:09 localhost kernel: Using anticipatory io scheduler
Mar 30 23:00:09 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Mar 30 23:00:09 localhost kernel: hda: max request size: 128KiB
Mar 30 23:00:09 localhost kernel: hda: 60030432 sectors (30735 MB) w/2048KiB Cache, CHS=59554/16/63, UDMA(33)
Mar 30 23:00:09 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1
Mar 30 23:00:09 localhost kernel: hdc: SAMSUNG DVD-ROM SD-608, ATAPI CD/DVD-ROM drive
Mar 30 23:00:09 localhost kernel: hdd: PHILIPS DVDR885P, ATAPI CD/DVD-ROM drive
Mar 30 23:00:09 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Mar 30 23:00:09 localhost kernel: CMD649: IDE controller at PCI slot 0000:00:12.0
Mar 30 23:00:09 localhost kernel: PCI: Found IRQ 3 for device 0000:00:12.0
Mar 30 23:00:09 localhost kernel: CMD649: chipset revision 2
Mar 30 23:00:09 localhost kernel: CMD649: ROM enabled at 0xee000000
Mar 30 23:00:09 localhost kernel: CMD649: 100%% native mode on irq 3
Mar 30 23:00:09 localhost kernel:     ide2: BM-DMA at 0xc000-0xc007, BIOS settings: hde:pio, hdf:pio
Mar 30 23:00:09 localhost kernel:     ide3: BM-DMA at 0xc008-0xc00f, BIOS settings: hdg:pio, hdh:pio
Mar 30 23:00:09 localhost kernel: hde: WDC WD800JB-00JJA0, ATA DISK drive
Mar 30 23:00:09 localhost kernel: ide2 at 0xb000-0xb007,0xb402 on irq 3
Mar 30 23:00:09 localhost kernel: hde: max request size: 128KiB
Mar 30 23:00:09 localhost kernel: hde: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(33)
Mar 30 23:00:09 localhost kernel:  /dev/ide/host2/bus0/target0/lun0: p1 p2 p3 p4
Mar 30 23:00:09 localhost kernel: kjournald starting.  Commit interval 5 seconds
Mar 30 23:00:09 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Mar 30 23:00:09 localhost kernel: Adding 499960k swap on /dev/hde2.  Priority:-1 extents:1
Mar 30 23:00:09 localhost kernel: EXT3 FS on hde3, internal journal
Mar 30 23:00:09 localhost kernel: input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
Mar 30 23:00:09 localhost kernel: mice: PS/2 mouse device common for all mice
Mar 30 23:00:09 localhost kernel: ts: Compaq touchscreen protocol output
Mar 30 23:00:09 localhost kernel: hdc: ATAPI 32X DVD-ROM drive, 512kB Cache, DMA
Mar 30 23:00:09 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Mar 30 23:00:09 localhost kernel: hdd: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Mar 30 23:00:09 localhost kernel: parport: PnPBIOS parport detected.
Mar 30 23:00:09 localhost kernel: parport0: PC-style at 0x278 (0x678), irq 5, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Mar 30 23:00:09 localhost kernel: parport0: faking semi-colon
Mar 30 23:00:09 localhost kernel: parport0: Printer, HEWLETT-PACKARD DESKJET 710C
Mar 30 23:00:09 localhost kernel: lp0: using parport0 (interrupt-driven).
Mar 30 23:00:09 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Mar 30 23:00:09 localhost kernel: PPP generic driver version 2.4.2
Mar 30 23:00:09 localhost kernel: nvidia: module license 'NVIDIA' taints kernel.
Mar 30 23:00:09 localhost kernel: NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-6111  Tue Jul 27 07:55:38 PDT 2004
Mar 30 23:00:09 localhost kernel: Capability LSM initialized
Mar 30 23:00:09 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Mar 30 23:00:09 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Mar 30 23:00:09 localhost kernel: cdrom: open failed.
Mar 30 23:00:09 localhost last message repeated 2 times
Mar 30 23:00:09 localhost kernel: kjournald starting.  Commit interval 5 seconds
Mar 30 23:00:09 localhost kernel: EXT3 FS on hde1, internal journal
Mar 30 23:00:09 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Mar 30 23:00:09 localhost kernel: Real Time Clock Driver v1.12
Mar 30 23:00:09 localhost kernel: input: PC Speaker
Mar 30 23:00:09 localhost kernel: inserting floppy driver for 2.6.8.1-5-386
Mar 30 23:00:09 localhost kernel: Floppy drive(s): fd0 is 1.44M
Mar 30 23:00:09 localhost kernel: FDC 0 is a post-1991 82077
Mar 30 23:00:09 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Mar 30 23:00:09 localhost kernel: agpgart: Detected VIA Apollo Pro 133 chipset
Mar 30 23:00:09 localhost kernel: agpgart: Maximum main memory to use for agp memory: 94M
Mar 30 23:00:09 localhost kernel: agpgart: AGP aperture is 64M @ 0xe8000000
[COLOR=Red][B]Mar 30 23:00:09 localhost kernel: usbcore: registered new driver usbfs
Mar 30 23:00:09 localhost kernel: usbcore: registered new driver hub
Mar 30 23:00:09 localhost kernel: USB Universal Host Controller Interface driver v2.2
Mar 30 23:00:09 localhost kernel: uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Mar 30 23:00:09 localhost kernel: uhci_hcd 0000:00:07.2: irq 10, io base 0000a400
Mar 30 23:00:09 localhost kernel: uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Mar 30 23:00:09 localhost kernel: hub 1-0:1.0: USB hub found
Mar 30 23:00:09 localhost kernel: hub 1-0:1.0: 2 ports detected
Mar 30 23:00:09 localhost kernel: usb 1-1: new full speed USB device using address 2
Mar 30 23:00:09 localhost kernel: usbcore: registered new driver speedtch
Mar 30 23:00:09 localhost kernel: usb 1-2: new full speed USB device using address 3
Mar 30 23:00:09 localhost kernel: hub 1-2:1.0: USB hub found
Mar 30 23:00:09 localhost kernel: hub 1-2:1.0: 4 ports detected
Mar 30 23:00:09 localhost kernel: usb 1-2.1: new full speed USB device using address 4
Mar 30 23:00:09 localhost kernel: usb 1-2.3: new low speed USB device using address 5
Mar 30 23:00:09 localhost kernel: PCI: Found IRQ 11 for device 0000:00:0e.0
Mar 30 23:00:09 localhost kernel: usbcore: registered new driver hiddev
Mar 30 23:00:09 localhost kernel: input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:07.2-2.3
Mar 30 23:00:09 localhost kernel: usbcore: registered new driver usbhid
Mar 30 23:00:09 localhost kernel: drivers/usb/input/hid-core.c: v2.0:USB HID core driver
[/B][/COLOR]Mar 30 23:00:09 localhost kernel: Linux Tulip driver version 1.1.13 (May 11, 2002)
Mar 30 23:00:09 localhost kernel: PCI: Found IRQ 7 for device 0000:00:14.0
Mar 30 23:00:09 localhost kernel: PCI: Sharing IRQ 7 with 0000:00:10.0
Mar 30 23:00:09 localhost kernel: tulip0:  EEPROM default media type Autosense.
Mar 30 23:00:09 localhost kernel: tulip0:  Index #0 - Media MII (#11) described by a 21140 MII PHY (1) block.
Mar 30 23:00:09 localhost kernel: tulip0:  MII transceiver #1 config 1100 status 7809 advertising 01e1.
Mar 30 23:00:09 localhost kernel: eth0: ASIX AX88140 rev 3 at 0xc400, 00:40:95:4A:1A:81, IRQ 7.
Mar 30 23:00:09 localhost kernel: NET: Registered protocol family 17
Mar 30 23:00:10 localhost kernel: lp0: ECP mode
Mar 30 23:00:14 localhost kernel: NET: Registered protocol family 10
Mar 30 23:00:14 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Mar 30 23:00:14 localhost kernel: IPv6 over IPv4 tunneling driver
Mar 30 23:00:14 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Mar 30 23:00:14 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
[COLOR=Red][B]Mar 30 23:00:17 localhost kernel: usb 1-2.3: control timeout on ep0in
Mar 30 23:00:22 localhost kernel: usb 1-2.3: control timeout on ep0in
Mar 30 23:00:23 localhost kernel: hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
Mar 30 23:00:23 localhost kernel: usb 1-2: USB disconnect, address 3
Mar 30 23:00:23 localhost kernel: usb 1-2.1: USB disconnect, address 4
Mar 30 23:00:23 localhost kernel: usb 1-2.3: USB disconnect, address 5
Mar 30 23:00:23 localhost kernel: usb 1-1: usbfs: interface 1 claimed while 'modem_run' sets config #1
Mar 30 23:00:23 localhost kernel: usb 1-1: usbfs: interface 2 claimed while 'modem_run' sets config #1
Mar 30 23:00:23 localhost kernel: usb 1-2: new full speed USB device using address 6
[/B][/COLOR]Mar 30 23:00:24 localhost kernel: eth0: no IPv6 routers present
[COLOR=Red][B]Mar 30 23:00:28 localhost kernel: usb 1-1: control timeout on ep0out
Mar 30 23:00:28 localhost kernel: usb 1-2: control timeout on ep0out
Mar 30 23:00:33 localhost kernel: usb 1-1: control timeout on ep0out
Mar 30 23:00:33 localhost kernel: usb 1-2: control timeout on ep0out
Mar 30 23:00:34 localhost kernel: usb 1-2: device not accepting address 6, error -110
Mar 30 23:00:34 localhost kernel: usb 1-2: new full speed USB device using address 7
Mar 30 23:00:36 localhost kernel: NVRM: not using NVAGP, AGPGART is loaded!!
Mar 30 23:00:37 localhost kernel: NVRM: not using NVAGP, AGPGART is loaded!!
Mar 30 23:00:39 localhost kernel: usb 1-2: control timeout on ep0out
Mar 30 23:00:44 localhost kernel: usb 1-2: control timeout on ep0out
Mar 30 23:00:44 localhost kernel: usb 1-2: device not accepting address 7, error -110
Mar 30 23:00:49 localhost kernel: usb 1-1: control timeout on ep0in
Mar 30 23:01:20 localhost last message repeated 6 times
Mar 30 23:02:21 localhost last message repeated 12 times
Mar 30 23:02:47 localhost last message repeated 5 times[/B][/COLOR]


---

### Post by soul_rebel on 2005-03-31
any kernel or bios change recently? If not I suggest to try a newer kernel (from hoary perhaps)

---

### Post by sander marechal on 2005-03-31
[QUOTE=soul_rebel]any kernel or bios change recently? If not I suggest to try a newer kernel (from hoary perhaps)[/QUOTE]
 Nope. No changes at all.  Even stranger: I invited a friend of mine to take a look at it and today everything went perfect somehow. Yesterday it didn't (despite several reboots). The only thing that could possibly be different between yesterday and today is that yesterday I did "restart computer" from Win98SE and selected Ubuntu in the grub menu upon reboot, where as today I didn't came from Win98 but went straight to Ubuntu on todays first boot up.

Theoretically that can't make a difference though but we all know MS's weird ways...

---

### Post by soul_rebel on 2005-03-31
It sometimes happens. I think it is a bios fault. For example if reboot in FreeBSD it has problem with the onboard lan. Everything it's ok if I do a "cold boot" of the machine directly in freebsd. Also today windows somehow managed to leave my pc extremely slow after the reboot, with problems in loading Ubuntu... weird things...
Let's see if it just depends on that. Bye

---

### Post by emmort on 2005-04-12
I have the same kind of problem, I see the same message on the syslog file, irq x rejected.
The difference is that it never works. (direct or from W98  )

I use the Kubuntu 5.04, Hoary. I installed it on saturday, four day ago and I don't find the solution until now.

I made some change on the acpi but no succes.

(previously, i used Mandrake 10.1, mepis ans Kaella-azur without any problem with the usb) 

Despite this problem, Kubuntu is a very good distri. I really want to find the bug to enjoy it fully.

Emmort

---

