---
title: "Dvico fusionhdtv dvbt-pro wont work"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by stowaway on 2008-02-02
hi, I have just installed mythbuntu. 
I followed the instructions here: ([www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)) 

well i hope i did. 

it seems to make it work except when im in myth it sees the card in capture cards (says dvico dvb-pro) and everthing. 

but it stil lcant open the card in the tuning section  

My /dev/dvb is populated by /dev/dvb/adapter0 

also: 
michael@mediacentre:/dev/dvb$ dmesg | grep dvb 
[ 31.481237] cx88/2: cx2388x dvb driver version 0.0.6 loaded 
[ 31.481241] cx88/2: registering cx8802 driver, type: dvb access: shared 

any ideas? 

update - i tried installing kaffeine player, it detects it wrong as a zarlink zli0353 dvb-t .. 
and "cant bind info socket" 

here is my dmesg output: 


------------------------------------------------------------------------------------- 
[ 0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic) 
[ 0.000000] Command line: root=UUID=010d5604-87d4-4e25-8e83-64aad0b67874 ro quiet splash 
[ 0.000000] BIOS-provided physical RAM map: 
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
[ 0.000000] BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved) 
[ 0.000000] BIOS-e820: 0000000000100000 - 000000007ff80000 (usable) 
[ 0.000000] BIOS-e820: 000000007ff80000 - 000000007ff8e000 (ACPI data) 
[ 0.000000] BIOS-e820: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS) 
[ 0.000000] BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved) 
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved) 
[ 0.000000] BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved) 
[ 0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used 
[ 0.000000] Entering add_active_range(0, 256, 524160) 1 entries of 3200 used 
[ 0.000000] end_pfn_map = 1048576 
[ 0.000000] DMI 2.4 present. 
[ 0.000000] ACPI: RSDP signature @ 0xFFFF8100000FBCB0 checksum 0 
[ 0.000000] ACPI: RSDP 000FBCB0, 0014 (r0 ACPIAM) 
[ 0.000000] ACPI: RSDT 7FF80000, 0040 (r1 A_M_I_ OEMRSDT 10000724 MSFT 97) 
[ 0.000000] ACPI: FACP 7FF80200, 0084 (r2 A_M_I_ OEMFACP 10000724 MSFT 97) 
[ 0.000000] ACPI: DSDT 7FF805C0, 8A37 (r1 A0867 A0867001 1 INTL 20060113) 
[ 0.000000] ACPI: FACS 7FF8E000, 0040 
[ 0.000000] ACPI: APIC 7FF80390, 006C (r1 A_M_I_ OEMAPIC 10000724 MSFT 97) 
[ 0.000000] ACPI: MCFG 7FF80400, 003C (r1 A_M_I_ OEMMCFG 10000724 MSFT 97) 
[ 0.000000] ACPI: OEMB 7FF8E040, 0081 (r1 A_M_I_ AMI_OEM 10000724 MSFT 97) 
[ 0.000000] ACPI: HPET 7FF89000, 0038 (r1 A_M_I_ OEMHPET 10000724 MSFT 97) 
[ 0.000000] ACPI: GSCI 7FF8E0D0, 2024 (r1 A_M_I_ GMCHSCI 10000724 MSFT 97) 
[ 0.000000] ACPI: OSFR 7FF89040, 00B0 (r1 A_M_I_ OEMOSFR 10000724 MSFT 97) 
[ 0.000000] No NUMA configuration found 
[ 0.000000] Faking a node at 0000000000000000-000000007ff80000 
[ 0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used 
[ 0.000000] Entering add_active_range(0, 256, 524160) 1 entries of 3200 used 
[ 0.000000] Bootmem setup node 0 0000000000000000-000000007ff80000 
[ 0.000000] Zone PFN ranges: 
[ 0.000000] DMA 0 -> 4096 
[ 0.000000] DMA32 4096 -> 1048576 
[ 0.000000] Normal 1048576 -> 1048576 
[ 0.000000] early_node_map[2] active PFN ranges 
[ 0.000000] 0: 0 -> 159 
[ 0.000000] 0: 256 -> 524160 
[ 0.000000] On node 0 totalpages: 524063 
[ 0.000000] DMA zone: 56 pages used for memmap 
[ 0.000000] DMA zone: 1125 pages reserved 
[ 0.000000] DMA zone: 2818 pages, LIFO batch:0 
[ 0.000000] DMA32 zone: 7110 pages used for memmap 
[ 0.000000] DMA32 zone: 512954 pages, LIFO batch:31 
[ 0.000000] Normal zone: 0 pages used for memmap 
[ 0.000000] ACPI: PM-Timer IO Port: 0x808 
[ 0.000000] ACPI: Local APIC address 0xfee00000 
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
[ 0.000000] Processor #0 (Bootup-CPU) 
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled) 
[ 0.000000] Processor #1 
[ 0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled) 
[ 0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled) 
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) 
[ 0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23 
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
[ 0.000000] ACPI: IRQ0 used by override. 
[ 0.000000] ACPI: IRQ2 used by override. 
[ 0.000000] ACPI: IRQ9 used by override. 
[ 0.000000] Setting APIC routing to flat 
[ 0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000 
[ 0.000000] Using ACPI (MADT) for SMP configuration information 
[ 0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000 
[ 0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000 
[ 0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000 
[ 0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000) 
[ 0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs 
[ 0.000000] PERCPU: Allocating 34696 bytes of per cpu data 
[ 0.000000] Built 1 zonelists. Total pages: 515772 
[ 0.000000] Kernel command line: root=UUID=010d5604-87d4-4e25-8e83-64aad0b67874 ro quiet splash 
[ 0.000000] Initializing CPU#0 
[ 0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes) 
[ 20.125274] time.c: Detected 2208.282 MHz processor. 
[ 20.126394] Console: colour VGA+ 80x25 
[ 20.126410] Checking aperture... 
[ 20.126417] Calgary: detecting Calgary via BIOS EBDA area 
[ 20.126419] Calgary: Unable to locate Rio Grande table in EBDA - bailing! 
[ 20.145834] Memory: 2055460k/2096640k available (2274k kernel code, 40792k reserved, 1181k data, 296k init) 
[ 20.145872] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1 
[ 20.223840] Calibrating delay using timer specific routine.. 4419.68 BogoMIPS (lpj=8839373) 
[ 20.223867] Security Framework v1.0.0 initialized 
[ 20.223874] SELinux: Disabled at boot. 
[ 20.224051] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes) 
[ 20.225223] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes) 
[ 20.225801] Mount-cache hash table entries: 256 
[ 20.225918] CPU: L1 I cache: 32K, L1 D cache: 32K 
[ 20.225921] CPU: L2 cache: 2048K 
[ 20.225923] CPU 0/0 -> Node 0 
[ 20.225925] using mwait in idle threads. 
[ 20.225926] CPU: Physical Processor ID: 0 
[ 20.225928] CPU: Processor Core ID: 0 
[ 20.225933] CPU0: Thermal monitoring enabled (TM2) 
[ 20.225942] SMP alternatives: switching to UP code 
[ 20.226165] Early unpacking initramfs... done 
[ 20.530485] ACPI: Core revision 20070126 
[ 20.530532] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
[ 20.573616] Using local APIC timer interrupts. 
[ 20.618834] result 12547051 
[ 20.618835] Detected 12.547 MHz APIC timer. 
[ 20.619279] SMP alternatives: switching to SMP code 
[ 20.619351] Booting processor 1/2 APIC 0x1 
[ 20.629577] Initializing CPU#1 
[ 20.707098] Calibrating delay using timer specific routine.. 4416.62 BogoMIPS (lpj=8833245) 
[ 20.707104] CPU: L1 I cache: 32K, L1 D cache: 32K 
[ 20.707106] CPU: L2 cache: 2048K 
[ 20.707108] CPU 1/1 -> Node 0 
[ 20.707109] CPU: Physical Processor ID: 0 
[ 20.707110] CPU: Processor Core ID: 1 
[ 20.707115] CPU1: Thermal monitoring enabled (TM2) 
[ 20.707383] Intel(R) Core(TM)2 Duo CPU E4500 @ 2.20GHz stepping 0d 
[ 20.707427] checking TSC synchronization [CPU#0 -> CPU#1]: passed. 
[ 20.731073] Brought up 2 CPUs 
[ 20.787602] migration_cost=10 
[ 20.787755] NET: Registered protocol family 16 
[ 20.787823] ACPI: bus type pci registered 
[ 20.787828] PCI: Using configuration type 1 
[ 20.790685] ACPI: EC: Look up EC in DSDT 
[ 20.796433] ACPI: Interpreter enabled 
[ 20.796436] ACPI: (supports S0 S1 S3 S4 S5) 
[ 20.796452] ACPI: Using IOAPIC for interrupt routing 
[ 20.804856] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[ 20.804867] PCI: Probing PCI hardware (bus 00) 
[ 20.806262] PCI: Transparent bridge - 0000:00:1e.0 
[ 20.806319] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[ 20.806457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT] 
[ 20.806534] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT] 
[ 20.806650] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT] 
[ 20.806730] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT] 
[ 20.806808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT] 
[ 20.822257] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[ 20.822369] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15) 
[ 20.822475] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15) 
[ 20.822580] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15) 
[ 20.822684] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[ 20.822789] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15) 
[ 20.822894] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15) 
[ 20.823025] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15) 
[ 20.823109] Linux Plug and Play Support v0.97 (c) Adam Belay 
[ 20.823119] pnp: PnP ACPI init 
[ 20.823125] ACPI: bus type pnp registered 
[ 20.826146] pnp: PnP ACPI: found 16 devices 
[ 20.826148] ACPI: ACPI bus type pnp unregistered 
[ 20.826191] PCI: Using ACPI for IRQ routing 
[ 20.826193] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report 
[ 20.826283] NET: Registered protocol family 8 
[ 20.826285] NET: Registered protocol family 20 
[ 20.826297] PCI-GART: No AMD northbridge found. 
[ 20.826301] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0 
[ 20.826305] hpet0: 4 64-bit timers, 14318180 Hz 
[ 20.827369] pnp: 00:01: iomem range 0xfed14000-0xfed19fff has been reserved 
[ 20.827375] pnp: 00:07: ioport range 0x290-0x297 has been reserved 
[ 20.827379] pnp: 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved 
[ 20.827381] pnp: 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved 
[ 20.827383] pnp: 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved 
[ 20.827386] pnp: 00:08: iomem range 0xffa00000-0xffafffff has been reserved 
[ 20.827392] pnp: 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved 
[ 20.827395] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved 
[ 20.827400] pnp: 00:0e: iomem range 0xe0000000-0xefffffff has been reserved 
[ 20.827404] pnp: 00:0f: iomem range 0x0-0x9ffff could not be reserved 
[ 20.827406] pnp: 00:0f: iomem range 0xc0000-0xcffff has been reserved 
[ 20.827408] pnp: 00:0f: iomem range 0xe0000-0xfffff could not be reserved 
[ 20.827411] pnp: 00:0f: iomem range 0x100000-0x7fffffff could not be reserved 
[ 20.827642] PCI: Bridge: 0000:00:01.0 
[ 20.827644] IO window: c000-cfff 
[ 20.827647] MEM window: f6000000-faefffff 
[ 20.827650] PREFETCH window: d0000000-dfffffff 
[ 20.827653] PCI: Bridge: 0000:00:1c.0 
[ 20.827654] IO window: disabled. 
[ 20.827658] MEM window: disabled. 
[ 20.827661] PREFETCH window: f4f00000-f4ffffff 
[ 20.827665] PCI: Bridge: 0000:00:1c.4 
[ 20.827667] IO window: d000-dfff 
[ 20.827671] MEM window: disabled. 
[ 20.827673] PREFETCH window: disabled. 
[ 20.827677] PCI: Bridge: 0000:00:1c.5 
[ 20.827678] IO window: disabled. 
[ 20.827682] MEM window: faf00000-faffffff 
[ 20.827685] PREFETCH window: disabled. 
[ 20.827689] PCI: Bridge: 0000:00:1e.0 
[ 20.827691] IO window: e000-efff 
[ 20.827695] MEM window: fb000000-febfffff 
[ 20.827698] PREFETCH window: disabled. 
[ 20.827710] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16 
[ 20.827715] PCI: Setting latency timer of device 0000:00:01.0 to 64 
[ 20.827729] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17 
[ 20.827733] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[ 20.827746] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17 
[ 20.827750] PCI: Setting latency timer of device 0000:00:1c.4 to 64 
[ 20.827764] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16 
[ 20.827768] PCI: Setting latency timer of device 0000:00:1c.5 to 64 
[ 20.827776] PCI: Setting latency timer of device 0000:00:1e.0 to 64 
[ 20.827785] NET: Registered protocol family 2 
[ 20.830910] Time: tsc clocksource has been installed. 
[ 20.871035] IP route cache hash table entries: 65536 (order: 7, 524288 bytes) 
[ 20.871684] TCP established hash table entries: 262144 (order: 10, 6291456 bytes) 
[ 20.875265] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[ 20.875925] TCP: Hash tables configured (established 262144 bind 65536) 
[ 20.875928] TCP reno registered 
[ 20.891180] checking if image is initramfs... it is 
[ 21.491223] Freeing initrd memory: 7353k freed 
[ 21.495993] audit: initializing netlink socket (disabled) 
[ 21.496010] audit(1201911251.320:1): initialized 
[ 21.497608] VFS: Disk quotas dquot_6.5.1 
[ 21.497647] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[ 21.497715] io scheduler noop registered 
[ 21.497716] io scheduler anticipatory registered 
[ 21.497718] io scheduler deadline registered 
[ 21.497790] io scheduler cfq registered (default) 
[ 21.499595] Boot video device is 0000:01:00.0 
[ 21.499705] PCI: Setting latency timer of device 0000:00:01.0 to 64 
[ 21.499733] assign_interrupt_mode Found MSI capability 
[ 21.499735] Allocate Port Service[0000:00:01.0:pcie00] 
[ 21.499800] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[ 21.499833] assign_interrupt_mode Found MSI capability 
[ 21.499835] Allocate Port Service[0000:00:1c.0:pcie00] 
[ 21.499860] Allocate Port Service[0000:00:1c.0:pcie02] 
[ 21.499922] PCI: Setting latency timer of device 0000:00:1c.4 to 64 
[ 21.499955] assign_interrupt_mode Found MSI capability 
[ 21.499957] Allocate Port Service[0000:00:1c.4:pcie00] 
[ 21.499978] Allocate Port Service[0000:00:1c.4:pcie02] 
[ 21.500041] PCI: Setting latency timer of device 0000:00:1c.5 to 64 
[ 21.500074] assign_interrupt_mode Found MSI capability 
[ 21.500076] Allocate Port Service[0000:00:1c.5:pcie00] 
[ 21.500098] Allocate Port Service[0000:00:1c.5:pcie02] 
[ 21.516056] Real Time Clock Driver v1.12ac 
[ 21.516207] hpet_resources: 0xfed00000 is busy 
[ 21.516241] Linux agpgart interface v0.102 (c) Dave Jones 
[ 21.516244] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[ 21.516330] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[ 21.516790] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[ 21.517304] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[ 21.517400] input: Macintosh mouse button emulation as /class/input/input0 
[ 21.517463] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
[ 21.520123] serio: i8042 KBD port at 0x60,0x64 irq 1 
[ 21.520126] serio: i8042 AUX port at 0x60,0x64 irq 12 
[ 21.520249] mice: PS/2 mouse device common for all mice 
[ 21.520355] TCP cubic registered 
[ 21.520408] NET: Registered protocol family 1 
[ 21.520575] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0) 
[ 21.520581] Freeing unused kernel memory: 296k freed 
[ 21.542029] input: AT Translated Set 2 keyboard as /class/input/input1 
[ 22.639361] AppArmor: AppArmor initialized<5>audit(1201911252.464:2): type=1505 info="AppArmor initialized" pid=1191 
[ 22.644243] fuse init (API version 7. 
[ 22.647312] Failure registering capabilities with primary security module. 
[ 22.676795] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 40, should be 37 [20070126] 
[ 22.676808] ACPI: SSDT 7FF90100, 0214 (r1 AMI CPU1PM 1 INTL 20060113) 
[ 22.677144] ACPI: SSDT 7FF90320, 0143 (r1 AMI CPU2PM 1 INTL 20060113) 
[ 22.677325] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126] 
[ 22.677333] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126] 
[ 23.023501] usbcore: registered new interface driver usbfs 
[ 23.023521] usbcore: registered new interface driver hub 
[ 23.023540] usbcore: registered new device driver usb 
[ 23.024189] USB Universal Host Controller Interface driver v3.0 
[ 23.024269] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16 
[ 23.024280] PCI: Setting latency timer of device 0000:00:1a.0 to 64 
[ 23.024283] uhci_hcd 0000:00:1a.0: UHCI Host Controller 
[ 23.024401] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1 
[ 23.024426] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800 
[ 23.024521] usb usb1: configuration #1 chosen from 1 choice 
[ 23.024542] hub 1-0:1.0: USB hub found 
[ 23.024547] hub 1-0:1.0: 2 ports detected 
[ 23.048894] SCSI subsystem initialized 
[ 23.098077] libata version 2.21 loaded. 
[ 23.101377] Floppy drive(s): fd0 is 1.44M 
[ 23.121711] FDC 0 is a post-1991 82077 
[ 23.130253] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21 
[ 23.130264] PCI: Setting latency timer of device 0000:00:1a.1 to 64 
[ 23.130267] uhci_hcd 0000:00:1a.1: UHCI Host Controller 
[ 23.130289] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2 
[ 23.130313] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880 
[ 23.130388] usb usb2: configuration #1 chosen from 1 choice 
[ 23.130407] hub 2-0:1.0: USB hub found 
[ 23.130411] hub 2-0:1.0: 2 ports detected 
[ 23.234601] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18 
[ 23.234612] PCI: Setting latency timer of device 0000:00:1a.2 to 64 
[ 23.234622] uhci_hcd 0000:00:1a.2: UHCI Host Controller 
[ 23.234637] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3 
[ 23.234659] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00 
[ 23.234727] usb usb3: configuration #1 chosen from 1 choice 
[ 23.234745] hub 3-0:1.0: USB hub found 
[ 23.234749] hub 3-0:1.0: 2 ports detected 
[ 23.338936] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23 
[ 23.338947] PCI: Setting latency timer of device 0000:00:1d.0 to 64 
[ 23.338951] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[ 23.338972] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4 
[ 23.338993] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080 
[ 23.339065] usb usb4: configuration #1 chosen from 1 choice 
[ 23.339083] hub 4-0:1.0: USB hub found 
[ 23.339087] hub 4-0:1.0: 2 ports detected 
[ 23.443045] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19 
[ 23.443055] PCI: Setting latency timer of device 0000:00:1d.1 to 64 
[ 23.443060] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[ 23.443081] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5 
[ 23.443102] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400 
[ 23.443171] usb usb5: configuration #1 chosen from 1 choice 
[ 23.443189] hub 5-0:1.0: USB hub found 
[ 23.443192] hub 5-0:1.0: 2 ports detected 
[ 23.547153] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18 
[ 23.547164] PCI: Setting latency timer of device 0000:00:1d.2 to 64 
[ 23.547169] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[ 23.547194] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6 
[ 23.547220] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480 
[ 23.547297] usb usb6: configuration #1 chosen from 1 choice 
[ 23.547315] hub 6-0:1.0: USB hub found 
[ 23.547319] hub 6-0:1.0: 2 ports detected 
[ 23.651877] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18 
[ 23.652308] PCI: Setting latency timer of device 0000:00:1a.7 to 64 
[ 23.652313] ehci_hcd 0000:00:1a.7: EHCI Host Controller 
[ 23.652573] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7 
[ 23.652602] ehci_hcd 0000:00:1a.7: debug port 1 
[ 23.652607] PCI: cache line size of 32 is not supported by device 0000:00:1a.7 
[ 23.652614] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf5fffc00 
[ 23.683408] usb 4-1: new low speed USB device using uhci_hcd and address 2 
[ 23.683430] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[ 23.683524] usb usb7: configuration #1 chosen from 1 choice 
[ 23.683551] hub 7-0:1.0: USB hub found 
[ 23.683557] hub 7-0:1.0: 6 ports detected 
[ 23.787913] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23 
[ 23.788342] PCI: Setting latency timer of device 0000:00:1d.7 to 64 
[ 23.788347] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[ 23.788393] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8 
[ 23.788421] ehci_hcd 0000:00:1d.7: debug port 1 
[ 23.788426] PCI: cache line size of 32 is not supported by device 0000:00:1d.7 
[ 23.788432] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf5fff800 
[ 23.799826] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[ 23.799941] usb usb8: configuration #1 chosen from 1 choice 
[ 23.799972] hub 8-0:1.0: USB hub found 
[ 23.799977] hub 8-0:1.0: 6 ports detected 
[ 23.904376] ACPI: PCI Interrupt 0000:05:03.0[A] -> GSI 16 (level, low) -> IRQ 16 
[ 23.957476] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16] MMIO=[febff800-febfffff] Max Packet=[2048] IR/IT contexts=[4/8] 
[ 23.962562] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16 
[ 23.962598] PCI: Setting latency timer of device 0000:03:00.0 to 64 
[ 23.962691] scsi0 : pata_jmicron 
[ 23.962728] scsi1 : pata_jmicron 
[ 23.962858] ata1: PATA max UDMA/100 cmd 0x000000000001dc00 ctl 0x000000000001d882 bmdma 0x000000000001d400 irq 16 
[ 23.962861] ata2: PATA max UDMA/100 cmd 0x000000000001d800 ctl 0x000000000001d482 bmdma 0x000000000001d408 irq 16 
[ 23.962971] ata_piix 0000:00:1f.2: version 2.11 
[ 23.962975] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ] 
[ 23.962992] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 22 (level, low) -> IRQ 22 
[ 23.963012] PCI: Setting latency timer of device 0000:00:1f.2 to 64 
[ 23.963035] scsi2 : ata_piix 
[ 23.963063] scsi3 : ata_piix 
[ 23.963132] ata3: SATA max UDMA/133 cmd 0x000000000001a000 ctl 0x0000000000019c02 bmdma 0x0000000000019480 irq 22 
[ 23.963135] ata4: SATA max UDMA/133 cmd 0x0000000000019880 ctl 0x0000000000019802 bmdma 0x0000000000019488 irq 22 
[ 24.217060] usb 4-1: device not accepting address 2, error -71 
[ 24.285786] ata1.00: ATAPI: ASUS DRW-1814BL, 1.13, max UDMA/66 
[ 24.382130] ata3.00: ATA-8: WDC WD10EACS-00ZJB0, 01.01B01, max UDMA/133 
[ 24.382136] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[ 24.406631] ata3.00: configured for UDMA/133 
[ 24.458004] ata1.00: configured for UDMA/66 
[ 24.570120] ata4.00: ATA-6: ST3160827AS, 3.03, max UDMA/133 
[ 24.570122] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[ 24.586190] ata4.00: configured for UDMA/133 
[ 24.586298] scsi 2:0:0:0: Direct-Access ATA WDC WD10EACS-00Z 01.0 PQ: 0 ANSI: 5 
[ 24.586629] scsi 3:0:0:0: Direct-Access ATA ST3160827AS 3.03 PQ: 0 ANSI: 5 
[ 24.586873] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ] 
[ 24.586892] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 22 (level, low) -> IRQ 22 
[ 24.586918] PCI: Setting latency timer of device 0000:00:1f.5 to 64 
[ 24.586940] scsi4 : ata_piix 
[ 24.587072] scsi5 : ata_piix 
[ 24.587249] ata5: SATA max UDMA/133 cmd 0x000000000001b000 ctl 0x000000000001ac02 bmdma 0x000000000001a480 irq 22 
[ 24.587252] ata6: SATA max UDMA/133 cmd 0x000000000001a880 ctl 0x000000000001a802 bmdma 0x000000000001a488 irq 22 
[ 24.614638] scsi 0:0:0:0: CD-ROM ASUS DRW-1814BL 1.13 PQ: 0 ANSI: 5 
[ 24.694291] usb 4-1: new low speed USB device using uhci_hcd and address 4 
[ 24.850814] usb 4-1: configuration #1 chosen from 1 choice 
[ 24.931727] sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB) 
[ 24.931736] sd 2:0:0:0: [sda] Write Protect is off 
[ 24.931738] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[ 24.931749] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 24.931786] sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB) 
[ 24.931793] sd 2:0:0:0: [sda] Write Protect is off 
[ 24.931794] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[ 24.931805] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 24.931808] sda:sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray 
[ 24.933858] Uniform CD-ROM driver Revision: 3.20 
[ 24.934041] sr 0:0:0:0: Attached scsi CD-ROM sr0 
[ 24.936687] sda1 
[ 24.936732] sd 2:0:0:0: [sda] Attached SCSI disk 
[ 24.936780] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB) 
[ 24.936788] sd 3:0:0:0: [sdb] Write Protect is off 
[ 24.936790] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00 
[ 24.936802] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 24.936826] sd 2:0:0:0: Attached scsi generic sg0 type 0 
[ 24.936833] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB) 
[ 24.936840] sd 3:0:0:0: [sdb] Write Protect is off 
[ 24.936842] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00 
[ 24.936853] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 24.936856] sdb:<5>sd 3:0:0:0: Attached scsi generic sg1 type 0 
[ 24.936920] sr 0:0:0:0: Attached scsi generic sg2 type 5 
[ 24.945226] sdb1 sdb2 < sdb5 > 
[ 24.966621] sd 3:0:0:0: [sdb] Attached SCSI disk 
[ 25.128815] Attempting manual resume 
[ 25.128818] swsusp: Resume From Partition 8:21 
[ 25.128819] PM: Checking swsusp image. 
[ 25.134088] PM: Resume from disk failed. 
[ 25.167889] kjournald starting. Commit interval 5 seconds 
[ 25.167896] EXT3-fs: mounted filesystem with ordered data mode. 
[ 25.240243] ieee1394: Host added: ID:BUS[0-00:1023] GUID[0011d800018e9bf3] 
[ 30.202693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[ 30.205399] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[ 30.398110] input: PC Speaker as /class/input/input2 
[ 30.628266] nvidia: module license 'NVIDIA' taints kernel. 
[ 30.804337] input: PS/2 Generic Mouse as /class/input/input3 
[ 30.881441] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16 
[ 30.881450] PCI: Setting latency timer of device 0000:01:00.0 to 64 
[ 30.881541] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 100.14.19 Wed Sep 12 14:08:38 PDT 2007 
[ 30.931117] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17 
[ 30.931127] PCI: Setting latency timer of device 0000:02:00.0 to 64 
[ 30.934012] atl1 0000:02:00.0: version 2.0.7 
[ 30.969982] Linux video capture interface: v2.00 
[ 31.008848] lirc_dev: IR Remote Control driver registered, at major 61 
[ 31.067143] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3 
[ 31.067147] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws> 
[ 31.067180] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: found IMON device 
[ 31.067185] lirc_dev: lirc_register_plugin: sample_rate: 0 
[ 31.067210] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin (minor:0) 
[ 31.067251] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<4:4> initialized 
[ 31.067261] usbcore: registered new interface driver lirc_imon 
[ 31.182707] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded 
[ 31.182764] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16 
[ 31.182786] cx88[0]: subsystem: 18ac:db30, board: DViCO FusionHDTV DVB-T PRO [card=58,autodetected] 
[ 31.182789] cx88[0]: TV tuner type 4, Radio tuner type -1 
[ 31.248300] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded 
[ 31.340700] cx2388x alsa driver version 0.0.6 loaded 
[ 31.348686] cx88[0]/0: found at 0000:05:00.0, rev: 5, irq: 16, latency: 64, mmio: 0xfb000000 
[ 31.348750] cx88[0]/0: registered device video0 [v4l2] 
[ 31.348767] cx88[0]/0: registered device vbi0 
[ 31.348831] cx88[0]/2: cx2388x 8802 Driver Manager 
[ 31.348853] ACPI: PCI Interrupt 0000:05:00.2[A] -> GSI 16 (level, low) -> IRQ 16 
[ 31.348862] cx88[0]/2: found at 0000:05:00.2, rev: 5, irq: 16, latency: 64, mmio: 0xfd000000 
[ 31.348965] ACPI: PCI Interrupt 0000:05:00.1[A] -> GSI 16 (level, low) -> IRQ 16 
[ 31.348990] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards 
[ 31.481237] cx88/2: cx2388x dvb driver version 0.0.6 loaded 
[ 31.481241] cx88/2: registering cx8802 driver, type: dvb access: shared 
[ 31.481244] cx88[0]/2: subsystem: 18ac:db30, board: DViCO FusionHDTV DVB-T PRO [card=58] 
[ 31.481246] cx88[0]/2: cx2388x based DVB/ATSC card 
[ 31.828471] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner 
[ 31.828477] DVB: registering new adapter (cx88[0]) 
[ 31.828480] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)... 
[ 31.860427] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22 
[ 31.860877] PCI: Setting latency timer of device 0000:00:1b.0 to 64 
[ 32.066593] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS... 
[ 32.977934] lp: driver loaded but no devices found 
[ 33.222254] Adding 6040400k swap on /dev/sdb5. Priority:-1 extents:1 across:6040400k 
[ 33.483716] EXT3 FS on sdb1, internal journal 
[ 35.172791] input: Power Button (FF) as /class/input/input4 
[ 35.172808] ACPI: Power Button (FF) [PWRF] 
[ 35.172898] input: Power Button (CM) as /class/input/input5 
[ 35.172909] ACPI: Power Button (CM) [PWRB] 
[ 35.208687] No dock devices found. 
[ 38.442411] atl1 0000:02:00.0: Unable to enable MSI: -22 
[ 38.442492] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex 
[ 38.921051] NET: Registered protocol family 10 
[ 38.921136] lo: Disabled Privacy Extensions 
[ 51.422937] NET: Registered protocol family 17 
[ 63.383062] eth0: no IPv6 routers present 
[ 154.485706] xc2028 0-0061: Error on line 1060: -121

---

