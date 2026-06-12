---
title: "No sound after Gutsy Upgrade"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by johannix on 2008-03-27
I've been kind of ignoring this problem for a while now, even though it's driving me nuts.

As you notice below, I've got a bunch of drivers setup to my card at this point. Was wondering what else I could try, and how I could clear those settings.

I've already turned off my system sound (I saw that listed as a potential fix somewhere).

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
05:02.0 Communication controller: NetMos Technology PCI 1 port parallel adapter (rev 01)
05:04.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

```

sudo lshw -class sound
  *-multimedia            
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106

```

---

### Post by johannix on 2008-03-27
OK. Now I've got it so that one of the four settings works in the sound test, but I get no sound out of any of my apps...

Let me know if any more info would help with the problem...

---

### Post by johannix on 2008-03-27
Also works playing CDs with Sound Juicer.

Still doesn't work with Amorak and FFox.

---

### Post by johannix on 2008-03-27
List of working/not working. Maybe that'll help?!?

Working:
Movie Player
Sound Juicer

Not working:
Amorak
FFox
Audacity
MPlayer
XMMS

Both:
RhythmBox could play CDs not MP3s

---

### Post by johannix on 2008-04-01
Really need some aid with this.

I'm forced to keep my laptop next to my development machine to listen to music. Real ridiculous! Please please help me, because I really don't want to boot into Windows. 

Oh and can't wait for April Fools CSS madness to end.

---

