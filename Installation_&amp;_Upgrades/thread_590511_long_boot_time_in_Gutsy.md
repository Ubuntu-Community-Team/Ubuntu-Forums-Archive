---
title: "long boot time in Gutsy"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by mummra1 on 2007-10-24
I did a clean install of Feisty.   Since then, I have made the following fixes to get things working:

1) Used ndiswrapper to get Belkin wireless up and running
2) changed /etc/usplash.conf to restore splash screen from 'black screen of death'

Now, Gutsy boots VERY slow, and takes forever to bring up the desktop after login.

Here is dmesg.  It is hanging at around the 27 second mark, right after it finds all the usb devices, or so it seems...

```

[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffe0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffe0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
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
[    0.000000] ACPI: RSDP signature @ 0xC00FF8F0 checksum 0
[    0.000000] ACPI: RSDP 000FF8F0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 0028 (r1  INTEL SOLANO70 20010907 IMA        97)
[    0.000000] ACPI: FACP 1FFF1000, 0074 (r1  INTEL SOLANO70 20010907 IMA        97)
[    0.000000] ACPI: DSDT 1FFE0000, 3315 (r1  0AAVE 0AAVEP09    60100 MSFT  100000C)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130017
[    0.000000] Kernel command line: root=UUID=50c7f1b7-e139-42bc-b2ac-90ffc3dbfc92 ro quiet splash
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 930.347 MHz processor.
[   19.124141] Console: colour VGA+ 80x25
[   19.124944] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.125970] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.170313] Memory: 508172k/524160k available (2015k kernel code, 15416k reserved, 916k data, 364k init, 0k highmem)
[   19.170337] virtual kernel memory layout:
[   19.170340]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   19.170343]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.170347]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   19.170350]     lowmem  : 0xc0000000 - 0xdffe0000   ( 511 MB)
[   19.170353]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   19.170356]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   19.170359]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   19.170367] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.170446] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.250427] Calibrating delay using timer specific routine.. 1862.16 BogoMIPS (lpj=3724332)
[   19.250483] Security Framework v1.0.0 initialized
[   19.250499] SELinux:  Disabled at boot.
[   19.250531] Mount-cache hash table entries: 512
[   19.250779] CPU: After generic identify, caps: 0387fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   19.250802] CPU: L1 I cache: 16K, L1 D cache: 16K
[   19.250808] CPU: L2 cache: 256K
[   19.250815] CPU serial number disabled.
[   19.250820] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[   19.250841] Compat vDSO mapped to ffffe000.
[   19.250869] Checking 'hlt' instruction... OK.
[   19.266617] SMP alternatives: switching to UP code
[   19.266951] Freeing SMP alternatives: 11k freed
[   19.267550] Early unpacking initramfs... done
[   19.980009] ACPI: Core revision 20070126
[   19.980240] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.983879] ACPI: setting ELCR to 0200 (from 0e00)
[   19.984217] CPU0: Intel Pentium III (Coppermine) stepping 0a
[   19.984230] SMP motherboard not detected.
[   20.090037] Brought up 1 CPUs
[   20.090330] Booting paravirtualized kernel on bare hardware
[   20.090446] Time: 20:46:53  Date: 09/24/107
[   20.090512] NET: Registered protocol family 16
[   20.090764] EISA bus registered
[   20.090786] ACPI: bus type pci registered
[   20.091410] PCI: PCI BIOS revision 2.10 entry at 0xfdba1, last bus=2
[   20.091416] PCI: Using configuration type 1
[   20.091420] Setting up standard PCI resources
[   20.097910] ACPI: EC: Look up EC in DSDT
[   20.107264] ACPI: Interpreter enabled
[   20.107274] ACPI: (supports S0 S1 S4 S5)
[   20.107310] ACPI: Using PIC for interrupt routing
[   20.119566] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.119605] PCI: Probing PCI hardware (bus 00)
[   20.119884] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   20.119892] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   20.120415] PCI: Transparent bridge - 0000:00:1e.0
[   20.120458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.120721] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   20.131179] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   20.131506] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   20.131824] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.132147] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   20.132470] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.132791] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.133110] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.133430] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.133682] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.133707] pnp: PnP ACPI init
[   20.133741] ACPI: bus type pnp registered
[   20.144343] pnp: PnP ACPI: found 16 devices
[   20.144351] ACPI: ACPI bus type pnp unregistered
[   20.144362] PnPBIOS: Disabled by ACPI PNP
[   20.144489] PCI: Using ACPI for IRQ routing
[   20.144497] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.147208] NET: Registered protocol family 8
[   20.147214] NET: Registered protocol family 20
[   20.147382] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   20.147391] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.147422] pnp: 00:0d: ioport range 0x680-0x6ff has been reserved
[   20.147437] pnp: 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   20.147444] pnp: 00:0f: iomem range 0xc0000-0xc7fff could not be reserved
[   20.147450] pnp: 00:0f: iomem range 0xcc000-0xfffff could not be reserved
[   20.147457] pnp: 00:0f: iomem range 0x100000-0x1fffffff could not be reserved
[   20.149918] Time: tsc clocksource has been installed.
[   20.178141] PCI: Bridge: 0000:00:01.0
[   20.178147]   IO window: c000-cfff
[   20.178156]   MEM window: ff800000-ff8fffff
[   20.178163]   PREFETCH window: ee900000-f69fffff
[   20.178175] PCI: Bridge: 0000:00:1e.0
[   20.178180]   IO window: d000-dfff
[   20.178188]   MEM window: ff900000-ff9fffff
[   20.178195]   PREFETCH window: f6a00000-f6afffff
[   20.178219] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.178247] NET: Registered protocol family 2
[   20.217988] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   20.218109] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   20.218688] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   20.219228] TCP: Hash tables configured (established 16384 bind 16384)
[   20.219237] TCP reno registered
[   20.230231] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   20.827801]  it is
[   21.572137] Freeing initrd memory: 7041k freed
[   21.573050] audit: initializing netlink socket (disabled)
[   21.573084] audit(1193258813.876:1): initialized
[   21.578238] VFS: Disk quotas dquot_6.5.1
[   21.578411] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.578679] io scheduler noop registered
[   21.578687] io scheduler anticipatory registered
[   21.578693] io scheduler deadline registered
[   21.578745] io scheduler cfq registered (default)
[   21.578804] Boot video device is 0000:01:00.0
[   21.579143] isapnp: Scanning for PnP cards...
[   21.932817] isapnp: No Plug & Play device found
[   22.004076] Real Time Clock Driver v1.12ac
[   22.004276] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.004412] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.004892] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.006227] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.006751] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.008388] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.008946] input: Macintosh mouse button emulation as /class/input/input0
[   22.009133] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.012581] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.012596] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.013033] mice: PS/2 mouse device common for all mice
[   22.013268] EISA: Probing bus 0 at eisa.0
[   22.013320] EISA: Detected 0 cards.
[   22.013534] TCP cubic registered
[   22.013571] NET: Registered protocol family 1
[   22.013723] Testing NMI watchdog ... OK.
[   22.093118] Using IPI No-Shortcut mode
[   22.093438]   Magic number: 11:187:802
[   22.094686] Freeing unused kernel memory: 364k freed
[   22.152705] input: AT Translated Set 2 keyboard as /class/input/input1
[   23.573763] AppArmor: AppArmor initialized<5>audit(1193258815.876:2):  type=1505 info="AppArmor initialized" pid=1177
[   23.595397] fuse init (API version 7.8)
[   23.607481] Failure registering capabilities with primary security module.
[   23.638464] ACPI: Processor [CPU1] (supports 8 throttling states)
[   25.005045] SCSI subsystem initialized
[   25.025467] libata version 2.21 loaded.
[   25.038849] ata_piix 0000:00:1f.1: version 2.11
[   25.038963] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.039190] scsi0 : ata_piix
[   25.039287] scsi1 : ata_piix
[   25.039532] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   25.039541] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   25.135245] usbcore: registered new interface driver usbfs
[   25.135313] usbcore: registered new interface driver hub
[   25.135362] usbcore: registered new device driver usb
[   25.138650] USB Universal Host Controller Interface driver v3.0
[   25.204232] ata1.00: Host Protected Area detected:
[   25.204237]  current size: 78156226 sectors
[   25.204240]  native size: 78165360 sectors
[   25.208848] ata1.00: native size increased to 78165360 sectors
[   25.208859] ata1.00: ATA-5: WDC WD400BB-53AUA1, 18.20D18, max UDMA/100
[   25.208866] ata1.00: 78165360 sectors, multi 16: LBA 
[   25.223647] ata1.00: configured for UDMA/100
[   25.420677] Floppy drive(s): fd0 is 1.44M
[   25.542559] ata2.00: ATAPI: CRD-8483B, 1.05, max UDMA/33
[   25.546566] FDC 0 is a post-1991 82077
[   25.706457] ata2.00: configured for UDMA/33
[   25.706723] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-53AU 18.2 PQ: 0 ANSI: 5
[   25.707150] scsi 1:0:0:0: CD-ROM            LG       CD-ROM CRD-8483B 1.05 PQ: 0 ANSI: 5
[   25.708316] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   25.708324] PCI: setting IRQ 9 as level-triggered
[   25.708330] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   25.708351] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   25.708359] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   25.708621] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   25.708658] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000e400
[   25.708961] usb usb1: configuration #1 chosen from 1 choice
[   25.709030] hub 1-0:1.0: USB hub found
[   25.709049] hub 1-0:1.0: 2 ports detected
[   25.750263] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   25.750330] sd 0:0:0:0: [sda] Write Protect is off
[   25.750336] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.750374] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.750518] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   25.750540] sd 0:0:0:0: [sda] Write Protect is off
[   25.750546] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.750581] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.750593]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[   25.804217] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.810979] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   25.811000] 3c59x: Donald Becker and others.
[   25.811012] 0000:02:09.0: 3Com PCI 3c905C Tornado at e0814c00.
[   25.842631] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.843055] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   25.895766] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   25.895779] Uniform CD-ROM driver Revision: 3.20
[   25.896359] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.050104] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   26.223527] usb 1-1: configuration #1 chosen from 1 choice
[   26.225477] hub 1-1:1.0: USB hub found
[   26.228370] hub 1-1:1.0: 4 ports detected
[   26.436192] Attempting manual resume
[   26.436201] swsusp: Resume From Partition 8:6
[   26.436206] PM: Checking swsusp image.
[   26.458246] PM: Resume from disk failed.
[   26.539103] usb 1-1.1: new full speed USB device using uhci_hcd and address 3
[   26.539497] kjournald starting.  Commit interval 5 seconds
[   26.539525] EXT3-fs: mounted filesystem with ordered data mode.
[   26.833041] usb 1-1.1: configuration #1 chosen from 1 choice
[   27.038665] usb 1-1.2: new full speed USB device using uhci_hcd and address 4
[   27.193711] usb 1-1.2: configuration #1 chosen from 1 choice
[   27.402366] usb 1-1.4: new full speed USB device using uhci_hcd and address 5
[   27.528400] usb 1-1.4: configuration #1 chosen from 1 choice
[  185.365443] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  185.591417] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  185.627003] intel_rng: FWH not detected
[  185.725828] Linux agpgart interface v0.102 (c) Dave Jones
[  185.736813] agpgart: Detected an Intel i815 Chipset.
[  185.741157] agpgart: AGP aperture is 64M @ 0xf8000000
[  185.916789] iTCO_vendor_support: vendor-support=0
[  185.919670] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[  185.919812] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[  185.919825] iTCO_wdt: No card detected
[  186.410710] input: PC Speaker as /class/input/input2
[  187.227317] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[  187.567565] parport_pc 00:0c: reported by Plug and Play ACPI
[  187.567626] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  188.943560] Linux video capture interface: v2.00
[  189.341151] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[  189.341162] PCI: setting IRQ 10 as level-triggered
[  189.341169] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[  189.341201] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  189.387886] usbcore: registered new interface driver libusual
[  189.837925] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[  189.844870] usbcore: registered new interface driver gspca
[  189.844884] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[  190.009604] intel8x0_measure_ac97_clock: measured 54804 usecs
[  190.009614] intel8x0: clocking to 48000
[  190.232108] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  190.232977] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  190.398863] p54: LM86 firmware
[  190.596139] Initializing USB Mass Storage driver...
[  192.401171] prism54usb: firmware upload failed!
[  192.401229] prism54usb: probe of 1-1.1:1.0 failed with error -110
[  192.401285] usbcore: registered new interface driver prism54usb
[  192.402894] scsi2 : SCSI emulation for USB Mass Storage devices
[  192.404044] usb-storage: device found at 5
[  192.404052] usb-storage: waiting for device to settle before scanning
[  192.404107] usbcore: registered new interface driver usb-storage
[  192.404115] USB Mass Storage support registered.
[  193.490296] lp0: using parport0 (interrupt-driven).
[  194.709361] ndiswrapper version 1.45 loaded (smp=yes)
[  194.836143] usb 1-1.1: reset full speed USB device using uhci_hcd and address 3
[  195.038059] ndiswrapper: driver rt2500usb (BELKIN,07/15/2004, 1.02.00.0000) loaded
[  195.715169] wlan0: ethernet device 00:11:50:88:58:c6 using NDIS driver: rt2500usb, version: 0x9, NDIS version: 0x500, vendor: 'Ralink Technology Inc.', 050D:7050.F.conf
[  195.730478] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[  195.732500] usbcore: registered new interface driver ndiswrapper
[  195.941251] Adding 2000052k swap on /dev/sda6.  Priority:-1 extents:1 across:2000052k
[  197.404075] usb-storage: device scan complete
[  197.458042] scsi 2:0:0:0: Direct-Access     Maxtor   OneTouch II      0244 PQ: 0 ANSI: 4
[  197.513978] sd 2:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[  197.567913] sd 2:0:0:0: [sdb] Write Protect is off
[  197.567926] sd 2:0:0:0: [sdb] Mode Sense: 24 00 00 00
[  197.567932] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  197.622858] sd 2:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[  197.676805] sd 2:0:0:0: [sdb] Write Protect is off
[  197.676813] sd 2:0:0:0: [sdb] Mode Sense: 24 00 00 00
[  197.676819] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  197.676826]  sdb: sdb1
[  197.703949] sd 2:0:0:0: [sdb] Attached SCSI disk
[  197.704041] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  198.634775] NET: Registered protocol family 17
[  198.965014] EXT3 FS on sda2, internal journal
[  204.581362] kjournald starting.  Commit interval 5 seconds
[  204.581563] EXT3 FS on sda5, internal journal
[  204.581574] EXT3-fs: mounted filesystem with ordered data mode.
[  205.940016] kjournald starting.  Commit interval 5 seconds
[  205.940203] EXT3 FS on sda7, internal journal
[  205.940214] EXT3-fs: mounted filesystem with ordered data mode.
[  208.849184] input: Power Button (FF) as /class/input/input4
[  208.849752] ACPI: Power Button (FF) [PWRF]
[  208.865177] input: Sleep Button (CM) as /class/input/input5
[  208.865751] ACPI: Sleep Button (CM) [SPBT]
[  209.074722] No dock devices found.
[  213.551532] ppdev: user-space parallel port driver
[  213.768740] eth0:  setting half-duplex.
[  214.217844] audit(1193273407.790:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4700 profile="/usr/sbin/cupsd"
[  214.466386] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  214.466399] apm: overridden by ACPI.
[  215.227881] Failure registering capabilities with primary security module.
[  215.837381] Bluetooth: Core ver 2.11
[  215.837630] NET: Registered protocol family 31
[  215.837637] Bluetooth: HCI device and connection manager initialized
[  215.837645] Bluetooth: HCI socket layer initialized
[  215.883406] Bluetooth: L2CAP ver 2.8
[  215.883417] Bluetooth: L2CAP socket layer initialized
[  216.097715] Bluetooth: RFCOMM socket layer initialized
[  216.097924] Bluetooth: RFCOMM TTY layer initialized
[  216.097930] Bluetooth: RFCOMM ver 1.8
[  221.394146] NET: Registered protocol family 10
[  221.394579] lo: Disabled Privacy Extensions
[  221.394821] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  225.343135] [drm] Initialized drm 1.1.0 20060810
[  225.510097] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[  225.510112] PCI: setting IRQ 11 as level-triggered
[  225.510153] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  225.512171] [drm] Initialized r128 2.5.0 20030725 on minor 0
[  225.513393] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  225.513424] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  225.513445] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  232.237677] wlan0: no IPv6 routers present


```


Any help is much appreciated.  Thanks!

---

### Post by Perpetual on 2007-10-27
Are you getting the Ubuntu progress bar during boot?  If not, you might try this tip [http://ubuntuforums.org/showpost.php?p=3568252&postcount=2](http://ubuntuforums.org/showpost.php?p=3568252&postcount=2)

It's worked for me and others.

---

### Post by mummra1 on 2007-10-29
hmmmm... 
I am getting the progress bar, but I will run the 'sudo update-usplash-theme usplash-theme-ubuntu' and see if that affects anything.

Thanks!

---

### Post by Habo on 2007-11-01
hi, mummra1,

I have similar problem:

```
Nov  1 09:40:29 habo kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov  1 09:40:29 habo kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov  1 09:40:29 habo kernel: Symbols match kernel version 2.6.22.
Nov  1 09:40:29 habo kernel: No module symbols loaded - kernel modules not enabled. 
Nov  1 09:40:29 habo kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov  1 09:40:29 habo kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  1 09:40:29 habo kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Nov  1 09:40:29 habo kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Nov  1 09:40:29 habo kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov  1 09:40:29 habo kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
Nov  1 09:40:29 habo kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Nov  1 09:40:29 habo kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Nov  1 09:40:29 habo kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Nov  1 09:40:29 habo kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov  1 09:40:29 habo kernel: [    0.000000] 1150MB HIGHMEM available.
Nov  1 09:40:29 habo kernel: [    0.000000] 896MB LOWMEM available.
Nov  1 09:40:29 habo kernel: [    0.000000] found SMP MP-table at 000f3a70
Nov  1 09:40:29 habo kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Nov  1 09:40:29 habo kernel: [    0.000000] Zone PFN ranges:
Nov  1 09:40:29 habo kernel: [    0.000000]   DMA             0 ->     4096
Nov  1 09:40:29 habo kernel: [    0.000000]   Normal       4096 ->   229376
Nov  1 09:40:29 habo kernel: [    0.000000]   HighMem    229376 ->   524016
Nov  1 09:40:29 habo kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov  1 09:40:29 habo kernel: [    0.000000]     0:        0 ->   524016
Nov  1 09:40:29 habo kernel: [    0.000000] On node 0 totalpages: 524016
Nov  1 09:40:29 habo kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov  1 09:40:29 habo kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov  1 09:40:29 habo kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov  1 09:40:29 habo kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov  1 09:40:29 habo kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov  1 09:40:29 habo kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Nov  1 09:40:29 habo kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Nov  1 09:40:29 habo kernel: [    0.000000] DMI 2.3 present.
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7B50 checksum 0
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: RSDP 000F7B50, 0014 (r0 K8M890)
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: RSDT 7FEF3040, 0034 (r1 K8M890 AWRDACPI 42302E31 AWRD        0)
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 K8M890 AWRDACPI 42302E31 AWRD        0)
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: DSDT 7FEF3180, 667C (r1 K8M890 AWRDACPI     1000 MSFT  100000E)
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: FACS 7FEF0000, 0040
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: SSDT 7FEF9900, 0248 (r1 PTLTD  POWERNOW        1  LTP        1)
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: MCFG 7FEF9BC0, 003C (r1 K8M890 AWRDACPI 42302E31 AWRD        0)
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: APIC 7FEF9840, 0074 (r1 K8M890 AWRDACPI 42302E31 AWRD        0)
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov  1 09:40:29 habo kernel: [    0.000000] Processor #0 15:11 APIC version 16
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov  1 09:40:29 habo kernel: [    0.000000] Processor #1 15:11 APIC version 16
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov  1 09:40:29 habo kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
Nov  1 09:40:29 habo kernel: [    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov  1 09:40:29 habo kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov  1 09:40:29 habo kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Nov  1 09:40:29 habo kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  1 09:40:29 habo kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
Nov  1 09:40:29 habo kernel: [    0.000000] Built 1 zonelists.  Total pages: 519923
Nov  1 09:40:29 habo kernel: [    0.000000] Kernel command line: root=UUID=6f024932-31bd-4434-bd90-53a4dcae712f ro quiet splash locale=de_DE
Nov  1 09:40:29 habo kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Nov  1 09:40:29 habo kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Nov  1 09:40:29 habo kernel: [    0.000000] mapped IOAPIC to ffffb000 (fecc0000)
Nov  1 09:40:29 habo kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  1 09:40:29 habo kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  1 09:40:29 habo kernel: [    0.000000] Initializing CPU#0
Nov  1 09:40:29 habo kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov  1 09:40:29 habo kernel: [    0.000000] Detected 2399.830 MHz processor.
Nov  1 09:40:29 habo kernel: [    0.000000] Console: colour VGA+ 80x25
Nov  1 09:40:29 habo kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  1 09:40:29 habo kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  1 09:40:29 habo kernel: [    0.000000] Memory: 2066592k/2096064k available (2015k kernel code, 28212k reserved, 916k data, 364k init, 1178560k highmem)
Nov  1 09:40:29 habo kernel: [    0.000000] virtual kernel memory layout:
Nov  1 09:40:29 habo kernel: [    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov  1 09:40:29 habo kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  1 09:40:29 habo kernel: [    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov  1 09:40:29 habo kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov  1 09:40:29 habo kernel: [    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov  1 09:40:29 habo kernel: [    0.000000]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov  1 09:40:29 habo kernel: [    0.000000]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov  1 09:40:29 habo kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov  1 09:40:29 habo kernel: [    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Nov  1 09:40:29 habo kernel: [    0.084000] Calibrating delay using timer specific routine.. 4805.20 BogoMIPS (lpj=9610407)
Nov  1 09:40:29 habo kernel: [    0.084000] Security Framework v1.0.0 initialized
Nov  1 09:40:29 habo kernel: [    0.084000] SELinux:  Disabled at boot.
Nov  1 09:40:29 habo kernel: [    0.084000] Mount-cache hash table entries: 512
Nov  1 09:40:29 habo kernel: [    0.084000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
Nov  1 09:40:29 habo kernel: [    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov  1 09:40:29 habo kernel: [    0.084000] CPU: L2 Cache: 512K (64 bytes/line)
Nov  1 09:40:29 habo kernel: [    0.084000] CPU 0(2) -> Core 0
Nov  1 09:40:29 habo kernel: [    0.084000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
Nov  1 09:40:29 habo kernel: [    0.084000] Compat vDSO mapped to ffffe000.
Nov  1 09:40:29 habo kernel: [    0.084000] Checking 'hlt' instruction... OK.
Nov  1 09:40:29 habo kernel: [    0.100000] SMP alternatives: switching to UP code
Nov  1 09:40:29 habo kernel: [    0.100000] Early unpacking initramfs... done
Nov  1 09:40:29 habo kernel: [    0.340000] ACPI: Core revision 20070126
Nov  1 09:40:29 habo kernel: [    0.340000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov  1 09:40:29 habo kernel: [    0.344000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
Nov  1 09:40:29 habo kernel: [    0.344000] SMP alternatives: switching to SMP code
Nov  1 09:40:29 habo kernel: [    0.344000] Booting processor 1/1 eip 3000
Nov  1 09:40:29 habo kernel: [    0.352000] Initializing CPU#1
Nov  1 09:40:29 habo kernel: [    0.436000] Calibrating delay using timer specific routine.. 4800.03 BogoMIPS (lpj=9600068)
Nov  1 09:40:29 habo kernel: [    0.436000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
Nov  1 09:40:29 habo kernel: [    0.436000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov  1 09:40:29 habo kernel: [    0.436000] CPU: L2 Cache: 512K (64 bytes/line)
Nov  1 09:40:29 habo kernel: [    0.436000] CPU 1(2) -> Core 1
Nov  1 09:40:29 habo kernel: [    0.436000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
Nov  1 09:40:29 habo kernel: [    0.436000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
Nov  1 09:40:29 habo kernel: [    0.436000] Total of 2 processors activated (9605.23 BogoMIPS).
Nov  1 09:40:29 habo kernel: [    0.436000] ENABLING IO-APIC IRQs
Nov  1 09:40:29 habo kernel: [    0.436000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
Nov  1 09:40:29 habo kernel: [    0.476000] Brought up 2 CPUs
Nov  1 09:40:29 habo kernel: [    0.504000] migration_cost=4000
Nov  1 09:40:29 habo kernel: [    0.504000] Booting paravirtualized kernel on bare hardware
Nov  1 09:40:29 habo kernel: [    0.504000] Time:  9:37:54  Date: 10/01/107
Nov  1 09:40:29 habo kernel: [    0.504000] NET: Registered protocol family 16
Nov  1 09:40:29 habo kernel: [    0.504000] EISA bus registered
Nov  1 09:40:29 habo kernel: [    0.504000] ACPI: bus type pci registered
Nov  1 09:40:29 habo kernel: [    0.512000] PCI: PCI BIOS revision 3.00 entry at 0xfa430, last bus=3
Nov  1 09:40:29 habo kernel: [    0.512000] PCI: Using configuration type 1
Nov  1 09:40:29 habo kernel: [    0.512000] Setting up standard PCI resources
Nov  1 09:40:29 habo kernel: [    0.516000] ACPI: EC: Look up EC in DSDT
Nov  1 09:40:29 habo kernel: [    0.520000] ACPI: Interpreter enabled
Nov  1 09:40:29 habo kernel: [    0.520000] ACPI: (supports S0 S1 S4 S5)
Nov  1 09:40:29 habo kernel: [    0.520000] ACPI: Using IOAPIC for interrupt routing
Nov  1 09:40:29 habo kernel: [    0.528000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  1 09:40:29 habo kernel: [    0.528000] PCI: Probing PCI hardware (bus 00)
Nov  1 09:40:29 habo kernel: [    0.528000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov  1 09:40:29 habo kernel: [    0.528000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
Nov  1 09:40:29 habo kernel: [    0.528000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Nov  1 09:40:29 habo kernel: [    0.580000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Nov  1 09:40:29 habo kernel: [    0.580000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Nov  1 09:40:29 habo kernel: [    0.580000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
Nov  1 09:40:29 habo kernel: [    0.580000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12)
Nov  1 09:40:29 habo kernel: [    0.580000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Nov  1 09:40:29 habo kernel: [    0.580000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Nov  1 09:40:29 habo kernel: [    0.580000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Nov  1 09:40:29 habo kernel: [    0.584000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
Nov  1 09:40:29 habo kernel: [    0.584000] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
Nov  1 09:40:29 habo kernel: [    0.584000] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Nov  1 09:40:29 habo kernel: [    0.584000] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Nov  1 09:40:29 habo kernel: [    0.584000] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
Nov  1 09:40:29 habo kernel: [    0.584000] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  1 09:40:29 habo kernel: [    0.584000] pnp: PnP ACPI init
Nov  1 09:40:29 habo kernel: [    0.584000] ACPI: bus type pnp registered
Nov  1 09:40:29 habo kernel: [    0.588000] pnp: PnP ACPI: found 15 devices
Nov  1 09:40:29 habo kernel: [    0.588000] ACPI: ACPI bus type pnp unregistered
Nov  1 09:40:29 habo kernel: [    0.588000] PnPBIOS: Disabled by ACPI PNP
Nov  1 09:40:29 habo kernel: [    0.588000] PCI: Using ACPI for IRQ routing
Nov  1 09:40:29 habo kernel: [    0.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov  1 09:40:29 habo kernel: [    0.644000] NET: Registered protocol family 8
Nov  1 09:40:29 habo kernel: [    0.644000] NET: Registered protocol family 20
Nov  1 09:40:29 habo kernel: [    0.644000] pnp: 00:01: ioport range 0x400-0x47f has been reserved
Nov  1 09:40:29 habo kernel: [    0.644000] pnp: 00:01: ioport range 0x500-0x50f has been reserved
Nov  1 09:40:29 habo kernel: [    0.644000] pnp: 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Nov  1 09:40:29 habo kernel: [    0.644000] pnp: 00:0e: iomem range 0xd0000-0xd3fff has been reserved
Nov  1 09:40:29 habo kernel: [    0.644000] pnp: 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
Nov  1 09:40:29 habo kernel: [    0.644000] pnp: 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Nov  1 09:40:29 habo kernel: [    0.644000] pnp: 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Nov  1 09:40:29 habo kernel: [    0.672000] PCI: Bridge: 0000:00:01.0
Nov  1 09:40:29 habo kernel: [    0.672000]   IO window: c000-cfff
Nov  1 09:40:29 habo kernel: [    0.672000]   MEM window: dfc00000-dfcfffff
Nov  1 09:40:29 habo kernel: [    0.672000]   PREFETCH window: dfb00000-dfbfffff
Nov  1 09:40:29 habo kernel: [    0.672000] PCI: Bridge: 0000:00:02.0
Nov  1 09:40:29 habo kernel: [    0.672000]   IO window: b000-bfff
Nov  1 09:40:29 habo kernel: [    0.672000]   MEM window: dfa00000-dfafffff
Nov  1 09:40:29 habo kernel: [    0.672000]   PREFETCH window: c0000000-cfffffff
Nov  1 09:40:29 habo kernel: [    0.672000] PCI: Bridge: 0000:00:03.0
Nov  1 09:40:29 habo kernel: [    0.672000]   IO window: d000-dfff
Nov  1 09:40:29 habo kernel: [    0.672000]   MEM window: dfe00000-dfefffff
Nov  1 09:40:29 habo kernel: [    0.672000]   PREFETCH window: dfd00000-dfdfffff
Nov  1 09:40:29 habo kernel: [    0.672000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  1 09:40:29 habo kernel: [    0.672000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
Nov  1 09:40:29 habo kernel: [    0.672000] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov  1 09:40:29 habo kernel: [    0.672000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
Nov  1 09:40:29 habo kernel: [    0.672000] PCI: Setting latency timer of device 0000:00:03.0 to 64
Nov  1 09:40:29 habo kernel: [    0.672000] NET: Registered protocol family 2
Nov  1 09:40:29 habo kernel: [    0.676000] Time: acpi_pm clocksource has been installed.
Nov  1 09:40:29 habo kernel: [    0.676000] Switched to high resolution mode on CPU 0
Nov  1 09:40:29 habo kernel: [    0.676000] Switched to high resolution mode on CPU 1
Nov  1 09:40:29 habo kernel: [    0.720000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  1 09:40:29 habo kernel: [    0.720000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov  1 09:40:29 habo kernel: [    0.720000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  1 09:40:29 habo kernel: [    0.720000] TCP: Hash tables configured (established 131072 bind 65536)
Nov  1 09:40:29 habo kernel: [    0.720000] TCP reno registered
Nov  1 09:40:29 habo kernel: [    0.736000] checking if image is initramfs... it is
Nov  1 09:40:29 habo kernel: [    1.208000] Freeing initrd memory: 7090k freed
Nov  1 09:40:29 habo kernel: [    1.208000] audit: initializing netlink socket (disabled)
Nov  1 09:40:29 habo kernel: [    1.208000] audit(1193909874.176:1): initialized
Nov  1 09:40:29 habo kernel: [    1.208000] highmem bounce pool size: 64 pages
Nov  1 09:40:29 habo kernel: [    1.212000] VFS: Disk quotas dquot_6.5.1
Nov  1 09:40:29 habo kernel: [    1.212000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  1 09:40:29 habo kernel: [    1.212000] io scheduler noop registered
Nov  1 09:40:29 habo kernel: [    1.212000] io scheduler anticipatory registered
Nov  1 09:40:29 habo kernel: [    1.212000] io scheduler deadline registered
Nov  1 09:40:29 habo kernel: [    1.212000] io scheduler cfq registered (default)
Nov  1 09:40:29 habo kernel: [    1.212000] PCI: VIA PCI bridge detected. Disabling DAC.
Nov  1 09:40:29 habo kernel: [    1.212000] Boot video device is 0000:02:00.0
Nov  1 09:40:29 habo kernel: [    1.212000] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov  1 09:40:29 habo kernel: [    1.212000] assign_interrupt_mode Found MSI capability
Nov  1 09:40:29 habo kernel: [    1.212000] Allocate Port Service[0000:00:02.0:pcie00]
Nov  1 09:40:29 habo kernel: [    1.212000] Allocate Port Service[0000:00:02.0:pcie02]
Nov  1 09:40:29 habo kernel: [    1.212000] PCI: Setting latency timer of device 0000:00:03.0 to 64
Nov  1 09:40:29 habo kernel: [    1.212000] assign_interrupt_mode Found MSI capability
Nov  1 09:40:29 habo kernel: [    1.212000] Allocate Port Service[0000:00:03.0:pcie00]
Nov  1 09:40:29 habo kernel: [    1.212000] Allocate Port Service[0000:00:03.0:pcie02]
Nov  1 09:40:29 habo kernel: [    1.212000] isapnp: Scanning for PnP cards...
Nov  1 09:40:29 habo kernel: [    1.564000] isapnp: No Plug & Play device found
Nov  1 09:40:29 habo kernel: [    1.580000] Real Time Clock Driver v1.12ac
Nov  1 09:40:29 habo kernel: [    1.580000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov  1 09:40:29 habo kernel: [    1.580000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  1 09:40:29 habo kernel: [    1.580000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov  1 09:40:29 habo kernel: [    1.584000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  1 09:40:29 habo kernel: [    1.584000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov  1 09:40:29 habo kernel: [    1.584000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov  1 09:40:29 habo kernel: [    1.584000] input: Macintosh mouse button emulation as /class/input/input0
Nov  1 09:40:29 habo kernel: [    1.584000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov  1 09:40:29 habo kernel: [    1.584000] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  1 09:40:29 habo kernel: [    1.584000] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov  1 09:40:29 habo kernel: [    1.584000] mice: PS/2 mouse device common for all mice
Nov  1 09:40:29 habo kernel: [    1.584000] EISA: Probing bus 0 at eisa.0
Nov  1 09:40:29 habo kernel: [    1.584000] EISA: Detected 0 cards.
Nov  1 09:40:29 habo kernel: [    1.584000] TCP cubic registered
Nov  1 09:40:29 habo kernel: [    1.584000] NET: Registered protocol family 1
Nov  1 09:40:29 habo kernel: [    1.584000] Using IPI No-Shortcut mode
Nov  1 09:40:29 habo kernel: [    1.584000]   Magic number: 15:637:625
Nov  1 09:40:29 habo kernel: [    1.584000] Freeing unused kernel memory: 364k freed
Nov  1 09:40:29 habo kernel: [    1.604000] input: AT Translated Set 2 keyboard as /class/input/input1
Nov  1 09:40:29 habo kernel: [    2.780000] AppArmor: AppArmor initialized<5>audit(1193909875.676:2):  type=1505 info="AppArmor initialized" pid=1366
Nov  1 09:40:29 habo kernel: [    2.784000] fuse init (API version 7.8)
Nov  1 09:40:29 habo kernel: [    2.788000] Failure registering capabilities with primary security module.
Nov  1 09:40:29 habo kernel: [    2.808000] ACPI: Fan [FAN] (on)
Nov  1 09:40:29 habo kernel: [    2.816000] ACPI: Thermal Zone [THRM] (40 C)
Nov  1 09:40:29 habo kernel: [    3.256000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Nov  1 09:40:29 habo kernel: [    3.256000] 8139cp 0000:00:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Nov  1 09:40:29 habo kernel: [    3.256000] 8139cp 0000:00:09.0: Try the "8139too" driver instead.
Nov  1 09:40:29 habo kernel: [    3.256000] 8139too Fast Ethernet driver 0.9.28
Nov  1 09:40:29 habo kernel: [    3.256000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 19 (level, low) -> IRQ 18
Nov  1 09:40:29 habo kernel: [    3.256000] eth0: RealTek RTL8139 at 0xf883c000, 00:15:58:54:4e:e6, IRQ 18
Nov  1 09:40:29 habo kernel: [    3.256000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Nov  1 09:40:29 habo kernel: [    3.268000] SCSI subsystem initialized
Nov  1 09:40:29 habo kernel: [    3.272000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 19
Nov  1 09:40:29 habo kernel: [    3.272000] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov  1 09:40:29 habo kernel: [    3.324000] usbcore: registered new interface driver usbfs
Nov  1 09:40:29 habo kernel: [    3.324000] usbcore: registered new interface driver hub
Nov  1 09:40:29 habo kernel: [    3.324000] usbcore: registered new device driver usb
Nov  1 09:40:29 habo kernel: [    3.328000] USB Universal Host Controller Interface driver v3.0
Nov  1 09:40:29 habo kernel: [    3.336000] libata version 2.21 loaded.
Nov  1 09:40:29 habo kernel: [    3.340000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov  1 09:40:29 habo kernel: [    3.340000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov  1 09:40:29 habo kernel: [    3.384000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[dffff000-dffff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov  1 09:40:29 habo kernel: [    3.392000] FDC 0 is a post-1991 82077
Nov  1 09:40:29 habo kernel: [    3.400000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Nov  1 09:40:29 habo kernel: [    3.400000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 20
Nov  1 09:40:29 habo kernel: [    3.400000] PCI: Setting latency timer of device 0000:00:10.0 to 64
Nov  1 09:40:29 habo kernel: [    3.400000] uhci_hcd 0000:00:10.0: UHCI Host Controller
Nov  1 09:40:29 habo kernel: [    3.400000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Nov  1 09:40:29 habo kernel: [    3.400000] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000f800
Nov  1 09:40:29 habo kernel: [    3.400000] usb usb1: configuration #1 chosen from 1 choice
Nov  1 09:40:29 habo kernel: [    3.400000] hub 1-0:1.0: USB hub found
Nov  1 09:40:29 habo kernel: [    3.400000] hub 1-0:1.0: 2 ports detected
Nov  1 09:40:29 habo kernel: [    3.504000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 20
Nov  1 09:40:29 habo kernel: [    3.504000] PCI: Setting latency timer of device 0000:00:10.1 to 64
Nov  1 09:40:29 habo kernel: [    3.504000] uhci_hcd 0000:00:10.1: UHCI Host Controller
Nov  1 09:40:29 habo kernel: [    3.504000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Nov  1 09:40:29 habo kernel: [    3.504000] uhci_hcd 0000:00:10.1: irq 20, io base 0x0000f700
Nov  1 09:40:29 habo kernel: [    3.504000] usb usb2: configuration #1 chosen from 1 choice
Nov  1 09:40:29 habo kernel: [    3.504000] hub 2-0:1.0: USB hub found
Nov  1 09:40:29 habo kernel: [    3.504000] hub 2-0:1.0: 2 ports detected
Nov  1 09:40:29 habo kernel: [    3.608000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 20
Nov  1 09:40:29 habo kernel: [    3.608000] PCI: Setting latency timer of device 0000:00:10.2 to 64
Nov  1 09:40:29 habo kernel: [    3.608000] uhci_hcd 0000:00:10.2: UHCI Host Controller
Nov  1 09:40:29 habo kernel: [    3.608000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Nov  1 09:40:29 habo kernel: [    3.608000] uhci_hcd 0000:00:10.2: irq 20, io base 0x0000f600
Nov  1 09:40:29 habo kernel: [    3.608000] usb usb3: configuration #1 chosen from 1 choice
Nov  1 09:40:29 habo kernel: [    3.608000] hub 3-0:1.0: USB hub found
Nov  1 09:40:29 habo kernel: [    3.608000] hub 3-0:1.0: 2 ports detected
Nov  1 09:40:29 habo kernel: [    3.712000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 20
Nov  1 09:40:29 habo kernel: [    3.712000] PCI: Setting latency timer of device 0000:00:10.3 to 64
Nov  1 09:40:29 habo kernel: [    3.712000] uhci_hcd 0000:00:10.3: UHCI Host Controller
Nov  1 09:40:29 habo kernel: [    3.712000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Nov  1 09:40:29 habo kernel: [    3.712000] uhci_hcd 0000:00:10.3: irq 20, io base 0x0000f500
Nov  1 09:40:29 habo kernel: [    3.712000] usb usb4: configuration #1 chosen from 1 choice
Nov  1 09:40:29 habo kernel: [    3.712000] hub 4-0:1.0: USB hub found
Nov  1 09:40:29 habo kernel: [    3.712000] hub 4-0:1.0: 2 ports detected
Nov  1 09:40:29 habo kernel: [    3.816000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 20
Nov  1 09:40:29 habo kernel: [    3.816000] PCI: Setting latency timer of device 0000:00:10.4 to 64
Nov  1 09:40:29 habo kernel: [    3.816000] ehci_hcd 0000:00:10.4: EHCI Host Controller
Nov  1 09:40:29 habo kernel: [    3.816000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Nov  1 09:40:29 habo kernel: [    3.816000] ehci_hcd 0000:00:10.4: irq 20, io mem 0xdfffd000
Nov  1 09:40:29 habo kernel: [    3.816000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  1 09:40:29 habo kernel: [    3.816000] usb usb5: configuration #1 chosen from 1 choice
Nov  1 09:40:29 habo kernel: [    3.816000] hub 5-0:1.0: USB hub found
Nov  1 09:40:29 habo kernel: [    3.816000] hub 5-0:1.0: 8 ports detected
Nov  1 09:40:29 habo kernel: [    3.920000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
Nov  1 09:40:29 habo kernel: [    3.920000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Nov  1 09:40:29 habo kernel: [    3.920000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 21
Nov  1 09:40:29 habo kernel: [    3.920000] VP_IDE: chipset revision 6
Nov  1 09:40:29 habo kernel: [    3.920000] VP_IDE: not 100%% native mode: will probe irqs later
Nov  1 09:40:29 habo kernel: [    3.920000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
Nov  1 09:40:29 habo kernel: [    3.920000]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:DMA, hdb:pio
Nov  1 09:40:29 habo kernel: [    3.920000]     ide1: BM-DMA at 0xf908-0xf90f, BIOS settings: hdc:pio, hdd:pio
Nov  1 09:40:29 habo kernel: [    3.920000] Probing IDE interface ide0...
Nov  1 09:40:29 habo kernel: [    4.672000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[2000000003001bf5]
Nov  1 09:40:29 habo kernel: [    4.768000] usb 5-4: new high speed USB device using ehci_hcd and address 2
Nov  1 09:40:29 habo kernel: [    4.784000] hda: ATAPI DVD DW 8X16X8X16, ATAPI CD/DVD-ROM drive
Nov  1 09:40:29 habo kernel: [    4.900000] usb 5-4: configuration #1 chosen from 1 choice
Nov  1 09:40:29 habo kernel: [    5.120000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov  1 09:40:29 habo kernel: [    5.120000] Probing IDE interface ide1...
Nov  1 09:40:29 habo kernel: [    5.692000] sata_via 0000:00:0f.0: version 2.2
Nov  1 09:40:29 habo kernel: [    5.692000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 21
Nov  1 09:40:29 habo kernel: [    5.692000] sata_via 0000:00:0f.0: routed to hard irq line 11
Nov  1 09:40:29 habo kernel: [    5.692000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Nov  1 09:40:29 habo kernel: [    5.692000] scsi0 : sata_via
Nov  1 09:40:29 habo kernel: [    5.692000] scsi1 : sata_via
Nov  1 09:40:29 habo kernel: [    5.692000] ata1: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fd02 bmdma 0x0001fa00 irq 21
Nov  1 09:40:29 habo kernel: [    5.692000] ata2: SATA max UDMA/133 cmd 0x0001fc00 ctl 0x0001fb02 bmdma 0x0001fa08 irq 21
Nov  1 09:40:29 habo kernel: [    5.700000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Nov  1 09:40:29 habo kernel: [    5.700000] Uniform CD-ROM driver Revision: 3.20
Nov  1 09:40:29 habo kernel: [    5.896000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  1 09:40:29 habo kernel: [    6.092000] ata1.00: ATA-7: WDC WD3000JS-19PDB0, 21.00M21, max UDMA/133
Nov  1 09:40:29 habo kernel: [    6.092000] ata1.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/1)
Nov  1 09:40:29 habo kernel: [    6.108000] ata1.00: configured for UDMA/133
Nov  1 09:40:29 habo kernel: [    6.312000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  1 09:40:29 habo kernel: [    6.496000] ata2.00: ATA-7: SAMSUNG SP2504C, VT100-50, max UDMA7
Nov  1 09:40:29 habo kernel: [    6.496000] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov  1 09:40:29 habo kernel: [    6.536000] ata2.00: configured for UDMA/133
Nov  1 09:40:29 habo kernel: [    6.536000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3000JS-19P 21.0 PQ: 0 ANSI: 5
Nov  1 09:40:29 habo kernel: [    6.536000] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5
Nov  1 09:40:29 habo kernel: [    6.540000] sd 0:0:0:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
Nov  1 09:40:29 habo kernel: [    6.540000] sd 0:0:0:0: [sda] Write Protect is off
Nov  1 09:40:29 habo kernel: [    6.540000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  1 09:40:29 habo kernel: [    6.540000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  1 09:40:29 habo kernel: [    6.540000] sd 0:0:0:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
Nov  1 09:40:29 habo kernel: [    6.540000] sd 0:0:0:0: [sda] Write Protect is off
Nov  1 09:40:29 habo kernel: [    6.540000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  1 09:40:29 habo kernel: [    6.540000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  1 09:40:29 habo kernel: [    6.540000]  sda: sda1 sda2 < sda5 >
Nov  1 09:40:29 habo kernel: [    6.560000] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  1 09:40:29 habo kernel: [    6.560000] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Nov  1 09:40:29 habo kernel: [    6.560000] sd 1:0:0:0: [sdb] Write Protect is off
Nov  1 09:40:29 habo kernel: [    6.560000] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  1 09:40:29 habo kernel: [    6.560000] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  1 09:40:29 habo kernel: [    6.560000] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Nov  1 09:40:29 habo kernel: [    6.560000] sd 1:0:0:0: [sdb] Write Protect is off
Nov  1 09:40:29 habo kernel: [    6.560000] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  1 09:40:29 habo kernel: [    6.560000] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  1 09:40:29 habo kernel: [    6.560000]  sdb: sdb1 sdb2 < sdb5 >
Nov  1 09:40:29 habo kernel: [    6.584000] sd 1:0:0:0: [sdb] Attached SCSI disk
Nov  1 09:40:29 habo kernel: [    6.588000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov  1 09:40:29 habo kernel: [    6.588000] sd 1:0:0:0: Attached scsi generic sg1 type 0
Nov  1 09:40:29 habo kernel: [    6.728000] Attempting manual resume
Nov  1 09:40:29 habo kernel: [    6.728000] swsusp: Resume From Partition 8:21
Nov  1 09:40:29 habo kernel: [    6.728000] PM: Checking swsusp image.
Nov  1 09:40:29 habo kernel: [    6.728000] PM: Resume from disk failed.
Nov  1 09:40:29 habo kernel: [    6.768000] kjournald starting.  Commit interval 5 seconds
Nov  1 09:40:29 habo kernel: [    6.768000] EXT3-fs: mounted filesystem with ordered data mode.
Nov  1 09:40:29 habo kernel: [   47.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  1 09:40:29 habo kernel: [   48.348000] Linux agpgart interface v0.102 (c) Dave Jones
Nov  1 09:40:29 habo kernel: [   48.368000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  1 09:40:29 habo kernel: [   48.408000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  1 09:40:29 habo kernel: [   48.484000] agpgart: Detected VIA VT3336 chipset
Nov  1 09:40:29 habo kernel: [   48.488000] agpgart: AGP aperture is 128M @ 0xd0000000
Nov  1 09:40:29 habo kernel: [   49.372000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04E8 pid 0x341B
Nov  1 09:40:29 habo kernel: [   49.372000] usbcore: registered new interface driver usblp
Nov  1 09:40:29 habo kernel: [   49.372000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Nov  1 09:40:29 habo kernel: [   49.460000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov  1 09:40:29 habo kernel: [   49.476000] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
Nov  1 09:40:29 habo kernel: [   49.476000] [fglrx] ASYNCIO init succeed!
Nov  1 09:40:29 habo kernel: [   49.476000] [fglrx] PAT is enabled successfully!
Nov  1 09:40:29 habo kernel: [   49.476000] [fglrx] module loaded - fglrx 8.42.3 [Oct 19 2007] on minor 0
Nov  1 09:40:29 habo kernel: [   49.692000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Nov  1 09:40:29 habo kernel: [   49.692000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  1 09:40:29 habo kernel: [   49.692000] PCI: Setting latency timer of device 0000:00:11.5 to 64
Nov  1 09:40:29 habo kernel: [   49.748000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
Nov  1 09:40:29 habo kernel: [   49.752000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Nov  1 09:40:29 habo kernel: [   49.756000] input: PC Speaker as /class/input/input3
Nov  1 09:40:29 habo kernel: [   51.792000] NET: Registered protocol family 10
Nov  1 09:40:29 habo kernel: [   51.796000] lo: Disabled Privacy Extensions
Nov  1 09:40:29 habo kernel: [   62.140000] eth0: no IPv6 routers present
Nov  1 09:40:29 habo kernel: [   64.984000] lp0: using parport0 (interrupt-driven).
Nov  1 09:40:29 habo kernel: [   71.812000] Adding 6080560k swap on /dev/sdb5.  Priority:-1 extents:1 across:6080560k
Nov  1 09:40:29 habo kernel: [   72.104000] EXT3 FS on sdb1, internal journal
Nov  1 09:40:29 habo kernel: [  137.720000] No dock devices found.
Nov  1 09:40:29 habo kernel: [  137.752000] input: Power Button (FF) as /class/input/input4
Nov  1 09:40:29 habo kernel: [  137.752000] ACPI: Power Button (FF) [PWRF]
Nov  1 09:40:29 habo kernel: [  137.752000] input: Power Button (CM) as /class/input/input5
Nov  1 09:40:29 habo kernel: [  137.752000] ACPI: Power Button (CM) [PWRB]
Nov  1 09:40:29 habo kernel: [  141.536000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ processors (version 2.00.00)
Nov  1 09:40:29 habo kernel: [  141.536000] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0xe
Nov  1 09:40:29 habo kernel: [  141.536000] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0x10
Nov  1 09:40:29 habo kernel: [  141.536000] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0x10
Nov  1 09:40:29 habo kernel: [  141.536000] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0x10
Nov  1 09:40:29 habo kernel: [  141.536000] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
Nov  1 09:40:52 habo kernel: [  178.496000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 23
Nov  1 09:40:53 habo kernel: [  179.364000] [fglrx] Reserve Block - 0 offset =  0X1000000 length = 0X5000
Nov  1 09:40:53 habo kernel: [  179.364000] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Nov  1 09:40:53 habo kernel: [  179.364000] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
Nov  1 09:40:53 habo kernel: [  179.364000] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
Nov  1 09:40:55 habo kernel: [  181.760000] ppdev: user-space parallel port driver
Nov  1 09:40:56 habo kernel: [  182.052000] audit(1193906455.834:3):  type=1502 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=15686 profile="/usr/sbin/cupsd"
Nov  1 09:40:59 habo kernel: [  185.476000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov  1 09:40:59 habo kernel: [  185.476000] apm: disabled - APM is not SMP safe.
Nov  1 09:41:15 habo kernel: [  200.992000] Failure registering capabilities with primary security module.
Nov  1 09:41:15 habo kernel: [  201.672000] Clocksource tsc unstable (delta = -76032137 ns)
Nov  1 09:41:19 habo kernel: [  205.600000] Bluetooth: Core ver 2.11
Nov  1 09:41:19 habo kernel: [  205.600000] NET: Registered protocol family 31
Nov  1 09:41:19 habo kernel: [  205.600000] Bluetooth: HCI device and connection manager initialized
Nov  1 09:41:19 habo kernel: [  205.600000] Bluetooth: HCI socket layer initialized
Nov  1 09:41:19 habo kernel: [  205.640000] Bluetooth: L2CAP ver 2.8
Nov  1 09:41:19 habo kernel: [  205.640000] Bluetooth: L2CAP socket layer initialized
Nov  1 09:41:20 habo kernel: [  206.244000] Bluetooth: RFCOMM socket layer initialized
Nov  1 09:41:20 habo kernel: [  206.244000] Bluetooth: RFCOMM TTY layer initialized
Nov  1 09:41:20 habo kernel: [  206.244000] Bluetooth: RFCOMM ver 1.8
```
Have you changed your usplash-theme? If yes, did that influenced something?

Habo

---

### Post by Habo on 2007-11-01
I've just tried that tip Perpetual suggested without any changes on boot speed. :(

---

### Post by mummra1 on 2007-11-01
Hi Habo,
     I think your problem may be different.  Check out your loopback interface.  Your bootup is hanging on

```
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
``` 

Definitely looks like a network related problem.  Have you looked at your /etc/network/interfaces  and ifconfig?

---

### Post by Habo on 2007-11-01
Thx for responce, mummra1

> **mummra1 said:**
> 
Definitely looks like a network related problem.  Have you looked at your /etc/network/interfaces  and ifconfig?

Yes I do and there are no errors or some strange behavior. Beside that, as I can see, there is another hang on here:

```
Nov  1 09:40:29 habo kernel: [   72.104000] EXT3 FS on sdb1, internal journal
Nov  1 09:40:29 habo kernel: [  137.720000] No dock devices found.
```

and I don't know why.

Habo

---

### Post by stevie_velvet on 2007-11-01
One way to confirm the above is to disable the network interface then restart

should be much fatser..then re-enable..see what happens

---

