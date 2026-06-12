---
title: "Intrepid [8.10] is EXTREMELY slow after upgrade from 8.04"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by tuxpenguin on 2008-11-07
Normally I would completely wipe the drive and install again when a new version of Ubuntu comes out, but since I'd never done it before, and I was feeling lazy, I figured I'd update from 8.04. 

Boy am I sad I did that.

Normally on bootup the Ubuntu splashscreen, the loading bar does it's bouncing thing once, then fills the bar in about 10 seconds. After upgrading, I noticed that it was taking longer...significantly longer, to boot. Almost 40 seconds. After I waited, I got to my login page and logged in. Again, it takes at least a year and a day for everything on my desktop to load.[I only have three extra programs loading on boot: Cairo-dock, and the "Places" and "Digi Clock" screenlets.]. It doesn't get much faster after booting...it's just acting sluggish in general.

Now, I do have a pretty slow HDD [it's IDE...another SATA is next on my list after a nice flat panel ;)], but it's never been THIS slow. It has to be something to do with the HDD...I don't think there's any other reason other than something screwy with the upgrade. I've seen others telling people to check their grub boot files for discrepancies in the kernel line, but I haven't found anything wrong there...and like I said, I haven't changed anything there either. 

Here are my specs: 
BioStar A770 A2+ Mobo
AMD Athlon 64 X2 [Dual-core at 2.6GHz]
2GB RAM
EVGA Geforce 8800 GS

Thanks for any help!
-Matt

---

### Post by dabl on 2008-11-07
I'd say ```
cat dmesg
``` and have a look at what is going on during the boot process. Probably one or two things are the source of the slowdown.

---

### Post by tuxpenguin on 2008-11-07
Believe it or not, that command returns: "No such file or directory". 

hmmm...:confused:

---

### Post by Slim Odds on 2008-11-07
dmesg is a command

Just run it

---

### Post by tuxpenguin on 2008-11-07
ah. Gotcha. I was wondering what the "cat" was for. :-/

The output is very long...I'm not sure which section of it I should be looking for. Should I post what I can see of the output here?

Thanks again.

---

### Post by dabl on 2008-11-07
> **tuxpenguin said:**
> Believe it or not, that command returns: "No such file or directory". 

hmmm...:confused:

Oops -- my bad!  Sorry -- it's just the dmesg command.

Look at the time stamps and the process -- you're looking for where a lot of time got lost.  Probably it's hanging on a piece of hardware, like a PVR card or optical drive or something.

---

### Post by petermck on 2008-11-07
You could try 'dmesg|grep time', 'dmesg|grep fail' etc to search for lines with keywords or dmesg|less to scroll up and down.
I've noticed a slow boot after the upgrade but nothing as bad as what you describe. It seems to be slow loading up network stuff.

---

### Post by tuxpenguin on 2008-11-07
I looked through the output, I came up with a couple things that look a little out of place...tell me what you think.

These were the only output when I used "dmesg|grep fail":
```
[    2.908020] ata1: softreset failed (device not ready)
[    2.908026] ata1: failed due to HW bug, retry pmp=0
[   13.287321] PM: Resume from disk failed.

```

[BTW, that brings to mind another problem. Whenever I shutdown or restart my computer from Ubuntu, it hangs on a blank screen with a blinking cursor...maybe these problems are connected?]

I also see this message during the first seconds after grub starts booting:
```
[    0.004000] Aperture beyond 4GB. Ignoring.

```

Doesn't look like anything, but then again I don't really know what I'm looking at here. I saw lots of network-related entries, nearly hundreds of them, to be more exact...is this normal?

-Matt

---

### Post by tuxpenguin on 2008-11-07
Just found this...seems like I lose a lot of time here [biggest jump in timestamps]:

```
[   22.629909] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   22.790753] ppdev: user-space parallel port driver
[   25.000028] Clocksource tsc unstable (delta = -153867949 ns)
[   31.273130] r8169: eth0: link up
[   31.273196] r8169: eth0: link up
[   31.654092] NET: Registered protocol family 17
[   76.351275] NET: Registered protocol family 10
[   76.352436] lo: Disabled Privacy Extensions
[   86.520538] eth0: no IPv6 routers present
[  132.881967] ppdev0: registered pardevice
[  132.928081] ppdev0: unregistered pardevice
[  133.278558] ppdev0: registered pardevice
[  133.324931] ppdev0: unregistered pardevice
[  133.380014] type=1503 audit(1226086930.398:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6743/net/" pid=6743 profile="/usr/sbin/cupsd"

```

The last entry in that example is similar to the kind of entry I see in the output for the next 50+ lines, so I just copied that one only.

---

### Post by poulpillusion on 2009-02-24
Hello, 

Did anyone eventually solve this problem ? My Intrepid Ibex Ubuntu is very slow after I have upgraded from Hardy too... 

Here is my full dmesg output : 

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3782b000 - 37fefabb
[    0.000000] ACPI: RSDP 000F7D60, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FEE3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEE3180, 906B (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: MCFG 7FEEC300, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEEC240, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003782b000 - 0037fefabb]          RAMDISK ==> [003782b000 - 0037fefabb]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f5d70] 000f5d70
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523887
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292034 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519281
[    0.000000] Kernel command line: root=UUID=19e4a0ce-2fab-4414-be18-d58d53432ce1 ro quiet splash locale=fr_FR 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2009.215 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062496k/2096000k available (2576k kernel code, 32216k reserved, 1165k data, 424k init, 1178496k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4018.43 BogoMIPS (lpj=8036860)
[    0.004027] Security Framework initialized
[    0.004033] SELinux:  Disabled at boot.
[    0.004055] AppArmor: AppArmor initialized
[    0.004063] Mount-cache hash table entries: 512
[    0.004218] Initializing cgroup subsys ns
[    0.004222] Initializing cgroup subsys cpuacct
[    0.004225] Initializing cgroup subsys memory
[    0.004238] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004240] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004243] CPU 0(2) -> Core 0
[    0.004245] using C1E aware idle routine
[    0.004255] Checking 'hlt' instruction... OK.
[    0.021519] ACPI: Core revision 20080609
[    0.024621] ACPI: Checking initramfs for custom DSDT
[    0.364309] ENABLING IO-APIC IRQs
[    0.364519] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.404797] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.408025] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4018.80 BogoMIPS (lpj=8037606)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.492163] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.492191] Brought up 2 CPUs
[    0.492193] Total of 2 processors activated (8037.23 BogoMIPS).
[    0.492232] CPU0 attaching sched-domain:
[    0.492235]  domain 0: span 0-1 level CPU
[    0.492237]   groups: 0 1
[    0.492243] CPU1 attaching sched-domain:
[    0.492246]  domain 0: span 0-1 level CPU
[    0.492248]   groups: 1 0
[    0.492311] net_namespace: 840 bytes
[    0.492311] Booting paravirtualized kernel on bare hardware
[    0.492311] Time:  9:22:42  Date: 02/24/09
[    0.492314] NET: Registered protocol family 16
[    0.492334] EISA bus registered
[    0.492334] ACPI: bus type pci registered
[    0.492334] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.492334] PCI: MCFG area at f0000000 reserved in E820
[    0.492334] PCI: Using MMCONFIG for extended config space
[    0.492334] PCI: Using configuration type 1 for base access
[    0.493356] ACPI: EC: Look up EC in DSDT
[    0.509449] ACPI: Interpreter enabled
[    0.509453] ACPI: (supports S0 S1 S3 S4 S5)
[    0.509471] ACPI: Using IOAPIC for interrupt routing
[    0.524377] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.524377] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.524377] PCI: 0000:00:01.1 reg 10 io port: [fc00, fc3f]
[    0.524377] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
[    0.524377] PCI: 0000:00:01.1 reg 24 io port: [1c40, 1c7f]
[    0.524377] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.524377] pci 0000:00:01.1: PME# disabled
[    0.524377] PCI: 0000:00:02.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.524377] pci 0000:00:02.0: supports D1
[    0.524377] pci 0000:00:02.0: supports D2
[    0.524377] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524377] pci 0000:00:02.0: PME# disabled
[    0.524377] PCI: 0000:00:02.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    0.524377] pci 0000:00:02.1: supports D1
[    0.524377] pci 0000:00:02.1: supports D2
[    0.524377] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524377] pci 0000:00:02.1: PME# disabled
[    0.524377] PCI: 0000:00:04.0 reg 20 io port: [f000, f00f]
[    0.524392] PCI: 0000:00:05.0 reg 10 io port: [9f0, 9f7]
[    0.524395] PCI: 0000:00:05.0 reg 14 io port: [bf0, bf3]
[    0.524399] PCI: 0000:00:05.0 reg 18 io port: [970, 977]
[    0.524403] PCI: 0000:00:05.0 reg 1c io port: [b70, b73]
[    0.524407] PCI: 0000:00:05.0 reg 20 io port: [dc00, dc0f]
[    0.524411] PCI: 0000:00:05.0 reg 24 32bit mmio: [fe02d000, fe02dfff]
[    0.524438] PCI: 0000:00:05.1 reg 10 io port: [9e0, 9e7]
[    0.524441] PCI: 0000:00:05.1 reg 14 io port: [be0, be3]
[    0.524445] PCI: 0000:00:05.1 reg 18 io port: [960, 967]
[    0.524449] PCI: 0000:00:05.1 reg 1c io port: [b60, b63]
[    0.524453] PCI: 0000:00:05.1 reg 20 io port: [c800, c80f]
[    0.524457] PCI: 0000:00:05.1 reg 24 32bit mmio: [fe02c000, fe02cfff]
[    0.524481] PCI: 0000:00:05.2 reg 10 io port: [c400, c407]
[    0.524485] PCI: 0000:00:05.2 reg 14 io port: [c000, c003]
[    0.524489] PCI: 0000:00:05.2 reg 18 io port: [bc00, bc07]
[    0.524493] PCI: 0000:00:05.2 reg 1c io port: [b800, b803]
[    0.524497] PCI: 0000:00:05.2 reg 20 io port: [b400, b40f]
[    0.524501] PCI: 0000:00:05.2 reg 24 32bit mmio: [fe02b000, fe02bfff]
[    0.524548] PCI: 0000:00:06.1 reg 10 32bit mmio: [fe020000, fe023fff]
[    0.524568] pci 0000:00:06.1: PME# supported from D3hot D3cold
[    0.524572] pci 0000:00:06.1: PME# disabled
[    0.524599] PCI: 0000:00:08.0 reg 10 32bit mmio: [fe02a000, fe02afff]
[    0.524603] PCI: 0000:00:08.0 reg 14 io port: [b000, b007]
[    0.524607] PCI: 0000:00:08.0 reg 18 32bit mmio: [fe029000, fe0290ff]
[    0.524612] PCI: 0000:00:08.0 reg 1c 32bit mmio: [fe028000, fe02800f]
[    0.524628] pci 0000:00:08.0: supports D1
[    0.524630] pci 0000:00:08.0: supports D2
[    0.524632] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524636] pci 0000:00:08.0: PME# disabled
[    0.524659] PCI: 0000:00:09.0 reg 10 32bit mmio: [fe027000, fe027fff]
[    0.524663] PCI: 0000:00:09.0 reg 14 io port: [ac00, ac07]
[    0.524667] PCI: 0000:00:09.0 reg 18 32bit mmio: [fe026000, fe0260ff]
[    0.524671] PCI: 0000:00:09.0 reg 1c 32bit mmio: [fe025000, fe02500f]
[    0.524688] pci 0000:00:09.0: supports D1
[    0.524689] pci 0000:00:09.0: supports D2
[    0.524692] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524696] pci 0000:00:09.0: PME# disabled
[    0.524721] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524724] pci 0000:00:0a.0: PME# disabled
[    0.524747] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524750] pci 0000:00:0b.0: PME# disabled
[    0.524772] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524776] pci 0000:00:0c.0: PME# disabled
[    0.524798] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524801] pci 0000:00:0d.0: PME# disabled
[    0.524824] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524827] pci 0000:00:0e.0: PME# disabled
[    0.524850] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524853] pci 0000:00:0f.0: PME# disabled
[    0.524947] PCI: 0000:01:0b.0 reg 10 32bit mmio: [fdeff000, fdeff7ff]
[    0.524952] PCI: 0000:01:0b.0 reg 14 32bit mmio: [fdef8000, fdefbfff]
[    0.524976] pci 0000:01:0b.0: supports D1
[    0.524978] pci 0000:01:0b.0: supports D2
[    0.524980] pci 0000:01:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.524984] pci 0000:01:0b.0: PME# disabled
[    0.525001] pci 0000:00:06.0: transparent bridge
[    0.525005] PCI: bridge 0000:00:06.0 32bit mmio: [fde00000, fdefffff]
[    0.525184] PCI: 0000:06:00.0 reg 24 32bit mmio: [fddfe000, fddfffff]
[    0.525191] PCI: 0000:06:00.0 reg 30 32bit mmio: [fdde0000, fddeffff]
[    0.525208] pci 0000:06:00.0: PME# supported from D3hot
[    0.525212] pci 0000:06:00.0: PME# disabled
[    0.525240] PCI: 0000:06:00.1 reg 10 io port: [9c00, 9c07]
[    0.525247] PCI: 0000:06:00.1 reg 14 io port: [9800, 9803]
[    0.525254] PCI: 0000:06:00.1 reg 18 io port: [9400, 9407]
[    0.525261] PCI: 0000:06:00.1 reg 1c io port: [9000, 9003]
[    0.525268] PCI: 0000:06:00.1 reg 20 io port: [8c00, 8c0f]
[    0.525324] PCI: bridge 0000:00:0e.0 io port: [8000, 9fff]
[    0.525327] PCI: bridge 0000:00:0e.0 32bit mmio: [fdd00000, fddfffff]
[    0.525349] PCI: 0000:07:00.0 reg 10 32bit mmio: [fa000000, faffffff]
[    0.525357] PCI: 0000:07:00.0 reg 14 64bit mmio: [e0000000, efffffff]
[    0.525364] PCI: 0000:07:00.0 reg 1c 64bit mmio: [fb000000, fbffffff]
[    0.525369] PCI: 0000:07:00.0 reg 24 io port: [7c00, 7c7f]
[    0.525374] PCI: 0000:07:00.0 reg 30 32bit mmio: [fcfe0000, fcffffff]
[    0.525409] PCI: bridge 0000:00:0f.0 io port: [7000, 7fff]
[    0.525412] PCI: bridge 0000:00:0f.0 32bit mmio: [fa000000, fcffffff]
[    0.525416] PCI: bridge 0000:00:0f.0 64bit mmio pref: [e0000000, efffffff]
[    0.525429] bus 00 -> node 0
[    0.525437] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.526029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.672370] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.672571] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.672864] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.673158] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.673451] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.673747] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 *10 11 14 15)
[    0.674042] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[    0.674334] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.674630] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.674925] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.676114] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.676411] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 9 *10 11 14 15)
[    0.676707] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[    0.677001] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.677298] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.677592] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.677886] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.678183] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.678478] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[    0.678774] ACPI: PCI Interrupt Link [LSA2] (IRQs *5 7 9 10 11 14 15)
[    0.679133] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.679483] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.679828] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.680174] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.680517] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.680856] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
[    0.681200] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    0.681545] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.681884] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.682229] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.682569] ACPI: PCI Interrupt Link [AMC1] (IRQs 20 21 22 23) *0
[    0.682916] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.683256] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.683602] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.683942] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.684297] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.684637] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.684984] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.685324] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.685670] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[    0.685770] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.685770] pnp: PnP ACPI init
[    0.685770] ACPI: bus type pnp registered
[    0.693127] pnp: PnP ACPI: found 14 devices
[    0.693127] ACPI: ACPI bus type pnp unregistered
[    0.693127] PnPBIOS: Disabled by ACPI PNP
[    0.693127] PCI: Using ACPI for IRQ routing
[    0.700041] NET: Registered protocol family 8
[    0.700043] NET: Registered protocol family 20
[    0.700072] NetLabel: Initializing
[    0.700074] NetLabel:  domain hash size = 128
[    0.700076] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.700090] NetLabel:  unlabeled traffic allowed by default
[    0.700696] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.700698]    actual entries 65620
[    0.700832] AppArmor: AppArmor Filesystem Enabled
[    0.700859] ACPI: RTC can wake from S4
[    0.708053] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.708057] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.708060] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.708063] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.708067] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.708070] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.708077] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.708080] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.708083] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.708099] system 00:0d: iomem range 0xd2800-0xd3fff has been reserved
[    0.708103] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.708106] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.708110] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.708113] system 00:0d: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.708116] system 00:0d: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.708120] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.708123] system 00:0d: iomem range 0x100000-0x7fedffff could not be reserved
[    0.708126] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.708129] system 00:0d: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.708133] system 00:0d: iomem range 0xfefff000-0xfeffffff could not be reserved
[    0.708136] system 00:0d: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.708139] system 00:0d: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.708143] system 00:0d: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.743305] pci 0000:00:06.0: PCI bridge, secondary bus 0000:01
[    0.743307] pci 0000:00:06.0:   IO window: disabled
[    0.743312] pci 0000:00:06.0:   MEM window: 0xfde00000-0xfdefffff
[    0.743315] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.743319] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.743321] pci 0000:00:0a.0:   IO window: disabled
[    0.743324] pci 0000:00:0a.0:   MEM window: disabled
[    0.743327] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.743331] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.743333] pci 0000:00:0b.0:   IO window: disabled
[    0.743336] pci 0000:00:0b.0:   MEM window: disabled
[    0.743339] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.743342] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.743345] pci 0000:00:0c.0:   IO window: disabled
[    0.743348] pci 0000:00:0c.0:   MEM window: disabled
[    0.743350] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.743354] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:05
[    0.743356] pci 0000:00:0d.0:   IO window: disabled
[    0.743359] pci 0000:00:0d.0:   MEM window: disabled
[    0.743362] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.743366] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:06
[    0.743369] pci 0000:00:0e.0:   IO window: 0x8000-0x9fff
[    0.743372] pci 0000:00:0e.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.743375] pci 0000:00:0e.0:   PREFETCH window: disabled
[    0.743379] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:07
[    0.743381] pci 0000:00:0f.0:   IO window: 0x7000-0x7fff
[    0.743385] pci 0000:00:0f.0:   MEM window: 0xfa000000-0xfcffffff
[    0.743388] pci 0000:00:0f.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.743397] pci 0000:00:06.0: setting latency timer to 64
[    0.743404] pci 0000:00:0a.0: setting latency timer to 64
[    0.743409] pci 0000:00:0b.0: setting latency timer to 64
[    0.743415] pci 0000:00:0c.0: setting latency timer to 64
[    0.743420] pci 0000:00:0d.0: setting latency timer to 64
[    0.743425] pci 0000:00:0e.0: setting latency timer to 64
[    0.743430] pci 0000:00:0f.0: setting latency timer to 64
[    0.743434] bus: 00 index 0 io port: [0, ffff]
[    0.743436] bus: 00 index 1 mmio: [0, ffffffff]
[    0.743438] bus: 01 index 0 mmio: [0, 0]
[    0.743441] bus: 01 index 1 mmio: [fde00000, fdefffff]
[    0.743443] bus: 01 index 2 mmio: [0, 0]
[    0.743445] bus: 01 index 3 io port: [0, ffff]
[    0.743448] bus: 01 index 4 mmio: [0, ffffffff]
[    0.743450] bus: 02 index 0 mmio: [0, 0]
[    0.743452] bus: 02 index 1 mmio: [0, 0]
[    0.743454] bus: 02 index 2 mmio: [0, 0]
[    0.743456] bus: 02 index 3 mmio: [0, 0]
[    0.743458] bus: 03 index 0 mmio: [0, 0]
[    0.743460] bus: 03 index 1 mmio: [0, 0]
[    0.743462] bus: 03 index 2 mmio: [0, 0]
[    0.743464] bus: 03 index 3 mmio: [0, 0]
[    0.743466] bus: 04 index 0 mmio: [0, 0]
[    0.743468] bus: 04 index 1 mmio: [0, 0]
[    0.743470] bus: 04 index 2 mmio: [0, 0]
[    0.743472] bus: 04 index 3 mmio: [0, 0]
[    0.743474] bus: 05 index 0 mmio: [0, 0]
[    0.743476] bus: 05 index 1 mmio: [0, 0]
[    0.743479] bus: 05 index 2 mmio: [0, 0]
[    0.743481] bus: 05 index 3 mmio: [0, 0]
[    0.743483] bus: 06 index 0 io port: [8000, 9fff]
[    0.743485] bus: 06 index 1 mmio: [fdd00000, fddfffff]
[    0.743488] bus: 06 index 2 mmio: [0, 0]
[    0.743490] bus: 06 index 3 mmio: [0, 0]
[    0.743492] bus: 07 index 0 io port: [7000, 7fff]
[    0.743494] bus: 07 index 1 mmio: [fa000000, fcffffff]
[    0.743497] bus: 07 index 2 mmio: [e0000000, efffffff]
[    0.743499] bus: 07 index 3 mmio: [0, 0]
[    0.743510] NET: Registered protocol family 2
[    0.744049] Switched to high resolution mode on CPU 0
[    0.744207] Switched to high resolution mode on CPU 1
[    0.756068] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.756368] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.756934] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.757222] TCP: Hash tables configured (established 131072 bind 65536)
[    0.757226] TCP reno registered
[    0.764091] NET: Registered protocol family 1
[    0.764216] checking if image is initramfs... it is
[    1.454879] Freeing initrd memory: 7954k freed
[    1.455969] audit: initializing netlink socket (disabled)
[    1.455990] type=2000 audit(1235467362.452:1): initialized
[    1.462054] highmem bounce pool size: 64 pages
[    1.462061] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.464832] VFS: Disk quotas dquot_6.5.1
[    1.464933] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.465055] msgmni has been set to 1743
[    1.465183] io scheduler noop registered
[    1.465186] io scheduler anticipatory registered
[    1.465188] io scheduler deadline registered
[    1.465200] io scheduler cfq registered (default)
[    1.481076] pci 0000:00:05.0: Enabling HT MSI Mapping
[    1.481092] pci 0000:00:05.1: Enabling HT MSI Mapping
[    1.481109] pci 0000:00:05.2: Enabling HT MSI Mapping
[    1.481123] pci 0000:00:06.0: Enabling HT MSI Mapping
[    1.481140] pci 0000:00:06.1: Enabling HT MSI Mapping
[    1.481159] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.481177] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.481193] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.481210] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.481227] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.481244] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.481261] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.481278] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.481305] pci 0000:07:00.0: Boot video device
[    1.481439] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.481465] pcieport-driver 0000:00:0a.0: found MSI capability
[    1.481487] pci_express 0000:00:0a.0:pcie00: allocate port service
[    1.481541] pci_express 0000:00:0a.0:pcie03: allocate port service
[    1.481628] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.481652] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.481669] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.481722] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.481809] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.481833] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.481850] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.481904] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.481990] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.482014] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.482031] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.482082] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.482169] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    1.482193] pcieport-driver 0000:00:0e.0: found MSI capability
[    1.482210] pci_express 0000:00:0e.0:pcie00: allocate port service
[    1.482260] pci_express 0000:00:0e.0:pcie03: allocate port service
[    1.482346] pcieport-driver 0000:00:0f.0: setting latency timer to 64
[    1.482369] pcieport-driver 0000:00:0f.0: found MSI capability
[    1.482387] pci_express 0000:00:0f.0:pcie00: allocate port service
[    1.482437] pci_express 0000:00:0f.0:pcie03: allocate port service
[    1.482829] isapnp: Scanning for PnP cards...
[    1.835291] isapnp: No Plug & Play device found
[    1.874729] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.874867] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.875602] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.877861] brd: module loaded
[    1.877944] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.878083] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.878474] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.878480] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.878817] mice: PS/2 mouse device common for all mice
[    1.878960] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.878987] rtc0: alarms up to one year, y3k
[    1.879145] EISA: Probing bus 0 at eisa.0
[    1.879151] Cannot allocate resource for EISA slot 1
[    1.879167] Cannot allocate resource for EISA slot 7
[    1.879170] Cannot allocate resource for EISA slot 8
[    1.879172] EISA: Detected 0 cards.
[    1.879175] cpuidle: using governor ladder
[    1.879178] cpuidle: using governor menu
[    1.879721] TCP cubic registered
[    1.879748] Using IPI No-Shortcut mode
[    1.879965] registered taskstats version 1
[    1.880128]   Magic number: 13:553:374
[    1.880315] rtc_cmos 00:04: setting system clock to 2009-02-24 09:22:43 UTC (1235467363)
[    1.880319] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.880321] EDD information not available.
[    1.880589] Freeing unused kernel memory: 424k freed
[    1.880655] Write protecting the kernel text: 2580k
[    1.880697] Write protecting the kernel read-only data: 940k
[    1.906599] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.077188] fuse init (API version 7.9)
[    2.365212] fan PNP0C0B:00: registered as cooling_device0
[    2.365220] ACPI: Fan [FAN] (on)
[    2.381224] processor ACPI0007:00: registered as cooling_device1
[    2.381287] processor ACPI0007:01: registered as cooling_device2
[    2.384302] thermal LNXTHERM:01: registered as thermal_zone0
[    2.384831] ACPI: Thermal Zone [THRM] (40 C)
[    2.801421] usbcore: registered new interface driver usbfs
[    2.801455] usbcore: registered new interface driver hub
[    2.801487] usbcore: registered new device driver usb
[    2.803373] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.803930] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    2.803941] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    2.803953] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.803956] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.804005] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.804029] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[    2.863193] usb usb1: configuration #1 chosen from 1 choice
[    2.863223] hub 1-0:1.0: USB hub found
[    2.863234] hub 1-0:1.0: 10 ports detected
[    3.156405] No dock devices found.
[    3.158684] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.159243] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    3.159255] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    3.159266] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.159269] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.159304] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    3.159330] ehci_hcd 0000:00:02.1: debug port 1
[    3.159334] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.159351] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    3.172763] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.172929] usb usb2: configuration #1 chosen from 1 choice
[    3.172957] hub 2-0:1.0: USB hub found
[    3.172967] hub 2-0:1.0: 10 ports detected
[    3.173422] SCSI subsystem initialized
[    3.190083] libata version 3.00 loaded.
[    3.277505] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.278052] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    3.278064] forcedeth 0000:00:08.0: PCI INT A -> Link[APCH] -> GSI 21 (level, low) -> IRQ 21
[    3.278069] forcedeth 0000:00:08.0: setting latency timer to 64
[    3.278095] nv_probe: set workaround bit for reversed mac addr
[    3.800541] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:18:f3:8b:8b:2f
[    3.800547] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[    3.801250] ACPI: PCI Interrupt Link [AMC1] enabled at IRQ 20
[    3.801261] forcedeth 0000:00:09.0: PCI INT A -> Link[AMC1] -> GSI 20 (level, low) -> IRQ 20
[    3.801266] forcedeth 0000:00:09.0: setting latency timer to 64
[    3.801293] nv_probe: set workaround bit for reversed mac addr
[    4.320534] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:18:f3:8b:96:8d
[    4.320539] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[    4.322492] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    4.322506] ohci1394 0000:01:0b.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    4.372253] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.375876] ahci 0000:06:00.0: version 3.0
[    4.376437] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[    4.376449] ahci 0000:06:00.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[    4.376685] pata_acpi 0000:00:04.0: setting latency timer to 64
[    4.377230] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    4.377234] pata_acpi 0000:00:05.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    4.377251] pata_acpi 0000:00:05.0: setting latency timer to 64
[    4.377259] pata_acpi 0000:00:05.0: PCI INT A disabled
[    4.377753] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    4.377757] pata_acpi 0000:00:05.1: PCI INT B -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    4.377773] pata_acpi 0000:00:05.1: setting latency timer to 64
[    4.377780] pata_acpi 0000:00:05.1: PCI INT B disabled
[    4.378274] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    4.378277] pata_acpi 0000:00:05.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[    4.378294] pata_acpi 0000:00:05.2: setting latency timer to 64
[    4.378301] pata_acpi 0000:00:05.2: PCI INT C disabled
[    4.389044] ahci 0000:06:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    4.389050] ahci 0000:06:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    4.389056] ahci 0000:06:00.0: setting latency timer to 64
[    4.389263] scsi0 : ahci
[    4.389679] scsi1 : ahci
[    4.389726] ata1: SATA max UDMA/133 abar m8192@0xfddfe000 port 0xfddfe100 irq 16
[    4.389730] ata2: SATA max UDMA/133 abar m8192@0xfddfe000 port 0xfddfe180 irq 16
[    4.708035] ata1: SATA link down (SStatus 0 SControl 300)
[    5.044035] ata2: SATA link down (SStatus 0 SControl 300)
[    5.060080] pata_amd 0000:00:04.0: version 0.3.10
[    5.060129] pata_amd 0000:00:04.0: setting latency timer to 64
[    5.060202] pata_acpi 0000:06:00.1: enabling device (0000 -> 0001)
[    5.060219] scsi2 : pata_amd
[    5.060523] scsi3 : pata_amd
[    5.061480] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    5.061483] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    5.062126] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[    5.062133] pata_acpi 0000:06:00.1: PCI INT B -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[    5.062174] pata_acpi 0000:06:00.1: setting latency timer to 64
[    5.062190] pata_acpi 0000:06:00.1: PCI INT B disabled
[    5.224294] ata3.00: ATAPI: Optiarc DVD RW AD-7170A, 1.02, max UDMA/66
[    5.224312] ata3: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    5.240229] ata3.00: configured for UDMA/66
[    5.240274] ata4: port disabled. ignoring.
[    5.241223] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7170A  1.02 PQ: 0 ANSI: 5
[    5.241404] scsi 2:0:0:0: Attached scsi generic sg0 type 5
[    5.242033] sata_nv 0000:00:05.0: version 3.5
[    5.242046] sata_nv 0000:00:05.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    5.242050] sata_nv 0000:00:05.0: Using SWNCQ mode
[    5.242092] sata_nv 0000:00:05.0: setting latency timer to 64
[    5.242208] scsi4 : sata_nv
[    5.242288] scsi5 : sata_nv
[    5.242529] ata5: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 23
[    5.242533] ata6: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 23
[    5.644279] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000ebfa6f]
[    5.708048] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.760603] ata5.00: ATA-7: ST3160815AS, 3.AAC, max UDMA/133
[    5.760606] ata5.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    5.827249] ata5.00: configured for UDMA/133
[    6.136122] scsi 4:0:0:0: Direct-Access     ATA      ST3160815AS      3.AA PQ: 0 ANSI: 5
[    6.136293] scsi 4:0:0:0: Attached scsi generic sg1 type 0
[    6.136843] sata_nv 0000:00:05.1: PCI INT B -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    6.136847] sata_nv 0000:00:05.1: Using SWNCQ mode
[    6.136890] sata_nv 0000:00:05.1: setting latency timer to 64
[    6.137017] scsi6 : sata_nv
[    6.137356] scsi7 : sata_nv
[    6.137609] ata7: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc800 irq 22
[    6.137612] ata8: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc808 irq 22
[    6.760099] sata_nv 0000:00:05.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[    6.760104] sata_nv 0000:00:05.2: Using SWNCQ mode
[    6.760146] sata_nv 0000:00:05.2: setting latency timer to 64
[    6.760295] scsi8 : sata_nv
[    6.760750] scsi9 : sata_nv
[    6.761004] ata9: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb400 irq 21
[    6.761009] ata10: SATA max UDMA/133 cmd 0xbc00 ctl 0xb800 bmdma 0xb408 irq 21
[    7.384997] pata_jmicron 0000:06:00.1: PCI INT B -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[    7.385040] pata_jmicron 0000:06:00.1: setting latency timer to 64
[    7.385125] scsi10 : pata_jmicron
[    7.386205] scsi11 : pata_jmicron
[    7.386270] ata11: PATA max UDMA/100 cmd 0x9c00 ctl 0x9800 bmdma 0x8c00 irq 16
[    7.386273] ata12: PATA max UDMA/100 cmd 0x9400 ctl 0x9000 bmdma 0x8c08 irq 16
[    7.416863] Driver 'sr' needs updating - please use bus_type methods
[    7.419424] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.419430] Uniform CD-ROM driver Revision: 3.20
[    7.419529] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    7.424817] Driver 'sd' needs updating - please use bus_type methods
[    7.424936] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.424953] sd 4:0:0:0: [sda] Write Protect is off
[    7.424955] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.424980] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.425103] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.425116] sd 4:0:0:0: [sda] Write Protect is off
[    7.425119] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.425141] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.425145]  sda: sda1 sda2 < sda5 >
[    7.470279] sd 4:0:0:0: [sda] Attached SCSI disk
[    7.961053] PM: Starting manual resume from disk
[    7.961059] PM: Resume from partition 8:5
[    7.961061] PM: Checking hibernation image.
[    7.961212] PM: Resume from disk failed.
[    8.012745] kjournald starting.  Commit interval 5 seconds
[    8.012757] EXT3-fs: mounted filesystem with ordered data mode.
[   15.595744] udevd version 124 started
[   16.192781] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   16.192789] ACPI: I/O resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM01 [0x1c40-0x1c45]
[   16.192792] ACPI: Device needs an ACPI driver
[   16.192821] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   16.288138] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
[   16.365230] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   16.385043] ACPI: Power Button (FF) [PWRF]
[   16.385128] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   16.401030] ACPI: Power Button (CM) [PWRB]
[   16.657223] parport_pc 00:09: reported by Plug and Play ACPI
[   16.657249] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   16.776742] Found: PMC Pm49FL004
[   16.776753] ck804xrom @fff80000: Found 1 x8 devices at 0x0 in 8-bit bank
[   16.902924] number of JEDEC chips: 1
[   16.902928] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
[   17.544305] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   17.544311] HDA Intel 0000:00:06.1: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[   17.544340] HDA Intel 0000:00:06.1: setting latency timer to 64
[   17.645874] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.963070] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.044115] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   18.212226] Linux agpgart interface v0.103
[   18.357080] nvidia: module license 'NVIDIA' taints kernel.
[   18.611774] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   18.611783] nvidia 0000:07:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[   18.611790] nvidia 0000:07:00.0: setting latency timer to 64
[   18.612218] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   18.794042] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   20.488550] lp0: using parport0 (interrupt-driven).
[   20.537487] it87: Found IT8716F chip at 0x290, revision 0
[   20.537498] it87: in3 is VCC (+5V)
[   20.537500] it87: in7 is VCCH (+5V Stand-By)
[   20.690305] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
[   21.252210] EXT3 FS on sda1, internal journal
[   22.436925] type=1505 audit(1235467384.070:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4366
[   22.502739] type=1505 audit(1235467384.135:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4371
[   22.708185] type=1505 audit(1235467384.339:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4375
[   22.708420] type=1505 audit(1235467384.339:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4375
[   22.760992] type=1505 audit(1235467384.391:6): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4379
[   22.921628] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.954104] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   22.955272] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   22.955277] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   22.955280] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   23.038659] NET: Registered protocol family 10
[   23.039251] lo: Disabled Privacy Extensions
[   23.051035] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   25.251437] ACPI: WMI: Mapper loaded
[   25.670708] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[   25.670736] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   25.670763] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   26.733056] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   28.221438] type=1502 audit(1235467374.417:7): operation="capable" name="sys_resource" pid=5406 profile="/usr/sbin/mysqld"
[   30.515993] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   30.516000] apm: disabled - APM is not SMP safe.
[   33.281318] ppdev: user-space parallel port driver
[   33.876022] eth0: no IPv6 routers present
[   40.250898] RPC: Registered udp transport module.
[   40.250904] RPC: Registered tcp transport module.
[   40.326417] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   40.408817] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   40.427981] NFSD: starting 90-second grace period
[   43.105554] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   43.105562] vboxdrv: Successfully done.
[   43.105564] vboxdrv: Found 2 processor cores.
[   43.105710] vboxdrv: fAsync=1 offMin=0x195311 offMax=0x195311
[   43.105724] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   43.105726] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   46.560321] Bluetooth: Core ver 2.13
[   46.565838] NET: Registered protocol family 31
[   46.565845] Bluetooth: HCI device and connection manager initialized
[   46.565850] Bluetooth: HCI socket layer initialized
[   46.583817] Bluetooth: L2CAP ver 2.11
[   46.583825] Bluetooth: L2CAP socket layer initialized
[   46.609232] Bluetooth: RFCOMM socket layer initialized
[   46.609254] Bluetooth: RFCOMM TTY layer initialized
[   46.609256] Bluetooth: RFCOMM ver 1.10
[   46.615788] Bluetooth: SCO (Voice Link) ver 0.6
[   46.615800] Bluetooth: SCO socket layer initialized
[   46.624640] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   46.624646] Bluetooth: BNEP filters: protocol multicast
[   46.738914] Bridge firewalling registered
[   51.340942] NET: Registered protocol family 17
[  202.465739] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:18:f3:8b:8b:2f:08:00:37:81:65:a9:08:00 SRC=192.168.0.100 DST=192.168.0.11 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=5250 PROTO=UDP SPT=161 DPT=47115 LEN=63 
[  203.644191] ppdev0: registered pardevice
[  203.692229] ppdev0: unregistered pardevice
[  204.290212] ppdev0: registered pardevice
[  204.336132] ppdev0: unregistered pardevice
[  204.422329] ppdev0: registered pardevice
[  204.468028] ppdev0: unregistered pardevice

```

---

### Post by TMoor on 2009-03-10
Same here, upgraded from 8.04 to 8.10 and the system is unusable, because as it seems there is a lot of hdd activity apparently for no reason. I don't know what to make of that.

Anyone has any idea what may be causing that?

---

### Post by Misaru-Meep on 2009-03-10
I've been searching for posts about problems with 8.10, but haven't found any that are too much alike to mine. Curious if anyone could help me. Sorry if I'm posting where I shouldn't, and if there is a similar post which I have not found yet. I upgraded from Hardy and now I can't seem to open my "Home" folder from the "Places" menu. It constantly gives me the message:

**Failed to execute child process "/media/KLAUSIE/Floola-linux/ffmpeg/Floola" (No such file or directory)**

"Klausie" is my iPod. If anyone could help, I'd surely appreciate it! Thank you!

---

### Post by TMoor on 2009-03-10
> **TMoor said:**
> Same here, upgraded from 8.04 to 8.10 and the system is unusable, because as it seems there is a lot of hdd activity apparently for no reason. I don't know what to make of that.

Anyone has any idea what may be causing that?


Problem was solved by switching to an older kernel.

---

### Post by chkhurum on 2009-09-28
I upgraded from 8.04 to 9.04 to find out that it is extremely slow on even very simple tasks. its like going back to 70s. Wireless not working and lots of other problems. 

How can you go back to previous kernel ?

---

### Post by chkhurum on 2009-09-28
Found the solution. Tried and it works much better.

[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

Thanks Ramoonus.

---

