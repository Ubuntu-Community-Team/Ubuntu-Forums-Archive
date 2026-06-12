---
title: "rotating screen"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by AugustQ on 2010-05-17
Hi,

I'm using Ubuntu 10.04 with an ATI HD5670 card and an Iiyama monitor (24" pivot).

My problem is: when I try to rotate the screen (switching to portrait-mode) I get a black screen and the monitor displays: no signal. Then I have to power down the machine. On reboot everything works as before.

What can I do here?

I tried it via Catalyst Control Center: as described.
I modified /etc/X11/xorg.conf: no effect.

This worked for another machine (SuSE 10.2 with NVidia 8500GT).

Any tips?
Thanks.
AugustQ

---

### Post by Johannes Eva on 2011-01-12
Edit the xorg.conf file:

gksudo sudo gedit /etc/X11/xorg.conf


Add the RandRRotation option somewhere in the "Screen" section to allow rotation:

```
Section "Screen"
...
Option "RandRRotation" "True"
....

```
 

Complete example:

```
Section "Screen"
    Identifier   "Screen0"
    Device       "Device0"
    Monitor      "Monitor0"
    DefaultDepth 24
    Option       "TwinView" "0"
    Option       "metamodes" "CRT: nvidia-auto-select +0+0"
    Option       "RandRRotation" "True"
    SubSection "Display"
        Depth 24
    EndSubSection
EndSection

```
 

Finally, restart your computer. You'll then be able to rotate your screen through the NVIDIA utility, or via the command line:

```
xrandr -o left
xrandr -o normal
...
```

Use man xrandr for more details and options.


Rotation / pivot with NVIDIA gfx work very well on recent Ubuntu releases. More infos:

_**[Ubuntu & NVIDIA: external monitor, rotation, ...]("http://www.johannes-eva.net/ubuntu-linux-external-monitor-nvidia-rotate")**_

---

