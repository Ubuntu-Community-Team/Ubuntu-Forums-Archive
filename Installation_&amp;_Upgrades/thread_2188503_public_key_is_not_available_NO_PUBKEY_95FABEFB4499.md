---
title: "public key is not available: NO_PUBKEY 95FABEFB4499973B"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by gunnvor on 2013-11-17
After trying:

```
sudo apt-get update
```

I get:

```
GPG error: http://ppa.launchpad.net saucy Release: The following  signatures couldn't be verified because the public key is not available:  NO_PUBKEY 95FABEFB4499973B
```

Xubuntu 13.10 64 bits

Help welcomed

---

### Post by oldos2er on 2013-11-17
```
sudo apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys 95FABEFB4499973B && sudo apt-get update
```

---

