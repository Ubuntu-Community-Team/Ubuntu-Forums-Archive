---
title: "clutter games slow with intel graphics?"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zombiepig on 2010-04-23
Is anyone else seeing incredibly slow performance with all the clutter-based games (quadrapassel, swell foop, etc) with intel graphics? I haven't been able to find a reported bug about this, which leads me to think it could be something wrong in my installation.

Can someone with an intel (965) graphics test out clutter games and let me know how they run?

---

### Post by Endomancer on 2010-04-24
Im using an Invidia card and for me Quadrapassel is so slow it's unplayable, yet games such as Open Arena which would require better graphics abilities run very fast

---

### Post by barisurum on 2010-04-24
[http://intellinuxgraphics.org/2010Q1.html](http://intellinuxgraphics.org/2010Q1.html)

Check to see if your clutter version is the same as intel's suggested one here. Also upgrading the graphics drivers to 2.11.0 with mesa 7.8.1 increases performance significantly both in 2D and 3D. Its still a bit experimental though.. But I'm using it :D

---

### Post by zombiepig on 2010-04-24
Installing 2.6.33 from the mainline kernel ppa fixed the problem for me. It was going to be the first thing I was going to do after lucid release this week anyway :P

---

