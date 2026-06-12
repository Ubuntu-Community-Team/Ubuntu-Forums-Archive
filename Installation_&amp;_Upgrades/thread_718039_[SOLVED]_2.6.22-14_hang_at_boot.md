---
title: "[SOLVED] 2.6.22-14 hang at boot"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by Obi-Wan-YJ on 2008-03-07
I'm having problems with 2.6.22-14 (current Gutsy kernel) hanging at boot.  Here's the long story:

Originally a dual-Pentium3 system running Feisty (2.6.20-16-generic).  All worked well.  After upgrading to Gutsy (2.6.22-14-generic or -i386), I get the grub menu, then it flashes about 6 lines of initrd lines for a fraction of a second (too fast to read), then the screen goes black.  The monitor is still getting a signal, but it's all black.  I let it sit for upwards of 30 minutes, and it never comes back.  I have to give the machine the finger to reboot it & select a different kernel.

This week, I upgraded to a new Athlon 64 X2 5000+, and the same behavior persists.  I'm still using the same hard drive and 32-bit OS install as before.  Booting off 2.6.20-16-generic still works fine.

Here's the default 22-14 kernel line from grub:

kernel      /vmlinuz-2.6.22-14-generic root=UUID=03de0031-862f-492e-8b07-d08b5caf0614 ro vga=788

I've also tried adding various combinations of irqpool, nosmp, and noacpi, but to no avail.  What's going on here?  Why won't it boot the gutsy kernel?

Here's some info from the new AMD hardware and the 2.6.20 kernel.  Sorry about the length of dmesg.

k# lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02)
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

# lsmod
Module                  Size  Used by
af_packet              23816  2 
binfmt_misc            12680  1 
capability              5896  0 
nfsd                  218992  13 
exportfs                6912  1 nfsd
lockd                  64904  2 nfsd
sunrpc                161340  8 nfsd,lockd
ppdev                  10116  0 
ipv6                  269088  22 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
dock                   10268  0 
button                  8720  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
battery                10756  0 
ide_generic             2304  0 [permanent]
fuse                   46612  1 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sbp2                   23812  0 
lp                     12452  0 
snd_hda_intel          21912  0 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
agpgart                35400  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
xpad                    9988  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
pcspkr                  4224  0 
k8temp                  6656  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
serio_raw               7940  0 
i2c_nforce2             6784  0 
i2c_core               22656  2 i2c_ec,i2c_nforce2
evdev                  11008  3 
tsdev                   8768  0 
ext3                  133128  3 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_disk               17024  6 
sg                     36252  0 
sd_mod                 23428  2 
pata_jmicron            7808  0 
sata_nv                20868  0 
usbhid                 26592  1 
hid                    27392  1 usbhid
ahci                   22020  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
pata_pdc2027x          11396  4 
floppy                 59524  0 
raid10                 26240  0 
ohci_hcd               22532  0 
ehci_hcd               34188  0 
ata_generic             9092  0 
amd74xx                15260  0 [permanent]
forcedeth              46728  0 
libata                125720  5 pata_jmicron,sata_nv,ahci,pata_pdc2027x,ata_generic
scsi_mod              142348  5 sr_mod,sbp2,sg,sd_mod,libata
generic                 5124  0 [permanent]
usbcore               134280  6 xpad,usbhid,ohci_hcd,ehci_hcd
raid456               126480  0 
xor                    16648  1 raid456
raid1                  25600  0 
raid0                   9600  0 
multipath               9856  0 
linear                  7296  0 
md_mod                 79764  6 raid10,raid456,raid1,raid0,multipath,linear
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
dm_mod                 59084  8 
commoncap               8192  1 capability
vesafb                  9220  1 
fbcon                  42656  72 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit

# dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Dec 18 05:45:12 UTC 2007 (Ubuntu 2.6.20-16.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009e000 end: 000000000009e000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009e000 size: 0000000000002000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 00000000dfde0000 end: 00000000dfee0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000dfee0000 size: 0000000000003000 end: 00000000dfee3000 type: 4
[    0.000000] copy_e820_map() start: 00000000dfee3000 size: 000000000000d000 end: 00000000dfef0000 type: 3
[    0.000000] copy_e820_map() start: 00000000dfef0000 size: 0000000000010000 end: 00000000dff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0000000 size: 0000000004000000 end: 00000000f4000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000] copy_e820_map() start: 0000000100000000 size: 0000000020000000 end: 0000000120000000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000dfee0000 - 00000000dfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a PAE enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5bd0
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 6400 pages used for memmap
[    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v002 Nvidia                                ) @ 0x000f7c80
[    0.000000] ACPI: XSDT (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0xdfee3100
[    0.000000] ACPI: FADT (v003 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0xdfeead00
[    0.000000] ACPI: HPET (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000098) @ 0xdfeeaf00
[    0.000000] ACPI: MCFG (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0xdfeeaf80
[    0.000000] ACPI: MADT (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0xdfeeae40
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
[    0.000000] Detected 2612.023 MHz processor.
[   38.193097] Built 1 zonelists.  Total pages: 1040384
[   38.193099] Kernel command line: root=UUID=03de0031-862f-492e-8b07-d08b5caf0614 ro vga=788
[   38.193194] mapped APIC to ffffd000 (fee00000)
[   38.193196] mapped IOAPIC to ffffc000 (fec00000)
[   38.193198] Enabling fast FPU save and restore... done.
[   38.193200] Enabling unmasked SIMD FPU exception support... done.
[   38.193204] Initializing CPU#0
[   38.193237] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   38.193259] spurious 8259A interrupt: IRQ7.
[   38.193276] Console: colour dummy device 80x25
[   38.193572] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   38.193842] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   38.300511] Memory: 3622168k/4194304k available (1993k kernel code, 45440k reserved, 900k data, 328k init, 2751360k highmem)
[   38.300524] virtual kernel memory layout:
[   38.300524]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   38.300525]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   38.300526]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   38.300527]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   38.300528]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   38.300529]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[   38.300530]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[   38.300540] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   38.300640] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[   38.300645] hpet0: 3 32-bit timers, 25000000 Hz
[   38.301653] Using HPET for base-timer
[   38.380636] Calibrating delay using timer specific routine.. 5228.05 BogoMIPS (lpj=10456114)
[   38.380666] Security Framework v1.0.0 initialized
[   38.380672] SELinux:  Disabled at boot.
[   38.380682] Mount-cache hash table entries: 512
[   38.380768] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[   38.380774] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.380777] CPU: L2 Cache: 512K (64 bytes/line)
[   38.380780] CPU 0(2) -> Core 0
[   38.380782] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[   38.380789] Compat vDSO mapped to ffffe000.
[   38.380793] Remapping vsyscall page to ffffe000
[   38.380800] Checking 'hlt' instruction... OK.
[   38.396718] SMP alternatives: switching to UP code
[   38.396955] Early unpacking initramfs... done
[   38.649373] ACPI: Core revision 20060707
[   38.655559] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   38.659509] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[   38.659529] SMP alternatives: switching to SMP code
[   38.659569] Booting processor 1/1 eip 3000
[   38.669803] Initializing CPU#1
[   38.748650] Calibrating delay using timer specific routine.. 5224.15 BogoMIPS (lpj=10448319)
[   38.748655] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[   38.748660] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.748662] CPU: L2 Cache: 512K (64 bytes/line)
[   38.748664] CPU 1(2) -> Core 1
[   38.748665] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[   38.748741] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[   38.748757] Total of 2 processors activated (10452.21 BogoMIPS).
[   38.748987] ENABLING IO-APIC IRQs
[   38.749183] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   38.896592] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -22 usecs TSC skew, fixed it up.
[    0.000004] CPU#1 had 22 usecs TSC skew, fixed it up.
[    0.004000] Brought up 2 CPUs
[    0.053299] migration_cost=132
[    0.053474] Booting paravirtualized kernel on bare hardware
[    0.053531] Time:  5:17:20  Date: 02/07/108
[    0.053554] NET: Registered protocol family 16
[    0.053613] EISA bus registered
[    0.053617] ACPI: bus type pci registered
[    0.084343] PCI: PCI BIOS revision 3.00 entry at 0xf2380, last bus=3
[    0.084345] PCI: Using configuration type 1
[    0.084348] Setting up standard PCI resources
[    0.098034] ACPI: Interpreter enabled
[    0.098041] ACPI: Using IOAPIC for interrupt routing
[    0.098544] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.098549] PCI: Probing PCI hardware (bus 00)
[    0.099237] PCI: Transparent bridge - 0000:00:06.0
[    0.099428] Boot video device is 0000:03:00.0
[    0.099468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.143244] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.146902] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147170] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147437] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[    0.147702] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147966] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.148239] ACPI: PCI Interrupt Link [LNK6] (IRQs *5 7 9 10 11 14 15)
[    0.148504] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[    0.148769] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.149034] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.149301] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.149566] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.149832] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 9 *10 11 14 15)
[    0.150097] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.150361] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.150630] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[    0.150895] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.151160] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151430] ACPI: PCI Interrupt Link [LSID] (IRQs *5 7 9 10 11 14 15)
[    0.151696] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.151962] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 10 *11 14 15)
[    0.152297] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.152622] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.152945] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.153268] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.153592] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.153916] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.154241] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.154566] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.154891] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.155221] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.155546] ACPI: PCI Interrupt Link [AMC1] (IRQs 20 21 22 23) *0, disabled.
[    0.155874] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.156205] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.156531] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.156856] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.157183] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.157510] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.157835] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.158162] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.158491] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0, disabled.
[    0.158692] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.158700] pnp: PnP ACPI init
[    0.163463] pnp: PnP ACPI: found 13 devices
[    0.163467] PnPBIOS: Disabled by ACPI PNP
[    0.163502] PCI: Using ACPI for IRQ routing
[    0.163506] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.204206] NET: Registered protocol family 8
[    0.204208] NET: Registered protocol family 20
[    0.204546] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[    0.204550] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.204553] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.204556] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[    0.204559] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.204562] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.204757] PCI: Bridge: 0000:00:06.0
[    0.204760]   IO window: 8000-9fff
[    0.204763]   MEM window: fde00000-fdefffff
[    0.204766]   PREFETCH window: f4000000-f40fffff
[    0.204770] PCI: Bridge: 0000:00:0e.0
[    0.204772]   IO window: 6000-7fff
[    0.204775]   MEM window: fdd00000-fddfffff
[    0.204778]   PREFETCH window: disabled.
[    0.204781] PCI: Bridge: 0000:00:0f.0
[    0.204783]   IO window: 5000-5fff
[    0.204786]   MEM window: fa000000-fcffffff
[    0.204789]   PREFETCH window: e0000000-efffffff
[    0.204796] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.204802] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.204806] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    0.204830] NET: Registered protocol family 2
[    0.248016] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.248122] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.248662] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.248934] TCP: Hash tables configured (established 131072 bind 65536)
[    0.248938] TCP reno registered
[    0.264058] checking if image is initramfs... it is
[    0.760999] Freeing initrd memory: 8092k freed
[    1.252000] audit: initializing netlink socket (disabled)
[    1.252000] audit(1204867040.436:1): initialized
[    1.252000] highmem bounce pool size: 64 pages
[    1.252000] VFS: Disk quotas dquot_6.5.1
[    1.252000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.252000] io scheduler noop registered
[    1.252000] io scheduler anticipatory registered
[    1.252000] io scheduler deadline registered
[    1.252000] io scheduler cfq registered (default)
[    1.272000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    1.272000] assign_interrupt_mode Found MSI capability
[    1.272000] Allocate Port Service[0000:00:0e.0:pcie00]
[    1.272000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    1.272000] assign_interrupt_mode Found MSI capability
[    1.272000] Allocate Port Service[0000:00:0f.0:pcie00]
[    1.272000] isapnp: Scanning for PnP cards...
[    1.624000] isapnp: No Plug & Play device found
[    1.636000] Real Time Clock Driver v1.12ac
[    1.636000] hpet_resources: 0xfefff000 is busy
[    1.636000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.636000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.640000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.640000] mice: PS/2 mouse device common for all mice
[    1.640000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.640000] input: Macintosh mouse button emulation as /class/input/input0
[    1.640000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.640000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.640000] PNP: No PS/2 controller found. Probing ports directly.
[    1.640000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.640000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.640000] EISA: Probing bus 0 at eisa.0
[    1.640000] Cannot allocate resource for EISA slot 1
[    1.640000] Cannot allocate resource for EISA slot 5
[    1.640000] Cannot allocate resource for EISA slot 6
[    1.640000] Cannot allocate resource for EISA slot 7
[    1.640000] Cannot allocate resource for EISA slot 8
[    1.640000] EISA: Detected 0 cards.
[    1.668000] TCP cubic registered
[    1.668000] NET: Registered protocol family 1
[    1.668000] Starting balanced_irq
[    1.668000] Using IPI No-Shortcut mode
[    1.672000] Time: hpet clocksource has been installed.
[    1.672000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.672000]   Magic number: 0:752:263
[    1.672000]   hash matches device ttyx5
[    1.672000] Freeing unused kernel memory: 328k freed
[    1.744000] vesafb: framebuffer at 0xe0000000, mapped to 0xf8880000, using 1875k, total 262144k
[    1.744000] vesafb: mode is 800x600x16, linelength=1600, pages=2
[    1.744000] vesafb: protected mode interface info at c000:c2e0
[    1.744000] vesafb: pmi: set display start = c00cc316, set palette = c00cc380
[    1.744000] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    1.744000] vesafb: scrolling: redraw
[    1.744000] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    1.748000] Console: switching to colour frame buffer device 100x37
[    1.756000] fb0: VESA VGA frame buffer device
[    1.836000] Capability LSM initialized
[    1.848000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[    1.868000] ACPI: Fan [FAN] (on)
[    1.872000] ACPI: Thermal Zone [THRM] (40 C)
[    1.936000] md: linear personality registered for level -1
[    1.944000] md: multipath personality registered for level -4
[    1.952000] md: raid0 personality registered for level 0
[    1.960000] md: raid1 personality registered for level 1
[    1.968000] raid5: automatically using best checksumming function: pIII_sse
[    1.992000]    pIII_sse  :  7709.000 MB/sec
[    1.992000] raid5: using function: pIII_sse (7709.000 MB/sec)
[    2.064000] raid6: int32x1   1112 MB/s
[    2.132000] raid6: int32x2   1132 MB/s
[    2.200000] raid6: int32x4    947 MB/s
[    2.268000] raid6: int32x8    699 MB/s
[    2.336000] raid6: mmxx1     2120 MB/s
[    2.404000] raid6: mmxx2     3842 MB/s
[    2.472000] raid6: sse1x1    2082 MB/s
[    2.540000] raid6: sse1x2    3472 MB/s
[    2.608000] raid6: sse2x1    3596 MB/s
[    2.676000] raid6: sse2x2    4889 MB/s
[    2.676000] raid6: using algorithm sse2x2 (4889 MB/s)
[    2.680000] md: raid6 personality registered for level 6
[    2.680000] md: raid5 personality registered for level 5
[    2.684000] md: raid4 personality registered for level 4
[    2.688000] SCSI subsystem initialized
[    2.700000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[    2.704000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    2.704000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[    2.704000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    2.704000] forcedeth: using HIGHDMA
[    2.704000] libata version 2.20 loaded.
[    2.712000] usbcore: registered new interface driver usbfs
[    2.712000] usbcore: registered new interface driver hub
[    2.712000] usbcore: registered new device driver usb
[    2.728000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.736000] md: raid10 personality registered for level 10
[    2.772000] Floppy drive(s): fd0 is 1.44M
[    2.788000] ieee1394: Initialized config rom entry `ip1394'
[    2.800000] FDC 0 is a post-1991 82077
[    3.228000] eth0: forcedeth.c: subsystem: 01043:8239 bound to 0000:00:08.0
[    3.228000] ACPI: PCI Interrupt Link [AMC1] enabled at IRQ 22
[    3.232000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [AMC1] -> GSI 22 (level, low) -> IRQ 17
[    3.232000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    3.232000] forcedeth: using HIGHDMA
[    3.760000] eth1: forcedeth.c: subsystem: 01043:8239 bound to 0000:00:09.0
[    3.760000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    3.764000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 18
[    3.764000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    3.764000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.768000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    3.772000] ohci_hcd 0000:00:02.0: irq 18, io mem 0xfe02f000
[    3.832000] usb usb1: configuration #1 chosen from 1 choice
[    3.836000] hub 1-0:1.0: USB hub found
[    3.836000] hub 1-0:1.0: 10 ports detected
[    3.948000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    3.948000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[    3.956000] NFORCE-MCP55: IDE controller at PCI slot 0000:00:04.0
[    3.960000] NFORCE-MCP55: chipset revision 161
[    3.964000] NFORCE-MCP55: not 100% native mode: will probe irqs later
[    3.964000] NFORCE-MCP55: BIOS didn't set cable bits correctly. Enabling workaround.
[    3.968000] NFORCE-MCP55: 0000:00:04.0 (rev a1) UDMA133 controller
[    3.972000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[    3.972000] Probing IDE interface ide0...
[    4.004000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.256000] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    4.268000] hda: ST3120026A, ATA DISK drive
[    4.552000] hdb: ST3750640A, ATA DISK drive
[    4.612000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.620000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[    4.620000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 20
[    4.624000] usb 1-2: configuration #1 chosen from 1 choice
[    4.628000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    4.628000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.632000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    4.636000] ehci_hcd 0000:00:02.1: debug port 1
[    4.640000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    4.640000] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfe02e000
[    4.640000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.644000] usb usb2: configuration #1 chosen from 1 choice
[    4.648000] hub 2-0:1.0: USB hub found
[    4.652000] hub 2-0:1.0: 10 ports detected
[    4.760000] ahci 0000:02:00.0: version 2.1
[    4.760000] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[    4.764000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 21
[    4.920000] usbcore: registered new interface driver hiddev
[    4.920000] usb 1-2: USB disconnect, address 2
[    5.288000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00000147c3]
[    5.604000] usbcore: registered new interface driver usbhid
[    5.608000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.768000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    5.768000] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    5.772000] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    5.776000] ata1: SATA max UDMA/133 cmd 0xf884c100 ctl 0x00000000 bmdma 0x00000000 irq 21
[    5.780000] ata2: SATA max UDMA/133 cmd 0xf884c180 ctl 0x00000000 bmdma 0x00000000 irq 21
[    5.780000] scsi0 : ahci
[    5.908000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    6.096000] ata1: SATA link down (SStatus 0 SControl 300)
[    6.100000] scsi1 : ahci
[    6.288000] usb 1-2: configuration #1 chosen from 1 choice
[    6.416000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.420000] pata_pdc2027x 0000:01:08.0: version 0.8
[    6.420000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    6.424000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 22
[    6.528000] pata_pdc2027x 0000:01:08.0: PLL input clock 16610 kHz
[    6.560000] ata3: PATA max UDMA/133 cmd 0xf8c197c0 ctl 0xf8c19fda bmdma 0xf8c19000 irq 22
[    6.564000] ata4: PATA max UDMA/133 cmd 0xf8c195c0 ctl 0xf8c19dda bmdma 0xf8c19008 irq 22
[    6.564000] scsi2 : pata_pdc2027x
[    6.784000] ata3.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[    6.788000] ata3.00: ATA-7: ST3400620A, 3.AAD, max UDMA/100
[    6.788000] ata3.00: 781422768 sectors, multi 16: LBA48 
[    6.852000] ata3.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[    6.852000] ata3.00: configured for UDMA/100
[    6.856000] scsi3 : pata_pdc2027x
[    7.016000] ATA: abnormal status 0x8 on port 0xf8c195df
[    7.020000] scsi 2:0:0:0: Direct-Access     ATA      ST3400620A       3.AA PQ: 0 ANSI: 5
[    7.020000] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[    7.024000] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[    7.024000] sata_nv 0000:00:05.0: version 3.3
[    7.028000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [APC8] -> GSI 16 (level, low) -> IRQ 21
[    7.028000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    7.028000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 16
[    7.028000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    7.028000] ata5: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001dc00 irq 16
[    7.028000] ata6: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001dc08 irq 16
[    7.028000] scsi4 : sata_nv
[    7.032000] PCI: Setting latency timer of device 0000:02:00.1 to 64
[    7.032000] ata7: PATA max UDMA/100 cmd 0x00017c00 ctl 0x00017802 bmdma 0x00016c00 irq 21
[    7.032000] ata8: PATA max UDMA/100 cmd 0x00017400 ctl 0x00017002 bmdma 0x00016c08 irq 21
[    7.036000] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
[    7.036000] scsi6 : pata_jmicron
[    7.040000] sda: Write Protect is off
[    7.040000] sda: Mode Sense: 00 3a 00 00
[    7.040000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.044000] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
[    7.044000] sda: Write Protect is off
[    7.048000] sda: Mode Sense: 00 3a 00 00
[    7.048000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.052000]  sda: sda1 sda2
[    7.068000] sd 2:0:0:0: Attached scsi disk sda
[    7.076000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    7.196000] scsi7 : pata_jmicron
[    7.340000] ata5: SATA link down (SStatus 0 SControl 300)
[    7.344000] hiddev96: USB HID v1.10 Device [American Power Conversion Back-UPS RS 1000 FW:7.g2 .D USB FW:g2 ] on usb-0000:00:02.0-2
[    7.356000] ATA: abnormal status 0x7F on port 0x000109f7
[    7.356000] scsi5 : sata_nv
[    7.356000] ATA: abnormal status 0x7F on port 0x00017407
[    7.648000] usb 1-3: new low speed USB device using ohci_hcd and address 4
[    7.668000] ata6: SATA link down (SStatus 0 SControl 300)
[    7.684000] ATA: abnormal status 0x7F on port 0x00010977
[    7.688000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    7.688000] ACPI: PCI Interrupt 0000:00:05.1[B] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 17
[    7.692000] PCI: Setting latency timer of device 0000:00:05.1 to 64
[    7.692000] ata9: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001c800 irq 17
[    7.696000] ata10: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001c808 irq 17
[    7.700000] scsi8 : sata_nv
[    7.860000] usb 1-3: configuration #1 chosen from 1 choice
[    7.876000] input: Logitech USB Receiver as /class/input/input1
[    7.880000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-3
[    8.016000] ata9: SATA link down (SStatus 0 SControl 300)
[    8.032000] ATA: abnormal status 0x7F on port 0x000109e7
[    8.036000] scsi9 : sata_nv
[    8.184000] usb 1-4: new full speed USB device using ohci_hcd and address 5
[    8.348000] ata10: SATA link down (SStatus 0 SControl 300)
[    8.364000] ATA: abnormal status 0x7F on port 0x00010967
[    8.368000] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    8.372000] ACPI: PCI Interrupt 0000:00:05.2[C] -> Link [ASA2] -> GSI 21 (level, low) -> IRQ 18
[    8.372000] PCI: Setting latency timer of device 0000:00:05.2 to 64
[    8.372000] ata11: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c002 bmdma 0x0001b400 irq 18
[    8.376000] ata12: SATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001b802 bmdma 0x0001b408 irq 18
[    8.380000] scsi10 : sata_nv
[    8.396000] usb 1-4: configuration #1 chosen from 1 choice
[    8.400000] hub 1-4:1.0: USB hub found
[    8.404000] hub 1-4:1.0: 3 ports detected
[    8.696000] ata11: SATA link down (SStatus 0 SControl 300)
[    8.704000] ATA: abnormal status 0x7F on port 0x0001c407
[    8.708000] scsi11 : sata_nv
[    8.756000] usb 1-4.1: new full speed USB device using ohci_hcd and address 6
[    8.880000] usb 1-4.1: configuration #1 chosen from 1 choice
[    8.892000] input: Chicony  PFU-65 USB Keyboard as /class/input/input2
[    8.896000] input: USB HID v1.00 Keyboard [Chicony  PFU-65 USB Keyboard] on usb-0000:00:02.0-4.1
[    9.024000] ata12: SATA link down (SStatus 0 SControl 300)
[    9.040000] ATA: abnormal status 0x7F on port 0x0001bc07
[    9.052000] hda: max request size: 512KiB
[    9.052000] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[    9.056000] hda: cache flushes supported
[    9.060000]  hda: hda1 hda2 hda3
[    9.072000] hdb: max request size: 512KiB
[    9.120000] hdb: 1465149168 sectors (750156 MB) w/16384KiB Cache, CHS=65535/255/63, UDMA(100)
[    9.144000] hdb: cache flushes supported
[    9.148000]  hdb: hdb1 hdb2
[    9.604000] kjournald starting.  Commit interval 5 seconds
[    9.604000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.508000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   20.512000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   20.808000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.812000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.960000] input: PC Speaker as /class/input/input3
[   21.032000] parport: PnPBIOS parport detected.
[   21.032000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   21.080000] usbcore: registered new interface driver xpad
[   21.080000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   21.200000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.432000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   21.432000] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [AAZA] -> GSI 20 (level, low) -> IRQ 20
[   21.436000] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   21.988000] lp0: using parport0 (interrupt-driven).
[   22.152000] fuse init (API version 7.8)
[   22.192000] Probing IDE interface ide1...
[   22.844000] Adding 2008084k swap on /dev/hdb1.  Priority:1 extents:1 across:2008084k
[   22.852000] Adding 2000052k swap on /dev/hda1.  Priority:3 extents:1 across:2000052k
[   23.152000] EXT3 FS on hda3, internal journal
[   25.116000] kjournald starting.  Commit interval 5 seconds
[   25.116000] EXT3 FS on hda2, internal journal
[   25.116000] EXT3-fs: mounted filesystem with ordered data mode.
[   25.132000] kjournald starting.  Commit interval 5 seconds
[   25.132000] EXT3 FS on sda2, internal journal
[   25.132000] EXT3-fs: mounted filesystem with ordered data mode.
[   28.300000] input: Power Button (FF) as /class/input/input4
[   28.300000] ACPI: Power Button (FF) [PWRF]
[   28.300000] input: Power Button (CM) as /class/input/input5
[   28.300000] ACPI: Power Button (CM) [PWRB]
[   28.336000] Using specific hotkey driver
[   28.380000] No dock devices found.
[   28.416000] ibm_acpi: ec object not found
[   28.552000] pcc_acpi: loading...
[   28.828000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (version 2.00.00)
[   28.828000] powernow-k8: MP systems not supported by PSB BIOS structure
[   28.828000] powernow-k8: MP systems not supported by PSB BIOS structure
[   30.472000] eth3: no link during initialization.
[   32.168000] NET: Registered protocol family 10
[   32.168000] lo: Disabled Privacy Extensions
[   32.168000] ADDRCONF(NETDEV_UP): eth3: link is not ready
[   33.132000] ppdev: user-space parallel port driver
[   37.552000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   37.552000] apm: disabled - APM is not SMP safe.
[   48.660000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   48.920000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   48.936000] NFSD: starting 90-second grace period
[   52.312000] process `snmpd' is using deprecated sysctl (syscall) net.ipv6.neigh.lo.retrans_time; Use net.ipv6.neigh.lo.retrans_time_ms instead.
[   53.948000] Capability LSM initialized
[   59.768000] NET: Registered protocol family 17
[   71.912000] eth2: no IPv6 routers present

---

### Post by Handssolow on 2008-03-07
I'm still unable to boot 2.6.22-14-generic since 5th February and had to drop back to 2.6.20-16-generic. I noticed your Grub kernel line has "vga=788" because I've just read that another Forum member who had a boot problem removed his vga line and was then able to boot. For some reason I have so such reference to vga in my Boot/Grub/Menu.lst file. At bootup, you could try pressing e to edit the vga reference out, press enter then b to boot. If it works you'll need to permanently edit the line later.

---

### Post by Obi-Wan-YJ on 2008-03-08
Hey, that did it!  Thanks!  I should have thought of that myself, since I had a similar problem when installing new RedHat Enterprise Linux 5 machines at work.  It sucks to lose all that great console resolution on my 21" monitor, but I'll do what I have to to make it boot.

---

