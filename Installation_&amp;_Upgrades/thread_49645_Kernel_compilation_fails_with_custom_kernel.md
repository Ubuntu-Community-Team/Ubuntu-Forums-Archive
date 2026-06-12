---
title: "Kernel compilation fails with custom kernel"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by keikoz on 2005-07-17
Hi to all : )

That's my problem: i'm installing ubuntu on a P5GDC Deluxe mobo, which has a it8212 ide/raid controller of ITE. To use it i need to compile a new kernel with the -ac patch (from Alan Cox), that i can find on kernel.org. 
Now , to use that patch i need to use the custom kernel (this one from kernel.org) and not the ubuntu kernel (i.e. the linux-tree); when i try to compile the linux-source of ubuntu, i have a kernel panic; but when i compile the custom kernel of kernel.org (compiled using the /boot/config-2.6.10-386 file), i have the following errors (i tried with and without the patch):

ERROR: Removing Sis5513: Device or resource busy
ERROR: Removing OPTI621: Device or resource busy
ERROR: Removing VIA82xxxx: Device or resource busy

I have at least 20 lines of such errors; after a little bit of time other errors happen, which are logged in kern.log (the above errors arent): 
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table

That's the entire log of the startup with the costum kernel :

```
Jul 16 19:00:43 localhost kernel: Inspecting /boot/System.map-2.6.10
Jul 16 19:00:43 localhost kernel: Loaded 27408 symbols from /boot/System.map-2.6.10.
Jul 16 19:00:43 localhost kernel: Symbols match kernel version 2.6.10.
Jul 16 19:00:43 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Jul 16 19:00:43 localhost kernel: Linux version 2.6.10 (root@localhost) (version gcc 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Sat Jul 16 18:30:19 CEST 2005
Jul 16 19:00:43 localhost kernel: BIOS-provided physical RAM map:
Jul 16 19:00:43 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul 16 19:00:43 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 16 19:00:43 localhost kernel:  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Jul 16 19:00:43 localhost kernel:  BIOS-e820: 0000000000100000 - 000000001ffb0000 (usable)
Jul 16 19:00:43 localhost kernel:  BIOS-e820: 000000001ffb0000 - 000000001ffbe000 (ACPI data)
Jul 16 19:00:43 localhost kernel:  BIOS-e820: 000000001ffbe000 - 000000001fff0000 (ACPI NVS)
Jul 16 19:00:43 localhost kernel:  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
Jul 16 19:00:43 localhost kernel:  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Jul 16 19:00:43 localhost kernel: 511MB LOWMEM available.
Jul 16 19:00:43 localhost kernel: found SMP MP-table at 000ff780
Jul 16 19:00:43 localhost kernel: On node 0 totalpages: 130992
Jul 16 19:00:43 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Jul 16 19:00:43 localhost kernel:   Normal zone: 126896 pages, LIFO batch:16
Jul 16 19:00:43 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Jul 16 19:00:43 localhost kernel: DMI 2.3 present.
Jul 16 19:00:43 localhost kernel: ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb060
Jul 16 19:00:43 localhost kernel: ACPI: RSDT (v001 A M I  OEMRSDT  0x06000517 MSFT 0x00000097) @ 0x1ffb0000
Jul 16 19:00:43 localhost kernel: ACPI: FADT (v001 A M I  OEMFACP  0x06000517 MSFT 0x00000097) @ 0x1ffb0200
Jul 16 19:00:43 localhost kernel: ACPI: MADT (v001 A M I  OEMAPIC  0x06000517 MSFT 0x00000097) @ 0x1ffb0390
Jul 16 19:00:43 localhost kernel: ACPI: OEMB (v001 A M I  AMI_OEM  0x06000517 MSFT 0x00000097) @ 0x1ffbe040
Jul 16 19:00:43 localhost kernel: ACPI: MCFG (v001 A M I  OEMMCFG  0x06000517 MSFT 0x00000097) @ 0x1ffb6e10
Jul 16 19:00:43 localhost kernel: ACPI: DSDT (v001  A0045 A0045001 0x00000001 INTL 0x02002026) @ 0x00000000
Jul 16 19:00:43 localhost kernel: ACPI: PM-Timer IO Port: 0x808
Jul 16 19:00:43 localhost kernel: ACPI: Local APIC address 0xfee00000
Jul 16 19:00:43 localhost kernel: ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul 16 19:00:43 localhost kernel: Processor #0 15:4 APIC version 20
Jul 16 19:00:43 localhost kernel: ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jul 16 19:00:43 localhost kernel: Processor #1 15:4 APIC version 20
Jul 16 19:00:43 localhost kernel: WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
Jul 16 19:00:43 localhost kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 16 19:00:43 localhost kernel: IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jul 16 19:00:43 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 16 19:00:43 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 16 19:00:43 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 16 19:00:43 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 16 19:00:43 localhost kernel: ACPI: IRQ0 used by override.
Jul 16 19:00:43 localhost kernel: ACPI: IRQ2 used by override.
Jul 16 19:00:43 localhost kernel: ACPI: IRQ9 used by override.
Jul 16 19:00:43 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 16 19:00:43 localhost kernel: Using ACPI (MADT) for SMP configuration information
Jul 16 19:00:43 localhost kernel: Built 1 zonelists
Jul 16 19:00:43 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash
Jul 16 19:00:43 localhost kernel: mapped APIC to ffffd000 (fee00000)
Jul 16 19:00:43 localhost kernel: mapped IOAPIC to ffffc000 (fec00000)
Jul 16 19:00:43 localhost kernel: Initializing CPU#0
Jul 16 19:00:43 localhost kernel: PID hash table entries: 2048 (order: 11, 32768 bytes)
Jul 16 19:00:43 localhost kernel: Detected 3212.446 MHz processor.
Jul 16 19:00:43 localhost kernel: Using pmtmr for high-res timesource
Jul 16 19:00:43 localhost kernel: Console: colour VGA+ 80x25
Jul 16 19:00:43 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 16 19:00:43 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 16 19:00:43 localhost kernel: Memory: 511660k/523968k available (1417k kernel code, 11764k reserved, 753k data, 224k init, 0k highmem)
Jul 16 19:00:43 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 16 19:00:43 localhost kernel: Calibrating delay loop... 6356.99 BogoMIPS (lpj=3178496)
Jul 16 19:00:43 localhost kernel: Security Framework v1.0.0 initialized
Jul 16 19:00:43 localhost kernel: SELinux:  Disabled at boot.
Jul 16 19:00:43 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Jul 16 19:00:43 localhost kernel: CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000
Jul 16 19:00:43 localhost kernel: CPU: After vendor identify, caps:  bfebfbff 20000000 00000000 00000000
Jul 16 19:00:43 localhost kernel: monitor/mwait feature present.
Jul 16 19:00:43 localhost kernel: using mwait in idle threads.
Jul 16 19:00:43 localhost kernel: CPU: Trace cache: 12K uops, L1 D cache: 16K
Jul 16 19:00:43 localhost kernel: CPU: L2 cache: 2048K
Jul 16 19:00:43 localhost kernel: CPU: After all inits, caps:        bfebfbff 20000000 00000000 00000080
Jul 16 19:00:43 localhost kernel: CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Jul 16 19:00:43 localhost kernel: Enabling fast FPU save and restore... done.
Jul 16 19:00:43 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Jul 16 19:00:43 localhost kernel: Checking 'hlt' instruction... OK.
Jul 16 19:00:43 localhost kernel: Checking for popad bug... OK.
Jul 16 19:00:43 localhost kernel: ENABLING IO-APIC IRQs
Jul 16 19:00:43 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=-1
Jul 16 19:00:43 localhost kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Jul 16 19:00:43 localhost kernel: Freeing initrd memory: 4220k freed
Jul 16 19:00:43 localhost kernel: NET: Registered protocol family 16
Jul 16 19:00:43 localhost kernel: EISA bus registered
Jul 16 19:00:43 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=4
Jul 16 19:00:43 localhost kernel: PCI: Using MMCONFIG
Jul 16 19:00:43 localhost kernel: mtrr: v2.0 (20020519)
Jul 16 19:00:43 localhost kernel: ACPI: Subsystem revision 20041105
Jul 16 19:00:43 localhost kernel: ACPI: Interpreter enabled
Jul 16 19:00:43 localhost kernel: ACPI: Using IOAPIC for interrupt routing
Jul 16 19:00:43 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Jul 16 19:00:43 localhost kernel: PCI: Probing PCI hardware (bus 00)
Jul 16 19:00:43 localhost kernel: PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Jul 16 19:00:43 localhost kernel: PCI: Transparent bridge - 0000:00:1e.0
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul 16 19:00:43 localhost kernel: ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jul 16 19:00:43 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 16 19:00:43 localhost kernel: pnp: PnP ACPI init
Jul 16 19:00:43 localhost kernel: pnp: PnP ACPI: found 19 devices
Jul 16 19:00:43 localhost kernel: PnPBIOS: Disabled by ACPI
Jul 16 19:00:43 localhost kernel: PCI: Using ACPI for IRQ routing
Jul 16 19:00:43 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
Jul 16 19:00:43 localhost kernel: ** causes a device to stop working, it is probably because the
Jul 16 19:00:43 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
Jul 16 19:00:43 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
Jul 16 19:00:43 localhost kernel: ** behavior.  If this argument makes the device work again,
Jul 16 19:00:43 localhost kernel: ** please email the output of "lspci" to bjorn.helgaas@hp.com
Jul 16 19:00:43 localhost kernel: ** so I can fix the driver.
Jul 16 19:00:43 localhost kernel: pnp: 00:07: ioport range 0x290-0x297 has been reserved
Jul 16 19:00:43 localhost kernel: audit: initializing netlink socket (disabled)
Jul 16 19:00:43 localhost kernel: audit(1121533227.772:0): initialized
Jul 16 19:00:43 localhost kernel: VFS: Disk quotas dquot_6.5.1
Jul 16 19:00:43 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 16 19:00:43 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Jul 16 19:00:43 localhost kernel: devfs: boot_options: 0x0
Jul 16 19:00:43 localhost kernel: Initializing Cryptographic API
Jul 16 19:00:43 localhost kernel: isapnp: Scanning for PnP cards...
Jul 16 19:00:43 localhost kernel: isapnp: No Plug & Play device found
Jul 16 19:00:43 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 16 19:00:43 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 16 19:00:43 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Jul 16 19:00:43 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 16 19:00:43 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 16 19:00:43 localhost kernel: io scheduler noop registered
Jul 16 19:00:43 localhost kernel: io scheduler anticipatory registered
Jul 16 19:00:43 localhost kernel: io scheduler deadline registered
Jul 16 19:00:43 localhost kernel: io scheduler cfq registered
Jul 16 19:00:43 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Jul 16 19:00:43 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Jul 16 19:00:43 localhost kernel: EISA: Probing bus 0 at eisa0
Jul 16 19:00:43 localhost kernel: Cannot allocate resource for EISA slot 8
Jul 16 19:00:43 localhost kernel: EISA: Detected 0 cards.
Jul 16 19:00:43 localhost kernel: NET: Registered protocol family 2
Jul 16 19:00:43 localhost kernel: IP: routing cache hash table of 4096 buckets, 32Kbytes
Jul 16 19:00:43 localhost kernel: TCP: Hash tables configured (established 32768 bind 65536)
Jul 16 19:00:43 localhost kernel: NET: Registered protocol family 8
Jul 16 19:00:43 localhost kernel: NET: Registered protocol family 20
Jul 16 19:00:43 localhost kernel: ACPI wakeup devices: 
Jul 16 19:00:43 localhost kernel: P0P1 P0P3 P0P4 P0P5 P0P6 P0P7 PS2K PS2M UAR1 USB1 USB2 USB3 USB4 EUSB MC97 
Jul 16 19:00:43 localhost kernel: ACPI: (supports S0 S1 S3 S4 S5)
Jul 16 19:00:43 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Jul 16 19:00:43 localhost kernel: RAMDISK: Loading 4220KiB [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^Hdone.
Jul 16 19:00:43 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Jul 16 19:00:43 localhost kernel: Freeing unused kernel memory: 224k freed
Jul 16 19:00:43 localhost kernel: ACPI: Processor [CPU1] (supports 8 throttling states)
Jul 16 19:00:43 localhost kernel: NET: Registered protocol family 1
Jul 16 19:00:43 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 16 19:00:43 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 16 19:00:43 localhost kernel: ICH6: IDE controller at PCI slot 0000:00:1f.1
Jul 16 19:00:43 localhost kernel: ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jul 16 19:00:43 localhost kernel: ICH6: chipset revision 3
Jul 16 19:00:43 localhost kernel: ICH6: not 100%% native mode: will probe irqs later
Jul 16 19:00:43 localhost kernel:     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
Jul 16 19:00:43 localhost kernel:     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
Jul 16 19:00:43 localhost kernel: Probing IDE interface ide0...
Jul 16 19:00:43 localhost kernel: hda: WDC WD1200JB-00GVC0, ATA DISK drive
Jul 16 19:00:43 localhost kernel: hdb: WDC WD1200JB-00FUA0, ATA DISK drive
Jul 16 19:00:43 localhost kernel: elevator: using anticipatory as default io scheduler
Jul 16 19:00:43 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 16 19:00:43 localhost kernel: hda: max request size: 1024KiB
Jul 16 19:00:43 localhost kernel: hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
Jul 16 19:00:43 localhost kernel: hda: cache flushes supported
Jul 16 19:00:43 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 >
Jul 16 19:00:43 localhost kernel: hdb: max request size: 1024KiB
Jul 16 19:00:43 localhost kernel: hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
Jul 16 19:00:43 localhost kernel: hdb: cache flushes supported
Jul 16 19:00:43 localhost kernel:  /dev/ide/host0/bus0/target1/lun0: p1
Jul 16 19:00:43 localhost kernel: Probing IDE interface ide1...
Jul 16 19:00:43 localhost kernel: Probing IDE interface ide1...
Jul 16 19:00:43 localhost kernel: Probing IDE interface ide2...
Jul 16 19:00:43 localhost kernel: ide2: Wait for ready failed before probe !
Jul 16 19:00:43 localhost kernel: Probing IDE interface ide3...
Jul 16 19:00:43 localhost kernel: ide3: Wait for ready failed before probe !
Jul 16 19:00:43 localhost kernel: Probing IDE interface ide4...
Jul 16 19:00:43 localhost kernel: ide4: Wait for ready failed before probe !
Jul 16 19:00:43 localhost kernel: Probing IDE interface ide5...
Jul 16 19:00:43 localhost kernel: ide5: Wait for ready failed before probe !
Jul 16 19:00:43 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Jul 16 19:00:43 localhost kernel: kjournald starting.  Commit interval 5 seconds
Jul 16 19:00:43 localhost kernel: Adding 979924k swap on /dev/hda5.  Priority:-1 extents:1
Jul 16 19:00:43 localhost kernel: EXT3 FS on hda1, internal journal
Jul 16 19:00:43 localhost kernel: parport_pc: Ignoring new-style parameters in presence of obsolete ones
Jul 16 19:00:43 localhost kernel: parport: PnPBIOS parport detected.
Jul 16 19:00:43 localhost kernel: parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jul 16 19:00:43 localhost kernel: lp0: using parport0 (interrupt-driven).
Jul 16 19:00:43 localhost kernel: mice: PS/2 mouse device common for all mice
Jul 16 19:00:43 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Jul 16 19:00:43 localhost kernel: ieee1394: Initialized config rom entry `ip1394'
Jul 16 19:00:43 localhost kernel: SCSI subsystem initialized
Jul 16 19:00:43 localhost kernel: sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Jul 16 19:00:43 localhost kernel: ts: Compaq touchscreen protocol output
Jul 16 19:00:43 localhost kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
Jul 16 19:00:43 localhost kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[b]Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table
Jul 16 19:00:43 localhost kernel: device-mapper: dm-linear: Device lookup failed
Jul 16 19:00:43 localhost kernel: device-mapper: error adding target to table[/b]
Jul 16 19:00:43 localhost kernel: kjournald starting.  Commit interval 5 seconds
Jul 16 19:00:43 localhost kernel: EXT3 FS on hda6, internal journal
Jul 16 19:00:43 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Jul 16 19:00:43 localhost kernel: Real Time Clock Driver v1.12
Jul 16 19:00:43 localhost kernel: input: PC Speaker
Jul 16 19:00:43 localhost kernel: inserting floppy driver for 2.6.10
Jul 16 19:00:43 localhost kernel: Floppy drive(s): fd0 is 1.44M
Jul 16 19:00:43 localhost kernel: FDC 0 is a post-1991 82077
Jul 16 19:00:43 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Jul 16 19:00:43 localhost kernel: agpgart: Detected an Intel 915G Chipset.
Jul 16 19:00:43 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
Jul 16 19:00:43 localhost kernel: agpgart: AGP aperture is 256M @ 0x0
Jul 16 19:00:43 localhost kernel: usbcore: registered new driver usbfs
Jul 16 19:00:43 localhost kernel: usbcore: registered new driver hub
Jul 16 19:00:43 localhost kernel: USB Universal Host Controller Interface driver v2.2
Jul 16 19:00:43 localhost kernel: ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.0: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
Jul 16 19:00:43 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.0 to 64
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.0: irq 23, io base 0x8000
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul 16 19:00:43 localhost kernel: hub 1-0:1.0: USB hub found
Jul 16 19:00:43 localhost kernel: hub 1-0:1.0: 2 ports detected
Jul 16 19:00:43 localhost kernel: ACPI: PCI interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 19
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.1: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
Jul 16 19:00:43 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.1 to 64
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.1: irq 19, io base 0x8400
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul 16 19:00:43 localhost kernel: hub 2-0:1.0: USB hub found
Jul 16 19:00:43 localhost kernel: hub 2-0:1.0: 2 ports detected
Jul 16 19:00:43 localhost kernel: ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.2: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
Jul 16 19:00:43 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.2 to 64
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.2: irq 18, io base 0x8800
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul 16 19:00:43 localhost kernel: hub 3-0:1.0: USB hub found
Jul 16 19:00:43 localhost kernel: hub 3-0:1.0: 2 ports detected
Jul 16 19:00:43 localhost kernel: ACPI: PCI interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
Jul 16 19:00:43 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.3 to 64
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.3: irq 16, io base 0x9000
Jul 16 19:00:43 localhost kernel: uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Jul 16 19:00:43 localhost kernel: hub 4-0:1.0: USB hub found
Jul 16 19:00:43 localhost kernel: hub 4-0:1.0: 2 ports detected
Jul 16 19:00:43 localhost kernel: ACPI: PCI interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
Jul 16 19:00:43 localhost kernel: ehci_hcd 0000:00:1d.7: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
Jul 16 19:00:43 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.7 to 64
Jul 16 19:00:43 localhost kernel: ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xcacff800
Jul 16 19:00:43 localhost kernel: ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jul 16 19:00:43 localhost kernel: PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Jul 16 19:00:43 localhost kernel: ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
Jul 16 19:00:43 localhost kernel: hub 5-0:1.0: USB hub found
Jul 16 19:00:43 localhost kernel: hub 5-0:1.0: 8 ports detected
Jul 16 19:00:43 localhost kernel: hw_random hardware driver 1.0.0 loaded
Jul 16 19:00:43 localhost kernel: libata version 1.10 loaded.
Jul 16 19:00:43 localhost kernel: ata_piix version 1.03
Jul 16 19:00:43 localhost kernel: ACPI: PCI interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 19
Jul 16 19:00:43 localhost kernel: PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jul 16 19:00:43 localhost kernel: ata1: SATA max UDMA/133 cmd 0xA800 ctl 0xA402 bmdma 0x9400 irq 19
Jul 16 19:00:43 localhost kernel: ata2: SATA max UDMA/133 cmd 0xA000 ctl 0x9802 bmdma 0x9408 irq 19
Jul 16 19:00:43 localhost kernel: ata1: SATA port has no device.
Jul 16 19:00:43 localhost kernel: scsi0 : ata_piix
Jul 16 19:00:43 localhost kernel: ata2: SATA port has no device.
Jul 16 19:00:43 localhost kernel: scsi1 : ata_piix
Jul 16 19:00:43 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
Jul 16 19:00:43 localhost kernel: ACPI: PCI interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
Jul 16 19:00:43 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[cadff800-cadfffff]  Max Packet=[2048]
Jul 16 19:00:43 localhost kernel: ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000004016a]
Jul 16 19:00:44 localhost kernel: ACPI: Power Button (FF) [PWRF]
Jul 16 19:00:44 localhost kernel: ibm_acpi: acpi_evalf(DHKC, d, ...) failed: 4097
Jul 16 19:00:44 localhost kernel: ibm_acpi: `enable,0xffff' invalid for parameter `hotkey'
Jul 16 19:00:44 localhost kernel: ibm_acpi: ec object not found
Jul 16 19:00:44 localhost kernel: toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
Jul 16 19:00:45 localhost kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 16 19:00:45 localhost kernel: apm: overridden by ACPI
```

I really dont know how to do; i tried compiling that custom kernel a lot of time with different options. Finally i need:

1. A way to compile a costum kernel (from kernel.org) without that pbl
2. Or a way to compile the kernel-source from ubuntu _including_ the -ac patch
3. Or a way to compile a single module from the entire source -tree for my kernel

If somebody could help me , i would really appreciate

Regards

keikoz

---

### Post by scoon on 2005-07-17
Hey there, 

I hand roll my kernels as well (cko2 patchset).  When I get kernel source and before I patch it, I run make mrproper.  That cleans out the source tree of anything stale.  Then I patch and then I copy my desired .config into the new kernel tree.  Then I these steps: 
1. make oldconfig
2. make all
3. sudo make modules_install
4. sudo make install
5. change /boot/grub/grub.conf as needed.
6. reboot && enjoy.

regards, 

scoon

---

### Post by keikoz on 2005-07-17
Thanks very much for helping :)

Actually, i tried a lot of methods, including the one you explain. I tried another time right now, including the make mrproper (i forgot it before): but it doesnt works, i just obtain that message on boot:

Kernel Panic - not syncing: VFS : Unable to mount root fs on unknown block (0,0)

Another thing to know: my root is mounted on hda1, which uses ext3 filesystem, and i put that filesystem (and ext2, and cramfs) built directly into the kernel.

Actually you tell you have no problems to compile the kernel, but do you use the kernel of kernel.org or the one that can be installed from ubuntu repository (linux-tree-2.6.10) ? All my problem comes from the necessity of using the kernel of kernel.org ...

regards,

keikoz

---

### Post by scoon on 2005-07-17
Hey there, 

I use vanilla kernels from kernel.org.   The other problem may be your grub set up.  What does that look like ?

Regards, 

scoon

---

### Post by keikoz on 2005-07-17
Re :)

my grub file: 

```
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-ac11 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-ac11 root=/dev/hda1 ro quiet splash
savedefault
boot

title		Ubuntu, kernel 2.6.10-ac11 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-ac11 root=/dev/hda1 ro single
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professionnel
map (hd0) (hd1)
map (hd1) (hd0) 
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

And the procedure i used, exactly:

- make mrproper
- apply the -ac patch; apply another patch for my ethernet;
- copying the config file as .config in /usr/src/linux
- make oldconfig
- make gconfig 
- make all && make modules_install && make install
- i modify the menu.lst file of grub like you can see it

I reboot, and i obtain that result

...
...
Starting Ubuntu ...
Kernel Panic - not syncing: VFS : Unable to mount root fs on unknown block (0,0)

 ](*,)  ](*,)  ](*,) 

If you have an idea ... thx very much for help

keikoz

---

### Post by scoon on 2005-07-17
Hey there, 

if you can stat /boot/vmlinuz-2.6.10-ac11, then i don't really have any ideas.  Why not get an ubuntu config that works and use that for this kernel's confing.  Do make oldconfig and then make all.  Don't change it.  Just to see if maybe it is your options. 

regards, 

scoon

---

### Post by keikoz on 2005-07-17
Wow you're really fast in replying  ;-) 

Actually the really strange thing, is that i could compile the kernel 3 days ago; after that i tried another time, and problems started; i couldnt do it more. I repeated exactly the same procedure, trying in all possible ways... No way  :roll: 

i dont think the config file is the problem; i used the same 3 days ago, and when problems started, i tried changing all what i could ... i always start using the /boot/config-2.6.10-5-386 shipped with the official ubuntu kernel; it works perfectly with the kernel source of ubuntu...

Maybee... if it doesnt disturbs you, could i try with your own config file ? 

Maybee some miracle : o )

---

### Post by scoon on 2005-07-17
Hey there, 

No, that won't work.  My hardware could/prolly is different than yours.  So all that'd prove is that our hardware is diff.  Besides, I use cko patchset.  You use ac.  

regards, 

scoon

---

### Post by keikoz on 2005-07-17
Yes, right...

Thx very much for help anyway :)

keikoz

---

### Post by keikoz on 2005-07-17
Mmh i'm having an idea:

my hda1 partition (where root is mounted) , is a ext3 partition; now i watched a little my grub directory; i noticed that no one ext3fs stage is present:

```
root@localhost:/boot/grub # ls
device.map     fat_stage1_5  menu.lst   minix_stage1_5     stage1  xfs_stage1_5
e2fs_stage1_5  jfs_stage1_5  menu.lst~  reiserfs_stage1_5  stage2
```

Could my problem come just from there ? If that is the good answer to the problem, what i dont understand is that the original kernel of ubuntu has no problems to startup, even using grub, and on the same partition.

More: if that's the problem, is it possible to add a ext3 stage, or should i recompile entirely grub ?

regards,

keikoz

---

### Post by keikoz on 2005-07-17
For those who are interested : i could make the kernel working; it is a problem of filesystems, it seems; ext3 isnt recognized bye grub as it is; to use it i did need to make a initrd file; was quite easy:

mkinitrd /boot/initrd.img-2.6.10-ac11 2.6.10-ac11

where the first parameter is the initrd file, and the second the directory of the kernel modules; finally, I need to add a line in the /boot/grub/menu.lst, like this:

```
title		Ubuntu, kernel 2.6.10-ac11 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-ac11 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-ac11
savedefault
boot
```

Now my problem isnt full resolved, because seems there is still a problem with the controller driver: the cd-roms on there are assigned as hda/hdb and my HD as hde/hdf

Maybee i'll assume it like this... but that's another problem and (maybee) another post.

---

