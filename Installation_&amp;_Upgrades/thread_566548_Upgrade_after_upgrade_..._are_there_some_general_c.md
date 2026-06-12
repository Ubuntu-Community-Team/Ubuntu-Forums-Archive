---
title: "Upgrade after upgrade ... are there some general consequences ?"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by Spear on 2007-10-03
Hi,

My old HP Pavilion ZV 5000 was born under Ubuntu Warty Warhog, and progressively migrated under Hoary, Breezy, Dapper, Edgy, Feisty,and soon Gutsy.

I was wondering : do successive migrations have a consequence on the system in general ? Like a bunch of old files lying in many places on the hard disk, or could it be slowlier or ... i don't know in fact :) ?

Those who use another OS sold with most computers novadays probably realised that after a while, that OS, from patch to patch, is slowlier and, more than all, bigger and bigger ... and if you make a fresh install, it's suddenly faster and smaller in size on the hard disk.

I carry those successive Ubuntu upgrades with pride, like a general holding medals on his uniform : i was there at the beginning with that good old laptop and still am now.

But would there be a technical interest in making a fresh new install instead of doing another dist-upgrade ?

Does anybody have an opinion on that technical point ?

---

### Post by Pumalite on 2007-10-03
I'm not in favor of upgrades; I always do a clean install. But there are people in this forum with different opinions. I can tell you this: do you have a working OS?...Yes?...Then you are fine. If not; Gutsy is coming in a few days. Do a clean install after saving your data. I have installed Beta, but I haven't done any updates...waiting for Stable in a few days.

---

### Post by zvacet on 2007-10-03
There is no reason not to continue do things that you use to do.To be sure that you have only latest version of packages 

```
sudo apt-get autoclean
```

This will delete all older versions of packages in var/cache/apt/archives and you will get extra space.

---

### Post by Spear on 2007-10-04
I always clean the packages ;) Imagine the stock after all these upgrades if i did'nt.

So, there's no real misfunction clearly identified after many dist-upgrades compared to a clean install ?

I think i'll try a second, clean install of Feisty on the same computer, and simply compare ;)

---

