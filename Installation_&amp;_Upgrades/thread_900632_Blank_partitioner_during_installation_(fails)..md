---
title: "Blank partitioner during installation (fails)."
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by twattle on 2008-08-25
Hey folks.

I'm having problems installing Kubuntu 8.04 x64 on my desktop PC. Tried both the KDE 3.5 and KDE 4 versions with the same result.

The problem is that upon entering the partitioner it just shows a blank window. Or rather; theres no hard disks/partitions displayed. Naturally this makes the installation fail as it want's me to choose a root partition.

Currently I have a windows partition, aprox 250 GB and an openSUSE partition of roughly the same size (including swap etc.). I want to replace openSUSE with Kubuntu.

I have reason to believe that the problem simply is that my hard drive is not found.

I hope someone can help me solve this issue or just shed a bit of light on what might be the problem.

Below is my system specs and the results of a few commands that might give valuable info.

Hardware:
Asus P5Q-E motherboard,
Seagate Barracuda 7200.11 500 GB (Sata3) hard drive,
random IDE DVD drive.

--------------------------------------------------------------

root@ubuntu:/home/ubuntu# cat /proc/version
Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008

--------------------------------------------------------------

root@ubuntu:/home/ubuntu# lspci
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation ICH10 PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation ICH10 PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation ICH10 PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation ICH10 LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation ICH10 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation ICH10 SMBus Controller
00:1f.5 IDE interface: Intel Corporation ICH10 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9442
01:00.1 Audio device: ATI Technologies Inc Unknown device aa30
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1)
05:02.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

--------------------------------------------------------------

root@ubuntu:/home/ubuntu# mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

--------------------------------------------------------------

root@ubuntu:/home/ubuntu# fdisk -l

--------------------------------------------------------------

root@ubuntu:/home/ubuntu# ls -l /dev/sd*
ls: cannot access /dev/sd*: No such file or directory

--------------------------------------------------------------

root@ubuntu:/home/ubuntu# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/kubuntu-kde4.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  BIOS-e820: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851824) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1245184
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FB460 checksum 0
[    0.000000] ACPI: RSDP 000FB460, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFF70000, 003C (r1 A_M_I_ OEMRSDT   8000805 MSFT       97)
[    0.000000] ACPI: FACP CFF70200, 0084 (r2 A_M_I_ OEMFACP   8000805 MSFT       97)
[    0.000000] ACPI: DSDT CFF70440, 963E (r1  A0986 A0986000        0 INTL 20060113)
[    0.000000] ACPI: FACS CFF7E000, 0040
[    0.000000] ACPI: APIC CFF70390, 006C (r1 A_M_I_ OEMAPIC   8000805 MSFT       97)
[    0.000000] ACPI: MCFG CFF70400, 003C (r1 A_M_I_ OEMMCFG   8000805 MSFT       97)
[    0.000000] ACPI: OEMB CFF7E040, 0081 (r1 A_M_I_ AMI_OEM   8000805 MSFT       97)
[    0.000000] ACPI: HPET CFF79A80, 0038 (r1 A_M_I_ OEMHPET   8000805 MSFT       97)
[    0.000000] ACPI: OSFR CFF79AC0, 00B0 (r1 A_M_I_ OEMOSFR   8000805 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851824) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1245184
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   851824
[    0.000000]     0:  1048576 ->  1245184
[    0.000000] On node 0 totalpages: 1048333
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1224 pages reserved
[    0.000000]   DMA zone: 2717 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833448 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000cff70000 - 00000000cff7e000
[    0.000000] swsusp: Registered nosave memory region: 00000000cff7e000 - 00000000cffd0000
[    0.000000] swsusp: Registered nosave memory region: 00000000cffd0000 - 00000000d0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000d0000000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000ffe00000
[    0.000000] swsusp: Registered nosave memory region: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ee00000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030085
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/kubuntu-kde4.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   41.028049] time.c: Detected 3199.883 MHz processor.
[   41.028734] Console: colour VGA+ 80x25
[   41.028736] console [tty0] enabled
[   41.028748] Checking aperture...
[   41.028754] Calgary: detecting Calgary via BIOS EBDA area
[   41.028755] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   41.028756] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   41.051326] Placing software IO TLB between 0x104d000 - 0x504d000
[   41.075573] Memory: 4045600k/4980736k available (2489k kernel code, 147732k reserved, 1318k data, 320k init)
[   41.075597] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   41.154033] Calibrating delay using timer specific routine.. 6403.74 BogoMIPS (lpj=12807495)
[   41.154053] Security Framework initialized
[   41.154057] SELinux:  Disabled at boot.
[   41.154066] AppArmor: AppArmor initialized
[   41.154068] Failure registering capabilities with primary security module.
[   41.154287] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   41.155754] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   41.156449] Mount-cache hash table entries: 256
[   41.156531] Initializing cgroup subsys ns
[   41.156534] Initializing cgroup subsys cpuacct
[   41.156545] CPU: L1 I cache: 32K, L1 D cache: 32K
[   41.156546] CPU: L2 cache: 6144K
[   41.156547] CPU 0/0 -> Node 0
[   41.156548] using mwait in idle threads.
[   41.156549] CPU: Physical Processor ID: 0
[   41.156550] CPU: Processor Core ID: 0
[   41.156554] CPU0: Thermal monitoring enabled (TM2)
[   41.156563] SMP alternatives: switching to UP code
[   41.157149] Early unpacking initramfs... done
[   41.393555] ACPI: Core revision 20070126
[   41.393590] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   41.458128] Using local APIC timer interrupts.
[   41.489380] APIC timer calibration result 24999081
[   41.489381] Detected 24.999 MHz APIC timer.
[   41.489430] SMP alternatives: switching to SMP code
[   41.489948] Booting processor 1/4 APIC 0x1
[   41.500470] Initializing CPU#1
[   41.577381] Calibrating delay using timer specific routine.. 6399.78 BogoMIPS (lpj=12799575)
[   41.577385] CPU: L1 I cache: 32K, L1 D cache: 32K
[   41.577386] CPU: L2 cache: 6144K
[   41.577387] CPU 1/1 -> Node 0
[   41.577388] CPU: Physical Processor ID: 0
[   41.577388] CPU: Processor Core ID: 1
[   41.577392] CPU1: Thermal monitoring enabled (TM2)
[   41.577976] Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz stepping 07
[   41.578031] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   41.598089] SMP alternatives: switching to SMP code
[   41.598624] Booting processor 2/4 APIC 0x2
[   41.609144] Initializing CPU#2
[   41.689376] Calibrating delay using timer specific routine.. 6399.80 BogoMIPS (lpj=12799613)
[   41.689381] CPU: L1 I cache: 32K, L1 D cache: 32K
[   41.689381] CPU: L2 cache: 6144K
[   41.689383] CPU 2/2 -> Node 0
[   41.689384] CPU: Physical Processor ID: 0
[   41.689384] CPU: Processor Core ID: 2
[   41.689388] CPU2: Thermal monitoring enabled (TM2)
[   41.689971] Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz stepping 07
[   41.690009] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   41.710048] SMP alternatives: switching to SMP code
[   41.710386] Booting processor 3/4 APIC 0x3
[   41.720906] Initializing CPU#3
[   41.801372] Calibrating delay using timer specific routine.. 6399.81 BogoMIPS (lpj=12799628)
[   41.801376] CPU: L1 I cache: 32K, L1 D cache: 32K
[   41.801377] CPU: L2 cache: 6144K
[   41.801378] CPU 3/3 -> Node 0
[   41.801379] CPU: Physical Processor ID: 0
[   41.801380] CPU: Processor Core ID: 3
[   41.801383] CPU3: Thermal monitoring enabled (TM2)
[   41.801968] Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz stepping 07
[   41.801972] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   41.821981] Brought up 4 CPUs
[   41.822047] CPU0 attaching sched-domain:
[   41.822049]  domain 0: span 03
[   41.822050]   groups: 01 02
[   41.822051]   domain 1: span 0f
[   41.822052]    groups: 03 0c
[   41.822053]    domain 2: span 0f
[   41.822054]     groups: 0f
[   41.822055] CPU1 attaching sched-domain:
[   41.822056]  domain 0: span 03
[   41.822057]   groups: 02 01
[   41.822058]   domain 1: span 0f
[   41.822059]    groups: 03 0c
[   41.822060]    domain 2: span 0f
[   41.822061]     groups: 0f
[   41.822062] CPU2 attaching sched-domain:
[   41.822062]  domain 0: span 0c
[   41.822063]   groups: 04 08
[   41.822064]   domain 1: span 0f
[   41.822065]    groups: 0c 03
[   41.822066]    domain 2: span 0f
[   41.822067]     groups: 0f
[   41.822068] CPU3 attaching sched-domain:
[   41.822069]  domain 0: span 0c
[   41.822069]   groups: 08 04
[   41.822071]   domain 1: span 0f
[   41.822071]    groups: 0c 03
[   41.822072]    domain 2: span 0f
[   41.822073]     groups: 0f
[   41.822252] net_namespace: 120 bytes
[   41.822466] Time: 21:02:18  Date: 08/25/08
[   41.822481] NET: Registered protocol family 16
[   41.822591] ACPI: bus type pci registered
[   41.822634] PCI: Using configuration type 1
[   41.824736] ACPI: EC: Look up EC in DSDT
[   41.830715] ACPI: Interpreter enabled
[   41.830716] ACPI: (supports S0 S1 S3 S4 S5)
[   41.830725] ACPI: Using IOAPIC for interrupt routing
[   41.830842] Error attaching device data
[   41.830865] Error attaching device data
[   41.830889] Error attaching device data
[   41.830913] Error attaching device data
[   41.835412] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   41.836534] PCI: Transparent bridge - 0000:00:1e.0
[   41.836556] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   41.836654] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   41.836708] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   41.836783] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   41.836835] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   41.836895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   41.847459] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   41.847533] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   41.847606] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   41.847678] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   41.847751] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   41.847824] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   41.847896] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   41.847970] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   41.848040] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  D9, should be D0 [20070126]
[   41.848044] Linux Plug and Play Support v0.97 (c) Adam Belay
[   41.848061] pnp: PnP ACPI init
[   41.848064] ACPI: bus type pnp registered
[   41.850030] pnp: PnP ACPI: found 17 devices
[   41.850031] ACPI: ACPI bus type pnp unregistered
[   41.850158] PCI: Using ACPI for IRQ routing
[   41.850159] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   41.861399] NET: Registered protocol family 8
[   41.861400] NET: Registered protocol family 20
[   41.861418] PCI-GART: No AMD northbridge found.
[   41.861421] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   41.861423] hpet0: 4 64-bit timers, 14318180 Hz
[   41.862442] AppArmor: AppArmor Filesystem Enabled
[   41.865370] Time: tsc clocksource has been installed.
[   41.865374] Switched to high resolution mode on CPU 0
[   41.865984] Switched to high resolution mode on CPU 3
[   41.866017] Switched to high resolution mode on CPU 2
[   41.866032] Switched to high resolution mode on CPU 1
[   41.873346] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   41.873351] system 00:07: ioport range 0x290-0x29f has been reserved
[   41.873354] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   41.873355] system 00:08: ioport range 0x800-0x87f has been reserved
[   41.873357] system 00:08: ioport range 0x500-0x57f has been reserved
[   41.873358] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
[   41.873360] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   41.873362] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   41.873363] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[   41.873367] system 00:0b: iomem range 0xffc00000-0xffdfffff has been reserved
[   41.873371] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[   41.873373] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   41.873378] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[   41.873382] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[   41.873383] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[   41.873385] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[   41.873386] system 00:10: iomem range 0x100000-0xcfffffff could not be reserved
[   41.873388] system 00:10: iomem range 0x0-0x0 could not be reserved
[   41.873605] PCI: Bridge: 0000:00:01.0
[   41.873606]   IO window: b000-bfff
[   41.873608]   MEM window: fe800000-fe8fffff
[   41.873609]   PREFETCH window: d0000000-dfffffff
[   41.873611] PCI: Bridge: 0000:00:1c.0
[   41.873611]   IO window: disabled.
[   41.873614]   MEM window: disabled.
[   41.873616]   PREFETCH window: fdf00000-fdffffff
[   41.873618] PCI: Bridge: 0000:00:1c.4
[   41.873620]   IO window: d000-dfff
[   41.873622]   MEM window: fea00000-feafffff
[   41.873624]   PREFETCH window: disabled.
[   41.873627] PCI: Bridge: 0000:00:1c.5
[   41.873628]   IO window: c000-cfff
[   41.873631]   MEM window: fe900000-fe9fffff
[   41.873633]   PREFETCH window: disabled.
[   41.873636] PCI: Bridge: 0000:00:1e.0
[   41.873637]   IO window: e000-efff
[   41.873640]   MEM window: feb00000-febfffff
[   41.873642]   PREFETCH window: disabled.
[   41.873650] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.873652] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   41.873663] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   41.873666] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   41.873676] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   41.873679] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   41.873689] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   41.873692] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   41.873698] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   41.873703] NET: Registered protocol family 2
[   41.909402] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   41.909994] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   41.912009] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   41.912351] TCP: Hash tables configured (established 524288 bind 65536)
[   41.912353] TCP reno registered
[   41.921441] checking if image is initramfs... it is
[   42.386868] Freeing initrd memory: 8446k freed
[   42.389460] audit: initializing netlink socket (disabled)
[   42.389470] audit(1219698139.276:1): initialized
[   42.390896] VFS: Disk quotas dquot_6.5.1
[   42.390937] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   42.391004] io scheduler noop registered
[   42.391005] io scheduler anticipatory registered
[   42.391006] io scheduler deadline registered
[   42.391072] io scheduler cfq registered (default)
[   42.395488] Boot video device is 0000:01:00.0
[   42.395608] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   42.395624] assign_interrupt_mode Found MSI capability
[   42.395639] Allocate Port Service[0000:00:01.0:pcie00]
[   42.395685] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   42.395711] assign_interrupt_mode Found MSI capability
[   42.395731] Allocate Port Service[0000:00:1c.0:pcie00]
[   42.395753] Allocate Port Service[0000:00:1c.0:pcie02]
[   42.395805] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   42.395831] assign_interrupt_mode Found MSI capability
[   42.395851] Allocate Port Service[0000:00:1c.4:pcie00]
[   42.395873] Allocate Port Service[0000:00:1c.4:pcie02]
[   42.395924] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   42.395950] assign_interrupt_mode Found MSI capability
[   42.395970] Allocate Port Service[0000:00:1c.5:pcie00]
[   42.395991] Allocate Port Service[0000:00:1c.5:pcie02]
[   42.411438] Real Time Clock Driver v1.12ac
[   42.411543] hpet_resources: 0xfed00000 is busy
[   42.411565] Linux agpgart interface v0.102
[   42.411566] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   42.411661] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.411999] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.412458] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   42.412495] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   42.412551] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   42.412552] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   42.413030] serio: i8042 KBD port at 0x60,0x64 irq 1
[   42.430846] mice: PS/2 mouse device common for all mice
[   42.430871] cpuidle: using governor ladder
[   42.430872] cpuidle: using governor menu
[   42.430949] NET: Registered protocol family 1
[   42.431009] registered taskstats version 1
[   42.431078]   Magic number: 4:82:46
[   42.431080]   hash matches device ttyef
[   42.431096] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   42.431098] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   42.431099] EDD information not available.
[   42.431106] Freeing unused kernel memory: 320k freed
[   42.451068] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   43.526332] fuse init (API version 7.9)
[   43.607802] usbcore: registered new interface driver usbfs
[   43.607815] usbcore: registered new interface driver hub
[   43.608497] usbcore: registered new device driver usb
[   43.612553] USB Universal Host Controller Interface driver v3.0
[   43.612590] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.612598] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   43.612600] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   43.612759] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   43.612780] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[   43.612847] usb usb1: configuration #1 chosen from 1 choice
[   43.612858] hub 1-0:1.0: USB hub found
[   43.612862] hub 1-0:1.0: 2 ports detected
[   43.654929] SCSI subsystem initialized
[   43.665005] libata version 3.00 loaded.
[   43.667210] Floppy drive(s): fd0 is 1.44M
[   43.690312] FDC 0 is a post-1991 82077
[   43.714752] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   43.714760] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   43.714762] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   43.714774] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   43.714795] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[   43.714858] usb usb2: configuration #1 chosen from 1 choice
[   43.714870] hub 2-0:1.0: USB hub found
[   43.714873] hub 2-0:1.0: 2 ports detected
[   43.818732] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   43.818740] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   43.818742] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   43.818756] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   43.818777] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
[   43.818832] usb usb3: configuration #1 chosen from 1 choice
[   43.818843] hub 3-0:1.0: USB hub found
[   43.818846] hub 3-0:1.0: 2 ports detected
[   43.921211] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   43.921215] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   43.921217] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   43.921229] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   43.921248] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[   43.921300] usb usb4: configuration #1 chosen from 1 choice
[   43.921311] hub 4-0:1.0: USB hub found
[   43.921313] hub 4-0:1.0: 2 ports detected
[   44.025194] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   44.025198] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   44.025199] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   44.025210] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   44.025229] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[   44.025279] usb usb5: configuration #1 chosen from 1 choice
[   44.025290] hub 5-0:1.0: USB hub found
[   44.025293] hub 5-0:1.0: 2 ports detected
[   44.129196] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   44.129200] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   44.129202] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   44.129211] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   44.129229] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[   44.129280] usb usb6: configuration #1 chosen from 1 choice
[   44.129291] hub 6-0:1.0: USB hub found
[   44.129295] hub 6-0:1.0: 2 ports detected
[   44.233221] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   44.234394] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   44.234399] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   44.234429] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   44.238346] ehci_hcd 0000:00:1a.7: debug port 1
[   44.238350] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   44.238354] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe7ffc00
[   44.253633] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   44.253690] usb usb7: configuration #1 chosen from 1 choice
[   44.253703] hub 7-0:1.0: USB hub found
[   44.253707] hub 7-0:1.0: 6 ports detected
[   44.353216] ACPI: PCI Interrupt 0000:05:03.0[A] -> GSI 19 (level, low) -> IRQ 19
[   44.353218] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   44.354258] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   44.354264] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   44.354324] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   44.358216] ehci_hcd 0000:00:1d.7: debug port 1
[   44.358220] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   44.358224] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe7ff800
[   44.406856] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febfb000-febfb7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   44.413917] usb 5-2: new low speed USB device using uhci_hcd and address 2
[   44.414416] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   44.415468] skge 1.13 addr 0xfebfc000 irq 18 chip Yukon-Lite rev 9
[   44.415647] skge eth0: addr 00:22:15:06:82:32
[   44.425618] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   44.425689] usb usb8: configuration #1 chosen from 1 choice
[   44.425703] hub 8-0:1.0: USB hub found
[   44.425707] hub 8-0:1.0: 6 ports detected
[   44.529192] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   44.529222] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   44.529229] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   44.529244] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   44.529255] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   44.529260] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[   44.529278] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.529291] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   44.529298] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   44.530843] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.530865] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   44.531333] scsi0 : pata_marvell
[   44.531562] scsi1 : pata_marvell
[   44.531576] ata1: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[   44.531577] ata2: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[   44.532623] BAR5:00:02 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:07 0D:00 0E:00 0F:00
[   44.870912] ata1.00: ATAPI: TSSTcorpCD/DVDW SH-W162C, TS11, max UDMA/33
[   44.977069] usb 5-2: new low speed USB device using uhci_hcd and address 3
[   45.057402] ata1.00: configured for UDMA/33
[   45.058710] BAR5:00:02 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:07 0D:00 0E:00 0F:00
[   45.152270] usb 5-2: configuration #1 chosen from 1 choice
[   45.161300] usbcore: registered new interface driver hiddev
[   45.177333] input: Razer Razer 1600dpi Mouse as /devices/pci0000:00/0000:00:1d.1/usb5/5-2/5-2:1.0/input/input2
[   45.194562] input,hidraw0: USB HID v1.10 Mouse [Razer Razer 1600dpi Mouse] on usb-0000:00:1d.1-2
[   45.194568] usbcore: registered new interface driver usbhid
[   45.194569] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   45.226210] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-W162C TS11 PQ: 0 ANSI: 5
[   45.229392] Driver 'sr' needs updating - please use bus_type methods
[   45.232879] sr0: scsi3-mmc drive: 32x/40x writer cd/rw xa/form2 cdda tray
[   45.232881] Uniform CD-ROM driver Revision: 3.20
[   45.232905] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   45.234698] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   45.685078] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00014867bd]
[   57.212746] end_request: I/O error, dev fd0, sector 0
[   69.387599] end_request: I/O error, dev fd0, sector 0
[   69.387601] Buffer I/O error on device fd0, logical block 0
[   81.558245] end_request: I/O error, dev fd0, sector 0
[   81.558247] Buffer I/O error on device fd0, logical block 0
[   94.737266] end_request: I/O error, dev fd0, sector 0
[  106.916085] end_request: I/O error, dev fd0, sector 0
[  106.916088] Buffer I/O error on device fd0, logical block 0
[  119.082642] end_request: I/O error, dev fd0, sector 0
[  119.082643] Buffer I/O error on device fd0, logical block 0
[  121.226798] ISO 9660 Extensions: Microsoft Joliet Level 3
[  121.256305] ISO 9660 Extensions: RRIP_1991A
[  121.479324] Registering unionfs 1.4
[  121.479326] unionfs: debugging is not enabled
[  121.483737] loop: module loaded
[  121.740468] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[  155.501895] input: PC Speaker as /devices/platform/pcspkr/input/input3
[  156.024491] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  156.323121] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  156.372357] input: Power Button (FF) as /devices/virtual/input/input4
[  156.439160] ACPI: Power Button (FF) [PWRF]
[  156.439215] input: Power Button (CM) as /devices/virtual/input/input5
[  156.499136] ACPI: Power Button (CM) [PWRB]
[  156.924339] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  156.924350] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  156.925445] sky2 0000:02:00.0: v1.20 addr 0xfe9fc000 irq 17 Yukon-EC Ultra (0xb4) rev 3
[  156.926273] sky2 eth1: addr 00:22:15:06:6a:a9
[  157.384166] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[  157.385433] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  157.806784] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[  157.807824] PCI: Setting latency timer of device 0000:01:00.1 to 64
[  159.601381] device-mapper: uevent: version 1.0.3
[  159.601397] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[  161.023379] ip_tables: (C) 2000-2006 Netfilter Core Team
[  161.841354] No dock devices found.
[  165.437046] lp: driver loaded but no devices found
[  165.482132] ppdev: user-space parallel port driver
[  170.598031] skge eth0: enabling interface
[  170.731754] sky2 eth1: enabling interface
[  170.822994] Bluetooth: Core ver 2.11
[  170.823246] NET: Registered protocol family 31
[  170.823248] Bluetooth: HCI device and connection manager initialized
[  170.823250] Bluetooth: HCI socket layer initialized
[  170.846559] Bluetooth: L2CAP ver 2.9
[  170.846561] Bluetooth: L2CAP socket layer initialized
[  170.986388] Bluetooth: RFCOMM socket layer initialized
[  170.986474] Bluetooth: RFCOMM TTY layer initialized
[  170.986475] Bluetooth: RFCOMM ver 1.8
[  172.266382] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[  174.927329] mtrr: type mismatch for d0000000,1000000 old: write-back new: write-combining
[  175.449579] NET: Registered protocol family 17
[  181.512625] NET: Registered protocol family 10
[  181.512760] lo: Disabled Privacy Extensions
[  181.513038] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  191.923309] eth0: no IPv6 routers present
[  321.487426] JFS: nTxBlock = 8192, nTxLock = 65536
[  321.687467] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  321.688860] SGI XFS Quota Management subsystem
[  333.954790] end_request: I/O error, dev fd0, sector 0
[  346.121464] end_request: I/O error, dev fd0, sector 0
[  346.186041] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO

--------------------------------------------------------------

Hope the above info helps.

Thanks in advance.

---

### Post by coffeecat on 2008-08-25
Try searching the forum for 'P5Q-E' or just 'P5Q'. After this thread, [this is the first one]("http://ubuntuforums.org/showthread.php?t=890604") that came up when I searched. It seems that you'll have to wait for drivers for the Intel P45 chipset to trickle down from upstream. Unless you can find a better solution when you search the forum. :p

Oh, and talking of 'razz' smileys - a suggestion. When you post large swathes of code or terminal output, click on 'disable smilies in text' under Additional Options below the message field. Or use the [noparse][noparse][/noparse][/noparse] BBCode.

Although I must admit, I do like the lone 'cool' smiley all by itself. :cool:


:wink:

**Edit:** Just for the record, and so that I don't look like I'm confabulating, the OP has now edited the first post and suppressed the smileys from the terminal output.

---

### Post by twattle on 2008-08-26
> **coffeecat said:**
> Try searching the forum for 'P5Q-E' or just 'P5Q'. After this thread, [this is the first one]("http://ubuntuforums.org/showthread.php?t=890604") that came up when I searched. It seems that you'll have to wait for drivers for the Intel P45 chipset to trickle down from upstream. Unless you can find a better solution when you search the forum. :p

Oh, and talking of 'razz' smileys - a suggestion. When you post large swathes of code or terminal output, click on 'disable smilies in text' under Additional Options below the message field. Or use the [noparse][noparse][/noparse][/noparse] BBCode.

Although I must admit, I do like the lone 'cool' smiley all by itself. :cool:


:wink:

Thanks for the reply. Didn't realize it might be a stand alone problem with the board/chipset. Oh well, seems i might have to look around for another distro.

---

### Post by ris2t on 2008-09-01
Ensure you have your drive set up with AHCI. I have Kubuntu 8.04 x64 with a Asus P5Q-E board working fine (just not full spif sound yet). Catch was ACHI rather than IDE compatibility.

---

