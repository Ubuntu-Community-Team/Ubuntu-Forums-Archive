---
title: "Bad impression: first run wizard freezes"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by glaivekiddo on 2008-05-24
ok, so i installed ubuntu, and run it.
The first run wizard juz freezes for like 15 mins now.
i selected my time zone and caught a glimpse of partman something and den it freezes.
i dont know wad to do now, can i cancel the wizard and rerun it later. or anything else?


p/s it's been 1 hour now, and it still freezes. Can i juz cancel the wizard and rerun it next time, any1 plz tell me. c'mon

---

### Post by Forlong on 2008-05-24
I'm answering here but this is a response to this post:  [http://ubuntuforums.org/showthread.php?p=5031728#post5031728](http://ubuntuforums.org/showthread.php?p=5031728#post5031728)

It's safe to cancel the installation. The wizard did no do any changes to your hard drive up until now.

---

### Post by glaivekiddo on 2008-05-24
ok, thanks. but can i rerun it later?

---

### Post by Forlong on 2008-05-24
I'd recommend rebooting first.


edit: sorry, just read the other thread. Please try to keep all install-related issues to this one here.

So, did you notice anything unusual in gparted?
You can post a screenshot of that window ([Alt]+[Print]) if you like.

---

### Post by glaivekiddo on 2008-05-24
installation problem + desktop effects, what a day...

---

### Post by glaivekiddo on 2008-05-24
*sigh* back to here
i tried reboot and the wizard rerun, same problem, this time i wrote down the error mssg : Partman failed with exit code: 10. Further information can be found in /var/log/syslog

and here it is:

May 24 20:29:31 ubuntu syslogd 1.5.0#1ubuntu1: restart.
May 24 20:29:31 ubuntu kernel: Inspecting /boot/System.map-2.6.24-16-generic
May 24 20:29:31 ubuntu kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
May 24 20:29:31 ubuntu kernel: Symbols match kernel version 2.6.24.
May 24 20:29:32 ubuntu kernel: Loaded 19581 symbols from 86 modules.
May 24 20:29:32 ubuntu kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
May 24 20:29:32 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe53c00 (usable)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fe53c00 - 000000007fe55c00 (ACPI NVS)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fe55c00 - 000000007fe57c00 (ACPI data)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007fe57c00 - 0000000080000000 (reserved)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
May 24 20:29:32 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
May 24 20:29:32 ubuntu kernel: [    0.000000] 1150MB HIGHMEM available.
May 24 20:29:32 ubuntu kernel: [    0.000000] 896MB LOWMEM available.
May 24 20:29:32 ubuntu kernel: [    0.000000] found SMP MP-table at 000fe710
May 24 20:29:32 ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 523859) 0 entries of 256 used
May 24 20:29:32 ubuntu kernel: [    0.000000] Zone PFN ranges:
May 24 20:29:32 ubuntu kernel: [    0.000000]   DMA             0 ->     4096
May 24 20:29:32 ubuntu kernel: [    0.000000]   Normal       4096 ->   229376
May 24 20:29:32 ubuntu kernel: [    0.000000]   HighMem    229376 ->   523859
May 24 20:29:32 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
May 24 20:29:32 ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
May 24 20:29:32 ubuntu kernel: [    0.000000]     0:        0 ->   523859
May 24 20:29:32 ubuntu kernel: [    0.000000] On node 0 totalpages: 523859
May 24 20:29:32 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 24 20:29:32 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
May 24 20:29:32 ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May 24 20:29:32 ubuntu kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
May 24 20:29:32 ubuntu kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
May 24 20:29:32 ubuntu kernel: [    0.000000]   HighMem zone: 2300 pages used for memmap
May 24 20:29:32 ubuntu kernel: [    0.000000]   HighMem zone: 292183 pages, LIFO batch:31
May 24 20:29:32 ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 24 20:29:32 ubuntu kernel: [    0.000000] DMI 2.5 present.
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FEBF0 checksum 0
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: RSDP 000FEBF0, 0024 (r2 DELL  )
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: XSDT 000FD0A0, 0064 (r1 DELL    B9K           15 ASL        61)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: FACP 000FD1C0, 00F4 (r3 DELL    B9K           15 ASL        61)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: DSDT FFF5AE62, 2CBC (r1   DELL    dt_ex     1000 INTL 20050624)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: FACS 7FE53C00, 0040
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: SSDT FFF5DC3F, 00AC (r1   DELL    st_ex     1000 INTL 20050624)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: APIC 000FD2B4, 0092 (r1 DELL    B9K           15 ASL        61)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: BOOT 000FD346, 0028 (r1 DELL    B9K           15 ASL        61)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: MCFG 000FD36E, 003E (r1 DELL    B9K           15 ASL        61)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: HPET 000FD3AC, 0038 (r1 DELL    B9K           15 ASL        61)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: DUMY 7FE55C00, 0024 (r1 DELL    B9K           15 ASL        61)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: SLIC 000FD3E4, 0176 (r1 DELL    B9K           15 ASL        61)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May 24 20:29:32 ubuntu kernel: [    0.000000] Processor #0 6:15 APIC version 20
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
May 24 20:29:32 ubuntu kernel: [    0.000000] Processor #1 6:15 APIC version 20
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
May 24 20:29:32 ubuntu kernel: [    0.000000] Processor #2 6:15 APIC version 20
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
May 24 20:29:32 ubuntu kernel: [    0.000000] Processor #3 6:15 APIC version 20
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
May 24 20:29:32 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
May 24 20:29:32 ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May 24 20:29:32 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
May 24 20:29:32 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 24 20:29:32 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
May 24 20:29:32 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000f0000
May 24 20:29:32 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 24 20:29:32 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519767
May 24 20:29:32 ubuntu kernel: [    0.000000] Kernel command line: debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_AU.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
May 24 20:29:32 ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May 24 20:29:32 ubuntu kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May 24 20:29:32 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 24 20:29:32 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May 24 20:29:32 ubuntu kernel: [    0.000000] Initializing CPU#0
May 24 20:29:32 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May 24 20:29:32 ubuntu kernel: [    0.000000] Detected 2394.008 MHz processor.
May 24 20:29:32 ubuntu kernel: [   20.731499] Console: colour VGA+ 80x25
May 24 20:29:32 ubuntu kernel: [   20.731502] console [tty0] enabled
May 24 20:29:32 ubuntu kernel: [   20.731683] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May 24 20:29:32 ubuntu kernel: [   20.731885] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May 24 20:29:32 ubuntu kernel: [   20.794535] Memory: 2065100k/2095436k available (2157k kernel code, 29088k reserved, 998k data, 364k init, 1177932k highmem)
May 24 20:29:32 ubuntu kernel: [   20.794540] virtual kernel memory layout:
May 24 20:29:32 ubuntu kernel: [   20.794540]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May 24 20:29:32 ubuntu kernel: [   20.794541]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 24 20:29:32 ubuntu kernel: [   20.794542]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
May 24 20:29:32 ubuntu kernel: [   20.794543]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
May 24 20:29:32 ubuntu kernel: [   20.794544]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
May 24 20:29:32 ubuntu kernel: [   20.794544]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
May 24 20:29:32 ubuntu kernel: [   20.794545]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
May 24 20:29:32 ubuntu kernel: [   20.794547] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 24 20:29:32 ubuntu kernel: [   20.794579] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
May 24 20:29:32 ubuntu kernel: [   20.794684] hpet clockevent registered
May 24 20:29:32 ubuntu kernel: [   20.874550] Calibrating delay using timer specific routine.. 4791.55 BogoMIPS (lpj=9583117)
May 24 20:29:32 ubuntu kernel: [   20.874566] Security Framework initialized
May 24 20:29:32 ubuntu kernel: [   20.874571] SELinux:  Disabled at boot.
May 24 20:29:32 ubuntu kernel: [   20.874581] AppArmor: AppArmor initialized
May 24 20:29:32 ubuntu kernel: [   20.874584] Failure registering capabilities with primary security module.
May 24 20:29:32 ubuntu kernel: [   20.874590] Mount-cache hash table entries: 512
May 24 20:29:32 ubuntu kernel: [   20.874683] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
May 24 20:29:32 ubuntu kernel: [   20.874690] monitor/mwait feature present.
May 24 20:29:32 ubuntu kernel: [   20.874691] using mwait in idle threads.
May 24 20:29:32 ubuntu kernel: [   20.874694] CPU: L1 I cache: 32K, L1 D cache: 32K
May 24 20:29:32 ubuntu kernel: [   20.874696] CPU: L2 cache: 4096K
May 24 20:29:32 ubuntu kernel: [   20.874698] CPU: Physical Processor ID: 0
May 24 20:29:32 ubuntu kernel: [   20.874699] CPU: Processor Core ID: 0
May 24 20:29:32 ubuntu kernel: [   20.874700] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
May 24 20:29:32 ubuntu kernel: [   20.874706] Compat vDSO mapped to ffffe000.
May 24 20:29:32 ubuntu kernel: [   20.874716] Checking 'hlt' instruction... OK.
May 24 20:29:32 ubuntu kernel: [   20.890866] SMP alternatives: switching to UP code
May 24 20:29:32 ubuntu kernel: [   20.892074] Early unpacking initramfs... done
May 24 20:29:32 ubuntu kernel: [   21.141199] ACPI: Core revision 20070126
May 24 20:29:32 ubuntu kernel: [   21.189185] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 24 20:29:32 ubuntu kernel: [   21.278917] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
May 24 20:29:32 ubuntu kernel: [   21.278928] SMP alternatives: switching to SMP code
May 24 20:29:32 ubuntu kernel: [   21.279453] Booting processor 1/1 eip 3000
May 24 20:29:32 ubuntu kernel: [   21.289756] Initializing CPU#1
May 24 20:29:32 ubuntu kernel: [   21.369685] Calibrating delay using timer specific routine.. 4787.96 BogoMIPS (lpj=9575922)
May 24 20:29:32 ubuntu kernel: [   21.369690] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
May 24 20:29:32 ubuntu kernel: [   21.369694] monitor/mwait feature present.
May 24 20:29:32 ubuntu kernel: [   21.369696] CPU: L1 I cache: 32K, L1 D cache: 32K
May 24 20:29:32 ubuntu kernel: [   21.369697] CPU: L2 cache: 4096K
May 24 20:29:32 ubuntu kernel: [   21.369699] CPU: Physical Processor ID: 0
May 24 20:29:32 ubuntu kernel: [   21.369700] CPU: Processor Core ID: 1
May 24 20:29:32 ubuntu kernel: [   21.369701] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
May 24 20:29:32 ubuntu kernel: [   21.370303] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
May 24 20:29:32 ubuntu kernel: [   21.370324] SMP alternatives: switching to SMP code
May 24 20:29:32 ubuntu kernel: [   21.370892] Booting processor 2/2 eip 3000
May 24 20:29:32 ubuntu kernel: [   21.381146] Initializing CPU#2
May 24 20:29:32 ubuntu kernel: [   21.461525] Calibrating delay using timer specific routine.. 4787.98 BogoMIPS (lpj=9575979)
May 24 20:29:32 ubuntu kernel: [   21.461530] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
May 24 20:29:32 ubuntu kernel: [   21.461534] monitor/mwait feature present.
May 24 20:29:32 ubuntu kernel: [   21.461536] CPU: L1 I cache: 32K, L1 D cache: 32K
May 24 20:29:32 ubuntu kernel: [   21.461537] CPU: L2 cache: 4096K
May 24 20:29:32 ubuntu kernel: [   21.461539] CPU: Physical Processor ID: 0
May 24 20:29:32 ubuntu kernel: [   21.461540] CPU: Processor Core ID: 2
May 24 20:29:32 ubuntu kernel: [   21.461541] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
May 24 20:29:32 ubuntu kernel: [   21.462142] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
May 24 20:29:32 ubuntu kernel: [   21.462151] SMP alternatives: switching to SMP code
May 24 20:29:32 ubuntu kernel: [   21.462502] Booting processor 3/3 eip 3000
May 24 20:29:32 ubuntu kernel: [   21.472756] Initializing CPU#3
May 24 20:29:32 ubuntu kernel: [   21.549372] Calibrating delay using timer specific routine.. 4788.00 BogoMIPS (lpj=9576017)
May 24 20:29:32 ubuntu kernel: [   21.549377] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
May 24 20:29:32 ubuntu kernel: [   21.549381] monitor/mwait feature present.
May 24 20:29:32 ubuntu kernel: [   21.549383] CPU: L1 I cache: 32K, L1 D cache: 32K
May 24 20:29:32 ubuntu kernel: [   21.549384] CPU: L2 cache: 4096K
May 24 20:29:32 ubuntu kernel: [   21.549386] CPU: Physical Processor ID: 0
May 24 20:29:32 ubuntu kernel: [   21.549387] CPU: Processor Core ID: 3
May 24 20:29:32 ubuntu kernel: [   21.549388] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
May 24 20:29:32 ubuntu kernel: [   21.549989] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
May 24 20:29:32 ubuntu kernel: [   21.550003] Total of 4 processors activated (19155.51 BogoMIPS).
May 24 20:29:32 ubuntu kernel: [   21.550145] ENABLING IO-APIC IRQs
May 24 20:29:32 ubuntu kernel: [   21.550303] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May 24 20:29:32 ubuntu kernel: [   21.697187] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
May 24 20:29:32 ubuntu kernel: [   21.717186] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
May 24 20:29:32 ubuntu kernel: [   21.737194] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
May 24 20:29:32 ubuntu kernel: [   21.757174] Brought up 4 CPUs
May 24 20:29:32 ubuntu kernel: [   21.757211] CPU0 attaching sched-domain:
May 24 20:29:32 ubuntu kernel: [   21.757213]  domain 0: span 03
May 24 20:29:32 ubuntu kernel: [   21.757214]   groups: 01 02
May 24 20:29:32 ubuntu kernel: [   21.757216]   domain 1: span 0f
May 24 20:29:32 ubuntu kernel: [   21.757217]    groups: 03 0c
May 24 20:29:32 ubuntu kernel: [   21.757219] CPU1 attaching sched-domain:
May 24 20:29:32 ubuntu kernel: [   21.757220]  domain 0: span 03
May 24 20:29:32 ubuntu kernel: [   21.757221]   groups: 02 01
May 24 20:29:32 ubuntu kernel: [   21.757223]   domain 1: span 0f
May 24 20:29:32 ubuntu kernel: [   21.757224]    groups: 03 0c
May 24 20:29:32 ubuntu kernel: [   21.757226] CPU2 attaching sched-domain:
May 24 20:29:32 ubuntu kernel: [   21.757227]  domain 0: span 0c
May 24 20:29:32 ubuntu kernel: [   21.757228]   groups: 04 08
May 24 20:29:32 ubuntu kernel: [   21.757230]   domain 1: span 0f
May 24 20:29:32 ubuntu kernel: [   21.757231]    groups: 0c 03
May 24 20:29:32 ubuntu kernel: [   21.757233] CPU3 attaching sched-domain:
May 24 20:29:32 ubuntu kernel: [   21.757234]  domain 0: span 0c
May 24 20:29:32 ubuntu kernel: [   21.757235]   groups: 08 04
May 24 20:29:32 ubuntu kernel: [   21.757237]   domain 1: span 0f
May 24 20:29:32 ubuntu kernel: [   21.757238]    groups: 0c 03
May 24 20:29:32 ubuntu kernel: [   21.757466] net_namespace: 64 bytes
May 24 20:29:32 ubuntu kernel: [   21.757473] Booting paravirtualized kernel on bare hardware
May 24 20:29:32 ubuntu kernel: [   21.757805] Time: 20:29:05  Date: 05/24/08
May 24 20:29:32 ubuntu kernel: [   21.757822] NET: Registered protocol family 16
May 24 20:29:32 ubuntu kernel: [   21.757946] EISA bus registered
May 24 20:29:32 ubuntu kernel: [   21.757950] ACPI: bus type pci registered
May 24 20:29:32 ubuntu kernel: [   21.764221] PCI: PCI BIOS revision 2.10 entry at 0xfbbe6, last bus=4
May 24 20:29:32 ubuntu kernel: [   21.764223] PCI: Using configuration type 1
May 24 20:29:32 ubuntu kernel: [   21.764224] Setting up standard PCI resources
May 24 20:29:32 ubuntu kernel: [   21.776410] ACPI: EC: Look up EC in DSDT
May 24 20:29:32 ubuntu kernel: [   21.819853] ACPI: BIOS _OSI(Linux) query ignored
May 24 20:29:32 ubuntu kernel: [   21.819854] ACPI: DMI System Vendor: Dell Inc.
May 24 20:29:32 ubuntu kernel: [   21.819856] ACPI: DMI Product Name: Dell XPS420                  
May 24 20:29:32 ubuntu kernel: [   21.819857] ACPI: DMI Product Version: 
May 24 20:29:32 ubuntu kernel: [   21.819858] ACPI: DMI Board Name: 0TP406
May 24 20:29:32 ubuntu kernel: [   21.819859] ACPI: DMI BIOS Vendor: Dell Inc.
May 24 20:29:32 ubuntu kernel: [   21.819860] ACPI: DMI BIOS Date: 01/02/2008
May 24 20:29:32 ubuntu kernel: [   21.819861] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
May 24 20:29:32 ubuntu kernel: [   21.819862] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
May 24 20:29:32 ubuntu kernel: [   21.844817] ACPI: Interpreter enabled
May 24 20:29:32 ubuntu kernel: [   21.844824] ACPI: (supports S0 S1 S3 S4 S5)
May 24 20:29:32 ubuntu kernel: [   21.844840] ACPI: Using IOAPIC for interrupt routing
May 24 20:29:32 ubuntu kernel: [   21.937618] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 24 20:29:32 ubuntu kernel: [   21.938305] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
May 24 20:29:32 ubuntu kernel: [   21.938308] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
May 24 20:29:32 ubuntu kernel: [   21.938716] PCI: Transparent bridge - 0000:00:1e.0
May 24 20:29:32 ubuntu kernel: [   21.938738] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 24 20:29:32 ubuntu kernel: [   21.939462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
May 24 20:29:32 ubuntu kernel: [   21.940077] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
May 24 20:29:32 ubuntu kernel: [   21.940576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
May 24 20:29:32 ubuntu kernel: [   23.219780] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
May 24 20:29:32 ubuntu kernel: [   23.220519] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
May 24 20:29:32 ubuntu kernel: [   23.221277] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
May 24 20:29:32 ubuntu kernel: [   23.222007] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
May 24 20:29:32 ubuntu kernel: [   23.222765] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
May 24 20:29:32 ubuntu kernel: [   23.223500] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
May 24 20:29:32 ubuntu kernel: [   23.224233] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
May 24 20:29:32 ubuntu kernel: [   23.224992] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
May 24 20:29:32 ubuntu kernel: [   23.225372] Linux Plug and Play Support v0.97 (c) Adam Belay
May 24 20:29:32 ubuntu kernel: [   23.225391] pnp: PnP ACPI init
May 24 20:29:32 ubuntu kernel: [   23.225395] ACPI: bus type pnp registered
May 24 20:29:32 ubuntu kernel: [   23.257037] pnp: PnP ACPI: found 7 devices
May 24 20:29:32 ubuntu kernel: [   23.257038] ACPI: ACPI bus type pnp unregistered
May 24 20:29:32 ubuntu kernel: [   23.257041] PnPBIOS: Disabled by ACPI PNP
May 24 20:29:32 ubuntu kernel: [   23.257187] PCI: Using ACPI for IRQ routing
May 24 20:29:32 ubuntu kernel: [   23.257188] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 24 20:29:32 ubuntu kernel: [   23.298471] NET: Registered protocol family 8
May 24 20:29:32 ubuntu kernel: [   23.298473] NET: Registered protocol family 20
May 24 20:29:32 ubuntu kernel: [   23.298503] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
May 24 20:29:32 ubuntu kernel: [   23.298508] hpet0: 4 64-bit timers, 14318180 Hz
May 24 20:29:32 ubuntu kernel: [   23.299529] AppArmor: AppArmor Filesystem Enabled
May 24 20:29:32 ubuntu kernel: [   23.302394] Time: tsc clocksource has been installed.
May 24 20:29:32 ubuntu kernel: [   23.302401] Switched to high resolution mode on CPU 0
May 24 20:29:32 ubuntu kernel: [   23.302470] Switched to high resolution mode on CPU 1
May 24 20:29:32 ubuntu kernel: [   23.304962] Switched to high resolution mode on CPU 2
May 24 20:29:32 ubuntu kernel: [   23.305000] Switched to high resolution mode on CPU 3
May 24 20:29:32 ubuntu kernel: [   23.318778] system 00:01: ioport range 0x800-0x85f has been reserved
May 24 20:29:32 ubuntu kernel: [   23.318782] system 00:01: ioport range 0xc00-0xc7f has been reserved
May 24 20:29:32 ubuntu kernel: [   23.318785] system 00:01: ioport range 0x860-0x8ff could not be reserved
May 24 20:29:32 ubuntu kernel: [   23.349057] PCI: Bridge: 0000:00:01.0
May 24 20:29:32 ubuntu kernel: [   23.349059]   IO window: d000-dfff
May 24 20:29:32 ubuntu kernel: [   23.349062]   MEM window: fa000000-fdefffff
May 24 20:29:32 ubuntu kernel: [   23.349064]   PREFETCH window: d0000000-dfffffff
May 24 20:29:32 ubuntu kernel: [   23.349066] PCI: Bridge: 0000:00:06.0
May 24 20:29:32 ubuntu kernel: [   23.349067]   IO window: disabled.
May 24 20:29:32 ubuntu kernel: [   23.349070]   MEM window: disabled.
May 24 20:29:32 ubuntu kernel: [   23.349071]   PREFETCH window: disabled.
May 24 20:29:32 ubuntu kernel: [   23.349074] PCI: Bridge: 0000:00:1c.0
May 24 20:29:32 ubuntu kernel: [   23.349074]   IO window: disabled.
May 24 20:29:32 ubuntu kernel: [   23.349078]   MEM window: f9f00000-f9ffffff
May 24 20:29:32 ubuntu kernel: [   23.349080]   PREFETCH window: disabled.
May 24 20:29:32 ubuntu kernel: [   23.349084] PCI: Bridge: 0000:00:1e.0
May 24 20:29:32 ubuntu kernel: [   23.349085]   IO window: disabled.
May 24 20:29:32 ubuntu kernel: [   23.349088]   MEM window: f9e00000-f9efffff
May 24 20:29:32 ubuntu kernel: [   23.349090]   PREFETCH window: disabled.
May 24 20:29:32 ubuntu kernel: [   23.349101] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
May 24 20:29:32 ubuntu kernel: [   23.349105] PCI: Setting latency timer of device 0000:00:01.0 to 64
May 24 20:29:32 ubuntu kernel: [   23.349111] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 16 (level, low) -> IRQ 16
May 24 20:29:32 ubuntu kernel: [   23.349114] PCI: Setting latency timer of device 0000:00:06.0 to 64
May 24 20:29:32 ubuntu kernel: [   23.349127] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
May 24 20:29:32 ubuntu kernel: [   23.349131] PCI: Setting latency timer of device 0000:00:1c.0 to 64
May 24 20:29:32 ubuntu kernel: [   23.349139] PCI: Setting latency timer of device 0000:00:1e.0 to 64
May 24 20:29:32 ubuntu kernel: [   23.349146] NET: Registered protocol family 2
May 24 20:29:32 ubuntu kernel: [   23.386677] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May 24 20:29:32 ubuntu kernel: [   23.386866] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May 24 20:29:32 ubuntu kernel: [   23.387164] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May 24 20:29:32 ubuntu kernel: [   23.387296] TCP: Hash tables configured (established 131072 bind 65536)
May 24 20:29:32 ubuntu kernel: [   23.387298] TCP reno registered
May 24 20:29:32 ubuntu kernel: [   23.398730] checking if image is initramfs... it is
May 24 20:29:32 ubuntu kernel: [   23.886599] Freeing initrd memory: 7665k freed
May 24 20:29:32 ubuntu kernel: [   23.886712] Simple Boot Flag at 0x7a set to 0x1
May 24 20:29:32 ubuntu kernel: [   23.887644] audit: initializing netlink socket (disabled)
May 24 20:29:32 ubuntu kernel: [   23.887658] audit(1211660946.941:1): initialized
May 24 20:29:32 ubuntu kernel: [   23.887872] highmem bounce pool size: 64 pages
May 24 20:29:32 ubuntu kernel: [   23.889986] VFS: Disk quotas dquot_6.5.1
May 24 20:29:32 ubuntu kernel: [   23.890063] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 24 20:29:32 ubuntu kernel: [   23.890190] io scheduler noop registered
May 24 20:29:32 ubuntu kernel: [   23.890192] io scheduler anticipatory registered
May 24 20:29:32 ubuntu kernel: [   23.890194] io scheduler deadline registered
May 24 20:29:32 ubuntu kernel: [   23.890205] io scheduler cfq registered (default)
May 24 20:29:32 ubuntu kernel: [   23.890329] Boot video device is 0000:01:00.0
May 24 20:29:32 ubuntu kernel: [   23.890433] PCI: Setting latency timer of device 0000:00:01.0 to 64
May 24 20:29:32 ubuntu kernel: [   23.890469] assign_interrupt_mode Found MSI capability
May 24 20:29:32 ubuntu kernel: [   23.890489] Allocate Port Service[0000:00:01.0:pcie00]
May 24 20:29:32 ubuntu kernel: [   23.890572] PCI: Setting latency timer of device 0000:00:06.0 to 64
May 24 20:29:32 ubuntu kernel: [   23.890606] assign_interrupt_mode Found MSI capability
May 24 20:29:32 ubuntu kernel: [   23.890631] Allocate Port Service[0000:00:06.0:pcie00]
May 24 20:29:32 ubuntu kernel: [   23.890705] PCI: Setting latency timer of device 0000:00:1c.0 to 64
May 24 20:29:32 ubuntu kernel: [   23.890744] assign_interrupt_mode Found MSI capability
May 24 20:29:32 ubuntu kernel: [   23.890775] Allocate Port Service[0000:00:1c.0:pcie00]
May 24 20:29:32 ubuntu kernel: [   23.890809] Allocate Port Service[0000:00:1c.0:pcie02]
May 24 20:29:32 ubuntu kernel: [   23.891094] isapnp: Scanning for PnP cards...
May 24 20:29:32 ubuntu kernel: [   24.243293] isapnp: No Plug & Play device found
May 24 20:29:32 ubuntu kernel: [   24.270942] Real Time Clock Driver v1.12ac
May 24 20:29:32 ubuntu kernel: [   24.271232] hpet_resources: 0xfed00000 is busy
May 24 20:29:32 ubuntu kernel: [   24.271248] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 24 20:29:32 ubuntu kernel: [   24.272415] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 24 20:29:32 ubuntu kernel: [   24.272483] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 24 20:29:32 ubuntu kernel: [   24.272624] PNP: No PS/2 controller found. Probing ports directly.
May 24 20:29:32 ubuntu kernel: [   24.275306] serio: i8042 KBD port at 0x60,0x64 irq 1
May 24 20:29:32 ubuntu kernel: [   24.275310] serio: i8042 AUX port at 0x60,0x64 irq 12
May 24 20:29:32 ubuntu kernel: [   24.290124] mice: PS/2 mouse device common for all mice
May 24 20:29:32 ubuntu kernel: [   24.290247] EISA: Probing bus 0 at eisa.0
May 24 20:29:32 ubuntu kernel: [   24.290269] EISA: Detected 0 cards.
May 24 20:29:32 ubuntu kernel: [   24.290271] cpuidle: using governor ladder
May 24 20:29:32 ubuntu kernel: [   24.290272] cpuidle: using governor menu
May 24 20:29:32 ubuntu kernel: [   24.290330] NET: Registered protocol family 1
May 24 20:29:32 ubuntu kernel: [   24.290348] Using IPI No-Shortcut mode
May 24 20:29:32 ubuntu kernel: [   24.290365] registered taskstats version 1
May 24 20:29:32 ubuntu kernel: [   24.290445]   Magic number: 8:844:498
May 24 20:29:32 ubuntu kernel: [   24.290469] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 24 20:29:32 ubuntu kernel: [   24.290470] EDD information not available.
May 24 20:29:32 ubuntu kernel: [   24.290557] Freeing unused kernel memory: 364k freed
May 24 20:29:32 ubuntu kernel: [   25.447300] fuse init (API version 7.9)
May 24 20:29:32 ubuntu kernel: [   25.563337] usbcore: registered new interface driver usbfs
May 24 20:29:32 ubuntu kernel: [   25.563354] usbcore: registered new interface driver hub
May 24 20:29:32 ubuntu kernel: [   25.563448] usbcore: registered new device driver usb
May 24 20:29:32 ubuntu kernel: [   25.564307] USB Universal Host Controller Interface driver v3.0
May 24 20:29:32 ubuntu kernel: [   25.564356] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
May 24 20:29:32 ubuntu kernel: [   25.564365] PCI: Setting latency timer of device 0000:00:1a.0 to 64
May 24 20:29:32 ubuntu kernel: [   25.564369] uhci_hcd 0000:00:1a.0: UHCI Host Controller
May 24 20:29:32 ubuntu kernel: [   25.564552] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
May 24 20:29:32 ubuntu kernel: [   25.564577] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
May 24 20:29:32 ubuntu kernel: [   25.564680] usb usb1: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   25.564696] hub 1-0:1.0: USB hub found
May 24 20:29:32 ubuntu kernel: [   25.564699] hub 1-0:1.0: 2 ports detected
May 24 20:29:32 ubuntu kernel: [   25.640814] SCSI subsystem initialized
May 24 20:29:32 ubuntu kernel: [   25.649805] libata version 3.00 loaded.
May 24 20:29:32 ubuntu kernel: [   25.666171] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 17
May 24 20:29:32 ubuntu kernel: [   25.666180] PCI: Setting latency timer of device 0000:00:1a.1 to 64
May 24 20:29:32 ubuntu kernel: [   25.666183] uhci_hcd 0000:00:1a.1: UHCI Host Controller
May 24 20:29:32 ubuntu kernel: [   25.666199] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
May 24 20:29:32 ubuntu kernel: [   25.666222] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ff00
May 24 20:29:32 ubuntu kernel: [   25.666298] usb usb2: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   25.666314] hub 2-0:1.0: USB hub found
May 24 20:29:32 ubuntu kernel: [   25.666317] hub 2-0:1.0: 2 ports detected
May 24 20:29:32 ubuntu kernel: [   25.773964] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 22 (level, low) -> IRQ 18
May 24 20:29:32 ubuntu kernel: [   25.773969] PCI: Setting latency timer of device 0000:00:1a.2 to 64
May 24 20:29:32 ubuntu kernel: [   25.773972] uhci_hcd 0000:00:1a.2: UHCI Host Controller
May 24 20:29:32 ubuntu kernel: [   25.773986] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
May 24 20:29:32 ubuntu kernel: [   25.774007] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ecc0
May 24 20:29:32 ubuntu kernel: [   25.774086] usb usb3: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   25.774102] hub 3-0:1.0: USB hub found
May 24 20:29:32 ubuntu kernel: [   25.774105] hub 3-0:1.0: 2 ports detected
May 24 20:29:32 ubuntu kernel: [   25.877774] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
May 24 20:29:32 ubuntu kernel: [   25.877780] PCI: Setting latency timer of device 0000:00:1d.0 to 64
May 24 20:29:32 ubuntu kernel: [   25.877783] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May 24 20:29:32 ubuntu kernel: [   25.877800] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
May 24 20:29:32 ubuntu kernel: [   25.877820] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ff80
May 24 20:29:32 ubuntu kernel: [   25.877892] usb usb4: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   25.877907] hub 4-0:1.0: USB hub found
May 24 20:29:32 ubuntu kernel: [   25.877910] hub 4-0:1.0: 2 ports detected
May 24 20:29:32 ubuntu kernel: [   25.981601] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
May 24 20:29:32 ubuntu kernel: [   25.981608] PCI: Setting latency timer of device 0000:00:1d.1 to 64
May 24 20:29:32 ubuntu kernel: [   25.981611] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May 24 20:29:32 ubuntu kernel: [   25.981631] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
May 24 20:29:32 ubuntu kernel: [   25.981652] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
May 24 20:29:32 ubuntu kernel: [   25.981745] usb usb5: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   25.981760] hub 5-0:1.0: USB hub found
May 24 20:29:32 ubuntu kernel: [   25.981763] hub 5-0:1.0: 2 ports detected
May 24 20:29:32 ubuntu kernel: [   26.085418] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
May 24 20:29:32 ubuntu kernel: [   26.085426] PCI: Setting latency timer of device 0000:00:1d.2 to 64
May 24 20:29:32 ubuntu kernel: [   26.085429] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May 24 20:29:32 ubuntu kernel: [   26.085450] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
May 24 20:29:32 ubuntu kernel: [   26.085473] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000ff40
May 24 20:29:32 ubuntu kernel: [   26.085566] usb usb6: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   26.085582] hub 6-0:1.0: USB hub found
May 24 20:29:32 ubuntu kernel: [   26.085584] hub 6-0:1.0: 2 ports detected
May 24 20:29:32 ubuntu kernel: [   26.117308] usb 3-2: new full speed USB device using uhci_hcd and address 2
May 24 20:29:32 ubuntu kernel: [   26.190141] ACPI: PCI Interrupt 0000:04:0a.0[A] -> GSI 18 (level, low) -> IRQ 20
May 24 20:29:32 ubuntu kernel: [   26.190276] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 18
May 24 20:29:32 ubuntu kernel: [   26.190283] PCI: Setting latency timer of device 0000:00:1a.7 to 64
May 24 20:29:32 ubuntu kernel: [   26.190285] ehci_hcd 0000:00:1a.7: EHCI Host Controller
May 24 20:29:32 ubuntu kernel: [   26.190301] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
May 24 20:29:32 ubuntu kernel: [   26.194186] ehci_hcd 0000:00:1a.7: debug port 1
May 24 20:29:32 ubuntu kernel: [   26.194191] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
May 24 20:29:32 ubuntu kernel: [   26.194194] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfdac00
May 24 20:29:32 ubuntu kernel: [   26.239792] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f9efb800-f9efbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
May 24 20:29:32 ubuntu kernel: [   26.249574] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 24 20:29:32 ubuntu kernel: [   26.249641] usb usb7: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   26.249659] hub 7-0:1.0: USB hub found
May 24 20:29:32 ubuntu kernel: [   26.249663] hub 7-0:1.0: 6 ports detected
May 24 20:29:32 ubuntu kernel: [   26.352950] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
May 24 20:29:32 ubuntu kernel: [   26.352960] PCI: Setting latency timer of device 0000:00:1d.7 to 64
May 24 20:29:32 ubuntu kernel: [   26.352964] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May 24 20:29:32 ubuntu kernel: [   26.352986] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
May 24 20:29:32 ubuntu kernel: [   26.356870] ehci_hcd 0000:00:1d.7: debug port 1
May 24 20:29:32 ubuntu kernel: [   26.356875] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
May 24 20:29:32 ubuntu kernel: [   26.356878] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xff980800
May 24 20:29:32 ubuntu kernel: [   26.368852] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 24 20:29:32 ubuntu kernel: [   26.368947] usb usb8: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   26.368970] hub 8-0:1.0: USB hub found
May 24 20:29:32 ubuntu kernel: [   26.368974] hub 8-0:1.0: 6 ports detected
May 24 20:29:32 ubuntu kernel: [   26.472745] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 21
May 24 20:29:32 ubuntu kernel: [   26.472780] PCI: Setting latency timer of device 0000:00:1f.2 to 64
May 24 20:29:32 ubuntu kernel: [   26.472792] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
May 24 20:29:32 ubuntu kernel: [   26.472814] ACPI: PCI Interrupt 0000:00:1f.5[C] -> GSI 20 (level, low) -> IRQ 21
May 24 20:29:32 ubuntu kernel: [   26.472843] PCI: Setting latency timer of device 0000:00:1f.5 to 64
May 24 20:29:32 ubuntu kernel: [   26.472851] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
May 24 20:29:32 ubuntu kernel: [   26.475096] ata_piix 0000:00:1f.2: version 2.12
May 24 20:29:32 ubuntu kernel: [   26.475100] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
May 24 20:29:32 ubuntu kernel: [   26.628418] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 21
May 24 20:29:32 ubuntu kernel: [   26.628443] PCI: Setting latency timer of device 0000:00:1f.2 to 64
May 24 20:29:32 ubuntu kernel: [   26.628497] scsi0 : ata_piix
May 24 20:29:32 ubuntu kernel: [   26.628624] scsi1 : ata_piix
May 24 20:29:32 ubuntu kernel: [   26.628644] ata1: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfec0 irq 21
May 24 20:29:32 ubuntu kernel: [   26.628646] ata2: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfec8 irq 21
May 24 20:29:32 ubuntu kernel: [   26.648353] usb 3-2: device not accepting address 2, error -71
May 24 20:29:32 ubuntu kernel: [   26.987846] ata1.00: ATA-8: WDC WD5000AAKS-75YGA0, 12.01C02, max UDMA/133
May 24 20:29:32 ubuntu kernel: [   26.987850] ata1.00: 976773168 sectors, multi 8: LBA48 NCQ (depth 0/32)
May 24 20:29:32 ubuntu kernel: [   26.987879] ata1.01: ATAPI: Optiarc DVD+/-RW AD-5170S, 101B, max UDMA/66
May 24 20:29:32 ubuntu kernel: [   27.004772] ata1.00: configured for UDMA/133
May 24 20:29:32 ubuntu kernel: [   27.175615] ata1.01: configured for UDMA/66
May 24 20:29:32 ubuntu kernel: [   27.199386] usb 7-6: new high speed USB device using ehci_hcd and address 2
May 24 20:29:32 ubuntu kernel: [   27.333992] usb 7-6: configuration #128 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   27.514904] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[8000000a651df07f]
May 24 20:29:32 ubuntu kernel: [   27.650768] ata2.00: ATAPI: TSSTcorpDVD-ROM TS-H353B, D200, max UDMA/33
May 24 20:29:32 ubuntu kernel: [   27.822454] ata2.00: configured for UDMA/33
May 24 20:29:32 ubuntu kernel: [   27.822543] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-7 12.0 PQ: 0 ANSI: 5
May 24 20:29:32 ubuntu kernel: [   27.823524] scsi 0:0:1:0: CD-ROM            Optiarc  DVD+-RW AD-5170S 101B PQ: 0 ANSI: 5
May 24 20:29:32 ubuntu kernel: [   27.824698] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD-ROM TS-H353B D200 PQ: 0 ANSI: 5
May 24 20:29:32 ubuntu kernel: [   27.824775] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
May 24 20:29:32 ubuntu kernel: [   27.978497] ACPI: PCI Interrupt 0000:00:1f.5[C] -> GSI 20 (level, low) -> IRQ 21
May 24 20:29:32 ubuntu kernel: [   27.978525] PCI: Setting latency timer of device 0000:00:1f.5 to 64
May 24 20:29:32 ubuntu kernel: [   27.978561] scsi2 : ata_piix
May 24 20:29:32 ubuntu kernel: [   27.978613] scsi3 : ata_piix
May 24 20:29:32 ubuntu kernel: [   27.978641] ata3: SATA max UDMA/133 cmd 0xfe40 ctl 0xfe50 bmdma 0xfed0 irq 21
May 24 20:29:32 ubuntu kernel: [   27.978644] ata4: SATA max UDMA/133 cmd 0xfe60 ctl 0xfe70 bmdma 0xfed8 irq 21
May 24 20:29:32 ubuntu kernel: [   27.997959] usb 6-1: new low speed USB device using uhci_hcd and address 2
May 24 20:29:32 ubuntu kernel: [   28.168982] usb 6-1: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   28.409225] usb 6-2: new full speed USB device using uhci_hcd and address 3
May 24 20:29:32 ubuntu kernel: [   28.579262] usb 6-2: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   28.585209] hub 6-2:1.0: USB hub found
May 24 20:29:32 ubuntu kernel: [   28.586179] hub 6-2:1.0: 3 ports detected
May 24 20:29:32 ubuntu kernel: [   28.898641] usb 6-2.1: new low speed USB device using uhci_hcd and address 4
May 24 20:29:32 ubuntu kernel: [   28.973122] Driver 'sd' needs updating - please use bus_type methods
May 24 20:29:32 ubuntu kernel: [   28.973170] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
May 24 20:29:32 ubuntu kernel: [   28.973178] sd 0:0:0:0: [sda] Write Protect is off
May 24 20:29:32 ubuntu kernel: [   28.973180] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 24 20:29:32 ubuntu kernel: [   28.973190] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 24 20:29:32 ubuntu kernel: [   28.973229] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
May 24 20:29:32 ubuntu kernel: [   28.973236] sd 0:0:0:0: [sda] Write Protect is off
May 24 20:29:32 ubuntu kernel: [   28.973237] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 24 20:29:32 ubuntu kernel: [   28.973248] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 24 20:29:32 ubuntu kernel: [   28.973251]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May 24 20:29:32 ubuntu kernel: [   28.980462]  sda1 sda2 sda3
May 24 20:29:32 ubuntu kernel: [   28.980545] sd 0:0:0:0: [sda] Attached SCSI disk
May 24 20:29:32 ubuntu kernel: [   28.983766] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 24 20:29:32 ubuntu kernel: [   28.983781] sr 0:0:1:0: Attached scsi generic sg1 type 5
May 24 20:29:32 ubuntu kernel: [   28.983792] scsi 1:0:0:0: Attached scsi generic sg2 type 5
May 24 20:29:32 ubuntu kernel: [   28.985937] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 24 20:29:32 ubuntu kernel: [   28.985939] Uniform CD-ROM driver Revision: 3.20
May 24 20:29:32 ubuntu kernel: [   28.985973] sr 0:0:1:0: Attached scsi CD-ROM sr0
May 24 20:29:32 ubuntu kernel: [   28.992158] sr1: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
May 24 20:29:32 ubuntu kernel: [   28.992197] sr 1:0:0:0: Attached scsi CD-ROM sr1
May 24 20:29:32 ubuntu kernel: [   29.039488] usb 6-2.1: configuration #1 chosen from 1 choice
May 24 20:29:32 ubuntu kernel: [   29.073352] usbcore: registered new interface driver hiddev
May 24 20:29:32 ubuntu kernel: [   29.090540] input: Dell Premium USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb6/6-1/6-1:1.0/input/input1
May 24 20:29:32 ubuntu kernel: [   29.100032] input,hidraw0: USB HID v1.11 Mouse [Dell Premium USB Optical Mouse] on usb-0000:00:1d.2-1
May 24 20:29:32 ubuntu kernel: [   29.114488] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2.1/6-2.1:1.0/input/input2
May 24 20:29:32 ubuntu kernel: [   29.136471] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
May 24 20:29:32 ubuntu kernel: [   29.171226] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2.1/6-2.1:1.1/input/input3
May 24 20:29:32 ubuntu kernel: [   29.179905] input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
May 24 20:29:32 ubuntu kernel: [   29.179920] usbcore: registered new interface driver usbhid
May 24 20:29:32 ubuntu kernel: [   29.179923] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
May 24 20:29:32 ubuntu kernel: [   29.352882] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
May 24 20:29:32 ubuntu kernel: [   29.353254] SGI XFS Quota Management subsystem
May 24 20:29:32 ubuntu kernel: [   29.357558] JFS: nTxBlock = 8192, nTxLock = 65536
May 24 20:29:32 ubuntu kernel: [   30.477983] loop: module loaded
May 24 20:29:32 ubuntu kernel: [   30.575223] ISO 9660 Extensions: Microsoft Joliet Level 3
May 24 20:29:32 ubuntu kernel: [   30.579986] ISO 9660 Extensions: RRIP_1991A
May 24 20:29:32 ubuntu kernel: [   30.586995] Registering unionfs 1.4
May 24 20:29:32 ubuntu kernel: [   30.586996] unionfs: debugging is not enabled
May 24 20:29:32 ubuntu kernel: [   30.616423] squashfs: version 3.3 (2007/10/31) Phillip Lougher
May 24 20:29:32 ubuntu kernel: [   44.375686] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 24 20:29:32 ubuntu kernel: [   44.423932] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 24 20:29:32 ubuntu kernel: [   44.731734] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
May 24 20:29:32 ubuntu kernel: [   44.731737] e1000e: Copyright (c) 1999-2007 Intel Corporation.
May 24 20:29:32 ubuntu kernel: [   44.731781] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 21 (level, low) -> IRQ 22
May 24 20:29:32 ubuntu kernel: [   44.731789] PCI: Setting latency timer of device 0000:00:19.0 to 64
May 24 20:29:32 ubuntu kernel: [   44.761024] input: Power Button (FF) as /devices/virtual/input/input4
May 24 20:29:32 ubuntu kernel: [   44.785112] ACPI: Power Button (FF) [PWRF]
May 24 20:29:32 ubuntu kernel: [   44.785166] input: Power Button (CM) as /devices/virtual/input/input5
May 24 20:29:32 ubuntu kernel: [   44.828492] ACPI: Power Button (CM) [VBTN]
May 24 20:29:32 ubuntu kernel: [   44.846891] input: PC Speaker as /devices/platform/pcspkr/input/input6
May 24 20:29:32 ubuntu kernel: [   44.870493] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1d:09:28:2b:56
May 24 20:29:32 ubuntu kernel: [   44.870496] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
May 24 20:29:32 ubuntu kernel: [   44.870518] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: 1031ff-0ff
May 24 20:29:32 ubuntu kernel: [   44.900282] iTCO_vendor_support: vendor-support=0
May 24 20:29:32 ubuntu kernel: [   45.035698] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
May 24 20:29:32 ubuntu kernel: [   45.080183] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0860)
May 24 20:29:32 ubuntu kernel: [   45.080213] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
May 24 20:29:32 ubuntu kernel: [   45.080239] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
May 24 20:29:32 ubuntu kernel: [   45.167607] Linux agpgart interface v0.102
May 24 20:29:32 ubuntu kernel: [   45.442935] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
May 24 20:29:32 ubuntu kernel: [   45.442950] PCI: Setting latency timer of device 0000:00:1b.0 to 64
May 24 20:29:32 ubuntu kernel: [   46.672964] ip_tables: (C) 2000-2006 Netfilter Core Team
May 24 20:29:32 ubuntu kernel: [   47.146418] No dock devices found.
May 24 20:29:32 ubuntu NetworkManager: <info>  starting... 
May 24 20:29:32 ubuntu avahi-daemon[8263]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
May 24 20:29:32 ubuntu avahi-daemon[8263]: Successfully dropped root privileges.
May 24 20:29:32 ubuntu avahi-daemon[8263]: avahi-daemon 0.6.22 starting up.
May 24 20:29:32 ubuntu avahi-daemon[8263]: Successfully called chroot().
May 24 20:29:32 ubuntu avahi-daemon[8263]: Successfully dropped remaining capabilities.
May 24 20:29:32 ubuntu avahi-daemon[8264]: chroot.c: open() failed: No such file or directory
May 24 20:29:32 ubuntu avahi-daemon[8263]: Failed to open /etc/resolv.conf: Invalid argument
May 24 20:29:32 ubuntu avahi-daemon[8263]: No service file found in /etc/avahi/services.
May 24 20:29:32 ubuntu avahi-daemon[8263]: Network interface enumeration completed.
May 24 20:29:32 ubuntu avahi-daemon[8263]: Registering HINFO record with values 'I686'/'LINUX'.
May 24 20:29:32 ubuntu avahi-daemon[8263]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3770759528.
May 24 20:29:32 ubuntu kernel: [   48.377332] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 24 20:29:32 ubuntu kernel: [   48.377337] apm: disabled - APM is not SMP safe.
May 24 20:29:32 ubuntu kernel: [   48.464473] lp: driver loaded but no devices found
May 24 20:29:32 ubuntu kernel: [   48.519696] ppdev: user-space parallel port driver
May 24 20:29:33 ubuntu dhcdbd: Started up.
May 24 20:29:33 ubuntu hcid[8565]: Bluetooth HCI daemon
May 24 20:29:33 ubuntu NetworkManager: <info>  eth0: Device is fully-supported using driver 'e1000e'. 
May 24 20:29:33 ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 24 20:29:33 ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 24 20:29:33 ubuntu NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
May 24 20:29:33 ubuntu NetworkManager: <info>  Deactivating device eth0. 
May 24 20:29:34 ubuntu NetworkManager: <debug> [1211660974.014493] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_ROM_TS_H353B'). 
May 24 20:29:34 ubuntu kernel: [   49.845852] Bluetooth: Core ver 2.11
May 24 20:29:34 ubuntu kernel: [   49.846140] NET: Registered protocol family 31
May 24 20:29:34 ubuntu kernel: [   49.846143] Bluetooth: HCI device and connection manager initialized
May 24 20:29:34 ubuntu kernel: [   49.846146] Bluetooth: HCI socket layer initialized
May 24 20:29:34 ubuntu hcid[8565]: Starting SDP server
May 24 20:29:34 ubuntu NetworkManager: <debug> [1211660974.050341] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 24 20:29:34 ubuntu kernel: [   49.917833] Bluetooth: L2CAP ver 2.9
May 24 20:29:34 ubuntu kernel: [   49.917836] Bluetooth: L2CAP socket layer initialized
May 24 20:29:34 ubuntu hcid[8565]: Created local server at unix:abstract=/var/run/dbus-kF9GFkLwot,guid=23a8d9d080ff73cfb1293c6c48387aae
May 24 20:29:34 ubuntu audio[8597]: Bluetooth Audio daemon
May 24 20:29:34 ubuntu audio[8597]: Unix socket created: 5
May 24 20:29:34 ubuntu audio[8597]: audio.conf: Key file does not have key 'Enable'
May 24 20:29:34 ubuntu audio[8597]: audio.conf: Key file does not have key 'Disable'
May 24 20:29:34 ubuntu input[8600]: Bluetooth Input daemon
May 24 20:29:34 ubuntu input[8600]: Registered input manager path:/org/bluez/input
May 24 20:29:34 ubuntu kernel: [   49.970613] Bluetooth: RFCOMM socket layer initialized
May 24 20:29:34 ubuntu kernel: [   49.970625] Bluetooth: RFCOMM TTY layer initialized
May 24 20:29:34 ubuntu kernel: [   49.970627] Bluetooth: RFCOMM ver 1.8
May 24 20:29:34 ubuntu audio[8597]: add_service_record: got record id 0x10000
May 24 20:29:34 ubuntu audio[8597]: audio.conf: Key file does not have key 'Disable'
May 24 20:29:34 ubuntu audio[8597]: audio.conf: Key file does not have group 'A2DP'
May 24 20:29:34 ubuntu last message repeated 3 times
May 24 20:29:34 ubuntu audio[8597]: SEP 0x806d248 registered: type:0 codec:0 seid:1
May 24 20:29:34 ubuntu audio[8597]: add_service_record: got record id 0x10001
May 24 20:29:34 ubuntu audio[8597]: add_service_record: got record id 0x10002
May 24 20:29:34 ubuntu audio[8597]: add_service_record: got record id 0x10003
May 24 20:29:34 ubuntu audio[8597]: Registered manager path:/org/bluez/audio
May 24 20:29:35 ubuntu kernel: [   51.512557] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
May 24 20:29:35 ubuntu kernel: [   51.512562] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
May 24 20:29:35 ubuntu NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
May 24 20:29:35 ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
May 24 20:29:35 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 24 20:29:35 ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
May 24 20:29:35 ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) started... 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May 24 20:29:35 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May 24 20:29:35 ubuntu kernel: [   51.615727] NET: Registered protocol family 10
May 24 20:29:35 ubuntu kernel: [   51.615910] lo: Disabled Privacy Extensions
May 24 20:29:36 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May 24 20:29:36 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 24 20:29:36 ubuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
May 24 20:29:36 ubuntu avahi-daemon[8263]: Registering new address record for fe80::21d:9ff:fe28:2b56 on eth0.*.
May 24 20:29:37 ubuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
May 24 20:29:37 ubuntu kernel: [   53.729649] NET: Registered protocol family 17
May 24 20:29:39 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 24 20:29:39 ubuntu dhclient: DHCPOFFER of 192.168.1.3 from 192.168.1.1
May 24 20:29:39 ubuntu dhclient: DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
May 24 20:29:39 ubuntu dhclient: DHCPACK of 192.168.1.3 from 192.168.1.1
May 24 20:29:39 ubuntu avahi-daemon[8263]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.3.
May 24 20:29:39 ubuntu avahi-daemon[8263]: New relevant interface eth0.IPv4 for mDNS.
May 24 20:29:39 ubuntu avahi-daemon[8263]: Registering new address record for 192.168.1.3 on eth0.IPv4.
May 24 20:29:39 ubuntu dhclient: bound to 192.168.1.3 -- renewal in 1754 seconds.
May 24 20:29:39 ubuntu NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
May 24 20:29:39 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May 24 20:29:39 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May 24 20:29:39 ubuntu ubiquity[8761]: Ubiquity 1.8.7
May 24 20:29:40 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
May 24 20:29:40 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 24 20:29:40 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 24 20:29:40 ubuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May 24 20:29:40 ubuntu NetworkManager: <info>    address 192.168.1.3 
May 24 20:29:40 ubuntu NetworkManager: <info>    netmask 255.255.255.0 
May 24 20:29:40 ubuntu NetworkManager: <info>    broadcast 192.168.1.255 
May 24 20:29:40 ubuntu NetworkManager: <info>    gateway 192.168.1.1 
May 24 20:29:40 ubuntu NetworkManager: <info>    nameserver 192.168.1.1 
May 24 20:29:40 ubuntu NetworkManager: <info>    hostname 'ubuntu' 
May 24 20:29:40 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
May 24 20:29:40 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 24 20:29:40 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May 24 20:29:40 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May 24 20:29:40 ubuntu avahi-daemon[8263]: Withdrawing address record for 192.168.1.3 on eth0.
May 24 20:29:40 ubuntu avahi-daemon[8263]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.3.
May 24 20:29:40 ubuntu avahi-daemon[8263]: Interface eth0.IPv4 no longer relevant for mDNS.
May 24 20:29:40 ubuntu avahi-daemon[8263]: Withdrawing address record for fe80::21d:9ff:fe28:2b56 on eth0.
May 24 20:29:40 ubuntu avahi-daemon[8263]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.3.
May 24 20:29:40 ubuntu avahi-daemon[8263]: New relevant interface eth0.IPv4 for mDNS.
May 24 20:29:40 ubuntu avahi-daemon[8263]: Registering new address record for 192.168.1.3 on eth0.IPv4.
May 24 20:29:41 ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
May 24 20:29:41 ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May 24 20:29:41 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated. 
May 24 20:29:41 ubuntu NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
May 24 20:29:41 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May 24 20:29:42 ubuntu avahi-daemon[8263]: Registering new address record for fe80::21d:9ff:fe28:2b56 on eth0.*.
May 24 20:29:42 ubuntu ubiquity[8761]: log-output -t ubiquity laptop-detect
May 24 20:29:42 ubuntu ubiquity[8761]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
May 24 20:29:44 ubuntu ubiquity[8761]: switched to page stepLanguage
May 24 20:29:44 ubuntu localechooser: info: Locale has been preseeded to en_AU.UTF-8
May 24 20:29:44 ubuntu localechooser: info: Set languagechooser/language-name = 'English'
May 24 20:29:44 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'AU'
May 24 20:29:44 ubuntu localechooser: info: Set debian-installer/locale = 'en_AU.UTF-8'
May 24 20:29:44 ubuntu localechooser: info: LANGNAME=English
May 24 20:29:44 ubuntu localechooser: info: line=English;0;en;US;en_US.UTF-8;UTF-8;;kbd=lat0-sun16(utf8)
May 24 20:29:44 ubuntu localechooser: info: Set debian-installer/language = 'en'
May 24 20:29:44 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
May 24 20:29:44 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
May 24 20:29:44 ubuntu localechooser: info: Set debian-installer/country = 'US'
May 24 20:29:44 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
May 24 20:29:44 ubuntu localechooser: info: Set debconf/language = 'en'
May 24 20:29:44 ubuntu localechooser: info: Set debian-installer/country = 'AU'
May 24 20:29:44 ubuntu localechooser: info: Set debian-installer/locale = 'en_AU.UTF-8'
May 24 20:29:45 ubuntu ubiquity[8761]: debconffilter_done: Language (current: Language)
May 24 20:29:45 ubuntu ubiquity[8761]: Step_before = stepLanguage
May 24 20:29:46 ubuntu ubiquity[8761]: switched to page stepLocation
May 24 20:29:49 ubuntu ntpdate[8814]: step time server 91.189.94.4 offset -28680.100152 sec
May 24 12:31:51 ubuntu kernel: [   67.157345] eth0: no IPv6 routers present
May 24 12:31:58 ubuntu ubiquity[8761]: debconffilter_done: Timezone (current: Timezone)
May 24 12:31:58 ubuntu ubiquity[8761]: Step_before = stepLocation
May 24 12:31:59 ubuntu ubiquity[8761]: log-output -t ubiquity setxkbmap -model pc105 -layout us
May 24 12:31:59 ubuntu ubiquity: Your console font configuration will be updated the next time your system
May 24 12:31:59 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
May 24 12:31:59 ubuntu ubiquity[8761]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
May 24 12:31:59 ubuntu ubiquity[8761]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
May 24 12:31:59 ubuntu ubiquity[8761]: Step_before = stepLocation
May 24 12:32:10 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:32:10 ubuntu ntfsresize: Device name        : /dev/sda2
May 24 12:32:10 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:32:10 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:32:10 ubuntu ntfsresize: Current volume size: 16106123776 bytes (16107 MB)
May 24 12:32:10 ubuntu ntfsresize: Current device size: 16106127360 bytes (16107 MB)
May 24 12:32:10 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:32:10 ubuntu ntfsresize: Accounting clusters ...
May 24 12:32:10 ubuntu ntfsresize: Space in use       : 4492 MB (27.9%)
May 24 12:32:10 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:32:10 ubuntu ntfsresize: You might resize at 4491632640 bytes or 4492 MB (freeing 11615 MB).
May 24 12:32:10 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:32:15 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:32:15 ubuntu ntfsresize: Device name        : /dev/sda3
May 24 12:32:15 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:32:15 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:32:15 ubuntu ntfsresize: Current volume size: 483950326272 bytes (483951 MB)
May 24 12:32:15 ubuntu ntfsresize: Current device size: 483950329856 bytes (483951 MB)
May 24 12:32:15 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:32:15 ubuntu ntfsresize: Accounting clusters ...
May 24 12:32:15 ubuntu ntfsresize: Space in use       : 138475 MB (28.6%)
May 24 12:32:15 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:32:15 ubuntu ntfsresize: You might resize at 138474127360 bytes or 138475 MB (freeing 345476 MB).
May 24 12:32:15 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:32:16 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:32:16 ubuntu ntfsresize: Device name        : /dev/sda3
May 24 12:32:16 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:32:16 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:32:16 ubuntu ntfsresize: Current volume size: 483950326272 bytes (483951 MB)
May 24 12:32:16 ubuntu ntfsresize: Current device size: 483950329856 bytes (483951 MB)
May 24 12:32:16 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:32:16 ubuntu ntfsresize: Accounting clusters ...
May 24 12:32:16 ubuntu ntfsresize: Space in use       : 138475 MB (28.6%)
May 24 12:32:16 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:32:16 ubuntu ntfsresize: You might resize at 138474127360 bytes or 138475 MB (freeing 345476 MB).
May 24 12:32:16 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:32:16 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:32:16 ubuntu ntfsresize: Device name        : /dev/sda2
May 24 12:32:16 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:32:16 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:32:16 ubuntu ntfsresize: Current volume size: 16106123776 bytes (16107 MB)
May 24 12:32:16 ubuntu ntfsresize: Current device size: 16106127360 bytes (16107 MB)
May 24 12:32:16 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:32:16 ubuntu ntfsresize: Accounting clusters ...
May 24 12:32:16 ubuntu ntfsresize: Space in use       : 4492 MB (27.9%)
May 24 12:32:16 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:32:16 ubuntu ntfsresize: You might resize at 4491632640 bytes or 4492 MB (freeing 11615 MB).
May 24 12:32:16 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:32:18 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:32:18 ubuntu ntfsresize: Device name        : /dev/sda3
May 24 12:32:18 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:32:18 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:32:18 ubuntu ntfsresize: Current volume size: 483950326272 bytes (483951 MB)
May 24 12:32:18 ubuntu ntfsresize: Current device size: 483950329856 bytes (483951 MB)
May 24 12:32:18 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:32:18 ubuntu ntfsresize: Accounting clusters ...
May 24 12:32:18 ubuntu ntfsresize: Space in use       : 138475 MB (28.6%)
May 24 12:32:18 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:32:18 ubuntu ntfsresize: You might resize at 138474127360 bytes or 138475 MB (freeing 345476 MB).
May 24 12:32:18 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:32:18 ubuntu ubiquity[8761]: debconffilter_done: Partman (current: Partman)
May 24 12:32:18 ubuntu ubiquity[8761]: dbfilter_handle_status: ('Partman', 10)
May 24 12:33:26 ubuntu ubiquity[8761]: dbfilter_handle_status: response 2
May 24 12:33:37 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:33:37 ubuntu ntfsresize: Device name        : /dev/sda2
May 24 12:33:37 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:33:37 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:33:37 ubuntu ntfsresize: Current volume size: 16106123776 bytes (16107 MB)
May 24 12:33:37 ubuntu ntfsresize: Current device size: 16106127360 bytes (16107 MB)
May 24 12:33:37 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:33:37 ubuntu ntfsresize: Accounting clusters ...
May 24 12:33:37 ubuntu ntfsresize: Space in use       : 4492 MB (27.9%)
May 24 12:33:37 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:33:37 ubuntu ntfsresize: You might resize at 4491632640 bytes or 4492 MB (freeing 11615 MB).
May 24 12:33:37 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:33:38 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:33:38 ubuntu ntfsresize: Device name        : /dev/sda3
May 24 12:33:38 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:33:38 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:33:38 ubuntu ntfsresize: Current volume size: 483950326272 bytes (483951 MB)
May 24 12:33:38 ubuntu ntfsresize: Current device size: 483950329856 bytes (483951 MB)
May 24 12:33:38 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:33:38 ubuntu ntfsresize: Accounting clusters ...
May 24 12:33:38 ubuntu ntfsresize: Space in use       : 138475 MB (28.6%)
May 24 12:33:38 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:33:38 ubuntu ntfsresize: You might resize at 138474127360 bytes or 138475 MB (freeing 345476 MB).
May 24 12:33:38 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:33:40 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:33:40 ubuntu ntfsresize: Device name        : /dev/sda3
May 24 12:33:40 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:33:40 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:33:40 ubuntu ntfsresize: Current volume size: 483950326272 bytes (483951 MB)
May 24 12:33:40 ubuntu ntfsresize: Current device size: 483950329856 bytes (483951 MB)
May 24 12:33:40 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:33:40 ubuntu ntfsresize: Accounting clusters ...
May 24 12:33:40 ubuntu ntfsresize: Space in use       : 138475 MB (28.6%)
May 24 12:33:40 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:33:40 ubuntu ntfsresize: You might resize at 138474127360 bytes or 138475 MB (freeing 345476 MB).
May 24 12:33:40 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:33:40 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:33:40 ubuntu ntfsresize: Device name        : /dev/sda2
May 24 12:33:40 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:33:40 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:33:40 ubuntu ntfsresize: Current volume size: 16106123776 bytes (16107 MB)
May 24 12:33:40 ubuntu ntfsresize: Current device size: 16106127360 bytes (16107 MB)
May 24 12:33:40 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:33:40 ubuntu ntfsresize: Accounting clusters ...
May 24 12:33:40 ubuntu ntfsresize: Space in use       : 4492 MB (27.9%)
May 24 12:33:40 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:33:40 ubuntu ntfsresize: You might resize at 4491632640 bytes or 4492 MB (freeing 11615 MB).
May 24 12:33:40 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:33:41 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:33:41 ubuntu ntfsresize: Device name        : /dev/sda3
May 24 12:33:41 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:33:41 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:33:41 ubuntu ntfsresize: Current volume size: 483950326272 bytes (483951 MB)
May 24 12:33:41 ubuntu ntfsresize: Current device size: 483950329856 bytes (483951 MB)
May 24 12:33:41 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:33:41 ubuntu ntfsresize: Accounting clusters ...
May 24 12:33:41 ubuntu ntfsresize: Space in use       : 138475 MB (28.6%)
May 24 12:33:41 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:33:41 ubuntu ntfsresize: You might resize at 138474127360 bytes or 138475 MB (freeing 345476 MB).
May 24 12:33:41 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:33:42 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:33:42 ubuntu ntfsresize: Device name        : /dev/sda3
May 24 12:33:42 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:33:42 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:33:42 ubuntu ntfsresize: Current volume size: 483950326272 bytes (483951 MB)
May 24 12:33:42 ubuntu ntfsresize: Current device size: 483950329856 bytes (483951 MB)
May 24 12:33:42 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:33:42 ubuntu ntfsresize: Accounting clusters ...
May 24 12:33:42 ubuntu ntfsresize: Space in use       : 138475 MB (28.6%)
May 24 12:33:42 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:33:42 ubuntu ntfsresize: You might resize at 138474127360 bytes or 138475 MB (freeing 345476 MB).
May 24 12:33:42 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:33:43 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:33:43 ubuntu ntfsresize: Device name        : /dev/sda2
May 24 12:33:43 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:33:43 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:33:43 ubuntu ntfsresize: Current volume size: 16106123776 bytes (16107 MB)
May 24 12:33:43 ubuntu ntfsresize: Current device size: 16106127360 bytes (16107 MB)
May 24 12:33:43 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:33:43 ubuntu ntfsresize: Accounting clusters ...
May 24 12:33:43 ubuntu ntfsresize: Space in use       : 4492 MB (27.9%)
May 24 12:33:43 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:33:43 ubuntu ntfsresize: You might resize at 4491632640 bytes or 4492 MB (freeing 11615 MB).
May 24 12:33:43 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:33:44 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:33:44 ubuntu ntfsresize: Device name        : /dev/sda3
May 24 12:33:44 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:33:44 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:33:44 ubuntu ntfsresize: Current volume size: 483950326272 bytes (483951 MB)
May 24 12:33:44 ubuntu ntfsresize: Current device size: 483950329856 bytes (483951 MB)
May 24 12:33:44 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:33:44 ubuntu ntfsresize: Accounting clusters ...
May 24 12:33:44 ubuntu ntfsresize: Space in use       : 138475 MB (28.6%)
May 24 12:33:44 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:33:44 ubuntu ntfsresize: You might resize at 138474127360 bytes or 138475 MB (freeing 345476 MB).
May 24 12:33:44 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:33:44 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
May 24 12:33:44 ubuntu ubiquity[8761]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
May 24 12:33:44 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
May 24 12:33:44 ubuntu ubiquity[8761]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^xserver-xorg/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
May 24 12:33:45 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
May 24 12:33:45 ubuntu ntfsresize: Device name        : /dev/sda3
May 24 12:33:45 ubuntu ntfsresize: NTFS volume version: 3.1
May 24 12:33:45 ubuntu ntfsresize: Cluster size       : 4096 bytes
May 24 12:33:45 ubuntu ntfsresize: Current volume size: 483950326272 bytes (483951 MB)
May 24 12:33:45 ubuntu ntfsresize: Current device size: 483950329856 bytes (483951 MB)
May 24 12:33:45 ubuntu ntfsresize: Checking filesystem consistency ...
May 24 12:33:45 ubuntu ntfsresize: Accounting clusters ...
May 24 12:33:45 ubuntu ntfsresize: Space in use       : 138475 MB (28.6%)
May 24 12:33:45 ubuntu ntfsresize: Collecting resizing constraints ...
May 24 12:33:45 ubuntu ntfsresize: You might resize at 138474127360 bytes or 138475 MB (freeing 345476 MB).
May 24 12:33:45 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
May 24 12:33:46 ubuntu /usr/sbin/cron[11074]: (CRON) INFO (pidfile fd = 3)
May 24 12:33:46 ubuntu /usr/sbin/cron[11079]: (CRON) STARTUP (fork ok)
May 24 12:33:46 ubuntu /usr/sbin/cron[11079]: (CRON) INFO (Running @reboot jobs)
May 24 12:33:47 ubuntu gdm[10496]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
May 24 12:33:47 ubuntu gdm[10496]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
May 24 12:33:47 ubuntu gdm[10496]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
May 24 12:33:48 ubuntu pulseaudio[13817]: pid.c: Stale PID file, overwriting.
May 24 12:33:49 ubuntu hcid[8565]: Default passkey agent (:1.24, /org/bluez/passkey) registered
May 24 12:33:49 ubuntu hcid[8565]: Default authorization agent (:1.24, /org/bluez/auth) registered
May 24 12:33:50 ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
May 24 12:33:50 ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by glaivekiddo on 2008-05-24
took a screenshot of the window popped up when i type sudo gparted and attached it to this post

---

### Post by Forlong on 2008-05-24
I'm sorry, I don't have enough knowledge about this.

This seems like a bug to me, you should consider filing a bugreport at [http://bugs.launchpad.net/ubuntu](http://bugs.launchpad.net/ubuntu) about this. The guys there should be able to tell you how to work around this as well.

---

