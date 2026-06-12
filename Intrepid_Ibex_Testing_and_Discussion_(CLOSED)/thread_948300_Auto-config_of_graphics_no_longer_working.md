---
title: "Auto-config of graphics no longer working"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by carlholmberg on 2008-10-15
Hi, I hope this isn't a duplicate of any other thread!

I recently upgraded my wifes Fujitsu-Siemens Amilo M7400 from Hardy to Intrepid and the auto-config of graphics no longer works. When I start I get:
```
(EE) intel(0): Output LVDS enabled but has no modes
(EE) intel(0): No valid modes
(EE) Screen(s) found, but none have a usable configuration
```

By setting the driver to "vesa" I don't get the errors but get 800x600 instead of 1024x768. By adding a subsection to the screen-part with 
```
Virtual 1024 768
Modes "1024x768"
```
I get 1024x768 but compiz doesn't work and the display settings aren't very informative...

I have attached Xorg.0.log and the output for ddcprobe, lspci and xrandr for when I use the default "low-graphics-mode".

In Hardy I think it used the i810-driver but of what I understand it's deprecated in the new Xorg. Manually setting the driver to i810 doesn't seem to help much either.

Where should I look for the problem? Is it in Xorg, hal or the kernel? It seems there is a regression somewhere...

Some simple changes in my xorg.conf-file gives me a somewhat usable system, but none of the changes I have tried correctly identifies the LVDS, makes it possible to use the intel driver or activates compiz.

Any help is appreciated because my knowledge of linux is severely limited!

/Carl

---

