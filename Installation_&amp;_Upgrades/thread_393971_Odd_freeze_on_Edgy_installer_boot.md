---
title: "Odd freeze on Edgy installer boot"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by smowton on 2007-03-26
This is a solved problem, but I'd be interested to know why it happened, or if it's likely to cause me further trouble...

The Edgy install CD boots quickly to the menu screen offering "Start/install Ubuntu", "Check CD for consistency" and so forth. If I choose Start/Install, I get a greyscale Ubuntu logo with a grey box going back and forth for around 2 minutes, then a blinking cursor in the top-left corner of the screen, then no further activity (at least not for 30 minutes).

If I simply edit the boot prompt and remove "quiet" and "splash" from the options, it boots fine, albeit with a 2 minute delay between loading SquashFS and my network drivers.

Computer is an Athalon64 3000+ with 1GB RAM and an ABit motherboard with VIA gigabit Ethernet and chipset.

Ubuntu version is 6.10 (EE) amd64.

Any ideas why it was behaving like this?

---

