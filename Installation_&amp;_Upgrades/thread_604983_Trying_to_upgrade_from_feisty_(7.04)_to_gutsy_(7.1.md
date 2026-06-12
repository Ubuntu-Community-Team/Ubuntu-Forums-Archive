---
title: "Trying to upgrade from feisty (7.04) to gutsy (7.10)"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by mad616 on 2007-11-06
When trying to upgrade with the update manager I get the following error message soon after the upgrade starts.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found

I think I need to add these repositories but am not sure how.

Thanks, any help is greatly appreciated.

---

### Post by bulldog on 2007-11-06
I think you need to disable those repositories:)
And all of the non official repo's for that matter.
```
gksu gedit /etc/apt/sources.list
```

---

### Post by Pumalite on 2007-11-06
See if this works:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list

sudo apt-get update

sudo apt-get dist-upgrade

---

