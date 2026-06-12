---
title: "No sound on Acer Travel Mate 6592 - Ubuntu 7.10"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by zer0_mah on 2008-02-26
Hi everyone,
This is my first every post in ubuntuforums.

I got sound problem on my laptop. 

I have TravelMate 6592 Acer laptop and i installed Ubuntu 7.10 last week. (amazing ubuntu.. rock! :guitar: )
I installed right way and haven't got any problem or error messages during the installation time.

But, i noticed later that there is no sound on my laptop. I have lack of knowledge in Linux and please help me out how to get the sound back on my laptop.

Thank you for your time.

---

### Post by Partyboi2 on 2008-02-26
[This]("https://help.ubuntu.com/community/SoundTroubleshooting") will help you troubleshoot

---

### Post by zer0_mah on 2008-03-17
> **Partyboi2 said:**
> [This]("https://help.ubuntu.com/community/SoundTroubleshooting") will help you troubleshoot

Hi,

I tried to follow the instructions from "sound Trouble Shooting". But i don't understand fully.
I think i made a mistake and i got another problem. Please help me out ....

[SIZE="4"]For first step: i got this:[/SIZE]
> aplay -l
```

aplay: device_list:204: no soundcards found...

```

[SIZE="4"]For second step: i got his:[/SIZE]
> 
lspci -v

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, fast devsel, latency 0
        Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at fc300000 (32-bit, non-prefetchable) [size=128K]
        Memory at fc325000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1840 [size=32]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1860 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1880 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at fc526400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at fc320000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f6000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c8000000-c9ffffff
        Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: fa000000-fbffffff
        Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 18a0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 18c0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 18e0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at fc526800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0f, sec-latency=32
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: fc200000-fc2fffff
        Prefetchable memory behind bridge: 0000000040000000-0000000047ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1c00 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 1c50 [size=8]
        I/O ports at 1c44 [size=4]
        I/O ports at 1c48 [size=8]
        I/O ports at 1c40 [size=4]
        I/O ports at 1c30 [size=16]
        I/O ports at 1c20 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: medium devsel, IRQ 5
        Memory at 48000000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c60 [size=32]

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1000
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c8000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

0a:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at fc204000 (32-bit, non-prefetchable) [size=4K]
        Memory at fc208000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

0a:04.1 CardBus bridge: O2 Micro, Inc. Unknown device 7175 (rev 21)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 20
        Memory at fc205000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0b, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 4c000000-4ffff000
        I/O window 0: 00006000-000060ff
        I/O window 1: 00006400-000064ff
        16-bit legacy interface ports at 0001

0a:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: slow devsel, IRQ 20
        Memory at fc209000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0a:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: slow devsel, IRQ 7
        Memory at fc206000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Capabilities: <access denied>

0a:05.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 21
        Memory at fc207000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0c, subordinate=0f, sec-latency=176
        Memory window 0: 44000000-47fff000 (prefetchable)
        Memory window 1: 50000000-53fff000
        I/O window 0: 00006800-000068ff
        I/O window 1: 00006c00-00006cff
        16-bit legacy interface ports at 0001

0a:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 011a
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at fc208800 (32-bit, non-prefetchable) [size=2K]
        Memory at fc200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

> lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
0a:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:04.1 CardBus bridge: O2 Micro, Inc. Unknown device 7175 (rev 21)
0a:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
0a:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
0a:05.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
0a:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

[SIZE="4"]I am stuck there at step three:[/SIZE]
I went to this web site :
[http://www.alsa-project.org/alsa-doc/]("http://www.alsa-project.org/alsa-doc/")
and looked for my driver or sound card.
But i don't know my driver name and model or something. 

Please give me more instructions how to do it.

Thanks


[SIZE="4"]Other system outputs, hope this helps to solve my problem[/SIZE]
 > cat /proc/asound/cards
```
--- no soundcards ---
```
> alsamixer
```
alsamixer: function snd_ctl_open failed for default: No such device
```

I am aslo getting Error message when i click on "Volume" icon on panel.
```
No Volume control GStreamer plugins and/or devices found.
```

System/Administrations/Restricted Drivers Manager
```
Your hardware does not need any restricted drivers.
```

System/Preferences/Sound
```

Deivces/Sound Events/Sound playback:
ALSA - Advanced Linux Sound Architecture


Deivces/Music and Movies/Sound playback:
ALSA - Advanced Linux Sound Architecture

Deivces/Audio Conferencing/Sound playback:
ALSA - Advanced Linux Sound Architecture

Deivces/Audio Conferencing/Sound Capture:
ALSA - Advanced Linux Sound Architecture

Deivces/Default Mixer Tracks/Device:
There is no list

```

---

### Post by zer0_mah on 2008-03-24
Please, help me out here!
Anyone?

Thanks

---

### Post by iclements on 2008-03-25
I had the same symptoms - and hage teh same sound adapter.
The problem was resolved when I followed the instructions at the following location:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

