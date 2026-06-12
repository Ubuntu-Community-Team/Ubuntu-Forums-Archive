---
title: "Pentium 4 slow as an old carthorse"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by fuddlestack on 2010-08-18
Greetings.  Crass newbie at the wheel...

I just installed 10.04 Desktop onto an external USB disk and used it to boot an old Acer Veriton 7600G with a Pentium 4 CPU clocked at 2.80 GHz, 3 Gb of memory and an AGP Sapphire ATI Radeon video card with 512 Mb of DDR2.

With nothing running, nothing swapping, only 7% of memory in use, and around 11% of both CPUs, this system is so slow that with no programs running it takes about 5 seconds to switch between dropdown menus in the main Applications/Places/System menu. The standard GMatrix screensaver takes forever to crank out a single character.

I'd be grateful for any suggestions or speculations as to reasons, tests I might run, etc.

---

### Post by sydbat on 2010-08-18
> **fuddlestack said:**
> Greetings.  Crass newbie at the wheel...

I just installed 10.04 Desktop onto an external USB disk and used it to boot an old Acer Veriton 7600G with a Pentium 4 CPU clocked at 2.80 GHz, 3 Gb of memory and an AGP Sapphire ATI Radeon video card with 512 Mb of DDR2.

With nothing running, nothing swapping, only 7% of memory in use, and around 11% of both CPUs, this system is so slow that with no programs running it takes about 5 seconds to switch between dropdown menus in the main Applications/Places/System menu. The standard GMatrix screensaver takes forever to crank out a single character.

I'd be grateful for any suggestions or speculations as to reasons, tests I might run, etc.Most likely the ATI card. Older ATI graphics cards are not supported by AMD/ATI anymore. The open driver automatically installed may or may not work 100% either.

Also, turn off any 'Desktop Effects' (System > Preferences > Appearance).

---

### Post by fuddlestack on 2010-08-18
> **sydbat said:**
> Most likely the ATI card. Older ATI graphics cards are not supported by AMD/ATI anymore. The open driver automatically installed may or may not work 100% either.

Also, turn off any 'Desktop Effects' (System > Preferences > Appearance).

Well, it was new when I bought it...;)

That did it.  Thank-you, sir.

I rather suspected video... are there any utilities going that would let one put a finger on such bottlenecks?

---

### Post by sydbat on 2010-08-18
> **fuddlestack said:**
> Well, it was new when I bought it...;)

That did it.  Thank-you, sir.

I rather suspected video... are there any utilities going that would let one put a finger on such bottlenecks?You've found the best one here - the Ubuntu Forums!

---

### Post by dabl on 2010-08-18
> **fuddlestack said:**
>  are there any utilities going that would let one put a finger on such bottlenecks?

"top" will show the running processes, in descending order of resource (CPU and memory) consumption.  The one sucking the most resources will be on ... {wait for it ...} ... *top*.    :lolflag:

---

### Post by tgalati4 on 2010-08-18
Open a terminal:

sudo apt-get install htop
htop

---

