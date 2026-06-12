---
title: "Can not update repositories"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by Steve Danahey on 2013-10-19
Hi, I have been away from ubuntu for a while, like 8 months because I dual boot and when I came back and tried to update everything I ran into errors. It said to check internet connection though I know I am not behind a proxy and have great connection. Here is the actual error code, if anyone can help me out I would greatly appriciate it. Thanks

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by steeldriver on 2013-10-19
Are those karmic-backports? If so your system is likely beyond EOL - see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Steve Danahey on 2013-10-19
If i burn a copy of a new ubuntu and install it will I lose all my data? or just the system data? I have close to a terabyte of music on this system and really do not want to have to re rip everything.

---

### Post by steeldriver on 2013-10-19
Don't count on retaining any data - it depends how your current system is partitioned (i.e. whether the data is on a separate partition) however accidents can happen even then so you should back up anything you want to keep

---

