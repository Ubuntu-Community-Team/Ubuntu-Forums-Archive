---
title: "Malformed Release File with 8.04 Upgrade?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Naurek on 2008-04-26
I am upgrading from 7.10 to 8.04. I am using the Upgrade Manager, and it successfully completes the first step (Preparing to Upgrade). When it reaches the second step (Setting new software channels), I receive the following error:

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
```

The installation does not complete. I have the latest updates for 7.10. Anyone else have this issue and know how to resolve it?

Thank you very much.

---

### Post by derekweber on 2008-04-26
Same for me from [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/Releases](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/hardy-updates/Releases).
Unable to find expected entry universes/source/Sources.

I looked at the file it mentions ("Releases") and I could see an entry for universes/source/Sources, so it's there.

Same behaviour with update not completing too.

Any tips anyone?

---

