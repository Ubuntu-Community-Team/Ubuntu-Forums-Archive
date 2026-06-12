---
title: "Fuseiso Problem"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by VoyeurOne on 2008-01-13
I tried to install fusio  as a deb package with package manager, it stopped before completing and package manager froze.

Now when I try to open Synaptic package manager I get this error, and Synaptic package manager closes after I click OK.

E: The package fuseiso needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Any help in cleaning this mess would be greatly appreciated.

---

### Post by Partyboi2 on 2008-01-13
In a terminal
try
```
sudo dpkg --remove --force-remove-reinstreq fuseiso
```

---

### Post by VoyeurOne on 2008-01-13
Again I was saved by the forums...... Thanks and solved as far as I can see.

---

