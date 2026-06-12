---
title: "System Freezes after Upgrade to 12.04 (from 11.10)"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by dwhitney67 on 2012-06-01
Every once in a while, for reasons unknown, my system freezes; this has happened twice this week.  The mouse and keyboard are unusable, nor can I SSH into my system from another system.

The last X11 activity on my monitor is still displayed, but there are no updates (i.e. clock is frozen), mouse pointer does not move, etc.

I believe this issue is due to a bug with the Intel X11 video driver (which I had recently updated after installing 12.04), but I'm unable to ascertain that.  For all I know, it could be a kernel issue.  The logs do not contain any information that indicates that an error was detected.

Below is the video h/w that I have on my system:
```

$ sudo lspci -v
[sudo] password for dwhitney67: 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
        Subsystem: Acer Incorporated [ALI] Device 0511
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 0511
        Flags: bus master, fast devsel, latency 0, IRQ 41
        Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 2000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [a4] PCI Advanced Features
        Kernel driver in use: i915
        Kernel modules: i915
...

```

Here's the current system information:
```

$ uname -a
Linux gateway 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Short of reinstalling 11.10 from the disk in an effort to rebuild my system, is there any way to revert to an older version of the X11 driver and/or kernel?

Has anyone else witnessed the same issue my system has experienced?

P.S.  I also have been unable to get the grub menu to display during start-up, nor are my attempts to press ESC and/or SHIFT successful in stopping the grub process.  Here's my /etc/default/grub; is it setup correctly?
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by dino99 on 2012-06-01
open your package manager to purge the graphic driver & jockey, then reinstall them. (be sure that the kernels headers & dkms are already installed)

logout/in then check the driver activation (jockey)

maybe some cleaning might help:

sudo apt-get clean (autoclean autoremove)

sudo dpkg-reconfigure -phigh -a
(be patient, can take a while, dont stop it)

---

### Post by dwhitney67 on 2012-06-05
Thanks for your reply.  I will take it under advisement.  Fortunately, my system has not suffered a single hiccup in the last few days, so for now, I'll wait-n-see if anything needs to be done.

---

### Post by serroba on 2012-06-22
Hey Guys. I'm having the same issues.

My sistem is all Intel. I'm using a lot as well VirtualBox, first was the official one that you can install from the ubuntu servers, and after I installed the version from que Oracle servers.

I have no idea how to know what is going on. I think I have no useful information in the logs. When the system dies, it's all. No response to anything.
lspci:
```

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
        Subsystem: Giga-byte Technology Device 5000
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Giga-byte Technology Device d000
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [a4] PCI Advanced Features
        Kernel driver in use: i915
        Kernel modules: i915

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
        Subsystem: Giga-byte Technology Device 5007
        Flags: bus master, medium devsel, latency 0, IRQ 41
        Memory at f7d00000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [70] Power Management version 2
        Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
        Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
        Subsystem: Giga-byte Technology Device 1c3a
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at f7d1a000 (64-bit, non-prefetchable) [size=16]
        Capabilities: [50] Power Management version 3
        Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Kernel driver in use: mei
        Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at f7d18000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCI Advanced Features
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
        Subsystem: Giga-byte Technology Device a014
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at f7d10000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Root Complex Link
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Giga-byte Technology Device 5001
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f7c00000-f7cfffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Giga-byte Technology Device 5001
        Capabilities: [a0] Power Management version 2
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Giga-byte Technology Device 5001
        Capabilities: [a0] Power Management version 2

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f7d17000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCI Advanced Features
        Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
        Subsystem: Giga-byte Technology Device 5001
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
        Subsystem: Giga-byte Technology Device b005
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
        I/O ports at f0b0 [size=8]
        I/O ports at f0a0 [size=4]
        I/O ports at f090 [size=8]
        I/O ports at f080 [size=4]
        I/O ports at f060 [size=32]
        Memory at f7d16000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] SATA HBA v1.0
        Capabilities: [b0] PCI Advanced Features
        Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
        Subsystem: Giga-byte Technology Device 5001
        Flags: medium devsel, IRQ 3
        Memory at f7d15000 (64-bit, non-prefetchable) [size=256]
        I/O ports at f040 [size=32]
        Kernel modules: i2c-i801

02:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
        Subsystem: Giga-byte Technology Device e000
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f7c00000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at e000 [size=128]
        Capabilities: [40] Power Management version 3
        Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [58] Express Endpoint, MSI 00
        Capabilities: [6c] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [180] Device Serial Number ff-11-f0-ca-90-2b-34-ff
        Kernel driver in use: atl1c
        Kernel modules: atl1c

03:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=03, secondary=04, subordinate=04, sec-latency=32
        Capabilities: [90] Power Management version 2
        Capabilities: [a0] Subsystem: Giga-byte Technology Device 8892


```

dmesg (this is the one that I'm running now):
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-25-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 (Ubuntu 3.2.0-25.40-generic 3.2.18)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-25-generic root=UUID=25465584-773e-4e45-8dc7-88efbf519004 ro crashkernel=384M-2G:64M,2G-:128M
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
[    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
[    0.000000]  BIOS-e820: 0000000040005000 - 00000000d99a3000 (usable)
[    0.000000]  BIOS-e820: 00000000d99a3000 - 00000000da09c000 (reserved)
[    0.000000]  BIOS-e820: 00000000da09c000 - 00000000da31c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da31c000 - 00000000da321000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000da321000 - 00000000da364000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da364000 - 00000000dac80000 (usable)
[    0.000000]  BIOS-e820: 00000000dac80000 - 00000000dafdd000 (reserved)
[    0.000000]  BIOS-e820: 00000000dafdd000 - 00000000db000000 (usable)
[    0.000000]  BIOS-e820: 00000000db800000 - 00000000dfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000021f600000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. To be filled by O.E.M./H77M-D3H, BIOS F4 02/16/2012
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x21f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FE0000000 write-back
[    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   5 base 21F800000 mask FFF800000 uncachable
[    0.000000]   6 base 21F600000 mask FFFE00000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 5, base: 8696MB, range: 8MB, type UC
[    0.000000] reg 6, base: 8694MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8110M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 128M        num_reg: 9      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 512MB, type WB
[    0.000000] reg 7, base: 8694MB, range: 2MB, type UC
[    0.000000] reg 8, base: 8696MB, range: 8MB, type UC
[    0.000000] e820 update range: 00000000db800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcb20] fcb20
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000db000000
[    0.000000]  0000000000 - 00db000000 page 2M
[    0.000000] kernel direct mapping tables up to db000000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000021f600000
[    0.000000]  0100000000 - 021f600000 page 2M
[    0.000000] kernel direct mapping tables up to 21f600000 @ daff6000-db000000
[    0.000000] RAMDISK: 35790000 - 36bc0000
[    0.000000] Reserving 128MB of memory at 720MB for crashkernel (System RAM: 8694MB)
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000da303070 00064 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000da30cd08 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000da303170 09B97 (v02 ALASKA    A M I 00000012 INTL 20051117)
[    0.000000] ACPI: FACS 00000000da31af80 00040
[    0.000000] ACPI: APIC 00000000da30ce00 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000da30ce78 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000da30ceb8 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000da30cef0 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000da30d260 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000da30dc10 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: BGRT 00000000da30e6a8 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000021f600000
[    0.000000] Initmem setup node 0 0000000000000000-000000021f600000
[    0.000000]   NODE_DATA [000000021f5fb000 - 000000021f5fffff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216c00000-ffff88021ebfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0021f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040004
[    0.000000]     0: 0x00040005 -> 0x000d99a3
[    0.000000]     0: 0x000da364 -> 0x000dac80
[    0.000000]     0: 0x000dafdd -> 0x000db000
[    0.000000]     0: 0x00100000 -> 0x0021f600
[    0.000000] On node 0 totalpages: 2070126
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 872737 pages, LIFO batch:31
[    0.000000]   Normal zone: 18392 pages used for memmap
[    0.000000]   Normal zone: 1158696 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000d99a3000 - 00000000da09c000
[    0.000000] PM: Registered nosave memory: 00000000da09c000 - 00000000da31c000
[    0.000000] PM: Registered nosave memory: 00000000da31c000 - 00000000da321000
[    0.000000] PM: Registered nosave memory: 00000000da321000 - 00000000da364000
[    0.000000] PM: Registered nosave memory: 00000000dac80000 - 00000000dafdd000
[    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000db800000
[    0.000000] PM: Registered nosave memory: 00000000db800000 - 00000000dfa00000
[    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at dfa00000 (gap: dfa00000:18600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021f200000 s83072 r8192 d23424 u524288
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2035345
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-25-generic root=UUID=25465584-773e-4e45-8dc7-88efbf519004 ro crashkernel=384M-2G:64M,2G-:128M
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7915336k/8902656k available (6570k kernel code, 622152k absent, 365168k reserved, 6633k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3092.959 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6185.91 BogoMIPS (lpj=12371836)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000023] Security Framework initialized
[    0.000035] AppArmor: AppArmor initialized
[    0.000036] Yama: becoming mindful.
[    0.000576] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002206] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002900] Mount-cache hash table entries: 256
[    0.002977] Initializing cgroup subsys cpuacct
[    0.002982] Initializing cgroup subsys memory
[    0.002989] Initializing cgroup subsys devices
[    0.002991] Initializing cgroup subsys freezer
[    0.002994] Initializing cgroup subsys blkio
[    0.002998] Initializing cgroup subsys perf_event
[    0.003019] CPU: Physical Processor ID: 0
[    0.003021] CPU: Processor Core ID: 0
[    0.003026] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003027] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.003317] mce: CPU supports 9 MCE banks
[    0.003329] CPU0: Thermal monitoring enabled (TM1)
[    0.003337] using mwait in idle threads.
[    0.004913] ACPI: Core revision 20110623
[    0.010889] ftrace: allocating 27073 entries in 107 pages
[    0.017927] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057603] CPU0: Intel(R) Core(TM) i5-3450 CPU @ 3.10GHz stepping 09
[    0.164331] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.164337] ... version:                3
[    0.164339] ... bit width:              48
[    0.164340] ... generic registers:      8
[    0.164342] ... value mask:             0000ffffffffffff
[    0.164344] ... max period:             000000007fffffff
[    0.164345] ... fixed-purpose events:   3
[    0.164347] ... event mask:             00000007000000ff
[    0.164437] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164492] Booting Node   0, Processors  #1
[    0.164495] smpboot cpu 1: start_ip = 98000
[    0.272702] NMI watchdog enabled, takes one hw-pmu counter.
[    0.272768]  #2
[    0.272769] smpboot cpu 2: start_ip = 98000
[    0.380675] NMI watchdog enabled, takes one hw-pmu counter.
[    0.380735]  #3 Ok.
[    0.380737] smpboot cpu 3: start_ip = 98000
[    0.488642] NMI watchdog enabled, takes one hw-pmu counter.
[    0.488667] Brought up 4 CPUs
[    0.488669] Total of 4 processors activated (24743.64 BogoMIPS).
[    0.491583] devtmpfs: initialized
[    0.492167] EVM: security.selinux
[    0.492169] EVM: security.SMACK64
[    0.492170] EVM: security.capability
[    0.492187] PM: Registering ACPI NVS region at da09c000 (2621440 bytes)
[    0.492215] PM: Registering ACPI NVS region at da321000 (274432 bytes)
[    0.492753] print_constraints: dummy: 
[    0.492782] RTC time: 22:57:12, date: 06/21/12
[    0.492803] NET: Registered protocol family 16
[    0.492870] Trying to unpack rootfs image as initramfs...
[    0.492874] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.492877] ACPI: bus type pci registered
[    0.492917] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.492921] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.503420] PCI: Using configuration type 1 for base access
[    0.504012] bio: create slab <bio-0> at 0
[    0.504064] ACPI: Added _OSI(Module Device)
[    0.504067] ACPI: Added _OSI(Processor Device)
[    0.504069] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.504071] ACPI: Added _OSI(Processor Aggregator Device)
[    0.505149] ACPI: EC: Look up EC in DSDT
[    0.506425] ACPI: Executed 1 blocks of module-level executable AML code
[    0.532537] ACPI: SSDT 00000000da03e018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.532809] ACPI: Dynamic OEM Table Load:
[    0.532812] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.556396] ACPI: SSDT 00000000da03fa98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.556687] ACPI: Dynamic OEM Table Load:
[    0.556690] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.580304] ACPI: SSDT 00000000da04bc18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.580571] ACPI: Dynamic OEM Table Load:
[    0.580574] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.604710] ACPI: Interpreter enabled
[    0.604715] ACPI: (supports S0 S3 S4 S5)
[    0.604731] ACPI: Using IOAPIC for interrupt routing
[    0.608710] ACPI: Power Resource [FN00] (off)
[    0.608762] ACPI: Power Resource [FN01] (off)
[    0.608811] ACPI: Power Resource [FN02] (off)
[    0.608859] ACPI: Power Resource [FN03] (off)
[    0.608907] ACPI: Power Resource [FN04] (off)
[    0.609220] ACPI: No dock devices found.
[    0.609222] HEST: Table not found.
[    0.609225] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.609431] \_SB_.PCI0:_OSC invalid UUID
[    0.609432] _OSC request data:1 8 1f 
[    0.609435] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.609763] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.609766] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.609768] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.609771] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.609774] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.609776] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.609779] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.609782] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.609784] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.609787] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfeafffff]
[    0.609790] pci_root PNP0A08:00: host bridge window [mem 0x21f600000-0xfffffffff]
[    0.609801] pci 0000:00:00.0: [8086:0150] type 0 class 0x000600
[    0.609829] pci 0000:00:02.0: [8086:0152] type 0 class 0x000300
[    0.609837] pci 0000:00:02.0: reg 10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.609842] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.609845] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.609888] pci 0000:00:14.0: [8086:1e31] type 0 class 0x000c03
[    0.609908] pci 0000:00:14.0: reg 10: [mem 0xf7d00000-0xf7d0ffff 64bit]
[    0.609976] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.609979] pci 0000:00:14.0: PME# disabled
[    0.609997] pci 0000:00:16.0: [8086:1e3a] type 0 class 0x000780
[    0.610018] pci 0000:00:16.0: reg 10: [mem 0xf7d1a000-0xf7d1a00f 64bit]
[    0.610090] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.610093] pci 0000:00:16.0: PME# disabled
[    0.610122] pci 0000:00:1a.0: [8086:1e2d] type 0 class 0x000c03
[    0.610142] pci 0000:00:1a.0: reg 10: [mem 0xf7d18000-0xf7d183ff]
[    0.610228] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.610231] pci 0000:00:1a.0: PME# disabled
[    0.610252] pci 0000:00:1b.0: [8086:1e20] type 0 class 0x000403
[    0.610266] pci 0000:00:1b.0: reg 10: [mem 0xf7d10000-0xf7d13fff 64bit]
[    0.610330] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.610332] pci 0000:00:1b.0: PME# disabled
[    0.610351] pci 0000:00:1c.0: [8086:1e10] type 1 class 0x000604
[    0.610426] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.610429] pci 0000:00:1c.0: PME# disabled
[    0.610452] pci 0000:00:1c.4: [8086:1e18] type 1 class 0x000604
[    0.610527] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.610530] pci 0000:00:1c.4: PME# disabled
[    0.610552] pci 0000:00:1c.6: [8086:244e] type 1 class 0x000604
[    0.610627] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.610630] pci 0000:00:1c.6: PME# disabled
[    0.610655] pci 0000:00:1d.0: [8086:1e26] type 0 class 0x000c03
[    0.610674] pci 0000:00:1d.0: reg 10: [mem 0xf7d17000-0xf7d173ff]
[    0.610760] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.610764] pci 0000:00:1d.0: PME# disabled
[    0.610785] pci 0000:00:1f.0: [8086:1e4a] type 0 class 0x000601
[    0.610903] pci 0000:00:1f.2: [8086:1e02] type 0 class 0x000106
[    0.610920] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    0.610926] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    0.610933] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    0.610940] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    0.610947] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    0.610954] pci 0000:00:1f.2: reg 24: [mem 0xf7d16000-0xf7d167ff]
[    0.610995] pci 0000:00:1f.2: PME# supported from D3hot
[    0.610998] pci 0000:00:1f.2: PME# disabled
[    0.611012] pci 0000:00:1f.3: [8086:1e22] type 0 class 0x000c05
[    0.611026] pci 0000:00:1f.3: reg 10: [mem 0xf7d15000-0xf7d150ff 64bit]
[    0.611046] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.611110] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.611181] pci 0000:02:00.0: [1969:1083] type 0 class 0x000200
[    0.611208] pci 0000:02:00.0: reg 10: [mem 0xf7c00000-0xf7c3ffff 64bit]
[    0.611222] pci 0000:02:00.0: reg 18: [io  0xe000-0xe07f]
[    0.611345] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.611350] pci 0000:02:00.0: PME# disabled
[    0.616242] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
[    0.616246] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.616250] pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.616318] pci 0000:03:00.0: [1283:8892] type 1 class 0x000604
[    0.616474] pci 0000:03:00.0: supports D1 D2
[    0.616475] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.616481] pci 0000:03:00.0: PME# disabled
[    0.616504] pci 0000:00:1c.6: PCI bridge to [bus 03-04] (subtractive decode)
[    0.616515] pci 0000:00:1c.6:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.616516] pci 0000:00:1c.6:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.616518] pci 0000:00:1c.6:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.616519] pci 0000:00:1c.6:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.616521] pci 0000:00:1c.6:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.616522] pci 0000:00:1c.6:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.616524] pci 0000:00:1c.6:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.616525] pci 0000:00:1c.6:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.616527] pci 0000:00:1c.6:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.616528] pci 0000:00:1c.6:   bridge window [mem 0xdfa00000-0xfeafffff] (subtractive decode)
[    0.616530] pci 0000:00:1c.6:   bridge window [mem 0x21f600000-0xfffffffff] (subtractive decode)
[    0.616681] pci 0000:03:00.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.616708] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.616709] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.616711] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.616712] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.616714] pci 0000:03:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.616715] pci 0000:03:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.616717] pci 0000:03:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.616718] pci 0000:03:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.616720] pci 0000:03:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.616721] pci 0000:03:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.616723] pci 0000:03:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.616724] pci 0000:03:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.616726] pci 0000:03:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.616727] pci 0000:03:00.0:   bridge window [mem 0xdfa00000-0xfeafffff] (subtractive decode)
[    0.616729] pci 0000:03:00.0:   bridge window [mem 0x21f600000-0xfffffffff] (subtractive decode)
[    0.616757] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.616869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.616894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.616917] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    0.616988] \_SB_.PCI0:_OSC invalid UUID
[    0.616989] _OSC request data:1 1f 1f 
[    0.616992]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.617021] \_SB_.PCI0:_OSC invalid UUID
[    0.617022] _OSC request data:1 0 1d 
[    0.617024]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.617027] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.619518] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.619552] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.619588] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.619620] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.619651] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.619682] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.619713] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.619743] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.619814] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.619821] vgaarb: loaded
[    0.619822] vgaarb: bridge control possible 0000:00:02.0
[    0.619881] i2c-core: driver [aat2870] using legacy suspend method
[    0.619883] i2c-core: driver [aat2870] using legacy resume method
[    0.619924] SCSI subsystem initialized
[    0.619957] libata version 3.00 loaded.
[    0.619984] usbcore: registered new interface driver usbfs
[    0.619991] usbcore: registered new interface driver hub
[    0.620004] usbcore: registered new device driver usb
[    0.620054] PCI: Using ACPI for IRQ routing
[    0.621537] PCI: pci_cache_line_size set to 64 bytes
[    0.621584] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.621585] reserve RAM buffer: 0000000040004000 - 0000000043ffffff 
[    0.621587] reserve RAM buffer: 00000000d99a3000 - 00000000dbffffff 
[    0.621589] reserve RAM buffer: 00000000dac80000 - 00000000dbffffff 
[    0.621590] reserve RAM buffer: 00000000db000000 - 00000000dbffffff 
[    0.621592] reserve RAM buffer: 000000021f600000 - 000000021fffffff 
[    0.621651] NetLabel: Initializing
[    0.621653] NetLabel:  domain hash size = 128
[    0.621655] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.621664] NetLabel:  unlabeled traffic allowed by default
[    0.621697] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.621702] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.623713] Switching to clocksource hpet
[    0.627491] AppArmor: AppArmor Filesystem Enabled
[    0.627505] pnp: PnP ACPI init
[    0.627515] ACPI: bus type pnp registered
[    0.627703] pnp 00:00: [bus 00-3e]
[    0.627705] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.627707] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.627708] pnp 00:00: [io  0x0d00-0xffff window]
[    0.627709] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.627710] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.627719] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.627720] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.627721] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.627722] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.627723] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.627725] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.627726] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.627727] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.627728] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.627730] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.627731] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.627732] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.627733] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    0.627735] pnp 00:00: [mem 0x21f600000-0xfffffffff window]
[    0.627777] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.627790] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.627813] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.627817] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.627824] pnp 00:02: [io  0x0000-0x001f]
[    0.627825] pnp 00:02: [io  0x0081-0x0091]
[    0.627826] pnp 00:02: [io  0x0093-0x009f]
[    0.627827] pnp 00:02: [io  0x00c0-0x00df]
[    0.627830] pnp 00:02: [dma 4]
[    0.627843] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.627848] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.627859] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.627907] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.627921] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.627929] pnp 00:05: [io  0x002e-0x002f]
[    0.627930] pnp 00:05: [io  0x004e-0x004f]
[    0.627931] pnp 00:05: [io  0x0061]
[    0.627932] pnp 00:05: [io  0x0063]
[    0.627933] pnp 00:05: [io  0x0065]
[    0.627934] pnp 00:05: [io  0x0067]
[    0.627935] pnp 00:05: [io  0x0070]
[    0.627936] pnp 00:05: [io  0x0080]
[    0.627937] pnp 00:05: [io  0x0092]
[    0.627938] pnp 00:05: [io  0x00b2-0x00b3]
[    0.627939] pnp 00:05: [io  0x0680-0x069f]
[    0.627940] pnp 00:05: [io  0x0200-0x020f]
[    0.627941] pnp 00:05: [io  0xffff]
[    0.627942] pnp 00:05: [io  0xffff]
[    0.627943] pnp 00:05: [io  0x0400-0x0453]
[    0.627944] pnp 00:05: [io  0x0458-0x047f]
[    0.627945] pnp 00:05: [io  0x0500-0x057f]
[    0.627946] pnp 00:05: [io  0x164e-0x164f]
[    0.627969] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.627971] system 00:05: [io  0x0200-0x020f] has been reserved
[    0.627975] system 00:05: [io  0xffff] has been reserved
[    0.627977] system 00:05: [io  0xffff] has been reserved
[    0.627979] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.627982] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.627984] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.627986] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.627989] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.627994] pnp 00:06: [io  0x0070-0x0077]
[    0.628001] pnp 00:06: [irq 8]
[    0.628013] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.628030] pnp 00:07: [io  0x0454-0x0457]
[    0.628049] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.628053] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.628117] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.628118] pnp 00:08: [io  0x0a00-0x0a0f]
[    0.628120] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.628121] pnp 00:08: [io  0x0a20-0x0a2f]
[    0.628141] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    0.628144] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.628146] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.628149] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.628163] pnp 00:09: [io  0x0060]
[    0.628164] pnp 00:09: [io  0x0064]
[    0.628167] pnp 00:09: [irq 1]
[    0.628186] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.628207] pnp 00:0a: [irq 12]
[    0.628224] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.628323] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.628327] pnp 00:0b: [irq 4]
[    0.628328] pnp 00:0b: [dma 0 disabled]
[    0.628363] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.628569] pnp 00:0c: [io  0x0378-0x037f]
[    0.628573] pnp 00:0c: [irq 7]
[    0.628574] pnp 00:0c: [dma 0 disabled]
[    0.628657] pnp 00:0c: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.628670] pnp 00:0d: [io  0x0010-0x001f]
[    0.628671] pnp 00:0d: [io  0x0022-0x003f]
[    0.628673] pnp 00:0d: [io  0x0044-0x005f]
[    0.628674] pnp 00:0d: [io  0x0062-0x0063]
[    0.628675] pnp 00:0d: [io  0x0065-0x006f]
[    0.628676] pnp 00:0d: [io  0x0072-0x007f]
[    0.628677] pnp 00:0d: [io  0x0080]
[    0.628678] pnp 00:0d: [io  0x0084-0x0086]
[    0.628679] pnp 00:0d: [io  0x0088]
[    0.628680] pnp 00:0d: [io  0x008c-0x008e]
[    0.628681] pnp 00:0d: [io  0x0090-0x009f]
[    0.628682] pnp 00:0d: [io  0x00a2-0x00bf]
[    0.628683] pnp 00:0d: [io  0x00e0-0x00ef]
[    0.628684] pnp 00:0d: [io  0x04d0-0x04d1]
[    0.628707] system 00:0d: [io  0x04d0-0x04d1] has been reserved
[    0.628710] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.628715] pnp 00:0e: [io  0x00f0-0x00ff]
[    0.628718] pnp 00:0e: [irq 13]
[    0.628733] pnp 00:0e: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.628878] pnp 00:0f: [mem 0xfed1c000-0xfed1ffff]
[    0.628879] pnp 00:0f: [mem 0xfed10000-0xfed17fff]
[    0.628881] pnp 00:0f: [mem 0xfed18000-0xfed18fff]
[    0.628883] pnp 00:0f: [mem 0xfed19000-0xfed19fff]
[    0.628884] pnp 00:0f: [mem 0xf8000000-0xfbffffff]
[    0.628885] pnp 00:0f: [mem 0xfed20000-0xfed3ffff]
[    0.628886] pnp 00:0f: [mem 0xfed90000-0xfed93fff]
[    0.628887] pnp 00:0f: [mem 0xfed45000-0xfed8ffff]
[    0.628888] pnp 00:0f: [mem 0xff000000-0xffffffff]
[    0.628889] pnp 00:0f: [mem 0xfee00000-0xfeefffff]
[    0.628891] pnp 00:0f: [mem 0xdfa00000-0xdfa00fff]
[    0.628925] system 00:0f: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.628928] system 00:0f: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.628932] system 00:0f: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.628935] system 00:0f: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.628937] system 00:0f: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.628940] system 00:0f: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.628942] system 00:0f: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.628945] system 00:0f: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.628947] system 00:0f: [mem 0xff000000-0xffffffff] has been reserved
[    0.628950] system 00:0f: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.628952] system 00:0f: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    0.628955] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.629047] pnp 00:10: [mem 0x20000000-0x201fffff]
[    0.629048] pnp 00:10: [mem 0x40004000-0x40004fff]
[    0.629082] system 00:10: [mem 0x20000000-0x201fffff] has been reserved
[    0.629085] system 00:10: [mem 0x40004000-0x40004fff] has been reserved
[    0.629088] system 00:10: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.629103] pnp: PnP ACPI: found 17 devices
[    0.629105] ACPI: ACPI bus type pnp unregistered
[    0.634890] PCI: max bus depth: 2 pci_try_num: 3
[    0.634928] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.634939] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
[    0.634943] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.634948] pci 0000:00:1c.4:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.634956] pci 0000:03:00.0: PCI bridge to [bus 04-04]
[    0.634980] pci 0000:00:1c.6: PCI bridge to [bus 03-04]
[    0.634999] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.635004] pci 0000:00:1c.0: setting latency timer to 64
[    0.635009] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.635014] pci 0000:00:1c.4: setting latency timer to 64
[    0.635020] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.635024] pci 0000:00:1c.6: setting latency timer to 64
[    0.635032] pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.635039] pci 0000:03:00.0: setting latency timer to 64
[    0.635044] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.635045] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.635046] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.635048] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.635049] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.635050] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.635052] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.635053] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.635054] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.635056] pci_bus 0000:00: resource 13 [mem 0xdfa00000-0xfeafffff]
[    0.635057] pci_bus 0000:00: resource 14 [mem 0x21f600000-0xfffffffff]
[    0.635059] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.635060] pci_bus 0000:02: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.635062] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.635063] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.635064] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.635066] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.635067] pci_bus 0000:03: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.635068] pci_bus 0000:03: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.635070] pci_bus 0000:03: resource 10 [mem 0x000dc000-0x000dffff]
[    0.635071] pci_bus 0000:03: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.635073] pci_bus 0000:03: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.635074] pci_bus 0000:03: resource 13 [mem 0xdfa00000-0xfeafffff]
[    0.635075] pci_bus 0000:03: resource 14 [mem 0x21f600000-0xfffffffff]
[    0.635077] pci_bus 0000:04: resource 8 [io  0x0000-0x0cf7]
[    0.635078] pci_bus 0000:04: resource 9 [io  0x0d00-0xffff]
[    0.635079] pci_bus 0000:04: resource 10 [mem 0x000a0000-0x000bffff]
[    0.635081] pci_bus 0000:04: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.635082] pci_bus 0000:04: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.635083] pci_bus 0000:04: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.635085] pci_bus 0000:04: resource 14 [mem 0x000dc000-0x000dffff]
[    0.635086] pci_bus 0000:04: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.635087] pci_bus 0000:04: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.635089] pci_bus 0000:04: resource 17 [mem 0xdfa00000-0xfeafffff]
[    0.635090] pci_bus 0000:04: resource 18 [mem 0x21f600000-0xfffffffff]
[    0.635109] NET: Registered protocol family 2
[    0.635262] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.635927] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.636955] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.637085] TCP: Hash tables configured (established 524288 bind 65536)
[    0.637088] TCP reno registered
[    0.637101] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.637129] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.637194] NET: Registered protocol family 1
[    0.637207] pci 0000:00:02.0: Boot video device
[    0.637214] pci 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.637264] pci 0000:00:14.0: PCI INT A disabled
[    0.637272] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.655725] pci 0000:00:1a.0: PCI INT A disabled
[    0.655743] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.675717] pci 0000:00:1d.0: PCI INT A disabled
[    0.675732] PCI: CLS 64 bytes, default 64
[    0.675733] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.675736] Placing 64MB software IO TLB between ffff8800d59a3000 - ffff8800d99a3000
[    0.675738] software IO TLB at phys 0xd59a3000 - 0xd99a3000
[    0.676033] audit: initializing netlink socket (disabled)
[    0.676040] type=2000 audit(1340319431.516:1): initialized
[    0.700460] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.719142] VFS: Disk quotas dquot_6.5.2
[    0.719178] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.719478] fuse init (API version 7.17)
[    0.719532] msgmni has been set to 15459
[    0.719746] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.719764] io scheduler noop registered
[    0.719766] io scheduler deadline registered
[    0.719784] io scheduler cfq registered (default)
[    0.719932] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.719946] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.719977] intel_idle: MWAIT substates: 0x1120
[    0.719978] intel_idle: does not run on family 6 model 58
[    0.720035] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.720041] ACPI: Power Button [PWRB]
[    0.720067] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.720070] ACPI: Power Button [PWRF]
[    0.720125] ACPI: Fan [FAN0] (off)
[    0.720145] ACPI: Fan [FAN1] (off)
[    0.720164] ACPI: Fan [FAN2] (off)
[    0.720182] ACPI: Fan [FAN3] (off)
[    0.720201] ACPI: Fan [FAN4] (off)
[    0.762190] Freeing initrd memory: 20672k freed
[    0.791925] Monitor-Mwait will be used to enter C-1 state
[    0.791946] Monitor-Mwait will be used to enter C-3 state
[    0.791958] ACPI: acpi_idle registered with cpuidle
[    0.811864] thermal LNXTHERM:00: registered as thermal_zone0
[    0.811867] ACPI: Thermal Zone [TZ00] (28 C)
[    0.811976] thermal LNXTHERM:01: registered as thermal_zone1
[    0.811979] ACPI: Thermal Zone [TZ01] (30 C)
[    0.812007] ERST: Table is not found!
[    0.812008] GHES: HEST is not enabled!
[    0.812061] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.832462] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.992130] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.027818] Linux agpgart interface v0.103
[    1.027868] agpgart-intel 0000:00:00.0: Intel Ivybridge Chipset
[    1.027971] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.028893] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.028983] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.029780] brd: module loaded
[    1.030193] loop: module loaded
[    1.030272] ahci 0000:00:1f.2: version 3.0
[    1.030287] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.030321] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.043672] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    1.043676] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    1.043680] ahci 0000:00:1f.2: setting latency timer to 64
[    1.083919] scsi0 : ahci
[    1.083967] scsi1 : ahci
[    1.084006] scsi2 : ahci
[    1.084045] scsi3 : ahci
[    1.084082] scsi4 : ahci
[    1.084118] scsi5 : ahci
[    1.084282] ata1: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16100 irq 40
[    1.084286] ata2: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16180 irq 40
[    1.084289] ata3: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16200 irq 40
[    1.084292] ata4: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16280 irq 40
[    1.084296] ata5: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16300 irq 40
[    1.084299] ata6: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16380 irq 40
[    1.084490] Fixed MDIO Bus: probed
[    1.084501] tun: Universal TUN/TAP device driver, 1.6
[    1.084503] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.084532] PPP generic driver version 2.4.2
[    1.084589] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.084599] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.084611] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.084614] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.084640] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.084662] ehci_hcd 0000:00:1a.0: debug port 2
[    1.088533] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.088542] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7d18000
[    1.103623] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.103715] hub 1-0:1.0: USB hub found
[    1.103719] hub 1-0:1.0: 2 ports detected
[    1.103756] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.103767] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.103770] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.103796] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.103814] ehci_hcd 0000:00:1d.0: debug port 2
[    1.107693] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.107703] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7d17000
[    1.119617] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.119699] hub 2-0:1.0: USB hub found
[    1.119702] hub 2-0:1.0: 2 ports detected
[    1.119735] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.119742] uhci_hcd: USB Universal Host Controller Interface driver
[    1.119762] xhci_hcd 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.119783] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.119785] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.119812] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.120160] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.120163] xhci_hcd 0000:00:14.0: irq 16, io mem 0xf7d00000
[    1.120201] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    1.120273] xHCI xhci_add_endpoint called for root hub
[    1.120274] xHCI xhci_check_bandwidth called for root hub
[    1.120288] hub 3-0:1.0: USB hub found
[    1.120294] hub 3-0:1.0: 4 ports detected
[    1.120331] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.120354] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.120400] xHCI xhci_add_endpoint called for root hub
[    1.120401] xHCI xhci_check_bandwidth called for root hub
[    1.120414] hub 4-0:1.0: USB hub found
[    1.120421] hub 4-0:1.0: 4 ports detected
[    1.155667] usbcore: registered new interface driver libusual
[    1.155695] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.156068] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.156073] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.156151] mousedev: PS/2 mouse device common for all mice
[    1.156238] rtc_cmos 00:06: RTC can wake from S4
[    1.156325] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.156350] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.156395] device-mapper: uevent: version 1.0.3
[    1.156437] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.156483] cpuidle: using governor ladder
[    1.156548] cpuidle: using governor menu
[    1.156550] EFI Variables Facility v0.08 2004-May-17
[    1.156656] TCP cubic registered
[    1.156715] NET: Registered protocol family 10
[    1.156945] NET: Registered protocol family 17
[    1.156955] Registering the dns_resolver key type
[    1.157096] PM: Hibernation image not present or could not be loaded.
[    1.157109] registered taskstats version 1
[    1.171379]   Magic number: 0:356:1008
[    1.171488] rtc_cmos 00:06: setting system clock to 2012-06-21 22:57:13 UTC (1340319433)
[    1.172043] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.172046] EDD information not available.
[    1.403610] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.403642] ata5: SATA link down (SStatus 0 SControl 300)
[    1.403660] ata2: SATA link down (SStatus 0 SControl 300)
[    1.403680] ata3: SATA link down (SStatus 0 SControl 300)
[    1.403715] ata6: SATA link down (SStatus 0 SControl 300)
[    1.403754] ata4: SATA link down (SStatus 0 SControl 300)
[    1.404722] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.404729] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff88021185ea00), AE_NOT_FOUND (20110623/psparse-536)
[    1.405006] ata1.00: ATA-8: ST500DM002-1BD142, KC45, max UDMA/133
[    1.405015] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.406349] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.406356] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff88021185ea00), AE_NOT_FOUND (20110623/psparse-536)
[    1.406634] ata1.00: configured for UDMA/133
[    1.406813] scsi 0:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 KC45 PQ: 0 ANSI: 5
[    1.406925] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.406929] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.406962] sd 0:0:0:0: [sda] Write Protect is off
[    1.406964] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.406967] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.406978] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.415599] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.443860]  sda: sda1 sda2 < sda5 sda6 >
[    1.444375] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.445378] Freeing unused kernel memory: 920k freed
[    1.445455] Write protecting the kernel read-only data: 12288k
[    1.448528] Freeing unused kernel memory: 1604k freed
[    1.450892] Freeing unused kernel memory: 1196k freed
[    1.462325] udevd[115]: starting version 175
[    1.472932] atl1c 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.472944] atl1c 0000:02:00.0: setting latency timer to 64
[    1.476617] [drm] Initialized drm 1.1.0 20060810
[    1.479417] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.479425] i915 0000:00:02.0: setting latency timer to 64
[    1.529241] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    1.529245] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.529248] [drm] Driver supports precise vblank timestamp query.
[    1.529652] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.552305] hub 1-1:1.0: USB hub found
[    1.552408] hub 1-1:1.0: 6 ports detected
[    1.599919] atl1c 0000:02:00.0: version 1.0.1.0-NAPI
[    1.667504] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.675498] Refined TSC clocksource calibration: 3092.970 MHz.
[    1.675505] Switching to clocksource tsc
[    1.800117] hub 2-1:1.0: USB hub found
[    1.800205] hub 2-1:1.0: 8 ports detected
[    1.875566] usb 1-1.3: new low-speed USB device number 3 using ehci_hcd
[    1.975611] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input2
[    1.975889] generic-usb 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.3/input0
[    1.975904] usbcore: registered new interface driver usbhid
[    1.975906] usbhid: USB HID core driver
[    2.043527] usb 1-1.4: new low-speed USB device number 4 using ehci_hcd
[    2.093669] fbcon: inteldrmfb (fb0) is primary device
[    2.146664] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input3
[    2.146842] generic-usb 0003:046D:C31D.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:1a.0-1.4/input0
[    2.154201] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input4
[    2.154388] generic-usb 0003:046D:C31D.0003: input,hidraw2: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:1a.0-1.4/input1
[    2.430534] Console: switching to colour frame buffer device 240x67
[    2.433762] fb0: inteldrmfb frame buffer device
[    2.433762] drm: registered panic notifier
[    2.435708] acpi device:4a: registered as cooling_device9
[    2.435846] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.435994] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.436048] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.992283] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.116652] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.160121] udevd[523]: starting version 175
[   15.200476] lp: driver loaded but no devices found
[   15.238102] Adding 8279036k swap on /dev/sda5.  Priority:-1 extents:1 across:8279036k 
[   15.430611] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   15.430841] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.430846] mei 0000:00:16.0: setting latency timer to 64
[   15.430894] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   15.440042] parport_pc 00:0c: reported by Plug and Play ACPI
[   15.440092] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.468984] type=1400 audit(1340319447.799:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=670 comm="apparmor_parser"
[   15.468991] type=1400 audit(1340319447.799:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=628 comm="apparmor_parser"
[   15.469220] type=1400 audit(1340319447.799:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=670 comm="apparmor_parser"
[   15.469235] type=1400 audit(1340319447.799:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=628 comm="apparmor_parser"
[   15.469354] type=1400 audit(1340319447.799:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=670 comm="apparmor_parser"
[   15.469370] type=1400 audit(1340319447.799:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=628 comm="apparmor_parser"
[   15.473386] ppdev: user-space parallel port driver
[   15.528661] lp0: using parport0 (interrupt-driven).
[   15.870451] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.870499] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   15.870518] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   16.161641] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.273394] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   17.135560] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.135608] HDMI status: Codec=3 Pin=6 Presence_Detect=0 ELD_Valid=0
[   17.135665] HDMI status: Codec=3 Pin=7 Presence_Detect=0 ELD_Valid=0
[   17.135717] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   17.135769] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   17.135804] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   17.135840] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   17.135872] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.135906] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   17.135940] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   17.135974] input: HDA Intel PCH Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   17.147723] init: failsafe main process (836) killed by TERM signal
[   17.332513] type=1400 audit(1340319449.663:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=898 comm="apparmor_parser"
[   17.332653] type=1400 audit(1340319449.663:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=895 comm="apparmor_parser"
[   17.332896] type=1400 audit(1340319449.663:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=895 comm="apparmor_parser"
[   17.333031] type=1400 audit(1340319449.663:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=895 comm="apparmor_parser"
[   17.877525] Bluetooth: Core ver 2.16
[   17.877536] NET: Registered protocol family 31
[   17.877537] Bluetooth: HCI device and connection manager initialized
[   17.877539] Bluetooth: HCI socket layer initialized
[   17.877539] Bluetooth: L2CAP socket layer initialized
[   17.877543] Bluetooth: SCO socket layer initialized
[   17.900560] Bluetooth: RFCOMM TTY layer initialized
[   17.900571] Bluetooth: RFCOMM socket layer initialized
[   17.900572] Bluetooth: RFCOMM ver 1.11
[   18.004756] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.004758] Bluetooth: BNEP filters: protocol multicast
[   18.748526] atl1c 0000:02:00.0: irq 45 for MSI/MSI-X
[   18.748610] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[   20.237738] postgres (1186): /proc/1186/oom_adj is deprecated, please use /proc/1186/oom_score_adj instead.
[   22.475093] vboxdrv: Found 4 processor cores.
[   22.475330] vboxdrv: fAsync=0 offMin=0x1e7 offMax=0xe564
[   22.475363] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.475364] vboxdrv: Successfully loaded version 4.1.16 (interface 0x00190000).
[   22.680486] vboxpci: IOMMU not found (not registered)
[   23.746093] init: plymouth-stop pre-start process (1804) terminated with status 1
[   29.285372] eth0: no IPv6 routers present
[   73.117694] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  184.938473] vboxdrv: Found 4 processor cores.
[  184.938779] vboxdrv: fAsync=0 offMin=0x3c1 offMax=0x1c30
[  184.938843] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  184.938845] vboxdrv: Successfully loaded version 4.1.18 (interface 0x00190000).
[  185.148682] vboxpci: IOMMU not found (not registered)
[  273.037714] EXT4-fs (sda6): Unaligned AIO/DIO on inode 19923652 by VirtualBox; performance will be poor.
[  275.792629] device eth0 entered promiscuous mode
[  313.374706] CIFS VFS: default security mechanism requested.  The default security mechanism will be upgraded from ntlm to ntlmv2 in kernel release 3.3
[ 1034.936547] device eth0 left promiscuous mode
[ 1039.449545] vboxnetflt: dropped 38284 out of 40244 packets
[ 1211.442530] usb 1-1.3: USB disconnect, device number 3
[ 1212.919201] usb 1-1.3: new low-speed USB device number 5 using ehci_hcd
[ 1213.017687] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input14
[ 1213.017943] generic-usb 0003:046D:C05A.0004: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.3/input0
[ 1322.380832] CIFS VFS: Server local.dev has not responded in 300 seconds. Reconnecting...
[ 1376.052275] device eth0 entered promiscuous mode

```

Kernel Version:
```

Linux Tachikoma 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

lsmod: 
```

Module                  Size  Used by
des_generic            21415  0 
md4                    12595  0 
nls_utf8               12557  1 
cifs                  287317  2 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  1 
vboxdrv               287130  4 vboxpci,vboxnetadp,vboxnetflt
pci_stub               12622  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_via      51398  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
ppdev                  17113  0 
joydev                 17693  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                87692  0 
serio_raw              13211  0 
parport_pc             32866  1 
mei                    41616  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
i915                  468745  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
atl1c                  41717  0 

```

And BTW, the version of KDE is
```
Platform Version 4.8.4 (4.8.4)
```

---

