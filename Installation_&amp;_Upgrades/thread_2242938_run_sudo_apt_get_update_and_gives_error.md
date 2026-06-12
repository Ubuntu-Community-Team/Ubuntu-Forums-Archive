---
title: "run sudo apt get update and gives error"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by Mohammad_Javad on 2014-09-05
Hi 

When i write [COLOR=#b22222]sudo apt-get update[/COLOR] in Terminal i give this [COLOR=#b22222]error


[/COLOR]
```
Fetched 177 kB in 1min 27s (2,031 B/s)W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A1715D88E1DF1F24
W: Failed to fetch http://ppa.launchpad.net/pcf/miro-releases/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/pcf/miro-releases/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```


how can fix it ??

---

### Post by grahammechanical on 2014-09-05
PPAs are useful for installing certain software that is not available in the Ubuntu software centre. After installing the software I always disable the PPA in Software and Updates.

---

