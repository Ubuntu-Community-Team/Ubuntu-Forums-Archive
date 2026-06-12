---
title: "Cant update :("
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by deadcold94 on 2010-06-20
cant update my linux i get this error


W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release](http://archive.ubuntu.com/ubuntu/dists/karmic/Release)  Unable to find expected entry  /etc/apt/sources.list/binary-i386/Packages in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)  Unable to find expected entry  /etc/apt/sources.list/binary-i386/Packages in Meta-index file (malformed Release file?)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release)  Unable to find expected entry  /etc/apt/sources.list/binary-i386/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by zvacet on 2010-06-25
Type in terminal

```
cat /etc/apt/sources.list
```

and post output here.

---

