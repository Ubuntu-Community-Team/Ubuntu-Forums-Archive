---
title: "Get Error with Cupys when I try to update"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by MaxDaisy on 2008-02-27
Whenever I try and install updates I get the following error message:

IE: cupsys: subprocess post-installation script returned error exit status 1
E: hplip: dependency problems - leaving unconfigured
E: hpijs: dependency problems - leaving unconfigured

---

### Post by Partyboi2 on 2008-02-27
try in a terminal (Applications>Accessories>Terminal)
```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```

---

### Post by MaxDaisy on 2008-02-27
Thanks ParyBoi2,

I tried that and it gives me the following error/output:

Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.7); however:
  Package hplip is not configured yet.
 hpijs depends on hplip (>= 2.7.12-0ubuntu2~gutsy1); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 hpijs

---

### Post by FastZ on 2008-03-17
Ok there are around 4 or five of these threads on this forum that all pertain to this cupsys, hplip, and hpijs issue with apt/aptitude, has anyone found a fix for this problem?  I've tried everything suggested by other members of the forums and not a single one has made any change in the problem here.  Anyone else have some suggestions on how to fix this problem?

---

