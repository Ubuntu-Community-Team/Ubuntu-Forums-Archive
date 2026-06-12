---
title: "gutsy radeon mobility sleep/suspend/hibernate and xvideo broken"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by mikeh on 2007-10-24
Gutsy upgrade: breaks sleep, hibernate and Xvideo with 'radeon' driver.

I see lots of threads on sleep/hibernate problems with ATI fglrx, but this is an old laptop.
IBM X23, ATI mobility M6 LY.  "radeon" driver. (or "ati")  8MB Video RAM.

Also, playing videos with Xv just gives a blue window.

MINIMAL TEST: boot recovery mode, start X server (no clients/desktop),
switch back to VT, "/etc/acpi/sleep.sh"  -> sleeps OK.
close/open lid -> system wakes to text VT.
Alt-F2 to get X-windows display -> system hangs. (cannot ping)

Is it possible to go back to the old X-windows server from 7.04, and would that fix it?

---

