---
title: "USB boot then mount raid?"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by fhebert on 2012-02-18
[SIZE=2][SIZE=2]Trying to build a new cheap home server. Want to boot from USB thumb drive and use all of the hard drives as a raid. I have an existing system that has worked well for several years but is getting OLD. I know I can't boot from a a raid and my existing system boots from a small hard drive. I am looking for some docs that explain what has to go where. I don't want to ware out the USB drive by writing to it so I want to put only what I need to boot and mount the raid.[/SIZE]
 
[SIZE=2]Before anyone suggests "just get something like Unraid[/SIZE][SIZE=2]", I do use the system for more than just storage. I run a small, in home only, web server and SQL server. I also do some software development so using a caned NAS type distro [/SIZE][SIZE=2]is probably not going to work.[/SIZE]
 
[SIZE=2]Anyhow I am sure I am not the first one to want to do this so I assume there are some docs out there.[/SIZE]
 
[SIZE=2]I am hoping someone can point me in the right direction.[/SIZE]
 
[SIZE=2]Thanks in advance.[/SIZE]
 
[/SIZE]

---

### Post by gordintoronto on 2012-02-18
This page:
[http://www.texsoft.it/index.php?c=hardware&m=hw.storage.boot-raid-squeeze&l=it](http://www.texsoft.it/index.php?c=hardware&m=hw.storage.boot-raid-squeeze&l=it)

describes how to boot from a RAID array. I have not done it; I believe in really good backup and an uncomplicated computer setup.

---

### Post by fhebert on 2012-02-18
[SIZE=2]Thanks for the reply.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I guess I should have been more specific. You can boot from a raid 1 drive, but not from raid 5.[/SIZE]
 
[SIZE=2]Basically I have 6 SATA ports and want to use all 6 for raid 5.  I figure I could clone/backup the USB drive and just keep a sapre.[/SIZE]

---

### Post by rubbleRoll on 2012-02-23
I got exactly same Issue here:
I want to boot from USB pendrive, 
then mount SW raid5 array and 
finally boot virtual machine that resides on that raid array.

I successfully created a live CD with remastersys.
It boots fine as long as the raid is offline.
But when the array is available I get kicked to BusyBox after loading initrd :'(
I couldn't figure out the Issue.
What can I do?


My Config is
sda,sdb,sdc: 2TB SATA drives
sdd: pendrive

My grub commands are
```
label LiveBase
menu label LiveBase 
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz file=/preseed/custom.seed boot=casper

```Casper.log:
```

chroot: can't execute 'mktemp': No such file or directory
cp: can't stat '/root/var/cache/debconf/config.dat': No such file or directory
cp: can't stat '/root/var/cache/debconf/passwords.dat': No such file or directory
sed: /root/etc/debconf.conf: No such file or directory
chroot: can't execute 'debconf-communicate': No such file or directory
mount: mounting /cdrom on /root/cdrom failed: Invalid argument
/scripts/casper-bottom/12fstab: line 25: can't create /root/etc/fstab: nonexistent directory
grep: /root/usr/share/i18n/SUPPORTED: No such file or directory
/scripts/casper-bottom/14locales: line 65: can't create /root/etc/default/locale: nonexistent directory
/scripts/casper-bottom/14locales: line 65: can't create /root/etc/environment: nonexistent directory
/scripts/casper-bottom/14locales: line 65: can't create /root/etc/locale.gen: nonexistent directory
chroot: can't execute '/usr/sbin/locale-gen': No such file or directory
/scripts/casper-bottom/18hostname: line 23: can't create /root/etc/hostname: nonexistent directory
/scripts/casper-bottom/18hostname: line 25: can't create /root/etc/hosts: nonexistent directory
chroot: can't execute '/usr/sbin/install-keymap': No such file or directory
/bin/casper-preseed: .: line 13: can't open '/root/usr/share/debconf/confmodule'
/scripts/casper-bottom/20xconfig: line 37: can't create /root/etc/X11/xorg.conf: nonexistent directory
/scripts/casper-bottom/22sslcert: .: line 20: can't open '/root/usr/share/debconf/confmodule'
/scripts/casper-bottom/23networking: line 31: can't create /root/etc/network/interfaces: nonexistent directory
/scripts/casper-bottom/23networking: line 103: can't create /root/etc/network/interfaces: nonexistent directory
grep: /root/etc/network/interfaces: No such file or directory
/scripts/casper-bottom/23networking: line 114: can't create /root/etc/network/interfaces: nonexistent directory
grep: /root/etc/network/interfaces: No such file or directory
/scripts/casper-bottom/23networking: line 114: can't create /root/etc/network/interfaces: nonexistent directory
grep: /root/etc/network/interfaces: No such file or directory
/scripts/casper-bottom/23networking: line 114: can't create /root/etc/network/interfaces: nonexistent directory
grep: /root/etc/network/interfaces: No such file or directory
/scripts/casper-bottom/23networking: line 114: can't create /root/etc/network/interfaces: nonexistent directory
grep: /root/etc/network/interfaces: No such file or directory
/scripts/casper-bottom/23networking: line 114: can't create /root/etc/network/interfaces: nonexistent directory
/scripts/casper-bottom/24preseed: .: line 20: can't open '/root/usr/share/debconf/confmodule'
sed: /root/etc/pam.d/login: No such file or directory
chroot: can't execute 'dpkg-divert': No such file or directory
ln: /root/usr/lib/update-notifier/apt-check: No such file or directory
chroot: can't execute 'dpkg-divert': No such file or directory
ln: /root/usr/lib/update-manager/check-new-release: No such file or directory
chroot: can't execute 'dpkg-divert': No such file or directory
ln: /root/usr/lib/update-manager/check-new-release-gtk: No such file or directory
/scripts/casper-bottom/32disable_hibernation: line 24: can't create /root/var/lib/polkit-1/localauthority/50-local.d/disable-hibernate.pkla: nonexistent directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
chroot: can't execute 'apt-cdrom': No such file or directory
umount: can't umount /root/dev: No such file or directory
umount: can't umount /root/proc: No such file or directory
umount: can't umount /root/sys: No such file or directory
chroot: can't execute 'dpkg-divert': No such file or directory
/scripts/casper-bottom/43disable_updateinitramfs: line 38: can't create /root/usr/sbin/update-initramfs: nonexistent directory
chmod: /root/usr/sbin/update-initramfs: No such file or directory
chroot: can't execute 'debconf-copydb': No such file or directory
chroot: can't execute 'debconf-copydb': No such file or directory

```

Here's BootLog, I cannot find any Issue here
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-server (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 16:36:30 UTC 2011 (Ubuntu 3.0.0-12.20-server 3.0.4)
[    0.000000] Command line: initrd=/ubninit file=/cdrom/preseed/custom.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7f90000 (usable)
[    0.000000]  BIOS-e820: 00000000d7f9e000 - 00000000d7fa0000 type 9
[    0.000000]  BIOS-e820: 00000000d7fa0000 - 00000000d7fae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d7fae000 - 00000000d7fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000d7fe0000 - 00000000d8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000220000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: HP ProLiant MicroServer, BIOS O41     07/29/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x220000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000220000000 aka 8704M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xd7f90 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000d7f90000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00d7e00000 page 2M
[    0.000000]  00d7e00000 - 00d7f90000 page 4k
[    0.000000] kernel direct mapping tables up to d7f90000 @ d7f8d000-d7f90000
[    0.000000] init_memory_mapping: 0000000100000000-0000000220000000
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 0220000000 page 2M
[    0.000000] kernel direct mapping tables up to 220000000 @ 21fffe000-220000000
[    0.000000] RAMDISK: 7efaf000 - 7ffff000
[    0.000000] ACPI: RSDP 00000000000f8f50 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 00000000d7fa0100 0007C (v01 HP     ProLiant 20110729 HP   00000097)
[    0.000000] ACPI: FACP 00000000d7fa0290 000F4 (v03 HP     ProLiant 20110729 HP   00000097)
[    0.000000] ACPI: DSDT 00000000d7fa0620 06947 (v01 HP     ProLiant 00000006 INTL 20051117)
[    0.000000] ACPI: FACS 00000000d7fae000 00040
[    0.000000] ACPI: APIC 00000000d7fa0390 00072 (v01 HP     ProLiant 20110729 HP   00000097)
[    0.000000] ACPI: MCFG 00000000d7fa0410 0003C (v01 HP     ProLiant 20110729 HP   00000097)
[    0.000000] ACPI: SPMI 00000000d7fa0450 00041 (v05 HP     ProLiant 20110729 HP   00000097)
[    0.000000] ACPI: OEMB 00000000d7fae040 00072 (v01 HP     ProLiant 20110729 HP   00000097)
[    0.000000] ACPI: HPET 00000000d7fab4e0 00038 (v01 HP     ProLiant 20110729 HP   00000097)
[    0.000000] ACPI: EINJ 00000000d7fab520 00130 (v01  AMIER AMI_EINJ 20110729 HP   00000097)
[    0.000000] ACPI: BERT 00000000d7fab6b0 00030 (v01  AMIER AMI_BERT 20110729 HP   00000097)
[    0.000000] ACPI: ERST 00000000d7fab6e0 001B0 (v01  AMIER AMI_ERST 20110729 HP   00000097)
[    0.000000] ACPI: HEST 00000000d7fab890 000A8 (v01  AMIER ABC_HEST 20110729 HP   00000097)
[    0.000000] ACPI: SSDT 00000000d7fab940 00458 (v01 HP     ProLiant 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000220000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000220000000
[    0.000000]   NODE_DATA [000000021fff9000 - 000000021fffdfff]
[    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880217800000-ffff88021e7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00220000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000d7f90
[    0.000000]     0: 0x00100000 -> 0x00220000
[    0.000000] On node 0 totalpages: 2064158
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 866248 pages, LIFO batch:31
[    0.000000]   Normal zone: 16128 pages used for memmap
[    0.000000]   Normal zone: 1163520 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000d7f90000 - 00000000d7f9e000
[    0.000000] PM: Registered nosave memory: 00000000d7f9e000 - 00000000d7fa0000
[    0.000000] PM: Registered nosave memory: 00000000d7fa0000 - 00000000d7fae000
[    0.000000] PM: Registered nosave memory: 00000000d7fae000 - 00000000d7fe0000
[    0.000000] PM: Registered nosave memory: 00000000d7fe0000 - 00000000d8000000
[    0.000000] PM: Registered nosave memory: 00000000d8000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at f0000000 (gap: f0000000:fa00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021fc00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2033689
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: initrd=/ubninit file=/cdrom/preseed/custom.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ d66c000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ cc000000
[    0.000000] PM: Registered nosave memory: 00000000cc000000 - 00000000d0000000
[    0.000000] Memory: 7977492k/8912896k available (6186k kernel code, 656264k absent, 279140k reserved, 6936k data, 904k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 66060288 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1497.484 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 2994.96 BogoMIPS (lpj=5989936)
[    0.004012] pid_max: default: 32768 minimum: 301
[    0.004044] Security Framework initialized
[    0.004064] AppArmor: AppArmor initialized
[    0.004066] Yama: becoming mindful.
[    0.005263] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.013306] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.014850] Mount-cache hash table entries: 256
[    0.015020] Initializing cgroup subsys cpuacct
[    0.015028] Initializing cgroup subsys memory
[    0.015039] Initializing cgroup subsys devices
[    0.015043] Initializing cgroup subsys freezer
[    0.015046] Initializing cgroup subsys net_cls
[    0.015049] Initializing cgroup subsys blkio
[    0.015058] Initializing cgroup subsys perf_event
[    0.015094] tseg: 0000000000
[    0.015115] CPU: Physical Processor ID: 0
[    0.015117] CPU: Processor Core ID: 0
[    0.015120] mce: CPU supports 6 MCE banks
[    0.015134] using AMD E400 aware idle routine
[    0.017232] ACPI: Core revision 20110413
[    0.023725] ftrace: allocating 26000 entries in 102 pages
[    0.028407] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069992] CPU0: AMD Turion(tm) II Neo N40L Dual-Core Processor stepping 03
[    0.072003] Performance Events: AMD PMU driver.
[    0.072003] ... version:                0
[    0.072003] ... bit width:              48
[    0.072003] ... generic registers:      4
[    0.072003] ... value mask:             0000ffffffffffff
[    0.072003] ... max period:             00007fffffffffff
[    0.072003] ... fixed-purpose events:   0
[    0.072003] ... event mask:             000000000000000f
[    0.072003] Booting Node   0, Processors  #1
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.160024] Brought up 2 CPUs
[    0.160028] Total of 2 processors activated (5990.04 BogoMIPS).
[    0.160025] System has AMD C1E enabled
[    0.160066] Switch to broadcast mode on CPU1
[    0.160643] Switch to broadcast mode on CPU0
[    0.160643] devtmpfs: initialized
[    0.162409] PM: Registering ACPI NVS region at d7fae000 (204800 bytes)
[    0.165273] print_constraints: dummy: 
[    0.165303] Time: 19:19:59  Date: 07/29/11
[    0.165357] NET: Registered protocol family 16
[    0.165501] node 0 link 0: io port [1000, ffffff]
[    0.165506] TOM: 00000000e0000000 aka 3584M
[    0.165509] Fam 10h mmconf [e0000000, efffffff]
[    0.165513] node 0 link 0: mmio [a0000, bffff]
[    0.165517] node 0 link 0: mmio [e0000000, f7ffffff] ==> [f0000000, f7ffffff]
[    0.165523] node 0 link 0: mmio [f8000000, fe6fffff]
[    0.165526] node 0 link 0: mmio [fe700000, fe8fffff]
[    0.165530] node 0 link 0: mmio [fe900000, ffdfffff]
[    0.165373] Trying to unpack rootfs image as initramfs...
[    0.165541] TOM2: 0000000220000000 aka 8704M
[    0.165544] bus: [00, 1f] on node 0 link 0
[    0.165548] bus: 00 index 0 [io  0x0000-0xffff]
[    0.165552] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.165555] bus: 00 index 2 [mem 0xf0000000-0xffffffff]
[    0.165558] bus: 00 index 3 [mem 0x220000000-0xfcffffffff]
[    0.165569] Extended Config Space enabled on 1 nodes
[    0.165584] ACPI: bus type pci registered
[    0.165660] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.165665] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.203258] PCI: Using configuration type 1 for base access
[    0.204347] bio: create slab <bio-0> at 0
[    0.205268] ACPI: EC: Look up EC in DSDT
[    0.205448] \_SB_:_OSC evaluation returned wrong type
[    0.205450] _OSC request data:1 7 
[    0.208179] ACPI: Executed 2 blocks of module-level executable AML code
[    0.210960] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.232105] ACPI: OEMN 00000000d7faaeb0 00624 (v01 AMD    NAHP     00000001 INTL 20051117)
[    0.232437] ACPI: Dynamic OEM Table Load:
[    0.232441] ACPI: OEMN           (null) 00624 (v01 AMD    NAHP     00000001 INTL 20051117)
[    0.244342] ACPI: Interpreter enabled
[    0.244349] ACPI: (supports S0 S4 S5)
[    0.244372] ACPI: Using IOAPIC for interrupt routing
[    0.249299] ACPI: No dock devices found.
[    0.249345] HEST: Table parsing has been initialized.
[    0.249350] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.250183] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.250834] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.250838] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.250843] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.250846] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.250850] pci_root PNP0A08:00: host bridge window [mem 0xd8000000-0xdfffffff]
[    0.250854] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.250858] pci_root PNP0A08:00: host bridge window [mem 0xd8000000-0xdfffffff]
[    0.250862] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff]
[    0.250868] pci_root PNP0A08:00: host bridge window expanded to [mem 0xd8000000-0xdfffffff]; [mem 0xd8000000-0xdfffffff] ignored
[    0.250873] pci_root PNP0A08:00: host bridge window expanded to [mem 0xf0000000-0xffffffff]; [mem 0xf0000000-0xffffffff] ignored
[    0.250881] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000d0000-0x000dffff] conflicts with Adapter ROM [mem 0x000cf000-0x000d19ff]
[    0.250901] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.250956] pci 0000:00:01.0: [103c:9602] type 1 class 0x000604
[    0.251005] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
[    0.251039] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.251044] pci 0000:00:06.0: PME# disabled
[    0.251081] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.251104] pci 0000:00:11.0: reg 10: [io  0xd000-0xd007]
[    0.251116] pci 0000:00:11.0: reg 14: [io  0xc000-0xc003]
[    0.251127] pci 0000:00:11.0: reg 18: [io  0xb000-0xb007]
[    0.251138] pci 0000:00:11.0: reg 1c: [io  0xa000-0xa003]
[    0.251149] pci 0000:00:11.0: reg 20: [io  0x9000-0x900f]
[    0.251161] pci 0000:00:11.0: reg 24: [mem 0xfe6ffc00-0xfe6fffff]
[    0.251220] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.251235] pci 0000:00:12.0: reg 10: [mem 0xfe6fe000-0xfe6fefff]
[    0.251308] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.251329] pci 0000:00:12.2: reg 10: [mem 0xfe6ff800-0xfe6ff8ff]
[    0.251401] pci 0000:00:12.2: supports D1 D2
[    0.251404] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.251409] pci 0000:00:12.2: PME# disabled
[    0.251432] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.251447] pci 0000:00:13.0: reg 10: [mem 0xfe6fd000-0xfe6fdfff]
[    0.251520] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.251541] pci 0000:00:13.2: reg 10: [mem 0xfe6ff400-0xfe6ff4ff]
[    0.251613] pci 0000:00:13.2: supports D1 D2
[    0.251616] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.251621] pci 0000:00:13.2: PME# disabled
[    0.251646] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.251722] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.251737] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.251748] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.251759] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.251771] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.251782] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.251818] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.251896] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.251943] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.251959] pci 0000:00:16.0: reg 10: [mem 0xfe6fc000-0xfe6fcfff]
[    0.252045] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.252066] pci 0000:00:16.2: reg 10: [mem 0xfe6ff000-0xfe6ff0ff]
[    0.252138] pci 0000:00:16.2: supports D1 D2
[    0.252141] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.252146] pci 0000:00:16.2: PME# disabled
[    0.252169] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.252191] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.252212] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.252231] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.252253] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.252308] pci 0000:01:05.0: [1002:9712] type 0 class 0x000300
[    0.252319] pci 0000:01:05.0: reg 10: [mem 0xf0000000-0xf7ffffff pref]
[    0.252326] pci 0000:01:05.0: reg 14: [io  0xe000-0xe0ff]
[    0.252333] pci 0000:01:05.0: reg 18: [mem 0xfe8f0000-0xfe8fffff]
[    0.252347] pci 0000:01:05.0: reg 24: [mem 0xfe700000-0xfe7fffff]
[    0.252363] pci 0000:01:05.0: supports D1 D2
[    0.252405] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.252410] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.252415] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
[    0.252421] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.252471] pci 0000:02:00.0: [14e4:165b] type 0 class 0x000200
[    0.252491] pci 0000:02:00.0: reg 10: [mem 0xfe9f0000-0xfe9fffff 64bit]
[    0.252573] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.252579] pci 0000:02:00.0: PME# disabled
[    0.260060] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.260070] pci 0000:00:06.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.260076] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.260081] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.260156] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.260162] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.260168] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.260174] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.260179] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.260182] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.260186] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.260190] pci 0000:00:14.4:   bridge window [mem 0xd8000000-0xdfffffff] (subtractive decode)
[    0.260194] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.260214] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.260489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.260547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.260807]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.261036]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.267020] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
[    0.267098] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
[    0.267175] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
[    0.267253] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
[    0.267313] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.267360] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.267407] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.267454] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.267588] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.267593] vgaarb: loaded
[    0.267595] vgaarb: bridge control possible 0000:01:05.0
[    0.267830] SCSI subsystem initialized
[    0.267906] libata version 3.00 loaded.
[    0.267961] usbcore: registered new interface driver usbfs
[    0.267975] usbcore: registered new interface driver hub
[    0.268007] usbcore: registered new device driver usb
[    0.268133] PCI: Using ACPI for IRQ routing
[    0.277292] PCI: pci_cache_line_size set to 64 bytes
[    0.277371] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.277374] reserve RAM buffer: 00000000d7f90000 - 00000000d7ffffff 
[    0.277493] NetLabel: Initializing
[    0.277495] NetLabel:  domain hash size = 128
[    0.277498] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.277514] NetLabel:  unlabeled traffic allowed by default
[    0.277560] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.277566] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.281055] Switching to clocksource hpet
[    0.282199] Switched to NOHz mode on CPU #1
[    0.282204] Switched to NOHz mode on CPU #0
[    0.287703] AppArmor: AppArmor Filesystem Enabled
[    0.287742] pnp: PnP ACPI init
[    0.287766] ACPI: bus type pnp registered
[    0.288184] pnp 00:00: [bus 00-ff]
[    0.288188] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.288194] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.288198] pnp 00:00: [io  0x0d00-0xffff window]
[    0.288201] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.288204] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.288207] pnp 00:00: [mem 0xd8000000-0xdfffffff window]
[    0.288211] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.288214] pnp 00:00: [mem 0xd8000000-0xdfffffff window]
[    0.288217] pnp 00:00: [mem 0xf0000000-0xffffffff window]
[    0.288291] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.288429] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.288433] pnp 00:01: [mem 0xd8000000-0xdfffffff]
[    0.288492] system 00:01: [mem 0xd8000000-0xdfffffff] has been reserved
[    0.288497] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.288570] pnp 00:02: [dma 4]
[    0.288573] pnp 00:02: [io  0x0000-0x000f]
[    0.288576] pnp 00:02: [io  0x0081-0x0083]
[    0.288579] pnp 00:02: [io  0x0087]
[    0.288581] pnp 00:02: [io  0x0089-0x008b]
[    0.288584] pnp 00:02: [io  0x008f]
[    0.288586] pnp 00:02: [io  0x00c0-0x00df]
[    0.288624] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.288637] pnp 00:03: [io  0x0070-0x0071]
[    0.288651] pnp 00:03: [irq 8]
[    0.288683] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.288735] pnp 00:04: [io  0x0061]
[    0.288768] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.288779] pnp 00:05: [io  0x00f0-0x00ff]
[    0.288786] pnp 00:05: [irq 13]
[    0.288821] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.288853] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    0.288887] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.288979] pnp 00:07: [io  0x0060]
[    0.288982] pnp 00:07: [io  0x0064]
[    0.288984] pnp 00:07: [mem 0xfec00000-0xfec00fff]
[    0.288987] pnp 00:07: [mem 0xfee00000-0xfee00fff]
[    0.289046] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.289051] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.289055] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.289227] pnp 00:08: [io  0x0010-0x001f]
[    0.289230] pnp 00:08: [io  0x0022-0x003f]
[    0.289233] pnp 00:08: [io  0x0062-0x0063]
[    0.289235] pnp 00:08: [io  0x0065-0x006f]
[    0.289238] pnp 00:08: [io  0x0072-0x007f]
[    0.289240] pnp 00:08: [io  0x0080]
[    0.289243] pnp 00:08: [io  0x0084-0x0086]
[    0.289245] pnp 00:08: [io  0x0088]
[    0.289248] pnp 00:08: [io  0x008c-0x008e]
[    0.289251] pnp 00:08: [io  0x0090-0x009f]
[    0.289253] pnp 00:08: [io  0x00a2-0x00bf]
[    0.289256] pnp 00:08: [io  0x00b1]
[    0.289258] pnp 00:08: [io  0x00e0-0x00ef]
[    0.289261] pnp 00:08: [io  0x04d0-0x04d1]
[    0.289263] pnp 00:08: [io  0x040b]
[    0.289268] pnp 00:08: [io  0x04d6]
[    0.289270] pnp 00:08: [io  0x0c00-0x0c01]
[    0.289273] pnp 00:08: [io  0x0c14]
[    0.289275] pnp 00:08: [io  0x0c50-0x0c51]
[    0.289278] pnp 00:08: [io  0x0c52]
[    0.289280] pnp 00:08: [io  0x0c6c]
[    0.289283] pnp 00:08: [io  0x0c6f]
[    0.289285] pnp 00:08: [io  0x0cd0-0x0cd1]
[    0.289288] pnp 00:08: [io  0x0cd2-0x0cd3]
[    0.289290] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.289293] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.289296] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.289298] pnp 00:08: [io  0x0800-0x089f]
[    0.289301] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.289304] pnp 00:08: [io  0x0b00-0x0b1f]
[    0.289307] pnp 00:08: [io  0x0b20-0x0b3f]
[    0.289310] pnp 00:08: [io  0x0900-0x090f]
[    0.289312] pnp 00:08: [io  0x0910-0x091f]
[    0.289315] pnp 00:08: [io  0xfe00-0xfefe]
[    0.289317] pnp 00:08: [io  0x0060]
[    0.289320] pnp 00:08: [io  0x0064]
[    0.289323] pnp 00:08: [mem 0xffb80000-0xffbfffff]
[    0.289326] pnp 00:08: [mem 0xfec10000-0xfec1001f]
[    0.289328] pnp 00:08: [mem 0xfed80000-0xfed80fff]
[    0.289332] pnp 00:08: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.289432] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.289436] system 00:08: [io  0x040b] has been reserved
[    0.289439] system 00:08: [io  0x04d6] has been reserved
[    0.289443] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.289447] system 00:08: [io  0x0c14] has been reserved
[    0.289450] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.289454] system 00:08: [io  0x0c52] has been reserved
[    0.289457] system 00:08: [io  0x0c6c] has been reserved
[    0.289461] system 00:08: [io  0x0c6f] has been reserved
[    0.289464] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.289468] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.289471] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.289475] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.289479] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.289483] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.289487] system 00:08: [io  0x0b00-0x0b1f] has been reserved
[    0.289490] system 00:08: [io  0x0b20-0x0b3f] has been reserved
[    0.289494] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.289498] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.289502] system 00:08: [io  0xfe00-0xfefe] has been reserved
[    0.289507] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.289511] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.289515] system 00:08: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.289520] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.289573] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    0.289626] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.289631] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.289752] pnp 00:0a: [mem 0x00000000-0x0009ffff]
[    0.289756] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.289759] pnp 00:0a: [mem 0x000e0000-0x000fffff]
[    0.289762] pnp 00:0a: [mem 0x00100000-0xd7ffffff]
[    0.289765] pnp 00:0a: [mem 0xfec00000-0xffffffff]
[    0.289826] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.289830] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.289834] system 00:0a: [mem 0x00100000-0xd7ffffff] could not be reserved
[    0.289839] system 00:0a: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.289843] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.289958] pnp: PnP ACPI: found 11 devices
[    0.289960] ACPI: ACPI bus type pnp unregistered
[    0.296213] PCI: max bus depth: 1 pci_try_num: 2
[    0.296235] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.296239] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.296244] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
[    0.296249] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.296255] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.296258] pci 0000:00:06.0:   bridge window [io  disabled]
[    0.296263] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.296267] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.296272] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.296275] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.296281] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.296286] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.296312] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.296317] pci 0000:00:06.0: setting latency timer to 64
[    0.296326] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.296330] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.296334] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.296337] pci_bus 0000:00: resource 7 [mem 0xd8000000-0xdfffffff]
[    0.296341] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xffffffff]
[    0.296345] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.296349] pci_bus 0000:01: resource 1 [mem 0xfe700000-0xfe8fffff]
[    0.296352] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.296357] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.296360] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.296364] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.296367] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.296371] pci_bus 0000:03: resource 7 [mem 0xd8000000-0xdfffffff]
[    0.296375] pci_bus 0000:03: resource 8 [mem 0xf0000000-0xffffffff]
[    0.296424] NET: Registered protocol family 2
[    0.296791] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.298859] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.302503] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.302947] TCP: Hash tables configured (established 524288 bind 65536)
[    0.302952] TCP reno registered
[    0.302980] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.303072] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.303278] NET: Registered protocol family 1
[    0.303295] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    1.136171] pci 0000:01:05.0: Boot video device
[    1.136181] PCI: CLS 64 bytes, default 64
[    1.136929] PCI-DMA: Disabling AGP.
[    1.137018] PCI-DMA: aperture base @ cc000000 size 65536 KB
[    1.137021] PCI-DMA: using GART IOMMU.
[    1.137026] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.141764] audit: initializing netlink socket (disabled)
[    1.141779] type=2000 audit(1311967199.140:1): initialized
[    1.196072] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.241303] VFS: Disk quotas dquot_6.5.2
[    1.241382] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.242203] fuse init (API version 7.16)
[    1.242310] msgmni has been set to 15709
[    1.242686] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.242715] io scheduler noop registered
[    1.242719] io scheduler deadline registered (default)
[    1.242773] io scheduler cfq registered
[    1.242967] pcieport 0000:00:06.0: setting latency timer to 64
[    1.243007] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
[    1.243111] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
[    1.243115] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.243120] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
[    1.243143] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.243171] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.243316] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.243324] ACPI: Power Button [PWRB]
[    1.243374] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.243379] ACPI: Power Button [PWRF]
[    1.243445] ACPI: acpi_idle registered with cpuidle
[    1.243474] ACPI: processor limited to max C-state 1
[    1.244545] APEI: Can not request iomem region <00000000d7fc21ea-00000000d7fc21ec> for GARs.
[    1.244636] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.494631] Freeing initrd memory: 16704k freed
[    1.515834] Linux agpgart interface v0.103
[    1.517144] brd: module loaded
[    1.517730] loop: module loaded
[    1.518149] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.518195] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.518778] Fixed MDIO Bus: probed
[    1.518807] PPP generic driver version 2.4.2
[    1.518874] tun: Universal TUN/TAP device driver, 1.6
[    1.518877] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.518980] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.519145] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.519197] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.519308] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.519327] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.519357] QUIRK: Enable AMD PLL fix
[    1.519371] ehci_hcd 0000:00:12.2: debug port 1
[    1.519402] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe6ff800
[    1.528134] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.528336] hub 1-0:1.0: USB hub found
[    1.528342] hub 1-0:1.0: 5 ports detected
[    1.528553] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.528581] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.528631] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.528641] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.528668] ehci_hcd 0000:00:13.2: debug port 1
[    1.528685] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe6ff400
[    1.540122] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.540321] hub 2-0:1.0: USB hub found
[    1.540326] hub 2-0:1.0: 5 ports detected
[    1.540527] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.540556] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.540603] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.540613] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.540639] ehci_hcd 0000:00:16.2: debug port 1
[    1.540658] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe6ff000
[    1.552130] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.552342] hub 3-0:1.0: USB hub found
[    1.552348] hub 3-0:1.0: 4 ports detected
[    1.552514] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.552669] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.552703] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.552805] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.552850] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe6fe000
[    1.612296] hub 4-0:1.0: USB hub found
[    1.612310] hub 4-0:1.0: 5 ports detected
[    1.612513] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.612541] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.612592] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.612616] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe6fd000
[    1.672290] hub 5-0:1.0: USB hub found
[    1.672304] hub 5-0:1.0: 5 ports detected
[    1.672507] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.672535] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.672585] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6
[    1.672610] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe6fc000
[    1.732310] hub 6-0:1.0: USB hub found
[    1.732324] hub 6-0:1.0: 4 ports detected
[    1.732469] uhci_hcd: USB Universal Host Controller Interface driver
[    1.732575] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.733432] i8042: No controller found
[    1.733546] mousedev: PS/2 mouse device common for all mice
[    1.733671] rtc_cmos 00:03: RTC can wake from S4
[    1.733773] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.733803] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.733935] device-mapper: uevent: version 1.0.3
[    1.734019] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.734033] cpuidle: using governor ladder
[    1.734036] cpuidle: using governor menu
[    1.734039] EFI Variables Facility v0.08 2004-May-17
[    1.734345] TCP cubic registered
[    1.734489] NET: Registered protocol family 10
[    1.735125] NET: Registered protocol family 17
[    1.735147] Registering the dns_resolver key type
[    1.735254] PM: Hibernation image not present or could not be loaded.
[    1.735268] registered taskstats version 1
[    1.764447]   Magic number: 3:473:345
[    1.764489] tty tty62: hash matches
[    1.764582] rtc_cmos 00:03: setting system clock to 2011-07-29 19:20:00 UTC (1311967200)
[    1.764592] powernow-k8: Found 1 AMD Turion(tm) II Neo N40L Dual-Core Processor (2 cpu cores) (version 2.20.00)
[    1.764633] powernow-k8:    0 : pstate 0 (1500 MHz)
[    1.764636] powernow-k8:    1 : pstate 1 (1300 MHz)
[    1.764638] powernow-k8:    2 : pstate 2 (1000 MHz)
[    1.764641] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.764822] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.764827] EDD information not available.
[    1.767096] Freeing unused kernel memory: 904k freed
[    1.767373] Write protecting the kernel read-only data: 12288k
[    1.778046] Freeing unused kernel memory: 1988k freed
[    1.786127] Freeing unused kernel memory: 1372k freed
<30>[    1.823533] udevd[116]: starting version 173
[    1.890114] ahci 0000:00:11.0: version 3.0
[    1.890186] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.890256] ahci 0000:00:11.0: irq 41 for MSI/MSI-X
[    1.890350] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.890356] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.891107] scsi0 : ahci
[    1.891382] scsi1 : ahci
[    1.895958] [drm] Initialized drm 1.1.0 20060810
[    1.896068] scsi2 : ahci
[    1.898381] scsi3 : ahci
[    1.898464] ata1: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 41
[    1.898469] ata2: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 41
[    1.898474] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 41
[    1.898478] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 41
[    1.905698] tg3.c:v3.119 (May 18, 2011)
[    1.905722] tg3 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.905734] tg3 0000:02:00.0: setting latency timer to 64
[    1.906980] [drm] radeon defaulting to kernel modesetting.
[    1.906985] [drm] radeon kernel modesetting enabled.
[    1.907671] scsi4 : pata_atiixp
[    1.908209] scsi5 : pata_atiixp
[    1.909014] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.909018] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.909327] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.909334] radeon 0000:01:05.0: setting latency timer to 64
[    1.909652] [drm] initializing kernel modesetting (RS880 0x1002:0x9712 0x103C:0x1609).
[    1.909686] [drm] register mmio base: 0xFE8F0000
[    1.909689] [drm] register mmio size: 65536
[    1.910503] ATOM BIOS: AMD_1407_150
[    1.910533] radeon 0000:01:05.0: VRAM: 128M 0x00000000C0000000 - 0x00000000C7FFFFFF (128M used)
[    1.910538] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    1.910861] [drm] Detected VRAM RAM=128M, BAR=128M
[    1.910868] [drm] RAM width 32bits DDR
[    1.910990] [TTM] Zone  kernel: Available graphics memory: 4032206 kiB.
[    1.910993] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    1.910996] [TTM] Initializing pool allocator.
[    1.911032] [drm] radeon: 128M of VRAM memory ready
[    1.911035] [drm] radeon: 512M of GTT memory ready.
[    1.911055] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.911058] [drm] Driver supports precise vblank timestamp query.
[    1.911081] [drm] radeon: irq initialized.
[    1.911089] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.912379] [drm] Loading RS780 Microcode
[    1.961344] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95723) rev 5784100] (PCI Express) MAC address 2c:76:8a:ad:e7:03
[    1.961352] tg3 0000:02:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.961357] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.961361] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.995454] radeon 0000:01:05.0: WB enabled
[    2.027583] [drm] ring test succeeded in 1 usecs
[    2.027773] [drm] radeon: ib pool ready.
[    2.027853] [drm] ib test succeeded in 0 usecs
[    2.028147] [drm] Radeon Display Connectors
[    2.028150] [drm] Connector 0:
[    2.028153] [drm]   VGA
[    2.028156] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.028159] [drm]   Encoders:
[    2.028161] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.056100] usb 4-3: new low speed USB device number 2 using ohci_hcd
[    2.099407] [drm] Radeon display connector VGA-1: Found valid EDID
[    2.099429] [drm] radeon: power management initialized
[    2.184165] [drm] fb mappable at 0xF0141000
[    2.184168] [drm] vram apper at 0xF0000000
[    2.184170] [drm] size 8294400
[    2.184172] [drm] fb depth is 24
[    2.184174] [drm]    pitch is 7680
[    2.184246] fbcon: radeondrmfb (fb0) is primary device
[    2.185093] Refined TSC clocksource calibration: 1497.505 MHz.
[    2.185099] Switching to clocksource tsc
[    2.220069] ata2: SATA link down (SStatus 0 SControl 300)
[    2.223279] Console: switching to colour frame buffer device 240x67
[    2.229575] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/input/input2
[    2.229693] generic-usb 0003:0B38:0003.0001: input,hidraw0: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:12.0-3/input0
[    2.237709] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.1/input/input3
[    2.237908] generic-usb 0003:0B38:0003.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:12.0-3/input1
[    2.237931] usbcore: registered new interface driver usbhid
[    2.237934] usbhid: USB HID core driver
[    2.246196] fb0: radeondrmfb frame buffer device
[    2.246199] drm: registered panic notifier
[    2.246209] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[    2.328115] usb 2-3: new high speed USB device number 2 using ehci_hcd
[    2.388086] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.400137] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.400170] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.466561] usbcore: registered new interface driver uas
[    2.843510] ata1.00: ATA-8: WDC WD20EARS-07MVWB0, 51.0AB51, max UDMA/133
[    2.843516] ata1.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.848835] ata1.00: configured for UDMA/133
[    2.849120] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EARS-07M 51.0 PQ: 0 ANSI: 5
[    2.849371] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.849528] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.849532] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.849658] sd 0:0:0:0: [sda] Write Protect is off
[    2.849665] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.849707] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.856579] ata3.00: ATA-8: WDC WD20EARS-07MVWB0, 51.0AB51, max UDMA/133
[    2.856585] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.871391] ata3.00: configured for UDMA/133
[    2.871656] scsi 2:0:0:0: Direct-Access     ATA      WDC WD20EARS-07M 51.0 PQ: 0 ANSI: 5
[    2.871906] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.872074] sd 2:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.872078] sd 2:0:0:0: [sdb] 4096-byte physical blocks
[    2.872395] sd 2:0:0:0: [sdb] Write Protect is off
[    2.872402] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.872555] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.884675]  sdb: sdb1
[    2.885123] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.890317] ata4.00: ATA-8: WDC WD20EARS-07MVWB0, 51.0AB51, max UDMA/133
[    2.890323] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.895645]  sda: sda1
[    2.896112] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.904216] ata4.00: configured for UDMA/133
[    2.904483] scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EARS-07M 51.0 PQ: 0 ANSI: 5
[    2.904726] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.904802] sd 3:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.904807] sd 3:0:0:0: [sdc] 4096-byte physical blocks
[    2.904900] sd 3:0:0:0: [sdc] Write Protect is off
[    2.904905] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.904973] sd 3:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.923898]  sdc: sdc1
[    2.924359] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.929750] Initializing USB Mass Storage driver...
[    2.936421] scsi6 : usb-storage 2-3:1.0
[    2.938957] usbcore: registered new interface driver usb-storage
[    2.938962] USB Mass Storage support registered.
[    3.065571] md: bind<sdb>
[    3.071892] md: bind<sda>
[    3.079039] md: bind<sdc>
[    3.082090] async_tx: api initialized (async)
[    3.148034] raid6: int64x1   1273 MB/s
[    3.216015] raid6: int64x2   1860 MB/s
[    3.284018] raid6: int64x4   1356 MB/s
[    3.352010] raid6: int64x8   1190 MB/s
[    3.420036] raid6: sse2x1    2140 MB/s
[    3.488005] raid6: sse2x2    3516 MB/s
[    3.556024] raid6: sse2x4    4017 MB/s
[    3.556027] raid6: using algorithm sse2x4 (4017 MB/s)
[    3.556574] xor: automatically using best checksumming function: generic_sse
[    3.576005]    generic_sse:  6131.000 MB/sec
[    3.576008] xor: using function: generic_sse (6131.000 MB/sec)
[    3.577050] md: raid6 personality registered for level 6
[    3.577054] md: raid5 personality registered for level 5
[    3.577056] md: raid4 personality registered for level 4
[    3.577337] bio: create slab <bio-1> at 1
[    3.577355] md/raid:md127: device sdc operational as raid disk 2
[    3.577358] md/raid:md127: device sda operational as raid disk 0
[    3.577361] md/raid:md127: device sdb operational as raid disk 1
[    3.577830] md/raid:md127: allocated 3230kB
[    3.577950] md/raid:md127: raid level 5 active with 3 out of 3 devices, algorithm 2
[    3.577956] RAID conf printout:
[    3.577959]  --- level:5 rd:3 wd:3
[    3.577963]  disk 0, o:1, dev:sda
[    3.577965]  disk 1, o:1, dev:sdb
[    3.577968]  disk 2, o:1, dev:sdc
[    3.578008] md127: detected capacity change from 0 to 4000794542080
[    3.581033]  md127: unknown partition table
[    3.872707] Btrfs loaded
[    3.881164] device-mapper: dm-raid45: initialized v0.2594b
[    3.883631] md: linear personality registered for level -1
[    3.886214] md: multipath personality registered for level -4
[    3.888755] md: raid0 personality registered for level 0
[    3.891417] md: raid1 personality registered for level 1
[    3.901661] md: raid10 personality registered for level 10
[    3.936706] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Micro     8.01 PQ: 0 ANSI: 0 CCS
[    3.937268] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    3.939948] sd 6:0:0:0: [sdd] 7862911 512-byte logical blocks: (4.02 GB/3.74 GiB)
[    3.940445] sd 6:0:0:0: [sdd] Write Protect is off
[    3.940453] sd 6:0:0:0: [sdd] Mode Sense: 45 00 00 08
[    3.940945] sd 6:0:0:0: [sdd] No Caching mode page present
[    3.940951] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[    3.943195] sd 6:0:0:0: [sdd] No Caching mode page present
[    3.943201] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[    3.944715]  sdd: sdd1
[    3.948148] sd 6:0:0:0: [sdd] No Caching mode page present
[    3.948153] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[    3.948158] sd 6:0:0:0: [sdd] Attached SCSI removable disk


```

---

### Post by darkod on 2012-02-23
Have you tried (both of you) setting up the raid at the same time as the OS on the stick? It should have no problems working in that case.

But since you already have an existing array, I guess what you are after is installing on the stick but using the existing raid.

Can't you just specify the same mount points for your raid when installing on the stick?

EDIT: Is this a software raid or fakeraid? With software raid you should also be able to install on the stick, boot it, then activate the array (not recreate it, just activate it), add it to /etc/fstab and off you go.

---

### Post by fhebert on 2012-02-23
In my case it will be a real software raid 5.
 
I was planning on installing Ubuntu from a USB CD.
 
I plan to have the thumb drive and the hard drives all connected.
 
My concerns are that I get everything needed to boot on the thumb drive but nothing that will do frequent writes the the flash drive. Don't want to ware it out...
 
In my current system that I am replacing I have 2 sata drives (raid 1) as the boot drive and 4 drives (raid 5).  This was pretty easy and has worked well but I was not worried about wearing out the sata drives with too much writing.

---

### Post by darkod on 2012-02-24
For a new installation to detect existing mdadm raid, after you install the OS you will need to run:
sudo mdadm --assemble --scan

That should auto detect your array under assumption it is working fine (no broken array). Later you simply add the md device in /etc/fstab and it should work just fine.

But if you have mount points like /home on the array, not sure how you need to do it, since that mount point is usually specified during the OS installation.
If your mount point is simply /data or whatever, no problem adding it after the OS install.

mdadm basics:
[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

I don't work a lot with mdadm yet, but from what I have read, the MAIN RULE is:
You use:
mdadm --create only once when creating the array first time
If you want to use the same array in a new installation, you do it with:
mdadm --assemble

If you use the --create again it will create new blank array deleting all your data on the existing. So just watch out for that.

---

### Post by rubbleRoll on 2012-02-24
> **darkod said:**
> Have you tried (both of you) setting up the raid at the same time as the OS on the stick? It should have no problems working in that case.

Yes, I setup a VM that as well has 3 SATA disks on SATA Port 0-2. I made a raid5 array of these. Then I introduced another disk where I installed ubuntu server. This system starts as expected. I remastered the systems installation and put it on my USB pendrive.
When I inserted the USB drive to my physical server machine it goes to busybox after initrd load. Boot messages show that mdadm detects all 3 raid drives ok. Even USB mass storage is detected fine.

> **darkod said:**
> 
But since you already have an existing array, I guess what you are after is installing on the stick but using the existing raid.
 
Correct. I want to have a liveCD installation on the USB and boot from there and just mount the raid as data storage. When boot is done I'd like to start VM that is stored on the raid.

> **darkod said:**
> 
Can't you just specify the same mount points for your raid when installing on the stick?

EDIT: Is this a software raid or fakeraid? With software raid you should also be able to install on the stick, boot it, then activate the array (not recreate it, just activate it), add it to /etc/fstab and off you go.
It's software raid. 
I created liveCD .iso with Remastersys and then copied it to USB via unetbootin. 
Unfortunately I get dropped to busybox when booting before /etc/fstab is available. I guess the rootfs is not getting correctly mounted somehow. I'll post boot messages later.

---

### Post by rubbleRoll on 2012-02-29
I managed to boot from pendrive by removing the initfs script for mdadm: 
/usr/share/initramfs-tools/scripts/mdadm

When system is up I try to assemble the raid. Unfortunately I get resource busy when I try to add any of them to raid. None of the disks is mounted.

---

### Post by rubbleRoll on 2012-03-11
I solved the last Issue by formatting the raid partition /dev/md0 with correct filesystem. 
I did this by booting into busybox and then manually assembled the array and formatted it accordingly. 
Now it gets mounted correctly on startup :P

---

