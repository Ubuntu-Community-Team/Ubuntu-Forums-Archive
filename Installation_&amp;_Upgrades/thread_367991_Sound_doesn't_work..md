---
title: "Sound doesn't work."
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by hvymtlsteve on 2007-02-22
So, I installed the OS this morning and had the issue that X wouldn't run because it didn't like the driver that was automatically selected for my NVIDIA onboard graphics. That was fixed by opening up the config file and changing the driver to "vesa."

Now, it seems that I'm getting issues with the sound:
When I open gedit through my shell, I get a bunch of errors that appear to be sound related:

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
 
Also when I try to open the DVD Player or Audio Recorder programs included in the OS, I get errors like: "unable to access sound server."

Do I need something similar to what I did for graphics?
If so, is there a generic driver already on the computer somewhere that I can just substitute in?

Thanks,


Steve

---

### Post by Kateikyoushi on 2007-02-22
With following these steps you can fairly easily get the soundcard to work. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

If you get stuck post the output of the commands.

---

### Post by hvymtlsteve on 2007-02-22
Thanks for that! BTW your username is interesting :)

---

### Post by geruss on 2007-02-23
I heve install UBUNTU 6.10 edgy on my laptop ASUS A9T sound card chipset SI7012 driver alsa intel8x0, but there is no sound.
I foun instructions for install the alsa driver here:

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

But its not work... If some one know how too fix this problem please tell me!!!

---

### Post by Kateikyoushi on 2007-02-23
What is the output of this ?

```
lspci -v
```

---

### Post by geruss on 2007-02-23
here is the output of lspci -v


geruss@geruss-laptop:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: df600000-df6fffff
        Prefetchable memory behind bridge: cd500000-dd4fffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
        Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 128
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1816
        Flags: medium devsel, IRQ 177
        I/O ports at e400 [size=256]
        I/O ports at e000 [size=128]
        Capabilities: <access denied>

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1193
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 185
        Memory at dfffc000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 193
        Memory at dfffd000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 201
        Memory at dfffe000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 209
        Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1455
        Flags: bus master, medium devsel, latency 64, IRQ 217
        I/O ports at d800 [size=256]
        Memory at dfffb000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at dffc0000 [disabled] [size=128K]
        Capabilities: <access denied>

00:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 168, IRQ 169
        Memory at 24000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 217
        Memory at dfffa000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:09.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at dfffa800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1197
        Flags: medium devsel, IRQ 10
        Memory at dfffac00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1921
        Flags: 66MHz, medium devsel, IRQ 11
        BIST result: 00
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at df6e0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at bc00 [size=128]
        Capabilities: <access denied>

---

### Post by geruss on 2007-02-24
No body cant help me!? Please, tell me whot to do. Or maby my laptop dont supported by ubuntu!?

---

### Post by AlexanderTumanovsky on 2007-05-14
Same problem... Asus A9T, Ubuntu 7.04... No Sound, but sound card detected properly.
Already tried alot of things, which was writen in other forums, but no solution found :(
Anybody, please help

---

### Post by gmh on 2007-05-15
I have the same problem. Have gone through everything I can find on the forums to get sound working. It seems like lots of folk are having sound issues on laptops using the HDA intel chipset. My sound card is recognized but no luck on sound. I guess we wait for some kind of patch to fix this.

---

### Post by tommawat on 2007-05-15
hi, my sound doesnt work as well...i am sure it did before, but i cannot get it to start again.  i typed the lspci -v and got this:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
        Subsystem: Dell Unknown device 0195
        Flags: bus master, medium devsel, latency 64
        Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: e4300000-e43fffff
        Prefetchable memory behind bridge: e8000000-efffffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 8100 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Dell Unknown device 0195
        Flags: bus master, medium devsel, latency 128, IRQ 18
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 2800 [size=16]

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: Dell Unknown device 0195
        Flags: medium devsel, IRQ 17
        I/O ports at 1000 [size=256]
        I/O ports at 2400 [size=128]
        Capabilities: <access denied>

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Dell Unknown device 0195
        Flags: bus master, medium devsel, latency 173, IRQ 17
        I/O ports at 1400 [size=256]
        I/O ports at 2480 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 0195
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at e4000000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 0195
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at e4001000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 0195
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at e4002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
        Subsystem: Dell Unknown device 0195
        Flags: bus master, medium devsel, latency 173, IRQ 22
        I/O ports at 1800 [size=256]
        Memory at e4003000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 68000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0a.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: Dell Unknown device 0195
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at e4004000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 60000000-63fff000 (prefetchable)
        Memory window 1: 64000000-67fff000
        I/O window 0: 00001c00-00001cff
        I/O window 1: 00002000-000020ff
        16-bit legacy interface ports at 0001

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 0195
        Flags: 66MHz, medium devsel, IRQ 7
        BIST result: 00
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e4300000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 9000 [size=128]
        Capabilities: <access denied>

any ideas?

---

### Post by al_azif on 2008-03-11
Same laptop, ubuntu 7.10, same problems...

---

