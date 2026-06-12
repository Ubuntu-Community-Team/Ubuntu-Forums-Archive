---
title: "Gutsy fresh installation slow as a snail"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by Venerence on 2007-12-12
So rather then doing an upgrade, I uninstalled feisty and installed gutsy. After installing, I do two things: sudo apt-get update and sudo apt-get dist upgrade, very first two things I do. After those had finished, I tested out gutsy and found that it is behaving *extremely* slow.

Mostly the slow behavior is having to do with window manipulation. Opening windows, closing windows, minimizing windows, moving windows, changing tabs in firefox, scrolling in firefox, changing workspaces with windows on it (if it doesn't have windows it changes fine), and maximizing windows all make my cpu jump to 100%. Also note that this is before any special effects are turned on, and before the restricted drivers for xgl are enabled. XGL is running though.

To try to fix it, I first enabled the restricted drivers, which do nothing to solve the problem. I then turn on the eye candy, get an error, then install compiz fusion to see if alternate rendering of window manipulation would help. It does slightly, as I can move the windows about without lag, but everything else didn't work at all.

Note that I could run feisty on this computer with full compiz fusion effects at less then 10% cpu. I'm also running the 32-bit version of gutsy for compatibility, even though I have a 64 bit processor.

The computers specs are the following:
CPU: AMD athalon 64 3200+
Graphics Card: Radeon x1600 pro 512 meg
Mobo: abit kv80
Ram: 2 gigs ddr522 ram
2 IDE drives (Ubuntu is running on the slave drive as a dual boot)

---

