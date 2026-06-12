---
title: "apt-get: How to get rid of all games?"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by jo.angel on 2008-06-10
HI!
How can I remove all games (or other packet groups) via commandline from Gutsy?

Summink like:

sudo apt-get remove "packetgroup-games"

Cheers

---

### Post by jo.angel on 2008-06-10
Well at least for the gnome games it works like this:
Because they are all in 1 package:

**sudo apt-get remove gnome-games-data**

This has removed all standard games from my gutsy
However, if u are looking for a way to deinstall other package gropus this wont help...

---

