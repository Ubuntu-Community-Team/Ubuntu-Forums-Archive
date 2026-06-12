---
title: "Monopod Fails to Configure"
date: 2005-09-04
forum: Installation &amp; Upgrades
---

### Post by coxc24 on 2005-09-04
When trying to use the ./configure command in the monopod directory I get the rror "checking for mono >= 1.1.6... Package mono was not found in the pkg-config search path.
Perhaps you should add the directory containing `mono.pc'
to the PKG_CONFIG_PATH environment variable
No package 'mono' found"

I have used apt to install mono but still get the above error. Any help would appreciated.

---

### Post by PuleX on 2005-10-14
Monopod is in Pete's openfestis.org repository. 
I added the sources, but when trying to install monopod synaptic threw an error about dependencies. I sent Pete an e-mail about it, so hopefully it will be fixed in the near future and everyone can install it from there or from universe.

---

### Post by YumZ on 2006-02-20
mono-devel and libmono-dev are what you need

---

