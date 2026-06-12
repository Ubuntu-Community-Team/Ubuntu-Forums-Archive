---
title: "Laptop running 12.04 won't power down on &quot;shutdown&quot; or &quot;restart"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2012-12-28
I have a Compaq Presaro 2100 on which I have been running Ubuntu Lucid Lynx and am upgrading to Ubuntu Precise Pangolin 12.04.1.  My system is multi-partition and multi-boot.  When running under Lucid, I can do either a restart or a shutdown and the computer powers off.  Also, suspend and resume work, although hibernate doesn't.  However, when I run Precise (either version 12.04 or 12.04.1) and do a restart or shutdown, the computer won't power down.  It hangs during the shutdown with "Ubuntu" and some progress dots underneath it.  One, two, or three dots will "brighten" and then all activity stops. The screen continues to show "Ubuntu" and dots.  The only way out is to push the power button killing power.  In trying to solve this problem I noticed that when I boot from a 12.04 ,or 12.04.1 cd and then try to shutdown, the computer will eject the cd and issue a message to "remove the cd, and press enter".  However, when I do a requested and push Enter, the computer hangs at this point and once again I have to push the power button to kill the computer.  Otherwise it will sit with that message forever.  Again, this works correctly under 10.04 Lucid Lynx.

Anyone have any idea of what might be wrong?  I had some trouble with grub, when I installed my first version of 12.04 (I already had Lucid installed, but it fixed itself.  Could grub cause a shutdown problem, and even affect shutting down from the live cd?  If this is possible, is there any way to reinstall grub without reformatting the entire disk.

---

### Post by rajhanschinmay on 2012-12-29
You can try:
sudo reboot 
or
sudo shutdown -h now

Many users had this problem when restarting using GUI.
But with commands it worked.

Your bug may be related to this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985471](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985471)

Is ur OS 32 bit or 64 bit/

Thank you.

---

### Post by Ralph L on 2012-12-30
Thanks for the response.  My system is 32 bit.  Its an old system--probably pre-2005.  Under 12.04, in addition to shutdown not working, neither suspend nor hibernate work properly.  For example, it will suspend but not resume.  Everything but hibernate worked properly under 10.04 Lucid Lynx.  So somebody changed something.

Neither "sudo reboot" nor "sudo shutdown -h now" worked.  Both hung in the same way that shutdown or restart from the menu hung.

I tried making the change suggested by [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985471](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985471) adding "reboot=pci" to /etc/default/grub so it read GRUB_CMDLINE_LINUX_DEFAULT="reboot=pci quiet splash", and then doing and then doing "sudo update-grub".

I also tried the fix from [http://ubuntuguide.net/can-not-shutdown-in-ubuntu-12-04-precise-pangolin](http://ubuntuguide.net/can-not-shutdown-in-ubuntu-12-04-precise-pangolin) , adding "acpi=force" to get GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force", and then doing "sudo update-grub".  I also tried both of them together.  

In addition, I tried the fix from [http://ubuntuforums.org/showthread.php?t=1427024](http://ubuntuforums.org/showthread.php?t=1427024) , adding  "acpi=force" to the next line to get GRUB_CMDLINE_LINUX=GRUB_CMDLINE_LINUX="acpi=force".  I also, tried adding all three suggestion at once.  None of this helped.

I looked at /etc/default/grub in Lucid, where everything works, and it was just the same as the Precise one (with none of the above mods)

So I am still stuck.  If you have other ideas, please pass them along.  Also, I don't understand grub and its role in shutdown and resume.  If you could enlighten me on that it would be appreciated.

Thanks
Ralph

---

### Post by Ralph L on 2013-01-08
bump!!  Come on people; I really could use some help on this by somebody who understands boot up and shutdown.  I read a lot of stuff, but I still don't understand it.

I have gotten some additional information that I hope could be useful to a knowledgeable person:

1.  Here is the output of dmesg immediately after start up:
```
ralph@Presario:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-35-generic-pae (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 (Ubuntu 3.2.0-35.55-generic-pae 3.2.34)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003beff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003beff000 - 000000003bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf00000 - 000000003c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Hewlett-Packard           Presario 2100 (DM728A)   /0024                     , BIOS KAM1.48   08/22/2003
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3bef0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DAFFF uncachable
[    0.000000]   DB000-DBFFF write-protect
[    0.000000]   DC000-DFFFF write-back
[    0.000000]   E0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364ea000 - 3726d000
[    0.000000] ACPI: RSDP 000f7450 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3bef8c94 00030 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3befee2b 00074 (v01 ATI    Raptor   06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 3bef8cc4 06167 (v01    ATI U1_M1535 06040000 MSFT 0100000D)
[    0.000000] ACPI: FACS 3befffc0 00040
[    0.000000] ACPI: BOOT 3befee9f 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3befeec7 00139 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] 66MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0003bef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bef0
[    0.000000] On node 0 totalpages: 245375
[    0.000000] free_area_init_node: node 0, pgdat c186b1c0, node_mem_map f747d200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 134 pages used for memmap
[    0.000000]   HighMem zone: 17004 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3c000000 (gap: 3c000000:c3fc0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7469000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243457
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=f6318a7b-151b-4731-8858-4f1fe5edd391 ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3927552 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003bef0)
[    0.000000] Memory: 944884k/981952k available (5825k kernel code, 36616k reserved, 2849k data, 744k init, 68552k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1879000 - 0xc1933000   ( 744 kB)
[    0.000000]       .data : 0xc15b05bc - 0xc1878a00   (2849 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b05bc   (5825 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5c08000 soft=f5c0a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1855.137 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3710.27 BogoMIPS (lpj=7420548)
[    0.004025] pid_max: default: 32768 minimum: 301
[    0.004081] Security Framework initialized
[    0.004153] AppArmor: AppArmor initialized
[    0.004161] Yama: becoming mindful.
[    0.008105] Mount-cache hash table entries: 512
[    0.008442] Initializing cgroup subsys cpuacct
[    0.008460] Initializing cgroup subsys memory
[    0.008482] Initializing cgroup subsys devices
[    0.008491] Initializing cgroup subsys freezer
[    0.008500] Initializing cgroup subsys blkio
[    0.008519] Initializing cgroup subsys perf_event
[    0.008576] mce: CPU supports 4 MCE banks
[    0.008723] SMP alternatives: switching to UP code
[    0.019893] Freeing SMP alternatives: 24k freed
[    0.019968] ACPI: Core revision 20110623
[    0.025056] ACPI: setting ELCR to 0200 (from 0e28)
[    0.025317] ftrace: allocating 26576 entries in 53 pages
[    0.028233] weird, boot CPU (#0) not listed by the BIOS.
[    0.028260] SMP motherboard not detected.
[    0.028268] Local APIC not detected. Using dummy APIC emulation.
[    0.028273] SMP disabled
[    0.028279] Performance Events: 
[    0.028287] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.028294] no hardware sampling interrupt available.
[    0.028303] AMD PMU driver.
[    0.028314] ... version:                0
[    0.028319] ... bit width:              48
[    0.028323] ... generic registers:      4
[    0.028328] ... value mask:             0000ffffffffffff
[    0.028334] ... max period:             00007fffffffffff
[    0.028339] ... fixed-purpose events:   0
[    0.028343] ... event mask:             000000000000000f
[    0.028946] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[    0.028989] Brought up 1 CPUs
[    0.028996] Total of 1 processors activated (3710.27 BogoMIPS).
[    0.029407] devtmpfs: initialized
[    0.029628] EVM: security.selinux
[    0.029633] EVM: security.SMACK64
[    0.029638] EVM: security.capability
[    0.029710] PM: Registering ACPI NVS region at 3beff000 (4096 bytes)
[    0.033746] print_constraints: dummy: 
[    0.033805] RTC time: 13:38:18, date: 01/08/13
[    0.033890] NET: Registered protocol family 16
[    0.034137] EISA bus registered
[    0.034163] ACPI: bus type pci registered
[    0.046532] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
[    0.046541] PCI: Using configuration type 1 for base access
[    0.048635] bio: create slab <bio-0> at 0
[    0.048814] ACPI: Added _OSI(Module Device)
[    0.048822] ACPI: Added _OSI(Processor Device)
[    0.048828] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.048833] ACPI: Added _OSI(Processor Aggregator Device)
[    0.049902] ACPI: EC: Look up EC in DSDT
[    0.060457] ACPI: Interpreter enabled
[    0.060478] ACPI: (supports S0 S3 S4 S5)
[    0.060509] ACPI: Using PIC for interrupt routing
[    0.100373] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.100521] ACPI: No dock devices found.
[    0.100529] HEST: Table not found.
[    0.100541] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.100717] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.101054] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.101059] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff] (ignored)
[    0.101064] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff] (ignored)
[    0.101067] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000cbfff] (ignored)
[    0.101071] pci_root PNP0A03:00: host bridge window [mem 0x000cc000-0x000cffff] (ignored)
[    0.101075] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d7fff] (ignored)
[    0.101079] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000cefff] (ignored)
[    0.101083] pci_root PNP0A03:00: host bridge window [mem 0x3c000000-0xfff7ffff] (ignored)
[    0.101087] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.101091] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.101115] pci 0000:00:00.0: [1002:cab0] type 0 class 0x000600
[    0.101130] pci 0000:00:00.0: reg 10: [mem 0xd4000000-0xd7ffffff pref]
[    0.101137] pci 0000:00:00.0: reg 14: [mem 0xd0500000-0xd0500fff pref]
[    0.101143] pci 0000:00:00.0: reg 18: [io  0x8090-0x8093]
[    0.101197] pci 0000:00:01.0: [1002:700f] type 1 class 0x000604
[    0.101235] pci 0000:00:02.0: [10b9:5237] type 0 class 0x000c03
[    0.101249] pci 0000:00:02.0: reg 10: [mem 0xd0006000-0xd0006fff]
[    0.101300] pci 0000:00:02.0: PME# supported from D3cold
[    0.101307] pci 0000:00:02.0: PME# disabled
[    0.101328] pci 0000:00:06.0: [10b9:5451] type 0 class 0x000401
[    0.101342] pci 0000:00:06.0: reg 10: [io  0x8400-0x84ff]
[    0.101351] pci 0000:00:06.0: reg 14: [mem 0xd0007000-0xd0007fff]
[    0.101397] pci 0000:00:06.0: supports D1 D2
[    0.101400] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.101405] pci 0000:00:06.0: PME# disabled
[    0.101424] pci 0000:00:07.0: [10b9:1533] type 0 class 0x000601
[    0.101512] pci 0000:00:08.0: [10b9:5457] type 0 class 0x000703
[    0.101526] pci 0000:00:08.0: reg 10: [mem 0xd0008000-0xd0008fff]
[    0.101535] pci 0000:00:08.0: reg 14: [io  0x8800-0x88ff]
[    0.101580] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.101584] pci 0000:00:08.0: PME# disabled
[    0.101602] pci 0000:00:09.0: [14e4:4320] type 0 class 0x000280
[    0.101616] pci 0000:00:09.0: reg 10: [mem 0xd0004000-0xd0005fff]
[    0.101665] pci 0000:00:09.0: supports D1 D2
[    0.101668] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.101673] pci 0000:00:09.0: PME# disabled
[    0.101692] pci 0000:00:0a.0: [1217:6972] type 2 class 0x000607
[    0.101706] pci 0000:00:0a.0: reg 10: [mem 0x80000000-0x80000fff]
[    0.101729] pci 0000:00:0a.0: supports D1 D2
[    0.101732] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.101736] pci 0000:00:0a.0: PME# disabled
[    0.101756] pci 0000:00:0c.0: [104c:8026] type 0 class 0x000c00
[    0.101771] pci 0000:00:0c.0: reg 10: [mem 0xd0009000-0xd00097ff]
[    0.101780] pci 0000:00:0c.0: reg 14: [mem 0xd0000000-0xd0003fff]
[    0.101829] pci 0000:00:0c.0: supports D1 D2
[    0.101832] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot
[    0.101837] pci 0000:00:0c.0: PME# disabled
[    0.101858] pci 0000:00:10.0: [10b9:5229] type 0 class 0x000101
[    0.101891] pci 0000:00:10.0: reg 20: [io  0x8080-0x808f]
[    0.101936] pci 0000:00:11.0: [10b9:7101] type 0 class 0x000680
[    0.101991] pci 0000:00:11.0: quirk: [io  0x8000-0x803f] claimed by ali7101 ACPI
[    0.102002] pci 0000:00:11.0: quirk: [io  0x8040-0x805f] claimed by ali7101 SMB
[    0.102028] pci 0000:00:12.0: [100b:0020] type 0 class 0x000200
[    0.102042] pci 0000:00:12.0: reg 10: [io  0x8c00-0x8cff]
[    0.102051] pci 0000:00:12.0: reg 14: [mem 0xd000a000-0xd000afff]
[    0.102082] pci 0000:00:12.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.102103] pci 0000:00:12.0: supports D1 D2
[    0.102106] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.102110] pci 0000:00:12.0: PME# disabled
[    0.102158] pci 0000:01:05.0: [1002:4336] type 0 class 0x000300
[    0.102172] pci 0000:01:05.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    0.102181] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.102189] pci 0000:01:05.0: reg 18: [mem 0xd0100000-0xd010ffff]
[    0.102212] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.102238] pci 0000:01:05.0: supports D1 D2
[    0.102266] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.102276] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.102281] pci 0000:00:01.0:   bridge window [mem 0xd0100000-0xd01fffff]
[    0.102286] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.102293] pci 0000:00:0a.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[    0.102331] pci_bus 0000:00: on NUMA node 0
[    0.102337] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.102418] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.102481]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.105112] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[    0.105220] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[    0.105323] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 *10)
[    0.105425] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *9
[    0.105528] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[    0.105631] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 *11)
[    0.105731] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[    0.105833] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[    0.105934] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[    0.106171] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.106181] vgaarb: loaded
[    0.106186] vgaarb: bridge control possible 0000:01:05.0
[    0.106421] i2c-core: driver [aat2870] using legacy suspend method
[    0.106428] i2c-core: driver [aat2870] using legacy resume method
[    0.106616] SCSI subsystem initialized
[    0.106759] libata version 3.00 loaded.
[    0.106863] usbcore: registered new interface driver usbfs
[    0.106889] usbcore: registered new interface driver hub
[    0.106949] usbcore: registered new device driver usb
[    0.107142] PCI: Using ACPI for IRQ routing
[    0.107152] PCI: pci_cache_line_size set to 32 bytes
[    0.107210] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.107215] reserve RAM buffer: 000000003bef0000 - 000000003bffffff 
[    0.107439] NetLabel: Initializing
[    0.107446] NetLabel:  domain hash size = 128
[    0.107451] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.107479] NetLabel:  unlabeled traffic allowed by default
[    0.107571] Switching to clocksource pit
[    0.119619] AppArmor: AppArmor Filesystem Enabled
[    0.119738] pnp: PnP ACPI init
[    0.119782] ACPI: bus type pnp registered
[    0.120093] pnp 00:00: [bus 00-ff]
[    0.120098] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.120102] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.120106] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.120109] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.120112] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.120116] pnp 00:00: [mem 0x000d0000-0x000d7fff window]
[    0.120119] pnp 00:00: [mem 0x000a0000-0x000cefff window]
[    0.120123] pnp 00:00: [mem 0x3c000000-0xfff7ffff window]
[    0.120127] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.120130] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.120134] pnp 00:00: [io  0x0d00-0xffff window]
[    0.120256] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.120564] pnp 00:01: [io  0x0000-0x000f]
[    0.120569] pnp 00:01: [io  0x0081-0x008f]
[    0.120572] pnp 00:01: [io  0x00c0-0x00df]
[    0.120576] pnp 00:01: [dma 4]
[    0.120627] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.120647] pnp 00:02: [io  0x0070-0x0073]
[    0.120656] pnp 00:02: [irq 8]
[    0.120701] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.120717] pnp 00:03: [io  0x00f0-0x00fe]
[    0.120721] pnp 00:03: [irq 13]
[    0.120774] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.120788] pnp 00:04: [io  0x0061]
[    0.120832] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.120848] pnp 00:05: [io  0x0060]
[    0.120851] pnp 00:05: [io  0x0064]
[    0.120854] pnp 00:05: [irq 1]
[    0.120899] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.120913] pnp 00:06: [irq 12]
[    0.120975] pnp 00:06: Plug and Play ACPI device, IDs SYN0105 SYN0100 SYN0002 PNP0f13 (active)
[    0.120995] pnp 00:07: [io  0x0080]
[    0.120998] pnp 00:07: [io  0x00b0-0x00b3]
[    0.121001] pnp 00:07: [io  0x0092]
[    0.121004] pnp 00:07: [io  0x040b]
[    0.121007] pnp 00:07: [io  0x0480-0x048f]
[    0.121010] pnp 00:07: [io  0x04d0-0x04d1]
[    0.121013] pnp 00:07: [io  0x04d6]
[    0.121016] pnp 00:07: [io  0x8000-0x807f]
[    0.121019] pnp 00:07: [io  0xff00-0xff01]
[    0.121022] pnp 00:07: [io  0x8004-0x8005]
[    0.121025] pnp 00:07: [io  0xfe00-0xfefe]
[    0.121028] pnp 00:07: [mem 0xe0500000-0xe0500fff]
[    0.121031] pnp 00:07: [mem 0xd0500000-0xd0500fff]
[    0.121051] pnp 00:07: disabling [mem 0xe0500000-0xe0500fff] because it overlaps 0000:00:01.0 BAR 15 [mem 0xe0000000-0xefffffff pref]
[    0.121094] pnp 00:07: disabling [io  0x8004-0x8005] because it overlaps 0000:00:11.0 BAR 13 [io  0x8000-0x803f]
[    0.121111] pnp 00:07: disabling [mem 0xe0500000-0xe0500fff disabled] because it overlaps 0000:01:05.0 BAR 0 [mem 0xe0000000-0xefffffff pref]
[    0.121181] system 00:07: [io  0x040b] has been reserved
[    0.121189] system 00:07: [io  0x0480-0x048f] has been reserved
[    0.121197] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.121204] system 00:07: [io  0x04d6] has been reserved
[    0.121211] system 00:07: [io  0x8000-0x807f] could not be reserved
[    0.121218] system 00:07: [io  0xff00-0xff01] has been reserved
[    0.121236] system 00:07: [io  0xfe00-0xfefe] has been reserved
[    0.121245] system 00:07: [mem 0xd0500000-0xd0500fff] has been reserved
[    0.121255] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.121624] pnp 00:08: [io  0x03f0-0x03f5]
[    0.121628] pnp 00:08: [io  0x03f7]
[    0.121632] pnp 00:08: [irq 6]
[    0.121635] pnp 00:08: [dma 2]
[    0.121713] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.122135] pnp 00:09: [io  0x0378-0x037f]
[    0.122139] pnp 00:09: [io  0x0778-0x077f]
[    0.122143] pnp 00:09: [irq 7]
[    0.122146] pnp 00:09: [dma 0]
[    0.122467] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.122733] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.122737] pnp 00:0a: [irq 4]
[    0.122839] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.123188] pnp: PnP ACPI: found 11 devices
[    0.123196] ACPI: ACPI bus type pnp unregistered
[    0.123206] PnPBIOS: Disabled by ACPI PNP
[    0.161105] Switching to clocksource acpi_pm
[    0.161156] PCI: max bus depth: 1 pci_try_num: 2
[    0.161199] pci 0000:00:12.0: BAR 6: assigned [mem 0x3c000000-0x3c00ffff pref]
[    0.161212] pci 0000:00:0a.0: BAR 16: assigned [mem 0x40000000-0x43ffffff]
[    0.161221] pci 0000:00:0a.0: BAR 15: assigned [mem 0x44000000-0x47ffffff pref]
[    0.161232] pci 0000:00:0a.0: BAR 14: assigned [io  0x1000-0x10ff]
[    0.161241] pci 0000:00:0a.0: BAR 13: assigned [io  0x1400-0x14ff]
[    0.161250] pci 0000:01:05.0: BAR 6: assigned [mem 0xd0120000-0xd013ffff pref]
[    0.161259] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.161267] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.161276] pci 0000:00:01.0:   bridge window [mem 0xd0100000-0xd01fffff]
[    0.161284] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.161296] pci 0000:00:0a.0: CardBus bridge to [bus 02-05]
[    0.161302] pci 0000:00:0a.0:   bridge window [io  0x1400-0x14ff]
[    0.161311] pci 0000:00:0a.0:   bridge window [io  0x1000-0x10ff]
[    0.161319] pci 0000:00:0a.0:   bridge window [mem 0x44000000-0x47ffffff pref]
[    0.161329] pci 0000:00:0a.0:   bridge window [mem 0x40000000-0x43ffffff]
[    0.161526] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    0.161535] PCI: setting IRQ 11 as level-triggered
[    0.161542] pci 0000:00:0a.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    0.161555] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.161559] pci_bus 0000:00: resource 1 [mem 0x00000000-0x3ffffffff]
[    0.161563] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.161566] pci_bus 0000:01: resource 1 [mem 0xd0100000-0xd01fffff]
[    0.161570] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff pref]
[    0.161574] pci_bus 0000:02: resource 0 [io  0x1400-0x14ff]
[    0.161578] pci_bus 0000:02: resource 1 [io  0x1000-0x10ff]
[    0.161581] pci_bus 0000:02: resource 2 [mem 0x44000000-0x47ffffff pref]
[    0.161585] pci_bus 0000:02: resource 3 [mem 0x40000000-0x43ffffff]
[    0.161691] NET: Registered protocol family 2
[    0.161824] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.162536] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.165879] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.167659] TCP: Hash tables configured (established 131072 bind 65536)
[    0.167668] TCP reno registered
[    0.167676] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.167724] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.167958] NET: Registered protocol family 1
[    0.167990] pci 0000:00:00.0: ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb
[    0.168370] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[    0.168380] PCI: setting IRQ 10 as level-triggered
[    0.168386] pci 0000:00:02.0: PCI INT A -> Link[LNKU] -> GSI 10 (level, low) -> IRQ 10
[    0.440068] pci 0000:00:02.0: PCI INT A disabled
[    0.440090] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    0.440129] pci 0000:01:05.0: Boot video device
[    0.440134] PCI: CLS 64 bytes, default 32
[    0.440265] Simple Boot Flag at 0x36 set to 0x1
[    0.440920] audit: initializing netlink socket (disabled)
[    0.440947] type=2000 audit(1357652298.437:1): initialized
[    0.470262] Trying to unpack rootfs image as initramfs...
[    0.504955] highmem bounce pool size: 64 pages
[    0.504990] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.516118] VFS: Disk quotas dquot_6.5.2
[    0.516263] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.517336] fuse init (API version 7.17)
[    0.517501] msgmni has been set to 1711
[    0.528598] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.532379] io scheduler noop registered
[    0.532402] io scheduler deadline registered
[    0.532452] io scheduler cfq registered (default)
[    0.532770] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.532833] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.533240] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.533382] ACPI: AC Adapter [ACAD] (on-line)
[    0.533651] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.533670] ACPI: Power Button [PWRB]
[    0.533765] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.560551] ACPI: Lid Switch [LID]
[    0.560749] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.560767] ACPI: Power Button [PWRF]
[    0.560926] Marking TSC unstable due to TSC halts in idle
[    0.560942] ACPI: acpi_idle registered with cpuidle
[    0.978476] Freeing initrd memory: 13836k freed
[    2.164149] thermal LNXTHERM:00: registered as thermal_zone0
[    2.164177] ACPI: Thermal Zone [THRM] (60 C)
[    2.164317] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.164339] ACPI: Battery Slot [BAT1] (battery absent)
[    2.164382] ERST: Table is not found!
[    2.164387] GHES: HEST is not enabled!
[    2.164828] ACPI: Battery Slot [BAT1] (battery present)
[    2.164864] isapnp: Scanning for PnP cards...
[    2.170484] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.191062] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.300787] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.301103] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[    2.301113] PCI: setting IRQ 3 as level-triggered
[    2.301121] serial 0000:00:08.0: PCI INT A -> Link[LNKG] -> GSI 3 (level, low) -> IRQ 3
[    2.301153] serial 0000:00:08.0: PCI INT A disabled
[    2.301412] Linux agpgart interface v0.103
[    2.304100] brd: module loaded
[    2.305400] loop: module loaded
[    2.305842] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    2.305978] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    2.306626] Fixed MDIO Bus: probed
[    2.306666] tun: Universal TUN/TAP device driver, 1.6
[    2.306672] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.306763] PPP generic driver version 2.4.2
[    2.306942] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.306975] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.307010] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LNKU] -> GSI 10 (level, low) -> IRQ 10
[    2.307060] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.307143] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.307185] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0006000
[    2.440254] hub 1-0:1.0: USB hub found
[    2.440269] hub 1-0:1.0: 4 ports detected
[    2.440387] uhci_hcd: USB Universal Host Controller Interface driver
[    2.440484] usbcore: registered new interface driver libusual
[    2.440572] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.443608] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.443626] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.443835] mousedev: PS/2 mouse device common for all mice
[    2.444358] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.444395] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    2.444527] device-mapper: uevent: version 1.0.3
[    2.444658] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    2.444730] EISA: Probing bus 0 at eisa.0
[    2.444749] Cannot allocate resource for EISA slot 1
[    2.444786] Cannot allocate resource for EISA slot 8
[    2.444792] EISA: Detected 0 cards.
[    2.444813] cpufreq-nforce2: No nForce2 chipset.
[    2.444873] cpuidle: using governor ladder
[    2.444945] cpuidle: using governor menu
[    2.444951] EFI Variables Facility v0.08 2004-May-17
[    2.445325] TCP cubic registered
[    2.445576] NET: Registered protocol family 10
[    2.446470] NET: Registered protocol family 17
[    2.446484] Registering the dns_resolver key type
[    2.446529] Using IPI No-Shortcut mode
[    2.446693] PM: Hibernation image not present or could not be loaded.
[    2.446724] registered taskstats version 1
[    2.490797] isapnp: No Plug & Play device found
[    2.504493]   Magic number: 13:527:634
[    2.504776] rtc_cmos 00:02: setting system clock to 2013-01-08 13:38:21 UTC (1357652301)
[    2.504788] powernow-k8: Processor cpuid 6a0 not supported
[    2.504903] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[    2.511209] powernow: No PST tables match this cpuid (0x7a0)
[    2.511216] powernow: This is indicative of a broken BIOS.
[    2.511222] powernow: Trying ACPI perflib
[    2.511389] powernow: Minimum speed 530 MHz. Maximum speed 1855 MHz.
[    2.511489] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.511495] EDD information not available.
[    2.511813] Freeing unused kernel memory: 744k freed
[    2.513581] Write protecting the kernel text: 5828k
[    2.513626] Write protecting the kernel read-only data: 2380k
[    2.520299] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.564577] udevd[82]: starting version 175
[    2.879538] pata_ali 0000:00:10.0: can't derive routing for PCI INT A
[    2.918453] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[    2.918457]   originally by Donald Becker <becker@scyld.com>
[    2.918459]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[    2.925727] scsi0 : pata_ali
[    2.929134] scsi1 : pata_ali
[    2.929509] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8080 irq 14
[    2.929519] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8088 irq 15
[    2.929983] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    2.929998] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    2.930068] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x02, vendor 0x4243)
[    2.930075] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    2.930081] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x01, vendor 0x4243)
[    2.930086] ssb: Core 3 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    2.930091] ssb: Core 4 found: PCI (cc 0x804, rev 0x07, vendor 0x4243)
[    2.930097] ssb: Core 5 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    2.933541] ssb: Sonics Silicon Backplane found on PCI device 0000:00:09.0
[    2.933716] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    2.933726] natsemi 0000:00:12.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    2.937131] natsemi eth0: NatSemi DP8381[56] at 0xd000a000 (0000:00:12.0), 00:0b:cd:7a:61:53, IRQ 11, port TP.
[    2.937458] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    2.937470] firewire_ohci 0000:00:0c.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    2.939584] FDC 0 is a post-1991 82077
[    2.992147] firewire_ohci: Added fw-ohci device 0000:00:0c.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.094135] ata1.00: ATA-8: SAMSUNG HM160HC, LQ100-10, max UDMA/100
[    3.094163] ata1.00: 312581808 sectors, multi 16: LBA48 
[    3.110005] ata1.00: configured for UDMA/100
[    3.110335] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HC  LQ10 PQ: 0 ANSI: 5
[    3.110784] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.111073] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    3.111169] sd 0:0:0:0: [sda] Write Protect is off
[    3.111178] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.111216] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.272366] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2312, 1905, max MWDMA2
[    3.272387] ata2.00: WARNING: ATAPI DMA disabled for reliability issues.  It can be enabled
[    3.272396] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    3.273450]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 sda14 > sda3 sda4
[    3.274733] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.288263] ata2.00: configured for MWDMA2
[    3.294335] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2312 1905 PQ: 0 ANSI: 5
[    3.298617] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.298628] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.298851] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.298960] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.492276] firewire_core: created device fw0: GUID 000bcd009e530407, S400
[    5.340049] EXT4-fs (sda14): mounted filesystem with ordered data mode. Opts: (null)
[   15.521069] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.633454] udevd[308]: starting version 175
[   16.173610] Adding 2144672k swap on /dev/sda4.  Priority:-1 extents:1 across:2144672k 
[   16.349508] agpgart-ati 0000:00:00.0: Ati IGP320/M chipset
[   16.349887] reserve_ram_pages_type failed 0x2c98c000-0x2c98d000, track 0x10, req 0x10
[   16.350390] reserve_ram_pages_type failed 0x2c9cc000-0x2c9cd000, track 0x10, req 0x10
[   16.350890] reserve_ram_pages_type failed 0x2c9cd000-0x2c9ce000, track 0x10, req 0x10
[   16.351389] reserve_ram_pages_type failed 0x2c9ce000-0x2c9cf000, track 0x10, req 0x10
[   16.351888] reserve_ram_pages_type failed 0x2c9cf000-0x2c9d0000, track 0x10, req 0x10
[   16.376676] lp: driver loaded but no devices found
[   16.384814] Disabling lock debugging due to kernel taint
[   16.404916] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   16.412898] reserve_ram_pages_type failed 0x2c9be000-0x2c9bf000, track 0x10, req 0x10
[   16.413392] reserve_ram_pages_type failed 0x2c9bd000-0x2c9be000, track 0x10, req 0x10
[   16.413876] reserve_ram_pages_type failed 0x2c9bb000-0x2c9bc000, track 0x10, req 0x10
[   16.414377] reserve_ram_pages_type failed 0x2c9ba000-0x2c9bb000, track 0x10, req 0x10
[   16.414878] reserve_ram_pages_type failed 0x2c9b9000-0x2c9ba000, track 0x10, req 0x10
[   16.415378] reserve_ram_pages_type failed 0x2c9b8000-0x2c9b9000, track 0x10, req 0x10
[   16.415880] reserve_ram_pages_type failed 0x2c983000-0x2c984000, track 0x10, req 0x10
[   16.465183] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input4
[   16.465344] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   16.542220] reserve_ram_pages_type failed 0x3373a000-0x3373b000, track 0x10, req 0x10
[   16.557095] reserve_ram_pages_type failed 0x2ca56000-0x2ca57000, track 0x10, req 0x10
[   16.557600] reserve_ram_pages_type failed 0x2ca5c000-0x2ca5d000, track 0x10, req 0x10
[   16.558104] reserve_ram_pages_type failed 0x2ca5d000-0x2ca5e000, track 0x10, req 0x10
[   16.558608] reserve_ram_pages_type failed 0x2ca6a000-0x2ca6b000, track 0x10, req 0x10
[   16.635304] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[   16.741102] EXT4-fs (sda14): re-mounted. Opts: errors=remount-ro
[   16.758382] usbcore: registered new interface driver ndiswrapper
[   16.762479] yenta_cardbus 0000:00:0a.0: CardBus bridge found [103c:0024]
[   16.762505] yenta_cardbus 0000:00:0a.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   16.762579] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.826533] parport_pc 00:09: reported by Plug and Play ACPI
[   16.826625] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.849217] cfg80211: Calling CRDA to update world regulatory domain
[   16.888917] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0038, PCI irq 11
[   16.888925] yenta_cardbus 0000:00:0a.0: Socket status: 30000007
[   16.924447] lp0: using parport0 (interrupt-driven).
[   17.051372] [drm] Initialized drm 1.1.0 20060810
[   17.255567] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[   17.276138] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   17.276256] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   17.304187] b43legacy-phy0 debug: Radio initialized
[   17.304669] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.304674] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304678] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.304683] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304686] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.304690] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304693] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.304697] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304700] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.304704] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304707] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.304711] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304714] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.304718] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304721] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.304726] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304729] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.304733] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304736] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.304740] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304743] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.304747] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   17.304750] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   17.304754] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   17.304757] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   17.304761] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   17.304765] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   17.304768] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   17.369708] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   17.371068] Broadcom 43xx-legacy driver loaded [ Features: PLID ]
[   17.622719] [drm] radeon defaulting to kernel modesetting.
[   17.622727] [drm] radeon kernel modesetting enabled.
[   17.622900] radeon 0000:01:05.0: power state changed by ACPI to D0
[   17.622906] radeon 0000:01:05.0: power state changed by ACPI to D0
[   17.622926] radeon 0000:01:05.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   17.643074] [drm] initializing kernel modesetting (RS100 0x1002:0x4336 0x103C:0x0024).
[   17.643138] [drm] register mmio base: 0xD0100000
[   17.643141] [drm] register mmio size: 65536
[   17.643542] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   17.643566] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   17.643613] radeon 0000:01:05.0: putting AGP V2 device into 4x mode
[   17.643619] radeon 0000:01:05.0: GTT: 64M 0xD4000000 - 0xD7FFFFFF
[   17.643630] radeon 0000:01:05.0: VRAM: 64M 0x000000003C000000 - 0x000000003FFFFFFF (64M used)
[   17.643661] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.643664] [drm] Driver supports precise vblank timestamp query.
[   17.643694] [drm] radeon: irq initialized.
[   17.651383] [drm] Detected VRAM RAM=64M, BAR=256M
[   17.651391] [drm] RAM width 64bits DDR
[   17.656345] [TTM] Zone  kernel: Available graphics memory: 445468 kiB.
[   17.656352] [TTM] Zone highmem: Available graphics memory: 479744 kiB.
[   17.656356] [TTM] Initializing pool allocator.
[   17.656420] [drm] radeon: 64M of VRAM memory ready
[   17.656424] [drm] radeon: 64M of GTT memory ready.
[   17.699530] radeon 0000:01:05.0: WB disabled
[   17.716162] [drm] Loading R100 Microcode
[   17.827159] psmouse serio1: synaptics: Touchpad model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008/0x0
[   17.866091] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   18.080997] EXT4-fs (sda8): warning: maximal mount count reached, running e2fsck is recommended
[   18.144414] type=1400 audit(1357681117.139:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=574 comm="apparmor_parser"
[   18.145123] type=1400 audit(1357681117.139:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=574 comm="apparmor_parser"
[   18.145522] type=1400 audit(1357681117.139:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=574 comm="apparmor_parser"
[   18.147198] type=1400 audit(1357681117.139:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=564 comm="apparmor_parser"
[   18.147916] type=1400 audit(1357681117.139:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=564 comm="apparmor_parser"
[   18.148399] type=1400 audit(1357681117.143:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=564 comm="apparmor_parser"
[   18.154946] type=1400 audit(1357681117.147:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=618 comm="apparmor_parser"
[   18.173325] type=1400 audit(1357681117.167:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=618 comm="apparmor_parser"
[   18.173719] type=1400 audit(1357681117.167:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=618 comm="apparmor_parser"
[   18.215701] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   18.218001] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   18.218860] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   18.219654] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   18.220569] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   18.220607] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   18.220643] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   18.220679] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.233029] ppdev: user-space parallel port driver
[   18.344893] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.344904] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344908] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.344912] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344916] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.344920] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344923] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.344927] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344930] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.344934] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344937] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.344941] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344944] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.344948] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344951] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.344955] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344958] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.344962] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344965] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.344969] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344973] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.344976] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.344980] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   18.344984] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.344987] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.344991] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.344994] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   18.344998] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.345004] cfg80211: World regulatory domain updated:
[   18.345007] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.345011] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.345014] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.345018] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.345022] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.345025] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.390366] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: acl,user_xattr
[   18.461214] [drm] radeon: ring at 0x00000000D4001000
[   18.461243] [drm] ring test succeeded in 1 usecs
[   18.461693] [drm] radeon: ib pool ready.
[   18.461821] [drm] ib test succeeded in 0 usecs
[   18.470573] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   18.470583] PCI: setting IRQ 5 as level-triggered
[   18.470592] snd_ali5451 0000:00:06.0: PCI INT A -> Link[LNKH] -> GSI 5 (level, low) -> IRQ 5
[   18.554347] [drm] Panel ID String: LGP                     
[   18.554356] [drm] Panel Size 1024x768
[   18.578488] [drm] radeon legacy LVDS backlight initialized
[   18.688188] [drm] Radeon Display Connectors
[   18.688198] [drm] Connector 0:
[   18.688201] [drm]   VGA
[   18.688206] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   18.688209] [drm]   Encoders:
[   18.688211] [drm]     CRT1: INTERNAL_DAC1
[   18.688214] [drm] Connector 1:
[   18.688216] [drm]   LVDS
[   18.688219] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   18.688222] [drm]   Encoders:
[   18.688224] [drm]     LCD1: INTERNAL_LVDS
[   18.688226] [drm] Connector 2:
[   18.688228] [drm]   S-video
[   18.688230] [drm]   Encoders:
[   18.688232] [drm]     TV1: INTERNAL_DAC2
[   18.882700] [drm] fb mappable at 0xE0040000
[   18.882708] [drm] vram apper at 0xE0000000
[   18.882710] [drm] size 3145728
[   18.882712] [drm] fb depth is 24
[   18.882714] [drm]    pitch is 4096
[   18.883205] fbcon: radeondrmfb (fb0) is primary device
[   18.945469] Console: switching to colour frame buffer device 128x48
[   18.959019] fb0: radeondrmfb frame buffer device
[   18.959023] drm: registered panic notifier
[   18.959046] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[   21.318796] type=1400 audit(1357681120.310:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=801 comm="apparmor_parser"
[   21.640165] AC'97 1 does not respond - RESET
[   21.656048] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   21.656251] ali mixer 1 creating error.
[   22.202943] Bluetooth: Core ver 2.16
[   22.203035] NET: Registered protocol family 31
[   22.203039] Bluetooth: HCI device and connection manager initialized
[   22.203046] Bluetooth: HCI socket layer initialized
[   22.203049] Bluetooth: L2CAP socket layer initialized
[   22.207698] Bluetooth: SCO socket layer initialized
[   22.258789] Bluetooth: RFCOMM TTY layer initialized
[   22.258820] Bluetooth: RFCOMM socket layer initialized
[   22.258823] Bluetooth: RFCOMM ver 1.11
[   22.552674] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.552685] Bluetooth: BNEP filters: protocol multicast
[   22.599906] b43-pci-bridge 0000:00:09.0: PCI INT A disabled
[   22.688684] usbcore: deregistering interface driver ndiswrapper
[   22.779077] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   22.962802] ndiswrapper: driver bcmwl5a (Broadcom,11/27/2004, 3.100.35.0) loaded
[   22.962964] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   22.982186] ndiswrapper: using IRQ 10
[   23.255692] audit_printk_skb: 48 callbacks suppressed
[   23.255700] type=1400 audit(1357681122.246:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=941 comm="apparmor_parser"
[   23.281798] type=1400 audit(1357681122.274:29): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=941 comm="apparmor_parser"
[   23.485190] wlan0: ethernet device 00:90:4b:44:7f:66 using NDIS driver: bcmwl5a, version: 0x3642300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[   23.485250] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   23.485348] usbcore: registered new interface driver ndiswrapper
[   24.039351] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.042680] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.071299] eth0: DSPCFG accepted after 0 usec.
[   24.075505] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.083829] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.666727] init: plymouth-stop pre-start process (1113) terminated with status 1
[   34.847775] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
ralph@Presario:~$
```

Attachment 1 (IMG_0540.jpg) is a photo of the messages on my screen, when the system hung and would not power down.  Note the message "Power Down", but it didn't power down.  Somehow the wrong command must have been given for power down and it didn't happen.  Under Ubuntu 10.04 the power down worked.

Attachment 2 (IMG_0541.jpg) is a photo of the messages on my screen, when the system hung after a "restart".  Note the "Restarting System" message.  Again it looks like everything worked until the command was given for a restart, which didn't work.

Any ideas about how to fix this would be very much appreciated.  This is over my head to figure out.

Thanks in advance.
Ralph

---

### Post by Ralph L on 2013-01-13
I finally figured out that I should use attachments show photos of the shutdown failure messages I get.  See the post immediately above this one.

Stumbling around on this issue I found and ran ```
sudo dmidecode
```, which is supposed to list the bios capabilities.  It runs fine on my Dell Latitude D610 (on which shutdown, restart, suspend and hibernate all work), but gets an error on my Presario 2100 (both are running Ubuntu 12.04.1).  ```
ralph@Presario:~$ sudo dmidecode
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine.h: 633: elf_machine_rel_relative: Assertion `((reloc->r_info) & 0xff) == 8' failed!

```This hints that something is wrong with the interface to the bios on the Presario, which could account for the shutdown problems.  I don't know enough to decode this error message.  Can anybody help me, and tell me what would be a solution to getting "dmidecode" running, so that I can tell what features my bios supports.

I also found that if I booted the Presario with the option "acpi=off" that "restart" works (but not a simple "shutdown").  The machine powers off and then back on like it should.  The acpi (Advanced Contller and Power Interface) is part of the bios and provides the OS with an interface to the hardware (or at least that is what I think it does).  However, from what I read one should not run with "acpi=off", because on many computers it controls the cooling.  It also controls the Presario's ability to adjust the clock, and results in the Presario running wide open at max clock all the time.  Anyway I now have two indications that 12.04.1 is not interfacing correctly to the Presario bios.

Any help on how Desktop Management Interface (DMI)/System Management Bios (SMBIOS) and Advance Controller and Power Interface (ACPI) work would be greatly appreciated.

Thanks
Ralph

---

### Post by Ralph L on 2013-01-14
Fixed the problem with dmidecode not running so here is what dmidecode listed as the machine/bios capabilities:  ```
# dmidecode 2.11
SMBIOS 2.3 present.
44 structures occupying 1332 bytes.
Table at 0x000DB010.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Phoenix Technologies Ltd.
	Version: KAM1.48  
	Release Date: 08/22/2003
	Address: 0xE4F60
	Runtime Size: 110752 bytes
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		Boot from PC Card (PCMCIA) is supported
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
	Manufacturer: Hewlett-Packard          
	Product Name: Presario 2100 (DM728A)   
	Version: KAM1.48  
	Serial Number: CNF339116N     
	UUID: A057A122-7AD7-D711-801A-000BCD7A6153
	Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Hewlett-Packard          
	Product Name: 0024                     
	Version: PQ1A78
	Serial Number: None

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Hewlett-Packard          
	Type: Notebook
	Lock: Not Present
	Version: N/A
	Serial Number: None
	Asset Tag: No Asset Tag
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 32 bytes
Processor Information
	Socket Designation: mPGA462B
	Type: Central Processor
	Family: Athlon
	Manufacturer: AuthenticAMD
	ID: A0 06 00 00 FF F9 83 03
	Signature: Family 6, Model 10, Stepping 0
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		MMX (MMX technology supported)
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
	Version: AMD Athlon  
	Voltage: 1.5 V
	External Clock: 133 MHz
	Max Speed: 1862 MHz
	Current Speed: 1862 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: Not Provided
	L2 Cache Handle: 0x0008
	L3 Cache Handle: Not Provided

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		Other
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 16 MB
	Maximum Total Memory Size: 32 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		FPM
		EDO
		DIMM
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 2
		0x0000
		0x0001
	Enabled Error Correcting Capabilities:
		None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM 1
	Bank Connections: 0 1
	Current Speed: 60 ns
	Type: DIMM SDRAM
	Installed Size: 512 MB (Single-bank Connection)
	Enabled Size: 512 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM 2
	Bank Connections: 2 3
	Current Speed: 60 ns
	Type: DIMM SDRAM
	Installed Size: 512 MB (Single-bank Connection)
	Enabled Size: 512 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 512 kB
	Maximum Size: 1024 kB
	Supported SRAM Types:
		Burst
		Pipeline Burst
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: 2-way Set-associative

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Primary IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Secondary IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FLOPPY
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: COM1
	External Connector Type: DB-9 male
	Port Type: Serial Port XT/AT Compatible

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: FIR
	External Connector Type: Infrared
	Port Type: Other

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: Printer
	External Connector Type: DB-25 female
	Port Type: Parallel Port ECP/EPP

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: KBD
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CD_IN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: MIC_IN
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: LINE_IN
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: LINE_OUT
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Other
	Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Other
	Port Type: USB

Handle 0x0017, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Slot 1
	Type: 32-bit PCI
	Current Usage: Unknown
	Length: Long
	ID: 0
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0018, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Disabled
	Description: ALi 1535 Sound

Handle 0x0019, DMI type 11, 5 bytes
OEM Strings
	String 1: Hewlett-Packard NoteBook Series
	String 2: Service ID: 14001
	String 3: $MODEL: DM728
	String 4: $OS:   
	String 5: $LOCAL: ABA
	String 6: $OPTION:    
	String 7: $DC:  

Handle 0x001A, DMI type 15, 29 bytes
System Event Log
	Area Length: 32 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x0000
	Status: Valid, Not Full
	Change Token: 0x00000050
	Header Format: Type 1
	Supported Log Type Descriptors: 3
	Descriptor 1: POST error
	Data Format 1: POST results bitmap
	Descriptor 2: Single-bit ECC memory error
	Data Format 2: Multiple-event
	Descriptor 3: Multi-bit ECC memory error
	Data Format 3: Multiple-event

Handle 0x001B, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 1 GB
	Error Information Handle: Not Provided
	Number Of Devices: 3

Handle 0x001C, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x001B
	Error Information Handle: No Error
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: 1
	Locator: M1
	Bank Locator: Bank 0
	Type: DRAM
	Type Detail: Synchronous
	Speed: Unknown

Handle 0x001D, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x001B
	Error Information Handle: No Error
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: 1
	Locator: M2
	Bank Locator: Bank 1
	Type: DRAM
	Type Detail: Synchronous
	Speed: Unknown

Handle 0x001E, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x001B
	Error Information Handle: No Error
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: 1
	Locator: M3
	Bank Locator: Bank 2
	Type: DRAM
	Type Detail: Synchronous
	Speed: Unknown

Handle 0x001F, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Array Handle: 0x001B
	Partition Width: 2

Handle 0x0020, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x001C
	Memory Array Mapped Address Handle: 0x001F
	Partition Row Position: 1

Handle 0x0021, DMI type 23, 13 bytes
System Reset
	Status: Enabled
	Watchdog Timer: Present
	Boot Option: Do Not Reboot
	Boot Option On Limit: Do Not Reboot
	Reset Count: Unknown
	Reset Limit: Unknown
	Timer Interval: Unknown
	Timeout: Unknown

Handle 0x0022, DMI type 24, 5 bytes
Hardware Security
	Power-On Password Status: Disabled
	Keyboard Password Status: Unknown
	Administrator Password Status: Enabled
	Front Panel Reset Status: Unknown

Handle 0x0023, DMI type 25, 9 bytes
	System Power Controls
	Next Scheduled Power-on: 12-31 23:59:59

Handle 0x0024, DMI type 26, 20 bytes
Voltage Probe
	Description: Voltage Probe
	Location: Processor
	Status: OK
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000

Handle 0x0025, DMI type 27, 12 bytes
Cooling Device
	Temperature Probe Handle: 0x0026
	Type: Fan
	Status: OK
	OEM-specific Information: 0x00000000

Handle 0x0026, DMI type 28, 20 bytes
Temperature Probe
	Description: Temperature Probe
	Location: Processor
	Status: OK
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000

Handle 0x0027, DMI type 29, 20 bytes
Electrical Current Probe
	Description: Electrical Current Probe
	Location: Processor
	Status: OK
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000

Handle 0x0028, DMI type 30, 6 bytes
Out-of-band Remote Access
	Manufacturer Name: Intel
	Inbound Connection: Enabled
	Outbound Connection: Disabled

Handle 0x0029, DMI type 32, 20 bytes
System Boot Information
	Status: <OUT OF SPEC>

Handle 0x002A, DMI type 140, 36 bytes
OEM-specific Type
	Header and Data:
		8C 24 2A 00 00 00 00 00 00 60 01 7D 00 7C 01 7D
		00 00 00 01 FF FF FF FF FF FF FF FF 00 00 00 00
		00 00 00 00

Handle 0x002B, DMI type 127, 4 bytes
End Of Table

```
Any help appreciated!!!

---

### Post by Jack27 on 2013-03-01
I'm new to this forum so I don't know if this should be a new question or a response to this thread.
I, too have a Pressario 2100 with the same type of problem (with 12.04).  I've tried the terminal shut down solutions to no avail.  I've also tried the suggested changes to the grub files to no avail.  The BIOS stuff is beyond my capabilities for now.  I was wondering though: with the splash screen turned off the last two lines before the hang up reads:

"* will now halt
[a bunch of numbers that change each time] Power down."

If the machine is ready to power down, but can't do the last step, why can't I treat this last line like the old Windows line - "It is now safe to turn off your computer"? And manually shut down without harming the system?

---

### Post by MAFoElffen on 2013-03-02
On both users...

I've helped other users with this problem. It has to do with how the OS asks for a power down, the interrupts and registers... Usually a BIOS or keyboard controller "variation."  

Try using a Linux kernel boot parameter of "reboot=xxxx", where vaild options for "xxxx" are shown in this list:
```

[COLOR=#000000][FONT=Trebuchet MS]warm =  Don&#8217;t set the cold reboot flag[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]cold = Set the cold reboot flag[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]bios = Reboot by jumping through the BIOS (only for X86_32)[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]smp = Reboot by executing reset on BSP or other CPU (only for X86_32)[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]triple = Force a triple fault (init)[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]kbd = Use the keyboard controller. cold reset (default)[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]acpi = Use the RESET_REG in the FADT[COLOR=#0000FF]
[/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Trebuchet MS]efi = Use efi reset_system runtime service[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]pci = Use the so-called &#8220;PCI reset register&#8221;, CF9[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]force = Avoid anything that could hang.[/FONT][/COLOR]

``` 
For example you could use "reboot=acpi" or "reboot=bios", etc. 

Also valid is giving it multiple options is using the first letter of the option and/or using a list of options to try in order such as- "reboot=a,b,k,c"" would be try reboot via acpi, bios, keyboard, cold.

Of course in the meantime, what someone posted here in an earlier post is old and outdated for shutdown commands. Current now would be 
```

sudo shutdown -r now    # for reboot
sudo shutdown -P now    # for shutdown

```
The previous post had a shutdown flag asking for a halt. Sometime after 10.04, if the newer version kernel saw that, it decided the state it went to, which sometimes halt ended in a hung state.

Of course, if that does not work, there are 3 other ways to force a shutdown or reboot- You could go ask for an "init" state change to ask for a shutdown or reboot...  echoing the command characters directly to the /proc registers... or manually issuing systematic commands to shutdown the system in a logical order.

---

### Post by Jack27 on 2013-03-07
I know this doesn't fix the problem Ubuntu 12.04 not shutting down on a Presario 2100, but I just installed Xubuntu 12.04 on my machine, and the shut down and reboot glitches went away.

---

### Post by Ralph L on 2013-03-08
MAFoElffen, Jack27

Thank you both for your replies.  I have been busy with other things recently and have been unable to get back to working on the Presario.  However, I will to that soon, and I will try both your suggestions.  

Ralph

---

### Post by Ralph L on 2013-03-22
Jack27

I can't thank you enough for telling me that xubuntu 12.04.2 will run on the compaq presario 2100.  I installed it and it seems to have fixed the suspend, hibernate, shutdown, and reboot problems (for hibernate see [http://ubuntuforums.org/showthread.php?t=2002578](http://ubuntuforums.org/showthread.php?t=2002578)).  Xubuntu is a little different from ubuntu, but I have managed to install some ubuntu stuff on it (nautilus, gnome-search-tool).  I also got the Clearlooks-Phenix theme to run (restoring the stepper arrows on the slide), although the lancher icons it placed on my top panel are awfully small.  I also have wifi running on it [http://ubuntuforums.org/showthread.php?t=2095736](http://ubuntuforums.org/showthread.php?t=2095736) .  Note that suspend and hibernate are slow shutting down.  It may take 3 or 4 minutes.  I think what may be happening is that the system wants to cool down the cpu before shutting off.  But that's just a guess.

I would like to know why ubuntu 12.04.2 and 12.10 won't run correctly.  The only difference that I know of between xubuntu and ubuntu is that ubuntu uses a "pae" operating system and xubuntu uses a "non-pae" OS.  I haven't had time to try any of MAFoElffen's suggestions.  I will try to do that, because he has suggested boot time stuff I did not know about, and I anticipate more boot problems in the future on my old computers.

And again, Thank You.
Ralph
PS.  If you have any problems with your presario 2100 that I might have solved, please send me a private message (I don't monitor all the forum traffic).  Us users of old computers need to stick to together.

---

