---
title: "Frequent Fiesty Freezes And More...."
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by likemindead on 2007-09-02
I just reinstalled Feisty on my laptop and I'm having a lot of problems:
[LIST=1]
[*]Sometimes it freezes up before I can even log in.
[*]Sometimes, if I do get past log in, after a couple of minutes my keyboard stops working altogether. Mouse still works though.
[*]Assuming I've logged in and my keyboard is still working (have to type in password) I try to download and install the 119 updates available through the Update Manager and my computer freezes up at some point during download.
[*]If I try to run a Live CD (either Feisty or Mint 3.0) I get a kernel panic or just long, weird lines of code that repeat over and over.
[*]If I try to reinstall, I get the same problems.
[*]When I shutdown, I get stuff like```
[  596.636000] atkbd serio0: shutdown
``` but it never shuts down. I have to power off manually.
[/LIST]

My computer is an Acer Aspire 3003LCi with a SiSM760GX chipset and a bcm4318 which has given me nothing but trouble.

Please help? What sys log can I look at to narrow down my problems?

Thanks so much in advance....

---

### Post by likemindead on 2007-09-02
Anyone? *Please?* My computer is  :evil:.

:::cough::: bumb :::cough:::

Here's what's in /var/log/syslog:

```
Sep  2 08:52:19 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  2 08:52:19 owner anacron[4763]: Job `cron.daily' terminated
Sep  2 08:52:20 owner NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth0: No such device 
Sep  2 08:52:36 owner kernel: [  416.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:53:06 owner kernel: [  446.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:53:36 owner kernel: [  476.556000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:54:06 owner kernel: [  506.552000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:54:20 owner firmware_helper[5464]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0b.0' with driver '(unknown)'
Sep  2 08:54:20 owner kernel: [  521.080000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Sep  2 08:54:23 owner NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth0: No such device 
Sep  2 08:54:36 owner kernel: [  536.552000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:55:07 owner kernel: [  566.644000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:55:08 owner gconfd (owner-4942): Exiting
Sep  2 08:55:08 owner gdm[4522]: Master halting...
Sep  2 08:55:19 owner init: Failed to open console: Input/output error
Sep  2 08:55:26 owner exiting on signal 15
Sep  2 13:43:42 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  2 13:43:42 owner kernel: Inspecting /boot/System.map-2.6.20-15-generic
Sep  2 13:43:42 owner kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Sep  2 13:43:42 owner kernel: Symbols match kernel version 2.6.20.
Sep  2 13:43:42 owner kernel: No module symbols loaded - kernel modules not enabled. 
Sep  2 13:43:42 owner kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Sep  2 13:43:42 owner kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  2 13:43:42 owner kernel: [    0.000000] sanitize start
Sep  2 13:43:42 owner kernel: [    0.000000] sanitize end
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000047df0000 end: 0000000047ef0000 type: 1
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000047ef0000 size: 000000000000a000 end: 0000000047efa000 type: 3
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000047efa000 size: 0000000000006000 end: 0000000047f00000 type: 4
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000047f00000 size: 0000000008100000 end: 0000000050000000 type: 2
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000047ef0000 (usable)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000047ef0000 - 0000000047efa000 (ACPI data)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000047efa000 - 0000000047f00000 (ACPI NVS)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000047f00000 - 0000000050000000 (reserved)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Sep  2 13:43:42 owner kernel: [    0.000000] 254MB HIGHMEM available.
Sep  2 13:43:42 owner kernel: [    0.000000] 896MB LOWMEM available.
Sep  2 13:43:42 owner kernel: [    0.000000] found SMP MP-table at 000f7fd0
Sep  2 13:43:42 owner kernel: [    0.000000] Entering add_active_range(0, 0, 294640) 0 entries of 256 used
Sep  2 13:43:42 owner kernel: [    0.000000] Zone PFN ranges:
Sep  2 13:43:42 owner kernel: [    0.000000]   DMA             0 ->     4096
Sep  2 13:43:42 owner kernel: [    0.000000]   Normal       4096 ->   229376
Sep  2 13:43:42 owner kernel: [    0.000000]   HighMem    229376 ->   294640
Sep  2 13:43:42 owner kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  2 13:43:42 owner kernel: [    0.000000]     0:        0 ->   294640
Sep  2 13:43:42 owner kernel: [    0.000000] On node 0 totalpages: 294640
Sep  2 13:43:42 owner kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep  2 13:43:42 owner kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep  2 13:43:42 owner kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep  2 13:43:42 owner kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Sep  2 13:43:42 owner kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Sep  2 13:43:42 owner kernel: [    0.000000]   HighMem zone: 509 pages used for memmap
Sep  2 13:43:42 owner kernel: [    0.000000]   HighMem zone: 64755 pages, LIFO batch:15
Sep  2 13:43:42 owner kernel: [    0.000000] DMI present.
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7f60
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x47ef619d
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: FADT (v001 SiS    755F     0x06040000 PTL  0x000f4240) @ 0x47ef9e3e
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x47ef9eb2
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x47ef9f88
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x47ef9fd8
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: DSDT (v001 PTLTD       755 0x06040000 MSFT 0x0100000e) @ 0x00000000
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  2 13:43:42 owner kernel: [    0.000000] Processor #0 15:12 APIC version 16
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  2 13:43:42 owner kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: IRQ2 used by override.
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: IRQ11 used by override.
Sep  2 13:43:42 owner kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  2 13:43:42 owner kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  2 13:43:42 owner kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aff00000)
Sep  2 13:43:42 owner kernel: [    0.000000] Detected 1800.153 MHz processor.
Sep  2 13:43:42 owner kernel: [   12.440237] Built 1 zonelists.  Total pages: 292339
Sep  2 13:43:42 owner kernel: [   12.440241] Kernel command line: root=UUID=36f4f755-b608-49ce-b11a-e96f60601f95 ro quiet splash
Sep  2 13:43:42 owner kernel: [   12.440382] mapped APIC to ffffd000 (fee00000)
Sep  2 13:43:42 owner kernel: [   12.440384] mapped IOAPIC to ffffc000 (fec00000)
Sep  2 13:43:42 owner kernel: [   12.440387] Enabling fast FPU save and restore... done.
Sep  2 13:43:42 owner kernel: [   12.440390] Enabling unmasked SIMD FPU exception support... done.
Sep  2 13:43:42 owner kernel: [   12.440397] Initializing CPU#0
Sep  2 13:43:42 owner kernel: [   12.440440] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  2 13:43:42 owner kernel: [   12.441200] Console: colour VGA+ 80x25
Sep  2 13:43:42 owner kernel: [   12.441783] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  2 13:43:42 owner kernel: [   12.442777] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  2 13:43:42 owner kernel: [   12.473238] Memory: 1157148k/1178560k available (1992k kernel code, 20492k reserved, 893k data, 328k init, 261056k highmem)
Sep  2 13:43:42 owner kernel: [   12.473249] virtual kernel memory layout:
Sep  2 13:43:42 owner kernel: [   12.473250]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep  2 13:43:42 owner kernel: [   12.473252]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  2 13:43:42 owner kernel: [   12.473253]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  2 13:43:42 owner kernel: [   12.473254]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  2 13:43:42 owner kernel: [   12.473255]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Sep  2 13:43:42 owner kernel: [   12.473257]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Sep  2 13:43:42 owner kernel: [   12.473258]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Sep  2 13:43:42 owner kernel: [   12.473261] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  2 13:43:42 owner kernel: [   12.552279] Calibrating delay using timer specific routine.. 3602.04 BogoMIPS (lpj=7204080)
Sep  2 13:43:42 owner kernel: [   12.552326] Security Framework v1.0.0 initialized
Sep  2 13:43:42 owner kernel: [   12.552335] SELinux:  Disabled at boot.
Sep  2 13:43:42 owner kernel: [   12.552351] Mount-cache hash table entries: 512
Sep  2 13:43:42 owner kernel: [   12.552502] CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000001 00000000 00000001
Sep  2 13:43:42 owner kernel: [   12.552511] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  2 13:43:42 owner kernel: [   12.552514] CPU: L2 Cache: 128K (64 bytes/line)
Sep  2 13:43:42 owner kernel: [   12.552517] CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000410 00000001 00000000 00000001
Sep  2 13:43:42 owner kernel: [   12.552528] Compat vDSO mapped to ffffe000.
Sep  2 13:43:42 owner kernel: [   12.552532] Remapping vsyscall page to ffffe000
Sep  2 13:43:42 owner kernel: [   12.552543] Checking 'hlt' instruction... OK.
Sep  2 13:43:42 owner kernel: [   12.568410] SMP alternatives: switching to UP code
Sep  2 13:43:42 owner kernel: [   12.568718] Freeing SMP alternatives: 11k freed
Sep  2 13:43:42 owner kernel: [   12.568979] Early unpacking initramfs... done
Sep  2 13:43:42 owner kernel: [   12.881262] ACPI: Core revision 20060707
Sep  2 13:43:42 owner kernel: [   12.881478] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep  2 13:43:42 owner kernel: [   12.885085] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
Sep  2 13:43:42 owner kernel: [   12.885105] Total of 1 processors activated (3602.04 BogoMIPS).
Sep  2 13:43:42 owner kernel: [   12.885258] ENABLING IO-APIC IRQs
Sep  2 13:43:42 owner kernel: [   12.885451] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  2 13:43:42 owner kernel: [   13.031611] Brought up 1 CPUs
Sep  2 13:43:42 owner kernel: [   13.031833] Booting paravirtualized kernel on bare hardware
Sep  2 13:43:42 owner kernel: [   13.031912] Time: 18:43:15  Date: 08/02/107
Sep  2 13:43:42 owner kernel: [   13.031947] NET: Registered protocol family 16
Sep  2 13:43:42 owner kernel: [   13.032050] EISA bus registered
Sep  2 13:43:42 owner kernel: [   13.032054] ACPI: bus type pci registered
Sep  2 13:43:42 owner kernel: [   13.032201] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
Sep  2 13:43:42 owner kernel: [   13.032203] PCI: Using configuration type 1
Sep  2 13:43:42 owner kernel: [   13.032205] Setting up standard PCI resources
Sep  2 13:43:42 owner kernel: [   13.034595] ACPI: Interpreter enabled
Sep  2 13:43:42 owner kernel: [   13.034599] ACPI: Using IOAPIC for interrupt routing
Sep  2 13:43:42 owner kernel: [   13.034938] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  2 13:43:42 owner kernel: [   13.034944] PCI: Probing PCI hardware (bus 00)
Sep  2 13:43:42 owner kernel: [   13.035992] Enabling SiS 96x SMBus.
Sep  2 13:43:42 owner kernel: [   13.036378] Boot video device is 0000:01:00.0
Sep  2 13:43:42 owner kernel: [   13.036440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  2 13:43:42 owner kernel: [   13.057919] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058098] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058273] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058442] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058632] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058802] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
Sep  2 13:43:42 owner kernel: [   13.058979] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Sep  2 13:43:42 owner kernel: [   13.059147] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
Sep  2 13:43:42 owner kernel: [   13.059434] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  2 13:43:42 owner kernel: [   13.059446] pnp: PnP ACPI init
Sep  2 13:43:42 owner kernel: [   13.061089] pnp: PnP ACPI: found 8 devices
Sep  2 13:43:42 owner kernel: [   13.061095] PnPBIOS: Disabled by ACPI PNP
Sep  2 13:43:42 owner kernel: [   13.061151] PCI: Using ACPI for IRQ routing
Sep  2 13:43:42 owner kernel: [   13.061154] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  2 13:43:42 owner kernel: [   13.063273] NET: Registered protocol family 8
Sep  2 13:43:42 owner kernel: [   13.063275] NET: Registered protocol family 20
Sep  2 13:43:42 owner kernel: [   13.063454] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
Sep  2 13:43:42 owner kernel: [   13.063458] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
Sep  2 13:43:42 owner kernel: [   13.063460] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
Sep  2 13:43:42 owner kernel: [   13.063463] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
Sep  2 13:43:42 owner kernel: [   13.063730] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
Sep  2 13:43:42 owner kernel: [   13.063734] PCI: Bridge: 0000:00:01.0
Sep  2 13:43:42 owner kernel: [   13.063737]   IO window: a000-afff
Sep  2 13:43:42 owner kernel: [   13.063741]   MEM window: e2100000-e21fffff
Sep  2 13:43:42 owner kernel: [   13.063744]   PREFETCH window: e8000000-efffffff
Sep  2 13:43:42 owner kernel: [   13.063749] PCI: Bus 2, cardbus bridge: 0000:00:06.0
Sep  2 13:43:42 owner kernel: [   13.063751]   IO window: 00002400-000024ff
Sep  2 13:43:42 owner kernel: [   13.063754]   IO window: 00002800-000028ff
Sep  2 13:43:42 owner kernel: [   13.063758]   PREFETCH window: 60000000-63ffffff
Sep  2 13:43:42 owner kernel: [   13.063762]   MEM window: 64000000-67ffffff
Sep  2 13:43:42 owner kernel: [   13.063778] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
Sep  2 13:43:42 owner kernel: [   13.063789] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 13:43:42 owner kernel: [   13.063830] NET: Registered protocol family 2
Sep  2 13:43:42 owner kernel: [   13.099565] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  2 13:43:42 owner kernel: [   13.099785] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  2 13:43:42 owner kernel: [   13.101122] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  2 13:43:42 owner kernel: [   13.101804] TCP: Hash tables configured (established 131072 bind 65536)
Sep  2 13:43:42 owner kernel: [   13.101809] TCP reno registered
Sep  2 13:43:42 owner kernel: [   13.111604] checking if image is initramfs... it is
Sep  2 13:43:42 owner kernel: [   13.727384] Freeing initrd memory: 6782k freed
Sep  2 13:43:42 owner kernel: [   13.727568] Simple Boot Flag at 0x38 set to 0x1
Sep  2 13:43:42 owner kernel: [   13.727826] audit: initializing netlink socket (disabled)
Sep  2 13:43:42 owner kernel: [   13.727840] audit(1188758595.368:1): initialized
Sep  2 13:43:42 owner kernel: [   13.727902] highmem bounce pool size: 64 pages
Sep  2 13:43:42 owner kernel: [   13.727983] VFS: Disk quotas dquot_6.5.1
Sep  2 13:43:42 owner kernel: [   13.728006] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  2 13:43:42 owner kernel: [   13.728065] io scheduler noop registered
Sep  2 13:43:42 owner kernel: [   13.728067] io scheduler anticipatory registered
Sep  2 13:43:42 owner kernel: [   13.728069] io scheduler deadline registered
Sep  2 13:43:42 owner kernel: [   13.728082] io scheduler cfq registered (default)
Sep  2 13:43:42 owner kernel: [   14.154199] isapnp: Scanning for PnP cards...
Sep  2 13:43:42 owner kernel: [   14.507074] isapnp: No Plug & Play device found
Sep  2 13:43:42 owner kernel: [   14.545808] Real Time Clock Driver v1.12ac
Sep  2 13:43:42 owner kernel: [   14.545846] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  2 13:43:42 owner kernel: [   14.546785] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 13:43:42 owner kernel: [   14.546793] ACPI: PCI interrupt for device 0000:00:02.6 disabled
Sep  2 13:43:42 owner kernel: [   14.546856] mice: PS/2 mouse device common for all mice
Sep  2 13:43:42 owner kernel: [   14.547293] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  2 13:43:42 owner kernel: [   14.547537] input: Macintosh mouse button emulation as /class/input/input0
Sep  2 13:43:42 owner kernel: [   14.547573] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep  2 13:43:42 owner kernel: [   14.547577] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep  2 13:43:42 owner kernel: [   14.547781] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  2 13:43:42 owner kernel: [   14.550382] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  2 13:43:42 owner kernel: [   14.550389] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  2 13:43:42 owner kernel: [   14.550544] EISA: Probing bus 0 at eisa.0
Sep  2 13:43:42 owner kernel: [   14.550555] Cannot allocate resource for EISA slot 1
Sep  2 13:43:42 owner kernel: [   14.550557] Cannot allocate resource for EISA slot 2
Sep  2 13:43:42 owner kernel: [   14.550575] Cannot allocate resource for EISA slot 8
Sep  2 13:43:42 owner kernel: [   14.550577] EISA: Detected 0 cards.
Sep  2 13:43:42 owner kernel: [   14.580622] TCP cubic registered
Sep  2 13:43:42 owner kernel: [   14.580632] NET: Registered protocol family 1
Sep  2 13:43:42 owner kernel: [   14.580656] Using IPI No-Shortcut mode
Sep  2 13:43:42 owner kernel: [   14.580721] ACPI: (supports S0 S3 S4 S5)
Sep  2 13:43:42 owner kernel: [   14.580755]   Magic number: 7:760:745
Sep  2 13:43:42 owner kernel: [   14.581205] Freeing unused kernel memory: 328k freed
Sep  2 13:43:42 owner kernel: [   14.581298] Time: tsc clocksource has been installed.
Sep  2 13:43:42 owner kernel: [   14.597763] input: AT Translated Set 2 keyboard as /class/input/input1
Sep  2 13:43:42 owner kernel: [   15.852860] Capability LSM initialized
Sep  2 13:43:42 owner kernel: [   15.900826] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 13:43:42 owner kernel: [   15.905568] ACPI: Thermal Zone [THRM] (32 C)
Sep  2 13:43:42 owner kernel: [   16.607765] usbcore: registered new interface driver usbfs
Sep  2 13:43:42 owner kernel: [   16.607787] usbcore: registered new interface driver hub
Sep  2 13:43:42 owner kernel: [   16.607806] usbcore: registered new device driver usb
Sep  2 13:43:42 owner kernel: [   16.608591] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Sep  2 13:43:42 owner kernel: [   16.608629] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 18
Sep  2 13:43:42 owner kernel: [   16.608641] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep  2 13:43:42 owner kernel: [   16.608777] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Sep  2 13:43:42 owner kernel: [   16.608797] ohci_hcd 0000:00:03.0: irq 18, io mem 0xe2002000
Sep  2 13:43:42 owner kernel: [   16.670400] usb usb1: configuration #1 chosen from 1 choice
Sep  2 13:43:42 owner kernel: [   16.670424] hub 1-0:1.0: USB hub found
Sep  2 13:43:42 owner kernel: [   16.670434] hub 1-0:1.0: 3 ports detected
Sep  2 13:43:42 owner kernel: [   16.707561] sis900.c: v1.08.10 Apr. 2 2006
Sep  2 13:43:42 owner kernel: [   16.774221] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 19
Sep  2 13:43:42 owner kernel: [   16.774241] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep  2 13:43:42 owner kernel: [   16.774262] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Sep  2 13:43:42 owner kernel: [   16.774282] ohci_hcd 0000:00:03.1: irq 19, io mem 0xe2003000
Sep  2 13:43:42 owner kernel: [    3.900000] Time: acpi_pm clocksource has been installed.
Sep  2 13:43:42 owner kernel: [    3.900000] usb usb2: configuration #1 chosen from 1 choice
Sep  2 13:43:42 owner kernel: [    3.900000] hub 2-0:1.0: USB hub found
Sep  2 13:43:42 owner kernel: [    3.900000] hub 2-0:1.0: 3 ports detected
Sep  2 13:43:42 owner kernel: [    4.004000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 20
Sep  2 13:43:42 owner kernel: [    4.004000] ehci_hcd 0000:00:03.2: EHCI Host Controller
Sep  2 13:43:42 owner kernel: [    4.004000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Sep  2 13:43:42 owner kernel: [    4.004000] PCI: cache line size of 64 is not supported by device 0000:00:03.2
Sep  2 13:43:42 owner kernel: [    4.004000] ehci_hcd 0000:00:03.2: irq 20, io mem 0xe2004000
Sep  2 13:43:42 owner kernel: [    4.004000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  2 13:43:42 owner kernel: [    4.004000] usb usb3: configuration #1 chosen from 1 choice
Sep  2 13:43:42 owner kernel: [    4.004000] hub 3-0:1.0: USB hub found
Sep  2 13:43:42 owner kernel: [    4.004000] hub 3-0:1.0: 6 ports detected
Sep  2 13:43:42 owner kernel: [    4.108000] SIS5513: IDE controller at PCI slot 0000:00:02.5
Sep  2 13:43:42 owner kernel: [    4.108000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 21
Sep  2 13:43:42 owner kernel: [    4.108000] SIS5513: chipset revision 0
Sep  2 13:43:42 owner kernel: [    4.108000] SIS5513: not 100%% native mode: will probe irqs later
Sep  2 13:43:42 owner kernel: [    4.108000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
Sep  2 13:43:42 owner kernel: [    4.108000]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
Sep  2 13:43:42 owner kernel: [    4.108000]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
Sep  2 13:43:42 owner kernel: [    4.108000] Probing IDE interface ide0...
Sep  2 13:43:42 owner kernel: [    4.396000] hda: TOSHIBA MK6025GAS, ATA DISK drive
Sep  2 13:43:42 owner kernel: [    4.692000] usb 1-2: new low speed USB device using ohci_hcd and address 3
Sep  2 13:43:42 owner kernel: [    4.900000] usb 1-2: configuration #1 chosen from 1 choice
Sep  2 13:43:42 owner kernel: [    4.916000] usbcore: registered new interface driver hiddev
Sep  2 13:43:42 owner kernel: [    4.928000] input: HID 1241:1166 as /class/input/input2
Sep  2 13:43:42 owner kernel: [    4.928000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:03.0-2
Sep  2 13:43:42 owner kernel: [    4.928000] usbcore: registered new interface driver usbhid
Sep  2 13:43:42 owner kernel: [    4.928000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Sep  2 13:43:42 owner kernel: [    5.068000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep  2 13:43:42 owner kernel: [    5.116000] Probing IDE interface ide1...
Sep  2 13:43:42 owner kernel: [    5.852000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
Sep  2 13:43:42 owner kernel: [    6.524000] ide1 at 0x170-0x177,0x376 on irq 15
Sep  2 13:43:42 owner kernel: [    6.528000] SCSI subsystem initialized
Sep  2 13:43:42 owner kernel: [    6.536000] libata version 2.20 loaded.
Sep  2 13:43:42 owner kernel: [    6.540000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 13:43:42 owner kernel: [    6.544000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Sep  2 13:43:42 owner kernel: [    6.552000] 0000:00:04.0: Using transceiver found at address 13 as default
Sep  2 13:43:42 owner kernel: [    6.552000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 16, 00:c0:9f:c1:44:ea.
Sep  2 13:43:42 owner kernel: [    6.564000] hda: max request size: 128KiB
Sep  2 13:43:42 owner kernel: [    6.572000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
Sep  2 13:43:42 owner kernel: [    6.572000] hda: cache flushes supported
Sep  2 13:43:42 owner kernel: [    6.572000]  hda: hda1 hda2 < hda5 >
Sep  2 13:43:42 owner kernel: [    6.664000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep  2 13:43:42 owner kernel: [    6.664000] Uniform CD-ROM driver Revision: 3.20
Sep  2 13:43:42 owner kernel: [    6.984000] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  2 13:43:42 owner kernel: [    6.984000] EXT3-fs: write access will be enabled during recovery.
Sep  2 13:43:42 owner kernel: [    9.252000] kjournald starting.  Commit interval 5 seconds
Sep  2 13:43:42 owner kernel: [    9.252000] EXT3-fs: recovery complete.
Sep  2 13:43:42 owner kernel: [    9.252000] EXT3-fs: mounted filesystem with ordered data mode.
Sep  2 13:43:42 owner kernel: [   23.324000] ieee80211_crypt: registered algorithm 'NULL'
Sep  2 13:43:42 owner kernel: [   23.344000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  2 13:43:42 owner kernel: [   23.348000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  2 13:43:42 owner kernel: [   23.396000] Linux agpgart interface v0.102 (c) Dave Jones
Sep  2 13:43:42 owner kernel: [   23.404000] agpgart: Detected AGP bridge 0
Sep  2 13:43:42 owner kernel: [   23.408000] agpgart: AGP aperture is 32M @ 0xe0000000
Sep  2 13:43:42 owner kernel: [   23.560000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
Sep  2 13:43:42 owner kernel: [   23.560000] Yenta: Using CSCINT to route CSC interrupts to PCI
Sep  2 13:43:42 owner kernel: [   23.560000] Yenta: Routing CardBus interrupts to PCI
Sep  2 13:43:42 owner kernel: [   23.560000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
Sep  2 13:43:42 owner kernel: [   23.564000] input: PC Speaker as /class/input/input3
Sep  2 13:43:42 owner kernel: [   23.600000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep  2 13:43:42 owner kernel: [   23.600000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep  2 13:43:42 owner kernel: [   23.668000] bcm43xx driver
Sep  2 13:43:42 owner kernel: [   23.792000] Yenta: ISA IRQ mask 0x06f8, PCI irq 16
Sep  2 13:43:42 owner kernel: [   23.792000] Socket status: 30000006
Sep  2 13:43:42 owner kernel: [   23.804000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
Sep  2 13:43:42 owner kernel: [   23.804000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  2 13:43:42 owner kernel: [   24.088000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 13:43:42 owner kernel: [   24.360000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Sep  2 13:43:42 owner kernel: [   24.396000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Sep  2 13:43:42 owner kernel: [   24.464000] cs: IO port probe 0x100-0x3af: clean.
Sep  2 13:43:42 owner kernel: [   24.468000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
Sep  2 13:43:42 owner kernel: [   24.468000] cs: IO port probe 0x820-0x8ff: clean.
Sep  2 13:43:42 owner kernel: [   24.468000] cs: IO port probe 0xc00-0xcf7: clean.
Sep  2 13:43:42 owner kernel: [   24.468000] cs: IO port probe 0xa00-0xaff: clean.
Sep  2 13:43:42 owner kernel: [   24.908000] intel8x0_measure_ac97_clock: measured 55455 usecs
Sep  2 13:43:42 owner kernel: [   24.908000] intel8x0: clocking to 48000
Sep  2 13:43:42 owner kernel: [   25.088000] lp: driver loaded but no devices found
Sep  2 13:43:42 owner kernel: [   25.164000] Adding 2441840k swap on /dev/disk/by-uuid/ed70067a-bce9-4fb6-907f-2c4c81db4df4.  Priority:-1 extents:1 across:2441840k
Sep  2 13:43:42 owner kernel: [   25.300000] EXT3 FS on hda1, internal journal
Sep  2 13:43:42 owner kernel: [   25.988000] ibm_acpi: ec object not found
Sep  2 13:43:42 owner kernel: [   26.044000] ACPI: Battery Slot [BAT1] (battery present)
Sep  2 13:43:42 owner kernel: [   26.084000] ACPI: AC Adapter [ACAD] (on-line)
Sep  2 13:43:42 owner kernel: [   26.128000] No dock devices found.
Sep  2 13:43:42 owner kernel: [   26.204000] Using specific hotkey driver
Sep  2 13:43:42 owner kernel: [   26.308000] input: Power Button (FF) as /class/input/input5
Sep  2 13:43:42 owner kernel: [   26.312000] ACPI: Power Button (FF) [PWRF]
Sep  2 13:43:42 owner kernel: [   26.348000] input: Lid Switch as /class/input/input6
Sep  2 13:43:42 owner kernel: [   26.356000] ACPI: Lid Switch [LID]
Sep  2 13:43:42 owner kernel: [   26.392000] input: Power Button (CM) as /class/input/input7
Sep  2 13:43:42 owner kernel: [   26.396000] ACPI: Power Button (CM) [PWRB]
Sep  2 13:43:42 owner kernel: [   26.436000] input: Sleep Button (CM) as /class/input/input8
Sep  2 13:43:42 owner kernel: [   26.440000] ACPI: Sleep Button (CM) [SLPB]
Sep  2 13:43:42 owner kernel: [   26.532000] pcc_acpi: loading...
Sep  2 13:43:42 owner kernel: [   26.780000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
Sep  2 13:43:42 owner kernel: [   26.780000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
Sep  2 13:43:42 owner kernel: [   26.780000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
Sep  2 13:43:42 owner kernel: [   26.780000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
Sep  2 13:43:45 owner kernel: [   29.684000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:43:45 owner kernel: [   29.700000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:43:45 owner kernel: [   29.732000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:43:45 owner dhcdbd: Started up.
Sep  2 13:43:45 owner NetworkManager: <information>^Istarting... 
Sep  2 13:43:45 owner kernel: [   29.956000] eth1: Media Link Off
Sep  2 13:43:45 owner NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'sis900'. 
Sep  2 13:43:45 owner NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Sep  2 13:43:45 owner avahi-daemon[4459]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Sep  2 13:43:45 owner avahi-daemon[4459]: Successfully dropped root privileges.
Sep  2 13:43:45 owner avahi-daemon[4459]: avahi-daemon 0.6.17 starting up.
Sep  2 13:43:45 owner avahi-daemon[4459]: Successfully called chroot().
Sep  2 13:43:45 owner avahi-daemon[4459]: Successfully dropped remaining capabilities.
Sep  2 13:43:45 owner avahi-daemon[4459]: No service found in /etc/avahi/services.
Sep  2 13:43:45 owner avahi-daemon[4459]: Network interface enumeration completed.
Sep  2 13:43:45 owner avahi-daemon[4459]: Registering HINFO record with values 'I686'/'LINUX'.
Sep  2 13:43:45 owner avahi-daemon[4459]: Server startup complete. Host name is owner.local. Local service cookie is 3052115148.
Sep  2 13:43:45 owner NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Sep  2 13:43:45 owner NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth1'. 
Sep  2 13:43:45 owner NetworkManager: <information>^IDeactivating device eth1. 
Sep  2 13:43:45 owner firmware_helper[4476]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0b.0' with driver '(unknown)'
Sep  2 13:43:45 owner kernel: [   30.100000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Sep  2 13:43:47 owner kernel: [   32.004000] ppdev: user-space parallel port driver
Sep  2 13:43:49 owner hpiod: 1.7.3 accepting connections at 2208... 
Sep  2 13:43:49 owner kernel: [   34.300000] apm: BIOS not found.
Sep  2 13:43:49 owner hcid[4705]: Bluetooth HCI daemon
Sep  2 13:43:49 owner kernel: [   34.496000] Bluetooth: Core ver 2.11
Sep  2 13:43:49 owner kernel: [   34.496000] NET: Registered protocol family 31
Sep  2 13:43:49 owner kernel: [   34.496000] Bluetooth: HCI device and connection manager initialized
Sep  2 13:43:49 owner kernel: [   34.496000] Bluetooth: HCI socket layer initialized
Sep  2 13:43:49 owner NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'bcm43xx'. 
Sep  2 13:43:49 owner NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Sep  2 13:43:49 owner kernel: [   34.532000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Sep  2 13:43:49 owner firmware_helper[4715]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0b.0' with driver '(unknown)'
Sep  2 13:43:49 owner hcid[4705]: Starting SDP server
Sep  2 13:43:49 owner kernel: [   34.544000] Bluetooth: L2CAP ver 2.8
Sep  2 13:43:49 owner kernel: [   34.544000] Bluetooth: L2CAP socket layer initialized
Sep  2 13:43:50 owner NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Sep  2 13:43:50 owner NetworkManager: <information>^INow managing wireless (802.11) device 'eth0'. 
Sep  2 13:43:50 owner NetworkManager: <information>^IDeactivating device eth0. 
Sep  2 13:43:50 owner NetworkManager: <debug info>^I[1188758630.002080] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Sep  2 13:43:50 owner kernel: [   34.636000] Bluetooth: RFCOMM socket layer initialized
Sep  2 13:43:50 owner kernel: [   34.636000] Bluetooth: RFCOMM TTY layer initialized
Sep  2 13:43:50 owner kernel: [   34.636000] Bluetooth: RFCOMM ver 1.8
Sep  2 13:43:50 owner anacron[4765]: Anacron 2.3 started on 2007-09-02
Sep  2 13:43:50 owner anacron[4765]: Will run job `cron.monthly' in 15 min.
Sep  2 13:43:50 owner anacron[4765]: Jobs will be executed sequentially
Sep  2 13:43:50 owner /usr/sbin/cron[4792]: (CRON) INFO (pidfile fd = 3)
Sep  2 13:43:50 owner /usr/sbin/cron[4793]: (CRON) STARTUP (fork ok)
Sep  2 13:43:50 owner /usr/sbin/cron[4793]: (CRON) INFO (Running @reboot jobs)
Sep  2 13:43:53 owner NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth0: No such device 
Sep  2 13:44:00 owner gconfd (owner-4944): starting (version 2.18.0.1), pid 4944 user 'owner'
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 13:44:02 owner kernel: [   47.108000] NET: Registered protocol family 10
Sep  2 13:44:02 owner kernel: [   47.108000] lo: Disabled Privacy Extensions
Sep  2 13:44:02 owner kernel: [   47.108000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep  2 13:44:08 owner NetworkManager: <information>^IUpdating allowed wireless network lists. 
Sep  2 13:44:09 owner NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep  2 13:44:09 owner gconfd (owner-4944): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 0
Sep  2 13:44:12 owner kernel: [   57.304000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:44:14 owner firmware_helper[5054]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0b.0' with driver '(unknown)'
Sep  2 13:44:14 owner kernel: [   58.620000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Sep  2 13:44:17 owner NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth0: No such device 
Sep  2 13:44:37 owner firmware_helper[5102]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0b.0' with driver '(unknown)'
Sep  2 13:44:37 owner kernel: [   82.396000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Sep  2 13:44:41 owner NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth0: No such device 
Sep  2 13:44:42 owner kernel: [   87.288000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:45:01 owner firmware_helper[5129]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0b.0' with driver '(unknown)'
Sep  2 13:45:01 owner kernel: [  105.632000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Sep  2 13:45:05 owner NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth0: No such device 
Sep  2 13:45:12 owner kernel: [  117.284000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:45:25 owner firmware_helper[5142]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0b.0' with driver '(unknown)'
Sep  2 13:45:25 owner kernel: [  130.128000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Sep  2 13:45:30 owner NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth0: No such device 
Sep  2 13:45:42 owner kernel: [  147.284000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:45:45 owner kernel: [  149.740000] usb 3-6: new high speed USB device using ehci_hcd and address 3
Sep  2 13:45:45 owner kernel: [  149.876000] usb 3-6: configuration #1 chosen from 1 choice
Sep  2 13:45:45 owner NetworkManager: <debug info>^I[1188758745.431318] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_12f7_1a00_075A1A93A655'). 
Sep  2 13:45:45 owner NetworkManager: <debug info>^I[1188758745.511508] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_12f7_1a00_075A1A93A655_if0'). 
Sep  2 13:45:45 owner NetworkManager: <debug info>^I[1188758745.538190] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_12f7_1a00_075A1A93A655_usbraw'). 
Sep  2 13:45:45 owner kernel: [  149.996000] usbcore: registered new interface driver libusual
Sep  2 13:45:45 owner kernel: [  150.096000] Initializing USB Mass Storage driver...
Sep  2 13:45:45 owner kernel: [  150.096000] scsi0 : SCSI emulation for USB Mass Storage devices
Sep  2 13:45:45 owner kernel: [  150.096000] usb-storage: device found at 3
Sep  2 13:45:45 owner kernel: [  150.096000] usb-storage: waiting for device to settle before scanning
Sep  2 13:45:45 owner kernel: [  150.100000] usbcore: registered new interface driver usb-storage
Sep  2 13:45:45 owner kernel: [  150.100000] USB Mass Storage support registered.
Sep  2 13:45:45 owner NetworkManager: <debug info>^I[1188758745.592456] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_12f7_1a00_075A1A93A655_if0_scsi_host'). 
Sep  2 13:45:50 owner kernel: [  154.616000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Sep  2 13:45:50 owner firmware_helper[5194]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0b.0' with driver '(unknown)'
Sep  2 13:45:50 owner kernel: [  155.096000] usb-storage: device scan complete
Sep  2 13:45:50 owner kernel: [  155.100000] scsi 0:0:0:0: Direct-Access     Memorex  Flashdrive 501B  PMAP PQ: 0 ANSI: 0 CCS
Sep  2 13:45:50 owner kernel: [  155.152000] SCSI device sda: 248096 512-byte hdwr sectors (127 MB)
Sep  2 13:45:50 owner kernel: [  155.156000] sda: Write Protect is off
Sep  2 13:45:50 owner kernel: [  155.156000] sda: Mode Sense: 23 00 00 00
Sep  2 13:45:50 owner kernel: [  155.156000] sda: assuming drive cache: write through
Sep  2 13:45:50 owner kernel: [  155.156000] SCSI device sda: 248096 512-byte hdwr sectors (127 MB)
Sep  2 13:45:50 owner kernel: [  155.156000] sda: Write Protect is off
Sep  2 13:45:50 owner kernel: [  155.156000] sda: Mode Sense: 23 00 00 00
Sep  2 13:45:50 owner kernel: [  155.156000] sda: assuming drive cache: write through
Sep  2 13:45:50 owner kernel: [  155.156000]  sda: sda1
Sep  2 13:45:50 owner kernel: [  155.160000] sd 0:0:0:0: Attached scsi removable disk sda
Sep  2 13:45:50 owner NetworkManager: <debug info>^I[1188758750.682801] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_12f7_1a00_075A1A93A655_if0_scsi_host_scsi_device_lun0'). 
Sep  2 13:45:50 owner kernel: [  155.188000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  2 13:45:51 owner NetworkManager: <debug info>^I[1188758751.117923] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_12f7_1a00_075A1A93A655_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Sep  2 13:45:51 owner NetworkManager: <debug info>^I[1188758751.131553] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Memorex_Flashdrive_501B_075A1A93A655_0_0'). 
Sep  2 13:45:51 owner NetworkManager: <debug info>^I[1188758751.168774] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_FCBE_B4EB'). 
Sep  2 13:45:51 owner hald: mounted /dev/sda1 on behalf of uid 1000
Sep  2 13:45:54 owner NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth0: No such device 
Sep  2 13:46:12 owner kernel: [  177.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:46:42 owner kernel: [  207.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:47:12 owner kernel: [  237.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
```

Does that help any?

:confused:

---

### Post by likemindead on 2007-09-02
Running

```
sudo /etc/init.d/powernowd stop
```

as soon as I boot stopped the freezes (for now) and let me update everything.

I could still use help getting things running correctly.

Here's the latest /var/log/messages if it'll help:

```
Sep  1 16:15:21 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  1 16:15:42 owner kernel: [  657.696000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:16:12 owner kernel: [  687.696000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:16:36 owner kernel: [  712.264000] usb 3-6: USB disconnect, address 3
Sep  1 16:16:42 owner kernel: [  717.696000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:16:47 owner gconfd (owner-4884): Exiting
Sep  1 16:16:56 owner exiting on signal 15
Sep  1 16:18:17 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  1 16:18:17 owner kernel: Inspecting /boot/System.map-2.6.20-15-generic
Sep  1 16:18:17 owner kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Sep  1 16:18:17 owner kernel: Symbols match kernel version 2.6.20.
Sep  1 16:18:17 owner kernel: No module symbols loaded - kernel modules not enabled. 
Sep  1 16:18:17 owner kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Sep  1 16:18:17 owner kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  1 16:18:17 owner kernel: [    0.000000] sanitize start
Sep  1 16:18:17 owner kernel: [    0.000000] sanitize end
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000047df0000 end: 0000000047ef0000 type: 1
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() start: 0000000047ef0000 size: 000000000000a000 end: 0000000047efa000 type: 3
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() start: 0000000047efa000 size: 0000000000006000 end: 0000000047f00000 type: 4
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() start: 0000000047f00000 size: 0000000008100000 end: 0000000050000000 type: 2
Sep  1 16:18:17 owner kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Sep  1 16:18:17 owner kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Sep  1 16:18:17 owner kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Sep  1 16:18:17 owner kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Sep  1 16:18:17 owner kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000047ef0000 (usable)
Sep  1 16:18:17 owner kernel: [    0.000000]  BIOS-e820: 0000000047ef0000 - 0000000047efa000 (ACPI data)
Sep  1 16:18:17 owner kernel: [    0.000000]  BIOS-e820: 0000000047efa000 - 0000000047f00000 (ACPI NVS)
Sep  1 16:18:17 owner kernel: [    0.000000]  BIOS-e820: 0000000047f00000 - 0000000050000000 (reserved)
Sep  1 16:18:17 owner kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Sep  1 16:18:17 owner kernel: [    0.000000] 254MB HIGHMEM available.
Sep  1 16:18:17 owner kernel: [    0.000000] 896MB LOWMEM available.
Sep  1 16:18:17 owner kernel: [    0.000000] found SMP MP-table at 000f7fd0
Sep  1 16:18:17 owner kernel: [    0.000000] Zone PFN ranges:
Sep  1 16:18:17 owner kernel: [    0.000000]   DMA             0 ->     4096
Sep  1 16:18:17 owner kernel: [    0.000000]   Normal       4096 ->   229376
Sep  1 16:18:17 owner kernel: [    0.000000]   HighMem    229376 ->   294640
Sep  1 16:18:17 owner kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  1 16:18:17 owner kernel: [    0.000000]     0:        0 ->   294640
Sep  1 16:18:17 owner kernel: [    0.000000] DMI present.
Sep  1 16:18:17 owner kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Sep  1 16:18:17 owner kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  1 16:18:17 owner kernel: [    0.000000] Processor #0 15:12 APIC version 16
Sep  1 16:18:17 owner kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  1 16:18:17 owner kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  1 16:18:17 owner kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Sep  1 16:18:17 owner kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Sep  1 16:18:17 owner kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  1 16:18:17 owner kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  1 16:18:17 owner kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aff00000)
Sep  1 16:18:17 owner kernel: [    0.000000] Detected 1800.078 MHz processor.
Sep  1 16:18:17 owner kernel: [   15.829848] Built 1 zonelists.  Total pages: 292339
Sep  1 16:18:17 owner kernel: [   15.829852] Kernel command line: root=UUID=36f4f755-b608-49ce-b11a-e96f60601f95 ro quiet splash
Sep  1 16:18:17 owner kernel: [   15.829998] Enabling fast FPU save and restore... done.
Sep  1 16:18:17 owner kernel: [   15.830001] Enabling unmasked SIMD FPU exception support... done.
Sep  1 16:18:17 owner kernel: [   15.830008] Initializing CPU#0
Sep  1 16:18:17 owner kernel: [   15.830051] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  1 16:18:17 owner kernel: [   15.830824] Console: colour VGA+ 80x25
Sep  1 16:18:17 owner kernel: [   15.831407] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  1 16:18:17 owner kernel: [   15.832401] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  1 16:18:17 owner kernel: [   15.862859] Memory: 1157148k/1178560k available (1992k kernel code, 20492k reserved, 893k data, 328k init, 261056k highmem)
Sep  1 16:18:17 owner kernel: [   15.862869] virtual kernel memory layout:
Sep  1 16:18:17 owner kernel: [   15.862870]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep  1 16:18:17 owner kernel: [   15.862872]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  1 16:18:17 owner kernel: [   15.862873]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  1 16:18:17 owner kernel: [   15.862874]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  1 16:18:17 owner kernel: [   15.862876]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Sep  1 16:18:17 owner kernel: [   15.862877]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Sep  1 16:18:17 owner kernel: [   15.862878]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Sep  1 16:18:17 owner kernel: [   15.862882] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  1 16:18:17 owner kernel: [   15.941891] Calibrating delay using timer specific routine.. 3602.05 BogoMIPS (lpj=7204115)
Sep  1 16:18:17 owner kernel: [   15.941936] Security Framework v1.0.0 initialized
Sep  1 16:18:17 owner kernel: [   15.941945] SELinux:  Disabled at boot.
Sep  1 16:18:17 owner kernel: [   15.941962] Mount-cache hash table entries: 512
Sep  1 16:18:17 owner kernel: [   15.942123] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  1 16:18:17 owner kernel: [   15.942125] CPU: L2 Cache: 128K (64 bytes/line)
Sep  1 16:18:17 owner kernel: [   15.942139] Compat vDSO mapped to ffffe000.
Sep  1 16:18:17 owner kernel: [   15.942144] Remapping vsyscall page to ffffe000
Sep  1 16:18:17 owner kernel: [   15.942155] Checking 'hlt' instruction... OK.
Sep  1 16:18:17 owner kernel: [   15.958022] SMP alternatives: switching to UP code
Sep  1 16:18:17 owner kernel: [   15.958330] Freeing SMP alternatives: 11k freed
Sep  1 16:18:17 owner kernel: [   15.958591] Early unpacking initramfs... done
Sep  1 16:18:17 owner kernel: [   16.270868] ACPI: Core revision 20060707
Sep  1 16:18:17 owner kernel: [   16.271085] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep  1 16:18:17 owner kernel: [   16.274890] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
Sep  1 16:18:17 owner kernel: [   16.274910] Total of 1 processors activated (3602.05 BogoMIPS).
Sep  1 16:18:17 owner kernel: [   16.275063] ENABLING IO-APIC IRQs
Sep  1 16:18:17 owner kernel: [   16.275256] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  1 16:18:17 owner kernel: [   16.421225] Brought up 1 CPUs
Sep  1 16:18:17 owner kernel: [   16.421448] Booting paravirtualized kernel on bare hardware
Sep  1 16:18:17 owner kernel: [   16.421527] Time: 21:17:48  Date: 08/01/107
Sep  1 16:18:17 owner kernel: [   16.421563] NET: Registered protocol family 16
Sep  1 16:18:17 owner kernel: [   16.421666] EISA bus registered
Sep  1 16:18:17 owner kernel: [   16.421670] ACPI: bus type pci registered
Sep  1 16:18:17 owner kernel: [   16.421819] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
Sep  1 16:18:17 owner kernel: [   16.421821] PCI: Using configuration type 1
Sep  1 16:18:17 owner kernel: [   16.421823] Setting up standard PCI resources
Sep  1 16:18:17 owner kernel: [   16.424214] ACPI: Interpreter enabled
Sep  1 16:18:17 owner kernel: [   16.424219] ACPI: Using IOAPIC for interrupt routing
Sep  1 16:18:17 owner kernel: [   16.424557] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  1 16:18:17 owner kernel: [   16.425668] Enabling SiS 96x SMBus.
Sep  1 16:18:17 owner kernel: [   16.448109] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
Sep  1 16:18:17 owner kernel: [   16.448288] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
Sep  1 16:18:17 owner kernel: [   16.448463] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
Sep  1 16:18:17 owner kernel: [   16.448634] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
Sep  1 16:18:17 owner kernel: [   16.448823] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
Sep  1 16:18:17 owner kernel: [   16.448994] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
Sep  1 16:18:17 owner kernel: [   16.449180] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Sep  1 16:18:17 owner kernel: [   16.449351] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
Sep  1 16:18:17 owner kernel: [   16.449639] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  1 16:18:17 owner kernel: [   16.449652] pnp: PnP ACPI init
Sep  1 16:18:17 owner kernel: [   16.451294] pnp: PnP ACPI: found 8 devices
Sep  1 16:18:17 owner kernel: [   16.451300] PnPBIOS: Disabled by ACPI PNP
Sep  1 16:18:17 owner kernel: [   16.451355] PCI: Using ACPI for IRQ routing
Sep  1 16:18:17 owner kernel: [   16.451358] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  1 16:18:17 owner kernel: [   16.453491] NET: Registered protocol family 8
Sep  1 16:18:17 owner kernel: [   16.453493] NET: Registered protocol family 20
Sep  1 16:18:17 owner kernel: [   16.453683] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
Sep  1 16:18:17 owner kernel: [   16.453686] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
Sep  1 16:18:17 owner kernel: [   16.453689] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
Sep  1 16:18:17 owner kernel: [   16.453692] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
Sep  1 16:18:17 owner kernel: [   16.453941] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
Sep  1 16:18:17 owner kernel: [   16.453944] PCI: Bridge: 0000:00:01.0
Sep  1 16:18:17 owner kernel: [   16.453947]   IO window: a000-afff
Sep  1 16:18:17 owner kernel: [   16.453951]   MEM window: e2100000-e21fffff
Sep  1 16:18:17 owner kernel: [   16.453955]   PREFETCH window: e8000000-efffffff
Sep  1 16:18:17 owner kernel: [   16.453959] PCI: Bus 2, cardbus bridge: 0000:00:06.0
Sep  1 16:18:17 owner kernel: [   16.453961]   IO window: 00002400-000024ff
Sep  1 16:18:17 owner kernel: [   16.453965]   IO window: 00002800-000028ff
Sep  1 16:18:17 owner kernel: [   16.453968]   PREFETCH window: 60000000-63ffffff
Sep  1 16:18:17 owner kernel: [   16.453972]   MEM window: 64000000-67ffffff
Sep  1 16:18:17 owner kernel: [   16.453989] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
Sep  1 16:18:17 owner kernel: [   16.454000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  1 16:18:17 owner kernel: [   16.454040] NET: Registered protocol family 2
Sep  1 16:18:17 owner kernel: [   16.489174] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  1 16:18:17 owner kernel: [   16.489392] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  1 16:18:17 owner kernel: [   16.490728] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  1 16:18:17 owner kernel: [   16.491409] TCP: Hash tables configured (established 131072 bind 65536)
Sep  1 16:18:17 owner kernel: [   16.491414] TCP reno registered
Sep  1 16:18:17 owner kernel: [   16.501211] checking if image is initramfs... it is
Sep  1 16:18:17 owner kernel: [   17.116976] Freeing initrd memory: 6782k freed
Sep  1 16:18:17 owner kernel: [   17.117160] Simple Boot Flag at 0x38 set to 0x1
Sep  1 16:18:17 owner kernel: [   17.117417] audit: initializing netlink socket (disabled)
Sep  1 16:18:17 owner kernel: [   17.117430] audit(1188681468.372:1): initialized
Sep  1 16:18:17 owner kernel: [   17.117492] highmem bounce pool size: 64 pages
Sep  1 16:18:17 owner kernel: [   17.117573] VFS: Disk quotas dquot_6.5.1
Sep  1 16:18:17 owner kernel: [   17.117596] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  1 16:18:17 owner kernel: [   17.117654] io scheduler noop registered
Sep  1 16:18:17 owner kernel: [   17.117657] io scheduler anticipatory registered
Sep  1 16:18:17 owner kernel: [   17.117659] io scheduler deadline registered
Sep  1 16:18:17 owner kernel: [   17.117672] io scheduler cfq registered (default)
Sep  1 16:18:17 owner kernel: [   17.375980] isapnp: Scanning for PnP cards...
Sep  1 16:18:17 owner kernel: [   17.728855] isapnp: No Plug & Play device found
Sep  1 16:18:17 owner kernel: [   17.767511] Real Time Clock Driver v1.12ac
Sep  1 16:18:17 owner kernel: [   17.767551] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  1 16:18:17 owner kernel: [   17.768471] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
Sep  1 16:18:17 owner kernel: [   17.768479] ACPI: PCI interrupt for device 0000:00:02.6 disabled
Sep  1 16:18:17 owner kernel: [   17.768541] mice: PS/2 mouse device common for all mice
Sep  1 16:18:17 owner kernel: [   17.768982] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  1 16:18:17 owner kernel: [   17.769135] input: Macintosh mouse button emulation as /class/input/input0
Sep  1 16:18:17 owner kernel: [   17.769170] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep  1 16:18:17 owner kernel: [   17.769174] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep  1 16:18:17 owner kernel: [   17.769384] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  1 16:18:17 owner kernel: [   17.772758] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  1 16:18:17 owner kernel: [   17.772763] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  1 16:18:17 owner kernel: [   17.772895] EISA: Probing bus 0 at eisa.0
Sep  1 16:18:17 owner kernel: [   17.772905] Cannot allocate resource for EISA slot 1
Sep  1 16:18:17 owner kernel: [   17.772908] Cannot allocate resource for EISA slot 2
Sep  1 16:18:17 owner kernel: [   17.772926] Cannot allocate resource for EISA slot 8
Sep  1 16:18:17 owner kernel: [   17.772928] EISA: Detected 0 cards.
Sep  1 16:18:17 owner kernel: [   17.802972] TCP cubic registered
Sep  1 16:18:17 owner kernel: [   17.802982] NET: Registered protocol family 1
Sep  1 16:18:17 owner kernel: [   17.803006] Using IPI No-Shortcut mode
Sep  1 16:18:17 owner kernel: [   17.803067] ACPI: (supports S0 S3 S4 S5)
Sep  1 16:18:17 owner kernel: [   17.803102]   Magic number: 7:41:297
Sep  1 16:18:17 owner kernel: [   17.803134]   hash matches device ttywe
Sep  1 16:18:17 owner kernel: [   17.803151] Time: tsc clocksource has been installed.
Sep  1 16:18:17 owner kernel: [   17.803561] Freeing unused kernel memory: 328k freed
Sep  1 16:18:17 owner kernel: [   17.819750] input: AT Translated Set 2 keyboard as /class/input/input1
Sep  1 16:18:17 owner kernel: [   19.078574] Capability LSM initialized
Sep  1 16:18:17 owner kernel: [   19.126958] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  1 16:18:17 owner kernel: [   19.130206] ACPI: Thermal Zone [THRM] (53 C)
Sep  1 16:18:17 owner kernel: [   19.815629] SIS5513: IDE controller at PCI slot 0000:00:02.5
Sep  1 16:18:17 owner kernel: [   19.815648] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 18
Sep  1 16:18:17 owner kernel: [   19.815657] SIS5513: chipset revision 0
Sep  1 16:18:17 owner kernel: [   19.815659] SIS5513: not 100%% native mode: will probe irqs later
Sep  1 16:18:17 owner kernel: [   19.815671] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
Sep  1 16:18:17 owner kernel: [   19.815683]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
Sep  1 16:18:17 owner kernel: [   19.815695]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
Sep  1 16:18:17 owner kernel: [   19.847860] usbcore: registered new interface driver usbfs
Sep  1 16:18:17 owner kernel: [   19.847883] usbcore: registered new interface driver hub
Sep  1 16:18:17 owner kernel: [   19.847902] usbcore: registered new device driver usb
Sep  1 16:18:17 owner kernel: [   19.890546] sis900.c: v1.08.10 Apr. 2 2006
Sep  1 16:18:17 owner kernel: [    3.920000] Time: acpi_pm clocksource has been installed.
Sep  1 16:18:17 owner kernel: [    4.012000] hda: TOSHIBA MK6025GAS, ATA DISK drive
Sep  1 16:18:17 owner kernel: [    4.684000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep  1 16:18:17 owner kernel: [    5.484000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
Sep  1 16:18:17 owner kernel: [    9.228000] ide1 at 0x170-0x177,0x376 on irq 15
Sep  1 16:18:17 owner kernel: [    9.228000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 19
Sep  1 16:18:17 owner kernel: [    9.228000] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep  1 16:18:17 owner kernel: [    9.228000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Sep  1 16:18:17 owner kernel: [    9.228000] ohci_hcd 0000:00:03.0: irq 19, io mem 0xe2002000
Sep  1 16:18:17 owner kernel: [    9.284000] usb usb1: configuration #1 chosen from 1 choice
Sep  1 16:18:17 owner kernel: [    9.284000] hub 1-0:1.0: USB hub found
Sep  1 16:18:17 owner kernel: [    9.284000] hub 1-0:1.0: 3 ports detected
Sep  1 16:18:17 owner kernel: [    9.388000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 20
Sep  1 16:18:17 owner kernel: [    9.388000] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep  1 16:18:17 owner kernel: [    9.388000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Sep  1 16:18:17 owner kernel: [    9.388000] ohci_hcd 0000:00:03.1: irq 20, io mem 0xe2003000
Sep  1 16:18:17 owner kernel: [    9.444000] usb usb2: configuration #1 chosen from 1 choice
Sep  1 16:18:17 owner kernel: [    9.444000] hub 2-0:1.0: USB hub found
Sep  1 16:18:17 owner kernel: [    9.444000] hub 2-0:1.0: 3 ports detected
Sep  1 16:18:17 owner kernel: [    9.548000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 21
Sep  1 16:18:17 owner kernel: [    9.548000] ehci_hcd 0000:00:03.2: EHCI Host Controller
Sep  1 16:18:17 owner kernel: [    9.548000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Sep  1 16:18:17 owner kernel: [    9.548000] ehci_hcd 0000:00:03.2: irq 21, io mem 0xe2004000
Sep  1 16:18:17 owner kernel: [    9.548000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  1 16:18:17 owner kernel: [    9.548000] usb usb3: configuration #1 chosen from 1 choice
Sep  1 16:18:17 owner kernel: [    9.548000] hub 3-0:1.0: USB hub found
Sep  1 16:18:17 owner kernel: [    9.548000] hub 3-0:1.0: 6 ports detected
Sep  1 16:18:17 owner kernel: [    9.652000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  1 16:18:17 owner kernel: [    9.656000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Sep  1 16:18:17 owner kernel: [    9.660000] 0000:00:04.0: Using transceiver found at address 13 as default
Sep  1 16:18:17 owner kernel: [    9.664000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 16, 00:c0:9f:c1:44:ea.
Sep  1 16:18:17 owner kernel: [    9.668000] SCSI subsystem initialized
Sep  1 16:18:17 owner kernel: [    9.688000] hda: max request size: 128KiB
Sep  1 16:18:17 owner kernel: [    9.704000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
Sep  1 16:18:17 owner kernel: [    9.704000] hda: cache flushes supported
Sep  1 16:18:17 owner kernel: [    9.704000]  hda: hda1 hda2 < hda5 >
Sep  1 16:18:17 owner kernel: [    9.800000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep  1 16:18:17 owner kernel: [    9.800000] Uniform CD-ROM driver Revision: 3.20
Sep  1 16:18:17 owner kernel: [   10.128000] kjournald starting.  Commit interval 5 seconds
Sep  1 16:18:17 owner kernel: [   10.128000] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 16:18:17 owner kernel: [   10.236000] usb 1-2: new low speed USB device using ohci_hcd and address 3
Sep  1 16:18:17 owner kernel: [   10.444000] usb 1-2: configuration #1 chosen from 1 choice
Sep  1 16:18:17 owner kernel: [   24.492000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  1 16:18:17 owner kernel: [   24.496000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  1 16:18:17 owner kernel: [   24.812000] Linux agpgart interface v0.102 (c) Dave Jones
Sep  1 16:18:17 owner kernel: [   24.864000] agpgart: Detected AGP bridge 0
Sep  1 16:18:17 owner kernel: [   24.864000] agpgart: AGP aperture is 32M @ 0xe0000000
Sep  1 16:18:17 owner kernel: [   24.928000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
Sep  1 16:18:17 owner kernel: [   24.928000] Yenta: Using CSCINT to route CSC interrupts to PCI
Sep  1 16:18:17 owner kernel: [   24.928000] Yenta: Routing CardBus interrupts to PCI
Sep  1 16:18:17 owner kernel: [   24.928000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
Sep  1 16:18:17 owner kernel: [   25.112000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep  1 16:18:17 owner kernel: [   25.112000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep  1 16:18:17 owner kernel: [   25.160000] Yenta: ISA IRQ mask 0x06f8, PCI irq 16
Sep  1 16:18:17 owner kernel: [   25.160000] Socket status: 30000006
Sep  1 16:18:17 owner kernel: [   25.200000] bcm43xx driver
Sep  1 16:18:17 owner kernel: [   25.200000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  1 16:18:17 owner kernel: [   25.472000] input: PC Speaker as /class/input/input2
Sep  1 16:18:17 owner kernel: [   25.544000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
Sep  1 16:18:17 owner kernel: [   25.680000] usbcore: registered new interface driver hiddev
Sep  1 16:18:17 owner kernel: [   25.868000] input: HID 1241:1166 as /class/input/input3
Sep  1 16:18:17 owner kernel: [   25.868000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:03.0-2
Sep  1 16:18:17 owner kernel: [   25.868000] usbcore: registered new interface driver usbhid
Sep  1 16:18:17 owner kernel: [   25.868000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Sep  1 16:18:17 owner kernel: [   25.884000] cs: IO port probe 0x100-0x3af: clean.
Sep  1 16:18:17 owner kernel: [   25.884000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
Sep  1 16:18:17 owner kernel: [   25.888000] cs: IO port probe 0x820-0x8ff: clean.
Sep  1 16:18:17 owner kernel: [   25.888000] cs: IO port probe 0xc00-0xcf7: clean.
Sep  1 16:18:17 owner kernel: [   25.900000] cs: IO port probe 0xa00-0xaff: clean.
Sep  1 16:18:17 owner kernel: [   25.964000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
Sep  1 16:18:17 owner kernel: [   26.144000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Sep  1 16:18:17 owner kernel: [   26.184000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Sep  1 16:18:17 owner kernel: [   26.784000] intel8x0_measure_ac97_clock: measured 55472 usecs
Sep  1 16:18:17 owner kernel: [   26.784000] intel8x0: clocking to 48000
Sep  1 16:18:17 owner kernel: [   27.008000] lp: driver loaded but no devices found
Sep  1 16:18:17 owner kernel: [   27.084000] Adding 2441840k swap on /dev/disk/by-uuid/ed70067a-bce9-4fb6-907f-2c4c81db4df4.  Priority:-1 extents:1 across:2441840k
Sep  1 16:18:17 owner kernel: [   27.220000] EXT3 FS on hda1, internal journal
Sep  1 16:18:17 owner kernel: [   28.192000] ACPI: Battery Slot [BAT1] (battery present)
Sep  1 16:18:17 owner kernel: [   28.232000] ACPI: AC Adapter [ACAD] (on-line)
Sep  1 16:18:17 owner kernel: [   28.276000] No dock devices found.
Sep  1 16:18:17 owner kernel: [   28.352000] Using specific hotkey driver
Sep  1 16:18:17 owner kernel: [   28.452000] input: Power Button (FF) as /class/input/input5
Sep  1 16:18:17 owner kernel: [   28.460000] ACPI: Power Button (FF) [PWRF]
Sep  1 16:18:17 owner kernel: [   28.496000] input: Lid Switch as /class/input/input6
Sep  1 16:18:17 owner kernel: [   28.500000] ACPI: Lid Switch [LID]
Sep  1 16:18:17 owner kernel: [   28.540000] input: Power Button (CM) as /class/input/input7
Sep  1 16:18:17 owner kernel: [   28.544000] ACPI: Power Button (CM) [PWRB]
Sep  1 16:18:17 owner kernel: [   28.584000] input: Sleep Button (CM) as /class/input/input8
Sep  1 16:18:17 owner kernel: [   28.588000] ACPI: Sleep Button (CM) [SLPB]
Sep  1 16:18:17 owner kernel: [   28.680000] pcc_acpi: loading...
Sep  1 16:18:17 owner kernel: [   28.972000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
Sep  1 16:18:17 owner kernel: [   28.972000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
Sep  1 16:18:17 owner kernel: [   28.972000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
Sep  1 16:18:17 owner kernel: [   28.972000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
Sep  1 16:18:20 owner kernel: [   32.008000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:18:20 owner kernel: [   32.028000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:18:20 owner kernel: [   32.056000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:18:20 owner dhcdbd: Started up.
Sep  1 16:18:20 owner kernel: [   32.476000] eth1: Media Link Off
Sep  1 16:18:23 owner kernel: [   35.028000] ppdev: user-space parallel port driver
Sep  1 16:18:24 owner hpiod: 1.7.3 accepting connections at 2208... 
Sep  1 16:18:25 owner kernel: [   37.160000] apm: BIOS not found.
Sep  1 16:18:25 owner kernel: [   37.684000] Bluetooth: Core ver 2.11
Sep  1 16:18:25 owner kernel: [   37.684000] NET: Registered protocol family 31
Sep  1 16:18:25 owner kernel: [   37.684000] Bluetooth: HCI device and connection manager initialized
Sep  1 16:18:25 owner kernel: [   37.684000] Bluetooth: HCI socket layer initialized
Sep  1 16:18:25 owner kernel: [   37.728000] Bluetooth: L2CAP ver 2.8
Sep  1 16:18:25 owner kernel: [   37.728000] Bluetooth: L2CAP socket layer initialized
Sep  1 16:18:26 owner kernel: [   37.800000] Bluetooth: RFCOMM socket layer initialized
Sep  1 16:18:26 owner kernel: [   37.800000] Bluetooth: RFCOMM TTY layer initialized
Sep  1 16:18:26 owner kernel: [   37.800000] Bluetooth: RFCOMM ver 1.8
Sep  1 16:18:34 owner gconfd (owner-4939): starting (version 2.18.0.1), pid 4939 user 'owner'
Sep  1 16:18:34 owner gconfd (owner-4939): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  1 16:18:34 owner gconfd (owner-4939): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  1 16:18:34 owner gconfd (owner-4939): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  1 16:18:34 owner gconfd (owner-4939): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  1 16:18:34 owner gconfd (owner-4939): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  1 16:18:37 owner kernel: [   49.104000] NET: Registered protocol family 10
Sep  1 16:18:37 owner kernel: [   49.104000] lo: Disabled Privacy Extensions
Sep  1 16:18:37 owner kernel: [   49.104000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep  1 16:18:44 owner gconfd (owner-4939): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 0
Sep  1 16:18:47 owner kernel: [   59.616000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96436, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96436, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96436, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96444, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96444, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96444, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96448, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96448, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96448, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96452, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96452, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96452, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96476, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96480, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96476, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96480, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96476, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96480, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96484, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96488, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96492, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96496, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96500, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96504, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96508, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96512, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96484, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96488, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96484, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=96488, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98428, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98432, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98436, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98440, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98444, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98448, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98452, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98456, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98428, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98432, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98428, limit=73856
Sep  1 16:19:14 owner kernel: [   85.976000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   85.976000] hdc: rw=0, want=98432, limit=73856
Sep  1 16:19:14 owner kernel: [   86.312000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.312000] hdc: rw=0, want=96436, limit=73856
Sep  1 16:19:14 owner kernel: [   86.368000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.368000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:14 owner kernel: [   86.380000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.380000] hdc: rw=0, want=96444, limit=73856
Sep  1 16:19:14 owner kernel: [   86.380000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.380000] hdc: rw=0, want=96448, limit=73856
Sep  1 16:19:14 owner kernel: [   86.384000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.384000] hdc: rw=0, want=96452, limit=73856
Sep  1 16:19:14 owner kernel: [   86.388000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.388000] hdc: rw=0, want=96476, limit=73856
Sep  1 16:19:14 owner kernel: [   86.388000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.388000] hdc: rw=0, want=96480, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96516, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96520, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96524, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96528, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96532, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96536, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96540, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96544, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96484, limit=73856
Sep  1 16:19:14 owner kernel: [   86.392000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.392000] hdc: rw=0, want=96488, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98460, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98464, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98468, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98472, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98476, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98480, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98484, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98488, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98428, limit=73856
Sep  1 16:19:14 owner kernel: [   86.400000] attempt to access beyond end of device
Sep  1 16:19:14 owner kernel: [   86.400000] hdc: rw=0, want=98432, limit=73856
Sep  1 16:19:17 owner kernel: [   89.608000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:19:19 owner kernel: [   90.584000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.584000] hdc: rw=0, want=96436, limit=73856
Sep  1 16:19:19 owner kernel: [   90.584000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.584000] hdc: rw=0, want=96436, limit=73856
Sep  1 16:19:19 owner kernel: [   90.584000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.584000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:19 owner kernel: [   90.584000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.584000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:19 owner kernel: [   90.584000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.584000] hdc: rw=0, want=96444, limit=73856
Sep  1 16:19:19 owner kernel: [   90.584000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.584000] hdc: rw=0, want=96444, limit=73856
Sep  1 16:19:19 owner kernel: [   90.584000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.584000] hdc: rw=0, want=96448, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96448, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96452, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96452, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96476, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96480, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96476, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96480, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96484, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96488, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96484, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=96488, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=98428, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=98432, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=98428, limit=73856
Sep  1 16:19:19 owner kernel: [   90.588000] attempt to access beyond end of device
Sep  1 16:19:19 owner kernel: [   90.588000] hdc: rw=0, want=98432, limit=73856
Sep  1 16:19:23 owner kernel: [   95.060000] attempt to access beyond end of device
Sep  1 16:19:23 owner kernel: [   95.060000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:23 owner kernel: [   95.060000] printk: 84 messages suppressed.
Sep  1 16:19:23 owner kernel: [   95.064000] attempt to access beyond end of device
Sep  1 16:19:23 owner kernel: [   95.064000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:25 owner kernel: [   97.304000] attempt to access beyond end of device
Sep  1 16:19:25 owner kernel: [   97.304000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:25 owner kernel: [   97.304000] printk: 1 messages suppressed.
Sep  1 16:19:25 owner kernel: [   97.304000] attempt to access beyond end of device
Sep  1 16:19:25 owner kernel: [   97.304000] hdc: rw=0, want=96440, limit=73856
Sep  1 16:19:47 owner kernel: [  119.592000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:20:12 owner kernel: [  144.584000] attempt to access beyond end of device
Sep  1 16:20:12 owner kernel: [  144.584000] hdc: rw=0, want=73860, limit=73856
Sep  1 16:20:12 owner kernel: [  144.584000] printk: 1 messages suppressed.
Sep  1 16:20:12 owner kernel: [  144.584000] attempt to access beyond end of device
Sep  1 16:20:12 owner kernel: [  144.584000] hdc: rw=0, want=73864, limit=73856
Sep  1 16:20:12 owner kernel: [  144.584000] attempt to access beyond end of device
Sep  1 16:20:12 owner kernel: [  144.584000] hdc: rw=0, want=73868, limit=73856
Sep  1 16:20:12 owner kernel: [  144.584000] attempt to access beyond end of device
Sep  1 16:20:12 owner kernel: [  144.584000] hdc: rw=0, want=73872, limit=73856
Sep  1 16:20:12 owner kernel: [  144.584000] attempt to access beyond end of device
Sep  1 16:20:12 owner kernel: [  144.584000] hdc: rw=0, want=73876, limit=73856
Sep  1 16:20:12 owner kernel: [  144.584000] attempt to access beyond end of device
Sep  1 16:20:12 owner kernel: [  144.584000] hdc: rw=0, want=73880, limit=73856
Sep  1 16:20:12 owner kernel: [  144.584000] attempt to access beyond end of device
Sep  1 16:20:12 owner kernel: [  144.584000] hdc: rw=0, want=73884, limit=73856
Sep  1 16:20:12 owner kernel: [  144.584000] attempt to access beyond end of device
Sep  1 16:20:12 owner kernel: [  144.584000] hdc: rw=0, want=73888, limit=73856
Sep  1 16:20:13 owner kernel: [  144.584000] attempt to access beyond end of device
Sep  1 16:20:13 owner kernel: [  144.584000] hdc: rw=0, want=73892, limit=73856
Sep  1 16:20:13 owner kernel: [  144.608000] attempt to access beyond end of device
Sep  1 16:20:13 owner kernel: [  144.608000] hdc: rw=0, want=73860, limit=73856
Sep  1 16:20:13 owner kernel: [  144.608000] attempt to access beyond end of device
Sep  1 16:20:13 owner kernel: [  144.608000] hdc: rw=0, want=73860, limit=73856
Sep  1 16:20:17 owner kernel: [  149.568000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:20:43 owner gconfd (owner-4939): Exiting
Sep  1 16:20:47 owner kernel: [  179.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:20:52 owner exiting on signal 15
Sep  1 16:22:28 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  1 16:22:28 owner kernel: Inspecting /boot/System.map-2.6.20-15-generic
Sep  1 16:22:28 owner kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Sep  1 16:22:28 owner kernel: Symbols match kernel version 2.6.20.
Sep  1 16:22:28 owner kernel: No module symbols loaded - kernel modules not enabled. 
Sep  1 16:22:28 owner kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Sep  1 16:22:28 owner kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  1 16:22:28 owner kernel: [    0.000000] sanitize start
Sep  1 16:22:28 owner kernel: [    0.000000] sanitize end
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000047df0000 end: 0000000047ef0000 type: 1
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() start: 0000000047ef0000 size: 000000000000a000 end: 0000000047efa000 type: 3
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() start: 0000000047efa000 size: 0000000000006000 end: 0000000047f00000 type: 4
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() start: 0000000047f00000 size: 0000000008100000 end: 0000000050000000 type: 2
Sep  1 16:22:28 owner kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Sep  1 16:22:28 owner kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Sep  1 16:22:28 owner kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Sep  1 16:22:28 owner kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Sep  1 16:22:28 owner kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000047ef0000 (usable)
Sep  1 16:22:28 owner kernel: [    0.000000]  BIOS-e820: 0000000047ef0000 - 0000000047efa000 (ACPI data)
Sep  1 16:22:28 owner kernel: [    0.000000]  BIOS-e820: 0000000047efa000 - 0000000047f00000 (ACPI NVS)
Sep  1 16:22:28 owner kernel: [    0.000000]  BIOS-e820: 0000000047f00000 - 0000000050000000 (reserved)
Sep  1 16:22:28 owner kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Sep  1 16:22:28 owner kernel: [    0.000000] 254MB HIGHMEM available.
Sep  1 16:22:28 owner kernel: [    0.000000] 896MB LOWMEM available.
Sep  1 16:22:28 owner kernel: [    0.000000] found SMP MP-table at 000f7fd0
Sep  1 16:22:28 owner kernel: [    0.000000] Zone PFN ranges:
Sep  1 16:22:28 owner kernel: [    0.000000]   DMA             0 ->     4096
Sep  1 16:22:28 owner kernel: [    0.000000]   Normal       4096 ->   229376
Sep  1 16:22:28 owner kernel: [    0.000000]   HighMem    229376 ->   294640
Sep  1 16:22:28 owner kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  1 16:22:28 owner kernel: [    0.000000]     0:        0 ->   294640
Sep  1 16:22:28 owner kernel: [    0.000000] DMI present.
Sep  1 16:22:28 owner kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Sep  1 16:22:28 owner kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  1 16:22:28 owner kernel: [    0.000000] Processor #0 15:12 APIC version 16
Sep  1 16:22:28 owner kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  1 16:22:28 owner kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  1 16:22:28 owner kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Sep  1 16:22:28 owner kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Sep  1 16:22:28 owner kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  1 16:22:28 owner kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  1 16:22:28 owner kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aff00000)
Sep  1 16:22:28 owner kernel: [    0.000000] Detected 1800.067 MHz processor.
Sep  1 16:22:28 owner kernel: [   26.284001] Built 1 zonelists.  Total pages: 292339
Sep  1 16:22:28 owner kernel: [   26.284005] Kernel command line: root=UUID=36f4f755-b608-49ce-b11a-e96f60601f95 ro quiet splash
Sep  1 16:22:28 owner kernel: [   26.284152] Enabling fast FPU save and restore... done.
Sep  1 16:22:28 owner kernel: [   26.284154] Enabling unmasked SIMD FPU exception support... done.
Sep  1 16:22:28 owner kernel: [   26.284162] Initializing CPU#0
Sep  1 16:22:28 owner kernel: [   26.284204] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  1 16:22:28 owner kernel: [   26.284964] Console: colour VGA+ 80x25
Sep  1 16:22:28 owner kernel: [   26.285547] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  1 16:22:28 owner kernel: [   26.286541] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  1 16:22:28 owner kernel: [   26.317004] Memory: 1157148k/1178560k available (1992k kernel code, 20492k reserved, 893k data, 328k init, 261056k highmem)
Sep  1 16:22:28 owner kernel: [   26.317014] virtual kernel memory layout:
Sep  1 16:22:28 owner kernel: [   26.317015]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep  1 16:22:28 owner kernel: [   26.317017]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  1 16:22:28 owner kernel: [   26.317018]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  1 16:22:28 owner kernel: [   26.317019]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  1 16:22:28 owner kernel: [   26.317021]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Sep  1 16:22:28 owner kernel: [   26.317022]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Sep  1 16:22:28 owner kernel: [   26.317023]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Sep  1 16:22:28 owner kernel: [   26.317027] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  1 16:22:28 owner kernel: [   26.396043] Calibrating delay using timer specific routine.. 3602.04 BogoMIPS (lpj=7204095)
Sep  1 16:22:28 owner kernel: [   26.396090] Security Framework v1.0.0 initialized
Sep  1 16:22:28 owner kernel: [   26.396099] SELinux:  Disabled at boot.
Sep  1 16:22:28 owner kernel: [   26.396115] Mount-cache hash table entries: 512
Sep  1 16:22:28 owner kernel: [   26.396276] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  1 16:22:28 owner kernel: [   26.396278] CPU: L2 Cache: 128K (64 bytes/line)
Sep  1 16:22:28 owner kernel: [   26.396292] Compat vDSO mapped to ffffe000.
Sep  1 16:22:28 owner kernel: [   26.396297] Remapping vsyscall page to ffffe000
Sep  1 16:22:28 owner kernel: [   26.396307] Checking 'hlt' instruction... OK.
Sep  1 16:22:28 owner kernel: [   26.412175] SMP alternatives: switching to UP code
Sep  1 16:22:28 owner kernel: [   26.412480] Freeing SMP alternatives: 11k freed
Sep  1 16:22:28 owner kernel: [   26.412743] Early unpacking initramfs... done
Sep  1 16:22:28 owner kernel: [   26.725015] ACPI: Core revision 20060707
Sep  1 16:22:28 owner kernel: [   26.725232] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep  1 16:22:28 owner kernel: [   26.728409] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
Sep  1 16:22:28 owner kernel: [   26.728428] Total of 1 processors activated (3602.04 BogoMIPS).
Sep  1 16:22:28 owner kernel: [   26.728581] ENABLING IO-APIC IRQs
Sep  1 16:22:28 owner kernel: [   26.728774] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  1 16:22:28 owner kernel: [   26.875379] Brought up 1 CPUs
Sep  1 16:22:28 owner kernel: [   26.875600] Booting paravirtualized kernel on bare hardware
Sep  1 16:22:28 owner kernel: [   26.875679] Time: 21:22:02  Date: 08/01/107
Sep  1 16:22:28 owner kernel: [   26.875715] NET: Registered protocol family 16
Sep  1 16:22:28 owner kernel: [   26.875818] EISA bus registered
Sep  1 16:22:28 owner kernel: [   26.875822] ACPI: bus type pci registered
Sep  1 16:22:28 owner kernel: [   26.875969] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
Sep  1 16:22:28 owner kernel: [   26.875972] PCI: Using configuration type 1
Sep  1 16:22:28 owner kernel: [   26.875974] Setting up standard PCI resources
Sep  1 16:22:28 owner kernel: [   26.878364] ACPI: Interpreter enabled
Sep  1 16:22:28 owner kernel: [   26.878369] ACPI: Using IOAPIC for interrupt routing
Sep  1 16:22:28 owner kernel: [   26.878707] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  1 16:22:28 owner kernel: [   26.879818] Enabling SiS 96x SMBus.
Sep  1 16:22:28 owner kernel: [   26.900861] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
Sep  1 16:22:28 owner kernel: [   26.901040] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
Sep  1 16:22:28 owner kernel: [   26.901216] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
Sep  1 16:22:28 owner kernel: [   26.901386] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
Sep  1 16:22:28 owner kernel: [   26.901576] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
Sep  1 16:22:28 owner kernel: [   26.901747] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
Sep  1 16:22:28 owner kernel: [   26.901923] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Sep  1 16:22:28 owner kernel: [   26.902092] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
Sep  1 16:22:28 owner kernel: [   26.902380] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  1 16:22:28 owner kernel: [   26.902392] pnp: PnP ACPI init
Sep  1 16:22:28 owner kernel: [   26.904059] pnp: PnP ACPI: found 8 devices
Sep  1 16:22:28 owner kernel: [   26.904065] PnPBIOS: Disabled by ACPI PNP
Sep  1 16:22:28 owner kernel: [   26.904120] PCI: Using ACPI for IRQ routing
Sep  1 16:22:28 owner kernel: [   26.904123] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  1 16:22:28 owner kernel: [   26.906237] NET: Registered protocol family 8
Sep  1 16:22:28 owner kernel: [   26.906239] NET: Registered protocol family 20
Sep  1 16:22:28 owner kernel: [   26.906422] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
Sep  1 16:22:28 owner kernel: [   26.906425] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
Sep  1 16:22:28 owner kernel: [   26.906428] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
Sep  1 16:22:28 owner kernel: [   26.906431] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
Sep  1 16:22:28 owner kernel: [   26.906680] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
Sep  1 16:22:28 owner kernel: [   26.906683] PCI: Bridge: 0000:00:01.0
Sep  1 16:22:28 owner kernel: [   26.906686]   IO window: a000-afff
Sep  1 16:22:28 owner kernel: [   26.906690]   MEM window: e2100000-e21fffff
Sep  1 16:22:28 owner kernel: [   26.906693]   PREFETCH window: e8000000-efffffff
Sep  1 16:22:28 owner kernel: [   26.906697] PCI: Bus 2, cardbus bridge: 0000:00:06.0
Sep  1 16:22:28 owner kernel: [   26.906700]   IO window: 00002400-000024ff
Sep  1 16:22:28 owner kernel: [   26.906703]   IO window: 00002800-000028ff
Sep  1 16:22:28 owner kernel: [   26.906706]   PREFETCH window: 60000000-63ffffff
Sep  1 16:22:28 owner kernel: [   26.906710]   MEM window: 64000000-67ffffff
Sep  1 16:22:28 owner kernel: [   26.906726] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
Sep  1 16:22:28 owner kernel: [   26.906738] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  1 16:22:28 owner kernel: [   26.906779] NET: Registered protocol family 2
Sep  1 16:22:28 owner kernel: [   26.943332] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  1 16:22:28 owner kernel: [   26.943552] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  1 16:22:28 owner kernel: [   26.944890] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  1 16:22:28 owner kernel: [   26.945573] TCP: Hash tables configured (established 131072 bind 65536)
Sep  1 16:22:28 owner kernel: [   26.945577] TCP reno registered
Sep  1 16:22:28 owner kernel: [   26.955370] checking if image is initramfs... it is
Sep  1 16:22:28 owner kernel: [   27.571133] Freeing initrd memory: 6782k freed
Sep  1 16:22:28 owner kernel: [   27.571318] Simple Boot Flag at 0x38 set to 0x1
Sep  1 16:22:28 owner kernel: [   27.571572] audit: initializing netlink socket (disabled)
Sep  1 16:22:28 owner kernel: [   27.571586] audit(1188681723.368:1): initialized
Sep  1 16:22:28 owner kernel: [   27.571647] highmem bounce pool size: 64 pages
Sep  1 16:22:28 owner kernel: [   27.571728] VFS: Disk quotas dquot_6.5.1
Sep  1 16:22:28 owner kernel: [   27.571751] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  1 16:22:28 owner kernel: [   27.571809] io scheduler noop registered
Sep  1 16:22:28 owner kernel: [   27.571812] io scheduler anticipatory registered
Sep  1 16:22:28 owner kernel: [   27.571814] io scheduler deadline registered
Sep  1 16:22:28 owner kernel: [   27.571827] io scheduler cfq registered (default)
Sep  1 16:22:28 owner kernel: [   27.997946] isapnp: Scanning for PnP cards...
Sep  1 16:22:28 owner kernel: [   28.350821] isapnp: No Plug & Play device found
Sep  1 16:22:28 owner kernel: [   28.389469] Real Time Clock Driver v1.12ac
Sep  1 16:22:28 owner kernel: [   28.389507] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  1 16:22:28 owner kernel: [   28.390444] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
Sep  1 16:22:28 owner kernel: [   28.390452] ACPI: PCI interrupt for device 0000:00:02.6 disabled
Sep  1 16:22:28 owner kernel: [   28.390514] mice: PS/2 mouse device common for all mice
Sep  1 16:22:28 owner kernel: [   28.390958] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  1 16:22:28 owner kernel: [   28.391198] input: Macintosh mouse button emulation as /class/input/input0
Sep  1 16:22:28 owner kernel: [   28.391233] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep  1 16:22:28 owner kernel: [   28.391237] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep  1 16:22:28 owner kernel: [   28.391443] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  1 16:22:28 owner kernel: [   28.396007] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  1 16:22:28 owner kernel: [   28.396014] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  1 16:22:28 owner kernel: [   28.396177] EISA: Probing bus 0 at eisa.0
Sep  1 16:22:28 owner kernel: [   28.396187] Cannot allocate resource for EISA slot 1
Sep  1 16:22:28 owner kernel: [   28.396190] Cannot allocate resource for EISA slot 2
Sep  1 16:22:28 owner kernel: [   28.396209] Cannot allocate resource for EISA slot 8
Sep  1 16:22:28 owner kernel: [   28.396211] EISA: Detected 0 cards.
Sep  1 16:22:28 owner kernel: [   28.426255] TCP cubic registered
Sep  1 16:22:28 owner kernel: [   28.426265] NET: Registered protocol family 1
Sep  1 16:22:28 owner kernel: [   28.426289] Using IPI No-Shortcut mode
Sep  1 16:22:28 owner kernel: [   28.426352] ACPI: (supports S0 S3 S4 S5)
Sep  1 16:22:28 owner kernel: [   28.426386]   Magic number: 7:144:398
Sep  1 16:22:28 owner kernel: [   28.426833] Freeing unused kernel memory: 328k freed
Sep  1 16:22:28 owner kernel: [   28.429055] Time: tsc clocksource has been installed.
Sep  1 16:22:28 owner kernel: [   28.443053] input: AT Translated Set 2 keyboard as /class/input/input1
Sep  1 16:22:28 owner kernel: [   29.696623] Capability LSM initialized
Sep  1 16:22:28 owner kernel: [   29.744988] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  1 16:22:28 owner kernel: [   29.748240] ACPI: Thermal Zone [THRM] (60 C)
Sep  1 16:22:28 owner kernel: [   30.423554] SIS5513: IDE controller at PCI slot 0000:00:02.5
Sep  1 16:22:28 owner kernel: [   30.423573] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 18
Sep  1 16:22:28 owner kernel: [   30.423583] SIS5513: chipset revision 0
Sep  1 16:22:28 owner kernel: [   30.423585] SIS5513: not 100%% native mode: will probe irqs later
Sep  1 16:22:28 owner kernel: [   30.423597] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
Sep  1 16:22:28 owner kernel: [   30.423609]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
Sep  1 16:22:28 owner kernel: [   30.423620]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
Sep  1 16:22:28 owner kernel: [   30.456219] usbcore: registered new interface driver usbfs
Sep  1 16:22:28 owner kernel: [   30.456241] usbcore: registered new interface driver hub
Sep  1 16:22:28 owner kernel: [   30.456260] usbcore: registered new device driver usb
Sep  1 16:22:28 owner kernel: [   30.492101] sis900.c: v1.08.10 Apr. 2 2006
Sep  1 16:22:28 owner kernel: [    3.900000] Time: acpi_pm clocksource has been installed.
Sep  1 16:22:28 owner kernel: [    3.936000] hda: TOSHIBA MK6025GAS, ATA DISK drive
Sep  1 16:22:28 owner kernel: [    4.608000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep  1 16:22:28 owner kernel: [    5.404000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
Sep  1 16:22:28 owner kernel: [    6.076000] ide1 at 0x170-0x177,0x376 on irq 15
Sep  1 16:22:28 owner kernel: [    6.084000] SCSI subsystem initialized
Sep  1 16:22:28 owner kernel: [    6.096000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 19
Sep  1 16:22:28 owner kernel: [    6.096000] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep  1 16:22:28 owner kernel: [    6.096000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Sep  1 16:22:28 owner kernel: [    6.096000] ohci_hcd 0000:00:03.0: irq 19, io mem 0xe2002000
Sep  1 16:22:28 owner kernel: [    6.108000] hda: max request size: 128KiB
Sep  1 16:22:28 owner kernel: [    6.120000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
Sep  1 16:22:28 owner kernel: [    6.120000] hda: cache flushes supported
Sep  1 16:22:28 owner kernel: [    6.120000]  hda:<6>usb usb1: configuration #1 chosen from 1 choice
Sep  1 16:22:28 owner kernel: [    6.152000] hub 1-0:1.0: USB hub found
Sep  1 16:22:28 owner kernel: [    6.152000] hub 1-0:1.0: 3 ports detected
Sep  1 16:22:28 owner kernel: [    6.176000]  hda1 hda2 < hda5 >
Sep  1 16:22:28 owner kernel: [    6.216000] hdc: ATAPI 20X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep  1 16:22:28 owner kernel: [    6.216000] Uniform CD-ROM driver Revision: 3.20
Sep  1 16:22:28 owner kernel: [    6.256000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 20
Sep  1 16:22:28 owner kernel: [    6.256000] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep  1 16:22:28 owner kernel: [    6.256000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Sep  1 16:22:28 owner kernel: [    6.256000] ohci_hcd 0000:00:03.1: irq 20, io mem 0xe2003000
Sep  1 16:22:28 owner kernel: [    6.312000] usb usb2: configuration #1 chosen from 1 choice
Sep  1 16:22:28 owner kernel: [    6.312000] hub 2-0:1.0: USB hub found
Sep  1 16:22:28 owner kernel: [    6.312000] hub 2-0:1.0: 3 ports detected
Sep  1 16:22:28 owner kernel: [    6.416000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 21
Sep  1 16:22:28 owner kernel: [    6.416000] ehci_hcd 0000:00:03.2: EHCI Host Controller
Sep  1 16:22:28 owner kernel: [    6.416000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Sep  1 16:22:28 owner kernel: [    6.416000] ehci_hcd 0000:00:03.2: irq 21, io mem 0xe2004000
Sep  1 16:22:28 owner kernel: [    6.416000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  1 16:22:28 owner kernel: [    6.416000] usb usb3: configuration #1 chosen from 1 choice
Sep  1 16:22:28 owner kernel: [    6.416000] hub 3-0:1.0: USB hub found
Sep  1 16:22:28 owner kernel: [    6.416000] hub 3-0:1.0: 6 ports detected
Sep  1 16:22:28 owner kernel: [    6.520000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  1 16:22:28 owner kernel: [    6.524000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Sep  1 16:22:28 owner kernel: [    6.528000] 0000:00:04.0: Using transceiver found at address 13 as default
Sep  1 16:22:28 owner kernel: [    6.528000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 16, 00:c0:9f:c1:44:ea.
Sep  1 16:22:28 owner kernel: [    6.604000] kjournald starting.  Commit interval 5 seconds
Sep  1 16:22:28 owner kernel: [    6.604000] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 16:22:28 owner kernel: [    7.104000] usb 1-2: new low speed USB device using ohci_hcd and address 3
Sep  1 16:22:28 owner kernel: [    7.312000] usb 1-2: configuration #1 chosen from 1 choice
Sep  1 16:22:28 owner kernel: [   21.068000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  1 16:22:28 owner kernel: [   21.072000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  1 16:22:28 owner kernel: [   21.112000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
Sep  1 16:22:28 owner kernel: [   21.364000] Linux agpgart interface v0.102 (c) Dave Jones
Sep  1 16:22:28 owner kernel: [   21.412000] agpgart: Detected AGP bridge 0
Sep  1 16:22:28 owner kernel: [   21.412000] agpgart: AGP aperture is 32M @ 0xe0000000
Sep  1 16:22:28 owner kernel: [   21.452000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
Sep  1 16:22:28 owner kernel: [   21.452000] Yenta: Using CSCINT to route CSC interrupts to PCI
Sep  1 16:22:28 owner kernel: [   21.452000] Yenta: Routing CardBus interrupts to PCI
Sep  1 16:22:28 owner kernel: [   21.452000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
Sep  1 16:22:28 owner kernel: [   21.684000] Yenta: ISA IRQ mask 0x06f8, PCI irq 16
Sep  1 16:22:28 owner kernel: [   21.684000] Socket status: 30000006
Sep  1 16:22:28 owner kernel: [   21.848000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep  1 16:22:28 owner kernel: [   21.848000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep  1 16:22:28 owner kernel: [   21.968000] input: PC Speaker as /class/input/input2
Sep  1 16:22:28 owner kernel: [   22.044000] usbcore: registered new interface driver hiddev
Sep  1 16:22:28 owner kernel: [   22.136000] bcm43xx driver
Sep  1 16:22:28 owner kernel: [   22.136000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  1 16:22:28 owner kernel: [   22.252000] input: HID 1241:1166 as /class/input/input3
Sep  1 16:22:28 owner kernel: [   22.252000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:03.0-2
Sep  1 16:22:28 owner kernel: [   22.252000] usbcore: registered new interface driver usbhid
Sep  1 16:22:28 owner kernel: [   22.252000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Sep  1 16:22:28 owner kernel: [   22.312000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
Sep  1 16:22:28 owner kernel: [   22.476000] cs: IO port probe 0x100-0x3af: clean.
Sep  1 16:22:28 owner kernel: [   22.476000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
Sep  1 16:22:28 owner kernel: [   22.476000] cs: IO port probe 0x820-0x8ff: clean.
Sep  1 16:22:28 owner kernel: [   22.476000] cs: IO port probe 0xc00-0xcf7: clean.
Sep  1 16:22:28 owner kernel: [   22.476000] cs: IO port probe 0xa00-0xaff: clean.
Sep  1 16:22:28 owner kernel: [   22.588000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Sep  1 16:22:28 owner kernel: [   22.624000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Sep  1 16:22:28 owner kernel: [   23.132000] intel8x0_measure_ac97_clock: measured 55466 usecs
Sep  1 16:22:28 owner kernel: [   23.132000] intel8x0: clocking to 48000
Sep  1 16:22:28 owner kernel: [   23.340000] lp: driver loaded but no devices found
Sep  1 16:22:28 owner kernel: [   23.416000] Adding 2441840k swap on /dev/disk/by-uuid/ed70067a-bce9-4fb6-907f-2c4c81db4df4.  Priority:-1 extents:1 across:2441840k
Sep  1 16:22:28 owner kernel: [   23.552000] EXT3 FS on hda1, internal journal
Sep  1 16:22:28 owner kernel: [   24.612000] ACPI: Battery Slot [BAT1] (battery present)
Sep  1 16:22:28 owner kernel: [   24.652000] ACPI: AC Adapter [ACAD] (on-line)
Sep  1 16:22:28 owner kernel: [   24.696000] No dock devices found.
Sep  1 16:22:28 owner kernel: [   24.772000] Using specific hotkey driver
Sep  1 16:22:28 owner kernel: [   24.876000] input: Power Button (FF) as /class/input/input5
Sep  1 16:22:28 owner kernel: [   24.880000] ACPI: Power Button (FF) [PWRF]
Sep  1 16:22:28 owner kernel: [   24.916000] input: Lid Switch as /class/input/input6
Sep  1 16:22:28 owner kernel: [   24.920000] ACPI: Lid Switch [LID]
Sep  1 16:22:28 owner kernel: [   24.960000] input: Power Button (CM) as /class/input/input7
Sep  1 16:22:28 owner kernel: [   24.964000] ACPI: Power Button (CM) [PWRB]
Sep  1 16:22:28 owner kernel: [   25.004000] input: Sleep Button (CM) as /class/input/input8
Sep  1 16:22:28 owner kernel: [   25.008000] ACPI: Sleep Button (CM) [SLPB]
Sep  1 16:22:28 owner kernel: [   25.100000] pcc_acpi: loading...
Sep  1 16:22:28 owner kernel: [   25.404000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
Sep  1 16:22:28 owner kernel: [   25.404000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
Sep  1 16:22:28 owner kernel: [   25.404000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
Sep  1 16:22:28 owner kernel: [   25.404000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
Sep  1 16:22:31 owner kernel: [   28.500000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:22:31 owner kernel: [   28.516000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:22:31 owner kernel: [   28.548000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:22:31 owner dhcdbd: Started up.
Sep  1 16:22:31 owner kernel: [   29.008000] eth1: Media Link Off
Sep  1 16:22:34 owner kernel: [   31.580000] ppdev: user-space parallel port driver
Sep  1 16:22:35 owner hpiod: 1.7.3 accepting connections at 2208... 
Sep  1 16:22:36 owner kernel: [   33.464000] apm: BIOS not found.
Sep  1 16:22:36 owner kernel: [   33.924000] Bluetooth: Core ver 2.11
Sep  1 16:22:36 owner kernel: [   33.924000] NET: Registered protocol family 31
Sep  1 16:22:36 owner kernel: [   33.924000] Bluetooth: HCI device and connection manager initialized
Sep  1 16:22:36 owner kernel: [   33.924000] Bluetooth: HCI socket layer initialized
Sep  1 16:22:36 owner kernel: [   33.948000] Bluetooth: L2CAP ver 2.8
Sep  1 16:22:36 owner kernel: [   33.948000] Bluetooth: L2CAP socket layer initialized
Sep  1 16:22:36 owner kernel: [   34.000000] Bluetooth: RFCOMM socket layer initialized
Sep  1 16:22:36 owner kernel: [   34.000000] Bluetooth: RFCOMM TTY layer initialized
Sep  1 16:22:36 owner kernel: [   34.000000] Bluetooth: RFCOMM ver 1.8
Sep  1 16:22:37 owner kernel: [   34.648000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Sep  1 16:22:37 owner kernel: [   34.648000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Sep  1 16:22:37 owner kernel: [   34.648000] ide: failed opcode was: unknown
Sep  1 16:22:37 owner kernel: [   34.648000] end_request: I/O error, dev hdc, sector 64
Sep  1 16:22:43 owner kernel: [   40.656000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Sep  1 16:22:43 owner kernel: [   40.656000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Sep  1 16:22:43 owner kernel: [   40.656000] ide: failed opcode was: unknown
Sep  1 16:22:43 owner kernel: [   40.656000] end_request: I/O error, dev hdc, sector 64
Sep  1 16:22:47 owner gconfd (owner-4928): starting (version 2.18.0.1), pid 4928 user 'owner'
Sep  1 16:22:47 owner gconfd (owner-4928): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  1 16:22:47 owner gconfd (owner-4928): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  1 16:22:47 owner gconfd (owner-4928): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  1 16:22:47 owner gconfd (owner-4928): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  1 16:22:47 owner gconfd (owner-4928): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  1 16:22:50 owner kernel: [   47.888000] NET: Registered protocol family 10
Sep  1 16:22:50 owner kernel: [   47.888000] lo: Disabled Privacy Extensions
Sep  1 16:22:50 owner kernel: [   47.888000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep  1 16:22:57 owner gconfd (owner-4928): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 0
Sep  1 16:22:58 owner kernel: [   56.096000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:23:28 owner kernel: [   86.068000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:23:58 owner kernel: [  116.056000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  1 16:24:03 owner gconfd (root-5103): starting (version 2.18.0.1), pid 5103 user 'root'
Sep  1 16:24:03 owner gconfd (root-5103): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  1 16:24:03 owner gconfd (root-5103): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Sep  1 16:24:03 owner gconfd (root-5103): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  1 16:24:03 owner gconfd (root-5103): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  1 16:24:03 owner gconfd (root-5103): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  1 16:24:04 owner kernel: [  121.264000] c0172d3a
Sep  1 16:24:04 owner kernel: [  121.264000] Modules linked in: ipv6 binfmt_misc rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_ondemand cpufreq_userspace freq_table cpufreq_conservative cpufreq_powersave pcc_acpi tc1100_wmi dev_acpi sony_acpi container button video dock sbs i2c_ec ac asus_acpi battery backlight parport_pc lp parport joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss pcmcia bcm43xx usbhid hid psmouse ieee80211softmac pcspkr serio_raw k8temp snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore ieee80211 ieee80211_crypt sis_agp snd_page_alloc yenta_socket rsrc_nonstatic pcmcia_core amd64_agp agpgart i2c_sis96x i2c_core shpchp pci_hotplug tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod sis900 mii ehci_hcd ohci_hcd usbcore sis5513 generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Sep  1 16:24:04 owner gconfd (root-5119): starting (version 2.18.0.1), pid 5119 user 'root'
Sep  1 16:24:04 owner kernel: [  121.264000]  <1>BUG: unable to handle kernel NULL pointer dereference at virtual address 00000380
Sep  1 16:24:04 owner kernel: [  121.352000] c0161236
Sep  1 16:24:04 owner kernel: [  121.352000] Modules linked in: ipv6 binfmt_misc rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_ondemand cpufreq_userspace freq_table cpufreq_conservative cpufreq_powersave pcc_acpi tc1100_wmi dev_acpi sony_acpi container button video dock sbs i2c_ec ac asus_acpi battery backlight parport_pc lp parport joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss pcmcia bcm43xx usbhid hid psmouse ieee80211softmac pcspkr serio_raw k8temp snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore ieee80211 ieee80211_crypt sis_agp snd_page_alloc yenta_socket rsrc_nonstatic pcmcia_core amd64_agp agpgart i2c_sis96x i2c_core shpchp pci_hotplug tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod sis900 mii ehci_hcd ohci_hcd usbcore sis5513 generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Sep  1 16:24:04 owner gconfd (root-5142): starting (version 2.18.0.1), pid 5142 user 'root'
Sep  1 16:24:05 owner kernel: [  121.352000]  <1>BUG: unable to handle kernel NULL pointer dereference at virtual address 00000180
Sep  1 16:24:05 owner kernel: [  123.024000] c017326c
Sep  1 16:24:05 owner kernel: [  123.024000] Modules linked in: ipv6 binfmt_misc rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_ondemand cpufreq_userspace freq_table cpufreq_conservative cpufreq_powersave pcc_acpi tc1100_wmi dev_acpi sony_acpi container button video dock sbs i2c_ec ac asus_acpi battery backlight parport_pc lp parport joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss pcmcia bcm43xx usbhid hid psmouse ieee80211softmac pcspkr serio_raw k8temp snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore ieee80211 ieee80211_crypt sis_agp snd_page_alloc yenta_socket rsrc_nonstatic pcmcia_core amd64_agp agpgart i2c_sis96x i2c_core shpchp pci_hotplug tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod sis900 mii ehci_hcd ohci_hcd usbcore sis5513 generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Sep  1 16:24:08 owner kernel: [  123.024000]  <1>BUG: unable to handle kernel NULL pointer dereference at virtual address 00000680
Sep  1 16:24:08 owner kernel: [  125.380000] c0190a68
Sep  1 16:24:08 owner kernel: [  125.380000] Modules linked in: ipv6 binfmt_misc rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_ondemand cpufreq_userspace freq_table cpufreq_conservative cpufreq_powersave pcc_acpi tc1100_wmi dev_acpi sony_acpi container button video dock sbs i2c_ec ac asus_acpi battery backlight parport_pc lp parport joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss pcmcia bcm43xx usbhid hid psmouse ieee80211softmac pcspkr serio_raw k8temp snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore ieee80211 ieee80211_crypt sis_agp snd_page_alloc yenta_socket rsrc_nonstatic pcmcia_core amd64_agp agpgart i2c_sis96x i2c_core shpchp pci_hotplug tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod sis900 mii ehci_hcd ohci_hcd usbcore sis5513 generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Sep  2 08:39:38 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  2 08:39:38 owner kernel: Inspecting /boot/System.map-2.6.20-15-generic
Sep  2 08:39:38 owner kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Sep  2 08:39:38 owner kernel: Symbols match kernel version 2.6.20.
Sep  2 08:39:38 owner kernel: No module symbols loaded - kernel modules not enabled. 
Sep  2 08:39:38 owner kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Sep  2 08:39:38 owner kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  2 08:39:38 owner kernel: [    0.000000] sanitize start
Sep  2 08:39:38 owner kernel: [    0.000000] sanitize end
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000047df0000 end: 0000000047ef0000 type: 1
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() start: 0000000047ef0000 size: 000000000000a000 end: 0000000047efa000 type: 3
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() start: 0000000047efa000 size: 0000000000006000 end: 0000000047f00000 type: 4
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() start: 0000000047f00000 size: 0000000008100000 end: 0000000050000000 type: 2
Sep  2 08:39:38 owner kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Sep  2 08:39:38 owner kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Sep  2 08:39:38 owner kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Sep  2 08:39:38 owner kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Sep  2 08:39:38 owner kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000047ef0000 (usable)
Sep  2 08:39:38 owner kernel: [    0.000000]  BIOS-e820: 0000000047ef0000 - 0000000047efa000 (ACPI data)
Sep  2 08:39:38 owner kernel: [    0.000000]  BIOS-e820: 0000000047efa000 - 0000000047f00000 (ACPI NVS)
Sep  2 08:39:38 owner kernel: [    0.000000]  BIOS-e820: 0000000047f00000 - 0000000050000000 (reserved)
Sep  2 08:39:38 owner kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Sep  2 08:39:38 owner kernel: [    0.000000] 254MB HIGHMEM available.
Sep  2 08:39:38 owner kernel: [    0.000000] 896MB LOWMEM available.
Sep  2 08:39:38 owner kernel: [    0.000000] found SMP MP-table at 000f7fd0
Sep  2 08:39:38 owner kernel: [    0.000000] Zone PFN ranges:
Sep  2 08:39:38 owner kernel: [    0.000000]   DMA             0 ->     4096
Sep  2 08:39:38 owner kernel: [    0.000000]   Normal       4096 ->   229376
Sep  2 08:39:38 owner kernel: [    0.000000]   HighMem    229376 ->   294640
Sep  2 08:39:38 owner kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  2 08:39:38 owner kernel: [    0.000000]     0:        0 ->   294640
Sep  2 08:39:38 owner kernel: [    0.000000] DMI present.
Sep  2 08:39:38 owner kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Sep  2 08:39:38 owner kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  2 08:39:38 owner kernel: [    0.000000] Processor #0 15:12 APIC version 16
Sep  2 08:39:38 owner kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  2 08:39:38 owner kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  2 08:39:38 owner kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Sep  2 08:39:38 owner kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Sep  2 08:39:38 owner kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  2 08:39:38 owner kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  2 08:39:38 owner kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aff00000)
Sep  2 08:39:38 owner kernel: [    0.000000] Detected 1800.170 MHz processor.
Sep  2 08:39:38 owner kernel: [   12.566332] Built 1 zonelists.  Total pages: 292339
Sep  2 08:39:38 owner kernel: [   12.566335] Kernel command line: root=UUID=36f4f755-b608-49ce-b11a-e96f60601f95 ro quiet splash
Sep  2 08:39:38 owner kernel: [   12.566482] Enabling fast FPU save and restore... done.
Sep  2 08:39:38 owner kernel: [   12.566484] Enabling unmasked SIMD FPU exception support... done.
Sep  2 08:39:38 owner kernel: [   12.566492] Initializing CPU#0
Sep  2 08:39:38 owner kernel: [   12.566534] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  2 08:39:38 owner kernel: [   12.567294] Console: colour VGA+ 80x25
Sep  2 08:39:38 owner kernel: [   12.567878] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  2 08:39:38 owner kernel: [   12.568868] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  2 08:39:38 owner kernel: [   12.599327] Memory: 1157148k/1178560k available (1992k kernel code, 20492k reserved, 893k data, 328k init, 261056k highmem)
Sep  2 08:39:38 owner kernel: [   12.599338] virtual kernel memory layout:
Sep  2 08:39:38 owner kernel: [   12.599339]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep  2 08:39:38 owner kernel: [   12.599340]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  2 08:39:38 owner kernel: [   12.599341]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  2 08:39:38 owner kernel: [   12.599343]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  2 08:39:38 owner kernel: [   12.599344]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Sep  2 08:39:38 owner kernel: [   12.599345]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Sep  2 08:39:38 owner kernel: [   12.599347]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Sep  2 08:39:38 owner kernel: [   12.599350] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  2 08:39:38 owner kernel: [   12.678374] Calibrating delay using timer specific routine.. 3602.03 BogoMIPS (lpj=7204077)
Sep  2 08:39:38 owner kernel: [   12.678420] Security Framework v1.0.0 initialized
Sep  2 08:39:38 owner kernel: [   12.678428] SELinux:  Disabled at boot.
Sep  2 08:39:38 owner kernel: [   12.678445] Mount-cache hash table entries: 512
Sep  2 08:39:38 owner kernel: [   12.678606] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  2 08:39:38 owner kernel: [   12.678608] CPU: L2 Cache: 128K (64 bytes/line)
Sep  2 08:39:38 owner kernel: [   12.678622] Compat vDSO mapped to ffffe000.
Sep  2 08:39:38 owner kernel: [   12.678627] Remapping vsyscall page to ffffe000
Sep  2 08:39:38 owner kernel: [   12.678637] Checking 'hlt' instruction... OK.
Sep  2 08:39:38 owner kernel: [   12.694505] SMP alternatives: switching to UP code
Sep  2 08:39:38 owner kernel: [   12.694811] Freeing SMP alternatives: 11k freed
Sep  2 08:39:38 owner kernel: [   12.695072] Early unpacking initramfs... done
Sep  2 08:39:38 owner kernel: [   13.007345] ACPI: Core revision 20060707
Sep  2 08:39:38 owner kernel: [   13.007563] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep  2 08:39:38 owner kernel: [   13.011063] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
Sep  2 08:39:38 owner kernel: [   13.011083] Total of 1 processors activated (3602.03 BogoMIPS).
Sep  2 08:39:38 owner kernel: [   13.011236] ENABLING IO-APIC IRQs
Sep  2 08:39:38 owner kernel: [   13.011429] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  2 08:39:38 owner kernel: [   13.157705] Brought up 1 CPUs
Sep  2 08:39:38 owner kernel: [   13.157928] Booting paravirtualized kernel on bare hardware
Sep  2 08:39:38 owner kernel: [   13.158006] Time: 13:39:12  Date: 08/02/107
Sep  2 08:39:38 owner kernel: [   13.158042] NET: Registered protocol family 16
Sep  2 08:39:38 owner kernel: [   13.158144] EISA bus registered
Sep  2 08:39:38 owner kernel: [   13.158148] ACPI: bus type pci registered
Sep  2 08:39:38 owner kernel: [   13.158294] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
Sep  2 08:39:38 owner kernel: [   13.158297] PCI: Using configuration type 1
Sep  2 08:39:38 owner kernel: [   13.158299] Setting up standard PCI resources
Sep  2 08:39:38 owner kernel: [   13.160689] ACPI: Interpreter enabled
Sep  2 08:39:38 owner kernel: [   13.160694] ACPI: Using IOAPIC for interrupt routing
Sep  2 08:39:38 owner kernel: [   13.161033] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  2 08:39:38 owner kernel: [   13.162144] Enabling SiS 96x SMBus.
Sep  2 08:39:38 owner kernel: [   13.183189] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
Sep  2 08:39:38 owner kernel: [   13.183368] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
Sep  2 08:39:38 owner kernel: [   13.183542] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
Sep  2 08:39:38 owner kernel: [   13.183712] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
Sep  2 08:39:38 owner kernel: [   13.183902] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
Sep  2 08:39:38 owner kernel: [   13.184074] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
Sep  2 08:39:38 owner kernel: [   13.184250] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Sep  2 08:39:38 owner kernel: [   13.184419] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
Sep  2 08:39:38 owner kernel: [   13.184707] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  2 08:39:38 owner kernel: [   13.184718] pnp: PnP ACPI init
Sep  2 08:39:38 owner kernel: [   13.186383] pnp: PnP ACPI: found 8 devices
Sep  2 08:39:38 owner kernel: [   13.186389] PnPBIOS: Disabled by ACPI PNP
Sep  2 08:39:38 owner kernel: [   13.186443] PCI: Using ACPI for IRQ routing
Sep  2 08:39:38 owner kernel: [   13.186446] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  2 08:39:38 owner kernel: [   13.188560] NET: Registered protocol family 8
Sep  2 08:39:38 owner kernel: [   13.188562] NET: Registered protocol family 20
Sep  2 08:39:38 owner kernel: [   13.188744] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
Sep  2 08:39:38 owner kernel: [   13.188747] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
Sep  2 08:39:38 owner kernel: [   13.188750] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
Sep  2 08:39:38 owner kernel: [   13.188753] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
Sep  2 08:39:38 owner kernel: [   13.189001] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
Sep  2 08:39:38 owner kernel: [   13.189004] PCI: Bridge: 0000:00:01.0
Sep  2 08:39:38 owner kernel: [   13.189007]   IO window: a000-afff
Sep  2 08:39:38 owner kernel: [   13.189011]   MEM window: e2100000-e21fffff
Sep  2 08:39:38 owner kernel: [   13.189014]   PREFETCH window: e8000000-efffffff
Sep  2 08:39:38 owner kernel: [   13.189019] PCI: Bus 2, cardbus bridge: 0000:00:06.0
Sep  2 08:39:38 owner kernel: [   13.189021]   IO window: 00002400-000024ff
Sep  2 08:39:38 owner kernel: [   13.189024]   IO window: 00002800-000028ff
Sep  2 08:39:38 owner kernel: [   13.189028]   PREFETCH window: 60000000-63ffffff
Sep  2 08:39:38 owner kernel: [   13.189032]   MEM window: 64000000-67ffffff
Sep  2 08:39:38 owner kernel: [   13.189048] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
Sep  2 08:39:38 owner kernel: [   13.189059] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 08:39:38 owner kernel: [   13.189100] NET: Registered protocol family 2
Sep  2 08:39:38 owner kernel: [   13.225657] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  2 08:39:38 owner kernel: [   13.225877] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  2 08:39:38 owner kernel: [   13.227213] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  2 08:39:38 owner kernel: [   13.227895] TCP: Hash tables configured (established 131072 bind 65536)
Sep  2 08:39:38 owner kernel: [   13.227900] TCP reno registered
Sep  2 08:39:38 owner kernel: [   13.237694] checking if image is initramfs... it is
Sep  2 08:39:38 owner kernel: [   13.853470] Freeing initrd memory: 6782k freed
Sep  2 08:39:38 owner kernel: [   13.853655] Simple Boot Flag at 0x38 set to 0x1
Sep  2 08:39:38 owner kernel: [   13.853913] audit: initializing netlink socket (disabled)
Sep  2 08:39:38 owner kernel: [   13.853927] audit(1188740352.368:1): initialized
Sep  2 08:39:38 owner kernel: [   13.853988] highmem bounce pool size: 64 pages
Sep  2 08:39:38 owner kernel: [   13.854069] VFS: Disk quotas dquot_6.5.1
Sep  2 08:39:38 owner kernel: [   13.854092] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  2 08:39:38 owner kernel: [   13.854150] io scheduler noop registered
Sep  2 08:39:38 owner kernel: [   13.854152] io scheduler anticipatory registered
Sep  2 08:39:38 owner kernel: [   13.854154] io scheduler deadline registered
Sep  2 08:39:38 owner kernel: [   13.854167] io scheduler cfq registered (default)
Sep  2 08:39:38 owner kernel: [   14.288239] isapnp: Scanning for PnP cards...
Sep  2 08:39:38 owner kernel: [   14.641113] isapnp: No Plug & Play device found
Sep  2 08:39:38 owner kernel: [   14.680132] Real Time Clock Driver v1.12ac
Sep  2 08:39:38 owner kernel: [   14.680170] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  2 08:39:38 owner kernel: [   14.681101] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 08:39:38 owner kernel: [   14.681109] ACPI: PCI interrupt for device 0000:00:02.6 disabled
Sep  2 08:39:38 owner kernel: [   14.681170] mice: PS/2 mouse device common for all mice
Sep  2 08:39:38 owner kernel: [   14.681618] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  2 08:39:38 owner kernel: [   14.681860] input: Macintosh mouse button emulation as /class/input/input0
Sep  2 08:39:38 owner kernel: [   14.681894] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep  2 08:39:38 owner kernel: [   14.681899] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep  2 08:39:38 owner kernel: [   14.682104] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  2 08:39:38 owner kernel: [   14.685350] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  2 08:39:38 owner kernel: [   14.685358] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  2 08:39:38 owner kernel: [   14.685519] EISA: Probing bus 0 at eisa.0
Sep  2 08:39:38 owner kernel: [   14.685529] Cannot allocate resource for EISA slot 1
Sep  2 08:39:38 owner kernel: [   14.685531] Cannot allocate resource for EISA slot 2
Sep  2 08:39:38 owner kernel: [   14.685550] Cannot allocate resource for EISA slot 8
Sep  2 08:39:38 owner kernel: [   14.685552] EISA: Detected 0 cards.
Sep  2 08:39:38 owner kernel: [   14.715597] TCP cubic registered
Sep  2 08:39:38 owner kernel: [   14.715606] NET: Registered protocol family 1
Sep  2 08:39:38 owner kernel: [   14.715631] Using IPI No-Shortcut mode
Sep  2 08:39:38 owner kernel: [   14.715691] ACPI: (supports S0 S3 S4 S5)
Sep  2 08:39:38 owner kernel: [   14.715724]   Magic number: 7:677:684
Sep  2 08:39:38 owner kernel: [   14.715841]   hash matches device full
Sep  2 08:39:38 owner kernel: [   14.716176] Freeing unused kernel memory: 328k freed
Sep  2 08:39:38 owner kernel: [   14.719373] Time: tsc clocksource has been installed.
Sep  2 08:39:38 owner kernel: [   14.732727] input: AT Translated Set 2 keyboard as /class/input/input1
Sep  2 08:39:38 owner kernel: [   15.990925] Capability LSM initialized
Sep  2 08:39:38 owner kernel: [   16.039422] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 08:39:38 owner kernel: [   16.042677] ACPI: Thermal Zone [THRM] (30 C)
Sep  2 08:39:38 owner kernel: [   16.711628] SIS5513: IDE controller at PCI slot 0000:00:02.5
Sep  2 08:39:38 owner kernel: [   16.711646] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 18
Sep  2 08:39:38 owner kernel: [   16.711655] SIS5513: chipset revision 0
Sep  2 08:39:38 owner kernel: [   16.711657] SIS5513: not 100%% native mode: will probe irqs later
Sep  2 08:39:38 owner kernel: [   16.711669] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
Sep  2 08:39:38 owner kernel: [   16.711682]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
Sep  2 08:39:38 owner kernel: [   16.711693]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
Sep  2 08:39:38 owner kernel: [   16.755853] usbcore: registered new interface driver usbfs
Sep  2 08:39:38 owner kernel: [   16.755875] usbcore: registered new interface driver hub
Sep  2 08:39:38 owner kernel: [   16.755895] usbcore: registered new device driver usb
Sep  2 08:39:38 owner kernel: [   16.775531] sis900.c: v1.08.10 Apr. 2 2006
Sep  2 08:39:38 owner kernel: [    3.920000] Time: acpi_pm clocksource has been installed.
Sep  2 08:39:38 owner kernel: [    3.964000] hda: TOSHIBA MK6025GAS, ATA DISK drive
Sep  2 08:39:38 owner kernel: [    4.636000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep  2 08:39:38 owner kernel: [    5.436000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
Sep  2 08:39:38 owner kernel: [    6.108000] ide1 at 0x170-0x177,0x376 on irq 15
Sep  2 08:39:38 owner kernel: [    6.116000] SCSI subsystem initialized
Sep  2 08:39:38 owner kernel: [    6.128000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 19
Sep  2 08:39:38 owner kernel: [    6.128000] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep  2 08:39:38 owner kernel: [    6.128000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Sep  2 08:39:38 owner kernel: [    6.128000] ohci_hcd 0000:00:03.0: irq 19, io mem 0xe2002000
Sep  2 08:39:38 owner kernel: [    6.140000] hda: max request size: 128KiB
Sep  2 08:39:38 owner kernel: [    6.152000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
Sep  2 08:39:38 owner kernel: [    6.156000] hda: cache flushes supported
Sep  2 08:39:38 owner kernel: [    6.156000]  hda:<6>usb usb1: configuration #1 chosen from 1 choice
Sep  2 08:39:38 owner kernel: [    6.184000] hub 1-0:1.0: USB hub found
Sep  2 08:39:38 owner kernel: [    6.184000] hub 1-0:1.0: 3 ports detected
Sep  2 08:39:38 owner kernel: [    6.212000]  hda1 hda2 < hda5 >
Sep  2 08:39:38 owner kernel: [    6.252000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep  2 08:39:38 owner kernel: [    6.252000] Uniform CD-ROM driver Revision: 3.20
Sep  2 08:39:38 owner kernel: [    6.288000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 20
Sep  2 08:39:38 owner kernel: [    6.288000] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep  2 08:39:38 owner kernel: [    6.288000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Sep  2 08:39:38 owner kernel: [    6.288000] ohci_hcd 0000:00:03.1: irq 20, io mem 0xe2003000
Sep  2 08:39:38 owner kernel: [    6.344000] usb usb2: configuration #1 chosen from 1 choice
Sep  2 08:39:38 owner kernel: [    6.344000] hub 2-0:1.0: USB hub found
Sep  2 08:39:38 owner kernel: [    6.344000] hub 2-0:1.0: 3 ports detected
Sep  2 08:39:38 owner kernel: [    6.448000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 21
Sep  2 08:39:38 owner kernel: [    6.448000] ehci_hcd 0000:00:03.2: EHCI Host Controller
Sep  2 08:39:38 owner kernel: [    6.448000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Sep  2 08:39:38 owner kernel: [    6.448000] ehci_hcd 0000:00:03.2: irq 21, io mem 0xe2004000
Sep  2 08:39:38 owner kernel: [    6.448000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  2 08:39:38 owner kernel: [    6.448000] usb usb3: configuration #1 chosen from 1 choice
Sep  2 08:39:38 owner kernel: [    6.448000] hub 3-0:1.0: USB hub found
Sep  2 08:39:38 owner kernel: [    6.448000] hub 3-0:1.0: 6 ports detected
Sep  2 08:39:38 owner kernel: [    6.552000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 08:39:38 owner kernel: [    6.556000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Sep  2 08:39:38 owner kernel: [    6.560000] 0000:00:04.0: Using transceiver found at address 13 as default
Sep  2 08:39:38 owner kernel: [    6.560000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 16, 00:c0:9f:c1:44:ea.
Sep  2 08:39:38 owner kernel: [    6.596000] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  2 08:39:38 owner kernel: [    6.596000] EXT3-fs: write access will be enabled during recovery.
Sep  2 08:39:38 owner kernel: [    7.136000] usb 1-2: new low speed USB device using ohci_hcd and address 3
Sep  2 08:39:38 owner kernel: [    7.344000] usb 1-2: configuration #1 chosen from 1 choice
Sep  2 08:39:38 owner kernel: [    7.360000] usbcore: registered new interface driver hiddev
Sep  2 08:39:38 owner kernel: [    7.372000] input: HID 1241:1166 as /class/input/input2
Sep  2 08:39:38 owner kernel: [    7.372000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:03.0-2
Sep  2 08:39:38 owner kernel: [    7.372000] usbcore: registered new interface driver usbhid
Sep  2 08:39:38 owner kernel: [    7.372000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Sep  2 08:39:38 owner kernel: [    7.712000] kjournald starting.  Commit interval 5 seconds
Sep  2 08:39:38 owner kernel: [    7.712000] EXT3-fs: recovery complete.
Sep  2 08:39:38 owner kernel: [    7.720000] EXT3-fs: mounted filesystem with ordered data mode.
Sep  2 08:39:38 owner kernel: [   21.776000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  2 08:39:38 owner kernel: [   21.808000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  2 08:39:38 owner kernel: [   21.844000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
Sep  2 08:39:38 owner kernel: [   21.984000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep  2 08:39:38 owner kernel: [   21.984000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep  2 08:39:38 owner kernel: [   22.280000] Linux agpgart interface v0.102 (c) Dave Jones
Sep  2 08:39:38 owner kernel: [   22.332000] bcm43xx driver
Sep  2 08:39:38 owner kernel: [   22.332000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  2 08:39:38 owner kernel: [   22.384000] agpgart: Detected AGP bridge 0
Sep  2 08:39:38 owner kernel: [   22.384000] agpgart: AGP aperture is 32M @ 0xe0000000
Sep  2 08:39:38 owner kernel: [   22.516000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
Sep  2 08:39:38 owner kernel: [   22.516000] Yenta: Using CSCINT to route CSC interrupts to PCI
Sep  2 08:39:38 owner kernel: [   22.516000] Yenta: Routing CardBus interrupts to PCI
Sep  2 08:39:38 owner kernel: [   22.516000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
Sep  2 08:39:38 owner kernel: [   22.608000] input: PC Speaker as /class/input/input3
Sep  2 08:39:38 owner kernel: [   22.748000] Yenta: ISA IRQ mask 0x06f8, PCI irq 16
Sep  2 08:39:38 owner kernel: [   22.748000] Socket status: 30000006
Sep  2 08:39:38 owner kernel: [   23.116000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 08:39:38 owner kernel: [   23.212000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Sep  2 08:39:38 owner kernel: [   23.252000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Sep  2 08:39:38 owner kernel: [   23.268000] cs: IO port probe 0x100-0x3af: clean.
Sep  2 08:39:38 owner kernel: [   23.268000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
Sep  2 08:39:38 owner kernel: [   23.268000] cs: IO port probe 0x820-0x8ff: clean.
Sep  2 08:39:38 owner kernel: [   23.268000] cs: IO port probe 0xc00-0xcf7: clean.
Sep  2 08:39:38 owner kernel: [   23.268000] cs: IO port probe 0xa00-0xaff: clean.
Sep  2 08:39:38 owner kernel: [   23.936000] intel8x0_measure_ac97_clock: measured 55476 usecs
Sep  2 08:39:38 owner kernel: [   23.936000] intel8x0: clocking to 48000
Sep  2 08:39:38 owner kernel: [   24.176000] lp: driver loaded but no devices found
Sep  2 08:39:38 owner kernel: [   24.252000] Adding 2441840k swap on /dev/disk/by-uuid/ed70067a-bce9-4fb6-907f-2c4c81db4df4.  Priority:-1 extents:1 across:2441840k
Sep  2 08:39:38 owner kernel: [   24.388000] EXT3 FS on hda1, internal journal
Sep  2 08:39:38 owner kernel: [   25.060000] ACPI: Battery Slot [BAT1] (battery present)
Sep  2 08:39:38 owner kernel: [   25.100000] ACPI: AC Adapter [ACAD] (on-line)
Sep  2 08:39:38 owner kernel: [   25.144000] No dock devices found.
Sep  2 08:39:38 owner kernel: [   25.220000] Using specific hotkey driver
Sep  2 08:39:38 owner kernel: [   25.324000] input: Power Button (FF) as /class/input/input5
Sep  2 08:39:38 owner kernel: [   25.328000] ACPI: Power Button (FF) [PWRF]
Sep  2 08:39:38 owner kernel: [   25.364000] input: Lid Switch as /class/input/input6
Sep  2 08:39:38 owner kernel: [   25.372000] ACPI: Lid Switch [LID]
Sep  2 08:39:38 owner kernel: [   25.408000] input: Power Button (CM) as /class/input/input7
Sep  2 08:39:38 owner kernel: [   25.412000] ACPI: Power Button (CM) [PWRB]
Sep  2 08:39:38 owner kernel: [   25.452000] input: Sleep Button (CM) as /class/input/input8
Sep  2 08:39:38 owner kernel: [   25.456000] ACPI: Sleep Button (CM) [SLPB]
Sep  2 08:39:38 owner kernel: [   25.548000] pcc_acpi: loading...
Sep  2 08:39:38 owner kernel: [   25.796000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
Sep  2 08:39:38 owner kernel: [   25.796000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
Sep  2 08:39:38 owner kernel: [   25.796000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
Sep  2 08:39:38 owner kernel: [   25.796000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
Sep  2 08:39:41 owner kernel: [   28.740000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:39:41 owner kernel: [   28.760000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:39:41 owner kernel: [   28.792000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:39:41 owner dhcdbd: Started up.
Sep  2 08:39:43 owner kernel: [   30.988000] eth1: Media Link On 10mbps half-duplex 
Sep  2 08:39:43 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  2 08:39:43 owner kernel: [   31.084000] ppdev: user-space parallel port driver
Sep  2 08:39:45 owner hpiod: 1.7.3 accepting connections at 2208... 
Sep  2 08:39:45 owner kernel: [   33.416000] apm: BIOS not found.
Sep  2 08:39:46 owner kernel: [   33.608000] Bluetooth: Core ver 2.11
Sep  2 08:39:46 owner kernel: [   33.612000] NET: Registered protocol family 31
Sep  2 08:39:46 owner kernel: [   33.612000] Bluetooth: HCI device and connection manager initialized
Sep  2 08:39:46 owner kernel: [   33.612000] Bluetooth: HCI socket layer initialized
Sep  2 08:39:46 owner kernel: [   33.660000] Bluetooth: L2CAP ver 2.8
Sep  2 08:39:46 owner kernel: [   33.660000] Bluetooth: L2CAP socket layer initialized
Sep  2 08:39:46 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  2 08:39:46 owner kernel: [   33.748000] Bluetooth: RFCOMM socket layer initialized
Sep  2 08:39:46 owner kernel: [   33.748000] Bluetooth: RFCOMM TTY layer initialized
Sep  2 08:39:46 owner kernel: [   33.748000] Bluetooth: RFCOMM ver 1.8
Sep  2 08:39:48 owner kernel: [   35.912000] NET: Registered protocol family 17
Sep  2 08:39:49 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep  2 08:39:49 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Sep  2 08:39:49 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep  2 08:39:49 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep  2 08:39:50 owner kernel: [   37.948000] NET: Registered protocol family 10
Sep  2 08:39:50 owner kernel: [   37.948000] lo: Disabled Privacy Extensions
Sep  2 08:39:55 owner gconfd (owner-5015): starting (version 2.18.0.1), pid 5015 user 'owner'
Sep  2 08:39:55 owner gconfd (owner-5015): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 08:39:55 owner gconfd (owner-5015): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  2 08:39:55 owner gconfd (owner-5015): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 08:39:55 owner gconfd (owner-5015): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 08:39:55 owner gconfd (owner-5015): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 08:40:05 owner gconfd (owner-5015): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 0
Sep  2 08:40:08 owner kernel: [   57.820000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:40:38 owner kernel: [   87.792000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:41:08 owner kernel: [  117.788000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:41:38 owner kernel: [  147.792000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:42:08 owner kernel: [  177.796000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:42:38 owner kernel: [  207.788000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:43:08 owner kernel: [  237.788000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:43:35 owner kernel: [  264.816000] c01727b1
Sep  2 08:43:35 owner kernel: [  264.816000] Modules linked in: ipv6 af_packet binfmt_misc rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_ondemand cpufreq_userspace freq_table cpufreq_conservative cpufreq_powersave pcc_acpi tc1100_wmi dev_acpi sony_acpi container button video dock sbs i2c_ec ac asus_acpi battery backlight parport_pc lp parport joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss pcmcia snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse serio_raw pcspkr yenta_socket rsrc_nonstatic sis_agp k8temp snd soundcore snd_page_alloc pcmcia_core amd64_agp bcm43xx agpgart ieee80211softmac ieee80211 ieee80211_crypt i2c_sis96x i2c_core shpchp pci_hotplug evdev tsdev usbhid hid ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod sis900 mii ehci_hcd ohci_hcd usbcore sis5513 generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Sep  2 08:43:38 owner kernel: [  264.816000]  ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:46:05 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  2 08:46:05 owner kernel: Inspecting /boot/System.map-2.6.20-15-generic
Sep  2 08:46:05 owner kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Sep  2 08:46:05 owner kernel: Symbols match kernel version 2.6.20.
Sep  2 08:46:05 owner kernel: No module symbols loaded - kernel modules not enabled. 
Sep  2 08:46:05 owner kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Sep  2 08:46:05 owner kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  2 08:46:05 owner kernel: [    0.000000] sanitize start
Sep  2 08:46:05 owner kernel: [    0.000000] sanitize end
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000047df0000 end: 0000000047ef0000 type: 1
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000047ef0000 size: 000000000000a000 end: 0000000047efa000 type: 3
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000047efa000 size: 0000000000006000 end: 0000000047f00000 type: 4
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000047f00000 size: 0000000008100000 end: 0000000050000000 type: 2
Sep  2 08:46:05 owner kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Sep  2 08:46:05 owner kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Sep  2 08:46:05 owner kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Sep  2 08:46:05 owner kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Sep  2 08:46:05 owner kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000047ef0000 (usable)
Sep  2 08:46:05 owner kernel: [    0.000000]  BIOS-e820: 0000000047ef0000 - 0000000047efa000 (ACPI data)
Sep  2 08:46:05 owner kernel: [    0.000000]  BIOS-e820: 0000000047efa000 - 0000000047f00000 (ACPI NVS)
Sep  2 08:46:05 owner kernel: [    0.000000]  BIOS-e820: 0000000047f00000 - 0000000050000000 (reserved)
Sep  2 08:46:05 owner kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Sep  2 08:46:05 owner kernel: [    0.000000] 254MB HIGHMEM available.
Sep  2 08:46:05 owner kernel: [    0.000000] 896MB LOWMEM available.
Sep  2 08:46:05 owner kernel: [    0.000000] found SMP MP-table at 000f7fd0
Sep  2 08:46:05 owner kernel: [    0.000000] Zone PFN ranges:
Sep  2 08:46:05 owner kernel: [    0.000000]   DMA             0 ->     4096
Sep  2 08:46:05 owner kernel: [    0.000000]   Normal       4096 ->   229376
Sep  2 08:46:05 owner kernel: [    0.000000]   HighMem    229376 ->   294640
Sep  2 08:46:05 owner kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  2 08:46:05 owner kernel: [    0.000000]     0:        0 ->   294640
Sep  2 08:46:05 owner kernel: [    0.000000] DMI present.
Sep  2 08:46:05 owner kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Sep  2 08:46:05 owner kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  2 08:46:05 owner kernel: [    0.000000] Processor #0 15:12 APIC version 16
Sep  2 08:46:05 owner kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  2 08:46:05 owner kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  2 08:46:05 owner kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Sep  2 08:46:05 owner kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Sep  2 08:46:05 owner kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  2 08:46:05 owner kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  2 08:46:05 owner kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aff00000)
Sep  2 08:46:05 owner kernel: [    0.000000] Detected 1800.157 MHz processor.
Sep  2 08:46:05 owner kernel: [   11.951754] Built 1 zonelists.  Total pages: 292339
Sep  2 08:46:05 owner kernel: [   11.951757] Kernel command line: root=UUID=36f4f755-b608-49ce-b11a-e96f60601f95 ro quiet splash
Sep  2 08:46:05 owner kernel: [   11.951904] Enabling fast FPU save and restore... done.
Sep  2 08:46:05 owner kernel: [   11.951906] Enabling unmasked SIMD FPU exception support... done.
Sep  2 08:46:05 owner kernel: [   11.951914] Initializing CPU#0
Sep  2 08:46:05 owner kernel: [   11.951956] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  2 08:46:05 owner kernel: [   11.952716] Console: colour VGA+ 80x25
Sep  2 08:46:05 owner kernel: [   11.953300] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  2 08:46:05 owner kernel: [   11.954292] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  2 08:46:05 owner kernel: [   11.984745] Memory: 1157148k/1178560k available (1992k kernel code, 20492k reserved, 893k data, 328k init, 261056k highmem)
Sep  2 08:46:05 owner kernel: [   11.984755] virtual kernel memory layout:
Sep  2 08:46:05 owner kernel: [   11.984756]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep  2 08:46:05 owner kernel: [   11.984758]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  2 08:46:05 owner kernel: [   11.984759]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  2 08:46:05 owner kernel: [   11.984760]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  2 08:46:05 owner kernel: [   11.984762]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Sep  2 08:46:05 owner kernel: [   11.984763]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Sep  2 08:46:05 owner kernel: [   11.984764]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Sep  2 08:46:05 owner kernel: [   11.984768] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  2 08:46:05 owner kernel: [   12.063795] Calibrating delay using timer specific routine.. 3602.04 BogoMIPS (lpj=7204085)
Sep  2 08:46:05 owner kernel: [   12.063841] Security Framework v1.0.0 initialized
Sep  2 08:46:05 owner kernel: [   12.063850] SELinux:  Disabled at boot.
Sep  2 08:46:05 owner kernel: [   12.063866] Mount-cache hash table entries: 512
Sep  2 08:46:05 owner kernel: [   12.064027] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  2 08:46:05 owner kernel: [   12.064030] CPU: L2 Cache: 128K (64 bytes/line)
Sep  2 08:46:05 owner kernel: [   12.064044] Compat vDSO mapped to ffffe000.
Sep  2 08:46:05 owner kernel: [   12.064049] Remapping vsyscall page to ffffe000
Sep  2 08:46:05 owner kernel: [   12.064059] Checking 'hlt' instruction... OK.
Sep  2 08:46:05 owner kernel: [   12.079926] SMP alternatives: switching to UP code
Sep  2 08:46:05 owner kernel: [   12.080229] Freeing SMP alternatives: 11k freed
Sep  2 08:46:05 owner kernel: [   12.080492] Early unpacking initramfs... done
Sep  2 08:46:05 owner kernel: [   12.392759] ACPI: Core revision 20060707
Sep  2 08:46:05 owner kernel: [   12.392976] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep  2 08:46:05 owner kernel: [   12.396376] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
Sep  2 08:46:05 owner kernel: [   12.396395] Total of 1 processors activated (3602.04 BogoMIPS).
Sep  2 08:46:05 owner kernel: [   12.396549] ENABLING IO-APIC IRQs
Sep  2 08:46:05 owner kernel: [   12.396741] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  2 08:46:05 owner kernel: [   12.543127] Brought up 1 CPUs
Sep  2 08:46:05 owner kernel: [   12.543350] Booting paravirtualized kernel on bare hardware
Sep  2 08:46:05 owner kernel: [   12.543428] Time: 13:45:39  Date: 08/02/107
Sep  2 08:46:05 owner kernel: [   12.543465] NET: Registered protocol family 16
Sep  2 08:46:05 owner kernel: [   12.543566] EISA bus registered
Sep  2 08:46:05 owner kernel: [   12.543570] ACPI: bus type pci registered
Sep  2 08:46:05 owner kernel: [   12.543716] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
Sep  2 08:46:05 owner kernel: [   12.543718] PCI: Using configuration type 1
Sep  2 08:46:05 owner kernel: [   12.543720] Setting up standard PCI resources
Sep  2 08:46:05 owner kernel: [   12.546108] ACPI: Interpreter enabled
Sep  2 08:46:05 owner kernel: [   12.546113] ACPI: Using IOAPIC for interrupt routing
Sep  2 08:46:05 owner kernel: [   12.546451] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  2 08:46:05 owner kernel: [   12.547563] Enabling SiS 96x SMBus.
Sep  2 08:46:05 owner kernel: [   12.569978] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
Sep  2 08:46:05 owner kernel: [   12.570158] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
Sep  2 08:46:05 owner kernel: [   12.570333] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
Sep  2 08:46:05 owner kernel: [   12.570503] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
Sep  2 08:46:05 owner kernel: [   12.570693] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
Sep  2 08:46:05 owner kernel: [   12.570864] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
Sep  2 08:46:05 owner kernel: [   12.571040] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Sep  2 08:46:05 owner kernel: [   12.571221] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
Sep  2 08:46:05 owner kernel: [   12.571511] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  2 08:46:05 owner kernel: [   12.571523] pnp: PnP ACPI init
Sep  2 08:46:05 owner kernel: [   12.573168] pnp: PnP ACPI: found 8 devices
Sep  2 08:46:05 owner kernel: [   12.573174] PnPBIOS: Disabled by ACPI PNP
Sep  2 08:46:05 owner kernel: [   12.573230] PCI: Using ACPI for IRQ routing
Sep  2 08:46:05 owner kernel: [   12.573234] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  2 08:46:05 owner kernel: [   12.575366] NET: Registered protocol family 8
Sep  2 08:46:05 owner kernel: [   12.575368] NET: Registered protocol family 20
Sep  2 08:46:05 owner kernel: [   12.575558] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
Sep  2 08:46:05 owner kernel: [   12.575561] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
Sep  2 08:46:05 owner kernel: [   12.575564] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
Sep  2 08:46:05 owner kernel: [   12.575567] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
Sep  2 08:46:05 owner kernel: [   12.575817] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
Sep  2 08:46:05 owner kernel: [   12.575820] PCI: Bridge: 0000:00:01.0
Sep  2 08:46:05 owner kernel: [   12.575822]   IO window: a000-afff
Sep  2 08:46:05 owner kernel: [   12.575826]   MEM window: e2100000-e21fffff
Sep  2 08:46:05 owner kernel: [   12.575830]   PREFETCH window: e8000000-efffffff
Sep  2 08:46:05 owner kernel: [   12.575834] PCI: Bus 2, cardbus bridge: 0000:00:06.0
Sep  2 08:46:05 owner kernel: [   12.575836]   IO window: 00002400-000024ff
Sep  2 08:46:05 owner kernel: [   12.575840]   IO window: 00002800-000028ff
Sep  2 08:46:05 owner kernel: [   12.575843]   PREFETCH window: 60000000-63ffffff
Sep  2 08:46:05 owner kernel: [   12.575847]   MEM window: 64000000-67ffffff
Sep  2 08:46:05 owner kernel: [   12.575864] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
Sep  2 08:46:05 owner kernel: [   12.575875] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 08:46:05 owner kernel: [   12.575915] NET: Registered protocol family 2
Sep  2 08:46:05 owner kernel: [   12.611081] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  2 08:46:05 owner kernel: [   12.611302] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  2 08:46:05 owner kernel: [   12.612639] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  2 08:46:05 owner kernel: [   12.613323] TCP: Hash tables configured (established 131072 bind 65536)
Sep  2 08:46:05 owner kernel: [   12.613327] TCP reno registered
Sep  2 08:46:05 owner kernel: [   12.623120] checking if image is initramfs... it is
Sep  2 08:46:05 owner kernel: [   13.238904] Freeing initrd memory: 6782k freed
Sep  2 08:46:05 owner kernel: [   13.239088] Simple Boot Flag at 0x38 set to 0x1
Sep  2 08:46:05 owner kernel: [   13.239344] audit: initializing netlink socket (disabled)
Sep  2 08:46:05 owner kernel: [   13.239357] audit(1188740739.368:1): initialized
Sep  2 08:46:05 owner kernel: [   13.239418] highmem bounce pool size: 64 pages
Sep  2 08:46:05 owner kernel: [   13.239499] VFS: Disk quotas dquot_6.5.1
Sep  2 08:46:05 owner kernel: [   13.239522] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  2 08:46:05 owner kernel: [   13.239581] io scheduler noop registered
Sep  2 08:46:05 owner kernel: [   13.239583] io scheduler anticipatory registered
Sep  2 08:46:05 owner kernel: [   13.239585] io scheduler deadline registered
Sep  2 08:46:05 owner kernel: [   13.239599] io scheduler cfq registered (default)
Sep  2 08:46:05 owner kernel: [   13.665715] isapnp: Scanning for PnP cards...
Sep  2 08:46:05 owner kernel: [   14.018590] isapnp: No Plug & Play device found
Sep  2 08:46:05 owner kernel: [   14.057092] Real Time Clock Driver v1.12ac
Sep  2 08:46:05 owner kernel: [   14.057130] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  2 08:46:05 owner kernel: [   14.058075] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 08:46:05 owner kernel: [   14.058083] ACPI: PCI interrupt for device 0000:00:02.6 disabled
Sep  2 08:46:05 owner kernel: [   14.058145] mice: PS/2 mouse device common for all mice
Sep  2 08:46:05 owner kernel: [   14.058583] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  2 08:46:05 owner kernel: [   14.058828] input: Macintosh mouse button emulation as /class/input/input0
Sep  2 08:46:05 owner kernel: [   14.058864] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep  2 08:46:05 owner kernel: [   14.058868] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep  2 08:46:05 owner kernel: [   14.059073] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  2 08:46:05 owner kernel: [   14.061623] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  2 08:46:05 owner kernel: [   14.061629] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  2 08:46:05 owner kernel: [   14.061782] EISA: Probing bus 0 at eisa.0
Sep  2 08:46:05 owner kernel: [   14.061793] Cannot allocate resource for EISA slot 1
Sep  2 08:46:05 owner kernel: [   14.061795] Cannot allocate resource for EISA slot 2
Sep  2 08:46:05 owner kernel: [   14.061814] Cannot allocate resource for EISA slot 8
Sep  2 08:46:05 owner kernel: [   14.061815] EISA: Detected 0 cards.
Sep  2 08:46:05 owner kernel: [   14.091860] TCP cubic registered
Sep  2 08:46:05 owner kernel: [   14.091870] NET: Registered protocol family 1
Sep  2 08:46:05 owner kernel: [   14.091895] Using IPI No-Shortcut mode
Sep  2 08:46:05 owner kernel: [   14.091959] ACPI: (supports S0 S3 S4 S5)
Sep  2 08:46:05 owner kernel: [   14.091992]   Magic number: 7:780:785
Sep  2 08:46:05 owner kernel: [   14.092089]   hash matches device ptyq7
Sep  2 08:46:05 owner kernel: [   14.092443] Freeing unused kernel memory: 328k freed
Sep  2 08:46:05 owner kernel: [   14.092812] Time: tsc clocksource has been installed.
Sep  2 08:46:05 owner kernel: [   14.116858] input: AT Translated Set 2 keyboard as /class/input/input1
Sep  2 08:46:05 owner kernel: [   15.368316] Capability LSM initialized
Sep  2 08:46:05 owner kernel: [   15.416335] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 08:46:05 owner kernel: [   15.420838] ACPI: Thermal Zone [THRM] (48 C)
Sep  2 08:46:05 owner kernel: [   16.083214] SIS5513: IDE controller at PCI slot 0000:00:02.5
Sep  2 08:46:05 owner kernel: [   16.083232] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 18
Sep  2 08:46:05 owner kernel: [   16.083242] SIS5513: chipset revision 0
Sep  2 08:46:05 owner kernel: [   16.083244] SIS5513: not 100%% native mode: will probe irqs later
Sep  2 08:46:05 owner kernel: [   16.083257] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
Sep  2 08:46:05 owner kernel: [   16.083269]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
Sep  2 08:46:05 owner kernel: [   16.083281]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
Sep  2 08:46:05 owner kernel: [   16.119684] usbcore: registered new interface driver usbfs
Sep  2 08:46:05 owner kernel: [   16.119705] usbcore: registered new interface driver hub
Sep  2 08:46:05 owner kernel: [   16.119726] usbcore: registered new device driver usb
Sep  2 08:46:05 owner kernel: [   16.155550] sis900.c: v1.08.10 Apr. 2 2006
Sep  2 08:46:05 owner kernel: [    3.896000] Time: acpi_pm clocksource has been installed.
Sep  2 08:46:05 owner kernel: [    3.976000] hda: TOSHIBA MK6025GAS, ATA DISK drive
Sep  2 08:46:05 owner kernel: [    4.648000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep  2 08:46:05 owner kernel: [    5.444000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
Sep  2 08:46:05 owner kernel: [    6.116000] ide1 at 0x170-0x177,0x376 on irq 15
Sep  2 08:46:05 owner kernel: [    6.124000] SCSI subsystem initialized
Sep  2 08:46:05 owner kernel: [    6.136000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 19
Sep  2 08:46:05 owner kernel: [    6.136000] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep  2 08:46:05 owner kernel: [    6.136000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Sep  2 08:46:05 owner kernel: [    6.136000] ohci_hcd 0000:00:03.0: irq 19, io mem 0xe2002000
Sep  2 08:46:05 owner kernel: [    6.148000] hda: max request size: 128KiB
Sep  2 08:46:05 owner kernel: [    6.160000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
Sep  2 08:46:05 owner kernel: [    6.160000] hda: cache flushes supported
Sep  2 08:46:05 owner kernel: [    6.160000]  hda:<6>usb usb1: configuration #1 chosen from 1 choice
Sep  2 08:46:05 owner kernel: [    6.192000] hub 1-0:1.0: USB hub found
Sep  2 08:46:05 owner kernel: [    6.192000] hub 1-0:1.0: 3 ports detected
Sep  2 08:46:05 owner kernel: [    6.224000]  hda1 hda2 < hda5 >
Sep  2 08:46:05 owner kernel: [    6.256000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep  2 08:46:05 owner kernel: [    6.256000] Uniform CD-ROM driver Revision: 3.20
Sep  2 08:46:05 owner kernel: [    6.296000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 20
Sep  2 08:46:05 owner kernel: [    6.296000] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep  2 08:46:05 owner kernel: [    6.296000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Sep  2 08:46:05 owner kernel: [    6.296000] ohci_hcd 0000:00:03.1: irq 20, io mem 0xe2003000
Sep  2 08:46:05 owner kernel: [    6.352000] usb usb2: configuration #1 chosen from 1 choice
Sep  2 08:46:05 owner kernel: [    6.352000] hub 2-0:1.0: USB hub found
Sep  2 08:46:05 owner kernel: [    6.352000] hub 2-0:1.0: 3 ports detected
Sep  2 08:46:06 owner kernel: [    6.456000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 21
Sep  2 08:46:06 owner kernel: [    6.456000] ehci_hcd 0000:00:03.2: EHCI Host Controller
Sep  2 08:46:06 owner kernel: [    6.456000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Sep  2 08:46:06 owner kernel: [    6.456000] ehci_hcd 0000:00:03.2: irq 21, io mem 0xe2004000
Sep  2 08:46:06 owner kernel: [    6.456000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  2 08:46:06 owner kernel: [    6.456000] usb usb3: configuration #1 chosen from 1 choice
Sep  2 08:46:06 owner kernel: [    6.456000] hub 3-0:1.0: USB hub found
Sep  2 08:46:06 owner kernel: [    6.456000] hub 3-0:1.0: 6 ports detected
Sep  2 08:46:06 owner kernel: [    6.560000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 08:46:06 owner kernel: [    6.564000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Sep  2 08:46:06 owner kernel: [    6.568000] 0000:00:04.0: Using transceiver found at address 13 as default
Sep  2 08:46:06 owner kernel: [    6.568000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 16, 00:c0:9f:c1:44:ea.
Sep  2 08:46:06 owner kernel: [    6.612000] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  2 08:46:06 owner kernel: [    6.612000] EXT3-fs: write access will be enabled during recovery.
Sep  2 08:46:06 owner kernel: [    7.144000] usb 1-2: new low speed USB device using ohci_hcd and address 3
Sep  2 08:46:06 owner kernel: [    7.352000] usb 1-2: configuration #1 chosen from 1 choice
Sep  2 08:46:06 owner kernel: [    7.368000] usbcore: registered new interface driver hiddev
Sep  2 08:46:06 owner kernel: [    7.380000] input: HID 1241:1166 as /class/input/input2
Sep  2 08:46:06 owner kernel: [    7.380000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:03.0-2
Sep  2 08:46:06 owner kernel: [    7.380000] usbcore: registered new interface driver usbhid
Sep  2 08:46:06 owner kernel: [    7.380000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Sep  2 08:46:06 owner kernel: [    7.800000] kjournald starting.  Commit interval 5 seconds
Sep  2 08:46:06 owner kernel: [    7.800000] EXT3-fs: recovery complete.
Sep  2 08:46:06 owner kernel: [    7.824000] EXT3-fs: mounted filesystem with ordered data mode.
Sep  2 08:46:06 owner kernel: [   22.060000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
Sep  2 08:46:06 owner kernel: [   22.216000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  2 08:46:06 owner kernel: [   22.276000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  2 08:46:06 owner kernel: [   22.520000] Linux agpgart interface v0.102 (c) Dave Jones
Sep  2 08:46:06 owner kernel: [   22.536000] agpgart: Detected AGP bridge 0
Sep  2 08:46:06 owner kernel: [   22.536000] agpgart: AGP aperture is 32M @ 0xe0000000
Sep  2 08:46:06 owner kernel: [   22.568000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
Sep  2 08:46:06 owner kernel: [   22.568000] Yenta: Using CSCINT to route CSC interrupts to PCI
Sep  2 08:46:06 owner kernel: [   22.568000] Yenta: Routing CardBus interrupts to PCI
Sep  2 08:46:06 owner kernel: [   22.568000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
Sep  2 08:46:06 owner kernel: [   22.688000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep  2 08:46:06 owner kernel: [   22.688000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep  2 08:46:06 owner kernel: [   22.792000] input: PC Speaker as /class/input/input3
Sep  2 08:46:06 owner kernel: [   22.800000] Yenta: ISA IRQ mask 0x06f8, PCI irq 16
Sep  2 08:46:06 owner kernel: [   22.800000] Socket status: 30000006
Sep  2 08:46:06 owner kernel: [   22.876000] bcm43xx driver
Sep  2 08:46:06 owner kernel: [   22.876000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  2 08:46:06 owner kernel: [   23.316000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 08:46:06 owner kernel: [   23.472000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Sep  2 08:46:06 owner kernel: [   23.480000] cs: IO port probe 0x100-0x3af: clean.
Sep  2 08:46:06 owner kernel: [   23.480000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
Sep  2 08:46:06 owner kernel: [   23.484000] cs: IO port probe 0x820-0x8ff: clean.
Sep  2 08:46:06 owner kernel: [   23.484000] cs: IO port probe 0xc00-0xcf7: clean.
Sep  2 08:46:06 owner kernel: [   23.484000] cs: IO port probe 0xa00-0xaff: clean.
Sep  2 08:46:06 owner kernel: [   23.508000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Sep  2 08:46:06 owner kernel: [   24.136000] intel8x0_measure_ac97_clock: measured 55455 usecs
Sep  2 08:46:06 owner kernel: [   24.136000] intel8x0: clocking to 48000
Sep  2 08:46:06 owner kernel: [   24.348000] lp: driver loaded but no devices found
Sep  2 08:46:06 owner kernel: [   24.424000] Adding 2441840k swap on /dev/disk/by-uuid/ed70067a-bce9-4fb6-907f-2c4c81db4df4.  Priority:-1 extents:1 across:2441840k
Sep  2 08:46:06 owner kernel: [   24.556000] EXT3 FS on hda1, internal journal
Sep  2 08:46:06 owner kernel: [   25.260000] ACPI: Battery Slot [BAT1] (battery present)
Sep  2 08:46:06 owner kernel: [   25.300000] ACPI: AC Adapter [ACAD] (on-line)
Sep  2 08:46:06 owner kernel: [   25.344000] No dock devices found.
Sep  2 08:46:06 owner kernel: [   25.420000] Using specific hotkey driver
Sep  2 08:46:06 owner kernel: [   25.520000] input: Power Button (FF) as /class/input/input5
Sep  2 08:46:06 owner kernel: [   25.528000] ACPI: Power Button (FF) [PWRF]
Sep  2 08:46:06 owner kernel: [   25.564000] input: Lid Switch as /class/input/input6
Sep  2 08:46:06 owner kernel: [   25.568000] ACPI: Lid Switch [LID]
Sep  2 08:46:06 owner kernel: [   25.608000] input: Power Button (CM) as /class/input/input7
Sep  2 08:46:06 owner kernel: [   25.616000] ACPI: Power Button (CM) [PWRB]
Sep  2 08:46:06 owner kernel: [   25.652000] input: Sleep Button (CM) as /class/input/input8
Sep  2 08:46:06 owner kernel: [   25.656000] ACPI: Sleep Button (CM) [SLPB]
Sep  2 08:46:06 owner kernel: [   25.752000] pcc_acpi: loading...
Sep  2 08:46:06 owner kernel: [   26.012000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
Sep  2 08:46:06 owner kernel: [   26.012000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
Sep  2 08:46:06 owner kernel: [   26.012000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
Sep  2 08:46:06 owner kernel: [   26.012000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
Sep  2 08:46:08 owner kernel: [   28.984000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:46:08 owner kernel: [   29.000000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:46:08 owner kernel: [   29.032000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:46:08 owner dhcdbd: Started up.
Sep  2 08:46:08 owner kernel: [   29.244000] eth1: Media Link Off
Sep  2 08:46:11 owner kernel: [   31.768000] ppdev: user-space parallel port driver
Sep  2 08:46:12 owner hpiod: 1.7.3 accepting connections at 2208... 
Sep  2 08:46:13 owner kernel: [   33.716000] apm: BIOS not found.
Sep  2 08:46:13 owner kernel: [   33.960000] Bluetooth: Core ver 2.11
Sep  2 08:46:13 owner kernel: [   33.960000] NET: Registered protocol family 31
Sep  2 08:46:13 owner kernel: [   33.960000] Bluetooth: HCI device and connection manager initialized
Sep  2 08:46:13 owner kernel: [   33.960000] Bluetooth: HCI socket layer initialized
Sep  2 08:46:13 owner kernel: [   34.020000] Bluetooth: L2CAP ver 2.8
Sep  2 08:46:13 owner kernel: [   34.020000] Bluetooth: L2CAP socket layer initialized
Sep  2 08:46:13 owner kernel: [   34.052000] Bluetooth: RFCOMM socket layer initialized
Sep  2 08:46:13 owner kernel: [   34.052000] Bluetooth: RFCOMM TTY layer initialized
Sep  2 08:46:13 owner kernel: [   34.052000] Bluetooth: RFCOMM ver 1.8
Sep  2 08:46:24 owner gconfd (owner-4942): starting (version 2.18.0.1), pid 4942 user 'owner'
Sep  2 08:46:24 owner gconfd (owner-4942): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 08:46:24 owner gconfd (owner-4942): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  2 08:46:24 owner gconfd (owner-4942): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 08:46:24 owner gconfd (owner-4942): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 08:46:24 owner gconfd (owner-4942): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 08:46:26 owner kernel: [   47.252000] NET: Registered protocol family 10
Sep  2 08:46:26 owner kernel: [   47.252000] lo: Disabled Privacy Extensions
Sep  2 08:46:26 owner kernel: [   47.252000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep  2 08:46:33 owner gconfd (owner-4942): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 0
Sep  2 08:46:36 owner kernel: [   56.584000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:46:46 owner kernel: [   66.816000] c01727b1
Sep  2 08:46:46 owner kernel: [   66.816000] Modules linked in: ipv6 binfmt_misc rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_ondemand cpufreq_userspace freq_table cpufreq_conservative cpufreq_powersave pcc_acpi tc1100_wmi dev_acpi sony_acpi container button video dock sbs i2c_ec ac asus_acpi battery backlight parport_pc lp parport joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss pcmcia snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse bcm43xx ieee80211softmac pcspkr sis_agp snd soundcore snd_page_alloc ieee80211 ieee80211_crypt serio_raw yenta_socket rsrc_nonstatic pcmcia_core amd64_agp agpgart k8temp shpchp pci_hotplug i2c_sis96x i2c_core evdev tsdev usbhid hid ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod sis900 mii ehci_hcd ohci_hcd usbcore sis5513 generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Sep  2 08:47:00 owner kernel: [   66.816000]  <3>bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Sep  2 08:47:06 owner kernel: [   86.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:47:36 owner kernel: [  116.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:48:06 owner kernel: [  146.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:48:36 owner kernel: [  176.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:49:06 owner kernel: [  206.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:49:36 owner kernel: [  236.564000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:50:06 owner kernel: [  266.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:50:36 owner kernel: [  296.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:51:06 owner kernel: [  326.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:51:36 owner kernel: [  356.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:52:06 owner kernel: [  386.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:52:19 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  2 08:52:36 owner kernel: [  416.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:53:06 owner kernel: [  446.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:53:36 owner kernel: [  476.556000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:54:06 owner kernel: [  506.552000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:54:36 owner kernel: [  536.552000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:55:07 owner kernel: [  566.644000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 08:55:08 owner gconfd (owner-4942): Exiting
Sep  2 08:55:26 owner exiting on signal 15
Sep  2 13:43:42 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  2 13:43:42 owner kernel: Inspecting /boot/System.map-2.6.20-15-generic
Sep  2 13:43:42 owner kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Sep  2 13:43:42 owner kernel: Symbols match kernel version 2.6.20.
Sep  2 13:43:42 owner kernel: No module symbols loaded - kernel modules not enabled. 
Sep  2 13:43:42 owner kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Sep  2 13:43:42 owner kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  2 13:43:42 owner kernel: [    0.000000] sanitize start
Sep  2 13:43:42 owner kernel: [    0.000000] sanitize end
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000047df0000 end: 0000000047ef0000 type: 1
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000047ef0000 size: 000000000000a000 end: 0000000047efa000 type: 3
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000047efa000 size: 0000000000006000 end: 0000000047f00000 type: 4
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 0000000047f00000 size: 0000000008100000 end: 0000000050000000 type: 2
Sep  2 13:43:42 owner kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000047ef0000 (usable)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000047ef0000 - 0000000047efa000 (ACPI data)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000047efa000 - 0000000047f00000 (ACPI NVS)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 0000000047f00000 - 0000000050000000 (reserved)
Sep  2 13:43:42 owner kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Sep  2 13:43:42 owner kernel: [    0.000000] 254MB HIGHMEM available.
Sep  2 13:43:42 owner kernel: [    0.000000] 896MB LOWMEM available.
Sep  2 13:43:42 owner kernel: [    0.000000] found SMP MP-table at 000f7fd0
Sep  2 13:43:42 owner kernel: [    0.000000] Zone PFN ranges:
Sep  2 13:43:42 owner kernel: [    0.000000]   DMA             0 ->     4096
Sep  2 13:43:42 owner kernel: [    0.000000]   Normal       4096 ->   229376
Sep  2 13:43:42 owner kernel: [    0.000000]   HighMem    229376 ->   294640
Sep  2 13:43:42 owner kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  2 13:43:42 owner kernel: [    0.000000]     0:        0 ->   294640
Sep  2 13:43:42 owner kernel: [    0.000000] DMI present.
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  2 13:43:42 owner kernel: [    0.000000] Processor #0 15:12 APIC version 16
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  2 13:43:42 owner kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Sep  2 13:43:42 owner kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Sep  2 13:43:42 owner kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  2 13:43:42 owner kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  2 13:43:42 owner kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aff00000)
Sep  2 13:43:42 owner kernel: [    0.000000] Detected 1800.153 MHz processor.
Sep  2 13:43:42 owner kernel: [   12.440237] Built 1 zonelists.  Total pages: 292339
Sep  2 13:43:42 owner kernel: [   12.440241] Kernel command line: root=UUID=36f4f755-b608-49ce-b11a-e96f60601f95 ro quiet splash
Sep  2 13:43:42 owner kernel: [   12.440387] Enabling fast FPU save and restore... done.
Sep  2 13:43:42 owner kernel: [   12.440390] Enabling unmasked SIMD FPU exception support... done.
Sep  2 13:43:42 owner kernel: [   12.440397] Initializing CPU#0
Sep  2 13:43:42 owner kernel: [   12.440440] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  2 13:43:42 owner kernel: [   12.441200] Console: colour VGA+ 80x25
Sep  2 13:43:42 owner kernel: [   12.441783] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  2 13:43:42 owner kernel: [   12.442777] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  2 13:43:42 owner kernel: [   12.473238] Memory: 1157148k/1178560k available (1992k kernel code, 20492k reserved, 893k data, 328k init, 261056k highmem)
Sep  2 13:43:42 owner kernel: [   12.473249] virtual kernel memory layout:
Sep  2 13:43:42 owner kernel: [   12.473250]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep  2 13:43:42 owner kernel: [   12.473252]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  2 13:43:42 owner kernel: [   12.473253]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  2 13:43:42 owner kernel: [   12.473254]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  2 13:43:42 owner kernel: [   12.473255]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Sep  2 13:43:42 owner kernel: [   12.473257]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Sep  2 13:43:42 owner kernel: [   12.473258]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Sep  2 13:43:42 owner kernel: [   12.473261] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  2 13:43:42 owner kernel: [   12.552279] Calibrating delay using timer specific routine.. 3602.04 BogoMIPS (lpj=7204080)
Sep  2 13:43:42 owner kernel: [   12.552326] Security Framework v1.0.0 initialized
Sep  2 13:43:42 owner kernel: [   12.552335] SELinux:  Disabled at boot.
Sep  2 13:43:42 owner kernel: [   12.552351] Mount-cache hash table entries: 512
Sep  2 13:43:42 owner kernel: [   12.552511] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  2 13:43:42 owner kernel: [   12.552514] CPU: L2 Cache: 128K (64 bytes/line)
Sep  2 13:43:42 owner kernel: [   12.552528] Compat vDSO mapped to ffffe000.
Sep  2 13:43:42 owner kernel: [   12.552532] Remapping vsyscall page to ffffe000
Sep  2 13:43:42 owner kernel: [   12.552543] Checking 'hlt' instruction... OK.
Sep  2 13:43:42 owner kernel: [   12.568410] SMP alternatives: switching to UP code
Sep  2 13:43:42 owner kernel: [   12.568718] Freeing SMP alternatives: 11k freed
Sep  2 13:43:42 owner kernel: [   12.568979] Early unpacking initramfs... done
Sep  2 13:43:42 owner kernel: [   12.881262] ACPI: Core revision 20060707
Sep  2 13:43:42 owner kernel: [   12.881478] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep  2 13:43:42 owner kernel: [   12.885085] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
Sep  2 13:43:42 owner kernel: [   12.885105] Total of 1 processors activated (3602.04 BogoMIPS).
Sep  2 13:43:42 owner kernel: [   12.885258] ENABLING IO-APIC IRQs
Sep  2 13:43:42 owner kernel: [   12.885451] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  2 13:43:42 owner kernel: [   13.031611] Brought up 1 CPUs
Sep  2 13:43:42 owner kernel: [   13.031833] Booting paravirtualized kernel on bare hardware
Sep  2 13:43:42 owner kernel: [   13.031912] Time: 18:43:15  Date: 08/02/107
Sep  2 13:43:42 owner kernel: [   13.031947] NET: Registered protocol family 16
Sep  2 13:43:42 owner kernel: [   13.032050] EISA bus registered
Sep  2 13:43:42 owner kernel: [   13.032054] ACPI: bus type pci registered
Sep  2 13:43:42 owner kernel: [   13.032201] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
Sep  2 13:43:42 owner kernel: [   13.032203] PCI: Using configuration type 1
Sep  2 13:43:42 owner kernel: [   13.032205] Setting up standard PCI resources
Sep  2 13:43:42 owner kernel: [   13.034595] ACPI: Interpreter enabled
Sep  2 13:43:42 owner kernel: [   13.034599] ACPI: Using IOAPIC for interrupt routing
Sep  2 13:43:42 owner kernel: [   13.034938] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  2 13:43:42 owner kernel: [   13.035992] Enabling SiS 96x SMBus.
Sep  2 13:43:42 owner kernel: [   13.057919] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058098] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058273] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058442] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058632] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
Sep  2 13:43:42 owner kernel: [   13.058802] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
Sep  2 13:43:42 owner kernel: [   13.058979] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Sep  2 13:43:42 owner kernel: [   13.059147] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
Sep  2 13:43:42 owner kernel: [   13.059434] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  2 13:43:42 owner kernel: [   13.059446] pnp: PnP ACPI init
Sep  2 13:43:42 owner kernel: [   13.061089] pnp: PnP ACPI: found 8 devices
Sep  2 13:43:42 owner kernel: [   13.061095] PnPBIOS: Disabled by ACPI PNP
Sep  2 13:43:42 owner kernel: [   13.061151] PCI: Using ACPI for IRQ routing
Sep  2 13:43:42 owner kernel: [   13.061154] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  2 13:43:42 owner kernel: [   13.063273] NET: Registered protocol family 8
Sep  2 13:43:42 owner kernel: [   13.063275] NET: Registered protocol family 20
Sep  2 13:43:42 owner kernel: [   13.063454] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
Sep  2 13:43:42 owner kernel: [   13.063458] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
Sep  2 13:43:42 owner kernel: [   13.063460] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
Sep  2 13:43:42 owner kernel: [   13.063463] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
Sep  2 13:43:42 owner kernel: [   13.063730] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
Sep  2 13:43:42 owner kernel: [   13.063734] PCI: Bridge: 0000:00:01.0
Sep  2 13:43:42 owner kernel: [   13.063737]   IO window: a000-afff
Sep  2 13:43:42 owner kernel: [   13.063741]   MEM window: e2100000-e21fffff
Sep  2 13:43:42 owner kernel: [   13.063744]   PREFETCH window: e8000000-efffffff
Sep  2 13:43:42 owner kernel: [   13.063749] PCI: Bus 2, cardbus bridge: 0000:00:06.0
Sep  2 13:43:42 owner kernel: [   13.063751]   IO window: 00002400-000024ff
Sep  2 13:43:42 owner kernel: [   13.063754]   IO window: 00002800-000028ff
Sep  2 13:43:42 owner kernel: [   13.063758]   PREFETCH window: 60000000-63ffffff
Sep  2 13:43:42 owner kernel: [   13.063762]   MEM window: 64000000-67ffffff
Sep  2 13:43:42 owner kernel: [   13.063778] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
Sep  2 13:43:42 owner kernel: [   13.063789] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 13:43:42 owner kernel: [   13.063830] NET: Registered protocol family 2
Sep  2 13:43:42 owner kernel: [   13.099565] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  2 13:43:42 owner kernel: [   13.099785] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  2 13:43:42 owner kernel: [   13.101122] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  2 13:43:42 owner kernel: [   13.101804] TCP: Hash tables configured (established 131072 bind 65536)
Sep  2 13:43:42 owner kernel: [   13.101809] TCP reno registered
Sep  2 13:43:42 owner kernel: [   13.111604] checking if image is initramfs... it is
Sep  2 13:43:42 owner kernel: [   13.727384] Freeing initrd memory: 6782k freed
Sep  2 13:43:42 owner kernel: [   13.727568] Simple Boot Flag at 0x38 set to 0x1
Sep  2 13:43:42 owner kernel: [   13.727826] audit: initializing netlink socket (disabled)
Sep  2 13:43:42 owner kernel: [   13.727840] audit(1188758595.368:1): initialized
Sep  2 13:43:42 owner kernel: [   13.727902] highmem bounce pool size: 64 pages
Sep  2 13:43:42 owner kernel: [   13.727983] VFS: Disk quotas dquot_6.5.1
Sep  2 13:43:42 owner kernel: [   13.728006] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  2 13:43:42 owner kernel: [   13.728065] io scheduler noop registered
Sep  2 13:43:42 owner kernel: [   13.728067] io scheduler anticipatory registered
Sep  2 13:43:42 owner kernel: [   13.728069] io scheduler deadline registered
Sep  2 13:43:42 owner kernel: [   13.728082] io scheduler cfq registered (default)
Sep  2 13:43:42 owner kernel: [   14.154199] isapnp: Scanning for PnP cards...
Sep  2 13:43:42 owner kernel: [   14.507074] isapnp: No Plug & Play device found
Sep  2 13:43:42 owner kernel: [   14.545808] Real Time Clock Driver v1.12ac
Sep  2 13:43:42 owner kernel: [   14.545846] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  2 13:43:42 owner kernel: [   14.546785] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 13:43:42 owner kernel: [   14.546793] ACPI: PCI interrupt for device 0000:00:02.6 disabled
Sep  2 13:43:42 owner kernel: [   14.546856] mice: PS/2 mouse device common for all mice
Sep  2 13:43:42 owner kernel: [   14.547293] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  2 13:43:42 owner kernel: [   14.547537] input: Macintosh mouse button emulation as /class/input/input0
Sep  2 13:43:42 owner kernel: [   14.547573] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep  2 13:43:42 owner kernel: [   14.547577] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep  2 13:43:42 owner kernel: [   14.547781] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  2 13:43:42 owner kernel: [   14.550382] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  2 13:43:42 owner kernel: [   14.550389] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  2 13:43:42 owner kernel: [   14.550544] EISA: Probing bus 0 at eisa.0
Sep  2 13:43:42 owner kernel: [   14.550555] Cannot allocate resource for EISA slot 1
Sep  2 13:43:42 owner kernel: [   14.550557] Cannot allocate resource for EISA slot 2
Sep  2 13:43:42 owner kernel: [   14.550575] Cannot allocate resource for EISA slot 8
Sep  2 13:43:42 owner kernel: [   14.550577] EISA: Detected 0 cards.
Sep  2 13:43:42 owner kernel: [   14.580622] TCP cubic registered
Sep  2 13:43:42 owner kernel: [   14.580632] NET: Registered protocol family 1
Sep  2 13:43:42 owner kernel: [   14.580656] Using IPI No-Shortcut mode
Sep  2 13:43:42 owner kernel: [   14.580721] ACPI: (supports S0 S3 S4 S5)
Sep  2 13:43:42 owner kernel: [   14.580755]   Magic number: 7:760:745
Sep  2 13:43:42 owner kernel: [   14.581205] Freeing unused kernel memory: 328k freed
Sep  2 13:43:42 owner kernel: [   14.581298] Time: tsc clocksource has been installed.
Sep  2 13:43:42 owner kernel: [   14.597763] input: AT Translated Set 2 keyboard as /class/input/input1
Sep  2 13:43:42 owner kernel: [   15.852860] Capability LSM initialized
Sep  2 13:43:42 owner kernel: [   15.900826] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 13:43:42 owner kernel: [   15.905568] ACPI: Thermal Zone [THRM] (32 C)
Sep  2 13:43:42 owner kernel: [   16.607765] usbcore: registered new interface driver usbfs
Sep  2 13:43:42 owner kernel: [   16.607787] usbcore: registered new interface driver hub
Sep  2 13:43:42 owner kernel: [   16.607806] usbcore: registered new device driver usb
Sep  2 13:43:42 owner kernel: [   16.608629] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 18
Sep  2 13:43:42 owner kernel: [   16.608641] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep  2 13:43:42 owner kernel: [   16.608777] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Sep  2 13:43:42 owner kernel: [   16.608797] ohci_hcd 0000:00:03.0: irq 18, io mem 0xe2002000
Sep  2 13:43:42 owner kernel: [   16.670400] usb usb1: configuration #1 chosen from 1 choice
Sep  2 13:43:42 owner kernel: [   16.670424] hub 1-0:1.0: USB hub found
Sep  2 13:43:42 owner kernel: [   16.670434] hub 1-0:1.0: 3 ports detected
Sep  2 13:43:42 owner kernel: [   16.707561] sis900.c: v1.08.10 Apr. 2 2006
Sep  2 13:43:42 owner kernel: [   16.774221] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 19
Sep  2 13:43:42 owner kernel: [   16.774241] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep  2 13:43:42 owner kernel: [   16.774262] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Sep  2 13:43:42 owner kernel: [   16.774282] ohci_hcd 0000:00:03.1: irq 19, io mem 0xe2003000
Sep  2 13:43:42 owner kernel: [    3.900000] Time: acpi_pm clocksource has been installed.
Sep  2 13:43:42 owner kernel: [    3.900000] usb usb2: configuration #1 chosen from 1 choice
Sep  2 13:43:42 owner kernel: [    3.900000] hub 2-0:1.0: USB hub found
Sep  2 13:43:42 owner kernel: [    3.900000] hub 2-0:1.0: 3 ports detected
Sep  2 13:43:42 owner kernel: [    4.004000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 20
Sep  2 13:43:42 owner kernel: [    4.004000] ehci_hcd 0000:00:03.2: EHCI Host Controller
Sep  2 13:43:42 owner kernel: [    4.004000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Sep  2 13:43:42 owner kernel: [    4.004000] ehci_hcd 0000:00:03.2: irq 20, io mem 0xe2004000
Sep  2 13:43:42 owner kernel: [    4.004000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  2 13:43:42 owner kernel: [    4.004000] usb usb3: configuration #1 chosen from 1 choice
Sep  2 13:43:42 owner kernel: [    4.004000] hub 3-0:1.0: USB hub found
Sep  2 13:43:42 owner kernel: [    4.004000] hub 3-0:1.0: 6 ports detected
Sep  2 13:43:42 owner kernel: [    4.108000] SIS5513: IDE controller at PCI slot 0000:00:02.5
Sep  2 13:43:42 owner kernel: [    4.108000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 21
Sep  2 13:43:42 owner kernel: [    4.108000] SIS5513: chipset revision 0
Sep  2 13:43:42 owner kernel: [    4.108000] SIS5513: not 100%% native mode: will probe irqs later
Sep  2 13:43:42 owner kernel: [    4.108000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
Sep  2 13:43:42 owner kernel: [    4.108000]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
Sep  2 13:43:42 owner kernel: [    4.108000]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
Sep  2 13:43:42 owner kernel: [    4.396000] hda: TOSHIBA MK6025GAS, ATA DISK drive
Sep  2 13:43:42 owner kernel: [    4.692000] usb 1-2: new low speed USB device using ohci_hcd and address 3
Sep  2 13:43:42 owner kernel: [    4.900000] usb 1-2: configuration #1 chosen from 1 choice
Sep  2 13:43:42 owner kernel: [    4.916000] usbcore: registered new interface driver hiddev
Sep  2 13:43:42 owner kernel: [    4.928000] input: HID 1241:1166 as /class/input/input2
Sep  2 13:43:42 owner kernel: [    4.928000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:03.0-2
Sep  2 13:43:42 owner kernel: [    4.928000] usbcore: registered new interface driver usbhid
Sep  2 13:43:42 owner kernel: [    4.928000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Sep  2 13:43:42 owner kernel: [    5.068000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep  2 13:43:42 owner kernel: [    5.852000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
Sep  2 13:43:42 owner kernel: [    6.524000] ide1 at 0x170-0x177,0x376 on irq 15
Sep  2 13:43:42 owner kernel: [    6.528000] SCSI subsystem initialized
Sep  2 13:43:42 owner kernel: [    6.540000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 13:43:42 owner kernel: [    6.544000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Sep  2 13:43:42 owner kernel: [    6.552000] 0000:00:04.0: Using transceiver found at address 13 as default
Sep  2 13:43:42 owner kernel: [    6.552000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 16, 00:c0:9f:c1:44:ea.
Sep  2 13:43:42 owner kernel: [    6.564000] hda: max request size: 128KiB
Sep  2 13:43:42 owner kernel: [    6.572000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
Sep  2 13:43:42 owner kernel: [    6.572000] hda: cache flushes supported
Sep  2 13:43:42 owner kernel: [    6.572000]  hda: hda1 hda2 < hda5 >
Sep  2 13:43:42 owner kernel: [    6.664000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep  2 13:43:42 owner kernel: [    6.664000] Uniform CD-ROM driver Revision: 3.20
Sep  2 13:43:42 owner kernel: [    6.984000] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  2 13:43:42 owner kernel: [    6.984000] EXT3-fs: write access will be enabled during recovery.
Sep  2 13:43:42 owner kernel: [    9.252000] kjournald starting.  Commit interval 5 seconds
Sep  2 13:43:42 owner kernel: [    9.252000] EXT3-fs: recovery complete.
Sep  2 13:43:42 owner kernel: [    9.252000] EXT3-fs: mounted filesystem with ordered data mode.
Sep  2 13:43:42 owner kernel: [   23.344000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  2 13:43:42 owner kernel: [   23.348000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  2 13:43:42 owner kernel: [   23.396000] Linux agpgart interface v0.102 (c) Dave Jones
Sep  2 13:43:42 owner kernel: [   23.404000] agpgart: Detected AGP bridge 0
Sep  2 13:43:42 owner kernel: [   23.408000] agpgart: AGP aperture is 32M @ 0xe0000000
Sep  2 13:43:42 owner kernel: [   23.560000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
Sep  2 13:43:42 owner kernel: [   23.560000] Yenta: Using CSCINT to route CSC interrupts to PCI
Sep  2 13:43:42 owner kernel: [   23.560000] Yenta: Routing CardBus interrupts to PCI
Sep  2 13:43:42 owner kernel: [   23.560000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
Sep  2 13:43:42 owner kernel: [   23.564000] input: PC Speaker as /class/input/input3
Sep  2 13:43:42 owner kernel: [   23.600000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep  2 13:43:42 owner kernel: [   23.600000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep  2 13:43:42 owner kernel: [   23.668000] bcm43xx driver
Sep  2 13:43:42 owner kernel: [   23.792000] Yenta: ISA IRQ mask 0x06f8, PCI irq 16
Sep  2 13:43:42 owner kernel: [   23.792000] Socket status: 30000006
Sep  2 13:43:42 owner kernel: [   23.804000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
Sep  2 13:43:42 owner kernel: [   23.804000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  2 13:43:42 owner kernel: [   24.088000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 13:43:42 owner kernel: [   24.360000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Sep  2 13:43:42 owner kernel: [   24.396000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Sep  2 13:43:42 owner kernel: [   24.464000] cs: IO port probe 0x100-0x3af: clean.
Sep  2 13:43:42 owner kernel: [   24.468000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
Sep  2 13:43:42 owner kernel: [   24.468000] cs: IO port probe 0x820-0x8ff: clean.
Sep  2 13:43:42 owner kernel: [   24.468000] cs: IO port probe 0xc00-0xcf7: clean.
Sep  2 13:43:42 owner kernel: [   24.468000] cs: IO port probe 0xa00-0xaff: clean.
Sep  2 13:43:42 owner kernel: [   24.908000] intel8x0_measure_ac97_clock: measured 55455 usecs
Sep  2 13:43:42 owner kernel: [   24.908000] intel8x0: clocking to 48000
Sep  2 13:43:42 owner kernel: [   25.088000] lp: driver loaded but no devices found
Sep  2 13:43:42 owner kernel: [   25.164000] Adding 2441840k swap on /dev/disk/by-uuid/ed70067a-bce9-4fb6-907f-2c4c81db4df4.  Priority:-1 extents:1 across:2441840k
Sep  2 13:43:42 owner kernel: [   25.300000] EXT3 FS on hda1, internal journal
Sep  2 13:43:42 owner kernel: [   26.044000] ACPI: Battery Slot [BAT1] (battery present)
Sep  2 13:43:42 owner kernel: [   26.084000] ACPI: AC Adapter [ACAD] (on-line)
Sep  2 13:43:42 owner kernel: [   26.128000] No dock devices found.
Sep  2 13:43:42 owner kernel: [   26.204000] Using specific hotkey driver
Sep  2 13:43:42 owner kernel: [   26.308000] input: Power Button (FF) as /class/input/input5
Sep  2 13:43:42 owner kernel: [   26.312000] ACPI: Power Button (FF) [PWRF]
Sep  2 13:43:42 owner kernel: [   26.348000] input: Lid Switch as /class/input/input6
Sep  2 13:43:42 owner kernel: [   26.356000] ACPI: Lid Switch [LID]
Sep  2 13:43:42 owner kernel: [   26.392000] input: Power Button (CM) as /class/input/input7
Sep  2 13:43:42 owner kernel: [   26.396000] ACPI: Power Button (CM) [PWRB]
Sep  2 13:43:42 owner kernel: [   26.436000] input: Sleep Button (CM) as /class/input/input8
Sep  2 13:43:42 owner kernel: [   26.440000] ACPI: Sleep Button (CM) [SLPB]
Sep  2 13:43:42 owner kernel: [   26.532000] pcc_acpi: loading...
Sep  2 13:43:42 owner kernel: [   26.780000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
Sep  2 13:43:42 owner kernel: [   26.780000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
Sep  2 13:43:42 owner kernel: [   26.780000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
Sep  2 13:43:42 owner kernel: [   26.780000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
Sep  2 13:43:45 owner kernel: [   29.684000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:43:45 owner kernel: [   29.700000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:43:45 owner kernel: [   29.732000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:43:45 owner dhcdbd: Started up.
Sep  2 13:43:45 owner kernel: [   29.956000] eth1: Media Link Off
Sep  2 13:43:47 owner kernel: [   32.004000] ppdev: user-space parallel port driver
Sep  2 13:43:49 owner hpiod: 1.7.3 accepting connections at 2208... 
Sep  2 13:43:49 owner kernel: [   34.300000] apm: BIOS not found.
Sep  2 13:43:49 owner kernel: [   34.496000] Bluetooth: Core ver 2.11
Sep  2 13:43:49 owner kernel: [   34.496000] NET: Registered protocol family 31
Sep  2 13:43:49 owner kernel: [   34.496000] Bluetooth: HCI device and connection manager initialized
Sep  2 13:43:49 owner kernel: [   34.496000] Bluetooth: HCI socket layer initialized
Sep  2 13:43:49 owner kernel: [   34.544000] Bluetooth: L2CAP ver 2.8
Sep  2 13:43:49 owner kernel: [   34.544000] Bluetooth: L2CAP socket layer initialized
Sep  2 13:43:50 owner kernel: [   34.636000] Bluetooth: RFCOMM socket layer initialized
Sep  2 13:43:50 owner kernel: [   34.636000] Bluetooth: RFCOMM TTY layer initialized
Sep  2 13:43:50 owner kernel: [   34.636000] Bluetooth: RFCOMM ver 1.8
Sep  2 13:44:00 owner gconfd (owner-4944): starting (version 2.18.0.1), pid 4944 user 'owner'
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 13:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 13:44:02 owner kernel: [   47.108000] NET: Registered protocol family 10
Sep  2 13:44:02 owner kernel: [   47.108000] lo: Disabled Privacy Extensions
Sep  2 13:44:02 owner kernel: [   47.108000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep  2 13:44:09 owner gconfd (owner-4944): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 0
Sep  2 13:44:12 owner kernel: [   57.304000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:44:42 owner kernel: [   87.288000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:45:12 owner kernel: [  117.284000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:45:42 owner kernel: [  147.284000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:45:45 owner kernel: [  149.740000] usb 3-6: new high speed USB device using ehci_hcd and address 3
Sep  2 13:45:45 owner kernel: [  149.876000] usb 3-6: configuration #1 chosen from 1 choice
Sep  2 13:45:45 owner kernel: [  149.996000] usbcore: registered new interface driver libusual
Sep  2 13:45:45 owner kernel: [  150.096000] Initializing USB Mass Storage driver...
Sep  2 13:45:45 owner kernel: [  150.096000] scsi0 : SCSI emulation for USB Mass Storage devices
Sep  2 13:45:45 owner kernel: [  150.100000] usbcore: registered new interface driver usb-storage
Sep  2 13:45:45 owner kernel: [  150.100000] USB Mass Storage support registered.
Sep  2 13:45:50 owner kernel: [  155.100000] scsi 0:0:0:0: Direct-Access     Memorex  Flashdrive 501B  PMAP PQ: 0 ANSI: 0 CCS
Sep  2 13:45:50 owner kernel: [  155.152000] SCSI device sda: 248096 512-byte hdwr sectors (127 MB)
Sep  2 13:45:50 owner kernel: [  155.156000] sda: Write Protect is off
Sep  2 13:45:50 owner kernel: [  155.156000] SCSI device sda: 248096 512-byte hdwr sectors (127 MB)
Sep  2 13:45:50 owner kernel: [  155.156000] sda: Write Protect is off
Sep  2 13:45:50 owner kernel: [  155.156000]  sda: sda1
Sep  2 13:45:50 owner kernel: [  155.160000] sd 0:0:0:0: Attached scsi removable disk sda
Sep  2 13:45:50 owner kernel: [  155.188000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  2 13:46:12 owner kernel: [  177.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:46:42 owner kernel: [  207.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:47:12 owner kernel: [  237.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:47:42 owner kernel: [  267.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:48:12 owner kernel: [  297.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:48:13 owner kernel: [  297.928000] usb 3-6: USB disconnect, address 3
Sep  2 13:48:42 owner kernel: [  327.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:49:12 owner kernel: [  357.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:49:42 owner kernel: [  387.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:50:12 owner kernel: [  417.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:50:42 owner kernel: [  447.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:51:12 owner kernel: [  477.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:51:42 owner kernel: [  507.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:52:12 owner kernel: [  537.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:52:42 owner kernel: [  567.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:53:12 owner kernel: [  597.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:53:42 owner kernel: [  627.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:54:12 owner kernel: [  657.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:54:42 owner kernel: [  687.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:55:12 owner kernel: [  717.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:55:42 owner kernel: [  747.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:56:12 owner kernel: [  777.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:56:42 owner kernel: [  807.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:57:12 owner kernel: [  837.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:57:42 owner kernel: [  867.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:58:12 owner kernel: [  897.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:58:42 owner kernel: [  927.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:59:12 owner kernel: [  957.268000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 13:59:12 owner kernel: [  957.268000] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat sg sd_mod usb_storage libusual ipv6 binfmt_misc rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_ondemand cpufreq_userspace freq_table cpufreq_conservative cpufreq_powersave pcc_acpi tc1100_wmi dev_acpi sony_acpi container button video dock sbs i2c_ec ac asus_acpi battery backlight parport_pc lp parport joydev pcmcia snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event psmouse snd_seq snd_timer snd_seq_device bcm43xx ieee80211softmac serio_raw ieee80211 i2c_sis96x pcspkr yenta_socket rsrc_nonstatic pcmcia_core snd k8temp sis_agp amd64_agp agpgart shpchp pci_hotplug ieee80211_crypt soundcore snd_page_alloc i2c_core evdev tsdev ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod usbhid hid sis5513 sis900 mii generic ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit so
Sep  2 13:59:12 owner kernel: tcursor vesafb capability commoncap
Sep  2 13:59:12 owner kernel: [  957.268000]  <0>------------[ cut here ]------------
Sep  2 13:59:12 owner kernel: [  957.284000] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat sg sd_mod usb_storage libusual ipv6 binfmt_misc rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_ondemand cpufreq_userspace freq_table cpufreq_conservative cpufreq_powersave pcc_acpi tc1100_wmi dev_acpi sony_acpi container button video dock sbs i2c_ec ac asus_acpi battery backlight parport_pc lp parport joydev pcmcia snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event psmouse snd_seq snd_timer snd_seq_device bcm43xx ieee80211softmac serio_raw ieee80211 i2c_sis96x pcspkr yenta_socket rsrc_nonstatic pcmcia_core snd k8temp sis_agp amd64_agp agpgart shpchp pci_hotplug ieee80211_crypt soundcore snd_page_alloc i2c_core evdev tsdev ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod usbhid hid sis5513 sis900 mii generic ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit so
Sep  2 13:59:12 owner kernel: tcursor vesafb capability commoncap
Sep  2 13:59:12 owner kernel: [  957.284000]  <1>Fixing recursive fault but reboot is needed!
Sep  2 14:01:56 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  2 14:01:56 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  2 14:01:56 owner kernel: [ 1120.956000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Sep  2 14:01:58 owner kernel: [ 1123.152000] NET: Registered protocol family 17
Sep  2 14:02:01 owner kernel: [ 1125.956000] eth1: Media Link On 10mbps half-duplex 
Sep  2 14:02:02 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep  2 14:02:02 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Sep  2 14:02:02 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep  2 14:02:02 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep  2 14:23:40 owner -- MARK --
Sep  2 14:39:29 owner gconfd (root-11404): starting (version 2.18.0.1), pid 11404 user 'root'
Sep  2 14:39:29 owner gconfd (root-11404): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 14:39:29 owner gconfd (root-11404): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Sep  2 14:39:29 owner gconfd (root-11404): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 14:39:29 owner gconfd (root-11404): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 14:39:29 owner gconfd (root-11404): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 14:39:59 owner gconfd (root-11404): GConf server is not in use, shutting down.
Sep  2 14:39:59 owner gconfd (root-11404): Exiting
Sep  2 14:41:55 owner gconfd (root-12707): starting (version 2.18.0.1), pid 12707 user 'root'
Sep  2 14:41:55 owner gconfd (root-12707): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 14:41:55 owner gconfd (root-12707): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Sep  2 14:41:55 owner gconfd (root-12707): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 14:41:55 owner gconfd (root-12707): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 14:41:55 owner gconfd (root-12707): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 14:42:00 owner gconfd (owner-4944): SIGHUP received, reloading all databases
Sep  2 14:42:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 14:42:00 owner gconfd (owner-4944): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  2 14:42:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 14:42:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 14:42:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 14:42:25 owner gconfd (root-12707): GConf server is not in use, shutting down.
Sep  2 14:42:25 owner gconfd (root-12707): Exiting
Sep  2 14:44:00 owner gconfd (owner-4944): SIGHUP received, reloading all databases
Sep  2 14:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 14:44:00 owner gconfd (owner-4944): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  2 14:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 14:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 14:44:00 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 14:44:27 owner gconfd (root-13732): starting (version 2.18.0.1), pid 13732 user 'root'
Sep  2 14:44:27 owner gconfd (root-13732): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 14:44:27 owner gconfd (root-13732): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Sep  2 14:44:27 owner gconfd (root-13732): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 14:44:27 owner gconfd (root-13732): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 14:44:27 owner gconfd (root-13732): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 14:44:30 owner gconfd (owner-4944): SIGHUP received, reloading all databases
Sep  2 14:44:30 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 14:44:30 owner gconfd (owner-4944): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  2 14:44:30 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 14:44:30 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 14:44:30 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 14:45:00 owner gconfd (root-13732): Exiting
Sep  2 14:45:30 owner gconfd (owner-4944): SIGHUP received, reloading all databases
Sep  2 14:45:30 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 14:45:30 owner gconfd (owner-4944): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  2 14:45:30 owner gconfd (owner-4944): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 14:45:30 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 14:45:30 owner gconfd (owner-4944): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 14:46:00 owner gconfd (owner-4944): Exiting
Sep  2 14:46:10 owner exiting on signal 15
Sep  2 14:47:04 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  2 14:47:04 owner kernel: Inspecting /boot/System.map-2.6.20-16-generic
Sep  2 14:47:04 owner kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Sep  2 14:47:04 owner kernel: Symbols match kernel version 2.6.20.
Sep  2 14:47:04 owner kernel: No module symbols loaded - kernel modules not enabled. 
Sep  2 14:47:04 owner kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
Sep  2 14:47:04 owner kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  2 14:47:04 owner kernel: [    0.000000] sanitize start
Sep  2 14:47:04 owner kernel: [    0.000000] sanitize end
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000047df0000 end: 0000000047ef0000 type: 1
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() start: 0000000047ef0000 size: 000000000000a000 end: 0000000047efa000 type: 3
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() start: 0000000047efa000 size: 0000000000006000 end: 0000000047f00000 type: 4
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() start: 0000000047f00000 size: 0000000008100000 end: 0000000050000000 type: 2
Sep  2 14:47:04 owner kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Sep  2 14:47:04 owner kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Sep  2 14:47:04 owner kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Sep  2 14:47:04 owner kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Sep  2 14:47:04 owner kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000047ef0000 (usable)
Sep  2 14:47:04 owner kernel: [    0.000000]  BIOS-e820: 0000000047ef0000 - 0000000047efa000 (ACPI data)
Sep  2 14:47:04 owner kernel: [    0.000000]  BIOS-e820: 0000000047efa000 - 0000000047f00000 (ACPI NVS)
Sep  2 14:47:04 owner kernel: [    0.000000]  BIOS-e820: 0000000047f00000 - 0000000050000000 (reserved)
Sep  2 14:47:04 owner kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Sep  2 14:47:04 owner kernel: [    0.000000] 254MB HIGHMEM available.
Sep  2 14:47:04 owner kernel: [    0.000000] 896MB LOWMEM available.
Sep  2 14:47:04 owner kernel: [    0.000000] found SMP MP-table at 000f7fd0
Sep  2 14:47:04 owner kernel: [    0.000000] Zone PFN ranges:
Sep  2 14:47:04 owner kernel: [    0.000000]   DMA             0 ->     4096
Sep  2 14:47:04 owner kernel: [    0.000000]   Normal       4096 ->   229376
Sep  2 14:47:04 owner kernel: [    0.000000]   HighMem    229376 ->   294640
Sep  2 14:47:04 owner kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  2 14:47:04 owner kernel: [    0.000000]     0:        0 ->   294640
Sep  2 14:47:04 owner kernel: [    0.000000] DMI present.
Sep  2 14:47:04 owner kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Sep  2 14:47:04 owner kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  2 14:47:04 owner kernel: [    0.000000] Processor #0 15:12 APIC version 16
Sep  2 14:47:04 owner kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  2 14:47:04 owner kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  2 14:47:04 owner kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Sep  2 14:47:04 owner kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Sep  2 14:47:04 owner kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  2 14:47:04 owner kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  2 14:47:04 owner kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aff00000)
Sep  2 14:47:04 owner kernel: [    0.000000] Detected 1800.168 MHz processor.
Sep  2 14:47:04 owner kernel: [   11.789345] Built 1 zonelists.  Total pages: 292339
Sep  2 14:47:04 owner kernel: [   11.789349] Kernel command line: root=UUID=36f4f755-b608-49ce-b11a-e96f60601f95 ro quiet splash
Sep  2 14:47:04 owner kernel: [   11.789495] Enabling fast FPU save and restore... done.
Sep  2 14:47:04 owner kernel: [   11.789498] Enabling unmasked SIMD FPU exception support... done.
Sep  2 14:47:04 owner kernel: [   11.789505] Initializing CPU#0
Sep  2 14:47:04 owner kernel: [   11.789548] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  2 14:47:04 owner kernel: [   11.790307] Console: colour VGA+ 80x25
Sep  2 14:47:04 owner kernel: [   11.790890] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  2 14:47:04 owner kernel: [   11.791884] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  2 14:47:04 owner kernel: [   11.822341] Memory: 1157140k/1178560k available (1993k kernel code, 20500k reserved, 900k data, 328k init, 261056k highmem)
Sep  2 14:47:04 owner kernel: [   11.822352] virtual kernel memory layout:
Sep  2 14:47:04 owner kernel: [   11.822354]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep  2 14:47:04 owner kernel: [   11.822355]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  2 14:47:04 owner kernel: [   11.822356]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  2 14:47:04 owner kernel: [   11.822358]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  2 14:47:04 owner kernel: [   11.822359]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Sep  2 14:47:04 owner kernel: [   11.822360]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
Sep  2 14:47:04 owner kernel: [   11.822362]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
Sep  2 14:47:04 owner kernel: [   11.822365] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  2 14:47:04 owner kernel: [   11.901387] Calibrating delay using timer specific routine.. 3602.06 BogoMIPS (lpj=7204128)
Sep  2 14:47:04 owner kernel: [   11.901434] Security Framework v1.0.0 initialized
Sep  2 14:47:04 owner kernel: [   11.901443] SELinux:  Disabled at boot.
Sep  2 14:47:04 owner kernel: [   11.901459] Mount-cache hash table entries: 512
Sep  2 14:47:04 owner kernel: [   11.901621] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  2 14:47:04 owner kernel: [   11.901624] CPU: L2 Cache: 128K (64 bytes/line)
Sep  2 14:47:04 owner kernel: [   11.901639] Compat vDSO mapped to ffffe000.
Sep  2 14:47:04 owner kernel: [   11.901644] Remapping vsyscall page to ffffe000
Sep  2 14:47:04 owner kernel: [   11.901654] Checking 'hlt' instruction... OK.
Sep  2 14:47:04 owner kernel: [   11.917515] SMP alternatives: switching to UP code
Sep  2 14:47:04 owner kernel: [   11.917818] Freeing SMP alternatives: 11k freed
Sep  2 14:47:04 owner kernel: [   11.918079] Early unpacking initramfs... done
Sep  2 14:47:04 owner kernel: [   12.230711] ACPI: Core revision 20060707
Sep  2 14:47:04 owner kernel: [   12.230929] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep  2 14:47:04 owner kernel: [   12.234484] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
Sep  2 14:47:04 owner kernel: [   12.234503] Total of 1 processors activated (3602.06 BogoMIPS).
Sep  2 14:47:04 owner kernel: [   12.234657] ENABLING IO-APIC IRQs
Sep  2 14:47:04 owner kernel: [   12.234849] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  2 14:47:04 owner kernel: [   12.380718] Brought up 1 CPUs
Sep  2 14:47:04 owner kernel: [   12.380946] Booting paravirtualized kernel on bare hardware
Sep  2 14:47:04 owner kernel: [   12.381021] Time: 19:46:38  Date: 08/02/107
Sep  2 14:47:04 owner kernel: [   12.381056] NET: Registered protocol family 16
Sep  2 14:47:04 owner kernel: [   12.381156] EISA bus registered
Sep  2 14:47:04 owner kernel: [   12.381161] ACPI: bus type pci registered
Sep  2 14:47:04 owner kernel: [   12.381309] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
Sep  2 14:47:04 owner kernel: [   12.381311] PCI: Using configuration type 1
Sep  2 14:47:04 owner kernel: [   12.381313] Setting up standard PCI resources
Sep  2 14:47:04 owner kernel: [   12.383719] ACPI: Interpreter enabled
Sep  2 14:47:04 owner kernel: [   12.383724] ACPI: Using IOAPIC for interrupt routing
Sep  2 14:47:04 owner kernel: [   12.384061] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  2 14:47:04 owner kernel: [   12.385171] Enabling SiS 96x SMBus.
Sep  2 14:47:04 owner kernel: [   12.406325] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
Sep  2 14:47:04 owner kernel: [   12.406505] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
Sep  2 14:47:04 owner kernel: [   12.406679] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
Sep  2 14:47:04 owner kernel: [   12.406849] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
Sep  2 14:47:04 owner kernel: [   12.407044] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
Sep  2 14:47:04 owner kernel: [   12.407215] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
Sep  2 14:47:04 owner kernel: [   12.407382] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Sep  2 14:47:04 owner kernel: [   12.407550] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
Sep  2 14:47:04 owner kernel: [   12.407834] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  2 14:47:04 owner kernel: [   12.407851] pnp: PnP ACPI init
Sep  2 14:47:04 owner kernel: [   12.409499] pnp: PnP ACPI: found 8 devices
Sep  2 14:47:04 owner kernel: [   12.409505] PnPBIOS: Disabled by ACPI PNP
Sep  2 14:47:04 owner kernel: [   12.409562] PCI: Using ACPI for IRQ routing
Sep  2 14:47:04 owner kernel: [   12.409565] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  2 14:47:04 owner kernel: [   12.411678] NET: Registered protocol family 8
Sep  2 14:47:04 owner kernel: [   12.411680] NET: Registered protocol family 20
Sep  2 14:47:04 owner kernel: [   12.411858] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
Sep  2 14:47:04 owner kernel: [   12.411861] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
Sep  2 14:47:04 owner kernel: [   12.411864] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
Sep  2 14:47:04 owner kernel: [   12.411867] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
Sep  2 14:47:04 owner kernel: [   12.412122] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
Sep  2 14:47:04 owner kernel: [   12.412126] PCI: Bridge: 0000:00:01.0
Sep  2 14:47:04 owner kernel: [   12.412129]   IO window: a000-afff
Sep  2 14:47:04 owner kernel: [   12.412133]   MEM window: e2100000-e21fffff
Sep  2 14:47:04 owner kernel: [   12.412136]   PREFETCH window: e8000000-efffffff
Sep  2 14:47:04 owner kernel: [   12.412141] PCI: Bus 2, cardbus bridge: 0000:00:06.0
Sep  2 14:47:04 owner kernel: [   12.412143]   IO window: 00002400-000024ff
Sep  2 14:47:04 owner kernel: [   12.412147]   IO window: 00002800-000028ff
Sep  2 14:47:04 owner kernel: [   12.412150]   PREFETCH window: 60000000-63ffffff
Sep  2 14:47:04 owner kernel: [   12.412154]   MEM window: 64000000-67ffffff
Sep  2 14:47:04 owner kernel: [   12.412171] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
Sep  2 14:47:04 owner kernel: [   12.412183] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 14:47:04 owner kernel: [   12.412225] NET: Registered protocol family 2
Sep  2 14:47:04 owner kernel: [   12.448668] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  2 14:47:04 owner kernel: [   12.448887] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  2 14:47:04 owner kernel: [   12.450225] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  2 14:47:04 owner kernel: [   12.450906] TCP: Hash tables configured (established 131072 bind 65536)
Sep  2 14:47:04 owner kernel: [   12.450911] TCP reno registered
Sep  2 14:47:04 owner kernel: [   12.460711] checking if image is initramfs... it is
Sep  2 14:47:04 owner kernel: [   13.075959] Freeing initrd memory: 6782k freed
Sep  2 14:47:04 owner kernel: [   13.076145] Simple Boot Flag at 0x38 set to 0x1
Sep  2 14:47:04 owner kernel: [   13.076406] audit: initializing netlink socket (disabled)
Sep  2 14:47:04 owner kernel: [   13.076422] audit(1188762398.368:1): initialized
Sep  2 14:47:04 owner kernel: [   13.076484] highmem bounce pool size: 64 pages
Sep  2 14:47:04 owner kernel: [   13.076564] VFS: Disk quotas dquot_6.5.1
Sep  2 14:47:04 owner kernel: [   13.076588] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  2 14:47:04 owner kernel: [   13.076646] io scheduler noop registered
Sep  2 14:47:04 owner kernel: [   13.076648] io scheduler anticipatory registered
Sep  2 14:47:04 owner kernel: [   13.076650] io scheduler deadline registered
Sep  2 14:47:04 owner kernel: [   13.076664] io scheduler cfq registered (default)
Sep  2 14:47:04 owner kernel: [   13.503284] isapnp: Scanning for PnP cards...
Sep  2 14:47:04 owner kernel: [   13.856161] isapnp: No Plug & Play device found
Sep  2 14:47:04 owner kernel: [   13.891820] Real Time Clock Driver v1.12ac
Sep  2 14:47:04 owner kernel: [   13.891859] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  2 14:47:04 owner kernel: [   13.892857] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 14:47:04 owner kernel: [   13.892864] ACPI: PCI interrupt for device 0000:00:02.6 disabled
Sep  2 14:47:04 owner kernel: [   13.892932] mice: PS/2 mouse device common for all mice
Sep  2 14:47:04 owner kernel: [   13.893378] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  2 14:47:04 owner kernel: [   13.893627] input: Macintosh mouse button emulation as /class/input/input0
Sep  2 14:47:04 owner kernel: [   13.893659] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep  2 14:47:04 owner kernel: [   13.893663] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep  2 14:47:04 owner kernel: [   13.893869] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  2 14:47:04 owner kernel: [   13.897486] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  2 14:47:04 owner kernel: [   13.897494] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  2 14:47:04 owner kernel: [   13.897656] EISA: Probing bus 0 at eisa.0
Sep  2 14:47:04 owner kernel: [   13.897666] Cannot allocate resource for EISA slot 1
Sep  2 14:47:04 owner kernel: [   13.897669] Cannot allocate resource for EISA slot 2
Sep  2 14:47:04 owner kernel: [   13.897687] Cannot allocate resource for EISA slot 8
Sep  2 14:47:04 owner kernel: [   13.897689] EISA: Detected 0 cards.
Sep  2 14:47:04 owner kernel: [   13.927735] TCP cubic registered
Sep  2 14:47:04 owner kernel: [   13.927744] NET: Registered protocol family 1
Sep  2 14:47:04 owner kernel: [   13.927768] Using IPI No-Shortcut mode
Sep  2 14:47:04 owner kernel: [   13.927829] ACPI: (supports S0 S3 S4 S5)
Sep  2 14:47:04 owner kernel: [   13.927862]   Magic number: 7:419:798
Sep  2 14:47:04 owner kernel: [   13.927956]   hash matches device ptyr6
Sep  2 14:47:04 owner kernel: [   13.928311] Freeing unused kernel memory: 328k freed
Sep  2 14:47:04 owner kernel: [   13.930405] Time: tsc clocksource has been installed.
Sep  2 14:47:04 owner kernel: [   13.944520] input: AT Translated Set 2 keyboard as /class/input/input1
Sep  2 14:47:04 owner kernel: [   15.201987] Capability LSM initialized
Sep  2 14:47:04 owner kernel: [   15.250729] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 14:47:04 owner kernel: [   15.253994] ACPI: Thermal Zone [THRM] (64 C)
Sep  2 14:47:04 owner kernel: [   15.924680] SIS5513: IDE controller at PCI slot 0000:00:02.5
Sep  2 14:47:04 owner kernel: [   15.924698] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 18
Sep  2 14:47:04 owner kernel: [   15.924708] SIS5513: chipset revision 0
Sep  2 14:47:04 owner kernel: [   15.924711] SIS5513: not 100%% native mode: will probe irqs later
Sep  2 14:47:04 owner kernel: [   15.924722] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
Sep  2 14:47:04 owner kernel: [   15.924736]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
Sep  2 14:47:04 owner kernel: [   15.924747]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
Sep  2 14:47:04 owner kernel: [   15.977131] usbcore: registered new interface driver usbfs
Sep  2 14:47:04 owner kernel: [   15.977153] usbcore: registered new interface driver hub
Sep  2 14:47:04 owner kernel: [   15.977173] usbcore: registered new device driver usb
Sep  2 14:47:04 owner kernel: [   15.992062] sis900.c: v1.08.10 Apr. 2 2006
Sep  2 14:47:04 owner kernel: [    3.916000] Time: acpi_pm clocksource has been installed.
Sep  2 14:47:04 owner kernel: [    3.964000] hda: TOSHIBA MK6025GAS, ATA DISK drive
Sep  2 14:47:04 owner kernel: [    4.636000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep  2 14:47:04 owner kernel: [    5.432000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
Sep  2 14:47:04 owner kernel: [    6.104000] ide1 at 0x170-0x177,0x376 on irq 15
Sep  2 14:47:04 owner kernel: [    6.112000] SCSI subsystem initialized
Sep  2 14:47:04 owner kernel: [    6.124000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 19
Sep  2 14:47:04 owner kernel: [    6.124000] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep  2 14:47:04 owner kernel: [    6.128000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Sep  2 14:47:04 owner kernel: [    6.128000] ohci_hcd 0000:00:03.0: irq 19, io mem 0xe2002000
Sep  2 14:47:04 owner kernel: [    6.136000] hda: max request size: 128KiB
Sep  2 14:47:04 owner kernel: [    6.152000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
Sep  2 14:47:04 owner kernel: [    6.152000] hda: cache flushes supported
Sep  2 14:47:04 owner kernel: [    6.152000]  hda:<6>usb usb1: configuration #1 chosen from 1 choice
Sep  2 14:47:04 owner kernel: [    6.184000] hub 1-0:1.0: USB hub found
Sep  2 14:47:04 owner kernel: [    6.184000] hub 1-0:1.0: 3 ports detected
Sep  2 14:47:04 owner kernel: [    6.212000]  hda1 hda2 < hda5 >
Sep  2 14:47:04 owner kernel: [    6.256000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep  2 14:47:04 owner kernel: [    6.256000] Uniform CD-ROM driver Revision: 3.20
Sep  2 14:47:04 owner kernel: [    6.288000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 20
Sep  2 14:47:04 owner kernel: [    6.288000] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep  2 14:47:04 owner kernel: [    6.288000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Sep  2 14:47:04 owner kernel: [    6.288000] ohci_hcd 0000:00:03.1: irq 20, io mem 0xe2003000
Sep  2 14:47:04 owner kernel: [    6.344000] usb usb2: configuration #1 chosen from 1 choice
Sep  2 14:47:04 owner kernel: [    6.344000] hub 2-0:1.0: USB hub found
Sep  2 14:47:04 owner kernel: [    6.344000] hub 2-0:1.0: 3 ports detected
Sep  2 14:47:04 owner kernel: [    6.448000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 14:47:04 owner kernel: [    6.452000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Sep  2 14:47:04 owner kernel: [    6.456000] 0000:00:04.0: Using transceiver found at address 13 as default
Sep  2 14:47:04 owner kernel: [    6.456000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 16, 00:c0:9f:c1:44:ea.
Sep  2 14:47:04 owner kernel: [    6.456000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 21
Sep  2 14:47:04 owner kernel: [    6.456000] ehci_hcd 0000:00:03.2: EHCI Host Controller
Sep  2 14:47:04 owner kernel: [    6.456000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Sep  2 14:47:04 owner kernel: [    6.456000] ehci_hcd 0000:00:03.2: irq 21, io mem 0xe2004000
Sep  2 14:47:04 owner kernel: [    6.456000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  2 14:47:04 owner kernel: [    6.456000] usb usb3: configuration #1 chosen from 1 choice
Sep  2 14:47:04 owner kernel: [    6.456000] hub 3-0:1.0: USB hub found
Sep  2 14:47:04 owner kernel: [    6.456000] hub 3-0:1.0: 6 ports detected
Sep  2 14:47:04 owner kernel: [    6.628000] kjournald starting.  Commit interval 5 seconds
Sep  2 14:47:04 owner kernel: [    6.628000] EXT3-fs: mounted filesystem with ordered data mode.
Sep  2 14:47:04 owner kernel: [    7.136000] usb 1-2: new low speed USB device using ohci_hcd and address 3
Sep  2 14:47:04 owner kernel: [    7.344000] usb 1-2: configuration #1 chosen from 1 choice
Sep  2 14:47:04 owner kernel: [   21.332000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  2 14:47:04 owner kernel: [   21.336000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  2 14:47:04 owner kernel: [   21.608000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep  2 14:47:04 owner kernel: [   21.608000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep  2 14:47:04 owner kernel: [   21.804000] Linux agpgart interface v0.102 (c) Dave Jones
Sep  2 14:47:04 owner kernel: [   21.880000] bcm43xx driver
Sep  2 14:47:04 owner kernel: [   21.880000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  2 14:47:04 owner kernel: [   21.940000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
Sep  2 14:47:04 owner kernel: [   21.940000] Yenta: Using CSCINT to route CSC interrupts to PCI
Sep  2 14:47:04 owner kernel: [   21.940000] Yenta: Routing CardBus interrupts to PCI
Sep  2 14:47:04 owner kernel: [   21.940000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
Sep  2 14:47:04 owner kernel: [   22.172000] Yenta: ISA IRQ mask 0x06f8, PCI irq 16
Sep  2 14:47:04 owner kernel: [   22.172000] Socket status: 30000006
Sep  2 14:47:04 owner kernel: [   22.172000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
Sep  2 14:47:04 owner kernel: [   22.172000] agpgart: Detected AGP bridge 0
Sep  2 14:47:04 owner kernel: [   22.172000] agpgart: AGP aperture is 32M @ 0xe0000000
Sep  2 14:47:04 owner kernel: [   22.340000] input: PC Speaker as /class/input/input2
Sep  2 14:47:04 owner kernel: [   22.568000] usbcore: registered new interface driver hiddev
Sep  2 14:47:04 owner kernel: [   22.708000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 14:47:04 owner kernel: [   22.736000] input: HID 1241:1166 as /class/input/input3
Sep  2 14:47:04 owner kernel: [   22.736000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:03.0-2
Sep  2 14:47:04 owner kernel: [   22.736000] usbcore: registered new interface driver usbhid
Sep  2 14:47:04 owner kernel: [   22.736000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Sep  2 14:47:04 owner kernel: [   22.852000] cs: IO port probe 0x100-0x3af: clean.
Sep  2 14:47:04 owner kernel: [   22.856000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
Sep  2 14:47:04 owner kernel: [   22.856000] cs: IO port probe 0x820-0x8ff: clean.
Sep  2 14:47:04 owner kernel: [   22.856000] cs: IO port probe 0xc00-0xcf7: clean.
Sep  2 14:47:04 owner kernel: [   22.856000] cs: IO port probe 0xa00-0xaff: clean.
Sep  2 14:47:04 owner kernel: [   22.872000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Sep  2 14:47:04 owner kernel: [   22.908000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Sep  2 14:47:04 owner kernel: [   23.528000] intel8x0_measure_ac97_clock: measured 55457 usecs
Sep  2 14:47:04 owner kernel: [   23.528000] intel8x0: clocking to 48000
Sep  2 14:47:04 owner kernel: [   23.736000] lp: driver loaded but no devices found
Sep  2 14:47:04 owner kernel: [   23.808000] Adding 2441840k swap on /dev/disk/by-uuid/ed70067a-bce9-4fb6-907f-2c4c81db4df4.  Priority:-1 extents:1 across:2441840k
Sep  2 14:47:04 owner kernel: [   23.944000] EXT3 FS on hda1, internal journal
Sep  2 14:47:04 owner kernel: [   25.080000] ACPI: Battery Slot [BAT1] (battery present)
Sep  2 14:47:04 owner kernel: [   25.120000] ACPI: AC Adapter [ACAD] (on-line)
Sep  2 14:47:04 owner kernel: [   25.164000] No dock devices found.
Sep  2 14:47:04 owner kernel: [   25.228000] Using specific hotkey driver
Sep  2 14:47:04 owner kernel: [   25.328000] input: Power Button (FF) as /class/input/input5
Sep  2 14:47:04 owner kernel: [   25.336000] ACPI: Power Button (FF) [PWRF]
Sep  2 14:47:04 owner kernel: [   25.372000] input: Lid Switch as /class/input/input6
Sep  2 14:47:04 owner kernel: [   25.376000] ACPI: Lid Switch [LID]
Sep  2 14:47:04 owner kernel: [   25.416000] input: Power Button (CM) as /class/input/input7
Sep  2 14:47:04 owner kernel: [   25.420000] ACPI: Power Button (CM) [PWRB]
Sep  2 14:47:04 owner kernel: [   25.456000] input: Sleep Button (CM) as /class/input/input8
Sep  2 14:47:04 owner kernel: [   25.460000] ACPI: Sleep Button (CM) [SLPB]
Sep  2 14:47:04 owner kernel: [   25.556000] pcc_acpi: loading...
Sep  2 14:47:04 owner kernel: [   25.860000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
Sep  2 14:47:04 owner kernel: [   25.860000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
Sep  2 14:47:04 owner kernel: [   25.860000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
Sep  2 14:47:04 owner kernel: [   25.860000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
Sep  2 14:47:07 owner kernel: [   28.952000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:47:07 owner kernel: [   28.972000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:47:07 owner kernel: [   29.004000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:47:07 owner dhcdbd: Started up.
Sep  2 14:47:10 owner kernel: [   31.632000] eth1: Media Link On 10mbps half-duplex 
Sep  2 14:47:10 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  2 14:47:10 owner kernel: [   32.376000] ppdev: user-space parallel port driver
Sep  2 14:47:11 owner hpiod: 1.7.3 accepting connections at 2208... 
Sep  2 14:47:12 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  2 14:47:12 owner kernel: [   34.464000] apm: BIOS not found.
Sep  2 14:47:13 owner kernel: [   34.664000] Bluetooth: Core ver 2.11
Sep  2 14:47:13 owner kernel: [   34.664000] NET: Registered protocol family 31
Sep  2 14:47:13 owner kernel: [   34.664000] Bluetooth: HCI device and connection manager initialized
Sep  2 14:47:13 owner kernel: [   34.664000] Bluetooth: HCI socket layer initialized
Sep  2 14:47:13 owner kernel: [   34.700000] Bluetooth: L2CAP ver 2.8
Sep  2 14:47:13 owner kernel: [   34.700000] Bluetooth: L2CAP socket layer initialized
Sep  2 14:47:13 owner kernel: [   34.776000] Bluetooth: RFCOMM socket layer initialized
Sep  2 14:47:13 owner kernel: [   34.776000] Bluetooth: RFCOMM TTY layer initialized
Sep  2 14:47:13 owner kernel: [   34.776000] Bluetooth: RFCOMM ver 1.8
Sep  2 14:47:14 owner kernel: [   36.496000] NET: Registered protocol family 17
Sep  2 14:47:16 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep  2 14:47:16 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Sep  2 14:47:16 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep  2 14:47:16 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep  2 14:47:17 owner kernel: [   39.004000] NET: Registered protocol family 10
Sep  2 14:47:17 owner kernel: [   39.004000] lo: Disabled Privacy Extensions
Sep  2 14:47:34 owner kernel: [   56.520000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:56:04 owner syslogd 1.4.1#20ubuntu4: restart.
Sep  2 14:56:05 owner kernel: Inspecting /boot/System.map-2.6.20-16-generic
Sep  2 14:56:05 owner kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Sep  2 14:56:05 owner kernel: Symbols match kernel version 2.6.20.
Sep  2 14:56:05 owner kernel: No module symbols loaded - kernel modules not enabled. 
Sep  2 14:56:05 owner kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
Sep  2 14:56:05 owner kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  2 14:56:05 owner kernel: [    0.000000] sanitize start
Sep  2 14:56:05 owner kernel: [    0.000000] sanitize end
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000047df0000 end: 0000000047ef0000 type: 1
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() type is E820_RAM
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000047ef0000 size: 000000000000a000 end: 0000000047efa000 type: 3
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000047efa000 size: 0000000000006000 end: 0000000047f00000 type: 4
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() start: 0000000047f00000 size: 0000000008100000 end: 0000000050000000 type: 2
Sep  2 14:56:05 owner kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Sep  2 14:56:05 owner kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Sep  2 14:56:05 owner kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Sep  2 14:56:05 owner kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Sep  2 14:56:05 owner kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000047ef0000 (usable)
Sep  2 14:56:05 owner kernel: [    0.000000]  BIOS-e820: 0000000047ef0000 - 0000000047efa000 (ACPI data)
Sep  2 14:56:05 owner kernel: [    0.000000]  BIOS-e820: 0000000047efa000 - 0000000047f00000 (ACPI NVS)
Sep  2 14:56:05 owner kernel: [    0.000000]  BIOS-e820: 0000000047f00000 - 0000000050000000 (reserved)
Sep  2 14:56:05 owner kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Sep  2 14:56:05 owner kernel: [    0.000000] 254MB HIGHMEM available.
Sep  2 14:56:05 owner kernel: [    0.000000] 896MB LOWMEM available.
Sep  2 14:56:05 owner kernel: [    0.000000] found SMP MP-table at 000f7fd0
Sep  2 14:56:05 owner kernel: [    0.000000] Zone PFN ranges:
Sep  2 14:56:05 owner kernel: [    0.000000]   DMA             0 ->     4096
Sep  2 14:56:05 owner kernel: [    0.000000]   Normal       4096 ->   229376
Sep  2 14:56:05 owner kernel: [    0.000000]   HighMem    229376 ->   294640
Sep  2 14:56:05 owner kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  2 14:56:05 owner kernel: [    0.000000]     0:        0 ->   294640
Sep  2 14:56:05 owner kernel: [    0.000000] DMI present.
Sep  2 14:56:05 owner kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Sep  2 14:56:05 owner kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  2 14:56:05 owner kernel: [    0.000000] Processor #0 15:12 APIC version 16
Sep  2 14:56:05 owner kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  2 14:56:05 owner kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Sep  2 14:56:05 owner kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Sep  2 14:56:05 owner kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Sep  2 14:56:05 owner kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  2 14:56:05 owner kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  2 14:56:05 owner kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aff00000)
Sep  2 14:56:05 owner kernel: [    0.000000] Detected 1800.162 MHz processor.
Sep  2 14:56:05 owner kernel: [   12.539249] Built 1 zonelists.  Total pages: 292339
Sep  2 14:56:05 owner kernel: [   12.539253] Kernel command line: root=UUID=36f4f755-b608-49ce-b11a-e96f60601f95 ro quiet splash
Sep  2 14:56:05 owner kernel: [   12.539399] Enabling fast FPU save and restore... done.
Sep  2 14:56:05 owner kernel: [   12.539401] Enabling unmasked SIMD FPU exception support... done.
Sep  2 14:56:05 owner kernel: [   12.539408] Initializing CPU#0
Sep  2 14:56:05 owner kernel: [   12.539451] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  2 14:56:05 owner kernel: [   12.540222] Console: colour VGA+ 80x25
Sep  2 14:56:05 owner kernel: [   12.540805] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  2 14:56:05 owner kernel: [   12.541796] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  2 14:56:05 owner kernel: [   12.572256] Memory: 1157140k/1178560k available (1993k kernel code, 20500k reserved, 900k data, 328k init, 261056k highmem)
Sep  2 14:56:05 owner kernel: [   12.572267] virtual kernel memory layout:
Sep  2 14:56:05 owner kernel: [   12.572268]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Sep  2 14:56:05 owner kernel: [   12.572269]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  2 14:56:05 owner kernel: [   12.572271]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  2 14:56:05 owner kernel: [   12.572272]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  2 14:56:05 owner kernel: [   12.572273]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Sep  2 14:56:05 owner kernel: [   12.572275]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
Sep  2 14:56:05 owner kernel: [   12.572276]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
Sep  2 14:56:05 owner kernel: [   12.572279] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  2 14:56:05 owner kernel: [   12.651290] Calibrating delay using timer specific routine.. 3602.08 BogoMIPS (lpj=7204161)
Sep  2 14:56:05 owner kernel: [   12.651336] Security Framework v1.0.0 initialized
Sep  2 14:56:05 owner kernel: [   12.651345] SELinux:  Disabled at boot.
Sep  2 14:56:05 owner kernel: [   12.651361] Mount-cache hash table entries: 512
Sep  2 14:56:05 owner kernel: [   12.651523] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  2 14:56:05 owner kernel: [   12.651526] CPU: L2 Cache: 128K (64 bytes/line)
Sep  2 14:56:05 owner kernel: [   12.651541] Compat vDSO mapped to ffffe000.
Sep  2 14:56:05 owner kernel: [   12.651545] Remapping vsyscall page to ffffe000
Sep  2 14:56:05 owner kernel: [   12.651555] Checking 'hlt' instruction... OK.
Sep  2 14:56:05 owner kernel: [   12.667417] SMP alternatives: switching to UP code
Sep  2 14:56:05 owner kernel: [   12.667718] Freeing SMP alternatives: 11k freed
Sep  2 14:56:05 owner kernel: [   12.667978] Early unpacking initramfs... done
Sep  2 14:56:05 owner kernel: [   12.980601] ACPI: Core revision 20060707
Sep  2 14:56:05 owner kernel: [   12.980819] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Sep  2 14:56:05 owner kernel: [   12.984577] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
Sep  2 14:56:05 owner kernel: [   12.984596] Total of 1 processors activated (3602.08 BogoMIPS).
Sep  2 14:56:05 owner kernel: [   12.984750] ENABLING IO-APIC IRQs
Sep  2 14:56:05 owner kernel: [   12.984943] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  2 14:56:05 owner kernel: [   13.130623] Brought up 1 CPUs
Sep  2 14:56:05 owner kernel: [   13.130851] Booting paravirtualized kernel on bare hardware
Sep  2 14:56:05 owner kernel: [   13.130926] Time: 19:55:39  Date: 08/02/107
Sep  2 14:56:05 owner kernel: [   13.130961] NET: Registered protocol family 16
Sep  2 14:56:05 owner kernel: [   13.131062] EISA bus registered
Sep  2 14:56:05 owner kernel: [   13.131066] ACPI: bus type pci registered
Sep  2 14:56:05 owner kernel: [   13.131215] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
Sep  2 14:56:05 owner kernel: [   13.131217] PCI: Using configuration type 1
Sep  2 14:56:05 owner kernel: [   13.131219] Setting up standard PCI resources
Sep  2 14:56:05 owner kernel: [   13.133627] ACPI: Interpreter enabled
Sep  2 14:56:05 owner kernel: [   13.133632] ACPI: Using IOAPIC for interrupt routing
Sep  2 14:56:05 owner kernel: [   13.133969] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  2 14:56:05 owner kernel: [   13.135081] Enabling SiS 96x SMBus.
Sep  2 14:56:05 owner kernel: [   13.156221] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
Sep  2 14:56:05 owner kernel: [   13.156401] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
Sep  2 14:56:05 owner kernel: [   13.156575] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
Sep  2 14:56:05 owner kernel: [   13.156744] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
Sep  2 14:56:05 owner kernel: [   13.156939] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
Sep  2 14:56:05 owner kernel: [   13.157109] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
Sep  2 14:56:05 owner kernel: [   13.157276] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Sep  2 14:56:05 owner kernel: [   13.157444] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
Sep  2 14:56:05 owner kernel: [   13.157726] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  2 14:56:05 owner kernel: [   13.157743] pnp: PnP ACPI init
Sep  2 14:56:05 owner kernel: [   13.159411] pnp: PnP ACPI: found 8 devices
Sep  2 14:56:05 owner kernel: [   13.159417] PnPBIOS: Disabled by ACPI PNP
Sep  2 14:56:05 owner kernel: [   13.159473] PCI: Using ACPI for IRQ routing
Sep  2 14:56:05 owner kernel: [   13.159477] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  2 14:56:05 owner kernel: [   13.161593] NET: Registered protocol family 8
Sep  2 14:56:05 owner kernel: [   13.161595] NET: Registered protocol family 20
Sep  2 14:56:05 owner kernel: [   13.161774] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
Sep  2 14:56:05 owner kernel: [   13.161777] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
Sep  2 14:56:05 owner kernel: [   13.161780] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
Sep  2 14:56:05 owner kernel: [   13.161783] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
Sep  2 14:56:05 owner kernel: [   13.162037] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
Sep  2 14:56:05 owner kernel: [   13.162040] PCI: Bridge: 0000:00:01.0
Sep  2 14:56:05 owner kernel: [   13.162043]   IO window: a000-afff
Sep  2 14:56:05 owner kernel: [   13.162047]   MEM window: e2100000-e21fffff
Sep  2 14:56:05 owner kernel: [   13.162051]   PREFETCH window: e8000000-efffffff
Sep  2 14:56:05 owner kernel: [   13.162055] PCI: Bus 2, cardbus bridge: 0000:00:06.0
Sep  2 14:56:05 owner kernel: [   13.162058]   IO window: 00002400-000024ff
Sep  2 14:56:05 owner kernel: [   13.162061]   IO window: 00002800-000028ff
Sep  2 14:56:05 owner kernel: [   13.162065]   PREFETCH window: 60000000-63ffffff
Sep  2 14:56:05 owner kernel: [   13.162068]   MEM window: 64000000-67ffffff
Sep  2 14:56:05 owner kernel: [   13.162085] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
Sep  2 14:56:05 owner kernel: [   13.162097] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 14:56:05 owner kernel: [   13.162139] NET: Registered protocol family 2
Sep  2 14:56:05 owner kernel: [   13.198570] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  2 14:56:05 owner kernel: [   13.198789] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  2 14:56:05 owner kernel: [   13.200125] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  2 14:56:05 owner kernel: [   13.200807] TCP: Hash tables configured (established 131072 bind 65536)
Sep  2 14:56:05 owner kernel: [   13.200812] TCP reno registered
Sep  2 14:56:05 owner kernel: [   13.210610] checking if image is initramfs... it is
Sep  2 14:56:05 owner kernel: [   13.825821] Freeing initrd memory: 6782k freed
Sep  2 14:56:05 owner kernel: [   13.826007] Simple Boot Flag at 0x38 set to 0x1
Sep  2 14:56:05 owner kernel: [   13.826266] audit: initializing netlink socket (disabled)
Sep  2 14:56:05 owner kernel: [   13.826281] audit(1188762939.372:1): initialized
Sep  2 14:56:05 owner kernel: [   13.826344] highmem bounce pool size: 64 pages
Sep  2 14:56:05 owner kernel: [   13.826425] VFS: Disk quotas dquot_6.5.1
Sep  2 14:56:05 owner kernel: [   13.826448] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  2 14:56:05 owner kernel: [   13.826505] io scheduler noop registered
Sep  2 14:56:05 owner kernel: [   13.826508] io scheduler anticipatory registered
Sep  2 14:56:05 owner kernel: [   13.826510] io scheduler deadline registered
Sep  2 14:56:05 owner kernel: [   13.826524] io scheduler cfq registered (default)
Sep  2 14:56:05 owner kernel: [   14.261112] isapnp: Scanning for PnP cards...
Sep  2 14:56:05 owner kernel: [   14.613985] isapnp: No Plug & Play device found
Sep  2 14:56:05 owner kernel: [   14.649750] Real Time Clock Driver v1.12ac
Sep  2 14:56:05 owner kernel: [   14.649789] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  2 14:56:05 owner kernel: [   14.650778] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 14:56:05 owner kernel: [   14.650786] ACPI: PCI interrupt for device 0000:00:02.6 disabled
Sep  2 14:56:05 owner kernel: [   14.650854] mice: PS/2 mouse device common for all mice
Sep  2 14:56:05 owner kernel: [   14.651288] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  2 14:56:05 owner kernel: [   14.651532] input: Macintosh mouse button emulation as /class/input/input0
Sep  2 14:56:05 owner kernel: [   14.651564] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep  2 14:56:05 owner kernel: [   14.651569] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep  2 14:56:05 owner kernel: [   14.651774] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  2 14:56:05 owner kernel: [   14.655489] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  2 14:56:05 owner kernel: [   14.655497] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  2 14:56:05 owner kernel: [   14.655655] EISA: Probing bus 0 at eisa.0
Sep  2 14:56:05 owner kernel: [   14.655664] Cannot allocate resource for EISA slot 1
Sep  2 14:56:05 owner kernel: [   14.655667] Cannot allocate resource for EISA slot 2
Sep  2 14:56:05 owner kernel: [   14.655685] Cannot allocate resource for EISA slot 8
Sep  2 14:56:05 owner kernel: [   14.655687] EISA: Detected 0 cards.
Sep  2 14:56:05 owner kernel: [   14.685734] TCP cubic registered
Sep  2 14:56:05 owner kernel: [   14.685743] NET: Registered protocol family 1
Sep  2 14:56:05 owner kernel: [   14.685768] Using IPI No-Shortcut mode
Sep  2 14:56:05 owner kernel: [   14.685831] ACPI: (supports S0 S3 S4 S5)
Sep  2 14:56:05 owner kernel: [   14.685865]   Magic number: 7:75:950
Sep  2 14:56:05 owner kernel: [   14.685885]   hash matches device ttya5
Sep  2 14:56:05 owner kernel: [   14.685976]   hash matches device tty7
Sep  2 14:56:05 owner kernel: [   14.686316] Freeing unused kernel memory: 328k freed
Sep  2 14:56:05 owner kernel: [   14.688295] Time: tsc clocksource has been installed.
Sep  2 14:56:05 owner kernel: [   14.702843] input: AT Translated Set 2 keyboard as /class/input/input1
Sep  2 14:56:05 owner kernel: [   15.959603] Capability LSM initialized
Sep  2 14:56:05 owner kernel: [   16.007855] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 14:56:05 owner kernel: [   16.011504] ACPI: Thermal Zone [THRM] (49 C)
Sep  2 14:56:05 owner kernel: [   16.693084] SIS5513: IDE controller at PCI slot 0000:00:02.5
Sep  2 14:56:05 owner kernel: [   16.693103] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 18
Sep  2 14:56:05 owner kernel: [   16.693112] SIS5513: chipset revision 0
Sep  2 14:56:05 owner kernel: [   16.693114] SIS5513: not 100%% native mode: will probe irqs later
Sep  2 14:56:05 owner kernel: [   16.693127] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
Sep  2 14:56:05 owner kernel: [   16.693140]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
Sep  2 14:56:05 owner kernel: [   16.693152]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
Sep  2 14:56:05 owner kernel: [   16.729881] usbcore: registered new interface driver usbfs
Sep  2 14:56:05 owner kernel: [   16.729904] usbcore: registered new interface driver hub
Sep  2 14:56:05 owner kernel: [   16.729923] usbcore: registered new device driver usb
Sep  2 14:56:05 owner kernel: [   16.762404] sis900.c: v1.08.10 Apr. 2 2006
Sep  2 14:56:05 owner kernel: [    3.924000] Time: acpi_pm clocksource has been installed.
Sep  2 14:56:05 owner kernel: [    3.996000] hda: TOSHIBA MK6025GAS, ATA DISK drive
Sep  2 14:56:05 owner kernel: [    4.668000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep  2 14:56:05 owner kernel: [    5.456000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
Sep  2 14:56:05 owner kernel: [    6.128000] ide1 at 0x170-0x177,0x376 on irq 15
Sep  2 14:56:05 owner kernel: [    6.136000] SCSI subsystem initialized
Sep  2 14:56:05 owner kernel: [    6.148000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 19
Sep  2 14:56:05 owner kernel: [    6.148000] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep  2 14:56:05 owner kernel: [    6.148000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Sep  2 14:56:05 owner kernel: [    6.148000] ohci_hcd 0000:00:03.0: irq 19, io mem 0xe2002000
Sep  2 14:56:05 owner kernel: [    6.160000] hda: max request size: 128KiB
Sep  2 14:56:05 owner kernel: [    6.172000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
Sep  2 14:56:05 owner kernel: [    6.176000] hda: cache flushes supported
Sep  2 14:56:05 owner kernel: [    6.176000]  hda:<6>usb usb1: configuration #1 chosen from 1 choice
Sep  2 14:56:05 owner kernel: [    6.204000] hub 1-0:1.0: USB hub found
Sep  2 14:56:05 owner kernel: [    6.204000] hub 1-0:1.0: 3 ports detected
Sep  2 14:56:05 owner kernel: [    6.224000]  hda1 hda2 < hda5 >
Sep  2 14:56:05 owner kernel: [    6.268000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Sep  2 14:56:05 owner kernel: [    6.268000] Uniform CD-ROM driver Revision: 3.20
Sep  2 14:56:05 owner kernel: [    6.308000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 20
Sep  2 14:56:05 owner kernel: [    6.308000] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep  2 14:56:05 owner kernel: [    6.308000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Sep  2 14:56:05 owner kernel: [    6.308000] ohci_hcd 0000:00:03.1: irq 20, io mem 0xe2003000
Sep  2 14:56:05 owner kernel: [    6.364000] usb usb2: configuration #1 chosen from 1 choice
Sep  2 14:56:05 owner kernel: [    6.364000] hub 2-0:1.0: USB hub found
Sep  2 14:56:05 owner kernel: [    6.364000] hub 2-0:1.0: 3 ports detected
Sep  2 14:56:05 owner kernel: [    6.468000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 21
Sep  2 14:56:05 owner kernel: [    6.468000] ehci_hcd 0000:00:03.2: EHCI Host Controller
Sep  2 14:56:05 owner kernel: [    6.468000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Sep  2 14:56:05 owner kernel: [    6.468000] ehci_hcd 0000:00:03.2: irq 21, io mem 0xe2004000
Sep  2 14:56:05 owner kernel: [    6.468000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  2 14:56:05 owner kernel: [    6.468000] usb usb3: configuration #1 chosen from 1 choice
Sep  2 14:56:05 owner kernel: [    6.468000] hub 3-0:1.0: USB hub found
Sep  2 14:56:05 owner kernel: [    6.468000] hub 3-0:1.0: 6 ports detected
Sep  2 14:56:05 owner kernel: [    6.572000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Sep  2 14:56:05 owner kernel: [    6.576000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Sep  2 14:56:05 owner kernel: [    6.580000] 0000:00:04.0: Using transceiver found at address 13 as default
Sep  2 14:56:05 owner kernel: [    6.580000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 16, 00:c0:9f:c1:44:ea.
Sep  2 14:56:05 owner kernel: [    6.612000] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  2 14:56:05 owner kernel: [    6.612000] EXT3-fs: write access will be enabled during recovery.
Sep  2 14:56:05 owner kernel: [    7.128000] kjournald starting.  Commit interval 5 seconds
Sep  2 14:56:05 owner kernel: [    7.128000] EXT3-fs: recovery complete.
Sep  2 14:56:05 owner kernel: [    7.144000] EXT3-fs: mounted filesystem with ordered data mode.
Sep  2 14:56:05 owner kernel: [    7.156000] usb 1-2: new low speed USB device using ohci_hcd and address 3
Sep  2 14:56:05 owner kernel: [    7.364000] usb 1-2: configuration #1 chosen from 1 choice
Sep  2 14:56:05 owner kernel: [   21.216000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  2 14:56:05 owner kernel: [   21.220000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  2 14:56:05 owner kernel: [   21.548000] Linux agpgart interface v0.102 (c) Dave Jones
Sep  2 14:56:05 owner kernel: [   21.604000] agpgart: Detected AGP bridge 0
Sep  2 14:56:05 owner kernel: [   21.608000] agpgart: AGP aperture is 32M @ 0xe0000000
Sep  2 14:56:05 owner kernel: [   21.632000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
Sep  2 14:56:05 owner kernel: [   21.632000] Yenta: Using CSCINT to route CSC interrupts to PCI
Sep  2 14:56:05 owner kernel: [   21.632000] Yenta: Routing CardBus interrupts to PCI
Sep  2 14:56:05 owner kernel: [   21.632000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
Sep  2 14:56:05 owner kernel: [   21.864000] Yenta: ISA IRQ mask 0x06f8, PCI irq 16
Sep  2 14:56:05 owner kernel: [   21.864000] Socket status: 30000006
Sep  2 14:56:05 owner kernel: [   21.968000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep  2 14:56:05 owner kernel: [   21.968000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep  2 14:56:05 owner kernel: [   22.120000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
Sep  2 14:56:05 owner kernel: [   22.208000] bcm43xx driver
Sep  2 14:56:05 owner kernel: [   22.208000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  2 14:56:05 owner kernel: [   22.224000] input: PC Speaker as /class/input/input2
Sep  2 14:56:05 owner kernel: [   22.412000] usbcore: registered new interface driver hiddev
Sep  2 14:56:05 owner kernel: [   22.592000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
Sep  2 14:56:05 owner kernel: [   22.608000] input: HID 1241:1166 as /class/input/input3
Sep  2 14:56:05 owner kernel: [   22.608000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:03.0-2
Sep  2 14:56:05 owner kernel: [   22.608000] usbcore: registered new interface driver usbhid
Sep  2 14:56:05 owner kernel: [   22.608000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Sep  2 14:56:05 owner kernel: [   22.696000] cs: IO port probe 0x100-0x3af: clean.
Sep  2 14:56:05 owner kernel: [   22.696000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
Sep  2 14:56:05 owner kernel: [   22.696000] cs: IO port probe 0x820-0x8ff: clean.
Sep  2 14:56:05 owner kernel: [   22.696000] cs: IO port probe 0xc00-0xcf7: clean.
Sep  2 14:56:05 owner kernel: [   22.700000] cs: IO port probe 0xa00-0xaff: clean.
Sep  2 14:56:05 owner kernel: [   22.840000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Sep  2 14:56:05 owner kernel: [   22.880000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Sep  2 14:56:05 owner kernel: [   23.412000] intel8x0_measure_ac97_clock: measured 55463 usecs
Sep  2 14:56:05 owner kernel: [   23.412000] intel8x0: clocking to 48000
Sep  2 14:56:05 owner kernel: [   23.636000] lp: driver loaded but no devices found
Sep  2 14:56:05 owner kernel: [   23.708000] Adding 2441840k swap on /dev/disk/by-uuid/ed70067a-bce9-4fb6-907f-2c4c81db4df4.  Priority:-1 extents:1 across:2441840k
Sep  2 14:56:05 owner kernel: [   23.848000] EXT3 FS on hda1, internal journal
Sep  2 14:56:05 owner kernel: [   24.584000] ACPI: Battery Slot [BAT1] (battery present)
Sep  2 14:56:05 owner kernel: [   24.628000] ACPI: AC Adapter [ACAD] (on-line)
Sep  2 14:56:05 owner kernel: [   24.672000] No dock devices found.
Sep  2 14:56:05 owner kernel: [   24.740000] Using specific hotkey driver
Sep  2 14:56:05 owner kernel: [   24.844000] input: Power Button (FF) as /class/input/input5
Sep  2 14:56:05 owner kernel: [   24.848000] ACPI: Power Button (FF) [PWRF]
Sep  2 14:56:05 owner kernel: [   24.884000] input: Lid Switch as /class/input/input6
Sep  2 14:56:05 owner kernel: [   24.892000] ACPI: Lid Switch [LID]
Sep  2 14:56:05 owner kernel: [   24.928000] input: Power Button (CM) as /class/input/input7
Sep  2 14:56:05 owner kernel: [   24.932000] ACPI: Power Button (CM) [PWRB]
Sep  2 14:56:05 owner kernel: [   24.972000] input: Sleep Button (CM) as /class/input/input8
Sep  2 14:56:05 owner kernel: [   24.976000] ACPI: Sleep Button (CM) [SLPB]
Sep  2 14:56:05 owner kernel: [   25.068000] pcc_acpi: loading...
Sep  2 14:56:05 owner kernel: [   25.344000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
Sep  2 14:56:05 owner kernel: [   25.344000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
Sep  2 14:56:05 owner kernel: [   25.344000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
Sep  2 14:56:05 owner kernel: [   25.344000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
Sep  2 14:56:07 owner kernel: [   28.288000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:56:07 owner kernel: [   28.304000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:56:07 owner kernel: [   28.336000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:56:07 owner dhcdbd: Started up.
Sep  2 14:56:09 owner kernel: [   30.572000] eth1: Media Link On 10mbps half-duplex 
Sep  2 14:56:09 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  2 14:56:10 owner kernel: [   31.096000] ppdev: user-space parallel port driver
Sep  2 14:56:11 owner hpiod: 1.7.3 accepting connections at 2208... 
Sep  2 14:56:12 owner kernel: [   33.080000] apm: BIOS not found.
Sep  2 14:56:12 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Sep  2 14:56:12 owner kernel: [   33.388000] Bluetooth: Core ver 2.11
Sep  2 14:56:12 owner kernel: [   33.388000] NET: Registered protocol family 31
Sep  2 14:56:12 owner kernel: [   33.388000] Bluetooth: HCI device and connection manager initialized
Sep  2 14:56:12 owner kernel: [   33.388000] Bluetooth: HCI socket layer initialized
Sep  2 14:56:12 owner kernel: [   33.428000] Bluetooth: L2CAP ver 2.8
Sep  2 14:56:12 owner kernel: [   33.428000] Bluetooth: L2CAP socket layer initialized
Sep  2 14:56:12 owner kernel: [   33.472000] Bluetooth: RFCOMM socket layer initialized
Sep  2 14:56:12 owner kernel: [   33.472000] Bluetooth: RFCOMM TTY layer initialized
Sep  2 14:56:12 owner kernel: [   33.472000] Bluetooth: RFCOMM ver 1.8
Sep  2 14:56:14 owner kernel: [   35.492000] NET: Registered protocol family 17
Sep  2 14:56:18 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep  2 14:56:18 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Sep  2 14:56:18 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep  2 14:56:18 owner dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep  2 14:56:19 owner kernel: [   40.336000] NET: Registered protocol family 10
Sep  2 14:56:19 owner kernel: [   40.336000] lo: Disabled Privacy Extensions
Sep  2 14:56:21 owner gconfd (owner-4999): starting (version 2.18.0.1), pid 4999 user 'owner'
Sep  2 14:56:21 owner gconfd (owner-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 14:56:21 owner gconfd (owner-4999): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 1
Sep  2 14:56:21 owner gconfd (owner-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 14:56:21 owner gconfd (owner-4999): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 14:56:21 owner gconfd (owner-4999): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 14:56:31 owner gconfd (owner-4999): Resolved address "xml:readwrite:/home/owner/.gconf" to a writable configuration source at position 0
Sep  2 14:56:35 owner kernel: [   55.888000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:57:05 owner kernel: [   85.884000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:57:33 owner kernel: [  114.028000] usb 3-6: new high speed USB device using ehci_hcd and address 3
Sep  2 14:57:33 owner kernel: [  114.164000] usb 3-6: configuration #1 chosen from 1 choice
Sep  2 14:57:33 owner kernel: [  114.304000] usbcore: registered new interface driver libusual
Sep  2 14:57:33 owner kernel: [  114.316000] Initializing USB Mass Storage driver...
Sep  2 14:57:33 owner kernel: [  114.316000] scsi0 : SCSI emulation for USB Mass Storage devices
Sep  2 14:57:33 owner kernel: [  114.316000] usbcore: registered new interface driver usb-storage
Sep  2 14:57:33 owner kernel: [  114.316000] USB Mass Storage support registered.
Sep  2 14:57:35 owner kernel: [  115.884000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Sep  2 14:57:38 owner kernel: [  119.316000] scsi 0:0:0:0: Direct-Access     Memorex  Flashdrive 501B  PMAP PQ: 0 ANSI: 0 CCS
Sep  2 14:57:38 owner kernel: [  119.356000] SCSI device sda: 248096 512-byte hdwr sectors (127 MB)
Sep  2 14:57:38 owner kernel: [  119.356000] sda: Write Protect is off
Sep  2 14:57:38 owner kernel: [  119.360000] SCSI device sda: 248096 512-byte hdwr sectors (127 MB)
Sep  2 14:57:38 owner kernel: [  119.360000] sda: Write Protect is off
Sep  2 14:57:38 owner kernel: [  119.360000]  sda: sda1
Sep  2 14:57:38 owner kernel: [  119.364000] sd 0:0:0:0: Attached scsi removable disk sda
Sep  2 14:57:38 owner kernel: [  119.472000] sd 0:0:0:0: Attached scsi generic sg0 type 0
```

Anybody?

---

### Post by betzelelgalut on 2007-09-02
i was reading online that there appears to be some kind of issue with the battery on your portable and ubuntu's power saveing settings. .... i'll keep looking into it. :guitar: in particular this thread looks like it is issue w/ power saveing settings. 
Sep  2 08:52:36 owner kernel: [  416.560000] _**ACPI Exception **_(acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
you might want to try and go intot he bios and disable ACPI power saving settings and see if that makes a diffeance. i know that you have installed xp on it - try teh live cd see if it works.

---

