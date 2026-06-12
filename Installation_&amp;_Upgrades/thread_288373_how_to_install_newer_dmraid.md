---
title: "how to install newer dmraid"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by t-minus10 on 2006-10-29
So I'm trying to install ubuntu for my first time, and I am (essentially) a linux noob.

Anyways, I want to install ubuntu onto an ich7r raid 5 fakeraid array (w/ 4 250gb samsung spinpoint drives).  I need compatibility with windows, hence the fakeraid.  

I want to use raid 5, but the newest version of dmraid on synaptic is RC9. RC10 is the oldest release with raid 5 support.

I'm wondering how to install dmraid either from source or from 'revu'.

Downloading the dmraid source left me somewhat lost.  When running ./configure it gave me the "c compiler cannot create executables"

'revu' is something I don't really understand at all.

anyways, any ideas?

---

### Post by njko on 2006-12-14
from the debian repository
[http://packages.debian.org/unstable/admin/dmraid](http://packages.debian.org/unstable/admin/dmraid)

you need to install libsepool and libselinux first.

---

### Post by Robbyx on 2006-12-27
T-10

Did you manage to install the dmrade?

Robin

---

