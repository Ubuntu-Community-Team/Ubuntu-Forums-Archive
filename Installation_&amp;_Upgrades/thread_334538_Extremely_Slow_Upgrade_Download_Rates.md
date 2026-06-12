---
title: "Extremely Slow Upgrade Download Rates"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by pdelorey on 2007-01-09
When I use any method of upragde, whether it is synaptic, apt, or automatix, my download speed is less than 1kB/s for the majority of the process. Occasionally, it will jump to its normal rate of 200-300 kB/s, but then just die again. Browsing with Firefox seems unaffected, as do downloads of material off the web. I've also tried changing the repositories in /etc/apt/sources.list to their mirrors,  but I seem to encounter similar troubles. Any thoughts or helpful suggestions?

---

### Post by jlc on 2007-01-09
Duplicate post

[http://www.ubuntuforums.org/showthread.php?t=334252&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=334252&highlight=automatix)

If you take out the "us." out of the lines, seems to help out a lot.

---

### Post by quartzy on 2007-01-09
edit /etc/apt/sources.list and remove the "us." prefixes.

---

