---
title: "still on 8.04 and wanted to upgrade"
date: 2013-11-07
forum: Installation &amp; Upgrades
---

### Post by anarchy2 on 2013-11-07
So i got on my ubuntu 8.04 server today and try to do a apt-get update and get the following errors:
```

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
  404 Not Found [IP: 91.189.91.14 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
404 Not Found [IP: 91.189.91.14 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
  404 Not Found [IP: 91.189.91.14 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources
  404 Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources
  404 Not Found [IP: 91.189.91.14 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.91.14 80]


E: Some index files failed to download, they have been ignored, or old ones used instead.






```

any ideas how to fix this and move on to 10.04 and so on from there?

---

### Post by phyzik on 2013-11-07
Sorry for such a bad answer, but upgrading for more than 2 releases is definitely not a good idea.

You should backup your data and make a clean install.

---

### Post by deadflowr on 2013-11-07
> **damien37 said:**
> Sorry for such a bad answer, but upgrading for more than 2 releases is definitely not a good idea.

You should backup your data and make a clean install.

It's only one upgrade from 8.04 to 10.04.
I do agree that backing the files up and doing a fresh install is the best way.
Moving past 10.04 and onto 12.04 will keep you up to date and supported longer.

But if backing up and reinstalling is not an option, look over this.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by grahammechanical on 2013-11-07
These are the instructions for upgrading Ubuntu server to the next LTS release

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

Ubuntu 8.04 server had 5 years support. That has now ended and that is why you are getting those error messages but you can upgrade to Ubuntu 10.04 server. It also has 5 years support so it is still supported (I work out it is 18 months). If you want you can then move on to 12.04 server, also with 5 years support (18 months used up). After that there is 14.04 server with 5 years support (out near the end of April 2014)

When we are using an LTS release we can upgrade to the next LTS release. When we are using an Interim (now called standard releases) we can only upgrade to the next version that was released. We cannot by-pass interim releases.

Regards.

---

