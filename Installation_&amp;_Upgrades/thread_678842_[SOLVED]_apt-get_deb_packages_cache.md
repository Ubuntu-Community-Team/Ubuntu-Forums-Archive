---
title: "[SOLVED] apt-get deb packages cache"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by AdHaR on 2008-01-26
i have some deb packages for gutsy from a previous installation (i recently reinstalled gutsy). i noticed that when apt-get downloads packages, it saves them to ```
/var/cache/apt/archives
```

so i saved the deb packages in there from my previous installation, so that when i reinstalled gutsy, i wouldnt need to download them again. now my question is, how can i configure apt-get now so that it picks up my saved deb packages, instead of downloading them again? do i just copy over the saved deb packages to ```
/var/cache/apt/archives
``` and apt-get will pick them up from there instead of the internet?

---

### Post by BlackNinjaVirus on 2008-01-26
> **AdHaR said:**
> i have some deb packages for gutsy from a previous installation (i recently reinstalled gutsy). i noticed that when apt-get downloads packages, it saves them to ```
/var/cache/apt/archives
```

so i saved the deb packages in there from my previous installation, so that when i reinstalled gutsy, i wouldnt need to download them again. now my question is, how can i configure apt-get now so that it picks up my saved deb packages, instead of downloading them again? do i just copy over the saved deb packages to ```
/var/cache/apt/archives
``` and apt-get will pick them up from there instead of the internet?

Yes, you are correct. When my APT-CD backup didn't work I put them in : /var/cache/apt/archives
and they work picked up without needing to be re-downloaded. Make sure that you 'apt-get update' before installing updates to refresh and catalog what you have in the archives.

---

### Post by zvacet on 2008-01-26
Yes,put them in var/cache/apt/archives.

---

### Post by AdHaR on 2008-01-26
thanks guys :)

btw how do i change the thread title to [SOLVED]?...do i have to?

---

