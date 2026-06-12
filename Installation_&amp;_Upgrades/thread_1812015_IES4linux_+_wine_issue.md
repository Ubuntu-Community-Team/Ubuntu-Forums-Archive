---
title: "IES4linux + wine issue"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by skatinjj on 2011-07-25
Everytime I try to install ies4linux onto my system I get this error about not having the latest wine installed and it can not create wineprefix or something to that effect.  I have attached the log file I created.

Any suggestions?

FYI
Running 11.04 (minimal install) with fluxbox installed.

---

### Post by skatinjj on 2011-07-25
Apparently I just had to do:

```
sudo apt-get install wine1.0
```

so the program could create a wine prefix

---

### Post by naga2raja on 2011-12-14
Thanks skatinjj,

Its works so cool , also the version is wine1.2 in oneiric

---

