---
title: "apt database is stuck with libreoffice package - can't install anything"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by landersohn on 2012-12-08
Please help, I have a big problem!
At some point I installed libreoffice 3.6.0 and later updagreded to 3.6.4. Problem is, there are two language packages left from 3.6.0 (es and fr) which I tried to remove using synaptic.
The removal failed with a post-removal script error. Now I am stuck:
the packages are marked for removal, unmarking thoses in synaptic didn't work and I can not install anything else because any install operation tries to remove these packages first which fails. using "-f" didn't help.

Does anybody know how I can get rid of these packages or at least unmark for removal?

Thanks

---

### Post by LuisGMarine on 2012-12-08
You can try these:

```
sudo apt-get clean
sudo apt-get autoclean
```

---

### Post by NightsShadeQueen on 2012-12-08
If that doesn't work, try 

```
sudo dpkg --remove --force-remove-reinstreq PACKAGENAME
```

This will *not* remove any dependents, though

?

---

### Post by phoenixstew49 on 2012-12-08
Should the solution given above not work:

```
sudo apt-get clean
sudo apt-get autoclean
```This slightly dirty trick (from [http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)) may provide the solution. I've adapted it to your package:

```
sudo rm /var/lib/dpkg/info/libreoffice-l10n-fr.* /var/lib/dpkg/info/libreoffice-l10n-es.*
sudo dpkg --remove --force-remove-reinstreq libreoffice-l10n-fr
sudo dpkg --remove --force-remove-reinstreq libreoffice-l10n-es

```

---

### Post by landersohn on 2012-12-09
Thank you all. The clean autoclean didn't work. I'll try the "dirty" trick.
I got halfway there by editing /var/lib/dpkg/status manually and changing the status of these packgages. I still get errors but at least I can install other stuff.

---

### Post by landersohn on 2012-12-09
Thanks, the "dirty" trick worked like a charm.

---

