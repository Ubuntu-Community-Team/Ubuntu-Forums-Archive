---
title: "swrast problems"
date: 2014-12-16
forum: Installation &amp; Upgrades
---

### Post by nibal on 2014-12-16
I have Ubuntu 14.04 64x up to date. I need to use libGL for a project. Doesn't work :-(
When I type glxinfo I get:

```

libGL: driver does not expose __driDriverGetExtensions_swrast(): /usr/lib/fglrx/dri/swrast_dri.so: undefined symbol: __driDriverGetExtensions_swrast
libGL: Can't open configuration file /home/nikos/.drirc: No such file or directory.
libGL: Can't open configuration file /home/nikos/.drirc: No such file or directory.
libGL error: failed to load driver: swrast

```

Tried:
```

sudo apt-get install --reinstall libgl1-mesa-dri

```

It installed a fresh swrast_dri.so, but I still get the same error. Anyone knows where can i get a patch for it?

TIA,
Nikos

---

### Post by nibal on 2014-12-16
It turns out that this is a mesa problem ever since 10.1.1. Now at 10.1.3 still haven't fixed it :mad:. Not only Ubuntu 14.04, but a host of other Linux have also broken mesa implementations.
Still need some ideas on how best to repair this. Are there any patches or updates without this problem, or do i have to compile from sources?

---

