---
title: "Upgrading Edgy Server 404 Not Found Error"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by gwong86 on 2006-11-18
I have been trying to update my Ubuntu server in preparation for setting up a spam/antivirus relaying server. When I try to do the apt-get update, most of it goes through and then I get about 6 errors ending with "404 Not Found". 

**Here are the results from the apt-get install:**

Ign [http://us.archive.com](http://us.archive.com) edgy-updates Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://us.archive.com](http://us.archive.com) edgy-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://us.archive.com](http://us.archive.com) edgy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://us.archive.com](http://us.archive.com) edgy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Ign [http://us.archive.com](http://us.archive.com) edgy/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://us.archive.com](http://us.archive.com) edgy/multiverse Translation-en_US
Ign [http://us.archive.com](http://us.archive.com) edgy-updates Release
Ign [http://us.archive.com](http://us.archive.com) edgy Release
Ign [http://us.archive.com](http://us.archive.com) edgy-updates/main Packages
Ign [http://us.archive.com](http://us.archive.com) edgy-updates/restricted Packages
Ign [http://us.archive.com](http://us.archive.com) edgy/universe Packages
Ign [http://us.archive.com](http://us.archive.com) edgy/multiverse Packages
Ign [http://us.archive.com](http://us.archive.com) edgy/universe Sources
Ign [http://us.archive.com](http://us.archive.com) edgy/multiverse Sources
Err [http://us.archive.com](http://us.archive.com) edgy-updates/main Packages
  404 Not Found
Err [http://us.archive.com](http://us.archive.com) edgy-updates/restricted Packages
  404 Not Found
Err [http://us.archive.com](http://us.archive.com) edgy/universe Packages
  404 Not Found
Err [http://us.archive.com](http://us.archive.com) edgy/multiverse Packages
  404 Not Found
Err [http://us.archive.com](http://us.archive.com) edgy/universe Sources
  404 Not Found
Err [http://us.archive.com](http://us.archive.com) edgy/multiverse Sources
  404 Not Found
Fetched 3B in 3s (1B/s)
Failed to fetch [http://us.archive.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://us.archive.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://us.archive.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://us.archive.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://us.archive.com/ubuntu/dists/edgy/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://us.archive.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://us.archive.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

**Here is a copy of my sources.list:**


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://us.archive.com/ubuntu](http://us.archive.com/ubuntu) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://us.archive.com/ubuntu](http://us.archive.com/ubuntu) edgy universe multiverse
deb-src [http://us.archive.com/ubuntu](http://us.archive.com/ubuntu) edgy universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

I have tried to replace us.archive.com with au.archive.com and i still got the same problems. I have tried to do this from 2 different locations thinking that it might have been my network configuration but it was not.

Any ideas why I keep getting this? Thanks!

---

