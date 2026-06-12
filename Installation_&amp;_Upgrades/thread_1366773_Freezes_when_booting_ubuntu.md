---
title: "Freezes when booting ubuntu"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by Hackie2 on 2009-12-28
I am absolutely unhappy with the new Karmic release:

1) When i boot, chances are 2:1 to end up in a frozen boot screen. see below..
2) video is not running anymore:
2a) any dvb player hangs or fails when seeking a channel. In later kernels it says it cannot find any dvb card.
2b) webcams which worked in Jaunty do not anymore. I even had to unplug my Logitech cam because pulseaudio hangs (Bug #459445)

All of them worked in Ubuntu Jaunty

To the boot problem:
I have douzens of photos documenting frozen screens. Kernel hangs somewhere when executing rcS.d-Scripts and freezes completely. I made a little script to print the last task and uptime to screen every second, and i can see, the system freezes completely. also the keyboard does not react anymore. It may have to do with hardware initialisation, or a kernel lock problem, but how can i debug this?
When it hangs i normally hit the reset button and hope it starts. Every day it takes me 2-4 reboots. kernel sub-version does not matter.

Can someone help me debug this and writing a useable bug report?

Thx

---

### Post by Hackie2 on 2009-12-31
btw: i often see the line

```

init: ureadahead-other main process (123) terminated with status 4

```

on screen when booting failed (and only then)

on a successfully booted system "dmesg | grep uread" shows nothing...

---

