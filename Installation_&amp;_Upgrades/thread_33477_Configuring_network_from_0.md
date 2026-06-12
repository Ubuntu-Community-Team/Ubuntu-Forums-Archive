---
title: "Configuring network from 0"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by Antoni on 2005-05-11
Trying to solve a weird  problem in the install I left off the net configuration during the install.

The present situation is Ubuntu answers pings from another PC but it's own net tools don't work. Net tools indicate the card is in loopback mode.

Where must I start to put the network to work? Any howto out there?

---

### Post by Zelut on 2005-05-11
Have you tried the system > Admin > Networks under the gnome panel & see if you can change the settings there?  Mine originally started in 'lo' as well so I used the drop-down to change it to eth0 and it seemed to reset & work.

Perhaps you've tried that... thought I'd start with the basics anyway.

---

### Post by Antoni on 2005-05-11
[QUOTE=kuyaedz]Have you tried the system > Admin > Networks under the gnome panel & see if you can change the settings there?  Mine originally started in 'lo' as well so I used the drop-down to change it to eth0 and it seemed to reset & work.

Perhaps you've tried that... thought I'd start with the basics anyway.[/QUOTE]
 I tried it It starts with eth0 greyed out, says it is unconfigured and does'nt retain changes i make

---

### Post by Zelut on 2005-05-11
Can you run a dmesg for me & post any output pertaining to eth0 or your network?  (its giong to post all kinds of info about your system, we only need eth0 or network related info)

# dmesg


I'm sure we'll get it figured out.

---

### Post by Antoni on 2005-05-11
Here is the output. 
```

toni@ubuntu:~$ dmesg
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
 BIOS-e820: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
 BIOS-e820: 000000000fff3000 - 0000000010000000 (ACPI data)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
255MB LOWMEM available.
On node 0 totalpages: 65520
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 61424 pages, LIFO batch:14
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.2 present.
ACPI: RSDP (v000 VIAP4X                                ) @ 0x000f71e0
ACPI: RSDT (v001 VIAP4X AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3000
ACPI: FADT (v001 VIAP4X AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3040
ACPI: DSDT (v001 VIAP4X AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
ACPI: PM-Timer IO Port: 0x408
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01204000)
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 16384 bytes)
Detected 1400.711 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 252060k/262080k available (1436k kernel code, 9356k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 2760.70 BogoMIPS (lpj=1380352)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 256K
CPU: After all inits, caps: 3febf9ff 00000000 00000000 00000080 00000000 00000000
CPU: Intel(R) Pentium(R) 4 CPU 1400MHz stepping 0a
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0e20)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfb160, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Via IRQ fixup
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
audit: initializing netlink socket (disabled)
audit(1115846369.147:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
SLPB PCI0 USB0 USB1 USB2 MC97 UAR1
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2])
ACPI: Processor [CPU0] (supports 2 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:11.1
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 11 (level, low) -> IRQ 11
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt8233 (rev 00) IDE UDMA100 controller on pci0000:00:11.1
    ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: Maxtor 6Y120L0, ATA DISK drive
hdb: ST340810A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 >
hdb: max request size: 128KiB
hdb: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hdb: cache flushes not supported
 /dev/ide/host0/bus0/target1/lun0: p1
Probing IDE interface ide1...
hdc: HL-DT-ST CD-RW GCE-8240B, ATAPI CD/DVD-ROM drive
hdd: LG CD-ROM CRD-8521B, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (455 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 488336k swap on /dev/hda6.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 40X CD-ROM CD-R/RW drive, 8192kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 52X CD-ROM drive, 128kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA P4X266 chipset
agpgart: Maximum main memory to use for agp memory: 203M
agpgart: AGP aperture is 128M @ 0xd0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 5 (level, low) -> IRQ 5
sis900.c: v1.08.07 11/02/2003
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 10 (level, low) -> IRQ 10
0000:00:0a.0: SiS 900 Internal MII PHY transceiver found at address 1.
0000:00:0a.0: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 10, 00:06:4f:0e:6e:de.
irda_init()
NET: Registered protocol family 23
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:11.2[D] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:11.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:11.2: irq 11, io base 0xdc00
uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:11.3[D] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:11.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:11.3: irq 11, io base 0xe000
uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:11.4[D] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:11.4: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:11.4: irq 11, io base 0xe400
uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
PPP BSD Compression module registered
PPP Deflate Compression module registered

```

---

