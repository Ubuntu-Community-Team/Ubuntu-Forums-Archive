---
title: "xubuntu 14 update causes screen to flicker or blink"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by bobnw on 2014-09-01
After a day of waiting I gave up on trying to fix this problem.   I am setting up the old laptop to give to an elderly lady in the neighborhood.   Xubuntu 14 was perfect for her.   Simple and easy until it strated blinking. 

After a day of wating I gave up and installed Opensusse 13.   It's not  as elegant or simple.  A lot more work then Xbuntu to get rid of features that she does not need and make the desktop simple and clean.   But the blinking was intolerable.

Ran Xbuntu 12.04 on same laptop, a Toshiba Satilitte A215,  with no problem for many months.       Xbuntu 14 ran fine for about a week.   Then a fews days back  I downloaded a large update and upon restart the screen blinks or flickers every one two three seconds.        I reinstalled Xbuntu 14 and it ran fine for a few minutes,  then the same thing happened.  I dowloaded the updates,   the update manager requested a restart,   and after the restrart the flicker was back.

Something in the update causes the problem on this particular machine.  On a newer Toshiba laptop the same update did not cause problems.

 The following video card data was displayed by running lshw
description: VGA compatible controller
                product: RS690M [Radeon Xpress 1200/1250/1270]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:44 memory:f0000000-f7ffffff 
memory:f8100000-f810ffff ioport:9000(size=256) memory:f8000000-f80fffff

---

### Post by pcar916 on 2014-09-15
Yours isn't an isolated case. This ATI chipset is consistently flickering on a lot of our screens after the upgrade to 14.04 (in my case from 12.04). I wasn't concerned about the RS690 because it was reported as compatible, and I have the same Satellite A215. It ran 12.04 for years with no issues. 

The flicker is the entire screen, momentary, and the intervals between flickers is not regular on my machine. Unfortunately, this is a deal-breaker if it can't be fixed. But since this isn't my main machine I can leave it as a 14.04 installation to keep on learning how Ubuntu works while this is addressed. One difference between yours and my installation. 

In my case, rather than waiting for an update to start the flickering, 14.04 flickered immediately and throughout all of the updates it remains.

I did use the "nomodeset" modification to GRUB after quiet /splash on the "linux /boot" line. The response was as follows.

1. The flicker went away.
2. The screen format was far too large to be useful
3. The system response was very slow.

This was the equivalent to booting into Windows "Safe Mode" so there were no drivers other than the bare-bones versions.

Predictably, I don't know yet how to configure around it.

---

