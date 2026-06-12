---
title: "Live CD dual monitor no login screen jaunty jackalope"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by alarson on 2009-04-12
The 9.04 (Jaunty Jackalope) Live CD boots fine if I disconnect (not just power off, but physically disconnect) one of my flat panel monitors.  However if both monitors are connected, the login screen never comes up.  I get a mouse and both monitors are powered on, but the mouse only appears in one monitor.

If I disconnect one of the monitors, boot, then hot connect the second monitor, then both work fine.

> lspci | grep -i vga
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)

Note that the C51G adapter is an onboard controller that is not connected in any of my experiements.  The 8400GS has VGA and DVI outputs where my monitors are connected.

I haven't been able to find a launchpad report for this, but it must be a pretty common problem.  Anyone else see this?

---

### Post by Cellojazz on 2009-04-14
Same thing here.  Not just live CD, with 2 monitors - I can login without looking - but login screen on both monitors is black.  Using latest Jaunty Beta - updated yesterday.

The login screen was working - but installed Catalyst - and that hosed everything so had to reinstall from scratch (couldn't even Alt-F1 to terminal)

I guess I can live without boot screen - but its much nicer with it :-)

---

