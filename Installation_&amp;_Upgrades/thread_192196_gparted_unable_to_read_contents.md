---
title: "gparted unable to read contents"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by jeremytaylor on 2006-06-08
Hi, I'm having the problem with ubuntu being unable to mount my root filesystem. I thought I'd bung in the install cd and run gparted to find out where my partitions had got to. It seems to this my disk is still labelled sda. However all my partitons have exclamation marks and clicking on information reveals that it is unable to read the contents of this filesystem. 
Any ideas as to what's gone wrong?

jeremy

---

### Post by franestepona on 2006-06-08
Have you edited your partitions before? (resized, moved or whatever) And if u did, which program you used? I try to move once an ext3 partition using partition magic and crashed in the middle, after that the partition had the exclamation mark and had to reformat it.

Fran.

---

### Post by jeremytaylor on 2006-06-08
Well I used the gparted in the installer to move them. In fact not even move them I just switched one fat32 one to a ext3 one. I haven't touched my others for a long time. Breezy ran fine with these partitions. Windows still runs. 
I'm worried that it's something do do with my sata controller as there are a few error messages in my dmesg. I've included it here.

thanks for your help!
Jeremy
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable)
[4294667.296000]  BIOS-e820: 000000007ffa0000 - 000000007ffb0000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000007ffb0000 - 000000007fff0000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[4294667.296000] 1151MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000ff780
[4294667.296000] On node 0 totalpages: 524192
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 294816 pages, LIFO batch:31
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb5e0
[4294667.296000] ACPI: RSDT (v001 A M I  OEMRSDT  0x08000511 MSFT 0x00000097) @ 0x7ffa0000
[4294667.296000] ACPI: FADT (v001 A M I  OEMFACP  0x08000511 MSFT 0x00000097) @ 0x7ffa0200
[4294667.296000] ACPI: MADT (v001 A M I  OEMAPIC  0x08000511 MSFT 0x00000097) @ 0x7ffa0390
[4294667.296000] ACPI: OEMB (v001 A M I  AMI_OEM  0x08000511 MSFT 0x00000097) @ 0x7ffb0040
[4294667.296000] ACPI: MCFG (v001 A M I  OEMMCFG  0x08000511 MSFT 0x00000097) @ 0x7ffa5e00
[4294667.296000] ACPI: SSDT (v001    AMI   CPU1CS 0x00000001 INTL 0x20030522) @ 0x7ffa5e40
[4294667.296000] ACPI: SSDT (v001    AMI   CPU1PM 0x00000001 INTL 0x20030522) @ 0x7ffa5f80
[4294667.296000] ACPI: DSDT (v001  A0074 A0074000 0x00000000 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 6:13 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 88000000 (gap: 80000000:7fb80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 1863.220 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.054000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294668.054000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.138000] Memory: 2068272k/2096768k available (1976k kernel code, 27360k reserved, 606k data, 288k init, 1179264k highmem)
[4294668.138000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.198000] Calibrating delay using timer specific routine.. 3726.71 BogoMIPS (lpj=1863357)
[4294668.198000] Security Framework v1.0.0 initialized
[4294668.198000] SELinux:  Disabled at boot.
[4294668.198000] Mount-cache hash table entries: 512
[4294668.198000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[4294668.198000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[4294668.198000] CPU: L1 I cache: 32K, L1 D cache: 32K
[4294668.198000] CPU: L2 cache: 2048K
[4294668.198000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 00000180 00000000 00000000
[4294668.198000] mtrr: v2.0 (20020519)
[4294668.198000] CPU: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[4294668.198000] Enabling fast FPU save and restore... done.
[4294668.198000] Enabling unmasked SIMD FPU exception support... done.
[4294668.198000] Checking 'hlt' instruction... OK.
[4294668.202000] checking if image is initramfs... it is
[4294668.784000] Freeing initrd memory: 6838k freed
[4294668.789000] ACPI: Looking for DSDT ... not found!
[4294668.813000] ENABLING IO-APIC IRQs
[4294668.813000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294668.924000] NET: Registered protocol family 16
[4294668.924000] EISA bus registered
[4294668.924000] ACPI: bus type pci registered
[4294668.924000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=4
[4294668.924000] PCI: Using MMCONFIG
[4294668.924000] ACPI: Subsystem revision 20051216
[4294668.940000] ACPI: Interpreter enabled
[4294668.940000] ACPI: Using IOAPIC for interrupt routing
[4294668.941000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.941000] PCI: Probing PCI hardware (bus 00)
[4294668.953000] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[4294668.953000] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[4294668.953000] PCI: Enabled ICH6/i801 SMBus device
[4294668.953000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[4294668.953000] Boot video device is 0000:01:00.0
[4294668.954000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.954000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.023000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[4294669.023000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[4294669.026000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[4294669.042000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294669.043000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[4294669.043000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294669.043000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[4294669.044000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.044000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.044000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.044000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294669.045000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.045000] pnp: PnP ACPI init
[4294669.055000] pnp: PnP ACPI: found 17 devices
[4294669.055000] PnPBIOS: Disabled by ACPI PNP
[4294669.055000] PCI: Using ACPI for IRQ routing
[4294669.055000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.069000] pnp: 00:08: ioport range 0x6c0-0x6cf has been reserved
[4294669.069000] PCI: Bridge: 0000:00:01.0
[4294669.069000]   IO window: b000-bfff
[4294669.069000]   MEM window: f0000000-fbefffff
[4294669.069000]   PREFETCH window: d0000000-deffffff
[4294669.069000] PCI: Bridge: 0000:00:1c.0
[4294669.069000]   IO window: c000-cfff
[4294669.069000]   MEM window: disabled.
[4294669.069000]   PREFETCH window: disabled.
[4294669.069000] PCI: Bus 4, cardbus bridge: 0000:03:01.0
[4294669.069000]   IO window: 0000d000-0000d0ff
[4294669.069000]   IO window: 0000d400-0000d4ff
[4294669.069000]   PREFETCH window: 88000000-89ffffff
[4294669.069000]   MEM window: 8c000000-8dffffff
[4294669.069000] PCI: Bridge: 0000:00:1e.0
[4294669.069000]   IO window: d000-efff
[4294669.069000]   MEM window: fbf00000-fbffffff
[4294669.069000]   PREFETCH window: 88000000-8affffff
[4294669.069000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294669.069000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294669.069000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294669.069000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294669.069000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294669.069000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 177
[4294669.070000] audit: initializing netlink socket (disabled)
[4294669.070000] audit(1149790438.069:1): initialized
[4294669.070000] highmem bounce pool size: 64 pages
[4294669.070000] VFS: Disk quotas dquot_6.5.1
[4294669.070000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.070000] Initializing Cryptographic API
[4294669.070000] io scheduler noop registered
[4294669.070000] io scheduler anticipatory registered
[4294669.070000] io scheduler deadline registered
[4294669.070000] io scheduler cfq registered
[4294669.070000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294669.070000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294669.070000] assign_interrupt_mode Found MSI capability
[4294669.070000] Allocate Port Service[pcie00]
[4294669.070000] Allocate Port Service[pcie03]
[4294669.070000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294669.070000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294669.070000] assign_interrupt_mode Found MSI capability
[4294669.070000] Allocate Port Service[pcie00]
[4294669.070000] Allocate Port Service[pcie02]
[4294669.070000] Allocate Port Service[pcie03]
[4294669.070000] isapnp: Scanning for PnP cards...
[4294669.427000] isapnp: No Plug & Play device found
[4294669.439000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294669.441000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294669.442000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294669.442000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294669.443000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294669.443000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294669.443000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.443000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.443000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.445000] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[4294669.445000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.445000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.445000] mice: PS/2 mouse device common for all mice
[4294669.445000] EISA: Probing bus 0 at eisa.0
[4294669.445000] EISA: Detected 0 cards.
[4294669.445000] NET: Registered protocol family 2
[4294669.454000] IP route cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294669.454000] TCP established hash table entries: 524288 (order: 9, 2097152 bytes)
[4294669.456000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.457000] TCP: Hash tables configured (established 524288 bind 65536)
[4294669.457000] TCP reno registered
[4294669.457000] TCP bic registered
[4294669.457000] NET: Registered protocol family 1
[4294669.457000] NET: Registered protocol family 8
[4294669.457000] NET: Registered protocol family 20
[4294669.457000] Using IPI Shortcut mode
[4294669.457000] ACPI wakeup devices: 
[4294669.457000] P0P1 P0P3 BLAN P0P4 P0P5 P0P6 P0P7 MC97 USB1 USB2 USB3 USB4 EUSB HDAU SLPB 
[4294669.457000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.457000] Freeing unused kernel memory: 288k freed
[4294669.496000] vga16fb: initializing
[4294669.496000] vga16fb: mapped to 0xc00a0000
[4294669.603000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294669.617000] Console: switching to colour frame buffer device 80x25
[4294669.617000] fb0: VGA16 VGA frame buffer device
[4294670.748000] Capability LSM initialized
[4294670.773000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294670.773000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294670.781000] ACPI: Thermal Zone [TZ00] (47 C)
[4294671.145000] SCSI subsystem initialized
[4294671.146000] ACPI: bus type scsi registered
[4294671.146000] libata version 1.20 loaded.
[4294671.147000] ahci 0000:00:1f.2: version 1.2
[4294671.147000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 209
[4294671.147000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[4294671.147000] ahci: probe of 0000:00:1f.2 failed with error -12
[4294671.149000] ata_piix 0000:00:1f.2: version 1.05
[4294671.149000] ata_pci_init_one: pci_dev class+intf: 0x10180
[4294671.149000] ata_pci_init_one: NO_LEGACY == 0
[4294671.149000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 209
[4294671.149000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294671.149000] ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xFFA0 irq 14
[4294671.303000] ata1: dev 0 cfg 00:045a 49:0f00 82:746b 83:7fe8 84:4023 85:f469 86:3e48 87:4023 88:203f 93:600b
[4294671.303000] ata1: dev 0 ATA-6, max UDMA/100, 156301488 sectors: LBA48
[4294671.303000] ata1(0): applying bridge limits
[4294671.303000] ata_acpi_push_id: skipping for PATA mode
[4294671.303000] ata1: dev 0 configured for UDMA/100
[4294671.303000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294671.303000] pata_get_dev_handle: dev_handle: 0xdfff5e60, parent_handle: 0xc20f0320
[4294671.303000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff82a00, *handle=0xdfff5e60
[4294671.303000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdfff3860
[4294671.303000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node dfff34c0), AE_AML_OPERAND_VALUE
[4294671.303000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node dfff3820), AE_AML_OPERAND_VALUE
[4294671.303000] scsi0 : ata_piix
[4294671.304000]   Vendor: ATA       Model: IC25N080ATMR04-0  Rev: MO4O
[4294671.304000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294671.304000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294671.304000] pata_get_dev_handle: dev_handle: 0xdfff5e60, parent_handle: 0xc20f0320
[4294671.304000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff82a00, *handle=0xdfff5e60
[4294671.307000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xFFA8 irq 15
[4294671.615000] ata2: dev 0 cfg 00:85c0 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407 93:4000
[4294671.615000] ata2: dev 0 ATAPI, max UDMA/33
[4294671.615000] ata2(0): applying bridge limits
[4294671.615000] ata_acpi_push_id: skipping for PATA mode
[4294671.615000] ata2: dev 0 configured for UDMA/33
[4294671.615000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294671.615000] pata_get_dev_handle: dev_handle: 0xdfff5e60, parent_handle: 0xc20f0320
[4294671.615000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff82a00, *handle=0xdfff5e60
[4294671.619000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdfff3720
[4294671.619000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node dfff34c0), AE_AML_OPERAND_VALUE
[4294671.619000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.IDE0.CHN1.DRV0._GTF] (Node dfff36e0), AE_AML_OPERAND_VALUE
[4294671.619000] scsi1 : ata_piix
[4294671.622000]   Vendor: MATSHITA  Model: UJ-831D           Rev: 1.00
[4294671.622000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[4294671.622000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[4294671.622000] pata_get_dev_handle: dev_handle: 0xdfff5e60, parent_handle: 0xc20f0320
[4294671.622000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff82a00, *handle=0xdfff5e60
[4294671.629000] Driver 'sd' needs updating - please use bus_type methods
[4294671.634000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294671.634000] SCSI device sda: drive cache: write back
[4294671.636000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294671.636000] SCSI device sda: drive cache: write back
[4294671.636000]  sda:<3>ata1: command 0x25 timeout, stat 0xd0 host_stat 0x24
[4294701.636000] ata1: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[4294701.636000] ata1: status=0xd0 { Busy }
[4294701.636000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[4294701.636000] sda: Current: sense key: Aborted Command
[4294701.636000]     Additional sense: Scsi parity error
[4294701.636000] end_request: I/O error, dev sda, sector 0
[4294701.636000] Buffer I/O error on device sda, logical block 0
[4294704.897000]  unable to read partition table
[4294704.897000] sd 0:0:0:0: Attached scsi disk sda
[4294704.910000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[4294704.910000] Uniform CD-ROM driver Revision: 3.20
[4294704.911000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[4294705.039000] ieee1394: Initialized config rom entry `ip1394'
[4294705.040000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294705.040000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 16 (level, low) -> IRQ 169
[4294705.074000] usbcore: registered new driver usbfs
[4294705.075000] usbcore: registered new driver hub
[4294705.076000] USB Universal Host Controller Interface driver v2.3
[4294705.076000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 217
[4294705.076000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294705.076000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294705.076000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294705.076000] uhci_hcd 0000:00:1d.0: irq 217, io base 0x00009800
[4294705.076000] hub 1-0:1.0: USB hub found
[4294705.076000] hub 1-0:1.0: 2 ports detected
[4294705.116000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[169]  MMIO=[fbffb000-fbffb7ff]  Max Packet=[2048]
[4294705.177000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 209
[4294705.177000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294705.177000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294705.177000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294705.177000] uhci_hcd 0000:00:1d.1: irq 209, io base 0x0000a000
[4294705.177000] hub 2-0:1.0: USB hub found
[4294705.177000] hub 2-0:1.0: 2 ports detected
[4294705.278000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 225
[4294705.278000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294705.278000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294705.278000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294705.278000] uhci_hcd 0000:00:1d.2: irq 225, io base 0x0000a400
[4294705.278000] hub 3-0:1.0: USB hub found
[4294705.278000] hub 3-0:1.0: 2 ports detected
[4294705.379000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[4294705.379000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294705.379000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294705.379000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294705.379000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000a800
[4294705.379000] hub 4-0:1.0: USB hub found
[4294705.379000] hub 4-0:1.0: 2 ports detected
[4294705.383000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294705.481000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 217
[4294705.481000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294705.481000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294705.481000] ehci_hcd 0000:00:1d.7: debug port 1
[4294705.481000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294705.481000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294705.481000] ehci_hcd 0000:00:1d.7: irq 217, io mem 0xdfffbc00
[4294705.485000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294705.485000] hub 5-0:1.0: USB hub found
[4294705.485000] hub 5-0:1.0: 8 ports detected
[4294705.597000] ide0: I/O resource 0x1F0-0x1F7 not free.
[4294705.597000] ide0: ports already in use, skipping probe
[4294705.597000] ide1: I/O resource 0x170-0x177 not free.
[4294705.597000] ide1: ports already in use, skipping probe
[4294705.899000] usb 1-1: device not accepting address 2, error -71
[4294706.381000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800032ef37c]
[4294706.383000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[4294706.553000] usbcore: registered new driver hiddev
[4294706.583000] input: Logitech USB Receiver as /class/input/input1
[4294706.583000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[4294706.583000] usbcore: registered new driver usbhid
[4294706.583000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294709.793000] end_request: I/O error, dev sr0, sector 1429192
[4294709.793000] Buffer I/O error on device sr0, logical block 357298
[4294711.123000] end_request: I/O error, dev sr0, sector 1429192
[4294711.123000] Buffer I/O error on device sr0, logical block 357298
[4294711.511000] end_request: I/O error, dev sr0, sector 1429192
[4294711.511000] Buffer I/O error on device sr0, logical block 357298
[4294711.900000] end_request: I/O error, dev sr0, sector 1429192
[4294711.900000] Buffer I/O error on device sr0, logical block 357298
[4294712.289000] end_request: I/O error, dev sr0, sector 1429192
[4294712.289000] Buffer I/O error on device sr0, logical block 357298
[4294712.678000] end_request: I/O error, dev sr0, sector 1429192
[4294712.678000] Buffer I/O error on device sr0, logical block 357298
[4294713.308000] end_request: I/O error, dev sr0, sector 1429188
[4294713.308000] Buffer I/O error on device sr0, logical block 357297
[4294713.697000] end_request: I/O error, dev sr0, sector 1429188
[4294713.697000] Buffer I/O error on device sr0, logical block 357297
[4294714.358000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294714.580000] ISO 9660 Extensions: RRIP_1991A
[4294714.699000] loop: loaded (max 8 devices)
[4294714.718000] Registering unionfs 1.1.2
[4294714.917000] squashfs: version 3.0prerelease (2006/1/24) Phillip Lougher
[4294868.075000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 225
[4294868.075000] skge 1.3 addr 0xfbffc000 irq 225 chip Yukon-Lite rev 9
[4294868.075000] skge eth0: addr 00:11:d8:cf:49:9e
[4294905.403000] input: PC Speaker as /class/input/input2
[4294905.735000] ts: Compaq touchscreen protocol output
[4294906.473000] Real Time Clock Driver v1.12
[4294907.214000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[4294907.253000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[4294907.446000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294909.650000] hw_random: RNG not detected
[4294911.594000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294912.671000] Linux agpgart interface v0.101 (c) Dave Jones
[4294912.685000] skge eth0: enabling interface
[4294914.459000] skge eth0: Link is up at 100 Mbps, full duplex, flow control tx and rx
[4294914.766000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[4294914.766000] sdhci: Copyright(c) Pierre Ossman
[4294914.766000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 18 (level, low) -> IRQ 225
[4294914.818000] sdhci: ============== REGISTER DUMP ==============
[4294914.818000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
[4294914.818000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294914.818000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294914.818000] sdhci: Present:  0x01f20000 | Host ctl: 0x00000000
[4294914.818000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294914.818000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[4294914.818000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294914.818000] sdhci: Int enab: 0xe1ff00cf | Sig enab: 0xe1ff00cf
[4294914.818000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294914.818000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[4294914.818000] sdhci:

---

### Post by jeremytaylor on 2006-06-08
In particular is this stuff that worries me...

[4294671.636000] sda:<3>ata1: command 0x25 timeout, stat 0xd0 host_stat 0x24
[4294701.636000] ata1: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[4294701.636000] ata1: status=0xd0 { Busy }
[4294701.636000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[4294701.636000] sda: Current: sense key: Aborted Command
[4294701.636000] Additional sense: Scsi parity error
[4294701.636000] end_request: I/O error, dev sda, sector 0
[4294701.636000] Buffer I/O error on device sda, logical block 0
[4294704.897000] unable to read partition table

but if I've really managed to muck up my partition tables how am I still able to boot windows?

Anyone know if this is fixable or if I'm really stuck?

Jeremy

---

### Post by franestepona on 2006-06-09
I am not an expert in this threat, but for me looks like there is a bad sector somewhere. Have you tried to re-format the partition?

Fran

---

### Post by franestepona on 2006-06-09
Since looks like it's complaining about the sector 0, maybe a cd recovery suite could help you. The problem could be MBR. I presonally would reinstall MBR through an utility recover or the ubuntu install cd (In the manual partition edit) I am sorry i cannot help u more since i dont really know much about it. hope tha could solve the problem.

Fran

---

### Post by jeremytaylor on 2006-06-09
Okay, thanks for the help. I'll try that tonight. Still seems peculiar to me that Windows can deal with it and read all the partitions with the help of  explore2fs but Linux can't. Although it wouldn't be the first time that i've found windows being less fussy about errors. oh well. 
jeremy

---

### Post by Kaukomieli on 2006-06-09
i have a similar problem with my notebook.

it came with windows preinstalled, so i just moved the partitions around with partitionexpert and made a swap, a root and a home-partition.

windows is still running, i can format the partitions etc. - but when i try to install kubuntu the partition-manager does not see any partition on sda0.

what puzzles me is, that i was able to install kanotix on the root-partition. on the other hand kanotix was unable to format the home-partition during installation, but could access it afterwards.

very weird.

---

### Post by jeremytaylor on 2006-06-09
This really is a bit baffling. Booting with an old knoppix  cd I can see all my partitions no problem they even seem to have the right stuff on them!

I really don't know what's going wrong with this. 
jeremy

---

### Post by jeremytaylor on 2006-06-09
No luck with the rescue approach. Incidentally, although gparted can't read the partitions, both parted and fdisk see them happily... 

Any suggestions on fixing this would be much appreciated (as is the help I've had so far of course!)

And umm, how would i go about fixing an MBR? never done that before.

jeremy

---

### Post by Kaukomieli on 2006-06-10
to be honest i doubt the mbr has anything to do with this, since on my box i was able to boot, to install grub etc. but the installer was unable to see any partitions.
if you can see the contents on the disk with some old knoppix (i tried 4.5 and was able to see partitions/content, too) then its most likely a driver-issue where a bug/feature/whatever was introduced in a recent version causing these problems.

---

### Post by jeremytaylor on 2006-06-10
Ah. well that doesn't sound too great. I'm not sure I like new features that keep me in on a sunny saturday trying to fix my computer when I should be drinking pimms in the fresh air. 
jeremy

---

### Post by jeremytaylor on 2006-06-11
Well that was a long way round to get a working dapper!

First get a working breezy
Second upgrade to dapper
Third boot to dapper using your old kernel
Forth build a brand new kernel 2.6.16.something (look in the how to section for instructions on building a blazingly fast version)
Fifth have a glass of gin and tonic!

jeremy

---

### Post by Kaukomieli on 2006-06-19
nice :)

i tried that way, too - but it didn't work.

i think my error has something to do with the sda-support of the live-system, but i got an error message when trying to install from the dvd, saying something about "ped_disk_new", whatever that means.
trying to google it up now - and maybe get somewhere finally...

---

