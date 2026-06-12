---
title: "problems with audio"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by ueghio on 2008-03-14
I've installed ubuntu 7.10 on my hp pavillon dv6580el but I can't hear any sound..on the volume control appears a red symbol (mute) and says "No volume control GStreamer plugins and/or devices found".Does anyone know what plugins should I install from synaptic?Thanks for your help

---

### Post by zvacet on 2008-03-14
First be sure that you have all repos open.System>admin>software sources>check all under Ubuntu software and updates tab.Reload.Applications>accessories>terminal type

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Pumalite on 2008-03-14
Post:
lshw -C sound

---

