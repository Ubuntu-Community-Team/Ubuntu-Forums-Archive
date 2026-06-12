---
title: "Ubuntu 10.04 LTS OnLine Upgrade; UDEVD-WORK.... mount request?"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by tecknomage on 2010-05-03
Just completed the _online_ update of **Ubuntu 10 -> 10.04 LTS**

One problem, on boot keeps trying to mount "**UDEVD-WORK....**" (*rest of line disappears before I can write down*), which fails because it does not exist.

How do I stop this?

---

### Post by tecknomage on 2010-05-03
**UPDATE**

The drive mount = **/dev/null**

Which does not exist.

---

### Post by frantid on 2010-05-03
check your /etc/fstab file, there have been others reporting similar issues.

---

### Post by tecknomage on 2010-05-03
> **frantid said:**
> check your /etc/fstab file, there have been others reporting similar issues.

OK, found it.  **This is the text (*pasted*)**:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c80a7137-7c88-4ebe-b8f9-aef2a9394730 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=259e0d6e-4a8f-41e4-a7ba-13d8a7109b49 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

-----------------

**Now what?**

Commenting out the last line (/dev/scd0) did not fix.

---

### Post by tecknomage on 2010-05-04
UPDATE

Used Termainal command** ls /dev/disk/by-uuid -l** (*suggested by another thread*) to get the correct drive UUIDs.

Confirmed the UUIDs iin **fstab** file are correct.

What else could be wrong?

---

### Post by frantid on 2010-05-04
try adding 
```
defaults,relatime,
```to etc/fstab before the errors=remout....

make sure of the space between ext4 and include the comma before errors

---

### Post by tecknomage on 2010-05-04
> **frantid said:**
> try adding 
```
defaults,relatime,
```to etc/fstab before the errors=remout....

make sure of the space between ext4 and include the comma before errors

Was **relatime** a typo? Should be **realtime**?

Thanks, but that did not fix the problem, in fact made things worst. Caused a mount error lock-up.

Had to boot to **Live CD**, enable root and edit the **fstab file**. Luckily I made a backup of the original.

---

### Post by frantid on 2010-05-04
No that wasn't a typo -- my ideas seem to have no success here.

Hopefully, someone else will come along with a few more ideas.

good luck.

---

### Post by tecknomage on 2010-05-05
**UPDATE**

:???:  **The problem has gone away on its own!**

I waited through several boots in the last 30hrs.  No failed mounting of **/dev/null**.

Go figure   ):P

---

### Post by tecknomage on 2010-05-05
**UPDATE**

](*,) "They're back."  Well several boots yesterday did NOT have the **/dev/null** mount failure, but just now, it's back.

So,** I still need a fix**  :cry:

Could it be the**     errors=remount-ro** ?

And what can I do that would NOT cause a boot lock-up like the last time I edited fstab.

The other question is, where does **/dev/null** come from, how could this exist at all?  Reminder, **I have confirmed that the drive UUIDs in fstab are correct**.

---

### Post by tecknomage on 2010-05-05
After reading posts on fstab in LaunchPad I tried the following as a fix:

# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# / was on /dev/sda1 during installation 
**[COLOR=Red]/dev/sda1    ext4    realtime,errors=remount-ro 0       1[/COLOR] **
# swap was on /dev/sda5 during installation 
[COLOR=Red]**/dev/sda5  none            swap    sw              0       0 **[/COLOR]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

This did NOT work.  Still gets the **/etc/null** mount failure  ](*,)

---

### Post by iskarion on 2010-05-05
I don't think this is related to fstab settings. I'm experiencing the same problem and did already try to change many fstab options to no avail.
Also I saw posts on this in other forums from users with quite different harddrive/hardware configurations and therefore probably also different fstab setup.

Edit: do you have AHCI enabled? Maybe it's just a coincidence, but on the computer (fresh Kubuntu 10.04 install) I'm getting this udevd-work.../dev/null error, AHCI is enabled. On another computer (upgrade from Kubuntu 9.10 to 10.04) where AHCI is not active I'm not experiencing this problem.

---

### Post by mikewhatever on 2010-05-05
```
dmesg > ~/Desktop/dmesg.txt
```

Then look for dmesg.txt on the desktop and attach the file to your next post. This way, those interested will be able to see those error messages in full.

---

### Post by tecknomage on 2010-05-05
**dmesg.txt**........

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007d6a1000 (usable)
[    0.000000]  BIOS-e820: 000000007d6a1000 - 000000007d6a7000 (reserved)
[    0.000000]  BIOS-e820: 000000007d6a7000 - 000000007d7bb000 (usable)
[    0.000000]  BIOS-e820: 000000007d7bb000 - 000000007d80f000 (reserved)
[    0.000000]  BIOS-e820: 000000007d80f000 - 000000007d908000 (usable)
[    0.000000]  BIOS-e820: 000000007d908000 - 000000007db0f000 (reserved)
[    0.000000]  BIOS-e820: 000000007db0f000 - 000000007db18000 (usable)
[    0.000000]  BIOS-e820: 000000007db18000 - 000000007db1f000 (reserved)
[    0.000000]  BIOS-e820: 000000007db1f000 - 000000007db64000 (usable)
[    0.000000]  BIOS-e820: 000000007db64000 - 000000007db9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007db9f000 - 000000007dc00000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007dc00000 - 000000007de00000 (reserved)
[    0.000000]  BIOS-e820: 000000007e000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7db64 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 07E000000 mask FFE000000 uncachable
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 07DC00000 mask FFFC00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d400 (usable)
[    0.000000]  modified: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007d6a1000 (usable)
[    0.000000]  modified: 000000007d6a1000 - 000000007d6a7000 (reserved)
[    0.000000]  modified: 000000007d6a7000 - 000000007d7bb000 (usable)
[    0.000000]  modified: 000000007d7bb000 - 000000007d80f000 (reserved)
[    0.000000]  modified: 000000007d80f000 - 000000007d908000 (usable)
[    0.000000]  modified: 000000007d908000 - 000000007db0f000 (reserved)
[    0.000000]  modified: 000000007db0f000 - 000000007db18000 (usable)
[    0.000000]  modified: 000000007db18000 - 000000007db1f000 (reserved)
[    0.000000]  modified: 000000007db1f000 - 000000007db64000 (usable)
[    0.000000]  modified: 000000007db64000 - 000000007db9f000 (ACPI NVS)
[    0.000000]  modified: 000000007db9f000 - 000000007dc00000 (ACPI data)
[    0.000000]  modified: 000000007dc00000 - 000000007de00000 (reserved)
[    0.000000]  modified: 000000007e000000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37858000 - 37fef2c0
[    0.000000] Allocated new RAMDISK: 008de000 - 010752c0
[    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fef2bf to 008de000 - 010752bf
[    0.000000] ACPI: RSDP 000f7150 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7dbf90e2 00064 (v01 MSTEST TESTONLY 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7dbe5000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7dbea000 05AB0 (v02 Intel  CANTIGA  06040000 INTL 20050624)
[    0.000000] ACPI: FACS 7db9efc0 00040
[    0.000000] ACPI: HPET 7dbfed86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7dbfedbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 7dbfedfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: SLIC 7dbfee62 00176 (v01 MSTEST TESTONLY 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7dbe9000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7dbe8000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7dbe7000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1123MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000009d400 - 0000100000]    BIOS reserved ==> [000009d400 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd28c]              BRK ==> [00008da000 - 00008dd28c]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008de000 - 00010752c0]      NEW RAMDISK ==> [00008de000 - 00010752c0]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f71e0] f71e0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007db64
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007d6a1
[    0.000000]     0: 0x0007d6a7 -> 0x0007d7bb
[    0.000000]     0: 0x0007d80f -> 0x0007d908
[    0.000000]     0: 0x0007db0f -> 0x0007db18
[    0.000000]     0: 0x0007db1f -> 0x0007db64
[    0.000000] On node 0 totalpages: 514185
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1077200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2247 pages used for memmap
[    0.000000]   HighMem zone: 284727 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 510162
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=c80a7137-7c88-4ebe-b8f9-aef2a9394730 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10298000 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007db64)
[    0.000000] Memory: 2012816k/2059664k available (4673k kernel code, 42960k reserved, 2122k data, 656k init, 1147896k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2161.326 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4322.65 BogoMIPS (lpj=8645304)
[    0.004022] Security Framework initialized
[    0.004044] AppArmor: AppArmor initialized
[    0.004051] Mount-cache hash table entries: 512
[    0.004183] Initializing cgroup subsys ns
[    0.004187] Initializing cgroup subsys cpuacct
[    0.004192] Initializing cgroup subsys memory
[    0.004199] Initializing cgroup subsys devices
[    0.004201] Initializing cgroup subsys freezer
[    0.004203] Initializing cgroup subsys net_cls
[    0.004223] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004225] CPU: L2 cache: 1024K
[    0.004228] CPU: Physical Processor ID: 0
[    0.004230] CPU: Processor Core ID: 0
[    0.004234] mce: CPU supports 6 MCE banks
[    0.004243] CPU0: Thermal monitoring enabled (TM1)
[    0.004246] using mwait in idle threads.
[    0.004253] Performance Events: Core2 events, Intel PMU driver.
[    0.004262] ... version:                2
[    0.004264] ... bit width:              40
[    0.004265] ... generic registers:      2
[    0.004267] ... value mask:             000000ffffffffff
[    0.004269] ... max period:             000000007fffffff
[    0.004271] ... fixed-purpose events:   3
[    0.004272] ... event mask:             0000000700000003
[    0.004277] Checking 'hlt' instruction... OK.
[    0.022556] ACPI: Core revision 20090903
[    0.033747] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.033752] ftrace: allocating 21771 entries in 43 pages
[    0.036064] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036415] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.079224] CPU0: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz stepping 0d
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 1024K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM1)
[    0.164055] CPU1: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz stepping 0d
[    0.164067] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168019] Brought up 2 CPUs
[    0.168022] Total of 2 processors activated (8645.16 BogoMIPS).
[    0.168371] CPU0 attaching sched-domain:
[    0.168375]  domain 0: span 0-1 level MC
[    0.168377]   groups: 0 1
[    0.168383] CPU1 attaching sched-domain:
[    0.168385]  domain 0: span 0-1 level MC
[    0.168387]   groups: 1 0
[    0.168486] devtmpfs: initialized
[    0.168486] regulator: core version 0.5
[    0.168486] Time: 19:47:27  Date: 05/05/10
[    0.168486] NET: Registered protocol family 16
[    0.168486] Trying to unpack rootfs image as initramfs...
[    0.168486] EISA bus registered
[    0.168486] ACPI: bus type pci registered
[    0.168486] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168486] PCI: MCFG area at e0000000 reserved in E820
[    0.168486] PCI: Using MMCONFIG for extended config space
[    0.168486] PCI: Using configuration type 1 for base access
[    0.172141] bio: create slab <bio-0> at 0
[    0.173289] ACPI: EC: Look up EC in DSDT
[    0.176897] ACPI: BIOS _OSI(Linux) query ignored
[    0.178192] ACPI: Interpreter enabled
[    0.178192] ACPI: (supports S0 S3 S4 S5)
[    0.178192] ACPI: Using IOAPIC for interrupt routing
[    0.184814] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.184814] ACPI: No dock devices found.
[    0.185312] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.185447] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.185451] pci 0000:00:01.0: PME# disabled
[    0.185485] pci 0000:00:02.0: reg 10 64bit mmio: [0xf4400000-0xf47fffff]
[    0.185494] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.185499] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.185546] pci 0000:00:02.1: reg 10 64bit mmio: [0xf4100000-0xf41fffff]
[    0.185679] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.185778] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.185886] pci 0000:00:1a.2: reg 20 io port: [0x1860-0x187f]
[    0.185994] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf4b04800-0xf4b04bff]
[    0.186070] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.186076] pci 0000:00:1a.7: PME# disabled
[    0.186136] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf4b00000-0xf4b03fff]
[    0.186199] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.186204] pci 0000:00:1b.0: PME# disabled
[    0.186303] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.186308] pci 0000:00:1c.0: PME# disabled
[    0.188066] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.188071] pci 0000:00:1c.1: PME# disabled
[    0.188173] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.188178] pci 0000:00:1c.2: PME# disabled
[    0.188275] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.188280] pci 0000:00:1c.3: PME# disabled
[    0.188387] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.188392] pci 0000:00:1c.4: PME# disabled
[    0.188494] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.188499] pci 0000:00:1c.5: PME# disabled
[    0.188576] pci 0000:00:1d.0: reg 20 io port: [0x1880-0x189f]
[    0.188692] pci 0000:00:1d.1: reg 20 io port: [0x18a0-0x18bf]
[    0.188795] pci 0000:00:1d.2: reg 20 io port: [0x18c0-0x18df]
[    0.188891] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4b04c00-0xf4b04fff]
[    0.188965] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.188971] pci 0000:00:1d.7: PME# disabled
[    0.189240] pci 0000:00:1f.2: reg 10 io port: [0x1818-0x181f]
[    0.189248] pci 0000:00:1f.2: reg 14 io port: [0x180c-0x180f]
[    0.189257] pci 0000:00:1f.2: reg 18 io port: [0x1810-0x1817]
[    0.189266] pci 0000:00:1f.2: reg 1c io port: [0x1808-0x180b]
[    0.189274] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.189283] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf4b04000-0xf4b047ff]
[    0.189337] pci 0000:00:1f.2: PME# supported from D3hot
[    0.189342] pci 0000:00:1f.2: PME# disabled
[    0.189387] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.189408] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.189592] pci 0000:02:00.0: reg 10 64bit mmio: [0xf4200000-0xf4201fff]
[    0.189711] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.189719] pci 0000:02:00.0: PME# disabled
[    0.189806] pci 0000:00:1c.0: bridge 32bit mmio: [0xf4200000-0xf42fffff]
[    0.189877] pci 0000:00:1c.1: bridge io port: [0x2000-0x2fff]
[    0.189882] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xfbffffff]
[    0.189891] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf0000000-0xf3ffffff]
[    0.190022] pci 0000:07:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.190047] pci 0000:07:00.0: reg 18 64bit mmio: [0xf4300000-0xf4300fff]
[    0.190065] pci 0000:07:00.0: reg 20 64bit mmio pref: [0xf4000000-0xf400ffff]
[    0.190074] pci 0000:07:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.190124] pci 0000:07:00.0: supports D1 D2
[    0.190127] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.190132] pci 0000:07:00.0: PME# disabled
[    0.190213] pci 0000:00:1c.3: bridge io port: [0x3000-0x3fff]
[    0.190218] pci 0000:00:1c.3: bridge 32bit mmio: [0xf4300000-0xf43fffff]
[    0.190226] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf4000000-0xf40fffff]
[    0.190286] pci 0000:08:00.0: reg 10 32bit mmio: [0xf4800000-0xf48000ff]
[    0.190460] pci 0000:08:00.2: reg 10 32bit mmio: [0xf4800400-0xf48004ff]
[    0.190631] pci 0000:08:00.3: reg 10 32bit mmio: [0xf4800800-0xf48008ff]
[    0.190814] pci 0000:00:1c.4: bridge 32bit mmio: [0xf4800000-0xf48fffff]
[    0.190951] pci 0000:00:1e.0: transparent bridge
[    0.191016] pci_bus 0000:00: on NUMA node 0
[    0.191029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.191254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.191335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.191539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.191618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.191689] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.191761] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.191833] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.205532] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.205636] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.205736] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.205839] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.205938] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.206037] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.206136] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.206236] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.206347] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.206367] vgaarb: loaded
[    0.206489] SCSI subsystem initialized
[    0.206608] libata version 3.00 loaded.
[    0.206681] usbcore: registered new interface driver usbfs
[    0.206693] usbcore: registered new interface driver hub
[    0.206717] usbcore: registered new device driver usb
[    0.206874] ACPI: WMI: Mapper loaded
[    0.206877] PCI: Using ACPI for IRQ routing
[    0.207118] NetLabel: Initializing
[    0.207120] NetLabel:  domain hash size = 128
[    0.207121] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.207134] NetLabel:  unlabeled traffic allowed by default
[    0.207176] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.207182] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.212215] Switching to clocksource tsc
[    0.214115] AppArmor: AppArmor Filesystem Enabled
[    0.214142] pnp: PnP ACPI init
[    0.214165] ACPI: bus type pnp registered
[    0.216482] pnp: PnP ACPI: found 11 devices
[    0.216525] ACPI: ACPI bus type pnp unregistered
[    0.216530] PnPBIOS: Disabled by ACPI PNP
[    0.216547] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.216555] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.216558] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.216561] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.216564] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.216567] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.216570] system 00:05: ioport range 0x1180-0x11ff has been reserved
[    0.216572] system 00:05: ioport range 0x164e-0x164f has been reserved
[    0.216575] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.216578] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.216584] system 00:06: ioport range 0x6a0-0x6af has been reserved
[    0.216586] system 00:06: ioport range 0x6b0-0x6ff has been reserved
[    0.216594] system 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.216596] system 00:0a: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.216599] system 00:0a: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.216602] system 00:0a: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.216605] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.216608] system 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.216611] system 00:0a: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.216614] system 00:0a: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.251442] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.251446] pci 0000:00:01.0:   IO window: 0x4000-0x4fff
[    0.251451] pci 0000:00:01.0:   MEM window: 0x80000000-0x801fffff
[    0.251455] pci 0000:00:01.0:   PREFETCH window: 0x00000080200000-0x000000803fffff
[    0.251460] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.251464] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    0.251471] pci 0000:00:1c.0:   MEM window: 0xf4200000-0xf42fffff
[    0.251476] pci 0000:00:1c.0:   PREFETCH window: 0x00000080400000-0x000000805fffff
[    0.251485] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.251489] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.251495] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xfbffffff
[    0.251501] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    0.251509] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.251513] pci 0000:00:1c.2:   IO window: 0x6000-0x6fff
[    0.251519] pci 0000:00:1c.2:   MEM window: 0x80600000-0x807fffff
[    0.251525] pci 0000:00:1c.2:   PREFETCH window: 0x00000080800000-0x000000809fffff
[    0.251534] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:07
[    0.251537] pci 0000:00:1c.3:   IO window: 0x3000-0x3fff
[    0.251544] pci 0000:00:1c.3:   MEM window: 0xf4300000-0xf43fffff
[    0.251550] pci 0000:00:1c.3:   PREFETCH window: 0x000000f4000000-0x000000f40fffff
[    0.251559] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:08
[    0.251562] pci 0000:00:1c.4:   IO window: 0x7000-0x7fff
[    0.251569] pci 0000:00:1c.4:   MEM window: 0xf4800000-0xf48fffff
[    0.251574] pci 0000:00:1c.4:   PREFETCH window: 0x00000080a00000-0x00000080bfffff
[    0.251583] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.251587] pci 0000:00:1c.5:   IO window: 0x8000-0x8fff
[    0.251594] pci 0000:00:1c.5:   MEM window: 0x80c00000-0x80dfffff
[    0.251599] pci 0000:00:1c.5:   PREFETCH window: 0x00000080e00000-0x00000080ffffff
[    0.251607] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    0.251609] pci 0000:00:1e.0:   IO window: disabled
[    0.251616] pci 0000:00:1e.0:   MEM window: disabled
[    0.251621] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.251647]   alloc irq_desc for 16 on node -1
[    0.251649]   alloc kstat_irqs on node -1
[    0.251659] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.251665] pci 0000:00:01.0: setting latency timer to 64
[    0.251675]   alloc irq_desc for 17 on node -1
[    0.251677]   alloc kstat_irqs on node -1
[    0.251681] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.251686] pci 0000:00:1c.0: setting latency timer to 64
[    0.251697] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.251702] pci 0000:00:1c.1: setting latency timer to 64
[    0.251712]   alloc irq_desc for 18 on node -1
[    0.251714]   alloc kstat_irqs on node -1
[    0.251718] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.251723] pci 0000:00:1c.2: setting latency timer to 64
[    0.251733]   alloc irq_desc for 19 on node -1
[    0.251735]   alloc kstat_irqs on node -1
[    0.251739] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.251744] pci 0000:00:1c.3: setting latency timer to 64
[    0.251754] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.251759] pci 0000:00:1c.4: setting latency timer to 64
[    0.251770] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.251775] pci 0000:00:1c.5: setting latency timer to 64
[    0.251783] pci 0000:00:1e.0: setting latency timer to 64
[    0.251788] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.251791] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.251794] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]
[    0.251796] pci_bus 0000:01: resource 1 mem: [0x80000000-0x801fffff]
[    0.251799] pci_bus 0000:01: resource 2 pref mem [0x80200000-0x803fffff]
[    0.251801] pci_bus 0000:02: resource 0 io:  [0x5000-0x5fff]
[    0.251804] pci_bus 0000:02: resource 1 mem: [0xf4200000-0xf42fffff]
[    0.251806] pci_bus 0000:02: resource 2 pref mem [0x80400000-0x805fffff]
[    0.251809] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    0.251811] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xfbffffff]
[    0.251814] pci_bus 0000:04: resource 2 pref mem [0xf0000000-0xf3ffffff]
[    0.251816] pci_bus 0000:06: resource 0 io:  [0x6000-0x6fff]
[    0.251819] pci_bus 0000:06: resource 1 mem: [0x80600000-0x807fffff]
[    0.251821] pci_bus 0000:06: resource 2 pref mem [0x80800000-0x809fffff]
[    0.251823] pci_bus 0000:07: resource 0 io:  [0x3000-0x3fff]
[    0.251826] pci_bus 0000:07: resource 1 mem: [0xf4300000-0xf43fffff]
[    0.251828] pci_bus 0000:07: resource 2 pref mem [0xf4000000-0xf40fffff]
[    0.251831] pci_bus 0000:08: resource 0 io:  [0x7000-0x7fff]
[    0.251833] pci_bus 0000:08: resource 1 mem: [0xf4800000-0xf48fffff]
[    0.251836] pci_bus 0000:08: resource 2 pref mem [0x80a00000-0x80bfffff]
[    0.251838] pci_bus 0000:09: resource 0 io:  [0x8000-0x8fff]
[    0.251841] pci_bus 0000:09: resource 1 mem: [0x80c00000-0x80dfffff]
[    0.251843] pci_bus 0000:09: resource 2 pref mem [0x80e00000-0x80ffffff]
[    0.251846] pci_bus 0000:0a: resource 3 io:  [0x00-0xffff]
[    0.251848] pci_bus 0000:0a: resource 4 mem: [0x000000-0xffffffff]
[    0.251889] NET: Registered protocol family 2
[    0.251991] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.252338] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.252894] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.253238] TCP: Hash tables configured (established 131072 bind 65536)
[    0.253241] TCP reno registered
[    0.253371] NET: Registered protocol family 1
[    0.253397] pci 0000:00:02.0: Boot video device
[    0.253782] cpufreq-nforce2: No nForce2 chipset.
[    0.253812] Scanning for low memory corruption every 60 seconds
[    0.253924] audit: initializing netlink socket (disabled)
[    0.253937] type=2000 audit(1273088847.251:1): initialized
[    0.263285] highmem bounce pool size: 64 pages
[    0.263290] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.264839] VFS: Disk quotas dquot_6.5.2
[    0.264903] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.265470] fuse init (API version 7.13)
[    0.265551] msgmni has been set to 1691
[    0.265774] alg: No test for stdrng (krng)
[    0.265832] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.265835] io scheduler noop registered
[    0.265837] io scheduler anticipatory registered
[    0.265839] io scheduler deadline registered
[    0.265880] io scheduler cfq registered (default)
[    0.266052]   alloc irq_desc for 24 on node -1
[    0.266054]   alloc kstat_irqs on node -1
[    0.266063] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.266070] pcieport 0000:00:01.0: setting latency timer to 64
[    0.266211]   alloc irq_desc for 25 on node -1
[    0.266213]   alloc kstat_irqs on node -1
[    0.266222] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.266234] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.266398]   alloc irq_desc for 26 on node -1
[    0.266400]   alloc kstat_irqs on node -1
[    0.266409] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.266420] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.266581]   alloc irq_desc for 27 on node -1
[    0.266583]   alloc kstat_irqs on node -1
[    0.266592] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.266604] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.266770]   alloc irq_desc for 28 on node -1
[    0.266772]   alloc kstat_irqs on node -1
[    0.266781] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.266792] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.266956]   alloc irq_desc for 29 on node -1
[    0.266958]   alloc kstat_irqs on node -1
[    0.266967] pcieport 0000:00:1c.4: irq 29 for MSI/MSI-X
[    0.266978] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.267140]   alloc irq_desc for 30 on node -1
[    0.267142]   alloc kstat_irqs on node -1
[    0.267151] pcieport 0000:00:1c.5: irq 30 for MSI/MSI-X
[    0.267163] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.267278] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.267524] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.268025] ACPI Error (psargs-0359): [\_PR_.CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND
[    0.268033] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.ADP0.ADJP] (Node f7015b10), AE_NOT_FOUND
[    0.268100] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.ADP0._PSR] (Node f7015ae0), AE_NOT_FOUND
[    0.268128] ACPI Exception: AE_NOT_FOUND, Error reading AC Adapter state (20090903/ac-140)
[    0.268207] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.268632] ACPI: Lid Switch [LID0]
[    0.268678] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.268685] ACPI: Power Button [PWRB]
[    0.268731] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.268738] ACPI: Sleep Button [SLPB]
[    0.268777] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.268780] ACPI: Power Button [PWRF]
[    0.269692] ACPI: SSDT 7db1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.271861] processor LNXCPU:00: registered as cooling_device0
[    0.272325] ACPI: SSDT 7db19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.273278] processor LNXCPU:01: registered as cooling_device1
[    0.355673] Freeing initrd memory: 7772k freed
[    0.785634] thermal LNXTHERM:01: registered as thermal_zone0
[    0.785645] ACPI: Thermal Zone [THM0] (54 C)
[    0.785883] isapnp: Scanning for PnP cards...
[    0.792697] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.794597] brd: module loaded
[    0.795235] loop: module loaded
[    0.795340] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.795864] Fixed MDIO Bus: probed
[    0.795896] PPP generic driver version 2.4.2
[    0.795930] tun: Universal TUN/TAP device driver, 1.6
[    0.795932] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.796008] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.796036] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.796053] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.796057] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.796091] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.796124] ehci_hcd 0000:00:1a.7: debug port 1
[    0.800025] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.800048] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf4b04800
[    0.815292] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.815376] usb usb1: configuration #1 chosen from 1 choice
[    0.815403] hub 1-0:1.0: USB hub found
[    0.815410] hub 1-0:1.0: 6 ports detected
[    0.815474]   alloc irq_desc for 23 on node -1
[    0.815476]   alloc kstat_irqs on node -1
[    0.815482] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.815493] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.815498] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.815531] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.815559] ehci_hcd 0000:00:1d.7: debug port 1
[    0.819434] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.819452] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4b04c00
[    0.835291] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.835373] usb usb2: configuration #1 chosen from 1 choice
[    0.835397] hub 2-0:1.0: USB hub found
[    0.835403] hub 2-0:1.0: 6 ports detected
[    0.835464] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.835480] uhci_hcd: USB Universal Host Controller Interface driver
[    0.835507] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.835514] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.835518] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.835550] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.835587] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.835673] usb usb3: configuration #1 chosen from 1 choice
[    0.835697] hub 3-0:1.0: USB hub found
[    0.835703] hub 3-0:1.0: 2 ports detected
[    0.835758]   alloc irq_desc for 21 on node -1
[    0.835760]   alloc kstat_irqs on node -1
[    0.835765] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.835772] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.835775] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.835804] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.835840] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.835928] usb usb4: configuration #1 chosen from 1 choice
[    0.835952] hub 4-0:1.0: USB hub found
[    0.835958] hub 4-0:1.0: 2 ports detected
[    0.836007] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.836014] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.836017] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.836046] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.836074] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    0.836161] usb usb5: configuration #1 chosen from 1 choice
[    0.836185] hub 5-0:1.0: USB hub found
[    0.836191] hub 5-0:1.0: 2 ports detected
[    0.836240] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.836246] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.836250] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.836278] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.836306] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    0.836391] usb usb6: configuration #1 chosen from 1 choice
[    0.836417] hub 6-0:1.0: USB hub found
[    0.836424] hub 6-0:1.0: 2 ports detected
[    0.836468] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.836476] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.836479] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.836508] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.836536] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    0.836622] usb usb7: configuration #1 chosen from 1 choice
[    0.836649] hub 7-0:1.0: USB hub found
[    0.836655] hub 7-0:1.0: 2 ports detected
[    0.836701] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.836708] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.836712] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.836746] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.836782] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    0.836867] usb usb8: configuration #1 chosen from 1 choice
[    0.836891] hub 8-0:1.0: USB hub found
[    0.836898] hub 8-0:1.0: 2 ports detected
[    0.836998] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.841386] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.844669] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.844675] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.844702] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.844722] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.844743] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.844849] mice: PS/2 mouse device common for all mice
[    0.845046] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.845079] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.845179] device-mapper: uevent: version 1.0.3
[    0.845288] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.845353] device-mapper: multipath: version 1.1.0 loaded
[    0.845356] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.845460] EISA: Probing bus 0 at eisa.0
[    0.845466] Cannot allocate resource for EISA slot 1
[    0.845469] Cannot allocate resource for EISA slot 2
[    0.845471] Cannot allocate resource for EISA slot 3
[    0.845473] Cannot allocate resource for EISA slot 4
[    0.845475] Cannot allocate resource for EISA slot 5
[    0.845477] Cannot allocate resource for EISA slot 6
[    0.845479] Cannot allocate resource for EISA slot 7
[    0.845481] Cannot allocate resource for EISA slot 8
[    0.845483] EISA: Detected 0 cards.
[    0.845554] cpuidle: using governor ladder
[    0.845556] cpuidle: using governor menu
[    0.845987] TCP cubic registered
[    0.846129] NET: Registered protocol family 10
[    0.846582] lo: Disabled Privacy Extensions
[    0.846908] NET: Registered protocol family 17
[    0.847544] Using IPI No-Shortcut mode
[    0.847624] PM: Resume from disk failed.
[    0.847636] registered taskstats version 1
[    0.848367]   Magic number: 10:619:798
[    0.848449] rtc_cmos 00:07: setting system clock to 2010-05-05 19:47:28 UTC (1273088848)
[    0.848452] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.848454] EDD information not available.
[    0.922493] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.140434] isapnp: No Plug & Play device found
[    1.292484] ACPI: Battery Slot [BAT0] (battery present)
[    1.295831] Freeing unused kernel memory: 656k freed
[    1.296196] Write protecting the kernel text: 4676k
[    1.296237] Write protecting the kernel read-only data: 1840k
[    1.313118] udev: starting version 151
[    1.404978] ahci 0000:00:1f.2: version 3.0
[    1.405053] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.431550] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.431577] r8169 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.431627] r8169 0000:07:00.0: setting latency timer to 64
[    1.431690]   alloc irq_desc for 31 on node -1
[    1.431693]   alloc kstat_irqs on node -1
[    1.431710] r8169 0000:07:00.0: irq 31 for MSI/MSI-X
[    1.434875] eth0: RTL8168c/8111c at 0xf808a000, 00:90:f5:8d:44:ae, XID 1c4000c0 IRQ 31
[    1.439221]   alloc irq_desc for 32 on node -1
[    1.439224]   alloc kstat_irqs on node -1
[    1.439238] ahci 0000:00:1f.2: irq 32 for MSI/MSI-X
[    1.439309] ahci: SSS flag set, parallel bus scan disabled
[    1.439355] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.439359] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pio slum part ccc ems sxs 
[    1.439365] ahci 0000:00:1f.2: setting latency timer to 64
[    1.460082] scsi0 : ahci
[    1.460220] scsi1 : ahci
[    1.460290] scsi2 : ahci
[    1.460355] scsi3 : ahci
[    1.460413] scsi4 : ahci
[    1.460473] scsi5 : ahci
[    1.460530] ata1: SATA max UDMA/133 abar m2048@0xf4b04000 port 0xf4b04100 irq 32
[    1.460534] ata2: SATA max UDMA/133 abar m2048@0xf4b04000 port 0xf4b04180 irq 32
[    1.460536] ata3: DUMMY
[    1.460538] ata4: DUMMY
[    1.460540] ata5: SATA max UDMA/133 abar m2048@0xf4b04000 port 0xf4b04300 irq 32
[    1.460544] ata6: SATA max UDMA/133 abar m2048@0xf4b04000 port 0xf4b04380 irq 32
[    1.508016] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.780023] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.828339] ata1.00: ATA-8: WDC WD2500BEVS-75UST0, 01.01A01, max UDMA/133
[    1.828342] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.829264] ata1.00: configured for UDMA/133
[    1.829379] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-7 01.0 PQ: 0 ANSI: 5
[    1.829562] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.829566] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.829639] sd 0:0:0:0: [sda] Write Protect is off
[    1.829642] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.829667] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.829809]  sda: sda1 sda2 < sda5 >
[    1.861457] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.944878] usb 1-2: configuration #1 chosen from 1 choice
[    2.384041] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    2.552023] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.555755] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50N, RH03, max UDMA/133
[    2.560809] ata2.00: configured for UDMA/133
[    2.562141] usb 5-2: configuration #1 chosen from 1 choice
[    2.672769] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50N  RH03 PQ: 0 ANSI: 5
[    2.804011] usb 7-2: new low speed USB device using uhci_hcd and address 2
[    2.973589] usb 7-2: configuration #1 chosen from 1 choice
[    3.003869] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.003874] Uniform CD-ROM driver Revision: 3.20
[    3.003988] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.004070] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.324021] ata5: SATA link down (SStatus 0 SControl 300)
[    3.644017] ata6: SATA link down (SStatus 0 SControl 300)
[    3.647892] usbcore: registered new interface driver hiddev
[    3.669813] input: HP Laser Mobile Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input6
[    3.669934] generic-usb 0003:0461:4D62.0001: input,hidraw0: USB HID v1.11 Mouse [HP Laser Mobile Mouse] on usb-0000:00:1d.1-2/input0
[    3.669968] usbcore: registered new interface driver usbhid
[    3.669971] usbhid: v2.6:USB HID core driver
[    3.921408] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   14.960230] Adding 5927944k swap on /dev/sda5.  Priority:-1 extents:1 across:5927944k 
[   15.231792] udev: starting version 151
[   15.692017] type=1505 audit(1273088863.339:2):  operation="profile_load" pid=576 name="/sbin/dhclient3"
[   15.692656] type=1505 audit(1273088863.343:3):  operation="profile_load" pid=576 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.692999] type=1505 audit(1273088863.343:4):  operation="profile_load" pid=576 name="/usr/lib/connman/scripts/dhclient-script"
[   15.904138] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.947573] lp: driver loaded but no devices found
[   16.141682] type=1505 audit(1273088863.792:5):  operation="profile_load" pid=743 name="/usr/share/gdm/guest-session/Xsession"
[   16.143457] type=1505 audit(1273088863.792:6):  operation="profile_replace" pid=744 name="/sbin/dhclient3"
[   16.144104] type=1505 audit(1273088863.792:7):  operation="profile_replace" pid=744 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.144454] type=1505 audit(1273088863.792:8):  operation="profile_replace" pid=744 name="/usr/lib/connman/scripts/dhclient-script"
[   16.148146] type=1505 audit(1273088863.796:9):  operation="profile_load" pid=745 name="/usr/bin/evince"
[   16.156410] type=1505 audit(1273088863.804:10):  operation="profile_load" pid=745 name="/usr/bin/evince-previewer"
[   16.162678] type=1505 audit(1273088863.812:11):  operation="profile_load" pid=745 name="/usr/bin/evince-thumbnailer"
[   16.172842] cfg80211: Calling CRDA to update world regulatory domain
[   16.194175] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.195573] sdhci: Secure Digital Host Controller Interface driver
[   16.195578] sdhci: Copyright(c) Pierre Ossman
[   16.198919] Linux video capture interface: v2.00
[   16.199220] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   16.199224] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   16.199226] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   16.201768] sdhci-pci 0000:08:00.0: SDHCI controller found [197b:2382] (rev 0)
[   16.201798] sdhci-pci 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.201856] sdhci-pci 0000:08:00.0: setting latency timer to 64
[   16.201980] Registered led device: mmc0::
[   16.202059] mmc0: SDHCI controller on PCI [0000:08:00.0] using ADMA
[   16.202076] sdhci-pci 0000:08:00.2: SDHCI controller found [197b:2381] (rev 0)
[   16.202099] sdhci-pci 0000:08:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.202109] sdhci-pci 0000:08:00.2: Refusing to bind to secondary interface.
[   16.202118] sdhci-pci 0000:08:00.2: PCI INT A disabled
[   16.204956] Linux agpgart interface v0.103
[   16.207556] jmb38x_ms 0000:08:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.207566] jmb38x_ms 0000:08:00.3: setting latency timer to 64
[   16.218029] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   16.218505] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   16.218924] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0303)
[   16.234923] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input7
[   16.234981] usbcore: registered new interface driver uvcvideo
[   16.234984] USB Video Class driver (v0.1.0)
[   16.252056] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   16.299101] cfg80211: World regulatory domain updated:
[   16.299104]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.299108]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.299110]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.299113]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.299115]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.299117]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.749922] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   16.749926] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   16.750003] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.750013] iwlagn 0000:02:00.0: setting latency timer to 64
[   16.750057] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   16.788536] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.788604]   alloc irq_desc for 33 on node -1
[   16.788606]   alloc kstat_irqs on node -1
[   16.788627] iwlagn 0000:02:00.0: irq 33 for MSI/MSI-X
[   16.797892] [drm] Initialized drm 1.1.0 20060810
[   16.913841] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x81a0b1, caps: 0xa04711/0xa04000
[   16.941439] i915 0000:00:02.0: power state changed by ACPI to D0
[   16.941450] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.941455] i915 0000:00:02.0: setting latency timer to 64
[   16.948662]   alloc irq_desc for 34 on node -1
[   16.948665]   alloc kstat_irqs on node -1
[   16.948675] i915 0000:00:02.0: irq 34 for MSI/MSI-X
[   16.948684] [drm] set up 31M of stolen space
[   16.951261] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   17.059140] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   17.072900] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.651044] fb0: inteldrmfb frame buffer device
[   17.651047] registered panic notifier
[   17.664514] acpi device:03: registered as cooling_device2
[   17.665358] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   17.665556] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.665697] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.665756]   alloc irq_desc for 22 on node -1
[   17.665758]   alloc kstat_irqs on node -1
[   17.665766] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.665841] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.716281] vga16fb: initializing
[   17.716285] vga16fb: mapped to 0xc00a0000
[   17.716289] vga16fb: not registering due to another framebuffer present
[   17.827548] r8169: eth0: link up
[   17.827558] r8169: eth0: link up
[   17.881671] hda_codec: ALC662 rev1: BIOS auto-probing.
[   17.882973] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   18.351841] Console: switching to colour frame buffer device 160x50
[   19.753288] RPC: Registered udp transport module.
[   19.753291] RPC: Registered tcp transport module.
[   19.753293] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   19.924765] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   19.980820] svc: failed to register lockdv1 RPC service (errno 97).
[   19.981831] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   20.010009] NFSD: starting 90-second grace period
[   21.575816] ppdev: user-space parallel port driver
[   28.636006] eth0: no IPv6 routers present

....**ends**

---

### Post by tecknomage on 2010-05-05
> **iskarion said:**
> I don't think this is related to fstab settings. I'm experiencing the same problem and did already try to change many fstab options to no avail.
Also I saw posts on this in other forums from users with quite different harddrive/hardware configurations and therefore probably also different fstab setup.

Edit: do you have AHCI enabled? Maybe it's just a coincidence, but on the computer (fresh Kubuntu 10.04 install) I'm getting this udevd-work.../dev/null error, AHCI is enabled. On another computer (upgrade from Kubuntu 9.10 to 10.04) where AHCI is not active I'm not experiencing this problem.

Switching from **AHCI -> IDE did not fix**, in fact to boot properly I had to go back to AHCI.

---

### Post by mikewhatever on 2010-05-05
Can't seem to find anything related to 'udevd-work.../dev/null' in the output.

---

### Post by iskarion on 2010-05-05
> **mikewhatever said:**
> Can't seem to find anything related to 'udevd-work.../dev/null' in the output.
Yes that's quite strange. Also for me this message is only visible during bootup process. But I can't find the error message in dmesg or any of the other logs in /var/log

---

### Post by frantid on 2010-05-05
Can you please check your udev log.

It's the only place in my logs that /dev/null appears.

also:

please run

```
sudo grep null /lib/udev/rules.d/*
``````
sudo grep null /etc/udev/rules.d/*
```

edit forgot 1

```
ls -l /dev/null
```

---

### Post by tecknomage on 2010-05-06
> **frantid said:**
> Can you please check your udev log.

It's the only place in my logs that /dev/null appears.

also:

please run

```
sudo grep null /lib/udev/rules.d/*
``````
sudo grep null /etc/udev/rules.d/*
```edit forgot 1

```
ls -l /dev/null
```

**RESULT:**

tecknode@LC2000SN:~$ sudo grep null /lib/udev/rules.d/*
[sudo] password for tecknode: 
/lib/udev/rules.d/50-udev-default.rules:KERNEL=="null|zero|full|random|urandom", MODE="0666"
tecknode@LC2000SN:~$ sudo grep null /etc/udev/rules.d/*
tecknode@LC2000SN:~$ ls -l /dev/null
crw-rw-rw- 1 root root 1, 3 2010-05-06 07:40 /dev/null
tecknode@LC2000SN:~$ 

:???: Now what?

Is this an attempt to access a CD that is not mounted?

---

### Post by tecknomage on 2010-05-06
UPDATE

Just rebooted and the problem is still there, but there is a minor difference.


[LIST=1]
[*]**BEFORE SUDO** runs above; display prefix =** UDEVD-WORK[[COLOR=Red]325[/COLOR]]**
[*]THIS BOOT, display prefix = **UDEVD-WORK[COLOR=Red][COLOR=Black][[/COLOR]285[/COLOR]]**
[/LIST]
[SIZE=2]Just performed a test[/SIZE], **mounted a data DVD and rebooted**.

Sure enough at the time, during boot, when the UDEVD-WORK would display,** the DVD drive would spin-up (*access LED flashed*) then the boot continued NORMALLY**.

So for whatever reason, the bootup tries to access the DVD.  Note that I have tried boot sequence HD then DVD and that did not fix the problem.  This tells me the attempt to read the DVD drive is coded into the Linux boot sequence.

**UPDATE**

**Experiment-2**: Change boot-order to **HD then CD**, mounted my copy of **Ubuntu 10.04 Live CD** and booted. Booted NORMALLY, _but did read the CD_. Rebooted, changed boot-order back to **CD then HD**, booted WITHOUT CD, mount error again.

I was testing to see if something needed to complete that was not done because of using the online upgrade method.  Didn't work of course.

[COLOR=Red]**Is there a way to stop this?**[/COLOR]

---

### Post by DeMus on 2010-05-11
I also have the same error line as you, and many others, have but I get 2 of them: I have 2 DVD drives in my computer. Also same as with you, the lights on the drives are on for a moment when the errors show up.
My boot order is HD - CD.

---

### Post by frantid on 2010-05-11
> **tecknomage said:**
> UPDATE

Just rebooted and the problem is still there, but there is a minor difference.


[LIST=1]
[*]**BEFORE SUDO** runs above; display prefix =** UDEVD-WORK[[COLOR=Red]325[/COLOR]]**
[*]THIS BOOT, display prefix = **UDEVD-WORK[COLOR=Red][COLOR=Black][[/COLOR]285[/COLOR]]**
[/LIST]
[SIZE=2]Just performed a test[/SIZE], **mounted a data DVD and rebooted**.

Sure enough at the time, during boot, when the UDEVD-WORK would display,** the DVD drive would spin-up (*access LED flashed*) then the boot continued NORMALLY**.

So for whatever reason, the bootup tries to access the DVD.  Note that I have tried boot sequence HD then DVD and that did not fix the problem.  This tells me the attempt to read the DVD drive is coded into the Linux boot sequence.

**UPDATE**

**Experiment-2**: Change boot-order to **HD then CD**, mounted my copy of **Ubuntu 10.04 Live CD** and booted. Booted NORMALLY, _but did read the CD_. Rebooted, changed boot-order back to **CD then HD**, booted WITHOUT CD, mount error again.

I was testing to see if something needed to complete that was not done because of using the online upgrade method.  Didn't work of course.

[COLOR=Red]**Is there a way to stop this?**[/COLOR]

Do you have any cd's listed in your software sources?

---

### Post by tecknomage on 2010-05-11
**NOTE:  [Ubuntu Bug Report 57533]("https://bugs.launchpad.net/ubuntu/+bug/575333")** (*link*) on this subject.  Bug is confirmed.

**Suggest others with this problem track this Bug Report**.  It has entries from me and others, including Ubuntu Logs.

Of special interest, **my last 2 entries from the bug report as of this time-date stamp**:

                 > OK - I am on my Ubuntu Notebook.  Here  are my Log Search results.


 Search = /dev/null


 **Log = SYSLOG**:

 LC2000SN CRON[2184]: (root) CMD (command -v debian-sa1 > /dev/null  && debian-sa1 1 1)

 **Log = UDEV**:

 UDEV  [1273598840.789083] add      /devices/virtual/mem/null  (mem)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/virtual/mem/null
SUBSYSTEM=mem
DEVNAME=/dev/null
DEVMODE=0666
SEQNUM=1454
MAJOR=1
MINOR=3
DEVLINKS=/dev/char/1:3


 From what I see above, is the SYSLOG "CMD" line entry the culprit?


                 Another thought.


 Since "/dev/null' is listed as a Virtual Memory Device, could the  problem be trying to access virtual memory BEFORE it is mounted?


Any suggestions/comments  :-k

---

### Post by davidsrsb on 2010-05-22
I have three Ubuntu 10.04 machines.
Only one does this, with the annoying 15 second delay
All are dual boot with XP and have dvd drives

---

