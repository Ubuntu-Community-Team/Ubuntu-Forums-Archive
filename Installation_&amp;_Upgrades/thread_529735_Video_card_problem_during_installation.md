---
title: "Video card problem during installation"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by rstafford2k7 on 2007-08-19
I am having a problem installing 7.04 on an HP Pavilion dv6140us laptop with the Nvidia GeForce Go 6150 video card. The install appears to have been successful but when I boot the computer, the screen goes blank after the splash screen completes loading.

I believe the video card is not being recognized since I was able to make the CD based version work in 1280x800 resolution with no problem. Even though initially, the screen also went blank using the default resolution.

I would like to know how to accomplish the following:

[LIST=1]
[*]Change the resolution on the installed operating system.
[*]Install the correct drivers, which I have.
[*]Just get it to work!
[/LIST]

I appreciate any assistance anyone can offer.

Thanks

Richard

---

### Post by Pumalite on 2007-08-19
Boot in 'Safe Graphics Mode'. At the command line: sudo dpkg-reconfigure xserver-xorg. Accept defaults, choose 'vesa as your driver, then: 'startx'.
If all you have is a blank screen you can get a command line with Ctrl+Alt+F1 or Alt+F1 or F2
You can install your drivers once you are in the system. On the other hand, if you have your driver tucked away somewhere use sh blah blah blah, after stopping gdm.

---

### Post by rstafford2k7 on 2007-08-19
By boot options are as follows:

Unbuntu, kernel 2.6.20-15-generic
Unbuntu, kernel 2.6.20-15-generic (recovery mode)
Unbuntu, memtest86+

As you can tell, I'm new at this, how do I get to the "safe graphics mode"?

Thanks

---

### Post by Pumalite on 2007-08-19
Let it go to a blank screen and use my suggestions above. If no go, then>Alternate CD ( text mode; avoids graphical interface and other hardware problems )

---

### Post by merlinus on 2007-08-19
Try Recovery Mode, which should get you to a CLI.  Then follow Pumalite's suggestions.

-merlin

---

### Post by rstafford2k7 on 2007-08-19
I tried booting to recovery mode and the system stops at the following line:

[    0.000096] CPU#1 had 107 usecs TSC skew, fixed it up.

Also, what is CLI?

Thanks,

Richard

---

### Post by Pumalite on 2007-08-19
Command Line Interface

---

### Post by svk on 2007-08-24
Hello,

I'm having the same exact problem.  When I try to boot into recovery mode, the system hangs after these lines:

[13.317739] Total of 2 processors activated (7236.19 BogoMIPS).
[13.318090] ENABLING IO-APIC IRQs
[13.318383] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[13.465065] checking TSC synchronization across 2 CPUs:
[0.000045] CPU#0 had -97 usecs TSC skew, fixed it up.
[0.000097] CPU#1 had 97 usecs TSC skew, fixed it up.

I'm running on the HP dv6449us (dual-booting with Vista).  The laptop has the AMD Turion-64 X2 TL-56 Processor. Note that I tried and failed to install the 64-bit version of Ubuntu, so I gave that up and installed the 32-bit version instead.

It seems that the HP dv6000 models are a bit problematic with Linux. Here' s a page that covers several issues:

[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)")

I'll be actively looking for a solution to this problem, and I'll let you know if I find one. If anyone knows something we can do, please help!

---

### Post by svk on 2007-08-24
Wow, I should have known. The very page I linked to contains (at least a temporary) solution.

Before booting, hit 'e' to edit the command line options. Scroll down to the longest line (which begins with "kernel"), and edit it (I forget using which key). Add the following right after all the other options on that line:

NOAPIC NOAPCI NOLAPIC NOIRQPOLL NOSMP

Hit enter, and then hit 'b' to boot with these options. For me, it worked immediately, and I'm currently writing this using my newly installed Ubuntu system :)

I need two things for complete happiness:

1) Right after booting in, I saved my boot log into a file. Unfortunately, I am no expert at interpreting it. Can someone please look at it to confirm that nothing is seriously messed up? I attached it at the end of this post.

2) Is this really a good solution? As I understand it, I just disabled several services which are responsible for handling power issues! And this being a laptop makes me wonder if this is really a permanent solution. Can someone advise?

And here's the boot log (which I saved into a file called "dmesg.txt" using the command **dmesg > ~/dmesg.txt**):

```

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009dc00 end: 000000000009dc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009dc00 size: 0000000000002400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d2000 size: 000000000002e000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007be00000 end: 000000007bf00000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007bf00000 size: 0000000000016000 end: 000000007bf16000 type: 3
[    0.000000] copy_e820_map() start: 000000007bf16000 size: 000000000006a000 end: 000000007bf80000 type: 4
[    0.000000] copy_e820_map() start: 000000007bf80000 size: 0000000004080000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf00000 (usable)
[    0.000000]  BIOS-e820: 000000007bf00000 - 000000007bf16000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bf16000 - 000000007bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1087MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8910
[    0.000000] Entering add_active_range(0, 0, 507648) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   507648
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   507648
[    0.000000] On node 0 totalpages: 507648
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2174 pages used for memmap
[    0.000000]   HighMem zone: 276098 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x000f88e0
[    0.000000] ACPI: RSDT (v001 HPQOEM SLIC-MPC 0x06040000  LTP 0x00000000) @ 0x7bf0cb68
[    0.000000] ACPI: FADT (v001 HP     MCP51M   0x06040000 PTL_ 0x000f4240) @ 0x7bf15b58
[    0.000000] ACPI: SSDT (v001 HP     POWERNOW 0x06040000  LTP 0x00000001) @ 0x7bf15bcc
[    0.000000] ACPI: MCFG (v001 HP       MCFG   0x06040000  LTP 0x00000000) @ 0x7bf15d90
[    0.000000] ACPI: HPET (v001 PTLTD  HPETTBL  0x06040000  LTP 0x00000001) @ 0x7bf15dcc
[    0.000000] ACPI: MADT (v001 HP       APIC   0x06040000  LTP 0x00000000) @ 0x7bf15e04
[    0.000000] ACPI: BOOT (v001     HP $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x7bf15e62
[    0.000000] ACPI: SLIC (v001 HPQOEM SLIC-MPC 0x06040000  LTP 0x00000001) @ 0x7bf15e8a
[    0.000000] ACPI: DSDT (v001 HP       MCP51M 0x06040000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: nVIDIA   Product ID: C51-MCP51    APIC at: 0xFEE00000
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Detected 1808.294 MHz processor.
[   57.748069] Built 1 zonelists.  Total pages: 503682
[   57.748073] Kernel command line: root=UUID=5489ef00-6eb2-403d-a100-ae29ab204275 ro noapic noapci nolapic noirqpoll nosmp
[   57.748226] mapped APIC to ffffd000 (fee00000)
[   57.748229] mapped IOAPIC to ffffc000 (fec00000)
[   57.748232] Enabling fast FPU save and restore... done.
[   57.748234] Enabling unmasked SIMD FPU exception support... done.
[   57.748241] Initializing CPU#0
[   57.748307] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   57.748339] spurious 8259A interrupt: IRQ7.
[   57.751465] Console: colour VGA+ 80x25
[   57.754573] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   57.755035] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   57.819578] Memory: 2002060k/2030592k available (1992k kernel code, 27184k reserved, 893k data, 328k init, 1113088k highmem)
[   57.819654] virtual kernel memory layout:
[   57.819655]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   57.819657]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   57.819658]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   57.819659]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   57.819661]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   57.819662]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   57.819663]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   57.820064] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   57.820320] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   57.820515] hpet0: 3 32-bit timers, 25000000 Hz
[   57.821572] Using HPET for base-timer
[   57.900279] Calibrating delay using timer specific routine.. 3619.62 BogoMIPS (lpj=7239257)
[   57.900416] Security Framework v1.0.0 initialized
[   57.900471] SELinux:  Disabled at boot.
[   57.900533] Mount-cache hash table entries: 512
[   57.900703] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[   57.900712] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   57.900766] CPU: L2 Cache: 512K (64 bytes/line)
[   57.900819] CPU 0(2) -> Core 0
[   57.900868] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[   57.900878] Compat vDSO mapped to ffffe000.
[   57.900930] Remapping vsyscall page to ffffe000
[   57.900988] Checking 'hlt' instruction... OK.
[   57.916441] SMP alternatives: switching to UP code
[   57.916854] Early unpacking initramfs... done
[   58.224229] ACPI: Core revision 20060707
[   58.227146] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   58.229470] ACPI: setting ELCR to 0200 (from 0ca0)
[   58.437278] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   58.437404] SMP mode deactivated, forcing use of dummy APIC emulation.
[   58.437484] Brought up 1 CPUs
[   58.437728] Booting paravirtualized kernel on bare hardware
[   58.437863] Time:  1:34:39  Date: 07/24/107
[   58.437935] NET: Registered protocol family 16
[   58.438052] EISA bus registered
[   58.438102] ACPI: bus type pci registered
[   58.453544] PCI: BIOS BUG #81[49435000] found
[   58.453594] PCI: Using configuration type 1
[   58.453643] Setting up standard PCI resources
[   58.459250] ACPI: Interpreter enabled
[   58.459301] ACPI: Using PIC for interrupt routing
[   58.460216] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   58.460269] PCI: Probing PCI hardware (bus 00)
[   58.460448] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   58.460813] Boot video device is 0000:00:05.0
[   58.461720] PCI: Transparent bridge - 0000:00:10.0
[   58.461796] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   58.498995] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   58.500097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   58.500256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   58.500609] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   58.501368] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   58.502042] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   58.502722] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   58.503474] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   58.504236] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   58.504988] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 *11 14 15)
[   58.505661] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   58.506416] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   58.507090] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   58.507766] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   58.508462] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   58.509136] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   58.509807] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   58.510559] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   58.511316] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   58.512092] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   58.512853] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   58.513526] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15), disabled.
[   58.514873] Linux Plug and Play Support v0.97 (c) Adam Belay
[   58.514931] pnp: PnP ACPI init
[   58.517876] pnp: PnP ACPI: found 13 devices
[   58.517927] PnPBIOS: Disabled by ACPI PNP
[   58.518016] PCI: Using ACPI for IRQ routing
[   58.518067] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   58.518220] NET: Registered protocol family 8
[   58.518270] NET: Registered protocol family 20
[   58.518816] pnp: 00:04: ioport range 0x1000-0x107f could not be reserved
[   58.518870] pnp: 00:04: ioport range 0x1080-0x10ff has been reserved
[   58.518922] pnp: 00:04: ioport range 0x1400-0x147f has been reserved
[   58.518975] pnp: 00:04: ioport range 0x1480-0x14ff could not be reserved
[   58.519028] pnp: 00:04: ioport range 0x1800-0x187f has been reserved
[   58.519081] pnp: 00:04: ioport range 0x1880-0x18ff has been reserved
[   58.519133] pnp: 00:04: ioport range 0x2000-0x203f has been reserved
[   58.519406] PCI: Bridge: 0000:00:02.0
[   58.519455]   IO window: 4000-4fff
[   58.519506]   MEM window: b4000000-b5ffffff
[   58.519557]   PREFETCH window: d0000000-d01fffff
[   58.519608] PCI: Bridge: 0000:00:03.0
[   58.519656]   IO window: disabled.
[   58.519706]   MEM window: b6000000-b7ffffff
[   58.519757]   PREFETCH window: d0200000-d03fffff
[   58.519809] PCI: Bridge: 0000:00:10.0
[   58.519857]   IO window: disabled.
[   58.519907]   MEM window: b8000000-b80fffff
[   58.519976]   PREFETCH window: disabled.
[   58.520036] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   58.520042] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   58.520050] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   58.520076] NET: Registered protocol family 2
[   58.551999] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   58.552192] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   58.553113] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   58.553609] TCP: Hash tables configured (established 131072 bind 65536)
[   58.553663] TCP reno registered
[   58.564056] checking if image is initramfs... it is
[   59.169857] Freeing initrd memory: 6766k freed
[   59.170050] Simple Boot Flag at 0x36 set to 0x1
[    1.144000] audit: initializing netlink socket (disabled)
[    1.144000] audit(1187919279.328:1): initialized
[    1.144000] highmem bounce pool size: 64 pages
[    1.144000] VFS: Disk quotas dquot_6.5.1
[    1.144000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.144000] io scheduler noop registered
[    1.144000] io scheduler anticipatory registered
[    1.144000] io scheduler deadline registered
[    1.144000] io scheduler cfq registered (default)
[    1.164000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.164000] assign_interrupt_mode Found MSI capability
[    1.164000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.164000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.164000] assign_interrupt_mode Found MSI capability
[    1.164000] Allocate Port Service[0000:00:03.0:pcie00]
[    1.164000] isapnp: Scanning for PnP cards...
[    1.516000] isapnp: No Plug & Play device found
[    1.536000] Real Time Clock Driver v1.12ac
[    1.540000] hpet_resources: 0xfed00000 is busy
[    1.540000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.540000] mice: PS/2 mouse device common for all mice
[    1.540000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.540000] input: Macintosh mouse button emulation as /class/input/input0
[    1.540000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.540000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.540000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.560000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.560000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.560000] EISA: Probing bus 0 at eisa.0
[    1.560000] Cannot allocate resource for EISA slot 1
[    1.560000] Cannot allocate resource for EISA slot 2
[    1.560000] Cannot allocate resource for EISA slot 3
[    1.560000] Cannot allocate resource for EISA slot 4
[    1.560000] EISA: Detected 0 cards.
[    1.592000] TCP cubic registered
[    1.592000] NET: Registered protocol family 1
[    1.592000] Using IPI No-Shortcut mode
[    1.592000] ACPI: (supports S0 S3 S4 S5)
[    1.592000]   Magic number: 3:946:559
[    1.592000]   hash matches device ptya5
[    1.592000] Freeing unused kernel memory: 328k freed
[    1.596000] Time: hpet clocksource has been installed.
[    1.600000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.784000] Capability LSM initialized
[    1.824000] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    1.828000] ACPI: Thermal Zone [THRM] (63 C)
[    2.428000] usbcore: registered new interface driver usbfs
[    2.428000] usbcore: registered new interface driver hub
[    2.428000] usbcore: registered new device driver usb
[    2.432000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.432000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[    2.432000] PCI: setting IRQ 11 as level-triggered
[    2.432000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[    2.432000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    2.432000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.432000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.432000] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
[    2.480000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[    2.500000] usb usb1: configuration #1 chosen from 1 choice
[    2.500000] hub 1-0:1.0: USB hub found
[    2.500000] hub 1-0:1.0: 8 ports detected
[    2.524000] ieee1394: Initialized config rom entry `ip1394'
[    2.604000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[    2.604000] PCI: setting IRQ 7 as level-triggered
[    2.604000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[    2.604000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    2.604000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.604000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    2.604000] ehci_hcd 0000:00:0b.1: debug port 1
[    2.604000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[    2.604000] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
[    2.604000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.604000] usb usb2: configuration #1 chosen from 1 choice
[    2.604000] hub 2-0:1.0: USB hub found
[    2.604000] hub 2-0:1.0: 8 ports detected
[    2.708000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    2.708000] NFORCE-MCP51: chipset revision 241
[    2.708000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    2.708000] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[    2.708000] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[    2.708000]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[    2.708000] Probing IDE interface ide0...
[    2.720000] SCSI subsystem initialized
[    2.724000] libata version 2.20 loaded.
[    3.004000] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    3.144000] usb 2-4: configuration #1 chosen from 1 choice
[    3.444000] hda: TSSTcorpCD/DVDW TS-L632M, ATAPI CD/DVD-ROM drive
[    4.116000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.140000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[    4.140000] PCI: setting IRQ 10 as level-triggered
[    4.140000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[    4.140000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    4.140000] forcedeth: using HIGHDMA
[    4.660000] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[    4.660000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[    4.660000] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[    4.712000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.720000] sata_nv 0000:00:0e.0: version 3.3
[    4.720000] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[    4.720000] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[    4.720000] PCI: setting IRQ 5 as level-triggered
[    4.720000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[    4.720000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    4.720000] ata1: SATA max UDMA/133 cmd 0x000130c0 ctl 0x000130b6 bmdma 0x00013090 irq 5
[    4.720000] ata2: SATA max UDMA/133 cmd 0x000130b8 ctl 0x000130b2 bmdma 0x00013098 irq 5
[    4.720000] scsi0 : sata_nv
[    5.188000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.196000] ata1.00: ATA-7: FUJITSU MHW2160BH PL, 891F, max UDMA/100
[    5.196000] ata1.00: 312581808 sectors, multi 16: LBA48 
[    5.204000] ata1.00: configured for UDMA/100
[    5.204000] scsi1 : sata_nv
[    5.516000] ata2: SATA link down (SStatus 0 SControl 300)
[    5.516000] ATA: abnormal status 0x7F on port 0x000130bf
[    5.520000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2160B 891F PQ: 0 ANSI: 5
[    5.536000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[    5.540000] Uniform CD-ROM driver Revision: 3.20
[    5.540000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    5.540000] sda: Write Protect is off
[    5.540000] sda: Mode Sense: 00 3a 00 00
[    5.540000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.540000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    5.540000] sda: Write Protect is off
[    5.540000] sda: Mode Sense: 00 3a 00 00
[    5.540000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.540000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    5.584000] sd 0:0:0:0: Attached scsi disk sda
[    5.588000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.892000] Attempting manual resume
[    5.892000] swsusp: Resume From Partition 8:5
[    5.892000] PM: Checking swsusp image.
[    5.896000] PM: Resume from disk failed.
[    5.912000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.912000] EXT3-fs: write access will be enabled during recovery.
[    5.988000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00e7a34100]
[    6.000000] kjournald starting.  Commit interval 5 seconds
[    6.000000] EXT3-fs: recovery complete.
[    6.000000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.756000] NET: Registered protocol family 17
[   17.788000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.792000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.784000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.812000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   18.812000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   19.096000] sdhci: Secure Digital Host Controller Interface driver
[   19.096000] sdhci: Copyright(c) Pierre Ossman
[   19.096000] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   19.096000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   19.096000] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   19.096000] mmc0: SDHCI at 0xb8000800 irq 11 DMA
[   19.216000] input: PC Speaker as /class/input/input2
[   19.252000] Linux video capture interface: v2.00
[   19.448000] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   19.448000] usbcore: registered new interface driver uvcvideo
[   19.448000] USB Video Class driver (v0.1.0)
[   19.468000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   19.468000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   19.468000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   19.852000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   19.916000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   20.188000] lp: driver loaded but no devices found
[   20.240000] Adding 2578392k swap on /dev/disk/by-uuid/3f580873-2e26-44d3-ab05-1b456082a98d.  Priority:-1 extents:1 across:2578392k
[   20.360000] EXT3 FS on sda3, internal journal
[   20.436000] NET: Registered protocol family 10
[   20.436000] lo: Disabled Privacy Extensions
[   21.596000] No dock devices found.
[   21.612000] ibm_acpi: ec object not found
[   21.684000] input: Power Button (FF) as /class/input/input4
[   21.688000] ACPI: Power Button (FF) [PWRF]
[   21.720000] input: Power Button (CM) as /class/input/input5
[   21.724000] ACPI: Power Button (CM) [PWRB]
[   21.760000] input: Sleep Button (CM) as /class/input/input6
[   21.764000] ACPI: Sleep Button (CM) [SLPB]
[   21.796000] input: Lid Switch as /class/input/input7
[   21.796000] ACPI: Lid Switch [LID]
[   21.828000] ACPI: Battery Slot [BAT0] (battery present)
[   21.884000] Using specific hotkey driver
[   21.932000] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   21.932000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   21.948000] ACPI: AC Adapter [ACAD] (on-line)
[   21.964000] pcc_acpi: loading...
[   21.976000] wmi_add device=df844000
[   21.976000] calling WQBA
[   22.204000] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (version 2.00.00)
[   22.204000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   22.204000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   22.204000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   27.380000] ppdev: user-space parallel port driver
[   28.468000] apm: BIOS not found.
[   28.684000] Bluetooth: Core ver 2.11
[   28.684000] NET: Registered protocol family 31
[   28.684000] Bluetooth: HCI device and connection manager initialized
[   28.684000] Bluetooth: HCI socket layer initialized
[   28.716000] Bluetooth: L2CAP ver 2.8
[   28.716000] Bluetooth: L2CAP socket layer initialized
[   28.760000] Bluetooth: RFCOMM socket layer initialized
[   28.760000] Bluetooth: RFCOMM TTY layer initialized
[   28.760000] Bluetooth: RFCOMM ver 1.8
[   42.604000] eth0: no IPv6 routers present


```

---

