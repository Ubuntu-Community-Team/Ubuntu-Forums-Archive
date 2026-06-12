---
title: "[SOLVED] Installing LMMS from source (and it's not working)"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by Envergure on 2008-09-01
Since LMMS 0.4b isn't available as a .deb i downloaded the sources.  I followed the included instructions but i get this error:
```
* VST-instrument hoster       : not found, please install (lib)wine-dev (or similiar) and gcc-multilib (only for 64 bit systems)
* VST-effect hoster           : not found, please install (lib)wine-dev (or similiar) and gcc-multilib (only for 64 bit systems)
```

wine-dev and gcc-multilib are both installed, according to Synaptic.


Figured it out:  reinstalled gcc-multilib and it worked.

---

### Post by Envergure on 2008-09-07
Nevermind, i just compiled it without VST support :)  A nuisance, but not a big problem.

---

