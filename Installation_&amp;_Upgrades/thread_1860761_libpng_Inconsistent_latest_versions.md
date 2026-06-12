---
title: "libpng: Inconsistent latest versions"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by robinhood2008 on 2011-10-15
I'm running Ubuntu 11.10 "Oneiric Ocelot," trying to run Snes9x version 1.53. But when I try to do this, the computer does absolutely nothing. Upon further investigation, when I try to run it from a terminal, the terminal tells me this:

```
./snes9x-gtk: error while loading shared libraries: libpng14.so.14: cannot open shared object file: No such file or directory
```

Upon researching this problem, I found out that my 'libpng' package is possibly out of date. So I searched for the latest version of 'libpng' and found it to be version 1.5.5. But Ubuntu Software Center disagrees: it claims that the latest available version of 'libpng' is version 1.2.46!

This leaves me in a quandary about what to do. I want to run Snes9x 1.53, but I don't want to do anything that might end up cratering my Ubuntu system. Is it possible to upgrade my version of 'libpng' to version 1.5.5 on Ubuntu, and if so, how do I go about doing that?

Brandon Taylor

---

