---
title: "Wine"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Ivan_Linux on 2007-04-25
So I have visited the Wine official site, downloaded wine and installed it using the terminal as explained. But what now? I don't see it anywhere, i don't know how to use it now. Thanks in advance! Ivan. :guitar:

---

### Post by tr2 on 2007-04-25
> **Ivan_Linux said:**
> So I have visited the Wine official site, downloaded wine and installed it using the terminal as explained. But what now? I don't see it anywhere, i don't know how to use it now. Thanks in advance! Ivan.Try```
wine --version
``` on the console to see whether you were successful with installing wine. Then try ```
wine whateverwindowsprogramyouwanttorun.exe
``` to start a windows program. If you need to configure wine beforehand use ```
wineconfig
```
EDIT: Corrected typos.

---

### Post by Ivan_Linux on 2007-04-25
command not recognised

---

### Post by tr2 on 2007-04-26
> **Ivan_Linux said:**
> command not recognisedLooks like wine wasn't installed successfully then. Try ```
sudo aptitude install wine
```

---

