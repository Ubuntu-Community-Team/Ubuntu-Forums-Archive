---
title: "CPU Scaling in Gutsy"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by mertle on 2007-10-27
I recently upgraded to Kubuntu Gutsy from Feisty and CPU scaling no longer works. I have a Pentium M 1.60 gHz processor on a Dell 9300 laptop and it's currently stuck at 800 mHz at all times. Speedstep is enabled in the BIOS and I've tried manually editing the scaling files, following numerous CPU scaling HOWTOS, loading/unloading modules by hand, and cpufrequtils... nada. The min and max freq are the same, no matter what I do.

This seems to be an often posted problem, but I've yet to find anything that works to solve it. I know this is a known bug in the Gutsy kernel, but has anyone found a workaround? Some people ound a temporary solution which only works until the next reboot, but even I haven't had that much success.

Will rolling back to an older kernel fix this until a solution is found, or just muck me up further?

$ cpufreq-info:

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
```

/etc/modules:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
i8k
acpi-cpufreq
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace

NOTE: Never needed anything after i8k in Feisty, but I added those just in case.
```

$ lsmod:

```
Module                  Size  Used by
speedstep_lib           6404  0
snd_hda_intel          22680  0
snd_hda_codec         249232  1 snd_hda_intel
hsfusbcd2              66216  0
hsfmc97sis             68248  0
hsfmc97ati             66840  0
hsfmc97ali             73504  0
hsfmc97via             69408  0
hsfmc97ich             71576  0
hsfpcibasic3          109608  0
hsfpcibasic2           67608  0
hsfserial              24612  8 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic3,hsfpcibasic2
hsfengine            1295244  9 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic3,hsfpcibasic2,hsfserial
hsfosspec             105704  13 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic3,hsfpcibasic2,hsfserial,hsfengine
hsfsoar                93904  7 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic2
ipv6                  273892  8
af_packet              24840  2
radeon                125472  2
drm                    83348  3 radeon
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vboxdrv                60208  0
ppdev                  10244  0
sbs                    19592  0
video                  18060  0
ac                      6148  0
container               5504  0
dock                   10656  0
button                  8976  0
battery                11012  0
cpufreq_userspace       5280  0
cpufreq_stats           7232  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9612  1
cpufreq_conservative     8072  0
acpi_cpufreq           10568  0
freq_table              5792  3 cpufreq_stats,cpufreq_ondemand,acpi_cpufreq
i8k                     7320  0
sbp2                   24072  0
parport_pc             37412  0
lp                     12580  0
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0           34972  1
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_usb_audio          81024  1
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_pcm                80388  6 snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            17920  1 snd_usb_audio
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ipw2200               149320  0
snd_rawmidi            25728  2 snd_usb_lib,snd_seq_midi
ieee80211              35656  1 ipw2200
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
ieee80211_crypt         7040  1 ieee80211
joydev                 11328  0
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 41388  0
snd_hwdep              10244  1 snd_usb_audio
snd                    54660  18 snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_hda_intel,snd_intel8x0,snd_pcm
sdhci                  18828  0
pcspkr                  4224  0
mmc_core               28420  1 sdhci
yenta_socket           27532  1
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                39952  0
iTCO_wdt               11940  0
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               8068  0
intel_agp              25620  0
agpgart                35016  2 drm,intel_agp
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
evdev                  11136  5
ext3                  133896  3
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sr_mod                 17828  0
cdrom                  37536  1 sr_mod
sd_mod                 30336  5
ahci                   23300  0
ata_piix               17540  4
ohci1394               36528  0
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0
libata                125168  3 ahci,ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
b44                    28300  0
mii                     6528  1 b44
ehci_hcd               36492  0
uhci_hcd               26640  0
usbcore               138632  7 hsfusbcd2,hsfosspec,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd
thermal                14344  0
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor

```

$ dmesg:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffda000 (usable)
[    0.000000]  BIOS-e820: 000000001ffda000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131034) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131034
[    0.000000]   HighMem    131034 ->   131034
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131034
[    0.000000] On node 0 totalpages: 131034
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125947 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FC9B0 checksum 0
[    0.000000] ACPI: RSDP 000FC9B0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 1FFDA7D3, 0040 (r1 DELL    CPi R   27D50217 ASL        61)
[    0.000000] ACPI: FACP 1FFDB400, 0074 (r1 DELL    CPi R   27D50217 ASL        61)
[    0.000000] ACPI: DSDT 1FFDC000, 25E5 (r1 INT430 SYSFexxx     1001 MSFT  100000E)
[    0.000000] ACPI: FACS 1FFEA800, 0040
[    0.000000] ACPI: APIC 1FFDBC00, 0068 (r1 DELL    CPi R   27D50217 ASL        47)
[    0.000000] ACPI: MCFG 1FFDBBC0, 003E (r16 DELL    CPi R   27D50217 ASL        61)
[    0.000000] ACPI: BOOT 1FFDB7C0, 0028 (r1 DELL    CPi R   27D50217 ASL        61)
[    0.000000] ACPI: SSDT 1FFDABE6, 023E (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
[    0.000000] ACPI: SSDT 1FFDAA0E, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: SSDT 1FFDA813, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Built 1 zonelists.  Total pages: 130011
[    0.000000] Kernel command line: root=UUID=01b43b36-c2f3-464a-bc34-7c365bc81fae ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1596.231 MHz processor.
[    7.102041] Console: colour VGA+ 80x25
[    7.102216] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.102429] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.114458] Memory: 508044k/524136k available (2015k kernel code, 15504k reserved, 916k data, 364k init, 0k highmem)
[    7.114468] virtual kernel memory layout:
[    7.114469]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    7.114471]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.114472]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    7.114474]     lowmem  : 0xc0000000 - 0xdffda000   ( 511 MB)
[    7.114475]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    7.114476]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    7.114478]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    7.114481] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.114519] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.194478] Calibrating delay using timer specific routine.. 3195.66 BogoMIPS (lpj=6391336)
[    7.194503] Security Framework v1.0.0 initialized
[    7.194511] SELinux:  Disabled at boot.
[    7.194525] Mount-cache hash table entries: 512
[    7.194651] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[    7.194663] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.194665] CPU: L2 cache: 2048K
[    7.194668] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[    7.194678] Compat vDSO mapped to ffffe000.
[    7.194689] Checking 'hlt' instruction... OK.
[    7.210562] SMP alternatives: switching to UP code
[    7.210733] Freeing SMP alternatives: 11k freed
[    7.210992] Early unpacking initramfs... done
[    7.574294] ACPI: Core revision 20070126
[    7.574346] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    7.577713] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    7.577738] Total of 1 processors activated (3195.66 BogoMIPS).
[    7.577929] ENABLING IO-APIC IRQs
[    7.578125] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    7.722095] Brought up 1 CPUs
[    7.722204] Booting paravirtualized kernel on bare hardware
[    7.722276] Time: 17:46:54  Date: 09/27/107
[    7.722297] NET: Registered protocol family 16
[    7.722372] EISA bus registered
[    7.722386] ACPI: bus type pci registered
[    7.759892] PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=4
[    7.759894] PCI: Using configuration type 1
[    7.759896] Setting up standard PCI resources
[    7.764280] ACPI: EC: Look up EC in DSDT
[    7.768611] ACPI: Interpreter enabled
[    7.768615] ACPI: (supports S0 S3 S4 S5)
[    7.768630] ACPI: Using IOAPIC for interrupt routing
[    7.779366] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    7.779381] PCI: Probing PCI hardware (bus 00)
[    7.779985] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    7.779990] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    7.780616] PCI: Transparent bridge - 0000:00:1e.0
[    7.780705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.781152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    7.781236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    7.786771] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    7.786869] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    7.786964] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    7.787059] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[    7.787141] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    7.787226] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    7.787311] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    7.787400] Linux Plug and Play Support v0.97 (c) Adam Belay
[    7.787409] pnp: PnP ACPI init
[    7.787419] ACPI: bus type pnp registered
[    7.810883] pnp: PnP ACPI: found 11 devices
[    7.810886] ACPI: ACPI bus type pnp unregistered
[    7.810890] PnPBIOS: Disabled by ACPI PNP
[    7.810930] PCI: Using ACPI for IRQ routing
[    7.810933] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    7.826393] NET: Registered protocol family 8
[    7.826396] NET: Registered protocol family 20
[    7.826444] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
[    7.826448] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    7.826451] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    7.826454] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    7.826460] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    7.826463] pnp: 00:02: ioport range 0x1000-0x1005 has been reserved
[    7.826466] pnp: 00:02: ioport range 0x1008-0x100f has been reserved
[    7.826471] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    7.826474] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    7.826478] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    7.826481] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    7.826484] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    7.826487] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    7.826494] pnp: 00:08: ioport range 0x900-0x90f has been reserved
[    7.826497] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    7.826499] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    7.826502] pnp: 00:08: ioport range 0x930-0x93f has been reserved
[    7.826505] pnp: 00:08: ioport range 0x940-0x97f has been reserved
[    7.829975] Time: tsc clocksource has been installed.
[    7.856759] PCI: Bridge: 0000:00:01.0
[    7.856761]   IO window: d000-dfff
[    7.856765]   MEM window: dfd00000-dfefffff
[    7.856769]   PREFETCH window: d0000000-d7ffffff
[    7.856778] PCI: Bus 4, cardbus bridge: 0000:03:01.0
[    7.856780]   IO window: 00002000-000020ff
[    7.856785]   IO window: 00002400-000024ff
[    7.856790]   PREFETCH window: 30000000-33ffffff
[    7.856795]   MEM window: 34000000-37ffffff
[    7.856800] PCI: Bridge: 0000:00:1e.0
[    7.856803]   IO window: 2000-2fff
[    7.856809]   MEM window: dfc00000-dfcfffff
[    7.856814]   PREFETCH window: 30000000-33ffffff
[    7.856829] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    7.856835] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    7.856847] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    7.856861] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
[    7.856866] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
[    7.856882] NET: Registered protocol family 2
[    7.893956] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    7.893989] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    7.894134] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    7.894233] TCP: Hash tables configured (established 16384 bind 16384)
[    7.894236] TCP reno registered
[    7.906026] checking if image is initramfs... it is
[    8.357563] Switched to high resolution mode on CPU 0
[    8.618709] Freeing initrd memory: 7129k freed
[    8.618859] Simple Boot Flag at 0x79 set to 0x1
[    8.619105] audit: initializing netlink socket (disabled)
[    8.619121] audit(1193507214.112:1): initialized
[    8.621013] VFS: Disk quotas dquot_6.5.1
[    8.621064] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.621158] io scheduler noop registered
[    8.621161] io scheduler anticipatory registered
[    8.621163] io scheduler deadline registered
[    8.621179] io scheduler cfq registered (default)
[    8.621276] Boot video device is 0000:01:00.0
[    8.621378] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    8.621408] assign_interrupt_mode Found MSI capability
[    8.621412] Allocate Port Service[0000:00:01.0:pcie00]
[    8.621543] isapnp: Scanning for PnP cards...
[    8.976057] isapnp: No Plug & Play device found
[    9.000050] Real Time Clock Driver v1.12ac
[    9.000161] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.000781] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
[    9.000790] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[    9.001359] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.001559] input: Macintosh mouse button emulation as /class/input/input0
[    9.001636] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.007078] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.007084] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.007239] mice: PS/2 mouse device common for all mice
[    9.007342] EISA: Probing bus 0 at eisa.0
[    9.007350] Cannot allocate resource for EISA slot 1
[    9.007353] Cannot allocate resource for EISA slot 2
[    9.007378] EISA: Detected 0 cards.
[    9.007475] TCP cubic registered
[    9.007491] NET: Registered protocol family 1
[    9.007516] Using IPI No-Shortcut mode
[    9.007687]   Magic number: 11:94:796
[    9.007777]   hash matches device ptyr4
[    9.008000] Freeing unused kernel memory: 364k freed
[    9.076946] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.188553] AppArmor: AppArmor initialized<5>audit(1193507215.612:2):  type=1505 info="AppArmor initialized" pid=1197
[   10.194029] fuse init (API version 7.8)
[   10.199206] Failure registering capabilities with primary security module.
[   10.210861] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   10.210867] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.210879] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   10.214199] ACPI: Thermal Zone [THM] (34 C)
[   10.572337] usbcore: registered new interface driver usbfs
[   10.572361] usbcore: registered new interface driver hub
[   10.572380] usbcore: registered new device driver usb
[   10.573176] USB Universal Host Controller Interface driver v3.0
[   10.573238] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   10.573250] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.573255] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.573434] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.573467] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[   10.573574] usb usb1: configuration #1 chosen from 1 choice
[   10.573601] hub 1-0:1.0: USB hub found
[   10.573606] hub 1-0:1.0: 2 ports detected
[   10.675677] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
[   10.675692] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.675696] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.675720] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.675754] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000bf60
[   10.675853] usb usb2: configuration #1 chosen from 1 choice
[   10.675879] hub 2-0:1.0: USB hub found
[   10.675884] hub 2-0:1.0: 2 ports detected
[   10.732735] SCSI subsystem initialized
[   10.738094] libata version 2.21 loaded.
[   10.779582] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   10.779595] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   10.779600] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   10.779623] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   10.779655] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
[   10.779749] usb usb3: configuration #1 chosen from 1 choice
[   10.779774] hub 3-0:1.0: USB hub found
[   10.779780] hub 3-0:1.0: 2 ports detected
[   10.883482] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
[   10.883495] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   10.883500] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   10.883524] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   10.883558] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000bf20
[   10.883658] usb usb4: configuration #1 chosen from 1 choice
[   10.883684] hub 4-0:1.0: USB hub found
[   10.883690] hub 4-0:1.0: 2 ports detected
[   10.915337] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.704000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.708000] Time: acpi_pm clocksource has been installed.
[    3.772000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
[    3.772000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.772000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.772000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.772000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.772000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.772000] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    3.872000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.872000] usb usb5: configuration #1 chosen from 1 choice
[    3.872000] hub 5-0:1.0: USB hub found
[    3.872000] hub 5-0:1.0: 8 ports detected
[    3.976000] b44.c:v1.01 (Jun 16, 2006)
[    3.976000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[    3.976000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:12:3f:cf:b1:3b
[    3.980000] ata_piix 0000:00:1f.2: version 2.11
[    3.980000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.136000] Clocksource tsc unstable (delta = -420819377 ns)
[    4.136000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
[    4.136000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.136000] scsi0 : ata_piix
[    4.136000] scsi1 : ata_piix
[    4.136000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    4.136000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.280000] usb 1-1: device not accepting address 2, error -71
[    4.300000] ata1.00: ATA-6: HTS548040M9AT00, MG2OA5EA, max UDMA/100
[    4.300000] ata1.00: 78140160 sectors, multi 8: LBA48
[    4.300000] ata1.00: applying bridge limits
[    4.316000] ata1.00: configured for UDMA/100
[    4.652000] ata2.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462C, DE01, max UDMA/33
[    4.840000] ata2.00: configured for UDMA/33
[    4.840000] scsi 0:0:0:0: Direct-Access     ATA      HTS548040M9AT00  MG2O PQ: 0 ANSI: 5
[    4.840000] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462C DE01 PQ: 0 ANSI: 5
[    4.844000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 19
[    4.896000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.916000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.916000] sd 0:0:0:0: [sda] Write Protect is off
[    4.916000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.916000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.916000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.916000] sd 0:0:0:0: [sda] Write Protect is off
[    4.916000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.916000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.916000]  sda: sda1 sda2 sda3 sda4
[    4.964000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.968000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.968000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.980000] sr0: scsi3-mmc drive: 10x/24x writer cd/rw xa/form2 cdda tray
[    4.980000] Uniform CD-ROM driver Revision: 3.20
[    4.984000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.004000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[    5.160000] usb 1-1: configuration #1 chosen from 1 choice
[    5.248000] Attempting manual resume
[    5.248000] swsusp: Resume From Partition 8:2
[    5.248000] PM: Checking swsusp image.
[    5.248000] PM: Resume from disk failed.
[    5.292000] kjournald starting.  Commit interval 5 seconds
[    5.292000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.176000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[5b4fc0003fffffff]
[   14.452000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.552000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.552000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.236000] intel_rng: FWH not detected
[   15.268000] iTCO_vendor_support: vendor-support=0
[   15.268000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   15.268000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   15.268000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.780000] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0189]
[   15.796000] input: PC Speaker as /class/input/input2
[   15.832000] input: PS/2 Mouse as /class/input/input3
[   15.848000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   15.908000] Yenta: ISA IRQ mask 0x04b8, PCI irq 17
[   15.908000] Socket status: 30000006
[   15.908000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   15.908000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   15.908000] cs: IO port probe 0x2000-0x2fff: clean.
[   15.908000] pcmcia: parent PCI bridge Memory window: 0xdfc00000 - 0xdfcfffff
[   15.908000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   15.932000] sdhci: Secure Digital Host Controller Interface driver
[   15.932000] sdhci: Copyright(c) Pierre Ossman
[   15.932000] sdhci: SDHCI controller found at 0000:03:01.2 [1180:0822] (rev 17)
[   15.932000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 18
[   15.932000] mmc0: SDHCI at 0xdfcfc700 irq 18 DMA
[   16.400000] ieee80211_crypt: registered algorithm 'NULL'
[   16.424000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.424000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.468000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   16.468000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.468000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 18
[   16.468000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.716000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   16.784000] cs: IO port probe 0x100-0x3af: clean.
[   16.784000] cs: IO port probe 0x3e0-0x4ff: clean.
[   16.784000] cs: IO port probe 0x820-0x8ff: clean.
[   16.788000] cs: IO port probe 0xc00-0xcf7: clean.
[   16.788000] cs: IO port probe 0xa00-0xaff: clean.
[   16.816000] usbcore: registered new interface driver snd-usb-audio
[   16.836000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
[   16.836000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   17.664000] intel8x0_measure_ac97_clock: measured 55501 usecs
[   17.664000] intel8x0: clocking to 48000
[   18.308000] lp: driver loaded but no devices found
[   18.344000] i8k: unable to get SMM BIOS version
[   18.344000] Dell laptop SMM driver v1.14 21/02/2005 Massimo Dal Zotto (dz@debian.org)
[   18.468000] Adding 2048276k swap on /dev/sda2.  Priority:-1 extents:1 across:2048276k
[   18.912000] EXT3 FS on sda1, internal journal
[   20.032000] kjournald starting.  Commit interval 5 seconds
[   20.032000] EXT3 FS on sda3, internal journal
[   20.032000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.060000] kjournald starting.  Commit interval 5 seconds
[   20.060000] EXT3 FS on sda4, internal journal
[   20.060000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.444000] ACPI: Battery Slot [BAT0] (battery present)
[   21.504000] input: Lid Switch as /class/input/input5
[   21.508000] ACPI: Lid Switch [LID]
[   21.552000] input: Power Button (CM) as /class/input/input6
[   21.556000] ACPI: Power Button (CM) [PBTN]
[   21.600000] input: Sleep Button (CM) as /class/input/input7
[   21.604000] ACPI: Sleep Button (CM) [SBTN]
[   21.620000] No dock devices found.
[   21.716000] ACPI: AC Adapter [AC] (on-line)
[   21.736000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.988000] ppdev: user-space parallel port driver
[   23.276000] audit(1193507237.022:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4757 profile="/usr/sbin/cupsd"
[   23.424000] apm: BIOS not found.
[   25.244000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   25.244000] vboxdrv: Successfully done.
[   25.628000] Failure registering capabilities with primary security module.
[   25.920000] Bluetooth: Core ver 2.11
[   25.920000] NET: Registered protocol family 31
[   25.920000] Bluetooth: HCI device and connection manager initialized
[   25.920000] Bluetooth: HCI socket layer initialized
[   26.036000] Bluetooth: L2CAP ver 2.8
[   26.036000] Bluetooth: L2CAP socket layer initialized
[   26.120000] Bluetooth: RFCOMM socket layer initialized
[   26.120000] Bluetooth: RFCOMM TTY layer initialized
[   26.120000] Bluetooth: RFCOMM ver 1.8
[   27.488000] [drm] Initialized drm 1.1.0 20060810
[   27.496000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.496000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   31.116000] [drm] Setting GART location based on new memory map
[   31.116000] [drm] Loading R300 Microcode
[   31.116000] [drm] writeback test succeeded in 1 usecs
[   31.604000] NET: Registered protocol family 17
[  211.480000] NET: Registered protocol family 10
[  211.480000] lo: Disabled Privacy Extensions
[  211.480000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  221.788000] eth1: no IPv6 routers present
[  300.708000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  368.256000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  398.204000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  409.172000] eth1: no IPv6 routers present
[  851.832000] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[  851.896000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
[  852.740000] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[  853.168000] ttySHSF0 at I/O 0xee00 (irq = 18) is a Conexant HSF softmodem (PCI-8086:266d-14f1:5423)
[  853.256000] usbcore: registered new interface driver hsfusbcd2
[  853.848000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[  853.904000] usbcore: deregistering interface driver hsfusbcd2
[  854.660000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
[  854.792000] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[  855.244000] ttySHSF0 at I/O 0xee00 (irq = 18) is a Conexant HSF softmodem (PCI-8086:266d-14f1:5423)
[  855.344000] usbcore: registered new interface driver hsfusbcd2
[  855.568000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[  855.624000] usbcore: deregistering interface driver hsfusbcd2
[  857.960000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
[  858.264000] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[  858.888000] ttySHSF0 at I/O 0xee00 (irq = 18) is a Conexant HSF softmodem (PCI-8086:266d-14f1:5423)
[  858.956000] usbcore: registered new interface driver hsfusbcd2
[ 1089.532000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[ 1089.584000] usbcore: deregistering interface driver hsfusbcd2
[ 1150.564000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 18
[ 1150.684000] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[ 1151.112000] ttySHSF0 at I/O 0xee00 (irq = 18) is a Conexant HSF softmodem (PCI-8086:266d-14f1:5423)
[ 1151.172000] usbcore: registered new interface driver hsfusbcd2
[ 1779.996000] Uhhuh. NMI received for unknown reason b1 on CPU 0.
[ 1779.996000] You have some hardware problem, likely on the PCI bus.
[ 1779.996000] Dazed and confused, but trying to continue
[ 3382.812000] ipw2200: Firmware error detected.  Restarting.

```

---

### Post by mertle on 2007-10-29
UPDATE: Nothing's fixed, but I found that it's not a kernel bug like I had thought. I rolled back to 2.6.20-15, the one I used prior to upgrade, and still no scaling.

---

### Post by Dr John on 2007-11-03
My situation is essentially identical to that of mertle.  1.6GHz Pentium M.  But, since I did an upgrade to Gutsy from Feisty, when I reboot in Feisty, CPU frequency scaling works fine.  In my case, under Gutsy I'm stuck at 1.6GHz.  Since I have a fanless computer (Sumicom), this is annoying because the system runs a LOT hotter.

I've been looking at the various posts on this, but have yet to identify a solution.  Saw some comments that suggested that there may not be one forthcoming either because of some changes between Feisty and Gusty that make Gutsy complete dependent on the BIOS whereas apparently the know-how for doing CPU frequency scaling is hard-coded in Feisty (at least, in some situations).

I'd really like to find out whether it is true that this problem will remain in Gusty.  From a user's perspective (as opposed to that of a software purist), this presents a big problem.  It's reason enough to revert permanently back to Feisty and look for other options in the future (back to Gentoo?).  Too bad, because I really liked the user experience I had with Edgy and Feisty.

---

### Post by mccartyj on 2008-02-06
I have this same problem, but on a desktop. I noticed after upgrading to Gusty that whenever I rebooted into Windows the computer ran incredibly slow. I happened to notice during a reboot that the "CPU Real Clock" was listed as 1000 (200x5) and Windows listed my AMD 64-bit 3200 as 1GHz (in reality it is 2GHz). Powering down then restarting changes the CPU Real Clock to 2000 (200x10). This is crazy! So every time I run Ubuntu I am at half speed! 

I do have to admit that Ubuntu is still faster than XP on a good day, but c'mon Ubuntu!

Apparently downgrading doesn't help...

---

