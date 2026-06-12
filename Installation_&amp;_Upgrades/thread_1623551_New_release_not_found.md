---
title: "New release not found?"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by blur xc on 2010-11-16
I'm running 10.04 in a vm, it's where I goof off and not worry about borking anything (snapshots ftw) - so today I tried to upgrade to 10.10, but it tells me there's no new release found...  What's up with that?  

On my home pc, w/ 10.04 on it, the update manger shows a new release is available, and asks if I want to install it...  Not in my vm though...
```

sudo do-release-upgrade 
Checking for a new ubuntu release
No new release found

```

:confused:

BM

---

### Post by wojox on 2010-11-16
You need to go into Software Sources > Updates > Release Upgrade and change it to Normal Releases.

---

### Post by blur xc on 2010-11-16
Sweet- thanks.  Dumb thing to miss.

BM

---

