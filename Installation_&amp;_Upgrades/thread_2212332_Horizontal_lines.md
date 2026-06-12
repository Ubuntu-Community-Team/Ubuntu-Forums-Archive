---
title: "Horizontal lines"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by knightdogg on 2014-03-20
Hi all

Here is my config:
OS: XFCE / Ubuntu 12.04

Pentium4 3GHz x 2
RAM 1 Gb
HD 117 Gb
Grafic card: ATI R200 (RV280 5964) x86/MMX/SSE2 TCL DRI2

Just after booting when XFCE is loading, the display is OK: splash screen is nice. Then 2 blocks of horizontal lines come in the front (color: yellow/green). And they're still there, on the login page, and after the session has been started.

When windows are displayed, the lines are still there but are less visible. Besides we cannot read very well what is written behind.

As the display is OK for a while, I think my screen is OK. I had not this problem before, but only since one update I made a few weeks ago.

I added "nomodeset" in the grub file (/etc/default/grub) :
GRUB_CMDLINE_LINUX_DEFAULT= "nomodeset quiet splash"
then I ran sudo grup-update, then I rebooted.
But the lines were still there. I lost the splash screen. So I undid my change.

System Settings > Additional Drivers: I have nothing.
Synaptic manager: search for "ati r200": I can see only 3 packages available for quantal raring and saucy. I guess I should not install these packages (unless I upgrade?).

Any idea?
Thank you very much !

---

