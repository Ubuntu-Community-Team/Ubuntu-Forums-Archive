---
title: "Error message on Update"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by PDA1 on 2010-05-17
In running Update Manager in 10.04 I get the following error message;

[B]Could not download the upgrades

The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2build2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2build2_i386.deb) Size mismatch[/B]


Also, I can't boot to XP anymore.

Any ideas how to fix the above problems?

---

### Post by zvacet on 2010-05-18
```
sudo aptitude update && sudo aptitude safe-upgrade

sudo aptitude full-upgrade
```

---

