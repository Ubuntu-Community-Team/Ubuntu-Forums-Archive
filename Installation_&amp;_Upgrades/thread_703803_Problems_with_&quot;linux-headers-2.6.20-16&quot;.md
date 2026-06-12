---
title: "Problems with &quot;linux-headers-2.6.20-16&quot;"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by iheartubuntu on 2008-02-21
A few days ago, on one of my other computers with Ubuntu (that has worked great for a while now) I was updating the software and it was downloading or installing "linux-headers-2.6.20-16" and the computer froze so I had no choice but to unplug it. 

Now, since then, It keeps asking for me to install it. The computer works if I dont install it, but sometimes will freeze again. When I do try to install this file "linux-headers-2.6.20-16" the details say it is preparing to replace "linux-headers-2.6.20-16" then it freezes when it starts unpacking it.

Any tips? It would be nice to fix this :) Thanks!

---

### Post by Pumalite on 2008-02-21
Post the output of:
sudo apt-get install -f

---

### Post by iheartubuntu on 2008-02-21
here it what i got..
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk-canvas1 libsmokeqt1 gdk-imlib1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-2.6.20-16
The following packages will be upgraded:
  linux-headers-2.6.20-16
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
2 not fully installed or removed.
Need to get 0B/8962kB of archives.
After unpacking 0B of additional disk space will be used.


I clicked Y to continue and now its unpacking through the terminal (but doesnt look like its doing anything)

---

### Post by iheartubuntu on 2008-02-21
It is still trying but I think its freezing up.

Right now in the terminal it says:

"Unpacking replacement linux-headers-2.6.20-16 ..."

The mouse barely works now.

The whole screen greys out, then fades back again.

---

### Post by MM23 on 2008-02-21
post the contents of the following commands:

dmesg

strace apt-get install -f

---

### Post by iheartubuntu on 2008-02-21
dmesg gets me this...

> d: 0000000020000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffe0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffe0000 - 000000001fffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fffffc0 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131040) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131040
[    0.000000]   HighMem    131040 ->   131040
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131040
[    0.000000] On node 0 totalpages: 131040
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125953 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 INSYDE                                ) @ 0x000e4110
[    0.000000] ACPI: RSDT (v001 INSYDE RSDT_000 0x00000100 ABCD 0x00010200) @ 0x1fff9c2b
[    0.000000] ACPI: FADT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1ffffac0
[    0.000000] ACPI: MADT (v001 STUPID MAPIC_00 0x30307830 ABCD 0x00010200) @ 0x1ffffb50
[    0.000000] ACPI: MCFG (v001 INSYDE MCFG_000 0x30303030 0000 0x30303030) @ 0x1ffffbc0
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030522) @ 0x1fff9e3b
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x1fff9c63
[    0.000000] ACPI: DSDT (v001 INSYDE SONOMA   0x00000001 INTL 0x02002036) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff00000)
[    0.000000] Detected 1862.011 MHz processor.
[   22.039093] Built 1 zonelists.  Total pages: 130017
[   22.039097] Kernel command line: find=/wubi/boot/linux ro quiet splash
[   22.039253] mapped APIC to ffffd000 (fee00000)
[   22.039255] mapped IOAPIC to ffffc000 (fec00000)
[   22.039258] Enabling fast FPU save and restore... done.
[   22.039261] Enabling unmasked SIMD FPU exception support... done.
[   22.039270] Initializing CPU#0
[   22.039337] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   22.040520] Console: colour VGA+ 80x25
[   22.040682] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.040880] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.052483] Memory: 507792k/524160k available (2019k kernel code, 15756k reserved, 902k data, 328k init, 0k highmem)
[   22.052493] virtual kernel memory layout:
[   22.052494]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   22.052495]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.052496]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   22.052497]     lowmem  : 0xc0000000 - 0xdffe0000   ( 511 MB)
[   22.052498]       .init : 0xc03e1000 - 0xc0433000   ( 328 kB)
[   22.052499]       .data : 0xc02f8e4a - 0xc03da6d4   ( 902 kB)
[   22.052500]       .text : 0xc0100000 - 0xc02f8e4a   (2019 kB)
[   22.052503] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.112209] Calibrating delay using timer specific routine.. 3726.44 BogoMIPS (lpj=1863221)
[   22.112251] Security Framework v1.0.0 initialized
[   22.112257] SELinux:  Disabled at boot.
[   22.112275] Mount-cache hash table entries: 512
[   22.112402] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[   22.112413] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.112416] CPU: L2 cache: 2048K
[   22.112419] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[   22.112428] Compat vDSO mapped to ffffe000.
[   22.112431] Remapping vsyscall page to ffffe000
[   22.112441] Checking 'hlt' instruction... OK.
[   22.116282] SMP alternatives: switching to UP code
[   22.116416] Freeing SMP alternatives: 9k freed
[   22.116544] Early unpacking initramfs... done
[   22.439516] ACPI: Core revision 20060707
[   22.439738] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   22.452318] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[   22.452342] Total of 1 processors activated (3726.44 BogoMIPS).
[   22.452530] ENABLING IO-APIC IRQs
[   22.452727] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.564398] Brought up 1 CPUs
[   22.564637] Booting paravirtualized kernel on bare hardware
[   22.564719] Time: 15:48:51  Date: 01/21/108
[   22.564746] NET: Registered protocol family 16
[   22.564826] EISA bus registered
[   22.564830] ACPI: bus type pci registered
[   22.565144] PCI: PCI BIOS revision 2.10 entry at 0xeafc4, last bus=6
[   22.565146] PCI: Using configuration type 1
[   22.565148] Setting up standard PCI resources
[   22.570699] ACPI: Interpreter enabled
[   22.570701] ACPI: Using IOAPIC for interrupt routing
[   22.571488] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.571492] PCI: Probing PCI hardware (bus 00)
[   22.572830] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   22.572835] PCI quirk: region 1300-133f claimed by ICH6 GPIO
[   22.573088] Boot video device is 0000:01:00.0
[   22.573708] PCI: Transparent bridge - 0000:00:1e.0
[   22.573774] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[   22.573776] Please report the result to linux-kernel to fix this permanently
[   22.573819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.581571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   22.581948] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   22.582855] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   22.583700] ACPI: PCI Interrupt Link [LNKA] (IRQs 10) *11
[   22.583911] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[   22.584123] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[   22.584341] ACPI: PCI Interrupt Link [LNKD] (IRQs *10)
[   22.584552] ACPI: PCI Interrupt Link [LNKE] (IRQs 10) *7
[   22.584765] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[   22.584979] ACPI: PCI Interrupt Link [LNKG] (IRQs 10) *0, disabled.
[   22.585190] ACPI: PCI Interrupt Link [LNKH] (IRQs 10) *5
[   22.586113] ACPI: Power Resource [QFAN] (off)
[   22.586207] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.586215] pnp: PnP ACPI init
[   22.587661] pnp: PnP ACPI: found 9 devices
[   22.587665] PnPBIOS: Disabled by ACPI PNP
[   22.587712] PCI: Using ACPI for IRQ routing
[   22.587714] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.598155] NET: Registered protocol family 8
[   22.598157] NET: Registered protocol family 20
[   22.598508] PCI: Bridge: 0000:00:01.0
[   22.598510]   IO window: c000-dfff
[   22.598514]   MEM window: c0000000-cfffffff
[   22.598517]   PREFETCH window: 90000000-9fffffff
[   22.598521] PCI: Bridge: 0000:00:1c.0
[   22.598524]   IO window: a000-bfff
[   22.598530]   MEM window: bc000000-bfffffff
[   22.598534]   PREFETCH window: 8c000000-8fffffff
[   22.598542] PCI: Bus 7, cardbus bridge: 0000:06:06.0
[   22.598544]   IO window: 00008000-000080ff
[   22.598549]   IO window: 00008400-000084ff
[   22.598555]   PREFETCH window: 84000000-87ffffff
[   22.598560]   MEM window: b8000000-bbffffff
[   22.598565] PCI: Bridge: 0000:00:1e.0
[   22.598568]   IO window: 8000-9fff
[   22.598574]   MEM window: b4000000-bbffffff
[   22.598579]   PREFETCH window: 84000000-8bffffff
[   22.598593] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.598598] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.598619] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   22.598625] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.598638] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.598653] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 17 (level, low) -> IRQ 17
[   22.598677] NET: Registered protocol family 2
[   22.608326] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   22.608400] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   22.608512] TCP bind hash table entries: 8192 (order: 4, 98304 bytes)
[   22.608570] TCP: Hash tables configured (established 16384 bind 8192)
[   22.608572] TCP reno registered
[   22.611373] checking if image is initramfs... it is
[   23.244486] Freeing initrd memory: 7517k freed
[   23.244937] audit: initializing netlink socket (disabled)
[   23.244954] audit(1203608932.392:1): initialized
[   23.245117] VFS: Disk quotas dquot_6.5.1
[   23.245138] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.245191] io scheduler noop registered
[   23.245194] io scheduler anticipatory registered
[   23.245196] io scheduler deadline registered
[   23.245208] io scheduler cfq registered (default)
[   23.245480] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.245510] assign_interrupt_mode Found MSI capability
[   23.245513] Allocate Port Service[0000:00:01.0:pcie00]
[   23.245594] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.245647] assign_interrupt_mode Found MSI capability
[   23.245650] Allocate Port Service[0000:00:1c.0:pcie00]
[   23.245677] Allocate Port Service[0000:00:1c.0:pcie02]
[   23.245838] isapnp: Scanning for PnP cards...
[   23.602044] isapnp: No Plug & Play device found
[   23.622173] Real Time Clock Driver v1.12ac
[   23.622231] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.622785] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[   23.622794] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   23.622856] mice: PS/2 mouse device common for all mice
[   23.623343] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.623494] input: Macintosh mouse button emulation as /class/input/input0
[   23.623525] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   23.623529] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   23.623751] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.625875] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.625918] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.625983] EISA: Probing bus 0 at eisa.0
[   23.625990] Cannot allocate resource for EISA slot 1
[   23.626000] Cannot allocate resource for EISA slot 4
[   23.626003] Cannot allocate resource for EISA slot 5
[   23.626012] Cannot allocate resource for EISA slot 8
[   23.626014] EISA: Detected 0 cards.
[   23.656064] TCP cubic registered
[   23.656075] NET: Registered protocol family 1
[   23.656096] Using IPI No-Shortcut mode
[   23.656154] ACPI: (supports S0 S3 S4 S5)
[   23.656202]   Magic number: 12:929:841
[   23.656252]   hash matches device ptyu7
[   23.656262]   hash matches device ptyra
[   23.656309] Time: tsc clocksource has been installed.
[   23.656461] Freeing unused kernel memory: 328k freed
[   23.662974] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.833621] md: raid1 personality registered for level 1
[   24.836103] md: raid0 personality registered for level 0
[   24.839977] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   24.852356] SCSI subsystem initialized
[   24.856871] libata version 2.20 loaded.
[   24.869653] usbcore: registered new interface driver usbfs
[   24.869685] usbcore: registered new interface driver hub
[   24.869729] usbcore: registered new device driver usb
[   24.870532] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   24.870544] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.870548] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.870593] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   24.870623] ehci_hcd 0000:00:1d.7: debug port 1
[   24.870629] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.870639] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd0000400
[   24.874514] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.874613] usb usb1: configuration #1 chosen from 1 choice
[   24.874652] hub 1-0:1.0: USB hub found
[   24.874656] hub 1-0:1.0: 8 ports detected
[   24.978833] USB Universal Host Controller Interface driver v3.0
[   24.978879] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   24.978888] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.978892] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.978926] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   24.978951] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001200
[   24.979051] usb usb2: configuration #1 chosen from 1 choice
[   24.979086] hub 2-0:1.0: USB hub found
[   24.979091] hub 2-0:1.0: 2 ports detected
[   25.080676] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   25.080683] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.080687] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.080717] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   25.080744] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001220
[   25.080842] usb usb3: configuration #1 chosen from 1 choice
[   25.080874] hub 3-0:1.0: USB hub found
[   25.080879] hub 3-0:1.0: 2 ports detected
[   25.182477] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   25.182485] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.182489] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.182520] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   25.182547] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000e380
[   25.182643] usb usb4: configuration #1 chosen from 1 choice
[   25.182676] hub 4-0:1.0: USB hub found
[   25.182682] hub 4-0:1.0: 2 ports detected
[   25.284284] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   25.284292] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   25.284295] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   25.284325] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   25.284348] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e3a0
[   25.284444] usb usb5: configuration #1 chosen from 1 choice
[   25.284476] hub 5-0:1.0: USB hub found
[   25.284482] hub 5-0:1.0: 0 ports detected
[   25.388861] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.391570] usbcore: registered new interface driver libusual
[   25.394879] Initializing USB Mass Storage driver...
[   25.394905] usbcore: registered new interface driver usb-storage
[   25.394907] USB Mass Storage support registered.
[   25.406608] ata_piix 0000:00:1f.1: version 2.10ac1
[   25.406628] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[   25.406645] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.406685] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[   25.406711] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[   25.406732] scsi0 : ata_piix
[   25.713889] ata1.00: ATAPI, max UDMA/33
[   25.869557] ata1.00: configured for UDMA/33
[   25.869563] scsi1 : ata_piix
[   26.031825] ATA: abnormal status 0x7F on port 0x00010177
[   26.033726] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-840S  1.00 PQ: 0 ANSI: 5
[   26.034435] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[   26.034439] ata_piix 0000:00:1f.2: invalid MAP value 0
[   26.034458] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 16 (level, low) -> IRQ 16
[   26.034472] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   26.034494] ata3: SATA max UDMA/133 cmd 0x00015800 ctl 0x00015402 bmdma 0x00014800 irq 16
[   26.034515] ata4: SATA max UDMA/133 cmd 0x00015000 ctl 0x00014c02 bmdma 0x00014808 irq 16
[   26.034523] scsi2 : ata_piix
[   26.189822] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   26.189825] ata3.00: ATA-6: TOSHIBA MK8025GAS, KA022K, max UDMA/100
[   26.189828] ata3.00: 156301488 sectors, multi 16: LBA 
[   26.189830] ata3.00: applying bridge limits
[   26.193810] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   26.193813] ata3.00: configured for UDMA/100
[   26.193817] scsi3 : ata_piix
[   26.356193] ATA: abnormal status 0x7F on port 0x00015007
[   26.356265] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK8025GA KA02 PQ: 0 ANSI: 5
[   26.356341] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   26.356352] sda: Write Protect is off
[   26.356353] sda: Mode Sense: 00 3a 00 00
[   26.356367] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.356415] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   26.356423] sda: Write Protect is off
[   26.356425] sda: Mode Sense: 00 3a 00 00
[   26.356439] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.356442]  sda: sda1
[   26.408067] sd 2:0:0:0: Attached scsi disk sda
[   26.497970] JFS: nTxBlock = 4030, nTxLock = 32242
[   26.506227] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   26.506415] SGI XFS Quota Management subsystem
[   26.523878] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   26.528827] fuse init (API version 7.8)
[   26.532478] loop: loaded (max 8 devices)
[   26.536608] Registering unionfs 20060916-2203
[   26.536611] unionfs: debugging is not enabled
[   26.540436] squashfs: version 3.2-UBUNTU (2007/08/29) Phillip Lougher
[   26.558787] Capability LSM initialized
[   26.585245] ACPI: Transitioning device [FAN] to D3
[   26.585248] ACPI: Transitioning device [FAN] to D3
[   26.585251] ACPI: Fan [FAN] (off)
[   26.588989] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   26.588995] ACPI: Processor [CPU0] (supports 8 throttling states)
[   26.589002] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   26.591496] ACPI: Thermal Zone [THRM] (62 C)
[   27.108243] b44.c:v1.01 (Jun 16, 2006)
[   27.108270] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 20
[   27.111790] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0b:5d:c6:a2:f9
[   27.136331] ieee1394: Initialized config rom entry `ip1394'
[   27.137660] ACPI: PCI Interrupt 0000:06:06.2[C] -> GSI 19 (level, low) -> IRQ 20
[   27.209727] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[b4000000-b40007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   27.262446] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   27.262467] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   27.273174] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   27.273179] Uniform CD-ROM driver Revision: 3.20
[   27.273236] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.140000] Time: acpi_pm clocksource has been installed.
[    5.598000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.598000] EXT3-fs: write access will be enabled during recovery.
[    6.306000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000e10000e5dd9]
[    7.075000] kjournald starting.  Commit interval 5 seconds
[    7.075000] EXT3-fs: recovery complete.
[    7.075000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.206000] EXT3 FS on loop0, internal journal
[   20.705000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.945000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.032000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.060000] intel_rng: FWH not detected
[   21.095000] agpgart: Detected an Intel 915GM Chipset.
[   21.128000] iTCO_vendor_support: vendor-support=0
[   21.129000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   21.129000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   21.129000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.142000] agpgart: AGP aperture is 256M @ 0x0
[   21.333000] ACPI: PCI Interrupt 0000:06:06.3[A] -> GSI 17 (level, low) -> IRQ 17
[   21.518000] Yenta: CardBus bridge found at 0000:06:06.0 [10cf:12d2]
[   21.518000] Yenta: Enabling burst memory read transactions
[   21.518000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   21.518000] Yenta: Routing CardBus interrupts to ISA
[   21.518000] Yenta TI: socket 0000:06:06.0, mfunc 0x01621b22, devctl 0x44
[   21.549000] ieee80211_crypt: registered algorithm 'NULL'
[   21.553000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.553000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.655000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   21.655000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.741000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   21.741000] Socket status: 30000006
[   21.741000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   21.741000] pcmcia: parent PCI bridge I/O window: 0x8000 - 0x9fff
[   21.741000] cs: IO port probe 0x8000-0x9fff: clean.
[   21.742000] pcmcia: parent PCI bridge Memory window: 0xb4000000 - 0xbbffffff
[   21.742000] pcmcia: parent PCI bridge Memory window: 0x84000000 - 0x8bffffff
[   21.749000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 18 (level, low) -> IRQ 21
[   21.766000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   21.829000] sdhci: Secure Digital Host Controller Interface driver
[   21.829000] sdhci: Copyright(c) Pierre Ossman
[   21.891000] input: PS/2 Mouse as /class/input/input2
[   21.910000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   22.176000] ipw2200: Detected geography ZZB (11 802.11bg channels, 13 802.11a channels)
[   22.176000] sdhci: SDHCI controller found at 0000:06:06.4 [104c:8034] (rev 0)
[   22.176000] ACPI: PCI Interrupt 0000:06:06.4[A] -> GSI 17 (level, low) -> IRQ 17
[   22.176000] mmc0: SDHCI at 0xb400a000 irq 17 DMA
[   22.176000] mmc1: SDHCI at 0xb400a100 irq 17 DMA
[   22.176000] mmc2: SDHCI at 0xb400a200 irq 17 DMA
[   22.225000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   22.243000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.243000] cs: IO port probe 0x820-0x8ff: clean.
[   22.244000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.245000] cs: IO port probe 0xa00-0xaff: clean.
[   22.427000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
[   22.427000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   23.238000] intel8x0_measure_ac97_clock: measured 50303 usecs
[   23.238000] intel8x0: clocking to 48000
[   23.439000] lp: driver loaded but no devices found
[   23.662000] EXT3 FS on loop0, internal journal
[   24.773000] kjournald starting.  Commit interval 5 seconds
[   24.774000] EXT3 FS on loop1, internal journal
[   24.774000] EXT3-fs: mounted filesystem with ordered data mode.
[   26.828000] Using specific hotkey driver
[   26.844000] ACPI: Video Device [PEGD] (multi-head: yes  rom: no  post: no)
[   26.933000] No dock devices found.
[   26.980000] ACPI: AC Adapter [ACAD] (off-line)
[   27.028000] input: Power Button (FF) as /class/input/input4
[   27.031000] ACPI: Power Button (FF) [PWRF]
[   27.067000] input: Lid Switch as /class/input/input5
[   27.070000] ACPI: Lid Switch [LID]
[   27.107000] input: Power Button (CM) as /class/input/input6
[   27.110000] ACPI: Power Button (CM) [PWRB]
[   27.124000] ibm_acpi: ec object not found
[   27.139000] ACPI: Battery Slot [BAT1] (battery present)
[   27.209000] pcc_acpi: loading...
[   36.206000] ppdev: user-space parallel port driver
[   38.753000] [drm] Initialized drm 1.1.0 20060810
[   38.808000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.810000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   41.087000] [drm] Setting GART location based on new memory map
[   41.089000] [drm] Loading R300 Microcode
[   41.089000] [drm] writeback test succeeded in 1 usecs
[   41.719000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   41.719000] apm: overridden by ACPI.
[   43.057000] Bluetooth: Core ver 2.11
[   43.057000] NET: Registered protocol family 31
[   43.057000] Bluetooth: HCI device and connection manager initialized
[   43.057000] Bluetooth: HCI socket layer initialized
[   43.158000] Bluetooth: L2CAP ver 2.8
[   43.158000] Bluetooth: L2CAP socket layer initialized
[   43.259000] Bluetooth: RFCOMM socket layer initialized
[   43.259000] Bluetooth: RFCOMM TTY layer initialized
[   43.259000] Bluetooth: RFCOMM ver 1.8
[   68.216000] NET: Registered protocol family 10
[   68.216000] lo: Disabled Privacy Extensions
[   68.217000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.966000] eth1: no IPv6 routers present
[  340.602000] NET: Registered protocol family 17
[  340.682000] ieee80211_crypt: registered algorithm 'WEP'
[  358.305000] eth1: no IPv6 routers present


re-edited with sudo command

---

### Post by iheartubuntu on 2008-02-21
Here is the results from the strace...

>   execve("/usr/bin/apt-get", ["apt-get", "install", "-f"], [/* 34 vars */]) = 0
brk(0)                                  = 0x806a000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f16000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=65444, ...}) = 0
mmap2(NULL, 65444, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f06000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapt-pkg-libc6.4-6.so.3.53", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p,\2\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=852540, ...}) = 0
mmap2(NULL, 851904, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e36000
mmap2(0xb7f04000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xce) = 0xb7f04000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\31\4"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=929648, ...}) = 0
mmap2(NULL, 956068, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d4c000
mmap2(0xb7e2b000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xde) = 0xb7e2b000
mmap2(0xb7e30000, 22180, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7e30000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P4\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=153424, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d4b000
mmap2(NULL, 155776, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d24000
mmap2(0xb7d49000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x24) = 0xb7d49000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\34\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=42796, ...}) = 0
mmap2(NULL, 45892, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d18000
mmap2(0xb7d23000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa) = 0xb7d23000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0`\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1307104, ...}) = 0
mmap2(NULL, 1312164, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bd7000
mmap2(0xb7d12000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13b) = 0xb7d12000
mmap2(0xb7d15000, 9636, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7d15000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7bd6000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7bd68e0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7d12000, 4096, PROT_READ)   = 0
mprotect(0xb7e2b000, 12288, PROT_READ)  = 0
munmap(0xb7f06000, 65444)               = 0
brk(0)                                  = 0x806a000
brk(0x808b000)                          = 0x808b000
open("/dev/null", O_WRONLY|O_CREAT|O_TRUNC|O_LARGEFILE, 0666) = 3
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=2586, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f15000
read(4, "# Locale name alias data base.\n#"..., 4096) = 2586
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb7f15000, 4096)                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=391, ...}) = 0
mmap2(NULL, 391, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f15000
close(4)                                = 0
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=25460, ...}) = 0
mmap2(NULL, 25460, PROT_READ, MAP_SHARED, 4, 0) = 0xb7f0e000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap2(NULL, 23, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f0d000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
mmap2(NULL, 59, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f0c000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
mmap2(NULL, 155, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f0b000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
mmap2(NULL, 77, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f0a000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap2(NULL, 34, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f09000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
close(4)                                = 0
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=52, ...}) = 0
mmap2(NULL, 52, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f08000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0
mmap2(NULL, 286, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f07000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=880094, ...}) = 0
mmap2(NULL, 880094, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7aff000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=2451, ...}) = 0
mmap2(NULL, 2451, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f06000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap2(NULL, 54, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7afe000
close(4)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=238336, ...}) = 0
mmap2(NULL, 238336, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7ac3000
close(4)                                = 0
stat64("/var/lib/apt/.", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/etc/apt/apt.conf.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/apt/apt.conf.d/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 4
fstat64(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
getdents64(4, /* 10 entries */, 4096)   = 336
stat64("/etc/apt/apt.conf.d/99update-notifier", {st_mode=S_IFREG|0644, st_size=116, ...}) = 0
stat64("/etc/apt/apt.conf.d/10periodic", {st_mode=S_IFREG|0644, st_size=129, ...}) = 0
stat64("/etc/apt/apt.conf.d/50unattended-upgrades", {st_mode=S_IFREG|0644, st_size=227, ...}) = 0
stat64("/etc/apt/apt.conf.d/01ubuntu", {st_mode=S_IFREG|0644, st_size=179, ...}) = 0
stat64("/etc/apt/apt.conf.d/70debconf", {st_mode=S_IFREG|0644, st_size=182, ...}) = 0
stat64("/etc/apt/apt.conf.d/00trustcdrom", {st_mode=S_IFREG|0644, st_size=40, ...}) = 0
stat64("/etc/apt/apt.conf.d/20archive", {st_mode=S_IFREG|0644, st_size=86, ...}) = 0
getdents64(4, /* 0 entries */, 4096)    = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/00trustcdrom", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT::Authentication::TrustCDROM "..., 8191) = 40
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/01ubuntu", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT\n{\n  NeverAutoRemove  \n  { \n\t"..., 8191) = 179
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/10periodic", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT::Periodic::Update-Package-Li"..., 8191) = 129
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/20archive", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT::Archives::MaxAge \"30\";\nAPT:"..., 8191) = 86
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/50unattended-upgrades", O_RDONLY|O_LARGEFILE) = 4
read(4, "// allowed (origin, archive) pai"..., 8191) = 227
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/70debconf", O_RDONLY|O_LARGEFILE) = 4
read(4, "// Pre-configure all packages wi"..., 8191) = 182
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/99update-notifier", O_RDONLY|O_LARGEFILE) = 4
read(4, "DPkg::Post-Invoke {\"if [ -d /var"..., 8191) = 116
read(4, "", 8191)                       = 0
close(4)                                = 0
stat64("/etc/apt/apt.conf", 0xbfcf4730) = -1 ENOENT (No such file or directory)
stat64("/var/lib/dpkg/status", {st_mode=S_IFREG|0644, st_size=1463470, ...}) = 0
stat64("/usr/bin/dpkg", {st_mode=S_IFREG|0755, st_size=340600, ...}) = 0
stat64("/etc/debian_version", {st_mode=S_IFREG|0644, st_size=4, ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
rt_sigaction(SIGPIPE, {SIG_IGN}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGWINCH, {0x804cb90, [WINCH], SA_RESTART}, {SIG_DFL}, 8) = 0
ioctl(1, TIOCGWINSZ, {ws_row=24, ws_col=80, ws_xpixel=0, ws_ypixel=0}) = 0
open("/var/lib/dpkg/lock", O_RDWR|O_CREAT|O_TRUNC, 0640) = 4
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(4, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=0, len=0}) = 0
open("/var/lib/dpkg/updates/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 5
fstat64(5, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(5, F_SETFD, FD_CLOEXEC)         = 0
getdents64(5, /* 4 entries */, 4096)    = 104
close(5)                                = 0
close(4)                                = 0
write(2, "E: ", 3E: )                      = 3
write(2, "dpkg was interrupted, you must m"..., 90dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. ) = 90
write(2, "\n", 1
)                       = 1
close(3)                                = 0
exit_group(100)                         = ?
Process 7455 detached


re-edited using sudo

---

### Post by Pumalite on 2008-02-21
sudo

---

### Post by iheartubuntu on 2008-02-21
sorry. i re-edited both of the above and used the sudo command

---

### Post by iheartubuntu on 2008-02-21
Im stuck on this. I tried to uninstall some software and install some other software and nothing works because its trying to unpack "linux-headers-2.6.20-16". :|

Would anyone have any suggestions? Thanks.

---

### Post by Pumalite on 2008-02-22
Post:
uname -a

---

### Post by iheartubuntu on 2008-02-22
Thanks for the help. "uname -a"gets me...

Linux ubuntu 2.6.20-16-lowlatency #2 SMP PREEMPT Fri Feb 1 03:06:51 UTC 2008 i686 GNU/Linux

---

### Post by Pumalite on 2008-02-22
Try:
sudo apt-get install linux-headers-`uname -r`

---

### Post by iheartubuntu on 2008-02-22
I then get this...

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk-canvas1 libsmokeqt1 gdk-imlib1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-2.6.20-16
The following NEW packages will be installed:
  linux-headers-2.6.20-16-lowlatency
The following packages will be upgraded:
  linux-headers-2.6.20-16
1 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
2 not fully installed or removed.
Need to get 849kB/9811kB of archives.
After unpacking 7234kB of additional disk space will be used.
Do you want to continue [Y/n]?


---

### Post by iheartubuntu on 2008-02-22
I clicked Y to continue and this is where it hangs up on me. Anytime it starts unpacking that "linux-headers-2.6.20-16".

I will note that it did do something new this time.

It downloaded the linux low latency file, but didnt have a chance to install it because the system is freezing up while trying to unpack the regular linux headers file.

---

### Post by dstew on 2008-02-22
In your strace output I see> you must manually run 'dpkg --configure -a' to correct the problemDid you try this? You might need to use sudo.

---

### Post by iheartubuntu on 2008-02-22
Maybe this will help...

dpkg: dependency problems prevent configuration of linux-headers-2.6.20-16-generic:
 linux-headers-2.6.20-16-generic depends on linux-headers-2.6.20-16; however:
  Package linux-headers-2.6.20-16 is not installed.
dpkg: error processing linux-headers-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.20-16-generic

---

### Post by Pumalite on 2008-02-22
You might have to force remove the package and then reinstall it:
sudo dpkg --remove --force-remove-reinstreq linux-headers-2.6.20-16-generic

---

### Post by iheartubuntu on 2008-02-22
dpkg: dependency problems prevent removal of linux-headers-2.6.20-16-generic:
 linux-headers-generic depends on linux-headers-2.6.20-16-generic.
dpkg: error processing linux-headers-2.6.20-16-generic (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-2.6.20-16-generic

---

### Post by Pumalite on 2008-02-22
Somebody better than I, lets hope, chimes in.

---

### Post by iheartubuntu on 2008-02-22
I was considering going back to the original config file, but since that particular Ubuntu is running thru Wubi on my XP system... well, XP just took a nose dive so I'm going to install only Ubuntu on that computer now.

---

### Post by Pumalite on 2008-02-22
So you turned out better off at the end. Good luck.

---

