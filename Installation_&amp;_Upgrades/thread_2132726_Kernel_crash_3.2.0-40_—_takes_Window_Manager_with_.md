---
title: "Kernel crash 3.2.0-40 — takes Window Manager with it"
date: 2013-04-05
forum: Installation &amp; Upgrades
---

### Post by questant on 2013-04-05
My last Ubuntu 12.04 kernel upgrade may have led to a series of problems.  There were intermittent error warnings indicating sudden crashes of applets such as Gnome Time Tracker and a few others, the names of which I no longer remember. (I am not certain but what all of my most recent posts may relate to this)

At one point my system became exceptionally slow, like a Windows machine doing an intense virus scan.  I discovered any application that accepted text from a keyboard would immediately be typing a string of lower case "t" characters as soon as I highlighted its window.  I began closing down applets for a reboot.  Upon reboot, and returning to work, one of the search programs locked up (Catfish) completely and with it the entire system.  I had mouse movement but nothing else.  I attempted to initiate a terminal through key calls to get an orderly shutdown.  Nada.  I attempted Alt-SysRq REISOB but to no avail.  I did an off-button shutdown of the system as there was no other way.

Upon reboot, the desktop (Mate) would not come up.  On the next reboot I moved to an earlier kernel.  I was able to boot through.  But I soon discovered Mate had been badly damaged, having lost much of its personalized configuration (such as virtual desktops, etc) and did not function properly properly even when reconfigured.  It, too, eventually locked up.  Other interfaces such as Ubuntu Unity, Cinnamon, Awesome, Cairo Dock, Gnome, you name it, they all work fine on any kernel but the latest upgrade.  

Most times, nothing will come up on 3.2.0-40 kernel but a black screen, although I've had screens that would go to text, listing a PID number and then a series of hex code and program lines (doubt seriously I'll hand-write this for submission, but who knows), and after circa 30 or 45 seconds, roll another one.  I have not let this run its course to see if it would complete to something significant yet this century.

At first I thought it might be just a damaged Mate desktop environment.  But as the latest kernel will no longer boot and all others (that I have tried--I'm currently booted to 3.2.0-38) do, I believe this is somehow a kernel issue.  In fact, I'm not certain the latest kernel (40) was ever stable on this system.  As long as I use an earlier kernel and any desktop but Mate, the system is stable and I have no reports of crashes.

As I've never had a kernel problem before (since beginning with Slackware in 1995-6) I am not quite sure how to proceed.  Do I reinstall the latest kernel?  Do I use an earlier kernel until a new update appears replacing the latest kernel?
The kernels I have installed are
3.0.0-23 (have no clue why that's still there)
3.2.0-27, 29-40
Also, given the damage to at least one window manager environments, namely Mate, do I need to reinstall it over itself or delete it with complete removal and reinstall it?  Thanks in advance for any feedback.

NB:  I would rather clean up these issues from a terminal than a GUI like Synaptic or Ubuntu Software Center if at all possible.  USC seems not sufficiently fine grained and with Synaptic I need to carefully peruse a time-consumingly long list of applets.  Please advise.

---

