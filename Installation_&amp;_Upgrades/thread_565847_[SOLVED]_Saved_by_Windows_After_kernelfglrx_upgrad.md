---
title: "[SOLVED] Saved by Windows? After kernel/fglrx upgrade gdm won't start"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by fsando on 2007-10-02
System ubuntu 7.04 ati-x1600
I Installed the the latest kernel upgrades (pushed through the update manager) then upgraded fglrx (ati-driver version 8.40.4) with envy. Now gdm won't start.
After boot the brown ubuntu screen flickers a bit, disappears and the console screen with various text is racing by, brown screen comes back shortly then the console, and then a black screen with the waiting cursor just going on for ever.

I can log in to recovery mode and I can even start a gnome session as root (simply by issuing 'startx' in a console) - but I have no idea what to do.

I've seen many reports on similar problem, though none of the solutions worked for me.
I've reinstall the fglrx driver
I've reinstalled the desktop (apt-get install ubuntu-desktop)
Still the same.

This is particularly bad as I can't access my email which I need badly.

Luckily I've kept my xp partition which lets me write this (and search for solutions) - what would a linux user do without windows ;) If this post leads to a solution I could say I was saved by Windows :D And, of course, the great Ubuntu community :guitar: (deserves a fanfare)

SOLVED:
Problem was that I had followed some advice to nicer fonts where you create new configuration files for font settings - I more or less just copy-pasted.
Solution:
Boot into recovery mode
issue 'startx' to have point-and-click
Removed those config files
Logged out
issued 'exit' at command prompt ... an presto! Shortly thereafter I was back in.
So not exactly saved by windows. Which makes me very happy.

---

