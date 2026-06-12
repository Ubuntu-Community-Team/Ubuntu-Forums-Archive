---
title: "ext3, acpi, kernel panics"
date: 2005-02-07
forum: Installation &amp; Upgrades
---

### Post by rick_write_taiwan on 2005-02-07
I've installed Ubuntu on a Gigabyte mobo with .75 gig ram, an Athlon, an Asus video, and on-board ethernet.

I noticed that the display was crashing to a black screen.  I saw an ACPI error, so I set the startup to acpi=no.

After that I got another crash with a lot of error messages relating to the ext3 filesystem.

If I restart immediately I get kernel panics, but I can restart if I completely power down and wait for a few seconds.

[Edit]
I forgot to mention that I get a weird message on startup:
PCI hotplug shpchp.ko
has a problem which scrolls by too quickly for me to write most of it down.

[2nd edit]
I was browsing with Firefox when abruptly Firefox quit.  The mouse pointer still moved, but the mouse buttons didn't produce results.  I couldn't get the menus to pull down.  I hit the hardware reboot button, but there was a kernel panic on reboot, so I shut off power completely for several seconds and got a normal boot.

---

### Post by eyephisc on 2005-02-07
could you post your /var/log/syslog sections with the errors so that we can help troubleshoot?

---

### Post by rick_write_taiwan on 2005-02-07
[QUOTE=eyephisc]could you post your /var/log/syslog sections with the errors so that we can help troubleshoot?[/QUOTE]

Thanks.

I just tried to post them all in one piece, but it looks like there was too much data for the php form to handle, so perhaps I should cut the log up into smaller pieces.


According to an error I just got, those pieces will have to be smaller than 30000 characters ... time to use head, tail, and >...

  I just screwed up a boring manual process.  Time to write a python script that will do it correctly.

---

### Post by rick_write_taiwan on 2005-02-09
The first 200 lines:
Feb  7 02:46:13 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  7 02:46:13 localhost udev[2623]: creating device node '/dev/vcs1'
Feb  7 02:46:13 localhost udev[2638]: removing device node '/dev/vcs1'
Feb  7 02:46:13 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  7 02:46:13 localhost kernel: Inspecting /boot/System.map-2.6.8.1-3-386
Feb  7 02:46:13 localhost udev[2640]: creating device node '/dev/vcs1'
Feb  7 02:46:13 localhost udev[2660]: removing device node '/dev/vcs1'
Feb  7 02:46:13 localhost kernel: Loaded 28166 symbols from /boot/System.map-2.6.8.1-3-386.
Feb  7 02:46:13 localhost kernel: Symbols match kernel version 2.6.8.
Feb  7 02:46:13 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  7 02:46:13 localhost kernel: Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004
Feb  7 02:46:13 localhost kernel: BIOS-provided physical RAM map:
Feb  7 02:46:13 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  7 02:46:13 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  7 02:46:13 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  7 02:46:13 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  7 02:46:13 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  7 02:46:13 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  7 02:46:13 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  7 02:46:13 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  7 02:46:13 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  7 02:46:13 localhost kernel: 767MB LOWMEM available.
Feb  7 02:46:13 localhost kernel: found SMP MP-table at 000f4d70
Feb  7 02:46:13 localhost kernel: On node 0 totalpages: 196592
Feb  7 02:46:13 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  7 02:46:13 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  7 02:46:13 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  7 02:46:13 localhost kernel: DMI 2.3 present.
Feb  7 02:46:13 localhost kernel: ACPI: RSDP (v000 GBT                                   ) @ 0x000f6760
Feb  7 02:46:13 localhost kernel: ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x2fff3000
Feb  7 02:46:13 localhost kernel: ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x2fff3040
Feb  7 02:46:13 localhost kernel: ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x2fff7600
Feb  7 02:46:13 localhost kernel: ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
Feb  7 02:46:13 localhost kernel: ACPI: PM-Timer IO Port: 0x4008
Feb  7 02:46:13 localhost kernel: ACPI: Local APIC address 0xfee00000
Feb  7 02:46:13 localhost kernel: ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb  7 02:46:13 localhost kernel: Processor #0 6:8 APIC version 16
Feb  7 02:46:13 localhost kernel: ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Feb  7 02:46:13 localhost kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb  7 02:46:13 localhost kernel: IOAPIC[0]: Assigned apic_id 2
Feb  7 02:46:13 localhost kernel: IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Feb  7 02:46:13 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  7 02:46:13 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Feb  7 02:46:13 localhost kernel: ACPI: IRQ0 used by override.
Feb  7 02:46:13 localhost kernel: ACPI: IRQ2 used by override.
Feb  7 02:46:13 localhost kernel: ACPI: IRQ9 used by override.
Feb  7 02:46:13 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  7 02:46:13 localhost kernel: Using ACPI (MADT) for SMP configuration information
Feb  7 02:46:13 localhost kernel: Built 1 zonelists
Feb  7 02:46:13 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash
Feb  7 02:46:13 localhost kernel: Initializing CPU#0
Feb  7 02:46:13 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  7 02:46:13 localhost kernel: Detected 1675.772 MHz processor.
Feb  7 02:46:13 localhost kernel: Using pmtmr for high-res timesource
Feb  7 02:46:13 localhost kernel: Console: colour VGA+ 80x25
Feb  7 02:46:13 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  7 02:46:13 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  7 02:46:13 localhost kernel: Memory: 771900k/786368k available (1336k kernel code, 13672k reserved, 728k data, 204k init, 0k highmem)
Feb  7 02:46:13 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  7 02:46:13 localhost kernel: Calibrating delay loop... 3317.76 BogoMIPS
Feb  7 02:46:13 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  7 02:46:13 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  7 02:46:13 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  7 02:46:13 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  7 02:46:13 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  7 02:46:13 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  7 02:46:13 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  7 02:46:13 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  7 02:46:13 localhost kernel: Enabling fast FPU save and restore... done.
Feb  7 02:46:13 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  7 02:46:13 localhost kernel: Checking 'hlt' instruction... OK.
Feb  7 02:46:13 localhost kernel: Checking for popad bug... OK.
Feb  7 02:46:13 localhost kernel: enabled ExtINT on CPU#0
Feb  7 02:46:13 localhost kernel: ESR value before enabling vector: 00000000
Feb  7 02:46:13 localhost kernel: ESR value after enabling vector: 00000000
Feb  7 02:46:13 localhost kernel: ENABLING IO-APIC IRQs
Feb  7 02:46:13 localhost kernel: init IO_APIC IRQs
Feb  7 02:46:13 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-16, 2-17, 2-18, 2-19, 2-20, 2-21, 2-22, 2-23 not connected.
Feb  7 02:46:13 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=-1
Feb  7 02:46:13 localhost kernel: Using local APIC timer interrupts.
Feb  7 02:46:13 localhost kernel: calibrating APIC timer ...
Feb  7 02:46:13 localhost kernel: ..... CPU clock speed is 1674.0844 MHz.
Feb  7 02:46:13 localhost kernel: ..... host bus clock speed is 267.0975 MHz.
Feb  7 02:46:13 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  7 02:46:13 localhost kernel: Freeing initrd memory: 4116k freed
Feb  7 02:46:13 localhost kernel: NET: Registered protocol family 16
Feb  7 02:46:13 localhost kernel: EISA bus registered
Feb  7 02:46:13 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  7 02:46:13 localhost kernel: PCI: Using configuration type 1
Feb  7 02:46:13 localhost kernel: mtrr: v2.0 (20020519)
Feb  7 02:46:13 localhost kernel: ACPI: Subsystem revision 20040816
Feb  7 02:46:13 localhost kernel: ACPI: Interpreter enabled
Feb  7 02:46:13 localhost kernel: ACPI: Using IOAPIC for interrupt routing
Feb  7 02:46:13 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Feb  7 02:46:13 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12)
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
Feb  7 02:46:13 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  7 02:46:13 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  7 02:46:13 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  7 02:46:13 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  7 02:46:13 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  7 02:46:13 localhost kernel: PCI: Using ACPI for IRQ routing
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 169
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 169
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 20 (level, low) -> IRQ 177
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 185
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
Feb  7 02:46:13 localhost kernel: ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 193
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
Feb  7 02:46:13 localhost kernel: number of MP IRQ sources: 15.
Feb  7 02:46:13 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  7 02:46:13 localhost kernel: testing the IO APIC.......................
Feb  7 02:46:13 localhost kernel: IO APIC #2......
Feb  7 02:46:13 localhost kernel: .... register #00: 02000000
Feb  7 02:46:13 localhost kernel: .......    : physical APIC id: 02
Feb  7 02:46:13 localhost kernel: .......    : Delivery Type: 0
Feb  7 02:46:13 localhost kernel: .......    : LTS          : 0
Feb  7 02:46:13 localhost kernel: .... register #01: 00178003
Feb  7 02:46:13 localhost kernel: .......     : max redirection entries: 0017
Feb  7 02:46:13 localhost kernel: .......     : PRQ implemented: 1
Feb  7 02:46:13 localhost kernel: .......     : IO APIC version: 0003
Feb  7 02:46:13 localhost kernel: .... IRQ redirection table:
Feb  7 02:46:13 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  7 02:46:13 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  7 02:46:13 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  7 02:46:13 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  7 02:46:13 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  7 02:46:13 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  7 02:46:13 localhost kernel:  05 001 01  0    0    0   0   0    1    1    51
Feb  7 02:46:13 localhost kernel:  06 001 01  0    0    0   0   0    1    1    59
Feb  7 02:46:13 localhost kernel:  07 001 01  0    0    0   0   0    1    1    61
Feb  7 02:46:13 localhost kernel:  08 001 01  0    0    0   0   0    1    1    69
Feb  7 02:46:13 localhost kernel:  09 001 01  0    1    0   1   0    1    1    71
Feb  7 02:46:13 localhost kernel:  0a 001 01  0    0    0   0   0    1    1    79
Feb  7 02:46:13 localhost kernel:  0b 001 01  0    0    0   0   0    1    1    81
Feb  7 02:46:13 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    89
Feb  7 02:46:13 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    91
Feb  7 02:46:13 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    99
Feb  7 02:46:13 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    A1
Feb  7 02:46:13 localhost kernel:  10 001 01  1    1    0   1   0    1    1    C9
Feb  7 02:46:13 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  7 02:46:13 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  7 02:46:13 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  7 02:46:13 localhost kernel:  14 001 01  1    1    0   1   0    1    1    B1
Feb  7 02:46:13 localhost kernel:  15 001 01  1    1    0   1   0    1    1    A9
Feb  7 02:46:13 localhost kernel:  16 001 01  1    1    0   1   0    1    1    B9
Feb  7 02:46:13 localhost kernel:  17 001 01  1    1    0   1   0    1    1    C1
Feb  7 02:46:13 localhost kernel: Using vector-based indexing
Feb  7 02:46:13 localhost kernel: IRQ to pin mappings:
Feb  7 02:46:13 localhost kernel: IRQ0 -> 0:2
Feb  7 02:46:13 localhost kernel: IRQ1 -> 0:1
Feb  7 02:46:13 localhost kernel: IRQ3 -> 0:3
Feb  7 02:46:13 localhost kernel: IRQ4 -> 0:4
Feb  7 02:46:13 localhost kernel: IRQ5 -> 0:5
Feb  7 02:46:13 localhost kernel: IRQ6 -> 0:6
Feb  7 02:46:13 localhost kernel: IRQ7 -> 0:7
Feb  7 02:46:13 localhost kernel: IRQ8 -> 0:8
Feb  7 02:46:13 localhost kernel: IRQ9 -> 0:9
Feb  7 02:46:13 localhost kernel: IRQ10 -> 0:10
Feb  7 02:46:13 localhost kernel: IRQ11 -> 0:11
Feb  7 02:46:13 localhost kernel: IRQ12 -> 0:12
Feb  7 02:46:13 localhost kernel: IRQ13 -> 0:13
Feb  7 02:46:13 localhost kernel: IRQ14 -> 0:14
Feb  7 02:46:13 localhost kernel: IRQ15 -> 0:15
Feb  7 02:46:13 localhost kernel: IRQ201 -> 0:16
Feb  7 02:46:13 localhost kernel: IRQ177 -> 0:20
Feb  7 02:46:13 localhost kernel: IRQ169 -> 0:21
Feb  7 02:46:13 localhost kernel: IRQ185 -> 0:22
Feb  7 02:46:13 localhost kernel: IRQ193 -> 0:23
Feb  7 02:46:13 localhost kernel: .................................... done.
Feb  7 02:46:13 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  7 02:46:13 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  7 02:46:13 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  7 02:46:13 localhost kernel: devfs: boot_options: 0x0
Feb  7 02:46:13 localhost kernel: Initializing Cryptographic API
Feb  7 02:46:13 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  7 02:46:13 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  7 02:46:13 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  7 02:46:13 localhost kernel: isapnp: Scanning for PnP cards...

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 02:46:13 localhost kernel: isapnp: No Plug & Play device found
Feb  7 02:46:13 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  7 02:46:13 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  7 02:46:13 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  7 02:46:13 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  7 02:46:13 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  7 02:46:13 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  7 02:46:13 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  7 02:46:13 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  7 02:46:13 localhost kernel: Cannot allocate resource for EISA slot 4
Feb  7 02:46:13 localhost kernel: Cannot allocate resource for EISA slot 5
Feb  7 02:46:13 localhost kernel: EISA: Detected 0 cards.
Feb  7 02:46:13 localhost kernel: NET: Registered protocol family 2
Feb  7 02:46:13 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  7 02:46:13 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  7 02:46:13 localhost kernel: NET: Registered protocol family 8
Feb  7 02:46:13 localhost kernel: NET: Registered protocol family 20
Feb  7 02:46:13 localhost kernel: ACPI: (supports S0 S3 S4 S5)
Feb  7 02:46:13 localhost kernel: ACPI wakeup devices: 
Feb  7 02:46:13 localhost kernel: PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 LAN0 UAR1 LPT1 
Feb  7 02:46:13 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  7 02:46:13 localhost kernel: RAMDISK: Loading 4116 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^Hdone.
Feb  7 02:46:13 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  7 02:46:13 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  7 02:46:13 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  7 02:46:13 localhost kernel: ACPI: Processor [CPU0] (supports C1)
Feb  7 02:46:13 localhost kernel: NET: Registered protocol family 1
Feb  7 02:46:13 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  7 02:46:13 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  7 02:46:13 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 20 (level, low) -> IRQ 177
Feb  7 02:46:13 localhost kernel: VP_IDE: chipset revision 6
Feb  7 02:46:13 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  7 02:46:13 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  7 02:46:13 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  7 02:46:13 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  7 02:46:13 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  7 02:46:13 localhost kernel: Using anticipatory io scheduler
Feb  7 02:46:13 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  7 02:46:13 localhost kernel: hda: max request size: 1024KiB
Feb  7 02:46:13 localhost kernel: hda: Host Protected Area detected.
Feb  7 02:46:13 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  7 02:46:13 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  7 02:46:13 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  7 02:46:13 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  7 02:46:13 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  7 02:46:13 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  7 02:46:13 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  7 02:46:13 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  7 02:46:13 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  7 02:46:13 localhost kernel: EXT3 FS on hda1, internal journal
Feb  7 02:46:13 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  7 02:46:13 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  7 02:46:13 localhost kernel: hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  7 02:46:13 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  7 02:46:13 localhost kernel: ts: Compaq touchscreen protocol output
Feb  7 02:46:13 localhost kernel: parport: PnPBIOS parport detected.
Feb  7 02:46:13 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  7 02:46:13 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  7 02:46:13 localhost kernel: Capability LSM initialized
Feb  7 02:46:13 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  7 02:46:13 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  7 02:46:13 localhost kernel: cdrom: open failed.
Feb  7 02:46:13 localhost kernel: Real Time Clock Driver v1.12
Feb  7 02:46:13 localhost kernel: input: PC Speaker
Feb  7 02:46:13 localhost kernel: inserting floppy driver for 2.6.8.1-3-386
Feb  7 02:46:13 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  7 02:46:13 localhost kernel: FDC 0 is a post-1991 82077
Feb  7 02:46:13 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  7 02:46:13 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  7 02:46:13 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  7 02:46:13 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  7 02:46:13 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  7 02:46:13 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  7 02:46:13 localhost kernel: pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb  7 02:46:13 localhost kernel: shpchp: shpc_init : shpc_cap_offset == 0
Feb  7 02:46:13 localhost kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  7 02:46:13 localhost kernel: usbcore: registered new driver usbfs
Feb  7 02:46:13 localhost kernel: usbcore: registered new driver hub
Feb  7 02:46:13 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
Feb  7 02:46:13 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  7 02:46:13 localhost kernel: uhci_hcd 0000:00:10.0: irq 169, io base 0000d000
Feb  7 02:46:13 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  7 02:46:13 localhost kernel: hub 1-0:1.0: USB hub found
Feb  7 02:46:13 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 169
Feb  7 02:46:13 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  7 02:46:13 localhost kernel: uhci_hcd 0000:00:10.1: irq 169, io base 0000d400
Feb  7 02:46:13 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  7 02:46:13 localhost kernel: hub 2-0:1.0: USB hub found
Feb  7 02:46:13 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 169
Feb  7 02:46:13 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  7 02:46:13 localhost kernel: uhci_hcd 0000:00:10.2: irq 169, io base 0000d800
Feb  7 02:46:13 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  7 02:46:13 localhost kernel: hub 3-0:1.0: USB hub found
Feb  7 02:46:13 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
Feb  7 02:46:13 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  7 02:46:13 localhost kernel: ehci_hcd 0000:00:10.3: irq 169, pci mem f092d000
Feb  7 02:46:13 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  7 02:46:13 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  7 02:46:13 localhost kernel: hub 4-0:1.0: USB hub found
Feb  7 02:46:13 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  7 02:46:13 localhost kernel: irda_init()
Feb  7 02:46:13 localhost kernel: NET: Registered protocol family 23
Feb  7 02:46:13 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  7 02:46:13 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  7 02:46:13 localhost kernel:          and report if it works on your machine.
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 185
Feb  7 02:46:13 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  7 02:46:13 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  7 02:46:13 localhost kernel: ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 193
Feb  7 02:46:13 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 193.
Feb  7 02:46:13 localhost kernel: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Feb  7 02:46:13 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  7 02:46:13 localhost kernel: NET: Registered protocol family 17
Feb  7 02:46:13 localhost kernel: NET: Registered protocol family 10
Feb  7 02:46:13 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  7 02:46:13 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  7 02:46:13 localhost udev[2662]: creating device node '/dev/vcs1'
Feb  7 02:46:14 localhost udev[2570]: creating device node '/dev/vcsa1'
Feb  7 02:46:14 localhost udev[2735]: removing device node '/dev/vcsa1'
Feb  7 02:46:14 localhost udev[2737]: creating device node '/dev/vcsa1'
Feb  7 02:46:14 localhost udev[2762]: removing device node '/dev/vcsa1'
Feb  7 02:46:14 localhost udev[2764]: creating device node '/dev/vcsa1'
Feb  7 02:46:14 localhost udev[2778]: removing device node '/dev/vcsa1'
Feb  7 02:46:14 localhost udev[2780]: creating device node '/dev/vcsa1'
Feb  7 02:46:14 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 02:46:14 localhost postfix/master[2816]: daemon started -- version 2.1.3
Feb  7 02:46:15 localhost /usr/sbin/cron[2852]: (CRON) INFO (pidfile fd = 3)
Feb  7 02:46:15 localhost /usr/sbin/cron[2853]: (CRON) STARTUP (fork ok)
Feb  7 02:46:15 localhost /usr/sbin/cron[2853]: (CRON) INFO (Running @reboot jobs)
Feb  7 02:46:15 localhost udev[2900]: removing device node '/dev/vcs1'
Feb  7 02:46:15 localhost udev[2921]: removing device node '/dev/vcsa1'
Feb  7 02:46:15 localhost udev[2923]: creating device node '/dev/vcs1'
Feb  7 02:46:15 localhost udev[2924]: creating device node '/dev/vcs2'
Feb  7 02:46:15 localhost udev[2927]: creating device node '/dev/vcsa3'
Feb  7 02:46:15 localhost udev[2928]: creating device node '/dev/vcsa1'
Feb  7 02:46:15 localhost udev[2925]: creating device node '/dev/vcs3'
Feb  7 02:46:15 localhost udev[2926]: creating device node '/dev/vcsa2'
Feb  7 02:46:16 localhost termwrap: info: Switching console charset mapping to ISO-8859-1
Feb  7 02:46:22 localhost kernel: eth0: no IPv6 routers present
Feb  7 10:46:26 localhost udev[3360]: removing device node '/dev/vcs4'
Feb  7 10:46:26 localhost udev[3362]: removing device node '/dev/vcsa4'
Feb  7 10:46:26 localhost udev[3364]: removing device node '/dev/vcs5'
Feb  7 10:46:26 localhost udev[3367]: removing device node '/dev/vcsa5'
Feb  7 10:46:26 localhost udev[3370]: removing device node '/dev/vcs6'
Feb  7 10:46:26 localhost udev[3372]: removing device node '/dev/vcsa6'
Feb  7 10:46:36 localhost udev[3382]: removing device node '/dev/vcs5'
Feb  7 10:46:36 localhost udev[3384]: removing device node '/dev/vcsa5'
Feb  7 03:06:13 localhost -- MARK --
Feb  7 03:17:01 localhost /USR/SBIN/CRON[3675]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  7 03:24:32 localhost postfix/pickup[2817]: C98B32685FB: uid=0 from=<root>
Feb  7 11:24:32 localhost postfix/cleanup[4974]: C98B32685FB: message-id=<20050207032432.C98B32685FB@localhost.localdomain>
Feb  7 03:24:32 localhost postfix/qmgr[2818]: C98B32685FB: from=<root@localhost.localdomain>, size=1215, nrcpt=1 (queue active)
Feb  7 03:24:32 localhost postfix/pickup[2817]: E93F72685FF: uid=0 from=<root>
Feb  7 11:24:32 localhost postfix/cleanup[4974]: E93F72685FF: message-id=<20050207032432.E93F72685FF@localhost.localdomain>
Feb  7 11:24:32 localhost postfix/local[4979]: C98B32685FB: to=<rick@localhost.localdomain>, orig_to=<root>, relay=local, delay=0, status=sent (delivered to mailbox)
Feb  7 03:24:32 localhost postfix/qmgr[2818]: C98B32685FB: removed
Feb  7 03:24:32 localhost postfix/qmgr[2818]: E93F72685FF: from=<root@localhost.localdomain>, size=999, nrcpt=1 (queue active)
Feb  7 11:24:32 localhost postfix/local[4979]: E93F72685FF: to=<rick@localhost.localdomain>, orig_to=<root>, relay=local, delay=0, status=sent (delivered to mailbox)
Feb  7 03:24:32 localhost postfix/qmgr[2818]: E93F72685FF: removed
Feb  7 03:24:41 localhost init: Trying to re-exec init
Feb  7 03:28:02 localhost kernel: ACPI: Power Button (FF) [PWRF]
Feb  7 03:30:01 localhost kernel: Unable to handle kernel paging request at virtual address 00800000
Feb  7 03:30:01 localhost kernel:  printing eip:
Feb  7 03:30:01 localhost kernel: c01507dd
Feb  7 03:30:01 localhost kernel: *pde = 00000000
Feb  7 03:30:01 localhost kernel: Oops: 0000 [#1]
Feb  7 03:30:01 localhost kernel: PREEMPT 
Feb  7 03:30:01 localhost kernel: Modules linked in: proc_intf freq_table cpufreq_userspace cpufreq_powersave button ac battery ipv6 af_packet via_rhine mii crc32 snd_via82xx snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore via_ircc irda crc_ccitt ehci_hcd uhci_hcd usbcore shpchp pciehp pci_hotplug via_agp agpgart analog gameport floppy pcspkr rtc md dm_mod capability commoncap parport_pc lp parport tsdev evdev ide_cd cdrom mousedev psmouse ext3 jbd ide_generic via82cxxx ide_disk ide_core unix fan thermal processor font vesafb cfbcopyarea cfbimgblt cfbfillrect
Feb  7 03:30:01 localhost kernel: CPU:    0
Feb  7 03:30:01 localhost kernel: EIP:    0060:[path_lookup+91/297]    Not tainted
Feb  7 03:30:01 localhost kernel: EFLAGS: 00010206   (2.6.8.1-3-386) 
Feb  7 03:30:01 localhost kernel: EIP is at path_lookup+0x5b/0x129
Feb  7 03:30:01 localhost kernel: eax: ef9713e0   ebx: e4b6d000   ecx: c04e5f18   edx: 00800000
Feb  7 03:30:01 localhost kernel: esi: c04e5f18   edi: e4b6d000   ebp: 00000001   esp: c04e5ef4
Feb  7 03:30:01 localhost kernel: ds: 007b   es: 007b   ss: 0068
Feb  7 03:30:01 localhost kernel: Process defoma-app (pid: 15289, threadinfo=c04e4000 task=ed922700)
Feb  7 03:30:01 localhost kernel: Stack: e4b6d000 e4b6d000 c04e5f18 c01509d5 c04e5f6c c04e5f18 083ea2b8 c04e4000 
Feb  7 03:30:01 localhost kernel:        c014c3fc c0116362 00000000 000002b5 00000076 c013aa75 00000001 00000001 
Feb  7 03:30:01 localhost kernel:        00000000 00000000 00000000 c011f2c3 00000001 00000000 ed922700 00000001 
Feb  7 03:30:01 localhost kernel: Call Trace:
Feb  7 03:30:01 localhost kernel:  [__user_walk+35/58] __user_walk+0x23/0x3a
Feb  7 03:30:01 localhost kernel:  [vfs_stat+23/65] vfs_stat+0x17/0x41
Feb  7 03:30:01 localhost kernel:  [scheduler_tick+717/924] scheduler_tick+0x2cd/0x39c
Feb  7 03:30:01 localhost kernel:  [vma_merge+205/314] vma_merge+0xcd/0x13a
Feb  7 03:30:01 localhost kernel:  [update_process_times+41/47] update_process_times+0x29/0x2f
Feb  7 03:30:01 localhost kernel:  [sys_stat64+16/39] sys_stat64+0x10/0x27
Feb  7 03:30:01 localhost kernel:  [timer_interrupt+72/258] timer_interrupt+0x48/0x102
Feb  7 03:30:01 localhost kernel:  [__do_softirq+52/115] __do_softirq+0x34/0x73
Feb  7 03:30:01 localhost kernel:  [do_IRQ+229/249] do_IRQ+0xe5/0xf9
Feb  7 03:30:01 localhost kernel:  [sysenter_past_esp+82/113] sysenter_past_esp+0x52/0x71
Feb  7 03:30:01 localhost kernel: Code: 8b 02 85 c0 75 08 0f 0b 14 01 ee d7 25 c0 ff 02 89 16 bb 00 
Feb  7 03:30:01 localhost kernel:  <6>note: defoma-app[15289] exited with preempt_count 1
Feb  7 03:30:01 localhost kernel: bad: scheduling while atomic!
Feb  7 03:30:01 localhost kernel:  [schedule+60/998] schedule+0x3c/0x3e6
Feb  7 03:30:01 localhost kernel:  [unmap_vmas+226/463] unmap_vmas+0xe2/0x1cf

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 03:30:01 localhost kernel:  [unmap_vmas+354/463] unmap_vmas+0x162/0x1cf
Feb  7 03:30:01 localhost kernel:  [exit_mmap+106/298] exit_mmap+0x6a/0x12a
Feb  7 03:30:01 localhost kernel:  [mmput+94/115] mmput+0x5e/0x73
Feb  7 03:30:01 localhost kernel:  [do_exit+354/847] do_exit+0x162/0x34f
Feb  7 03:30:01 localhost kernel:  [do_page_fault+0/1183] do_page_fault+0x0/0x49f
Feb  7 03:30:01 localhost kernel:  [do_divide_error+0/167] do_divide_error+0x0/0xa7
Feb  7 03:30:01 localhost kernel:  [do_page_fault+868/1183] do_page_fault+0x364/0x49f
Feb  7 03:30:01 localhost kernel:  [buffered_rmqueue+360/371] buffered_rmqueue+0x168/0x173
Feb  7 03:30:01 localhost kernel:  [__alloc_pages+140/686] __alloc_pages+0x8c/0x2ae
Feb  7 03:30:01 localhost kernel:  [__alloc_pages+674/686] __alloc_pages+0x2a2/0x2ae
Feb  7 03:30:01 localhost kernel:  [do_anonymous_page+292/334] do_anonymous_page+0x124/0x14e
Feb  7 03:30:01 localhost kernel:  [do_page_fault+0/1183] do_page_fault+0x0/0x49f
Feb  7 03:30:01 localhost kernel:  [error_code+45/56] error_code+0x2d/0x38
Feb  7 03:30:01 localhost kernel:  [path_lookup+91/297] path_lookup+0x5b/0x129
Feb  7 03:30:01 localhost kernel:  [__user_walk+35/58] __user_walk+0x23/0x3a
Feb  7 03:30:01 localhost kernel:  [vfs_stat+23/65] vfs_stat+0x17/0x41
Feb  7 03:30:01 localhost kernel:  [scheduler_tick+717/924] scheduler_tick+0x2cd/0x39c
Feb  7 03:30:01 localhost kernel:  [vma_merge+205/314] vma_merge+0xcd/0x13a
Feb  7 03:30:01 localhost kernel:  [update_process_times+41/47] update_process_times+0x29/0x2f
Feb  7 03:30:01 localhost kernel:  [sys_stat64+16/39] sys_stat64+0x10/0x27
Feb  7 03:30:01 localhost kernel:  [timer_interrupt+72/258] timer_interrupt+0x48/0x102
Feb  7 03:30:01 localhost kernel:  [__do_softirq+52/115] __do_softirq+0x34/0x73
Feb  7 03:30:01 localhost kernel:  [do_IRQ+229/249] do_IRQ+0xe5/0xf9
Feb  7 03:30:01 localhost kernel:  [sysenter_past_esp+82/113] sysenter_past_esp+0x52/0x71
Feb  7 11:53:38 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  7 11:53:38 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  7 11:53:38 localhost kernel: Inspecting /boot/System.map-2.6.8.1-3-386
Feb  7 11:53:38 localhost udev[2948]: creating device node '/dev/vcs1'
Feb  7 11:53:38 localhost udev[2977]: removing device node '/dev/vcs1'
Feb  7 11:53:38 localhost udev[2954]: creating device node '/dev/vcsa1'
Feb  7 11:53:38 localhost udev[2983]: removing device node '/dev/vcsa1'
Feb  7 11:53:38 localhost kernel: Loaded 28166 symbols from /boot/System.map-2.6.8.1-3-386.
Feb  7 11:53:38 localhost kernel: Symbols match kernel version 2.6.8.
Feb  7 11:53:38 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  7 11:53:38 localhost kernel: Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004
Feb  7 11:53:38 localhost kernel: BIOS-provided physical RAM map:
Feb  7 11:53:38 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  7 11:53:38 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  7 11:53:38 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  7 11:53:38 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  7 11:53:38 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  7 11:53:38 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  7 11:53:38 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  7 11:53:38 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  7 11:53:38 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  7 11:53:38 localhost kernel: 767MB LOWMEM available.
Feb  7 11:53:38 localhost kernel: found SMP MP-table at 000f4d70
Feb  7 11:53:38 localhost kernel: On node 0 totalpages: 196592
Feb  7 11:53:38 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  7 11:53:38 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  7 11:53:38 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  7 11:53:38 localhost kernel: DMI 2.3 present.
Feb  7 11:53:38 localhost kernel: ACPI: RSDP (v000 GBT                                   ) @ 0x000f6760
Feb  7 11:53:38 localhost kernel: ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x2fff3000
Feb  7 11:53:38 localhost kernel: ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x2fff3040
Feb  7 11:53:38 localhost udev[2980]: creating device node '/dev/vcs1'
Feb  7 11:53:38 localhost udev[3000]: removing device node '/dev/vcs1'
Feb  7 11:53:38 localhost udev[2986]: creating device node '/dev/vcsa1'
Feb  7 11:53:38 localhost udev[3006]: removing device node '/dev/vcsa1'
Feb  7 11:53:38 localhost kernel: ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x2fff7600
Feb  7 11:53:38 localhost kernel: ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
Feb  7 11:53:38 localhost kernel: ACPI: PM-Timer IO Port: 0x4008
Feb  7 11:53:38 localhost kernel: ACPI: Local APIC address 0xfee00000
Feb  7 11:53:38 localhost kernel: ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb  7 11:53:38 localhost kernel: Processor #0 6:8 APIC version 16
Feb  7 11:53:38 localhost kernel: ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Feb  7 11:53:38 localhost kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb  7 11:53:38 localhost kernel: IOAPIC[0]: Assigned apic_id 2
Feb  7 11:53:38 localhost kernel: IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Feb  7 11:53:38 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  7 11:53:38 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Feb  7 11:53:38 localhost kernel: ACPI: IRQ0 used by override.
Feb  7 11:53:38 localhost kernel: ACPI: IRQ2 used by override.
Feb  7 11:53:38 localhost kernel: ACPI: IRQ9 used by override.
Feb  7 11:53:38 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  7 11:53:38 localhost kernel: Using ACPI (MADT) for SMP configuration information
Feb  7 11:53:38 localhost kernel: Built 1 zonelists
Feb  7 11:53:38 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash
Feb  7 11:53:38 localhost kernel: Initializing CPU#0
Feb  7 11:53:38 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  7 11:53:38 localhost kernel: Detected 1675.772 MHz processor.
Feb  7 11:53:38 localhost kernel: Using pmtmr for high-res timesource
Feb  7 11:53:38 localhost kernel: Console: colour VGA+ 80x25
Feb  7 11:53:38 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  7 11:53:38 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  7 11:53:38 localhost kernel: Memory: 771900k/786368k available (1336k kernel code, 13672k reserved, 728k data, 204k init, 0k highmem)
Feb  7 11:53:38 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  7 11:53:38 localhost kernel: Calibrating delay loop... 3317.76 BogoMIPS
Feb  7 11:53:38 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  7 11:53:38 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  7 11:53:38 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  7 11:53:38 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  7 11:53:38 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  7 11:53:38 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  7 11:53:38 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  7 11:53:38 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  7 11:53:38 localhost kernel: Enabling fast FPU save and restore... done.
Feb  7 11:53:38 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  7 11:53:38 localhost kernel: Checking 'hlt' instruction... OK.
Feb  7 11:53:38 localhost kernel: Checking for popad bug... OK.
Feb  7 11:53:38 localhost kernel: enabled ExtINT on CPU#0
Feb  7 11:53:38 localhost kernel: ESR value before enabling vector: 00000000
Feb  7 11:53:38 localhost kernel: ESR value after enabling vector: 00000000
Feb  7 11:53:38 localhost kernel: ENABLING IO-APIC IRQs
Feb  7 11:53:38 localhost kernel: init IO_APIC IRQs
Feb  7 11:53:38 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-16, 2-17, 2-18, 2-19, 2-20, 2-21, 2-22, 2-23 not connected.
Feb  7 11:53:38 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=-1
Feb  7 11:53:38 localhost kernel: Using local APIC timer interrupts.
Feb  7 11:53:38 localhost kernel: calibrating APIC timer ...
Feb  7 11:53:38 localhost kernel: ..... CPU clock speed is 1674.0844 MHz.
Feb  7 11:53:38 localhost kernel: ..... host bus clock speed is 267.0975 MHz.
Feb  7 11:53:38 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  7 11:53:38 localhost kernel: Freeing initrd memory: 4116k freed
Feb  7 11:53:38 localhost kernel: NET: Registered protocol family 16
Feb  7 11:53:38 localhost kernel: EISA bus registered
Feb  7 11:53:38 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  7 11:53:38 localhost kernel: PCI: Using configuration type 1
Feb  7 11:53:38 localhost kernel: mtrr: v2.0 (20020519)
Feb  7 11:53:38 localhost kernel: ACPI: Subsystem revision 20040816
Feb  7 11:53:38 localhost kernel: ACPI: Interpreter enabled
Feb  7 11:53:38 localhost kernel: ACPI: Using IOAPIC for interrupt routing
Feb  7 11:53:38 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Feb  7 11:53:38 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12)
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
Feb  7 11:53:38 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  7 11:53:38 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  7 11:53:38 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  7 11:53:38 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  7 11:53:38 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  7 11:53:38 localhost kernel: PCI: Using ACPI for IRQ routing
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 169
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 169
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 20 (level, low) -> IRQ 177
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 185
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
Feb  7 11:53:38 localhost kernel: ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 193
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
Feb  7 11:53:38 localhost kernel: number of MP IRQ sources: 15.
Feb  7 11:53:38 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  7 11:53:38 localhost kernel: testing the IO APIC.......................
Feb  7 11:53:38 localhost kernel: IO APIC #2......
Feb  7 11:53:38 localhost kernel: .... register #00: 02000000
Feb  7 11:53:38 localhost kernel: .......    : physical APIC id: 02
Feb  7 11:53:38 localhost kernel: .......    : Delivery Type: 0
Feb  7 11:53:38 localhost kernel: .......    : LTS          : 0
Feb  7 11:53:38 localhost kernel: .... register #01: 00178003
Feb  7 11:53:38 localhost kernel: .......     : max redirection entries: 0017
Feb  7 11:53:38 localhost kernel: .......     : PRQ implemented: 1
Feb  7 11:53:38 localhost kernel: .......     : IO APIC version: 0003
Feb  7 11:53:38 localhost kernel: .... IRQ redirection table:
Feb  7 11:53:38 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  7 11:53:38 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  7 11:53:38 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  7 11:53:38 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  7 11:53:38 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  7 11:53:38 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  7 11:53:38 localhost kernel:  05 001 01  0    0    0   0   0    1    1    51
Feb  7 11:53:38 localhost kernel:  06 001 01  0    0    0   0   0    1    1    59
Feb  7 11:53:38 localhost kernel:  07 001 01  0    0    0   0   0    1    1    61
Feb  7 11:53:38 localhost kernel:  08 001 01  0    0    0   0   0    1    1    69
Feb  7 11:53:38 localhost kernel:  09 001 01  0    1    0   1   0    1    1    71
Feb  7 11:53:38 localhost kernel:  0a 001 01  0    0    0   0   0    1    1    79
Feb  7 11:53:38 localhost kernel:  0b 001 01  0    0    0   0   0    1    1    81
Feb  7 11:53:38 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    89
Feb  7 11:53:38 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    91
Feb  7 11:53:38 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    99
Feb  7 11:53:38 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    A1
Feb  7 11:53:38 localhost kernel:  10 001 01  1    1    0   1   0    1    1    C9
Feb  7 11:53:38 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  7 11:53:38 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  7 11:53:38 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  7 11:53:38 localhost kernel:  14 001 01  1    1    0   1   0    1    1    B1
Feb  7 11:53:38 localhost kernel:  15 001 01  1    1    0   1   0    1    1    A9
Feb  7 11:53:38 localhost kernel:  16 001 01  1    1    0   1   0    1    1    B9
Feb  7 11:53:38 localhost kernel:  17 001 01  1    1    0   1   0    1    1    C1
Feb  7 11:53:38 localhost kernel: Using vector-based indexing
Feb  7 11:53:38 localhost kernel: IRQ to pin mappings:
Feb  7 11:53:38 localhost kernel: IRQ0 -> 0:2
Feb  7 11:53:38 localhost kernel: IRQ1 -> 0:1

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 11:53:38 localhost kernel: IRQ3 -> 0:3
Feb  7 11:53:38 localhost kernel: IRQ4 -> 0:4
Feb  7 11:53:38 localhost kernel: IRQ5 -> 0:5
Feb  7 11:53:38 localhost kernel: IRQ6 -> 0:6
Feb  7 11:53:38 localhost kernel: IRQ7 -> 0:7
Feb  7 11:53:38 localhost kernel: IRQ8 -> 0:8
Feb  7 11:53:38 localhost kernel: IRQ9 -> 0:9
Feb  7 11:53:38 localhost kernel: IRQ10 -> 0:10
Feb  7 11:53:38 localhost kernel: IRQ11 -> 0:11
Feb  7 11:53:38 localhost kernel: IRQ12 -> 0:12
Feb  7 11:53:38 localhost kernel: IRQ13 -> 0:13
Feb  7 11:53:38 localhost kernel: IRQ14 -> 0:14
Feb  7 11:53:38 localhost kernel: IRQ15 -> 0:15
Feb  7 11:53:38 localhost kernel: IRQ201 -> 0:16
Feb  7 11:53:38 localhost kernel: IRQ177 -> 0:20
Feb  7 11:53:38 localhost kernel: IRQ169 -> 0:21
Feb  7 11:53:38 localhost kernel: IRQ185 -> 0:22
Feb  7 11:53:38 localhost kernel: IRQ193 -> 0:23
Feb  7 11:53:38 localhost kernel: .................................... done.
Feb  7 11:53:38 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  7 11:53:38 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  7 11:53:38 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  7 11:53:38 localhost kernel: devfs: boot_options: 0x0
Feb  7 11:53:38 localhost kernel: Initializing Cryptographic API
Feb  7 11:53:38 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  7 11:53:38 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  7 11:53:38 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  7 11:53:38 localhost kernel: isapnp: Scanning for PnP cards...
Feb  7 11:53:38 localhost kernel: isapnp: No Plug & Play device found
Feb  7 11:53:38 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  7 11:53:38 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  7 11:53:38 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  7 11:53:38 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  7 11:53:38 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  7 11:53:38 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  7 11:53:38 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  7 11:53:38 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  7 11:53:38 localhost kernel: Cannot allocate resource for EISA slot 4
Feb  7 11:53:38 localhost kernel: Cannot allocate resource for EISA slot 5
Feb  7 11:53:38 localhost kernel: EISA: Detected 0 cards.
Feb  7 11:53:38 localhost kernel: NET: Registered protocol family 2
Feb  7 11:53:38 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  7 11:53:38 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  7 11:53:38 localhost kernel: NET: Registered protocol family 8
Feb  7 11:53:38 localhost kernel: NET: Registered protocol family 20
Feb  7 11:53:38 localhost kernel: ACPI: (supports S0 S3 S4 S5)
Feb  7 11:53:38 localhost kernel: ACPI wakeup devices: 
Feb  7 11:53:38 localhost kernel: PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 LAN0 UAR1 LPT1 
Feb  7 11:53:38 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  7 11:53:38 localhost kernel: RAMDISK: Loading 4116 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^Hdone.
Feb  7 11:53:38 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  7 11:53:38 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  7 11:53:38 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  7 11:53:38 localhost kernel: ACPI: Processor [CPU0] (supports C1)
Feb  7 11:53:38 localhost kernel: NET: Registered protocol family 1
Feb  7 11:53:38 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  7 11:53:38 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  7 11:53:38 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 20 (level, low) -> IRQ 177
Feb  7 11:53:38 localhost kernel: VP_IDE: chipset revision 6
Feb  7 11:53:38 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  7 11:53:38 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  7 11:53:38 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  7 11:53:38 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  7 11:53:38 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  7 11:53:38 localhost kernel: Using anticipatory io scheduler
Feb  7 11:53:38 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  7 11:53:38 localhost kernel: hda: max request size: 1024KiB
Feb  7 11:53:38 localhost kernel: hda: Host Protected Area detected.
Feb  7 11:53:38 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  7 11:53:38 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  7 11:53:38 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  7 11:53:38 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  7 11:53:38 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  7 11:53:38 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  7 11:53:38 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  7 11:53:38 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  7 11:53:38 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  7 11:53:38 localhost kernel: EXT3 FS on hda1, internal journal
Feb  7 11:53:38 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  7 11:53:38 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  7 11:53:38 localhost kernel: hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  7 11:53:38 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  7 11:53:38 localhost kernel: ts: Compaq touchscreen protocol output
Feb  7 11:53:38 localhost kernel: parport: PnPBIOS parport detected.
Feb  7 11:53:38 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  7 11:53:38 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  7 11:53:38 localhost kernel: Capability LSM initialized
Feb  7 11:53:38 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  7 11:53:38 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  7 11:53:38 localhost kernel: cdrom: open failed.
Feb  7 11:53:38 localhost kernel: Real Time Clock Driver v1.12
Feb  7 11:53:38 localhost kernel: input: PC Speaker
Feb  7 11:53:38 localhost kernel: inserting floppy driver for 2.6.8.1-3-386
Feb  7 11:53:38 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  7 11:53:38 localhost kernel: FDC 0 is a post-1991 82077
Feb  7 11:53:38 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  7 11:53:38 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  7 11:53:38 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  7 11:53:38 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  7 11:53:38 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  7 11:53:38 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  7 11:53:38 localhost kernel: pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb  7 11:53:38 localhost kernel: shpchp: shpc_init : shpc_cap_offset == 0
Feb  7 11:53:38 localhost kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  7 11:53:38 localhost kernel: usbcore: registered new driver usbfs
Feb  7 11:53:38 localhost kernel: usbcore: registered new driver hub
Feb  7 11:53:38 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
Feb  7 11:53:38 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  7 11:53:38 localhost kernel: uhci_hcd 0000:00:10.0: irq 169, io base 0000d000
Feb  7 11:53:38 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  7 11:53:38 localhost kernel: hub 1-0:1.0: USB hub found
Feb  7 11:53:38 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 169
Feb  7 11:53:38 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  7 11:53:38 localhost kernel: uhci_hcd 0000:00:10.1: irq 169, io base 0000d400
Feb  7 11:53:38 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  7 11:53:38 localhost kernel: hub 2-0:1.0: USB hub found
Feb  7 11:53:38 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 169
Feb  7 11:53:38 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  7 11:53:38 localhost kernel: uhci_hcd 0000:00:10.2: irq 169, io base 0000d800
Feb  7 11:53:38 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  7 11:53:38 localhost kernel: hub 3-0:1.0: USB hub found
Feb  7 11:53:38 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
Feb  7 11:53:38 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  7 11:53:38 localhost kernel: ehci_hcd 0000:00:10.3: irq 169, pci mem f0939000
Feb  7 11:53:38 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  7 11:53:38 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  7 11:53:38 localhost kernel: hub 4-0:1.0: USB hub found
Feb  7 11:53:38 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  7 11:53:38 localhost kernel: irda_init()
Feb  7 11:53:38 localhost kernel: NET: Registered protocol family 23
Feb  7 11:53:38 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  7 11:53:38 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  7 11:53:38 localhost kernel:          and report if it works on your machine.
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 185
Feb  7 11:53:38 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  7 11:53:38 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  7 11:53:38 localhost kernel: ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 193
Feb  7 11:53:38 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 193.
Feb  7 11:53:38 localhost kernel: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Feb  7 11:53:38 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  7 11:53:38 localhost kernel: NET: Registered protocol family 17
Feb  7 11:53:38 localhost kernel: NET: Registered protocol family 10
Feb  7 11:53:38 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  7 11:53:38 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  7 11:53:39 localhost udev[3003]: creating device node '/dev/vcs1'
Feb  7 11:53:39 localhost kernel: ACPI: Power Button (FF) [PWRF]
Feb  7 11:53:39 localhost udev[3009]: creating device node '/dev/vcsa1'
Feb  7 11:53:42 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 11:53:42 localhost postfix/master[3293]: daemon started -- version 2.1.3
Feb  7 11:53:42 localhost /usr/sbin/cron[3366]: (CRON) INFO (pidfile fd = 3)
Feb  7 11:53:42 localhost /usr/sbin/cron[3367]: (CRON) STARTUP (fork ok)
Feb  7 11:53:42 localhost /usr/sbin/cron[3367]: (CRON) INFO (Running @reboot jobs)
Feb  7 11:53:43 localhost udev[3423]: removing device node '/dev/vcs1'
Feb  7 11:53:43 localhost udev[3426]: removing device node '/dev/vcsa1'
Feb  7 11:53:43 localhost udev[3429]: creating device node '/dev/vcs1'
Feb  7 11:53:43 localhost udev[3430]: creating device node '/dev/vcsa1'
Feb  7 11:53:43 localhost udev[3459]: creating device node '/dev/vcs2'
Feb  7 11:53:43 localhost udev[3462]: creating device node '/dev/vcsa3'
Feb  7 11:53:43 localhost udev[3460]: creating device node '/dev/vcs3'
Feb  7 11:53:43 localhost udev[3461]: creating device node '/dev/vcsa2'
Feb  7 11:53:44 localhost termwrap: info: Switching console charset mapping to ISO-8859-1
Feb  7 11:53:46 localhost kernel: eth0: no IPv6 routers present
Feb  7 11:53:54 localhost udev[3824]: removing device node '/dev/vcs4'
Feb  7 11:53:54 localhost udev[3827]: removing device node '/dev/vcsa4'
Feb  7 11:53:54 localhost udev[3830]: removing device node '/dev/vcs5'
Feb  7 11:53:54 localhost udev[3833]: removing device node '/dev/vcsa5'
Feb  7 11:53:54 localhost udev[3836]: removing device node '/dev/vcs6'
Feb  7 11:53:54 localhost udev[3839]: removing device node '/dev/vcsa6'
Feb  7 12:13:38 localhost -- MARK --
Feb  7 12:17:02 localhost /USR/SBIN/CRON[4039]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  7 12:20:17 localhost postfix/postfix-script: stopping the Postfix mail system
Feb  7 12:20:17 localhost postfix/master[3293]: terminating on signal 15
Feb  7 12:20:17 localhost postfix/postfix-script: fatal: the Postfix mail system is not running
Feb  7 12:22:16 localhost gconfd (root-7288): starting (version 2.8.1), pid 7288 user 'root'
Feb  7 12:22:16 localhost gconfd (root-7288): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 12:22:16 localhost gconfd (root-7288): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb  7 12:22:16 localhost gconfd (root-7288): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 12:22:44 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 12:22:44 localhost postfix/master[7670]: daemon started -- version 2.1.3
Feb  7 12:23:02 localhost gconfd (root-7288): Exiting
Feb  7 12:23:51 localhost init: Re-reading inittab
Feb  7 12:23:51 localhost udev[10306]: creating device node '/dev/vcs6'
Feb  7 12:23:51 localhost udev[10307]: creating device node '/dev/vcsa4'
Feb  7 12:23:51 localhost udev[10313]: creating device node '/dev/vcsa5'
Feb  7 12:23:51 localhost udev[10314]: creating device node '/dev/vcsa6'
Feb  7 12:23:51 localhost udev[10346]: creating device node '/dev/vcs7'
Feb  7 12:23:51 localhost udev[10347]: creating device node '/dev/vcsa7'
Feb  7 12:23:51 localhost udev[10361]: removing device node '/dev/vcs7'
Feb  7 12:23:51 localhost udev[10370]: removing device node '/dev/vcsa7'
Feb  7 12:23:52 localhost udev[10270]: creating device node '/dev/vcs4'
Feb  7 12:23:52 localhost udev[10279]: creating device node '/dev/vcs5'
Feb  7 12:23:53 localhost udev[10380]: creating device node '/dev/vcs7'
Feb  7 12:23:53 localhost udev[10388]: creating device node '/dev/vcsa7'
Feb  7 12:24:13 localhost gconfd (rick-10457): starting (version 2.8.1), pid 10457 user 'rick'
Feb  7 12:24:13 localhost gconfd (rick-10457): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 12:24:13 localhost gconfd (rick-10457): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  7 12:24:13 localhost gconfd (rick-10457): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 12:24:21 localhost gconfd (rick-10457): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  7 12:26:38 localhost gconfd (root-10627): starting (version 2.8.1), pid 10627 user 'root'
Feb  7 12:26:38 localhost gconfd (root-10627): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 12:26:38 localhost gconfd (root-10627): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb  7 12:26:38 localhost gconfd (root-10627): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 12:40:54 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  7 12:40:54 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  7 12:40:54 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  7 12:40:54 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  7 12:40:54 localhost kernel: Symbols match kernel version 2.6.8.
Feb  7 12:40:54 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  7 12:40:54 localhost kernel:  #1 Fri Jan 14 11:19:34 UTC 2005
Feb  7 12:40:54 localhost kernel: BIOS-provided physical RAM map:
Feb  7 12:40:54 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  7 12:40:54 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  7 12:40:54 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  7 12:40:54 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  7 12:40:54 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  7 12:40:54 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  7 12:40:54 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  7 12:40:54 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  7 12:40:54 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  7 12:40:54 localhost kernel: 767MB LOWMEM available.
Feb  7 12:40:54 localhost kernel: found SMP MP-table at 000f4d70
Feb  7 12:40:54 localhost kernel: On node 0 totalpages: 196592
Feb  7 12:40:54 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  7 12:40:54 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  7 12:40:54 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  7 12:40:54 localhost kernel: DMI 2.3 present.
Feb  7 12:40:54 localhost kernel: ACPI: RSDP (v000 GBT                                   ) @ 0x000f6760
Feb  7 12:40:54 localhost kernel: ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x2fff3000
Feb  7 12:40:54 localhost kernel: ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x2fff3040
Feb  7 12:40:54 localhost kernel: ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x2fff7600
Feb  7 12:40:54 localhost kernel: ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
Feb  7 12:40:54 localhost kernel: ACPI: PM-Timer IO Port: 0x4008
Feb  7 12:40:54 localhost kernel: ACPI: Local APIC address 0xfee00000
Feb  7 12:40:54 localhost kernel: ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb  7 12:40:54 localhost kernel: Processor #0 6:8 APIC version 16
Feb  7 12:40:54 localhost kernel: ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Feb  7 12:40:54 localhost kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb  7 12:40:54 localhost kernel: IOAPIC[0]: Assigned apic_id 2
Feb  7 12:40:54 localhost kernel: IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Feb  7 12:40:54 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  7 12:40:54 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Feb  7 12:40:54 localhost kernel: ACPI: IRQ0 used by override.
Feb  7 12:40:54 localhost kernel: ACPI: IRQ2 used by override.
Feb  7 12:40:54 localhost kernel: ACPI: IRQ9 used by override.
Feb  7 12:40:54 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  7 12:40:54 localhost kernel: Using ACPI (MADT) for SMP configuration information
Feb  7 12:40:54 localhost kernel: Built 1 zonelists
Feb  7 12:40:54 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash
Feb  7 12:40:54 localhost kernel: Initializing CPU#0
Feb  7 12:40:54 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  7 12:40:54 localhost kernel: Detected 1675.772 MHz processor.
Feb  7 12:40:54 localhost kernel: Using pmtmr for high-res timesource
Feb  7 12:40:54 localhost kernel: Console: colour VGA+ 80x25
Feb  7 12:40:54 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  7 12:40:54 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  7 12:40:54 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  7 12:40:54 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  7 12:40:54 localhost kernel: Calibrating delay loop... 3317.76 BogoMIPS
Feb  7 12:40:54 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  7 12:40:54 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  7 12:40:54 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  7 12:40:54 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  7 12:40:54 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  7 12:40:54 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  7 12:40:54 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  7 12:40:54 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  7 12:40:54 localhost kernel: Enabling fast FPU save and restore... done.
Feb  7 12:40:54 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  7 12:40:54 localhost kernel: Checking 'hlt' instruction... OK.
Feb  7 12:40:54 localhost kernel: Checking for popad bug... OK.
Feb  7 12:40:54 localhost kernel: enabled ExtINT on CPU#0
Feb  7 12:40:54 localhost kernel: ESR value before enabling vector: 00000000
Feb  7 12:40:54 localhost kernel: ESR value after enabling vector: 00000000
Feb  7 12:40:54 localhost kernel: ENABLING IO-APIC IRQs
Feb  7 12:40:54 localhost kernel: init IO_APIC IRQs
Feb  7 12:40:54 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-16, 2-17, 2-18, 2-19, 2-20, 2-21, 2-22, 2-23 not connected.
Feb  7 12:40:54 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=-1
Feb  7 12:40:54 localhost kernel: Using local APIC timer interrupts.
Feb  7 12:40:54 localhost kernel: calibrating APIC timer ...
Feb  7 12:40:54 localhost kernel: ..... CPU clock speed is 1674.0694 MHz.
Feb  7 12:40:54 localhost kernel: ..... host bus clock speed is 267.0951 MHz.
Feb  7 12:40:54 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  7 12:40:54 localhost kernel: Freeing initrd memory: 4136k freed
Feb  7 12:40:54 localhost kernel: NET: Registered protocol family 16
Feb  7 12:40:54 localhost kernel: EISA bus registered
Feb  7 12:40:54 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  7 12:40:54 localhost kernel: PCI: Using configuration type 1
Feb  7 12:40:54 localhost kernel: mtrr: v2.0 (20020519)
Feb  7 12:40:54 localhost kernel: ACPI: Subsystem revision 20040816
Feb  7 12:40:54 localhost kernel: ACPI: Interpreter enabled
Feb  7 12:40:54 localhost kernel: ACPI: Using IOAPIC for interrupt routing
Feb  7 12:40:54 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Feb  7 12:40:54 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12)
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
Feb  7 12:40:54 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  7 12:40:54 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  7 12:40:54 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  7 12:40:54 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  7 12:40:54 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  7 12:40:54 localhost kernel: PCI: Using ACPI for IRQ routing
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 169
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 169
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 20 (level, low) -> IRQ 177
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 185
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
Feb  7 12:40:54 localhost kernel: ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 193
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
Feb  7 12:40:54 localhost kernel: number of MP IRQ sources: 15.
Feb  7 12:40:54 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  7 12:40:54 localhost kernel: testing the IO APIC.......................
Feb  7 12:40:54 localhost kernel: IO APIC #2......
Feb  7 12:40:54 localhost kernel: .... register #00: 02000000
Feb  7 12:40:54 localhost kernel: .......    : physical APIC id: 02
Feb  7 12:40:54 localhost kernel: .......    : Delivery Type: 0
Feb  7 12:40:54 localhost kernel: .......    : LTS          : 0
Feb  7 12:40:54 localhost kernel: .... register #01: 00178003
Feb  7 12:40:54 localhost kernel: .......     : max redirection entries: 0017
Feb  7 12:40:54 localhost kernel: .......     : PRQ implemented: 1
Feb  7 12:40:54 localhost kernel: .......     : IO APIC version: 0003
Feb  7 12:40:54 localhost kernel: .... IRQ redirection table:
Feb  7 12:40:54 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  7 12:40:54 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  7 12:40:54 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  7 12:40:54 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  7 12:40:54 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  7 12:40:54 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  7 12:40:54 localhost kernel:  05 001 01  0    0    0   0   0    1    1    51
Feb  7 12:40:54 localhost kernel:  06 001 01  0    0    0   0   0    1    1    59
Feb  7 12:40:54 localhost kernel:  07 001 01  0    0    0   0   0    1    1    61
Feb  7 12:40:54 localhost kernel:  08 001 01  0    0    0   0   0    1    1    69
Feb  7 12:40:54 localhost kernel:  09 001 01  0    1    0   1   0    1    1    71
Feb  7 12:40:54 localhost kernel:  0a 001 01  0    0    0   0   0    1    1    79
Feb  7 12:40:54 localhost kernel:  0b 001 01  0    0    0   0   0    1    1    81
Feb  7 12:40:54 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    89
Feb  7 12:40:54 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    91
Feb  7 12:40:54 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    99
Feb  7 12:40:54 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    A1
Feb  7 12:40:54 localhost kernel:  10 001 01  1    1    0   1   0    1    1    C9
Feb  7 12:40:54 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  7 12:40:54 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  7 12:40:54 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  7 12:40:54 localhost kernel:  14 001 01  1    1    0   1   0    1    1    B1
Feb  7 12:40:54 localhost kernel:  15 001 01  1    1    0   1   0    1    1    A9
Feb  7 12:40:54 localhost kernel:  16 001 01  1    1    0   1   0    1    1    B9
Feb  7 12:40:54 localhost kernel:  17 001 01  1    1    0   1   0    1    1    C1
Feb  7 12:40:54 localhost kernel: Using vector-based indexing
Feb  7 12:40:54 localhost kernel: IRQ to pin mappings:
Feb  7 12:40:54 localhost kernel: IRQ0 -> 0:2
Feb  7 12:40:54 localhost kernel: IRQ1 -> 0:1
Feb  7 12:40:54 localhost kernel: IRQ3 -> 0:3
Feb  7 12:40:54 localhost kernel: IRQ4 -> 0:4
Feb  7 12:40:54 localhost kernel: IRQ5 -> 0:5
Feb  7 12:40:54 localhost kernel: IRQ6 -> 0:6
Feb  7 12:40:54 localhost kernel: IRQ7 -> 0:7
Feb  7 12:40:54 localhost kernel: IRQ8 -> 0:8
Feb  7 12:40:54 localhost kernel: IRQ9 -> 0:9
Feb  7 12:40:54 localhost kernel: IRQ10 -> 0:10
Feb  7 12:40:54 localhost kernel: IRQ11 -> 0:11
Feb  7 12:40:54 localhost kernel: IRQ12 -> 0:12
Feb  7 12:40:54 localhost kernel: IRQ13 -> 0:13
Feb  7 12:40:54 localhost kernel: IRQ14 -> 0:14
Feb  7 12:40:54 localhost kernel: IRQ15 -> 0:15
Feb  7 12:40:54 localhost kernel: IRQ201 -> 0:16
Feb  7 12:40:54 localhost kernel: IRQ177 -> 0:20
Feb  7 12:40:54 localhost kernel: IRQ169 -> 0:21
Feb  7 12:40:54 localhost kernel: IRQ185 -> 0:22
Feb  7 12:40:54 localhost kernel: IRQ193 -> 0:23
Feb  7 12:40:54 localhost kernel: .................................... done.
Feb  7 12:40:54 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  7 12:40:54 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  7 12:40:54 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  7 12:40:54 localhost kernel: devfs: boot_options: 0x0
Feb  7 12:40:54 localhost kernel: Initializing Cryptographic API
Feb  7 12:40:54 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 12:40:54 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  7 12:40:54 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  7 12:40:54 localhost kernel: isapnp: Scanning for PnP cards...
Feb  7 12:40:54 localhost kernel: isapnp: No Plug & Play device found
Feb  7 12:40:54 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  7 12:40:54 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  7 12:40:54 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  7 12:40:54 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  7 12:40:54 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  7 12:40:54 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  7 12:40:54 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  7 12:40:54 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  7 12:40:54 localhost kernel: Cannot allocate resource for EISA slot 4
Feb  7 12:40:54 localhost kernel: Cannot allocate resource for EISA slot 5
Feb  7 12:40:54 localhost kernel: EISA: Detected 0 cards.
Feb  7 12:40:54 localhost kernel: NET: Registered protocol family 2
Feb  7 12:40:54 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  7 12:40:54 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  7 12:40:54 localhost kernel: NET: Registered protocol family 8
Feb  7 12:40:54 localhost kernel: NET: Registered protocol family 20
Feb  7 12:40:54 localhost kernel: ACPI: (supports S0 S3 S4 S5)
Feb  7 12:40:54 localhost kernel: ACPI wakeup devices: 
Feb  7 12:40:54 localhost kernel: PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 LAN0 UAR1 LPT1 
Feb  7 12:40:54 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  7 12:40:54 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  7 12:40:54 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  7 12:40:54 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  7 12:40:54 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  7 12:40:54 localhost kernel: ACPI: Processor [CPU0] (supports C1)
Feb  7 12:40:54 localhost kernel: NET: Registered protocol family 1
Feb  7 12:40:54 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  7 12:40:54 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  7 12:40:54 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 20 (level, low) -> IRQ 177
Feb  7 12:40:54 localhost kernel: VP_IDE: chipset revision 6
Feb  7 12:40:54 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  7 12:40:54 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  7 12:40:54 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  7 12:40:54 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  7 12:40:54 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  7 12:40:54 localhost kernel: Using anticipatory io scheduler
Feb  7 12:40:54 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  7 12:40:54 localhost kernel: hda: max request size: 1024KiB
Feb  7 12:40:54 localhost kernel: hda: Host Protected Area detected.
Feb  7 12:40:54 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  7 12:40:54 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  7 12:40:54 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  7 12:40:54 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  7 12:40:54 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  7 12:40:54 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  7 12:40:54 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  7 12:40:54 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Feb  7 12:40:54 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  7 12:40:54 localhost kernel: EXT3-fs: hda1: orphan cleanup on readonly fs
Feb  7 12:40:54 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6882468
Feb  7 12:40:54 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6882469
Feb  7 12:40:54 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881317
Feb  7 12:40:54 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881314
Feb  7 12:40:54 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881310
Feb  7 12:40:54 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881308
Feb  7 12:40:54 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881304
Feb  7 12:40:54 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 2883589
Feb  7 12:40:54 localhost kernel: EXT3-fs: hda1: 8 orphan inodes deleted
Feb  7 12:40:54 localhost kernel: EXT3-fs: recovery complete.
Feb  7 12:40:54 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  7 12:40:54 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  7 12:40:54 localhost kernel: EXT3 FS on hda1, internal journal
Feb  7 12:40:54 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  7 12:40:54 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  7 12:40:54 localhost kernel: ts: Compaq touchscreen protocol output
Feb  7 12:40:54 localhost kernel: hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  7 12:40:54 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  7 12:40:54 localhost kernel: parport: PnPBIOS parport detected.
Feb  7 12:40:54 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  7 12:40:54 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  7 12:40:54 localhost kernel: Capability LSM initialized
Feb  7 12:40:54 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  7 12:40:54 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  7 12:40:54 localhost kernel: cdrom: open failed.
Feb  7 12:40:54 localhost kernel: Real Time Clock Driver v1.12
Feb  7 12:40:54 localhost kernel: input: PC Speaker
Feb  7 12:40:54 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  7 12:40:54 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  7 12:40:54 localhost kernel: FDC 0 is a post-1991 82077
Feb  7 12:40:54 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  7 12:40:54 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  7 12:40:54 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  7 12:40:54 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  7 12:40:54 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  7 12:40:54 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  7 12:40:54 localhost kernel: pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb  7 12:40:54 localhost kernel: shpchp: shpc_init : shpc_cap_offset == 0
Feb  7 12:40:54 localhost kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  7 12:40:54 localhost kernel: usbcore: registered new driver usbfs
Feb  7 12:40:54 localhost kernel: usbcore: registered new driver hub
Feb  7 12:40:54 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
Feb  7 12:40:54 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  7 12:40:54 localhost kernel: uhci_hcd 0000:00:10.0: irq 169, io base 0000d000
Feb  7 12:40:54 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  7 12:40:54 localhost kernel: hub 1-0:1.0: USB hub found
Feb  7 12:40:54 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 169
Feb  7 12:40:54 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  7 12:40:54 localhost kernel: uhci_hcd 0000:00:10.1: irq 169, io base 0000d400
Feb  7 12:40:54 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  7 12:40:54 localhost kernel: hub 2-0:1.0: USB hub found
Feb  7 12:40:54 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 169
Feb  7 12:40:54 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  7 12:40:54 localhost kernel: uhci_hcd 0000:00:10.2: irq 169, io base 0000d800
Feb  7 12:40:54 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  7 12:40:54 localhost kernel: hub 3-0:1.0: USB hub found
Feb  7 12:40:54 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
Feb  7 12:40:54 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  7 12:40:54 localhost kernel: ehci_hcd 0000:00:10.3: irq 169, pci mem f0921000
Feb  7 12:40:54 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  7 12:40:54 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  7 12:40:54 localhost kernel: hub 4-0:1.0: USB hub found
Feb  7 12:40:54 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  7 12:40:54 localhost kernel: irda_init()
Feb  7 12:40:54 localhost kernel: NET: Registered protocol family 23
Feb  7 12:40:54 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  7 12:40:54 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  7 12:40:54 localhost kernel:          and report if it works on your machine.
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 185
Feb  7 12:40:54 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  7 12:40:54 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  7 12:40:54 localhost kernel: ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 193
Feb  7 12:40:54 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 193.
Feb  7 12:40:54 localhost kernel: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Feb  7 12:40:54 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  7 12:40:54 localhost kernel: NET: Registered protocol family 17
Feb  7 12:40:54 localhost kernel: NET: Registered protocol family 10
Feb  7 12:40:54 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  7 12:40:54 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  7 12:40:55 localhost kernel: ACPI: Power Button (FF) [PWRF]
Feb  7 12:40:55 localhost udev[2937]: creating device node '/dev/vcs1'
Feb  7 12:40:55 localhost udev[2938]: creating device node '/dev/vcsa1'
Feb  7 12:40:55 localhost udev[3089]: removing device node '/dev/vcs1'
Feb  7 12:40:55 localhost udev[3093]: removing device node '/dev/vcsa1'
Feb  7 12:40:55 localhost udev[3092]: creating device node '/dev/vcs1'
Feb  7 12:40:55 localhost udev[3096]: creating device node '/dev/vcsa1'
Feb  7 12:40:55 localhost udev[3100]: removing device node '/dev/vcs1'
Feb  7 12:40:55 localhost udev[3106]: removing device node '/dev/vcsa1'
Feb  7 12:40:55 localhost udev[3104]: creating device node '/dev/vcs1'
Feb  7 12:40:55 localhost udev[3112]: removing device node '/dev/vcs1'
Feb  7 12:40:55 localhost udev[3109]: creating device node '/dev/vcsa1'
Feb  7 12:40:55 localhost udev[3118]: removing device node '/dev/vcsa1'
Feb  7 12:40:56 localhost udev[3115]: creating device node '/dev/vcs1'
Feb  7 12:40:56 localhost udev[3121]: creating device node '/dev/vcsa1'
Feb  7 12:40:58 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 12:40:58 localhost postfix/master[3319]: daemon started -- version 2.1.3
Feb  7 12:40:59 localhost /usr/sbin/cron[3392]: (CRON) INFO (pidfile fd = 3)
Feb  7 12:40:59 localhost /usr/sbin/cron[3393]: (CRON) STARTUP (fork ok)
Feb  7 12:40:59 localhost /usr/sbin/cron[3393]: (CRON) INFO (Running @reboot jobs)
Feb  7 12:41:00 localhost udev[3438]: removing device node '/dev/vcs1'
Feb  7 12:41:00 localhost udev[3465]: removing device node '/dev/vcsa1'
Feb  7 12:41:00 localhost udev[3508]: creating device node '/dev/vcs1'
Feb  7 12:41:00 localhost udev[3509]: creating device node '/dev/vcsa1'
Feb  7 12:41:00 localhost udev[3510]: creating device node '/dev/vcs2'
Feb  7 12:41:00 localhost udev[3511]: creating device node '/dev/vcs3'
Feb  7 12:41:00 localhost udev[3512]: creating device node '/dev/vcsa2'
Feb  7 12:41:00 localhost udev[3562]: creating device node '/dev/vcs5'
Feb  7 12:41:00 localhost udev[3563]: creating device node '/dev/vcsa4'
Feb  7 12:41:00 localhost udev[3564]: creating device node '/dev/vcs6'
Feb  7 12:41:00 localhost udev[3565]: creating device node '/dev/vcsa5'
Feb  7 12:41:00 localhost udev[3566]: creating device node '/dev/vcsa6'
Feb  7 12:41:00 localhost udev[3560]: creating device node '/dev/vcs4'
Feb  7 12:41:00 localhost udev[3561]: creating device node '/dev/vcsa3'
Feb  7 12:41:00 localhost udev[3567]: creating device node '/dev/vcs7'
Feb  7 12:41:00 localhost udev[3580]: creating device node '/dev/vcsa7'
Feb  7 12:41:00 localhost udev[3613]: removing device node '/dev/vcs7'
Feb  7 12:41:00 localhost udev[3616]: removing device node '/dev/vcsa7'
Feb  7 12:41:01 localhost udev[3633]: creating device node '/dev/vcs7'
Feb  7 12:41:01 localhost udev[3634]: creating device node '/dev/vcsa7'
Feb  7 12:41:03 localhost kernel: eth0: no IPv6 routers present
Feb  7 12:41:17 localhost gconfd (rick-3699): starting (version 2.8.1), pid 3699 user 'rick'
Feb  7 12:41:17 localhost gconfd (rick-3699): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 12:41:17 localhost gconfd (rick-3699): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  7 12:41:17 localhost gconfd (rick-3699): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 12:41:27 localhost gconfd (rick-3699): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  7 12:42:27 localhost gconfd (root-3845): starting (version 2.8.1), pid 3845 user 'root'
Feb  7 12:42:27 localhost gconfd (root-3845): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 12:42:27 localhost gconfd (root-3845): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb  7 12:42:27 localhost gconfd (root-3845): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 12:44:00 localhost shutdown[3878]: shutting down for system reboot
Feb  7 12:44:00 localhost init: Switching to runlevel: 6
Feb  7 12:44:00 localhost udev[3888]: removing device node '/dev/vcs2'
Feb  7 12:44:00 localhost udev[3951]: removing device node '/dev/vcsa2'
Feb  7 12:44:00 localhost udev[3955]: removing device node '/dev/vcsa3'
Feb  7 12:44:00 localhost udev[3958]: removing device node '/dev/vcs4'
Feb  7 12:44:00 localhost udev[3967]: removing device node '/dev/vcsa5'
Feb  7 12:44:00 localhost udev[3968]: removing device node '/dev/vcs6'
Feb  7 12:44:00 localhost udev[3954]: removing device node '/dev/vcs3'
Feb  7 12:44:00 localhost udev[3961]: removing device node '/dev/vcsa4'
Feb  7 12:44:00 localhost udev[3964]: removing device node '/dev/vcs5'
Feb  7 12:44:00 localhost udev[3977]: removing device node '/dev/vcsa6'
Feb  7 12:44:01 localhost gconfd (rick-3699): Received signal 15, shutting down cleanly

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 12:44:01 localhost gconfd (rick-3699): Exiting
Feb  7 12:44:01 localhost udev[4006]: removing device node '/dev/vcs1'
Feb  7 12:44:01 localhost udev[4009]: removing device node '/dev/vcsa1'
Feb  7 12:44:02 localhost udev[4033]: creating device node '/dev/vcsa1'
Feb  7 12:44:02 localhost udev[4075]: removing device node '/dev/vcsa1'
Feb  7 12:44:02 localhost udev[4078]: creating device node '/dev/vcsa1'
Feb  7 12:44:02 localhost udev[4123]: removing device node '/dev/vcsa1'
Feb  7 12:44:03 localhost postfix/postfix-script: stopping the Postfix mail system
Feb  7 12:44:03 localhost postfix/master[3319]: terminating on signal 15
Feb  7 12:44:04 localhost kernel: Kernel logging (proc) stopped.
Feb  7 12:44:04 localhost kernel: Kernel log daemon terminating.
Feb  7 12:44:04 localhost exiting on signal 15
Feb  7 12:45:01 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  7 12:45:01 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  7 12:45:01 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  7 12:45:01 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  7 12:45:01 localhost kernel: Symbols match kernel version 2.6.8.
Feb  7 12:45:01 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  7 12:45:01 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  7 12:45:01 localhost kernel: BIOS-provided physical RAM map:
Feb  7 12:45:01 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  7 12:45:01 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  7 12:45:01 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  7 12:45:01 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  7 12:45:01 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  7 12:45:01 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  7 12:45:01 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  7 12:45:01 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  7 12:45:01 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  7 12:45:01 localhost kernel: 767MB LOWMEM available.
Feb  7 12:45:01 localhost kernel: found SMP MP-table at 000f4d70
Feb  7 12:45:01 localhost kernel: On node 0 totalpages: 196592
Feb  7 12:45:01 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  7 12:45:01 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  7 12:45:01 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  7 12:45:01 localhost kernel: DMI 2.3 present.
Feb  7 12:45:01 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  7 12:45:01 localhost kernel:     Virtual Wire compatibility mode.
Feb  7 12:45:01 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  7 12:45:01 localhost kernel: Processor #0 6:8 APIC version 17
Feb  7 12:45:01 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  7 12:45:01 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  7 12:45:01 localhost kernel: Processors: 1
Feb  7 12:45:01 localhost kernel: Built 1 zonelists
Feb  7 12:45:01 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  7 12:45:01 localhost kernel: Initializing CPU#0
Feb  7 12:45:01 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  7 12:45:01 localhost kernel: Detected 1675.772 MHz processor.
Feb  7 12:45:01 localhost kernel: Using tsc for high-res timesource
Feb  7 12:45:01 localhost kernel: Console: colour VGA+ 80x25
Feb  7 12:45:01 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  7 12:45:01 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  7 12:45:01 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  7 12:45:01 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  7 12:45:01 localhost kernel: Calibrating delay loop... 3293.18 BogoMIPS
Feb  7 12:45:01 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  7 12:45:01 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  7 12:45:01 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  7 12:45:01 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  7 12:45:01 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  7 12:45:01 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  7 12:45:01 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  7 12:45:01 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  7 12:45:01 localhost kernel: Enabling fast FPU save and restore... done.
Feb  7 12:45:01 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  7 12:45:01 localhost kernel: Checking 'hlt' instruction... OK.
Feb  7 12:45:01 localhost kernel: Checking for popad bug... OK.
Feb  7 12:45:01 localhost kernel: enabled ExtINT on CPU#0
Feb  7 12:45:01 localhost kernel: ESR value before enabling vector: 00000000
Feb  7 12:45:01 localhost kernel: ESR value after enabling vector: 00000000
Feb  7 12:45:01 localhost kernel: ENABLING IO-APIC IRQs
Feb  7 12:45:01 localhost kernel: Setting 2 in the phys_id_present_map
Feb  7 12:45:01 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  7 12:45:01 localhost kernel: init IO_APIC IRQs
Feb  7 12:45:01 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  7 12:45:01 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  7 12:45:01 localhost kernel: number of MP IRQ sources: 20.
Feb  7 12:45:01 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  7 12:45:01 localhost kernel: testing the IO APIC.......................
Feb  7 12:45:01 localhost kernel: IO APIC #2......
Feb  7 12:45:01 localhost kernel: .... register #00: 02000000
Feb  7 12:45:01 localhost kernel: .......    : physical APIC id: 02
Feb  7 12:45:01 localhost kernel: .......    : Delivery Type: 0
Feb  7 12:45:01 localhost kernel: .......    : LTS          : 0
Feb  7 12:45:01 localhost kernel: .... register #01: 00178003
Feb  7 12:45:01 localhost kernel: .......     : max redirection entries: 0017
Feb  7 12:45:01 localhost kernel: .......     : PRQ implemented: 1
Feb  7 12:45:01 localhost kernel: .......     : IO APIC version: 0003
Feb  7 12:45:01 localhost kernel: .... IRQ redirection table:
Feb  7 12:45:01 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  7 12:45:01 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  7 12:45:01 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  7 12:45:01 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  7 12:45:01 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  7 12:45:01 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  7 12:45:01 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  7 12:45:01 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  7 12:45:01 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  7 12:45:01 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  7 12:45:01 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  7 12:45:01 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  7 12:45:01 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  7 12:45:01 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  7 12:45:01 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  7 12:45:01 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  7 12:45:01 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  7 12:45:01 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  7 12:45:01 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  7 12:45:01 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  7 12:45:01 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  7 12:45:01 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  7 12:45:01 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  7 12:45:01 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  7 12:45:01 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  7 12:45:01 localhost kernel: Using vector-based indexing
Feb  7 12:45:01 localhost kernel: IRQ to pin mappings:
Feb  7 12:45:01 localhost kernel: IRQ0 -> 0:2
Feb  7 12:45:01 localhost kernel: IRQ1 -> 0:1
Feb  7 12:45:01 localhost kernel: IRQ3 -> 0:3
Feb  7 12:45:01 localhost kernel: IRQ4 -> 0:4
Feb  7 12:45:01 localhost kernel: IRQ6 -> 0:6
Feb  7 12:45:01 localhost kernel: IRQ7 -> 0:7
Feb  7 12:45:01 localhost kernel: IRQ8 -> 0:8
Feb  7 12:45:01 localhost kernel: IRQ9 -> 0:9
Feb  7 12:45:01 localhost kernel: IRQ12 -> 0:12
Feb  7 12:45:01 localhost kernel: IRQ13 -> 0:13
Feb  7 12:45:01 localhost kernel: IRQ14 -> 0:14
Feb  7 12:45:01 localhost kernel: IRQ15 -> 0:15
Feb  7 12:45:01 localhost kernel: IRQ145 -> 0:16
Feb  7 12:45:01 localhost kernel: IRQ153 -> 0:21
Feb  7 12:45:01 localhost kernel: IRQ161 -> 0:22
Feb  7 12:45:01 localhost kernel: IRQ169 -> 0:23
Feb  7 12:45:01 localhost kernel: .................................... done.
Feb  7 12:45:01 localhost kernel: Using local APIC timer interrupts.
Feb  7 12:45:01 localhost kernel: calibrating APIC timer ...
Feb  7 12:45:01 localhost kernel: ..... CPU clock speed is 1674.0694 MHz.
Feb  7 12:45:01 localhost kernel: ..... host bus clock speed is 267.0951 MHz.
Feb  7 12:45:01 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  7 12:45:01 localhost kernel: Freeing initrd memory: 4136k freed
Feb  7 12:45:01 localhost kernel: NET: Registered protocol family 16
Feb  7 12:45:01 localhost kernel: EISA bus registered
Feb  7 12:45:01 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  7 12:45:01 localhost kernel: PCI: Using configuration type 1
Feb  7 12:45:01 localhost kernel: mtrr: v2.0 (20020519)
Feb  7 12:45:01 localhost kernel: ACPI: Subsystem revision 20040816
Feb  7 12:45:01 localhost kernel: ACPI: Interpreter disabled.
Feb  7 12:45:01 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  7 12:45:01 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  7 12:45:01 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  7 12:45:01 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  7 12:45:01 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  7 12:45:01 localhost kernel: PCI: Probing PCI hardware
Feb  7 12:45:01 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  7 12:45:01 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  7 12:45:01 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  7 12:45:01 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  7 12:45:01 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  7 12:45:01 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  7 12:45:01 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  7 12:45:01 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  7 12:45:01 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  7 12:45:01 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  7 12:45:01 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  7 12:45:01 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  7 12:45:01 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  7 12:45:01 localhost kernel: devfs: boot_options: 0x0
Feb  7 12:45:01 localhost kernel: Initializing Cryptographic API
Feb  7 12:45:01 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  7 12:45:01 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  7 12:45:01 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  7 12:45:01 localhost kernel: isapnp: Scanning for PnP cards...
Feb  7 12:45:01 localhost kernel: isapnp: No Plug & Play device found
Feb  7 12:45:01 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  7 12:45:01 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  7 12:45:01 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  7 12:45:01 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  7 12:45:01 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  7 12:45:01 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  7 12:45:01 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  7 12:45:01 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  7 12:45:01 localhost kernel: EISA: Detected 0 cards.
Feb  7 12:45:01 localhost kernel: NET: Registered protocol family 2
Feb  7 12:45:01 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  7 12:45:01 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  7 12:45:01 localhost kernel: NET: Registered protocol family 8
Feb  7 12:45:01 localhost kernel: NET: Registered protocol family 20
Feb  7 12:45:01 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  7 12:45:01 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  7 12:45:01 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  7 12:45:01 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  7 12:45:01 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  7 12:45:01 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  7 12:45:01 localhost kernel: NET: Registered protocol family 1
Feb  7 12:45:01 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  7 12:45:01 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  7 12:45:01 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  7 12:45:01 localhost kernel: VP_IDE: chipset revision 6
Feb  7 12:45:01 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  7 12:45:01 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  7 12:45:01 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 12:45:01 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  7 12:45:01 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  7 12:45:01 localhost kernel: Using anticipatory io scheduler
Feb  7 12:45:01 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  7 12:45:01 localhost kernel: hda: max request size: 1024KiB
Feb  7 12:45:01 localhost kernel: hda: Host Protected Area detected.
Feb  7 12:45:01 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  7 12:45:01 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  7 12:45:01 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  7 12:45:01 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  7 12:45:01 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  7 12:45:01 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  7 12:45:01 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  7 12:45:01 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  7 12:45:01 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  7 12:45:01 localhost kernel: EXT3 FS on hda1, internal journal
Feb  7 12:45:01 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  7 12:45:01 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  7 12:45:01 localhost kernel: ts: Compaq touchscreen protocol output
Feb  7 12:45:01 localhost kernel: hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  7 12:45:01 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  7 12:45:01 localhost kernel: parport: PnPBIOS parport detected.
Feb  7 12:45:01 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  7 12:45:01 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  7 12:45:01 localhost kernel: Capability LSM initialized
Feb  7 12:45:01 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  7 12:45:01 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  7 12:45:01 localhost kernel: cdrom: open failed.
Feb  7 12:45:01 localhost kernel: Real Time Clock Driver v1.12
Feb  7 12:45:01 localhost kernel: input: PC Speaker
Feb  7 12:45:01 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  7 12:45:01 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  7 12:45:01 localhost kernel: FDC 0 is a post-1991 82077
Feb  7 12:45:01 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  7 12:45:01 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  7 12:45:01 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  7 12:45:01 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  7 12:45:01 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  7 12:45:01 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  7 12:45:01 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  7 12:45:01 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  7 12:45:01 localhost kernel: usbcore: registered new driver usbfs
Feb  7 12:45:01 localhost kernel: usbcore: registered new driver hub
Feb  7 12:45:01 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  7 12:45:01 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  7 12:45:01 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  7 12:45:01 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  7 12:45:01 localhost kernel: hub 1-0:1.0: USB hub found
Feb  7 12:45:01 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  7 12:45:01 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  7 12:45:01 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  7 12:45:01 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  7 12:45:01 localhost kernel: hub 2-0:1.0: USB hub found
Feb  7 12:45:01 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  7 12:45:01 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  7 12:45:01 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  7 12:45:01 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  7 12:45:01 localhost kernel: hub 3-0:1.0: USB hub found
Feb  7 12:45:01 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  7 12:45:01 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  7 12:45:01 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f092a000
Feb  7 12:45:01 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  7 12:45:01 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  7 12:45:01 localhost kernel: hub 4-0:1.0: USB hub found
Feb  7 12:45:01 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  7 12:45:01 localhost kernel: irda_init()
Feb  7 12:45:01 localhost kernel: NET: Registered protocol family 23
Feb  7 12:45:01 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  7 12:45:01 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  7 12:45:01 localhost kernel:          and report if it works on your machine.
Feb  7 12:45:01 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  7 12:45:01 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  7 12:45:01 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  7 12:45:01 localhost kernel: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Feb  7 12:45:01 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  7 12:45:01 localhost kernel: NET: Registered protocol family 17
Feb  7 12:45:01 localhost kernel: NET: Registered protocol family 10
Feb  7 12:45:01 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  7 12:45:01 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  7 12:45:02 localhost udev[2863]: creating device node '/dev/vcs1'
Feb  7 12:45:02 localhost udev[3019]: removing device node '/dev/vcs1'
Feb  7 12:45:02 localhost udev[2871]: creating device node '/dev/vcsa1'
Feb  7 12:45:02 localhost udev[3026]: removing device node '/dev/vcsa1'
Feb  7 12:45:02 localhost udev[3022]: creating device node '/dev/vcs1'
Feb  7 12:45:02 localhost udev[3032]: removing device node '/dev/vcs1'
Feb  7 12:45:02 localhost udev[3029]: creating device node '/dev/vcsa1'
Feb  7 12:45:02 localhost udev[3038]: removing device node '/dev/vcsa1'
Feb  7 12:45:02 localhost udev[3035]: creating device node '/dev/vcs1'
Feb  7 12:45:02 localhost udev[3053]: removing device node '/dev/vcs1'
Feb  7 12:45:02 localhost udev[3041]: creating device node '/dev/vcsa1'
Feb  7 12:45:02 localhost udev[3059]: removing device node '/dev/vcsa1'
Feb  7 12:45:02 localhost udev[3056]: creating device node '/dev/vcs1'
Feb  7 12:45:02 localhost udev[3062]: creating device node '/dev/vcsa1'
Feb  7 12:45:05 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 12:45:05 localhost postfix/master[3251]: daemon started -- version 2.1.3
Feb  7 12:45:05 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  7 12:45:05 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  7 12:45:05 localhost /usr/sbin/cron[3324]: (CRON) INFO (pidfile fd = 3)
Feb  7 12:45:05 localhost /usr/sbin/cron[3325]: (CRON) STARTUP (fork ok)
Feb  7 12:45:05 localhost /usr/sbin/cron[3325]: (CRON) INFO (Running @reboot jobs)
Feb  7 12:45:06 localhost udev[3369]: removing device node '/dev/vcs1'
Feb  7 12:45:06 localhost udev[3379]: removing device node '/dev/vcsa1'
Feb  7 12:45:07 localhost udev[3473]: creating device node '/dev/vcsa5'
Feb  7 12:45:07 localhost udev[3484]: creating device node '/dev/vcs6'
Feb  7 12:45:07 localhost udev[3499]: creating device node '/dev/vcsa6'
Feb  7 12:45:07 localhost udev[3500]: creating device node '/dev/vcs7'
Feb  7 12:45:07 localhost udev[3501]: creating device node '/dev/vcsa7'
Feb  7 12:45:07 localhost udev[3519]: removing device node '/dev/vcs7'
Feb  7 12:45:07 localhost udev[3529]: removing device node '/dev/vcsa7'
Feb  7 12:45:07 localhost udev[3391]: creating device node '/dev/vcs1'
Feb  7 12:45:07 localhost udev[3404]: creating device node '/dev/vcsa1'
Feb  7 12:45:07 localhost udev[3412]: creating device node '/dev/vcs2'
Feb  7 12:45:08 localhost udev[3420]: creating device node '/dev/vcs3'
Feb  7 12:45:08 localhost udev[3428]: creating device node '/dev/vcsa2'
Feb  7 12:45:08 localhost udev[3436]: creating device node '/dev/vcsa3'
Feb  7 12:45:08 localhost udev[3444]: creating device node '/dev/vcs4'
Feb  7 12:45:08 localhost udev[3452]: creating device node '/dev/vcsa4'
Feb  7 12:45:08 localhost udev[3460]: creating device node '/dev/vcs5'
Feb  7 12:45:08 localhost udev[3539]: creating device node '/dev/vcs7'
Feb  7 12:45:08 localhost udev[3547]: creating device node '/dev/vcsa7'
Feb  7 12:45:10 localhost kernel: eth0: no IPv6 routers present
Feb  7 12:45:27 localhost gconfd (rick-3630): starting (version 2.8.1), pid 3630 user 'rick'
Feb  7 12:45:27 localhost gconfd (rick-3630): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 12:45:27 localhost gconfd (rick-3630): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  7 12:45:27 localhost gconfd (rick-3630): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 12:45:38 localhost gconfd (rick-3630): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  7 13:05:01 localhost -- MARK --
Feb  7 13:07:41 localhost udev[4062]: removing device node '/dev/vcs7'
Feb  7 13:07:41 localhost udev[4072]: removing device node '/dev/vcsa7'
Feb  7 13:07:42 localhost gconfd (rick-3630): Received signal 15, shutting down cleanly
Feb  7 13:07:42 localhost gconfd (rick-3630): Exiting
Feb  7 13:07:42 localhost gdm[3382]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Feb  7 13:07:44 localhost udev[4083]: creating device node '/dev/vcs7'
Feb  7 13:07:44 localhost udev[4124]: removing device node '/dev/vcs7'
Feb  7 13:07:44 localhost udev[4091]: creating device node '/dev/vcsa7'
Feb  7 13:07:44 localhost udev[4130]: removing device node '/dev/vcsa7'
Feb  7 13:07:44 localhost udev[4127]: creating device node '/dev/vcs7'
Feb  7 13:07:44 localhost udev[4133]: creating device node '/dev/vcsa7'
Feb  7 13:11:15 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  7 13:11:15 localhost udev[2960]: creating device node '/dev/vcsa1'
Feb  7 13:11:15 localhost udev[2971]: removing device node '/dev/vcsa1'
Feb  7 13:11:15 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  7 13:11:15 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  7 13:11:15 localhost udev[2974]: creating device node '/dev/vcsa1'
Feb  7 13:11:15 localhost udev[2997]: removing device node '/dev/vcsa1'
Feb  7 13:11:15 localhost udev[3000]: creating device node '/dev/vcsa1'
Feb  7 13:11:15 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  7 13:11:15 localhost kernel: Symbols match kernel version 2.6.8.
Feb  7 13:11:15 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  7 13:11:15 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  7 13:11:15 localhost kernel: BIOS-provided physical RAM map:
Feb  7 13:11:15 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  7 13:11:15 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  7 13:11:15 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  7 13:11:15 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  7 13:11:15 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  7 13:11:15 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  7 13:11:15 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  7 13:11:15 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  7 13:11:15 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  7 13:11:15 localhost kernel: 767MB LOWMEM available.
Feb  7 13:11:15 localhost kernel: found SMP MP-table at 000f4d70
Feb  7 13:11:15 localhost kernel: On node 0 totalpages: 196592
Feb  7 13:11:15 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  7 13:11:15 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  7 13:11:15 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  7 13:11:15 localhost kernel: DMI 2.3 present.
Feb  7 13:11:15 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  7 13:11:15 localhost kernel:     Virtual Wire compatibility mode.
Feb  7 13:11:15 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  7 13:11:15 localhost kernel: Processor #0 6:8 APIC version 17
Feb  7 13:11:15 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  7 13:11:15 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  7 13:11:15 localhost kernel: Processors: 1
Feb  7 13:11:15 localhost kernel: Built 1 zonelists
Feb  7 13:11:15 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  7 13:11:15 localhost kernel: Initializing CPU#0
Feb  7 13:11:15 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  7 13:11:15 localhost kernel: Detected 1675.682 MHz processor.
Feb  7 13:11:15 localhost kernel: Using tsc for high-res timesource
Feb  7 13:11:15 localhost kernel: Console: colour VGA+ 80x25
Feb  7 13:11:15 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  7 13:11:15 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  7 13:11:15 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  7 13:11:15 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  7 13:11:15 localhost kernel: Calibrating delay loop... 3301.37 BogoMIPS
Feb  7 13:11:15 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  7 13:11:15 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  7 13:11:15 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  7 13:11:15 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  7 13:11:15 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  7 13:11:15 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  7 13:11:15 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  7 13:11:15 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  7 13:11:15 localhost kernel: Enabling fast FPU save and restore... done.
Feb  7 13:11:15 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  7 13:11:15 localhost kernel: Checking 'hlt' instruction... OK.
Feb  7 13:11:15 localhost kernel: Checking for popad bug... OK.
Feb  7 13:11:15 localhost kernel: enabled ExtINT on CPU#0
Feb  7 13:11:15 localhost kernel: ESR value before enabling vector: 00000000

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 13:11:15 localhost kernel: ESR value after enabling vector: 00000000
Feb  7 13:11:15 localhost kernel: ENABLING IO-APIC IRQs
Feb  7 13:11:15 localhost kernel: Setting 2 in the phys_id_present_map
Feb  7 13:11:15 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  7 13:11:15 localhost kernel: init IO_APIC IRQs
Feb  7 13:11:15 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  7 13:11:15 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  7 13:11:15 localhost kernel: number of MP IRQ sources: 20.
Feb  7 13:11:15 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  7 13:11:15 localhost kernel: testing the IO APIC.......................
Feb  7 13:11:15 localhost kernel: IO APIC #2......
Feb  7 13:11:15 localhost kernel: .... register #00: 02000000
Feb  7 13:11:15 localhost kernel: .......    : physical APIC id: 02
Feb  7 13:11:15 localhost kernel: .......    : Delivery Type: 0
Feb  7 13:11:15 localhost kernel: .......    : LTS          : 0
Feb  7 13:11:15 localhost kernel: .... register #01: 00178003
Feb  7 13:11:15 localhost kernel: .......     : max redirection entries: 0017
Feb  7 13:11:15 localhost kernel: .......     : PRQ implemented: 1
Feb  7 13:11:15 localhost kernel: .......     : IO APIC version: 0003
Feb  7 13:11:15 localhost kernel: .... IRQ redirection table:
Feb  7 13:11:15 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  7 13:11:15 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  7 13:11:15 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  7 13:11:15 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  7 13:11:15 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  7 13:11:15 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  7 13:11:15 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  7 13:11:15 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  7 13:11:15 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  7 13:11:15 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  7 13:11:15 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  7 13:11:15 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  7 13:11:15 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  7 13:11:15 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  7 13:11:15 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  7 13:11:15 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  7 13:11:15 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  7 13:11:15 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  7 13:11:15 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  7 13:11:15 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  7 13:11:16 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  7 13:11:16 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  7 13:11:16 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  7 13:11:16 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  7 13:11:16 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  7 13:11:16 localhost kernel: Using vector-based indexing
Feb  7 13:11:16 localhost kernel: IRQ to pin mappings:
Feb  7 13:11:16 localhost kernel: IRQ0 -> 0:2
Feb  7 13:11:16 localhost kernel: IRQ1 -> 0:1
Feb  7 13:11:16 localhost kernel: IRQ3 -> 0:3
Feb  7 13:11:16 localhost kernel: IRQ4 -> 0:4
Feb  7 13:11:16 localhost kernel: IRQ6 -> 0:6
Feb  7 13:11:16 localhost kernel: IRQ7 -> 0:7
Feb  7 13:11:16 localhost kernel: IRQ8 -> 0:8
Feb  7 13:11:16 localhost kernel: IRQ9 -> 0:9
Feb  7 13:11:16 localhost kernel: IRQ12 -> 0:12
Feb  7 13:11:16 localhost kernel: IRQ13 -> 0:13
Feb  7 13:11:16 localhost kernel: IRQ14 -> 0:14
Feb  7 13:11:16 localhost kernel: IRQ15 -> 0:15
Feb  7 13:11:16 localhost kernel: IRQ145 -> 0:16
Feb  7 13:11:16 localhost kernel: IRQ153 -> 0:21
Feb  7 13:11:16 localhost kernel: IRQ161 -> 0:22
Feb  7 13:11:16 localhost kernel: IRQ169 -> 0:23
Feb  7 13:11:16 localhost kernel: .................................... done.
Feb  7 13:11:16 localhost kernel: Using local APIC timer interrupts.
Feb  7 13:11:16 localhost kernel: calibrating APIC timer ...
Feb  7 13:11:16 localhost kernel: ..... CPU clock speed is 1674.0839 MHz.
Feb  7 13:11:16 localhost kernel: ..... host bus clock speed is 267.0974 MHz.
Feb  7 13:11:16 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  7 13:11:16 localhost kernel: Freeing initrd memory: 4136k freed
Feb  7 13:11:16 localhost kernel: NET: Registered protocol family 16
Feb  7 13:11:16 localhost kernel: EISA bus registered
Feb  7 13:11:16 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  7 13:11:16 localhost kernel: PCI: Using configuration type 1
Feb  7 13:11:16 localhost kernel: mtrr: v2.0 (20020519)
Feb  7 13:11:16 localhost kernel: ACPI: Subsystem revision 20040816
Feb  7 13:11:16 localhost kernel: ACPI: Interpreter disabled.
Feb  7 13:11:16 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  7 13:11:16 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  7 13:11:16 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  7 13:11:16 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  7 13:11:16 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  7 13:11:16 localhost kernel: PCI: Probing PCI hardware
Feb  7 13:11:16 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  7 13:11:16 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  7 13:11:16 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  7 13:11:16 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  7 13:11:16 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  7 13:11:16 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  7 13:11:16 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  7 13:11:16 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  7 13:11:16 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  7 13:11:16 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  7 13:11:16 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  7 13:11:16 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  7 13:11:16 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  7 13:11:16 localhost kernel: devfs: boot_options: 0x0
Feb  7 13:11:16 localhost kernel: Initializing Cryptographic API
Feb  7 13:11:16 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  7 13:11:16 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  7 13:11:16 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  7 13:11:16 localhost kernel: isapnp: Scanning for PnP cards...
Feb  7 13:11:16 localhost kernel: isapnp: No Plug & Play device found
Feb  7 13:11:16 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  7 13:11:16 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  7 13:11:16 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  7 13:11:16 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  7 13:11:16 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  7 13:11:16 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  7 13:11:16 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  7 13:11:16 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  7 13:11:16 localhost kernel: EISA: Detected 0 cards.
Feb  7 13:11:16 localhost kernel: NET: Registered protocol family 2
Feb  7 13:11:16 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  7 13:11:16 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  7 13:11:16 localhost kernel: NET: Registered protocol family 8
Feb  7 13:11:16 localhost kernel: NET: Registered protocol family 20
Feb  7 13:11:16 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  7 13:11:16 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  7 13:11:16 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  7 13:11:16 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  7 13:11:16 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  7 13:11:16 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  7 13:11:16 localhost kernel: NET: Registered protocol family 1
Feb  7 13:11:16 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  7 13:11:16 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  7 13:11:16 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  7 13:11:16 localhost kernel: VP_IDE: chipset revision 6
Feb  7 13:11:16 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  7 13:11:16 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  7 13:11:16 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  7 13:11:16 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  7 13:11:16 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  7 13:11:16 localhost kernel: Using anticipatory io scheduler
Feb  7 13:11:16 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  7 13:11:16 localhost kernel: hda: max request size: 1024KiB
Feb  7 13:11:16 localhost kernel: hda: Host Protected Area detected.
Feb  7 13:11:16 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  7 13:11:16 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  7 13:11:16 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  7 13:11:16 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  7 13:11:16 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  7 13:11:16 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  7 13:11:16 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  7 13:11:16 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Feb  7 13:11:16 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  7 13:11:16 localhost kernel: EXT3-fs: recovery complete.
Feb  7 13:11:16 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  7 13:11:16 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  7 13:11:16 localhost kernel: EXT3 FS on hda1, internal journal
Feb  7 13:11:16 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  7 13:11:16 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  7 13:11:16 localhost kernel: ts: Compaq touchscreen protocol output
Feb  7 13:11:16 localhost kernel: hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  7 13:11:16 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  7 13:11:16 localhost kernel: parport: PnPBIOS parport detected.
Feb  7 13:11:16 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  7 13:11:16 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  7 13:11:16 localhost kernel: Capability LSM initialized
Feb  7 13:11:16 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  7 13:11:16 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  7 13:11:16 localhost kernel: cdrom: open failed.
Feb  7 13:11:16 localhost kernel: Real Time Clock Driver v1.12
Feb  7 13:11:16 localhost kernel: input: PC Speaker
Feb  7 13:11:16 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  7 13:11:16 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  7 13:11:16 localhost kernel: FDC 0 is a post-1991 82077
Feb  7 13:11:16 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  7 13:11:16 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  7 13:11:16 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  7 13:11:16 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  7 13:11:16 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  7 13:11:16 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  7 13:11:16 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  7 13:11:16 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  7 13:11:16 localhost kernel: usbcore: registered new driver usbfs
Feb  7 13:11:16 localhost kernel: usbcore: registered new driver hub
Feb  7 13:11:16 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  7 13:11:16 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  7 13:11:16 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  7 13:11:16 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  7 13:11:16 localhost kernel: hub 1-0:1.0: USB hub found
Feb  7 13:11:16 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  7 13:11:16 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  7 13:11:16 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  7 13:11:16 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  7 13:11:16 localhost kernel: hub 2-0:1.0: USB hub found
Feb  7 13:11:16 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  7 13:11:16 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  7 13:11:16 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  7 13:11:16 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  7 13:11:16 localhost kernel: hub 3-0:1.0: USB hub found
Feb  7 13:11:16 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  7 13:11:16 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  7 13:11:16 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f08a4000
Feb  7 13:11:16 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  7 13:11:16 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  7 13:11:16 localhost kernel: hub 4-0:1.0: USB hub found
Feb  7 13:11:16 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  7 13:11:16 localhost kernel: irda_init()

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 13:11:16 localhost kernel: NET: Registered protocol family 23
Feb  7 13:11:16 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  7 13:11:16 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  7 13:11:16 localhost kernel:          and report if it works on your machine.
Feb  7 13:11:16 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  7 13:11:16 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  7 13:11:16 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  7 13:11:16 localhost kernel: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Feb  7 13:11:16 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  7 13:11:16 localhost kernel: NET: Registered protocol family 17
Feb  7 13:11:16 localhost kernel: NET: Registered protocol family 10
Feb  7 13:11:16 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  7 13:11:16 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  7 13:11:16 localhost udev[2884]: creating device node '/dev/vcs1'
Feb  7 13:11:16 localhost udev[3039]: removing device node '/dev/vcs1'
Feb  7 13:11:16 localhost udev[3042]: creating device node '/dev/vcs1'
Feb  7 13:11:16 localhost udev[3046]: removing device node '/dev/vcs1'
Feb  7 13:11:16 localhost udev[3049]: creating device node '/dev/vcs1'
Feb  7 13:11:16 localhost udev[3052]: removing device node '/dev/vcs1'
Feb  7 13:11:16 localhost udev[3055]: creating device node '/dev/vcs1'
Feb  7 13:11:19 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 13:11:19 localhost postfix/master[3251]: daemon started -- version 2.1.3
Feb  7 13:11:19 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  7 13:11:19 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  7 13:11:19 localhost /usr/sbin/cron[3324]: (CRON) INFO (pidfile fd = 3)
Feb  7 13:11:19 localhost /usr/sbin/cron[3325]: (CRON) STARTUP (fork ok)
Feb  7 13:11:19 localhost /usr/sbin/cron[3325]: (CRON) INFO (Running @reboot jobs)
Feb  7 13:11:20 localhost udev[3398]: removing device node '/dev/vcs1'
Feb  7 13:11:20 localhost udev[3463]: removing device node '/dev/vcsa1'
Feb  7 13:11:20 localhost udev[3466]: creating device node '/dev/vcs1'
Feb  7 13:11:20 localhost udev[3467]: creating device node '/dev/vcsa1'
Feb  7 13:11:20 localhost udev[3474]: creating device node '/dev/vcs2'
Feb  7 13:11:20 localhost udev[3475]: creating device node '/dev/vcs3'
Feb  7 13:11:20 localhost udev[3476]: creating device node '/dev/vcs4'
Feb  7 13:11:20 localhost udev[3477]: creating device node '/dev/vcs5'
Feb  7 13:11:21 localhost udev[3478]: creating device node '/dev/vcs6'
Feb  7 13:11:21 localhost udev[3491]: creating device node '/dev/vcsa3'
Feb  7 13:11:21 localhost udev[3479]: creating device node '/dev/vcsa2'
Feb  7 13:11:21 localhost udev[3492]: creating device node '/dev/vcsa4'
Feb  7 13:11:21 localhost udev[3494]: creating device node '/dev/vcsa5'
Feb  7 13:11:21 localhost udev[3495]: creating device node '/dev/vcsa6'
Feb  7 13:11:21 localhost udev[3500]: creating device node '/dev/vcs7'
Feb  7 13:11:21 localhost udev[3501]: creating device node '/dev/vcsa7'
Feb  7 13:11:21 localhost udev[3544]: removing device node '/dev/vcs7'
Feb  7 13:11:21 localhost udev[3547]: removing device node '/dev/vcsa7'
Feb  7 13:11:21 localhost udev[3558]: creating device node '/dev/vcs7'
Feb  7 13:11:21 localhost udev[3565]: creating device node '/dev/vcsa7'
Feb  7 13:11:23 localhost kernel: eth0: no IPv6 routers present
Feb  7 13:13:50 localhost gconfd (rick-3630): starting (version 2.8.1), pid 3630 user 'rick'
Feb  7 13:13:50 localhost gconfd (rick-3630): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 13:13:50 localhost gconfd (rick-3630): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  7 13:13:50 localhost gconfd (rick-3630): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 13:14:01 localhost gconfd (rick-3630): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  7 13:17:01 localhost /USR/SBIN/CRON[3801]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  7 13:31:15 localhost -- MARK --
Feb  7 14:02:13 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  7 14:02:13 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  7 14:02:13 localhost udev[2974]: creating device node '/dev/vcs1'
Feb  7 14:02:13 localhost udev[3003]: removing device node '/dev/vcs1'
Feb  7 14:02:13 localhost udev[2980]: creating device node '/dev/vcsa1'
Feb  7 14:02:13 localhost udev[3009]: removing device node '/dev/vcsa1'
Feb  7 14:02:14 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  7 14:02:14 localhost udev[3006]: creating device node '/dev/vcs1'
Feb  7 14:02:14 localhost udev[3026]: removing device node '/dev/vcs1'
Feb  7 14:02:14 localhost udev[3012]: creating device node '/dev/vcsa1'
Feb  7 14:02:14 localhost udev[3032]: removing device node '/dev/vcsa1'
Feb  7 14:02:14 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  7 14:02:14 localhost kernel: Symbols match kernel version 2.6.8.
Feb  7 14:02:14 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  7 14:02:14 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  7 14:02:14 localhost kernel: BIOS-provided physical RAM map:
Feb  7 14:02:14 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  7 14:02:14 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  7 14:02:14 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  7 14:02:14 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  7 14:02:14 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  7 14:02:14 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  7 14:02:14 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  7 14:02:14 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  7 14:02:14 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  7 14:02:14 localhost kernel: 767MB LOWMEM available.
Feb  7 14:02:14 localhost kernel: found SMP MP-table at 000f4d70
Feb  7 14:02:14 localhost kernel: On node 0 totalpages: 196592
Feb  7 14:02:14 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  7 14:02:14 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  7 14:02:14 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  7 14:02:14 localhost kernel: DMI 2.3 present.
Feb  7 14:02:14 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  7 14:02:14 localhost kernel:     Virtual Wire compatibility mode.
Feb  7 14:02:14 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  7 14:02:14 localhost kernel: Processor #0 6:8 APIC version 17
Feb  7 14:02:14 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  7 14:02:14 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  7 14:02:14 localhost kernel: Processors: 1
Feb  7 14:02:14 localhost kernel: Built 1 zonelists
Feb  7 14:02:14 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  7 14:02:14 localhost kernel: Initializing CPU#0
Feb  7 14:02:14 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  7 14:02:14 localhost kernel: Detected 1675.772 MHz processor.
Feb  7 14:02:14 localhost kernel: Using tsc for high-res timesource
Feb  7 14:02:14 localhost kernel: Console: colour VGA+ 80x25
Feb  7 14:02:14 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  7 14:02:14 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  7 14:02:14 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  7 14:02:14 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  7 14:02:14 localhost kernel: Calibrating delay loop... 3301.37 BogoMIPS
Feb  7 14:02:14 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  7 14:02:14 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  7 14:02:14 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  7 14:02:14 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  7 14:02:14 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  7 14:02:14 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  7 14:02:14 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  7 14:02:14 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  7 14:02:14 localhost kernel: Enabling fast FPU save and restore... done.
Feb  7 14:02:14 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  7 14:02:14 localhost kernel: Checking 'hlt' instruction... OK.
Feb  7 14:02:14 localhost kernel: Checking for popad bug... OK.
Feb  7 14:02:14 localhost kernel: enabled ExtINT on CPU#0
Feb  7 14:02:14 localhost kernel: ESR value before enabling vector: 00000000
Feb  7 14:02:14 localhost kernel: ESR value after enabling vector: 00000000
Feb  7 14:02:14 localhost kernel: ENABLING IO-APIC IRQs
Feb  7 14:02:14 localhost kernel: Setting 2 in the phys_id_present_map
Feb  7 14:02:14 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  7 14:02:14 localhost kernel: init IO_APIC IRQs
Feb  7 14:02:14 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  7 14:02:14 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  7 14:02:14 localhost kernel: number of MP IRQ sources: 20.
Feb  7 14:02:14 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  7 14:02:14 localhost kernel: testing the IO APIC.......................
Feb  7 14:02:14 localhost kernel: IO APIC #2......
Feb  7 14:02:14 localhost kernel: .... register #00: 02000000
Feb  7 14:02:14 localhost kernel: .......    : physical APIC id: 02
Feb  7 14:02:14 localhost kernel: .......    : Delivery Type: 0
Feb  7 14:02:14 localhost kernel: .......    : LTS          : 0
Feb  7 14:02:14 localhost kernel: .... register #01: 00178003
Feb  7 14:02:14 localhost kernel: .......     : max redirection entries: 0017
Feb  7 14:02:14 localhost kernel: .......     : PRQ implemented: 1
Feb  7 14:02:14 localhost kernel: .......     : IO APIC version: 0003
Feb  7 14:02:14 localhost kernel: .... IRQ redirection table:
Feb  7 14:02:14 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  7 14:02:14 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  7 14:02:14 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  7 14:02:14 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  7 14:02:14 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  7 14:02:14 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  7 14:02:14 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  7 14:02:14 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  7 14:02:14 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  7 14:02:14 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  7 14:02:14 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  7 14:02:14 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  7 14:02:14 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  7 14:02:14 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  7 14:02:14 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  7 14:02:14 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  7 14:02:14 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  7 14:02:14 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  7 14:02:14 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  7 14:02:14 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  7 14:02:14 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  7 14:02:14 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  7 14:02:14 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  7 14:02:14 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  7 14:02:14 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  7 14:02:14 localhost kernel: Using vector-based indexing
Feb  7 14:02:14 localhost kernel: IRQ to pin mappings:
Feb  7 14:02:14 localhost kernel: IRQ0 -> 0:2
Feb  7 14:02:14 localhost kernel: IRQ1 -> 0:1
Feb  7 14:02:14 localhost kernel: IRQ3 -> 0:3
Feb  7 14:02:14 localhost kernel: IRQ4 -> 0:4
Feb  7 14:02:14 localhost kernel: IRQ6 -> 0:6
Feb  7 14:02:14 localhost kernel: IRQ7 -> 0:7
Feb  7 14:02:14 localhost kernel: IRQ8 -> 0:8
Feb  7 14:02:14 localhost kernel: IRQ9 -> 0:9
Feb  7 14:02:14 localhost kernel: IRQ12 -> 0:12
Feb  7 14:02:14 localhost kernel: IRQ13 -> 0:13
Feb  7 14:02:14 localhost kernel: IRQ14 -> 0:14
Feb  7 14:02:14 localhost kernel: IRQ15 -> 0:15
Feb  7 14:02:14 localhost kernel: IRQ145 -> 0:16
Feb  7 14:02:14 localhost kernel: IRQ153 -> 0:21
Feb  7 14:02:14 localhost kernel: IRQ161 -> 0:22
Feb  7 14:02:14 localhost kernel: IRQ169 -> 0:23
Feb  7 14:02:14 localhost kernel: .................................... done.
Feb  7 14:02:14 localhost kernel: Using local APIC timer interrupts.
Feb  7 14:02:14 localhost kernel: calibrating APIC timer ...
Feb  7 14:02:14 localhost kernel: ..... CPU clock speed is 1674.0839 MHz.
Feb  7 14:02:14 localhost kernel: ..... host bus clock speed is 267.0974 MHz.
Feb  7 14:02:14 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  7 14:02:14 localhost kernel: Freeing initrd memory: 4136k freed
Feb  7 14:02:14 localhost kernel: NET: Registered protocol family 16
Feb  7 14:02:14 localhost kernel: EISA bus registered
Feb  7 14:02:14 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  7 14:02:14 localhost kernel: PCI: Using configuration type 1
Feb  7 14:02:14 localhost kernel: mtrr: v2.0 (20020519)
Feb  7 14:02:14 localhost kernel: ACPI: Subsystem revision 20040816
Feb  7 14:02:14 localhost kernel: ACPI: Interpreter disabled.
Feb  7 14:02:14 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  7 14:02:14 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  7 14:02:14 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 14:02:14 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  7 14:02:14 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  7 14:02:14 localhost kernel: PCI: Probing PCI hardware
Feb  7 14:02:14 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  7 14:02:14 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  7 14:02:14 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  7 14:02:14 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  7 14:02:14 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  7 14:02:14 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  7 14:02:14 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  7 14:02:14 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  7 14:02:14 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  7 14:02:14 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  7 14:02:14 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  7 14:02:14 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  7 14:02:14 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  7 14:02:14 localhost kernel: devfs: boot_options: 0x0
Feb  7 14:02:14 localhost kernel: Initializing Cryptographic API
Feb  7 14:02:14 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  7 14:02:14 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  7 14:02:14 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  7 14:02:14 localhost kernel: isapnp: Scanning for PnP cards...
Feb  7 14:02:14 localhost kernel: isapnp: No Plug & Play device found
Feb  7 14:02:14 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  7 14:02:14 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  7 14:02:14 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  7 14:02:14 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  7 14:02:14 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  7 14:02:14 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  7 14:02:14 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  7 14:02:14 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  7 14:02:14 localhost kernel: EISA: Detected 0 cards.
Feb  7 14:02:14 localhost kernel: NET: Registered protocol family 2
Feb  7 14:02:14 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  7 14:02:14 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  7 14:02:14 localhost kernel: NET: Registered protocol family 8
Feb  7 14:02:14 localhost kernel: NET: Registered protocol family 20
Feb  7 14:02:14 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  7 14:02:14 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  7 14:02:14 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  7 14:02:14 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  7 14:02:14 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  7 14:02:14 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  7 14:02:14 localhost kernel: NET: Registered protocol family 1
Feb  7 14:02:14 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  7 14:02:14 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  7 14:02:14 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  7 14:02:14 localhost kernel: VP_IDE: chipset revision 6
Feb  7 14:02:14 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  7 14:02:14 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  7 14:02:14 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  7 14:02:14 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  7 14:02:14 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  7 14:02:14 localhost kernel: Using anticipatory io scheduler
Feb  7 14:02:14 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  7 14:02:14 localhost kernel: hda: max request size: 1024KiB
Feb  7 14:02:14 localhost kernel: hda: Host Protected Area detected.
Feb  7 14:02:14 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  7 14:02:14 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  7 14:02:14 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  7 14:02:14 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  7 14:02:14 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  7 14:02:14 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  7 14:02:14 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  7 14:02:14 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Feb  7 14:02:14 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  7 14:02:14 localhost kernel: EXT3-fs: hda1: orphan cleanup on readonly fs
Feb  7 14:02:14 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881318
Feb  7 14:02:14 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881315
Feb  7 14:02:14 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881312
Feb  7 14:02:14 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881309
Feb  7 14:02:14 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881305
Feb  7 14:02:14 localhost kernel: EXT3-fs: hda1: 5 orphan inodes deleted
Feb  7 14:02:14 localhost kernel: EXT3-fs: recovery complete.
Feb  7 14:02:14 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  7 14:02:14 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  7 14:02:14 localhost kernel: EXT3 FS on hda1, internal journal
Feb  7 14:02:14 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  7 14:02:14 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  7 14:02:14 localhost kernel: hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  7 14:02:14 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  7 14:02:14 localhost kernel: ts: Compaq touchscreen protocol output
Feb  7 14:02:14 localhost kernel: parport: PnPBIOS parport detected.
Feb  7 14:02:14 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  7 14:02:14 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  7 14:02:14 localhost kernel: Capability LSM initialized
Feb  7 14:02:14 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  7 14:02:14 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  7 14:02:14 localhost kernel: cdrom: open failed.
Feb  7 14:02:14 localhost kernel: Real Time Clock Driver v1.12
Feb  7 14:02:14 localhost kernel: input: PC Speaker
Feb  7 14:02:14 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  7 14:02:14 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  7 14:02:14 localhost kernel: FDC 0 is a post-1991 82077
Feb  7 14:02:14 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  7 14:02:14 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  7 14:02:14 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  7 14:02:14 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  7 14:02:14 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  7 14:02:14 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  7 14:02:14 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  7 14:02:14 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  7 14:02:14 localhost kernel: usbcore: registered new driver usbfs
Feb  7 14:02:14 localhost kernel: usbcore: registered new driver hub
Feb  7 14:02:14 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  7 14:02:14 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  7 14:02:14 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  7 14:02:14 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  7 14:02:14 localhost kernel: hub 1-0:1.0: USB hub found
Feb  7 14:02:14 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  7 14:02:14 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  7 14:02:14 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  7 14:02:14 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  7 14:02:14 localhost kernel: hub 2-0:1.0: USB hub found
Feb  7 14:02:14 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  7 14:02:14 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  7 14:02:14 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  7 14:02:14 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  7 14:02:14 localhost kernel: hub 3-0:1.0: USB hub found
Feb  7 14:02:14 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  7 14:02:14 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  7 14:02:14 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f093b000
Feb  7 14:02:14 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  7 14:02:14 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  7 14:02:14 localhost kernel: hub 4-0:1.0: USB hub found
Feb  7 14:02:14 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  7 14:02:14 localhost kernel: irda_init()
Feb  7 14:02:14 localhost kernel: NET: Registered protocol family 23
Feb  7 14:02:14 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  7 14:02:14 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  7 14:02:14 localhost kernel:          and report if it works on your machine.
Feb  7 14:02:14 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  7 14:02:14 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  7 14:02:14 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  7 14:02:14 localhost kernel: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Feb  7 14:02:14 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  7 14:02:14 localhost kernel: NET: Registered protocol family 17
Feb  7 14:02:14 localhost kernel: NET: Registered protocol family 10
Feb  7 14:02:14 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  7 14:02:14 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  7 14:02:14 localhost udev[3029]: creating device node '/dev/vcs1'
Feb  7 14:02:14 localhost udev[3035]: creating device node '/dev/vcsa1'
Feb  7 14:02:17 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 14:02:17 localhost postfix/master[3257]: daemon started -- version 2.1.3
Feb  7 14:02:17 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  7 14:02:17 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  7 14:02:17 localhost /usr/sbin/cron[3330]: (CRON) INFO (pidfile fd = 3)
Feb  7 14:02:17 localhost /usr/sbin/cron[3331]: (CRON) STARTUP (fork ok)
Feb  7 14:02:17 localhost /usr/sbin/cron[3331]: (CRON) INFO (Running @reboot jobs)
Feb  7 14:02:18 localhost udev[3375]: removing device node '/dev/vcs1'
Feb  7 14:02:18 localhost udev[3386]: removing device node '/dev/vcsa1'
Feb  7 14:02:19 localhost udev[3636]: creating device node '/dev/vcs7'
Feb  7 14:02:19 localhost udev[3637]: creating device node '/dev/vcsa7'
Feb  7 14:02:19 localhost udev[3658]: removing device node '/dev/vcs7'
Feb  7 14:02:19 localhost udev[3669]: removing device node '/dev/vcsa7'
Feb  7 14:02:19 localhost udev[3396]: creating device node '/dev/vcs1'
Feb  7 14:02:19 localhost udev[3410]: creating device node '/dev/vcsa1'
Feb  7 14:02:19 localhost udev[3687]: creating device node '/dev/vcsa7'
Feb  7 14:02:20 localhost udev[3418]: creating device node '/dev/vcs2'
Feb  7 14:02:20 localhost udev[3696]: removing device node '/dev/vcs2'
Feb  7 14:02:20 localhost udev[3426]: creating device node '/dev/vcsa2'
Feb  7 14:02:20 localhost udev[3702]: removing device node '/dev/vcsa2'
Feb  7 14:02:20 localhost udev[3434]: creating device node '/dev/vcs3'
Feb  7 14:02:20 localhost udev[3708]: removing device node '/dev/vcs3'
Feb  7 14:02:20 localhost udev[3442]: creating device node '/dev/vcsa3'
Feb  7 14:02:20 localhost udev[3714]: removing device node '/dev/vcsa3'
Feb  7 14:02:20 localhost udev[3450]: creating device node '/dev/vcs4'
Feb  7 14:02:20 localhost udev[3720]: removing device node '/dev/vcs4'
Feb  7 14:02:20 localhost udev[3458]: creating device node '/dev/vcsa4'
Feb  7 14:02:20 localhost udev[3726]: removing device node '/dev/vcsa4'
Feb  7 14:02:20 localhost udev[3466]: creating device node '/dev/vcs5'
Feb  7 14:02:20 localhost udev[3732]: removing device node '/dev/vcs5'
Feb  7 14:02:20 localhost udev[3474]: creating device node '/dev/vcsa5'
Feb  7 14:02:20 localhost udev[3738]: removing device node '/dev/vcsa5'
Feb  7 14:02:20 localhost udev[3699]: creating device node '/dev/vcs2'
Feb  7 14:02:20 localhost udev[3705]: creating device node '/dev/vcsa2'
Feb  7 14:02:20 localhost udev[3711]: creating device node '/dev/vcs3'
Feb  7 14:02:20 localhost udev[3717]: creating device node '/dev/vcsa3'
Feb  7 14:02:20 localhost udev[3723]: creating device node '/dev/vcs4'
Feb  7 14:02:20 localhost udev[3729]: creating device node '/dev/vcsa4'
Feb  7 14:02:20 localhost udev[3735]: creating device node '/dev/vcs5'
Feb  7 14:02:20 localhost udev[3741]: creating device node '/dev/vcsa5'
Feb  7 14:02:20 localhost udev[3570]: creating device node '/dev/vcs6'
Feb  7 14:02:20 localhost udev[3571]: creating device node '/dev/vcsa6'
Feb  7 14:02:20 localhost udev[3762]: removing device node '/dev/vcsa6'
Feb  7 14:02:20 localhost udev[3766]: removing device node '/dev/vcs6'
Feb  7 14:02:20 localhost udev[3765]: creating device node '/dev/vcsa6'
Feb  7 14:02:20 localhost udev[3769]: creating device node '/dev/vcs6'
Feb  7 14:02:20 localhost udev[3679]: creating device node '/dev/vcs7'
Feb  7 14:02:22 localhost kernel: eth0: no IPv6 routers present
Feb  7 14:02:37 localhost gconfd (rick-3836): starting (version 2.8.1), pid 3836 user 'rick'
Feb  7 14:02:37 localhost gconfd (rick-3836): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 14:02:37 localhost gconfd (rick-3836): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  7 14:02:37 localhost gconfd (rick-3836): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 14:02:48 localhost gconfd (rick-3836): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  7 14:12:07 localhost gconfd (root-4100): starting (version 2.8.1), pid 4100 user 'root'
Feb  7 14:12:07 localhost gconfd (root-4100): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 14:12:07 localhost gconfd (root-4100): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb  7 14:12:07 localhost gconfd (root-4100): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 14:15:24 localhost shutdown[4180]: shutting down for system reboot

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 14:15:24 localhost init: Switching to runlevel: 6
Feb  7 14:15:24 localhost udev[4252]: removing device node '/dev/vcs2'
Feb  7 14:15:24 localhost udev[4255]: removing device node '/dev/vcsa2'
Feb  7 14:15:24 localhost udev[4258]: removing device node '/dev/vcs3'
Feb  7 14:15:24 localhost udev[4261]: removing device node '/dev/vcsa3'
Feb  7 14:15:24 localhost udev[4264]: removing device node '/dev/vcs4'
Feb  7 14:15:24 localhost udev[4267]: removing device node '/dev/vcsa4'
Feb  7 14:15:24 localhost udev[4269]: removing device node '/dev/vcs5'
Feb  7 14:15:24 localhost udev[4274]: removing device node '/dev/vcs6'
Feb  7 14:15:24 localhost udev[4276]: removing device node '/dev/vcsa6'
Feb  7 14:15:24 localhost udev[4270]: removing device node '/dev/vcsa5'
Feb  7 14:15:25 localhost gconfd (rick-3836): Received signal 15, shutting down cleanly
Feb  7 14:15:25 localhost gconfd (rick-3836): Exiting
Feb  7 14:15:25 localhost udev[4296]: removing device node '/dev/vcs1'
Feb  7 14:15:26 localhost udev[4415]: removing device node '/dev/vcsa1'
Feb  7 14:15:27 localhost postfix/postfix-script: stopping the Postfix mail system
Feb  7 14:15:27 localhost postfix/master[3257]: terminating on signal 15
Feb  7 14:15:28 localhost udev[4418]: creating device node '/dev/vcs1'
Feb  7 14:15:28 localhost udev[4419]: creating device node '/dev/vcsa1'
Feb  7 14:15:28 localhost udev[5103]: removing device node '/dev/vcs1'
Feb  7 14:15:28 localhost udev[5108]: removing device node '/dev/vcsa1'
Feb  7 14:15:28 localhost udev[5111]: creating device node '/dev/vcsa1'
Feb  7 14:15:28 localhost udev[5161]: removing device node '/dev/vcsa1'
Feb  7 14:15:28 localhost kernel: Kernel logging (proc) stopped.
Feb  7 14:15:28 localhost kernel: Kernel log daemon terminating.
Feb  7 14:15:28 localhost exiting on signal 15
Feb  7 15:38:52 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  7 15:38:52 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  7 15:38:52 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  7 15:38:53 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  7 15:38:53 localhost kernel: Symbols match kernel version 2.6.8.
Feb  7 15:38:53 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  7 15:38:53 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  7 15:38:53 localhost kernel: BIOS-provided physical RAM map:
Feb  7 15:38:53 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  7 15:38:53 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  7 15:38:53 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  7 15:38:53 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  7 15:38:53 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  7 15:38:53 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  7 15:38:53 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  7 15:38:53 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  7 15:38:53 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  7 15:38:53 localhost kernel: 767MB LOWMEM available.
Feb  7 15:38:53 localhost kernel: found SMP MP-table at 000f4d70
Feb  7 15:38:53 localhost kernel: On node 0 totalpages: 196592
Feb  7 15:38:53 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  7 15:38:53 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  7 15:38:53 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  7 15:38:53 localhost kernel: DMI 2.3 present.
Feb  7 15:38:53 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  7 15:38:53 localhost kernel:     Virtual Wire compatibility mode.
Feb  7 15:38:53 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  7 15:38:53 localhost kernel: Processor #0 6:8 APIC version 17
Feb  7 15:38:53 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  7 15:38:53 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  7 15:38:53 localhost kernel: Processors: 1
Feb  7 15:38:53 localhost kernel: Built 1 zonelists
Feb  7 15:38:53 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  7 15:38:53 localhost kernel: Initializing CPU#0
Feb  7 15:38:53 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  7 15:38:53 localhost kernel: Detected 1675.772 MHz processor.
Feb  7 15:38:53 localhost kernel: Using tsc for high-res timesource
Feb  7 15:38:53 localhost kernel: Console: colour VGA+ 80x25
Feb  7 15:38:53 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  7 15:38:53 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  7 15:38:53 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  7 15:38:53 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  7 15:38:53 localhost kernel: Calibrating delay loop... 3301.37 BogoMIPS
Feb  7 15:38:53 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  7 15:38:53 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  7 15:38:53 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  7 15:38:53 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  7 15:38:53 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  7 15:38:53 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  7 15:38:53 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  7 15:38:53 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  7 15:38:53 localhost kernel: Enabling fast FPU save and restore... done.
Feb  7 15:38:53 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  7 15:38:53 localhost kernel: Checking 'hlt' instruction... OK.
Feb  7 15:38:53 localhost kernel: Checking for popad bug... OK.
Feb  7 15:38:53 localhost kernel: enabled ExtINT on CPU#0
Feb  7 15:38:53 localhost kernel: ESR value before enabling vector: 00000000
Feb  7 15:38:53 localhost kernel: ESR value after enabling vector: 00000000
Feb  7 15:38:53 localhost kernel: ENABLING IO-APIC IRQs
Feb  7 15:38:53 localhost kernel: Setting 2 in the phys_id_present_map
Feb  7 15:38:53 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  7 15:38:53 localhost kernel: init IO_APIC IRQs
Feb  7 15:38:53 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  7 15:38:53 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  7 15:38:53 localhost kernel: number of MP IRQ sources: 20.
Feb  7 15:38:53 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  7 15:38:53 localhost kernel: testing the IO APIC.......................
Feb  7 15:38:53 localhost kernel: IO APIC #2......
Feb  7 15:38:53 localhost kernel: .... register #00: 02000000
Feb  7 15:38:53 localhost kernel: .......    : physical APIC id: 02
Feb  7 15:38:53 localhost kernel: .......    : Delivery Type: 0
Feb  7 15:38:53 localhost kernel: .......    : LTS          : 0
Feb  7 15:38:53 localhost kernel: .... register #01: 00178003
Feb  7 15:38:53 localhost kernel: .......     : max redirection entries: 0017
Feb  7 15:38:53 localhost kernel: .......     : PRQ implemented: 1
Feb  7 15:38:53 localhost kernel: .......     : IO APIC version: 0003
Feb  7 15:38:53 localhost kernel: .... IRQ redirection table:
Feb  7 15:38:53 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  7 15:38:53 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  7 15:38:53 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  7 15:38:53 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  7 15:38:53 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  7 15:38:53 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  7 15:38:53 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  7 15:38:53 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  7 15:38:53 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  7 15:38:53 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  7 15:38:53 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  7 15:38:53 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  7 15:38:53 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  7 15:38:53 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  7 15:38:53 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  7 15:38:53 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  7 15:38:53 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  7 15:38:53 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  7 15:38:53 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  7 15:38:53 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  7 15:38:53 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  7 15:38:53 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  7 15:38:53 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  7 15:38:53 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  7 15:38:53 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  7 15:38:53 localhost kernel: Using vector-based indexing
Feb  7 15:38:53 localhost kernel: IRQ to pin mappings:
Feb  7 15:38:53 localhost kernel: IRQ0 -> 0:2
Feb  7 15:38:53 localhost kernel: IRQ1 -> 0:1
Feb  7 15:38:53 localhost kernel: IRQ3 -> 0:3
Feb  7 15:38:53 localhost kernel: IRQ4 -> 0:4
Feb  7 15:38:53 localhost kernel: IRQ6 -> 0:6
Feb  7 15:38:53 localhost kernel: IRQ7 -> 0:7
Feb  7 15:38:53 localhost kernel: IRQ8 -> 0:8
Feb  7 15:38:53 localhost kernel: IRQ9 -> 0:9
Feb  7 15:38:53 localhost kernel: IRQ12 -> 0:12
Feb  7 15:38:53 localhost kernel: IRQ13 -> 0:13
Feb  7 15:38:53 localhost kernel: IRQ14 -> 0:14
Feb  7 15:38:53 localhost kernel: IRQ15 -> 0:15
Feb  7 15:38:53 localhost kernel: IRQ145 -> 0:16
Feb  7 15:38:53 localhost kernel: IRQ153 -> 0:21
Feb  7 15:38:53 localhost kernel: IRQ161 -> 0:22
Feb  7 15:38:53 localhost kernel: IRQ169 -> 0:23
Feb  7 15:38:53 localhost kernel: .................................... done.
Feb  7 15:38:53 localhost kernel: Using local APIC timer interrupts.
Feb  7 15:38:53 localhost kernel: calibrating APIC timer ...
Feb  7 15:38:53 localhost kernel: ..... CPU clock speed is 1674.0844 MHz.
Feb  7 15:38:53 localhost kernel: ..... host bus clock speed is 267.0975 MHz.
Feb  7 15:38:53 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  7 15:38:53 localhost kernel: Freeing initrd memory: 4136k freed
Feb  7 15:38:53 localhost kernel: NET: Registered protocol family 16
Feb  7 15:38:53 localhost kernel: EISA bus registered
Feb  7 15:38:53 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  7 15:38:53 localhost kernel: PCI: Using configuration type 1
Feb  7 15:38:53 localhost kernel: mtrr: v2.0 (20020519)
Feb  7 15:38:53 localhost kernel: ACPI: Subsystem revision 20040816
Feb  7 15:38:53 localhost kernel: ACPI: Interpreter disabled.
Feb  7 15:38:53 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  7 15:38:53 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  7 15:38:53 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  7 15:38:53 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  7 15:38:53 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  7 15:38:53 localhost kernel: PCI: Probing PCI hardware
Feb  7 15:38:53 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  7 15:38:53 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  7 15:38:53 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  7 15:38:53 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  7 15:38:53 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  7 15:38:53 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  7 15:38:53 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  7 15:38:53 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  7 15:38:53 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  7 15:38:53 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  7 15:38:53 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  7 15:38:53 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  7 15:38:53 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  7 15:38:53 localhost kernel: devfs: boot_options: 0x0
Feb  7 15:38:53 localhost kernel: Initializing Cryptographic API
Feb  7 15:38:53 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  7 15:38:53 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  7 15:38:53 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  7 15:38:53 localhost kernel: isapnp: Scanning for PnP cards...
Feb  7 15:38:53 localhost kernel: isapnp: No Plug & Play device found
Feb  7 15:38:53 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  7 15:38:53 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  7 15:38:53 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  7 15:38:53 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  7 15:38:53 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  7 15:38:53 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  7 15:38:53 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  7 15:38:53 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  7 15:38:53 localhost kernel: EISA: Detected 0 cards.
Feb  7 15:38:53 localhost kernel: NET: Registered protocol family 2
Feb  7 15:38:53 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  7 15:38:53 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  7 15:38:53 localhost kernel: NET: Registered protocol family 8
Feb  7 15:38:53 localhost kernel: NET: Registered protocol family 20

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 15:38:53 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  7 15:38:53 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  7 15:38:53 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  7 15:38:53 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  7 15:38:53 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  7 15:38:53 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  7 15:38:53 localhost kernel: NET: Registered protocol family 1
Feb  7 15:38:53 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  7 15:38:53 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  7 15:38:53 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  7 15:38:53 localhost kernel: VP_IDE: chipset revision 6
Feb  7 15:38:53 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  7 15:38:53 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  7 15:38:53 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  7 15:38:53 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  7 15:38:53 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  7 15:38:53 localhost kernel: Using anticipatory io scheduler
Feb  7 15:38:53 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  7 15:38:53 localhost kernel: hda: max request size: 1024KiB
Feb  7 15:38:53 localhost kernel: hda: Host Protected Area detected.
Feb  7 15:38:53 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  7 15:38:53 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  7 15:38:53 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  7 15:38:53 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  7 15:38:53 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  7 15:38:53 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  7 15:38:53 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  7 15:38:53 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  7 15:38:53 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  7 15:38:53 localhost kernel: EXT3 FS on hda1, internal journal
Feb  7 15:38:53 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  7 15:38:53 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  7 15:38:53 localhost kernel: hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  7 15:38:53 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  7 15:38:53 localhost kernel: ts: Compaq touchscreen protocol output
Feb  7 15:38:53 localhost kernel: parport: PnPBIOS parport detected.
Feb  7 15:38:53 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  7 15:38:53 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  7 15:38:53 localhost kernel: Capability LSM initialized
Feb  7 15:38:53 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  7 15:38:53 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  7 15:38:53 localhost kernel: cdrom: open failed.
Feb  7 15:38:53 localhost kernel: Real Time Clock Driver v1.12
Feb  7 15:38:53 localhost kernel: input: PC Speaker
Feb  7 15:38:53 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  7 15:38:53 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  7 15:38:53 localhost kernel: FDC 0 is a post-1991 82077
Feb  7 15:38:53 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  7 15:38:53 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  7 15:38:53 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  7 15:38:53 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  7 15:38:53 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  7 15:38:53 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  7 15:38:53 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  7 15:38:53 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  7 15:38:53 localhost kernel: usbcore: registered new driver usbfs
Feb  7 15:38:53 localhost kernel: usbcore: registered new driver hub
Feb  7 15:38:53 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  7 15:38:53 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  7 15:38:53 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  7 15:38:53 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  7 15:38:53 localhost kernel: hub 1-0:1.0: USB hub found
Feb  7 15:38:53 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  7 15:38:53 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  7 15:38:53 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  7 15:38:53 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  7 15:38:53 localhost kernel: hub 2-0:1.0: USB hub found
Feb  7 15:38:53 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  7 15:38:53 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  7 15:38:53 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  7 15:38:53 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  7 15:38:53 localhost kernel: hub 3-0:1.0: USB hub found
Feb  7 15:38:53 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  7 15:38:53 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  7 15:38:53 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f093b000
Feb  7 15:38:53 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  7 15:38:53 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  7 15:38:53 localhost kernel: hub 4-0:1.0: USB hub found
Feb  7 15:38:53 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  7 15:38:53 localhost kernel: irda_init()
Feb  7 15:38:53 localhost kernel: NET: Registered protocol family 23
Feb  7 15:38:53 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  7 15:38:53 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  7 15:38:53 localhost kernel:          and report if it works on your machine.
Feb  7 15:38:53 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  7 15:38:53 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  7 15:38:53 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  7 15:38:53 localhost kernel: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Feb  7 15:38:53 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  7 15:38:53 localhost kernel: NET: Registered protocol family 17
Feb  7 15:38:53 localhost kernel: NET: Registered protocol family 10
Feb  7 15:38:53 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  7 15:38:53 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  7 15:38:53 localhost udev[2860]: creating device node '/dev/vcs1'
Feb  7 15:38:53 localhost udev[3016]: removing device node '/dev/vcs1'
Feb  7 15:38:53 localhost udev[2868]: creating device node '/dev/vcsa1'
Feb  7 15:38:53 localhost udev[3022]: removing device node '/dev/vcsa1'
Feb  7 15:38:53 localhost udev[3019]: creating device node '/dev/vcs1'
Feb  7 15:38:53 localhost udev[3029]: removing device node '/dev/vcs1'
Feb  7 15:38:53 localhost udev[3025]: creating device node '/dev/vcsa1'
Feb  7 15:38:53 localhost udev[3035]: removing device node '/dev/vcsa1'
Feb  7 15:38:53 localhost udev[3032]: creating device node '/dev/vcs1'
Feb  7 15:38:53 localhost udev[3041]: removing device node '/dev/vcs1'
Feb  7 15:38:53 localhost udev[3038]: creating device node '/dev/vcsa1'
Feb  7 15:38:53 localhost udev[3047]: removing device node '/dev/vcsa1'
Feb  7 15:38:54 localhost udev[3044]: creating device node '/dev/vcs1'
Feb  7 15:38:54 localhost udev[3050]: creating device node '/dev/vcsa1'
Feb  7 15:38:56 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 15:38:56 localhost postfix/master[3248]: daemon started -- version 2.1.3
Feb  7 15:38:56 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  7 15:38:56 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  7 15:38:56 localhost /usr/sbin/cron[3321]: (CRON) INFO (pidfile fd = 3)
Feb  7 15:38:56 localhost /usr/sbin/cron[3322]: (CRON) STARTUP (fork ok)
Feb  7 15:38:56 localhost /usr/sbin/cron[3322]: (CRON) INFO (Running @reboot jobs)
Feb  7 15:38:57 localhost udev[3366]: removing device node '/dev/vcs1'
Feb  7 15:38:57 localhost udev[3377]: removing device node '/dev/vcsa1'
Feb  7 15:38:58 localhost udev[3490]: creating device node '/dev/vcsa5'
Feb  7 15:38:58 localhost udev[3491]: creating device node '/dev/vcs6'
Feb  7 15:38:58 localhost udev[3496]: creating device node '/dev/vcs7'
Feb  7 15:38:58 localhost udev[3497]: creating device node '/dev/vcsa6'
Feb  7 15:38:58 localhost udev[3498]: creating device node '/dev/vcsa7'
Feb  7 15:38:58 localhost udev[3516]: removing device node '/dev/vcs7'
Feb  7 15:38:58 localhost udev[3526]: removing device node '/dev/vcsa7'
Feb  7 15:38:58 localhost udev[3388]: creating device node '/dev/vcs1'
Feb  7 15:38:58 localhost udev[3401]: creating device node '/dev/vcsa1'
Feb  7 15:38:59 localhost udev[3409]: creating device node '/dev/vcs2'
Feb  7 15:38:59 localhost udev[3417]: creating device node '/dev/vcsa2'
Feb  7 15:38:59 localhost udev[3425]: creating device node '/dev/vcs3'
Feb  7 15:38:59 localhost udev[3433]: creating device node '/dev/vcsa3'
Feb  7 15:38:59 localhost udev[3441]: creating device node '/dev/vcs4'
Feb  7 15:38:59 localhost udev[3449]: creating device node '/dev/vcs5'
Feb  7 15:38:59 localhost udev[3457]: creating device node '/dev/vcsa4'
Feb  7 15:38:59 localhost udev[3536]: creating device node '/dev/vcs7'
Feb  7 15:38:59 localhost udev[3544]: creating device node '/dev/vcsa7'
Feb  7 15:39:00 localhost kernel: eth0: no IPv6 routers present
Feb  7 15:39:22 localhost gconfd (rick-3627): starting (version 2.8.1), pid 3627 user 'rick'
Feb  7 15:39:23 localhost gconfd (rick-3627): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 15:39:23 localhost gconfd (rick-3627): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  7 15:39:23 localhost gconfd (rick-3627): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 15:39:33 localhost gconfd (rick-3627): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  7 15:58:52 localhost -- MARK --
Feb  7 16:17:01 localhost /USR/SBIN/CRON[4239]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  7 16:31:32 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  7 16:31:32 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  7 16:31:32 localhost udev[2974]: creating device node '/dev/vcs1'
Feb  7 16:31:32 localhost udev[2998]: removing device node '/dev/vcs1'
Feb  7 16:31:32 localhost udev[2980]: creating device node '/dev/vcsa1'
Feb  7 16:31:32 localhost udev[3004]: removing device node '/dev/vcsa1'
Feb  7 16:31:32 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  7 16:31:32 localhost udev[3001]: creating device node '/dev/vcs1'
Feb  7 16:31:32 localhost udev[3015]: removing device node '/dev/vcs1'
Feb  7 16:31:32 localhost udev[3007]: creating device node '/dev/vcsa1'
Feb  7 16:31:32 localhost udev[3021]: removing device node '/dev/vcsa1'
Feb  7 16:31:32 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  7 16:31:32 localhost kernel: Symbols match kernel version 2.6.8.
Feb  7 16:31:32 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  7 16:31:32 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  7 16:31:32 localhost kernel: BIOS-provided physical RAM map:
Feb  7 16:31:32 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  7 16:31:32 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  7 16:31:32 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  7 16:31:32 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  7 16:31:32 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  7 16:31:32 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  7 16:31:32 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  7 16:31:32 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  7 16:31:32 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  7 16:31:32 localhost kernel: 767MB LOWMEM available.
Feb  7 16:31:32 localhost kernel: found SMP MP-table at 000f4d70
Feb  7 16:31:32 localhost kernel: On node 0 totalpages: 196592
Feb  7 16:31:32 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  7 16:31:32 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  7 16:31:32 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  7 16:31:32 localhost kernel: DMI 2.3 present.
Feb  7 16:31:32 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  7 16:31:32 localhost kernel:     Virtual Wire compatibility mode.
Feb  7 16:31:32 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  7 16:31:32 localhost kernel: Processor #0 6:8 APIC version 17
Feb  7 16:31:32 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  7 16:31:32 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  7 16:31:32 localhost kernel: Processors: 1
Feb  7 16:31:32 localhost kernel: Built 1 zonelists
Feb  7 16:31:32 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  7 16:31:32 localhost kernel: Initializing CPU#0
Feb  7 16:31:32 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  7 16:31:32 localhost kernel: Detected 1675.682 MHz processor.
Feb  7 16:31:32 localhost kernel: Using tsc for high-res timesource
Feb  7 16:31:32 localhost kernel: Console: colour VGA+ 80x25
Feb  7 16:31:32 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  7 16:31:32 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  7 16:31:32 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  7 16:31:32 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  7 16:31:32 localhost kernel: Calibrating delay loop... 3293.18 BogoMIPS
Feb  7 16:31:32 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  7 16:31:32 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  7 16:31:32 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  7 16:31:32 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  7 16:31:32 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  7 16:31:32 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  7 16:31:32 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 16:31:32 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  7 16:31:32 localhost kernel: Enabling fast FPU save and restore... done.
Feb  7 16:31:32 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  7 16:31:32 localhost kernel: Checking 'hlt' instruction... OK.
Feb  7 16:31:32 localhost kernel: Checking for popad bug... OK.
Feb  7 16:31:32 localhost kernel: enabled ExtINT on CPU#0
Feb  7 16:31:32 localhost kernel: ESR value before enabling vector: 00000000
Feb  7 16:31:32 localhost kernel: ESR value after enabling vector: 00000000
Feb  7 16:31:32 localhost kernel: ENABLING IO-APIC IRQs
Feb  7 16:31:32 localhost kernel: Setting 2 in the phys_id_present_map
Feb  7 16:31:32 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  7 16:31:32 localhost kernel: init IO_APIC IRQs
Feb  7 16:31:32 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  7 16:31:32 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  7 16:31:32 localhost kernel: number of MP IRQ sources: 20.
Feb  7 16:31:32 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  7 16:31:32 localhost kernel: testing the IO APIC.......................
Feb  7 16:31:32 localhost kernel: IO APIC #2......
Feb  7 16:31:32 localhost kernel: .... register #00: 02000000
Feb  7 16:31:32 localhost kernel: .......    : physical APIC id: 02
Feb  7 16:31:32 localhost kernel: .......    : Delivery Type: 0
Feb  7 16:31:32 localhost kernel: .......    : LTS          : 0
Feb  7 16:31:32 localhost kernel: .... register #01: 00178003
Feb  7 16:31:32 localhost kernel: .......     : max redirection entries: 0017
Feb  7 16:31:32 localhost kernel: .......     : PRQ implemented: 1
Feb  7 16:31:32 localhost kernel: .......     : IO APIC version: 0003
Feb  7 16:31:32 localhost kernel: .... IRQ redirection table:
Feb  7 16:31:32 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  7 16:31:32 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  7 16:31:32 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  7 16:31:32 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  7 16:31:32 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  7 16:31:32 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  7 16:31:32 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  7 16:31:32 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  7 16:31:32 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  7 16:31:32 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  7 16:31:32 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  7 16:31:32 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  7 16:31:32 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  7 16:31:32 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  7 16:31:32 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  7 16:31:32 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  7 16:31:32 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  7 16:31:32 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  7 16:31:32 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  7 16:31:32 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  7 16:31:32 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  7 16:31:32 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  7 16:31:32 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  7 16:31:32 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  7 16:31:32 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  7 16:31:32 localhost kernel: Using vector-based indexing
Feb  7 16:31:32 localhost kernel: IRQ to pin mappings:
Feb  7 16:31:32 localhost kernel: IRQ0 -> 0:2
Feb  7 16:31:32 localhost kernel: IRQ1 -> 0:1
Feb  7 16:31:32 localhost kernel: IRQ3 -> 0:3
Feb  7 16:31:32 localhost kernel: IRQ4 -> 0:4
Feb  7 16:31:32 localhost kernel: IRQ6 -> 0:6
Feb  7 16:31:32 localhost kernel: IRQ7 -> 0:7
Feb  7 16:31:32 localhost kernel: IRQ8 -> 0:8
Feb  7 16:31:32 localhost kernel: IRQ9 -> 0:9
Feb  7 16:31:32 localhost kernel: IRQ12 -> 0:12
Feb  7 16:31:32 localhost kernel: IRQ13 -> 0:13
Feb  7 16:31:32 localhost kernel: IRQ14 -> 0:14
Feb  7 16:31:32 localhost kernel: IRQ15 -> 0:15
Feb  7 16:31:32 localhost kernel: IRQ145 -> 0:16
Feb  7 16:31:32 localhost kernel: IRQ153 -> 0:21
Feb  7 16:31:32 localhost kernel: IRQ161 -> 0:22
Feb  7 16:31:32 localhost kernel: IRQ169 -> 0:23
Feb  7 16:31:32 localhost kernel: .................................... done.
Feb  7 16:31:32 localhost kernel: Using local APIC timer interrupts.
Feb  7 16:31:32 localhost kernel: calibrating APIC timer ...
Feb  7 16:31:32 localhost kernel: ..... CPU clock speed is 1674.0844 MHz.
Feb  7 16:31:32 localhost kernel: ..... host bus clock speed is 267.0975 MHz.
Feb  7 16:31:32 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  7 16:31:32 localhost kernel: Freeing initrd memory: 4136k freed
Feb  7 16:31:32 localhost kernel: NET: Registered protocol family 16
Feb  7 16:31:32 localhost kernel: EISA bus registered
Feb  7 16:31:32 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  7 16:31:32 localhost kernel: PCI: Using configuration type 1
Feb  7 16:31:32 localhost kernel: mtrr: v2.0 (20020519)
Feb  7 16:31:32 localhost kernel: ACPI: Subsystem revision 20040816
Feb  7 16:31:32 localhost kernel: ACPI: Interpreter disabled.
Feb  7 16:31:32 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  7 16:31:32 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  7 16:31:32 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  7 16:31:32 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  7 16:31:32 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  7 16:31:32 localhost kernel: PCI: Probing PCI hardware
Feb  7 16:31:32 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  7 16:31:32 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  7 16:31:32 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  7 16:31:32 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  7 16:31:32 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  7 16:31:32 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  7 16:31:32 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  7 16:31:32 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  7 16:31:32 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  7 16:31:32 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  7 16:31:32 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  7 16:31:32 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  7 16:31:32 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  7 16:31:32 localhost kernel: devfs: boot_options: 0x0
Feb  7 16:31:32 localhost kernel: Initializing Cryptographic API
Feb  7 16:31:32 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  7 16:31:32 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  7 16:31:32 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  7 16:31:32 localhost kernel: isapnp: Scanning for PnP cards...
Feb  7 16:31:32 localhost kernel: isapnp: No Plug & Play device found
Feb  7 16:31:32 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  7 16:31:32 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  7 16:31:32 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  7 16:31:32 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  7 16:31:32 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  7 16:31:32 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  7 16:31:32 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  7 16:31:32 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  7 16:31:32 localhost kernel: EISA: Detected 0 cards.
Feb  7 16:31:32 localhost kernel: NET: Registered protocol family 2
Feb  7 16:31:32 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  7 16:31:32 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  7 16:31:32 localhost kernel: NET: Registered protocol family 8
Feb  7 16:31:32 localhost kernel: NET: Registered protocol family 20
Feb  7 16:31:32 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  7 16:31:32 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  7 16:31:32 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  7 16:31:32 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  7 16:31:32 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  7 16:31:32 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  7 16:31:32 localhost kernel: NET: Registered protocol family 1
Feb  7 16:31:32 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  7 16:31:32 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  7 16:31:32 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  7 16:31:32 localhost kernel: VP_IDE: chipset revision 6
Feb  7 16:31:32 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  7 16:31:32 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  7 16:31:32 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  7 16:31:32 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  7 16:31:32 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  7 16:31:32 localhost kernel: Using anticipatory io scheduler
Feb  7 16:31:32 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  7 16:31:32 localhost kernel: hda: max request size: 1024KiB
Feb  7 16:31:32 localhost kernel: hda: Host Protected Area detected.
Feb  7 16:31:32 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  7 16:31:32 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  7 16:31:32 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  7 16:31:32 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  7 16:31:32 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  7 16:31:32 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  7 16:31:32 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  7 16:31:32 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Feb  7 16:31:32 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  7 16:31:32 localhost kernel: EXT3-fs: hda1: orphan cleanup on readonly fs
Feb  7 16:31:32 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881318
Feb  7 16:31:32 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881314
Feb  7 16:31:32 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881312
Feb  7 16:31:32 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881309
Feb  7 16:31:32 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881305
Feb  7 16:31:32 localhost kernel: EXT3-fs: hda1: 5 orphan inodes deleted
Feb  7 16:31:32 localhost kernel: EXT3-fs: recovery complete.
Feb  7 16:31:32 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  7 16:31:32 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  7 16:31:32 localhost kernel: EXT3 FS on hda1, internal journal
Feb  7 16:31:32 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  7 16:31:32 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  7 16:31:32 localhost kernel: hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  7 16:31:32 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  7 16:31:32 localhost kernel: ts: Compaq touchscreen protocol output
Feb  7 16:31:32 localhost kernel: parport: PnPBIOS parport detected.
Feb  7 16:31:32 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  7 16:31:32 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  7 16:31:32 localhost kernel: Capability LSM initialized
Feb  7 16:31:32 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  7 16:31:32 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  7 16:31:32 localhost kernel: cdrom: open failed.
Feb  7 16:31:32 localhost kernel: Real Time Clock Driver v1.12
Feb  7 16:31:32 localhost kernel: input: PC Speaker
Feb  7 16:31:32 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  7 16:31:32 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  7 16:31:32 localhost kernel: FDC 0 is a post-1991 82077
Feb  7 16:31:32 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  7 16:31:32 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  7 16:31:32 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  7 16:31:32 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  7 16:31:32 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  7 16:31:32 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  7 16:31:32 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  7 16:31:32 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  7 16:31:32 localhost kernel: usbcore: registered new driver usbfs
Feb  7 16:31:32 localhost kernel: usbcore: registered new driver hub
Feb  7 16:31:32 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  7 16:31:32 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  7 16:31:32 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  7 16:31:32 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  7 16:31:32 localhost kernel: hub 1-0:1.0: USB hub found
Feb  7 16:31:32 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  7 16:31:32 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  7 16:31:32 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  7 16:31:32 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 16:31:32 localhost kernel: hub 2-0:1.0: USB hub found
Feb  7 16:31:32 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  7 16:31:32 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  7 16:31:32 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  7 16:31:32 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  7 16:31:32 localhost kernel: hub 3-0:1.0: USB hub found
Feb  7 16:31:32 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  7 16:31:32 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  7 16:31:32 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f093b000
Feb  7 16:31:32 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  7 16:31:32 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  7 16:31:32 localhost kernel: hub 4-0:1.0: USB hub found
Feb  7 16:31:32 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  7 16:31:32 localhost kernel: irda_init()
Feb  7 16:31:32 localhost kernel: NET: Registered protocol family 23
Feb  7 16:31:32 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  7 16:31:32 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  7 16:31:32 localhost kernel:          and report if it works on your machine.
Feb  7 16:31:32 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  7 16:31:32 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  7 16:31:32 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  7 16:31:32 localhost kernel: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Feb  7 16:31:32 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  7 16:31:32 localhost kernel: NET: Registered protocol family 17
Feb  7 16:31:32 localhost kernel: NET: Registered protocol family 10
Feb  7 16:31:32 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  7 16:31:32 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  7 16:31:32 localhost udev[3018]: creating device node '/dev/vcs1'
Feb  7 16:31:32 localhost udev[3024]: creating device node '/dev/vcsa1'
Feb  7 16:31:35 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 16:31:35 localhost postfix/master[3257]: daemon started -- version 2.1.3
Feb  7 16:31:36 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  7 16:31:36 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  7 16:31:36 localhost /usr/sbin/cron[3330]: (CRON) INFO (pidfile fd = 3)
Feb  7 16:31:36 localhost /usr/sbin/cron[3331]: (CRON) STARTUP (fork ok)
Feb  7 16:31:36 localhost /usr/sbin/cron[3331]: (CRON) INFO (Running @reboot jobs)
Feb  7 16:31:37 localhost udev[3375]: removing device node '/dev/vcs1'
Feb  7 16:31:37 localhost udev[3386]: removing device node '/dev/vcsa1'
Feb  7 16:31:37 localhost udev[3474]: creating device node '/dev/vcsa3'
Feb  7 16:31:37 localhost udev[3534]: creating device node '/dev/vcs6'
Feb  7 16:31:37 localhost udev[3536]: creating device node '/dev/vcs7'
Feb  7 16:31:37 localhost udev[3535]: creating device node '/dev/vcsa6'
Feb  7 16:31:37 localhost udev[3550]: removing device node '/dev/vcsa6'
Feb  7 16:31:37 localhost udev[3537]: creating device node '/dev/vcsa7'
Feb  7 16:31:37 localhost udev[3557]: removing device node '/dev/vcs7'
Feb  7 16:31:37 localhost udev[3560]: removing device node '/dev/vcs6'
Feb  7 16:31:37 localhost udev[3571]: removing device node '/dev/vcsa7'
Feb  7 16:31:37 localhost udev[3553]: creating device node '/dev/vcsa6'
Feb  7 16:31:37 localhost udev[3563]: creating device node '/dev/vcs6'
Feb  7 16:31:38 localhost udev[3397]: creating device node '/dev/vcs1'
Feb  7 16:31:38 localhost udev[3410]: creating device node '/dev/vcsa1'
Feb  7 16:31:38 localhost udev[3418]: creating device node '/dev/vcs2'
Feb  7 16:31:38 localhost udev[3426]: creating device node '/dev/vcsa2'
Feb  7 16:31:38 localhost udev[3434]: creating device node '/dev/vcs4'
Feb  7 16:31:38 localhost udev[3442]: creating device node '/dev/vcsa4'
Feb  7 16:31:38 localhost udev[3450]: creating device node '/dev/vcs5'
Feb  7 16:31:38 localhost udev[3458]: creating device node '/dev/vcsa5'
Feb  7 16:31:38 localhost udev[3466]: creating device node '/dev/vcs3'
Feb  7 16:31:39 localhost udev[3585]: creating device node '/dev/vcs7'
Feb  7 16:31:39 localhost udev[3593]: creating device node '/dev/vcsa7'
Feb  7 16:31:40 localhost kernel: eth0: no IPv6 routers present
Feb  7 16:31:55 localhost gconfd (rick-3676): starting (version 2.8.1), pid 3676 user 'rick'
Feb  7 16:31:55 localhost gconfd (rick-3676): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 16:31:55 localhost gconfd (rick-3676): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  7 16:31:55 localhost gconfd (rick-3676): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 16:32:05 localhost gconfd (rick-3676): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  7 16:51:32 localhost -- MARK --
Feb  7 16:52:56 localhost gconfd (rick-3676): Exiting
Feb  7 16:52:56 localhost gconfd (rick-4221): starting (version 2.8.1), pid 4221 user 'rick'
Feb  7 16:52:56 localhost gconfd (rick-4221): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 16:52:56 localhost gconfd (rick-4221): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  7 16:52:56 localhost gconfd (rick-4221): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 16:52:56 localhost gdm[3354]: Master halting...
Feb  7 16:52:57 localhost udev[4233]: removing device node '/dev/vcs7'
Feb  7 16:52:57 localhost udev[4244]: removing device node '/dev/vcsa7'
Feb  7 16:52:57 localhost shutdown[3354]: shutting down for system halt
Feb  7 16:52:57 localhost init: Switching to runlevel: 0
Feb  7 16:52:57 localhost udev[4255]: removing device node '/dev/vcs2'
Feb  7 16:52:57 localhost udev[4265]: removing device node '/dev/vcsa2'
Feb  7 16:52:57 localhost udev[4275]: removing device node '/dev/vcs3'
Feb  7 16:52:57 localhost udev[4285]: removing device node '/dev/vcsa3'
Feb  7 16:52:57 localhost udev[4295]: removing device node '/dev/vcs4'
Feb  7 16:52:57 localhost udev[4305]: removing device node '/dev/vcsa4'
Feb  7 16:52:57 localhost udev[4315]: removing device node '/dev/vcs5'
Feb  7 16:52:57 localhost udev[4325]: removing device node '/dev/vcsa5'
Feb  7 16:52:57 localhost udev[4335]: removing device node '/dev/vcs6'
Feb  7 16:52:57 localhost udev[4345]: removing device node '/dev/vcsa6'
Feb  7 16:52:57 localhost udev[4355]: removing device node '/dev/vcs1'
Feb  7 16:52:57 localhost udev[4365]: removing device node '/dev/vcsa1'
Feb  7 16:52:58 localhost postfix/postfix-script: stopping the Postfix mail system
Feb  7 16:52:58 localhost postfix/master[3257]: terminating on signal 15
Feb  7 16:52:59 localhost udev[4376]: creating device node '/dev/vcs1'
Feb  7 16:52:59 localhost udev[4384]: creating device node '/dev/vcsa1'
Feb  7 16:53:00 localhost kernel: Kernel logging (proc) stopped.
Feb  7 16:53:00 localhost kernel: Kernel log daemon terminating.
Feb  7 16:53:00 localhost exiting on signal 15
Feb  7 18:52:37 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  7 18:52:37 localhost udev[2936]: creating device node '/dev/vcs1'
Feb  7 18:52:37 localhost udev[2956]: removing device node '/dev/vcs1'
Feb  7 18:52:37 localhost udev[2937]: creating device node '/dev/vcsa1'
Feb  7 18:52:37 localhost udev[2962]: removing device node '/dev/vcsa1'
Feb  7 18:52:37 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  7 18:52:37 localhost udev[2959]: creating device node '/dev/vcs1'
Feb  7 18:52:37 localhost udev[2988]: removing device node '/dev/vcs1'
Feb  7 18:52:37 localhost udev[2965]: creating device node '/dev/vcsa1'
Feb  7 18:52:37 localhost udev[2994]: removing device node '/dev/vcsa1'
Feb  7 18:52:37 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  7 18:52:37 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  7 18:52:37 localhost kernel: Symbols match kernel version 2.6.8.
Feb  7 18:52:37 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  7 18:52:37 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  7 18:52:37 localhost kernel: BIOS-provided physical RAM map:
Feb  7 18:52:37 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  7 18:52:37 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  7 18:52:37 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  7 18:52:37 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  7 18:52:37 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  7 18:52:37 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  7 18:52:37 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  7 18:52:37 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  7 18:52:37 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  7 18:52:37 localhost kernel: 767MB LOWMEM available.
Feb  7 18:52:37 localhost kernel: found SMP MP-table at 000f4d70
Feb  7 18:52:37 localhost kernel: On node 0 totalpages: 196592
Feb  7 18:52:37 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  7 18:52:37 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  7 18:52:37 localhost udev[2991]: creating device node '/dev/vcs1'
Feb  7 18:52:37 localhost udev[3005]: removing device node '/dev/vcs1'
Feb  7 18:52:38 localhost udev[2997]: creating device node '/dev/vcsa1'
Feb  7 18:52:38 localhost udev[3011]: removing device node '/dev/vcsa1'
Feb  7 18:52:37 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  7 18:52:38 localhost kernel: DMI 2.3 present.
Feb  7 18:52:38 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  7 18:52:38 localhost kernel:     Virtual Wire compatibility mode.
Feb  7 18:52:38 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  7 18:52:38 localhost kernel: Processor #0 6:8 APIC version 17
Feb  7 18:52:38 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  7 18:52:38 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  7 18:52:38 localhost kernel: Processors: 1
Feb  7 18:52:38 localhost kernel: Built 1 zonelists
Feb  7 18:52:38 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  7 18:52:38 localhost kernel: Initializing CPU#0
Feb  7 18:52:38 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  7 18:52:38 localhost kernel: Detected 1675.682 MHz processor.
Feb  7 18:52:38 localhost kernel: Using tsc for high-res timesource
Feb  7 18:52:38 localhost kernel: Console: colour VGA+ 80x25
Feb  7 18:52:38 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  7 18:52:38 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  7 18:52:38 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  7 18:52:38 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  7 18:52:38 localhost kernel: Calibrating delay loop... 3293.18 BogoMIPS
Feb  7 18:52:38 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  7 18:52:38 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  7 18:52:38 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  7 18:52:38 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  7 18:52:38 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  7 18:52:38 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  7 18:52:38 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  7 18:52:38 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  7 18:52:38 localhost kernel: Enabling fast FPU save and restore... done.
Feb  7 18:52:38 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  7 18:52:38 localhost kernel: Checking 'hlt' instruction... OK.
Feb  7 18:52:38 localhost kernel: Checking for popad bug... OK.
Feb  7 18:52:38 localhost kernel: enabled ExtINT on CPU#0
Feb  7 18:52:38 localhost kernel: ESR value before enabling vector: 00000000
Feb  7 18:52:38 localhost kernel: ESR value after enabling vector: 00000000
Feb  7 18:52:38 localhost kernel: ENABLING IO-APIC IRQs
Feb  7 18:52:38 localhost kernel: Setting 2 in the phys_id_present_map
Feb  7 18:52:38 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  7 18:52:38 localhost kernel: init IO_APIC IRQs
Feb  7 18:52:38 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  7 18:52:38 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  7 18:52:38 localhost kernel: number of MP IRQ sources: 20.
Feb  7 18:52:38 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  7 18:52:38 localhost kernel: testing the IO APIC.......................
Feb  7 18:52:38 localhost kernel: IO APIC #2......
Feb  7 18:52:38 localhost kernel: .... register #00: 02000000
Feb  7 18:52:38 localhost kernel: .......    : physical APIC id: 02
Feb  7 18:52:38 localhost kernel: .......    : Delivery Type: 0
Feb  7 18:52:38 localhost kernel: .......    : LTS          : 0
Feb  7 18:52:38 localhost kernel: .... register #01: 00178003
Feb  7 18:52:38 localhost kernel: .......     : max redirection entries: 0017
Feb  7 18:52:38 localhost kernel: .......     : PRQ implemented: 1
Feb  7 18:52:38 localhost kernel: .......     : IO APIC version: 0003
Feb  7 18:52:38 localhost kernel: .... IRQ redirection table:
Feb  7 18:52:38 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  7 18:52:38 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  7 18:52:38 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  7 18:52:38 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  7 18:52:38 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  7 18:52:38 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  7 18:52:38 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  7 18:52:38 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  7 18:52:38 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  7 18:52:38 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  7 18:52:38 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  7 18:52:38 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  7 18:52:38 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  7 18:52:38 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  7 18:52:38 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 18:52:38 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  7 18:52:38 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  7 18:52:38 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  7 18:52:38 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  7 18:52:38 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  7 18:52:38 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  7 18:52:38 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  7 18:52:38 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  7 18:52:38 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  7 18:52:38 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  7 18:52:38 localhost kernel: Using vector-based indexing
Feb  7 18:52:38 localhost kernel: IRQ to pin mappings:
Feb  7 18:52:38 localhost kernel: IRQ0 -> 0:2
Feb  7 18:52:38 localhost kernel: IRQ1 -> 0:1
Feb  7 18:52:38 localhost kernel: IRQ3 -> 0:3
Feb  7 18:52:38 localhost kernel: IRQ4 -> 0:4
Feb  7 18:52:38 localhost kernel: IRQ6 -> 0:6
Feb  7 18:52:38 localhost kernel: IRQ7 -> 0:7
Feb  7 18:52:38 localhost kernel: IRQ8 -> 0:8
Feb  7 18:52:38 localhost kernel: IRQ9 -> 0:9
Feb  7 18:52:38 localhost kernel: IRQ12 -> 0:12
Feb  7 18:52:38 localhost kernel: IRQ13 -> 0:13
Feb  7 18:52:38 localhost kernel: IRQ14 -> 0:14
Feb  7 18:52:38 localhost kernel: IRQ15 -> 0:15
Feb  7 18:52:38 localhost kernel: IRQ145 -> 0:16
Feb  7 18:52:38 localhost kernel: IRQ153 -> 0:21
Feb  7 18:52:38 localhost kernel: IRQ161 -> 0:22
Feb  7 18:52:38 localhost kernel: IRQ169 -> 0:23
Feb  7 18:52:38 localhost kernel: .................................... done.
Feb  7 18:52:38 localhost kernel: Using local APIC timer interrupts.
Feb  7 18:52:38 localhost kernel: calibrating APIC timer ...
Feb  7 18:52:38 localhost kernel: ..... CPU clock speed is 1674.0839 MHz.
Feb  7 18:52:38 localhost kernel: ..... host bus clock speed is 267.0974 MHz.
Feb  7 18:52:38 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  7 18:52:38 localhost kernel: Freeing initrd memory: 4136k freed
Feb  7 18:52:38 localhost kernel: NET: Registered protocol family 16
Feb  7 18:52:38 localhost kernel: EISA bus registered
Feb  7 18:52:38 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  7 18:52:38 localhost kernel: PCI: Using configuration type 1
Feb  7 18:52:38 localhost kernel: mtrr: v2.0 (20020519)
Feb  7 18:52:38 localhost kernel: ACPI: Subsystem revision 20040816
Feb  7 18:52:38 localhost kernel: ACPI: Interpreter disabled.
Feb  7 18:52:38 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  7 18:52:38 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  7 18:52:38 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  7 18:52:38 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  7 18:52:38 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  7 18:52:38 localhost kernel: PCI: Probing PCI hardware
Feb  7 18:52:38 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  7 18:52:38 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  7 18:52:38 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  7 18:52:38 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  7 18:52:38 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  7 18:52:38 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  7 18:52:38 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  7 18:52:38 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  7 18:52:38 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  7 18:52:38 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  7 18:52:38 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  7 18:52:38 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  7 18:52:38 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  7 18:52:38 localhost kernel: devfs: boot_options: 0x0
Feb  7 18:52:38 localhost kernel: Initializing Cryptographic API
Feb  7 18:52:38 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  7 18:52:38 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  7 18:52:38 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  7 18:52:38 localhost kernel: isapnp: Scanning for PnP cards...
Feb  7 18:52:38 localhost kernel: isapnp: No Plug & Play device found
Feb  7 18:52:38 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  7 18:52:38 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  7 18:52:38 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  7 18:52:38 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  7 18:52:38 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  7 18:52:38 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  7 18:52:38 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  7 18:52:38 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  7 18:52:38 localhost kernel: EISA: Detected 0 cards.
Feb  7 18:52:38 localhost kernel: NET: Registered protocol family 2
Feb  7 18:52:38 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  7 18:52:38 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  7 18:52:38 localhost kernel: NET: Registered protocol family 8
Feb  7 18:52:38 localhost kernel: NET: Registered protocol family 20
Feb  7 18:52:38 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  7 18:52:38 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  7 18:52:38 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  7 18:52:38 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  7 18:52:38 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  7 18:52:38 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  7 18:52:38 localhost kernel: NET: Registered protocol family 1
Feb  7 18:52:38 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  7 18:52:38 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  7 18:52:38 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  7 18:52:38 localhost kernel: VP_IDE: chipset revision 6
Feb  7 18:52:38 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  7 18:52:38 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  7 18:52:38 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  7 18:52:38 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  7 18:52:38 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  7 18:52:38 localhost kernel: Using anticipatory io scheduler
Feb  7 18:52:38 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  7 18:52:38 localhost kernel: hda: max request size: 1024KiB
Feb  7 18:52:38 localhost kernel: hda: Host Protected Area detected.
Feb  7 18:52:38 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  7 18:52:38 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  7 18:52:38 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  7 18:52:38 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  7 18:52:38 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  7 18:52:38 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  7 18:52:38 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  7 18:52:38 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  7 18:52:38 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  7 18:52:38 localhost kernel: EXT3 FS on hda1, internal journal
Feb  7 18:52:38 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  7 18:52:38 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  7 18:52:38 localhost kernel: ts: Compaq touchscreen protocol output
Feb  7 18:52:38 localhost kernel: hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  7 18:52:38 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  7 18:52:38 localhost kernel: parport: PnPBIOS parport detected.
Feb  7 18:52:38 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  7 18:52:38 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  7 18:52:38 localhost kernel: Capability LSM initialized
Feb  7 18:52:38 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  7 18:52:38 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  7 18:52:38 localhost kernel: cdrom: hdc: mrw address space DMA selected
Feb  7 18:52:38 localhost kernel: Real Time Clock Driver v1.12
Feb  7 18:52:38 localhost kernel: input: PC Speaker
Feb  7 18:52:38 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  7 18:52:38 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  7 18:52:38 localhost kernel: FDC 0 is a post-1991 82077
Feb  7 18:52:38 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  7 18:52:38 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  7 18:52:38 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  7 18:52:38 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  7 18:52:38 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  7 18:52:38 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  7 18:52:38 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  7 18:52:38 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  7 18:52:38 localhost kernel: usbcore: registered new driver usbfs
Feb  7 18:52:38 localhost kernel: usbcore: registered new driver hub
Feb  7 18:52:38 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  7 18:52:38 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  7 18:52:38 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  7 18:52:38 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  7 18:52:38 localhost kernel: hub 1-0:1.0: USB hub found
Feb  7 18:52:38 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  7 18:52:38 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  7 18:52:38 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  7 18:52:38 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  7 18:52:38 localhost kernel: hub 2-0:1.0: USB hub found
Feb  7 18:52:38 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  7 18:52:38 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  7 18:52:38 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  7 18:52:38 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  7 18:52:38 localhost kernel: hub 3-0:1.0: USB hub found
Feb  7 18:52:38 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  7 18:52:38 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  7 18:52:38 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f08a4000
Feb  7 18:52:38 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  7 18:52:38 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  7 18:52:38 localhost kernel: hub 4-0:1.0: USB hub found
Feb  7 18:52:38 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  7 18:52:38 localhost kernel: irda_init()
Feb  7 18:52:38 localhost kernel: NET: Registered protocol family 23
Feb  7 18:52:38 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  7 18:52:38 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  7 18:52:38 localhost kernel:          and report if it works on your machine.
Feb  7 18:52:38 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  7 18:52:38 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  7 18:52:38 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  7 18:52:38 localhost kernel: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Feb  7 18:52:38 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  7 18:52:38 localhost kernel: NET: Registered protocol family 17
Feb  7 18:52:38 localhost kernel: NET: Registered protocol family 10
Feb  7 18:52:38 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  7 18:52:38 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  7 18:52:38 localhost udev[3008]: creating device node '/dev/vcs1'
Feb  7 18:52:38 localhost udev[3014]: creating device node '/dev/vcsa1'
Feb  7 18:52:41 localhost postfix/postfix-script: starting the Postfix mail system
Feb  7 18:52:41 localhost postfix/master[3243]: daemon started -- version 2.1.3
Feb  7 18:52:41 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  7 18:52:41 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  7 18:52:41 localhost /usr/sbin/cron[3316]: (CRON) INFO (pidfile fd = 3)
Feb  7 18:52:41 localhost /usr/sbin/cron[3317]: (CRON) STARTUP (fork ok)
Feb  7 18:52:41 localhost /usr/sbin/cron[3317]: (CRON) INFO (Running @reboot jobs)
Feb  7 18:52:42 localhost udev[3453]: removing device node '/dev/vcs1'
Feb  7 18:52:42 localhost udev[3456]: removing device node '/dev/vcsa1'
Feb  7 18:52:43 localhost udev[3459]: creating device node '/dev/vcs2'
Feb  7 18:52:43 localhost udev[3460]: creating device node '/dev/vcs3'
Feb  7 18:52:43 localhost udev[3461]: creating device node '/dev/vcsa2'
Feb  7 18:52:43 localhost udev[3462]: creating device node '/dev/vcs4'
Feb  7 18:52:43 localhost udev[3480]: creating device node '/dev/vcs5'
Feb  7 18:52:43 localhost udev[3481]: creating device node '/dev/vcsa4'
Feb  7 18:52:43 localhost udev[3482]: creating device node '/dev/vcsa5'
Feb  7 18:52:43 localhost udev[3483]: creating device node '/dev/vcs1'
Feb  7 18:52:43 localhost udev[3484]: creating device node '/dev/vcsa1'
Feb  7 18:52:43 localhost udev[3485]: creating device node '/dev/vcs6'
Feb  7 18:52:43 localhost udev[3463]: creating device node '/dev/vcsa3'
Feb  7 18:52:43 localhost udev[3491]: creating device node '/dev/vcsa6'
Feb  7 18:52:43 localhost udev[3492]: creating device node '/dev/vcs7'
Feb  7 18:52:43 localhost udev[3493]: creating device node '/dev/vcsa7'

---

### Post by rick_write_taiwan on 2005-02-09
Feb  7 18:52:43 localhost udev[3536]: removing device node '/dev/vcs7'
Feb  7 18:52:43 localhost udev[3539]: removing device node '/dev/vcsa7'
Feb  7 18:52:43 localhost udev[3550]: creating device node '/dev/vcs7'
Feb  7 18:52:43 localhost udev[3557]: creating device node '/dev/vcsa7'
Feb  7 18:52:46 localhost kernel: eth0: no IPv6 routers present
Feb  7 18:53:03 localhost gconfd (rick-3622): starting (version 2.8.1), pid 3622 user 'rick'
Feb  7 18:53:03 localhost gconfd (rick-3622): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  7 18:53:03 localhost gconfd (rick-3622): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  7 18:53:03 localhost gconfd (rick-3622): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  7 18:53:13 localhost gconfd (rick-3622): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  7 19:12:37 localhost -- MARK --
Feb  7 19:17:01 localhost /USR/SBIN/CRON[4118]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  7 19:32:37 localhost -- MARK --
Feb  8 09:59:03 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  8 09:59:03 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  8 09:59:03 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  8 09:59:03 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  8 09:59:03 localhost kernel: Symbols match kernel version 2.6.8.
Feb  8 09:59:03 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  8 09:59:03 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  8 09:59:03 localhost kernel: BIOS-provided physical RAM map:
Feb  8 09:59:03 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  8 09:59:03 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  8 09:59:03 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  8 09:59:03 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  8 09:59:03 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  8 09:59:03 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  8 09:59:03 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  8 09:59:03 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  8 09:59:03 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  8 09:59:03 localhost kernel: 767MB LOWMEM available.
Feb  8 09:59:03 localhost kernel: found SMP MP-table at 000f4d70
Feb  8 09:59:03 localhost kernel: On node 0 totalpages: 196592
Feb  8 09:59:03 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  8 09:59:03 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  8 09:59:03 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  8 09:59:03 localhost kernel: DMI 2.3 present.
Feb  8 09:59:03 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  8 09:59:03 localhost kernel:     Virtual Wire compatibility mode.
Feb  8 09:59:03 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  8 09:59:03 localhost kernel: Processor #0 6:8 APIC version 17
Feb  8 09:59:03 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  8 09:59:03 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  8 09:59:03 localhost kernel: Processors: 1
Feb  8 09:59:03 localhost kernel: Built 1 zonelists
Feb  8 09:59:03 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  8 09:59:03 localhost kernel: Initializing CPU#0
Feb  8 09:59:03 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  8 09:59:03 localhost kernel: Detected 1675.772 MHz processor.
Feb  8 09:59:03 localhost kernel: Using tsc for high-res timesource
Feb  8 09:59:03 localhost kernel: Console: colour VGA+ 80x25
Feb  8 09:59:03 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  8 09:59:03 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  8 09:59:03 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  8 09:59:03 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  8 09:59:03 localhost kernel: Calibrating delay loop... 3301.37 BogoMIPS
Feb  8 09:59:03 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  8 09:59:03 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  8 09:59:03 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  8 09:59:03 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  8 09:59:03 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  8 09:59:03 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  8 09:59:03 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  8 09:59:03 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  8 09:59:03 localhost kernel: Enabling fast FPU save and restore... done.
Feb  8 09:59:03 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  8 09:59:03 localhost kernel: Checking 'hlt' instruction... OK.
Feb  8 09:59:03 localhost kernel: Checking for popad bug... OK.
Feb  8 09:59:03 localhost kernel: enabled ExtINT on CPU#0
Feb  8 09:59:03 localhost kernel: ESR value before enabling vector: 00000000
Feb  8 09:59:03 localhost kernel: ESR value after enabling vector: 00000000
Feb  8 09:59:03 localhost kernel: ENABLING IO-APIC IRQs
Feb  8 09:59:03 localhost kernel: Setting 2 in the phys_id_present_map
Feb  8 09:59:03 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  8 09:59:03 localhost kernel: init IO_APIC IRQs
Feb  8 09:59:03 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  8 09:59:03 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  8 09:59:03 localhost kernel: number of MP IRQ sources: 20.
Feb  8 09:59:03 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  8 09:59:03 localhost kernel: testing the IO APIC.......................
Feb  8 09:59:03 localhost kernel: IO APIC #2......
Feb  8 09:59:03 localhost kernel: .... register #00: 02000000
Feb  8 09:59:03 localhost kernel: .......    : physical APIC id: 02
Feb  8 09:59:03 localhost kernel: .......    : Delivery Type: 0
Feb  8 09:59:03 localhost kernel: .......    : LTS          : 0
Feb  8 09:59:03 localhost kernel: .... register #01: 00178003
Feb  8 09:59:03 localhost kernel: .......     : max redirection entries: 0017
Feb  8 09:59:03 localhost kernel: .......     : PRQ implemented: 1
Feb  8 09:59:03 localhost kernel: .......     : IO APIC version: 0003
Feb  8 09:59:03 localhost kernel: .... IRQ redirection table:
Feb  8 09:59:03 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  8 09:59:03 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  8 09:59:03 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  8 09:59:03 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  8 09:59:03 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  8 09:59:03 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  8 09:59:03 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  8 09:59:03 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  8 09:59:03 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  8 09:59:03 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  8 09:59:03 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  8 09:59:03 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  8 09:59:03 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  8 09:59:03 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  8 09:59:03 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  8 09:59:03 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  8 09:59:03 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  8 09:59:03 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  8 09:59:03 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  8 09:59:03 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  8 09:59:03 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  8 09:59:03 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  8 09:59:03 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  8 09:59:03 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  8 09:59:03 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  8 09:59:03 localhost kernel: Using vector-based indexing
Feb  8 09:59:03 localhost kernel: IRQ to pin mappings:
Feb  8 09:59:03 localhost kernel: IRQ0 -> 0:2
Feb  8 09:59:03 localhost kernel: IRQ1 -> 0:1
Feb  8 09:59:03 localhost kernel: IRQ3 -> 0:3
Feb  8 09:59:03 localhost kernel: IRQ4 -> 0:4
Feb  8 09:59:03 localhost kernel: IRQ6 -> 0:6
Feb  8 09:59:03 localhost kernel: IRQ7 -> 0:7
Feb  8 09:59:03 localhost kernel: IRQ8 -> 0:8
Feb  8 09:59:03 localhost kernel: IRQ9 -> 0:9
Feb  8 09:59:03 localhost kernel: IRQ12 -> 0:12
Feb  8 09:59:03 localhost kernel: IRQ13 -> 0:13
Feb  8 09:59:03 localhost kernel: IRQ14 -> 0:14
Feb  8 09:59:03 localhost kernel: IRQ15 -> 0:15
Feb  8 09:59:03 localhost kernel: IRQ145 -> 0:16
Feb  8 09:59:03 localhost kernel: IRQ153 -> 0:21
Feb  8 09:59:03 localhost kernel: IRQ161 -> 0:22
Feb  8 09:59:03 localhost kernel: IRQ169 -> 0:23
Feb  8 09:59:03 localhost kernel: .................................... done.
Feb  8 09:59:03 localhost kernel: Using local APIC timer interrupts.
Feb  8 09:59:03 localhost kernel: calibrating APIC timer ...
Feb  8 09:59:03 localhost kernel: ..... CPU clock speed is 1674.0839 MHz.
Feb  8 09:59:03 localhost kernel: ..... host bus clock speed is 267.0974 MHz.
Feb  8 09:59:03 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  8 09:59:03 localhost kernel: Freeing initrd memory: 4136k freed
Feb  8 09:59:03 localhost kernel: NET: Registered protocol family 16
Feb  8 09:59:03 localhost kernel: EISA bus registered
Feb  8 09:59:03 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  8 09:59:03 localhost kernel: PCI: Using configuration type 1
Feb  8 09:59:03 localhost kernel: mtrr: v2.0 (20020519)
Feb  8 09:59:03 localhost kernel: ACPI: Subsystem revision 20040816
Feb  8 09:59:03 localhost kernel: ACPI: Interpreter disabled.
Feb  8 09:59:03 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  8 09:59:03 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  8 09:59:03 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  8 09:59:03 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  8 09:59:03 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  8 09:59:03 localhost kernel: PCI: Probing PCI hardware
Feb  8 09:59:03 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  8 09:59:03 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  8 09:59:03 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  8 09:59:03 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  8 09:59:03 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  8 09:59:03 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  8 09:59:03 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  8 09:59:03 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  8 09:59:03 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  8 09:59:03 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  8 09:59:03 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  8 09:59:03 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  8 09:59:03 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  8 09:59:03 localhost kernel: devfs: boot_options: 0x0
Feb  8 09:59:03 localhost kernel: Initializing Cryptographic API
Feb  8 09:59:03 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  8 09:59:03 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  8 09:59:03 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  8 09:59:03 localhost kernel: isapnp: Scanning for PnP cards...
Feb  8 09:59:03 localhost kernel: isapnp: No Plug & Play device found
Feb  8 09:59:03 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  8 09:59:03 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  8 09:59:03 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  8 09:59:03 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  8 09:59:03 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  8 09:59:03 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  8 09:59:03 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  8 09:59:03 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  8 09:59:03 localhost kernel: EISA: Detected 0 cards.
Feb  8 09:59:03 localhost kernel: NET: Registered protocol family 2
Feb  8 09:59:03 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  8 09:59:03 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  8 09:59:03 localhost kernel: NET: Registered protocol family 8
Feb  8 09:59:03 localhost kernel: NET: Registered protocol family 20
Feb  8 09:59:03 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  8 09:59:03 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  8 09:59:03 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  8 09:59:03 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  8 09:59:03 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  8 09:59:03 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  8 09:59:03 localhost kernel: NET: Registered protocol family 1
Feb  8 09:59:03 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  8 09:59:03 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  8 09:59:03 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  8 09:59:03 localhost kernel: VP_IDE: chipset revision 6
Feb  8 09:59:03 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  8 09:59:03 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1

---

### Post by rick_write_taiwan on 2005-02-09
Feb  8 09:59:03 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  8 09:59:03 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  8 09:59:03 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  8 09:59:03 localhost kernel: Using anticipatory io scheduler
Feb  8 09:59:03 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  8 09:59:03 localhost kernel: hda: max request size: 1024KiB
Feb  8 09:59:03 localhost kernel: hda: Host Protected Area detected.
Feb  8 09:59:03 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  8 09:59:03 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  8 09:59:03 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  8 09:59:03 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  8 09:59:03 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  8 09:59:03 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  8 09:59:03 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  8 09:59:03 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Feb  8 09:59:03 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  8 09:59:03 localhost kernel: EXT3-fs: hda1: orphan cleanup on readonly fs
Feb  8 09:59:03 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881318
Feb  8 09:59:03 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881315
Feb  8 09:59:03 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881312
Feb  8 09:59:03 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881308
Feb  8 09:59:03 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881305
Feb  8 09:59:03 localhost kernel: EXT3-fs: hda1: 5 orphan inodes deleted
Feb  8 09:59:03 localhost kernel: EXT3-fs: recovery complete.
Feb  8 09:59:03 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  8 09:59:03 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  8 09:59:03 localhost kernel: EXT3 FS on hda1, internal journal
Feb  8 09:59:03 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  8 09:59:03 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  8 09:59:03 localhost kernel: ts: Compaq touchscreen protocol output
Feb  8 09:59:03 localhost kernel: hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  8 09:59:03 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  8 09:59:03 localhost kernel: parport: PnPBIOS parport detected.
Feb  8 09:59:03 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  8 09:59:03 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  8 09:59:03 localhost kernel: Capability LSM initialized
Feb  8 09:59:03 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  8 09:59:03 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  8 09:59:03 localhost kernel: cdrom: hdc: mrw address space DMA selected
Feb  8 09:59:03 localhost kernel: Real Time Clock Driver v1.12
Feb  8 09:59:03 localhost kernel: input: PC Speaker
Feb  8 09:59:03 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  8 09:59:03 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  8 09:59:03 localhost kernel: FDC 0 is a post-1991 82077
Feb  8 09:59:03 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  8 09:59:03 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  8 09:59:03 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  8 09:59:03 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  8 09:59:03 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  8 09:59:03 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  8 09:59:03 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  8 09:59:03 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  8 09:59:03 localhost kernel: usbcore: registered new driver usbfs
Feb  8 09:59:03 localhost kernel: usbcore: registered new driver hub
Feb  8 09:59:03 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  8 09:59:03 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  8 09:59:03 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  8 09:59:03 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  8 09:59:03 localhost kernel: hub 1-0:1.0: USB hub found
Feb  8 09:59:03 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  8 09:59:03 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  8 09:59:03 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  8 09:59:03 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  8 09:59:03 localhost kernel: hub 2-0:1.0: USB hub found
Feb  8 09:59:03 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  8 09:59:03 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  8 09:59:03 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  8 09:59:03 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  8 09:59:03 localhost kernel: hub 3-0:1.0: USB hub found
Feb  8 09:59:03 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  8 09:59:03 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  8 09:59:03 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f08a4000
Feb  8 09:59:03 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  8 09:59:03 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  8 09:59:03 localhost kernel: hub 4-0:1.0: USB hub found
Feb  8 09:59:03 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  8 09:59:03 localhost kernel: irda_init()
Feb  8 09:59:03 localhost kernel: NET: Registered protocol family 23
Feb  8 09:59:03 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  8 09:59:03 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  8 09:59:03 localhost kernel:          and report if it works on your machine.
Feb  8 09:59:03 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  8 09:59:03 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  8 09:59:03 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  8 09:59:03 localhost kernel: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Feb  8 09:59:03 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  8 09:59:03 localhost kernel: NET: Registered protocol family 17
Feb  8 09:59:03 localhost kernel: NET: Registered protocol family 10
Feb  8 09:59:03 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  8 09:59:03 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  8 09:59:04 localhost udev[2866]: creating device node '/dev/vcs1'
Feb  8 09:59:04 localhost udev[3023]: removing device node '/dev/vcs1'
Feb  8 09:59:04 localhost udev[2874]: creating device node '/dev/vcsa1'
Feb  8 09:59:04 localhost udev[3029]: removing device node '/dev/vcsa1'
Feb  8 09:59:04 localhost udev[3026]: creating device node '/dev/vcs1'
Feb  8 09:59:04 localhost udev[3035]: removing device node '/dev/vcs1'
Feb  8 09:59:04 localhost udev[3032]: creating device node '/dev/vcsa1'
Feb  8 09:59:04 localhost udev[3041]: removing device node '/dev/vcsa1'
Feb  8 09:59:04 localhost udev[3038]: creating device node '/dev/vcs1'
Feb  8 09:59:04 localhost udev[3056]: removing device node '/dev/vcs1'
Feb  8 09:59:04 localhost udev[3044]: creating device node '/dev/vcsa1'
Feb  8 09:59:04 localhost udev[3062]: removing device node '/dev/vcsa1'
Feb  8 09:59:04 localhost udev[3059]: creating device node '/dev/vcs1'
Feb  8 09:59:04 localhost udev[3065]: creating device node '/dev/vcsa1'
Feb  8 09:59:07 localhost postfix/postfix-script: starting the Postfix mail system
Feb  8 09:59:07 localhost postfix/master[3255]: daemon started -- version 2.1.3
Feb  8 09:59:07 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  8 09:59:07 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  8 09:59:07 localhost /usr/sbin/cron[3328]: (CRON) INFO (pidfile fd = 3)
Feb  8 09:59:07 localhost /usr/sbin/cron[3329]: (CRON) STARTUP (fork ok)
Feb  8 09:59:07 localhost /usr/sbin/cron[3329]: (CRON) INFO (Running @reboot jobs)
Feb  8 09:59:08 localhost udev[3373]: removing device node '/dev/vcs1'
Feb  8 09:59:08 localhost udev[3383]: removing device node '/dev/vcsa1'
Feb  8 09:59:09 localhost udev[3490]: creating device node '/dev/vcs5'
Feb  8 09:59:09 localhost udev[3491]: creating device node '/dev/vcsa5'
Feb  8 09:59:09 localhost udev[3502]: creating device node '/dev/vcs6'
Feb  8 09:59:09 localhost udev[3503]: creating device node '/dev/vcsa6'
Feb  8 09:59:09 localhost udev[3504]: creating device node '/dev/vcs7'
Feb  8 09:59:09 localhost udev[3505]: creating device node '/dev/vcsa7'
Feb  8 09:59:09 localhost udev[3525]: removing device node '/dev/vcs7'
Feb  8 09:59:09 localhost udev[3535]: removing device node '/dev/vcsa7'
Feb  8 09:59:09 localhost udev[3395]: creating device node '/dev/vcs1'
Feb  8 09:59:09 localhost udev[3403]: creating device node '/dev/vcsa1'
Feb  8 09:59:09 localhost udev[3411]: creating device node '/dev/vcs2'
Feb  8 09:59:09 localhost udev[3424]: creating device node '/dev/vcsa2'
Feb  8 09:59:09 localhost udev[3432]: creating device node '/dev/vcs3'
Feb  8 09:59:10 localhost udev[3440]: creating device node '/dev/vcsa3'
Feb  8 09:59:10 localhost udev[3448]: creating device node '/dev/vcs4'
Feb  8 09:59:10 localhost udev[3456]: creating device node '/dev/vcsa4'
Feb  8 09:59:10 localhost udev[3545]: creating device node '/dev/vcs7'
Feb  8 09:59:10 localhost udev[3553]: creating device node '/dev/vcsa7'
Feb  8 09:59:11 localhost kernel: eth0: no IPv6 routers present
Feb  8 09:59:26 localhost gconfd (rick-3634): starting (version 2.8.1), pid 3634 user 'rick'
Feb  8 09:59:27 localhost gconfd (rick-3634): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 09:59:27 localhost gconfd (rick-3634): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  8 09:59:27 localhost gconfd (rick-3634): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  8 09:59:37 localhost gconfd (rick-3634): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  8 10:01:02 localhost gconfd (root-3783): starting (version 2.8.1), pid 3783 user 'root'
Feb  8 10:01:02 localhost gconfd (root-3783): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 10:01:02 localhost gconfd (root-3783): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb  8 10:01:02 localhost gconfd (root-3783): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  8 10:06:22 localhost gconfd (rick-3634): Resolved address "xml::/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
Feb  8 10:06:22 localhost gconfd (rick-3634): None of the resolved addresses are writable; saving configuration settings will not be possible
Feb  8 10:17:01 localhost /USR/SBIN/CRON[4097]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  8 10:39:03 localhost -- MARK --
Feb  8 13:21:15 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  8 13:21:15 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  8 13:21:15 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  8 13:21:15 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  8 13:21:15 localhost kernel: Symbols match kernel version 2.6.8.
Feb  8 13:21:15 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  8 13:21:15 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  8 13:21:15 localhost kernel: BIOS-provided physical RAM map:
Feb  8 13:21:15 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  8 13:21:15 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  8 13:21:15 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  8 13:21:15 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  8 13:21:15 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  8 13:21:15 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  8 13:21:15 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  8 13:21:15 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  8 13:21:15 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  8 13:21:15 localhost kernel: 767MB LOWMEM available.
Feb  8 13:21:15 localhost kernel: found SMP MP-table at 000f4d70
Feb  8 13:21:15 localhost kernel: On node 0 totalpages: 196592
Feb  8 13:21:15 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  8 13:21:15 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  8 13:21:15 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  8 13:21:15 localhost kernel: DMI 2.3 present.
Feb  8 13:21:15 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  8 13:21:15 localhost kernel:     Virtual Wire compatibility mode.
Feb  8 13:21:15 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  8 13:21:15 localhost kernel: Processor #0 6:8 APIC version 17
Feb  8 13:21:15 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  8 13:21:15 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  8 13:21:15 localhost kernel: Processors: 1
Feb  8 13:21:15 localhost kernel: Built 1 zonelists
Feb  8 13:21:15 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  8 13:21:15 localhost kernel: Initializing CPU#0
Feb  8 13:21:15 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  8 13:21:15 localhost kernel: Detected 1675.682 MHz processor.
Feb  8 13:21:15 localhost kernel: Using tsc for high-res timesource
Feb  8 13:21:15 localhost kernel: Console: colour VGA+ 80x25
Feb  8 13:21:15 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  8 13:21:15 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  8 13:21:15 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  8 13:21:15 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  8 13:21:15 localhost kernel: Calibrating delay loop... 3301.37 BogoMIPS
Feb  8 13:21:15 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  8 13:21:15 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  8 13:21:15 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  8 13:21:15 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  8 13:21:15 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  8 13:21:15 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  8 13:21:15 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  8 13:21:15 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  8 13:21:15 localhost kernel: Enabling fast FPU save and restore... done.
Feb  8 13:21:15 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  8 13:21:15 localhost kernel: Checking 'hlt' instruction... OK.
Feb  8 13:21:15 localhost kernel: Checking for popad bug... OK.

---

### Post by rick_write_taiwan on 2005-02-09
Feb  8 13:21:15 localhost kernel: enabled ExtINT on CPU#0
Feb  8 13:21:15 localhost kernel: ESR value before enabling vector: 00000000
Feb  8 13:21:15 localhost kernel: ESR value after enabling vector: 00000000
Feb  8 13:21:15 localhost kernel: ENABLING IO-APIC IRQs
Feb  8 13:21:15 localhost kernel: Setting 2 in the phys_id_present_map
Feb  8 13:21:15 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  8 13:21:15 localhost kernel: init IO_APIC IRQs
Feb  8 13:21:15 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  8 13:21:15 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  8 13:21:15 localhost kernel: number of MP IRQ sources: 20.
Feb  8 13:21:15 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  8 13:21:15 localhost kernel: testing the IO APIC.......................
Feb  8 13:21:15 localhost kernel: IO APIC #2......
Feb  8 13:21:15 localhost kernel: .... register #00: 02000000
Feb  8 13:21:15 localhost kernel: .......    : physical APIC id: 02
Feb  8 13:21:15 localhost kernel: .......    : Delivery Type: 0
Feb  8 13:21:15 localhost kernel: .......    : LTS          : 0
Feb  8 13:21:15 localhost kernel: .... register #01: 00178003
Feb  8 13:21:15 localhost kernel: .......     : max redirection entries: 0017
Feb  8 13:21:15 localhost kernel: .......     : PRQ implemented: 1
Feb  8 13:21:15 localhost kernel: .......     : IO APIC version: 0003
Feb  8 13:21:15 localhost kernel: .... IRQ redirection table:
Feb  8 13:21:15 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  8 13:21:15 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  8 13:21:15 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  8 13:21:15 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  8 13:21:15 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  8 13:21:15 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  8 13:21:15 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  8 13:21:15 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  8 13:21:15 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  8 13:21:15 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  8 13:21:15 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  8 13:21:15 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  8 13:21:15 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  8 13:21:15 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  8 13:21:15 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  8 13:21:15 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  8 13:21:15 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  8 13:21:15 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  8 13:21:15 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  8 13:21:15 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  8 13:21:15 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  8 13:21:15 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  8 13:21:15 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  8 13:21:15 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  8 13:21:15 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  8 13:21:15 localhost kernel: Using vector-based indexing
Feb  8 13:21:15 localhost kernel: IRQ to pin mappings:
Feb  8 13:21:15 localhost kernel: IRQ0 -> 0:2
Feb  8 13:21:15 localhost kernel: IRQ1 -> 0:1
Feb  8 13:21:15 localhost kernel: IRQ3 -> 0:3
Feb  8 13:21:15 localhost kernel: IRQ4 -> 0:4
Feb  8 13:21:15 localhost kernel: IRQ6 -> 0:6
Feb  8 13:21:15 localhost kernel: IRQ7 -> 0:7
Feb  8 13:21:15 localhost kernel: IRQ8 -> 0:8
Feb  8 13:21:15 localhost kernel: IRQ9 -> 0:9
Feb  8 13:21:15 localhost kernel: IRQ12 -> 0:12
Feb  8 13:21:15 localhost kernel: IRQ13 -> 0:13
Feb  8 13:21:15 localhost kernel: IRQ14 -> 0:14
Feb  8 13:21:15 localhost kernel: IRQ15 -> 0:15
Feb  8 13:21:15 localhost kernel: IRQ145 -> 0:16
Feb  8 13:21:15 localhost kernel: IRQ153 -> 0:21
Feb  8 13:21:15 localhost kernel: IRQ161 -> 0:22
Feb  8 13:21:15 localhost kernel: IRQ169 -> 0:23
Feb  8 13:21:15 localhost kernel: .................................... done.
Feb  8 13:21:15 localhost kernel: Using local APIC timer interrupts.
Feb  8 13:21:15 localhost kernel: calibrating APIC timer ...
Feb  8 13:21:15 localhost kernel: ..... CPU clock speed is 1674.0839 MHz.
Feb  8 13:21:15 localhost kernel: ..... host bus clock speed is 267.0974 MHz.
Feb  8 13:21:15 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  8 13:21:15 localhost kernel: Freeing initrd memory: 4136k freed
Feb  8 13:21:15 localhost kernel: NET: Registered protocol family 16
Feb  8 13:21:15 localhost kernel: EISA bus registered
Feb  8 13:21:15 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  8 13:21:15 localhost kernel: PCI: Using configuration type 1
Feb  8 13:21:15 localhost kernel: mtrr: v2.0 (20020519)
Feb  8 13:21:15 localhost kernel: ACPI: Subsystem revision 20040816
Feb  8 13:21:15 localhost kernel: ACPI: Interpreter disabled.
Feb  8 13:21:15 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  8 13:21:15 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  8 13:21:15 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  8 13:21:15 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  8 13:21:15 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  8 13:21:15 localhost kernel: PCI: Probing PCI hardware
Feb  8 13:21:15 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  8 13:21:15 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  8 13:21:15 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  8 13:21:15 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  8 13:21:15 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  8 13:21:15 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  8 13:21:15 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  8 13:21:15 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  8 13:21:15 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  8 13:21:15 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  8 13:21:15 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  8 13:21:15 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  8 13:21:15 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  8 13:21:15 localhost kernel: devfs: boot_options: 0x0
Feb  8 13:21:15 localhost kernel: Initializing Cryptographic API
Feb  8 13:21:15 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  8 13:21:15 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  8 13:21:15 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  8 13:21:15 localhost kernel: isapnp: Scanning for PnP cards...
Feb  8 13:21:15 localhost kernel: isapnp: No Plug & Play device found
Feb  8 13:21:15 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  8 13:21:15 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  8 13:21:15 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  8 13:21:15 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  8 13:21:15 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  8 13:21:15 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  8 13:21:15 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  8 13:21:15 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  8 13:21:15 localhost kernel: EISA: Detected 0 cards.
Feb  8 13:21:15 localhost kernel: NET: Registered protocol family 2
Feb  8 13:21:15 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  8 13:21:15 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  8 13:21:15 localhost kernel: NET: Registered protocol family 8
Feb  8 13:21:15 localhost kernel: NET: Registered protocol family 20
Feb  8 13:21:15 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  8 13:21:15 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  8 13:21:15 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  8 13:21:15 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  8 13:21:15 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  8 13:21:15 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  8 13:21:15 localhost kernel: NET: Registered protocol family 1
Feb  8 13:21:15 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  8 13:21:15 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  8 13:21:15 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  8 13:21:15 localhost kernel: VP_IDE: chipset revision 6
Feb  8 13:21:15 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  8 13:21:15 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  8 13:21:15 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  8 13:21:15 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  8 13:21:15 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  8 13:21:15 localhost kernel: Using anticipatory io scheduler
Feb  8 13:21:15 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  8 13:21:15 localhost kernel: hda: max request size: 1024KiB
Feb  8 13:21:15 localhost kernel: hda: Host Protected Area detected.
Feb  8 13:21:15 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  8 13:21:15 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  8 13:21:15 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  8 13:21:15 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  8 13:21:15 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  8 13:21:15 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  8 13:21:15 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  8 13:21:15 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Feb  8 13:21:15 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  8 13:21:15 localhost kernel: EXT3-fs: hda1: orphan cleanup on readonly fs
Feb  8 13:21:15 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6882486
Feb  8 13:21:15 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881318
Feb  8 13:21:15 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881314
Feb  8 13:21:15 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881312
Feb  8 13:21:15 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881309
Feb  8 13:21:15 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881305
Feb  8 13:21:15 localhost kernel: EXT3-fs: hda1: 6 orphan inodes deleted
Feb  8 13:21:15 localhost kernel: EXT3-fs: recovery complete.
Feb  8 13:21:15 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  8 13:21:15 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  8 13:21:15 localhost kernel: EXT3 FS on hda1, internal journal
Feb  8 13:21:15 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  8 13:21:15 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  8 13:21:15 localhost kernel: hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  8 13:21:15 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  8 13:21:15 localhost kernel: ts: Compaq touchscreen protocol output
Feb  8 13:21:15 localhost kernel: parport: PnPBIOS parport detected.
Feb  8 13:21:15 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  8 13:21:15 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  8 13:21:15 localhost kernel: Capability LSM initialized
Feb  8 13:21:15 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  8 13:21:15 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  8 13:21:15 localhost kernel: cdrom: hdc: mrw address space DMA selected
Feb  8 13:21:15 localhost kernel: Real Time Clock Driver v1.12
Feb  8 13:21:15 localhost kernel: input: PC Speaker
Feb  8 13:21:15 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  8 13:21:15 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  8 13:21:15 localhost kernel: FDC 0 is a post-1991 82077
Feb  8 13:21:15 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  8 13:21:15 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  8 13:21:15 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  8 13:21:15 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  8 13:21:15 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  8 13:21:15 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  8 13:21:15 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  8 13:21:15 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  8 13:21:15 localhost kernel: usbcore: registered new driver usbfs
Feb  8 13:21:15 localhost kernel: usbcore: registered new driver hub
Feb  8 13:21:15 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  8 13:21:15 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  8 13:21:15 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  8 13:21:15 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  8 13:21:15 localhost kernel: hub 1-0:1.0: USB hub found
Feb  8 13:21:15 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  8 13:21:15 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  8 13:21:15 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  8 13:21:15 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  8 13:21:15 localhost kernel: hub 2-0:1.0: USB hub found
Feb  8 13:21:15 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  8 13:21:15 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  8 13:21:15 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800

---

### Post by rick_write_taiwan on 2005-02-09
Feb  8 13:21:15 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  8 13:21:15 localhost kernel: hub 3-0:1.0: USB hub found
Feb  8 13:21:15 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  8 13:21:15 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  8 13:21:15 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f093b000
Feb  8 13:21:15 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  8 13:21:15 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  8 13:21:15 localhost kernel: hub 4-0:1.0: USB hub found
Feb  8 13:21:15 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  8 13:21:15 localhost kernel: irda_init()
Feb  8 13:21:15 localhost kernel: NET: Registered protocol family 23
Feb  8 13:21:15 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  8 13:21:15 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  8 13:21:15 localhost kernel:          and report if it works on your machine.
Feb  8 13:21:15 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  8 13:21:15 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  8 13:21:15 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  8 13:21:15 localhost kernel: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Feb  8 13:21:15 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  8 13:21:15 localhost kernel: NET: Registered protocol family 17
Feb  8 13:21:15 localhost kernel: NET: Registered protocol family 10
Feb  8 13:21:15 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  8 13:21:15 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  8 13:21:16 localhost udev[2877]: creating device node '/dev/vcs1'
Feb  8 13:21:16 localhost udev[3034]: removing device node '/dev/vcs1'
Feb  8 13:21:16 localhost udev[2885]: creating device node '/dev/vcsa1'
Feb  8 13:21:16 localhost udev[3040]: removing device node '/dev/vcsa1'
Feb  8 13:21:16 localhost udev[3037]: creating device node '/dev/vcs1'
Feb  8 13:21:16 localhost udev[3046]: removing device node '/dev/vcs1'
Feb  8 13:21:16 localhost udev[3043]: creating device node '/dev/vcsa1'
Feb  8 13:21:16 localhost udev[3052]: removing device node '/dev/vcsa1'
Feb  8 13:21:16 localhost udev[3049]: creating device node '/dev/vcs1'
Feb  8 13:21:16 localhost udev[3067]: removing device node '/dev/vcs1'
Feb  8 13:21:16 localhost udev[3055]: creating device node '/dev/vcsa1'
Feb  8 13:21:16 localhost udev[3073]: removing device node '/dev/vcsa1'
Feb  8 13:21:16 localhost udev[3070]: creating device node '/dev/vcs1'
Feb  8 13:21:16 localhost udev[3076]: creating device node '/dev/vcsa1'
Feb  8 13:21:19 localhost postfix/postfix-script: starting the Postfix mail system
Feb  8 13:21:19 localhost postfix/master[3266]: daemon started -- version 2.1.3
Feb  8 13:21:19 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  8 13:21:19 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  8 13:21:19 localhost /usr/sbin/cron[3339]: (CRON) INFO (pidfile fd = 3)
Feb  8 13:21:19 localhost /usr/sbin/cron[3340]: (CRON) STARTUP (fork ok)
Feb  8 13:21:19 localhost /usr/sbin/cron[3340]: (CRON) INFO (Running @reboot jobs)
Feb  8 13:21:20 localhost udev[3384]: removing device node '/dev/vcs1'
Feb  8 13:21:20 localhost udev[3395]: removing device node '/dev/vcsa1'
Feb  8 13:21:20 localhost udev[3516]: creating device node '/dev/vcsa5'
Feb  8 13:21:20 localhost udev[3542]: creating device node '/dev/vcsa6'
Feb  8 13:21:20 localhost udev[3543]: creating device node '/dev/vcs7'
Feb  8 13:21:20 localhost udev[3544]: creating device node '/dev/vcsa7'
Feb  8 13:21:20 localhost udev[3565]: removing device node '/dev/vcsa6'
Feb  8 13:21:20 localhost udev[3571]: removing device node '/dev/vcsa7'
Feb  8 13:21:20 localhost udev[3574]: removing device node '/dev/vcs7'
Feb  8 13:21:21 localhost udev[3568]: creating device node '/dev/vcsa6'
Feb  8 13:21:21 localhost udev[3405]: creating device node '/dev/vcs1'
Feb  8 13:21:21 localhost udev[3419]: creating device node '/dev/vcsa1'
Feb  8 13:21:21 localhost udev[3427]: creating device node '/dev/vcs2'
Feb  8 13:21:21 localhost udev[3435]: creating device node '/dev/vcsa2'
Feb  8 13:21:21 localhost udev[3443]: creating device node '/dev/vcs3'
Feb  8 13:21:21 localhost udev[3451]: creating device node '/dev/vcsa3'
Feb  8 13:21:21 localhost udev[3459]: creating device node '/dev/vcs4'
Feb  8 13:21:21 localhost udev[3467]: creating device node '/dev/vcsa4'
Feb  8 13:21:21 localhost udev[3475]: creating device node '/dev/vcs5'
Feb  8 13:21:21 localhost udev[3517]: creating device node '/dev/vcs6'
Feb  8 13:21:21 localhost udev[3615]: removing device node '/dev/vcs6'
Feb  8 13:21:21 localhost udev[3618]: creating device node '/dev/vcs6'
Feb  8 13:21:22 localhost udev[3586]: creating device node '/dev/vcs7'
Feb  8 13:21:22 localhost udev[3594]: creating device node '/dev/vcsa7'
Feb  8 13:21:22 localhost kernel: eth0: no IPv6 routers present
Feb  8 13:21:39 localhost gconfd (rick-3685): starting (version 2.8.1), pid 3685 user 'rick'
Feb  8 13:21:39 localhost gconfd (rick-3685): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 13:21:39 localhost gconfd (rick-3685): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  8 13:21:39 localhost gconfd (rick-3685): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  8 13:21:49 localhost gconfd (rick-3685): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  8 13:41:15 localhost -- MARK --
Feb  8 14:01:15 localhost -- MARK --
Feb  8 14:13:40 localhost kernel: Unable to handle kernel paging request at virtual address 6e6f6994
Feb  8 14:13:40 localhost kernel:  printing eip:
Feb  8 14:13:40 localhost kernel: c01f850c
Feb  8 14:13:40 localhost kernel: *pde = 00000000
Feb  8 14:13:40 localhost kernel: Oops: 0000 [#1]
Feb  8 14:13:40 localhost kernel: PREEMPT 
Feb  8 14:13:40 localhost kernel: Modules linked in: proc_intf freq_table cpufreq_userspace cpufreq_powersave ipv6 af_packet via_rhine mii crc32 snd_via82xx snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore via_ircc irda crc_ccitt ehci_hcd uhci_hcd usbcore pci_hotplug via_agp agpgart analog gameport floppy pcspkr rtc md dm_mod capability commoncap parport_pc lp parport tsdev evdev ide_cd cdrom mousedev psmouse ext3 jbd ide_generic via82cxxx ide_disk ide_core unix font vesafb cfbcopyarea cfbimgblt cfbfillrect
Feb  8 14:13:40 localhost kernel: CPU:    0
Feb  8 14:13:40 localhost kernel: EIP:    0060:[sock_poll+22/29]    Not tainted
Feb  8 14:13:40 localhost kernel: EFLAGS: 00010282   (2.6.8.1-4-386) 
Feb  8 14:13:40 localhost kernel: EIP is at sock_poll+0x16/0x1d
Feb  8 14:13:40 localhost kernel: eax: ea0aa340   ebx: e75ca240   ecx: 6e6f6974   edx: e75ca240
Feb  8 14:13:40 localhost kernel: esi: 00000145   edi: e84c3920   ebp: 00000007   esp: e8b31f28
Feb  8 14:13:40 localhost kernel: ds: 007b   es: 007b   ss: 0068
Feb  8 14:13:40 localhost kernel: Process mixer_applet2 (pid: 3770, threadinfo=e8b30000 task=e786e1f0)
Feb  8 14:13:40 localhost kernel: Stack: e75ca240 ea0aa340 00000000 c015474c e75ca240 00000000 e84c38e0 00000000 
Feb  8 14:13:40 localhost kernel:        e8b31fa0 e84c38e0 c01547db 0000000b e84c38e8 e8b31f64 e8b31f68 00000000 
Feb  8 14:13:40 localhost kernel:        00000000 00000000 e84c38e0 000001f5 0819e208 c0154972 0000000b e84c38e0 
Feb  8 14:13:40 localhost kernel: Call Trace:
Feb  8 14:13:40 localhost kernel:  [do_pollfd+68/128] do_pollfd+0x44/0x80
Feb  8 14:13:40 localhost kernel:  [do_poll+83/177] do_poll+0x53/0xb1
Feb  8 14:13:40 localhost kernel:  [sys_poll+313/479] sys_poll+0x139/0x1df
Feb  8 14:13:40 localhost kernel:  [sys_gettimeofday+34/85] sys_gettimeofday+0x22/0x55
Feb  8 14:13:40 localhost kernel:  [__pollwait+0/154] __pollwait+0x0/0x9a
Feb  8 14:13:40 localhost kernel:  [sysenter_past_esp+82/113] sysenter_past_esp+0x52/0x71
Feb  8 14:13:40 localhost kernel: Code: ff 51 20 83 c4 0c c3 8b 54 24 04 8b 42 08 8b 40 08 83 e8 24 
Feb  8 16:59:18 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  8 16:59:18 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  8 16:59:18 localhost udev[2971]: creating device node '/dev/vcs1'
Feb  8 16:59:18 localhost udev[3000]: removing device node '/dev/vcs1'
Feb  8 16:59:18 localhost udev[2977]: creating device node '/dev/vcsa1'
Feb  8 16:59:18 localhost udev[3006]: removing device node '/dev/vcsa1'
Feb  8 16:59:18 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  8 16:59:18 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  8 16:59:18 localhost kernel: Symbols match kernel version 2.6.8.
Feb  8 16:59:18 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  8 16:59:18 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  8 16:59:18 localhost kernel: BIOS-provided physical RAM map:
Feb  8 16:59:18 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  8 16:59:18 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  8 16:59:18 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  8 16:59:18 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  8 16:59:18 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  8 16:59:18 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  8 16:59:18 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  8 16:59:18 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  8 16:59:18 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  8 16:59:18 localhost kernel: 767MB LOWMEM available.
Feb  8 16:59:18 localhost kernel: found SMP MP-table at 000f4d70
Feb  8 16:59:18 localhost kernel: On node 0 totalpages: 196592
Feb  8 16:59:18 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  8 16:59:18 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  8 16:59:18 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  8 16:59:19 localhost udev[3003]: creating device node '/dev/vcs1'
Feb  8 16:59:19 localhost udev[3015]: removing device node '/dev/vcs1'
Feb  8 16:59:19 localhost udev[3009]: creating device node '/dev/vcsa1'
Feb  8 16:59:19 localhost udev[3021]: removing device node '/dev/vcsa1'
Feb  8 16:59:18 localhost kernel: DMI 2.3 present.
Feb  8 16:59:19 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  8 16:59:19 localhost kernel:     Virtual Wire compatibility mode.
Feb  8 16:59:19 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  8 16:59:19 localhost kernel: Processor #0 6:8 APIC version 17
Feb  8 16:59:19 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  8 16:59:19 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  8 16:59:19 localhost kernel: Processors: 1
Feb  8 16:59:19 localhost kernel: Built 1 zonelists
Feb  8 16:59:19 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  8 16:59:19 localhost kernel: Initializing CPU#0
Feb  8 16:59:19 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  8 16:59:19 localhost kernel: Detected 1675.772 MHz processor.
Feb  8 16:59:19 localhost kernel: Using tsc for high-res timesource
Feb  8 16:59:19 localhost kernel: Console: colour VGA+ 80x25
Feb  8 16:59:19 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  8 16:59:19 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  8 16:59:19 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  8 16:59:19 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  8 16:59:19 localhost kernel: Calibrating delay loop... 3301.37 BogoMIPS
Feb  8 16:59:19 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  8 16:59:19 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  8 16:59:19 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  8 16:59:19 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  8 16:59:19 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  8 16:59:19 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  8 16:59:19 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  8 16:59:19 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  8 16:59:19 localhost kernel: Enabling fast FPU save and restore... done.
Feb  8 16:59:19 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  8 16:59:19 localhost kernel: Checking 'hlt' instruction... OK.
Feb  8 16:59:19 localhost kernel: Checking for popad bug... OK.
Feb  8 16:59:19 localhost kernel: enabled ExtINT on CPU#0
Feb  8 16:59:19 localhost kernel: ESR value before enabling vector: 00000000
Feb  8 16:59:19 localhost kernel: ESR value after enabling vector: 00000000
Feb  8 16:59:19 localhost kernel: ENABLING IO-APIC IRQs
Feb  8 16:59:19 localhost kernel: Setting 2 in the phys_id_present_map
Feb  8 16:59:19 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  8 16:59:19 localhost kernel: init IO_APIC IRQs
Feb  8 16:59:19 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  8 16:59:19 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  8 16:59:19 localhost kernel: number of MP IRQ sources: 20.
Feb  8 16:59:19 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  8 16:59:19 localhost kernel: testing the IO APIC.......................
Feb  8 16:59:19 localhost kernel: IO APIC #2......
Feb  8 16:59:19 localhost kernel: .... register #00: 02000000
Feb  8 16:59:19 localhost kernel: .......    : physical APIC id: 02
Feb  8 16:59:19 localhost kernel: .......    : Delivery Type: 0
Feb  8 16:59:19 localhost kernel: .......    : LTS          : 0
Feb  8 16:59:19 localhost kernel: .... register #01: 00178003
Feb  8 16:59:19 localhost kernel: .......     : max redirection entries: 0017
Feb  8 16:59:19 localhost kernel: .......     : PRQ implemented: 1
Feb  8 16:59:19 localhost kernel: .......     : IO APIC version: 0003
Feb  8 16:59:19 localhost kernel: .... IRQ redirection table:
Feb  8 16:59:19 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  8 16:59:19 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  8 16:59:19 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  8 16:59:19 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  8 16:59:19 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  8 16:59:19 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  8 16:59:19 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  8 16:59:19 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  8 16:59:19 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  8 16:59:19 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  8 16:59:19 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  8 16:59:19 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  8 16:59:19 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00

---

### Post by rick_write_taiwan on 2005-02-09
Feb  8 16:59:19 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  8 16:59:19 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  8 16:59:19 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  8 16:59:19 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  8 16:59:19 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  8 16:59:19 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  8 16:59:19 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  8 16:59:19 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  8 16:59:19 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  8 16:59:19 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  8 16:59:19 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  8 16:59:19 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  8 16:59:19 localhost kernel: Using vector-based indexing
Feb  8 16:59:19 localhost kernel: IRQ to pin mappings:
Feb  8 16:59:19 localhost kernel: IRQ0 -> 0:2
Feb  8 16:59:19 localhost kernel: IRQ1 -> 0:1
Feb  8 16:59:19 localhost kernel: IRQ3 -> 0:3
Feb  8 16:59:19 localhost kernel: IRQ4 -> 0:4
Feb  8 16:59:19 localhost kernel: IRQ6 -> 0:6
Feb  8 16:59:19 localhost kernel: IRQ7 -> 0:7
Feb  8 16:59:19 localhost kernel: IRQ8 -> 0:8
Feb  8 16:59:19 localhost kernel: IRQ9 -> 0:9
Feb  8 16:59:19 localhost kernel: IRQ12 -> 0:12
Feb  8 16:59:19 localhost kernel: IRQ13 -> 0:13
Feb  8 16:59:19 localhost kernel: IRQ14 -> 0:14
Feb  8 16:59:19 localhost kernel: IRQ15 -> 0:15
Feb  8 16:59:19 localhost kernel: IRQ145 -> 0:16
Feb  8 16:59:19 localhost kernel: IRQ153 -> 0:21
Feb  8 16:59:19 localhost kernel: IRQ161 -> 0:22
Feb  8 16:59:19 localhost kernel: IRQ169 -> 0:23
Feb  8 16:59:19 localhost kernel: .................................... done.
Feb  8 16:59:19 localhost kernel: Using local APIC timer interrupts.
Feb  8 16:59:19 localhost kernel: calibrating APIC timer ...
Feb  8 16:59:19 localhost kernel: ..... CPU clock speed is 1674.0844 MHz.
Feb  8 16:59:19 localhost kernel: ..... host bus clock speed is 267.0975 MHz.
Feb  8 16:59:19 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  8 16:59:19 localhost kernel: Freeing initrd memory: 4136k freed
Feb  8 16:59:19 localhost kernel: NET: Registered protocol family 16
Feb  8 16:59:19 localhost kernel: EISA bus registered
Feb  8 16:59:19 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  8 16:59:19 localhost kernel: PCI: Using configuration type 1
Feb  8 16:59:19 localhost kernel: mtrr: v2.0 (20020519)
Feb  8 16:59:19 localhost kernel: ACPI: Subsystem revision 20040816
Feb  8 16:59:19 localhost kernel: ACPI: Interpreter disabled.
Feb  8 16:59:19 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  8 16:59:19 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  8 16:59:19 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  8 16:59:19 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  8 16:59:19 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  8 16:59:19 localhost kernel: PCI: Probing PCI hardware
Feb  8 16:59:19 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  8 16:59:19 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  8 16:59:19 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  8 16:59:19 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  8 16:59:19 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  8 16:59:19 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  8 16:59:19 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  8 16:59:19 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  8 16:59:19 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  8 16:59:19 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  8 16:59:19 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  8 16:59:19 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  8 16:59:19 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  8 16:59:19 localhost kernel: devfs: boot_options: 0x0
Feb  8 16:59:19 localhost kernel: Initializing Cryptographic API
Feb  8 16:59:19 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  8 16:59:19 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  8 16:59:19 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  8 16:59:19 localhost kernel: isapnp: Scanning for PnP cards...
Feb  8 16:59:19 localhost kernel: isapnp: No Plug & Play device found
Feb  8 16:59:19 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  8 16:59:19 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  8 16:59:19 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  8 16:59:19 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  8 16:59:19 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  8 16:59:19 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  8 16:59:19 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  8 16:59:19 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  8 16:59:19 localhost kernel: EISA: Detected 0 cards.
Feb  8 16:59:19 localhost kernel: NET: Registered protocol family 2
Feb  8 16:59:19 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  8 16:59:19 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  8 16:59:19 localhost kernel: NET: Registered protocol family 8
Feb  8 16:59:19 localhost kernel: NET: Registered protocol family 20
Feb  8 16:59:19 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  8 16:59:19 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  8 16:59:19 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  8 16:59:19 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  8 16:59:19 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  8 16:59:19 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  8 16:59:19 localhost kernel: NET: Registered protocol family 1
Feb  8 16:59:19 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  8 16:59:19 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  8 16:59:19 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  8 16:59:19 localhost kernel: VP_IDE: chipset revision 6
Feb  8 16:59:19 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  8 16:59:19 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  8 16:59:19 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  8 16:59:19 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  8 16:59:19 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  8 16:59:19 localhost kernel: Using anticipatory io scheduler
Feb  8 16:59:19 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  8 16:59:19 localhost kernel: hda: max request size: 1024KiB
Feb  8 16:59:19 localhost kernel: hda: Host Protected Area detected.
Feb  8 16:59:19 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  8 16:59:19 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  8 16:59:19 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  8 16:59:19 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  8 16:59:19 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  8 16:59:19 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  8 16:59:19 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  8 16:59:19 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Feb  8 16:59:19 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  8 16:59:19 localhost kernel: EXT3-fs: hda1: orphan cleanup on readonly fs
Feb  8 16:59:19 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6882469
Feb  8 16:59:19 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881318
Feb  8 16:59:19 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881314
Feb  8 16:59:19 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881312
Feb  8 16:59:19 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881309
Feb  8 16:59:19 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881305
Feb  8 16:59:19 localhost kernel: EXT3-fs: hda1: 6 orphan inodes deleted
Feb  8 16:59:19 localhost kernel: EXT3-fs: recovery complete.
Feb  8 16:59:19 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  8 16:59:19 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  8 16:59:19 localhost kernel: EXT3 FS on hda1, internal journal
Feb  8 16:59:19 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  8 16:59:19 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  8 16:59:19 localhost kernel: ts: Compaq touchscreen protocol output
Feb  8 16:59:19 localhost kernel: hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  8 16:59:19 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  8 16:59:19 localhost kernel: parport: PnPBIOS parport detected.
Feb  8 16:59:19 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  8 16:59:19 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  8 16:59:19 localhost kernel: Capability LSM initialized
Feb  8 16:59:19 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  8 16:59:19 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  8 16:59:19 localhost kernel: cdrom: hdc: mrw address space DMA selected
Feb  8 16:59:19 localhost kernel: Real Time Clock Driver v1.12
Feb  8 16:59:19 localhost kernel: input: PC Speaker
Feb  8 16:59:19 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  8 16:59:19 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  8 16:59:19 localhost kernel: FDC 0 is a post-1991 82077
Feb  8 16:59:19 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  8 16:59:19 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  8 16:59:19 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  8 16:59:19 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  8 16:59:19 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  8 16:59:19 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  8 16:59:19 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  8 16:59:19 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  8 16:59:19 localhost kernel: usbcore: registered new driver usbfs
Feb  8 16:59:19 localhost kernel: usbcore: registered new driver hub
Feb  8 16:59:19 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  8 16:59:19 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  8 16:59:19 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  8 16:59:19 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  8 16:59:19 localhost kernel: hub 1-0:1.0: USB hub found
Feb  8 16:59:19 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  8 16:59:19 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  8 16:59:19 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  8 16:59:19 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  8 16:59:19 localhost kernel: hub 2-0:1.0: USB hub found
Feb  8 16:59:19 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  8 16:59:19 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  8 16:59:19 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  8 16:59:19 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  8 16:59:19 localhost kernel: hub 3-0:1.0: USB hub found
Feb  8 16:59:19 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  8 16:59:19 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  8 16:59:19 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f08a4000
Feb  8 16:59:19 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  8 16:59:19 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  8 16:59:19 localhost kernel: hub 4-0:1.0: USB hub found
Feb  8 16:59:19 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  8 16:59:19 localhost kernel: irda_init()
Feb  8 16:59:19 localhost kernel: NET: Registered protocol family 23
Feb  8 16:59:19 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  8 16:59:19 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  8 16:59:19 localhost kernel:          and report if it works on your machine.
Feb  8 16:59:19 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  8 16:59:19 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  8 16:59:19 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  8 16:59:19 localhost kernel: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Feb  8 16:59:19 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  8 16:59:19 localhost kernel: NET: Registered protocol family 17
Feb  8 16:59:19 localhost kernel: NET: Registered protocol family 10
Feb  8 16:59:19 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  8 16:59:19 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  8 16:59:19 localhost udev[3018]: creating device node '/dev/vcs1'
Feb  8 16:59:19 localhost udev[3024]: creating device node '/dev/vcsa1'
Feb  8 16:59:22 localhost postfix/postfix-script: starting the Postfix mail system
Feb  8 16:59:22 localhost postfix/master[3255]: daemon started -- version 2.1.3
Feb  8 16:59:22 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  8 16:59:22 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  8 16:59:22 localhost /usr/sbin/cron[3328]: (CRON) INFO (pidfile fd = 3)
Feb  8 16:59:22 localhost /usr/sbin/cron[3329]: (CRON) STARTUP (fork ok)
Feb  8 16:59:22 localhost /usr/sbin/cron[3329]: (CRON) INFO (Running @reboot jobs)
Feb  8 16:59:23 localhost udev[3465]: removing device node '/dev/vcs1'
Feb  8 16:59:23 localhost udev[3468]: removing device node '/dev/vcsa1'
Feb  8 16:59:24 localhost udev[3471]: creating device node '/dev/vcs3'

---

### Post by rick_write_taiwan on 2005-02-09
Feb  8 16:59:24 localhost udev[3472]: creating device node '/dev/vcsa3'
Feb  8 16:59:24 localhost udev[3473]: creating device node '/dev/vcs5'
Feb  8 16:59:24 localhost udev[3474]: creating device node '/dev/vcsa5'
Feb  8 16:59:24 localhost udev[3493]: creating device node '/dev/vcsa4'
Feb  8 16:59:24 localhost udev[3494]: creating device node '/dev/vcs2'
Feb  8 16:59:24 localhost udev[3495]: creating device node '/dev/vcsa2'
Feb  8 16:59:24 localhost udev[3475]: creating device node '/dev/vcs4'
Feb  8 16:59:24 localhost udev[3496]: creating device node '/dev/vcs1'
Feb  8 16:59:24 localhost udev[3497]: creating device node '/dev/vcsa1'
Feb  8 16:59:24 localhost udev[3498]: creating device node '/dev/vcs6'
Feb  8 16:59:24 localhost udev[3503]: creating device node '/dev/vcsa6'
Feb  8 16:59:24 localhost udev[3505]: creating device node '/dev/vcsa7'
Feb  8 16:59:24 localhost udev[3504]: creating device node '/dev/vcs7'
Feb  8 16:59:24 localhost udev[3548]: removing device node '/dev/vcs7'
Feb  8 16:59:24 localhost udev[3551]: removing device node '/dev/vcsa7'
Feb  8 16:59:24 localhost udev[3562]: creating device node '/dev/vcs7'
Feb  8 16:59:24 localhost udev[3569]: creating device node '/dev/vcsa7'
Feb  8 16:59:27 localhost kernel: eth0: no IPv6 routers present
Feb  8 16:59:42 localhost gconfd (rick-3634): starting (version 2.8.1), pid 3634 user 'rick'
Feb  8 16:59:42 localhost gconfd (rick-3634): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 16:59:42 localhost gconfd (rick-3634): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  8 16:59:42 localhost gconfd (rick-3634): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  8 16:59:53 localhost gconfd (rick-3634): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  8 17:17:01 localhost /USR/SBIN/CRON[3989]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  8 17:29:32 localhost gconfd (rick-3634): Exiting
Feb  8 17:29:32 localhost gconfd (rick-4213): starting (version 2.8.1), pid 4213 user 'rick'
Feb  8 17:29:32 localhost gconfd (rick-4213): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 17:29:32 localhost gconfd (rick-4213): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  8 17:29:32 localhost gconfd (rick-4213): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  8 17:29:32 localhost gdm[3352]: Master halting...
Feb  8 17:29:33 localhost udev[4225]: removing device node '/dev/vcs7'
Feb  8 17:29:33 localhost udev[4235]: removing device node '/dev/vcsa7'
Feb  8 17:29:33 localhost shutdown[3352]: shutting down for system halt
Feb  8 17:29:33 localhost init: Switching to runlevel: 0
Feb  8 17:29:33 localhost udev[4247]: removing device node '/dev/vcs2'
Feb  8 17:29:33 localhost udev[4257]: removing device node '/dev/vcsa2'
Feb  8 17:29:33 localhost udev[4267]: removing device node '/dev/vcs3'
Feb  8 17:29:33 localhost udev[4277]: removing device node '/dev/vcsa3'
Feb  8 17:29:33 localhost udev[4287]: removing device node '/dev/vcs4'
Feb  8 17:29:33 localhost udev[4329]: removing device node '/dev/vcsa4'
Feb  8 17:29:33 localhost udev[4332]: removing device node '/dev/vcs5'
Feb  8 17:29:33 localhost udev[4345]: removing device node '/dev/vcsa5'
Feb  8 17:29:33 localhost udev[4348]: removing device node '/dev/vcs6'
Feb  8 17:29:33 localhost udev[4351]: removing device node '/dev/vcsa6'
Feb  8 17:29:33 localhost udev[4354]: removing device node '/dev/vcs1'
Feb  8 17:29:33 localhost udev[4357]: removing device node '/dev/vcsa1'
Feb  8 17:29:34 localhost postfix/postfix-script: stopping the Postfix mail system
Feb  8 17:29:34 localhost postfix/master[3255]: terminating on signal 15
Feb  8 17:29:35 localhost udev[4368]: creating device node '/dev/vcs1'
Feb  8 17:29:35 localhost udev[4376]: creating device node '/dev/vcsa1'
Feb  8 17:29:36 localhost kernel: Kernel logging (proc) stopped.
Feb  8 17:29:36 localhost kernel: Kernel log daemon terminating.
Feb  8 17:29:36 localhost exiting on signal 15
Feb  9 08:53:27 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  9 08:53:27 localhost udev[2936]: creating device node '/dev/vcs1'
Feb  9 08:53:27 localhost udev[2937]: creating device node '/dev/vcsa1'
Feb  9 08:53:27 localhost udev[2961]: removing device node '/dev/vcsa1'
Feb  9 08:53:27 localhost udev[2956]: removing device node '/dev/vcs1'
Feb  9 08:53:27 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  9 08:53:27 localhost udev[2964]: creating device node '/dev/vcsa1'
Feb  9 08:53:27 localhost udev[2965]: creating device node '/dev/vcs1'
Feb  9 08:53:27 localhost udev[2988]: removing device node '/dev/vcsa1'
Feb  9 08:53:27 localhost udev[2994]: removing device node '/dev/vcs1'
Feb  9 08:53:27 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  9 08:53:27 localhost udev[2993]: creating device node '/dev/vcsa1'
Feb  9 08:53:27 localhost udev[3011]: removing device node '/dev/vcsa1'
Feb  9 08:53:27 localhost udev[2997]: creating device node '/dev/vcs1'
Feb  9 08:53:27 localhost udev[3017]: removing device node '/dev/vcs1'
Feb  9 08:53:27 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  9 08:53:27 localhost kernel: Symbols match kernel version 2.6.8.
Feb  9 08:53:27 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  9 08:53:27 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  9 08:53:27 localhost kernel: BIOS-provided physical RAM map:
Feb  9 08:53:27 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  9 08:53:27 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  9 08:53:27 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  9 08:53:27 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Feb  9 08:53:27 localhost kernel:  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
Feb  9 08:53:27 localhost kernel:  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
Feb  9 08:53:27 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  9 08:53:27 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  9 08:53:27 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  9 08:53:27 localhost kernel: 767MB LOWMEM available.
Feb  9 08:53:27 localhost kernel: found SMP MP-table at 000f4d70
Feb  9 08:53:27 localhost kernel: On node 0 totalpages: 196592
Feb  9 08:53:27 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  9 08:53:27 localhost kernel:   Normal zone: 192496 pages, LIFO batch:16
Feb  9 08:53:27 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  9 08:53:27 localhost kernel: DMI 2.3 present.
Feb  9 08:53:27 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  9 08:53:27 localhost kernel:     Virtual Wire compatibility mode.
Feb  9 08:53:27 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  9 08:53:27 localhost kernel: Processor #0 6:8 APIC version 17
Feb  9 08:53:27 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  9 08:53:27 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  9 08:53:27 localhost kernel: Processors: 1
Feb  9 08:53:27 localhost kernel: Built 1 zonelists
Feb  9 08:53:27 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  9 08:53:27 localhost kernel: Initializing CPU#0
Feb  9 08:53:27 localhost kernel: PID hash table entries: 4096 (order 12: 32768 bytes)
Feb  9 08:53:27 localhost kernel: Detected 1675.772 MHz processor.
Feb  9 08:53:27 localhost kernel: Using tsc for high-res timesource
Feb  9 08:53:27 localhost kernel: Console: colour VGA+ 80x25
Feb  9 08:53:27 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  9 08:53:27 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  9 08:53:27 localhost kernel: Memory: 771900k/786368k available (1337k kernel code, 13692k reserved, 732k data, 204k init, 0k highmem)
Feb  9 08:53:27 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  9 08:53:27 localhost kernel: Calibrating delay loop... 3301.37 BogoMIPS
Feb  9 08:53:27 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  9 08:53:27 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  9 08:53:27 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  9 08:53:27 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  9 08:53:27 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  9 08:53:27 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  9 08:53:27 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  9 08:53:27 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  9 08:53:27 localhost kernel: Enabling fast FPU save and restore... done.
Feb  9 08:53:27 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  9 08:53:27 localhost kernel: Checking 'hlt' instruction... OK.
Feb  9 08:53:27 localhost kernel: Checking for popad bug... OK.
Feb  9 08:53:27 localhost kernel: enabled ExtINT on CPU#0
Feb  9 08:53:27 localhost kernel: ESR value before enabling vector: 00000000
Feb  9 08:53:27 localhost kernel: ESR value after enabling vector: 00000000
Feb  9 08:53:27 localhost kernel: ENABLING IO-APIC IRQs
Feb  9 08:53:27 localhost kernel: Setting 2 in the phys_id_present_map
Feb  9 08:53:27 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  9 08:53:27 localhost kernel: init IO_APIC IRQs
Feb  9 08:53:27 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  9 08:53:27 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  9 08:53:27 localhost kernel: number of MP IRQ sources: 20.
Feb  9 08:53:27 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  9 08:53:27 localhost kernel: testing the IO APIC.......................
Feb  9 08:53:27 localhost kernel: IO APIC #2......
Feb  9 08:53:27 localhost kernel: .... register #00: 02000000
Feb  9 08:53:27 localhost kernel: .......    : physical APIC id: 02
Feb  9 08:53:27 localhost kernel: .......    : Delivery Type: 0
Feb  9 08:53:27 localhost kernel: .......    : LTS          : 0
Feb  9 08:53:27 localhost kernel: .... register #01: 00178003
Feb  9 08:53:27 localhost kernel: .......     : max redirection entries: 0017
Feb  9 08:53:27 localhost kernel: .......     : PRQ implemented: 1
Feb  9 08:53:27 localhost kernel: .......     : IO APIC version: 0003
Feb  9 08:53:27 localhost kernel: .... IRQ redirection table:
Feb  9 08:53:27 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  9 08:53:27 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  9 08:53:27 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  9 08:53:27 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  9 08:53:27 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  9 08:53:27 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  9 08:53:27 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  9 08:53:27 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  9 08:53:27 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  9 08:53:27 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  9 08:53:27 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  9 08:53:27 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  9 08:53:27 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  9 08:53:27 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  9 08:53:27 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  9 08:53:27 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  9 08:53:27 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  9 08:53:27 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  9 08:53:27 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  9 08:53:27 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  9 08:53:27 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  9 08:53:27 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  9 08:53:27 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  9 08:53:27 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  9 08:53:27 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  9 08:53:27 localhost kernel: Using vector-based indexing
Feb  9 08:53:27 localhost kernel: IRQ to pin mappings:
Feb  9 08:53:27 localhost kernel: IRQ0 -> 0:2
Feb  9 08:53:27 localhost kernel: IRQ1 -> 0:1
Feb  9 08:53:27 localhost kernel: IRQ3 -> 0:3
Feb  9 08:53:27 localhost kernel: IRQ4 -> 0:4
Feb  9 08:53:27 localhost kernel: IRQ6 -> 0:6
Feb  9 08:53:27 localhost kernel: IRQ7 -> 0:7
Feb  9 08:53:27 localhost kernel: IRQ8 -> 0:8
Feb  9 08:53:27 localhost kernel: IRQ9 -> 0:9
Feb  9 08:53:27 localhost kernel: IRQ12 -> 0:12
Feb  9 08:53:27 localhost kernel: IRQ13 -> 0:13
Feb  9 08:53:27 localhost kernel: IRQ14 -> 0:14
Feb  9 08:53:27 localhost kernel: IRQ15 -> 0:15
Feb  9 08:53:27 localhost kernel: IRQ145 -> 0:16
Feb  9 08:53:27 localhost kernel: IRQ153 -> 0:21
Feb  9 08:53:27 localhost kernel: IRQ161 -> 0:22
Feb  9 08:53:27 localhost kernel: IRQ169 -> 0:23
Feb  9 08:53:27 localhost kernel: .................................... done.
Feb  9 08:53:27 localhost kernel: Using local APIC timer interrupts.
Feb  9 08:53:27 localhost kernel: calibrating APIC timer ...
Feb  9 08:53:27 localhost kernel: ..... CPU clock speed is 1674.0839 MHz.
Feb  9 08:53:27 localhost kernel: ..... host bus clock speed is 267.0974 MHz.
Feb  9 08:53:27 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  9 08:53:27 localhost kernel: Freeing initrd memory: 4136k freed
Feb  9 08:53:27 localhost kernel: NET: Registered protocol family 16
Feb  9 08:53:27 localhost kernel: EISA bus registered
Feb  9 08:53:27 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  9 08:53:27 localhost kernel: PCI: Using configuration type 1
Feb  9 08:53:27 localhost kernel: mtrr: v2.0 (20020519)
Feb  9 08:53:27 localhost kernel: ACPI: Subsystem revision 20040816
Feb  9 08:53:27 localhost kernel: ACPI: Interpreter disabled.
Feb  9 08:53:27 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay

---

### Post by rick_write_taiwan on 2005-02-09
Feb  9 08:53:27 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  9 08:53:27 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  9 08:53:27 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  9 08:53:27 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  9 08:53:27 localhost kernel: PCI: Probing PCI hardware
Feb  9 08:53:27 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  9 08:53:27 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  9 08:53:27 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  9 08:53:27 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  9 08:53:27 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  9 08:53:27 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  9 08:53:27 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  9 08:53:27 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  9 08:53:27 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  9 08:53:27 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  9 08:53:27 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  9 08:53:27 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  9 08:53:27 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  9 08:53:27 localhost kernel: devfs: boot_options: 0x0
Feb  9 08:53:27 localhost kernel: Initializing Cryptographic API
Feb  9 08:53:27 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  9 08:53:27 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  9 08:53:27 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  9 08:53:27 localhost kernel: isapnp: Scanning for PnP cards...
Feb  9 08:53:27 localhost kernel: isapnp: No Plug & Play device found
Feb  9 08:53:27 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  9 08:53:27 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  9 08:53:27 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  9 08:53:27 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  9 08:53:27 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  9 08:53:27 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  9 08:53:27 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  9 08:53:27 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  9 08:53:27 localhost kernel: EISA: Detected 0 cards.
Feb  9 08:53:27 localhost kernel: NET: Registered protocol family 2
Feb  9 08:53:27 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb  9 08:53:27 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb  9 08:53:27 localhost kernel: NET: Registered protocol family 8
Feb  9 08:53:27 localhost kernel: NET: Registered protocol family 20
Feb  9 08:53:27 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  9 08:53:27 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  9 08:53:27 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  9 08:53:27 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  9 08:53:27 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  9 08:53:27 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  9 08:53:27 localhost kernel: NET: Registered protocol family 1
Feb  9 08:53:27 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  9 08:53:27 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  9 08:53:27 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  9 08:53:27 localhost kernel: VP_IDE: chipset revision 6
Feb  9 08:53:27 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  9 08:53:27 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  9 08:53:27 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  9 08:53:27 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  9 08:53:27 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  9 08:53:27 localhost kernel: Using anticipatory io scheduler
Feb  9 08:53:27 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  9 08:53:27 localhost kernel: hda: max request size: 1024KiB
Feb  9 08:53:27 localhost kernel: hda: Host Protected Area detected.
Feb  9 08:53:27 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  9 08:53:27 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  9 08:53:27 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  9 08:53:27 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  9 08:53:27 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  9 08:53:27 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  9 08:53:27 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  9 08:53:27 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  9 08:53:27 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  9 08:53:27 localhost kernel: EXT3 FS on hda1, internal journal
Feb  9 08:53:27 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Feb  9 08:53:27 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  9 08:53:27 localhost kernel: ts: Compaq touchscreen protocol output
Feb  9 08:53:27 localhost kernel: hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  9 08:53:27 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  9 08:53:27 localhost kernel: parport: PnPBIOS parport detected.
Feb  9 08:53:27 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  9 08:53:27 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  9 08:53:27 localhost kernel: Capability LSM initialized
Feb  9 08:53:27 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  9 08:53:27 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  9 08:53:27 localhost kernel: cdrom: hdc: mrw address space DMA selected
Feb  9 08:53:27 localhost kernel: Real Time Clock Driver v1.12
Feb  9 08:53:27 localhost udev[3014]: creating device node '/dev/vcsa1'
Feb  9 08:53:27 localhost kernel: input: PC Speaker
Feb  9 08:53:27 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  9 08:53:27 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  9 08:53:27 localhost kernel: FDC 0 is a post-1991 82077
Feb  9 08:53:27 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  9 08:53:27 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  9 08:53:27 localhost kernel: agpgart: Maximum main memory to use for agp memory: 690M
Feb  9 08:53:27 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  9 08:53:27 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  9 08:53:27 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  9 08:53:27 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  9 08:53:27 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  9 08:53:27 localhost kernel: usbcore: registered new driver usbfs
Feb  9 08:53:27 localhost kernel: usbcore: registered new driver hub
Feb  9 08:53:27 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  9 08:53:27 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  9 08:53:27 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  9 08:53:27 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  9 08:53:27 localhost kernel: hub 1-0:1.0: USB hub found
Feb  9 08:53:27 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  9 08:53:27 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  9 08:53:27 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  9 08:53:27 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  9 08:53:27 localhost kernel: hub 2-0:1.0: USB hub found
Feb  9 08:53:27 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  9 08:53:27 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  9 08:53:27 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  9 08:53:27 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  9 08:53:27 localhost kernel: hub 3-0:1.0: USB hub found
Feb  9 08:53:27 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  9 08:53:27 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  9 08:53:27 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem f08a4000
Feb  9 08:53:27 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  9 08:53:27 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  9 08:53:27 localhost kernel: hub 4-0:1.0: USB hub found
Feb  9 08:53:27 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  9 08:53:27 localhost kernel: irda_init()
Feb  9 08:53:27 localhost kernel: NET: Registered protocol family 23
Feb  9 08:53:27 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  9 08:53:27 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  9 08:53:27 localhost kernel:          and report if it works on your machine.
Feb  9 08:53:27 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  9 08:53:27 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  9 08:53:27 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  9 08:53:27 localhost kernel: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Feb  9 08:53:27 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  9 08:53:27 localhost kernel: NET: Registered protocol family 17
Feb  9 08:53:27 localhost kernel: NET: Registered protocol family 10
Feb  9 08:53:27 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  9 08:53:27 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  9 08:53:27 localhost udev[3020]: creating device node '/dev/vcs1'
Feb  9 08:53:30 localhost postfix/postfix-script: starting the Postfix mail system
Feb  9 08:53:30 localhost postfix/master[3243]: daemon started -- version 2.1.3
Feb  9 08:53:31 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  9 08:53:31 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  9 08:53:31 localhost /usr/sbin/cron[3316]: (CRON) INFO (pidfile fd = 3)
Feb  9 08:53:31 localhost /usr/sbin/cron[3317]: (CRON) STARTUP (fork ok)
Feb  9 08:53:31 localhost /usr/sbin/cron[3317]: (CRON) INFO (Running @reboot jobs)
Feb  9 08:53:32 localhost udev[3361]: removing device node '/dev/vcs1'
Feb  9 08:53:32 localhost udev[3372]: removing device node '/dev/vcsa1'
Feb  9 08:53:32 localhost udev[3478]: creating device node '/dev/vcs5'
Feb  9 08:53:32 localhost udev[3479]: creating device node '/dev/vcsa5'
Feb  9 08:53:32 localhost udev[3490]: creating device node '/dev/vcs6'
Feb  9 08:53:32 localhost udev[3491]: creating device node '/dev/vcsa6'
Feb  9 08:53:32 localhost udev[3492]: creating device node '/dev/vcs7'
Feb  9 08:53:32 localhost udev[3493]: creating device node '/dev/vcsa7'
Feb  9 08:53:32 localhost udev[3513]: removing device node '/dev/vcs7'
Feb  9 08:53:32 localhost udev[3523]: removing device node '/dev/vcsa7'
Feb  9 08:53:33 localhost udev[3383]: creating device node '/dev/vcs1'
Feb  9 08:53:33 localhost udev[3396]: creating device node '/dev/vcsa1'
Feb  9 08:53:33 localhost udev[3404]: creating device node '/dev/vcs2'
Feb  9 08:53:33 localhost udev[3412]: creating device node '/dev/vcsa2'
Feb  9 08:53:33 localhost udev[3420]: creating device node '/dev/vcs3'
Feb  9 08:53:33 localhost udev[3428]: creating device node '/dev/vcsa3'
Feb  9 08:53:33 localhost udev[3436]: creating device node '/dev/vcs4'
Feb  9 08:53:33 localhost udev[3444]: creating device node '/dev/vcsa4'
Feb  9 08:53:33 localhost udev[3533]: creating device node '/dev/vcs7'
Feb  9 08:53:33 localhost udev[3541]: creating device node '/dev/vcsa7'
Feb  9 08:53:34 localhost kernel: eth0: no IPv6 routers present
Feb  9 08:53:54 localhost gconfd (rick-3622): starting (version 2.8.1), pid 3622 user 'rick'
Feb  9 08:53:55 localhost gconfd (rick-3622): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  9 08:53:55 localhost gconfd (rick-3622): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  9 08:53:55 localhost gconfd (rick-3622): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  9 08:54:05 localhost gconfd (rick-3622): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  9 08:54:58 localhost gconfd (root-3735): starting (version 2.8.1), pid 3735 user 'root'
Feb  9 08:54:58 localhost gconfd (root-3735): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  9 08:54:58 localhost gconfd (root-3735): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb  9 08:54:58 localhost gconfd (root-3735): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  9 09:13:27 localhost -- MARK --
Feb  9 09:17:01 localhost /USR/SBIN/CRON[4055]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  9 09:33:27 localhost -- MARK --
Feb  9 09:53:27 localhost -- MARK --
Feb  9 10:03:34 localhost syslogd 1.4.1#14ubuntu4: restart.
Feb  9 10:03:34 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Feb  9 10:03:34 localhost udev[2980]: creating device node '/dev/vcs1'
Feb  9 10:03:34 localhost udev[3002]: removing device node '/dev/vcs1'
Feb  9 10:03:34 localhost udev[2986]: creating device node '/dev/vcsa1'
Feb  9 10:03:34 localhost udev[3008]: removing device node '/dev/vcsa1'
Feb  9 10:03:34 localhost kernel: Inspecting /boot/System.map-2.6.8.1-4-386
Feb  9 10:03:34 localhost udev[3005]: creating device node '/dev/vcs1'
Feb  9 10:03:34 localhost udev[3021]: removing device node '/dev/vcs1'
Feb  9 10:03:34 localhost udev[3011]: creating device node '/dev/vcsa1'
Feb  9 10:03:34 localhost udev[3027]: removing device node '/dev/vcsa1'
Feb  9 10:03:34 localhost kernel: Loaded 28209 symbols from /boot/System.map-2.6.8.1-4-386.
Feb  9 10:03:34 localhost kernel: Symbols match kernel version 2.6.8.
Feb  9 10:03:34 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  9 10:03:34 localhost kernel: Linux version 2.6.8.1-4-386 (buildd@rockhopper) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Fri Jan 14 11:19:34 UTC 2005
Feb  9 10:03:34 localhost kernel: BIOS-provided physical RAM map:
Feb  9 10:03:34 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb  9 10:03:34 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb  9 10:03:34 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  9 10:03:34 localhost kernel:  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
Feb  9 10:03:34 localhost kernel:  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
Feb  9 10:03:34 localhost kernel:  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
Feb  9 10:03:34 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  9 10:03:34 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  9 10:03:34 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)

---

### Post by rick_write_taiwan on 2005-02-09
Feb  9 10:03:34 localhost kernel: 511MB LOWMEM available.
Feb  9 10:03:34 localhost kernel: found SMP MP-table at 000f4d70
Feb  9 10:03:34 localhost kernel: On node 0 totalpages: 131056
Feb  9 10:03:34 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb  9 10:03:34 localhost kernel:   Normal zone: 126960 pages, LIFO batch:16
Feb  9 10:03:34 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Feb  9 10:03:34 localhost kernel: DMI 2.3 present.
Feb  9 10:03:34 localhost kernel: Intel MultiProcessor Specification v1.4
Feb  9 10:03:34 localhost kernel:     Virtual Wire compatibility mode.
Feb  9 10:03:34 localhost kernel: OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
Feb  9 10:03:34 localhost kernel: Processor #0 6:8 APIC version 17
Feb  9 10:03:34 localhost kernel: I/O APIC #2 Version 17 at 0xFEC00000.
Feb  9 10:03:34 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  9 10:03:34 localhost kernel: Processors: 1
Feb  9 10:03:34 localhost udev[3024]: creating device node '/dev/vcs1'
Feb  9 10:03:34 localhost udev[3030]: creating device node '/dev/vcsa1'
Feb  9 10:03:34 localhost kernel: Built 1 zonelists
Feb  9 10:03:34 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash acpi=off
Feb  9 10:03:34 localhost kernel: Initializing CPU#0
Feb  9 10:03:34 localhost kernel: PID hash table entries: 2048 (order 11: 16384 bytes)
Feb  9 10:03:34 localhost kernel: Detected 1675.772 MHz processor.
Feb  9 10:03:34 localhost kernel: Using tsc for high-res timesource
Feb  9 10:03:34 localhost kernel: Console: colour VGA+ 80x25
Feb  9 10:03:34 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  9 10:03:34 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  9 10:03:34 localhost kernel: Memory: 511868k/524224k available (1337k kernel code, 11568k reserved, 732k data, 204k init, 0k highmem)
Feb  9 10:03:34 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  9 10:03:34 localhost kernel: Calibrating delay loop... 3293.18 BogoMIPS
Feb  9 10:03:34 localhost kernel: Security Scaffold v1.0.0 initialized
Feb  9 10:03:34 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb  9 10:03:34 localhost kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
Feb  9 10:03:34 localhost kernel: CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
Feb  9 10:03:34 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  9 10:03:34 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Feb  9 10:03:34 localhost kernel: CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
Feb  9 10:03:34 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 01
Feb  9 10:03:34 localhost kernel: Enabling fast FPU save and restore... done.
Feb  9 10:03:34 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Feb  9 10:03:34 localhost kernel: Checking 'hlt' instruction... OK.
Feb  9 10:03:34 localhost kernel: Checking for popad bug... OK.
Feb  9 10:03:34 localhost kernel: enabled ExtINT on CPU#0
Feb  9 10:03:34 localhost kernel: ESR value before enabling vector: 00000000
Feb  9 10:03:34 localhost kernel: ESR value after enabling vector: 00000000
Feb  9 10:03:34 localhost kernel: ENABLING IO-APIC IRQs
Feb  9 10:03:34 localhost kernel: Setting 2 in the phys_id_present_map
Feb  9 10:03:34 localhost kernel: ...changing IO-APIC physical APIC ID to 2 ... ok.
Feb  9 10:03:34 localhost kernel: init IO_APIC IRQs
Feb  9 10:03:34 localhost kernel:  IO-APIC (apicid-pin) 2-0, 2-5, 2-10, 2-11, 2-17, 2-18, 2-19, 2-20 not connected.
Feb  9 10:03:34 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=0
Feb  9 10:03:34 localhost kernel: number of MP IRQ sources: 20.
Feb  9 10:03:34 localhost kernel: number of IO-APIC #2 registers: 24.
Feb  9 10:03:34 localhost kernel: testing the IO APIC.......................
Feb  9 10:03:34 localhost kernel: IO APIC #2......
Feb  9 10:03:34 localhost kernel: .... register #00: 02000000
Feb  9 10:03:34 localhost kernel: .......    : physical APIC id: 02
Feb  9 10:03:34 localhost kernel: .......    : Delivery Type: 0
Feb  9 10:03:34 localhost kernel: .......    : LTS          : 0
Feb  9 10:03:34 localhost kernel: .... register #01: 00178003
Feb  9 10:03:34 localhost kernel: .......     : max redirection entries: 0017
Feb  9 10:03:34 localhost kernel: .......     : PRQ implemented: 1
Feb  9 10:03:34 localhost kernel: .......     : IO APIC version: 0003
Feb  9 10:03:34 localhost kernel: .... IRQ redirection table:
Feb  9 10:03:34 localhost kernel:  NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
Feb  9 10:03:34 localhost kernel:  00 000 00  1    0    0   0   0    0    0    00
Feb  9 10:03:34 localhost kernel:  01 001 01  0    0    0   0   0    1    1    39
Feb  9 10:03:34 localhost kernel:  02 001 01  0    0    0   0   0    1    1    31
Feb  9 10:03:34 localhost kernel:  03 001 01  0    0    0   0   0    1    1    41
Feb  9 10:03:34 localhost kernel:  04 001 01  0    0    0   0   0    1    1    49
Feb  9 10:03:34 localhost kernel:  05 000 00  1    0    0   0   0    0    0    00
Feb  9 10:03:34 localhost kernel:  06 001 01  0    0    0   0   0    1    1    51
Feb  9 10:03:34 localhost kernel:  07 001 01  0    0    0   0   0    1    1    59
Feb  9 10:03:34 localhost kernel:  08 001 01  0    0    0   0   0    1    1    61
Feb  9 10:03:34 localhost kernel:  09 001 01  0    0    0   0   0    1    1    69
Feb  9 10:03:34 localhost kernel:  0a 000 00  1    0    0   0   0    0    0    00
Feb  9 10:03:34 localhost kernel:  0b 000 00  1    0    0   0   0    0    0    00
Feb  9 10:03:34 localhost kernel:  0c 001 01  0    0    0   0   0    1    1    71
Feb  9 10:03:34 localhost kernel:  0d 001 01  0    0    0   0   0    1    1    79
Feb  9 10:03:34 localhost kernel:  0e 001 01  0    0    0   0   0    1    1    81
Feb  9 10:03:34 localhost kernel:  0f 001 01  0    0    0   0   0    1    1    89
Feb  9 10:03:34 localhost kernel:  10 001 01  1    1    0   1   0    1    1    91
Feb  9 10:03:34 localhost kernel:  11 000 00  1    0    0   0   0    0    0    00
Feb  9 10:03:34 localhost kernel:  12 000 00  1    0    0   0   0    0    0    00
Feb  9 10:03:34 localhost kernel:  13 000 00  1    0    0   0   0    0    0    00
Feb  9 10:03:34 localhost kernel:  14 000 00  1    0    0   0   0    0    0    00
Feb  9 10:03:34 localhost kernel:  15 001 01  1    1    0   1   0    1    1    99
Feb  9 10:03:34 localhost kernel:  16 001 01  1    1    0   1   0    1    1    A1
Feb  9 10:03:34 localhost kernel:  17 001 01  1    1    0   1   0    1    1    A9
Feb  9 10:03:34 localhost kernel: Using vector-based indexing
Feb  9 10:03:34 localhost kernel: IRQ to pin mappings:
Feb  9 10:03:34 localhost kernel: IRQ0 -> 0:2
Feb  9 10:03:34 localhost kernel: IRQ1 -> 0:1
Feb  9 10:03:34 localhost kernel: IRQ3 -> 0:3
Feb  9 10:03:34 localhost kernel: IRQ4 -> 0:4
Feb  9 10:03:34 localhost kernel: IRQ6 -> 0:6
Feb  9 10:03:34 localhost kernel: IRQ7 -> 0:7
Feb  9 10:03:34 localhost kernel: IRQ8 -> 0:8
Feb  9 10:03:34 localhost kernel: IRQ9 -> 0:9
Feb  9 10:03:34 localhost kernel: IRQ12 -> 0:12
Feb  9 10:03:34 localhost kernel: IRQ13 -> 0:13
Feb  9 10:03:34 localhost kernel: IRQ14 -> 0:14
Feb  9 10:03:34 localhost kernel: IRQ15 -> 0:15
Feb  9 10:03:34 localhost kernel: IRQ145 -> 0:16
Feb  9 10:03:34 localhost kernel: IRQ153 -> 0:21
Feb  9 10:03:34 localhost kernel: IRQ161 -> 0:22
Feb  9 10:03:34 localhost kernel: IRQ169 -> 0:23
Feb  9 10:03:34 localhost kernel: .................................... done.
Feb  9 10:03:34 localhost kernel: Using local APIC timer interrupts.
Feb  9 10:03:34 localhost kernel: calibrating APIC timer ...
Feb  9 10:03:34 localhost kernel: ..... CPU clock speed is 1674.0839 MHz.
Feb  9 10:03:34 localhost kernel: ..... host bus clock speed is 267.0974 MHz.
Feb  9 10:03:34 localhost kernel: checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Feb  9 10:03:34 localhost kernel: Freeing initrd memory: 4136k freed
Feb  9 10:03:34 localhost kernel: NET: Registered protocol family 16
Feb  9 10:03:34 localhost kernel: EISA bus registered
Feb  9 10:03:34 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfa400, last bus=1
Feb  9 10:03:34 localhost kernel: PCI: Using configuration type 1
Feb  9 10:03:34 localhost kernel: mtrr: v2.0 (20020519)
Feb  9 10:03:34 localhost kernel: ACPI: Subsystem revision 20040816
Feb  9 10:03:34 localhost kernel: ACPI: Interpreter disabled.
Feb  9 10:03:34 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  9 10:03:34 localhost kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb  9 10:03:34 localhost kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00fae40
Feb  9 10:03:34 localhost kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xae70, dseg 0xf0000
Feb  9 10:03:34 localhost kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb  9 10:03:34 localhost kernel: PCI: Probing PCI hardware
Feb  9 10:03:34 localhost kernel: PCI: Probing PCI hardware (bus 00)
Feb  9 10:03:34 localhost kernel: PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
Feb  9 10:03:34 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P0) -> 153
Feb  9 10:03:34 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P1) -> 153
Feb  9 10:03:34 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P2) -> 153
Feb  9 10:03:34 localhost kernel: PCI->APIC IRQ transform: (B0,I16,P3) -> 153
Feb  9 10:03:34 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P0) -> 161
Feb  9 10:03:34 localhost kernel: PCI->APIC IRQ transform: (B0,I17,P2) -> 161
Feb  9 10:03:34 localhost kernel: PCI->APIC IRQ transform: (B0,I18,P0) -> 169
Feb  9 10:03:34 localhost kernel: PCI->APIC IRQ transform: (B1,I0,P0) -> 145
Feb  9 10:03:34 localhost kernel: VFS: Disk quotas dquot_6.5.1
Feb  9 10:03:34 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  9 10:03:34 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb  9 10:03:34 localhost kernel: devfs: boot_options: 0x0
Feb  9 10:03:34 localhost kernel: Initializing Cryptographic API
Feb  9 10:03:34 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
Feb  9 10:03:34 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
Feb  9 10:03:34 localhost kernel: PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
Feb  9 10:03:34 localhost kernel: isapnp: Scanning for PnP cards...
Feb  9 10:03:34 localhost kernel: isapnp: No Plug & Play device found
Feb  9 10:03:34 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb  9 10:03:34 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  9 10:03:34 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  9 10:03:34 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb  9 10:03:34 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  9 10:03:34 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  9 10:03:34 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Feb  9 10:03:34 localhost kernel: EISA: Probing bus 0 at eisa0
Feb  9 10:03:34 localhost kernel: EISA: Detected 0 cards.
Feb  9 10:03:34 localhost kernel: NET: Registered protocol family 2
Feb  9 10:03:34 localhost kernel: IP: routing cache hash table of 4096 buckets, 32Kbytes
Feb  9 10:03:34 localhost kernel: TCP: Hash tables configured (established 32768 bind 65536)
Feb  9 10:03:34 localhost kernel: NET: Registered protocol family 8
Feb  9 10:03:34 localhost kernel: NET: Registered protocol family 20
Feb  9 10:03:34 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Feb  9 10:03:34 localhost kernel: RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb  9 10:03:34 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb  9 10:03:34 localhost kernel: Freeing unused kernel memory: 204k freed
Feb  9 10:03:34 localhost kernel: vesafb: probe of vesafb0 failed with error -6
Feb  9 10:03:34 localhost kernel: thermal: Unknown symbol acpi_processor_set_thermal_limit
Feb  9 10:03:34 localhost kernel: NET: Registered protocol family 1
Feb  9 10:03:34 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  9 10:03:34 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  9 10:03:34 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  9 10:03:34 localhost kernel: VP_IDE: chipset revision 6
Feb  9 10:03:34 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb  9 10:03:34 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  9 10:03:34 localhost kernel:     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  9 10:03:34 localhost kernel:     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  9 10:03:34 localhost kernel: hda: IC35L060AVV207-0, ATA DISK drive
Feb  9 10:03:34 localhost kernel: Using anticipatory io scheduler
Feb  9 10:03:34 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  9 10:03:34 localhost kernel: hda: max request size: 1024KiB
Feb  9 10:03:34 localhost kernel: hda: Host Protected Area detected.
Feb  9 10:03:34 localhost kernel: ^Icurrent capacity is 120096991 sectors (61489 MB)
Feb  9 10:03:34 localhost kernel: ^Inative  capacity is 120103200 sectors (61492 MB)
Feb  9 10:03:34 localhost kernel: hda: 120096991 sectors (61489 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Feb  9 10:03:34 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb  9 10:03:34 localhost kernel: hdc: COMBO-52X16C, ATAPI CD/DVD-ROM drive
Feb  9 10:03:34 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb  9 10:03:34 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  9 10:03:34 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Feb  9 10:03:34 localhost kernel: kjournald starting.  Commit interval 5 seconds
Feb  9 10:03:34 localhost kernel: EXT3-fs: hda1: orphan cleanup on readonly fs
Feb  9 10:03:34 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881318
Feb  9 10:03:34 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881315
Feb  9 10:03:34 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881312
Feb  9 10:03:34 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881308
Feb  9 10:03:34 localhost kernel: ext3_orphan_cleanup: deleting unreferenced inode 6881305
Feb  9 10:03:34 localhost kernel: EXT3-fs: hda1: 5 orphan inodes deleted
Feb  9 10:03:34 localhost kernel: EXT3-fs: recovery complete.
Feb  9 10:03:34 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb  9 10:03:34 localhost kernel: Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
Feb  9 10:03:34 localhost kernel: EXT3 FS on hda1, internal journal
Feb  9 10:03:34 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1

---

### Post by rick_write_taiwan on 2005-02-09
Feb  9 10:03:34 localhost kernel: mice: PS/2 mouse device common for all mice
Feb  9 10:03:34 localhost kernel: hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  9 10:03:34 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Feb  9 10:03:34 localhost kernel: ts: Compaq touchscreen protocol output
Feb  9 10:03:34 localhost kernel: parport: PnPBIOS parport detected.
Feb  9 10:03:34 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  9 10:03:34 localhost kernel: lp0: using parport0 (interrupt-driven).
Feb  9 10:03:34 localhost kernel: Capability LSM initialized
Feb  9 10:03:34 localhost kernel: device-mapper: 4.1.0-ioctl (2003-12-10) initialised: [email]dm@uk.sistina.com[/email]
Feb  9 10:03:34 localhost kernel: md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb  9 10:03:34 localhost kernel: cdrom: hdc: mrw address space DMA selected
Feb  9 10:03:34 localhost kernel: Real Time Clock Driver v1.12
Feb  9 10:03:34 localhost kernel: input: PC Speaker
Feb  9 10:03:34 localhost kernel: inserting floppy driver for 2.6.8.1-4-386
Feb  9 10:03:34 localhost kernel: Floppy drive(s): fd0 is 1.44M
Feb  9 10:03:34 localhost kernel: FDC 0 is a post-1991 82077
Feb  9 10:03:34 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb  9 10:03:34 localhost kernel: agpgart: Detected VIA KM400/KM400A chipset
Feb  9 10:03:34 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
Feb  9 10:03:34 localhost kernel: agpgart: AGP aperture is 128M @ 0xd0000000
Feb  9 10:03:34 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb  9 10:03:34 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  9 10:03:34 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb  9 10:03:34 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb  9 10:03:34 localhost kernel: usbcore: registered new driver usbfs
Feb  9 10:03:34 localhost kernel: usbcore: registered new driver hub
Feb  9 10:03:34 localhost kernel: USB Universal Host Controller Interface driver v2.2
Feb  9 10:03:34 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb  9 10:03:34 localhost kernel: uhci_hcd 0000:00:10.0: irq 153, io base 0000d000
Feb  9 10:03:34 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb  9 10:03:34 localhost kernel: hub 1-0:1.0: USB hub found
Feb  9 10:03:34 localhost kernel: hub 1-0:1.0: 2 ports detected
Feb  9 10:03:34 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb  9 10:03:34 localhost kernel: uhci_hcd 0000:00:10.1: irq 153, io base 0000d400
Feb  9 10:03:34 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb  9 10:03:34 localhost kernel: hub 2-0:1.0: USB hub found
Feb  9 10:03:34 localhost kernel: hub 2-0:1.0: 2 ports detected
Feb  9 10:03:34 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb  9 10:03:34 localhost kernel: uhci_hcd 0000:00:10.2: irq 153, io base 0000d800
Feb  9 10:03:34 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb  9 10:03:34 localhost kernel: hub 3-0:1.0: USB hub found
Feb  9 10:03:34 localhost kernel: hub 3-0:1.0: 2 ports detected
Feb  9 10:03:34 localhost kernel: ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
Feb  9 10:03:34 localhost kernel: ehci_hcd 0000:00:10.3: irq 153, pci mem e092a000
Feb  9 10:03:34 localhost kernel: ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb  9 10:03:34 localhost kernel: ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Feb  9 10:03:34 localhost kernel: hub 4-0:1.0: USB hub found
Feb  9 10:03:34 localhost kernel: hub 4-0:1.0: 6 ports detected
Feb  9 10:03:34 localhost kernel: irda_init()
Feb  9 10:03:34 localhost kernel: NET: Registered protocol family 23
Feb  9 10:03:34 localhost kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb  9 10:03:34 localhost kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb  9 10:03:34 localhost kernel:          and report if it works on your machine.
Feb  9 10:03:34 localhost kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb  9 10:03:34 localhost kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Feb  9 10:03:34 localhost kernel: eth0: VIA Rhine II at 0xe400, 00:0d:61:66:cd:88, IRQ 169.
Feb  9 10:03:34 localhost kernel: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Feb  9 10:03:34 localhost kernel: eth0: Setting full-duplex based on MII #1 link partner capability of 45e1.
Feb  9 10:03:34 localhost kernel: NET: Registered protocol family 17
Feb  9 10:03:34 localhost kernel: NET: Registered protocol family 10
Feb  9 10:03:34 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb  9 10:03:34 localhost kernel: IPv6 over IPv4 tunneling driver
Feb  9 10:03:38 localhost postfix/postfix-script: starting the Postfix mail system
Feb  9 10:03:38 localhost postfix/master[3264]: daemon started -- version 2.1.3
Feb  9 10:03:38 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb  9 10:03:38 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb  9 10:03:38 localhost /usr/sbin/cron[3337]: (CRON) INFO (pidfile fd = 3)
Feb  9 10:03:38 localhost /usr/sbin/cron[3338]: (CRON) STARTUP (fork ok)
Feb  9 10:03:38 localhost /usr/sbin/cron[3338]: (CRON) INFO (Running @reboot jobs)
Feb  9 10:03:39 localhost udev[3435]: removing device node '/dev/vcsa1'
Feb  9 10:03:39 localhost udev[3432]: removing device node '/dev/vcs1'
Feb  9 10:03:39 localhost udev[3438]: creating device node '/dev/vcsa1'
Feb  9 10:03:39 localhost udev[3439]: creating device node '/dev/vcs1'
Feb  9 10:03:39 localhost udev[3486]: creating device node '/dev/vcs2'
Feb  9 10:03:39 localhost udev[3487]: creating device node '/dev/vcs3'
Feb  9 10:03:39 localhost udev[3488]: creating device node '/dev/vcs4'
Feb  9 10:03:39 localhost udev[3489]: creating device node '/dev/vcs5'
Feb  9 10:03:39 localhost udev[3490]: creating device node '/dev/vcs6'
Feb  9 10:03:39 localhost udev[3491]: creating device node '/dev/vcsa3'
Feb  9 10:03:39 localhost udev[3492]: creating device node '/dev/vcsa4'
Feb  9 10:03:39 localhost udev[3510]: creating device node '/dev/vcsa6'
Feb  9 10:03:39 localhost udev[3511]: creating device node '/dev/vcsa2'
Feb  9 10:03:39 localhost udev[3493]: creating device node '/dev/vcsa5'
Feb  9 10:03:39 localhost udev[3517]: creating device node '/dev/vcs7'
Feb  9 10:03:39 localhost udev[3518]: creating device node '/dev/vcsa7'
Feb  9 10:03:39 localhost udev[3557]: removing device node '/dev/vcs7'
Feb  9 10:03:39 localhost udev[3560]: removing device node '/dev/vcsa7'
Feb  9 10:03:40 localhost udev[3571]: creating device node '/dev/vcs7'
Feb  9 10:03:40 localhost udev[3578]: creating device node '/dev/vcsa7'
Feb  9 10:03:41 localhost kernel: eth0: no IPv6 routers present
Feb  9 10:04:02 localhost gconfd (rick-3643): starting (version 2.8.1), pid 3643 user 'rick'
Feb  9 10:04:02 localhost gconfd (rick-3643): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  9 10:04:02 localhost gconfd (rick-3643): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 1
Feb  9 10:04:02 localhost gconfd (rick-3643): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  9 10:04:12 localhost gconfd (rick-3643): Resolved address "xml:readwrite:/home/rick/.gconf" to a writable configuration source at position 0
Feb  9 10:17:01 localhost /USR/SBIN/CRON[3927]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  9 10:43:34 localhost -- MARK --
Feb  9 11:03:34 localhost -- MARK --
Feb  9 11:17:01 localhost /USR/SBIN/CRON[4661]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  9 11:43:34 localhost -- MARK --
Feb  9 12:03:34 localhost -- MARK --
Feb  9 12:17:02 localhost /USR/SBIN/CRON[5385]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  9 12:43:34 localhost -- MARK --
Feb  9 12:57:19 localhost dhclient: DHCPREQUEST on eth0 to 10.10.2.1 port 67
Feb  9 12:57:19 localhost dhclient: DHCPACK from 10.10.2.1
Feb  9 12:57:19 localhost dhclient: bound to 222.157.8.60 -- renewal in 8195 seconds.
Feb  9 13:17:01 localhost /USR/SBIN/CRON[6141]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  9 13:43:34 localhost -- MARK --
Feb  9 14:03:34 localhost -- MARK --
Feb  9 14:17:01 localhost /USR/SBIN/CRON[6910]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb  9 14:43:34 localhost -- MARK --
Feb  9 14:44:24 localhost gconfd (root-7295): starting (version 2.8.1), pid 7295 user 'root'
Feb  9 14:44:24 localhost gconfd (root-7295): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  9 14:44:24 localhost gconfd (root-7295): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb  9 14:44:24 localhost gconfd (root-7295): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

---

### Post by rick_write_taiwan on 2005-02-09
Sorry about the wide pages due to control characters in the output.

The above goes for several days.

The logs from 7 February mention ACPI, but it seems to drop out after that, so I guess I had already switched it off after the 7th.

Comments welcome.

I am much obliged to anyone who actually takes the trouble to read through the logs.

---

