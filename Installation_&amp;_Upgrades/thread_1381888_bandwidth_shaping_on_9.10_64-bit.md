---
title: "bandwidth shaping on 9.10 64-bit"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by pbj on 2010-01-15
i am trying to use the trickle bandwidth shaper with xubutu 9.10 64-bit.

i call trickle as such:

```
trickle -s -d 120 -u 20 <command>
```the error that i get is:

```
ERROR: ld.so: object '/usr/lib/trickle/trickle-overload.so' from LD_PRELOAD cannot be preloaded: ignored.
```i installed trickle using the Synaptic Package manager.

32/64 bit issue?

any ideas?

thanks.

---

