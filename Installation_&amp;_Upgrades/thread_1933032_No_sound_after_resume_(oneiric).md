---
title: "No sound after resume (oneiric)"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by anutosho on 2012-02-28
Hi Folks.
after hesitating for a long time I finally upgraded my Kubuntu 11.04, and it doesn't work :(

The big majority of things work, but after a suspend my sound is gone.

The mixer setting from kmix is pretty much deserted . It just shows "Internal Audio Analog Stereo"

Alsamixer still shows all the in- and outputs of my card, and if I pull up the volume of my microphone I can hear it thru the speakers, but that's it.

aplay -l returns this
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci sais
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

```

My audio backend id Phonon (probably. I'm not shure)

Please help me. Any hint where/how to investigate the problem is appreciated.

---

