---
title: "I can not install kile on ubuntu 13.04"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by dnovai on 2015-03-01
Hi guys,

I had tried to install Kile from repository (Ubuntu 13.04). There is a option "Available from the "universe" source". Then, I clicked on "Use this source", but I got the following message:

Failed to download repository information.

Check your internet connection.

```
W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/restricted/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring/restricted/source/Sources)  404  Not Found, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/main/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/multiverse/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring/multiverse/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/universe/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/main/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/restricted/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring/restricted/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/universe/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring/universe/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/multiverse/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring/multiverse/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/main/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/restricted/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/universe/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/restricted/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/main/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/multiverse/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/multiverse/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/universe/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/main/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/universe/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/universe/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/main/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/restricted/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/universe/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/multiverse/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/multiverse/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/main/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/universe/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/universe/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/restricted/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-security/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/main/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-security/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/multiverse/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-security/multiverse/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/universe/source/Sources](http://mirror.netlinux.cl/ubuntu/dists/raring-security/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/main/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-security/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/restricted/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-security/restricted/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/universe/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-security/universe/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/main/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-security/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-security/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-security/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://mirror.netlinux.cl/ubuntu/dists/raring-security/multiverse/binary-i386/Packages](http://mirror.netlinux.cl/ubuntu/dists/raring-security/multiverse/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Of course, I checked my i-net connection and everything is OK.

What should I do?

---

### Post by Bucky Ball on 2015-03-01
13.04 is no longer supported. The repos have been closed for sometime. Please upgrade/reinstall to a supported release. 12.04 LTS and 14.04 LTS both have five years support (2017 and 2019 repectively), 14.10 is supported for about five more months.

See [here]("http://ubuntuforums.org/showthread.php?t=2229730") for recommendations re. EOL releases. If you have older hardware and it's struggling to run the newer releases of Ubuntu, try Xubuntu or Lubuntu. 

Good luck. ;)

PS: Please use [code] tags rather than [quote] tags for terminal output. Thanks. See the last link in my signature for how.

---

### Post by sammiev on 2015-03-01
Sorry to say that 13.04 has reached end of life. (EOL)

You will need to move on to 14.04LTS for a long term version. The newer version from 14.10 and up will be short lived version until we reach 16.04 down the road.

---

### Post by dnovai on 2015-03-01
Ok, Probably I must upgrade to 14.04 because I do not want to lose my GPU configuration.

Thank you for your help.

---

### Post by sammiev on 2015-03-01
Make sure you backup all your data first.

---

