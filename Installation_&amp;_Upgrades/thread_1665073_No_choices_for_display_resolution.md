---
title: "No choices for display resolution"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Kernel Software on 2011-01-11
A customer system was running fine with 10.04, other than the display had a problem where it would at random times display flashing vertical bars.  We tried different display resolutions and monitors, but nothing helped.

We decided to upgrade the system to 10.10.  That seemed to go fine and the issue with the flashing vertical bars appears to have been resolved.  However, the display resolution is now at 1600x1200 and offers no other choices.  10.04 offered other lower resolutions, but 10.10 does not.

1600x1200 on a 17" display is a bit small for comfortable reading.  Is there something we can do to change the display resolution and refresh rate offerings?  Here is the graphics adapter info:

  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:88000000-8fffffff memory:80000000-8007ffff

Thanks in advance for any assistance.

---

### Post by Kernel Software on 2011-01-11
Continued research on this issue turned up a known bug regarding Intel 845G chipset support:

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

Following the instructions in the bug report, we created an xorg.conf file as described.  Upon restarting, we were again offered the full set of options supported by this chipset.

As indicated in the bug report, this action might again result in the original problem (randomly entering low-graphics mode).  However, that situation is simply remedied by a restart.  Use of the default driver results in a stable system, but the lack of choices for display resolution and the lack of hardware acceleration have such a significant impact on performance that instability is the lesser of two evils in this case.

---

### Post by Kernel Software on 2011-01-13
Just a follow-up note on this issue.  With the Intel 845G driver installed under 10.10, we ran the system for 24 hours displaying random 2D and 3D screensavers.  We had no crashes, hangs, or entry into low-graphics mode as we did under 10.04.  Seems to be running just fine at this point.

---

