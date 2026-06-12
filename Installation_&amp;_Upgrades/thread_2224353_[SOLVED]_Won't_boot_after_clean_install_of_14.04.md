---
title: "[SOLVED] Won't boot after clean install of 14.04"
date: 2014-05-15
forum: Installation &amp; Upgrades
---

### Post by fredbird67 on 2014-05-15
About 3 weeks or so ago, I backed up everything and did a _clean_ upgrade to Xubuntu 14.04.  At first, it had problems booting in that it would display some gibberish on-screen (don't remember the exact words) and would hang, but I could correct that by going into recovery mode, select grub, and then reboot (or whatever that first option is), and then it would boot normally.  Every once in a while I'd have to go through this rigamarole again, but I'd be able to get it to boot.  Well, now the only way I can do so is via recovery mode, and when doing that, it won't let me use the full width of my widescreen monitor.  And when I try to boot normally, I can't.  BTW, Xubuntu is the _only_ OS I'm running on my system, so I'm not dealing with WinD'OH!s at all here.

Right now I'm running Greenie, a Lubuntu variant, via a USB stick (I've been thinking about changing from Xfce to LXDE as my preferred desktop).  It has Sysinfo installed by default, and here's what all it has to say about my system, which is a 64-bit system I built myself about a year or so ago.

SYSTEM:
Release:  Ubuntu 14.04 (trusty)
GNOME:  3.8.4 (Ubuntu 2014-03-17)
Kernel:  3.13.0-24-generic (#46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014)
OS Type:  Linux
GCC version:  no gcc detected
Xorg version:  1.15.1 (16 April 2014  01:40:08PM)
Hostname:  lubuntu (remember, this is from the USB stick, although irrelevant to this problem I'm having)

-------------------------

CPU:
Vendor:  AuthenticAMD
CPUs:  4
Model name:  AMD FX(tm)-4100 Quad-Core Processor
Frequency:  1400.000 MHz
L2 cache:  2048 KB
Bogomips:  7199.77
Numbering:  family(21) model(1) stepping(2)
Flags:  fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold

-------------------------

MEMORY:
Memory total:  3984 MiB (91% free)
Swap total:  6035 MiB (100% free)
Cached:  481 MiB
Active:  421 MiB
Inactive:  421 MiB

-------------------------

STORAGE:
SCSI device:  scsi0
Vendor:  ATA
Model:  ST3100528AS

SCSI device:  scsi1
Vendor:  HL-DT-ST
Model:  DVDRRW GSA-H30L

SCSI device:  scsi6
Vendor:  HitachiG
Model:  ST

SCSI device:  scsi7
Vendor:  Verbatim
Model:  STORE N GO

-------------------------

HARDWARE:

Host bridge:
Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
Subsystem:  Micro-Star International Co., Ltd. [MSI] Device 7693

PCI bridge(s):
Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) (prog-if 00 [Normal decode])
Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) (prog-if 00 [Normal decode])
Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A) (prog-if 00 [Normal decode])
Advanced Micro Devices, Inc. [AMD/ATI] BSx00 PCI to PCI bridge (rev 40) (prog-if 01 [Subtractive decode])
Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])

ISA bridge:
Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
Subsystem:  Micro-Star International Co., Ltd. [MSI] Device 7693

IDE interface:
Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE controller (rev 40) (prog-if 8a [Master SecP PriP])
Subsystem:  Micro-Star International Co., Ltd. [MSI] Device 7693

-------------------------

GRAPHICS CARD:

VGA compatible controller:
NVIDIA Corporation NV44 [GeForce 6200 TurboCache] (rev a1) (prog-if-00 [VGA controller])
Subsystem:  XFX Pine Group Inc. Device 2143

-------------------------

SOUND CARD:

Multimedia audio controller:
Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
Subsystem:  Micro-Star International Co., Ltd. [MSI] Device d693

-------------------------

ETHERNET CONTROLLER:

Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)
Subsystem:  Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet Controller

And that's all she wrote.  Any ideas how to get it to consistently boot given the above hardware specs?  Or, is there something I can download and install to fix this?

Thanx in advance,
Fred in St. Louis

---

### Post by fredbird67 on 2014-05-16
OK, I started digging around online to find an answer to this one, and found that the error message (no caching page found...or something like that) appears only when some form of external storage is plugged in when booting up.  And then I just happened to remember that I have an external hard drive I had connected to the system all the time.  So I tried unplugging it...and VOILA, my system now boots up! :D

---

