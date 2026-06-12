---
title: "can't boot with optical drive attached"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by scottdow4 on 2007-09-09
I built a new machine - ground up - and am having a series of boot issues:

With optical drive attached, boot hangs at ubuntu load screen. No movement in progress
bar. When I unplug the drive, boots fine.

Here's the config:

ABIT IP35-E, Intel P35/ICH9 Chipset
Intel Pentium D 805, Dual Core 2.66GHz@533, 2 X 1Mb cache
2 X 1Gb DDR2 800MHz
EVGA GeForce7600GS
Maxtor 500Gb SATAII/300
Samsung DVD Writer SATA

Booted from iso image Ubuntu 7.04 Desktop i386
formatted entire drive
uploaded all updates

Originally had old CD drives and floppy via IDE, thought that was the conflict, 
bought the SATA DVD, still...

uname -a
Linux scott4 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Unknown device [8086:29c0] (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:29c1] (rev 02)
(prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2937] (rev
02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 4: I/O ports at ff00 [size=32]
        Capabilities: <access denied>

00:1a.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2938] (rev
02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 4: I/O ports at fe00 [size=32]
        Capabilities: <access denied>

00:1a.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2939] (rev
02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 20
        Region 4: I/O ports at fd00 [size=32]
        Capabilities: <access denied>

00:1a.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293c] (rev
02) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 18
        Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation Unknown device [8086:293e] (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:2940] (rev 02)
(prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fdb00000-fdbfffff
        Prefetchable memory behind bridge: 00000000fd800000-00000000fd8fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.1 PCI bridge [0604]: Intel Corporation Unknown device [8086:2942] (rev 02)
(prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fd700000-fd7fffff
        Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.2 PCI bridge [0604]: Intel Corporation Unknown device [8086:2944] (rev 02)
(prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1d.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2934] (rev
02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 21
        Region 4: I/O ports at fc00 [size=32]
        Capabilities: <access denied>

00:1d.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2935] (rev
02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 20
        Region 4: I/O ports at fb00 [size=32]
        Capabilities: <access denied>

00:1d.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2936] (rev
02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 18
        Region 4: I/O ports at fa00 [size=32]
        Capabilities: <access denied>

00:1d.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293a] (rev
02) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
(prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation Unknown device [8086:2918] (rev 02)
        Subsystem: Intel Corporation Unknown device [8086:2918]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:1f.2 IDE interface [0101]: Intel Corporation Unknown device [8086:2921] (rev 
02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 0: I/O ports at f900 [size=8]
        Region 1: I/O ports at f800 [size=4]
        Region 2: I/O ports at f700 [size=8]
        Region 3: I/O ports at f600 [size=4]
        Region 4: I/O ports at f500 [size=16]
        Region 5: I/O ports at f400 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus [0c05]: Intel Corporation Unknown device [8086:2930] (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 11
        Region 0: Memory at fdffd000 (64-bit, non-prefetchable) [size=256]
        Region 4: I/O ports at 0500 [size=32]

00:1f.5 IDE interface [0101]: Intel Corporation Unknown device [8086:2926] (rev 
02) (prog-if 85 [Master SecO PriO])
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 0: I/O ports at f200 [size=8]
        Region 1: I/O ports at f100 [size=4]
        Region 2: I/O ports at f000 [size=8]
        Region 3: I/O ports at ef00 [size=4]
        Region 4: I/O ports at ee00 [size=16]
        Region 5: I/O ports at ed00 [size=16]
        Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7600 GS]
[10de:0392] (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device [3842:c541]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 7
        Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        Region 5: I/O ports at af00 [size=128]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 IDE interface [0101]: JMicron Technologies, Inc. Unknown device [197b:2368]
(prog-if 85 [Master SecO PriO])
        Subsystem: JMicron Technologies, Inc. Unknown device [197b:2368]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at df00 [size=8]
        Region 1: I/O ports at de00 [size=4]
        Region 2: I/O ports at dd00 [size=8]
        Region 3: I/O ports at dc00 [size=4]
        Region 4: I/O ports at db00 [size=16]
        [virtual] Expansion ROM at fde00000 [disabled] [size=64K]
        Capabilities: <access denied>

04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device
[11ab:4364] (rev 13)
        Subsystem: ABIT Computer Corp. Unknown device [147b:1085]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping-
SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at fddfc000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at be00 [size=256]
        [virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by Keith_Beef on 2007-09-11
Have you tried [this]("http://ubuntuforums.org/showpost.php?p=3315183&postcount=3")?

Beef

---

