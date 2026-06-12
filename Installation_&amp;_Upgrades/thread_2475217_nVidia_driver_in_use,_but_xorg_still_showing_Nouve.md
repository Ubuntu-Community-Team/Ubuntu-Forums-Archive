---
title: "nVidia driver in use, but xorg still showing Nouveau display driver"
date: 2022-05-19
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-05-19
Additiional drivers section of Synaptic shows NVIDIA Corporation: GT218M [Geforce 310M] using NVIDIA binary driver 340.108 from nvidia 340, but there is no corresponding xorg-xserver software listed, only the previously used xorg-xserver-nouveu.  Nothing shows in System Monitor for video drivers.

Have I missed something?  Ubuntu Unity 22.04 is OS.

Thank you,

John

---

### Post by Bashing-om on 2022-05-19
cigtoxdoc; Hummm ....

> 
Nothing shows in System Monitor for video drivers.


More confidence from me in terminal.
What shows from terminal commands:
```

sudo lshw -C display
dpkg -l | grep -i nvidia

```

[INDENT]the terminal can not lie
[/INDENT]

---

### Post by cigtoxdoc on 2022-05-19
Thank you for your suggestion.  Results are shown below:

john@john-Vostro-3500:~$ sudo lshw -C display
[sudo] password for john: 
  *-display                 
       description: VGA compatible controller
       product: GT218M [GeForce 310M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:31 memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff
  *-graphics
       product: VESA VGA
       physical id: 2
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=640,480
john@john-Vostro-3500:~$ dpkg -l | grep -l nvidia
(standard input)

---

### Post by Bashing-om on 2022-05-19
igtoxdoc - Huh ?

No result for "dpkg -l | grep -l nvidia" ?
when we have:
> 
configuration: driver=nvidia

Well then - what environment are you operating in ?
show us: Between code tags, please - to maintain formatting >>
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

ps -efly | grep Xorg

```

-smells of old fish ??-

---

