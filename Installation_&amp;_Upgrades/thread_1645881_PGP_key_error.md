---
title: "PGP key error"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by researcher123 on 2010-12-15
I want to upgrade my system from behind a firewall when I got the following error

PGP error: [http://deb.opera.com](http://deb.opera.com)  stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/source/Sources.gz](http://deb.opera.com/opera/dists/stable/non-free/source/Sources.gz)  404  Not Found Some index files failed to download, they have been ignored, or old ones used instead."

Please help.

---

### Post by sikander3786 on 2010-12-15
Either add the missing Opera key by,

```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```

If that doesn't help, edit your sources.list by,

```
gksudo gedit /etc/apt/sources.list
```

And put a # at the beginning of Opera line. Save and close and try update/upgrade again.

---

