---
title: "totally freaky problems in jaunty when power cord pulled"
date: 2009-01-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hyperform on 2009-01-20
I have a Sony FZ410E and just upgraded to Jaunty using a dist-upgrade (alpha 3) after intrepid would lock up CONSTANTLY for no reason.  While jaunty is peachy keen as long as the power cord is plugged in, as soon as I pull it weird things begin to happen.  

First, gnome starts to move very slowly and jerkily, with the mouse cursor jumping all over the screen.  The hard drive starts making loud taxing sounds like it's working really hard to do... something, but nothing seems to happen.  Gnome basically stops working, the keyboard shortcuts become unresponsive, despite the fact I can still type into a window (but the characters take several seconds to appear).  Additionally, it refuses to accept suspend or hibernate commands in this state, it will only shut down or restart.  If I plug the cord back in, the problems continue until I restart.  

The Ctrl-Alt-Backspace trick to kill X doesn't seem to work anymore in Jaunty, either, which is very frustrating.  Is there a way to re-initialize this command?  Has it been taken out of the X server that Jaunty is packaged with?  

The system is screamingly fast and efficient, way better than any previous version of Ubuntu on this computer, and things like the brightness adjustment keys actually work for the first time ever (although there is a lot of lag on these...  I'll accept that).  I'd say that the dist upgrade WOULD have been 100% successful if not for this weird screwy unplugging problem.  Since I'd rather not be tethered indefinitely (I take the computer out a lot and don't want to only be plugged in), I'm curious if anybody has seen this before?  More importantly if there's anything that can be done about it?


EDIT:

Restarting gdm seems to solve the glitchy, SLOOOW X performance, but only when the power cord has been re-inserted.  Running on battery power, nothing will make it speed up or act anywhere near normal.  Additionally, gnome-power-manager crashes immediately when the power cord is taken out, but restarting it doesn't have any effect at all, only if gdm is entirely restarted.  Leaving glxgears running while taking out the cord makes the FPS go from ~770 to ~9.  

Additionally, starting on battery power leads to same, freaky X behavior once the computer boots into it.  

EDIT 2: 

I've narrowed it down to being a Gnome-specific problem, probably has something to do with gnome-power-manager?  That won't load if the computer is booted on battery, and crashes immediately if the battery is engaged.  Everything works fine in the gdm login screen no matter what, Gnome just gets freaky when it has to deal with battery power.  KDE and fluxbox both acted completely normal.  

Any ideas?

EDIT 3:

The problem was, in fact "powermanagement-interface."  The most recent dist-upgrade removed the package, and there are suddenly no more problems at all.  All GUIs work seamlessly on AC or battery power.  Jaunty is now the fastest and most efficient system that has run on this computer.  Xfce works lightning-fast, and GNOME only has lag when using the Sonypi keys.  But that's miraculous enough, because they didn't work at all in Intrepid.  Still no ctrl-alt-backspace to kill X though.  Bummer.

---

