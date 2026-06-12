---
title: "New Open Source ATI drivers much faster?"
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mazza558 on 2009-01-15
After upgrading to Jaunty, compiz and 2D rendering feels much, much faster than it was on the open-source drivers. Why is this? A new version? Bug fix?

---

### Post by billyShears on 2009-01-15
probably it is faster due to the switch from XAA to EXA:
[https://wiki.ubuntu.com/X/Blueprints/RadeonXaaToExa](https://wiki.ubuntu.com/X/Blueprints/RadeonXaaToExa)

---

### Post by Miguel on 2009-01-15
That, and the ton of EXA fixes that radeon and radeonhd have recieved in the last 6 months! I think it's a mildly safe guess that by the time 9.10 arrives, we'll even have 3D support in R600+ hardware out of the box. And DRI2 plus Gallium plud Kernel Mode Setting is only going to improve the experience versus fglrx. I'd dare say that we'll be within 20% fglrx performance in a year, and with much better 2D and stability.

---

### Post by uljanow on 2009-01-15
It seems like the free radeon drivers don't have PowerPlay support which makes it useless for a laptop.

---

### Post by Miguel on 2009-01-15
type on a terminal
```

man radeon

```

And while on the manpage, type exactly
```

/Dynamic

```
This will search all "Dynamic" words from within the man page. Once you press enter, "n" will bring you to the next one, and "N" to the previous one (this is all for people not used to Vi). That part of the manual states:

[quote="Radeon man page"]
       **Option "DynamicClocks" "boolean"**
Enable  dynamic clock scaling.  The on-chip clocks will scale dynamically based on usage. This can help reduce heat and increase battery life by reducing power usage. Some  users report reduced 3D performance with this enabled. The default is off.
[/quote]

I do concede though that powerplay will perform more aggresive powersaving, but this option shouldn't be forgotten. Furthermore, battery life is never going to be great with a dedicated video card. Note that AFAIK fglrx doesn't perform on the fly power switching in older models (I think older than R500). It sure didn't on my Mobility Radeon 9600.

---

### Post by marmuta on 2009-01-16
> **billyShears said:**
> probably it is faster due to the switch from XAA to EXA:
[/url]

I had actually switched from EXA to XAA in Intrepid because everything felt sluggish with EXA...
Miguel is probably right, radeon EXA has improved a lot recently. Jaunty finally feels as snappy as XP on my lowly X800.

[QUOTE=uljanow]It seems like the free radeon drivers don't have PowerPlay support which makes it useless for a laptop.[/QUOTE]
For ancient chips like mine there is also rovclock in the repos.

---

