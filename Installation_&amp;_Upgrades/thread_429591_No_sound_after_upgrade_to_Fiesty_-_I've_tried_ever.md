---
title: "No sound after upgrade to Fiesty - I've tried everything"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Armor on 2007-05-01
I know there are many posts regarding this same problem and I've gone through all of them to no avail. Please help! There is no sound at all, and I've tried everything. Can't get anywhere with Alsa, tried that Comprehensive Sound Card thread and couldn't get anywhere with that, either. Linux noob here - plz take a look

> tana@tana-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
tana@tana-desktop:~$ 



> tana@tana-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tana@tana-desktop:~$ 



> tana@tana-desktop:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
        Flags: bus master, medium devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: dfe00000-dfefffff
        Prefetchable memory behind bridge: cfd00000-dfcfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
        Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
        Flags: bus master, medium devsel, latency 128
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Elitegroup Computer Systems Unknown device aa51
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at dffdc000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at dffdd000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at dffde000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at dffdf000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: Silicon Integrated Systems [SiS] SiS900 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at e400 [size=256]
        Memory at dffdb000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at dffa0000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
        Subsystem: Agere Systems Unknown device 044c
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at dffffc00 (32-bit, non-prefetchable) [size=256]
        I/O ports at e000 [size=8]
        I/O ports at d800 [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (prog-if 00 [VGA])
        Flags: 66MHz, medium devsel, IRQ 11
        BIST result: 00
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at dfee0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at cc00 [size=128]
        Capabilities: <access denied>

tana@tana-desktop:~$ 


It appears that Ubuntu Fiesty is detecting the sound card. Top right corner does not show that the sound is muted. Everything unmuted in Alsamixer. Any ideas at all?

---

### Post by Armor on 2007-05-01
Anyone? Ideas?

---

### Post by Armor on 2007-05-02
Plz Help!

---

### Post by junky on 2007-05-02
Open your sound mixer, unhide the External Amplifier option, and uncheck the box

---

### Post by GnuSense on 2007-05-04
That's a little concise, junky, since there are gobs of mixers available on Ubuntu.  The one you want is:

  gnome-volume-control

Go to the SWITCHES tab, uncheck HEADPHONE JACK SENSE.  Make sure MASTER & PCM are enabled in the PLAYBACK tab.

There may be another way to do it, but I haven't figured it out yet.  Also, I had to do it again after I rebooted this time.  We'll set if the setting stays set next time.  

This little snafu is really stupid, a blot upon an otherwise great distro. How is this behavior helpful to the average user?  What the heck does Headphone Jack Sense suggest to an average user?

 I learned what to do here:
[http://weichen.wordpress.com/2007/04/23/upgrade-to-ubuntu-feisty-solve-some-problems/](http://weichen.wordpress.com/2007/04/23/upgrade-to-ubuntu-feisty-solve-some-problems/)

---

