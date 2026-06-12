---
title: "Synaptic Get STUCK with EMESENE"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by whiskyansoda on 2008-04-15
Ok I don-t know exactly what happend, but I know which is the main problem, and is EMESENE, I try to install it, but something happend, then the installation fail, and the synaptic stucks there...also I cant remove the installation neither reinstall it. 

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package emesene needs to be reinstalled, but I can't find an archive for it.'

---

### Post by Partyboi2 on 2008-04-15
Open a terminal (Applications>Accessories>Terminal) and try this:
```
 sudo dpkg --remove --force-remove-reinstreq emesene
```

---

