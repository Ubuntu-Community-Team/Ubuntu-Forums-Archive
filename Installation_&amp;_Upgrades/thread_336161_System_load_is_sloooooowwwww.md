---
title: "System load is sloooooowwwww"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by bornakke on 2007-01-11
Just installed kubuntu edgy on my laptop for the first time. Everything seemed to go all right  until i restarted the computer for the first time. The first couple of times I thought the computre had frozen, but the computer actually loads after nearly 5 min.! When the computer is finaly loaded it doesn't seem to suffer for any other problems.

Please write if you need any futher information! All help, even just idears of where to look, will be appriciated!

This is the printout from /var/log/messages: (I'm not use to interpretat those kind of messages, so I have just choosen to send everything printed after pressing the reboot - hope that doesn't give you guys too much trouble!)

> Jan 11 15:10:25 Toby2 kernel: [17180343.604000] mtrr: 0xd0000000,0x8000000 overlaps existing 0xd0000000,0x4000000
Jan 11 15:10:25 Toby2 last message repeated 2 times
Jan 11 15:10:25 Toby2 kernel: [17180343.604000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jan 11 15:10:25 Toby2 kernel: [17180343.604000] agpgart: Device is in legacy mode, falling back to 2.x
Jan 11 15:10:25 Toby2 kernel: [17180343.604000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Jan 11 15:10:25 Toby2 kernel: [17180343.604000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Jan 11 15:10:26 Toby2 kernel: [17180344.404000] [drm] Setting GART location based on new memory map
Jan 11 15:10:26 Toby2 kernel: [17180344.404000] [drm] Loading R200 Microcode
Jan 11 15:10:26 Toby2 kernel: [17180344.404000] [drm] writeback test succeeded in 1 usecs
Jan 11 15:10:34 Toby2 exiting on signal 15
Jan 11 15:17:23 Toby2 syslogd 1.4.1#18ubuntu6: restart.
Jan 11 15:17:23 Toby2 kernel: Inspecting /boot/System.map-2.6.17-10-generic
Jan 11 15:17:23 Toby2 kernel: Loaded 22825 symbols from /boot/System.map-2.6.17-10-generic.
Jan 11 15:17:23 Toby2 kernel: Symbols match kernel version 2.6.17.
Jan 11 15:17:23 Toby2 kernel: No module symbols loaded - kernel modules not enabled. 
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] BIOS-provided physical RAM map:
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 00000000000d2000 - 00000000000d8000 (reserved)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] 0MB HIGHMEM available.
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] 511MB LOWMEM available.
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] DMI 2.3 present.
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x808
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Built 1 zonelists
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Enabling fast FPU save and restore... done.
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Enabling unmasked SIMD FPU exception support... done.
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Initializing CPU#0
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Detected 2194.151 MHz processor.
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Using pmtmr for high-res timesource
Jan 11 15:17:23 Toby2 kernel: [17179569.184000] Console: colour VGA+ 80x25
Jan 11 15:17:23 Toby2 kernel: [17179571.252000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 11 15:17:23 Toby2 kernel: [17179571.252000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 11 15:17:23 Toby2 kernel: [17179571.268000] Memory: 509800k/524224k available (1910k kernel code, 13800k reserved, 1070k data, 308k init, 0k highmem)
Jan 11 15:17:23 Toby2 kernel: [17179571.268000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jan 11 15:17:23 Toby2 kernel: [17179571.348000] Calibrating delay using timer specific routine.. 4390.66 BogoMIPS (lpj=8781339)
Jan 11 15:17:23 Toby2 kernel: [17179571.348000] Security Framework v1.0.0 initialized
Jan 11 15:17:23 Toby2 kernel: [17179571.348000] SELinux:  Disabled at boot.
Jan 11 15:17:23 Toby2 kernel: [17179571.348000] Mount-cache hash table entries: 512
Jan 11 15:17:23 Toby2 kernel: [17179571.348000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jan 11 15:17:23 Toby2 kernel: [17179571.348000] CPU: L2 Cache: 512K (64 bytes/line)
Jan 11 15:17:23 Toby2 kernel: [17179571.348000] Checking 'hlt' instruction... OK.
Jan 11 15:17:23 Toby2 kernel: [17179571.364000] SMP alternatives: switching to UP code
Jan 11 15:17:23 Toby2 kernel: [17179571.364000] Freeing SMP alternatives: 16k freed
Jan 11 15:17:23 Toby2 kernel: [17179571.364000] checking if image is initramfs... it is
Jan 11 15:17:23 Toby2 kernel: [17179571.804000] Freeing initrd memory: 5523k freed
Jan 11 15:17:23 Toby2 kernel: [17179571.804000] ACPI: Core revision 20060707
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] ACPI: Looking for DSDT ... not found!
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] ACPI: setting ELCR to 0200 (from 0c28)
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] CPU0: AMD mobile AMD Athlon(tm) XP 3000+ stepping 00
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] SMP motherboard not detected.
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] Local APIC not detected. Using dummy APIC emulation.
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] Brought up 1 CPUs
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] migration_cost=0
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] NET: Registered protocol family 16
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] EISA bus registered
Jan 11 15:17:23 Toby2 kernel: [17179571.808000] ACPI: bus type pci registered
Jan 11 15:17:23 Toby2 kernel: [17179571.812000] PCI: PCI BIOS revision 2.10 entry at 0xfda81, last bus=1
Jan 11 15:17:23 Toby2 kernel: [17179571.812000] PCI: Using configuration type 1
Jan 11 15:17:23 Toby2 kernel: [17179571.812000] Setting up standard PCI resources
Jan 11 15:17:23 Toby2 kernel: [17179571.828000] ACPI: Interpreter enabled
Jan 11 15:17:23 Toby2 kernel: [17179571.828000] ACPI: Using PIC for interrupt routing
Jan 11 15:17:23 Toby2 kernel: [17179571.828000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 11 15:17:23 Toby2 kernel: [17179571.828000] PCI quirk: region 0800-087f claimed by vt8235 PM
Jan 11 15:17:23 Toby2 kernel: [17179571.828000] PCI quirk: region 0400-040f claimed by vt8235 SMB
Jan 11 15:17:23 Toby2 kernel: [17179571.828000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
Jan 11 15:17:23 Toby2 kernel: [17179571.884000] ACPI: Power Resource [LPTP] (off)
Jan 11 15:17:23 Toby2 kernel: [17179571.884000] ACPI: Embedded Controller [EC0] (gpe 5) interrupt mode.
Jan 11 15:17:23 Toby2 kernel: [17179571.888000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jan 11 15:17:23 Toby2 kernel: [17179571.888000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jan 11 15:17:23 Toby2 kernel: [17179571.888000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jan 11 15:17:23 Toby2 kernel: [17179571.888000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jan 11 15:17:23 Toby2 kernel: [17179571.888000] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 11 15:17:23 Toby2 kernel: [17179571.888000] pnp: PnP ACPI init
Jan 11 15:17:23 Toby2 kernel: [17179571.892000] pnp: PnP ACPI: found 9 devices
Jan 11 15:17:23 Toby2 kernel: [17179571.892000] PnPBIOS: Disabled by ACPI PNP
Jan 11 15:17:23 Toby2 kernel: [17179571.892000] PCI: Using ACPI for IRQ routing
Jan 11 15:17:23 Toby2 kernel: [17179571.892000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jan 11 15:17:23 Toby2 kernel: [17179571.896000] PCI: Bridge: 0000:00:01.0
Jan 11 15:17:23 Toby2 kernel: [17179571.896000]   IO window: c000-cfff
Jan 11 15:17:23 Toby2 kernel: [17179571.896000]   MEM window: dfe00000-dfefffff
Jan 11 15:17:23 Toby2 kernel: [17179571.896000]   PREFETCH window: cfd00000-dfcfffff
Jan 11 15:17:23 Toby2 kernel: [17179571.896000] PCI: Bus 2, cardbus bridge: 0000:00:0b.0
Jan 11 15:17:23 Toby2 kernel: [17179571.896000]   IO window: 00001000-000010ff
Jan 11 15:17:23 Toby2 kernel: [17179571.896000]   IO window: 00001400-000014ff
Jan 11 15:17:23 Toby2 kernel: [17179571.896000]   PREFETCH window: 30000000-31ffffff
Jan 11 15:17:23 Toby2 kernel: [17179571.896000]   MEM window: 32000000-33ffffff
Jan 11 15:17:23 Toby2 kernel: [17179571.896000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
Jan 11 15:17:23 Toby2 kernel: [17179571.896000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
Jan 11 15:17:23 Toby2 kernel: [17179571.896000] NET: Registered protocol family 2
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] TCP: Hash tables configured (established 16384 bind 8192)
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] TCP reno registered
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] audit: initializing netlink socket (disabled)
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] audit(1168524662.928:1): initialized
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] VFS: Disk quotas dquot_6.5.1
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] Initializing Cryptographic API
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] io scheduler noop registered
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] io scheduler anticipatory registered
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] io scheduler deadline registered
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] io scheduler cfq registered (default)
Jan 11 15:17:23 Toby2 kernel: [17179571.928000] isapnp: Scanning for PnP cards...
Jan 11 15:17:23 Toby2 kernel: [17179572.280000] isapnp: No Plug & Play device found
Jan 11 15:17:23 Toby2 kernel: [17179572.304000] Real Time Clock Driver v1.12ac
Jan 11 15:17:23 Toby2 kernel: [17179572.304000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jan 11 15:17:23 Toby2 kernel: [17179572.304000] mice: PS/2 mouse device common for all mice
Jan 11 15:17:23 Toby2 kernel: [17179572.304000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jan 11 15:17:23 Toby2 kernel: [17179572.304000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jan 11 15:17:23 Toby2 kernel: [17179572.304000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jan 11 15:17:23 Toby2 kernel: [17179572.304000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 11 15:17:23 Toby2 kernel: [17179572.308000] i8042.c: Detected active multiplexing controller, rev 1.0.
Jan 11 15:17:23 Toby2 kernel: [17179572.308000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] EISA: Probing bus 0 at eisa.0
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] Cannot allocate resource for EISA slot 1
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] EISA: Detected 0 cards.
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] TCP bic registered
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] NET: Registered protocol family 1
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] NET: Registered protocol family 8
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] NET: Registered protocol family 20
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] Using IPI No-Shortcut mode
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] ACPI: (supports S0 S3 S4 S5)
Jan 11 15:17:23 Toby2 kernel: [17179572.312000] Freeing unused kernel memory: 308k freed
Jan 11 15:17:23 Toby2 kernel: [17179572.716000] input: AT Translated Set 2 keyboard as /class/input/input0
Jan 11 15:17:23 Toby2 kernel: [17179573.496000] Capability LSM initialized
Jan 11 15:17:23 Toby2 kernel: [17179573.528000] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jan 11 15:17:23 Toby2 kernel: [17179573.528000] ACPI: Thermal Zone [THRM] (75 C)
Jan 11 15:17:23 Toby2 kernel: [17179573.808000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
Jan 11 15:17:23 Toby2 kernel: [17179573.808000] ACPI: Unable to derive IRQ for device 0000:00:11.1
Jan 11 15:17:23 Toby2 kernel: [17179573.808000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
Jan 11 15:17:23 Toby2 kernel: [17179573.808000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
Jan 11 15:17:23 Toby2 kernel: [17179573.808000] VP_IDE: chipset revision 6
Jan 11 15:17:23 Toby2 kernel: [17179573.808000] VP_IDE: not 100%% native mode: will probe irqs later
Jan 11 15:17:23 Toby2 kernel: [17179573.808000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Jan 11 15:17:23 Toby2 kernel: [17179573.808000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
Jan 11 15:17:23 Toby2 kernel: [17179573.808000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
Jan 11 15:17:23 Toby2 kernel: [17179574.252000] hda: FUJITSU MHT2060AT, ATA DISK drive
Jan 11 15:17:23 Toby2 kernel: [17179574.924000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jan 11 15:17:23 Toby2 kernel: [17179575.872000] hdc: DVD+RW RW8160, ATAPI CD/DVD-ROM drive
Jan 11 15:17:23 Toby2 kernel: [17179576.544000] ide1 at 0x170-0x177,0x376 on irq 15
Jan 11 15:17:23 Toby2 kernel: [17179576.552000] hda: max request size: 128KiB
Jan 11 15:17:23 Toby2 kernel: [17179576.560000] hda: 117210240 sectors (60011 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Jan 11 15:17:23 Toby2 kernel: [17179576.560000] hda: cache flushes supported
Jan 11 15:17:23 Toby2 kernel: [17179576.560000]  hda: hda1 hda2 hda3
Jan 11 15:17:23 Toby2 kernel: [17179576.608000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 8192kB Cache, UDMA(33)
Jan 11 15:17:23 Toby2 kernel: [17179576.608000] Uniform CD-ROM driver Revision: 3.20
Jan 11 15:17:23 Toby2 kernel: [17179636.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:17:23 Toby2 kernel: [17179636.632000] hdc: lost interrupt
Jan 11 15:17:23 Toby2 kernel: [17179696.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:17:23 Toby2 kernel: [17179696.632000] hdc: lost interrupt
Jan 11 15:17:23 Toby2 kernel: [17179756.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:17:23 Toby2 kernel: [17179756.632000] hdc: lost interrupt
Jan 11 15:17:23 Toby2 kernel: [17179756.668000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
Jan 11 15:17:23 Toby2 kernel: [17179756.668000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Jan 11 15:17:23 Toby2 kernel: [17179756.720000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[dffff800-dfffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jan 11 15:17:23 Toby2 kernel: [17179756.744000] usbcore: registered new driver usbfs
Jan 11 15:17:23 Toby2 kernel: [17179756.744000] usbcore: registered new driver hub
Jan 11 15:17:23 Toby2 kernel: [17179756.748000] USB Universal Host Controller Interface driver v3.0
Jan 11 15:17:23 Toby2 kernel: [17179756.748000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Jan 11 15:17:23 Toby2 kernel: [17179756.748000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jan 11 15:17:23 Toby2 kernel: [17179756.748000] uhci_hcd 0000:00:10.0: UHCI Host Controller
Jan 11 15:17:23 Toby2 kernel: [17179756.748000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Jan 11 15:17:23 Toby2 kernel: [17179756.748000] uhci_hcd 0000:00:10.0: irq 11, io base 0x0000e000
Jan 11 15:17:23 Toby2 kernel: [17179756.748000] usb usb1: configuration #1 chosen from 1 choice
Jan 11 15:17:23 Toby2 kernel: [17179756.748000] hub 1-0:1.0: USB hub found
Jan 11 15:17:23 Toby2 kernel: [17179756.748000] hub 1-0:1.0: 2 ports detected
Jan 11 15:17:23 Toby2 kernel: [17179756.852000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
Jan 11 15:17:23 Toby2 kernel: [17179756.852000] uhci_hcd 0000:00:10.1: UHCI Host Controller
Jan 11 15:17:23 Toby2 kernel: [17179756.852000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Jan 11 15:17:23 Toby2 kernel: [17179756.852000] uhci_hcd 0000:00:10.1: irq 3, io base 0x0000e400
Jan 11 15:17:23 Toby2 kernel: [17179756.852000] usb usb2: configuration #1 chosen from 1 choice
Jan 11 15:17:23 Toby2 kernel: [17179756.852000] hub 2-0:1.0: USB hub found
Jan 11 15:17:23 Toby2 kernel: [17179756.852000] hub 2-0:1.0: 2 ports detected
Jan 11 15:17:23 Toby2 kernel: [17179756.956000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
Jan 11 15:17:23 Toby2 kernel: [17179756.956000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
Jan 11 15:17:23 Toby2 kernel: [17179756.956000] uhci_hcd 0000:00:10.2: UHCI Host Controller
Jan 11 15:17:23 Toby2 kernel: [17179756.956000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Jan 11 15:17:23 Toby2 kernel: [17179756.956000] uhci_hcd 0000:00:10.2: irq 5, io base 0x0000e800
Jan 11 15:17:23 Toby2 kernel: [17179756.956000] usb usb3: configuration #1 chosen from 1 choice
Jan 11 15:17:23 Toby2 kernel: [17179756.956000] hub 3-0:1.0: USB hub found
Jan 11 15:17:23 Toby2 kernel: [17179756.956000] hub 3-0:1.0: 2 ports detected
Jan 11 15:17:23 Toby2 kernel: [17179757.060000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Jan 11 15:17:23 Toby2 kernel: [17179757.060000] ehci_hcd 0000:00:10.3: EHCI Host Controller
Jan 11 15:17:23 Toby2 kernel: [17179757.060000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Jan 11 15:17:23 Toby2 kernel: [17179757.060000] ehci_hcd 0000:00:10.3: irq 10, io mem 0xdffff700
Jan 11 15:17:23 Toby2 kernel: [17179757.060000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 11 15:17:23 Toby2 kernel: [17179757.060000] usb usb4: configuration #1 chosen from 1 choice
Jan 11 15:17:23 Toby2 kernel: [17179757.060000] hub 4-0:1.0: USB hub found
Jan 11 15:17:23 Toby2 kernel: [17179757.060000] hub 4-0:1.0: 6 ports detected
Jan 11 15:17:23 Toby2 kernel: [17179757.676000] Attempting manual resume
Jan 11 15:17:23 Toby2 kernel: [17179757.728000] kjournald starting.  Commit interval 5 seconds
Jan 11 15:17:23 Toby2 kernel: [17179757.728000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 11 15:17:23 Toby2 kernel: [17179758.204000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jan 11 15:17:23 Toby2 kernel: [17179758.368000] usb 2-1: configuration #1 chosen from 1 choice
Jan 11 15:17:23 Toby2 kernel: [17179768.860000] NET: Registered protocol family 23
Jan 11 15:17:23 Toby2 kernel: [17179769.296000] parport: PnPBIOS parport detected.
Jan 11 15:17:23 Toby2 kernel: [17179769.296000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jan 11 15:17:23 Toby2 kernel: [17179769.416000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
Jan 11 15:17:23 Toby2 kernel: [17179769.416000] Yenta: CardBus bridge found at 0000:00:0b.0 [1734:1032]
Jan 11 15:17:23 Toby2 kernel: [17179769.416000] Yenta O2: res at 0x94/0xD4: 00/ea
Jan 11 15:17:23 Toby2 kernel: [17179769.416000] Yenta O2: enabling read prefetch/write burst
Jan 11 15:17:23 Toby2 kernel: [17179769.544000] Yenta: ISA IRQ mask 0x0010, PCI irq 3
Jan 11 15:17:23 Toby2 kernel: [17179769.544000] Socket status: 30000820
Jan 11 15:17:23 Toby2 kernel: [17179769.544000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 11 15:17:23 Toby2 kernel: [17179769.548000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 11 15:17:23 Toby2 kernel: [17179769.560000] input: PC Speaker as /class/input/input1
Jan 11 15:17:23 Toby2 kernel: [17179769.644000] Linux agpgart interface v0.101 (c) Dave Jones
Jan 11 15:17:23 Toby2 kernel: [17179769.652000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
Jan 11 15:17:23 Toby2 kernel: [17179769.656000] agpgart: AGP aperture is 64M @ 0xe0000000
Jan 11 15:17:23 Toby2 kernel: [17179769.692000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
Jan 11 15:17:23 Toby2 kernel: [17179769.692000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jan 11 15:17:23 Toby2 kernel: [17179769.696000] eth0: VIA Rhine II at 0x1d400, 00:03:0d:06:c3:c1, IRQ 11.
Jan 11 15:17:23 Toby2 kernel: [17179769.696000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
Jan 11 15:17:23 Toby2 kernel: [17179769.980000] eth0: link down
Jan 11 15:17:23 Toby2 kernel: [17179770.136000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
Jan 11 15:17:23 Toby2 kernel: [17179770.140000] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x848a1, caps: 0x0/0x0
Jan 11 15:17:23 Toby2 kernel: [17179770.180000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
Jan 11 15:17:23 Toby2 kernel: [17179770.200000] pccard: CardBus card inserted into slot 0
Jan 11 15:17:23 Toby2 kernel: [17179770.200000] usbcore: registered new driver libusual
Jan 11 15:17:23 Toby2 kernel: [17179770.284000] ts: Compaq touchscreen protocol output
Jan 11 15:17:23 Toby2 kernel: [17179770.380000] ath_hal: module license 'Proprietary' taints kernel.
Jan 11 15:17:23 Toby2 kernel: [17179770.384000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jan 11 15:17:23 Toby2 kernel: [17179770.444000] SCSI subsystem initialized
Jan 11 15:17:23 Toby2 kernel: [17179770.484000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
Jan 11 15:17:23 Toby2 kernel: [17179770.488000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jan 11 15:17:23 Toby2 kernel: [17179770.488000] cs: IO port probe 0x820-0x8ff: clean.
Jan 11 15:17:23 Toby2 kernel: [17179770.488000] cs: IO port probe 0xc00-0xcf7: clean.
Jan 11 15:17:23 Toby2 kernel: [17179770.488000] cs: IO port probe 0xa00-0xaff: clean.
Jan 11 15:17:23 Toby2 kernel: [17179770.548000] Initializing USB Mass Storage driver...
Jan 11 15:17:23 Toby2 kernel: [17179770.548000] scsi0 : SCSI emulation for USB Mass Storage devices
Jan 11 15:17:23 Toby2 kernel: [17179770.572000] usbcore: registered new driver usb-storage
Jan 11 15:17:23 Toby2 kernel: [17179770.572000] USB Mass Storage support registered.
Jan 11 15:17:23 Toby2 kernel: [17179770.608000] wlan: 0.8.4.2 (0.9.2)
Jan 11 15:17:23 Toby2 kernel: [17179770.640000] ath_rate_sample: 1.2 (0.9.2)
Jan 11 15:17:23 Toby2 kernel: [17179770.648000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
Jan 11 15:17:23 Toby2 kernel: [17179770.652000] ath_pci: 0.9.4.5 (0.9.2)
Jan 11 15:17:23 Toby2 kernel: [17179771.028000] NET: Registered protocol family 17
Jan 11 15:17:23 Toby2 kernel: [17179771.176000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Jan 11 15:17:23 Toby2 kernel: [17179771.176000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: mac 7.9 phy 4.5 radio 5.6
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: Use hw queue 1 for WME_AC_BE traffic
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: Use hw queue 0 for WME_AC_BK traffic
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: Use hw queue 2 for WME_AC_VI traffic
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: Use hw queue 3 for WME_AC_VO traffic
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: Use hw queue 8 for CAB traffic
Jan 11 15:17:23 Toby2 kernel: [17179771.756000] wifi0: Use hw queue 9 for beacons
Jan 11 15:17:23 Toby2 kernel: [17179771.784000] wifi0: Atheros 5212: mem=0x32000000, irq=3
Jan 11 15:17:23 Toby2 kernel: [17179775.576000]   Vendor: GENERIC   Model: USB FLASH DISK    Rev: 0201
Jan 11 15:17:23 Toby2 kernel: [17179775.576000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan 11 15:17:23 Toby2 kernel: [17179775.692000] SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
Jan 11 15:17:23 Toby2 kernel: [17179775.696000] sda: Write Protect is off
Jan 11 15:17:23 Toby2 kernel: [17179775.708000] SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
Jan 11 15:17:23 Toby2 kernel: [17179775.712000] sda: Write Protect is off
Jan 11 15:17:23 Toby2 kernel: [17179775.712000]  sda: sda1
Jan 11 15:17:23 Toby2 kernel: [17179775.720000] sd 0:0:0:0: Attached scsi removable disk sda
Jan 11 15:17:23 Toby2 kernel: [17179775.732000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 11 15:17:23 Toby2 kernel: [17179816.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:17:23 Toby2 kernel: [17179816.632000] hdc: lost interrupt
Jan 11 15:17:23 Toby2 kernel: [17179876.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:17:23 Toby2 kernel: [17179876.632000] hdc: lost interrupt
Jan 11 15:17:23 Toby2 kernel: [17179936.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:17:23 Toby2 kernel: [17179936.632000] hdc: lost interrupt
Jan 11 15:17:23 Toby2 kernel: [17179948.632000] lp0: using parport0 (interrupt-driven).
Jan 11 15:17:23 Toby2 kernel: [17179948.724000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Jan 11 15:17:23 Toby2 kernel: [17179948.724000] ieee1394: sbp2: Try serialize_io=0 for better performance
Jan 11 15:17:23 Toby2 kernel: [17179948.752000] Adding 1060248k swap on /dev/disk/by-uuid/9cb028e0-dee1-488d-8759-e3d5b202c1a5.  Priority:-1 extents:1 across:1060248k
Jan 11 15:17:23 Toby2 kernel: [17179948.836000] EXT3 FS on hda2, internal journal
Jan 11 15:17:23 Toby2 kernel: [17179949.024000] kjournald starting.  Commit interval 5 seconds
Jan 11 15:17:23 Toby2 kernel: [17179949.032000] EXT3 FS on hda3, internal journal
Jan 11 15:17:23 Toby2 kernel: [17179949.032000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 11 15:17:23 Toby2 kernel: [17179953.420000] ACPI: AC Adapter [AC0] (on-line)
Jan 11 15:17:23 Toby2 kernel: [17179953.464000] ACPI: Battery Slot [BAT0] (battery present)
Jan 11 15:17:23 Toby2 kernel: [17179953.480000] ACPI: Power Button (FF) [PWRF]
Jan 11 15:17:23 Toby2 kernel: [17179953.480000] ACPI: Power Button (CM) [PWRB]
Jan 11 15:17:23 Toby2 kernel: [17179953.480000] ACPI: Lid Switch [LID]
Jan 11 15:17:23 Toby2 kernel: [17179953.480000] ACPI: Sleep Button (CM) [SLPB]
Jan 11 15:17:23 Toby2 kernel: [17179953.636000] pcc_acpi: loading...
Jan 11 15:17:23 Toby2 kernel: [17179954.060000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
Jan 11 15:17:23 Toby2 kernel: [17179954.064000] powernow: SGTC: 13333
Jan 11 15:17:23 Toby2 kernel: [17179954.064000] powernow: Minimum speed 1462 MHz. Maximum speed 2194 MHz.
Jan 11 15:17:25 Toby2 kernel: [17179955.768000] [drm] Initialized drm 1.0.1 20051102
Jan 11 15:17:25 Toby2 kernel: [17179955.796000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jan 11 15:17:25 Toby2 kernel: [17179955.796000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
Jan 11 15:17:25 Toby2 hpiod: 1.6.9 accepting connections at 2208... 
Jan 11 15:17:26 Toby2 kernel: [17179956.856000] mtrr: 0xd0000000,0x8000000 overlaps existing 0xd0000000,0x4000000
Jan 11 15:17:26 Toby2 last message repeated 2 times
Jan 11 15:17:26 Toby2 kernel: [17179956.856000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jan 11 15:17:26 Toby2 kernel: [17179956.856000] agpgart: Device is in legacy mode, falling back to 2.x
Jan 11 15:17:26 Toby2 kernel: [17179956.856000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Jan 11 15:17:26 Toby2 kernel: [17179956.856000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Jan 11 15:17:26 Toby2 kernel: [17179956.860000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jan 11 15:17:26 Toby2 kernel: [17179956.860000] apm: overridden by ACPI.
Jan 11 15:17:26 Toby2 kernel: [17179957.216000] [drm] Setting GART location based on new memory map
Jan 11 15:17:26 Toby2 kernel: [17179957.216000] [drm] Loading R200 Microcode
Jan 11 15:17:26 Toby2 kernel: [17179957.216000] [drm] writeback test succeeded in 1 usecs
Jan 11 15:17:30 Toby2 kernel: [17179961.096000] Bluetooth: Core ver 2.8
Jan 11 15:17:30 Toby2 kernel: [17179961.096000] NET: Registered protocol family 31
Jan 11 15:17:30 Toby2 kernel: [17179961.096000] Bluetooth: HCI device and connection manager initialized
Jan 11 15:17:30 Toby2 kernel: [17179961.096000] Bluetooth: HCI socket layer initialized
Jan 11 15:17:30 Toby2 kernel: [17179961.256000] Bluetooth: L2CAP ver 2.8
Jan 11 15:17:30 Toby2 kernel: [17179961.256000] Bluetooth: L2CAP socket layer initialized
Jan 11 15:17:30 Toby2 kernel: [17179961.392000] Bluetooth: RFCOMM socket layer initialized
Jan 11 15:17:30 Toby2 kernel: [17179961.392000] Bluetooth: RFCOMM TTY layer initialized
Jan 11 15:17:30 Toby2 kernel: [17179961.392000] Bluetooth: RFCOMM ver 1.7
Jan 11 15:18:06 Toby2 kernel: [17179996.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:18:06 Toby2 kernel: [17179996.632000] hdc: lost interrupt
Jan 11 15:19:06 Toby2 kernel: [17180056.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:19:06 Toby2 kernel: [17180056.632000] hdc: lost interrupt
Jan 11 15:20:06 Toby2 kernel: [17180116.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:20:06 Toby2 kernel: [17180116.632000] hdc: lost interrupt
Jan 11 15:21:06 Toby2 kernel: [17180176.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:21:06 Toby2 kernel: [17180176.632000] hdc: lost interrupt
Jan 11 15:22:06 Toby2 kernel: [17180236.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:22:06 Toby2 kernel: [17180236.632000] hdc: lost interrupt
Jan 11 15:23:06 Toby2 kernel: [17180296.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:23:06 Toby2 kernel: [17180296.632000] hdc: lost interrupt
Jan 11 15:24:06 Toby2 kernel: [17180356.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:24:06 Toby2 kernel: [17180356.632000] hdc: lost interrupt
Jan 11 15:25:06 Toby2 kernel: [17180416.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:25:06 Toby2 kernel: [17180416.632000] hdc: lost interrupt
Jan 11 15:26:06 Toby2 kernel: [17180476.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:26:06 Toby2 kernel: [17180476.632000] hdc: lost interrupt
Jan 11 15:27:06 Toby2 kernel: [17180536.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:27:06 Toby2 kernel: [17180536.632000] hdc: lost interrupt
Jan 11 15:28:06 Toby2 kernel: [17180596.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:28:06 Toby2 kernel: [17180596.632000] hdc: lost interrupt
Jan 11 15:29:06 Toby2 kernel: [17180656.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:29:06 Toby2 kernel: [17180656.632000] hdc: lost interrupt
Jan 11 15:30:06 Toby2 kernel: [17180716.632000] ide-cd: cmd 0x3 timed out
Jan 11 15:30:06 Toby2 kernel: [17180716.632000] hdc: lost interrupt

---

### Post by computergroove on 2007-01-11
The biggest problem I see is that it doesnt find the cd drive in several lines which causes long pauses and then finally timesout and goes to the next startup process. "Jan 11 15:17:23 Toby2 kernel: [17179636.632000] ide-cd: cmd 0x3 timed out" Did you install the OS and then remove a cd drive connected to the system during the install and try to boot the system again? Your cd drive may also be failing and causing a error when the computer is trying to communicate with it. I would edit the fstab and remove the cd drive and see what the results were. Post a reply.

---

### Post by bornakke on 2007-01-18
Sorry I haven't answared before - had to leave the internet for a few days. I haven't tried removing the CD drive from the fstab, but have found a lot of other problems with loading anything from the CD drive. So your teori seems correct. I will try to search the forum for people having problems with the CD drive when I get home today.

---

### Post by bornakke on 2007-01-22
After a lot of searching, I have found the following solution ([http://www.ee.oulu.fi/~iiska/articles/ubuntu_in_a7620.html](http://www.ee.oulu.fi/~iiska/articles/ubuntu_in_a7620.html)) that I will share with you all. 

How to making Toshiba Amilo 7620 DVD drive work under edgy:

open the file menu.lst
> 
sudo gedit /boot/grub/menu.lst

add the line to the kernel parameters:
> hdc=noprobe hdc=cdrom

which will make it look something like this:
> 
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash hdc=noprobe hdc=cdrom
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot


---

### Post by Kinslayer on 2007-04-16
I had a problem with long startup & shutdown times.  The problem was my cd rom & dvd rom weren't mounting properly.  They were attached to the same ide cable.  How I fixed it was I shutdown the system, unplugged the cables from each, & rebooted.  It started right up.  Aha.  I shutdown again, which took less than a minute instead of the usual 5-10 minutes.  I connected one drive, started up, & it loaded quickly.  I repeated this with the second drive, with no problems.  A third time with both booted up quickly, and it hasn't been an issue since, at least for the couple of days since I've done this.

---

