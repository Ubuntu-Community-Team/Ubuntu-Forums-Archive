---
title: "acpid power event shutting down on startup!"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by aweber1nj on 2010-01-17
I was trying to get the power button to be operational and perform a "controlled shutdown" for a new desktop I'm configuring with 9.04.

As a desktop, I guess it didn't install acpid by default, but that was easy with apt-get.  However, just installing and starting acpid didn't really do anything for me.

So using the man-page for acpid, I saw the example to do exactly what I was hoping; create an event for the power-button, and direct that to a simple script that calls "shutdown -P now..."

That worked great when I tried it the first time.  But when I tried to reboot the PC, it would continually get through most of the startup, then shut itself down!  I knew that was the only thing I had changed, so I used the LiveCD and commented-out the shutdown command and it started-up cleanly again.

So 1) that man-page probably should change.
2) Can anyone help me with a simple power.sh script to shutdown Ubuntu cleanly when someone presses the power-button?

Seems like somehow acpid was getting the startup power-button-press and calling the shutdown?  I guess there must be some way to check state-changes and only fire the shutdown if the state is changing from run-level 3/5 to 0?

I looked at the original power.sh, but that seems to want to find ac adapter entries, battery entries, etc.  I don't think my PC will ever change AC/Battery state (since it's a desktop with no UPS), unless there's some way to check poweroff state or something I'm unaware of?

Thanks in advance!
-AJ

---

