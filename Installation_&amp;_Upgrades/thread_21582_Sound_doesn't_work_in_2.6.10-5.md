---
title: "Sound doesn't work in 2.6.10-5"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by cyu021 on 2005-03-22
I just upgraded to 2.6.10-5-386 from 2.6.10-4-386 yesterday, my sound used to be working all right. I didn't notice anything unusual after the upgrade (I didn't reboot immediately). I also watched a few movies after the  upgrade with xine. When it got late, I shutdown my laptop and had a nice sleep. However, I woke up this morning and found the sound somehow doesn't work in 2.6.10-5 !!! It says something like codec can't be loaded into register blah blah blah, is anyone facing the same problem? This is my dmesg:

```

Subsystem revision 20050211
spurious 8259A interrupt: IRQ7.
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
ACPI: Embedded Controller [EC0] (gpe 29)
ACPI: Power Resource [PFN0] (off)
ACPI: Power Resource [PFN1] (off)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 9 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** Routing PCI interrupts for all devices because "pci=routeirq"
** was specified.  If this was required to make a driver work,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
PCI: setting IRQ 6 as level-triggered
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1f.3[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:02:06.2[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:02:06.3[A] -> GSI 10 (level, low) -> IRQ 10
pnp: 00:03: ioport range 0x164e-0x164f has been reserved
Simple Boot Flag at 0x37 set to 0x1
audit: initializing netlink socket (disabled)
audit(1111571065.850:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 10 (level, low) -> IRQ 10
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
    ACPI-0405: *** Error: Handler for [EmbeddedControl] returned AE_TIME
    ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.LPC0.EC0_._Q20] (Node c147f140), AE_TIME
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
Cannot allocate resource for EISA slot 3
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
GLAN MPCI T394 MDM0 USB1 USB2 USB3 
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4372KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Fan [FAN0] (off)
ACPI: Fan [FAN1] (off)
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THRM] (55 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 6 (level, low) -> IRQ 6
ICH4: chipset revision 3
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: TOSHIBA MK6025GAS, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 >
Probing IDE interface ide1...
hdc: UJDA760 DVD/CDRW, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory...  -\|/done (457 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1164672k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 5.9
 Sensor: 18
 new absolute packet format
 Touchpad has extended capability bits
 -> 4 multi-buttons, i.e. besides standard buttons
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio4
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 6 (level, low) -> IRQ 6
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
b44.c:v0.95 (Aug 3, 2004)
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 6 (level, low) -> IRQ 6
eth0: Broadcom 4400 10/100BaseT Ethernet 00:c0:9f:6e:35:bb
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 10 (level, low) -> IRQ 10
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Radio Frequency Kill Switch is On:
Kill switch must be turned off for wireless networking to work.
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 6 (level, low) -> IRQ 6
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 6, io base 0x1800
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 6 (level, low) -> IRQ 6
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 6, io base 0x1820
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 6 (level, low) -> IRQ 6
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 6, io base 0x1840
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
b44: eth0: Link is down.
b44: eth0: Link is up at 100 Mbps, full duplex.
b44: eth0: Flow control is on for TX and on for RX.
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 10 (level, low) -> IRQ 10
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 10, pci mem 0xd0000000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 855GM Chipset.
agpgart: Maximum main memory to use for agp memory: 438M
agpgart: AGP aperture is 256M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
hw_random: cannot enable RNG, aborting
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49728 usecs
intel8x0: clocking to 48000
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:00:1f.6 to 64
Unable to initialize codec #0
Intel ICH Modem: probe of 0000:00:1f.6 failed with error -13
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Enabling device 0000:02:06.0 (0104 -> 0106)
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:02:06.0 [1025:0064]
Yenta: ISA IRQ mask 0x08b8, PCI irq 10
Socket status: 30000006
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:06.2[A] -> GSI 10 (level, low) -> IRQ 10
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d020a000-d020a7ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f0000342034]
eth1394: $Rev: 1224 $ Ben Collins <bcollins@debian.org>
eth1394: eth2: IEEE-1394 IPv4 over 1394 Ethernet (fw-host0)
Real Time Clock Driver v1.12
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
codec_write 0: semaphore is not ready for register 0x2
codec_write 0: semaphore is not ready for register 0x2
codec_write 0: semaphore is not ready for register 0x4
codec_write 0: semaphore is not ready for register 0x4
codec_write 0: semaphore is not ready for register 0x12
codec_write 0: semaphore is not ready for register 0x12
codec_write 0: semaphore is not ready for register 0x18
codec_write 0: semaphore is not ready for register 0x18
codec_write 0: semaphore is not ready for register 0x3a
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: excluding 0x800-0x807
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
Fire GL built-in AGP-support
Based on agpgart interface v0.99 (c) Jeff Hartmann
agpgart: Maximum main memory to use for agp memory: 438M
agpgart: Detected an Intel 855PM Chipset, no integrated grapics found.
agpgart: Detected Intel(R) i855PM chipset
agpgart: AGP aperture is 256M @ 0xe0000000
Power management callback for AGP chipset installed
[fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
AGP: Found 2 AGPv2 devices
AGP: Doing enable for AGPv2
[fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[fglrx] free  AGP = 256126976
[fglrx] max   AGP = 256126976
[fglrx] free  LFB = 52719616
[fglrx] max   LFB = 52719616
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 65536
codec_write 0: semaphore is not ready for register 0x32
codec_read 0: semaphore is not ready for register 0x32
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x32
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_write 0: semaphore is not ready for register 0x2
codec_write 0: semaphore is not ready for register 0x2
codec_write 0: semaphore is not ready for register 0x2
codec_write 0: semaphore is not ready for register 0x2
codec_write 0: semaphore is not ready for register 0x2
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c
codec_read 0: semaphore is not ready for register 0x2c

```


Wish you all have a nice day

---

