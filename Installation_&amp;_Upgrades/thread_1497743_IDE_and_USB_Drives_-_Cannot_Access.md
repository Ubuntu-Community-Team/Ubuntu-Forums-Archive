---
title: "IDE and USB Drives - Cannot Access"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by supernal on 2010-05-31
I decided to take the plunge, and ran the Upgrade from the Ubuntu Update Manager.
Installation went fairly smoothly.

Upon reboot i was welcomed with the Purple Ubuntu screen, stating that my 120GB IDE drive was not ready or not available.

I could either wait... Press S to Skip, or M to manually take care of the issue.

In this state, Ubuntu could not see my keyboard from behind my ATEN KVM.
I plugged in my USB Keyboard directly into the machine, and pressed S

Running commands like 
lshw -C disk

Shows me everything plugged into my box, except my IDE Drives.
So i am missing my 120 GB hard drive, and my DVD player. (Both are connected to the single IDE ribbon in my box (Asus p5E3) 
This setup was fine under Karmic Kola 9.10


I also cannot see my USB mass storage device (Seagate External USB drive)

Is this new stable release missing drivers?

How do i even start fixing this issue?

in short.. HELP!!!

---

### Post by supernal on 2010-05-31
Scratch the USB device issue.

Still cannot access anything on my IDE ribbon.

---

### Post by captain_conrad on 2010-05-31
I have a very similar problem

When I start up I am greeted with the purple screen with ubuntu logo and ubuntu word with 5 or 6 dots under it, and the text reads as follows:

An error ocurred while mounting /proc/bus/usb
Press s to skip mounting or m for manual recvoery

I have looked in the /proc/bus folder and there just is not a folder called usb (even with ¨show hidden files¨ selected from the view drop down menu)

Well i just press s and the login screen works fine and i can use my pc, so no major trainsmash. But my compiz desktop effects aren´t switched on when I arrive on my desktop. I then switch them all on, they work perfectly fine, my 6 desktop hexagon rotates nicly in 3d, fun fun fun, but when I switch off and back on, or restart, I get the same purple screen, and arrive at the same standard desktop with all my compiz effects all switched off.

I have no cooking clue whats going on, please help!

---

### Post by supernal on 2010-06-02
Ok, i did some digging.

My IDE controller is the:
**Marvell 88SE6111** 
 1 xUltraDMA  133/100/66 for up to  2 PATA devices 

[http://en.wikipedia.org]("http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#Linux_IDE.28PATA.29_driver_problem_workaround_for_Marvell_88SE6111.2C_88SE6121.2C_88SE6145")

[http://forums.gentoo.org]("http://forums.gentoo.org/viewtopic-t-691990.html?sid=4f805fcbb5da142cb5fd1244379dd59c")


It seems 
nano /etc/modprobe.d/my-marvell.conf
file has a line in it to enable PATA drivers:
```

install pata_marvell /bin/true
options ahci marvell_enable=0
```

I'm not sure where this code segment stands, or if i even have the kernal drivers needed to make it work. (as changing this doesn't seem to enable my IDE cable


I also found this link, which sheds a LOT of light on the situation.

[http://lkml.indiana.edu]("http://lkml.indiana.edu/hypermail/linux/kernel/0809.1/0207.html")

So it seems that the new distros do NOT in fact support a 3 year old IDE controller.
I thought linux always worked on older hardware???

---

### Post by supernal on 2010-06-02
lspci:
```
# lspci
00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01)
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)

```

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=2743040b-9d73-4739-ad1b-1544e8f4993c ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009cc00 (usable)
[    0.000000]  BIOS-e820: 000000000009cc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  BIOS-e820: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 000000000 mask F00000000 write-back
[    0.000000]   3 base 100000000 mask FE0000000 write-back
[    0.000000]   4 base 120000000 mask FF0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff70 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009cc00 (usable)
[    0.000000]  modified: 000000000009cc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  modified: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  modified: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff70000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff70000 page 4k
[    0.000000] kernel direct mapping tables up to cff70000 @ 10000-16000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 14000-1a000
[    0.000000] RAMDISK: 37780000 - 37fef516
[    0.000000] ACPI: RSDP 00000000000fbcf0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cff70100 00054 (v01 A_M_I_ OEMXSDT  11000906 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff70290 000F4 (v03 A_M_I_ OEMFACP  11000906 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff70440 08219 (v01  A1389 A1389002 00000002 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff7e000 00040
[    0.000000] ACPI: APIC 00000000cff70390 0006C (v01 A_M_I_ OEMAPIC  11000906 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff70400 0003C (v01 A_M_I_ OEMMCFG  11000906 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff7e040 00081 (v01 A_M_I_ AMI_OEM  11000906 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff78660 00038 (v01 A_M_I_ OEMHPET  11000906 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000cff786a0 000B0 (v01 A_M_I_ OEMOSFR  11000906 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000015000 - 0000000000019fff]
[    0.000000]   bootmap [000000000001a000 -  000000000003ffff] pages 26
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [0037780000 - 0037fef516]          RAMDISK ==> [0037780000 - 0037fef516]
[    0.000000]   #4 [000009cc00 - 0000100000]    BIOS reserved ==> [000009cc00 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a290]              BRK ==> [0001a2a000 - 0001a2a290]
[    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #7 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 - 0000015000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000cff70
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048316
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 107 pages reserved
[    0.000000]   DMA zone: 3817 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833448 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff70000 - 00000000cff7e000
[    0.000000] PM: Registered nosave memory: 00000000cff7e000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031185
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=2743040b-9d73-4739-ad1b-1544e8f4993c ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4048136k/4980736k available (5409k kernel code, 787472k absent, 145128k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2666.589 MHz processor.
[    0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.17 BogoMIPS (lpj=26665890)
[    0.000027] Security Framework initialized
[    0.000042] AppArmor: AppArmor initialized
[    0.010237] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011643] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.012271] Mount-cache hash table entries: 256
[    0.012388] Initializing cgroup subsys ns
[    0.012392] Initializing cgroup subsys cpuacct
[    0.012395] Initializing cgroup subsys memory
[    0.012401] Initializing cgroup subsys devices
[    0.012403] Initializing cgroup subsys freezer
[    0.012404] Initializing cgroup subsys net_cls
[    0.012420] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.012422] CPU: L2 cache: 2048K
[    0.012425] CPU 0/0x0 -> Node 0
[    0.012426] CPU: Physical Processor ID: 0
[    0.012428] CPU: Processor Core ID: 0
[    0.012430] mce: CPU supports 6 MCE banks
[    0.012437] CPU0: Thermal monitoring enabled (TM2)
[    0.012440] using mwait in idle threads.
[    0.012441] Performance Events: Core2 events, Intel PMU driver.
[    0.012446] ... version:                2
[    0.012447] ... bit width:              40
[    0.012448] ... generic registers:      2
[    0.012450] ... value mask:             000000ffffffffff
[    0.012451] ... max period:             000000007fffffff
[    0.012452] ... fixed-purpose events:   3
[    0.012453] ... event mask:             0000000700000003
[    0.015181] ACPI: Core revision 20090903
[    0.030006] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030010] ftrace: allocating 22518 entries in 89 pages
[    0.040045] Setting APIC routing to flat
[    0.040343] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.154736] CPU0: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.310046] CPU1: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
[    0.310051] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320083] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] CPU2: Thermal monitoring enabled (TM2)
[    0.480120] CPU2: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
[    0.480125] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.490062] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] CPU3: Thermal monitoring enabled (TM2)
[    0.650102] CPU3: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
[    0.650107] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.660009] Brought up 4 CPUs
[    0.660011] Total of 4 processors activated (21331.37 BogoMIPS).
[    0.661116] CPU0 attaching sched-domain:
[    0.661119]  domain 0: span 0-1 level MC
[    0.661121]   groups: 0 1
[    0.661124]   domain 1: span 0-3 level CPU
[    0.661126]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[    0.661132] CPU1 attaching sched-domain:
[    0.661133]  domain 0: span 0-1 level MC
[    0.661135]   groups: 1 0
[    0.661137]   domain 1: span 0-3 level CPU
[    0.661139]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[    0.661143] CPU2 attaching sched-domain:
[    0.661145]  domain 0: span 2-3 level MC
[    0.661146]   groups: 2 3
[    0.661149]   domain 1: span 0-3 level CPU
[    0.661151]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[    0.661155] CPU3 attaching sched-domain:
[    0.661156]  domain 0: span 2-3 level MC
[    0.661158]   groups: 3 2
[    0.661161]   domain 1: span 0-3 level CPU
[    0.661162]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[    0.661288] devtmpfs: initialized
[    0.661288] regulator: core version 0.5
[    0.661288] Time:  3:33:27  Date: 06/02/10
[    0.661288] NET: Registered protocol family 16
[    0.661288] Trying to unpack rootfs image as initramfs...
[    0.661288] ACPI: bus type pci registered
[    0.661288] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.661288] PCI: Not using MMCONFIG.
[    0.661288] PCI: Using configuration type 1 for base access
[    0.661288] bio: create slab <bio-0> at 0
[    0.661288] ACPI: EC: Look up EC in DSDT
[    0.662717] ACPI: Executed 1 blocks of module-level executable AML code
[    0.671554] ACPI: Interpreter enabled
[    0.671557] ACPI: (supports S0 S1 S3 S4 S5)
[    0.671574] ACPI: Using IOAPIC for interrupt routing
[    0.671615] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.673348] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.679939] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.686389] ACPI Warning: Incorrect checksum in table [OEMB] - 92, should be 91 (20090903/tbutils-314)
[    0.686492] ACPI: No dock devices found.
[    0.686582] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.686662] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.686665] pci 0000:00:01.0: PME# disabled
[    0.686725] pci 0000:00:1a.0: reg 20 io port: [0xb800-0xb81f]
[    0.686782] pci 0000:00:1a.1: reg 20 io port: [0xb880-0xb89f]
[    0.686839] pci 0000:00:1a.2: reg 20 io port: [0xbc00-0xbc1f]
[    0.686906] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe8ffc00-0xfe8fffff]
[    0.686952] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.686956] pci 0000:00:1a.7: PME# disabled
[    0.686989] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe8f8000-0xfe8fbfff]
[    0.687023] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.687026] pci 0000:00:1b.0: PME# disabled
[    0.687076] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.687079] pci 0000:00:1c.0: PME# disabled
[    0.687138] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.687141] pci 0000:00:1c.4: PME# disabled
[    0.687192] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.687195] pci 0000:00:1c.5: PME# disabled
[    0.687240] pci 0000:00:1d.0: reg 20 io port: [0xb080-0xb09f]
[    0.687297] pci 0000:00:1d.1: reg 20 io port: [0xb400-0xb41f]
[    0.687356] pci 0000:00:1d.2: reg 20 io port: [0xb480-0xb49f]
[    0.687416] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe8ff800-0xfe8ffbff]
[    0.687462] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.687466] pci 0000:00:1d.7: PME# disabled
[    0.687569] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.687572] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.687575] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.687632] pci 0000:00:1f.2: reg 10 io port: [0xac00-0xac07]
[    0.687637] pci 0000:00:1f.2: reg 14 io port: [0xa880-0xa883]
[    0.687641] pci 0000:00:1f.2: reg 18 io port: [0xa800-0xa807]
[    0.687646] pci 0000:00:1f.2: reg 1c io port: [0xa480-0xa483]
[    0.687651] pci 0000:00:1f.2: reg 20 io port: [0xa400-0xa41f]
[    0.687655] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe8fe800-0xfe8fefff]
[    0.687680] pci 0000:00:1f.2: PME# supported from D3hot
[    0.687683] pci 0000:00:1f.2: PME# disabled
[    0.687706] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe8ff400-0xfe8ff4ff]
[    0.687717] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.687755] pci 0000:01:00.0: reg 10 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.687762] pci 0000:01:00.0: reg 18 64bit mmio: [0xfe9e0000-0xfe9effff]
[    0.687767] pci 0000:01:00.0: reg 20 io port: [0xc000-0xc0ff]
[    0.687774] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfe9c0000-0xfe9dffff]
[    0.687789] pci 0000:01:00.0: supports D1 D2
[    0.687817] pci 0000:01:00.1: reg 10 64bit mmio: [0xfe9fc000-0xfe9fffff]
[    0.687845] pci 0000:01:00.1: supports D1 D2
[    0.687883] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.687886] pci 0000:00:01.0: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.687889] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.687926] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.687966] pci 0000:03:00.0: reg 10 io port: [0xec00-0xec07]
[    0.687973] pci 0000:03:00.0: reg 14 io port: [0xe880-0xe883]
[    0.687979] pci 0000:03:00.0: reg 18 io port: [0xe800-0xe807]
[    0.687986] pci 0000:03:00.0: reg 1c io port: [0xe480-0xe483]
[    0.687993] pci 0000:03:00.0: reg 20 io port: [0xe400-0xe40f]
[    0.688000] pci 0000:03:00.0: reg 24 32bit mmio: [0xfebffc00-0xfebfffff]
[    0.688035] pci 0000:03:00.0: supports D1
[    0.688037] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.688041] pci 0000:03:00.0: PME# disabled
[    0.688082] pci 0000:00:1c.4: bridge io port: [0xe000-0xefff]
[    0.688085] pci 0000:00:1c.4: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.688140] pci 0000:02:00.0: reg 10 64bit mmio: [0xfeafc000-0xfeafffff]
[    0.688147] pci 0000:02:00.0: reg 18 io port: [0xd800-0xd8ff]
[    0.688170] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfeac0000-0xfeadffff]
[    0.688205] pci 0000:02:00.0: supports D1 D2
[    0.688207] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.688211] pci 0000:02:00.0: PME# disabled
[    0.688248] pci 0000:00:1c.5: bridge io port: [0xd000-0xdfff]
[    0.688251] pci 0000:00:1c.5: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.688297] pci 0000:00:1e.0: transparent bridge
[    0.688321] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.688427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.688472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.688541] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.688589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.688629] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.701796] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.701884] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.701970] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.702056] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.702142] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.702228] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.702314] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.702400] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.702496] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.702499] vgaarb: loaded
[    0.702583] SCSI subsystem initialized
[    0.702612] libata version 3.00 loaded.
[    0.702612] usbcore: registered new interface driver usbfs
[    0.702612] usbcore: registered new interface driver hub
[    0.702612] usbcore: registered new device driver usb
[    0.702612] ACPI: WMI: Mapper loaded
[    0.702612] PCI: Using ACPI for IRQ routing
[    0.702612] NetLabel: Initializing
[    0.702612] NetLabel:  domain hash size = 128
[    0.702612] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.702612] NetLabel:  unlabeled traffic allowed by default
[    0.702612] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.702612] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.720181] Switching to clocksource tsc
[    0.721583] AppArmor: AppArmor Filesystem Enabled
[    0.721600] pnp: PnP ACPI init
[    0.721617] ACPI: bus type pnp registered
[    0.723840] pnp: PnP ACPI: found 13 devices
[    0.723842] ACPI: ACPI bus type pnp unregistered
[    0.723852] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.723859] system 00:06: ioport range 0x290-0x297 has been reserved
[    0.723863] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.723865] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.723868] system 00:07: ioport range 0x480-0x4bf has been reserved
[    0.723870] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.723872] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.723875] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.723877] system 00:07: iomem range 0xffa00000-0xffafffff has been reserved
[    0.723879] system 00:07: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.723881] system 00:07: iomem range 0xffe00000-0xffefffff has been reserved
[    0.723884] system 00:07: iomem range 0xfff00000-0xfffffffe has been reserved
[    0.723889] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.723891] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.723897] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.723902] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.723904] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    0.723906] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.723909] system 00:0c: iomem range 0x100000-0xcfffffff could not be reserved
[    0.728612] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.728615] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.728618] pci 0000:00:01.0:   MEM window: 0xfe900000-0xfe9fffff
[    0.728621] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.728624] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.728626] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.728630] pci 0000:00:1c.0:   MEM window: 0xf0000000-0xf03fffff
[    0.728633] pci 0000:00:1c.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.728638] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.728640] pci 0000:00:1c.4:   IO window: 0xe000-0xefff
[    0.728644] pci 0000:00:1c.4:   MEM window: 0xfeb00000-0xfebfffff
[    0.728648] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0400000-0x000000f05fffff
[    0.728652] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.728654] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
[    0.728658] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
[    0.728661] pci 0000:00:1c.5:   PREFETCH window: 0x000000f0600000-0x000000f07fffff
[    0.728666] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.728667] pci 0000:00:1e.0:   IO window: disabled
[    0.728671] pci 0000:00:1e.0:   MEM window: disabled
[    0.728674] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.728685]   alloc irq_desc for 16 on node -1
[    0.728687]   alloc kstat_irqs on node -1
[    0.728692] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.728695] pci 0000:00:01.0: setting latency timer to 64
[    0.728701] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.728704]   alloc irq_desc for 17 on node -1
[    0.728705]   alloc kstat_irqs on node -1
[    0.728707] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.728711] pci 0000:00:1c.0: setting latency timer to 64
[    0.728717] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.728720] pci 0000:00:1c.4: setting latency timer to 64
[    0.728726] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.728729] pci 0000:00:1c.5: setting latency timer to 64
[    0.728734] pci 0000:00:1e.0: setting latency timer to 64
[    0.728737] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.728739] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.728742] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.728743] pci_bus 0000:01: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.728745] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.728747] pci_bus 0000:04: resource 0 io:  [0x1000-0x1fff]
[    0.728749] pci_bus 0000:04: resource 1 mem: [0xf0000000-0xf03fffff]
[    0.728751] pci_bus 0000:04: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.728753] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.728754] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.728756] pci_bus 0000:03: resource 2 pref mem [0xf0400000-0xf05fffff]
[    0.728758] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.728760] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.728762] pci_bus 0000:02: resource 2 pref mem [0xf0600000-0xf07fffff]
[    0.728763] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.728765] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.728795] NET: Registered protocol family 2
[    0.728935] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.729892] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.732807] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.733178] TCP: Hash tables configured (established 524288 bind 65536)
[    0.733180] TCP reno registered
[    0.733273] NET: Registered protocol family 1
[    0.733421] pci 0000:01:00.0: Boot video device
[    0.733713] Scanning for low memory corruption every 60 seconds
[    0.733816] audit: initializing netlink socket (disabled)
[    0.733825] type=2000 audit(1275449606.729:1): initialized
[    0.741255] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.742425] VFS: Disk quotas dquot_6.5.2
[    0.742465] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.742934] fuse init (API version 7.13)
[    0.742996] msgmni has been set to 7906
[    0.743269] alg: No test for stdrng (krng)
[    0.743325] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.743327] io scheduler noop registered
[    0.743329] io scheduler anticipatory registered
[    0.743330] io scheduler deadline registered
[    0.743355] io scheduler cfq registered (default)
[    0.743458]   alloc irq_desc for 24 on node -1
[    0.743460]   alloc kstat_irqs on node -1
[    0.743467] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.743471] pcieport 0000:00:01.0: setting latency timer to 64
[    0.743547]   alloc irq_desc for 25 on node -1
[    0.743549]   alloc kstat_irqs on node -1
[    0.743554] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.743560] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.743646]   alloc irq_desc for 26 on node -1
[    0.743648]   alloc kstat_irqs on node -1
[    0.743653] pcieport 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.743659] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.743747]   alloc irq_desc for 27 on node -1
[    0.743748]   alloc kstat_irqs on node -1
[    0.743754] pcieport 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.743760] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.743822] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.743900] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.743981] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.743984] ACPI: Power Button [PWRB]
[    0.744018] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.744020] ACPI: Power Button [PWRF]
[    0.744497] ACPI: SSDT 00000000cff7e0d0 001D2 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    0.744887] processor LNXCPU:00: registered as cooling_device0
[    0.745106] ACPI: SSDT 00000000cff7e2b0 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    0.745471] processor LNXCPU:01: registered as cooling_device1
[    0.745691] ACPI: SSDT 00000000cff7e400 00143 (v01    AMI   CPU3PM 00000001 INTL 20060113)
[    0.746052] processor LNXCPU:02: registered as cooling_device2
[    0.746274] ACPI: SSDT 00000000cff7e550 00143 (v01    AMI   CPU4PM 00000001 INTL 20060113)
[    0.746631] processor LNXCPU:03: registered as cooling_device3
[    0.749715] Linux agpgart interface v0.103
[    0.749742] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.749828] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.750089] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.750864] brd: module loaded
[    0.751217] loop: module loaded
[    0.751282] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.751397] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.751421] pata_acpi 0000:03:00.0: setting latency timer to 64
[    0.751432] pata_acpi 0000:03:00.0: PCI INT A disabled
[    0.751641] Fixed MDIO Bus: probed
[    0.751665] PPP generic driver version 2.4.2
[    0.751689] tun: Universal TUN/TAP device driver, 1.6
[    0.751690] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.751749] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.751764]   alloc irq_desc for 18 on node -1
[    0.751765]   alloc kstat_irqs on node -1
[    0.751771] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.751799] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.751802] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.751834] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.751859] ehci_hcd 0000:00:1a.7: debug port 1
[    0.755739] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.755754] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe8ffc00
[    0.779585] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.779692] usb usb1: configuration #1 chosen from 1 choice
[    0.779716] hub 1-0:1.0: USB hub found
[    0.779724] hub 1-0:1.0: 6 ports detected
[    0.779778]   alloc irq_desc for 23 on node -1
[    0.779780]   alloc kstat_irqs on node -1
[    0.779785] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.779804] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.779807] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.779834] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.779855] ehci_hcd 0000:00:1d.7: debug port 1
[    0.783753] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.783767] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe8ff800
[    0.799576] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.799664] usb usb2: configuration #1 chosen from 1 choice
[    0.799688] hub 2-0:1.0: USB hub found
[    0.799695] hub 2-0:1.0: 6 ports detected
[    0.799746] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.799759] uhci_hcd: USB Universal Host Controller Interface driver
[    0.799791] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.799798] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.799800] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.799829] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.799861] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[    0.799922] usb usb3: configuration #1 chosen from 1 choice
[    0.799943] hub 3-0:1.0: USB hub found
[    0.799948] hub 3-0:1.0: 2 ports detected
[    0.799981]   alloc irq_desc for 21 on node -1
[    0.799983]   alloc kstat_irqs on node -1
[    0.799988] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.799992] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.799994] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.800017] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.800044] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    0.800108] usb usb4: configuration #1 chosen from 1 choice
[    0.800127] hub 4-0:1.0: USB hub found
[    0.800132] hub 4-0:1.0: 2 ports detected
[    0.800163] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.800167] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.800170] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.800193] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.800213] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[    0.800278] usb usb5: configuration #1 chosen from 1 choice
[    0.800295] hub 5-0:1.0: USB hub found
[    0.800300] hub 5-0:1.0: 2 ports detected
[    0.800335] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.800339] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.800342] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.800364] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.800383] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[    0.800444] usb usb6: configuration #1 chosen from 1 choice
[    0.800463] hub 6-0:1.0: USB hub found
[    0.800467] hub 6-0:1.0: 2 ports detected
[    0.800501]   alloc irq_desc for 19 on node -1
[    0.800503]   alloc kstat_irqs on node -1
[    0.800506] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.800510] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.800513] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.800535] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.800559] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    0.800631] usb usb7: configuration #1 chosen from 1 choice
[    0.800650] hub 7-0:1.0: USB hub found
[    0.800655] hub 7-0:1.0: 2 ports detected
[    0.800687] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.800692] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.800694] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.800716] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.800737] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[    0.800799] usb usb8: configuration #1 chosen from 1 choice
[    0.800816] hub 8-0:1.0: USB hub found
[    0.800822] hub 8-0:1.0: 2 ports detected
[    0.800893] PNP: No PS/2 controller found. Probing ports directly.
[    0.803571] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.803575] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.803653] mice: PS/2 mouse device common for all mice
[    0.803727] rtc_cmos 00:03: RTC can wake from S4
[    0.803758] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.803779] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.803876] device-mapper: uevent: version 1.0.3
[    0.803958] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.804099] device-mapper: multipath: version 1.1.0 loaded
[    0.804101] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.804333] cpuidle: using governor ladder
[    0.804335] cpuidle: using governor menu
[    0.804582] TCP cubic registered
[    0.804674] NET: Registered protocol family 10
[    0.805002] lo: Disabled Privacy Extensions
[    0.805207] NET: Registered protocol family 17
[    0.805988] PM: Resume from disk failed.
[    0.805996] registered taskstats version 1
[    0.806324]   Magic number: 14:492:562
[    0.806388] rtc_cmos 00:03: setting system clock to 2010-06-02 03:33:27 UTC (1275449607)
[    0.806391] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.806392] EDD information not available.
[    0.815975] Freeing initrd memory: 8637k freed
[    0.818289] Freeing unused kernel memory: 876k freed
[    0.818463] Write protecting the kernel read-only data: 7680k
[    0.831075] udev: starting version 151
[    0.851792] ahci 0000:00:1f.2: version 3.0
[    0.851809]   alloc irq_desc for 22 on node -1
[    0.851811]   alloc kstat_irqs on node -1
[    0.851817] ahci 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.851863]   alloc irq_desc for 28 on node -1
[    0.851864]   alloc kstat_irqs on node -1
[    0.851871] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.851927] ahci: SSS flag set, parallel bus scan disabled
[    0.851962] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.851965] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
[    0.851969] ahci 0000:00:1f.2: setting latency timer to 64
[    0.855704] xor: automatically using best checksumming function: generic_sse
[    0.862267] sky2 driver version 1.25
[    0.862300] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.862312] sky2 0000:02:00.0: setting latency timer to 64
[    0.862341] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 3
[    0.862418]   alloc irq_desc for 29 on node -1
[    0.862419]   alloc kstat_irqs on node -1
[    0.862431] sky2 0000:02:00.0: irq 29 for MSI/MSI-X
[    0.863423] sky2 eth0: addr 90:e6:ba:53:35:57
[    0.898837]    generic_sse: 10158.400 MB/sec
[    0.898839] xor: using function: generic_sse (10158.400 MB/sec)
[    0.900601] device-mapper: dm-raid45: initialized v0.2594b
[    0.902398] md: linear personality registered for level -1
[    0.904270] md: multipath personality registered for level -4
[    0.905947] md: raid0 personality registered for level 0
[    0.908364] md: raid1 personality registered for level 1
[    0.910112] async_tx: api initialized (async)
[    0.988702] scsi0 : ahci
[    0.988798] scsi1 : ahci
[    0.988859] scsi2 : ahci
[    0.988919] scsi3 : ahci
[    0.988979] scsi4 : ahci
[    0.989026] scsi5 : ahci
[    0.989154] ata1: SATA max UDMA/133 abar m2048@0xfe8fe800 port 0xfe8fe900 irq 28
[    0.989156] ata2: SATA max UDMA/133 abar m2048@0xfe8fe800 port 0xfe8fe980 irq 28
[    0.989159] ata3: SATA max UDMA/133 abar m2048@0xfe8fe800 port 0xfe8fea00 irq 28
[    0.989161] ata4: SATA max UDMA/133 abar m2048@0xfe8fe800 port 0xfe8fea80 irq 28
[    0.989163] ata5: SATA max UDMA/133 abar m2048@0xfe8fe800 port 0xfe8feb00 irq 28
[    0.989165] ata6: SATA max UDMA/133 abar m2048@0xfe8fe800 port 0xfe8feb80 irq 28
[    0.989197] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.989241] ahci 0000:03:00.0: controller can't do NCQ, turning off CAP_NCQ
[    0.989242] ahci 0000:03:00.0: controller can't do PMP, turning off CAP_PMP
[    0.989244] ahci 0000:03:00.0: MV_AHCI HACK: port_map 7 -> 3
[    0.989246] ahci 0000:03:00.0: Disabling your PATA port. Use the boot option 'ahci.marvell_enable=0' to avoid this.
[    0.989260] ahci: SSS flag set, parallel bus scan disabled
[    0.989289] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 3 ports 3 Gbps 0x3 impl IDE mode
[    0.989292] ahci 0000:03:00.0: flags: 64bit stag led slum part 
[    0.989298] ahci 0000:03:00.0: setting latency timer to 64
[    0.989397] scsi6 : ahci
[    0.989465] scsi7 : ahci
[    0.989513] scsi8 : ahci
[    0.989555] ata7: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 16
[    0.989558] ata8: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 16
[    0.989559] ata9: DUMMY
[    1.083775] raid6: int64x1   2160 MB/s
[    1.253765] raid6: int64x2   2788 MB/s
[    1.350029] ata7: SATA link down (SStatus 0 SControl 300)
[    1.423769] raid6: int64x4   2044 MB/s
[    1.530010] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.536437] ata1.00: ATA-7: SAMSUNG HD103UJ, 1AA01118, max UDMA7
[    1.536439] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.542919] ata1.00: configured for UDMA/133
[    1.560085] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    1.560259] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.560370] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.560406] sd 0:0:0:0: [sda] Write Protect is off
[    1.560408] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.560426] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.560526]  sda: sda1 sda2 < sda5 >
[    1.587011] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.593766] raid6: int64x8   1820 MB/s
[    1.763761] raid6: sse2x1    4830 MB/s
[    1.910013] ata2: SATA link down (SStatus 0 SControl 300)
[    1.933754] raid6: sse2x2    5150 MB/s
[    2.103752] raid6: sse2x4    7863 MB/s
[    2.103753] raid6: using algorithm sse2x4 (7863 MB/s)
[    2.230012] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.270012] ata3: SATA link down (SStatus 0 SControl 300)
[    2.380501] usb 1-1: configuration #1 chosen from 1 choice
[    2.380600] hub 1-1:1.0: USB hub found
[    2.380666] hub 1-1:1.0: 4 ports detected
[    2.510010] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    2.632516] ata4: SATA link down (SStatus 0 SControl 300)
[    2.672956] usb 1-5: configuration #1 chosen from 1 choice
[    2.673062] hub 1-5:1.0: USB hub found
[    2.673147] hub 1-5:1.0: 4 ports detected
[    2.792510] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    2.949183] usb 1-6: configuration #1 chosen from 1 choice
[    2.957359] Initializing USB Mass Storage driver...
[    2.957534] scsi9 : SCSI emulation for USB Mass Storage devices
[    2.957627] usb-storage: device found at 4
[    2.957629] usb-storage: waiting for device to settle before scanning
[    2.957640] usbcore: registered new interface driver usb-storage
[    2.957642] USB Mass Storage support registered.
[    3.032615] usb 1-5.2: new high speed USB device using ehci_hcd and address 5
[    3.141433] usb 1-5.2: configuration #1 chosen from 1 choice
[    3.141601] scsi10 : SCSI emulation for USB Mass Storage devices
[    3.141739] usb-storage: device found at 5
[    3.141741] usb-storage: waiting for device to settle before scanning
[    3.222605] usb 1-5.3: new full speed USB device using ehci_hcd and address 6
[    3.353034] usb 1-5.3: configuration #1 chosen from 1 choice
[    3.353245] hub 1-5.3:1.0: USB hub found
[    3.353342] hub 1-5.3:1.0: 4 ports detected
[    3.582514] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.588391] ata5.00: ATA-8: SAMSUNG HD203WI, 1AN10002, max UDMA/133
[    3.588395] ata5.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.594321] ata5.00: configured for UDMA/133
[    3.610099] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD203WI  1AN1 PQ: 0 ANSI: 5
[    3.610252] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    3.610257] sd 4:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.610314] sd 4:0:0:0: [sdb] Write Protect is off
[    3.610317] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.610337] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.610447]  sdb: sdb1
[    3.622567] sd 4:0:0:0: [sdb] Attached SCSI disk
[    3.642711] usb 1-5.3.1: new low speed USB device using ehci_hcd and address 7
[    3.788239] usb 1-5.3.1: configuration #1 chosen from 1 choice
[    3.796523] usbcore: registered new interface driver hiddev
[    3.812825] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.3/1-5.3.1/1-5.3.1:1.0/input/input3
[    3.812900] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1a.7-5.3.1/input0
[    3.850733] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.3/1-5.3.1/1-5.3.1:1.1/input/input4
[    3.850842] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Device [DELL DELL USB Keyboard] on usb-0000:00:1a.7-5.3.1/input1
[    3.863919] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.3/1-5.3.1/1-5.3.1:1.2/input/input5
[    3.863994] generic-usb 0003:413C:2003.0003: input,hidraw2: USB HID v1.10 Mouse [DELL DELL USB Keyboard] on usb-0000:00:1a.7-5.3.1/input2
[    3.864015] usbcore: registered new interface driver usbhid
[    3.864017] usbhid: v2.6:USB HID core driver
[    4.560010] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.565963] ata6.00: ATA-8: SAMSUNG HD203WI, 1AN10002, max UDMA/133
[    4.565966] ata6.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    4.571963] ata6.00: configured for UDMA/133
[    4.590098] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD203WI  1AN1 PQ: 0 ANSI: 5
[    4.590248] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    4.590253] sd 5:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    4.590296] sd 5:0:0:0: [sdc] Write Protect is off
[    4.590298] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.590320] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.590437]  sdc: sdc1
[    4.602452] sd 5:0:0:0: [sdc] Attached SCSI disk
[    4.940020] ata8: SATA link down (SStatus 0 SControl 300)
[    4.944883] md: raid6 personality registered for level 6
[    4.944885] md: raid5 personality registered for level 5
[    4.944887] md: raid4 personality registered for level 4
[    4.950831] md: raid10 personality registered for level 10
[    5.045764] md: bind<sdb1>
[    5.187665] md: bind<sdc1>
[    5.189012] raid1: raid set md0 active with 2 out of 2 mirrors
[    5.189029] md0: detected capacity change from 0 to 2000396222464
[    5.189832]  md0: unknown partition table
[    5.326868] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    7.951282] usb-storage: device scan complete
[    7.952733] scsi 9:0:0:0: Direct-Access     Seagate  FreeAgent XTreme 4113 PQ: 0 ANSI: 4
[    7.953206] sd 9:0:0:0: Attached scsi generic sg3 type 0
[    7.954834] sd 9:0:0:0: [sdd] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    7.955835] sd 9:0:0:0: [sdd] Write Protect is off
[    7.955838] sd 9:0:0:0: [sdd] Mode Sense: 1c 00 00 00
[    7.955841] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[    7.958584] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[    7.958587]  sdd: sdd1
[    7.974078] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[    7.974081] sd 9:0:0:0: [sdd] Attached SCSI disk
[    8.151479] usb-storage: device scan complete
[    8.152071] scsi 10:0:0:0: CD-ROM            SONY     DVD RW DRU-830A  SS25 PQ: 0 ANSI: 0
[    8.160688] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.160691] Uniform CD-ROM driver Revision: 3.20
[    8.160786] sr 10:0:0:0: Attached scsi CD-ROM sr0
[    8.160829] sr 10:0:0:0: Attached scsi generic sg4 type 5
[   19.502482] udev: starting version 151
[   19.511290] lp: driver loaded but no devices found
[   19.522072] ehci_hcd 0000:00:1d.7: remove, state 4
[   19.522080] usb usb2: USB disconnect, address 1
[   19.523270] vga16fb: initializing
[   19.523273] vga16fb: mapped to 0xffff8800000a0000
[   19.523320] fb0: VGA16 VGA frame buffer device
[   19.529408] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   19.529412] Disabling lock debugging due to kernel taint
[   19.553792] ehci_hcd 0000:00:1d.7: USB bus 2 deregistered
[   19.553880] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[   19.569423] ehci_hcd 0000:00:1a.7: remove, state 1
[   19.569434] usb usb1: USB disconnect, address 1
[   19.569435] usb 1-1: USB disconnect, address 2
[   19.569640] usb 1-5: USB disconnect, address 3
[   19.569642] usb 1-5.2: USB disconnect, address 5
[   19.584272] usb 1-5.3: USB disconnect, address 6
[   19.584275] usb 1-5.3.1: USB disconnect, address 7
[   19.608395] Adding 11888060k swap on /dev/sda5.  Priority:-1 extents:1 across:11888060k 
[   19.624992] type=1505 audit(1275449626.316:2):  operation="profile_load" pid=712 name="/sbin/dhclient3"
[   19.625495] type=1505 audit(1275449626.316:3):  operation="profile_load" pid=712 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.625778] type=1505 audit(1275449626.316:4):  operation="profile_load" pid=712 name="/usr/lib/connman/scripts/dhclient-script"
[   19.632610] [fglrx] Maximum main memory to use for locked dma buffers: 3800 MBytes.
[   19.632757] [fglrx]   vendor: 1002 device: 9498 count: 1
[   19.633060] [fglrx] ioport: bar 4, base 0xc000, size: 0x100
[   19.633072] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.633077] pci 0000:01:00.0: setting latency timer to 64
[   19.633263] [fglrx] Kernel PAT support is enabled
[   19.633283] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[   19.637667] EDAC MC: Ver: 2.1.0 Apr 28 2010
[   19.757734] Console: switching to colour frame buffer device 80x30
[   19.834898] usb 1-6: USB disconnect, address 4
[   19.868342] ehci_hcd 0000:00:1a.7: USB bus 1 deregistered
[   19.868398] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[   19.868523] EDAC MC0: Giving out device to 'x38_edac' 'x38': DEV 0000:00:00.0
[   19.868644] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.868673] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.988977] hda_codec: ALC1200: BIOS auto-probing.
[   19.990308] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   19.998392] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   19.998445] HDA Intel 0000:01:00.1: setting latency timer to 64
[   20.080150] EXT4-fs (md0): mounted filesystem with ordered data mode
[   20.124868] type=1505 audit(1275449626.816:5):  operation="profile_load" pid=1070 name="/usr/share/gdm/guest-session/Xsession"
[   20.126151] type=1505 audit(1275449626.816:6):  operation="profile_replace" pid=1071 name="/sbin/dhclient3"
[   20.126659] type=1505 audit(1275449626.816:7):  operation="profile_replace" pid=1071 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.126943] type=1505 audit(1275449626.816:8):  operation="profile_replace" pid=1071 name="/usr/lib/connman/scripts/dhclient-script"
[   20.131299] type=1505 audit(1275449626.816:9):  operation="profile_load" pid=1072 name="/usr/bin/evince"
[   20.138000] type=1505 audit(1275449626.826:10):  operation="profile_load" pid=1072 name="/usr/bin/evince-previewer"
[   20.142990] type=1505 audit(1275449626.836:11):  operation="profile_load" pid=1072 name="/usr/bin/evince-thumbnailer"
[   20.150053] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   20.164927] sky2 eth0: enabling interface
[   20.165258] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.314596] usb 5-1: configuration #1 chosen from 1 choice
[   20.317563] hub 5-1:1.0: USB hub found
[   20.319513] hub 5-1:1.0: 4 ports detected
[   20.442537] usb 5-2: new full speed USB device using uhci_hcd and address 3
[   20.629574] usb 5-2: configuration #1 chosen from 1 choice
[   20.640594] scsi11 : SCSI emulation for USB Mass Storage devices
[   20.640724] usb-storage: device found at 3
[   20.640725] usb-storage: waiting for device to settle before scanning
[   20.758451]   alloc irq_desc for 30 on node -1
[   20.758454]   alloc kstat_irqs on node -1
[   20.758462] fglrx_pci 0000:01:00.0: irq 30 for MSI/MSI-X
[   20.758952] [fglrx] Firegl kernel thread PID: 1345
[   20.759110] [fglrx] IRQ 30 Enabled
[   20.760016] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   20.918866] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.918869] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   20.918870] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   20.918871] vboxdrv: the usage of hardware performance counters by
[   20.918872] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   20.918875] vboxdrv: Found 4 processor cores.
[   20.918935] VBoxDrv: dbg - g_abExecMemory=ffffffffa048ec60
[   20.918979] vboxdrv: fAsync=0 offMin=0x428 offMax=0x1c60
[   20.919168] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.919170] vboxdrv: Successfully loaded version 3.2.0 (interface 0x00140001).
[   20.925532] usb 3-1: configuration #1 chosen from 1 choice
[   20.928501] hub 3-1:1.0: USB hub found
[   20.930468] hub 3-1:1.0: 4 ports detected
[   21.021454] usb 5-1.2: new full speed USB device using uhci_hcd and address 4
[   21.182522] usb 5-1.2: configuration #1 chosen from 1 choice
[   21.185184] ppdev: user-space parallel port driver
[   21.185547] scsi12 : SCSI emulation for USB Mass Storage devices
[   21.185611] usb-storage: device found at 4
[   21.185613] usb-storage: waiting for device to settle before scanning
[   21.271431] usb 5-1.3: new full speed USB device using uhci_hcd and address 5
[   21.328574] [fglrx] Gart USWC size:1237 M.
[   21.328577] [fglrx] Gart cacheable size:491 M.
[   21.328582] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   21.328584] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   21.328586] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   21.401505] usb 5-1.3: configuration #1 chosen from 1 choice
[   21.404465] hub 5-1.3:1.0: USB hub found
[   21.406423] hub 5-1.3:1.0: 4 ports detected
[   21.510800] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.683799] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   21.683996] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   21.683998] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   21.683999] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   21.691403] usb 5-1.3.1: new low speed USB device using uhci_hcd and address 6
[   21.848078] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   21.848408] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.879463] usb 5-1.3.1: configuration #1 chosen from 1 choice
[   21.905625] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1.3/5-1.3.1/5-1.3.1:1.0/input/input7
[   21.905698] generic-usb 0003:413C:2003.0004: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1a.2-1.3.1/input0
[   21.957435] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1.3/5-1.3.1/5-1.3.1:1.1/input/input8
[   21.957506] generic-usb 0003:413C:2003.0005: input,hidraw1: USB HID v1.10 Device [DELL DELL USB Keyboard] on usb-0000:00:1a.2-1.3.1/input1
[   21.976590] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1.3/5-1.3.1/5-1.3.1:1.2/input/input9
[   21.976679] generic-usb 0003:413C:2003.0006: input,hidraw2: USB HID v1.10 Mouse [DELL DELL USB Keyboard] on usb-0000:00:1a.2-1.3.1/input2
[   25.640077] usb-storage: device scan complete
[   25.643041] scsi 11:0:0:0: Direct-Access     Seagate  FreeAgent XTreme 4113 PQ: 0 ANSI: 4
[   25.643423] sd 11:0:0:0: Attached scsi generic sg3 type 0
[   25.648032] sd 11:0:0:0: [sdd] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[   25.651027] sd 11:0:0:0: [sdd] Write Protect is off
[   25.651029] sd 11:0:0:0: [sdd] Mode Sense: 1c 00 00 00
[   25.651032] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[   25.659023] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[   25.659031]  sdd: sdd1
[   25.679000] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[   25.679004] sd 11:0:0:0: [sdd] Attached SCSI disk
[   26.184732] usb-storage: device scan complete
[   26.187728] scsi 12:0:0:0: CD-ROM            SONY     DVD RW DRU-830A  SS25 PQ: 0 ANSI: 0
[   26.210694] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   26.210813] sr 12:0:0:0: Attached scsi CD-ROM sr0
[   26.211126] sr 12:0:0:0: Attached scsi generic sg4 type 5
[   32.472491] eth0: no IPv6 routers present

```

---

### Post by jacrider on 2010-06-02
I have the same symptoms, but I have a different IDE controller:


00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)

I can't believe this isn't resolved yet.  I have gone back to 9.10, but check in once a week or so to see if others are still having the issue.

---

