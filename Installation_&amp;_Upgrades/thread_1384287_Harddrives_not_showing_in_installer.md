---
title: "Harddrives not showing in installer"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by neamhaol on 2010-01-18
I am trying to install ubuntu, I have both the 9.10 and 9.04 versions and when I go through the installer neither of my sata harddrives which are 250 and 500gb are showing up. Even in gparted in livecd boot does not show. Windows and fedora 10 recognize them right away but not ubunutu.
 
I have tried having a single hd plugged in 1st sata slot and still have nothing. I would really like to use ubuntu because of the great things i hear from it. If anyone could help I would greatly appreciate it.

---

### Post by lidex on 2010-01-18
What do you currently have installed on your PC?

---

### Post by neamhaol on 2010-01-18
I have windows xp installed on a partition on my main 250gb harddrive. This OS is useless because my wife got some nasty virus or something on it and I do not have a disc to format and wipe.
 
I also have Fedora 10 installed on the 500gb however I was wanting to try to get Ubuntu, since my end result is to attempt to use wine to play a couple of the games I actually care about. Almost all the forum help for using the program is from ubuntu users so some is differant.
 
I would not care to lose either OS as I have backed up everything I need to external storage.
 
I have tried running LiveCD to maybe install a driver or something that maybe ubuntu is missing, but im not competent enough to find anything.

---

### Post by audiomick on 2010-01-18
Hi,
a number of people, including me, have had the problem that the live CD can't  find the drives during install.
The commonest advice is to try the alternate CD, which has a different partitioning tool.

That worked for me.

It is a text based installer instead of a GUI one, but don't let that scare you. It isn't hard to deal with.

---

### Post by lidex on 2010-01-18
> **audiomick said:**
> Hi,
a number of people, including me, have had the problem that the live CD can't  find the drives during install.
The commonest advice is to try the alternate CD, which has a different partitioning tool.

That worked for me.

It is a text based installer instead of a GUI one, but don't let that scare you. It isn't hard to deal with.

Sounds good to me. You can download here:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by neamhaol on 2010-01-18
Will attempt and let you know how it goes.
 
Thanks alot for such quick help....

---

### Post by neamhaol on 2010-01-19
Still no autodtect even in alternate installer.
 
Shows list of drivers to pick from however I cannot find anything showing which relates to my HDs in particular.
 
In bios it says 4m-wdc wd2500 as the first hd and 3m-st3500320a as my 2nd.
I know one is a western digital 500gb and the other is a seagate 250gb.
Would anyone know which drivers i could choose or another fix for the autodetect?

---

### Post by darkod on 2010-01-19
Does the same thing happen with the installer of both 9.10 and 9.04 or just 9.10?

---

### Post by darkod on 2010-01-19
Sometimes remains of raid settings can make 9.10 not "see" the drives.
Go into BIOS and make sure you have no raid options enabled.
Then boot with the 9.10 cd, Try Ubuntu option, and execute in terminal:

sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
sudo apt-get remove dmraid

That should get rid of raid settings remains, provided that was the problem. See if that helps.

---

### Post by neamhaol on 2010-01-19
Yes, same issue both releases.
Will try to disable any raid settings that may be on, and let you know.

---

### Post by recluce on 2010-01-19
Some alternatives to try:

- get the drive manufacturer's diagnostic tool disk (hopefully a selfbooting CD image), usually this includes tools for low level formatting or "zeroing" drives. That should wipe everything.

- Try Knoppix (Live Linux) to run gparted, that would exclude any Ubuntu specific issues that you might have

- Get the "UBCD" (Universal Boot CD), which contains many tools to nuke (completely erase) the disks.

---

### Post by viper250 on 2010-01-19
with some sata drives the bios setting has to be set to ide before some versions of linux will see them. (had this problem with an hp media center laptop):twisted:
and in some older systems the jumper on the drive needs to be set for the lower speed before the drive can be detected.:D

---

### Post by viper250 on 2010-01-19
and for a good drive wiper use d-ban It will forensically clean a hard drive you can download it from linuxlinks.com

---

### Post by lidex on 2010-01-19
Can you boot into a live session and get the output of this command in a terminal:
```
sudo fdisk -l
```

And also these log files (in live session):
/var/log/syslog and /var/log/partman

---

### Post by lidex on 2010-01-19
From **[this]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470")** bug report:



> My test case:

1. Boot Karmic regular CD
2. I Can see SATA HDD on desktop and can mount it etc.
3. Open Ubiquity from desktop icon
4. Ubiquity doesn't see SATA HDD.

To work around this and be able to install karmic I did:

1. Disable everything that has to do with RAID in the BIOS (some Nvidia on-board software RAID)
2. Boot the karmic alternate CD
3. When asked, choose to *not* load RAID drivers
4. Installer detects the SATA HDD fine.


---

### Post by neamhaol on 2010-01-19
syslog

Jan 20 03:50:10 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Jan 20 03:50:10 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1311" x-info="http://www.rsyslog.com"] (re)start
Jan 20 03:50:10 ubuntu rsyslogd: rsyslogd's groupid changed to 102
Jan 20 03:50:10 ubuntu rsyslogd: rsyslogd's userid changed to 101
Jan 20 03:50:10 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Command line: file=/cdrom/ubuntu/preseed/ubuntu.seed boot=casper initrd=/ubuntu/casper/initrd.lz quiet splash -- BOOT_IMAGE=/ubuntu/casper/vmlinuz Ubuntu without any change to your computer
Jan 20 03:50:10 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Jan 20 03:50:10 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] DMI present.
Jan 20 03:50:10 ubuntu kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jan 20 03:50:10 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] last_pfn = 0xbffa0 max_arch_pfn = 0x400000000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Jan 20 03:50:10 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   A0000-EFFFF uncachable
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Jan 20 03:50:10 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   1 base 0080000000 mask FFC0000000 write-back
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   2 disabled
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   3 disabled
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   4 disabled
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   5 disabled
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   6 disabled
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   7 disabled
Jan 20 03:50:10 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jan 20 03:50:10 ubuntu kernel: [    0.000000] modified physical RAM map:
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009e000 (usable)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 00000000bffa0000 (usable)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 00000000bffa0000 - 00000000bffae000 (ACPI data)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bffa0000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  0000000000 - 00bfe00000 page 2M
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  00bfe00000 - 00bffa0000 page 4k
Jan 20 03:50:10 ubuntu kernel: [    0.000000] kernel direct mapping tables up to bffa0000 @ 10000-15000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] RAMDISK: 7fa6c000 - 7fffe58e
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000fa230 00014 (v00 ACPIAM)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: RSDT 00000000bffa0000 00044 (v01 090108 RSDT1535 20080901 MSFT 00000097)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: FACP 00000000bffa0200 00084 (v01 090108 FACP1535 20080901 MSFT 00000097)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: DSDT 00000000bffa04a0 0964C (v01  C780A C780A340 00000340 INTL 20051117)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: FACS 00000000bffae000 00040
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: APIC 00000000bffa0390 00080 (v01 090108 APIC1535 20080901 MSFT 00000097)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: MCFG 00000000bffa0410 0003C (v01 090108 OEMMCFG  20080901 MSFT 00000097)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: WDRT 00000000bffa0450 00047 (v01 090108 NV-WDRT  20080901 MSFT 00000097)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: OEMB 00000000bffae040 00073 (v01 090108 OEMB1535 20080901 MSFT 00000097)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: HPET 00000000bffa9af0 00038 (v01 090108 OEMHPET0 20080901 MSFT 00000097)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: INFO 00000000bffae0c0 00124 (v01 090108 AMDINFO  20080901 MSFT 00000097)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: NVHD 00000000bffae1f0 00284 (v01 090108  NVHDCP  20080901 MSFT 00000097)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jan 20 03:50:10 ubuntu kernel: [    0.000000] No NUMA configuration found
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-00000000bffa0000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-00000000bffa0000
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   bootmap [0000000000018000 -  000000000002fff7] pages 18
Jan 20 03:50:10 ubuntu kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00bffa0000]
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   #3 [007fa6c000 - 007fffe58e]          RAMDISK ==> [007fa6c000 - 007fffe58e]
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   #5 [00019e3000 - 00019e31a9]              BRK ==> [00019e3000 - 00019e31a9]
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Jan 20 03:50:10 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jan 20 03:50:10 ubuntu kernel: [    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff880001e00000-ffff8800047fffff] on node 0
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Zone PFN ranges:
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Jan 20 03:50:10 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan 20 03:50:10 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jan 20 03:50:10 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000bffa0
Jan 20 03:50:10 ubuntu kernel: [    0.000000] On node 0 totalpages: 786222
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   DMA zone: 104 pages reserved
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   DMA zone: 3822 pages, LIFO batch:0
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   DMA32 zone: 10695 pages used for memmap
Jan 20 03:50:10 ubuntu kernel: [    0.000000]   DMA32 zone: 771545 pages, LIFO batch:31
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x2008
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan 20 03:50:10 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 20 03:50:10 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jan 20 03:50:10 ubuntu kernel: [    0.000000] nr_irqs_gsi: 24
Jan 20 03:50:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ec00000)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Jan 20 03:50:10 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages at ffff880001a00000, static data 90720 bytes
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 775367
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Policy zone: DMA32
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Kernel command line: file=/cdrom/ubuntu/preseed/ubuntu.seed boot=casper initrd=/ubuntu/casper/initrd.lz quiet splash -- BOOT_IMAGE=/ubuntu/casper/vmlinuz Ubuntu without any change to your computer
Jan 20 03:50:10 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Initializing CPU#0
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Checking aperture...
Jan 20 03:50:10 ubuntu kernel: [    0.000000] No AGP bridge found
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Node 0: aperture @ b002000000 size 32 MB
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Memory: 3085356k/3145344k available (5313k kernel code, 456k absent, 59532k reserved, 3011k data, 660k init)
Jan 20 03:50:10 ubuntu kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jan 20 03:50:10 ubuntu kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Jan 20 03:50:10 ubuntu kernel: [    0.000000] Detected 2800.322 MHz processor.
Jan 20 03:50:10 ubuntu kernel: [    0.000015] spurious 8259A interrupt: IRQ7.
Jan 20 03:50:10 ubuntu kernel: [    0.001914] Console: colour VGA+ 80x25
Jan 20 03:50:10 ubuntu kernel: [    0.001916] console [tty0] enabled
Jan 20 03:50:10 ubuntu kernel: [    0.010000] allocated 31457280 bytes of page_cgroup
Jan 20 03:50:10 ubuntu kernel: [    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan 20 03:50:10 ubuntu kernel: [    0.010000] hpet clockevent registered
Jan 20 03:50:10 ubuntu kernel: [    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.64 BogoMIPS (lpj=28003220)
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Security Framework initialized
Jan 20 03:50:10 ubuntu kernel: [    0.010000] AppArmor: AppArmor initialized
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Mount-cache hash table entries: 256
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Initializing cgroup subsys ns
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Initializing cgroup subsys cpuacct
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Initializing cgroup subsys memory
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Initializing cgroup subsys freezer
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Initializing cgroup subsys net_cls
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU 0/0x0 -> Node 0
Jan 20 03:50:10 ubuntu kernel: [    0.010000] tseg: 0000000000
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU: Physical Processor ID: 0
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU: Processor Core ID: 0
Jan 20 03:50:10 ubuntu kernel: [    0.010000] mce: CPU supports 5 MCE banks
Jan 20 03:50:10 ubuntu kernel: [    0.010000] using C1E aware idle routine
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Performance Counters: AMD PMU driver.
Jan 20 03:50:10 ubuntu kernel: [    0.010000] ... version:                 0
Jan 20 03:50:10 ubuntu kernel: [    0.010000] ... bit width:               48
Jan 20 03:50:10 ubuntu kernel: [    0.010000] ... generic counters:        4
Jan 20 03:50:10 ubuntu kernel: [    0.010000] ... value mask:              0000ffffffffffff
Jan 20 03:50:10 ubuntu kernel: [    0.010000] ... max period:              00007fffffffffff
Jan 20 03:50:10 ubuntu kernel: [    0.010000] ... fixed-purpose counters:  0
Jan 20 03:50:10 ubuntu kernel: [    0.010000] ... counter mask:            000000000000000f
Jan 20 03:50:10 ubuntu kernel: [    0.010000] ACPI: Core revision 20090521
Jan 20 03:50:10 ubuntu kernel: [    0.018213] Setting APIC routing to flat
Jan 20 03:50:10 ubuntu kernel: [    0.018700] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 20 03:50:10 ubuntu kernel: [    0.118734] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ stepping 02
Jan 20 03:50:10 ubuntu kernel: [    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Initializing CPU#1
Jan 20 03:50:10 ubuntu kernel: [    0.010000] Calibrating delay using timer specific routine.. 5600.06 BogoMIPS (lpj=28000328)
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU 1/0x1 -> Node 0
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU: Physical Processor ID: 0
Jan 20 03:50:10 ubuntu kernel: [    0.010000] CPU: Processor Core ID: 1
Jan 20 03:50:10 ubuntu kernel: [    0.010000] mce: CPU supports 5 MCE banks
Jan 20 03:50:10 ubuntu kernel: [    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Jan 20 03:50:10 ubuntu kernel: [    0.270410] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ stepping 02
Jan 20 03:50:10 ubuntu kernel: [    0.270425] Brought up 2 CPUs
Jan 20 03:50:10 ubuntu kernel: [    0.270427] Total of 2 processors activated (11200.70 BogoMIPS).
Jan 20 03:50:10 ubuntu kernel: [    0.270520] CPU0 attaching sched-domain:
Jan 20 03:50:10 ubuntu kernel: [    0.270523]  domain 0: span 0-1 level MC
Jan 20 03:50:10 ubuntu kernel: [    0.270525]   groups: 0 1
Jan 20 03:50:10 ubuntu kernel: [    0.270529] CPU1 attaching sched-domain:
Jan 20 03:50:10 ubuntu kernel: [    0.270530]  domain 0: span 0-1 level MC
Jan 20 03:50:10 ubuntu kernel: [    0.270532]   groups: 1 0
Jan 20 03:50:10 ubuntu kernel: [    0.270590] Booting paravirtualized kernel on bare hardware
Jan 20 03:50:10 ubuntu kernel: [    0.270590] regulator: core version 0.5
Jan 20 03:50:10 ubuntu kernel: [    0.270590] Time:  3:48:30  Date: 01/20/10
Jan 20 03:50:10 ubuntu kernel: [    0.270590] NET: Registered protocol family 16
Jan 20 03:50:10 ubuntu kernel: [    0.270590] node 0 link 0: io port [1000, ffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.270590] node 0 link 0: io port [2000, 2fff]
Jan 20 03:50:10 ubuntu kernel: [    0.270590] TOM: 00000000c0000000 aka 3072M
Jan 20 03:50:10 ubuntu kernel: [    0.270590] node 0 link 0: mmio [e0000000, efffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.270590] node 0 link 0: mmio [a0000, bffff]
Jan 20 03:50:10 ubuntu kernel: [    0.270590] node 0 link 0: mmio [c0000000, fe0bffff]
Jan 20 03:50:10 ubuntu kernel: [    0.270590] bus: [00,07] on node 0 link 0
Jan 20 03:50:10 ubuntu kernel: [    0.270590] bus: 00 index 0 io port: [0, ffff]
Jan 20 03:50:10 ubuntu kernel: [    0.270590] bus: 00 index 1 mmio: [c0000000, fcffffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.270590] bus: 00 index 2 mmio: [a0000, bffff]
Jan 20 03:50:10 ubuntu kernel: [    0.270590] ACPI: bus type pci registered
Jan 20 03:50:10 ubuntu kernel: [    0.270590] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jan 20 03:50:10 ubuntu kernel: [    0.270590] PCI: Not using MMCONFIG.
Jan 20 03:50:10 ubuntu kernel: [    0.270590] PCI: Using configuration type 1 for base access
Jan 20 03:50:10 ubuntu kernel: [    0.270891] bio: create slab <bio-0> at 0
Jan 20 03:50:10 ubuntu kernel: [    0.270891] ACPI: EC: Look up EC in DSDT
Jan 20 03:50:10 ubuntu kernel: [    0.285345] ACPI: Interpreter enabled
Jan 20 03:50:10 ubuntu kernel: [    0.285348] ACPI: (supports S0 S1 S3 S4 S5)
Jan 20 03:50:10 ubuntu kernel: [    0.285365] ACPI: Using IOAPIC for interrupt routing
Jan 20 03:50:10 ubuntu kernel: [    0.285419] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jan 20 03:50:10 ubuntu kernel: [    0.291275] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jan 20 03:50:10 ubuntu kernel: [    0.295770] PCI: Using MMCONFIG at e0000000 - efffffff
Jan 20 03:50:10 ubuntu kernel: [    0.308083] ACPI Warning: Incorrect checksum in table [OEMB] - 37, should be 36 20090521 tbutils-246
Jan 20 03:50:10 ubuntu kernel: [    0.308301] ACPI: No dock devices found.
Jan 20 03:50:10 ubuntu kernel: [    0.308669] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 20 03:50:10 ubuntu kernel: [    0.308936] pci 0000:00:01.0: reg 10 io port: [0x2f00-0x2fff]
Jan 20 03:50:10 ubuntu kernel: [    0.308976] pci 0000:00:01.1: reg 10 io port: [0x2900-0x293f]
Jan 20 03:50:10 ubuntu kernel: [    0.308986] pci 0000:00:01.1: reg 20 io port: [0x2d00-0x2d3f]
Jan 20 03:50:10 ubuntu kernel: [    0.308990] pci 0000:00:01.1: reg 24 io port: [0x2e00-0x2e3f]
Jan 20 03:50:10 ubuntu kernel: [    0.309010] pci 0000:00:01.1: PME# supported from D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.309015] pci 0000:00:01.1: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.309072] pci 0000:00:01.3: reg 10 32bit mmio: [0xf9f80000-0xf9ffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.309199] pci 0000:00:02.0: reg 10 32bit mmio: [0xf9f7f000-0xf9f7ffff]
Jan 20 03:50:10 ubuntu kernel: [    0.309222] pci 0000:00:02.0: supports D1 D2
Jan 20 03:50:10 ubuntu kernel: [    0.309224] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.309226] pci 0000:00:02.0: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.309249] pci 0000:00:02.1: reg 10 32bit mmio: [0xf9f7ec00-0xf9f7ecff]
Jan 20 03:50:10 ubuntu kernel: [    0.309277] pci 0000:00:02.1: supports D1 D2
Jan 20 03:50:10 ubuntu kernel: [    0.309278] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.309281] pci 0000:00:02.1: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.309310] pci 0000:00:04.0: reg 10 32bit mmio: [0xf9f7d000-0xf9f7dfff]
Jan 20 03:50:10 ubuntu kernel: [    0.309333] pci 0000:00:04.0: supports D1 D2
Jan 20 03:50:10 ubuntu kernel: [    0.309335] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.309338] pci 0000:00:04.0: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.309361] pci 0000:00:04.1: reg 10 32bit mmio: [0xf9f7e800-0xf9f7e8ff]
Jan 20 03:50:10 ubuntu kernel: [    0.309388] pci 0000:00:04.1: supports D1 D2
Jan 20 03:50:10 ubuntu kernel: [    0.309390] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.309393] pci 0000:00:04.1: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.309427] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
Jan 20 03:50:10 ubuntu kernel: [    0.309465] pci 0000:00:07.0: reg 10 32bit mmio: [0xf9f78000-0xf9f7bfff]
Jan 20 03:50:10 ubuntu kernel: [    0.309493] pci 0000:00:07.0: PME# supported from D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.309495] pci 0000:00:07.0: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.309548] pci 0000:00:09.0: reg 10 io port: [0xc080-0xc087]
Jan 20 03:50:10 ubuntu kernel: [    0.309551] pci 0000:00:09.0: reg 14 io port: [0xc000-0xc003]
Jan 20 03:50:10 ubuntu kernel: [    0.309554] pci 0000:00:09.0: reg 18 io port: [0xbc00-0xbc07]
Jan 20 03:50:10 ubuntu kernel: [    0.309558] pci 0000:00:09.0: reg 1c io port: [0xb880-0xb883]
Jan 20 03:50:10 ubuntu kernel: [    0.309561] pci 0000:00:09.0: reg 20 io port: [0xb800-0xb80f]
Jan 20 03:50:10 ubuntu kernel: [    0.309565] pci 0000:00:09.0: reg 24 32bit mmio: [0xf9f76000-0xf9f77fff]
Jan 20 03:50:10 ubuntu kernel: [    0.309785] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.309792] pci 0000:00:10.0: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.310059] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.310066] pci 0000:00:12.0: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.310302] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.310309] pci 0000:00:13.0: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.310546] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.310553] pci 0000:00:14.0: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.310680] pci 0000:00:08.0: transparent bridge
Jan 20 03:50:10 ubuntu kernel: [    0.310714] pci 0000:02:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.310721] pci 0000:02:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.310728] pci 0000:02:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.310733] pci 0000:02:00.0: reg 24 io port: [0xdc00-0xdc7f]
Jan 20 03:50:10 ubuntu kernel: [    0.310737] pci 0000:02:00.0: reg 30 32bit mmio: [0xfeae0000-0xfeafffff]
Jan 20 03:50:10 ubuntu kernel: [    0.310804] pci 0000:00:10.0: bridge io port: [0xd000-0xdfff]
Jan 20 03:50:10 ubuntu kernel: [    0.310811] pci 0000:00:10.0: bridge 32bit mmio: [0xfa000000-0xfeafffff]
Jan 20 03:50:10 ubuntu kernel: [    0.310825] pci 0000:00:10.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.310946] pci 0000:04:00.0: reg 10 64bit mmio: [0xfebfc000-0xfebfffff]
Jan 20 03:50:10 ubuntu kernel: [    0.310953] pci 0000:04:00.0: reg 18 io port: [0xe800-0xe8ff]
Jan 20 03:50:10 ubuntu kernel: [    0.310971] pci 0000:04:00.0: reg 30 32bit mmio: [0xfebc0000-0xfebdffff]
Jan 20 03:50:10 ubuntu kernel: [    0.310999] pci 0000:04:00.0: supports D1 D2
Jan 20 03:50:10 ubuntu kernel: [    0.311000] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 20 03:50:10 ubuntu kernel: [    0.311004] pci 0000:04:00.0: PME# disabled
Jan 20 03:50:10 ubuntu kernel: [    0.311054] pci 0000:00:13.0: bridge io port: [0xe000-0xefff]
Jan 20 03:50:10 ubuntu kernel: [    0.311061] pci 0000:00:13.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
Jan 20 03:50:10 ubuntu kernel: [    0.311195] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 20 03:50:10 ubuntu kernel: [    0.311466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Jan 20 03:50:10 ubuntu kernel: [    0.311573] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MXR0._PRT]
Jan 20 03:50:10 ubuntu kernel: [    0.311630] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
Jan 20 03:50:10 ubuntu kernel: [    0.311684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
Jan 20 03:50:10 ubuntu kernel: [    0.311739] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
Jan 20 03:50:10 ubuntu kernel: [    0.325182] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.325403] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.325623] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.325841] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.326064] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *10
Jan 20 03:50:10 ubuntu kernel: [    0.326283] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.326507] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.326726] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.326945] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.327164] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.327387] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.327606] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.327829] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *11
Jan 20 03:50:10 ubuntu kernel: [    0.328047] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.328267] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.328486] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.328709] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *15
Jan 20 03:50:10 ubuntu kernel: [    0.328929] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.329149] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.329368] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.329592] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *7
Jan 20 03:50:10 ubuntu kernel: [    0.329812] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.330054] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.330275] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.330494] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.330714] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.330933] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.331154] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.331375] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.331595] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.331816] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.332043] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.332268] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.332487] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.332708] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.332928] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.333151] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *15
Jan 20 03:50:10 ubuntu kernel: [    0.333374] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
Jan 20 03:50:10 ubuntu kernel: [    0.333594] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.333817] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *15
Jan 20 03:50:10 ubuntu kernel: [    0.334037] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.334260] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
Jan 20 03:50:10 ubuntu kernel: [    0.334483] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11
Jan 20 03:50:10 ubuntu kernel: [    0.334706] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
Jan 20 03:50:10 ubuntu kernel: [    0.334962] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Jan 20 03:50:10 ubuntu kernel: [    0.335186] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *10
Jan 20 03:50:10 ubuntu kernel: [    0.335410] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *11
Jan 20 03:50:10 ubuntu kernel: [    0.335573] SCSI subsystem initialized
Jan 20 03:50:10 ubuntu kernel: [    0.335627] libata version 3.00 loaded.
Jan 20 03:50:10 ubuntu kernel: [    0.335627] usbcore: registered new interface driver usbfs
Jan 20 03:50:10 ubuntu kernel: [    0.335627] usbcore: registered new interface driver hub
Jan 20 03:50:10 ubuntu kernel: [    0.335627] usbcore: registered new device driver usb
Jan 20 03:50:10 ubuntu kernel: [    0.335627] ACPI: WMI: Mapper loaded
Jan 20 03:50:10 ubuntu kernel: [    0.335627] PCI: Using ACPI for IRQ routing
Jan 20 03:50:10 ubuntu kernel: [    0.360006] Bluetooth: Core ver 2.15
Jan 20 03:50:10 ubuntu kernel: [    0.360021] NET: Registered protocol family 31
Jan 20 03:50:10 ubuntu kernel: [    0.360021] Bluetooth: HCI device and connection manager initialized
Jan 20 03:50:10 ubuntu kernel: [    0.360021] Bluetooth: HCI socket layer initialized
Jan 20 03:50:10 ubuntu kernel: [    0.360021] NetLabel: Initializing
Jan 20 03:50:10 ubuntu kernel: [    0.360021] NetLabel:  domain hash size = 128
Jan 20 03:50:10 ubuntu kernel: [    0.360021] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 20 03:50:10 ubuntu kernel: [    0.360037] NetLabel:  unlabeled traffic allowed by default
Jan 20 03:50:10 ubuntu kernel: [    0.360320] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Jan 20 03:50:10 ubuntu kernel: [    0.360323] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Jan 20 03:50:10 ubuntu kernel: [    0.380018] Switched to high resolution mode on CPU 0
Jan 20 03:50:10 ubuntu kernel: [    0.380390] Switched to high resolution mode on CPU 1
Jan 20 03:50:10 ubuntu kernel: [    0.400019] pnp: PnP ACPI init
Jan 20 03:50:10 ubuntu kernel: [    0.400036] ACPI: bus type pnp registered
Jan 20 03:50:10 ubuntu kernel: [    0.405991] pnp: PnP ACPI: found 13 devices
Jan 20 03:50:10 ubuntu kernel: [    0.405993] ACPI: ACPI bus type pnp unregistered
Jan 20 03:50:10 ubuntu kernel: [    0.406004] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406006] system 00:05: ioport range 0x800-0x80f has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406009] system 00:05: ioport range 0x2000-0x207f has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406011] system 00:05: ioport range 0x2080-0x20ff has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406013] system 00:05: ioport range 0x2400-0x247f has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406015] system 00:05: ioport range 0x2480-0x24ff has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406017] system 00:05: ioport range 0x2800-0x287f has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406019] system 00:05: ioport range 0x2880-0x28ff has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406026] system 00:05: iomem range 0xfed04000-0xfed04fff has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406029] system 00:05: iomem range 0xfee01000-0xfeefffff has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406033] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406036] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406040] system 00:0a: ioport range 0xa00-0xa0f has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406042] system 00:0a: ioport range 0xa10-0xa1f has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406046] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406050] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406052] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406054] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406057] system 00:0c: iomem range 0x100000-0xbfffffff could not be reserved
Jan 20 03:50:10 ubuntu kernel: [    0.406059] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
Jan 20 03:50:10 ubuntu kernel: [    0.410735] AppArmor: AppArmor Filesystem Enabled
Jan 20 03:50:10 ubuntu kernel: [    0.410830] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
Jan 20 03:50:10 ubuntu kernel: [    0.410832] pci 0000:00:08.0:   IO window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410835] pci 0000:00:08.0:   MEM window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410838] pci 0000:00:08.0:   PREFETCH window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410841] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
Jan 20 03:50:10 ubuntu kernel: [    0.410846] pci 0000:00:10.0:   IO window: 0xd000-0xdfff
Jan 20 03:50:10 ubuntu kernel: [    0.410856] pci 0000:00:10.0:   MEM window: 0xfa000000-0xfeafffff
Jan 20 03:50:10 ubuntu kernel: [    0.410863] pci 0000:00:10.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jan 20 03:50:10 ubuntu kernel: [    0.410876] pci 0000:00:12.0: PCI bridge, secondary bus 0000:03
Jan 20 03:50:10 ubuntu kernel: [    0.410877] pci 0000:00:12.0:   IO window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410886] pci 0000:00:12.0:   MEM window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410893] pci 0000:00:12.0:   PREFETCH window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410900] pci 0000:00:13.0: PCI bridge, secondary bus 0000:04
Jan 20 03:50:10 ubuntu kernel: [    0.410905] pci 0000:00:13.0:   IO window: 0xe000-0xefff
Jan 20 03:50:10 ubuntu kernel: [    0.410914] pci 0000:00:13.0:   MEM window: 0xfeb00000-0xfebfffff
Jan 20 03:50:10 ubuntu kernel: [    0.410921] pci 0000:00:13.0:   PREFETCH window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410928] pci 0000:00:14.0: PCI bridge, secondary bus 0000:05
Jan 20 03:50:10 ubuntu kernel: [    0.410929] pci 0000:00:14.0:   IO window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410938] pci 0000:00:14.0:   MEM window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410945] pci 0000:00:14.0:   PREFETCH window: disabled
Jan 20 03:50:10 ubuntu kernel: [    0.410957] pci 0000:00:08.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    0.411299] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
Jan 20 03:50:10 ubuntu kernel: [    0.411302]   alloc irq_desc for 19 on node 0
Jan 20 03:50:10 ubuntu kernel: [    0.411303]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    0.411312] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
Jan 20 03:50:10 ubuntu kernel: [    0.411320] pci 0000:00:10.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    0.411645] ACPI: PCI Interrupt Link [LN2A] enabled at IRQ 18
Jan 20 03:50:10 ubuntu kernel: [    0.411647]   alloc irq_desc for 18 on node 0
Jan 20 03:50:10 ubuntu kernel: [    0.411649]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    0.411655] pci 0000:00:12.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
Jan 20 03:50:10 ubuntu kernel: [    0.411663] pci 0000:00:12.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    0.411988] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 17
Jan 20 03:50:10 ubuntu kernel: [    0.411990]   alloc irq_desc for 17 on node 0
Jan 20 03:50:10 ubuntu kernel: [    0.411991]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    0.411998] pci 0000:00:13.0: PCI INT A -> Link[LN3A] -> GSI 17 (level, low) -> IRQ 17
Jan 20 03:50:10 ubuntu kernel: [    0.412005] pci 0000:00:13.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    0.412331] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 16
Jan 20 03:50:10 ubuntu kernel: [    0.412333]   alloc irq_desc for 16 on node 0
Jan 20 03:50:10 ubuntu kernel: [    0.412334]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    0.412340] pci 0000:00:14.0: PCI INT A -> Link[LN4A] -> GSI 16 (level, low) -> IRQ 16
Jan 20 03:50:10 ubuntu kernel: [    0.412348] pci 0000:00:14.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    0.412354] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jan 20 03:50:10 ubuntu kernel: [    0.412356] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.412359] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
Jan 20 03:50:10 ubuntu kernel: [    0.412361] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.412363] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
Jan 20 03:50:10 ubuntu kernel: [    0.412365] pci_bus 0000:02: resource 1 mem: [0xfa000000-0xfeafffff]
Jan 20 03:50:10 ubuntu kernel: [    0.412366] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
Jan 20 03:50:10 ubuntu kernel: [    0.412369] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
Jan 20 03:50:10 ubuntu kernel: [    0.412371] pci_bus 0000:04: resource 1 mem: [0xfeb00000-0xfebfffff]
Jan 20 03:50:10 ubuntu kernel: [    0.412406] NET: Registered protocol family 2
Jan 20 03:50:10 ubuntu kernel: [    0.412546] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 20 03:50:10 ubuntu kernel: [    0.414050] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jan 20 03:50:10 ubuntu kernel: [    0.419635] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jan 20 03:50:10 ubuntu kernel: [    0.420326] TCP: Hash tables configured (established 524288 bind 65536)
Jan 20 03:50:10 ubuntu kernel: [    0.420329] TCP reno registered
Jan 20 03:50:10 ubuntu kernel: [    0.420437] NET: Registered protocol family 1
Jan 20 03:50:10 ubuntu kernel: [    0.420496] Trying to unpack rootfs image as initramfs...
Jan 20 03:50:10 ubuntu kernel: [    1.557438] Freeing initrd memory: 5705k freed
Jan 20 03:50:10 ubuntu kernel: [    1.560784] Scanning for low memory corruption every 60 seconds
Jan 20 03:50:10 ubuntu kernel: [    1.560904] audit: initializing netlink socket (disabled)
Jan 20 03:50:10 ubuntu kernel: [    1.560921] type=2000 audit(1263959311.560:1): initialized
Jan 20 03:50:10 ubuntu kernel: [    1.567832] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan 20 03:50:10 ubuntu kernel: [    1.568941] VFS: Disk quotas dquot_6.5.2
Jan 20 03:50:10 ubuntu kernel: [    1.568987] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan 20 03:50:10 ubuntu kernel: [    1.569489] fuse init (API version 7.12)
Jan 20 03:50:10 ubuntu kernel: [    1.569551] msgmni has been set to 6037
Jan 20 03:50:10 ubuntu kernel: [    1.569785] alg: No test for stdrng (krng)
Jan 20 03:50:10 ubuntu kernel: [    1.569807] io scheduler noop registered
Jan 20 03:50:10 ubuntu kernel: [    1.569808] io scheduler anticipatory registered
Jan 20 03:50:10 ubuntu kernel: [    1.569810] io scheduler deadline registered
Jan 20 03:50:10 ubuntu kernel: [    1.569842] io scheduler cfq registered (default)
Jan 20 03:50:10 ubuntu kernel: [    1.600127] pci 0000:00:07.0: Enabling HT MSI Mapping
Jan 20 03:50:10 ubuntu kernel: [    1.600227] pci 0000:00:08.0: Enabling HT MSI Mapping
Jan 20 03:50:10 ubuntu kernel: [    1.600465] pci 0000:02:00.0: Boot video device
Jan 20 03:50:10 ubuntu kernel: [    1.600776]   alloc irq_desc for 24 on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.600778]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.600798] pcieport-driver 0000:00:10.0: irq 24 for MSI/MSI-X
Jan 20 03:50:10 ubuntu kernel: [    1.600818] pcieport-driver 0000:00:10.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.601221]   alloc irq_desc for 25 on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.601222]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.601238] pcieport-driver 0000:00:12.0: irq 25 for MSI/MSI-X
Jan 20 03:50:10 ubuntu kernel: [    1.601257] pcieport-driver 0000:00:12.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.601645]   alloc irq_desc for 26 on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.601647]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.601662] pcieport-driver 0000:00:13.0: irq 26 for MSI/MSI-X
Jan 20 03:50:10 ubuntu kernel: [    1.601681] pcieport-driver 0000:00:13.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.602066]   alloc irq_desc for 27 on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.602068]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.602083] pcieport-driver 0000:00:14.0: irq 27 for MSI/MSI-X
Jan 20 03:50:10 ubuntu kernel: [    1.602102] pcieport-driver 0000:00:14.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.602260] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 20 03:50:10 ubuntu kernel: [    1.602280] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan 20 03:50:10 ubuntu kernel: [    1.602397] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Jan 20 03:50:10 ubuntu kernel: [    1.602400] ACPI: Power Button [PWRF]
Jan 20 03:50:10 ubuntu kernel: [    1.602458] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Jan 20 03:50:10 ubuntu kernel: [    1.602464] ACPI: Power Button [PWRB]
Jan 20 03:50:10 ubuntu kernel: [    1.602782] processor LNXCPU:00: registered as cooling_device0
Jan 20 03:50:10 ubuntu kernel: [    1.602812] processor LNXCPU:01: registered as cooling_device1
Jan 20 03:50:10 ubuntu kernel: [    1.609234] Linux agpgart interface v0.103
Jan 20 03:50:10 ubuntu kernel: [    1.609245] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jan 20 03:50:10 ubuntu kernel: [    1.609345] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 20 03:50:10 ubuntu kernel: [    1.609558] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 20 03:50:10 ubuntu kernel: [    1.610684] brd: module loaded
Jan 20 03:50:10 ubuntu kernel: [    1.611048] loop: module loaded
Jan 20 03:50:10 ubuntu kernel: [    1.611125] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jan 20 03:50:10 ubuntu kernel: [    1.611251] ahci 0000:00:09.0: version 3.0
Jan 20 03:50:10 ubuntu kernel: [    1.611647] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
Jan 20 03:50:10 ubuntu kernel: [    1.611651]   alloc irq_desc for 23 on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.611652]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.611662] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
Jan 20 03:50:10 ubuntu kernel: [    1.611700]   alloc irq_desc for 28 on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.611702]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.611708] ahci 0000:00:09.0: irq 28 for MSI/MSI-X
Jan 20 03:50:10 ubuntu kernel: [    1.611798] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Jan 20 03:50:10 ubuntu kernel: [    1.611801] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
Jan 20 03:50:10 ubuntu kernel: [    1.611803] ahci 0000:00:09.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.612403] scsi0 : ahci
Jan 20 03:50:10 ubuntu kernel: [    1.612533] scsi1 : ahci
Jan 20 03:50:10 ubuntu kernel: [    1.612589] scsi2 : ahci
Jan 20 03:50:10 ubuntu kernel: [    1.612646] scsi3 : ahci
Jan 20 03:50:10 ubuntu kernel: [    1.612700] scsi4 : ahci
Jan 20 03:50:10 ubuntu kernel: [    1.612756] scsi5 : ahci
Jan 20 03:50:10 ubuntu kernel: [    1.612865] ata1: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 28
Jan 20 03:50:10 ubuntu kernel: [    1.612868] ata2: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76180 irq 28
Jan 20 03:50:10 ubuntu kernel: [    1.612870] ata3: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76200 irq 28
Jan 20 03:50:10 ubuntu kernel: [    1.612873] ata4: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76280 irq 28
Jan 20 03:50:10 ubuntu kernel: [    1.612875] ata5: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76300 irq 28
Jan 20 03:50:10 ubuntu kernel: [    1.612877] ata6: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76380 irq 28
Jan 20 03:50:10 ubuntu kernel: [    1.613115] pata_amd 0000:00:06.0: version 0.4.1
Jan 20 03:50:10 ubuntu kernel: [    1.613154] pata_amd 0000:00:06.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.613233] scsi6 : pata_amd
Jan 20 03:50:10 ubuntu kernel: [    1.613289] scsi7 : pata_amd
Jan 20 03:50:10 ubuntu kernel: [    1.614429] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jan 20 03:50:10 ubuntu kernel: [    1.614432] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jan 20 03:50:10 ubuntu kernel: [    1.614959] Fixed MDIO Bus: probed
Jan 20 03:50:10 ubuntu kernel: [    1.614985] PPP generic driver version 2.4.2
Jan 20 03:50:10 ubuntu kernel: [    1.615080] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan 20 03:50:10 ubuntu kernel: [    1.615498] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
Jan 20 03:50:10 ubuntu kernel: [    1.615502]   alloc irq_desc for 22 on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.615504]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.615514] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
Jan 20 03:50:10 ubuntu kernel: [    1.615534] ehci_hcd 0000:00:02.1: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.615536] ehci_hcd 0000:00:02.1: EHCI Host Controller
Jan 20 03:50:10 ubuntu kernel: [    1.615584] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Jan 20 03:50:10 ubuntu kernel: [    1.615615] ehci_hcd 0000:00:02.1: debug port 1
Jan 20 03:50:10 ubuntu kernel: [    1.615618] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Jan 20 03:50:10 ubuntu kernel: [    1.615641] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf9f7ec00
Jan 20 03:50:10 ubuntu kernel: [    1.630020] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Jan 20 03:50:10 ubuntu kernel: [    1.630079] usb usb1: configuration #1 chosen from 1 choice
Jan 20 03:50:10 ubuntu kernel: [    1.630102] hub 1-0:1.0: USB hub found
Jan 20 03:50:10 ubuntu kernel: [    1.630109] hub 1-0:1.0: 6 ports detected
Jan 20 03:50:10 ubuntu kernel: [    1.630558] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
Jan 20 03:50:10 ubuntu kernel: [    1.630561]   alloc irq_desc for 21 on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.630562]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.630569] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
Jan 20 03:50:10 ubuntu kernel: [    1.630579] ehci_hcd 0000:00:04.1: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.630582] ehci_hcd 0000:00:04.1: EHCI Host Controller
Jan 20 03:50:10 ubuntu kernel: [    1.630620] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
Jan 20 03:50:10 ubuntu kernel: [    1.630645] ehci_hcd 0000:00:04.1: debug port 1
Jan 20 03:50:10 ubuntu kernel: [    1.630649] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
Jan 20 03:50:10 ubuntu kernel: [    1.630666] ehci_hcd 0000:00:04.1: irq 21, io mem 0xf9f7e800
Jan 20 03:50:10 ubuntu kernel: [    1.650018] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
Jan 20 03:50:10 ubuntu kernel: [    1.650060] usb usb2: configuration #1 chosen from 1 choice
Jan 20 03:50:10 ubuntu kernel: [    1.650081] hub 2-0:1.0: USB hub found
Jan 20 03:50:10 ubuntu kernel: [    1.650087] hub 2-0:1.0: 6 ports detected
Jan 20 03:50:10 ubuntu kernel: [    1.650144] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 20 03:50:10 ubuntu kernel: [    1.650545] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
Jan 20 03:50:10 ubuntu kernel: [    1.650547]   alloc irq_desc for 20 on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.650549]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [    1.650556] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
Jan 20 03:50:10 ubuntu kernel: [    1.650566] ohci_hcd 0000:00:02.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.650568] ohci_hcd 0000:00:02.0: OHCI Host Controller
Jan 20 03:50:10 ubuntu kernel: [    1.650599] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
Jan 20 03:50:10 ubuntu kernel: [    1.650623] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf9f7f000
Jan 20 03:50:10 ubuntu kernel: [    1.712056] usb usb3: configuration #1 chosen from 1 choice
Jan 20 03:50:10 ubuntu kernel: [    1.712077] hub 3-0:1.0: USB hub found
Jan 20 03:50:10 ubuntu kernel: [    1.712085] hub 3-0:1.0: 6 ports detected
Jan 20 03:50:10 ubuntu kernel: [    1.712503] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 23
Jan 20 03:50:10 ubuntu kernel: [    1.712506] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 23 (level, low) -> IRQ 23
Jan 20 03:50:10 ubuntu kernel: [    1.712516] ohci_hcd 0000:00:04.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [    1.712518] ohci_hcd 0000:00:04.0: OHCI Host Controller
Jan 20 03:50:10 ubuntu kernel: [    1.712548] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
Jan 20 03:50:10 ubuntu kernel: [    1.712570] ohci_hcd 0000:00:04.0: irq 23, io mem 0xf9f7d000
Jan 20 03:50:10 ubuntu kernel: [    1.772240] usb usb4: configuration #1 chosen from 1 choice
Jan 20 03:50:10 ubuntu kernel: [    1.772262] hub 4-0:1.0: USB hub found
Jan 20 03:50:10 ubuntu kernel: [    1.772269] hub 4-0:1.0: 6 ports detected
Jan 20 03:50:10 ubuntu kernel: [    1.772319] uhci_hcd: USB Universal Host Controller Interface driver
Jan 20 03:50:10 ubuntu kernel: [    1.772421] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jan 20 03:50:10 ubuntu kernel: [    1.772423] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jan 20 03:50:10 ubuntu kernel: [    1.772823] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 20 03:50:10 ubuntu kernel: [    1.772885] mice: PS/2 mouse device common for all mice
Jan 20 03:50:10 ubuntu kernel: [    1.772966] rtc_cmos 00:07: RTC can wake from S4
Jan 20 03:50:10 ubuntu kernel: [    1.772999] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Jan 20 03:50:10 ubuntu kernel: [    1.773052] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
Jan 20 03:50:10 ubuntu kernel: [    1.773138] device-mapper: uevent: version 1.0.3
Jan 20 03:50:10 ubuntu kernel: [    1.773233] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Jan 20 03:50:10 ubuntu kernel: [    1.773315] device-mapper: multipath: version 1.1.0 loaded
Jan 20 03:50:10 ubuntu kernel: [    1.773318] device-mapper: multipath round-robin: version 1.0.0 loaded
Jan 20 03:50:10 ubuntu kernel: [    1.773500] cpuidle: using governor ladder
Jan 20 03:50:10 ubuntu kernel: [    1.773501] cpuidle: using governor menu
Jan 20 03:50:10 ubuntu kernel: [    1.773841] TCP cubic registered
Jan 20 03:50:10 ubuntu kernel: [    1.773943] NET: Registered protocol family 10
Jan 20 03:50:10 ubuntu kernel: [    1.774315] lo: Disabled Privacy Extensions
Jan 20 03:50:10 ubuntu kernel: [    1.774527] NET: Registered protocol family 17
Jan 20 03:50:10 ubuntu kernel: [    1.774546] Bluetooth: L2CAP ver 2.13
Jan 20 03:50:10 ubuntu kernel: [    1.774548] Bluetooth: L2CAP socket layer initialized
Jan 20 03:50:10 ubuntu kernel: [    1.774551] Bluetooth: SCO (Voice Link) ver 0.6
Jan 20 03:50:10 ubuntu kernel: [    1.774552] Bluetooth: SCO socket layer initialized
Jan 20 03:50:10 ubuntu kernel: [    1.774601] Bluetooth: RFCOMM TTY layer initialized
Jan 20 03:50:10 ubuntu kernel: [    1.774604] Bluetooth: RFCOMM socket layer initialized
Jan 20 03:50:10 ubuntu kernel: [    1.774605] Bluetooth: RFCOMM ver 1.11
Jan 20 03:50:10 ubuntu kernel: [    1.774627] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ processors (2 cpu cores) (version 2.20.00)
Jan 20 03:50:10 ubuntu kernel: [    1.774637] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
Jan 20 03:50:10 ubuntu kernel: [    1.774638] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
Jan 20 03:50:10 ubuntu kernel: [    1.774724] PM: Resume from disk failed.
Jan 20 03:50:10 ubuntu kernel: [    1.774736] registered taskstats version 1
Jan 20 03:50:10 ubuntu kernel: [    1.774868]   Magic number: 10:573:816
Jan 20 03:50:10 ubuntu kernel: [    1.774999] rtc_cmos 00:07: setting system clock to 2010-01-20 03:48:32 UTC (1263959312)
Jan 20 03:50:10 ubuntu kernel: [    1.775002] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 20 03:50:10 ubuntu kernel: [    1.775003] EDD information not available.
Jan 20 03:50:10 ubuntu kernel: [    1.792100] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jan 20 03:50:10 ubuntu kernel: [    1.810332] ata7.00: ATAPI: SONY    DVD RW DW-Q28A, KFS1, max UDMA/66
Jan 20 03:50:10 ubuntu kernel: [    1.810355] ata7.01: ATAPI: HL-DT-STDVD-ROM GDR8163B, 0S24, max UDMA/66
Jan 20 03:50:10 ubuntu kernel: [    1.810374] ata7: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5c50000) ACPI=0x1f01f (30:30:0x15)
Jan 20 03:50:10 ubuntu kernel: [    1.810379] ata7: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5c50000) ACPI=0x1f01f (30:30:0x15)
Jan 20 03:50:10 ubuntu kernel: [    1.850277] ata7.00: configured for UDMA/66
Jan 20 03:50:10 ubuntu kernel: [    1.890252] ata7.01: configured for UDMA/66
Jan 20 03:50:10 ubuntu kernel: [    1.960020] ata3: SATA link down (SStatus 0 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [    1.960033] ata5: SATA link down (SStatus 0 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [    1.960050] ata4: SATA link down (SStatus 0 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [    1.960066] ata6: SATA link down (SStatus 0 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [    2.140016] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [    2.140026] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [    2.151262] usb 4-2: new low speed USB device using ohci_hcd and address 2
Jan 20 03:50:10 ubuntu kernel: [    2.378256] usb 4-2: configuration #1 chosen from 1 choice
Jan 20 03:50:10 ubuntu kernel: [    7.140018] ata2.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [    7.140022] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [    7.140029] ata1.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [    7.140033] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [    7.670018] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [    7.670025] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [   17.670015] ata2.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [   17.670018] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [   17.670021] ata2: limiting SATA link speed to 1.5 Gbps
Jan 20 03:50:10 ubuntu kernel: [   17.670027] ata1.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [   17.670030] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [   17.670032] ata1: limiting SATA link speed to 1.5 Gbps
Jan 20 03:50:10 ubuntu kernel: [   18.200016] ata2: SATA link up <unknown> (SStatus 103 SControl 310)
Jan 20 03:50:10 ubuntu kernel: [   23.240016] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 20 03:50:10 ubuntu kernel: [   48.200016] ata2.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [   48.200019] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [   48.730016] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 20 03:50:10 ubuntu kernel: [   53.240017] ata1.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [   53.240020] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [   53.770016] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 20 03:50:10 ubuntu kernel: [   53.770862] scsi 6:0:0:0: CD-ROM            SONY     DVD RW DW-Q28A   KFS1 PQ: 0 ANSI: 5
Jan 20 03:50:10 ubuntu kernel: [   53.772695] sr0: scsi3-mmc drive: 125x/125x writer cd/rw xa/form2 cdda tray
Jan 20 03:50:10 ubuntu kernel: [   53.772698] Uniform CD-ROM driver Revision: 3.20
Jan 20 03:50:10 ubuntu kernel: [   53.772775] sr 6:0:0:0: Attached scsi CD-ROM sr0
Jan 20 03:50:10 ubuntu kernel: [   53.772822] sr 6:0:0:0: Attached scsi generic sg0 type 5
Jan 20 03:50:10 ubuntu kernel: [   53.775741] scsi 6:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8163B 0S24 PQ: 0 ANSI: 5
Jan 20 03:50:10 ubuntu kernel: [   53.782894] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
Jan 20 03:50:10 ubuntu kernel: [   53.782945] sr 6:0:1:0: Attached scsi CD-ROM sr1
Jan 20 03:50:10 ubuntu kernel: [   53.782973] sr 6:0:1:0: Attached scsi generic sg1 type 5
Jan 20 03:50:10 ubuntu kernel: [   53.783007] ata8: port disabled. ignoring.
Jan 20 03:50:10 ubuntu kernel: [   53.783048] Freeing unused kernel memory: 660k freed
Jan 20 03:50:10 ubuntu kernel: [   53.783369] Write protecting the kernel read-only data: 7580k
Jan 20 03:50:10 ubuntu kernel: [   53.965530] sky2 driver version 1.23
Jan 20 03:50:10 ubuntu kernel: [   53.968934] sky2 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 17 (level, low) -> IRQ 17
Jan 20 03:50:10 ubuntu kernel: [   53.968948] sky2 0000:04:00.0: setting latency timer to 64
Jan 20 03:50:10 ubuntu kernel: [   53.968979] sky2 0000:04:00.0: Yukon-2 EC Ultra chip revision 5
Jan 20 03:50:10 ubuntu kernel: [   53.969048]   alloc irq_desc for 29 on node 0
Jan 20 03:50:10 ubuntu kernel: [   53.969050]   alloc kstat_irqs on node 0
Jan 20 03:50:10 ubuntu kernel: [   53.969062] sky2 0000:04:00.0: irq 29 for MSI/MSI-X
Jan 20 03:50:10 ubuntu kernel: [   53.969856] sky2 eth0: addr 00:e0:61:12:dd:32
Jan 20 03:50:10 ubuntu kernel: [   53.978045] usbcore: registered new interface driver hiddev
Jan 20 03:50:10 ubuntu kernel: [   53.984547] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.0/input/input4
Jan 20 03:50:10 ubuntu kernel: [   53.984617] generic-usb 0003:046D:C01E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:04.0-2/input0
Jan 20 03:50:10 ubuntu kernel: [   53.984633] usbcore: registered new interface driver usbhid
Jan 20 03:50:10 ubuntu kernel: [   53.984636] usbhid: v2.6:USB HID core driver
Jan 20 03:50:10 ubuntu kernel: [   55.167799] xor: automatically using best checksumming function: generic_sse
Jan 20 03:50:10 ubuntu kernel: [   55.211253]    generic_sse:  8758.800 MB/sec
Jan 20 03:50:10 ubuntu kernel: [   55.211255] xor: using function: generic_sse (8758.800 MB/sec)
Jan 20 03:50:10 ubuntu kernel: [   55.248099] device-mapper: dm-raid45: initialized v0.2594b
Jan 20 03:50:10 ubuntu kernel: [   57.948667] ISO 9660 Extensions: Microsoft Joliet Level 3
Jan 20 03:50:10 ubuntu kernel: [   58.094651] ISO 9660 Extensions: RRIP_1991A
Jan 20 03:50:10 ubuntu kernel: [   58.499631] aufs 2-standalone.tree-30-20090727
Jan 20 03:50:10 ubuntu kernel: [   58.560054] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Jan 20 03:50:10 ubuntu kernel: [   99.397676] udev: starting version 147
Jan 20 03:50:10 ubuntu kernel: [   99.704646] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2d00
Jan 20 03:50:10 ubuntu kernel: [   99.704652] ACPI: I/O resource nForce2_smbus [0x2e00-0x2e3f] conflicts with ACPI region SM00 [0x2e00-0x2e3f]
Jan 20 03:50:10 ubuntu kernel: [   99.704656] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 20 03:50:10 ubuntu kernel: [   99.704658] nForce2_smbus 0000:00:01.1: Error probing SMB2.
Jan 20 03:50:11 ubuntu kernel: [  100.497790] EDAC MC: Ver: 2.1.0 Oct 16 2009
Jan 20 03:50:11 ubuntu kernel: [  100.845182] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Jan 20 03:50:11 ubuntu kernel: [  100.853976] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
Jan 20 03:50:11 ubuntu kernel: [  100.857207] EDAC amd64: This node reports that Memory ECC is currently disabled.
Jan 20 03:50:11 ubuntu kernel: [  100.857213] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
Jan 20 03:50:11 ubuntu kernel: [  100.857215] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
Jan 20 03:50:11 ubuntu kernel: [  100.857217]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
Jan 20 03:50:11 ubuntu kernel: [  100.857218]     Might be a BIOS bug, if BIOS says ECC is enabled
Jan 20 03:50:11 ubuntu kernel: [  100.857218]     Use of the override can cause unknown side effects.
Jan 20 03:50:11 ubuntu kernel: [  100.857246] amd64_edac: probe of 0000:00:18.2 failed with error -22
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: Successfully dropped root privileges.
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: avahi-daemon 0.6.25 starting up.
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: Successfully called chroot().
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: Successfully dropped remaining capabilities.
Jan 20 03:50:12 ubuntu avahi-daemon[1724]: chroot.c: open() failed: No such file or directory
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: Failed to open /etc/resolv.conf: Invalid argument
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: No service file found in /etc/avahi/services.
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: Network interface enumeration completed.
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jan 20 03:50:12 ubuntu avahi-daemon[1722]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3233232540.
Jan 20 03:50:12 ubuntu kernel: [  101.909962] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 20 03:50:14 ubuntu NetworkManager: <info>  starting...
Jan 20 03:50:14 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Jan 20 03:50:15 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Jan 20 03:50:15 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jan 20 03:50:15 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jan 20 03:50:15 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.0/0000:04:00.0/net/eth0, iface: eth0)
Jan 20 03:50:15 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.0/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 20 03:50:15 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan 20 03:50:15 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan 20 03:50:15 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Jan 20 03:50:15 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan 20 03:50:15 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin Generic
Jan 20 03:50:15 ubuntu NetworkManager: <info>  Wireless now enabled by radio killswitch
Jan 20 03:50:15 ubuntu NetworkManager:    SCPlugin-Ifupdown: (14720096) ... get_connections.
Jan 20 03:50:15 ubuntu NetworkManager:    SCPlugin-Ifupdown: (14720096) ... get_connections (managed=false): return empty list.
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin Gobi
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin Option High-Speed
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin Huawei
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin Ericsson MBM
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin MotoC
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin Nokia
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin Novatel
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin Option
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin Sierra
Jan 20 03:50:15 ubuntu modem-manager: Loaded plugin ZTE
Jan 20 03:50:15 ubuntu kernel: [  105.244037] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
Jan 20 03:50:15 ubuntu kernel: [  105.244413] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
Jan 20 03:50:15 ubuntu kernel: [  105.244418] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
Jan 20 03:50:15 ubuntu kernel: [  105.244445] HDA Intel 0000:00:07.0: setting latency timer to 64
Jan 20 03:50:16 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jan 20 03:50:16 ubuntu kernel: [  105.456785] sky2 eth0: enabling interface
Jan 20 03:50:16 ubuntu kernel: [  105.457387] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 20 03:50:16 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Jan 20 03:50:16 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2')
Jan 20 03:50:16 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 20 03:50:16 ubuntu NetworkManager: <info>  (eth0): now managed
Jan 20 03:50:16 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan 20 03:50:16 ubuntu NetworkManager: <info>  (eth0): bringing up device.
Jan 20 03:50:16 ubuntu NetworkManager: <info>  (eth0): preparing device.
Jan 20 03:50:16 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan 20 03:50:16 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:13.0/0000:04:00.0/net/eth0
Jan 20 03:50:16 ubuntu NetworkManager: <info>  modem-manager is now available
Jan 20 03:50:16 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 20 03:50:16 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Jan 20 03:50:17 ubuntu kernel: [  106.710025] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
Jan 20 03:50:17 ubuntu kernel: [  106.750323] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input5
Jan 20 03:50:17 ubuntu cron[2006]: (CRON) INFO (pidfile fd = 3)
Jan 20 03:50:17 ubuntu cron[2049]: (CRON) STARTUP (fork ok)
Jan 20 03:50:17 ubuntu cron[2049]: (CRON) INFO (Running @reboot jobs)
Jan 20 03:50:18 ubuntu acpid: client connected from 2124[107:114]
Jan 20 03:50:18 ubuntu kernel: [  108.050618] lp: driver loaded but no devices found
Jan 20 03:50:19 ubuntu kernel: [  108.324895] ppdev: user-space parallel port driver
Jan 20 03:50:19 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jan 20 03:50:19 ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 20 03:50:19 ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 20 03:50:19 ubuntu NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 20 03:50:19 ubuntu NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 20 03:50:19 ubuntu kernel: [  108.442998] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan 20 03:50:19 ubuntu kernel: [  108.443690] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan 20 03:50:19 ubuntu NetworkManager: <info>  dhclient started with pid 2363
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 20 03:50:19 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 20 03:50:19 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan 20 03:50:19 ubuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan 20 03:50:19 ubuntu dhclient: All rights reserved.
Jan 20 03:50:19 ubuntu dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan 20 03:50:19 ubuntu dhclient: 
Jan 20 03:50:20 ubuntu avahi-daemon[1722]: Registering new address record for fe80::2e0:61ff:fe12:dd32 on eth0.*.
Jan 20 03:50:21 ubuntu udev-configure-printer: add /module/lp
Jan 20 03:50:21 ubuntu udev-configure-printer: Failed to get parent
Jan 20 03:50:21 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan 20 03:50:21 ubuntu dhclient: Listening on LPF/eth0/00:e0:61:12:dd:32
Jan 20 03:50:21 ubuntu dhclient: Sending on   LPF/eth0/00:e0:61:12:dd:32
Jan 20 03:50:21 ubuntu dhclient: Sending on   Socket/fallback
Jan 20 03:50:21 ubuntu init: ubiquity main process (2475) terminated with status 1
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb3
Jan 20 03:50:22 ubuntu udev-configure-printer: Failed to get parent
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0
Jan 20 03:50:22 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb3
Jan 20 03:50:22 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4/4-2
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.0
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:04.1/usb2
Jan 20 03:50:22 ubuntu console-kit-daemon[1804]: WARNING: Couldn't read /proc/1743/environ: Failed to open file '/proc/1743/environ': No such file or directory
Jan 20 03:50:22 ubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0
Jan 20 03:50:22 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 20 03:50:22 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:04.1/usb2
Jan 20 03:50:22 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 20 03:50:22 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 20 03:50:22 ubuntu udev-configure-printer: Failed to get parent
Jan 20 03:50:22 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.1/usb1
Jan 20 03:50:22 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 20 03:50:22 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 20 03:50:22 ubuntu udev-configure-printer: Failed to get parent
Jan 20 03:50:22 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:04.0/usb4
Jan 20 03:50:22 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 20 03:50:22 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 20 03:50:22 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:04.0/usb4
Jan 20 03:50:22 ubuntu udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 20 03:50:22 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 20 03:50:22 ubuntu udev-configure-printer: Failed to get parent
Jan 20 03:50:22 ubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:04.0/usb4/4-2
Jan 20 03:50:22 ubuntu udev-configure-printer: Device vendor/product is 046D:C01E
Jan 20 03:50:22 ubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 20 03:50:22 ubuntu kernel: [  111.722922] usplash:412 freeing invalid memtype fffffffffb000000-fffffffffbe00000
Jan 20 03:50:22 ubuntu gdm-binary[2487]: WARNING: Unable to find users: no seat-id found
Jan 20 03:50:23 ubuntu acpid: client connected from 2692[0:0]
Jan 20 03:50:24 ubuntu kernel: [  114.038917] CPU0 attaching NULL sched-domain.
Jan 20 03:50:24 ubuntu kernel: [  114.038926] CPU1 attaching NULL sched-domain.
Jan 20 03:50:24 ubuntu kernel: [  114.060308] CPU0 attaching sched-domain:
Jan 20 03:50:24 ubuntu kernel: [  114.060313]  domain 0: span 0-1 level MC
Jan 20 03:50:24 ubuntu kernel: [  114.060315]   groups: 0 1
Jan 20 03:50:24 ubuntu kernel: [  114.060318]   domain 1: span 0-1 level CPU
Jan 20 03:50:24 ubuntu kernel: [  114.060320]    groups: 0-1 (__cpu_power = 2048)
Jan 20 03:50:24 ubuntu kernel: [  114.060325] CPU1 attaching sched-domain:
Jan 20 03:50:24 ubuntu kernel: [  114.060326]  domain 0: span 0-1 level MC
Jan 20 03:50:24 ubuntu kernel: [  114.060327]   groups: 1 0
Jan 20 03:50:24 ubuntu kernel: [  114.060330]   domain 1: span 0-1 level CPU
Jan 20 03:50:24 ubuntu kernel: [  114.060331]    groups: 0-1 (__cpu_power = 2048)
Jan 20 03:50:25 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan 20 03:50:26 ubuntu dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Jan 20 03:50:26 ubuntu dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Jan 20 03:50:26 ubuntu dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Jan 20 03:50:26 ubuntu dhclient: bound to 192.168.2.2 -- renewal in 14989133 seconds.
Jan 20 03:50:26 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan 20 03:50:26 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 20 03:50:26 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 20 03:50:26 ubuntu NetworkManager: <info>    address 192.168.2.2
Jan 20 03:50:26 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Jan 20 03:50:26 ubuntu NetworkManager: <info>    gateway 192.168.2.1
Jan 20 03:50:26 ubuntu NetworkManager: <info>    nameserver '192.168.2.1'
Jan 20 03:50:26 ubuntu NetworkManager: <info>    domain name 'Belkin'
Jan 20 03:50:26 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 20 03:50:26 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 20 03:50:26 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 20 03:50:26 ubuntu avahi-daemon[1722]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Jan 20 03:50:26 ubuntu avahi-daemon[1722]: New relevant interface eth0.IPv4 for mDNS.
Jan 20 03:50:26 ubuntu avahi-daemon[1722]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Jan 20 03:50:27 ubuntu NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jan 20 03:50:27 ubuntu NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 20 03:50:27 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated.
Jan 20 03:50:27 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 20 03:50:29 ubuntu kernel: [  118.671263] eth0: no IPv6 routers present
Jan 20 03:50:31 ubuntu ntpdate[3144]: step time server 91.189.94.4 offset 1.344647 sec
Jan 20 03:50:35 ubuntu kernel: [  123.909440] CPU0 attaching NULL sched-domain.
Jan 20 03:50:35 ubuntu kernel: [  123.909448] CPU1 attaching NULL sched-domain.
Jan 20 03:50:36 ubuntu kernel: [  123.940115] CPU0 attaching sched-domain:
Jan 20 03:50:36 ubuntu kernel: [  123.940120]  domain 0: span 0-1 level MC
Jan 20 03:50:36 ubuntu kernel: [  123.940122]   groups: 0 1
Jan 20 03:50:36 ubuntu kernel: [  123.940127] CPU1 attaching sched-domain:
Jan 20 03:50:36 ubuntu kernel: [  123.940129]  domain 0: span 0-1 level MC
Jan 20 03:50:36 ubuntu kernel: [  123.940130]   groups: 1 0


Couldnt find a partman log in the viewer.
Also sudo fdisk -l returns no response

---

### Post by neamhaol on 2010-01-19
As for the second post, I made sure all raid settings were disabled. 
No, option found to not load raid drivers on alternate cd, after selecting keyboard it goes straight into disk utility where I get a no drives detected message along with a list of available drivers to load.

---

### Post by neamhaol on 2010-01-19
Ok, i hooked up an external hdd which is a usb device with an ide cable to connect a hdd.
Ubuntu installs on this, still no sata drives found. At least I got it installed though. I now have a sudo fdisk -l return which is below

Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000da6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2388    19181578+  83  Linux
/dev/sda2            2389        2498      883575    5  Extended
/dev/sda5            2389        2498      883543+  82  Linux swap / Solaris

This is the pos i can install on.

No sata shown. Fedora 10 recognizes right out of the box. Doesnt Ubuntu have the same drivers preloaded?

---

### Post by neamhaol on 2010-01-19
I guess another question would be, is it possible to copy the entire OS onto the sata drive and boot from it? Or would it boot and then not see what its even installed on?

---

### Post by lidex on 2010-01-20
I have a hunch it has something to do with your partition table. In a live session, does nautilus see the partitions? Can you get a fdisk or equivalent output from within fedora?

---

### Post by lidex on 2010-01-20
Go here and download TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")
It should be able to figure out disk errors.

Interesting thread here:
[http://ubuntuforums.org/showthread.php?t=766355]("http://ubuntuforums.org/showthread.php?t=766355")

---

### Post by neamhaol on 2010-01-20
My fedora fdisk -l
First is the hd I want ubuntu to see, second is the one ubuntu will actually see


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b769

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26       60801   488183220   8e  Linux LVM

Disk /dev/sdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000da6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2388    19181578+  83  Linux
/dev/sdb2            2389        2498      883575    5  Extended
/dev/sdb5            2389        2498      883543+  82  Linux swap / Solaris

---

### Post by neamhaol on 2010-01-20
Btw, I have my ntfs windows hd unplugged on that one. so its just the hd that works and the one I want to work.

---

### Post by neamhaol on 2010-01-20
I have confirmed that no raid settings are on, hds have been 0'd, and they function correctly in other OSs. Still no sata drives showing for ubuntu...

---

### Post by lidex on 2010-01-20
[http://ubuntuforums.org/showpost.php?p=8693926&postcount=21]("http://ubuntuforums.org/showpost.php?p=8693926&postcount=21")

---

### Post by jocko on 2010-01-20
> **lidex said:**
> [http://ubuntuforums.org/showpost.php?p=8693926&postcount=21](http://ubuntuforums.org/showpost.php?p=8693926&postcount=21)
Testdisk will probably not help when ubuntu doesn't even see the actual hardware (even if there were no partitions that could be read by any of the filesystem driver ubuntu has, fdisk would see the drive).
If another distro can see the drive but not ubuntu, my guess is that something is wrong with the driver for that particular sata controller...

This command will give more information about the sata controller (and other disk controllers), including which driver it uses:
```
sudo lshw -c storage
```And this will give information about all disks:
```
sudo lshw -c disk
```If you (the op) can run this both on a linux os that can see the drive and one that can't see it, maybe someone can see where the problem is.
"lshw" without any options will give information about all hardware, in a tree-like format so you can see which disk is connected to which sata/ata controller.

---

### Post by lidex on 2010-01-20
> Testdisk will probably not help when ubuntu doesn't even see the actual hardware (even if there were no partitions that could be read by any of the filesystem driver ubuntu has, fdisk would see the drive).

You know, I was wondering about that. Pretty much every other mention of a similar problem (that I have seen) still were able to recognize the partitions with fdisk. I'd love to see the answer to this one.

---

### Post by neamhaol on 2010-01-20
I like your idea. Will try when I get home and will update on the status.

---

### Post by neamhaol on 2010-01-21
sudo lshw -c storage
  *-ide:0                 
       description: IDE interface
       product: MCP78S [GeForce 8200] IDE
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: scsi6
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
       resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
  *-ide:1
       description: IDE interface
       product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
       vendor: nVidia Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm msi bus_master cap_list
       configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
       resources: irq:28 ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=16) memory:f9f76000-f9f77fff

---

### Post by neamhaol on 2010-01-21
sudo lshw -c disk
  *-cdrom:0               
       description: DVD writer
       product: DVD RW DW-Q28A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: KFS1
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM GDR8163B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@6:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 0S24
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc

---

### Post by neamhaol on 2010-01-21
This problem persists in all ubuntu related os's. Kubuntu, Mint etc.

The sudo lshw -c storage will not work in fedora, the lshw returns a command not found

---

### Post by neamhaol on 2010-01-21
Fedoras lshw -c storage output

*-ide:0                 
       description: IDE interface
       product: MCP78S [GeForce 8200] IDE
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: scsi6
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
       resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
  *-ide:1
       description: IDE interface
       product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
       vendor: nVidia Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: scsi0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm msi bus_master cap_list emulated
       configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
       resources: irq:23 ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=16) memory:f9f76000-f9f77fff

---

### Post by neamhaol on 2010-01-21
Fedora lshw -c disk output

sudo lshw -c disk
  *-cdrom:0               
       description: DVD writer
       product: DVD RW DW-Q28A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrw
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: KFS1
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM GDR8163B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@6:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 0S24
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: ST3500320AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SD15
       serial: 9QM54LJ3
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0002b769

---

### Post by lidex on 2010-01-22
You should make sure your bios is configured properly. Haven't done anything with that recently, have you? I'd suggest you make sure your disks are set for auto-detect. Then in your storage configuration, make sure onboard (on-chip)sata is enabled. Finally for sata mode you'll want IDE, not ACHI or RAID. Save and reboot.

---

### Post by Nucklez on 2010-01-22
I am having a very similar problem.  This post is the closest one to my problem that I can find.  I have an IBM Intellistation Pro Z with two SCSI U320 hard drives.  The installers cannot see the disks or partitions at all.  Nautilus, gparted, fdisk -l, nor lshw can see the physical disks as well.  I've had Ubuntu Ultimate installed for quite some time.  The one I have is based on Ubuntu 9.04.  I tried to upgrade to UU 2.5, which is based on Ubuntu 9.10 and it did the same thing that this post is about.  So, I download the Ubuntu 9.10 CD today and I'm getting the same thing.  Ubuntu 9.04 works great, but 9.10 will not see the physical disks at all.  I can see the IDE CD ROMs, and sudo lshw -c storage can see the scsi controllers, but no disks.  I'll post my output from lshw in the next post.  I can't copy and paste from one computer to another computer at the moment.  :)  Gparted is blank, and sudo fdisk -l returns nothing.

ubuntu@ubuntu:~$ sudo lshw -c storage
  *-scsi:0                
       description: SCSI storage controller
       product: 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI
       vendor: LSI Logic / Symbios Logic
       physical id: 3
       bus info: pci@0000:04:03.0
       logical name: scsi2
       version: 07
       width: 64 bits
       clock: 66MHz
       capabilities: scsi pm msi pcix bus_master cap_list rom scsi-host
       configuration: driver=mptspi latency=72 maxlatency=18 mingnt=17
       resources: irq:32 ioport:c000(size=256) memory:fb010000-fb01ffff memory:fb000000-fb00ffff memory:40000000-400fffff(prefetchable)
  *-scsi:1 UNCLAIMED
       description: SCSI storage controller
       product: 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI
       vendor: LSI Logic / Symbios Logic
       physical id: 3.1
       bus info: pci@0000:04:03.1
       version: 07
       width: 64 bits
       clock: 66MHz
       capabilities: scsi pm msi pcix bus_master cap_list
       configuration: latency=72 maxlatency=18 mingnt=17
       resources: ioport:c400(size=256) memory:fb020000-fb02ffff memory:fb030000-fb03ffff memory:40100000-401fffff(prefetchable)
  *-ide
       description: IDE interface
       product: 82801DB (ICH4) IDE Controller
       vendor: Intel Corporation
       physical id: 1f.1
       bus info: pci@0000:00:1f.1
       logical name: scsi1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: ide bus_master emulated
       configuration: driver=ata_piix latency=0
       resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:40200000-402003ff

---

### Post by Nucklez on 2010-01-22
ubuntu@ubuntu:~$ sudo lshw -c disk
  *-cdrom:0               
       description: CD-R/CD-RW writer
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: DVDRAM GSA-4040B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /cdrom
       version: A109
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted

---

### Post by Nucklez on 2010-01-22
To include more information, here are my results from my 9.04 install.  At a glance, it appears that the lshw -c storage results are the same.

:/# fdisk -l

Disk /dev/sda: 73.4 GB, 73407820800 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008c63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8555    68718006   83  Linux
/dev/sda2            8556        8924     2963992+   5  Extended
/dev/sda5            8556        8924     2963961   82  Linux swap / Solaris

Disk /dev/sdb: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e398e39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4425    35543781    5  Extended
/dev/sdb5               1        1020     8193087   83  Linux
/dev/sdb6            1021        2040     8193118+  83  Linux
/dev/sdb7            2041        2295     2048256   83  Linux
/dev/sdb8            2296        2550     2048256   83  Linux

**************************************************************
:/# sudo lshw -c storage
  *-scsi:0                
       description: SCSI storage controller
       product: 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI
       vendor: LSI Logic / Symbios Logic
       physical id: 3
       bus info: pci@0000:04:03.0
       logical name: scsi2
       version: 07
       width: 64 bits
       clock: 66MHz
       capabilities: scsi pm msi pcix bus_master cap_list scsi-host
       configuration: driver=mptspi latency=72 maxlatency=18 mingnt=17 module=mptspi
  *-scsi:1
       description: SCSI storage controller
       product: 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI
       vendor: LSI Logic / Symbios Logic
       physical id: 3.1
       bus info: pci@0000:04:03.1
       logical name: scsi3
       version: 07
       width: 64 bits
       clock: 66MHz
       capabilities: scsi pm msi pcix bus_master cap_list scsi-host
       configuration: driver=mptspi latency=72 maxlatency=18 mingnt=17 module=mptspi
  *-ide
       description: IDE interface
       product: 82801DB (ICH4) IDE Controller
       vendor: Intel Corporation
       physical id: 1f.1
       bus info: pci@0000:00:1f.1
       logical name: scsi1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: ide bus_master emulated
       configuration: driver=ata_piix latency=0

**************************************************************
:/# sudo lshw -c disk
  *-disk:0                
       description: SCSI Disk
       product: MAP3735NC
       vendor: FUJITSU
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 5605
       serial: UPA3P3203CWU
       size: 68GiB (73GB)
       capacity: 85GiB (92GB)
       capabilities: 10000rpm partitioned partitioned:dos
       configuration: ansiversion=3 signature=00008c63
  *-disk:1
       description: SCSI Disk
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/sdb
       size: 33GiB (36GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=8e398e39
  *-cdrom:0
       description: CD-R/CD-RW writer
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: DVDRAM GSA-4040B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: A109
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

### Post by neamhaol on 2010-01-22
bump for maybe more help?

---

### Post by lidex on 2010-01-22
> **neamhaol said:**
> bump for maybe more help?

Did you check your bios settings?
Did you download testdisk to check your partition table?

---

### Post by neamhaol on 2010-01-22
Yes all bios settings are normal. My drivers in fedora are the same as ubuntu, doesnt make sense why one works, the other wont.

Testdisk seems to say everything is ok.

---

### Post by lidex on 2010-01-23
OK. What is your processor make, model and architecture? What version (server, desktop) and arch(32 or 64 bit) ubuntu are you trying to install?

---

### Post by lidex on 2010-01-23
I've been scanning the syslog you posted and this section seems to be relevant;
```
Jan 20 03:50:10 ubuntu kernel: [ 7.140018] ata2.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [ 7.140022] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [ 7.140029] ata1.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [ 7.140033] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [ 7.670018] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [ 7.670025] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 20 03:50:10 ubuntu kernel: [ 17.670015] ata2.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [ 17.670018] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [ 17.670021] ata2: limiting SATA link speed to 1.5 Gbps
Jan 20 03:50:10 ubuntu kernel: [ 17.670027] ata1.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [ 17.670030] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [ 17.670032] ata1: limiting SATA link speed to 1.5 Gbps
Jan 20 03:50:10 ubuntu kernel: [ 18.200016] ata2: SATA link up <unknown> (SStatus 103 SControl 310)
Jan 20 03:50:10 ubuntu kernel: [ 23.240016] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 20 03:50:10 ubuntu kernel: [ 48.200016] ata2.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [ 48.200019] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [ 48.730016] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 20 03:50:10 ubuntu kernel: [ 53.240017] ata1.00: qc timeout (cmd 0xec)
Jan 20 03:50:10 ubuntu kernel: [ 53.240020] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan 20 03:50:10 ubuntu kernel: [ 53.770016] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
```

I found some info through google similar to this. One thing that pops up frequently is nvidia chipsets. One thing to try now that we know IDE mode doesn't work, is to try ACHI. If you have PATA devices, try unplugging them. It would be worthwhile to update your bios as well.

[http://www.linuxquestions.org/questions/linux-general-1/dmesg-says-sata-link-down-690437/]("http://www.linuxquestions.org/questions/linux-general-1/dmesg-says-sata-link-down-690437/")
[http://lkml.indiana.edu/hypermail/linux/kernel/0707.3/3804.html]("http://lkml.indiana.edu/hypermail/linux/kernel/0707.3/3804.html")
[https://bugzilla.redhat.com/show_bug.cgi?id=513257]("https://bugzilla.redhat.com/show_bug.cgi?id=513257")
[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg08912.html]("http://www.mail-archive.com/linux-ide@vger.kernel.org/msg08912.html")

---

### Post by neamhaol on 2010-01-23
My processor is an AMD dual core 5400+ Black Edition
Its a 64-bit processor.
Im trying to install Ubuntu 9.10 64bit.
Also tried 9.10 32bit and both versions of 9.04.
All desktop.

---

### Post by neamhaol on 2010-01-23
I have tried booting them in AHCI mode, same result.
No PATA drives are installed, will look into updating my bios.

---

### Post by neamhaol on 2010-01-25
[http://ubuntuforums.org/archive/index.php/t-1026362.html](http://ubuntuforums.org/archive/index.php/t-1026362.html)
 
Found this which appears to directly apply to my problem.
 
Apparently xfx nforce 750a SLI motherboards come with a specific sata controller which is known to be an issue with linux. Most people cannot get any linux to reconize sata drives, however I have found 1 which will, go figure. Fedora 10.
 
Am going to attempt to do this, Im not very familiar with linux but maybe I can handle it. Will update on status.

---

### Post by lidex on 2010-01-25
Or perhaps install a PCI sata controller.

---

### Post by neamhaol on 2010-01-25
True, but all in my area that arent internet ordered appear to be in the $40 range. 
 
What are the downsides to doing what is listed in that thread? Is it detrimental or will it cause any problems?

---

### Post by JuhazOne on 2011-09-17
> **lidex said:**
> From **[this]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470")** bug report:

I found this post helpful. I was trying to install Kubuntu 11.04 using the alternate install cd, but the partition manager in the installer (called partman, I believe) wouldn't recognize /dev/sda, it only suggested partitions on /dev/sdb. This seemed odd since fdisk could recognize /dev/sda and print its partitions.

Turns out the problem was answering "yes" to the question about RAID drives just before partitioning (at the phase where the installer was detecting disks). It didn't help to go back and answer "no" to RAIDs – but rebooting and then answering "no" did. Now the installer suggested partitions on /dev/sda, too.

(I didn't test anything related to dmraid, so I don't know if disabling it would have helped.)

---

