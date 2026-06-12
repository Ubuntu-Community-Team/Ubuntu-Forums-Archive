---
title: "DPKG: Get last updated programs"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by raffaele181188 on 2010-06-27
Due to Lucid upgrade in May, I got a minor performance problem: since GDM login to a usable desktop it took ~20seconds (on Karmic it was immediate). I thought it was a known regression, so I stop to mind it. Today I discovered that my GNOME loading time is back to ~0 seconds :D
I'm truly happy and I'd like to know whether there is a way through dpkg or apt to get the latest package upgrades, in order to realize what has gone on, since I use autoupdates

So, is there a way to see what package did I upgrade since the last 2/3 days?

---

### Post by sisco311 on 2010-06-27
> **raffaele181188 said:**
> 
So, is there a way to see what package did I upgrade since the last 2/3 days?

Assuming that you didn't clear the cache, try something like:
```
find /var/cache/apt/archives/ -mtime 3
```

---

