---
title: "corrupt screen when x starts after new install"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by keratos on 2008-10-26
AMD LE-110 2ghz CPU
VIA Technologies, Inc. K8M890 [Chrome9] Integrated Video (rev 11)

just installed ubuntu 8.10 and when X starts the screen goes weird: green and black stripes vertically, I can see two ubuntu splash images albeit they are small, next to each other, at the top of the screen. The text appears green. Weird. 

When I used fedora to examine the ubuntu X log file from fedora I notice the line
**EE VESA(0) V_BIOS address 0xa5340 out of range**


Installed fedora 8, vector linux 5.9 and debian etch 4 on the same box today with no problems.

I can reboot to failsafe mode (single user) which does not start X and I get a console with no networking.

Also, if I add vga=794 to the grub line for the same boot, I get a blank screen all the way through although I can "hear" the boot process.

googled and found/tried this 
[https://bugs.launchpad.net/ubuntu/+source/v86d/+bug/189621](https://bugs.launchpad.net/ubuntu/+source/v86d/+bug/189621)
however I have no networking to download any packages like v86d. /etc/init.d/networking restart gives
**error unknown interface eth0=eth0**
Could this even be the issue ???

---

### Post by taseedorf on 2008-10-26
Had a very similar problem upgrading to 8.10 today...
what video card are you using?  nvidia? if so this is what I did to get it to work.

Uninstalled every nvidia driver and app (such as the settings manager, etc...) and than downloaded the nvidia driver from nvidia.com and installed that.  It may give you some error, but ignore it and continue.  Than, you can install the nvidia settings manager after if you want...

that worked for me, with a similar problem to you...

otherwise...

I would run sudo dpkg-reconfigure xserver-xorg
I think thats the command anyways...
and see if you can get into x

OR boot into failsafe and just do startx and see what it says.

---

### Post by keratos on 2008-10-27
video card as above in 2nd line of 1st post:
**VIA Technologies, Inc. K8M890 [Chrome9] Integrated Video (rev 11)**

dpkg-reconfigure ... NO EFFECT!

login single user and start x from command line ... NO EFFECT!
same error!
**EE VESA(0) V_BIOS address 0xa5340 out of range**

think its a bit less obvious than that , but thanks anyway

---

### Post by keratos on 2008-10-27
BUMP!

this is REALLY annoying. ANY distro I've tried tonight - except ubuntu - works!

Everything is fine until X starts - then the display goes corrupted, freezes and I have to warm reset the box.

I have even cut down the xorg.conf to a minimum!?

combined xorg.conf and X log file attached.

---

### Post by keratos on 2008-10-28
dmesg output is:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Wed Oct 22 00:29:18 UTC 2008 (Ubuntu 2.6.27-7.13-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e9c40 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dfb0000 (usable)
[    0.000000]  BIOS-e820: 000000001dfb0000 - 000000001dfbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dfbe000 - 000000001dfe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dfe0000 - 000000001e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x1dfb0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 1dfb0000 @ 7000-d000
[    0.000000] RAMDISK: 1d75e000 - 1df9f947
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FA910, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 1DFB0100, 0054 (r1 A_M_I_ OEMXSDT   2000820 MSFT       97)
[    0.000000] ACPI: FACP 1DFB0290, 00F4 (r3 A_M_I_ OEMFACP   2000820 MSFT       97)
[    0.000000] ACPI: DSDT 1DFB05C0, 5A0E (r1  A0654 A0654000        0 INTL  2002026)
[    0.000000] ACPI: FACS 1DFBE000, 0040
[    0.000000] ACPI: APIC 1DFB0390, 0068 (r1 A_M_I_ OEMAPIC   2000820 MSFT       97)
[    0.000000] ACPI: MCFG 1DFB0580, 003C (r1 A_M_I_ OEMMCFG   2000820 MSFT       97)
[    0.000000] ACPI: OEMB 1DFBE040, 0046 (r1 A_M_I_ AMI_OEM   2000820 MSFT       97)
[    0.000000] ACPI: HPET 1DFB5FD0, 0038 (r1 A_M_I_ OEMHPET   2000820 MSFT       97)
[    0.000000] ACPI: SSDT 1DFB6010, 00F4 (r1 A_M_I_ POWERNOW        1 AMD         1)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1dfb0000
[    0.000000]   low ram: 00000000 - 1dfb0000
[    0.000000]   bootmap 00002000 - 00005bf8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dfb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [001d75e000 - 001df9f947]          RAMDISK ==> [001d75e000 - 001df9f947]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009b000 - 0000100000]    BIOS reserved ==> [000009b000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000006000]          BOOTMAP ==> [0000002000 - 0000006000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001dfb0
[    0.000000]   HighMem  0x0001dfb0 -> 0x0001dfb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0001dfb0
[    0.000000] On node 0 totalpages: 122699
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3959 pages, LIFO batch:0
[    0.000000]   Normal zone: 117660 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ea000
[    0.000000] PM: Registered nosave memory: 00000000000ea000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121619
[    0.000000] Kernel command line: root=UUID=dbb5761e-0fa1-4a0e-bb03-c6b3a31f5033 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2279.971 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 472372k/491200k available (2572k kernel code, 18188k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xde800000 - 0xff3fe000   ( 523 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xddfb0000   ( 479 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4559.94 BogoMIPS (lpj=9119884)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.016451] SMP alternatives: switching to UP code
[    0.033974] ACPI: Core revision 20080609
[    0.036082] ACPI: Checking initramfs for custom DSDT
[    0.356262] ENABLING IO-APIC IRQs
[    0.356437] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[    0.396129] CPU0: AMD Sempron(tm) Processor LE-1100 stepping 01
[    0.400025] Brought up 1 CPUs
[    0.400025] Total of 1 processors activated (4559.94 BogoMIPS).
[    0.400025] CPU0 attaching sched-domain:
[    0.400025]  domain 0: span 0 level CPU
[    0.400025]   groups: 0
[    0.400025] net_namespace: 840 bytes
[    0.400025] Booting paravirtualized kernel on bare hardware
[    0.400025] Time: 21:12:37  Date: 10/27/08
[    0.400025] NET: Registered protocol family 16
[    0.400025] EISA bus registered
[    0.400025] ACPI: bus type pci registered
[    0.400025] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.400025] PCI: Not using MMCONFIG.
[    0.400025] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.400025] PCI: Using configuration type 1 for base access
[    0.400025] ACPI: EC: Look up EC in DSDT
[    0.409456] ACPI: Interpreter enabled
[    0.409460] ACPI: (supports S0 S1 S3 S4 S5)
[    0.409478] ACPI: Using IOAPIC for interrupt routing
[    0.409545] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.415281] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.415284] PCI: Using MMCONFIG for extended config space
[    0.424894] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.424994] PCI: 0000:00:00.0 reg 10 32bit mmio: [ce000000, cfffffff]
[    0.425360] pci 0000:00:01.0: supports D1
[    0.425401] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.425405] pci 0000:00:02.0: PME# disabled
[    0.425451] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.425456] pci 0000:00:03.0: PME# disabled
[    0.425507] PCI: 0000:00:0f.0 reg 20 io port: [fc00, fc0f]
[    0.425565] PCI: 0000:00:10.0 reg 20 io port: [dc00, dc1f]
[    0.425585] pci 0000:00:10.0: supports D1
[    0.425587] pci 0000:00:10.0: supports D2
[    0.425588] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425592] pci 0000:00:10.0: PME# disabled
[    0.425631] PCI: 0000:00:10.1 reg 20 io port: [d880, d89f]
[    0.425650] pci 0000:00:10.1: supports D1
[    0.425652] pci 0000:00:10.1: supports D2
[    0.425654] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425658] pci 0000:00:10.1: PME# disabled
[    0.425699] PCI: 0000:00:10.2 reg 20 io port: [d800, d81f]
[    0.425719] pci 0000:00:10.2: supports D1
[    0.425721] pci 0000:00:10.2: supports D2
[    0.425723] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425727] pci 0000:00:10.2: PME# disabled
[    0.425766] PCI: 0000:00:10.3 reg 20 io port: [d480, d49f]
[    0.425786] pci 0000:00:10.3: supports D1
[    0.425787] pci 0000:00:10.3: supports D2
[    0.425789] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425793] pci 0000:00:10.3: PME# disabled
[    0.425817] PCI: 0000:00:10.4 reg 10 32bit mmio: [f9fffc00, f9fffcff]
[    0.425852] pci 0000:00:10.4: supports D1
[    0.425854] pci 0000:00:10.4: supports D2
[    0.425856] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425860] pci 0000:00:10.4: PME# disabled
[    0.426149] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.426155] PCI: 0000:01:00.0 reg 14 32bit mmio: [fa000000, faffffff]
[    0.426172] PCI: 0000:01:00.0 reg 30 32bit mmio: [fbdf0000, fbdfffff]
[    0.426184] pci 0000:01:00.0: supports D1
[    0.426185] pci 0000:01:00.0: supports D2
[    0.426217] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, fbdfffff]
[    0.426221] PCI: bridge 0000:00:01.0 32bit mmio pref: [d0000000, dfffffff]
[    0.426270] PCI: bridge 0000:00:02.0 64bit mmio pref: [f8e00000, f8efffff]
[    0.426320] PCI: bridge 0000:00:03.0 64bit mmio pref: [f8f00000, f8ffffff]
[    0.426355] PCI: 0000:04:01.0 reg 10 64bit mmio: [fbefc000, fbefffff]
[    0.426385] pci 0000:04:01.0: PME# supported from D0 D3hot D3cold
[    0.426389] pci 0000:04:01.0: PME# disabled
[    0.426427] PCI: bridge 0000:00:13.0 32bit mmio: [fbe00000, fbefffff]
[    0.426470] PCI: 0000:05:09.0 reg 10 io port: [e800, e8ff]
[    0.426476] PCI: 0000:05:09.0 reg 14 32bit mmio: [fbfffc00, fbfffcff]
[    0.426508] pci 0000:05:09.0: supports D1
[    0.426510] pci 0000:05:09.0: supports D2
[    0.426512] pci 0000:05:09.0: PME# supported from D1 D2 D3hot D3cold
[    0.426515] pci 0000:05:09.0: PME# disabled
[    0.426541] pci 0000:00:13.1: transparent bridge
[    0.426545] PCI: bridge 0000:00:13.1 io port: [e000, efff]
[    0.426549] PCI: bridge 0000:00:13.1 32bit mmio: [fbf00000, fbffffff]
[    0.426573] bus 00 -> node 0
[    0.426579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.426887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.426990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.427121] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[    0.427266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.427375] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[    0.449359] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.449509] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.449654] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.449798] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.449942] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.450087] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.450232] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.450377] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.450570] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - C5, should be BD [20080609]
[    0.450591] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.450623] pnp: PnP ACPI init
[    0.450636] ACPI: bus type pnp registered
[    0.456242] pnp: PnP ACPI: found 14 devices
[    0.456246] ACPI: ACPI bus type pnp unregistered
[    0.456249] PnPBIOS: Disabled by ACPI PNP
[    0.456597] PCI: Using ACPI for IRQ routing
[    0.456745] NET: Registered protocol family 8
[    0.456745] NET: Registered protocol family 20
[    0.456745] NetLabel: Initializing
[    0.456745] NetLabel:  domain hash size = 128
[    0.456745] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.456745] NetLabel:  unlabeled traffic allowed by default
[    0.456745] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.456745] hpet0: 3 32-bit timers, 14318180 Hz
[    0.457636] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.457639]    actual entries 65620
[    0.457801] AppArmor: AppArmor Filesystem Enabled
[    0.457823] ACPI: RTC can wake from S4
[    0.457841] system 00:05: ioport range 0xc00-0xc0f has been reserved
[    0.457841] system 00:05: ioport range 0xd00-0xd0f has been reserved
[    0.457841] system 00:05: ioport range 0xa20-0xa2f has been reserved
[    0.457841] system 00:05: ioport range 0xa30-0xa3f has been reserved
[    0.457841] system 00:07: ioport range 0x3e0-0x3e7 has been reserved
[    0.457841] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.457841] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.457841] system 00:07: ioport range 0x400-0x41f has been reserved
[    0.457841] system 00:07: iomem range 0x1c000000-0x1fffffff could not be reserved
[    0.457841] system 00:07: iomem range 0x3c000000-0x3fffffff has been reserved
[    0.457841] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.457841] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.457841] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.457841] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.457841] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.457841] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.457841] system 00:0d: iomem range 0x100000-0x1dffffff could not be reserved
[    0.457841] system 00:0d: iomem range 0xff780000-0xffffffff could not be reserved
[    0.460053] Switched to high resolution mode on CPU 0
[    0.493880] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.493882] pci 0000:00:01.0:   IO window: disabled
[    0.493888] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfbdfffff
[    0.493892] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.493897] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.493899] pci 0000:00:02.0:   IO window: disabled
[    0.493903] pci 0000:00:02.0:   MEM window: disabled
[    0.493907] pci 0000:00:02.0:   PREFETCH window: 0x000000f8e00000-0x000000f8efffff
[    0.493912] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.493914] pci 0000:00:03.0:   IO window: disabled
[    0.493919] pci 0000:00:03.0:   MEM window: disabled
[    0.493923] pci 0000:00:03.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.493929] pci 0000:00:13.0: PCI bridge, secondary bus 0000:04
[    0.493931] pci 0000:00:13.0:   IO window: disabled
[    0.493935] pci 0000:00:13.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.493939] pci 0000:00:13.0:   PREFETCH window: disabled
[    0.493944] pci 0000:00:13.1: PCI bridge, secondary bus 0000:05
[    0.493947] pci 0000:00:13.1:   IO window: 0xe000-0xefff
[    0.493951] pci 0000:00:13.1:   MEM window: 0xfbf00000-0xfbffffff
[    0.493955] pci 0000:00:13.1:   PREFETCH window: disabled
[    0.493974] pci 0000:00:01.0: setting latency timer to 64
[    0.493988] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.493992] pci 0000:00:02.0: setting latency timer to 64
[    0.494000] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    0.494004] pci 0000:00:03.0: setting latency timer to 64
[    0.494010] pci 0000:00:13.0: setting latency timer to 64
[    0.494016] pci 0000:00:13.1: setting latency timer to 64
[    0.494020] bus: 00 index 0 io port: [0, ffff]
[    0.494022] bus: 00 index 1 mmio: [0, ffffffff]
[    0.494024] bus: 01 index 0 mmio: [0, 0]
[    0.494026] bus: 01 index 1 mmio: [fa000000, fbdfffff]
[    0.494028] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.494029] bus: 01 index 3 mmio: [0, 0]
[    0.494031] bus: 02 index 0 mmio: [0, 0]
[    0.494033] bus: 02 index 1 mmio: [0, 0]
[    0.494035] bus: 02 index 2 mmio: [f8e00000, f8efffff]
[    0.494037] bus: 02 index 3 mmio: [0, 0]
[    0.494038] bus: 03 index 0 mmio: [0, 0]
[    0.494040] bus: 03 index 1 mmio: [0, 0]
[    0.494042] bus: 03 index 2 mmio: [f8f00000, f8ffffff]
[    0.494044] bus: 03 index 3 mmio: [0, 0]
[    0.494046] bus: 04 index 0 mmio: [0, 0]
[    0.494048] bus: 04 index 1 mmio: [fbe00000, fbefffff]
[    0.494050] bus: 04 index 2 mmio: [0, 0]
[    0.494051] bus: 04 index 3 mmio: [0, 0]
[    0.494053] bus: 05 index 0 io port: [e000, efff]
[    0.494055] bus: 05 index 1 mmio: [fbf00000, fbffffff]
[    0.494057] bus: 05 index 2 mmio: [0, 0]
[    0.494059] bus: 05 index 3 io port: [0, ffff]
[    0.494061] bus: 05 index 4 mmio: [0, ffffffff]
[    0.494076] NET: Registered protocol family 2
[    0.494251] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.494456] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.494552] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.494654] TCP: Hash tables configured (established 16384 bind 16384)
[    0.494658] TCP reno registered
[    0.494783] NET: Registered protocol family 1
[    0.494911] checking if image is initramfs... it is
[    1.143984] Freeing initrd memory: 8454k freed
[    1.144917] audit: initializing netlink socket (disabled)
[    1.144939] type=2000 audit(1225141957.144:1): initialized
[    1.150227] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.152592] VFS: Disk quotas dquot_6.5.1
[    1.152696] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.152837] msgmni has been set to 939
[    1.152977] io scheduler noop registered
[    1.152980] io scheduler anticipatory registered
[    1.152982] io scheduler deadline registered
[    1.152993] io scheduler cfq registered (default)
[    1.153009] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    1.153021] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.153110] pci 0000:01:00.0: Boot video device
[    1.153261] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.153297] pcieport-driver 0000:00:02.0: found MSI capability
[    1.153301] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.153353] pci_express 0000:00:02.0:pcie01: allocate port service
[    1.153395] pci_express 0000:00:02.0:pcie02: allocate port service
[    1.153436] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.153521] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.153560] pcieport-driver 0000:00:03.0: found MSI capability
[    1.153563] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.153606] pci_express 0000:00:03.0:pcie01: allocate port service
[    1.153651] pci_express 0000:00:03.0:pcie02: allocate port service
[    1.153693] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.156475] aer 0000:00:02.0:pcie01: AER service couldn't init device: no _OSC support
[    1.158992] aer 0000:00:03.0:pcie01: AER service couldn't init device: no _OSC support
[    1.159209] isapnp: Scanning for PnP cards...
[    1.513019] isapnp: No Plug & Play device found
[    1.558943] hpet_acpi_add: no address or irqs in _CRS
[    1.559024] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.561632] brd: module loaded
[    1.561716] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.561855] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.561858] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.561998] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.562749] mice: PS/2 mouse device common for all mice
[    1.562928] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.562962] rtc0: alarms up to one year, y3k, hpet irqs
[    1.563110] EISA: Probing bus 0 at eisa.0
[    1.563147] EISA: Detected 0 cards.
[    1.563151] cpuidle: using governor ladder
[    1.563153] cpuidle: using governor menu
[    1.563607] TCP cubic registered
[    1.563639] Using IPI No-Shortcut mode
[    1.563924] registered taskstats version 1
[    1.564080]   Magic number: 12:450:248
[    1.564125] tty ttyw4: hash matches
[    1.564292] rtc_cmos 00:09: setting system clock to 2008-10-27 21:12:38 UTC (1225141958)
[    1.564295] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.564297] EDD information not available.
[    1.564629] Freeing unused kernel memory: 424k freed
[    1.564689] Write protecting the kernel text: 2576k
[    1.564733] Write protecting the kernel read-only data: 936k
[    1.587421] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.748519] fuse init (API version 7.9)
[    1.843685] processor ACPI0007:00: registered as cooling_device0
[    1.843690] ACPI: Processor [P001] (supports 16 throttling states)
[    1.862311] device-mapper: uevent: version 1.0.3
[    1.862566] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.457919] No dock devices found.
[    2.471790] SCSI subsystem initialized
[    2.498289] libata version 3.00 loaded.
[    2.528318] pata_via 0000:00:0f.0: version 0.3.3
[    2.539621] scsi0 : pata_via
[    2.546891] scsi1 : pata_via
[    2.546970] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.546974] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.581558] usbcore: registered new interface driver usbfs
[    2.581588] usbcore: registered new interface driver hub
[    2.582402] usbcore: registered new device driver usb
[    2.588491] USB Universal Host Controller Interface driver v3.0
[    2.660180] 8139too Fast Ethernet driver 0.9.28
[    2.708623] ata1.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[    2.708627] ata1.00: 320173056 sectors, multi 16: LBA48 
[    2.724474] ata1.00: configured for UDMA/133
[    3.088638] ata2.00: ATA-6: IC35L120AVV207-1, V24OA66A, max UDMA/100
[    3.088643] ata2.00: 241254720 sectors, multi 16: LBA48 
[    3.088660] ata2.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P53, max UDMA/66
[    3.112526] ata2.00: configured for UDMA/100
[    3.144291] ata2.01: configured for UDMA/66
[    3.144443] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[    3.144588] scsi 1:0:0:0: Direct-Access     ATA      IC35L120AVV207-1 V24O PQ: 0 ANSI: 5
[    3.145667] scsi 1:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P53 PQ: 0 ANSI: 5
[    3.146029] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.146041] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.146097] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    3.146130] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000dc00
[    3.146320] usb usb1: configuration #1 chosen from 1 choice
[    3.146345] hub 1-0:1.0: USB hub found
[    3.146356] hub 1-0:1.0: 2 ports detected
[    3.352796] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    3.352809] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.352852] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    3.352886] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000d880
[    3.353058] usb usb2: configuration #1 chosen from 1 choice
[    3.353083] hub 2-0:1.0: USB hub found
[    3.353092] hub 2-0:1.0: 2 ports detected
[    3.422843] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.422882] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    3.422919] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    3.456232] Driver 'sd' needs updating - please use bus_type methods
[    3.456375] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[    3.456398] sd 0:0:0:0: [sda] Write Protect is off
[    3.456400] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.456432] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.456509] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[    3.456526] sd 0:0:0:0: [sda] Write Protect is off
[    3.456528] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.456559] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.456564]  sda: sda1 sda2
[    3.467566] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.467669] sd 1:0:0:0: [sdb] 241254720 512-byte hardware sectors (123522 MB)
[    3.467692] sd 1:0:0:0: [sdb] Write Protect is off
[    3.467694] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.467729] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.467794] sd 1:0:0:0: [sdb] 241254720 512-byte hardware sectors (123522 MB)
[    3.467813] sd 1:0:0:0: [sdb] Write Protect is off
[    3.467815] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.467850] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.467854]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
[    3.488491]  sdb1 sdb2 sdb3
[    3.489095] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.503897] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.503904] Uniform CD-ROM driver Revision: 3.20
[    3.504039] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    3.560364] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    3.560376] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.560405] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    3.560437] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    3.560550] usb usb3: configuration #1 chosen from 1 choice
[    3.560574] hub 3-0:1.0: USB hub found
[    3.560584] hub 3-0:1.0: 2 ports detected
[    3.672062] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    3.768333] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.768345] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    3.768374] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    3.768408] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000d480
[    3.768523] usb usb4: configuration #1 chosen from 1 choice
[    3.768549] hub 4-0:1.0: USB hub found
[    3.768558] hub 4-0:1.0: 2 ports detected
[    3.852436] usb 2-2: configuration #1 chosen from 1 choice
[    3.976321] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    3.976341] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    3.976368] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    3.976407] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf9fffc00
[    3.988021] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.988202] usb usb5: configuration #1 chosen from 1 choice
[    3.988234] hub 5-0:1.0: USB hub found
[    3.988244] hub 5-0:1.0: 8 ports detected
[    4.120050] usb 2-2: USB disconnect, address 2
[    4.198701] 8139too 0000:05:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.199292] eth0: RealTek RTL8139 at 0xe800, 00:1a:92:06:3f:42, IRQ 20
[    4.199294] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.202675] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.304102] usbcore: registered new interface driver hiddev
[    4.304123] usbcore: registered new interface driver usbhid
[    4.304126] usbhid: v2.6:USB HID core driver
[    4.351493] PM: Starting manual resume from disk
[    4.351498] PM: Resume from partition 8:17
[    4.351500] PM: Checking hibernation image.
[    4.351684] PM: Resume from disk failed.
[    4.362839] ReiserFS: sdb3: found reiserfs format "3.6" with standard journal
[    4.362851] ReiserFS: sdb3: using ordered data mode
[    4.367137] ReiserFS: sdb3: journal params: device sdb3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    4.367995] ReiserFS: sdb3: checking transaction log (sdb3)
[    4.405115] ReiserFS: sdb3: Using r5 hash to sort names
[    4.608030] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    4.788093] usb 2-2: configuration #1 chosen from 1 choice
[    4.815226] input: A4Tech Wireless Battery Free Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input2
[    4.815426] input,hidraw0: USB HID v1.10 Mouse [A4Tech Wireless Battery Free Optical Mouse] on usb-0000:00:10.1-2
[    9.845205] udevd version 124 started
[   10.320332] Linux agpgart interface v0.103
[   10.357485] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0336]
[   10.358837] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xd0000000
[   10.627615] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   10.639111] ACPI: Power Button (FF) [PWRF]
[   10.639295] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   10.652043] ACPI: Power Button (CM) [PWRB]
[   11.585743] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.636160] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.080460] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   13.351130] HDA Intel 0000:04:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.351167] HDA Intel 0000:04:01.0: setting latency timer to 64
[   13.351173] HDA Intel 0000:04:01.0: PCI: Disallowing DAC for device
[   15.097282] NET: Registered protocol family 10
[   15.097707] lo: Disabled Privacy Extensions
[   15.805217] loop: module loaded
[   15.857739] lp: driver loaded but no devices found
[   16.106056] Adding 506008k swap on /dev/sdb1.  Priority:-1 extents:1 across:506008k
[   23.482587] type=1505 audit(1225141980.770:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4087
[   23.673496] type=1505 audit(1225141980.962:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4092
[   23.673815] type=1505 audit(1225141980.962:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4092
[   23.769701] ip_tables: (C) 2000-2006 Netfilter Core Team

```

---

### Post by keratos on 2008-10-28
dmesg output is:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Wed Oct 22 00:29:18 UTC 2008 (Ubuntu 2.6.27-7.13-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e9c40 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dfb0000 (usable)
[    0.000000]  BIOS-e820: 000000001dfb0000 - 000000001dfbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dfbe000 - 000000001dfe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dfe0000 - 000000001e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x1dfb0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 1dfb0000 @ 7000-d000
[    0.000000] RAMDISK: 1d75e000 - 1df9f947
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FA910, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 1DFB0100, 0054 (r1 A_M_I_ OEMXSDT   2000820 MSFT       97)
[    0.000000] ACPI: FACP 1DFB0290, 00F4 (r3 A_M_I_ OEMFACP   2000820 MSFT       97)
[    0.000000] ACPI: DSDT 1DFB05C0, 5A0E (r1  A0654 A0654000        0 INTL  2002026)
[    0.000000] ACPI: FACS 1DFBE000, 0040
[    0.000000] ACPI: APIC 1DFB0390, 0068 (r1 A_M_I_ OEMAPIC   2000820 MSFT       97)
[    0.000000] ACPI: MCFG 1DFB0580, 003C (r1 A_M_I_ OEMMCFG   2000820 MSFT       97)
[    0.000000] ACPI: OEMB 1DFBE040, 0046 (r1 A_M_I_ AMI_OEM   2000820 MSFT       97)
[    0.000000] ACPI: HPET 1DFB5FD0, 0038 (r1 A_M_I_ OEMHPET   2000820 MSFT       97)
[    0.000000] ACPI: SSDT 1DFB6010, 00F4 (r1 A_M_I_ POWERNOW        1 AMD         1)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1dfb0000
[    0.000000]   low ram: 00000000 - 1dfb0000
[    0.000000]   bootmap 00002000 - 00005bf8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dfb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [001d75e000 - 001df9f947]          RAMDISK ==> [001d75e000 - 001df9f947]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009b000 - 0000100000]    BIOS reserved ==> [000009b000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000006000]          BOOTMAP ==> [0000002000 - 0000006000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001dfb0
[    0.000000]   HighMem  0x0001dfb0 -> 0x0001dfb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0001dfb0
[    0.000000] On node 0 totalpages: 122699
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3959 pages, LIFO batch:0
[    0.000000]   Normal zone: 117660 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ea000
[    0.000000] PM: Registered nosave memory: 00000000000ea000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121619
[    0.000000] Kernel command line: root=UUID=dbb5761e-0fa1-4a0e-bb03-c6b3a31f5033 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2279.971 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 472372k/491200k available (2572k kernel code, 18188k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xde800000 - 0xff3fe000   ( 523 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xddfb0000   ( 479 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4559.94 BogoMIPS (lpj=9119884)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.016451] SMP alternatives: switching to UP code
[    0.033974] ACPI: Core revision 20080609
[    0.036082] ACPI: Checking initramfs for custom DSDT
[    0.356262] ENABLING IO-APIC IRQs
[    0.356437] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[    0.396129] CPU0: AMD Sempron(tm) Processor LE-1100 stepping 01
[    0.400025] Brought up 1 CPUs
[    0.400025] Total of 1 processors activated (4559.94 BogoMIPS).
[    0.400025] CPU0 attaching sched-domain:
[    0.400025]  domain 0: span 0 level CPU
[    0.400025]   groups: 0
[    0.400025] net_namespace: 840 bytes
[    0.400025] Booting paravirtualized kernel on bare hardware
[    0.400025] Time: 21:12:37  Date: 10/27/08
[    0.400025] NET: Registered protocol family 16
[    0.400025] EISA bus registered
[    0.400025] ACPI: bus type pci registered
[    0.400025] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.400025] PCI: Not using MMCONFIG.
[    0.400025] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.400025] PCI: Using configuration type 1 for base access
[    0.400025] ACPI: EC: Look up EC in DSDT
[    0.409456] ACPI: Interpreter enabled
[    0.409460] ACPI: (supports S0 S1 S3 S4 S5)
[    0.409478] ACPI: Using IOAPIC for interrupt routing
[    0.409545] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.415281] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.415284] PCI: Using MMCONFIG for extended config space
[    0.424894] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.424994] PCI: 0000:00:00.0 reg 10 32bit mmio: [ce000000, cfffffff]
[    0.425360] pci 0000:00:01.0: supports D1
[    0.425401] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.425405] pci 0000:00:02.0: PME# disabled
[    0.425451] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.425456] pci 0000:00:03.0: PME# disabled
[    0.425507] PCI: 0000:00:0f.0 reg 20 io port: [fc00, fc0f]
[    0.425565] PCI: 0000:00:10.0 reg 20 io port: [dc00, dc1f]
[    0.425585] pci 0000:00:10.0: supports D1
[    0.425587] pci 0000:00:10.0: supports D2
[    0.425588] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425592] pci 0000:00:10.0: PME# disabled
[    0.425631] PCI: 0000:00:10.1 reg 20 io port: [d880, d89f]
[    0.425650] pci 0000:00:10.1: supports D1
[    0.425652] pci 0000:00:10.1: supports D2
[    0.425654] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425658] pci 0000:00:10.1: PME# disabled
[    0.425699] PCI: 0000:00:10.2 reg 20 io port: [d800, d81f]
[    0.425719] pci 0000:00:10.2: supports D1
[    0.425721] pci 0000:00:10.2: supports D2
[    0.425723] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425727] pci 0000:00:10.2: PME# disabled
[    0.425766] PCI: 0000:00:10.3 reg 20 io port: [d480, d49f]
[    0.425786] pci 0000:00:10.3: supports D1
[    0.425787] pci 0000:00:10.3: supports D2
[    0.425789] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425793] pci 0000:00:10.3: PME# disabled
[    0.425817] PCI: 0000:00:10.4 reg 10 32bit mmio: [f9fffc00, f9fffcff]
[    0.425852] pci 0000:00:10.4: supports D1
[    0.425854] pci 0000:00:10.4: supports D2
[    0.425856] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425860] pci 0000:00:10.4: PME# disabled
[    0.426149] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.426155] PCI: 0000:01:00.0 reg 14 32bit mmio: [fa000000, faffffff]
[    0.426172] PCI: 0000:01:00.0 reg 30 32bit mmio: [fbdf0000, fbdfffff]
[    0.426184] pci 0000:01:00.0: supports D1
[    0.426185] pci 0000:01:00.0: supports D2
[    0.426217] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, fbdfffff]
[    0.426221] PCI: bridge 0000:00:01.0 32bit mmio pref: [d0000000, dfffffff]
[    0.426270] PCI: bridge 0000:00:02.0 64bit mmio pref: [f8e00000, f8efffff]
[    0.426320] PCI: bridge 0000:00:03.0 64bit mmio pref: [f8f00000, f8ffffff]
[    0.426355] PCI: 0000:04:01.0 reg 10 64bit mmio: [fbefc000, fbefffff]
[    0.426385] pci 0000:04:01.0: PME# supported from D0 D3hot D3cold
[    0.426389] pci 0000:04:01.0: PME# disabled
[    0.426427] PCI: bridge 0000:00:13.0 32bit mmio: [fbe00000, fbefffff]
[    0.426470] PCI: 0000:05:09.0 reg 10 io port: [e800, e8ff]
[    0.426476] PCI: 0000:05:09.0 reg 14 32bit mmio: [fbfffc00, fbfffcff]
[    0.426508] pci 0000:05:09.0: supports D1
[    0.426510] pci 0000:05:09.0: supports D2
[    0.426512] pci 0000:05:09.0: PME# supported from D1 D2 D3hot D3cold
[    0.426515] pci 0000:05:09.0: PME# disabled
[    0.426541] pci 0000:00:13.1: transparent bridge
[    0.426545] PCI: bridge 0000:00:13.1 io port: [e000, efff]
[    0.426549] PCI: bridge 0000:00:13.1 32bit mmio: [fbf00000, fbffffff]
[    0.426573] bus 00 -> node 0
[    0.426579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.426887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.426990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.427121] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[    0.427266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.427375] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[    0.449359] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.449509] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.449654] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.449798] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.449942] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.450087] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.450232] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.450377] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.450570] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - C5, should be BD [20080609]
[    0.450591] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.450623] pnp: PnP ACPI init
[    0.450636] ACPI: bus type pnp registered
[    0.456242] pnp: PnP ACPI: found 14 devices
[    0.456246] ACPI: ACPI bus type pnp unregistered
[    0.456249] PnPBIOS: Disabled by ACPI PNP
[    0.456597] PCI: Using ACPI for IRQ routing
[    0.456745] NET: Registered protocol family 8
[    0.456745] NET: Registered protocol family 20
[    0.456745] NetLabel: Initializing
[    0.456745] NetLabel:  domain hash size = 128
[    0.456745] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.456745] NetLabel:  unlabeled traffic allowed by default
[    0.456745] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.456745] hpet0: 3 32-bit timers, 14318180 Hz
[    0.457636] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.457639]    actual entries 65620
[    0.457801] AppArmor: AppArmor Filesystem Enabled
[    0.457823] ACPI: RTC can wake from S4
[    0.457841] system 00:05: ioport range 0xc00-0xc0f has been reserved
[    0.457841] system 00:05: ioport range 0xd00-0xd0f has been reserved
[    0.457841] system 00:05: ioport range 0xa20-0xa2f has been reserved
[    0.457841] system 00:05: ioport range 0xa30-0xa3f has been reserved
[    0.457841] system 00:07: ioport range 0x3e0-0x3e7 has been reserved
[    0.457841] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.457841] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.457841] system 00:07: ioport range 0x400-0x41f has been reserved
[    0.457841] system 00:07: iomem range 0x1c000000-0x1fffffff could not be reserved
[    0.457841] system 00:07: iomem range 0x3c000000-0x3fffffff has been reserved
[    0.457841] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.457841] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.457841] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.457841] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.457841] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.457841] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.457841] system 00:0d: iomem range 0x100000-0x1dffffff could not be reserved
[    0.457841] system 00:0d: iomem range 0xff780000-0xffffffff could not be reserved
[    0.460053] Switched to high resolution mode on CPU 0
[    0.493880] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.493882] pci 0000:00:01.0:   IO window: disabled
[    0.493888] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfbdfffff
[    0.493892] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.493897] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.493899] pci 0000:00:02.0:   IO window: disabled
[    0.493903] pci 0000:00:02.0:   MEM window: disabled
[    0.493907] pci 0000:00:02.0:   PREFETCH window: 0x000000f8e00000-0x000000f8efffff
[    0.493912] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.493914] pci 0000:00:03.0:   IO window: disabled
[    0.493919] pci 0000:00:03.0:   MEM window: disabled
[    0.493923] pci 0000:00:03.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.493929] pci 0000:00:13.0: PCI bridge, secondary bus 0000:04
[    0.493931] pci 0000:00:13.0:   IO window: disabled
[    0.493935] pci 0000:00:13.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.493939] pci 0000:00:13.0:   PREFETCH window: disabled
[    0.493944] pci 0000:00:13.1: PCI bridge, secondary bus 0000:05
[    0.493947] pci 0000:00:13.1:   IO window: 0xe000-0xefff
[    0.493951] pci 0000:00:13.1:   MEM window: 0xfbf00000-0xfbffffff
[    0.493955] pci 0000:00:13.1:   PREFETCH window: disabled
[    0.493974] pci 0000:00:01.0: setting latency timer to 64
[    0.493988] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.493992] pci 0000:00:02.0: setting latency timer to 64
[    0.494000] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    0.494004] pci 0000:00:03.0: setting latency timer to 64
[    0.494010] pci 0000:00:13.0: setting latency timer to 64
[    0.494016] pci 0000:00:13.1: setting latency timer to 64
[    0.494020] bus: 00 index 0 io port: [0, ffff]
[    0.494022] bus: 00 index 1 mmio: [0, ffffffff]
[    0.494024] bus: 01 index 0 mmio: [0, 0]
[    0.494026] bus: 01 index 1 mmio: [fa000000, fbdfffff]
[    0.494028] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.494029] bus: 01 index 3 mmio: [0, 0]
[    0.494031] bus: 02 index 0 mmio: [0, 0]
[    0.494033] bus: 02 index 1 mmio: [0, 0]
[    0.494035] bus: 02 index 2 mmio: [f8e00000, f8efffff]
[    0.494037] bus: 02 index 3 mmio: [0, 0]
[    0.494038] bus: 03 index 0 mmio: [0, 0]
[    0.494040] bus: 03 index 1 mmio: [0, 0]
[    0.494042] bus: 03 index 2 mmio: [f8f00000, f8ffffff]
[    0.494044] bus: 03 index 3 mmio: [0, 0]
[    0.494046] bus: 04 index 0 mmio: [0, 0]
[    0.494048] bus: 04 index 1 mmio: [fbe00000, fbefffff]
[    0.494050] bus: 04 index 2 mmio: [0, 0]
[    0.494051] bus: 04 index 3 mmio: [0, 0]
[    0.494053] bus: 05 index 0 io port: [e000, efff]
[    0.494055] bus: 05 index 1 mmio: [fbf00000, fbffffff]
[    0.494057] bus: 05 index 2 mmio: [0, 0]
[    0.494059] bus: 05 index 3 io port: [0, ffff]
[    0.494061] bus: 05 index 4 mmio: [0, ffffffff]
[    0.494076] NET: Registered protocol family 2
[    0.494251] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.494456] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.494552] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.494654] TCP: Hash tables configured (established 16384 bind 16384)
[    0.494658] TCP reno registered
[    0.494783] NET: Registered protocol family 1
[    0.494911] checking if image is initramfs... it is
[    1.143984] Freeing initrd memory: 8454k freed
[    1.144917] audit: initializing netlink socket (disabled)
[    1.144939] type=2000 audit(1225141957.144:1): initialized
[    1.150227] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.152592] VFS: Disk quotas dquot_6.5.1
[    1.152696] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.152837] msgmni has been set to 939
[    1.152977] io scheduler noop registered
[    1.152980] io scheduler anticipatory registered
[    1.152982] io scheduler deadline registered
[    1.152993] io scheduler cfq registered (default)
[    1.153009] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    1.153021] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.153110] pci 0000:01:00.0: Boot video device
[    1.153261] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.153297] pcieport-driver 0000:00:02.0: found MSI capability
[    1.153301] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.153353] pci_express 0000:00:02.0:pcie01: allocate port service
[    1.153395] pci_express 0000:00:02.0:pcie02: allocate port service
[    1.153436] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.153521] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.153560] pcieport-driver 0000:00:03.0: found MSI capability
[    1.153563] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.153606] pci_express 0000:00:03.0:pcie01: allocate port service
[    1.153651] pci_express 0000:00:03.0:pcie02: allocate port service
[    1.153693] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.156475] aer 0000:00:02.0:pcie01: AER service couldn't init device: no _OSC support
[    1.158992] aer 0000:00:03.0:pcie01: AER service couldn't init device: no _OSC support
[    1.159209] isapnp: Scanning for PnP cards...
[    1.513019] isapnp: No Plug & Play device found
[    1.558943] hpet_acpi_add: no address or irqs in _CRS
[    1.559024] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.561632] brd: module loaded
[    1.561716] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.561855] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.561858] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.561998] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.562749] mice: PS/2 mouse device common for all mice
[    1.562928] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.562962] rtc0: alarms up to one year, y3k, hpet irqs
[    1.563110] EISA: Probing bus 0 at eisa.0
[    1.563147] EISA: Detected 0 cards.
[    1.563151] cpuidle: using governor ladder
[    1.563153] cpuidle: using governor menu
[    1.563607] TCP cubic registered
[    1.563639] Using IPI No-Shortcut mode
[    1.563924] registered taskstats version 1
[    1.564080]   Magic number: 12:450:248
[    1.564125] tty ttyw4: hash matches
[    1.564292] rtc_cmos 00:09: setting system clock to 2008-10-27 21:12:38 UTC (1225141958)
[    1.564295] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.564297] EDD information not available.
[    1.564629] Freeing unused kernel memory: 424k freed
[    1.564689] Write protecting the kernel text: 2576k
[    1.564733] Write protecting the kernel read-only data: 936k
[    1.587421] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.748519] fuse init (API version 7.9)
[    1.843685] processor ACPI0007:00: registered as cooling_device0
[    1.843690] ACPI: Processor [P001] (supports 16 throttling states)
[    1.862311] device-mapper: uevent: version 1.0.3
[    1.862566] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.457919] No dock devices found.
[    2.471790] SCSI subsystem initialized
[    2.498289] libata version 3.00 loaded.
[    2.528318] pata_via 0000:00:0f.0: version 0.3.3
[    2.539621] scsi0 : pata_via
[    2.546891] scsi1 : pata_via
[    2.546970] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.546974] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.581558] usbcore: registered new interface driver usbfs
[    2.581588] usbcore: registered new interface driver hub
[    2.582402] usbcore: registered new device driver usb
[    2.588491] USB Universal Host Controller Interface driver v3.0
[    2.660180] 8139too Fast Ethernet driver 0.9.28
[    2.708623] ata1.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[    2.708627] ata1.00: 320173056 sectors, multi 16: LBA48 
[    2.724474] ata1.00: configured for UDMA/133
[    3.088638] ata2.00: ATA-6: IC35L120AVV207-1, V24OA66A, max UDMA/100
[    3.088643] ata2.00: 241254720 sectors, multi 16: LBA48 
[    3.088660] ata2.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P53, max UDMA/66
[    3.112526] ata2.00: configured for UDMA/100
[    3.144291] ata2.01: configured for UDMA/66
[    3.144443] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[    3.144588] scsi 1:0:0:0: Direct-Access     ATA      IC35L120AVV207-1 V24O PQ: 0 ANSI: 5
[    3.145667] scsi 1:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P53 PQ: 0 ANSI: 5
[    3.146029] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.146041] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.146097] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    3.146130] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000dc00
[    3.146320] usb usb1: configuration #1 chosen from 1 choice
[    3.146345] hub 1-0:1.0: USB hub found
[    3.146356] hub 1-0:1.0: 2 ports detected
[    3.352796] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    3.352809] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.352852] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    3.352886] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000d880
[    3.353058] usb usb2: configuration #1 chosen from 1 choice
[    3.353083] hub 2-0:1.0: USB hub found
[    3.353092] hub 2-0:1.0: 2 ports detected
[    3.422843] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.422882] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    3.422919] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    3.456232] Driver 'sd' needs updating - please use bus_type methods
[    3.456375] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[    3.456398] sd 0:0:0:0: [sda] Write Protect is off
[    3.456400] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.456432] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.456509] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[    3.456526] sd 0:0:0:0: [sda] Write Protect is off
[    3.456528] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.456559] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.456564]  sda: sda1 sda2
[    3.467566] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.467669] sd 1:0:0:0: [sdb] 241254720 512-byte hardware sectors (123522 MB)
[    3.467692] sd 1:0:0:0: [sdb] Write Protect is off
[    3.467694] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.467729] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.467794] sd 1:0:0:0: [sdb] 241254720 512-byte hardware sectors (123522 MB)
[    3.467813] sd 1:0:0:0: [sdb] Write Protect is off
[    3.467815] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.467850] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.467854]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
[    3.488491]  sdb1 sdb2 sdb3
[    3.489095] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.503897] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.503904] Uniform CD-ROM driver Revision: 3.20
[    3.504039] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    3.560364] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    3.560376] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.560405] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    3.560437] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    3.560550] usb usb3: configuration #1 chosen from 1 choice
[    3.560574] hub 3-0:1.0: USB hub found
[    3.560584] hub 3-0:1.0: 2 ports detected
[    3.672062] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    3.768333] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.768345] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    3.768374] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    3.768408] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000d480
[    3.768523] usb usb4: configuration #1 chosen from 1 choice
[    3.768549] hub 4-0:1.0: USB hub found
[    3.768558] hub 4-0:1.0: 2 ports detected
[    3.852436] usb 2-2: configuration #1 chosen from 1 choice
[    3.976321] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    3.976341] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    3.976368] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    3.976407] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf9fffc00
[    3.988021] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.988202] usb usb5: configuration #1 chosen from 1 choice
[    3.988234] hub 5-0:1.0: USB hub found
[    3.988244] hub 5-0:1.0: 8 ports detected
[    4.120050] usb 2-2: USB disconnect, address 2
[    4.198701] 8139too 0000:05:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.199292] eth0: RealTek RTL8139 at 0xe800, 00:1a:92:06:3f:42, IRQ 20
[    4.199294] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.202675] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.304102] usbcore: registered new interface driver hiddev
[    4.304123] usbcore: registered new interface driver usbhid
[    4.304126] usbhid: v2.6:USB HID core driver
[    4.351493] PM: Starting manual resume from disk
[    4.351498] PM: Resume from partition 8:17
[    4.351500] PM: Checking hibernation image.
[    4.351684] PM: Resume from disk failed.
[    4.362839] ReiserFS: sdb3: found reiserfs format "3.6" with standard journal
[    4.362851] ReiserFS: sdb3: using ordered data mode
[    4.367137] ReiserFS: sdb3: journal params: device sdb3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    4.367995] ReiserFS: sdb3: checking transaction log (sdb3)
[    4.405115] ReiserFS: sdb3: Using r5 hash to sort names
[    4.608030] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    4.788093] usb 2-2: configuration #1 chosen from 1 choice
[    4.815226] input: A4Tech Wireless Battery Free Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input2
[    4.815426] input,hidraw0: USB HID v1.10 Mouse [A4Tech Wireless Battery Free Optical Mouse] on usb-0000:00:10.1-2
[    9.845205] udevd version 124 started
[   10.320332] Linux agpgart interface v0.103
[   10.357485] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0336]
[   10.358837] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xd0000000
[   10.627615] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   10.639111] ACPI: Power Button (FF) [PWRF]
[   10.639295] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   10.652043] ACPI: Power Button (CM) [PWRB]
[   11.585743] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.636160] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.080460] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   13.351130] HDA Intel 0000:04:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.351167] HDA Intel 0000:04:01.0: setting latency timer to 64
[   13.351173] HDA Intel 0000:04:01.0: PCI: Disallowing DAC for device
[   15.097282] NET: Registered protocol family 10
[   15.097707] lo: Disabled Privacy Extensions
[   15.805217] loop: module loaded
[   15.857739] lp: driver loaded but no devices found
[   16.106056] Adding 506008k swap on /dev/sdb1.  Priority:-1 extents:1 across:506008k
[   23.482587] type=1505 audit(1225141980.770:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4087
[   23.673496] type=1505 audit(1225141980.962:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4092
[   23.673815] type=1505 audit(1225141980.962:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4092
[   23.769701] ip_tables: (C) 2000-2006 Netfilter Core Team

```

---

