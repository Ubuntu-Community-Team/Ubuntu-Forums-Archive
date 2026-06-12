---
title: "Need help installing lime wire"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by Ricey on 2008-02-14
Hi All

I recently downloaded and tried to install lime wire (limewirelinux.deb) but I am having some problems. In the synaptic package manager I get an error as shown below.


[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]


I have no idea what to do or what this error means, it would be great if some one could help me.

Cheers

---

### Post by zvacet on 2008-02-14
Programs>accessories>terminal

```
sudo dpkg --configure -a
```

---

