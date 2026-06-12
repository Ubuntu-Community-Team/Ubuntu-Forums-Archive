---
title: "Only one CPU detected on dual Xeon machine"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by jarthurs on 2007-09-16
I've just installed Ubuntu Server 7.04 on a Compaq Proliant 5500 (Xeon not Pentium Pro) machine. This has been working fine under SME Server but having installed Ubuntu server it doesn't appear to be detecting two CPUs despite having loaded an SMP kernel.

Both 'top' and cat /proc/cpuinfo only gives details for processor 0.

On boot it reports:

Linux teishu 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686

This is quite an elderly box, but having sucessfully installed it on a Proliant 2500 dual Pentium Pro 200MHz I'm a bit miffed my (soon to be) quad Xeon 550MHz machine looks decidedly single processor to Ubuntu...

Any suggestions?

Regards,
Jason.

---

### Post by jnorth on 2007-09-18
See my comment in your other post about the same issue.

HTH

---

### Post by digitalbenji on 2007-09-18
can you go into the /proc directory and print the output of:
cat /proc/cpuinfo

also do an ls in this directory to see if there is something that says anything about number of CPUs.  

thanks

---

### Post by jarthurs on 2007-09-19
As requested here is a copy of my dmesg 

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fefc000 end: 000000007fffc000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fffc000 size: 0000000000004000 end: 0000000080000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fffc000 (usable)
[    0.000000]  BIOS-e820: 000000007fffc000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 524284) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524284
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524284
[    0.000000] On node 0 totalpages: 524284
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved

[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292605 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000f4f70
[    0.000000]   >>> ERROR: Invalid checksum
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Detected 549.901 MHz processor.
[   89.343458] Built 1 zonelists.  Total pages: 520189
[   89.343472] Kernel command line: root=UUID=e53d4e29-bd41-4b75-98d3-6815d9378bd1 ro quiet splash
[   89.344194] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   89.344224] mapped APIC to ffffd000 (02012000)
[   89.344238] Enabling fast FPU save and restore... done.
[   89.344249] Enabling unmasked SIMD FPU exception support... done.
[   89.344281] Initializing CPU#0
[   89.344440] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   89.346598] Console: colour VGA+ 80x25
[   89.348431] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   89.350350] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   89.723043] Memory: 2068392k/2097136k available (1993k kernel code, 27536k reserved, 900k data, 328k init, 1179632k highmem)
[   89.723088] virtual kernel memory layout:
[   89.723093]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   89.723098]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   89.723104]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   89.723109]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   89.723115]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   89.723120]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)nabled, disablin[   89.723125]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   89.723139] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   89.800392] Calibrating delay using timer specific routine.. 1100.92 BogoMIPS (lpj=2201841)
[   89.800571] Security Framework v1.0.0 initialized
[   89.800616] SELinux:  Disabled at boot.
[   89.800686] Mount-cache hash table entries: 512
[   89.801280] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   89.801324] CPU: L1 I cache: 16K, L1 D cache: 16K
[   89.801334] CPU: L2 cache: 2048K
[   89.801348] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   89.801391] Compat vDSO mapped to ffffe000.
[   89.801420] Remapping vsyscall page to ffffe000
[   89.801459] Checking 'hlt' instruction... OK.
[   89.816722] SMP alternatives: switching to UP code
[   89.817351] Freeing SMP alternatives: 11k freed
[   89.818010] Early unpacking initramfs... done
[   90.853702] CPU0: Intel Pentium III (Katmai) stepping 03
[   90.853725] SMP motherboard not detected.
[   90.853734] Local APIC not detected. Using dummy APIC emulation.
[   90.853889] Brought up 1 CPUs
[   90.854801] Booting paravirtualized kernel on bare hardware
[   90.855002] Time: 12:02:08  Date: 08/19/107

Bearing in mind this all worked perfectly (i.e. multiple processors) under SME Server 6.01 which is built on RedHat 7.2!!

Help! My server is only firing on one cylinder!

Regards,
Jason.

---

### Post by jarthurs on 2007-09-19
I finally nailed this one!

On Compaq Proliant servers it's necessary to warn the server what OS you intend to install. This option had already been set to 'Linux' using the System Configuration Utility, I decided to try setting it to 'Other' but rebooting the server revealed the same single CPU as before.

I went into the System Configuration Utility again and set it back to Linux, whilst it was running I remembered that the only difference between the old working RedHat 7.2 setup and the new non-working Ubuntu 7.10 install was a second NIC I had added. So whilst in the configuration screen I changed the IRQs on both NICs just to see what would happen.

When I rebooted and ran cat /proc/cpuinfo the information scrolled off up the screen as usual but this time I noticed that the processor number was '2' instead of '0'. Sure enough top reports all three cpus!!!

So I'm not clear if this was some sort of resource conflict with the second NIC or if the OS flag on the Proliant mainboard wasn't set correctly (despite giving the correct 'Linux' setting in the SCU).

Hope this sheds some light on the problem for other Compaq Proliant users.

Thanks,
Jason.

---

### Post by kjpires on 2008-04-05
Thanks for posting the resolution; I had the same problem and your post saved my week!

Kurt

---

