---
title: "'Not all updates can be installed' error"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by forgeuk on 2007-06-30
Anyone help me out with this error, each time the update manager fires up, it says that, and both the compiz-core and compiz-plugins are greyed-out. I'm running 7.04, so it won't allow me to uninstall those two, I don't use the desktop effect. I had beryl on instead for a while, but now just use metacity.

I read somewhere it could be Automatix causing the problem, so I took that off, but still no change, also done a ```
sudo apt-get update
sudo apt-get upgrade
```

It does install other updates, so not really a big problem, just a little annoying that popping up every time theres an update available.

Thanks

---

### Post by mayfer on 2007-10-18
open up synaptic, and click "mark all upgrades"
that should remove the package that's causing this problem, and mark all the remaining upgrades.

---

### Post by Slade Winstone on 2007-10-19
I was having this problem too (maybe left-overs from Automatix?)

I tried the Synaptic >> "Mark All Upgrades" but this didn't work for me.

What worked was to use Synaptic to remove compiz-core and the re-install the correct version for Gutsy.  Now all the upgrades work fine and I also have my title bar, minimize, maximize buttons showing again.

Slade.

---

