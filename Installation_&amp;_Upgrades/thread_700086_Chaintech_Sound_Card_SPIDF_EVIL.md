---
title: "Chaintech Sound Card SPIDF EVIL"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by datarhythm on 2008-02-18
SPIDF isn't working. It's hooked up to my receiver. I know it's not the card because the last machine that had it (Windows XP) worked just fine. VERY frustrating. 

lspci:

```
04:07.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: AV710 [Chaintech AV-710], device 0: ICE1724 [ICE1724]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AV710 [Chaintech AV-710], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I've searched Google and found this to be a common problem and I've yet to see someone with a solution. I know enough of Linux to be dangerous, so please talk like I'm just out of Windows.

I installed alsamixer and noticed that the IEC958 column had nothing in it but that small square at the bottom (nothing above it like all the others). 

Here's all the alsa related packages I have installed:

```

un  alsa                  <none>          (no description available)
ii  alsa-base             1.0.14-1ubuntu2 ALSA driver configuration files
ii  alsa-firmware-loaders 1.0.14-1ubuntu2 ALSA software loaders for specific hardware
un  alsa-oss              <none>          (no description available)
ii  alsa-source           1.0.14-1ubuntu2 ALSA driver sources
ii  alsa-tools-gui        1.0.14-1ubuntu2 GUI based ALSA utilities for specific hardwa
ii  alsa-utils            1.0.14-1ubuntu4 ALSA utilities
```

I noticed that I didn't have a asound.conf file in /etc, but I did have .asoundrc and .asoundrc.asoundconf files in my home directory. 

ANY help would be appreciated.

Oh yeah, here's my uname:

```
Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
```

Thanks!

---

### Post by datarhythm on 2008-02-18
Solved it here:

```
http://ubuntuforums.org/showthread.php?p=4359626#post4359626
```

---

