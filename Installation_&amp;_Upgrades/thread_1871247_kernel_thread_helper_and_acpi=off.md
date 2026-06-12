---
title: "kernel_thread_helper and acpi=off"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by zeero_k on 2011-10-28
I recently upgraded my desktop to 11.10 from 11.04. Upgrade went smoothly until time to reboot. When booting it got stuck at “kernel_thread_helper+0x6/0x10” just after GRUB. From reading other threads I learned that this could be fixed by using the acpi=off boot option, and that other people were having the same problem. This allowed me to boot, but the side effects of using acpi=off are not acceptable, for two main reasons:

1. No Hyperthreading support (i.e. only one CPU core available)
2. The system does not actually turn off when using the shutdown command. (I often use a remote or delayed shutdown command, acpi=off prevents this)

I tried various other boot options, such as acpi=ht, pci=noapci, acpi=oldboot, acpi_osi=linux, but these all still cause the system to hang at kernel_thread_helper. I tried booting from USB stick with a fresh copy of Ubuntu, same problem. I tried toggling the PnP OS setting in by BIOS, no luck. My hardware is not brand new, but not that old either (Pentium 4 2.8GHz dual core, Nvidia GeForce FX 5700).

I can, however, boot into an older kernel (2.6.38-11-generic) and everything seems to work. So, a few questions:

1. Has anyone found any other boot options that fix the problem without being as severe as acpi=off?

2. Is there any hope of having this problem fixed in an update or later version, or am I doomed to be stuck forever with 11.04 (or 11.10 using older kernel) on this machine?

3. What are the consequences of booting into an earlier kernel version? So far, I have not found any issues with this, but I wonder if some software will complain or break or if there are unfixed security issues. Should I just set the older kernel as my default and forget about it?

Thanks for the help.
   ~0K

---

### Post by MAFoElffen on 2011-10-28
> **zeero_k said:**
> I recently upgraded my desktop to 11.10 from 11.04. Upgrade went smoothly until time to reboot. When booting it got stuck at &#8220;kernel_thread_helper+0x6/0x10&#8221; just after GRUB. From reading other threads I learned that this could be fixed by using the acpi=off boot option, and that other people were having the same problem. This allowed me to boot, but the side effects of using acpi=off are not acceptable, for two main reasons:

1. No Hyperthreading support (i.e. only one CPU core available)
2. The system does not actually turn off when using the shutdown command. (I often use a remote or delayed shutdown command, acpi=off prevents this)

I tried various other boot options, such as acpi=ht, pci=noapci, acpi=oldboot, acpi_osi=linux, but these all still cause the system to hang at kernel_thread_helper. I tried booting from USB stick with a fresh copy of Ubuntu, same problem. I tried toggling the PnP OS setting in by BIOS, no luck. My hardware is not brand new, but not that old either (Pentium 4 2.8GHz dual core, Nvidia GeForce FX 5700).

I can, however, boot into an older kernel (2.6.38-11-generic) and everything seems to work. So, a few questions:

1. Has anyone found any other boot options that fix the problem without being as severe as acpi=off?

2. Is there any hope of having this problem fixed in an update or later version, or am I doomed to be stuck forever with 11.04 (or 11.10 using older kernel) on this machine?

3. What are the consequences of booting into an earlier kernel version? So far, I have not found any issues with this, but I wonder if some software will complain or break or if there are unfixed security issues. Should I just set the older kernel as my default and forget about it?

Thanks for the help.
   ~0K
Yes- I first found this problem and worked on the work-around for it back in May for natty...  So, yes, I know the pro's and con's of rolling back the kernel and using acpi=off.

The latest iteration my explanation of this workaround is in my post here:
[http://ubuntuforums.org/showpost.php?p=11403846&postcount=13](http://ubuntuforums.org/showpost.php?p=11403846&postcount=13)

Besides the 2 issues you brought up, then there are HDD issues, screensaver issues, sleep/suspend/wake issues, etc.

The kernel roll-back brings other problems.  The enhanced desktop in 11.10 and patches in kernel 3.x were written for each other.  That is still just like running Natty with a Meerkat kernel (before Unity)... Things don't work the same- not because they are "disabled" but rather because they just aren't there to enable those new features.  Does that make sense to you?

---

### Post by zeero_k on 2011-10-29
Thanks for the tips. I tried adding vga=0x0318 to the boot options, per your suggested work-around, but I just got stuck at a black screen, and couldn't switch to any virtual terminals. I'm a little confused about the "#GFXMODE=..." line, it seems like it is commented out and shouldn't have any effect.

I'm not convinced that this is a video issue. Everything worked fine in Natty. Is there a way to boot into a console without the framebuffer, to rule out video issues? 

Also, by the way, I think I have found at least one problem with booting into the older kernel. When I leave the machine alone for a while and the screen goes to sleep, I can't get it back; just a black screen and a mouse pointer that moves but nothing to click on. In this case I can access the virtual terminals, but I can't find a way to get vt7 back other than rebooting. I'm using classic Gnome, so maybe I won't have any "enhanced desktop" issues.

Anyway, let me know if you have any other suggestions. Otherwise, I'm thinking that I might have to go back to Natty and never upgrade again.
   ~0K

---

### Post by zeero_k on 2011-11-03
UPDATE:

I found that the "nolapic" option will allow me to boot with the new kernel. This fixes the shutdown problem, but still no hyperthreading :(

---

### Post by zeero_k on 2011-11-19
ANOTHER UPDATE:

This is still a frustrating problem, but I have narrowed it down a bit:

1. Booting still hangs when using the "single" option from grub, so I think that rules out graphics issues.
2. It seems that booting hangs before logging is started, so there is no helpful info in syslog or dmesg.
3. If I go into the BIOS and disable hyperthreading support, I can boot fine with no boot options!

Any ideas about how I can get hyper-threading back? Without it my system is sluggish, hesitates when I browse through menus, and audio skips :(

Here is the output of cat /proc/cpuinfo:
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 9
cpu MHz		: 2793.060
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips	: 5586.12
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

```

and sudo lspci -vvnn:

```

00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
	Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: fc800000-fe8fffff
	Prefetchable memory behind bridge: d4700000-f46fffff
	Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at cc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at d000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 23
	Region 0: Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000bfff
	Memory behind bridge: fe900000-feafffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ffa0 [size=16]
	Region 5: Memory at 80000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at ec00 [size=8]
	Region 1: I/O ports at e800 [size=4]
	Region 2: I/O ports at e400 [size=8]
	Region 3: I/O ports at e000 [size=4]
	Region 4: I/O ports at dc00 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 3
	Region 4: I/O ports at c800 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV36.2 [GeForce FX 5700] [10de:0342] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device [1462:9480]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 248 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at fe8e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_96, nvidia_173_updates, nvidia_173, nouveau, nvidiafb

02:01.0 RAID bus controller [0104]: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller [1095:0680] (rev 02)
	Subsystem: Silicon Image, Inc. Winic W-680 (Silicon Image 680 based) [1095:3680]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at bc00 [size=8]
	Region 1: I/O ports at b800 [size=4]
	Region 2: I/O ports at b400 [size=8]
	Region 3: I/O ports at b000 [size=4]
	Region 4: I/O ports at ac00 [size=16]
	Region 5: Memory at feaffc00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at fea00000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: pata_sil680
	Kernel modules: pata_sil680

02:02.0 Multimedia audio controller [0401]: Aureal Semiconductor Vortex 2 [12eb:0002] (rev fe)
	Subsystem: Aureal Semiconductor AU8830 Vortex 3D Digital Audio Processor [12eb:0088]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (1000ns min, 3000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fea80000 (32-bit, non-prefetchable) [size=256K]
	Region 1: I/O ports at a800 [size=8]
	Region 2: I/O ports at a400 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: au8830
	Kernel modules: snd-au8830

02:04.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) [104c:8020] (prog-if 10 [OHCI])
	Subsystem: Accton Technology Corporation Device [1113:1394]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at feaff000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at feaf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 01)
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:302f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (2000ns min, 14000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at a000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

zeerok@milkview:~$ sudo lspci -vvnn
[sudo] password for zeerok: 
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
	Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [e4] Vendor Specific Information: Len=06 <?>
	Capabilities: [a0] AGP version 3.0
		Status: RQ=32 Iso- ArqSz=2 Cal=2 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=2 SBA+ AGP+ GART64- 64bit- FW- Rate=x8
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: fc800000-fe8fffff
	Prefetchable memory behind bridge: d4700000-f46fffff
	Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at cc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at d000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 23
	Region 0: Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000bfff
	Memory behind bridge: fe900000-feafffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ffa0 [size=16]
	Region 5: Memory at 80000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at ec00 [size=8]
	Region 1: I/O ports at e800 [size=4]
	Region 2: I/O ports at e400 [size=8]
	Region 3: I/O ports at e000 [size=4]
	Region 4: I/O ports at dc00 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:4246]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 3
	Region 4: I/O ports at c800 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV36.2 [GeForce FX 5700] [10de:0342] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device [1462:9480]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 248 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at fe8e0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [44] AGP version 3.0
		Status: RQ=32 Iso- ArqSz=0 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
		Command: RQ=32 ArqSz=2 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x8
	Kernel driver in use: nvidia
	Kernel modules: nvidia_96, nvidia_173_updates, nvidia_173, nouveau, nvidiafb

02:01.0 RAID bus controller [0104]: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller [1095:0680] (rev 02)
	Subsystem: Silicon Image, Inc. Winic W-680 (Silicon Image 680 based) [1095:3680]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at bc00 [size=8]
	Region 1: I/O ports at b800 [size=4]
	Region 2: I/O ports at b400 [size=8]
	Region 3: I/O ports at b000 [size=4]
	Region 4: I/O ports at ac00 [size=16]
	Region 5: Memory at feaffc00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at fea00000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-
	Kernel driver in use: pata_sil680
	Kernel modules: pata_sil680

02:02.0 Multimedia audio controller [0401]: Aureal Semiconductor Vortex 2 [12eb:0002] (rev fe)
	Subsystem: Aureal Semiconductor AU8830 Vortex 3D Digital Audio Processor [12eb:0088]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (1000ns min, 3000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fea80000 (32-bit, non-prefetchable) [size=256K]
	Region 1: I/O ports at a800 [size=8]
	Region 2: I/O ports at a400 [size=8]
	Capabilities: [dc] Power Management version 1
		Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: au8830
	Kernel modules: snd-au8830

02:04.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) [104c:8020] (prog-if 10 [OHCI])
	Subsystem: Accton Technology Corporation Device [1113:1394]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at feaff000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at feaf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 1
		Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 01)
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:302f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (2000ns min, 14000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at a000 [size=64]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-
	Kernel driver in use: e100
	Kernel modules: e100


```

Anything else that would be helpful to include?

   ~0K

---

### Post by zeero_k on 2011-12-09
Yay! I found a boot option that seems to fix the issue and lets me now run with hyperthreading:

```

processor.nocst=1

```

Using this kernel option in the GRUB configuration lets me boot with hyperthreading. I get my 2 cores, the system is snappy and responsive, and audio doesn't skip anymore! So far, no apparent side-effects.

The issue seems to be specific to my motherboard, which is an Intel D865GBF. I found the tip here:
[http://us.generation-nt.com/answer/bug-632734-isnt-another-sign-problems-d865gbf-motherboards-help-204639081.html](http://us.generation-nt.com/answer/bug-632734-isnt-another-sign-problems-d865gbf-motherboards-help-204639081.html)

Some vague information about what this option does is here:
[http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/re91.html](http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/re91.html)

   ~0K

---

### Post by zeero_k on 2012-05-01
Final Update:

The issue seems to have been solved in 12.04! I no longer need to use processor.nocst=1 to boot. I think that boot option made my system run slower and standby/hibernate never worked proplerly. 12.04 is running much better and standy works like a dream (pun not quite intentional).

I highly suggest that anyone using one of these Intel motherboards and having to boot with processor.nocst=1 upgrade to 12.04 ASAP.

As a side note, I decided to try Kubuntu this time around, since I am not fond of Unity. I must say I am impressed and now consider myself Konverted.

   ~0K

---

