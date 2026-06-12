---
title: "Hardy installer x86 goes blank and beeps after showing the ubuntu  load screen"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by noarc on 2008-07-14
Hi, my machine has Intel Q965 express graphics. I'm trying to install hardy but it gives me a black screen after the load screen (at which point it would normally start the gui installer). I'm aware of the alternate install CD, but I'm a little hesitant to install with that if I'm going to run into the same problem when I boot into an actual install. Last time I checked Q965 is supported by the kernel. Am I wrong? Thanks!

---

### Post by forger on 2008-07-14
is this hardy heron 8.04 or 8.04**[COLOR="Red"].1[/COLOR]** ? the 8.04.1 release fixes some bugs

By the way, I've known users running into problems with the installer, yet they were successful using the alternate installer :) And it really worked afterwards, even their internet connection

---

### Post by noarc on 2008-07-16
It's 8.0.4.1. I managed to install with alternate install disk, and the screen still goes blank after the ubuntu load screen shows up for a little.

Now, if I boot into recovery mode and select root console, then do a

$ startx

it actually loads into X, high resolution / full colors. How can I debug this?

---

