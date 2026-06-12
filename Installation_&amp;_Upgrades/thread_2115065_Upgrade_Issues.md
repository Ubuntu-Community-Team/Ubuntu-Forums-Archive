---
title: "Upgrade Issues"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by cbxroger on 2013-02-11
After upgrading to to 12.10, I no longer can access my menus or launchers. I can get 'terminal' and I have 12.10 installed. The page that I enter my name and password onto says 12.04.

Sudo apt-get -f install errors out and there are 56 items not yet fully installed or removed. When I proceed, it errors out with multiple error messages, many dealing with pulseaudio and conflicts with AMD64 and i386. 

Using terminal I am able to start firefox, system monitor, and top.

What should I try next?

---

### Post by zvacet on 2013-02-14
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Post output here.

---

