---
title: "Dapper Dual Monitor / Dual Video Card Issue"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by bistros on 2006-06-05
Hi All:

I have a system that has been upgraded from Breezy to Dapper.  On upgrade the dual monitors that had been working fine stopped doing so.

It is NOT a Radeon or Nvidia install.  Proprietary binary driver options do not apply (twinview, fireGL options).

The xorg.conf file has worked fine in the past.  Testing each monitor/video card individually in a testing xorg.conf file works fine - the problem is with two monitors & two video cards in the same xorg.conf file.

One video card is embedded in the motherboard (Intel 82865G) and the other is an elderly ATI 3D Rage IIC (Mach64) card.

Reconfiguring the motherboard video priority does not have any effect on the error other than to change which video/monitor combo fails.  The error reported in the Xorg.0.log file occurs at LoadModule "Int10", where on initializing the libint10.so module, it fails indicating it "Cannot read V_BIOS".  The same error is reproduced regardless of which video/monitor is started first - the second fails consistently at this step - so I do not expect this is a card-specific error. I expect this is a libint10.so error.

If anyone requests, I can supply error logs, lspci dump, dmesg output and xorg.conf files, but I've tested and confirmed this error cold. I do not think this is a newbie, RTFM or configuration error.

--
Bill Strosberg

---

### Post by bistros on 2007-12-13
I've been through a number of variations and permutations here.  Tried a bunch of video cards and eventually got things working - sorta.

The automated configuration editors for xorg.conf and much of the instructions online are in conflict - the automated ones number the screens and the online instructions tend to name them.  There is usually a bunch of conflicting crap in the  server layout section of xorg.conf - therein were some of the problems in may case.

The proprietary "screen 0" lines in the device section put in by the displayconfig-gtk are supposed to be driver specific, but they put them in regardless.  The xorg.conf documentation appears to not have been consulted in developing the screens and resolutions handler.

The i810 driver in Gutsy seems to have problems in combination with other video drivers and Xinerama.  The older one didn't have the same issues in Dapper.  I had a working system in Dapper, and I could not get the Intel 82865G to behave in Gutsy, and I've been doing this stuff for many years. I'd consider pinning and downgrading the i810 driver if I had time to play with this but I don't.

---

