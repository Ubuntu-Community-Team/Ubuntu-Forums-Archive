---
title: "[SOLVED] Pnpbios problem on upgrade... please please help"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by xfred on 2007-02-23
OK, I recently installed a bunch of upgrades that apparently included kernel version 2.6.19 (upgraded from 2.6.15-28-686 (dual core version, can't recall exact name)).  But now it won't boot :( .  Well, obviously the old kernel does, but the new one doesn't, and I presume it's probably wise to upgrade if possible (though to be honest I'm not entirely sure why).

Problem #1: 8254 timer not connected to io-apic.  OK, google has an answer to that (the noapic switch, though apparently it might mess with the whole dual core thing... but I'll deal with that later, if it's a problem).

Problem #2 (the big one): I get a message "PnPBios: resource structure does not contain an end tag".  Then the screen goes blank and the boot process hangs.  This does not happen when the old kernel is booted, and google turns up nothing I can comprehend.

Problem is, I don't even know where to start with this.  Is this a syntax error in some setup file somewhere?  If so, where can I find the pnpbios setup file which (I assume) is missing an end tag?  What directory should I start looking in (I did look around for a while, but ended up more lost and confused than when I started looking).  Is there a logfile somewhere that might contain clues?  If so, where?

I'm utterly lost, and google is not being friendly right now.  Please help!  Please?

EDIT: fwiw here's my hardware spec:
- Asus p5n32sli deluxe motherboard
- pentium d 940 3.2GHz processor (smp)
- 4*1GB dimms
- Asus N6600 video card
- bt878 tv tuner card
- 250GB hdd (primary ide).
- dvd burner + dvd drive (secondary ide)
- 2*250GB sata hdd
- single 3.5" fdd

---

### Post by xfred on 2007-02-23
Anyone?  All I'm looking for is some idea where pnpbios setup files can be found so I've got something (anything) to work with.

---

### Post by xfred on 2007-02-24
Well, I tried updating the bios... it didn't fix anything, but now running bios version 0405.

Seriously, doesn't anyone have any suggestions about the phpbios problem?  Surely there is some information about this somewhere?

---

### Post by xfred on 2007-02-24
I decided to try to just let the boot process go to completion while I went and did something else.  Anyhow, when I came back after about 30 minutes it had actually put up a text login (no graphics, so I presume graphics drivers are borked), so I logged in and grabbed dmesg (really really slow, but anyhow).  Here's the output:

```
[FONT="Courier New"][    0.000000] Linux version 2.6.19.1 (root@shadowfax) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Feb 1 17:34:40 EST 2007
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e9b60 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] 3968MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 1245184) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1245184
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1245184
[    0.000000] On node 0 totalpages: 1245184
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7936 pages used for memmap
[    0.000000]   HighMem zone: 1007872 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] Intel MultiProcessor Specification v1.1
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: TEMPLATE Product ID: Deluxe       APIC at: 0xFEE00000
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ec00000)
[    0.000000] Detected 3200.304 MHz processor.
[   23.129431] Built 1 zonelists.  Total pages: 1235456
[   23.129434] Kernel command line: root=/dev/hda1 ro quiet splash
[   23.129582] mapped APIC to ffffd000 (fee00000)
[   23.129585] mapped IOAPIC to ffffc000 (fec00000)
[   23.129588] Enabling fast FPU save and restore... done.
[   23.129591] Enabling unmasked SIMD FPU exception support... done.
[   23.129594] Initializing CPU#0
[   23.129644] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   23.129696] spurious 8259A interrupt: IRQ7.
[   23.131629] Console: colour VGA+ 80x25
[   23.131876] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.132247] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.322409] Memory: 4143452k/4980736k available (2140k kernel code, 49284k reserved, 616k data, 284k init, 3276480k highmem)
[   23.322419] virtual kernel memory layout:
[   23.322420]     fixmap  : 0xfff54000 - 0xfffff000   ( 684 kB)
[   23.322421]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   23.322422]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   23.322423]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.322424]       .init : 0xc03b7000 - 0xc03fe000   ( 284 kB)
[   23.322426]       .data : 0xc03173f0 - 0xc03b1470   ( 616 kB)
[   23.322427]       .text : 0xc0100000 - 0xc03173f0   (2140 kB)
[   23.322429] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.400823] Calibrating delay using timer specific routine.. 6405.42 BogoMIPS (lpj=12810859)
[   23.400862] Security Framework v1.0.0 initialized
[   23.400868] SELinux:  Disabled at boot.
[   23.400883] Mount-cache hash table entries: 512
[   23.401004] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
[   23.401013] monitor/mwait feature present.
[   23.401014] using mwait in idle threads.
[   23.401021] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.401023] CPU: L2 cache: 2048K
[   23.401026] CPU: Physical Processor ID: 0
[   23.401027] CPU: Processor Core ID: 0
[   23.401029] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000180 0000e43d 00000000 00000001
[   23.401040] Compat vDSO mapped to ffffe000.
[   23.401053] Checking 'hlt' instruction... OK.
[   23.416839] SMP alternatives: switching to UP code
[   23.416968] CPU0: Intel(R) Pentium(R) D CPU 3.20GHz stepping 02
[   23.416976] SMP alternatives: switching to SMP code
[   23.416998] Booting processor 1/1 eip 2000
[   23.427514] Initializing CPU#1
[   23.504506] Calibrating delay using timer specific routine.. 6400.81 BogoMIPS (lpj=12801632)
[   23.504514] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
[   23.504519] monitor/mwait feature present.
[   23.504524] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.504526] CPU: L2 cache: 2048K
[   23.504528] CPU: Physical Processor ID: 0
[   23.504530] CPU: Processor Core ID: 1
[   23.504531] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000180 0000e43d 00000000 00000001
[   23.504904] CPU1: Intel(R) Pentium(R) D CPU 3.20GHz stepping 02
[   23.504935] Total of 2 processors activated (12806.24 BogoMIPS).
[   23.504993] ExtINT not setup in hardware but reported by MP table
[   23.505074] ENABLING IO-APIC IRQs
[   23.505236] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   23.544835] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   23.544873] ...trying to set up timer (IRQ0) through the 8259A ... 
[   23.544875] ..... (found pin 0) ...works.
[   23.691941] checking TSC synchronization across 2 CPUs: passed.
[    0.003986] Brought up 2 CPUs
[    1.241383] migration_cost=1618
[    1.241499] checking if image is initramfs... it is
[    1.750128] Freeing initrd memory: 6025k freed
[    1.750436] NET: Registered protocol family 16
[    1.750513] EISA bus registered
[    1.750632] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=9
[    1.750634] PCI: Using configuration type 1
[    1.750636] Setting up standard PCI resources
[    1.758453] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.758465] PnPBIOS: Scanning system for PnP BIOS support...
[    1.758482] PnPBIOS: Found PnP BIOS installation structure at 0xc00f8e30
[    1.758485] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9c3a, dseg 0xf0000
[    1.759372] PnPBIOS: Resource structure does not contain an end tag.
[    1.759667] PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
[    1.759810] SCSI subsystem initialized
[    1.759849] libata version 2.00 loaded.
[    1.759876] PCI: Probing PCI hardware
[    1.759883] PCI: Probing PCI hardware (bus 00)
[    1.761026] Boot video device is 0000:01:00.0
[    1.761801] PCI: Transparent bridge - 0000:00:12.0
[    1.763734] PCI: Using IRQ router default [10de/0050] at 0000:00:0a.0
[    1.794787] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    1.794791] pnp: 00:0c: ioport range 0xcf8-0xcff could not be reserved
[    1.794794] pnp: 00:0c: ioport range 0x900-0x97f has been reserved
[    1.794797] pnp: 00:0c: ioport range 0x980-0x9ff has been reserved
[    1.794799] pnp: 00:0c: ioport range 0x500-0x57f has been reserved
[    1.794802] pnp: 00:0c: ioport range 0x580-0x5ff has been reserved
[    1.794804] pnp: 00:0c: ioport range 0xe00-0xe7f has been reserved
[    1.794811] pnp: 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[    1.794814] pnp: 00:0d: ioport range 0xcf8-0xcff could not be reserved
[    1.795146] PCI: Bridge: 0000:00:02.0
[    1.795148]   IO window: disabled.
[    1.795153]   MEM window: f4000000-fbcfffff
[    1.795156]   PREFETCH window: d0000000-dfffffff
[    1.795161] PCI: Bridge: 0000:00:04.0
[    1.795162]   IO window: disabled.
[    1.795166]   MEM window: disabled.
[    1.795169]   PREFETCH window: disabled.
[    1.795172] PCI: Bridge: 0000:00:05.0
[    1.795175]   IO window: d000-dfff
[    1.795179]   MEM window: fbd00000-fbdfffff
[    1.795182]   PREFETCH window: disabled.
[    1.795186] PCI: Bridge: 0000:00:06.0
[    1.795187]   IO window: disabled.
[    1.795191]   MEM window: disabled.
[    1.795194]   PREFETCH window: disabled.
[    1.795197] PCI: Bridge: 0000:00:07.0
[    1.795200]   IO window: e000-efff
[    1.795204]   MEM window: fbe00000-fbefffff
[    1.795207]   PREFETCH window: disabled.
[    1.795211] PCI: Bridge: 0000:00:12.0
[    1.795213]   IO window: disabled.
[    1.795217]   MEM window: fbf00000-fbffffff
[    1.795221]   PREFETCH window: f2f00000-f2ffffff
[    1.795225] PCI: Bridge: 0000:00:14.0
[    1.795227]   IO window: disabled.
[    1.795231]   MEM window: disabled.
[    1.795234]   PREFETCH window: disabled.
[    1.795238] PCI: Bridge: 0000:00:16.0
[    1.795240]   IO window: disabled.
[    1.795243]   MEM window: disabled.
[    1.795247]   PREFETCH window: disabled.
[    1.795251] PCI: Bridge: 0000:00:17.0
[    1.795252]   IO window: disabled.
[    1.795256]   MEM window: disabled.
[    1.795259]   PREFETCH window: disabled.
[    1.795273] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.795284] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    1.795295] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    1.795305] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    1.795316] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    1.795323] PCI: Setting latency timer of device 0000:00:12.0 to 64
[    1.795335] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    1.795347] PCI: Setting latency timer of device 0000:00:16.0 to 64
[    1.795359] PCI: Setting latency timer of device 0000:00:17.0 to 64
[    1.795392] NET: Registered protocol family 2
[    1.834450] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.834561] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    1.835232] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[    1.835586] TCP: Hash tables configured (established 131072 bind 65536)
[    1.835589] TCP reno registered
[    1.836097] audit: initializing netlink socket (disabled)
[    1.836106] audit(1172365914.444:1): initialized
[    1.836162] highmem bounce pool size: 64 pages
[    1.836243] VFS: Disk quotas dquot_6.5.1
[    1.836262] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.836308] io scheduler noop registered
[    1.836311] io scheduler anticipatory registered (default)
[    1.836315] io scheduler deadline registered
[    1.836327] io scheduler cfq registered
[    1.862334] PCI: Found HT MSI mapping on 0000:00:14.0 with capability disabled
[    1.862340] PCI: MSI quirk detected. MSI disabled on chipset 0000:00:14.0.
[    1.862351] PCI: Found HT MSI mapping on 0000:00:16.0 with capability disabled
[    1.862357] PCI: MSI quirk detected. MSI disabled on chipset 0000:00:16.0.
[    1.862367] PCI: Found HT MSI mapping on 0000:00:17.0 with capability disabled
[    1.862373] PCI: MSI quirk detected. MSI disabled on chipset 0000:00:17.0.
[    1.862530] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.862534] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[    1.862568] assign_interrupt_mode Found MSI capability
[    1.862607] Allocate Port Service[0000:00:02.0:pcie00]
[    1.862687] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    1.862691] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[    1.862724] assign_interrupt_mode Found MSI capability
[    1.862753] Allocate Port Service[0000:00:04.0:pcie00]
[    1.862829] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    1.862833] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[    1.862866] assign_interrupt_mode Found MSI capability
[    1.862895] Allocate Port Service[0000:00:05.0:pcie00]
[    1.862970] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    1.862974] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[    1.863007] assign_interrupt_mode Found MSI capability
[    1.863036] Allocate Port Service[0000:00:06.0:pcie00]
[    1.863114] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    1.863117] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[    1.863151] assign_interrupt_mode Found MSI capability
[    1.863179] Allocate Port Service[0000:00:07.0:pcie00]
[    1.863263] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    1.863266] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[    1.863313] assign_interrupt_mode Found MSI capability
[    1.863350] Allocate Port Service[0000:00:14.0:pcie00]
[    1.863442] PCI: Setting latency timer of device 0000:00:16.0 to 64
[    1.863446] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[    1.863493] assign_interrupt_mode Found MSI capability
[    1.863530] Allocate Port Service[0000:00:16.0:pcie00]
[    1.863619] PCI: Setting latency timer of device 0000:00:17.0 to 64
[    1.863623] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[    1.863669] assign_interrupt_mode Found MSI capability
[    1.863706] Allocate Port Service[0000:00:17.0:pcie00]
[    1.863799] isapnp: Scanning for PnP cards...
[    2.214371] isapnp: No Plug & Play device found
[    2.237682] Real Time Clock Driver v1.12ac
[    2.237686] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.237805] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.238508] 00:11: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.239190] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.239284] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.239287] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.239434] sata_sil24 0000:03:00.0: version 0.3
[    2.239481] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    2.239567] ata1: SATA max UDMA/100 cmd 0xF8810000 ctl 0x0 bmdma 0x0 irq 10
[    2.239626] ata2: SATA max UDMA/100 cmd 0xF8812000 ctl 0x0 bmdma 0x0 irq 10
[    2.239635] scsi0 : sata_sil24
[    2.552206] ata1: SATA link down (SStatus 0 SControl 300)
[    2.552220] scsi1 : sata_sil24
[    2.867243] ata2: SATA link down (SStatus 0 SControl 300)
[    2.867300] sata_nv 0000:00:10.0: version 2.0
[    2.867322] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    2.867352] ata3: SATA max UDMA/133 cmd 0xBC00 ctl 0xB882 bmdma 0xB400 irq 11
[    2.867380] ata4: SATA max UDMA/133 cmd 0xB800 ctl 0xB482 bmdma 0xB408 irq 11
[    2.867389] scsi2 : sata_nv
[    3.341807] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.342765] ata3.00: ATA-7, max UDMA/133, 488397168 sectors: LBA48 NCQ (depth 0/32)
[    3.342769] ata3.00: ata3: dev 0 multi count 16
[    3.343812] ata3.00: configured for UDMA/133
[    3.343819] scsi3 : sata_nv
[    3.816356] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.817290] ata4.00: ATA-7, max UDMA/133, 625142448 sectors: LBA48 NCQ (depth 0/32)
[    3.817293] ata4.00: ata4: dev 0 multi count 16
[    3.818430] ata4.00: configured for UDMA/133
[    3.818520] scsi 2:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
[    3.818651] scsi 3:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    3.818743] PCI: Setting latency timer of device 0000:00:11.0 to 64
[    3.818774] ata5: SATA max UDMA/133 cmd 0xB080 ctl 0xB002 bmdma 0xA800 irq 11
[    3.818800] ata6: SATA max UDMA/133 cmd 0xAC00 ctl 0xA882 bmdma 0xA808 irq 11
[    3.818806] scsi4 : sata_nv
[    4.131377] ata5: SATA link down (SStatus 0 SControl 300)
[    4.131386] scsi5 : sata_nv
[    4.446415] ata6: SATA link down (SStatus 0 SControl 300)
[    4.446518] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[    4.446521] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    4.448577] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.448582] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.448681] mice: PS/2 mouse device common for all mice
[    4.448781] EISA: Probing bus 0 at eisa.0
[    4.448812] EISA: Detected 0 cards.
[    4.448872] TCP cubic registered
[    4.448880] NET: Registered protocol family 1
[    4.448886] NET: Registered protocol family 8
[    4.448887] NET: Registered protocol family 20
[    4.448920] Starting balanced_irq
[    4.448926] Using IPI No-Shortcut mode
[    4.449080] Freeing unused kernel memory: 284k freed
[    4.450439] Time: tsc clocksource has been installed.
[    4.470291] input: AT Translated Set 2 keyboard as /class/input/input0
[    8.687468] vga16fb: initializing
[    8.687477] vga16fb: mapped to 0xc00a0000
[    8.687544] fb0: VGA16 VGA frame buffer device
[   19.145550] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   19.145573] sda: Write Protect is off
[   19.145584] sda: Mode Sense: 00 3a 00 00
[   19.145616] SCSI device sda: drive cache: write back
[   19.145687] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   19.145712] sda: Write Protect is off
[   19.145722] sda: Mode Sense: 00 3a 00 00
[   19.145755] SCSI device sda: drive cache: write back
[   19.145759]  sda: sda1
[   19.389019] sd 2:0:0:0: Attached scsi disk sda
[   19.403664] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   19.403685] sdb: Write Protect is off
[   19.403696] sdb: Mode Sense: 00 3a 00 00
[   19.403729] SCSI device sdb: drive cache: write back
[   19.403789] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   19.403809] sdb: Write Protect is off
[   19.403819] sdb: Mode Sense: 00 3a 00 00
[   19.403850] SCSI device sdb: drive cache: write back
[   19.403854]  sdb: sdb1
[   19.447132] sd 3:0:0:0: Attached scsi disk sdb
[   27.077485] NFORCE-CK804: IDE controller at PCI slot 0000:00:0f.0
[   27.077511] NFORCE-CK804: chipset revision 243
[   27.077518] NFORCE-CK804: not 100% native mode: will probe irqs later
[   27.077549] NFORCE-CK804: 0000:00:0f.0 (rev f3) UDMA133 controller
[   27.077566]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   27.077582]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[   27.077593] Probing IDE interface ide0...
[   27.372482] hda: ST3250824A, ATA DISK drive
[   28.042794] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   28.042827] Probing IDE interface ide1...
[   28.780183] hdc: PIONEER DVD-RW DVR-111D, ATAPI CD/DVD-ROM drive
[   29.561795] hdd: LITE-ON DVD SOHD-16P9S, ATAPI CD/DVD-ROM drive
[   29.618057] ide1 at 0x170-0x177,0x376 on irq 15
[   30.016457] hda: max request size: 512KiB
[   30.055694] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[   30.080004] hda: cache flushes supported
[   30.080036]  hda: hda1 hda2 < hda5 >
[   30.171843] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[   30.171880] Uniform CD-ROM driver Revision: 3.20
[   30.191610] hdd: ATAPI 48X DVD-ROM drive, 254kB Cache, UDMA(33)
[   40.495149] usbcore: registered new interface driver usbfs
[   40.495221] usbcore: registered new interface driver hub
[   40.495289] usbcore: registered new device driver usb
[   40.513836] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   40.513941] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   40.513957] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   40.514314] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   40.514354] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xf3ffe000
[   41.288071] usb usb1: configuration #1 chosen from 1 choice
[   41.289988] hub 1-0:1.0: USB hub found
[   41.290030] hub 1-0:1.0: 10 ports detected
[   41.634094] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.57.
[   41.654803] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   41.654819] forcedeth: using HIGHDMA
[   41.704649] usb 1-5: new full speed USB device using ohci_hcd and address 2
[   41.906262] usb 1-5: configuration #1 chosen from 1 choice
[   41.909097] hub 1-5:1.0: USB hub found
[   41.912001] hub 1-5:1.0: 4 ports detected
[   42.178290] eth0: forcedeth.c: subsystem: 01043:81d3 bound to 0000:00:13.0
[   42.272889] usb 1-5.1: new low speed USB device using ohci_hcd and address 3
[   42.378649] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   42.378665] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   42.383172] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   42.383393] ehci_hcd 0000:00:0b.1: debug port 1
[   42.383398] PCI: cache line size of 128 is not supported by device 0000:00:0b.1
[   42.383425] ehci_hcd 0000:00:0b.1: irq 3, io mem 0xf3fffc00
[   42.383451] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   42.386540] usb 1-5.1: unable to read config index 0 descriptor/all
[   42.386556] usb 1-5.1: can't read configurations, error -62
[   42.387526] hub 1-5:1.0: cannot disable port 1 (err = -62)
[   42.388836] usb usb2: configuration #1 chosen from 1 choice
[   42.390513] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.391466] hub 2-0:1.0: USB hub found
[   42.391518] hub 2-0:1.0: 10 ports detected
[   42.393506] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.396496] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.399486] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.402477] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.402496] hub 1-5:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   42.405468] hub 1-5:1.0: cannot disable port 1 (err = -62)
[   42.408459] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.411450] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.414438] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.417429] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.420421] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.420435] hub 1-5:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   42.423412] hub 1-5:1.0: cannot disable port 1 (err = -62)
[   42.426403] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.429394] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.432386] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.435375] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.438365] hub 1-5:1.0: cannot reset port 1 (err = -62)
[   42.438383] hub 1-5:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   42.441356] hub 1-5:1.0: cannot disable port 1 (err = -62)
[   42.444347] hub 1-5:1.0: cannot disable port 1 (err = -62)
[   42.447346] hub 1-5:1.0: hub_port_status failed (err = -62)
[   42.450335] hub 1-5:1.0: hub_port_status failed (err = -62)
[   42.453353] hub 1-5:1.0: hub_port_status failed (err = -62)
[   42.456317] hub 1-5:1.0: hub_port_status failed (err = -62)
[   42.456413] usb 1-5: USB disconnect, address 2
[   42.837189] usb 2-5: new high speed USB device using ehci_hcd and address 2
[   42.979906] usb 2-5: configuration #1 chosen from 1 choice
[   42.980344] hub 2-5:1.0: USB hub found
[   42.980633] hub 2-5:1.0: 4 ports detected
[   43.312904] usb 2-5.1: new low speed USB device using ehci_hcd and address 3
[   43.422244] usb 2-5.1: configuration #1 chosen from 1 choice
[   44.845784] ieee1394: Initialized config rom entry `ip1394'
[   44.948260] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fbfff800-fbffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   46.226073] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800009e22c6]
[   46.331780] usbcore: registered new interface driver hiddev
[   46.660158] input: Logitech USB Optical Mouse as /class/input/input1
[   46.661869] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:0b.1-5.1
[   46.661915] usbcore: registered new interface driver usbhid
[   46.661937] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   49.642454] kjournald starting.  Commit interval 5 seconds
[   49.642513] EXT3-fs: mounted filesystem with ordered data mode.
[  108.683425] sd 2:0:0:0: Attached scsi generic sg0 type 0
[  108.683900] sd 3:0:0:0: Attached scsi generic sg1 type 0
[  244.678578] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  244.706472] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  264.661389] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x600
[  264.662016] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x700
[  284.493380] input: PC Speaker as /class/input/input2
[  293.366834] PCI: Setting latency timer of device 0000:05:00.0 to 64
[  293.366905] sky2 v1.10 addr 0xfbefc000 irq 11 Yukon-EC (0xb6) rev 2
[  293.367501] sky2 eth1: addr 00:17:31:07:b3:a0
[  304.130912] Linux video capture interface: v2.00
[  312.958597] bttv: driver version 0.9.16 loaded
[  312.958613] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  312.959060] bttv: Bt8xx card found (0).
[  312.959128] bttv0: Bt878 (rev 17) at 0000:06:06.0, irq: 11, latency: 64, mmio: 0xf2ffe000
[  312.959204] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[  312.959232] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[  312.959293] bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
[  312.960834] bttv0: using tuner=38
[  312.960859] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[  312.961972] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[  312.963068] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[  312.964165] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  314.206237] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[  314.206324] tuner 2-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[  314.206358] tuner 2-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[  314.484778] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[  314.617744] Floppy drive(s): fd0 is 1.44M
[  314.638721] FDC 0 is a post-1991 82077
[  314.802433] intel8x0_measure_ac97_clock: measured 53204 usecs
[  314.802441] intel8x0: clocking to 46858
[  316.665334] bttv0: registered device video0
[  316.665834] bttv0: registered device vbi0
[  316.666322] bttv0: registered device radio0
[  316.666407] bttv0: PLL: 28636363 => 35468950 .. ok
[  320.912190] input: bttv IR (card=34) as /class/input/input3
[  320.935130] bttv-input: bttv IR (card=34) detected at pci-0000:06:06.0/ir0
[  353.967430] parport: PnPBIOS parport detected.
[  353.967498] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  362.036269] sky2 eth1: enabling interface
[  364.295280] sky2 eth1: Link is up at 10 Mbps, half duplex, flow control none
[  394.340424] lp0: using parport0 (interrupt-driven).
[  398.084455] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[  398.084467] ieee1394: sbp2: Try serialize_io=0 for better performance
[  402.935048] Adding 6080560k swap on /dev/hda5.  Priority:-1 extents:1 across:6080560k
[  403.632196] EXT3 FS on hda1, internal journal
[  420.960696] device-mapper: ioctl: 4.10.0-ioctl (2006-09-14) initialised: [email]dm-devel@redhat.com[/email]
[  425.174633] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[  425.174677] device-mapper: ioctl: error adding target to table
[  425.180201] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[  425.180243] device-mapper: ioctl: error adding target to table
[  425.210870] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[  425.210913] device-mapper: ioctl: error adding target to table
[  425.217317] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[  425.217359] device-mapper: ioctl: error adding target to table
[  425.227485] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[  425.227545] device-mapper: ioctl: error adding target to table
[  425.244666] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[  425.244728] device-mapper: ioctl: error adding target to table
[  425.252575] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[  425.252635] device-mapper: ioctl: error adding target to table
[  425.263477] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[  425.263539] device-mapper: ioctl: error adding target to table
[  433.810043] loop: loaded (max 256 devices)
[  462.004913] NET: Registered protocol family 17
[  716.801514] ppdev: user-space parallel port driver
[  747.620097] NET: Registered protocol family 10
[  747.622640] lo: Disabled Privacy Extensions
[  753.742245] Bluetooth: Core ver 2.11
[  753.745712] NET: Registered protocol family 31
[  753.745725] Bluetooth: HCI device and connection manager initialized
[  753.745737] Bluetooth: HCI socket layer initialized
[  754.831361] Bluetooth: L2CAP ver 2.8
[  754.831371] Bluetooth: L2CAP socket layer initialized
[  756.069531] Bluetooth: RFCOMM socket layer initialized
[  756.069562] Bluetooth: RFCOMM TTY layer initialized
[  756.069569] Bluetooth: RFCOMM ver 1.8
[  758.487159] eth1: no IPv6 routers present[/FONT]
```

Interestingly it seems to be detecting the dual processor fine despite the apic warnings.  Here's the pnpbios bit:

```
[FONT="Courier New"][    1.758465] PnPBIOS: Scanning system for PnP BIOS support...
[    1.758482] PnPBIOS: Found PnP BIOS installation structure at 0xc00f8e30
[    1.758485] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9c3a, dseg 0xf0000
[    1.759372] PnPBIOS: Resource structure does not contain an end tag.
[    1.759667] PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver[/FONT]
```

So I guess this is hardware, not os as I had originally suspected.  Net result: I'm now even more confused than I was previously.  Anyone :confused:

---

### Post by Jose Consuervo on 2007-03-17
Hey I'm having the same problem, mine actually completely stops completely quite a bit lower, where it says pnpbios parport detected. I don't know if this is because of the same reason or not.

---

### Post by Jose Consuervo on 2007-03-17
Okay this is what helped me with my problem, I don't know whether or not this is your problem, but i just disabled the acip and the acpi with the boot options noapic and noacpi. Hopefully it will work for you

---

