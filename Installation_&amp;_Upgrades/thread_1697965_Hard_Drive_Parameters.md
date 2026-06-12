---
title: "Hard Drive Parameters"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by twjolson on 2011-03-01
I am working on a shell script, and I was wondering if there was a command that will give me all the same info about a hard drive (model, manufacturer, location, size, etc) as it gives in the Disk Utility program?  That is a GUI only application.

I know about hdparm, but that isn't working on my local machine, so I can't tell if that is a good fit.

---

### Post by dabl on 2011-03-01
> **twjolson said:**
> 

I know about hdparm, but that isn't working on my local machine, 

```
sudo apt-get update && apt-get install smartmontools
```

```
sudo smartctl -ia /dev/sda
```

for /dev/sda.

---

### Post by twjolson on 2011-03-01
Yes, that is exactly what I needed.  Thank you very much.

---

