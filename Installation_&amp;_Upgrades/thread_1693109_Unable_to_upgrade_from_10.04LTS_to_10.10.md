---
title: "Unable to upgrade from 10.04LTS to 10.10"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by suresnjain on 2011-02-22
I am running 10.04 LTS inside Windowsxp.LTS is totally updated.What is more,in the settings section of update manager I have ticked to show normal releases as well.Still,update manager is not displaying "10.10 is available"Thus,unable to upgrade.How to solve this?Help appreciated in simple language:confused:

---

### Post by zvacet on 2011-02-22
Try

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

After that see if you can upgrade via update manager.

---

### Post by suresnjain on 2011-02-22
Also tried in the terminal update-manager -d and this displayed "10.10 is available" just once in the update manager but after that this tip also failed to respond.

---

### Post by suresnjain on 2011-02-22
Tried the method suggested by zvacet but no result

---

