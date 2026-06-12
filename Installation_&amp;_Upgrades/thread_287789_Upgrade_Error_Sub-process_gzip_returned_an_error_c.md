---
title: "Upgrade Error: Sub-process gzip returned an error code"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by ScottSatkin on 2006-10-29
When I update using:
```
gksu "update-manager -c"
```
I get the following error:

> 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

I tried:
```
sudo apt-get install --reinstall gzip
```

However, I still get the same error.

Anyone else getting this error?  Any advice?

---

### Post by unisol on 2006-10-29
the repositories may be down or are getting updated they also could be flooded with other people trying to update give it a little while try again

---

