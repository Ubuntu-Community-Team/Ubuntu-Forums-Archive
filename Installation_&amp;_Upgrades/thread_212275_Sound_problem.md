---
title: "Sound problem"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by fycloops on 2006-07-09
I get continuous white noise. With Alsamixer I can turn down the CD volume which reduces the hissing significantly but not all the way.

I have oboard sound on my GA-K8N Ultra SLI motherboard (NFORCE4).

So after a lot of research I managed to install the Nforce drivers from the Nvidia website. No change. I think while driver is installed I now need to configure Ubuntu to use it. Don't know how to do that...

Anyway here is the output from:

aplay -l

ALSA lib conf.c:1592:(snd_config_load1) _toplevel_:25:0:Unexpected char
ALSA lib conf.c:2837:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2700:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3066:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:230: control open (0): Invalid argument

lspci -v

0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: Giga-byte Technology: Unknown device 5000
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at e400 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 50
        Memory at f5003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at f5005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: Giga-byte Technology: Unknown device ae01
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at a800 [size=256]
        I/O ports at ac00 [size=256]
        Memory at f5006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology: Unknown device 5002
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology: Unknown device b003
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at c800 [size=16]
        Memory at f5001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology: Unknown device b003
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at dc00 [size=16]
        Memory at f5002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: f2000000-f4ffffff

0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Giga-byte Technology: Unknown device e000
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        Memory at f5004000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e000 [size=8]
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f0000000-f1ffffff
        Prefetchable memory behind bridge: 0000000050000000-0000000050000000
        Capabilities: <available only to root>

0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Capabilities: <available only to root>

0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Capabilities: <available only to root>

0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: e0000000-efffffff
        Prefetchable memory behind bridge: 0000000050100000-0000000050100000
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

0000:01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: LeadTek Research Inc. Leadtek PVR 2000
        Flags: bus master, medium devsel, latency 32, IRQ 82
        Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:01:08.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: LeadTek Research Inc. Leadtek PVR 2000
        Flags: bus master, medium devsel, latency 32, IRQ 82
        Memory at f3000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 58
        Memory at f4004000 (32-bit, non-prefetchable) [size=2K]
        Memory at f4000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 19)
        Subsystem: Giga-byte Technology Marvell 88E8053 Gigabit Ethernet Controller (Gigabyte)
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at f1000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 9000 [size=256]
        Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2) (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology: Unknown device 3125
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Memory at e0000000 (64-bit, prefetchable) [size=128M]
        Memory at ec000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at 50100000 [disabled] [size=128K]
        Capabilities: <available only to root>


I am hoping someone can make sense of this. I really want to use Ubuntu!


Thanks,

Fycloops

---

### Post by fycloops on 2006-07-10
OK. Now ALSAmixer is not working...

Output:
ALSA lib conf.c:1592:(snd_config_load1) _toplevel_:25:0:Unexpected char
ALSA lib conf.c:2837:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2700:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3066:(snd_config_update_r) hooks failed, removing configuration

alsamixer: function snd_ctl_open failed for default: Invalid argument

I can play my music! HELP!!!

Fycloops

---

