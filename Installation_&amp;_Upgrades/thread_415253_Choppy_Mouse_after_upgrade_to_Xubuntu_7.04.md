---
title: "Choppy Mouse after upgrade to Xubuntu 7.04"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Dakiraun on 2007-04-20
Did the upgrade from 6.10 to 7.04 in Xubuntu which was very slick, though after the reboot I seem to be having some mouse issues.

Quick overview:

- System is an older K6-III+ on an EPoX MVPG5 super 7 board using an A-Open USB mouse
- Had been running Xubuntu 6.10 for quite some time without any issues

What the mouse is doing:

It's basically being very choppy and reacting in a delayed way to movement to the point where it is not usable.  Imagine trying to get an 8088 CPU to animate and move a cursor in XFCE... that's basically what it's like. :P

Findings:

lsmod shows psmouse in use.  A look at /var/log/messages doesn't seem to have any errata about the mouse, nor are any tracking errors/issues being captured on moving the mouse  

At this point I'm still investigating it, but if anyone else has run into this or has some ideas on a specific place to look to isolate the problem, the input would be helpful!  Thanks.

---

### Post by Dakiraun on 2007-04-20
Some further troubleshooting I did to add to this - tried a different mouse (a Logitech USB) to see if it was specific to the A-open, and the result was the same.  I also loaded mdetect to see what it might find, and it actually reports finding nothing (using verbose option).  I should also mention that the system behavior is otherwise fine - everything loads quickly and runs smoothly.  Real head-scratcher so far.

---

### Post by Dakiraun on 2007-04-26
**Problem solved!**

Okay... more like side-stepped.  I used an adapter to convert the USB to PS/2 wondering if that would make any difference, and it did - mouse works perfectly now.  So as far as I can tell, the problem is a weird combo of the psmouse module, the new kernel, and the USB bus on an older EPoX MVP3G5 super7 board.  I've not yet seen this problem with Xubuntu 7.04 on another system.

So quick workaround - convert the USB mouse to PS/2 if you have this happen to you.  The longer work around would probably be to change the setup of the system to use something other than psmouse for tracking, possibly using gdm - but much quicker just to dig out one of those adapters. ;)

---

