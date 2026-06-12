---
title: "Failed to fetch on upgrade to 7.10"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Dragonflyoh on 2007-12-09
When attempting to upgrade to 7.10 I receive the follwing errors:
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Any Ideas?

---

### Post by PmDematagoda on 2007-12-09
Open the sources.list file for editing using:-

```
sudo gedit /etc/apt/sources.list
```

Then comment out the Medibuntu repos by typing # in front of them.

After editing the file do:-

```
sudo apt-get update
```

Then try upgrading Ubuntu again.

---

### Post by Dragonflyoh on 2007-12-10
Thank you! Did it and everything worked.

---

