---
title: "Error updating"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by cezar_dan on 2012-06-14
Every time I check for new updates I get this error message:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ro.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz](http://ro.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ro.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz](http://ro.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ro.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz](http://ro.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ro.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz](http://ro.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

What does it mean exactly and how can I fix it?

I'm using Ubuntu 10.04

---

### Post by wojox on 2012-06-14
Karmic is EOL (end of life).

You could do a fresh install or enable these repo's [Index of /ubuntu/dists]("http://old-releases.ubuntu.com/ubuntu/dists/")

---

### Post by fantab on 2012-06-15
Since Karmic has reached End Of Life, remove Karmic repos.

---

