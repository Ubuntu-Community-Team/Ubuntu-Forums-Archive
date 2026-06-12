---
title: "Help! New Lubuntu 15.1 install won't boot after software update and apt-get update"
date: 2016-03-20
forum: Installation &amp; Upgrades
---

### Post by cheapodonuts on 2016-03-20
I did a fresh erase disk and install of Wiley a yesterday and it's now dead after running apt-get update this morning.
Even yesterday problems were occurring with graphics crashes and a long boot time (9 mins). And previous to this install I had problems with 14.04 graphics and extreme boot times (20+ mins)

 I didn't allow updates to run while installing 15.10 this time and got most videos streaming by installing flash plugin installer with synaptic. Then, in the evening, I allowed software updater to run and carried on using the system after reboot, but still seeing occasional graphics crashes. Long boots were only occurring on 14.04 only after long shut downs and the same thing happened this morning with the new system.
 Which is why I finally decided to run apt-get update. I then rebooted and it failed. All I could do was take photos of what was on the screen. But When I tried to install Gimp a terminal popped up showing an error. I did as instructed, but afterwards, halfway through editing the images, I had a graphics and system crash. I still have the images, but I'm not starting Gimp again 

First screen of the failed boot 

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

-------------------

  After entering "help" it shows a huge list of single words that I'm not typing out here and I had no idea what to enter.

I have due to bad tinnitus and problems paying attention when stuff like this goes on so I often get angry and quit. But I may have entered something random, which didn't work.  I did  a second reboot after hard shut down. Same result. Messed about somehow, sorry I was getting angry and don't recall what, but  ended up seeing this 

[    0.218895] pnp 00:05: can't evaluate _CRS: 12298
Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the syatem wait long enough?)
  -Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/byuuid/a98004da-c473-4dce-a447-10ca8ec77 does not exist.
Dropping to a shell!


BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

--------------------------------------

After that I gave up and used the older version off the boot screen.

If someone thinks I may have made a mistake in typing out what I see in the images, please tell me and I'll check again, the images aren't perfectly focused..

----------

My system:

-Computer-
Processor        : 2x AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
Memory        : 1930MB (582MB used)
Operating System        : Ubuntu 15.10
User Name        : cheapo (cheapo)
Date/Time        : Sun 20 Mar 2016 11:31:07 GMT
-Display-
Resolution        : 1280x1024 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA NVidia
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Microsoft Microsoft Trackball Explorer®
 HDA NVidia Front Mic
 HDA NVidia Rear Mic
 HDA NVidia Line
 HDA NVidia Line Out Front
 HDA NVidia Line Out Surround
 HDA NVidia Line Out CLFE
 HDA NVidia Line Out Side
 HDA NVidia Front Headphone
-Printers-
No printers found
-SCSI Disks-
ATA WDC WD3200AAJS-6
Generic USB SD Reader
Generic USB CF Reader
Generic USB SM Reader
Generic USB MS Reader
TSSTcorp CDDVDW TS-H653Q


Thanx in advance for your assistance people! :)
Images of tasty donuts await you!due to bad tinnitus

---

### Post by Bucky Ball on 2016-03-20
Boot the machine, highlight the kernel you want to boot, hit 'e' to edit it, find the line that ends in 'quiet splash' and add 'nomodeset' so it looks like this:

> quiet splash nomodeset

... at the END of that line. You only add that one word 'nomodeset'. Do not delete or add anything else. 

Follow the instructions at the bottom of that screen to save and continue (control+x or b from memory).

---

### Post by cheapodonuts on 2016-03-20
That line does not end with quiet splash, $vt_handoff comes after it. Shall I add it to that?

---

### Post by Bucky Ball on 2016-03-20
No. After 'quiet splash' insert a space then 'nomodeset', regardless of what comes after it.

---

### Post by cheapodonuts on 2016-03-20
Unfortunately, no difference was made. I still get the "Can't evaluate_12298 blah blah dropping to a shell" result. :(

---

### Post by Bucky Ball on 2016-03-20
Let's see this file:

> nano /etc/default/grub

---

### Post by cheapodonuts on 2016-03-22
Not sure if this is any use as the select version screen no longer comes up. It was doing that before, even though I had selected auto login.
 But the system is pretty much borked right now ans doesn't boot unless I do several hard resets. After that the previous version finally opens up without any view of a grub or Dos screen.  

But here it is for this one anyway.

nano /etc/default/grub # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by cheapodonuts on 2016-03-28
So,
 After another fresh wipe and install of Wiley, with no updates or anything installed I had just a couple of graphics issues during the day. But next day had a long boot, though I didn't time it. Yesterday and today both had very long boot times, 20+mins and I did several hard resets and eventually held down the esc key, then selected the hard drive to get something on the screen a couple of minutes later. I have since installed flash plugin installer so I can watch BBC vids.
I tried running the live disk just now and it was ok, watched a couple of Youtube vids, then made the graphics crash after installing and running Chromium browser. So I'm back on the fresh Wiley install to type this.

---------------------------------

nano /etc/default/grub # If you change this file, run 'update-grub' afterwards $
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)

--------------------------------

dmesg

```

[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: HP-Pavilion KX733AA-ABU a6511.uk/NARRA3, BIOS  5.14 06/20/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x77ee0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] found SMP MP-table at [mem 0x000f55f0-0x000f55ff] mapped at [c00f55f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20000000-0x377fffff]
[    0.000000]  [mem 0x20000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01cdc000, 0x01cdcfff] PGTABLE
[    0.000000] BRK [0x01cdd000, 0x01cddfff] PGTABLE
[    0.000000] RAMDISK: [mem 0x3411e000-0x36086fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F7740 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0x0000000077EE3100 000054 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 0x0000000077EE7F40 0000F4 (v03 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Pm1aEventBlock: 32/8 (20150619/tbfadt-623)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Pm1aControlBlock: 16/8 (20150619/tbfadt-623)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/PmTimerBlock: 32/8 (20150619/tbfadt-623)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 64/8 (20150619/tbfadt-623)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe1Block: 128/8 (20150619/tbfadt-623)
[    0.000000] ACPI BIOS Warning (bug): Invalid length for FADT/Pm1aEventBlock: 8, using default 32 (20150619/tbfadt-704)
[    0.000000] ACPI BIOS Warning (bug): Invalid length for FADT/Pm1aControlBlock: 8, using default 16 (20150619/tbfadt-704)
[    0.000000] ACPI BIOS Warning (bug): Invalid length for FADT/PmTimerBlock: 8, using default 32 (20150619/tbfadt-704)
[    0.000000] ACPI: DSDT 0x0000000077EE32C0 004C2F (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 0x0000000077EE0000 000040
[    0.000000] ACPI: FACS 0x0000000077EE0000 000040
[    0.000000] ACPI: SLIC 0x0000000077EE8180 000176 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: SSDT 0x0000000077EE8340 000248 (v01 HPQOEM SLIC-CPC 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 0x0000000077EE8600 000038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
[    0.000000] ACPI: MCFG 0x0000000077EE8680 00003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 0x0000000077EE8080 000098 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1026MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   Normal   [mem 0x0000000001000000-0x0000000037bfdfff]
[    0.000000]   HighMem  [mem 0x0000000037bfe000-0x0000000077edffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x0000000077edffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x0000000077edffff]
[    0.000000] On node 0 totalpages: 491134
[    0.000000]   DMA zone: 40 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 2190 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 262882 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 19 pages/cpu @f678b000 s47116 r0 d30708 u77824
[    0.000000] pcpu-alloc: s47116 r0 d30708 u77824 alloc=19*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 488904
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic root=UUID=1615d545-2cc2-4ece-bcd6-1d5c2c77392d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (00037bfe:00077ee0)
[    0.000000] Initializing Movable for node 0 (00000000:00000000)
[    0.000000] Memory: 1897384K/1964536K available (7574K kernel code, 738K rwdata, 3020K rodata, 928K init, 796K bss, 67152K reserved, 0K cma-reserved, 1051528K highmem)
[    0.000000] virtual kernel memory layout:
                   fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
                   pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
                   vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
                   lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
                     .init : 0xc1b14000 - 0xc1bfc000   ( 928 kB)
                     .data : 0xc1765bf0 - 0xc1b12a40   (3763 kB)
                     .text : 0xc1000000 - 0xc1765bf0   (7574 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 32.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=32, nr_cpu_ids=4
[    0.000000] NR_IRQS:2304 nr_irqs:456 16
[    0.000000] CPU 0 irqstacks, hard=f3c36000 soft=f3c38000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 76450417870 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2410.874 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 4821.74 BogoMIPS (lpj=9643496)
[    0.004017] pid_max: default: 32768 minimum: 301
[    0.004025] ACPI: Core revision 20150619
[    0.013260] ACPI: All ACPI Tables successfully acquired
[    0.013283] Security Framework initialized
[    0.013296] AppArmor: AppArmor initialized
[    0.013298] Yama: becoming mindful.
[    0.013349] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.013352] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.013610] Initializing cgroup subsys blkio
[    0.013615] Initializing cgroup subsys memory
[    0.013627] Initializing cgroup subsys devices
[    0.013630] Initializing cgroup subsys freezer
[    0.013634] Initializing cgroup subsys net_cls
[    0.013638] Initializing cgroup subsys perf_event
[    0.013642] Initializing cgroup subsys net_prio
[    0.013646] Initializing cgroup subsys hugetlb
[    0.013667] CPU: Physical Processor ID: 0
[    0.013669] CPU: Processor Core ID: 0
[    0.013672] mce: CPU supports 5 MCE banks
[    0.013678] LVT offset 0 assigned for vector 0xf9
[    0.013682] process: using AMD E400 aware idle routine
[    0.013687] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.013689] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4, 1GB 0
[    0.014131] Freeing SMP alternatives memory: 28K (c1bfc000 - c1c03000)
[    0.016017] ftrace: allocating 30215 entries in 60 pages
[    0.028115] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028616] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072000] smpboot: CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (fam: 0f, model: 6b, stepping: 02)
[    0.072000] Performance Events: AMD PMU driver.
[    0.072000] ... version:                0
[    0.072000] ... bit width:              48
[    0.072000] ... generic registers:      4
[    0.072000] ... value mask:             0000ffffffffffff
[    0.072000] ... max period:             00007fffffffffff
[    0.072000] ... fixed-purpose events:   0
[    0.072000] ... event mask:             000000000000000f
[    0.072000] CPU 1 irqstacks, hard=f3d76000 soft=f3d78000
[    0.072000] x86: Booting SMP configuration:
[    0.072000] .... node  #0, CPUs:      #1
[    0.008000] Initializing CPU#1
[    0.072221] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.148127] x86: Booted up 1 node, 2 CPUs
[    0.148130] smpboot: Total of 2 processors activated (9643.60 BogoMIPS)
[    0.148655] devtmpfs: initialized
[    0.148655] evm: security.selinux
[    0.148655] evm: security.SMACK64
[    0.148655] evm: security.SMACK64EXEC
[    0.148655] evm: security.SMACK64TRANSMUTE
[    0.148655] evm: security.SMACK64MMAP
[    0.148655] evm: security.ima
[    0.148655] evm: security.capability
[    0.148655] PM: Registering ACPI NVS region [mem 0x77ee0000-0x77ee2fff] (12288 bytes)
[    0.148655] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.148655] pinctrl core: initialized pinctrl subsystem
[    0.148655] RTC time: 10:30:32, date: 03/28/16
[    0.148655] NET: Registered protocol family 16
[    0.148655] EISA bus registered
[    0.160008] cpuidle: using governor ladder
[    0.172005] cpuidle: using governor menu
[    0.172018] node 0 link 0: io port [8000, ffff]
[    0.172021] TOM: 0000000080000000 aka 2048M
[    0.172024] node 0 link 0: mmio [a0000, bffff]
[    0.172027] node 0 link 0: mmio [80000000, efffffff]
[    0.172030] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.172032] node 0 link 0: mmio [f0000000, f04fffff]
[    0.172034] bus: [bus 00-04] on node 0 link 0
[    0.172036] bus: 00 [io  0x0000-0xffff]
[    0.172038] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.172040] bus: 00 [mem 0x80000000-0xf3ffffff]
[    0.172042] bus: 00 [mem 0xf4000000-0xfcffffffff]
[    0.172149] ACPI: bus type PCI registered
[    0.172153] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.172268] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.172271] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.172273] PCI: Using MMCONFIG for extended config space
[    0.172274] PCI: Using configuration type 1 for base access
[    0.172407] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.172408] mtrr: probably your BIOS does not setup all CPUs.
[    0.172409] mtrr: corrected configuration.
[    0.184152] ACPI: Added _OSI(Module Device)
[    0.184155] ACPI: Added _OSI(Processor Device)
[    0.184156] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.184158] ACPI: Added _OSI(Processor Aggregator Device)
[    0.189404] ACPI: Interpreter enabled
[    0.189422] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.189438] ACPI: (supports S0 S1 S3 S4 S5)
[    0.189441] ACPI: Using IOAPIC for interrupt routing
[    0.189477] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.195939] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.195947] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.195953] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.196017] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.196216] PCI host bridge to bus 0000:00
[    0.196220] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.196224] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.196226] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.196231] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.196234] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.196237] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfebfffff window]
[    0.196257] pci 0000:00:00.0: [10de:03ea] type 00 class 0x050000
[    0.196495] pci 0000:00:01.0: [10de:03e0] type 00 class 0x060100
[    0.196623] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
[    0.196639] pci 0000:00:01.1: reg 0x10: [io  0xfc00-0xfc3f]
[    0.196654] pci 0000:00:01.1: reg 0x20: [io  0x1c00-0x1c3f]
[    0.196660] pci 0000:00:01.1: reg 0x24: [io  0x1c40-0x1c7f]
[    0.196679] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.196788] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
[    0.196906] pci 0000:00:02.0: [10de:03f1] type 00 class 0x0c0310
[    0.196918] pci 0000:00:02.0: reg 0x10: [mem 0xfe02f000-0xfe02ffff]
[    0.196948] pci 0000:00:02.0: supports D1 D2
[    0.196951] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.197002] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.197064] pci 0000:00:02.1: [10de:03f2] type 00 class 0x0c0320
[    0.197078] pci 0000:00:02.1: reg 0x10: [mem 0xfe02e000-0xfe02e0ff]
[    0.197111] pci 0000:00:02.1: supports D1 D2
[    0.197113] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.197177] pci 0000:00:02.1: System wakeup disabled by ACPI
[    0.197242] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
[    0.197318] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.197376] pci 0000:00:05.0: [10de:03f0] type 00 class 0x040300
[    0.197391] pci 0000:00:05.0: reg 0x10: [mem 0xfe024000-0xfe027fff]
[    0.197424] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.197531] pci 0000:00:06.0: [10de:03ec] type 00 class 0x01018a
[    0.197554] pci 0000:00:06.0: reg 0x20: [io  0xf000-0xf00f]
[    0.197564] pci 0000:00:06.0: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.197567] pci 0000:00:06.0: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.197569] pci 0000:00:06.0: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.197572] pci 0000:00:06.0: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.197675] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
[    0.197688] pci 0000:00:07.0: reg 0x10: [mem 0xfe02d000-0xfe02dfff]
[    0.197694] pci 0000:00:07.0: reg 0x14: [io  0xec00-0xec07]
[    0.197718] pci 0000:00:07.0: supports D1 D2
[    0.197721] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.197773] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.197832] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
[    0.197843] pci 0000:00:08.0: reg 0x10: [io  0x09f0-0x09f7]
[    0.197848] pci 0000:00:08.0: reg 0x14: [io  0x0bf0-0x0bf3]
[    0.197852] pci 0000:00:08.0: reg 0x18: [io  0x0970-0x0977]
[    0.197857] pci 0000:00:08.0: reg 0x1c: [io  0x0b70-0x0b73]
[    0.197861] pci 0000:00:08.0: reg 0x20: [io  0xd800-0xd80f]
[    0.197866] pci 0000:00:08.0: reg 0x24: [mem 0xfe02c000-0xfe02cfff]
[    0.197972] pci 0000:00:08.1: [10de:03f6] type 00 class 0x010185
[    0.197984] pci 0000:00:08.1: reg 0x10: [io  0x09e0-0x09e7]
[    0.197988] pci 0000:00:08.1: reg 0x14: [io  0x0be0-0x0be3]
[    0.197993] pci 0000:00:08.1: reg 0x18: [io  0x0960-0x0967]
[    0.197997] pci 0000:00:08.1: reg 0x1c: [io  0x0b60-0x0b63]
[    0.198002] pci 0000:00:08.1: reg 0x20: [io  0xc400-0xc40f]
[    0.198007] pci 0000:00:08.1: reg 0x24: [mem 0xfe02b000-0xfe02bfff]
[    0.198120] pci 0000:00:09.0: [10de:03e8] type 01 class 0x060400
[    0.198148] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198199] pci 0000:00:09.0: System wakeup disabled by ACPI
[    0.198258] pci 0000:00:0b.0: [10de:03e9] type 01 class 0x060400
[    0.198283] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198336] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.198394] pci 0000:00:0c.0: [10de:03e9] type 01 class 0x060400
[    0.198419] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198470] pci 0000:00:0c.0: System wakeup disabled by ACPI
[    0.198529] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
[    0.198539] pci 0000:00:0d.0: reg 0x10: [mem 0xfb000000-0xfbffffff]
[    0.198545] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.198551] pci 0000:00:0d.0: reg 0x1c: [mem 0xfc000000-0xfcffffff 64bit]
[    0.198557] pci 0000:00:0d.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.198661] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.198759] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.198856] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.198951] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.199100] pci 0000:01:05.0: [11c1:5811] type 00 class 0x0c0010
[    0.199117] pci 0000:01:05.0: reg 0x10: [mem 0xfd7ff000-0xfd7fffff]
[    0.199164] pci 0000:01:05.0: supports D1 D2
[    0.199166] pci 0000:01:05.0: PME# supported from D0 D1 D2 D3hot
[    0.199248] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
[    0.199252] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.199255] pci 0000:00:04.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.199259] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.199262] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.199264] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.199267] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.199270] pci 0000:00:04.0:   bridge window [mem 0x000c0000-0x000dffff window] (subtractive decode)
[    0.199273] pci 0000:00:04.0:   bridge window [mem 0x80000000-0xfebfffff window] (subtractive decode)
[    0.199313] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.199317] pci 0000:00:09.0:   bridge window [io  0xa000-0xafff]
[    0.199320] pci 0000:00:09.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.199324] pci 0000:00:09.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.199366] pci 0000:00:0b.0: PCI bridge to [bus 03]
[    0.199370] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.199373] pci 0000:00:0b.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.199377] pci 0000:00:0b.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.199416] pci 0000:00:0c.0: PCI bridge to [bus 04]
[    0.199420] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.199423] pci 0000:00:0c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.199427] pci 0000:00:0c.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.199436] pci_bus 0000:00: on NUMA node 0
[    0.199872] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.199925] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.199974] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.200030] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 *7 9 10 11 14 15)
[    0.200079] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.200128] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.200178] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.200227] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.200277] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 *7 9 10 11 14 15)
[    0.200326] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.200376] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.200425] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.200475] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.200523] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.200573] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
[    0.200623] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.200672] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.200722] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.200772] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.200858] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.200940] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.201021] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.201101] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.201181] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.201262] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.201342] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.201422] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.201503] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0, disabled.
[    0.201584] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0, disabled.
[    0.201664] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0, disabled.
[    0.201745] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
[    0.201825] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0, disabled.
[    0.201906] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0, disabled.
[    0.201987] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0, disabled.
[    0.202068] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
[    0.202149] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
[    0.202230] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0, disabled.
[    0.202311] ACPI: PCI Interrupt Link [APSJ] (IRQs 21) *0, disabled.
[    0.202582] vgaarb: setting as boot device: PCI:0000:00:0d.0
[    0.202582] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
[    0.202582] vgaarb: loaded
[    0.202582] vgaarb: bridge control possible 0000:00:0d.0
[    0.202582] SCSI subsystem initialized
[    0.202582] libata version 3.00 loaded.
[    0.202582] ACPI: bus type USB registered
[    0.202582] usbcore: registered new interface driver usbfs
[    0.202582] usbcore: registered new interface driver hub
[    0.202582] usbcore: registered new device driver usb
[    0.202582] PCI: Using ACPI for IRQ routing
[    0.204966] PCI: pci_cache_line_size set to 64 bytes
[    0.205003] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.205006] e820: reserve RAM buffer [mem 0x77ee0000-0x77ffffff]
[    0.205188] NetLabel: Initializing
[    0.205190] NetLabel:  domain hash size = 128
[    0.205191] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.205206] NetLabel:  unlabeled traffic allowed by default
[    0.205242] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.205242] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[    0.205242] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.206119] clocksource: Switched to clocksource hpet
[    0.213603] AppArmor: AppArmor Filesystem Enabled
[    0.213714] pnp: PnP ACPI init
[    0.213887] system 00:00: [io  0x1000-0x107f] has been reserved
[    0.213891] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.213894] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.213897] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.213899] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.213902] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.213908] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.214016] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.214019] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.214022] system 00:01: [io  0x0294-0x0297] has been reserved
[    0.214026] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.214111] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.214262] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.214837] system 00:04: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.214841] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.214858] ACPI Error: Field [ASSM] at 524320 exceeds Buffer [BUF0] size 880 (bits) (20150619/dsopcode-236)
[    0.214864] ACPI Error: Method parse/execution failed [\_SB_.MEM_._CRS] (Node f3c920a8), AE_AML_BUFFER_LIMIT (20150619/psparse-536)
[    0.214871] ACPI Error: Method execution failed [\_SB_.MEM_._CRS] (Node f3c920a8), AE_AML_BUFFER_LIMIT (20150619/uteval-103)
[    0.214877] pnp 00:05: can't evaluate _CRS: 12298
[    0.214920] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.214929] pnp: PnP ACPI: found 6 devices
[    0.214934] PnPBIOS: Disabled by ACPI PNP
[    0.252951] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.252981] pci 0000:00:0d.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.252985] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.252988] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.252993] pci 0000:00:04.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.252996] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.253000] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.253003] pci 0000:00:09.0:   bridge window [io  0xa000-0xafff]
[    0.253006] pci 0000:00:09.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.253009] pci 0000:00:09.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.253013] pci 0000:00:0b.0: PCI bridge to [bus 03]
[    0.253016] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.253019] pci 0000:00:0b.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.253022] pci 0000:00:0b.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.253026] pci 0000:00:0c.0: PCI bridge to [bus 04]
[    0.253028] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.253031] pci 0000:00:0c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.253035] pci 0000:00:0c.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.253039] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.253042] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.253044] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.253047] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.253050] pci_bus 0000:00: resource 8 [mem 0x80000000-0xfebfffff window]
[    0.253053] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.253055] pci_bus 0000:01: resource 1 [mem 0xfd700000-0xfd7fffff]
[    0.253058] pci_bus 0000:01: resource 2 [mem 0xfde00000-0xfdefffff pref]
[    0.253061] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7 window]
[    0.253063] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff window]
[    0.253066] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.253069] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.253071] pci_bus 0000:01: resource 8 [mem 0x80000000-0xfebfffff window]
[    0.253074] pci_bus 0000:02: resource 0 [io  0xa000-0xafff]
[    0.253076] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.253079] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.253082] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
[    0.253084] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.253087] pci_bus 0000:03: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.253090] pci_bus 0000:04: resource 0 [io  0x8000-0x8fff]
[    0.253092] pci_bus 0000:04: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.253095] pci_bus 0000:04: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.253138] NET: Registered protocol family 2
[    0.253333] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.253356] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.253393] TCP: Hash tables configured (established 8192 bind 8192)
[    0.253434] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.253444] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.253507] NET: Registered protocol family 1
[    0.253801] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    0.254081] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.254197] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.254241] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.254291] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.254339] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.254388] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.254439] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.254493] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.254549] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.254556] pci 0000:00:0d.0: Video device with shadowed ROM
[    0.254566] PCI: CLS 32 bytes, default 64
[    0.254642] Trying to unpack rootfs image as initramfs...
[    0.953861] Freeing initrd memory: 32164K (f411e000 - f6087000)
[    0.953962] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x22c057a8ad1, max_idle_ns: 440795262396 ns
[    0.953986] microcode: AMD CPU family 0xf not supported
[    0.954178] Scanning for low memory corruption every 60 seconds
[    0.954635] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.954674] Initialise system trusted keyring
[    0.954704] audit: initializing netlink subsys (disabled)
[    0.954729] audit: type=2000 audit(1459161032.952:1): initialized
[    0.955086] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.957910] zpool: loaded
[    0.957913] zbud: loaded
[    0.958034] VFS: Disk quotas dquot_6.6.0
[    0.958098] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.958895] fuse init (API version 7.23)
[    0.959142] Key type big_key registered
[    0.959621] Key type asymmetric registered
[    0.959625] Asymmetric key parser 'x509' registered
[    0.959648] bounce: pool size: 64 pages
[    0.959709] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.959755] io scheduler noop registered
[    0.959758] io scheduler deadline registered (default)
[    0.959812] io scheduler cfq registered
[    0.960203] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.960215] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.960264] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    0.960266] vesafb: scrolling: redraw
[    0.960268] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.960287] vesafb: framebuffer at 0xe0000000, mapped to 0xf8600000, using 1216k, total 1216k
[    0.960422] Console: switching to colour frame buffer device 80x30
[    0.960438] fb0: VESA VGA frame buffer device
[    0.960575] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.960580] ACPI: Power Button [PWRB]
[    0.960658] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.960661] ACPI: Power Button [PWRF]
[    0.961083] ACPI: Invalid passive threshold
[    0.961339] thermal LNXTHERM:00: registered as thermal_zone0
[    0.961341] ACPI: Thermal Zone [THRM] (34 C)
[    0.961391] GHES: HEST is not enabled!
[    0.961452] isapnp: Scanning for PnP cards...
[    0.968069] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.970376] Linux agpgart interface v0.103
[    0.975989] brd: module loaded
[    0.977547] loop: module loaded
[    0.977941] libphy: Fixed MDIO Bus: probed
[    0.977945] tun: Universal TUN/TAP device driver, 1.6
[    0.977946] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.978010] PPP generic driver version 2.4.2
[    0.978110] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.978115] ehci-pci: EHCI PCI platform driver
[    0.978287] ehci-pci 0000:00:02.1: EHCI Host Controller
[    0.978297] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.978307] ehci-pci 0000:00:02.1: debug port 1
[    0.978342] ehci-pci 0000:00:02.1: cache line size of 32 is not supported
[    0.978367] ehci-pci 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.988020] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.988072] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.988074] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.988077] usb usb1: Product: EHCI Host Controller
[    0.988079] usb usb1: Manufacturer: Linux 4.2.0-16-generic ehci_hcd
[    0.988081] usb usb1: SerialNumber: 0000:00:02.1
[    0.988242] hub 1-0:1.0: USB hub found
[    0.988251] hub 1-0:1.0: 10 ports detected
[    0.988559] ehci-platform: EHCI generic platform driver
[    0.988576] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.988581] ohci-pci: OHCI PCI platform driver
[    0.988684] ohci-pci 0000:00:02.0: OHCI PCI host controller
[    0.988690] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.988722] ohci-pci 0000:00:02.0: irq 23, io mem 0xfe02f000
[    1.046048] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.046050] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.046053] usb usb2: Product: OHCI PCI host controller
[    1.046055] usb usb2: Manufacturer: Linux 4.2.0-16-generic ohci_hcd
[    1.046057] usb usb2: SerialNumber: 0000:00:02.0
[    1.046205] hub 2-0:1.0: USB hub found
[    1.046213] hub 2-0:1.0: 10 ports detected
[    1.046508] ohci-platform: OHCI generic platform driver
[    1.046523] uhci_hcd: USB Universal Host Controller Interface driver
[    1.046598] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.046600] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.047194] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.047342] mousedev: PS/2 mouse device common for all mice
[    1.047513] rtc_cmos 00:02: RTC can wake from S4
[    1.047687] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.047727] rtc_cmos 00:02: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.047740] i2c /dev entries driver
[    1.047829] device-mapper: uevent: version 1.0.3
[    1.047926] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.047960] platform eisa.0: Probing EISA bus 0
[    1.047964] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.047967] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.047970] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.047972] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.047975] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.047978] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.047980] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.047983] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.047985] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.047988] platform eisa.0: EISA: Detected 0 cards
[    1.048031] cpufreq-nforce2: No nForce2 chipset.
[    1.048043] ledtrig-cpu: registered to indicate activity on CPUs
[    1.048057] PCCT header not found.
[    1.048380] NET: Registered protocol family 10
[    1.048677] NET: Registered protocol family 17
[    1.048694] Key type dns_resolver registered
[    1.048941] Using IPI No-Shortcut mode
[    1.049114] Loading compiled-in X.509 certificates
[    1.052332] Loaded X.509 cert 'Build time autogenerated kernel key: 9a18469980b5ebdd28885474f95f179ffebbdfd7'
[    1.052350] registered taskstats version 1
[    1.052372] zswap: loading zswap
[    1.052375] zswap: using zbud pool
[    1.052380] zswap: using lzo compressor
[    1.055154] Key type trusted registered
[    1.060326] Key type encrypted registered
[    1.060338] AppArmor: AppArmor sha1 policy hashing enabled
[    1.060342] ima: No TPM chip found, activating TPM-bypass!
[    1.060374] evm: HMAC attrs: 0x1
[    1.060654]   Magic number: 8:622:528
[    1.060777] rtc_cmos 00:02: setting system clock to 2016-03-28 10:30:33 UTC (1459161033)
[    1.060995] powernow_k8: fid 0x10 (2400 MHz), vid 0xa
[    1.060997] powernow_k8: fid 0xe (2200 MHz), vid 0xc
[    1.060999] powernow_k8: fid 0xc (2000 MHz), vid 0xe
[    1.061000] powernow_k8: fid 0xa (1800 MHz), vid 0x10
[    1.061002] powernow_k8: fid 0x2 (1000 MHz), vid 0x12
[    1.061028] powernow_k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (2 cpu cores) (version 2.20.00)
[    1.061039] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.061040] EDD information not available.
[    1.061127] PM: Hibernation image not present or could not be loaded.
[    1.069956] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.270784] isapnp: No Plug & Play device found
[    1.271324] Freeing unused kernel memory: 928K (c1b14000 - c1bfc000)
[    1.271394] Write protecting the kernel text: 7576k
[    1.271426] Write protecting the kernel read-only data: 3024k
[    1.271428] NX-protecting the kernel data: 4712k
[    1.288627] random: systemd-udevd urandom read with 0 bits of entropy available
[    1.351029] pata_amd 0000:00:06.0: version 0.4.1
[    1.357092] usb 1-8: new high-speed USB device number 3 using ehci-pci
[    1.360204] scsi host0: pata_amd
[    1.362305] scsi host1: pata_amd
[    1.362394] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.362397] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.362456] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.362704] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    1.381884] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.388317] [drm] Initialized drm 1.1.0 20060810
[    1.416761] wmi: Mapper loaded
[    1.436069] firewire_ohci 0000:01:05.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    1.494019] usb 1-8: New USB device found, idVendor=058f, idProduct=6377
[    1.494025] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.494027] usb 1-8: Product: Mass Storage Device
[    1.494030] usb 1-8: Manufacturer: Generic
[    1.494032] usb 1-8: SerialNumber: 920321111113
[    1.526995] ata2: port disabled--ignoring
[    1.544025] usb 2-2: new low-speed USB device number 2 using ohci-pci
[    1.628478] usb-storage 1-8:1.0: USB Mass Storage device detected
[    1.628611] scsi host2: usb-storage 1-8:1.0
[    1.628730] usbcore: registered new interface driver usb-storage
[    1.632963] usbcore: registered new interface driver uas
[    1.768040] usb 2-2: New USB device found, idVendor=045e, idProduct=0024
[    1.768044] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.768047] usb 2-2: Product: Microsoft Trackball Explorer®
[    1.768049] usb 2-2: Manufacturer: Microsoft
[    1.780280] hidraw: raw HID events driver (C) Jiri Kosina
[    1.795568] usbcore: registered new interface driver usbhid
[    1.795572] usbhid: USB HID core driver
[    1.800312] input: Microsoft Microsoft Trackball Explorer® as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/0003:045E:0024.0001/input/input3
[    1.800466] hid-generic 0003:045E:0024.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Explorer®] on usb-0000:00:02.0-2/input0
[    1.884795] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:22:15:25:dc:0a
[    1.884801] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.884845] sata_nv 0000:00:08.0: version 3.5
[    1.885108] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    1.885675] scsi host3: sata_nv
[    1.885831] scsi host4: sata_nv
[    1.885908] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[    1.885911] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[    1.886135] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[    1.886620] scsi host5: sata_nv
[    1.887366] forcedeth 0000:00:07.0 enp0s7: renamed from eth0
[    1.887621] scsi host6: sata_nv
[    1.887705] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 21
[    1.887708] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 21
[    1.887773] checking generic (e0000000 130000) vs hw (e0000000 10000000)
[    1.887775] fb: switching to nouveaufb from VESA VGA
[    1.887810] Console: switching to colour dummy device 80x25
[    1.888313] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[    1.888548] nouveau  [  DEVICE][0000:00:0d.0] BOOT0  : 0x04c000a2
[    1.888551] nouveau  [  DEVICE][0000:00:0d.0] Chipset: C61 (NV4C)
[    1.888553] nouveau  [  DEVICE][0000:00:0d.0] Family : NV40
[    1.897695] nouveau  [   VBIOS][0000:00:0d.0] using image from PRAMIN
[    1.897847] nouveau  [   VBIOS][0000:00:0d.0] BIT signature found
[    1.897850] nouveau  [   VBIOS][0000:00:0d.0] version 05.61.32.25.02
[    1.898325] nouveau  [     PFB][0000:00:0d.0] RAM type: unknown
[    1.898328] nouveau  [     PFB][0000:00:0d.0] RAM size: 128 MiB
[    1.898330] nouveau  [     PFB][0000:00:0d.0]    ZCOMP: 0 tags
[    1.933491] nouveau  [  PTHERM][0000:00:0d.0] FAN control: none / external
[    1.933503] nouveau  [  PTHERM][0000:00:0d.0] internal sensor: no
[    1.953354] nouveau  [     CLK][0000:00:0d.0] 20: core 425 MHz shader 425 MHz 
[    1.953364] nouveau  [     CLK][0000:00:0d.0] --:   
[    1.953485] [TTM] Zone  kernel: Available graphics memory: 439488 kiB
[    1.953487] [TTM] Zone highmem: Available graphics memory: 965252 kiB
[    1.953489] [TTM] Initializing pool allocator
[    1.953497] [TTM] Initializing DMA pool allocator
[    1.953513] nouveau  [     DRM] VRAM: 125 MiB
[    1.953515] nouveau  [     DRM] GART: 512 MiB
[    1.953519] nouveau  [     DRM] TMDS table version 1.1
[    1.953521] nouveau  [     DRM] DCB version 3.0
[    1.953524] nouveau  [     DRM] DCB outp 00: 01000310 00000023
[    1.953527] nouveau  [     DRM] DCB outp 01: 00110204 98830003
[    1.953529] nouveau  [     DRM] DCB conn 00: 0000
[    1.953532] nouveau  [     DRM] DCB conn 01: 1131
[    1.953534] nouveau  [     DRM] DCB conn 02: 0110
[    1.953536] nouveau  [     DRM] DCB conn 03: 0111
[    1.953538] nouveau  [     DRM] DCB conn 04: 0113
[    1.954042] nouveau W[     DRM] DCB type 4 not known
[    1.954045] nouveau W[     DRM] Unknown-1 has no encoders, removing
[    1.954882] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.954883] [drm] Driver supports precise vblank timestamp query.
[    1.956826] nouveau  [     DRM] MM: using M2MF for buffer copies
[    1.964129] firewire_core 0000:01:05.0: created device fw0: GUID 001e8c00014ecccf, S400
[    1.985781] nouveau  [     DRM] allocated 1280x1024 fb: 0x9000, bo f6290000
[    1.985874] fbcon: nouveaufb (fb0) is primary device
[    1.986026] Console: switching to colour frame buffer device 160x64
[    1.986073] nouveau 0000:00:0d.0: fb0: nouveaufb frame buffer device
[    1.986075] nouveau 0000:00:0d.0: registered panic notifier
[    2.000033] [drm] Initialized nouveau 1.2.2 20120801 for 0000:00:0d.0 on minor 0
[    2.206244] ata5: SATA link down (SStatus 0 SControl 300)
[    2.352039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.360126] ata3.00: ATA-8: WDC WD3200AAJS-65B4A0, 01.03A01, max UDMA/133
[    2.360130] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.376119] ata3.00: configured for UDMA/133
[    2.376281] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-6 3A01 PQ: 0 ANSI: 5
[    2.376646] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    2.376670] sd 3:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.376712] sd 3:0:0:0: [sda] Write Protect is off
[    2.376715] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.376744] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.432494]  sda: sda1 sda2 < sda5 >
[    2.432876] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.628784] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.629407] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.630031] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.630655] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.630980] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.631237] sd 2:0:0:1: Attached scsi generic sg2 type 0
[    2.631454] sd 2:0:0:2: Attached scsi generic sg3 type 0
[    2.632354] sd 2:0:0:3: Attached scsi generic sg4 type 0
[    2.632916] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    2.633522] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    2.651029] sd 2:0:0:3: [sde] Attached SCSI removable disk
[    2.659152] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[    2.844037] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.852128] ata4.00: ATAPI: TSSTcorp CDDVDW TS-H653Q, 0303, max UDMA/33
[    2.868120] ata4.00: configured for UDMA/33
[    2.869063] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653Q  0303 PQ: 0 ANSI: 5
[    2.887404] sr 4:0:0:0: [sr0] scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.887407] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.887582] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.887727] sr 4:0:0:0: Attached scsi generic sg5 type 5
[    3.206232] ata6: SATA link down (SStatus 0 SControl 300)
[    4.384041] floppy0: no floppy controllers found
[    4.577521] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.185752] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    5.291528] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    5.291707] systemd[1]: Detected architecture x86.
[    5.306383] systemd[1]: Set hostname to <cheapo-KX733AA-ABU-a6511-uk>.
[    5.545052] random: nonblocking pool is initialized
[    5.951336] systemd[1]: Reached target Remote File Systems (Pre).
[    5.951479] systemd[1]: Created slice Root Slice.
[    5.951536] systemd[1]: Listening on udev Kernel Socket.
[    5.951598] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    5.951732] systemd[1]: Created slice User and Session Slice.
[    5.951841] systemd[1]: Listening on Journal Audit Socket.
[    5.951903] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    5.952059] systemd[1]: Created slice System Slice.
[    5.952942] systemd[1]: Starting Increase datagram queue length...
[    5.953181] systemd[1]: Created slice system-getty.slice.
[    5.953237] systemd[1]: Reached target Slices.
[    5.953555] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    5.953662] systemd[1]: Listening on Journal Socket (/dev/log).
[    5.953765] systemd[1]: Listening on udev Control Socket.
[    5.953794] systemd[1]: Reached target Encrypted Volumes.
[    5.953836] systemd[1]: Reached target User and Group Name Lookups.
[    5.953901] systemd[1]: Listening on fsck to fsckd communication Socket.
[    5.953968] systemd[1]: Listening on Journal Socket.
[    5.998436] systemd[1]: Starting udev Coldplug all Devices...
[    6.050444] systemd[1]: Starting Load Kernel Modules...
[    6.051662] systemd[1]: Mounting Debug File System...
[    6.053017] systemd[1]: Mounting Huge Pages File System...
[    6.054253] systemd[1]: Mounting POSIX Message Queue File System...
[    6.055388] systemd[1]: Starting Uncomplicated firewall...
[    6.056441] systemd[1]: Starting Setup Virtual Console...
[    6.059014] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    6.060318] systemd[1]: Started Read required files in advance.
[    6.160335] systemd[1]: Started Setup Virtual Console.
[    6.300770] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    6.301921] systemd[1]: Starting Create Static Device Nodes in /dev...
[    6.404192] systemd[1]: Mounted Huge Pages File System.
[    6.404258] systemd[1]: Mounted Debug File System.
[    6.404927] systemd[1]: Mounted POSIX Message Queue File System.
[    6.405233] systemd[1]: Started Increase datagram queue length.
[    6.418061] systemd[1]: Listening on Syslog Socket.
[    6.419053] systemd[1]: Starting Journal Service...
[    6.460847] systemd[1]: Started Uncomplicated firewall.
[    6.568687] systemd[1]: Started udev Coldplug all Devices.
[    6.825131] lp: driver loaded but no devices found
[    6.880138] ppdev: user-space parallel port driver
[    6.945458] systemd[1]: Started Load Kernel Modules.
[    6.946592] systemd[1]: Starting Apply Kernel Variables...
[    6.947899] systemd[1]: Mounting FUSE Control File System...
[    6.955159] systemd[1]: Mounted FUSE Control File System.
[    7.195265] systemd[1]: Started Journal Service.
[    8.637932] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.100445] systemd-journald[215]: Received request to flush runtime journal from PID 1
[    9.781850] i2c i2c-3: nForce2 SMBus adapter at 0x1c00
[    9.781987] i2c i2c-4: nForce2 SMBus adapter at 0x1c40
[   10.005491] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.182080] MCE: In-kernel MCE decoding enabled.
[   10.185283] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.281638] EDAC MC: Ver: 3.0.0
[   10.341559] AMD64 EDAC driver v3.4.0
[   10.341608] EDAC amd64: DRAM ECC disabled.
[   10.341613] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
                (Note that use of the override may cause unknown side effects.)
[   10.763373] kvm: disabled by bios
[   11.207151] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   11.207167] snd_hda_intel 0000:00:05.0: Disabling MSI
[   11.928033] snd_hda_codec_realtek hdaudioC0D0: ALC1200: SKU not ready 0x411111f0
[   12.016024] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC1200: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   12.016030] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.016033] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   12.016036] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   12.016038] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x1e/0x0
[   12.016040] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   12.016043] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[   12.016045] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[   12.016048] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1c
[   12.410962] Adding 1963004k swap on /dev/sda5.  Priority:-1 extents:1 across:1963004k FS
[   12.491100] audit: type=1400 audit(1459161044.924:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=433 comm="apparmor_parser"
[   12.491116] audit: type=1400 audit(1459161044.924:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=433 comm="apparmor_parser"
[   12.598682] audit: type=1400 audit(1459161045.036:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=433 comm="apparmor_parser"
[   12.598697] audit: type=1400 audit(1459161045.036:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=433 comm="apparmor_parser"
[   12.598704] audit: type=1400 audit(1459161045.036:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=433 comm="apparmor_parser"
[   12.598711] audit: type=1400 audit(1459161045.036:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=433 comm="apparmor_parser"
[   12.760245] audit: type=1400 audit(1459161045.196:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=433 comm="apparmor_parser"
[   12.760261] audit: type=1400 audit(1459161045.196:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=433 comm="apparmor_parser"
[   12.760269] audit: type=1400 audit(1459161045.196:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=433 comm="apparmor_parser"
[   12.760275] audit: type=1400 audit(1459161045.196:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=433 comm="apparmor_parser"
[   12.800058] floppy0: no floppy controllers found
[   13.951285] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input4
[   13.951405] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input5
[   13.951785] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input6
[   13.952049] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
[   13.952295] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
[   13.952402] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
[   13.952507] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
[   13.952611] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input11
[   23.494679] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[   23.495262] forcedeth 0000:00:07.0 enp0s7: MSI enabled
[   25.684445] nouveau E[    PBUS][0000:00:0d.0] MMIO write of 0x00a40001 FAULT at 0x00b000
[  115.164154] nouveau E[    PBUS][0000:00:0d.0] MMIO write of 0x00fc0001 FAULT at 0x00b010
[  115.675861] nouveau E[    PBUS][0000:00:0d.0] MMIO write of 0x00000000 FAULT at 0x00b010
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$

```
------------------------------------------------

---

### Post by Bucky Ball on 2016-03-28
Please start using code tags (see how in the green link in my signature below) rather than posting these massive terminal outputs. Otherwise a waste of space. Thanks.

---

### Post by cheapodonuts on 2016-03-28
Noted and sorted. Yes, it's way neater. :)

---

### Post by cheapodonuts on 2016-03-29
Anyway. Some vids won't play, so I'm about to run update manager to fully update the system. I'm confident that this won't fix any of the problems highlighted in this thread, so here goes.

---

### Post by cheapodonuts on 2016-05-02
Well.
 I've had no choice other than to keep  using what I have. Allowing all updates etc, but still have had to put up with 25 - 30 mins boot times.
I've just allowed the system to upgrade to Xenial, so I'll find out later today if my cold boot times have improved.
 
I don't think it will change as I now believe there is some kind of issue with the graphics not starting. The reason I say that is that I tried going through the key presses to run the live disk. Hold down 'esc' for about 90 seconds, then hit the down arrow 3 times which selects the CD drive to boot, then boot. Immediately after that I can see the led indicating that the CD drive is reading the disk that's in the tray.

Just for the heck of it, I've ordered a refurbished graphics card, so I will also be trying that when it arrives.

---

### Post by Bucky Ball on 2016-05-02
You're moving into a different line of inquiry and are heading toward needing support with a new issue which involves upgrading from 15.10 to 16.04 and problems, which has nothing to do with your original support request.

If you want help with this I'd suggest you improve your chances of getting it by posting a new thread with a descriptive title in Installations and Upgrades rather than looking for it two pages deep on a thread with an unrelated title and topic.

Good luck.

---

