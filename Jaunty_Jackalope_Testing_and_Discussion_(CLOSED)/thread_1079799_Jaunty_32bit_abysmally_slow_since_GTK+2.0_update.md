---
title: "Jaunty 32bit abysmally slow since GTK+2.0 update"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JPorter on 2009-02-24
Hello all!

I experienced a bug with lockup on boot following a GTK update last week, it was subsequently fixed with another GTK update, but since that time my system performance has been UNBELIEVABLY slow.  Multitasking is a painful experience, waiting for the UI to catch up.  I'm running the standard Human theme, so nothing wacky going on theme related that I know of.

Here's the original bug report, with fix, and my comments at bottom... [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/331324](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/331324)


Running Jaunty 32bit, kernel 2.6.28-8 generic, Nvidia 180.29 proprietary driver standard repo version.

GTK+ packages are primarily 2.15.4-0ubuntu3 flavors, the current up-to-date packages from the Jaunty repos.  The only exceptions to the gtk 2.15.4 packages seem to be libgtk2.0-cil (2.12.7-1ubuntu2), libgtk2-perl (1:1.190-1ubuntu1), and gtk2-engines (1:2.17.3-0ubuntu1).


Can anyone help?  Launchpad bug reports are primarily oriented toward clear breakage, rather than performance issues, so I don't expect a great deal of response there.

Thanks!

---

### Post by mdurham on 2009-02-24
Have you looked with the System Monitor to see what's eating the time?

---

### Post by exploder on 2009-02-24
Run "top" in the terminal, that will give you a clear indication of what is going on.

---

### Post by JPorter on 2009-02-24
Nothing appearing System Monitor that jumps out... total CPU usage is around 40-50% minimum on each thread, but the individual processes don't add up to that amount.  Largest running process is ~15% (the system monitor itself) and nothing else is eating processor time.  It's a process that doesn't appear in the System Monitor for some reason.

This is on a PC at work... I will check using top tomorrow.  Thanks for the help, guys, I will be back with you on it first thing in the morning (GMT-5).

---

### Post by mdurham on 2009-02-25
> **JPorter said:**
> Nothing appearing System Monitor that jumps out... total CPU usage is around 40-50% minimum on each thread, but the individual processes don't add up to that amount.  Largest running process is ~15% (the system monitor itself) and nothing else is eating processor time.  It's a process that doesn't appear in the System Monitor for some reason.

This is on a PC at work... I will check using top tomorrow.  Thanks for the help, guys, I will be back with you on it first thing in the morning (GMT-5).
Make sure you have View->'all processes' selected in System Monitor

---

### Post by JPorter on 2009-02-25
Weird, whatever it is was solved in this morning's updates.  I neglected to make a note of the packages.  

It's zippy once again!  No problems that I can see at the moment.

Thanks for your help, folks.

---

