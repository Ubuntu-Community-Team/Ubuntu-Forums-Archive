---
title: "Ubuntu installation using alternate install extremely slow"
date: 2014-01-22
forum: Installation &amp; Upgrades
---

### Post by jamesaepp on 2014-01-22
Installation question. I am using the ubuntu 12.04.2 alternate install method (Booting it over PxE). 

It does end up working, but here is the issue. After the important stuff such as locale and network setup, (literally right after you confirm HTTP proxy settings, which I leave blank) it quickly flashes "Downloading package lists", uses the network for about 1-2 seconds, and then dies down with absolutely no activity for about 10-20 minutes before continuing on normally. 

I experience this both in a VM and on metal. 

Anyone know why this could be? Is there some way I could optimize my network for what I am doing? To me it feels like it is doing something in the background that could be resolved? I already have a squid cache, but the problem persists!

---

### Post by ibjsb4 on 2014-01-23
I use the mini.iso and have this same 10 to 20 minute wait that I assume is just because of my older equipment.

---

