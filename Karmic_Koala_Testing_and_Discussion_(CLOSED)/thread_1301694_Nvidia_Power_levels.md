---
title: "Nvidia Power levels"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ayle on 2009-10-26
Hi, for some reason my 9600m GT is stuck in "Performance mode" even when using battery. I tried adding:

```
Option  "RegistryDwords"	"PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3"
```

in the device section of my xorg.conf but that doesn't seem to be doing anything... I'm using the catalyst v185 by the way.

---

