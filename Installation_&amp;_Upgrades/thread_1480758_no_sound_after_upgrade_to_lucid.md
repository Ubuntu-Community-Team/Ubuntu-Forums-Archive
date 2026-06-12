---
title: "no sound after upgrade to lucid"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by jabrilm on 2010-05-11
I upgraded successfully last night from Hardy Heron to Lucid Lynx, but have no sound now. After searching around I can see that this is a fairly common problem. But none of the proposed solutions that work for other people have yet worked for me. 

If I type 'alsamixer' at the command line, everything looks fine. There are no 'MM's indicating something being muted. I tried removing and reinstalling alsamixer and pulseaudio with no success. Edited lines 45 and 46 of **/etc/pulse/default.pa **with no luck. Any other tips/tricks?

Cheers

Also tried deleting .pulse and restarting, with no luck.

Also tried 'amixer set Speaker 100%', no luck.

It would be a shame not to be able to use Lucid Lynx simple because of this audio problem. Is there really no simple solution?

---

### Post by raygj on 2010-05-13
> **jabrilm said:**
> I upgraded successfully last night from Hardy Heron to Lucid Lynx, but have no sound now. After searching around I can see that this is a fairly common problem. But none of the proposed solutions that work for other people have yet worked for me. 

If I type 'alsamixer' at the command line, everything looks fine. There are no 'MM's indicating something being muted. I tried removing and reinstalling alsamixer and pulseaudio with no success. Edited lines 45 and 46 of **/etc/pulse/default.pa **with no luck. Any other tips/tricks?

Cheers

hi i had the same problem and this worked for me.
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script")

---

### Post by jabrilm on 2010-05-25
When I type

> speaker-test -Dplughw:0,0 -c2 

I get the output:

speaker-test 1.0.23

Playback device is plughw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
...

---

### Post by garvinrick4 on 2010-05-25
This is a fix that worked for me in previous versions, just might work in Lucid, is a PulseAudio thing..

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by jabrilm on 2010-05-25
I followed those instructions in Part A and it seemed to make things even worse. Now when I type

$ pulseaudio & pavucontrol

I get a popup about 'connection refused' and then:


```
[1] 7834
W: module.c: module-oss is deprecated: Please use module-alsa-card instead of module-oss!
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:7835): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
```

And now under Volume Control there are no input or output devices listed.

I reinstalled pulseaudio and rebooted and at least seem to be back where I was before (still no sound, but can access volume control again). One thing I noticed is that in Sound Preferences --> Applications tab it says "No application is currently playing or recording audio" even if I have Banshee playing a song. 

Under the Sound Preferences --> Output tab, it says choose a device for sound output, but gives only one option: /dev/dsp Stereo. Is this as it should be?

If I revert to the previous LTS am I likely to get sound restored? And if so, what's the easiest way to do that reversion? Can it be done through update manager somehow?

Also, reading all the posts about people not getting sound with Lucid Lynx, I wonder if there will be any fix released for this problem in the near future.

Is it possible that alsa is not recognizing my sound card? These are my sound cards.

```
jabrilm@homemade:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```I checked /etc/modprobe.d/alsa-base.conf and this is the contents

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```There doesn't seem to be any reference to those cards, so I added the line

options snd-STAC92xx=-2

and rebooted, but still no dice. Any suggestions on how to force alsa to recognize my sound card? Thanks for any help.

More info:

```

jabrilm@homemade:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at 90380000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 2430 [size=8]
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    Memory at 90200000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, fast devsel, latency 0
    Memory at 90300000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 90426100 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
    Subsystem: Intel Corporation Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at 90400000 (32-bit, non-prefetchable) [size=128K]
    Memory at 90424000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 2400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 20e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 20c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 20a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, medium devsel, latency 0, IRQ 17
    Memory at 90425c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Intel Corporation Device 4001
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at 90420000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 90500000-905fffff
    Prefetchable memory behind bridge: 0000000090900000-0000000090afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 90600000-906fffff
    Prefetchable memory behind bridge: 0000000090b00000-0000000090cfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 90100000-901fffff
    Prefetchable memory behind bridge: 0000000090d00000-0000000090efffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 90700000-907fffff
    Prefetchable memory behind bridge: 0000000090f00000-00000000910fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: 90800000-908fffff
    Prefetchable memory behind bridge: 0000000091100000-00000000912fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 2080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 2060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 2040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at 90425800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
    Memory behind bridge: 90000000-900fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 30
    I/O ports at 2428 [size=8]
    I/O ports at 243c [size=4]
    I/O ports at 2420 [size=8]
    I/O ports at 2438 [size=4]
    I/O ports at 2020 [size=32]
    Memory at 90425000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: Intel Corporation Device 5044
    Flags: medium devsel, IRQ 10
    Memory at 90426000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 2000 [size=32]
    Kernel modules: i2c-i801

03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at 1018 [size=8]
    I/O ports at 1024 [size=4]
    I/O ports at 1010 [size=8]
    I/O ports at 1020 [size=4]
    I/O ports at 1000 [size=16]
    Memory at 90100000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: pata_marvell
    Kernel modules: pata_marvell

06:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) (prog-if 10)
    Subsystem: Agere Systems FW322/323
    Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 19
    Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

```

I've 'solved' this problem for the time being by discovering that the speaker jack on the rear of the computer still works with both headphones and speakers, even though the jack on the front of the computer no longer works after update to lucid lynx. Have no idea why, but at least I have sound.

---

