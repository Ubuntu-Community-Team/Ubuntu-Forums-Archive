---
title: "no Internet after install from Live CD"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pbpersson on 2009-04-02
I was almost certain I saw someone post this very thing but now I cannot find it.

Jaunty worked fine from the Live CD but when I installed it on my system - no Internet.  It says "you are not connected to the wired network" or something like that.

I went to the CL and did "sudo dhclient eth0" and the gateway kept offering Jaunty different IP addresses but when Jaunty would say "fine, give me that address" then it would get a NAK from the DHCP machine and they would start the process all over.

Each time Jaunty was offered a new IP, it would sent a request for that IP and then get a NAK in return.

What is the next step?  I do not know how to see if this is a known bug.  Every page I search on the web says to report a bug click somewhere but I cannot send a bug report if I cannot connect.

This is a 64-bit installation by the way

---

### Post by pbpersson on 2009-04-02
output from ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:13:d4:8d:cd:be  
          inet6 addr: fe80::213:d4ff:fe8d:cdbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76605 (76.6 KB)  TX bytes:25092 (25.0 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```

output from dhclient:
```
Listening on LPF/eth0/00:13:d4:8d:cd:be
Sending on   LPF/eth0/00:13:d4:8d:cd:be
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.253 from 192.168.0.1
DHCPREQUEST of 192.168.0.253 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPREQUEST of 192.168.0.253 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.0.185 from 192.168.0.1
DHCPREQUEST of 192.168.0.185 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPREQUEST of 192.168.0.185 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.253 from 192.168.0.1
DHCPREQUEST of 192.168.0.253 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
```

output from dmesg:
```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009f400
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #37-Ubuntu SMP Mon Mar 23 16:40:00 UTC 2009 (Ubuntu 2.6.28-11.37-generic)
[    0.000000] Command line: root=UUID=797c3825-3eb3-4dd3-9c70-20dcac7a949c ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  modified: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  modified: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000007ffb0000
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007ffb0000 page 4k
[    0.000000] kernel direct mapping tables up to 7ffb0000 @ 10000-14000
[    0.000000] last_map_addr: 7ffb0000 end: 7ffb0000
[    0.000000] RAMDISK: 3785a000 - 37fef6e5
[    0.000000] ACPI: RSDP 000FAB00, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFB0000, 0030 (r1 A M I  OEMRSDT   4000620 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0200, 0081 (r1 A M I  OEMFACP   4000620 MSFT       97)
[    0.000000] ACPI: DSDT 7FFB03E0, 3641 (r1  A0232 A0232008        8 MSFT  100000D)
[    0.000000] ACPI: FACS 7FFC0000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 004A (r1 A M I  OEMAPIC   4000620 MSFT       97)
[    0.000000] ACPI: OEMB 7FFC0040, 003F (r1 A M I  OEMBIOS   4000620 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007ffb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003785a000 - 0037fef6e5]          RAMDISK ==> [003785a000 - 0037fef6e5]
[    0.000000]   #4 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524095
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2540 pages reserved
[    0.000000]   DMA zone: 1387 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7111 pages used for memmap
[    0.000000]   DMA32 zone: 513001 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7f780000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 514388
[    0.000000] Kernel command line: root=UUID=797c3825-3eb3-4dd3-9c70-20dcac7a949c ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1400.046 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 20971520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] AGP bridge at 00:00:00
[    0.004000] Aperture from AGP @ e4000000 old size 32 MB
[    0.004000] Aperture from AGP @ e4000000 size 64 MB (APSIZE f30)
[    0.004000] Node 0: aperture @ e4000000 size 64 MB
[    0.004000] Memory: 2025736k/2096832k available (4764k kernel code, 452k absent, 69956k reserved, 2541k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004020] Calibrating delay loop (skipped), value calculated using timer frequency.. 2800.09 BogoMIPS (lpj=5600184)
[    0.004055] Security Framework initialized
[    0.004069] SELinux:  Disabled at boot.
[    0.004095] AppArmor: AppArmor initialized
[    0.004109] Mount-cache hash table entries: 256
[    0.004325] Initializing cgroup subsys ns
[    0.004330] Initializing cgroup subsys cpuacct
[    0.004333] Initializing cgroup subsys memory
[    0.004338] Initializing cgroup subsys freezer
[    0.004358] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004361] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004364] tseg: 0000000000
[    0.004406] SMP alternatives: switching to UP code
[    0.187293] Freeing SMP alternatives: 37k freed
[    0.188395] ACPI: Core revision 20080926
[    0.189922] ACPI: Checking initramfs for custom DSDT
[    0.597066] Setting APIC routing to flat
[    0.598123] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.637820] CPU0: AMD Sempron(tm) Processor 2500+ stepping 02
[    0.640002] Brought up 1 CPUs
[    0.640002] Total of 1 processors activated (2800.09 BogoMIPS).
[    0.640002] CPU0 attaching NULL sched-domain.
[    0.640002] net_namespace: 1400 bytes
[    0.640002] Booting paravirtualized kernel on bare hardware
[    0.640002] Time: 20:59:02  Date: 04/01/09
[    0.640002] regulator: core version 0.5
[    0.640002] NET: Registered protocol family 16
[    0.640002] node 0 link 0: io port [1000, ffffff]
[    0.640002] TOM: 0000000080000000 aka 2048M
[    0.640002] node 0 link 0: mmio [a0000, bffff]
[    0.640002] node 0 link 0: mmio [80000000, ffffffff]
[    0.640002] bus: [00,ff] on node 0 link 0
[    0.640002] bus: 00 index 0 io port: [0, ffff]
[    0.640002] bus: 00 index 1 mmio: [a0000, bffff]
[    0.640002] bus: 00 index 2 mmio: [80000000, fcffffffff]
[    0.640002] ACPI: bus type pci registered
[    0.640002] PCI: Using configuration type 1 for base access
[    0.640002] ACPI: EC: Look up EC in DSDT
[    0.646380] ACPI: Interpreter enabled
[    0.646386] ACPI: (supports S0 S1 S3 S4 S5)
[    0.646413] ACPI: Using IOAPIC for interrupt routing
[    0.654512] ACPI: No dock devices found.
[    0.654525] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.654596] pci 0000:00:00.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
[    0.654665] pci 0000:00:01.0: supports D1
[    0.654708] pci 0000:00:0f.0: reg 10 io port: [0xd800-0xd807]
[    0.654715] pci 0000:00:0f.0: reg 14 io port: [0xd400-0xd403]
[    0.654721] pci 0000:00:0f.0: reg 18 io port: [0xd000-0xd007]
[    0.654728] pci 0000:00:0f.0: reg 1c io port: [0xc800-0xc803]
[    0.654734] pci 0000:00:0f.0: reg 20 io port: [0xc400-0xc40f]
[    0.654741] pci 0000:00:0f.0: reg 24 io port: [0xc000-0xc0ff]
[    0.654796] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.654861] pci 0000:00:10.0: reg 20 io port: [0xa800-0xa81f]
[    0.654877] pci 0000:00:10.0: supports D1 D2
[    0.654880] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.654885] pci 0000:00:10.0: PME# disabled
[    0.654928] pci 0000:00:10.1: reg 20 io port: [0xb000-0xb01f]
[    0.654944] pci 0000:00:10.1: supports D1 D2
[    0.654946] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.654950] pci 0000:00:10.1: PME# disabled
[    0.654995] pci 0000:00:10.2: reg 20 io port: [0xb400-0xb41f]
[    0.655011] pci 0000:00:10.2: supports D1 D2
[    0.655013] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.655017] pci 0000:00:10.2: PME# disabled
[    0.655059] pci 0000:00:10.3: reg 20 io port: [0xb800-0xb81f]
[    0.655075] pci 0000:00:10.3: supports D1 D2
[    0.655078] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.655082] pci 0000:00:10.3: PME# disabled
[    0.655110] pci 0000:00:10.4: reg 10 32bit mmio: [0xfbb00000-0xfbb000ff]
[    0.655141] pci 0000:00:10.4: supports D1 D2
[    0.655143] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.655147] pci 0000:00:10.4: PME# disabled
[    0.655204] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.655210] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.655251] pci 0000:00:11.5: reg 10 io port: [0xa400-0xa4ff]
[    0.655283] pci 0000:00:11.5: supports D1 D2
[    0.655313] pci 0000:00:11.6: reg 10 io port: [0x00-0xff]
[    0.655372] pci 0000:00:12.0: reg 10 io port: [0xa000-0xa0ff]
[    0.655379] pci 0000:00:12.0: reg 14 32bit mmio: [0xfba00000-0xfba000ff]
[    0.655407] pci 0000:00:12.0: supports D1 D2
[    0.655409] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.655413] pci 0000:00:12.0: PME# disabled
[    0.655527] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.655532] pci 0000:01:00.0: reg 14 io port: [0xe000-0xe0ff]
[    0.655538] pci 0000:01:00.0: reg 18 32bit mmio: [0xfbe00000-0xfbe0ffff]
[    0.655550] pci 0000:01:00.0: reg 30 32bit mmio: [0xfbd00000-0xfbd1ffff]
[    0.655557] pci 0000:01:00.0: supports D1 D2
[    0.655578] pci 0000:01:00.1: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.655583] pci 0000:01:00.1: reg 14 32bit mmio: [0xfbf00000-0xfbf0ffff]
[    0.655601] pci 0000:01:00.1: supports D1 D2
[    0.655630] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.655635] pci 0000:00:01.0: bridge 32bit mmio: [0xfbd00000-0xfbffffff]
[    0.655639] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xfaffffff]
[    0.655647] bus 00 -> node 0
[    0.655655] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.663824] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.663968] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[    0.664115] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.664253] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.664391] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.664530] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.664668] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.664806] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.664935] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - A8, should be A3 [20080926]
[    0.664969] ACPI: WMI: Mapper loaded
[    0.665245] SCSI subsystem initialized
[    0.665294] libata version 3.00 loaded.
[    0.665357] usbcore: registered new interface driver usbfs
[    0.665378] usbcore: registered new interface driver hub
[    0.665420] usbcore: registered new device driver usb
[    0.665547] PCI: Using ACPI for IRQ routing
[    0.665562] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.680012] Bluetooth: Core ver 2.13
[    0.680073] NET: Registered protocol family 31
[    0.680075] Bluetooth: HCI device and connection manager initialized
[    0.680080] Bluetooth: HCI socket layer initialized
[    0.680083] NET: Registered protocol family 8
[    0.680085] NET: Registered protocol family 20
[    0.680097] NetLabel: Initializing
[    0.680099] NetLabel:  domain hash size = 128
[    0.680101] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.680119] NetLabel:  unlabeled traffic allowed by default
[    0.680174] agpgart-amd64 0000:00:00.0: AGP bridge [1106/3188]
[    0.682815] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xe4000000
[    0.682940] AppArmor: AppArmor Filesystem Enabled
[    0.692019] pnp: PnP ACPI init
[    0.692031] ACPI: bus type pnp registered
[    0.694361] pnp 00:09: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694366] pnp 00:09: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694370] pnp 00:09: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694374] pnp 00:09: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694377] pnp 00:09: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694381] pnp 00:09: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694384] pnp 00:09: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694388] pnp 00:09: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694392] pnp 00:09: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694395] pnp 00:09: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694399] pnp 00:09: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694402] pnp 00:09: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.694406] pnp 00:09: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.695652] pnp 00:0c: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.695656] pnp 00:0c: mem resource (0xc0000-0xdffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.695660] pnp 00:0c: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.695664] pnp 00:0c: mem resource (0x100000-0x7ffeffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.696118] pnp: PnP ACPI: found 13 devices
[    0.696120] ACPI: ACPI bus type pnp unregistered
[    0.696137] system 00:08: ioport range 0x290-0x297 has been reserved
[    0.696144] system 00:09: ioport range 0x3e1-0x3e7 has been reserved
[    0.696147] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.696151] system 00:09: ioport range 0x800-0x87f has been reserved
[    0.696154] system 00:09: ioport range 0x400-0x41f has been reserved
[    0.696161] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.696164] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.696168] system 00:0a: iomem range 0xfff80000-0xffffffff has been reserved
[    0.700915] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.700919] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.700924] pci 0000:00:01.0:   MEM window: 0xfbd00000-0xfbffffff
[    0.700929] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000faffffff
[    0.700945] pci 0000:00:01.0: setting latency timer to 64
[    0.700949] bus: 00 index 0 io port: [0x00-0xffff]
[    0.700952] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.700955] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.700958] bus: 01 index 1 mmio: [0xfbd00000-0xfbffffff]
[    0.700960] bus: 01 index 2 mmio: [0xe8000000-0xfaffffff]
[    0.700963] bus: 01 index 3 mmio: [0x0-0x0]
[    0.700982] NET: Registered protocol family 2
[    0.736071] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.737019] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.742878] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.744261] TCP: Hash tables configured (established 262144 bind 65536)
[    0.744265] TCP reno registered
[    0.756137] NET: Registered protocol family 1
[    0.756320] checking if image is initramfs... it is
[    1.204039] Switched to high resolution mode on CPU 0
[    1.591481] Freeing initrd memory: 7765k freed
[    1.601641] audit: initializing netlink socket (disabled)
[    1.601663] type=2000 audit(1238619542.600:1): initialized
[    1.613147] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.614788] VFS: Disk quotas dquot_6.5.1
[    1.614888] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.615685] fuse init (API version 7.10)
[    1.615790] msgmni has been set to 3973
[    1.616062] alg: No test for stdrng (krng)
[    1.616078] io scheduler noop registered
[    1.616080] io scheduler anticipatory registered
[    1.616082] io scheduler deadline registered
[    1.616149] io scheduler cfq registered (default)
[    1.616162] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.616264] pci 0000:01:00.0: Boot video device
[    1.619747] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.619757] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.619913] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.619917] ACPI: Power Button (FF) [PWRF]
[    1.619975] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.619984] ACPI: Power Button (CM) [PWRB]
[    1.620071] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.620077] ACPI: Sleep Button (CM) [SLPB]
[    1.620303] processor ACPI_CPU:00: registered as cooling_device0
[    1.652262] Linux agpgart interface v0.103
[    1.652280] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.652377] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.652746] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.653686] brd: module loaded
[    1.654104] loop: module loaded
[    1.654239] Fixed MDIO Bus: probed
[    1.654248] PPP generic driver version 2.4.2
[    1.654351] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.654404] Driver 'sd' needs updating - please use bus_type methods
[    1.654416] Driver 'sr' needs updating - please use bus_type methods
[    1.654604] sata_via 0000:00:0f.0: version 2.4
[    1.654631] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.654697] sata_via 0000:00:0f.0: routed to hard irq line 10
[    1.654862] scsi0 : sata_via
[    1.654999] scsi1 : sata_via
[    1.655047] ata1: SATA max UDMA/133 cmd 0xd800 ctl 0xd400 bmdma 0xc400 irq 20
[    1.655050] ata2: SATA max UDMA/133 cmd 0xd000 ctl 0xc800 bmdma 0xc408 irq 20
[    1.856011] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.021043] ata1.00: ATA-7: WDC WD4000YR-01PLB0, 01.06A01, max UDMA/133
[    2.021046] ata1.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.037033] ata1.00: configured for UDMA/133
[    2.240008] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.250615] isa bounce pool size: 16 pages
[    2.250714] scsi 0:0:0:0: Direct-Access     ATA      WDC WD4000YR-01P 01.0 PQ: 0 ANSI: 5
[    2.250845] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors: (400 GB/372 GiB)
[    2.250866] sd 0:0:0:0: [sda] Write Protect is off
[    2.250869] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.250898] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.250987] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors: (400 GB/372 GiB)
[    2.251004] sd 0:0:0:0: [sda] Write Protect is off
[    2.251007] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.251034] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.251039]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 >
[    2.333653] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.333730] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.334209] pata_via 0000:00:0f.1: version 0.3.3
[    2.334230] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.334485] scsi2 : pata_via
[    2.334569] scsi3 : pata_via
[    2.336588] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.336592] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.664359] ata4.00: ATAPI: Memorex DVD+/-RW True8XI, UWS4, max UDMA/33
[    2.680246] ata4.00: configured for UDMA/33
[    2.681506] scsi 3:0:0:0: CD-ROM            Memorex  DVD+/-RW True8XI UWS4 PQ: 0 ANSI: 5
[    2.685244] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.685248] Uniform CD-ROM driver Revision: 3.20
[    2.685422] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.685488] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.685666] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.685703] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.685747] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    2.685820] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    2.685899] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfbb00000
[    2.696012] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    2.696095] usb usb1: configuration #1 chosen from 1 choice
[    2.696127] hub 1-0:1.0: USB hub found
[    2.696138] hub 1-0:1.0: 8 ports detected
[    2.696273] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.696297] uhci_hcd: USB Universal Host Controller Interface driver
[    2.696357] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.696367] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.696427] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.696452] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000a800
[    2.696554] usb usb2: configuration #1 chosen from 1 choice
[    2.696582] hub 2-0:1.0: USB hub found
[    2.696593] hub 2-0:1.0: 2 ports detected
[    2.696689] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.696695] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.696752] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.696774] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b000
[    2.696867] usb usb3: configuration #1 chosen from 1 choice
[    2.696899] hub 3-0:1.0: USB hub found
[    2.696907] hub 3-0:1.0: 2 ports detected
[    2.696998] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.697004] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.697057] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.697077] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b400
[    2.697176] usb usb4: configuration #1 chosen from 1 choice
[    2.697203] hub 4-0:1.0: USB hub found
[    2.697211] hub 4-0:1.0: 2 ports detected
[    2.697304] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.697310] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    2.697371] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    2.697392] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000b800
[    2.697507] usb usb5: configuration #1 chosen from 1 choice
[    2.697535] hub 5-0:1.0: USB hub found
[    2.697545] hub 5-0:1.0: 2 ports detected
[    2.697701] usbcore: registered new interface driver libusual
[    2.697756] usbcore: registered new interface driver usbserial
[    2.697770] USB Serial support registered for generic
[    2.697786] usbcore: registered new interface driver usbserial_generic
[    2.697788] usbserial: USB Serial Driver core
[    2.697844] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.698279] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.698290] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.708048] mice: PS/2 mouse device common for all mice
[    2.756062] rtc_cmos 00:02: RTC can wake from S4
[    2.756120] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.756173] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.756281] device-mapper: uevent: version 1.0.3
[    2.756443] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.756503] device-mapper: multipath: version 1.0.5 loaded
[    2.756507] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.756587] cpuidle: using governor ladder
[    2.756590] cpuidle: using governor menu
[    2.757167] TCP cubic registered
[    2.757263] NET: Registered protocol family 10
[    2.757742] lo: Disabled Privacy Extensions
[    2.758111] NET: Registered protocol family 17
[    2.758143] Bluetooth: L2CAP ver 2.11
[    2.758145] Bluetooth: L2CAP socket layer initialized
[    2.758148] Bluetooth: SCO (Voice Link) ver 0.6
[    2.758150] Bluetooth: SCO socket layer initialized
[    2.758217] Bluetooth: RFCOMM socket layer initialized
[    2.758226] Bluetooth: RFCOMM TTY layer initialized
[    2.758228] Bluetooth: RFCOMM ver 1.10
[    2.758258] powernow-k8: Power state transitions not supported
[    2.758420] registered taskstats version 1
[    2.758586]   Magic number: 5:625:1002
[    2.758604] block sda4: hash matches
[    2.758640] i8042 aux 00:04: hash matches
[    2.758702] rtc_cmos 00:02: setting system clock to 2009-04-01 20:59:04 UTC (1238619544)
[    2.758706] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.758708] EDD information not available.
[    2.758755] Freeing unused kernel memory: 536k freed
[    2.759333] Write protecting the kernel read-only data: 6712k
[    2.801561] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.918407] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.918470] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.919261] eth0: VIA Rhine II at 0xfba00000, 00:13:d4:8d:cd:be, IRQ 23.
[    3.919971] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[    4.367527] PM: Starting manual resume from disk
[    4.367534] PM: Resume from partition 8:9
[    4.367536] PM: Checking hibernation image.
[    4.367753] PM: Resume from disk failed.
[    4.391583] kjournald starting.  Commit interval 5 seconds
[    4.391605] EXT3-fs: mounted filesystem with ordered data mode.
[    8.096679] udev: starting version 140
[    8.250284] parport_pc 00:07: reported by Plug and Play ACPI
[    8.250394] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    8.317861] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.926099] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.111612] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[    9.111628] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    9.192111] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.217596] ppdev: user-space parallel port driver
[    9.693057] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[    9.868018] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   10.372225] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   10.372246] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   10.373262] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   10.373429] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   10.886814] codec_read: codec 0 is not valid [0xfe0000]
[   10.893418] codec_read: codec 0 is not valid [0xfe0000]
[   10.900065] codec_read: codec 0 is not valid [0xfe0000]
[   10.906664] codec_read: codec 0 is not valid [0xfe0000]
[   11.108815] lp0: using parport0 (interrupt-driven).
[   11.452545] Adding 5116660k swap on /dev/sda9.  Priority:-1 extents:1 across:5116660k
[   12.096216] EXT3 FS on sda8, internal journal
[   13.228740] type=1505 audit(1238619554.969:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1909
[   13.308928] type=1505 audit(1238619555.049:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1913
[   13.309196] type=1505 audit(1238619555.049:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1913
[   13.309277] type=1505 audit(1238619555.049:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1913
[   13.309354] type=1505 audit(1238619555.049:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1913
[   13.513289] type=1505 audit(1238619555.253:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1918
[   13.513637] type=1505 audit(1238619555.253:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1918
[   13.563843] type=1505 audit(1238619555.301:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1922
[   16.834353] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.834358] Bluetooth: BNEP filters: protocol multicast
[   16.848278] Bridge firewalling registered
[   18.247233] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.645468] [drm] Initialized drm 1.1.0 20060810
[   18.764509] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   19.008685] agpgart-amd64 0000:00:00.0: AGP 3.5 bridge
[   19.008709] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   19.008776] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   19.237717] [drm] Setting GART location based on new memory map
[   19.237727] [drm] Loading R300 Microcode
[   19.237789] [drm] Num pipes: 1
[   19.237795] [drm] writeback test succeeded in 1 usecs
[   22.260831] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   32.440019] eth0: no IPv6 routers present
[  109.732293] ppdev0: registered pardevice
[  109.780271] ppdev0: unregistered pardevice
[  109.928101] ppdev0: registered pardevice
[  109.976030] ppdev0: unregistered pardevice
[  109.981312] ppdev0: registered pardevice
[  110.028442] ppdev0: unregistered pardevice
```

---

### Post by Cybie257 on 2009-04-02
I've seen this a few times so here's the first thing I would check...

go to : System -> Administration -> Hardware Drivers

Make sure there isn't a driver there for the WIFI that needs to be enabled. 

If there, enable it and you should be good to go. If not, back to the drawing board, I guess. But this has fixed a few that I've come across, especially HP notebooks. 

-Cybie

---

### Post by pbpersson on 2009-04-02
1.  This machine is a desktop with no WIFI

2.  The machine is communicating with the gateway but it is not getting a DHCP lease

---

### Post by Cybie257 on 2009-04-02
> **pbpersson said:**
> 1.  This machine is a desktop with no WIFI

2.  The machine is communicating with the gateway but it is not getting a DHCP lease

Sorry bout that. I must have been extremely tired last night when I posted. I could've sworn I was posting to a WIFI issue. lol.. 

Looking closer at your if config output, the only difference I see with yours is that is't only showing for IPV6.

Check out your System -> Prefernces -> Network Connections and see if IPV4 tab is there. if not, it might just be the IPv4 isn't enable for some odd reason. 

If it's there, try manually setting an IP and see if that connects you.

Other than that, I'm not sure where else to go as I can't say I've run into any such problems. 

Here is my output (first 3 lines):

```
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:4f:62:51  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe4f:6251/64 Scope:Link
```

Hopefully this might help get you somewhere... All I can do is try. :) 

-Cybie

---

### Post by pbpersson on 2009-04-02
Thinking out loud.....

I have not worked on this since.....well, 20 hours ago and now I am at work.

However, I was reviewing some documentation on how DHCP works.

The one part I did not mention - this is a test machine with multiple OS installations.  That Ethernet card - the MAC address is bound to 6 other IP addresses within the DHCP server.

I am wondering if when I start Jaunty dhclient I need to sit there and wait for the DHCP server to offer all previous 6 IP addresses and then tell Jaunty it cannot use them before it will offer Jaunty a new IP address that it really can use that is not taken by the other 6 operating systems on other partitions of that test machine.

Just a random thought....

---

### Post by pbpersson on 2009-04-02
> **Cybie257 said:**
> 

Here is my output (first 3 lines):

```
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:4f:62:51  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe4f:6251/64 Scope:Link
```

Hopefully this might help get you somewhere... All I can do is try. :) 

-Cybie

Can you tell me how your first three lines are different from my three lines?

---

### Post by pbpersson on 2009-04-02
NO, I cannot get it to work.  

I would like to know why it works fine from a Live CD but not when you install it.

I guess I will wait for them to come out with the production CD.

Hopefully this will all be fixed by then.

---

### Post by pbpersson on 2009-04-03
I installed a different network card in the machine - that one works fine from the Live CD and also will not work from the installation on the hard drive.

While I was on the Live CD I sent a hardware report for Jaunty and told them of my problems in the comments.

---

### Post by Cybie257 on 2009-04-05
> **pbpersson said:**
> Can you tell me how your first three lines are different from my three lines?

Sorry bout the delay..

YOUR first 3 lines:
```
eth0      Link encap:Ethernet  HWaddr 00:13:d4:8d:cd:be  
          inet6 addr: fe80::213:d4ff:fe8d:cdbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```

MINE:
```
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:4f:62:51  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe4f:6251/64 Scope:Link
```

I was just noticing that I had the IPv4 address AND the IPv6, while yours was missing the IPv4. So, my first and only thought on that was the possibility noted about IPv4 not being enabled. Might be as simple as that, may be way off. just offering something easy to check. :)

-Cybie

---

### Post by pbpersson on 2009-04-05
> **Cybie257 said:**
> Sorry bout the delay..

I was just noticing that I had the IPv4 address AND the IPv6, while yours was missing the IPv4. So, my first and only thought on that was the possibility noted about IPv4 not being enabled. Might be as simple as that, may be way off. just offering something easy to check. :)

-Cybie

Yes, I have no idea what that means or why it is missing.

It is very frustrating that it works perfectly from the Live CD but will not when it is installed to the hard drive.

I really wanted to try Jaunty Jackalope since I heard such good things about it

**UPDATE**

I just downloaded and burned the production version of Jaunty and had this very same problem

I had to do into the network connection properties and change the IPv4 setting from

DHCP

to 

DHCP (address only)

and now it works just fine.  I don't know what this means but I thought I would add this note in case it helps anyone

---

### Post by autocrosser on 2009-04-11
My output:

eth1      Link encap:Ethernet  HWaddr 00:1f:d0:da:14:5e  
                 inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
                 inet6 addr: fe80::21f:d0ff:feda:145e/64 Scope:Link
                 UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
                 RX packets:160157 errors:0 dropped:0 overruns:0 frame:0
                 TX packets:165709 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:1000 
                 RX bytes:120982595 (120.9 MB)  TX bytes:17713420 (17.7 MB)
                 Interrupt:247 Base address:0x2000 


I noted that sometime during testing my ethernet went from eth0 to eth1--have had no ill-effects from it. but maybe that is something to look at..............

second random thought: Ronacc has had problems with the new way inet6 is done---it is now very hard to blacklist it & several people have had ISP problems--that may be your root problem with a non-connect...

---

