---
title: "Realtime kernel tinkering"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by shanz1999 on 2007-11-07
I have installed Gutsy and then changed it to boot the realtime kernel 2.6.22-14-rt instead.
Now supposing I wasn't happy with the realtime kernel configuration.  If I wanted to do "sudo make menuconfig" and change some of the settings, how could I do it without the linux-source code?

I have managed to open menuconfig and can see the settings of the realtime kernel.  Synaptic doesn't have any source code like it does for the non-realtime kernel.  That is, linux-source-2.6.22 exists but linux-source-2.6.22-rt doesn't!

Am I stuck with the precompiled realtime kernel image or is there another solution?

Anyone?
:confused:

<<Update>>
[http://rt.wiki.kernel.org](http://rt.wiki.kernel.org) suggests certain kernel config settings for optimum realtime performance.  For instance, i would like to deactivate ACPI sub modules like "fan", "processor", "button".  I also don't like the sound (under Processor type and features) of Tickless System (Dynamic Ticks).  I'd prefer a system with ordinary ticks I think.  The Timer Frequency is set to 1000HZ which is fine by me.

---

