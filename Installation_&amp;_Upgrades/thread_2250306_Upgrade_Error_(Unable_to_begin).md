---
title: "Upgrade Error (Unable to begin)"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by ozette9 on 2014-10-27
Trying to upgrade from 14.04 Trusty Tahr to 14.10 Utopic Unicorn, and i'm running into this lovely portfolio of 404 errors:

```

W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/utopic-security/main/binary-armhf/Packages](http://security.ubuntu.com/ubuntu/dists/utopic-security/main/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-armhf/Packages](http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-armhf/Packages](http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-armhf/Packages](http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/utopic/main/binary-armhf/Packages](http://extras.ubuntu.com/ubuntu/dists/utopic/main/binary-armhf/Packages)  404  Not Found
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

I'm an intermediately experienced Ubuntu user, but I'm not sure what to do when it comes to 404 errors in the update. I'm having some issues with my 14.04 install, so the upgrade couldn't come earlier.

Happens every time I try to run the update.

---

### Post by bapoumba on 2014-10-28
There is no binary-armhf on [http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/](http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/), I also get a 404 (Page not found).
Looks to me it is on [http://ports.ubuntu.com/ubuntu-ports/dists/utopic-updates/universe/binary-armhf/](http://ports.ubuntu.com/ubuntu-ports/dists/utopic-updates/universe/binary-armhf/), ie you have to activate the universe repositories in your sources.list or Software Sources.

---

