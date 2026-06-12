---
title: "NVidia 8800GTS and 100.14.09 driver"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by Shinobi326 on 2007-06-15
I'm thinking about upgrading from 9755 driver to the new 100.14.09 driver in hopes to get better performance out of my dual 8800gts video cards.  Before I do this I'm curious about my output of my "lspci -v" (below).  More specifically I'm a little concerned about the last few sections of this report like 

> 06:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0421

Given how quirky the 8800GTS cards are with Linux/Ubuntu at the moment (at least in my experience) I could not get the drivers running using the restricted drivers or Envy.  However, recently there was some new upgrades (within last week?) and now I'm showing "NVIDIA restricted driver - In Use" in the restricted drivers.  Am I really using the restricted drivers even though I did a manual compile of the drivers by downloading the .9755 package from NVIDIA and doing it manually?

Any other 8800GTS owners out there upgraded to 100.14.09?  What are your experiences with the newer drivers?

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: d7e00000-d7efffff
        Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: d7f00000-d7ffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: d8000000-dbefffff
        Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
        Capabilities: <access denied>

00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at ac00 [size=32]
        I/O ports at 0600 [size=64]
        I/O ports at 0700 [size=64]
        Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at d7dfe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at d7dffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at a400 [size=256]
        I/O ports at a000 [size=256]
        Memory at d7dfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at 9c00 [size=8]
        I/O ports at 9880 [size=4]
        I/O ports at 9800 [size=8]
        I/O ports at 9480 [size=4]
        I/O ports at 9400 [size=16]
        Memory at d7dfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at 9080 [size=8]
        I/O ports at 9000 [size=4]
        I/O ports at 8c00 [size=8]
        I/O ports at 8880 [size=4]
        I/O ports at 8800 [size=16]
        Memory at d7dfb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
        Memory behind bridge: dbf00000-dbffffff

00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at d7dfa000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8480 [size=8]
        Capabilities: <access denied>

00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: <access denied>

00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: dc000000-dfffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 819f
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d7effc00 (64-bit, non-prefetchable) [size=128]
        Memory at d7ef8000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at bc00 [size=128]
        Expansion ROM at d7e00000 [disabled] [size=512K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at d7ffc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at c800 [size=256]
        Expansion ROM at d7fc0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0421
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at da000000 (32-bit, non-prefetchable) [size=16M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at d8000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at dc00 [size=128]
        [virtual] Expansion ROM at dbee0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at dbfff800 (32-bit, non-prefetchable) [size=2K]
        Memory at dbff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0421
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at df000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at ec00 [disabled] [size=128]
        [virtual] Expansion ROM at defe0000 [disabled] [size=128K]
        Capabilities: <access denied>
```

My current system:
AMD64 3200 CPU
NForce4 ASUS MB
2 Gig ram
Dual NVIDIA 8800GTS video cards
Dual Raptor 74gig drives (one Windows, one Ubuntu)

---

### Post by lamadredelsapo on 2007-06-15
Did you compile the latest driver? Or just installed it from the repos?

---

### Post by Shinobi326 on 2007-06-15
I manually compiled the .9755 driver because it was the only thing that would work.  I tried numerous times to follow the more "upgrade friendly" approaches like using the restricted drivers or from the repos but neither worked.  Envy scripts didn't even work for my 8800GTS.:(

---

### Post by Shinobi326 on 2007-06-28
In case anyone was scouring through the forums for answers I wanted to post my results.

I went ahead and recently upgraded to actually the new 100.14.11 version instead of the 100.14.09.  I do notice slightly more snappiness and since manually compiling the new driver automatically removes the prior version it was actually quite painless to do (using the SH command line method from the Nvidia website).

So my vote is that if you already have manually compiled drivers, go ahead and upgrade to at least make sure you have the latest and greatest possible performance and compatibility.

---

