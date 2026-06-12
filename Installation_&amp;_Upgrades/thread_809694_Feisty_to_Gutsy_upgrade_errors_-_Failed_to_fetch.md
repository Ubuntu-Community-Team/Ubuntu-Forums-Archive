---
title: "Feisty to Gutsy upgrade errors - Failed to fetch"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by OzzMosiz on 2008-05-27
Whenever I try and upgrade using the Upgrade Wizard I keep getting this error:
Failed to fetch [http://download.tuxfamily.org/3v1dev/dists/feisty/3v1n0/binary-i386/Packages.gz](http://download.tuxfamily.org/3v1dev/dists/feisty/3v1n0/binary-i386/Packages.gz) 404 Not Found

Google has not yielded any results when searching this :(

Any advice?

---

### Post by overdrank on 2008-05-27
> **OzzMosiz said:**
> Whenever I try and upgrade using the Upgrade Wizard I keep getting this error:
Failed to fetch [http://download.tuxfamily.org/3v1dev/dists/feisty/3v1n0/binary-i386/Packages.gz](http://download.tuxfamily.org/3v1dev/dists/feisty/3v1n0/binary-i386/Packages.gz) 404 Not Found

Google has not yielded any results when searching this :(

Any advice?

HI and I believe when upgrading you will need to remove all third party repos or it can cause errors. 
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by OzzMosiz on 2008-05-27
overdrank (cool nick ;) )
thanks for taking the time to respond, I'll check out out...

---

### Post by OzzMosiz on 2008-05-27
Those pages don't seem to help :( really annoying this is.
Can someone suggest what would be good to put in my sources.list - I'm sure this is the problem.

Edit: Remove  [http://download.tuxfamily.org](http://download.tuxfamily.org) from sources.list and its working

Overdrank - cheers-  didn't realise it was 3rd party.

---

