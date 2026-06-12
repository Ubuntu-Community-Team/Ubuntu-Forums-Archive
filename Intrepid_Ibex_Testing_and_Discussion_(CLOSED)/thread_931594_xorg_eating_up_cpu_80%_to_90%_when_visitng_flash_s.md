---
title: "xorg eating up cpu 80% to 90% when visitng flash site + running compiz"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-09-27
this just happened today after updating.
Actually computer becomes unusably slow when this happens, closing the offending firefox tab lets xorg go back to around 8%
I am using the free radeon driver on an x1300 agp 256mb video while running compiz.

when not running compiz, xorg stays at 11% or under when visiting youtube site.

---

### Post by psyke83 on 2008-09-27
Please, search the forum first. There's at least half a dozen threads about Flash. Look at the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=866965") thread for a link to my PPA where you can get an updated flashplugin-nonfree package. Please note that it's not working correctly for 64 bit users yet, though.

Also note that the Flash 10 release notes specifically warn that hardware acceleration is disabled if you use a compositing manager, so higher CPU usage is to be expected. The older version of Flash 10 has serious performance issues, however, so an upgrade will help.

---

### Post by stewacide on 2008-09-27
Yup, flash videos bring my Intrepid install w/ the non-free Flash 10 plugin to a crawl. Is it likely that they'd get hardware acceleration working in conjunction w/ OpenGL window composting?

---

### Post by sdowney717 on 2008-09-27
actually discovered going to cnn video kills performance even without running compiz
youtube is ok

---

### Post by psyke83 on 2008-09-27
> **sdowney717 said:**
> actually discovered going to cnn video kills performance even without running compiz
youtube is ok

[http://ubuntuforums.org/showpost.php?p=5866387&postcount=24](http://ubuntuforums.org/showpost.php?p=5866387&postcount=24)

---

