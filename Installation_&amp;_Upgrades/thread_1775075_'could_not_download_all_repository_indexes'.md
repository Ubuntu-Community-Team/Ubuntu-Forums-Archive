---
title: "'could not download all repository indexes'"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by Smiley Coyote on 2011-06-04
Whenever I do an update, I get updates but first I get the following (it's accompanied by a red icon with an exclamation point so I figure it is important):

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

----------------------------------------------------------

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2011-06-04
> **Smiley Coyote said:**
> Whenever I do an update, I get updates but first I get the following (it's accompanied by a red icon with an exclamation point so I figure it is important):

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

----------------------------------------------------------

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

It is trying to access the Jaunty-backport repositories which are no longer active as Jaunty is no longer supported.

You can remove them using Software Sources GUI.

Good Luck

---

