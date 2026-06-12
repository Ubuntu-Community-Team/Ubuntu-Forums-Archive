---
title: "Insert CD - Xubuntu 7.04 Freezes"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by 8oluf7 on 2007-09-10
I have installed Xubuntu on a 1999-vintage Compaq Presario 5441, which uses an AMD K6 CPU and a SiS chipset. I had to add 'irqpoll' to the kernel command line to get the thing to boot. The mouse froze - but I found a solution on this Forum: upgrade to the latest kernel from  the command line.

Now my problem is that when I insert a CD into the CD-ROM drive the system freezes. The drive light is permanently on, the mouse cursor is frozen and I have to use Alt+SysRq and R,S,E,I,U,B to reboot the system.

If I examine fstab I get:
```
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sda1 
UUID=c28aba18-6268-42ad-8a67-78b016a2cad9 /               ext3    defaults,errors=remount-ro 0       1 
# /dev/sda5 
UUID=c8a436f7-24d8-4956-862d-536d80afaf36 none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0 
```
The hard and optical drives are identified as 's' - which I thought meant SCSI - and they're definitely IDE.

Running dmesg gives:
```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000] sanitize start 
[    0.000000] sanitize end 
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1 
[    0.000000] copy_e820_map() type is E820_RAM 
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2 
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2 
[    0.000000] copy_e820_map() start: 0000000000100000 size: 00000000176f0000 end: 00000000177f0000 type: 1 
[    0.000000] copy_e820_map() type is E820_RAM 
[    0.000000] copy_e820_map() start: 00000000177f0000 size: 0000000000003000 end: 00000000177f3000 type: 4 
[    0.000000] copy_e820_map() start: 00000000177f3000 size: 000000000000d000 end: 0000000017800000 type: 3 
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000177f0000 (usable) 
[    0.000000]  BIOS-e820: 00000000177f0000 - 00000000177f3000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 00000000177f3000 - 0000000017800000 (ACPI data) 
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved) 
[    0.000000] 0MB HIGHMEM available. 
[    0.000000] 375MB LOWMEM available. 
[    0.000000] Entering add_active_range(0, 0, 96240) 0 entries of 256 used 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA             0 ->     4096 
[    0.000000]   Normal       4096 ->    96240 
[    0.000000]   HighMem     96240 ->    96240 
[    0.000000] early_node_map[1] active PFN ranges 
[    0.000000]     0:        0 ->    96240 
[    0.000000] On node 0 totalpages: 96240 
[    0.000000]   DMA zone: 32 pages used for memmap 
[    0.000000]   DMA zone: 0 pages reserved 
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0 
[    0.000000]   Normal zone: 719 pages used for memmap 
[    0.000000]   Normal zone: 91425 pages, LIFO batch:31 
[    0.000000]   HighMem zone: 0 pages used for memmap 
[    0.000000] DMI 2.1 present. 
[    0.000000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f6a10 
[    0.000000] ACPI: RSDT (v001 GBT    AWRDACPI 0x30302e31 AWRD 0x00000000) @ 0x177f3000 
[    0.000000] ACPI: FADT (v001 GBT    AWRDACPI 0x30302e31 AWRD 0x00000000) @ 0x177f3040 
[    0.000000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000a) @ 0x00000000 
[    0.000000] ACPI: PM-Timer IO Port: 0x5008 
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 17800000:e87f0000) 
[    0.000000] Detected 474.985 MHz processor. 
[   38.702861] Built 1 zonelists.  Total pages: 95489 
[   38.702879] Kernel command line: root=UUID=c28aba18-6268-42ad-8a67-78b016a2cad9 ro quiet splash irqpoll 
[   38.702998] Misrouted IRQ fixup and polling support enabled 
[   38.703010] This may significantly impact system performance 
[   38.703908] No local APIC present or hardware disabled 
[   38.703967] mapped APIC to ffffd000 (012fa000) 
[   38.704037] Initializing CPU#0 
[   38.704336] PID hash table entries: 2048 (order: 11, 8192 bytes) 
[   38.706876] Console: colour VGA+ 80x25 
[   38.710854] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
[   38.714368] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   38.799362] Memory: 370616k/384960k available (1993k kernel code, 13876k reserved, 900k data, 328k init, 0k highmem) 
[   38.799408] virtual kernel memory layout: 
[   38.799413]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
[   38.799419]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   38.799425]     vmalloc : 0xd8000000 - 0xff7fe000   ( 631 MB) 
[   38.799431]     lowmem  : 0xc0000000 - 0xd77f0000   ( 375 MB) 
[   38.799437]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB) 
[   38.799443]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB) 
[   38.799448]       .text : 0xc0100000 - 0xc02f2434   (1993 kB) 
[   38.799467] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   38.876551] Calibrating delay using timer specific routine.. 983.29 BogoMIPS (lpj=1966586) 
[   38.876927] Security Framework v1.0.0 initialized 
[   38.876974] SELinux:  Disabled at boot. 
[   38.877110] Mount-cache hash table entries: 512 
[   38.878424] CPU: After generic identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000 
[   38.878490] CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line) 
[   38.878506] CPU: After all inits, caps: 008021bf 808029bf 00000000 00000002 00000000 00000000 00000000 
[   38.878601] Compat vDSO mapped to ffffe000. 
[   38.878642] Remapping vsyscall page to ffffe000 
[   38.878677] Checking 'hlt' instruction... OK. 
[   38.892703] SMP alternatives: switching to UP code 
[   38.894496] Freeing SMP alternatives: 11k freed 
[   38.895799] Early unpacking initramfs... done 
[   40.927020] ACPI: Core revision 20060707 
[   40.935332] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
[   40.940426] ACPI: setting ELCR to 0200 (from 0e28) 
[   40.958282] CPU0: AMD-K6(tm) 3D processor stepping 0c 
[   40.958314] SMP motherboard not detected. 
[   40.958327] Local APIC not detected. Using dummy APIC emulation. 
[   40.958756] Brought up 1 CPUs 
[   40.961145] Booting paravirtualized kernel on bare hardware 
[   40.961684] Time: 15:55:20  Date: 08/05/107 
[   40.961962] NET: Registered protocol family 16 
[   40.962901] EISA bus registered 
[   40.962938] ACPI: bus type pci registered 
[   40.998818] PCI: PCI BIOS revision 2.10 entry at 0xfb4f0, last bus=1 
[   40.998831] PCI: Using configuration type 1 
[   40.998840] Setting up standard PCI resources 
[   41.037081] ACPI: Interpreter enabled 
[   41.037102] ACPI: Using PIC for interrupt routing 
[   41.041840] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   41.041867] PCI: Probing PCI hardware (bus 00) 
[   41.042265] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0 
[   41.044494] Boot video device is 0000:00:0d.0 
[   41.045351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   41.060585] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[   41.062537] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15) 
[   41.064757] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15) 
[   41.066652] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15) 
[   41.069054] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *9 
[   41.094331] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   41.094441] pnp: PnP ACPI init 
[   41.126310] pnp: PnP ACPI: found 12 devices 
[   41.126337] PnPBIOS: Disabled by ACPI PNP 
[   41.126898] PCI: Using ACPI for IRQ routing 
[   41.126922] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   41.150632] NET: Registered protocol family 8 
[   41.150644] NET: Registered protocol family 20 
[   41.157754] PCI: Bridge: 0000:00:02.0 
[   41.157774]   IO window: c000-cfff 
[   41.157791]   MEM window: ef800000-ef8fffff 
[   41.157806]   PREFETCH window: ef000000-ef7fffff 
[   41.157837] PCI: Enabling device 0000:00:02.0 (0000 -> 0003) 
[   41.157862] PCI: Setting latency timer of device 0000:00:02.0 to 64 
[   41.158049] NET: Registered protocol family 2 
[   41.192484] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
[   41.193455] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
[   41.195203] TCP bind hash table entries: 8192 (order: 4, 65536 bytes) 
[   41.196383] TCP: Hash tables configured (established 16384 bind 8192) 
[   41.196400] TCP reno registered 
[   41.208426] checking if image is initramfs... it is 
[   44.836681] Freeing initrd memory: 6765k freed 
[   44.840404] audit: initializing netlink socket (disabled) 
[   44.840484] audit(1189007724.308:1): initialized 
[   44.841860] VFS: Disk quotas dquot_6.5.1 
[   44.842056] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   44.842805] io scheduler noop registered 
[   44.842826] io scheduler anticipatory registered 
[   44.842840] io scheduler deadline registered 
[   44.842934] io scheduler cfq registered (default) 
[   44.844967] isapnp: Scanning for PnP cards... 
[   45.223378] isapnp: No Plug & Play device found 
[   45.787308] Real Time Clock Driver v1.12ac 
[   45.787829] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   45.788478] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   45.796790] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   45.799895] mice: PS/2 mouse device common for all mice 
[   45.808273] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   45.809738] input: Macintosh mouse button emulation as /class/input/input0 
[   45.810515] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[   45.810543] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[   45.812070] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[   45.814441] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   45.814474] serio: i8042 AUX port at 0x60,0x64 irq 12 
[   45.815914] EISA: Probing bus 0 at eisa.0 
[   45.815980] Cannot allocate resource for EISA slot 4 
[   45.815993] Cannot allocate resource for EISA slot 5 
[   45.816024] EISA: Detected 0 cards. 
[   45.816043] PM-Timer had inconsistent results: 0x0xc79f1f, 0x0xc79b20 - aborting. 
[   45.816552] TCP cubic registered 
[   45.816613] NET: Registered protocol family 1 
[   45.816777] Using IPI No-Shortcut mode 
[   45.817331] ACPI: (supports S0 S1 S5) 
[   45.817588]   Magic number: 7:873:941 
[   45.817820] Time: tsc clocksource has been installed. 
[   45.817878] ACPI Error (evgpe-0711): No handler or method for GPE[ 7], disabling event [20060707] 
[   45.818172]   hash matches device ptyyc 
[   45.823341] Freeing unused kernel memory: 328k freed 
[   45.843510] input: AT Translated Set 2 keyboard as /class/input/input1 
[   49.114605] Capability LSM initialized 
[   49.571151] ACPI: CPU0 (power states: C1[C1] C2[C2]) 
[   49.571192] ACPI: Processor [CPU0] (supports 2 throttling states) 
[   55.655942] SIS5513: IDE controller at PCI slot 0000:00:00.1 
[   55.656000] ACPI: Unable to derive IRQ for device 0000:00:00.1 
[   55.656012] ACPI: PCI Interrupt 0000:00:00.1[A]: no GSI - using IRQ 14 
[   55.656030] PCI: setting IRQ 14 as level-triggered 
[   55.656069] SIS5513: chipset revision 208 
[   55.656080] SIS5513: not 100% native mode: will probe irqs later 
[   55.656111] SIS5513: SiS530 ATA 66 controller 
[   55.656178]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:DMA 
[   55.656247]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:DMA 
[   55.656311] Probing IDE interface ide0... 
[   55.991975] usbcore: registered new interface driver usbfs 
[   55.992193] usbcore: registered new interface driver hub 
[   55.992579] usbcore: registered new device driver usb 
[   56.166608] hda: ST310212A, ATA DISK drive 
[   56.283365] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver 
[   56.300504] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004) 
[   56.842823] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14 
[   56.843180] Probing IDE interface ide1... 
[   57.174749] Floppy drive(s): fd0 is 1.44M 
[   57.272127] FDC 0 is a post-1991 82077 
[   57.578094] hdc: LTN323, ATAPI CD/DVD-ROM drive 
[   19.064000] Time: pit clocksource has been installed. 
[   19.204000] ide1 at 0x170-0x177,0x376 on irq 15 
[   19.272000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11 
[   19.272000] PCI: setting IRQ 11 as level-triggered 
[   19.272000] ACPI: PCI Interrupt 0000:00:01.2[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11 
[   19.272000] ohci_hcd 0000:00:01.2: OHCI Host Controller 
[   19.272000] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1 
[   19.272000] ohci_hcd 0000:00:01.2: irq 11, io mem 0xef910000 
[   19.276000] SCSI subsystem initialized 
[   19.344000] libata version 2.20 loaded. 
[   19.360000] usb usb1: configuration #1 chosen from 1 choice 
[   19.360000] hub 1-0:1.0: USB hub found 
[   19.360000] hub 1-0:1.0: 2 ports detected 
[   19.464000] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip 
[   19.464000] 8139cp 0000:00:0b.0: Try the "8139too" driver instead. 
[   19.476000] 8139too Fast Ethernet driver 0.9.28 
[   19.480000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10 
[   19.480000] PCI: setting IRQ 10 as level-triggered 
[   19.480000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10 
[   19.480000] eth0: RealTek RTL8139 at 0xd8050000, 00:14:78:7b:d7:63, IRQ 10 
[   19.480000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D' 
[   19.584000] hda: max request size: 128KiB 
[   19.660000] hda: 20005650 sectors (10242 MB) w/512KiB Cache, CHS=19846/16/63, UDMA(33) 
[   19.660000] hda: cache flushes not supported 
[   19.660000]  hda: hda1 hda2 < hda5 > 
[   19.844000] hdc: ATAPI 32X CD-ROM drive, 120kB Cache, DMA 
[   19.844000] Uniform CD-ROM driver Revision: 3.20 
[   21.240000] kjournald starting.  Commit interval 5 seconds 
[   21.240000] EXT3-fs: mounted filesystem with ordered data mode. 
[   53.988000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1 
[   55.960000] NET: Registered protocol family 17 
[   63.520000] sis630_smbus 0000:00:01.0: SIS630 comp. bus not detected, module not inserted. 
[   65.036000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   65.064000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   65.128000] Linux agpgart interface v0.102 (c) Dave Jones 
[   65.152000] agpgart: Detected SiS 530 chipset 
[   65.156000] agpgart: AGP aperture is 64M @ 0xe8000000 
[   67.484000] nvidia: module license 'NVIDIA' taints kernel. 
[   69.492000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2 
[   69.524000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5 
[   69.524000] PCI: setting IRQ 5 as level-triggered 
[   69.524000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5 
[   69.528000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006 
[   69.528000] NVRM: CPU does not support the PAT, falling back to MTRRs. 
[   69.856000] input: PC Speaker as /class/input/input3 
[   71.900000] parport: PnPBIOS parport detected. 
[   71.900000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE] 
[   74.572000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3 
[   74.572000] PCI: setting IRQ 3 as level-triggered 
[   74.572000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3 
[   74.600000] gameport: ES1938 is pci0000:00:0f.0/gameport0, io 0xe800, speed 1028kHz 
[   76.496000] lp0: using parport0 (interrupt-driven). 
[   76.888000] Adding 473876k swap on /dev/disk/by-uuid/c8a436f7-24d8-4956-862d-536d80afaf36.  Priority:-1 extents:1 across:473876k 
[   77.396000] EXT3 FS on hda1, internal journal 
[   82.984000] No dock devices found. 
[   83.288000] Using specific hotkey driver 
[   83.920000] input: Power Button (FF) as /class/input/input4 
[   83.920000] ACPI: Power Button (FF) [PWRF] 
[   83.972000] input: Power Button (CM) as /class/input/input5 
[   83.972000] ACPI: Power Button (CM) [PWRB] 
[   83.976000] ACPI Error (evgpe-0711): No handler or method for GPE[ 7], disabling event [20060707] 
[   84.572000] ibm_acpi: ec object not found 
[   84.896000] pcc_acpi: loading... 
[   97.408000] ppdev: user-space parallel port driver 
[  109.548000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac) 
[  109.548000] apm: overridden by ACPI. 
```
Here the hard drive and optical drive are identified as 'h' - which is what I would expect. Other posts have indicated that the different identifications are the cause of the problem. One - it doesn't seem to upset the workings of the hard drive. Two, I've tried changing the identity of the optical drive in fstab from scd0 to hdc and the machine still locked up.

For completeness, here is the output from sudo lshw:
```
5441                      
    description: Mini Tower Computer 
    serial: None 
    width: 32 bits 
    capabilities: smbios-2.1 dmi-2.1 
    configuration: chassis=mini-tower 
  *-core 
       description: Motherboard 
       product: SiS-530 
       physical id: 0 
       slot: LPT 
     *-firmware 
          description: BIOS 
          vendor: Award Software International, Inc. 
          physical id: 0 
          version: 4.51 PG (11/22/00) 
          size: 128KB 
          capacity: 192KB 
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification 
     *-cpu 
          description: CPU 
          product: AMD-K6(tm) 3D processor 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 4 
          bus info: cpu@0 
          version: 5.8.12 
          slot: Socket 7 
          size: 475MHz 
          capacity: 475MHz 
          width: 32 bits 
          clock: 95MHz 
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 pge mmx syscall 3dnow k6_mtrr up 
        *-cache:0 
             description: L1 cache 
             physical id: 9 
             slot: Internal Cache 
             size: 64KB 
             capacity: 64KB 
             capabilities: synchronous internal write-back 
        *-cache:1 
             description: L2 cache 
             physical id: a 
             slot: External Cache 
             size: 512KB 
             capabilities: synchronous external write-through 
     *-memory 
          description: System memory 
          physical id: 1 
          size: 375MB 
     *-pci 
          description: Host bridge 
          product: 530 Host 
          vendor: Silicon Integrated Systems [SiS] 
          physical id: e8000000 
          bus info: pci@00:00.0 
          version: 03 
          width: 32 bits 
          clock: 33MHz 
          configuration: latency=64 
          resources: iomemory:e8000000-ebffffff 
        *-ide 
             description: IDE interface 
             product: 5513 [IDE] 
             vendor: Silicon Integrated Systems [SiS] 
             physical id: 0.1 
             bus info: pci@00:00.1 
             version: d0 
             width: 32 bits 
             clock: 33MHz 
             capabilities: ide bus_master 
             configuration: driver=SIS_IDE latency=16 
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:4000-400f irq:14 
           *-ide:0 
                description: IDE Channel 0 
                physical id: 0 
                bus info: ide@0 
                logical name: ide0 
                clock: 33MHz 
              *-disk 
                   description: ATA Disk 
                   product: ST310212A 
                   vendor: Seagate 
                   physical id: 0 
                   bus info: ide@0.0 
                   logical name: /dev/hda 
                   version: 3.02 
                   serial: 6EG0HS4F 
                   size: 9768MB 
                   capacity: 9768MB 
                   capabilities: ata dma lba iordy smart pm apm partitioned partitioned:dos 
                   configuration: apm=off mode=udma2 smart=on 
                 *-volume:0 
                      description: Linux filesystem partition 
                      physical id: 1 
                      bus info: ide@0.0,1 
                      logical name: /dev/hda1 
                      capacity: 9303MB 
                      capabilities: primary bootable 
                 *-volume:1 
                      description: Extended partition 
                      physical id: 2 
                      bus info: ide@0.0,2 
                      logical name: /dev/hda2 
                      size: 462MB 
                      capacity: 462MB 
                      capabilities: primary extended partitioned partitioned:extended 
                    *-logicalvolume 
                         description: Linux swap / Solaris partition 
                         physical id: 5 
                         logical name: /dev/hda5 
                         capacity: 462MB 
                         capabilities: nofs 
           *-ide:1 
                description: IDE Channel 1 
                physical id: 1 
                bus info: ide@1 
                logical name: ide1 
                clock: 33MHz 
              *-cdrom 
                   description: IDE CD-ROM 
                   product: LTN323 
                   physical id: 0 
                   bus info: ide@1.0 
                   logical name: /dev/hdc 
                   version: DQ14 
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio 
                 *-disc 
                      physical id: 0 
                      logical name: /dev/hdc 
        *-isa 
             description: ISA bridge 
             product: SiS85C503/5513 (LPC Bridge) 
             vendor: Silicon Integrated Systems [SiS] 
             physical id: 1 
             bus info: pci@00:01.0 
             version: b1 
             width: 32 bits 
             clock: 33MHz 
             capabilities: isa bus_master 
             configuration: driver=sis5595_smbus latency=0 
        *-generic UNCLAIMED 
             product: ACPI 
             vendor: Silicon Integrated Systems [SiS] 
             physical id: 1.1 
             bus info: pci@00:01.1 
             version: 00 
             width: 32 bits 
             clock: 33MHz 
             configuration: latency=0 
        *-usb 
             description: USB Controller 
             product: USB 1.0 Controller 
             vendor: Silicon Integrated Systems [SiS] 
             physical id: 1.2 
             bus info: pci@00:01.2 
             version: 11 
             width: 32 bits 
             clock: 33MHz 
             capabilities: ohci bus_master 
             configuration: driver=ohci_hcd latency=64 maxlatency=80 
             resources: iomemory:ef910000-ef910fff irq:11 
           *-usbhost 
                product: OHCI Host Controller 
                vendor: Linux 2.6.20-16-generic ohci_hcd 
                physical id: 1 
                bus info: usb@1 
                logical name: usb1 
                version: 2.06 
                capabilities: usb-1.10 
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s 
        *-pci 
             description: PCI bridge 
             product: Virtual PCI-to-PCI bridge (AGP) 
             vendor: Silicon Integrated Systems [SiS] 
             physical id: 2 
             bus info: pci@00:02.0 
             version: 00 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci normal_decode bus_master 
           *-display 
                description: VGA compatible controller 
                product: 530/620 PCI/AGP VGA Display Adapter 
                vendor: Silicon Integrated Systems [SiS] 
                physical id: 0 
                bus info: pci@01:00.0 
                version: a3 
                size: 8MB 
                width: 32 bits 
                clock: 66MHz 
                capabilities: vga cap_list 
                configuration: latency=64 mingnt=2 
                resources: iomemory:ef000000-ef7fffff iomemory:ef800000-ef80ffff 
        *-communication UNCLAIMED 
             description: Communication controller 
             product: HCF 56k Data/Fax Modem 
             vendor: Conexant 
             physical id: 9 
             bus info: pci@00:09.0 
             version: 08 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: latency=64 
             resources: iomemory:ef900000-ef90ffff ioport:d000-d007 irq:11 
        *-network 
             description: Ethernet interface 
             product: RTL-8139/8139C/8139C+ 
             vendor: Realtek Semiconductor Co., Ltd. 
             physical id: b 
             bus info: pci@00:0b.0 
             logical name: eth0 
             version: 10 
             serial: 00:14:78:7b:d7:63 
             size: 100MB/s 
             capacity: 100MB/s 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.20 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s 
             resources: ioport:d400-d4ff iomemory:ef911000-ef9110ff irq:10 
        *-display 
             description: VGA compatible controller 
             product: NV18 [GeForce4 MX 4000 AGP 8x] 
             vendor: nVidia Corporation 
             physical id: d 
             bus info: pci@00:0d.0 
             version: c1 
             size: 128MB 
             width: 32 bits 
             clock: 66MHz 
             capabilities: vga bus_master cap_list 
             configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 
             resources: iomemory:ec000000-ecffffff iomemory:e0000000-e7ffffff irq:5 
        *-multimedia 
             description: Multimedia audio controller 
             product: ES1969 Solo-1 Audiodrive 
             vendor: ESS Technology 
             physical id: f 
             bus info: pci@00:0f.0 
             version: 01 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=ESS ES1938 (Solo-1) latency=64 maxlatency=24 mingnt=2 
             resources: ioport:d800-d83f ioport:dc00-dc0f ioport:e000-e00f ioport:e400-e403 ioport:e800-e803 irq:3 
```
Also identifying the drives as 'h'.

So - why is the system locking up and how do I persuade it not to?

---

### Post by 8oluf7 on 2007-09-19
System threw a REAL wobbly just before I was due to do a demonstration. Fatal error before we got to the login screen. 

So - I did a ground-up install of Xubuntu 6.06. (LTS) from the Live CD (I'd been forced to use the Alternative CD for the 7.04 install due to the frozen mouse pointer problem - couldn't click the 'install' button!).

6.06 installed without a hitch - I didn't even need to use the 'irqpoll' modifier.  

When I tried to login I got multiple repeats of each letter! AAAGH! So, I ran 
```
sudo apt-get update
sudo apt-get upgrade
``` No improvement. So, I ran
```
sudo apt-get dist-upgrade
```Problem solved! 

I checked that a CD could be inserted without freezing the system, then installed OpenOffice.org and used it to open a file on the CD.

Magic - I appeared to be where I wanted to be.

Final check - read fstab and compare. Yes, the CD-ROM shows up as /hdc.

But - hang on a minute - there's no entry for the floppy drive! Sure enough, inserting a disk in the floppy drive produces a big fat nothing. Thunar can't see it, and there's no media/floppy folder.

Do I need to do anything other than add the floppy drive line in the previous post to my fstab file (and, presumably, reboot)?

---

### Post by 8oluf7 on 2007-09-20
I wrote too soon.

Still plagued by repeated keystrokes when I try to log in at the graphical prompt. Unchecking the 'repeat' box in System > Preferences > Keyboard doesn't make any difference. Problem does not appear when working at the command line.

This computer was earmarked for use by a novice. I can't release it until I've fixed or found a work-round for this problem. Puppy Linux works without any problems but is a bit 'wuff' round the edges, particularly its printing support.

---

### Post by dabl on 2007-09-20
Probably a line like this in your /etc/fstab file will set you up to see floppy diskettes:

> /dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0

But you only see them when a diskette is in the drive.

I don't recommend a "h_" anything number for a CD ROM drive.  Here's one that works:

> /dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

HTH!  :)

---

### Post by kerry_s on 2007-09-20
ubuntu is not the best for old machines, they drop all kinds of support for the old stuff.

try debian-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

here's the link for net installer, should you want to do a custom install, which is the best option if you want the best performance you can get->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

---

### Post by 8oluf7 on 2007-09-22
Thanks for the good advice.

I couldn't make the xfce ISO into a system disk. (The MD5 sum was OK and I burned at the lowest possible speed - but no joy.) 

I have used the 'business card' to do an install from the net. I couldn't work out what I should install for best performance - or how to install it. So I've gone with the default Desktop Environment. It's a bit sluggish but the problems I described at the beginning of this thread appear to be cured. I  can use the CD and floppy drives. I did have one instance of repeated keys at log-in, but I've slowed the keyboard repeat and haven't had any problems since. 

If I find the response unbearably sluggish I can try changing the desktop environment to xfce or something even lighter. 

The good news for someone trying Debian after Ubuntu is that, because Ubuntu is based on Debian, the Debian installer is recognizably similar to the one on the Ubuntu Alternate CD, and the various menus, tools etc. are sufficiently similarly organized for the switch to be fairly stress-free.

---

