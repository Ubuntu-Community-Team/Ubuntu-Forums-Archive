---
title: "Upgrade won't boot"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by thereid on 2010-10-24
Please note: I'm a newbie user....

I upgraded from Jaunty Jackalope to Karmic Koala, via the automatic system packages upgrade and now my Thinkpad won't boot.
Error msg reads:

Gave up waiting for root device. Common Problems:

- Boot Args (cat /proc/cmdline)
  - Check rootdelay (did system wait long enough?)
  _ Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/ [serial number here]  does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)


I recognize some of the "help" commands, but I don't know how to use them.
Can anyone help me get either my previous OR new version of GUI back??
:confused:

---

### Post by kansasnoob on 2010-10-24
Since you upgraded from Jaunty to Karmic you probably still have legacy grub, so as you boot, right after the System/BIOS screen passes, press the Esc key. That should display the grub menu.

If so try to boot the older Jaunty kernel (2.6.28-*). If that works I'd next run these two commands:

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

The output of either of those may provide some clues.

You might also try one of the "recovery mode" entries from the grub menu followed by the "dpkg" option.

---

### Post by thereid on 2010-10-24
> **kansasnoob said:**
> Since you upgraded from Jaunty to Karmic you probably still have legacy grub, so as you boot, right after the System/BIOS screen passes, press the Esc key. That should display the grub menu.

If so try to boot the older Jaunty kernel (2.6.28-*). If that works I'd next run these two commands:

```
sudo apt-get -f install
``````
sudo dpkg --configure -a
```The output of either of those may provide some clues.

You might also try one of the "recovery mode" entries from the grub menu followed by the "dpkg" option.



It tells me that I need to load the kernel first.  How do I do that?

Would it just be easier to burn a new disk and do a fresh install?  The problem is that it's a dual boot machine (partitioned) with Win XP.  I don't want to do anything to corrupt my XP files because that's what I use most.  I'm just trying to learn about Ubuntu (apparently with limited success.)

---

### Post by CadetD on 2010-10-24
<rant>
This seems to be a major and common problem with the 10.4 to 10.10 upgrade. I have found dozens of posts reporting the same problem but no single solution. I now have two machines in that state. 

Someone please help.....
</rant>

After two days of trying miscellaneous fixes:
- reinstall grub after booting to previous kernel
- edit boot line to change from UID=xxxx to /dev/sda1
- verify that blkid, fstab, menu.lst all had the same UUIDs 
- some others I forget

I tried blkid from the initramfs busybox propmt and found that it only reports the external firewire drive. None of my SATA drives show up. 

If I boot a previous kernel, all my drives show up. 

What now?

---

### Post by kansasnoob on 2010-10-25
> **thereid said:**
> It tells me that I need to load the kernel first.  How do I do that?

Would it just be easier to burn a new disk and do a fresh install?  The problem is that it's a dual boot machine (partitioned) with Win XP.  I don't want to do anything to corrupt my XP files because that's what I use most.  I'm just trying to learn about Ubuntu (apparently with limited success.)

Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That will help us either straighten this out or give you reinstall instructions. I think there's a good chance we can get this booting.

---

### Post by kansasnoob on 2010-10-25
> **CadetD said:**
> <rant>
This seems to be a major and common problem with the 10.4 to 10.10 upgrade. I have found dozens of posts reporting the same problem but no single solution. I now have two machines in that state. 

Someone please help.....
</rant>

After two days of trying miscellaneous fixes:
- reinstall grub after booting to previous kernel
- edit boot line to change from UID=xxxx to /dev/sda1
- verify that blkid, fstab, menu.lst all had the same UUIDs 
- some others I forget

I tried blkid from the initramfs busybox propmt and found that it only reports the external firewire drive. None of my SATA drives show up. 

If I boot a previous kernel, all my drives show up. 

What now?

Please start a new thread here:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

Explain the exact problem you're having and post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by CadetD on 2010-10-30
> **kansasnoob said:**
> Please start a new thread here:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

Explain the exact problem you're having and post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
I don't quite follow why open a new thread in the same section for the exact same problem. Does that not make it more difficult to find the resolution. Isn't that also considered double posting (to be frowned upon)?

---

### Post by CadetD on 2010-10-30
Additional digging showed that my SATA drives were detected but somehow unreadable. 

I booted from the CD and tried a rescue, which fails after detecting the /dev/sda1. 

Here is the syslog: 
> 
Oct 30 13:44:23 syslogd started: BusyBox v1.15.3
Oct 30 13:44:23 kernel: klogd started: BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5)
Oct 30 13:44:23 kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 30 13:44:23 kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 30 13:44:23 kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
Oct 30 13:44:23 kernel: [    0.000000] Command line: rescue/enable=true vga=788 initrd=/install/initrd.gz --
Oct 30 13:44:23 kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 30 13:44:23 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 30 13:44:23 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 30 13:44:23 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct 30 13:44:23 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bdff0000 (usable)
Oct 30 13:44:23 kernel: [    0.000000]  BIOS-e820: 00000000bdff0000 - 00000000bdfff000 (ACPI data)
Oct 30 13:44:23 kernel: [    0.000000]  BIOS-e820: 00000000bdfff000 - 00000000be000000 (ACPI NVS)
Oct 30 13:44:23 kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Oct 30 13:44:23 kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 30 13:44:23 kernel: [    0.000000] DMI 2.3 present.
Oct 30 13:44:23 kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Oct 30 13:44:23 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Oct 30 13:44:23 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Oct 30 13:44:23 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Oct 30 13:44:23 kernel: [    0.000000] AGP bridge at 04:00:00
Oct 30 13:44:23 kernel: [    0.000000] Aperture from AGP @ e0000000 old size 32 MB
Oct 30 13:44:23 kernel: [    0.000000] Aperture from AGP @ e0000000 size 256 MB (APSIZE f00)
Oct 30 13:44:23 kernel: [    0.000000] last_pfn = 0xbdff0 max_arch_pfn = 0x400000000
Oct 30 13:44:23 kernel: [    0.000000] MTRR default type: uncachable
Oct 30 13:44:23 kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 30 13:44:23 kernel: [    0.000000]   00000-9FFFF write-back
Oct 30 13:44:23 kernel: [    0.000000]   A0000-EFFFF uncachable
Oct 30 13:44:23 kernel: [    0.000000]   F0000-FFFFF write-protect
Oct 30 13:44:23 kernel: [    0.000000] MTRR variable ranges enabled:
Oct 30 13:44:23 kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Oct 30 13:44:23 kernel: [    0.000000]   1 base 0080000000 mask FFE0000000 write-back
Oct 30 13:44:23 kernel: [    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
Oct 30 13:44:23 kernel: [    0.000000]   3 base 00B0000000 mask FFF8000000 write-back
Oct 30 13:44:23 kernel: [    0.000000]   4 base 00B8000000 mask FFFC000000 write-back
Oct 30 13:44:23 kernel: [    0.000000]   5 base 00BC000000 mask FFFE000000 write-back
Oct 30 13:44:23 kernel: [    0.000000]   6 disabled
Oct 30 13:44:23 kernel: [    0.000000]   7 disabled
Oct 30 13:44:23 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Oct 30 13:44:23 kernel: [    0.000000] Scanning 0 areas for low memory corruption
Oct 30 13:44:23 kernel: [    0.000000] modified physical RAM map:
Oct 30 13:44:23 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Oct 30 13:44:23 kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Oct 30 13:44:23 kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 30 13:44:23 kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Oct 30 13:44:23 kernel: [    0.000000]  modified: 0000000000100000 - 00000000bdff0000 (usable)
Oct 30 13:44:23 kernel: [    0.000000]  modified: 00000000bdff0000 - 00000000bdfff000 (ACPI data)
Oct 30 13:44:23 kernel: [    0.000000]  modified: 00000000bdfff000 - 00000000be000000 (ACPI NVS)
Oct 30 13:44:23 kernel: [    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
Oct 30 13:44:23 kernel: [    0.000000] initial memory mapped : 0 - 20000000
Oct 30 13:44:23 kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Oct 30 13:44:23 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bdff0000
Oct 30 13:44:23 kernel: [    0.000000]  0000000000 - 00bde00000 page 2M
Oct 30 13:44:23 kernel: [    0.000000]  00bde00000 - 00bdff0000 page 4k
Oct 30 13:44:23 kernel: [    0.000000] kernel direct mapping tables up to bdff0000 @ 16000-1b000
Oct 30 13:44:23 kernel: [    0.000000] RAMDISK: 7f986000 - 80000000
Oct 30 13:44:23 kernel: [    0.000000] ACPI: RSDP 00000000000f6e10 00024 (v02 ACPIAM)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: XSDT 00000000bdff0100 00054 (v01 A M I  OEMXSDT  06000514 MSFT 00000097)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: FACP 00000000bdff0281 000F4 (v01 A M I  OEMFACP  06000514 MSFT 00000097)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: DSDT 00000000bdff0410 03E43 (v01  0AAAA 0AAAA001 00000001 INTL 02002026)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: FACS 00000000bdfff000 00040
Oct 30 13:44:23 kernel: [    0.000000] ACPI: APIC 00000000bdff0380 00084 (v01 A M I  OEMAPIC  06000514 MSFT 00000097)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: OEMB 00000000bdfff040 0005E (v01 A M I  OEMBIOS  06000514 MSFT 00000097)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: SRAT 00000000bdff4260 00110 (v01 A M I  OEMSRAT  06000514 MSFT 00000097)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: HPET 00000000bdff4370 00038 (v01 A M I  OEMHPET  06000514 MSFT 00000097)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: ASF! 00000000bdff43b0 00086 (v01 AMIASF AMDSTRET 00000001 INTL 02002026)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 30 13:44:23 kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
Oct 30 13:44:23 kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
Oct 30 13:44:23 kernel: [    0.000000] SRAT: PXM 1 -> APIC 0x02 -> Node 1
Oct 30 13:44:23 kernel: [    0.000000] SRAT: PXM 1 -> APIC 0x03 -> Node 1
Oct 30 13:44:23 kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-80000000
Oct 30 13:44:23 kernel: [    0.000000] SRAT: Node 1 PXM 1 80000000-be000000
Oct 30 13:44:23 kernel: [    0.000000] SRAT: Node 1 PXM 1 100000000-100000000
Oct 30 13:44:23 kernel: [    0.000000] SRAT: Node 0 PXM 0 0-9fc00
Oct 30 13:44:23 kernel: [    0.000000] SRAT: Node 0 [100000,80000000) + [0,9fc00) -> [0,80000000)
Oct 30 13:44:23 kernel: [    0.000000] SRAT: Node 1 [80000000,be000000) + [100000000,100000000) -> [80000000,100000000)
Oct 30 13:44:23 kernel: [    0.000000] NUMA: Using 31 for the hash shift.
Oct 30 13:44:23 kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000080000000
Oct 30 13:44:23 kernel: [    0.000000]   NODE_DATA [0000000001d181c0 - 0000000001d1d1bf]
Oct 30 13:44:23 kernel: [    0.000000] Initmem setup node 1 0000000080000000-00000000bdff0000
Oct 30 13:44:23 kernel: [    0.000000]   NODE_DATA [0000000080000000 - 0000000080004fff]
Oct 30 13:44:23 kernel: [    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880002600000-ffff8800041fffff] on node 0
Oct 30 13:44:23 kernel: [    0.000000]  [ffffea0001c00000-ffffea00029fffff] PMD -> [ffff880080200000-ffff880080ffffff] on node 1
Oct 30 13:44:23 kernel: [    0.000000] Zone PFN ranges:
Oct 30 13:44:23 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct 30 13:44:23 kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Oct 30 13:44:23 kernel: [    0.000000]   Normal   empty
Oct 30 13:44:23 kernel: [    0.000000] Movable zone start PFN for each node
Oct 30 13:44:23 kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 30 13:44:23 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct 30 13:44:23 kernel: [    0.000000]     0: 0x00000100 -> 0x00080000
Oct 30 13:44:23 kernel: [    0.000000]     1: 0x00080000 -> 0x000bdff0
Oct 30 13:44:23 kernel: [    0.000000] On node 0 totalpages: 524175
Oct 30 13:44:23 kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Oct 30 13:44:23 kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 30 13:44:23 kernel: [    0.000000]   DMA zone: 3927 pages, LIFO batch:0
Oct 30 13:44:23 kernel: [    0.000000]   DMA32 zone: 7112 pages used for memmap
Oct 30 13:44:23 kernel: [    0.000000]   DMA32 zone: 513080 pages, LIFO batch:31
Oct 30 13:44:23 kernel: [    0.000000] On node 1 totalpages: 253936
Oct 30 13:44:23 kernel: [    0.000000]   DMA32 zone: 3472 pages used for memmap
Oct 30 13:44:23 kernel: [    0.000000]   DMA32 zone: 250464 pages, LIFO batch:31
Oct 30 13:44:23 kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Oct 30 13:44:23 kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Oct 30 13:44:23 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x5008
Oct 30 13:44:23 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 30 13:44:23 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Oct 30 13:44:23 kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Oct 30 13:44:23 kernel: [    0.000000] ACPI: IOAPIC (id[0x05] address[0xff4ff000] gsi_base[24])
Oct 30 13:44:23 kernel: [    0.000000] IOAPIC[1]: apic_id 5, version 17, address 0xff4ff000, GSI 24-27
Oct 30 13:44:23 kernel: [    0.000000] ACPI: IOAPIC (id[0x06] address[0xff4fe000] gsi_base[28])
Oct 30 13:44:23 kernel: [    0.000000] IOAPIC[2]: apic_id 6, version 17, address 0xff4fe000, GSI 28-31
Oct 30 13:44:23 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 30 13:44:23 kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 30 13:44:23 kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 30 13:44:23 kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 30 13:44:23 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 30 13:44:23 kernel: [    0.000000] ACPI: HPET id: 0x102282a0 base: 0xfec01000
Oct 30 13:44:23 kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Oct 30 13:44:23 kernel: [    0.000000] nr_irqs_gsi: 48
Oct 30 13:44:23 kernel: [    0.000000] early_res array is doubled to 64 at [19000 - 197ff]
Oct 30 13:44:23 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 30 13:44:23 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Oct 30 13:44:23 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Oct 30 13:44:23 kernel: [    0.000000] Allocating PCI resources starting at be000000 (gap: be000000:41780000)
Oct 30 13:44:23 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 30 13:44:23 kernel: [    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:2
Oct 30 13:44:23 kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u1048576
Oct 30 13:44:23 kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u1048576 alloc=1*2097152
Oct 30 13:44:23 kernel: [    0.000000] pcpu-alloc: [0] 0 1 [1] 2 3 
Oct 30 13:44:23 kernel: [    0.000000] Built 2 zonelists in Node order, mobility grouping on.  Total pages: 767471
Oct 30 13:44:23 kernel: [    0.000000] Policy zone: DMA32
Oct 30 13:44:23 kernel: [    0.000000] Kernel command line: rescue/enable=true vga=788 initrd=/install/initrd.gz --
Oct 30 13:44:23 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Oct 30 13:44:23 kernel: [    0.000000] Checking aperture...
Oct 30 13:44:23 kernel: [    0.000000] AGP bridge at 04:00:00
Oct 30 13:44:23 kernel: [    0.000000] Aperture from AGP @ e0000000 old size 32 MB
Oct 30 13:44:23 kernel: [    0.000000] Aperture from AGP @ e0000000 size 256 MB (APSIZE f00)
Oct 30 13:44:23 kernel: [    0.000000] Node 0: aperture @ e0000000 size 256 MB
Oct 30 13:44:23 kernel: [    0.000000] Node 1: aperture @ e0000000 size 256 MB
Oct 30 13:44:23 kernel: [    0.000000] Subtract (50 early reservations)
Oct 30 13:44:23 kernel: [    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
Oct 30 13:44:23 kernel: [    0.000000]   #2 [007f986000 - 0080000000]         RAMDISK
Oct 30 13:44:23 kernel: [    0.000000]   #3 [0001d18000 - 0001d181b5]             BRK
Oct 30 13:44:23 kernel: [    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
Oct 30 13:44:23 kernel: [    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
Oct 30 13:44:23 kernel: [    0.000000]   #6 [000009f800 - 00000fa490]   BIOS reserved
Oct 30 13:44:23 kernel: [    0.000000]   #7 [00000fa614 - 00000ff780]   BIOS reserved
Oct 30 13:44:23 kernel: [    0.000000]   #8 [00000fa490 - 00000fa614]    MP-table mpc
Oct 30 13:44:23 kernel: [    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
Oct 30 13:44:23 kernel: [    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
Oct 30 13:44:23 kernel: [    0.000000]   #11 [0000016000 - 0000019000]         PGTABLE
Oct 30 13:44:23 kernel: [    0.000000]   #12 [0001d181c0 - 0001d1d1c0]       NODE_DATA
Oct 30 13:44:23 kernel: [    0.000000]   #13 [0080000000 - 0080005000]       NODE_DATA
Oct 30 13:44:23 kernel: [    0.000000]   #14 [0001d1d1c0 - 0001d1e1c0]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #15 [0001d17140 - 0001d172c0]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #16 [0080005000 - 00800050c0]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #17 [000251f000 - 0002520000]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #18 [0002520000 - 0002521000]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #19 [0002600000 - 0004200000]        MEMMAP 0
Oct 30 13:44:23 kernel: [    0.000000]   #20 [0080200000 - 0081000000]        MEMMAP 1
Oct 30 13:44:23 kernel: [    0.000000]   #21 [0001d172c0 - 0001d17440]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #22 [0001d1e1c0 - 0001d2a1c0]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #23 [00800050c0 - 008000b0c0]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #24 [0001d2b000 - 0001d2c000]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #25 [0001d17440 - 0001d17481]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #26 [0001d174c0 - 0001d17589]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #27 [0001d175c0 - 0001d17780]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #28 [0001d17780 - 0001d177e8]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #29 [0001d17800 - 0001d17868]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #30 [0001d17880 - 0001d178e8]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #31 [0001d17900 - 0001d17968]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #32 [0001d17980 - 0001d179e8]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #33 [0001d17a00 - 0001d17a68]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #34 [0001d17a80 - 0001d17ae8]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #35 [0001d17b00 - 0001d17b20]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #36 [0001d17b40 - 0001d17b78]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #37 [0001d17b80 - 0001d17bb8]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #38 [0001e00000 - 0001e1e000]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #39 [0001f00000 - 0001f1e000]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #40 [0081000000 - 008101e000]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #41 [0081100000 - 008111e000]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #42 [0001d17bc0 - 0001d17bd0]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #43 [0001d17c00 - 0001d17c10]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #44 [0001d17c40 - 0001d17c50]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #45 [0001d17c80 - 0001d17ca0]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #46 [0001d17cc0 - 0001d17e00]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #47 [0001d17e00 - 0001d17e60]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #48 [0001d17e80 - 0001d17ee0]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000]   #49 [0001d2c000 - 0001d34000]         BOOTMEM
Oct 30 13:44:23 kernel: [    0.000000] Memory: 3048712k/3112896k available (5708k kernel code, 452k absent, 63732k reserved, 5382k data, 908k init)
Oct 30 13:44:23 kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=2
Oct 30 13:44:23 kernel: [    0.000000] Hierarchical RCU implementation.
Oct 30 13:44:23 kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Oct 30 13:44:23 kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Oct 30 13:44:23 kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Oct 30 13:44:23 kernel: [    0.000000] NR_IRQS:4352 nr_irqs:848
Oct 30 13:44:23 kernel: [    0.000000] Console: colour dummy device 80x25
Oct 30 13:44:23 kernel: [    0.000000] console [tty0] enabled
Oct 30 13:44:23 kernel: [    0.000000] allocated 31457280 bytes of page_cgroup
Oct 30 13:44:23 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 30 13:44:23 kernel: [    0.000000] hpet clockevent registered
Oct 30 13:44:23 kernel: [    0.000000] Fast TSC calibration using PIT
Oct 30 13:44:23 kernel: [    0.000000] Detected 1993.071 MHz processor.
Oct 30 13:44:23 kernel: [    0.020010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3986.14 BogoMIPS (lpj=19930710)
Oct 30 13:44:23 kernel: [    0.020020] pid_max: default: 32768 minimum: 301
Oct 30 13:44:23 kernel: [    0.020057] Security Framework initialized
Oct 30 13:44:23 kernel: [    0.020079] AppArmor: AppArmor initialized
Oct 30 13:44:23 kernel: [    0.020083] Yama: becoming mindful.
Oct 30 13:44:23 kernel: [    0.020615] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Oct 30 13:44:23 kernel: [    0.024089] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Oct 30 13:44:23 kernel: [    0.025557] Mount-cache hash table entries: 256
Oct 30 13:44:23 kernel: [    0.025740] Initializing cgroup subsys ns
Oct 30 13:44:23 kernel: [    0.025747] Initializing cgroup subsys cpuacct
Oct 30 13:44:23 kernel: [    0.025754] Initializing cgroup subsys memory
Oct 30 13:44:23 kernel: [    0.025778] Initializing cgroup subsys devices
Oct 30 13:44:23 kernel: [    0.025783] Initializing cgroup subsys freezer
Oct 30 13:44:23 kernel: [    0.025787] Initializing cgroup subsys net_cls
Oct 30 13:44:23 kernel: [    0.025824] tseg: 0000000000
Oct 30 13:44:23 kernel: [    0.025841] CPU: Physical Processor ID: 0
Oct 30 13:44:23 kernel: [    0.025845] CPU: Processor Core ID: 0
Oct 30 13:44:23 kernel: [    0.025849] mce: CPU supports 5 MCE banks
Oct 30 13:44:23 kernel: [    0.025863] Performance Events: AMD PMU driver.
Oct 30 13:44:23 kernel: [    0.025871] ... version:                0
Oct 30 13:44:23 kernel: [    0.025874] ... bit width:              48
Oct 30 13:44:23 kernel: [    0.025878] ... generic registers:      4
Oct 30 13:44:23 kernel: [    0.025882] ... value mask:             0000ffffffffffff
Oct 30 13:44:23 kernel: [    0.025886] ... max period:             00007fffffffffff
Oct 30 13:44:23 kernel: [    0.025891] ... fixed-purpose events:   0
Oct 30 13:44:23 kernel: [    0.025894] ... event mask:             000000000000000f
Oct 30 13:44:23 kernel: [    0.027585] ACPI: Core revision 20100428
Oct 30 13:44:23 kernel: [    0.035759] ftrace: converting mcount calls to 0f 1f 44 00 00
Oct 30 13:44:23 kernel: [    0.035771] ftrace: allocating 22680 entries in 89 pages
Oct 30 13:44:23 kernel: [    0.040106] Setting APIC routing to flat
Oct 30 13:44:23 kernel: [    0.040591] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Oct 30 13:44:23 kernel: [    0.143475] CPU0: Dual Core AMD Opteron(tm) Processor 270 stepping 02
Oct 30 13:44:23 kernel: [    0.150000] Booting Node   0, Processors  #1 Ok.
Oct 30 13:44:23 kernel: [    0.300151] Booting Node   1, Processors  #2 #3 Ok.
Oct 30 13:44:23 kernel: [    0.620113] Brought up 4 CPUs
Oct 30 13:44:23 kernel: [    0.620118] Total of 4 processors activated (15945.52 BogoMIPS).
Oct 30 13:44:23 kernel: [    0.620828] devtmpfs: initialized
Oct 30 13:44:23 kernel: [    0.620932] regulator: core version 0.5
Oct 30 13:44:23 kernel: [    0.620965] Time: 13:44:16  Date: 10/30/10
Oct 30 13:44:23 kernel: [    0.621012] NET: Registered protocol family 16
Oct 30 13:44:23 kernel: [    0.621152] node 0 link 2: io port [7000, bfff]
Oct 30 13:44:23 kernel: [    0.621156] node 0 link 0: io port [c000, cfff]
Oct 30 13:44:23 kernel: [    0.621159] TOM: 00000000be000000 aka 3040M
Oct 30 13:44:23 kernel: [    0.621164] node 0 link 2: mmio [ff100000, ff4fffff]
Oct 30 13:44:23 kernel: [    0.621168] node 0 link 2: mmio [be900000, beafffff]
Oct 30 13:44:23 kernel: [    0.621171] node 0 link 0: mmio [ff500000, ff6fffff]
Oct 30 13:44:23 kernel: [    0.621174] node 0 link 0: mmio [beb00000, febfffff]
Oct 30 13:44:23 kernel: [    0.621178] node 0 link 0: mmio [a0000, bffff]
Oct 30 13:44:23 kernel: [    0.621181] bus: [00, 03] on node 0 link 2
Oct 30 13:44:23 kernel: [    0.621185] bus: 00 index 0 [io  0x0000-0xbfff]
Oct 30 13:44:23 kernel: [    0.621187] bus: 00 index 1 [io  0xd000-0xffff]
Oct 30 13:44:23 kernel: [    0.621189] bus: 00 index 2 [mem 0xfec00000-0xff4fffff]
Oct 30 13:44:23 kernel: [    0.621192] bus: 00 index 3 [mem 0xbe000000-0xbeafffff]
Oct 30 13:44:23 kernel: [    0.621194] bus: 00 index 4 [mem 0xff700000-0xfcffffffff]
Oct 30 13:44:23 kernel: [    0.621197] bus: [04, 05] on node 0 link 0
Oct 30 13:44:23 kernel: [    0.621199] bus: 04 index 0 [io  0xc000-0xcfff]
Oct 30 13:44:23 kernel: [    0.621201] bus: 04 index 1 [mem 0xff500000-0xff6fffff]
Oct 30 13:44:23 kernel: [    0.621203] bus: 04 index 2 [mem 0xbeb00000-0xfebfffff]
Oct 30 13:44:23 kernel: [    0.621206] bus: 04 index 3 [mem 0x000a0000-0x000bffff]
Oct 30 13:44:23 kernel: [    0.621029] Trying to unpack rootfs image as initramfs...
Oct 30 13:44:23 kernel: [    0.621225] ACPI: bus type pci registered
Oct 30 13:44:23 kernel: [    0.621288] PCI: Using configuration type 1 for base access
Oct 30 13:44:23 kernel: [    0.622100] bio: create slab <bio-0> at 0
Oct 30 13:44:23 kernel: [    0.622100] ACPI: EC: Look up EC in DSDT
Oct 30 13:44:23 kernel: [    0.622100] ACPI: Executed 1 blocks of module-level executable AML code
Oct 30 13:44:23 kernel: [    0.635579] ACPI: Interpreter enabled
Oct 30 13:44:23 kernel: [    0.635584] ACPI: (supports S0 S1 S4 S5)
Oct 30 13:44:23 kernel: [    0.635607] ACPI: Using IOAPIC for interrupt routing
Oct 30 13:44:23 kernel: [    0.642524] ACPI: No dock devices found.
Oct 30 13:44:23 kernel: [    0.642531] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Oct 30 13:44:23 kernel: [    0.642888] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
Oct 30 13:44:23 kernel: [    0.643608] pci_root PNP0A03:00: host bridge window [io  0x0000-0x03af] (ignored)
Oct 30 13:44:23 kernel: [    0.643611] pci_root PNP0A03:00: host bridge window [io  0x03bc-0x03bf] (ignored)
Oct 30 13:44:23 kernel: [    0.643614] pci_root PNP0A03:00: host bridge window [io  0x03e0-0x0cf7] (ignored)
Oct 30 13:44:23 kernel: [    0.643617] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xbfff] (ignored)
Oct 30 13:44:23 kernel: [    0.643619] pci_root PNP0A03:00: host bridge window [io  0xd000-0xffff] (ignored)
Oct 30 13:44:23 kernel: [    0.643622] pci_root PNP0A03:00: host bridge window [mem 0xbe000000-0xbeafffff] (ignored)
Oct 30 13:44:23 kernel: [    0.643625] pci_root PNP0A03:00: host bridge window [mem 0xfec00000-0xff4fffff] (ignored)
Oct 30 13:44:23 kernel: [    0.643628] pci_root PNP0A03:00: host bridge window [mem 0xff700000-0xffffffff] (ignored)
Oct 30 13:44:23 kernel: [    0.643773] pci 0000:00:07.1: reg 20: [io  0xffa0-0xffaf]
Oct 30 13:44:23 kernel: [    0.643805] pci 0000:00:07.2: reg 10: [io  0xb400-0xb41f]
Oct 30 13:44:23 kernel: [    0.643911] pci 0000:00:07.5: reg 10: [io  0xb800-0xb8ff]
Oct 30 13:44:23 kernel: [    0.643918] pci 0000:00:07.5: reg 14: [io  0xbc00-0xbc3f]
Oct 30 13:44:23 kernel: [    0.644022] pci 0000:00:0a.1: reg 10: [mem 0xff4ff000-0xff4fffff 64bit]
Oct 30 13:44:23 kernel: [    0.644095] pci 0000:00:0b.1: reg 10: [mem 0xff4fe000-0xff4fefff 64bit]
Oct 30 13:44:23 kernel: [    0.644290] PCI: peer root bus 00 res updated from pci conf
Oct 30 13:44:23 kernel: [    0.644342] pci 0000:01:00.0: reg 10: [mem 0xff2fd000-0xff2fdfff]
Oct 30 13:44:23 kernel: [    0.644398] pci 0000:01:00.1: reg 10: [mem 0xff2fe000-0xff2fefff]
Oct 30 13:44:23 kernel: [    0.644480] pci 0000:01:0a.0: reg 10: [io  0x8800-0x881f]
Oct 30 13:44:23 kernel: [    0.644488] pci 0000:01:0a.0: reg 14: [io  0x8400-0x840f]
Oct 30 13:44:23 kernel: [    0.644495] pci 0000:01:0a.0: reg 18: [io  0x8000-0x800f]
Oct 30 13:44:23 kernel: [    0.644503] pci 0000:01:0a.0: reg 1c: [io  0x7c00-0x7c3f]
Oct 30 13:44:23 kernel: [    0.644538] pci 0000:01:0a.0: supports D2
Oct 30 13:44:23 kernel: [    0.644569] pci 0000:01:0b.0: reg 10: [io  0x9c00-0x9c07]
Oct 30 13:44:23 kernel: [    0.644577] pci 0000:01:0b.0: reg 14: [io  0x9800-0x9803]
Oct 30 13:44:23 kernel: [    0.644584] pci 0000:01:0b.0: reg 18: [io  0x9400-0x9407]
Oct 30 13:44:23 kernel: [    0.644591] pci 0000:01:0b.0: reg 1c: [io  0x9000-0x9003]
Oct 30 13:44:23 kernel: [    0.644599] pci 0000:01:0b.0: reg 20: [io  0x8c00-0x8c0f]
Oct 30 13:44:23 kernel: [    0.644606] pci 0000:01:0b.0: reg 24: [mem 0xff2ffc00-0xff2fffff]
Oct 30 13:44:23 kernel: [    0.644614] pci 0000:01:0b.0: reg 30: [mem 0xff200000-0xff27ffff pref]
Oct 30 13:44:23 kernel: [    0.644634] pci 0000:01:0b.0: supports D1 D2
Oct 30 13:44:23 kernel: [    0.644666] pci 0000:01:0c.0: reg 10: [mem 0xff2ff000-0xff2ff7ff]
Oct 30 13:44:23 kernel: [    0.644674] pci 0000:01:0c.0: reg 14: [mem 0xff2f8000-0xff2fbfff]
Oct 30 13:44:23 kernel: [    0.644721] pci 0000:01:0c.0: supports D1 D2
Oct 30 13:44:23 kernel: [    0.644723] pci 0000:01:0c.0: PME# supported from D0 D1 D2 D3hot
Oct 30 13:44:23 kernel: [    0.644728] pci 0000:01:0c.0: PME# disabled
Oct 30 13:44:23 kernel: [    0.644760] pci 0000:00:06.0: PCI bridge to [bus 01-01]
Oct 30 13:44:23 kernel: [    0.644768] pci 0000:00:06.0:   bridge window [io  0x7000-0x9fff]
Oct 30 13:44:23 kernel: [    0.644772] pci 0000:00:06.0:   bridge window [mem 0xff100000-0xff2fffff]
Oct 30 13:44:23 kernel: [    0.644777] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 30 13:44:23 kernel: [    0.644826] pci 0000:02:07.0: reg 10: [io  0xa800-0xa8ff]
Oct 30 13:44:23 kernel: [    0.644832] pci 0000:02:07.0: reg 14: [mem 0xff3ffc00-0xff3ffdff]
Oct 30 13:44:23 kernel: [    0.644865] pci 0000:02:07.0: supports D1 D2
Oct 30 13:44:23 kernel: [    0.644867] pci 0000:02:07.0: PME# supported from D1 D2 D3hot D3cold
Oct 30 13:44:23 kernel: [    0.644871] pci 0000:02:07.0: PME# disabled
Oct 30 13:44:23 kernel: [    0.644908] pci 0000:02:09.0: reg 10: [mem 0xff3e0000-0xff3effff 64bit]
Oct 30 13:44:23 kernel: [    0.644930] pci 0000:02:09.0: reg 30: [mem 0xff3d0000-0xff3dffff pref]
Oct 30 13:44:23 kernel: [    0.644955] pci 0000:02:09.0: PME# supported from D3hot D3cold
Oct 30 13:44:23 kernel: [    0.644959] pci 0000:02:09.0: PME# disabled
Oct 30 13:44:23 kernel: [    0.644989] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
Oct 30 13:44:23 kernel: [    0.644997] pci 0000:00:0a.0:   bridge window [io  0xa000-0xafff]
Oct 30 13:44:23 kernel: [    0.645001] pci 0000:00:0a.0:   bridge window [mem 0xff300000-0xff3fffff]
Oct 30 13:44:23 kernel: [    0.645006] pci 0000:00:0a.0:   bridge window [mem 0xbe900000-0xbe9fffff 64bit pref]
Oct 30 13:44:23 kernel: [    0.645042] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Oct 30 13:44:23 kernel: [    0.645049] pci 0000:00:0b.0:   bridge window [io  0xf000-0x0000] (disabled)
Oct 30 13:44:23 kernel: [    0.645052] pci 0000:00:0b.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Oct 30 13:44:23 kernel: [    0.645057] pci 0000:00:0b.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 30 13:44:23 kernel: [    0.645072] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 30 13:44:23 kernel: [    0.645138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Oct 30 13:44:23 kernel: [    0.645250] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GOLA._PRT]
Oct 30 13:44:23 kernel: [    0.645360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GOLB._PRT]
Oct 30 13:44:23 kernel: [    0.648150] ACPI: PCI Root Bridge [PCIB] (domain 0000 [bus 04-05])
Oct 30 13:44:23 kernel: [    0.648612] pci_root PNP0A03:01: host bridge window [io  0xc000-0xcfff] (ignored)
Oct 30 13:44:23 kernel: [    0.648615] pci_root PNP0A03:01: host bridge window [io  0x03b0-0x03bb] (ignored)
Oct 30 13:44:23 kernel: [    0.648618] pci_root PNP0A03:01: host bridge window [io  0x03c0-0x03df] (ignored)
Oct 30 13:44:23 kernel: [    0.648621] pci_root PNP0A03:01: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Oct 30 13:44:23 kernel: [    0.648624] pci_root PNP0A03:01: host bridge window [mem 0xbeb00000-0xfebfffff] (ignored)
Oct 30 13:44:23 kernel: [    0.648627] pci_root PNP0A03:01: host bridge window [mem 0xff500000-0xff6fffff] (ignored)
Oct 30 13:44:23 kernel: [    0.648641] pci 0000:04:00.0: reg 10: [mem 0xe0000000-0xefffffff pref]
Oct 30 13:44:23 kernel: [    0.648704] PCI: peer root bus 04 res updated from pci conf
Oct 30 13:44:23 kernel: [    0.648742] pci 0000:05:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
Oct 30 13:44:23 kernel: [    0.648748] pci 0000:05:00.0: reg 14: [io  0xc800-0xc8ff]
Oct 30 13:44:23 kernel: [    0.648754] pci 0000:05:00.0: reg 18: [mem 0xff5f0000-0xff5fffff]
Oct 30 13:44:23 kernel: [    0.648771] pci 0000:05:00.0: reg 30: [mem 0xff5c0000-0xff5dffff pref]
Oct 30 13:44:23 kernel: [    0.648797] pci 0000:05:00.0: supports D1 D2
Oct 30 13:44:23 kernel: [    0.648827] pci 0000:05:00.1: reg 10: [mem 0xff5e0000-0xff5effff]
Oct 30 13:44:23 kernel: [    0.648865] pci 0000:05:00.1: supports D1 D2
Oct 30 13:44:23 kernel: [    0.648898] pci 0000:04:01.0: PCI bridge to [bus 05-05]
Oct 30 13:44:23 kernel: [    0.648905] pci 0000:04:01.0:   bridge window [io  0xc000-0xcfff]
Oct 30 13:44:23 kernel: [    0.648908] pci 0000:04:01.0:   bridge window [mem 0xff500000-0xff5fffff]
Oct 30 13:44:23 kernel: [    0.648912] pci 0000:04:01.0:   bridge window [mem 0xbeb00000-0xdeafffff pref]
Oct 30 13:44:23 kernel: [    0.648924] ACPI: PCI Interrupt Routing Table [\_SB_.PCIB.PBP2._PRT]
Oct 30 13:44:23 kernel: [    0.649225] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Oct 30 13:44:23 kernel: [    0.649362] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Oct 30 13:44:23 kernel: [    0.649496] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 30 13:44:23 kernel: [    0.649630] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Oct 30 13:44:23 kernel: [    0.649678] HEST: Table is not found!
Oct 30 13:44:23 kernel: [    0.649787] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
Oct 30 13:44:23 kernel: [    0.649794] vgaarb: loaded
Oct 30 13:44:23 kernel: [    0.649965] SCSI subsystem initialized
Oct 30 13:44:23 kernel: [    0.650029] libata version 3.00 loaded.
Oct 30 13:44:23 kernel: [    0.650074] usbcore: registered new interface driver usbfs
Oct 30 13:44:23 kernel: [    0.650089] usbcore: registered new interface driver hub
Oct 30 13:44:23 kernel: [    0.650097] usbcore: registered new device driver usb
Oct 30 13:44:23 kernel: [    0.650097] ACPI: WMI: Mapper loaded
Oct 30 13:44:23 kernel: [    0.650097] PCI: Using ACPI for IRQ routing
Oct 30 13:44:23 kernel: [    0.650097] PCI: pci_cache_line_size set to 64 bytes
Oct 30 13:44:23 kernel: [    0.650117] pci 0000:04:00.0: address space collision: [mem 0xe0000000-0xefffffff pref] conflicts with GART [mem 0xe0000000-0xefffffff]
Oct 30 13:44:23 kernel: [    0.650174] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Oct 30 13:44:23 kernel: [    0.650177] reserve RAM buffer: 00000000bdff0000 - 00000000bfffffff 
Oct 30 13:44:23 kernel: [    0.650281] NetLabel: Initializing
Oct 30 13:44:23 kernel: [    0.650286] NetLabel:  domain hash size = 128
Oct 30 13:44:23 kernel: [    0.650289] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 30 13:44:23 kernel: [    0.650306] NetLabel:  unlabeled traffic allowed by default
Oct 30 13:44:23 kernel: [    0.650342] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Oct 30 13:44:23 kernel: [    0.650357] hpet0: at MMIO 0xfec01000, IRQs 2, 8, 0
Oct 30 13:44:23 kernel: [    0.650365] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Oct 30 13:44:23 kernel: [    0.680387] Switching to clocksource hpet
Oct 30 13:44:23 kernel: [    0.691526] AppArmor: AppArmor Filesystem Enabled
Oct 30 13:44:23 kernel: [    0.691554] pnp: PnP ACPI init
Oct 30 13:44:23 kernel: [    0.691579] ACPI: bus type pnp registered
Oct 30 13:44:23 kernel: [    0.696601] pnp 00:0d: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:04:00.0 BAR 0 [mem 0x00000000-0x0fffffff pref]
Oct 30 13:44:23 kernel: [    0.696611] pnp 00:0d: disabling [mem 0x000c0000-0x000dffff] because it overlaps 0000:04:00.0 BAR 0 [mem 0x00000000-0x0fffffff pref]
Oct 30 13:44:23 kernel: [    0.696620] pnp 00:0d: disabling [mem 0x000e0000-0x000fffff] because it overlaps 0000:04:00.0 BAR 0 [mem 0x00000000-0x0fffffff pref]
Oct 30 13:44:23 kernel: [    0.696628] pnp 00:0d: disabling [mem 0x00100000-0xbdffffff] because it overlaps 0000:04:00.0 BAR 0 [mem 0x00000000-0x0fffffff pref]
Oct 30 13:44:23 kernel: [    0.697158] pnp: PnP ACPI: found 15 devices
Oct 30 13:44:23 kernel: [    0.697162] ACPI: ACPI bus type pnp unregistered
Oct 30 13:44:23 kernel: [    0.697179] system 00:09: [io  0x0680-0x06ff] has been reserved
Oct 30 13:44:23 kernel: [    0.697185] system 00:09: [io  0x0295-0x0296] has been reserved
Oct 30 13:44:23 kernel: [    0.697190] system 00:09: [io  0x0778-0x077f] has been reserved
Oct 30 13:44:23 kernel: [    0.697196] system 00:09: [io  0x0b78-0x0b7f] has been reserved
Oct 30 13:44:23 kernel: [    0.697201] system 00:09: [io  0x0f78-0x0f7f] has been reserved
Oct 30 13:44:23 kernel: [    0.697210] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Oct 30 13:44:23 kernel: [    0.697215] system 00:0a: [io  0x5000-0x50bf] has been reserved
Oct 30 13:44:23 kernel: [    0.697221] system 00:0a: [io  0x50e0-0x50ff] has been reserved
Oct 30 13:44:23 kernel: [    0.697226] system 00:0a: [io  0x50c0-0x50df] has been reserved
Oct 30 13:44:23 kernel: [    0.697231] system 00:0a: [io  0xde00-0xde7f] has been reserved
Oct 30 13:44:23 kernel: [    0.697237] system 00:0a: [io  0xde80-0xdeff] has been reserved
Oct 30 13:44:23 kernel: [    0.697246] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
Oct 30 13:44:23 kernel: [    0.697253] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
Oct 30 13:44:23 kernel: [    0.697258] system 00:0c: [mem 0xfff80000-0xffffffff] has been reserved
Oct 30 13:44:23 kernel: [    0.697264] system 00:0c: [mem 0xff780000-0xff7fffff] has been reserved
Oct 30 13:44:23 kernel: [    0.703571] pci 0000:00:06.0: PCI bridge to [bus 01-01]
Oct 30 13:44:23 kernel: [    0.703578] pci 0000:00:06.0:   bridge window [io  0x7000-0x9fff]
Oct 30 13:44:23 kernel: [    0.703587] pci 0000:00:06.0:   bridge window [mem 0xff100000-0xff2fffff]
Oct 30 13:44:23 kernel: [    0.703594] pci 0000:00:06.0:   bridge window [mem pref disabled]
Oct 30 13:44:23 kernel: [    0.703603] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
Oct 30 13:44:23 kernel: [    0.703608] pci 0000:00:0a.0:   bridge window [io  0xa000-0xafff]
Oct 30 13:44:23 kernel: [    0.703616] pci 0000:00:0a.0:   bridge window [mem 0xff300000-0xff3fffff]
Oct 30 13:44:23 kernel: [    0.703622] pci 0000:00:0a.0:   bridge window [mem 0xbe900000-0xbe9fffff 64bit pref]
Oct 30 13:44:23 kernel: [    0.703632] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Oct 30 13:44:23 kernel: [    0.703636] pci 0000:00:0b.0:   bridge window [io  disabled]
Oct 30 13:44:23 kernel: [    0.703641] pci 0000:00:0b.0:   bridge window [mem disabled]
Oct 30 13:44:23 kernel: [    0.703647] pci 0000:00:0b.0:   bridge window [mem pref disabled]
Oct 30 13:44:23 kernel: [    0.703668] pci 0000:04:01.0: PCI bridge to [bus 05-05]
Oct 30 13:44:23 kernel: [    0.703673] pci 0000:04:01.0:   bridge window [io  0xc000-0xcfff]
Oct 30 13:44:23 kernel: [    0.703680] pci 0000:04:01.0:   bridge window [mem 0xff500000-0xff5fffff]
Oct 30 13:44:23 kernel: [    0.703686] pci 0000:04:01.0:   bridge window [mem 0xbeb00000-0xdeafffff pref]
Oct 30 13:44:23 kernel: [    0.703698] pci_bus 0000:00: resource 4 [io  0x0000-0xbfff]
Oct 30 13:44:23 kernel: [    0.703701] pci_bus 0000:00: resource 5 [io  0xd000-0xffff]
Oct 30 13:44:23 kernel: [    0.703703] pci_bus 0000:00: resource 6 [mem 0xfec00000-0xff4fffff]
Oct 30 13:44:23 kernel: [    0.703706] pci_bus 0000:00: resource 7 [mem 0xbe000000-0xbeafffff]
Oct 30 13:44:23 kernel: [    0.703709] pci_bus 0000:00: resource 8 [mem 0xff700000-0xfcffffffff]
Oct 30 13:44:23 kernel: [    0.703712] pci_bus 0000:01: resource 0 [io  0x7000-0x9fff]
Oct 30 13:44:23 kernel: [    0.703714] pci_bus 0000:01: resource 1 [mem 0xff100000-0xff2fffff]
Oct 30 13:44:23 kernel: [    0.703717] pci_bus 0000:02: resource 0 [io  0xa000-0xafff]
Oct 30 13:44:23 kernel: [    0.703720] pci_bus 0000:02: resource 1 [mem 0xff300000-0xff3fffff]
Oct 30 13:44:23 kernel: [    0.703722] pci_bus 0000:02: resource 2 [mem 0xbe900000-0xbe9fffff 64bit pref]
Oct 30 13:44:23 kernel: [    0.703726] pci_bus 0000:04: resource 4 [io  0xc000-0xcfff]
Oct 30 13:44:23 kernel: [    0.703728] pci_bus 0000:04: resource 5 [mem 0xff500000-0xff6fffff]
Oct 30 13:44:23 kernel: [    0.703731] pci_bus 0000:04: resource 6 [mem 0xbeb00000-0xfebfffff]
Oct 30 13:44:23 kernel: [    0.703734] pci_bus 0000:04: resource 7 [mem 0x000a0000-0x000bffff]
Oct 30 13:44:23 kernel: [    0.703737] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
Oct 30 13:44:23 kernel: [    0.703739] pci_bus 0000:05: resource 1 [mem 0xff500000-0xff5fffff]
Oct 30 13:44:23 kernel: [    0.703742] pci_bus 0000:05: resource 2 [mem 0xbeb00000-0xdeafffff pref]
Oct 30 13:44:23 kernel: [    0.703789] NET: Registered protocol family 2
Oct 30 13:44:23 kernel: [    0.703984] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 30 13:44:23 kernel: [    0.705965] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Oct 30 13:44:23 kernel: [    0.711973] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Oct 30 13:44:23 kernel: [    0.712658] TCP: Hash tables configured (established 524288 bind 65536)
Oct 30 13:44:23 kernel: [    0.712665] TCP reno registered
Oct 30 13:44:23 kernel: [    0.712686] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Oct 30 13:44:23 kernel: [    0.712751] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Oct 30 13:44:23 kernel: [    0.712923] NET: Registered protocol family 1
Oct 30 13:44:23 kernel: [    0.712954] pci 0000:00:07.3: boot interrupts on device [1022:746b] already disabled
Oct 30 13:44:23 kernel: [    0.712966] pci 0000:00:0a.0: MSI quirk detected; subordinate MSI disabled
Oct 30 13:44:23 kernel: [    0.712972] pci 0000:00:0a.0: AMD8131 rev 12 detected; disabling PCI-X MMRBC
Oct 30 13:44:23 kernel: [    0.712981] pci 0000:00:0b.0: MSI quirk detected; subordinate MSI disabled
Oct 30 13:44:23 kernel: [    0.712987] pci 0000:00:0b.0: AMD8131 rev 12 detected; disabling PCI-X MMRBC
Oct 30 13:44:23 kernel: [    0.770042] pci 0000:05:00.0: Boot video device
Oct 30 13:44:23 kernel: [    0.770049] PCI: CLS 64 bytes, default 64
Oct 30 13:44:23 kernel: [    0.770135] agpgart-amd64 0000:04:00.0: AMD 8151 AGP Bridge rev B3
Oct 30 13:44:23 kernel: [    0.782862] agpgart-amd64 0000:04:00.0: AGP aperture is 256M @ 0xe0000000
Oct 30 13:44:23 kernel: [    0.783292] Scanning for low memory corruption every 60 seconds
Oct 30 13:44:23 kernel: [    0.783474] audit: initializing netlink socket (disabled)
Oct 30 13:44:23 kernel: [    0.783489] type=2000 audit(1288446255.780:1): initialized
Oct 30 13:44:23 kernel: [    0.798522] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 30 13:44:23 kernel: [    0.800370] VFS: Disk quotas dquot_6.5.2
Oct 30 13:44:23 kernel: [    0.800467] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 30 13:44:23 kernel: [    0.801177] fuse init (API version 7.14)
Oct 30 13:44:23 kernel: [    0.801306] msgmni has been set to 5954
Oct 30 13:44:23 kernel: [    0.801992] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Oct 30 13:44:23 kernel: [    0.802002] io scheduler noop registered
Oct 30 13:44:23 kernel: [    0.802006] io scheduler deadline registered
Oct 30 13:44:23 kernel: [    0.802050] io scheduler cfq registered (default)
Oct 30 13:44:23 kernel: [    0.802411] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 30 13:44:23 kernel: [    0.802435] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 30 13:44:23 kernel: [    0.802695] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90001080000, using 1875k, total 16384k
Oct 30 13:44:23 kernel: [    0.802703] vesafb: mode is 800x600x16, linelength=1600, pages=16
Oct 30 13:44:23 kernel: [    0.802707] vesafb: scrolling: redraw
Oct 30 13:44:23 kernel: [    0.802711] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
Oct 30 13:44:23 kernel: [    0.825035] Freeing initrd memory: 6632k freed
Oct 30 13:44:23 kernel: [    0.842713] Console: switching to colour frame buffer device 100x37
Oct 30 13:44:23 kernel: [    0.883651] fb0: VESA VGA frame buffer device
Oct 30 13:44:23 kernel: [    0.884289] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Oct 30 13:44:23 kernel: [    0.885320] ACPI: Power Button [PWRB]
Oct 30 13:44:23 kernel: [    0.885809] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Oct 30 13:44:23 kernel: [    0.886714] ACPI: Power Button [PWRF]
Oct 30 13:44:23 kernel: [    0.887362] ACPI: acpi_idle registered with cpuidle
Oct 30 13:44:23 kernel: [    0.889686] ERST: Table is not found!
Oct 30 13:44:23 kernel: [    0.890310] Linux agpgart interface v0.103
Oct 30 13:44:23 kernel: [    0.890813] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Oct 30 13:44:23 kernel: [    0.891699] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 30 13:44:23 kernel: [    0.892548] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Oct 30 13:44:23 kernel: [    0.893573] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 30 13:44:23 kernel: [    0.902224] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Oct 30 13:44:23 kernel: [    0.912172] brd: module loaded
Oct 30 13:44:23 kernel: [    0.921500] loop: module loaded
Oct 30 13:44:23 kernel: [    0.931298] Fixed MDIO Bus: probed
Oct 30 13:44:23 kernel: [    0.940625] PPP generic driver version 2.4.2
Oct 30 13:44:23 kernel: [    0.950453] tun: Universal TUN/TAP device driver, 1.6
Oct 30 13:44:23 kernel: [    0.960776] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 30 13:44:23 kernel: [    0.971874] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 30 13:44:23 kernel: [    0.983572] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 30 13:44:23 kernel: [    0.995735]   alloc irq_desc for 19 on node 0
Oct 30 13:44:23 kernel: [    0.995737]   alloc kstat_irqs on node 0
Oct 30 13:44:23 kernel: [    0.995750] ohci_hcd 0000:01:00.0: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 30 13:44:23 kernel: [    1.008631] ohci_hcd 0000:01:00.0: OHCI Host Controller
Oct 30 13:44:23 kernel: [    1.021756] ohci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 1
Oct 30 13:44:23 kernel: [    1.035602] ohci_hcd 0000:01:00.0: irq 19, io mem 0xff2fd000
Oct 30 13:44:23 kernel: [    1.102151] hub 1-0:1.0: USB hub found
Oct 30 13:44:23 kernel: [    1.116502] hub 1-0:1.0: 3 ports detected
Oct 30 13:44:23 kernel: [    1.131228] ohci_hcd 0000:01:00.1: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 30 13:44:23 kernel: [    1.146842] ohci_hcd 0000:01:00.1: OHCI Host Controller
Oct 30 13:44:23 kernel: [    1.162693] ohci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 2
Oct 30 13:44:23 kernel: [    1.179251] ohci_hcd 0000:01:00.1: irq 19, io mem 0xff2fe000
Oct 30 13:44:23 kernel: [    1.252120] hub 2-0:1.0: USB hub found
Oct 30 13:44:23 kernel: [    1.269221] hub 2-0:1.0: 3 ports detected
Oct 30 13:44:23 kernel: [    1.286622] uhci_hcd: USB Universal Host Controller Interface driver
Oct 30 13:44:23 kernel: [    1.304973] PNP: No PS/2 controller found. Probing ports directly.
Oct 30 13:44:23 kernel: [    1.326137] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 30 13:44:23 kernel: [    1.344966] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 30 13:44:23 kernel: [    1.363475] mice: PS/2 mouse device common for all mice
Oct 30 13:44:23 kernel: [    1.381830] rtc_cmos 00:02: RTC can wake from S4
Oct 30 13:44:23 kernel: [    1.399637] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Oct 30 13:44:23 kernel: [    1.417130] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
Oct 30 13:44:23 kernel: [    1.434691] device-mapper: uevent: version 1.0.3
Oct 30 13:44:23 kernel: [    1.451944] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
Oct 30 13:44:23 kernel: [    1.470144] device-mapper: multipath: version 1.1.1 loaded
Oct 30 13:44:23 kernel: [    1.488062] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct 30 13:44:23 kernel: [    1.506402] cpuidle: using governor ladder
Oct 30 13:44:23 kernel: [    1.511268] usb 1-1: new full speed USB device using ohci_hcd and address 2
Oct 30 13:44:23 kernel: [    1.542580] cpuidle: using governor menu
Oct 30 13:44:23 kernel: [    1.561175] TCP cubic registered
Oct 30 13:44:23 kernel: [    1.579724] NET: Registered protocol family 10
Oct 30 13:44:23 kernel: [    1.598674] lo: Disabled Privacy Extensions
Oct 30 13:44:23 kernel: [    1.617499] NET: Registered protocol family 17
Oct 30 13:44:23 kernel: [    1.636304] powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 270 (4 cpu cores) (version 2.20.00)
Oct 30 13:44:23 kernel: [    1.675321] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
Oct 30 13:44:23 kernel: [    1.675323] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
Oct 30 13:44:23 kernel: [    1.715633] PM: Resume from disk failed.
Oct 30 13:44:23 kernel: [    1.715648] registered taskstats version 1
Oct 30 13:44:23 kernel: [    1.735718]   Magic number: 14:342:737
Oct 30 13:44:23 kernel: [    1.741004] hub 1-1:1.0: USB hub found
Oct 30 13:44:23 kernel: [    1.743945] hub 1-1:1.0: 4 ports detected
Oct 30 13:44:23 kernel: [    1.793608] rtc_cmos 00:02: setting system clock to 2010-10-30 13:44:17 UTC (1288446257)
Oct 30 13:44:23 kernel: [    1.813456] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 30 13:44:23 kernel: [    1.833337] EDD information not available.
Oct 30 13:44:23 kernel: [    1.853405] Freeing unused kernel memory: 908k freed
Oct 30 13:44:23 kernel: [    1.873832] Write protecting the kernel read-only data: 10240k
Oct 30 13:44:23 kernel: [    1.894128] Freeing unused kernel memory: 416k freed
Oct 30 13:44:23 kernel: [    1.914622] Freeing unused kernel memory: 1644k freed
Oct 30 13:44:23 kernel: [    1.943772] usb 1-2: new full speed USB device using ohci_hcd and address 3
Oct 30 13:44:23 kernel: [    2.029240] sata_sil 0000:01:0b.0: version 2.4
Oct 30 13:44:23 kernel: [    2.029301]   alloc irq_desc for 17 on node 0
Oct 30 13:44:23 kernel: [    2.029304]   alloc kstat_irqs on node 0
Oct 30 13:44:23 kernel: [    2.029318] sata_sil 0000:01:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 30 13:44:23 kernel: [    2.050329] pata_amd 0000:00:07.1: version 0.4.1
Oct 30 13:44:23 kernel: [    2.055006] Floppy drive(s): fd0 is 1.44M
Oct 30 13:44:23 kernel: [    2.057919] scsi0 : pata_amd
Oct 30 13:44:23 kernel: [    2.058306] scsi2 : sata_sil
Oct 30 13:44:23 kernel: [    2.062751] scsi1 : pata_amd
Oct 30 13:44:23 kernel: [    2.063481] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Oct 30 13:44:23 kernel: [    2.063484] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Oct 30 13:44:23 kernel: [    2.063521] scsi3 : sata_sil
Oct 30 13:44:23 kernel: [    2.063919] scsi4 : sata_sil
Oct 30 13:44:23 kernel: [    2.064108] scsi5 : sata_sil
Oct 30 13:44:23 kernel: [    2.064158] ata3: SATA max UDMA/100 mmio m1024@0xff2ffc00 tf 0xff2ffc80 irq 17
Oct 30 13:44:23 kernel: [    2.064162] ata4: SATA max UDMA/100 mmio m1024@0xff2ffc00 tf 0xff2ffcc0 irq 17
Oct 30 13:44:23 kernel: [    2.064166] ata5: SATA max UDMA/100 mmio m1024@0xff2ffc00 tf 0xff2ffe80 irq 17
Oct 30 13:44:23 kernel: [    2.064170] ata6: SATA max UDMA/100 mmio m1024@0xff2ffc00 tf 0xff2ffec0 irq 17
Oct 30 13:44:23 kernel: [    2.325139] FDC 0 is a post-1991 82077
Oct 30 13:44:23 kernel: [    2.412523] usb 2-1: new full speed USB device using ohci_hcd and address 2
Oct 30 13:44:23 kernel: [    2.420069] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 30 13:44:23 kernel: [    2.441312] ata3.00: both IDENTIFYs aborted, assuming NODEV
Oct 30 13:44:23 kernel: [    2.448787] ata2.00: ATAPI: TDK DVDRW880N, 1.33, max UDMA/33
Oct 30 13:44:23 kernel: [    2.502895] ata2.00: configured for UDMA/33
Oct 30 13:44:23 kernel: [    2.521576] scsi 1:0:0:0: CD-ROM            TDK      DVDRW880N        1.33 PQ: 0 ANSI: 5
Oct 30 13:44:23 kernel: [    2.540242] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Oct 30 13:44:23 kernel: [    2.557604] Uniform CD-ROM driver Revision: 3.20
Oct 30 13:44:23 kernel: [    2.574984] sr 1:0:0:0: Attached scsi CD-ROM sr0
Oct 30 13:44:23 kernel: [    2.575053] sr 1:0:0:0: Attached scsi generic sg0 type 5
Oct 30 13:44:23 kernel: [    2.692871] hub 2-1:1.0: USB hub found
Oct 30 13:44:23 kernel: [    2.711798] hub 2-1:1.0: 4 ports detected
Oct 30 13:44:23 kernel: [    2.923768] usb 2-3: new full speed USB device using ohci_hcd and address 3
Oct 30 13:44:23 kernel: [    2.942551] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 30 13:44:23 kernel: [    2.980105] ata4.00: both IDENTIFYs aborted, assuming NODEV
Oct 30 13:44:23 kernel: [    3.175748] hub 2-3:1.0: USB hub found
Oct 30 13:44:23 kernel: [    3.194715] hub 2-3:1.0: 3 ports detected
Oct 30 13:44:23 kernel: [    3.305672] usb 1-1.2: new full speed USB device using ohci_hcd and address 4
Oct 30 13:44:23 kernel: [    3.332536] ata5: SATA link down (SStatus 0 SControl 310)
Oct 30 13:44:23 kernel: [    3.555633] usb 1-1.3: new full speed USB device using ohci_hcd and address 5
Oct 30 13:44:23 kernel: [    3.690047] ata6: SATA link down (SStatus 0 SControl 310)
Oct 30 13:44:23 kernel: [    3.714489] usbcore: registered new interface driver hiddev
Oct 30 13:44:23 kernel: [    3.716594] ohci1394 0000:01:0c.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Oct 30 13:44:23 kernel: [    3.758706] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:06.0/0000:01:00.0/usb1/1-2/1-2:1.3/input/input2
Oct 30 13:44:23 kernel: [    3.795927] generic-usb 0003:0D8C:000C.0001: input,hidraw0: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:01:00.0-2/input3
Oct 30 13:44:23 kernel: [    3.800058] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ff2ff000-ff2ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Oct 30 13:44:23 kernel: [    3.879202] usb 2-1.2: new full speed USB device using ohci_hcd and address 4
Oct 30 13:44:23 kernel: [    3.879530] usbcore: registered new interface driver usbhid
Oct 30 13:44:23 kernel: [    3.879534] usbhid: USB HID core driver
Oct 30 13:44:23 kernel: [    4.165556] usb 2-1.3: new low speed USB device using ohci_hcd and address 5
Oct 30 13:44:23 kernel: [    5.110164] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Oct 30 13:44:23 kernel: [    5.179541] generic-usb 0003:050D:0750.0002: hiddev96,hidraw1: USB HID v1.11 Device [Belkin  Belkin UPS] on usb-0000:01:00.1-1.3/input0
Oct 30 13:44:23 kernel: [    5.315371] usb 2-1.4: new full speed USB device using ohci_hcd and address 6
Oct 30 13:44:23 kernel: [    5.462759] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00063adee0000919]
Oct 30 13:44:23 kernel: [    5.467511] ieee1394: Node added: ID:BUS[0-01:1023]  GUID[0010100345c45831]
Oct 30 13:44:23 kernel: [    5.467766] ieee1394: Host added: ID:BUS[0-02:1023]  GUID[00e081000030aa75]
Oct 30 13:44:23 kernel: [    5.469389] hub 2-1.4:1.0: USB hub found
Oct 30 13:44:23 kernel: [    5.496329] hub 2-1.4:1.0: 4 ports detected
Oct 30 13:44:23 kernel: [    5.530556] scsi6 : SBP-2 IEEE-1394
Oct 30 13:44:23 kernel: [    5.645311] usb 2-3.1: new full speed USB device using ohci_hcd and address 7
Oct 30 13:44:23 kernel: [    5.815630] input: BTC USB Hub Keyboard    as /devices/pci0000:00/0000:00:06.0/0000:01:00.1/usb2/2-3/2-3.1/2-3.1:1.0/input/input3
Oct 30 13:44:23 kernel: [    5.866185] generic-usb 0003:046E:5305.0003: input,hidraw2: USB HID v1.00 Keyboard [BTC USB Hub Keyboard   ] on usb-0000:01:00.1-3.1/input0
Oct 30 13:44:23 kernel: [    5.932312] input: BTC USB Hub Keyboard    as /devices/pci0000:00/0000:00:06.0/0000:01:00.1/usb2/2-3/2-3.1/2-3.1:1.1/input/input4
Oct 30 13:44:23 kernel: [    5.985801] generic-usb 0003:046E:5305.0004: input,hidraw3: USB HID v1.00 Device [BTC USB Hub Keyboard   ] on usb-0000:01:00.1-3.1/input1
Oct 30 13:44:23 kernel: [    6.121234] usb 2-3.2: new full speed USB device using ohci_hcd and address 8
Oct 30 13:44:23 kernel: [    6.267276] usb 2-3.2: rejected 1 configuration due to insufficient available bus power
Oct 30 13:44:23 kernel: [    6.295965] usb 2-3.2: no configuration chosen from 1 choice
Oct 30 13:44:23 kernel: [    6.401185] usb 2-3.3: new low speed USB device using ohci_hcd and address 9
Oct 30 13:44:23 kernel: [    6.633806] ieee1394: sbp2: Logged into SBP-2 device
Oct 30 13:44:23 kernel: [    6.663017] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Oct 30 13:44:23 kernel: [    6.664162] usb 2-1.4.2: new full speed USB device using ohci_hcd and address 10
Oct 30 13:44:23 kernel: [    6.723026] scsi 6:0:0:0: Direct-Access     SAMSUNG  HD103UJ          1AA0 PQ: 0 ANSI: 4
Oct 30 13:44:23 kernel: [    6.752641] sd 6:0:0:0: Attached scsi generic sg1 type 0
Oct 30 13:44:23 kernel: [    6.781731] scsi7 : SBP-2 IEEE-1394
Oct 30 13:44:23 kernel: [    6.810271] sd 6:0:0:0: [sda] 3907049984 512-byte logical blocks: (2.00 TB/1.81 TiB)
Oct 30 13:44:23 kernel: [    6.840338] sd 6:0:0:0: [sda] Write Protect is off
Oct 30 13:44:23 kernel: [    6.868702] sd 6:0:0:0: [sda] Mode Sense: 10 00 00 00
Oct 30 13:44:23 kernel: [    6.869446] sd 6:0:0:0: [sda] Cache data unavailable
Oct 30 13:44:23 kernel: [    6.897120] sd 6:0:0:0: [sda] Assuming drive cache: write through
Oct 30 13:44:23 kernel: [    6.927391] sd 6:0:0:0: [sda] Cache data unavailable
Oct 30 13:44:23 kernel: [    6.953975] sd 6:0:0:0: [sda] Assuming drive cache: write through
Oct 30 13:44:23 kernel: [    6.980160]  sda: sda1
Oct 30 13:44:23 kernel: [    7.016112] sd 6:0:0:0: [sda] Cache data unavailable
Oct 30 13:44:23 kernel: [    7.041462] sd 6:0:0:0: [sda] Assuming drive cache: write through
Oct 30 13:44:23 kernel: [    7.066701] sd 6:0:0:0: [sda] Attached SCSI disk
Oct 30 13:44:23 kernel: [    7.161069] usb 2-1.4.4: new full speed USB device using ohci_hcd and address 11
Oct 30 13:44:23 kernel: [    7.351142] Initializing USB Mass Storage driver...
Oct 30 13:44:23 kernel: [    7.376230] scsi8 : usb-storage 2-1.4.4:1.0
Oct 30 13:44:23 kernel: [    7.400666] usbcore: registered new interface driver usb-storage
Oct 30 13:44:23 kernel: [    7.424987] USB Mass Storage support registered.
Oct 30 13:44:23 kernel: [    7.820953] ieee1394: sbp2: Logged into SBP-2 device
Oct 30 13:44:23 kernel: [    7.845484] ieee1394: sbp2: Node 0-01:1023: Max speed [S400] - Max payload [2048]
Oct 30 13:44:23 kernel: [    7.871011] scsi 7:0:0:0: CD-ROM            TDK      DVDRW840G        1.03 PQ: 0 ANSI: 0 CCS
Oct 30 13:44:23 kernel: [    7.898016] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Oct 30 13:44:23 kernel: [    7.923137] sr 7:0:0:0: Attached scsi CD-ROM sr1
Oct 30 13:44:23 kernel: [    7.923415] sr 7:0:0:0: Attached scsi generic sg2 type 5
Oct 30 13:44:24 kernel: [    8.408880] scsi 8:0:0:0: Direct-Access     IOMEGA   ZIP 250          27.P PQ: 0 ANSI: 0 CCS
Oct 30 13:44:24 kernel: [    8.409539] sd 8:0:0:0: Attached scsi generic sg3 type 0
Oct 30 13:44:24 anna-install: Queueing udeb rescue-mode for later installation
Oct 30 13:44:24 init: starting pid 461, tty '': '/sbin/reopen-console /sbin/debian-installer'
Oct 30 13:44:24 init: starting pid 464, tty '/dev/tty4': '/usr/bin/tail -f /var/log/syslog'
Oct 30 13:44:24 debconf: Setting debconf/language to en
Oct 30 13:44:24 main-menu[483]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Oct 30 13:44:24 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 13:44:24 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:44:24 main-menu[483]: INFO: Menu item 'localechooser' selected
Oct 30 13:44:24 debconf: Setting debconf/language to en
Oct 30 13:44:25 kernel: [   10.056577] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Oct 30 13:44:26 localechooser: info: Language = 'en'
Oct 30 13:44:26 localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Oct 30 13:44:26 localechooser: info: Set debian-installer/language = 'en'
Oct 30 13:44:26 localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Oct 30 13:44:26 localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Oct 30 13:44:26 localechooser: info: Default country = 'US'
Oct 30 13:44:26 localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Oct 30 13:44:26 debconf: Setting debconf/language to en
Oct 30 13:44:28 localechooser: info: Set debian-installer/country = 'US'
Oct 30 13:44:28 localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Oct 30 13:44:28 localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Oct 30 13:44:28 main-menu[483]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Oct 30 13:44:28 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 13:44:28 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:44:28 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:44:28 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:44:28 main-menu[483]: INFO: Menu item 'console-setup-udeb' selected
Oct 30 13:44:28 main-menu[483]: INFO: Falling back to the package description for console-setup-pc-ekmap
Oct 30 13:44:28 main-menu[483]: INFO: Falling back to the package description for console-setup-pc-ekmap
Oct 30 13:44:28 main-menu[483]: WARNING **: Unable to set title for console-setup-udeb.
Oct 30 13:44:38 main-menu[483]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Oct 30 13:44:38 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 13:44:38 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:44:38 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:44:38 main-menu[483]: INFO: Menu item 'cdrom-detect' selected
Oct 30 13:44:38 create_floppy_devices[1580]: specified group 'floppy' unknown
Oct 30 13:44:38 net/hw-detect.hotplug: Detected hotpluggable network interface lo
Oct 30 13:44:39 hw-detect: Loading PCMCIA bridge driver module: i82365
Oct 30 13:44:39 hw-detect: FATAL: Module i82365 not found.
Oct 30 13:44:39 apt-install: Queueing package udev for later installation
Oct 30 13:44:39 apt-install: Queueing package usbutils for later installation
Oct 30 13:44:39 apt-install: Queueing package eject for later installation
Oct 30 13:44:40 check-missing-firmware: no missing firmware in /tmp/missing-firmware
Oct 30 13:44:40 cdrom-detect: Searching for Ubuntu installation media...
Oct 30 13:44:41 kernel: [   25.706188] ISO 9660 Extensions: Microsoft Joliet Level 3
Oct 30 13:44:41 cdrom-detect: CD-ROM mount succeeded: device=/dev/sr0 fstype=iso9660
Oct 30 13:44:41 kernel: [   25.946693] ISO 9660 Extensions: RRIP_1991A
Oct 30 13:44:41 cdrom-detect: Detected CD 'Ubuntu-Studio 10.10 "Maverick Meerkat" - Release amd64 (20101008)'
Oct 30 13:44:41 cdrom-detect: Detected CD 'Ubuntu-Studio 10.10 "Maverick Meerkat" - Release amd64 (20101008)'
Oct 30 13:46:32 cdrom-detect: Detected CD with 'maverick' (maverick) distribution
Oct 30 13:46:32 anna-install: Queueing udeb eject-udeb for later installation
Oct 30 13:46:32 anna-install: Queueing udeb apt-mirror-setup for later installation
Oct 30 13:46:32 anna-install: Queueing udeb apt-cdrom-setup for later installation
Oct 30 13:46:32 anna-install: Queueing udeb maverick-support for later installation
Oct 30 13:46:32 main-menu[483]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Oct 30 13:46:32 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 13:46:32 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:46:32 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:46:32 main-menu[483]: INFO: Menu item 'load-cdrom' selected
Oct 30 13:46:32 cdrom-retriever: warning: File /cdrom/dists/maverick/main/debian-installer/binary-amd64/Packages does not exist.
Oct 30 13:46:32 cdrom-retriever: warning: File /cdrom/dists/maverick/restricted/debian-installer/binary-amd64/Packages does not exist.
Oct 30 13:46:33 cdrom-retriever: warning: File /cdrom/dists/maverick/universe/debian-installer/binary-amd64/Packages does not exist.
Oct 30 13:46:33 cdrom-retriever: warning: Unable to find multiverse/debian-installer/binary-amd64/Packages in /cdrom/dists/maverick/Release.
Oct 30 13:46:33 cdrom-retriever: warning: Unable to find multiverse/debian-installer/binary-amd64/Packages.gz in /cdrom/dists/maverick/Release.
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (fat-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (btrfs-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (fat-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (btrfs-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
Oct 30 13:46:33 anna[3165]: DEBUG: retrieving apt-cdrom-setup 1:0.45ubuntu4
Oct 30 13:46:33 anna[3165]: DEBUG: retrieving apt-mirror-setup 1:0.45ubuntu4
Oct 30 13:46:33 anna[3165]: DEBUG: retrieving apt-setup-udeb 1:0.45ubuntu4
Oct 30 13:46:33 anna[3165]: DEBUG: retrieving base-installer 1.107ubuntu3
Oct 30 13:46:33 anna[3165]: DEBUG: retrieving bootstrap-base 1.107ubuntu3
Oct 30 13:46:33 anna[3165]: DEBUG: retrieving binutils-static-udeb 2.20.51.20100908-0ubuntu2
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving btrfs-tools-udeb 0.19+20100601-3
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving choose-mirror-bin 2.33ubuntu3
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving clock-setup 0.103ubuntu1
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving cryptsetup-udeb 2:1.1.2-1ubuntu1
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving di-utils-mapdevfs 1.79ubuntu1
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving debootstrap-udeb 1.0.23ubuntu1
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving dhcp3-client-udeb 3.1.3-2ubuntu6
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving e2fsprogs-udeb 1.41.12-1ubuntu2
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving libc6-udeb 2.12.1-0ubuntu6
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving eject-udeb 2.1.5+deb1+cvs20081104-7
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving finish-install 2.25ubuntu1
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving fuse-utils-udeb 2.8.4-1ubuntu1
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving libfuse2-udeb 2.8.4-1ubuntu1
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving gpgv-udeb 1.4.10-2ubuntu2
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving grub-installer 1.55ubuntu4
Oct 30 13:46:34 anna[3165]: DEBUG: retrieving disk-detect 1.73ubuntu5
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving ethdetect 1.73ubuntu5
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving jfsutils-udeb 1.1.12-2.1
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving updates-modules-2.6.35-22-generic-di 2.6.35-22.12
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving ntfsprogs-udeb 2.0.0-1ubuntu4
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving block-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving char-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving crypto-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving fs-core-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving fs-secondary-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving irda-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving md-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving message-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving nfs-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:35 anna[3165]: DEBUG: retrieving nic-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving nic-pcmcia-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving nic-shared-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving nic-usb-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving parport-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving plip-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving ppp-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving virtio-modules-2.6.35-22-generic-di 2.6.35-22.33
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving dmsetup-udeb 2:1.02.39-1ubuntu6
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving libdevmapper1.02.1-udeb 2:1.02.39-1ubuntu6
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving lvm2-udeb 2.02.54-1ubuntu6
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving libbsd0-udeb 0.2.0-1
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving libgcrypt11-udeb 1.4.5-2ubuntu1
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving libgpg-error0-udeb 1.6-1ubuntu2
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving libusb-0.1-udeb 2:0.1.12-15ubuntu2
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving mdadm-udeb 2.6.7.1-1ubuntu16
Oct 30 13:46:36 anna[3165]: DEBUG: retrieving netcfg 1.51ubuntu2
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving nobootloader 1.26
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving libntfs-3g79-udeb 1:2010.8.8-0ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving ntfs-3g-udeb 1:2010.8.8-0ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving os-prober-udeb 1.39
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partconf-mkfstab 1.33
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving libparted0-udeb 2.3-2ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving parted-udeb 2.3-2ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-auto-crypto 13ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-auto-loop 0ubuntu18
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-auto-lvm 34ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-auto-raid 15ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-auto 91ubuntu4
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-base 141ubuntu2
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-utils 141ubuntu2
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-basicfilesystems 63ubuntu7
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-basicmethods 44
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-btrfs 2
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-crypto-dm 43ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-crypto 43ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-efi 21ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-ext3 59ubuntu1
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-jfs 30
Oct 30 13:46:37 anna[3165]: DEBUG: retrieving partman-lvm 70
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving partman-md 51
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving partman-partitioning 74ubuntu2
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving partman-reiserfs 47
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving partman-target 67ubuntu1
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving partman-xfs 44
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving pkgsel 0.25ubuntu8
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving libpopt0-udeb 1.16-1
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving network-preseed 1.45
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving rdate-udeb 1:1.2-4build1
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving mkreiserfs-udeb 1:3.6.21-1build1
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving reiserfsprogs-udeb 1:3.6.21-1build1
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving rescue-mode 1.21
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving tzsetup-udeb 1:0.26ubuntu9
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving ubuntu-keyring-udeb 2010.+09.30
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving usbutils-udeb 0.87-4
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving user-setup-udeb 1.28ubuntu10
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving fdisk-udeb 2.17.2-0ubuntu1
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving libiw30-udeb 30~pre9-3ubuntu4
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving wireless-tools-udeb 30~pre9-3ubuntu4
Oct 30 13:46:38 anna[3165]: DEBUG: retrieving xfsprogs-udeb 3.1.2ubuntu1
Oct 30 13:46:39 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 13:46:39 main-menu[483]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Oct 30 13:46:39 main-menu[483]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Oct 30 13:46:39 main-menu[483]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Oct 30 13:46:39 main-menu[483]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Oct 30 13:46:39 main-menu[483]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
Oct 30 13:46:39 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:46:39 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:46:39 main-menu[483]: INFO: Menu item 'ethdetect' selected
Oct 30 13:46:39 kernel: [  144.095115] parport_pc 00:08: reported by Plug and Play ACPI
Oct 30 13:46:39 kernel: [  144.095173] parport0: PC-style at 0x378, irq 7 [PCSPP]
Oct 30 13:46:39 create_floppy_devices[5555]: specified group 'floppy' unknown
Oct 30 13:46:39 kernel: [  144.135230] tg3.c:v3.110 (April 9, 2010)
Oct 30 13:46:39 kernel: [  144.135251]   alloc irq_desc for 24 on node 0
Oct 30 13:46:39 kernel: [  144.135254]   alloc kstat_irqs on node 0
Oct 30 13:46:39 kernel: [  144.135264] tg3 0000:02:09.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
Oct 30 13:46:39 net/hw-detect.hotplug: Detected hotpluggable network interface lo
Oct 30 13:46:39 kernel: [  144.184084] tg3 0000:02:09.0: eth0: Tigon3 [partno(BCM95703A30) rev 1002] (PCI:33MHz:64-bit) MAC address 00:e0:81:41:a7:2f
Oct 30 13:46:39 kernel: [  144.184090] tg3 0000:02:09.0: eth0: attached PHY is 5703 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Oct 30 13:46:39 kernel: [  144.184094] tg3 0000:02:09.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Oct 30 13:46:39 kernel: [  144.184097] tg3 0000:02:09.0: eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Oct 30 13:46:39 net/hw-detect.hotplug: Detected hotpluggable network interface eth0
Oct 30 13:46:41 hw-detect: Loading PCMCIA bridge driver module: i82365
Oct 30 13:46:41 hw-detect: FATAL: Module i82365 not found.
Oct 30 13:46:42 check-missing-firmware: no missing firmware in /tmp/missing-firmware
Oct 30 13:46:42 kernel: [  146.971881] tg3 0000:02:09.0: eth0: Failed to load firmware "tigon/tg3_tso.bin"
Oct 30 13:46:42 kernel: [  146.971886] tg3 0000:02:09.0: eth0: TSO capability disabled
Oct 30 13:46:42 kernel: [  147.025395] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 30 13:46:42 kernel: [  147.124299] tg3 0000:02:09.0: PME# enabled
Oct 30 13:46:42 kernel: [  147.124316] tg3 0000:02:09.0: wake-up capability enabled by ACPI
Oct 30 13:46:43 check-missing-firmware: no missing firmware in /tmp/missing-firmware
Oct 30 13:46:43 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 13:46:43 main-menu[483]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Oct 30 13:46:43 main-menu[483]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Oct 30 13:46:43 main-menu[483]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Oct 30 13:46:43 main-menu[483]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Oct 30 13:46:43 main-menu[483]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
Oct 30 13:46:43 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:46:43 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:46:43 main-menu[483]: INFO: Menu item 'netcfg' selected
Oct 30 13:46:43 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Oct 30 13:46:43 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Oct 30 13:46:43 dhclient: All rights reserved.
Oct 30 13:46:43 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Oct 30 13:46:43 dhclient: 
Oct 30 13:46:43 kernel: [  148.225196] tg3 0000:02:09.0: eth0: Failed to load firmware "tigon/tg3_tso.bin"
Oct 30 13:46:43 kernel: [  148.225201] tg3 0000:02:09.0: eth0: TSO capability disabled
Oct 30 13:46:43 kernel: [  148.225222] tg3 0000:02:09.0: wake-up capability disabled by ACPI
Oct 30 13:46:43 kernel: [  148.225227] tg3 0000:02:09.0: PME# disabled
Oct 30 13:46:43 kernel: [  148.240048] tg3 0000:02:09.0: BAR 0: set to [mem 0xff3e0000-0xff3effff 64bit] (PCI address [0xff3e0000-0xff3effff]
Oct 30 13:46:44 kernel: [  148.294435] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 30 13:46:44 dhclient: Listening on LPF/eth0/00:e0:81:41:a7:2f
Oct 30 13:46:44 dhclient: Sending on   LPF/eth0/00:e0:81:41:a7:2f
Oct 30 13:46:44 dhclient: Sending on   Socket/fallback
Oct 30 13:46:44 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 30 13:46:45 kernel: [  149.857591] tg3 0000:02:09.0: eth0: Link is up at 100 Mbps, full duplex
Oct 30 13:46:45 kernel: [  149.857597] tg3 0000:02:09.0: eth0: Flow control is off for TX and off for RX
Oct 30 13:46:45 kernel: [  149.858327] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 30 13:46:47 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Oct 30 13:46:49 dhclient: DHCPOFFER of 192.168.1.151 from 192.168.1.1
Oct 30 13:46:49 dhclient: DHCPREQUEST of 192.168.1.151 on eth0 to 255.255.255.255 port 67
Oct 30 13:46:49 dhclient: DHCPACK of 192.168.1.151 from 192.168.1.1
Oct 30 13:46:49 dhclient: bound to 192.168.1.151 -- renewal in 1290701 seconds.
Oct 30 13:47:01 main-menu[483]: (process:6369): Internet Systems Consortium DHCP Client V3.1.3
Oct 30 13:47:01 main-menu[483]: (process:6369): 
Oct 30 13:47:01 main-menu[483]: (process:6369): Copyright 2004-2009 Internet Systems Consortium.
Oct 30 13:47:01 main-menu[483]: (process:6369): 
Oct 30 13:47:01 main-menu[483]: (process:6369): All rights reserved.
Oct 30 13:47:01 main-menu[483]: (process:6369): 
Oct 30 13:47:01 main-menu[483]: (process:6369): For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Oct 30 13:47:01 main-menu[483]: (process:6369): 
Oct 30 13:47:01 main-menu[483]: (process:6369): 
Oct 30 13:47:01 main-menu[483]: (process:6369): Listening on LPF/eth0/00:e0:81:41:a7:2f
Oct 30 13:47:01 main-menu[483]: (process:6369): 
Oct 30 13:47:01 main-menu[483]: (process:6369): Sending on   LPF/eth0/00:e0:81:41:a7:2f
Oct 30 13:47:01 main-menu[483]: (process:6369): Sending on   Socket/fallback
Oct 30 13:47:01 main-menu[483]: (process:6369): DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 30 13:47:01 main-menu[483]: (process:6369): DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Oct 30 13:47:01 main-menu[483]: (process:6369): DHCPOFFER of 192.168.1.151 from 192.168.1.1
Oct 30 13:47:01 main-menu[483]: (process:6369): DHCPREQUEST of 192.168.1.151 on eth0 to 255.255.255.255 port 67
Oct 30 13:47:01 main-menu[483]: (process:6369): 
Oct 30 13:47:01 main-menu[483]: (process:6369): DHCPACK of 192.168.1.151 from 192.168.1.1
Oct 30 13:47:01 main-menu[483]: (process:6369): bound to 192.168.1.151 -- renewal in 1290701 seconds.
Oct 30 13:47:01 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 13:47:01 main-menu[483]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Oct 30 13:47:01 main-menu[483]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Oct 30 13:47:01 main-menu[483]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Oct 30 13:47:01 main-menu[483]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Oct 30 13:47:01 main-menu[483]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
Oct 30 13:47:01 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:47:01 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 13:47:01 main-menu[483]: INFO: Menu item 'clock-setup' selected
Oct 30 17:46:59 clock-setup: Sat Oct 30 17:46:59 UTC 2010
Oct 30 17:46:59 clock-setup: rdate: adjust local clock by 14397.183492 seconds
Oct 30 17:47:03 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 17:47:03 main-menu[483]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Oct 30 17:47:03 main-menu[483]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Oct 30 17:47:03 main-menu[483]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Oct 30 17:47:03 main-menu[483]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Oct 30 17:47:03 main-menu[483]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
Oct 30 17:47:03 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 17:47:03 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 17:47:03 main-menu[483]: INFO: Menu item 'disk-detect' selected
Oct 30 17:47:04 create_floppy_devices[6564]: specified group 'floppy' unknown
Oct 30 17:47:04 net/hw-detect.hotplug: Detected hotpluggable network interface eth0
Oct 30 17:47:04 net/hw-detect.hotplug: Detected hotpluggable network interface lo
Oct 30 17:47:04 hw-detect: Loading PCMCIA bridge driver module: i82365
Oct 30 17:47:04 hw-detect: FATAL: Module i82365 not found.
Oct 30 17:47:05 check-missing-firmware: no missing firmware in /tmp/missing-firmware
Oct 30 17:47:05 kernel: [  172.943789] end_request: I/O error, dev fd0, sector 0
Oct 30 17:47:05 kernel: [  172.963782] end_request: I/O error, dev fd0, sector 0
Oct 30 17:47:05 anna-install: Installing dmraid-udeb
Oct 30 17:47:05 anna[7348]: DEBUG: retrieving dmraid-udeb 1.0.0.rc16-3ubuntu2
Oct 30 17:47:06 anna[7348]: DEBUG: retrieving libdmraid1.0.0.rc16-udeb 1.0.0.rc16-3ubuntu2
Oct 30 17:47:06 disk-detect: No Serial ATA RAID disks detected
Oct 30 17:47:07 check-missing-firmware: no missing firmware in /tmp/missing-firmware
Oct 30 17:47:08 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 17:47:08 main-menu[483]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Oct 30 17:47:08 main-menu[483]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Oct 30 17:47:08 main-menu[483]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Oct 30 17:47:08 main-menu[483]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Oct 30 17:47:08 main-menu[483]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
Oct 30 17:47:08 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 17:47:08 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 17:47:08 main-menu[483]: INFO: Menu item 'rescue-mode' selected
Oct 30 17:47:08 main-menu[483]: INFO: Falling back to the package description for fat-modules-2.6.35-22-generic-di
Oct 30 17:47:08 main-menu[483]: INFO: Falling back to the package description for fat-modules-2.6.35-22-generic-di
Oct 30 17:47:08 main-menu[483]: WARNING **: Unable to set title for fdisk-udeb.
Oct 30 17:47:08 main-menu[483]: WARNING **: Unable to set title for parted-udeb.
Oct 30 17:47:08 rescue: FATAL: Module ext2 not found.
Oct 30 17:47:08 rescue: FATAL: Module ext3 not found.
Oct 30 17:47:08 rescue: FATAL: Module ext4 not found.
Oct 30 17:47:08 kernel: [  175.215389] JFS: nTxBlock = 8192, nTxLock = 65536
Oct 30 17:47:08 kernel: [  175.252170] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Oct 30 17:47:08 kernel: [  175.253931] SGI XFS Quota Management subsystem
Oct 30 17:47:08 rescue: FATAL: Module md not found.
Oct 30 17:47:08 kernel: [  175.268242] md: raid0 personality registered for level 0
Oct 30 17:47:08 kernel: [  175.272442] md: raid1 personality registered for level 1
Oct 30 17:47:08 kernel: [  175.275221] async_tx: api initialized (async)
Oct 30 17:47:08 kernel: [  175.442517] raid6: int64x1   1637 MB/s
Oct 30 17:47:08 kernel: [  175.612513] raid6: int64x2   2145 MB/s
Oct 30 17:47:08 kernel: [  175.782533] raid6: int64x4   1465 MB/s
Oct 30 17:47:08 kernel: [  175.952546] raid6: int64x8   1450 MB/s
Oct 30 17:47:09 kernel: [  176.122528] raid6: sse2x1    2017 MB/s
Oct 30 17:47:09 kernel: [  176.292507] raid6: sse2x2    2691 MB/s
Oct 30 17:47:09 kernel: [  176.462512] raid6: sse2x4    3015 MB/s
Oct 30 17:47:09 kernel: [  176.462514] raid6: using algorithm sse2x4 (3015 MB/s)
Oct 30 17:47:09 kernel: [  176.464103] xor: automatically using best checksumming function: generic_sse
Oct 30 17:47:09 kernel: [  176.512505]    generic_sse:  6535.600 MB/sec
Oct 30 17:47:09 kernel: [  176.512508] xor: using function: generic_sse (6535.600 MB/sec)
Oct 30 17:47:09 kernel: [  176.518038] md: raid6 personality registered for level 6
Oct 30 17:47:09 kernel: [  176.518041] md: raid5 personality registered for level 5
Oct 30 17:47:09 kernel: [  176.518043] md: raid4 personality registered for level 4
Oct 30 17:47:09 rescue: mdadm: No arrays found in config file
Oct 30 17:47:09 rescue: FATAL: Module dm_mod not found.
Oct 30 17:47:09 rescue: FATAL: Module lvm_mod not found.
Oct 30 17:47:09 rescue: File descriptor 3 (pipe:[6342]) leaked on pvscan invocation. Parent PID 7496: log-output
Oct 30 17:47:09 rescue: File descriptor 4 (/dev/pts/0) leaked on pvscan invocation. Parent PID 7496: log-output
Oct 30 17:47:09 rescue: File descriptor 5 (/dev/pts/0) leaked on pvscan invocation. Parent PID 7496: log-output
Oct 30 17:47:09 rescue: File descriptor 6 (/dev/pts/0) leaked on pvscan invocation. Parent PID 7496: log-output
Oct 30 17:47:09 rescue:   No matching physical volumes found
Oct 30 17:47:09 rescue: File descriptor 3 (pipe:[6342]) leaked on vgscan invocation. Parent PID 7498: log-output
Oct 30 17:47:09 rescue: File descriptor 4 (/dev/pts/0) leaked on vgscan invocation. Parent PID 7498: log-output
Oct 30 17:47:09 rescue: File descriptor 5 (/dev/pts/0) leaked on vgscan invocation. Parent PID 7498: log-output
Oct 30 17:47:09 rescue: File descriptor 6 (/dev/pts/0) leaked on vgscan invocation. Parent PID 7498: log-output
Oct 30 17:47:09 rescue:   Reading all physical volumes.  This may take a while...
Oct 30 17:47:09 rescue-mode: partitions found: /dev/sda1
Oct 30 17:47:13 rescue-mode: selected root device '/dev/sda1'
Oct 30 17:47:13 rescue: umount: can't umount /target: Invalid argument
Oct 30 17:47:13 rescue: mount: mounting /dev/sda1 on /target failed: Invalid argument
Oct 30 17:47:13 rescue-mode: mount '/dev/sda1' /target failed
Oct 30 17:47:26 rescue-mode: partitions found: /dev/sda1
Oct 30 17:47:40 rescue: umount: can't umount /target: Invalid argument
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 3 (pipe:[6342]) leaked on lvdisplay invocation. Parent PID 7443: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 4 (/dev/pts/0) leaked on lvdisplay invocation. Parent PID 7443: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 5 (/dev/pts/0) leaked on lvdisplay invocation. Parent PID 7443: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 6 (/dev/pts/0) leaked on lvdisplay invocation. Parent PID 7443: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 3 (pipe:[6342]) leaked on lvdisplay invocation. Parent PID 7524: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 4 (/dev/pts/0) leaked on lvdisplay invocation. Parent PID 7524: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 5 (/dev/pts/0) leaked on lvdisplay invocation. Parent PID 7524: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 6 (/dev/pts/0) leaked on lvdisplay invocation. Parent PID 7524: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 3 (pipe:[6342]) leaked on lvdisplay invocation.
Oct 30 17:47:40 main-menu[483]: (process:7442):  Parent PID 7443: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 4 (/dev/pts/0) leaked on lvdisplay invocation.
Oct 30 17:47:40 main-menu[483]: (process:7442):  Parent PID 7443: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 5 (/dev/pts/0) leaked on lvdisplay invocation.
Oct 30 17:47:40 main-menu[483]: (process:7442):  Parent PID 7443: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 6 (/dev/pts/0) leaked on lvdisplay invocation.
Oct 30 17:47:40 main-menu[483]: (process:7442):  Parent PID 7443: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 3 (pipe:[6342]) leaked on lvdisplay invocation.
Oct 30 17:47:40 main-menu[483]: (process:7442):  Parent PID 7568: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 4 (/dev/pts/0) leaked on lvdisplay invocation.
Oct 30 17:47:40 main-menu[483]: (process:7442):  Parent PID 7568: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 5 (/dev/pts/0) leaked on lvdisplay invocation.
Oct 30 17:47:40 main-menu[483]: (process:7442):  Parent PID 7568: /bin/sh
Oct 30 17:47:40 main-menu[483]: (process:7442): File descriptor 6 (/dev/pts/0) leaked on lvdisplay invocation.
Oct 30 17:47:40 main-menu[483]: (process:7442):  Parent PID 7568: /bin/sh
Oct 30 17:47:40 main-menu[483]: INFO: Menu item 'rescue-mode' succeeded but requested to be left unconfigured.
Oct 30 17:47:40 main-menu[483]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Oct 30 17:47:40 main-menu[483]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Oct 30 17:47:40 main-menu[483]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Oct 30 17:47:40 main-menu[483]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Oct 30 17:47:40 main-menu[483]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Oct 30 17:47:40 main-menu[483]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
Oct 30 17:47:40 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 17:48:01 main-menu[483]: INFO: Falling back to the package description for console-setup-udeb
Oct 30 17:48:01 main-menu[483]: INFO: Menu item 'save-logs' selected



Does this mean that it is mising the EXT* modules to load those partitions?

---

### Post by thereid on 2010-11-01
> **kansasnoob said:**
> Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That will help us either straighten this out or give you reinstall instructions. I think there's a good chance we can get this booting.


Sorry to be such a NOOB, but i don't get this.
** How to use the boot info script**

  
[LIST]
[*] Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
[/LIST]
Dude...If I could boot into Linux, then I wouldn't have posted in the first place.
My Linux partition boot-up displays the black and white (circles) logo for a few seconds, then goes blank.

I would be happy to reinstall Ubuntu from a CD, but how do I know that it's going into the correct HD partition, and not corrupting my Windows OS? (Which I need).
:confused:

---

### Post by thereid on 2010-11-03
> **kansasnoob said:**
> Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That will help us either straighten this out or give you reinstall instructions. I think there's a good chance we can get this booting.


OK;
I had to boot from my Hardy CD, so I'm not sure this is what you want, but here it is...

=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bc49df2f-3701-4d7e-b041-dcce8999df0e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=bc49df2f-3701-4d7e-b041-dcce8999df0e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=bc49df2f-3701-4d7e-b041-dcce8999df0e ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=bc49df2f-3701-4d7e-b041-dcce8999df0e /               ext2    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  94.4GB: boot/grub/menu.lst
  94.4GB: boot/grub/stage2
  94.3GB: boot/initrd.img-2.6.24-16-generic
  94.1GB: boot/initrd.img-2.6.24-16-generic.bak
  94.2GB: boot/initrd.img-2.6.24-26-generic
  94.1GB: boot/initrd.img-2.6.24-26-generic.bak
  94.2GB: boot/initrd.img-2.6.24-27-generic
  94.2GB: boot/initrd.img-2.6.24-27-generic.bak
  94.3GB: boot/initrd.img-2.6.28-19-generic
  94.1GB: boot/initrd.img-2.6.31-22-generic
  94.2GB: boot/vmlinuz-2.6.24-16-generic
  94.2GB: boot/vmlinuz-2.6.24-26-generic
  94.3GB: boot/vmlinuz-2.6.24-27-generic
  94.1GB: boot/vmlinuz-2.6.28-19-generic
  94.1GB: boot/vmlinuz-2.6.31-22-generic
  94.1GB: initrd.img
  94.3GB: initrd.img.old
  94.1GB: vmlinuz
  94.1GB: vmlinuz.old
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sda1: device is busy
umount: /tmp/BootInfo0/sda1: device is busy

---

### Post by thereid on 2010-11-09
> **kansasnoob said:**
> Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That will help us either straighten this out or give you reinstall instructions. I think there's a good chance we can get this booting.


Kansasnoob;

I hate to be a pain, but could you Please look at my last post with the boot info script?
If that's NOT what you need, I will try a re-install.

Any help (from anyone) would be much appreciated!
Thanks!

---

### Post by thereid on 2010-11-29
I still haven't solved this problem....
Can someone please help?

I don't mind re-installing some version of Ubuntu, but I need to make sure that it installs in the correct partition, and doesn't overwrite my Win XP (which I use for other things).


Thanks

---

### Post by thereid on 2010-11-29
Since you upgraded from Jaunty to Karmic you probably still have legacy  grub, so as you boot, right after the System/BIOS screen passes, press  the Esc key. That should display the grub menu.

**Thanks for the tip, but that didn't work.  I'm running a Thinkpad with an "access IBM" button to interrupt normal startup.  That just lists drives, none of which I can identify as my Linux partition.  It's also a dual-boot disk with Win XP.**



You might also try one of the "recovery mode" entries from the grub menu followed by the "dpkg" option.
[B]I tried Recovery mode, but once it dropped to a shell it didn't recognize "dpkg" as a command.

[/B]

---

### Post by thereid on 2010-12-04
> **kansasnoob said:**
> Since you upgraded from Jaunty to Karmic you probably still have legacy grub, so as you boot, right after the System/BIOS screen passes, press the Esc key. That should display the grub menu.

If so try to boot the older Jaunty kernel (2.6.28-*). If that works I'd next run these two commands:

```
sudo apt-get -f install
``````
sudo dpkg --configure -a
```The output of either of those may provide some clues.

You might also try one of the "recovery mode" entries from the grub menu followed by the "dpkg" option.

Great. What's a grub menu, and what does it look like?
I upgraded from Hardy to karmic to Maverick(attempted).

---

### Post by wilee-nilee on 2010-12-04
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

Honestly with more then a month into your problem why haven't you just backed up what you need and done a fresh install?

Post the bootscript, and let us know if you can backup the stuff you need. **Post all the text** from the generated file from running the boot script and follow the instructions to code tag the text in my signature or the first paragraph of this post.

---

### Post by thereid on 2010-12-05
"Honestly with more then a month into your problem why haven't you just backed up what you need and done a fresh install?"

I'm TRYING to do a fresh install.  But I need to do it without corrupting my Windows partition.
I have nothing in the Ubuntu partition that I need to save.

I'm trying to overcome my own ignorance here, so I appreciate the help.

---

