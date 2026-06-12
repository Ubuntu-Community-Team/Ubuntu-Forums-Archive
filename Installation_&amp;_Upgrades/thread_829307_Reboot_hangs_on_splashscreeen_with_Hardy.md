---
title: "Reboot hangs on splashscreeen with Hardy"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by myotis on 2008-06-14
I have finally upgraded to Hardy, and it is hanging on the splash screen when I reboot.

If I use the reset button on the Systems box it resets and reboots OK.


Any pointers as to what to check out - very much a beginner here, so may need a bit of hand holding.


Many thanks,


Graham

---

### Post by hal8000 on 2008-06-14
When the splash screen appears press Alt+F1.
You will now see the boot messgages.

Post the last message displayed when the system freezes.
Not sure why pressing the reset switch allows the system to load, there may be clues in /var/log/messages

---

### Post by myotis on 2008-06-14
Alt + F1 does nothing and the splash screen just stays frozen.

To explain more casrefully, I hit the restart menu option and Ubuntu jumps  to the splash screen with the time elapsed bar frozen, until I use the manual reset button on the PC 

The log has the following which may be relavant

Jun 14 23:48:19 Antec-Linux kernel: [   71.448981] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
Jun 14 23:48:19 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 14 23:48:22 Antec-Linux kernel: [   73.669134] NET: Registered protocol family 17
Jun 14 23:48:22 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun 14 23:48:22 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 14 23:48:22 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 14 23:48:22 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun 14 23:48:23 Antec-Linux kernel: [   75.190500] NET: Registered protocol family 10
Jun 14 23:48:23 Antec-Linux kernel: [   75.190800] lo: Disabled Privacy Extensions
Jun 14 23:48:23 Antec-Linux kernel: [   75.192014] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 14 23:48:56 Antec-Linux pulseaudio[6273]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
Jun 14 23:48:56 Antec-Linux pulseaudio[6273]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.


And a  complete post between restart attempts is shown below,

Many thanks for your help.

Graham

Jun 14 21:02:51 Antec-Linux exiting on signal 15
Jun 14 21:05:22 Antec-Linux syslogd 1.5.0#1ubuntu1: restart.
Jun 14 21:05:23 Antec-Linux kernel: Inspecting /boot/System.map-2.6.24-18-generic
Jun 14 21:05:23 Antec-Linux kernel: Loaded 27880 symbols from /boot/System.map-2.6.24-18-generic.
Jun 14 21:05:23 Antec-Linux kernel: Symbols match kernel version 2.6.24.
Jun 14 21:05:23 Antec-Linux kernel: Loaded 19059 symbols from 94 modules.
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff80000 (usable)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]  BIOS-e820: 000000007ff80000 - 000000007ff8e000 (ACPI data)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]  BIOS-e820: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] 1151MB HIGHMEM available.
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] 896MB LOWMEM available.
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] found SMP MP-table at 000ff780
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Zone PFN ranges:
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]   DMA             0 ->     4096
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]   Normal       4096 ->   229376
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]   HighMem    229376 ->   524160
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Movable zone start PFN for each node
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] early_node_map[1] active PFN ranges
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000]     0:        0 ->   524160
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] DMI 2.3 present.
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FA940 checksum 0
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: RSDP 000FA940, 0014 (r0 ACPIAM)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: RSDT 7FF80000, 0034 (r1 A M I  OEMRSDT   3000631 MSFT       97)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: FACP 7FF80200, 0081 (r1 A M I  OEMFACP   3000631 MSFT       97)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: DSDT 7FF80410, 83F0 (r1  A0229 A0229000        0 INTL  2002026)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: FACS 7FF8E000, 0040
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: APIC 7FF80390, 0080 (r1 A M I  OEMAPIC   3000631 MSFT       97)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: OEMB 7FF8E040, 0066 (r1 A M I  AMI_OEM   3000631 MSFT       97)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: MCFG 7FF88800, 003C (r1 A M I  OEMMCFG   3000631 MSFT       97)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Processor #0 15:4 APIC version 20
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Processor #1 15:4 APIC version 20
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7fb00000)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520065
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Kernel command line: root=UUID=b562d2a2-c030-4bb4-909d-87602a889c8e ro quiet splash
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Initializing CPU#0
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 14 21:05:23 Antec-Linux kernel: [    0.000000] Detected 2810.016 MHz processor.
Jun 14 21:05:23 Antec-Linux kernel: [   46.989857] Console: colour VGA+ 80x25
Jun 14 21:05:23 Antec-Linux kernel: [   46.989861] console [tty0] enabled
Jun 14 21:05:23 Antec-Linux kernel: [   46.990116] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 14 21:05:23 Antec-Linux kernel: [   46.990438] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 14 21:05:23 Antec-Linux kernel: [   47.109934] Memory: 2066692k/2096640k available (2176k kernel code, 28704k reserved, 1006k data, 368k init, 1179136k highmem)
Jun 14 21:05:23 Antec-Linux kernel: [   47.109943] virtual kernel memory layout:
Jun 14 21:05:23 Antec-Linux kernel: [   47.109944]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Jun 14 21:05:23 Antec-Linux kernel: [   47.109945]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 14 21:05:23 Antec-Linux kernel: [   47.109946]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jun 14 21:05:23 Antec-Linux kernel: [   47.109947]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jun 14 21:05:23 Antec-Linux kernel: [   47.109948]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Jun 14 21:05:23 Antec-Linux kernel: [   47.109949]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
Jun 14 21:05:23 Antec-Linux kernel: [   47.109950]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
Jun 14 21:05:23 Antec-Linux kernel: [   47.109953] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun 14 21:05:23 Antec-Linux kernel: [   47.109992] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jun 14 21:05:23 Antec-Linux kernel: [   47.189927] Calibrating delay using timer specific routine.. 5625.69 BogoMIPS (lpj=11251397)
Jun 14 21:05:23 Antec-Linux kernel: [   47.189951] Security Framework initialized
Jun 14 21:05:23 Antec-Linux kernel: [   47.189956] SELinux:  Disabled at boot.
Jun 14 21:05:23 Antec-Linux kernel: [   47.189970] AppArmor: AppArmor initialized
Jun 14 21:05:23 Antec-Linux kernel: [   47.189974] Failure registering capabilities with primary security module.
Jun 14 21:05:23 Antec-Linux kernel: [   47.189983] Mount-cache hash table entries: 512
Jun 14 21:05:23 Antec-Linux kernel: [   47.190106] Initializing cgroup subsys ns
Jun 14 21:05:23 Antec-Linux kernel: [   47.190111] Initializing cgroup subsys cpuacct
Jun 14 21:05:23 Antec-Linux kernel: [   47.190134] monitor/mwait feature present.
Jun 14 21:05:23 Antec-Linux kernel: [   47.190135] using mwait in idle threads.
Jun 14 21:05:23 Antec-Linux kernel: [   47.190142] CPU: Trace cache: 12K uops, L1 D cache: 16K
Jun 14 21:05:23 Antec-Linux kernel: [   47.190145] CPU: L2 cache: 1024K
Jun 14 21:05:23 Antec-Linux kernel: [   47.190147] CPU: Physical Processor ID: 0
Jun 14 21:05:23 Antec-Linux kernel: [   47.190149] CPU: Processor Core ID: 0
Jun 14 21:05:23 Antec-Linux kernel: [   47.190163] Compat vDSO mapped to ffffe000.
Jun 14 21:05:23 Antec-Linux kernel: [   47.190179] Checking 'hlt' instruction... OK.
Jun 14 21:05:23 Antec-Linux kernel: [   47.206346] SMP alternatives: switching to UP code
Jun 14 21:05:23 Antec-Linux kernel: [   47.208217] Early unpacking initramfs... done
Jun 14 21:05:23 Antec-Linux kernel: [   47.520967] ACPI: Core revision 20070126
Jun 14 21:05:23 Antec-Linux kernel: [   47.521036] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun 14 21:05:23 Antec-Linux kernel: [   47.536736] CPU0: Intel(R) Pentium(R) D CPU 2.80GHz stepping 04
Jun 14 21:05:23 Antec-Linux kernel: [   47.536757] SMP alternatives: switching to SMP code
Jun 14 21:05:23 Antec-Linux kernel: [   47.537491] Booting processor 1/1 eip 3000
Jun 14 21:05:23 Antec-Linux kernel: [   47.588013] Initializing CPU#1
Jun 14 21:05:23 Antec-Linux kernel: [   47.669511] Calibrating delay using timer specific routine.. 5845.54 BogoMIPS (lpj=11691096)
Jun 14 21:05:23 Antec-Linux kernel: [   47.669526] monitor/mwait feature present.
Jun 14 21:05:23 Antec-Linux kernel: [   47.669531] CPU: Trace cache: 12K uops, L1 D cache: 16K
Jun 14 21:05:23 Antec-Linux kernel: [   47.669533] CPU: L2 cache: 1024K
Jun 14 21:05:23 Antec-Linux kernel: [   47.669536] CPU: Physical Processor ID: 0
Jun 14 21:05:23 Antec-Linux kernel: [   47.669537] CPU: Processor Core ID: 1
Jun 14 21:05:23 Antec-Linux kernel: [   47.669842] CPU1: Intel(R) Pentium(R) D CPU 2.80GHz stepping 04
Jun 14 21:05:23 Antec-Linux kernel: [   47.669877] Total of 2 processors activated (11471.24 BogoMIPS).
Jun 14 21:05:23 Antec-Linux kernel: [   47.670029] ENABLING IO-APIC IRQs
Jun 14 21:05:23 Antec-Linux kernel: [   47.670205] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 14 21:05:23 Antec-Linux kernel: [   47.820244] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 14 21:05:23 Antec-Linux kernel: [   47.840246] Brought up 2 CPUs
Jun 14 21:05:23 Antec-Linux kernel: [   47.840506] net_namespace: 64 bytes
Jun 14 21:05:23 Antec-Linux kernel: [   47.840517] Booting paravirtualized kernel on bare hardware
Jun 14 21:05:23 Antec-Linux kernel: [   47.841164] Time: 21:04:53  Date: 06/14/08
Jun 14 21:05:23 Antec-Linux kernel: [   47.841188] NET: Registered protocol family 16
Jun 14 21:05:23 Antec-Linux kernel: [   47.841434] EISA bus registered
Jun 14 21:05:23 Antec-Linux kernel: [   47.841440] ACPI: bus type pci registered
Jun 14 21:05:23 Antec-Linux kernel: [   47.841797] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=5
Jun 14 21:05:23 Antec-Linux kernel: [   47.841800] PCI: Using configuration type 1
Jun 14 21:05:23 Antec-Linux kernel: [   47.841802] Setting up standard PCI resources
Jun 14 21:05:23 Antec-Linux kernel: [   47.863829] ACPI: Interpreter enabled
Jun 14 21:05:23 Antec-Linux kernel: [   47.863833] ACPI: (supports S0 S1 S3 S4 S5)
Jun 14 21:05:23 Antec-Linux kernel: [   47.863854] ACPI: Using IOAPIC for interrupt routing
Jun 14 21:05:23 Antec-Linux kernel: [   47.873998] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 14 21:05:23 Antec-Linux kernel: [   47.874699] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Jun 14 21:05:23 Antec-Linux kernel: [   47.874703] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Jun 14 21:05:23 Antec-Linux kernel: [   47.875794] PCI: Transparent bridge - 0000:00:1e.0
Jun 14 21:05:23 Antec-Linux kernel: [   47.879764] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jun 14 21:05:23 Antec-Linux kernel: [   47.879903] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jun 14 21:05:23 Antec-Linux kernel: [   47.880041] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jun 14 21:05:23 Antec-Linux kernel: [   47.880178] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jun 14 21:05:23 Antec-Linux kernel: [   47.880315] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jun 14 21:05:23 Antec-Linux kernel: [   47.880451] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jun 14 21:05:23 Antec-Linux kernel: [   47.880588] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jun 14 21:05:23 Antec-Linux kernel: [   47.880725] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jun 14 21:05:23 Antec-Linux kernel: [   47.880882] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  5E, should be 30 [20070126]
Jun 14 21:05:23 Antec-Linux kernel: [   47.880891] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 14 21:05:23 Antec-Linux kernel: [   47.880930] pnp: PnP ACPI init
Jun 14 21:05:23 Antec-Linux kernel: [   47.880940] ACPI: bus type pnp registered
Jun 14 21:05:23 Antec-Linux kernel: [   47.886723] pnp: PnP ACPI: found 18 devices
Jun 14 21:05:23 Antec-Linux kernel: [   47.886726] ACPI: ACPI bus type pnp unregistered
Jun 14 21:05:23 Antec-Linux kernel: [   47.886731] PnPBIOS: Disabled by ACPI PNP
Jun 14 21:05:23 Antec-Linux kernel: [   47.887014] PCI: Using ACPI for IRQ routing
Jun 14 21:05:23 Antec-Linux kernel: [   47.887018] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 14 21:05:23 Antec-Linux kernel: [   47.920570] NET: Registered protocol family 8
Jun 14 21:05:23 Antec-Linux kernel: [   47.920573] NET: Registered protocol family 20
Jun 14 21:05:23 Antec-Linux kernel: [   47.920696] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 14 21:05:23 Antec-Linux kernel: [   47.920702] hpet0: 3 64-bit timers, 14318180 Hz
Jun 14 21:05:23 Antec-Linux kernel: [   47.921741] AppArmor: AppArmor Filesystem Enabled
Jun 14 21:05:23 Antec-Linux kernel: [   47.924745] Time: tsc clocksource has been installed.
Jun 14 21:05:23 Antec-Linux kernel: [   47.933162] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933173] system 00:08: ioport range 0x290-0x297 has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933180] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933183] system 00:09: ioport range 0x800-0x87f has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933186] system 00:09: ioport range 0x400-0x41f has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933188] system 00:09: ioport range 0x480-0x4bf has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933191] system 00:09: ioport range 0x900-0x91f has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933194] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933197] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933200] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933203] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933212] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933215] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933223] system 00:10: iomem range 0xf0000000-0xf3ffffff has been reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933231] system 00:11: iomem range 0x0-0x9ffff could not be reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933235] system 00:11: iomem range 0xc0000-0xdffff could not be reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933238] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933241] system 00:11: iomem range 0x100000-0x7fffffff could not be reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.933243] system 00:11: iomem range 0x0-0x0 could not be reserved
Jun 14 21:05:23 Antec-Linux kernel: [   47.963737] PCI: Bridge: 0000:00:01.0
Jun 14 21:05:23 Antec-Linux kernel: [   47.963741]   IO window: e000-efff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963745]   MEM window: e7f00000-e7ffffff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963749]   PREFETCH window: e8000000-efffffff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963753] PCI: Bridge: 0000:00:1c.0
Jun 14 21:05:23 Antec-Linux kernel: [   47.963756]   IO window: d000-dfff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963761]   MEM window: disabled.
Jun 14 21:05:23 Antec-Linux kernel: [   47.963765]   PREFETCH window: disabled.
Jun 14 21:05:23 Antec-Linux kernel: [   47.963770] PCI: Bridge: 0000:00:1c.4
Jun 14 21:05:23 Antec-Linux kernel: [   47.963773]   IO window: c000-cfff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963778]   MEM window: e7e00000-e7efffff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963782]   PREFETCH window: disabled.
Jun 14 21:05:23 Antec-Linux kernel: [   47.963787] PCI: Bridge: 0000:00:1c.5
Jun 14 21:05:23 Antec-Linux kernel: [   47.963790]   IO window: b000-bfff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963795]   MEM window: e7d00000-e7dfffff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963799]   PREFETCH window: disabled.
Jun 14 21:05:23 Antec-Linux kernel: [   47.963807] PCI: Bridge: 0000:00:1e.0
Jun 14 21:05:23 Antec-Linux kernel: [   47.963810]   IO window: 9000-afff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963816]   MEM window: e7c00000-e7cfffff
Jun 14 21:05:23 Antec-Linux kernel: [   47.963820]   PREFETCH window: disabled.
Jun 14 21:05:23 Antec-Linux kernel: [   47.963841] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 14 21:05:23 Antec-Linux kernel: [   47.963866] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 14 21:05:23 Antec-Linux kernel: [   47.963891] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Jun 14 21:05:23 Antec-Linux kernel: [   47.963917] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
Jun 14 21:05:23 Antec-Linux kernel: [   47.963948] NET: Registered protocol family 2
Jun 14 21:05:23 Antec-Linux kernel: [   48.004314] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 14 21:05:23 Antec-Linux kernel: [   48.004636] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 14 21:05:23 Antec-Linux kernel: [   48.005252] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 14 21:05:23 Antec-Linux kernel: [   48.005557] TCP: Hash tables configured (established 131072 bind 65536)
Jun 14 21:05:23 Antec-Linux kernel: [   48.005560] TCP reno registered
Jun 14 21:05:23 Antec-Linux kernel: [   48.016960] checking if image is initramfs... it is
Jun 14 21:05:23 Antec-Linux kernel: [   48.632678] Freeing initrd memory: 7321k freed
Jun 14 21:05:23 Antec-Linux kernel: [   48.633605] audit: initializing netlink socket (disabled)
Jun 14 21:05:23 Antec-Linux kernel: [   48.633620] audit(1213477493.344:1): initialized
Jun 14 21:05:23 Antec-Linux kernel: [   48.633852] highmem bounce pool size: 64 pages
Jun 14 21:05:23 Antec-Linux kernel: [   48.636353] VFS: Disk quotas dquot_6.5.1
Jun 14 21:05:23 Antec-Linux kernel: [   48.636442] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 14 21:05:23 Antec-Linux kernel: [   48.636587] io scheduler noop registered
Jun 14 21:05:23 Antec-Linux kernel: [   48.636590] io scheduler anticipatory registered
Jun 14 21:05:23 Antec-Linux kernel: [   48.636592] io scheduler deadline registered
Jun 14 21:05:23 Antec-Linux kernel: [   48.636605] io scheduler cfq registered (default)
Jun 14 21:05:23 Antec-Linux kernel: [   48.636871] assign_interrupt_mode Found MSI capability
Jun 14 21:05:23 Antec-Linux kernel: [   48.637049] assign_interrupt_mode Found MSI capability
Jun 14 21:05:23 Antec-Linux kernel: [   48.637293] assign_interrupt_mode Found MSI capability
Jun 14 21:05:23 Antec-Linux kernel: [   48.637475] assign_interrupt_mode Found MSI capability
Jun 14 21:05:23 Antec-Linux kernel: [   48.637835] isapnp: Scanning for PnP cards...
Jun 14 21:05:23 Antec-Linux kernel: [   49.003200] isapnp: No Plug & Play device found
Jun 14 21:05:23 Antec-Linux kernel: [   49.040890] Real Time Clock Driver v1.12ac
Jun 14 21:05:23 Antec-Linux kernel: [   49.041008] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 14 21:05:23 Antec-Linux kernel: [   49.041136] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 14 21:05:23 Antec-Linux kernel: [   49.042045] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 14 21:05:23 Antec-Linux kernel: [   49.043025] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 14 21:05:23 Antec-Linux kernel: [   49.043103] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 14 21:05:23 Antec-Linux kernel: [   49.043242] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Jun 14 21:05:23 Antec-Linux kernel: [   49.045412] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 14 21:05:23 Antec-Linux kernel: [   49.045419] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 14 21:05:23 Antec-Linux kernel: [   49.055751] mice: PS/2 mouse device common for all mice
Jun 14 21:05:23 Antec-Linux kernel: [   49.055900] EISA: Probing bus 0 at eisa.0
Jun 14 21:05:23 Antec-Linux kernel: [   49.055922] Cannot allocate resource for EISA slot 6
Jun 14 21:05:23 Antec-Linux kernel: [   49.055925] Cannot allocate resource for EISA slot 7
Jun 14 21:05:23 Antec-Linux kernel: [   49.055927] Cannot allocate resource for EISA slot 8
Jun 14 21:05:23 Antec-Linux kernel: [   49.055929] EISA: Detected 0 cards.
Jun 14 21:05:23 Antec-Linux kernel: [   49.055931] cpuidle: using governor ladder
Jun 14 21:05:23 Antec-Linux kernel: [   49.055934] cpuidle: using governor menu
Jun 14 21:05:23 Antec-Linux kernel: [   49.056014] NET: Registered protocol family 1
Jun 14 21:05:23 Antec-Linux kernel: [   49.056045] Using IPI No-Shortcut mode
Jun 14 21:05:23 Antec-Linux kernel: [   49.056075] registered taskstats version 1
Jun 14 21:05:23 Antec-Linux kernel: [   49.056196]   Magic number: 12:791:95
Jun 14 21:05:23 Antec-Linux kernel: [   49.056308] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 14 21:05:23 Antec-Linux kernel: [   49.056310] EDD information not available.
Jun 14 21:05:23 Antec-Linux kernel: [   49.056501] Freeing unused kernel memory: 368k freed
Jun 14 21:05:23 Antec-Linux kernel: [   49.074800] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 14 21:05:23 Antec-Linux kernel: [   50.303211] fuse init (API version 7.9)
Jun 14 21:05:23 Antec-Linux kernel: [   50.457507] ACPI Warning (tbutils-0217): Incorrect checksum in table [  ^Y°] -  00, should be 36 [20070126]
Jun 14 21:05:23 Antec-Linux kernel: [   50.457529] ACPI Error (tbinstal-0134): Table has invalid signature [  ^Y°], must be SSDT, PSDT or OEMx [20070126]
Jun 14 21:05:23 Antec-Linux kernel: [   50.457551] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node f7c45150), AE_BAD_SIGNATURE
Jun 14 21:05:23 Antec-Linux kernel: [   50.539109] ACPI: Processor [CPU1] (supports 8 throttling states)
Jun 14 21:05:23 Antec-Linux kernel: [   50.639330] ACPI Warning (tbutils-0217): Incorrect checksum in table [  ^Y°] -  00, should be 36 [20070126]
Jun 14 21:05:23 Antec-Linux kernel: [   50.639350] ACPI Error (tbinstal-0134): Table has invalid signature [  ^Y°], must be SSDT, PSDT or OEMx [20070126]
Jun 14 21:05:23 Antec-Linux kernel: [   50.639375] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node f7c451e0), AE_BAD_SIGNATURE
Jun 14 21:05:23 Antec-Linux kernel: [   50.639446] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 14 21:05:23 Antec-Linux kernel: [   50.639460] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 14 21:05:23 Antec-Linux kernel: [   51.027918] usbcore: registered new interface driver usbfs
Jun 14 21:05:23 Antec-Linux kernel: [   51.027945] usbcore: registered new interface driver hub
Jun 14 21:05:23 Antec-Linux kernel: [   51.038275] usbcore: registered new device driver usb
Jun 14 21:05:23 Antec-Linux kernel: [   51.054796] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
Jun 14 21:05:23 Antec-Linux kernel: [   51.054801] Copyright (c) 1999-2006 Intel Corporation.
Jun 14 21:05:23 Antec-Linux kernel: [   51.054874] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 14 21:05:23 Antec-Linux kernel: [   51.073781] USB Universal Host Controller Interface driver v3.0
Jun 14 21:05:23 Antec-Linux kernel: [   51.119510] e1000: 0000:03:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:17:31:3f:73:49
Jun 14 21:05:23 Antec-Linux kernel: [   51.153440] SCSI subsystem initialized
Jun 14 21:05:23 Antec-Linux kernel: [   51.177821] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Jun 14 21:05:23 Antec-Linux kernel: [   51.177874] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Jun 14 21:05:23 Antec-Linux kernel: [   51.177891] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 14 21:05:23 Antec-Linux kernel: [   51.178113] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jun 14 21:05:23 Antec-Linux kernel: [   51.178144] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006000
Jun 14 21:05:23 Antec-Linux kernel: [   51.178303] usb usb1: configuration #1 chosen from 1 choice
Jun 14 21:05:23 Antec-Linux kernel: [   51.178332] hub 1-0:1.0: USB hub found
Jun 14 21:05:23 Antec-Linux kernel: [   51.178339] hub 1-0:1.0: 2 ports detected
Jun 14 21:05:23 Antec-Linux kernel: [   51.211924] Floppy drive(s): fd0 is 1.44M
Jun 14 21:05:23 Antec-Linux kernel: [   51.233702] FDC 0 is a post-1991 82077
Jun 14 21:05:23 Antec-Linux kernel: [   51.282049] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
Jun 14 21:05:23 Antec-Linux kernel: [   51.282067] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun 14 21:05:23 Antec-Linux kernel: [   51.282095] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jun 14 21:05:23 Antec-Linux kernel: [   51.282125] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006400
Jun 14 21:05:23 Antec-Linux kernel: [   51.282253] usb usb2: configuration #1 chosen from 1 choice
Jun 14 21:05:23 Antec-Linux kernel: [   51.282282] hub 2-0:1.0: USB hub found
Jun 14 21:05:23 Antec-Linux kernel: [   51.282290] hub 2-0:1.0: 2 ports detected
Jun 14 21:05:23 Antec-Linux kernel: [   51.385958] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Jun 14 21:05:23 Antec-Linux kernel: [   51.385974] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 14 21:05:23 Antec-Linux kernel: [   51.386000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jun 14 21:05:23 Antec-Linux kernel: [   51.386029] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00006800
Jun 14 21:05:23 Antec-Linux kernel: [   51.386153] usb usb3: configuration #1 chosen from 1 choice
Jun 14 21:05:23 Antec-Linux kernel: [   51.386182] hub 3-0:1.0: USB hub found
Jun 14 21:05:23 Antec-Linux kernel: [   51.386189] hub 3-0:1.0: 2 ports detected
Jun 14 21:05:23 Antec-Linux kernel: [   51.489839] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 20
Jun 14 21:05:23 Antec-Linux kernel: [   51.489857] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jun 14 21:05:23 Antec-Linux kernel: [   51.489883] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Jun 14 21:05:23 Antec-Linux kernel: [   51.489912] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00007000
Jun 14 21:05:23 Antec-Linux kernel: [   51.490039] usb usb4: configuration #1 chosen from 1 choice
Jun 14 21:05:23 Antec-Linux kernel: [   51.490068] hub 4-0:1.0: USB hub found
Jun 14 21:05:23 Antec-Linux kernel: [   51.490075] hub 4-0:1.0: 2 ports detected
Jun 14 21:05:23 Antec-Linux kernel: [   51.521704] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jun 14 21:05:23 Antec-Linux kernel: [   51.593858] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun 14 21:05:23 Antec-Linux kernel: [   51.593900] skge 1.13 addr 0xe7cfc000 irq 21 chip Yukon-Lite rev 9
Jun 14 21:05:23 Antec-Linux kernel: [   51.594284] skge eth1: addr 00:17:31:3f:66:6b
Jun 14 21:05:23 Antec-Linux kernel: [   51.594433] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Jun 14 21:05:23 Antec-Linux kernel: [   51.594448] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 14 21:05:23 Antec-Linux kernel: [   51.594480] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jun 14 21:05:23 Antec-Linux kernel: [   51.598381] ehci_hcd 0000:00:1d.7: debug port 1
Jun 14 21:05:23 Antec-Linux kernel: [   51.598393] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xe7bff800
Jun 14 21:05:23 Antec-Linux kernel: [   51.652488] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 14 21:05:23 Antec-Linux kernel: [   51.652618] usb usb5: configuration #1 chosen from 1 choice
Jun 14 21:05:23 Antec-Linux kernel: [   51.652650] hub 5-0:1.0: USB hub found
Jun 14 21:05:23 Antec-Linux kernel: [   51.652659] hub 5-0:1.0: 8 ports detected
Jun 14 21:05:23 Antec-Linux kernel: [   51.756627] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 14 21:05:23 Antec-Linux kernel: [   51.759935] scsi0 : sata_sil24
Jun 14 21:05:23 Antec-Linux kernel: [   51.760002] scsi1 : sata_sil24
Jun 14 21:05:23 Antec-Linux kernel: [   51.760038] ata1: SATA max UDMA/100 host m128@0xe7dffc00 port 0xe7df8000 irq 17
Jun 14 21:05:23 Antec-Linux kernel: [   51.760043] ata2: SATA max UDMA/100 host m128@0xe7dffc00 port 0xe7dfa000 irq 17
Jun 14 21:05:23 Antec-Linux kernel: [   52.609601] usb 5-1: new high speed USB device using ehci_hcd and address 2
Jun 14 21:05:23 Antec-Linux kernel: [   52.886031] usb 5-1: configuration #1 chosen from 1 choice
Jun 14 21:05:23 Antec-Linux kernel: [   53.362483] usb 5-7: new high speed USB device using ehci_hcd and address 4
Jun 14 21:05:23 Antec-Linux kernel: [   53.498727] usb 5-7: configuration #1 chosen from 1 choice
Jun 14 21:05:23 Antec-Linux kernel: [   53.738229] usb 1-2: new full speed USB device using uhci_hcd and address 4
Jun 14 21:05:23 Antec-Linux kernel: [   53.834957] ata1: SATA link down (SStatus 0 SControl 0)
Jun 14 21:05:23 Antec-Linux kernel: [   53.963544] usb 1-2: configuration #1 chosen from 1 choice
Jun 14 21:05:23 Antec-Linux kernel: [   53.968495] usbcore: registered new interface driver libusual
Jun 14 21:05:23 Antec-Linux kernel: [   53.974156] Initializing USB Mass Storage driver...
Jun 14 21:05:23 Antec-Linux kernel: [   53.974966] scsi2 : SCSI emulation for USB Mass Storage devices
Jun 14 21:05:23 Antec-Linux kernel: [   53.975574] usbcore: registered new interface driver usb-storage
Jun 14 21:05:23 Antec-Linux kernel: [   53.975578] USB Mass Storage support registered.
Jun 14 21:05:23 Antec-Linux kernel: [   55.911433] ata2: SATA link down (SStatus 0 SControl 0)
Jun 14 21:05:23 Antec-Linux kernel: [   55.911614] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun 14 21:05:23 Antec-Linux kernel: [   55.961349] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[e7cfb800-e7cfbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun 14 21:05:23 Antec-Linux kernel: [   55.961439] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
Jun 14 21:05:23 Antec-Linux kernel: [   55.961499] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Jun 14 21:05:23 Antec-Linux kernel: [   55.961531] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
Jun 14 21:05:23 Antec-Linux kernel: [   55.961566] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Jun 14 21:05:23 Antec-Linux kernel: [   55.964359] pata_it821x: controller in pass through mode.
Jun 14 21:05:23 Antec-Linux kernel: [   55.964376] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 19 (level, low) -> IRQ 20
Jun 14 21:05:23 Antec-Linux kernel: [   55.964539] scsi3 : pata_it821x
Jun 14 21:05:23 Antec-Linux kernel: [   55.964597] scsi4 : pata_it821x
Jun 14 21:05:23 Antec-Linux kernel: [   55.964630] ata3: PATA max UDMA/133 cmd 0xa400 ctl 0xa000 bmdma 0x9000 irq 20
Jun 14 21:05:23 Antec-Linux kernel: [   55.964633] ata4: PATA max UDMA/133 cmd 0x9800 ctl 0x9400 bmdma 0x9008 irq 20
Jun 14 21:05:23 Antec-Linux kernel: [   56.299419] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
Jun 14 21:05:23 Antec-Linux kernel: [   56.301337] scsi5 : ata_piix
Jun 14 21:05:23 Antec-Linux kernel: [   56.301833] scsi6 : ata_piix
Jun 14 21:05:23 Antec-Linux kernel: [   56.303347] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jun 14 21:05:23 Antec-Linux kernel: [   56.303351] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jun 14 21:05:23 Antec-Linux kernel: [   56.974724] ata5.00: ATAPI: LITE-ON DVDRW SHW-16H5S, LS0N, max UDMA/66
Jun 14 21:05:23 Antec-Linux kernel: [   56.974753] ata5.01: ATAPI: LITE-ON DVD SHD-16P1S, GS02, max UDMA/33
Jun 14 21:05:23 Antec-Linux kernel: [   57.162251] ata5.00: configured for UDMA/66
Jun 14 21:05:23 Antec-Linux kernel: [   57.334132] ata5.01: configured for UDMA/33
Jun 14 21:05:23 Antec-Linux kernel: [   57.502113] scsi 5:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-16H5S  LS0N PQ: 0 ANSI: 5
Jun 14 21:05:23 Antec-Linux kernel: [   57.502708] scsi 5:0:1:0: CD-ROM            LITE-ON  DVD SHD-16P1S    GS02 PQ: 0 ANSI: 5
Jun 14 21:05:23 Antec-Linux kernel: [   57.502782] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jun 14 21:05:23 Antec-Linux kernel: [   57.502806] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
Jun 14 21:05:23 Antec-Linux kernel: [   57.502904] scsi7 : ata_piix
Jun 14 21:05:23 Antec-Linux kernel: [   57.502954] scsi8 : ata_piix
Jun 14 21:05:23 Antec-Linux kernel: [   57.502990] ata7: SATA max UDMA/133 cmd 0x8800 ctl 0x8400 bmdma 0x7400 irq 23
Jun 14 21:05:23 Antec-Linux kernel: [   57.502993] ata8: SATA max UDMA/133 cmd 0x8000 ctl 0x7800 bmdma 0x7408 irq 23
Jun 14 21:05:23 Antec-Linux kernel: [   57.713607] ata7.00: ATA-7: ST3300622AS, 3.AAH, max UDMA/133
Jun 14 21:05:23 Antec-Linux kernel: [   57.713611] ata7.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 14 21:05:23 Antec-Linux kernel: [   57.780168] ata7.00: configured for UDMA/133
Jun 14 21:05:23 Antec-Linux kernel: [   57.991022] ata8.00: ATA-7: ST3300622AS, 3.AAH, max UDMA/133
Jun 14 21:05:23 Antec-Linux kernel: [   57.991026] ata8.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 14 21:05:23 Antec-Linux kernel: [   58.082551] ata8.00: configured for UDMA/133
Jun 14 21:05:23 Antec-Linux kernel: [   58.082660] scsi 7:0:0:0: Direct-Access     ATA      ST3300622AS      3.AA PQ: 0 ANSI: 5
Jun 14 21:05:23 Antec-Linux kernel: [   58.082816] scsi 8:0:0:0: Direct-Access     ATA      ST3300622AS      3.AA PQ: 0 ANSI: 5
Jun 14 21:05:23 Antec-Linux kernel: [   58.091441] Driver 'sr' needs updating - please use bus_type methods
Jun 14 21:05:23 Antec-Linux kernel: [   58.095626] Driver 'sd' needs updating - please use bus_type methods
Jun 14 21:05:23 Antec-Linux kernel: [   58.097794] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Jun 14 21:05:23 Antec-Linux kernel: [   58.097800] Uniform CD-ROM driver Revision: 3.20
Jun 14 21:05:23 Antec-Linux kernel: [   58.100835] sr1: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
Jun 14 21:05:23 Antec-Linux kernel: [   58.101013] sd 7:0:0:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
Jun 14 21:05:23 Antec-Linux kernel: [   58.101030] sd 7:0:0:0: [sda] Write Protect is off
Jun 14 21:05:23 Antec-Linux kernel: [   58.101059] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 14 21:05:23 Antec-Linux kernel: [   58.101126] sd 7:0:0:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
Jun 14 21:05:23 Antec-Linux kernel: [   58.101146] sd 7:0:0:0: [sda] Write Protect is off
Jun 14 21:05:23 Antec-Linux kernel: [   58.101178] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 14 21:05:23 Antec-Linux kernel: [   58.101182]  sda:<5>sr 5:0:0:0: Attached scsi generic sg0 type 5
Jun 14 21:05:23 Antec-Linux kernel: [   58.109209] sr 5:0:1:0: Attached scsi generic sg1 type 5
Jun 14 21:05:23 Antec-Linux kernel: [   58.109233] sd 7:0:0:0: Attached scsi generic sg2 type 0
Jun 14 21:05:23 Antec-Linux kernel: [   58.109255] scsi 8:0:0:0: Attached scsi generic sg3 type 0
Jun 14 21:05:23 Antec-Linux kernel: [   58.120335]  sda1
Jun 14 21:05:23 Antec-Linux kernel: [   58.120422] sd 7:0:0:0: [sda] Attached SCSI disk
Jun 14 21:05:23 Antec-Linux kernel: [   58.120503] sd 8:0:0:0: [sdb] 586072368 512-byte hardware sectors (300069 MB)
Jun 14 21:05:23 Antec-Linux kernel: [   58.120520] sd 8:0:0:0: [sdb] Write Protect is off
Jun 14 21:05:23 Antec-Linux kernel: [   58.120549] sd 8:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 14 21:05:23 Antec-Linux kernel: [   58.120603] sd 8:0:0:0: [sdb] 586072368 512-byte hardware sectors (300069 MB)
Jun 14 21:05:23 Antec-Linux kernel: [   58.120618] sd 8:0:0:0: [sdb] Write Protect is off
Jun 14 21:05:23 Antec-Linux kernel: [   58.120645] sd 8:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 14 21:05:23 Antec-Linux kernel: [   58.120649]  sdb: sdb1 sdb2 sdb3 < sdb5 >
Jun 14 21:05:23 Antec-Linux kernel: [   58.182888] sd 8:0:0:0: [sdb] Attached SCSI disk
Jun 14 21:05:23 Antec-Linux kernel: [   58.494849] Attempting manual resume
Jun 14 21:05:23 Antec-Linux kernel: [   58.511379] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun 14 21:05:23 Antec-Linux kernel: [   58.511383] EXT3-fs: write access will be enabled during recovery.
Jun 14 21:05:23 Antec-Linux kernel: [   58.968539] scsi 2:0:0:0: Direct-Access     VIA-P    VT6205-DevB      2.82 PQ: 0 ANSI: 2
Jun 14 21:05:23 Antec-Linux kernel: [   58.969159] scsi 2:0:0:1: Direct-Access     VIA-P    VT6205-DevM      2.82 PQ: 0 ANSI: 2
Jun 14 21:05:23 Antec-Linux kernel: [   58.970697] sd 2:0:0:0: [sdc] Attached SCSI removable disk
Jun 14 21:05:23 Antec-Linux kernel: [   58.970742] sd 2:0:0:0: Attached scsi generic sg4 type 0
Jun 14 21:05:23 Antec-Linux kernel: [   58.971811] sd 2:0:0:1: [sdd] Attached SCSI removable disk
Jun 14 21:05:23 Antec-Linux kernel: [   58.971863] sd 2:0:0:1: Attached scsi generic sg5 type 0
Jun 14 21:05:23 Antec-Linux kernel: [   62.137497] kjournald starting.  Commit interval 5 seconds
Jun 14 21:05:23 Antec-Linux kernel: [   62.137515] EXT3-fs: recovery complete.
Jun 14 21:05:23 Antec-Linux kernel: [   62.137886] EXT3-fs: mounted filesystem with ordered data mode.
Jun 14 21:05:23 Antec-Linux kernel: [   70.713057] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jun 14 21:05:23 Antec-Linux kernel: [   70.867546] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 14 21:05:23 Antec-Linux kernel: [   70.897844] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 14 21:05:23 Antec-Linux kernel: [   71.093733] parport_pc 00:07: reported by Plug and Play ACPI
Jun 14 21:05:23 Antec-Linux kernel: [   71.093848] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jun 14 21:05:23 Antec-Linux kernel: [   71.297437] iTCO_vendor_support: vendor-support=0
Jun 14 21:05:23 Antec-Linux kernel: [   71.337289] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Jun 14 21:05:23 Antec-Linux kernel: [   71.337394] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
Jun 14 21:05:23 Antec-Linux kernel: [   71.337431] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun 14 21:05:23 Antec-Linux kernel: [   71.483148] input: Power Button (FF) as /devices/virtual/input/input3
Jun 14 21:05:23 Antec-Linux kernel: [   71.501140] ACPI: Power Button (FF) [PWRF]
Jun 14 21:05:23 Antec-Linux kernel: [   71.501243] input: Power Button (CM) as /devices/virtual/input/input4
Jun 14 21:05:23 Antec-Linux kernel: [   71.532999] ACPI: Power Button (CM) [PWRB]
Jun 14 21:05:23 Antec-Linux kernel: [   72.157164] udev: renamed network interface eth0 to eth1
Jun 14 21:05:23 Antec-Linux kernel: [   72.190166] udev: renamed network interface eth1_rename to eth0
Jun 14 21:05:23 Antec-Linux kernel: [   72.372621] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 20
Jun 14 21:05:23 Antec-Linux kernel: [   72.398849] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
Jun 14 21:05:23 Antec-Linux kernel: [   72.563825] Linux video capture interface: v2.00
Jun 14 21:05:23 Antec-Linux kernel: [   72.620911] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
Jun 14 21:05:23 Antec-Linux kernel: [   72.645137] usbcore: registered new interface driver uvcvideo
Jun 14 21:05:23 Antec-Linux kernel: [   72.645143] USB Video Class driver (v0.1.0)
Jun 14 21:05:23 Antec-Linux kernel: [   72.653202] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x6004
Jun 14 21:05:23 Antec-Linux kernel: [   72.653221] usbcore: registered new interface driver usblp
Jun 14 21:05:23 Antec-Linux kernel: [   72.743065] usbcore: registered new interface driver snd-usb-audio
Jun 14 21:05:23 Antec-Linux kernel: [   72.805459] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jun 14 21:05:23 Antec-Linux kernel: [   74.006716] lp0: using parport0 (interrupt-driven).
Jun 14 21:05:23 Antec-Linux kernel: [   74.083528] Adding 5100596k swap on /dev/sdb5.  Priority:-1 extents:1 across:5100596k
Jun 14 21:05:23 Antec-Linux kernel: [   74.646961] EXT3 FS on sdb2, internal journal
Jun 14 21:05:23 Antec-Linux kernel: [   75.677230] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 14 21:05:23 Antec-Linux kernel: [   77.297550] No dock devices found.
Jun 14 21:05:23 Antec-Linux kernel: [   78.654026] ppdev: user-space parallel port driver
Jun 14 21:05:24 Antec-Linux kernel: [   78.890755] audit(1213473924.002:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5627 profile="/usr/sbin/cupsd" namespace="default"
Jun 14 21:05:24 Antec-Linux kernel: [   78.954445] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jun 14 21:05:24 Antec-Linux kernel: [   78.954451] apm: disabled - APM is not SMP safe.
Jun 14 21:05:24 Antec-Linux dhcdbd: Started up.
Jun 14 21:05:25 Antec-Linux kernel: [   80.773889] skge eth0: enabling interface
Jun 14 21:05:26 Antec-Linux kernel: [   80.948800] Bluetooth: Core ver 2.11
Jun 14 21:05:26 Antec-Linux kernel: [   80.948900] NET: Registered protocol family 31
Jun 14 21:05:26 Antec-Linux kernel: [   80.948903] Bluetooth: HCI device and connection manager initialized
Jun 14 21:05:26 Antec-Linux kernel: [   80.948907] Bluetooth: HCI socket layer initialized
Jun 14 21:05:26 Antec-Linux kernel: [   81.045609] Bluetooth: L2CAP ver 2.9
Jun 14 21:05:26 Antec-Linux kernel: [   81.045614] Bluetooth: L2CAP socket layer initialized
Jun 14 21:05:26 Antec-Linux kernel: [   81.119344] Bluetooth: RFCOMM socket layer initialized
Jun 14 21:05:26 Antec-Linux kernel: [   81.119359] Bluetooth: RFCOMM TTY layer initialized
Jun 14 21:05:26 Antec-Linux kernel: [   81.119362] Bluetooth: RFCOMM ver 1.8
Jun 14 21:05:27 Antec-Linux kernel: [   82.722548] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
Jun 14 21:05:27 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 14 21:05:30 Antec-Linux kernel: [   84.941070] NET: Registered protocol family 17
Jun 14 21:05:35 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun 14 21:05:35 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 14 21:05:35 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 14 21:05:35 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun 14 21:05:36 Antec-Linux kernel: [   91.400142] NET: Registered protocol family 10
Jun 14 21:05:36 Antec-Linux kernel: [   91.400467] lo: Disabled Privacy Extensions
Jun 14 21:05:36 Antec-Linux kernel: [   91.401555] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 14 21:05:59 Antec-Linux pulseaudio[6449]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
Jun 14 21:05:59 Antec-Linux pulseaudio[6449]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
Jun 14 21:07:22 Antec-Linux kernel: [  199.649165] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun 14 21:07:24 Antec-Linux exiting on signal 15
Jun 14 21:09:45 Antec-Linux syslogd 1.5.0#1ubuntu1: restart.

---

### Post by myotis on 2008-06-14
Can I add to the above and say that it seems to be a problem with shutting down rather than restarting.


I have just tried to shut down the PC rather than re-starting it, and it has hung on the splash screen just as it has been doing when trying to restart it.


Sorry, but the hopefully the log will give a clue, as it seems to throw up several errors.

Graham

---

### Post by myotis on 2008-06-15
Still ploughing through the forum for clues, and while I haven't found an answer, I do realise that its probably worthwhile mentioning that I am dual booting with WINXP so Grub is involved in the start up/maybe shutdown.


I mention it becasue some of the other start up/shut down issues in the forum seem to be related to Grub.


Graham

---

### Post by myotis on 2008-06-15
Ok some more information, if I walk away and leave the PC with the frozen splash screen, it does shut down eventually.


As this now seems to be a shut down problem, should I repost this with a new heading?


Graham

---

### Post by myotis on 2008-06-16
Not a lot of response to this, but continuing to trawl through the forum suggests that this might be a kernal bug, does that sound reasonable, do I just ignore it until a bug fix is released.


There are however, several errors in the log, so is there something else going on here.


I would really appreciate some help on this.


Thanks,


Graham

---

### Post by myotis on 2008-06-18
Not sure if this is allowed but I am going to close this thread as its getting no response and the title is now misleading to the problem.


Graham

---

