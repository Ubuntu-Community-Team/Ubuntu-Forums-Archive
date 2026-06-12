---
title: "Missing Repositories"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by larry on 2005-10-14
Dear All,
I have quite a long list of repositories in my apt sources:

## Uncomment the following two lines to fetch updated software from the network
 deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary main restricted
 deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary-updates main restricted
 deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 


deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java


# here I add multiverse

deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary multiverse
 deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary multiverse


## Backports
#  deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

Now, I tried to update the list of my repositories for breezy (I replaced "hoary" with "breezes" in all its occurrencies).
I ended up with some complains:

larry@hal:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:3 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) breezy Release.gpg
Get:5 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release [30.9kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
Ign [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) breezy/java Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Err [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) breezy/java Packages
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found [IP: 82.211.81.193 80]
Get:6 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release [19.6kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found [IP: 82.211.81.193 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found [IP: 82.211.81.193 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found [IP: 82.211.81.193 80]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [2611B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [937B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [14B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [521B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [14B]
Get:13 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages [585kB]
Get:14 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:15 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Sources [232kB]
Get:16 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:17 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages [2304kB]
Get:18 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Sources [915kB]
Get:19 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages [91.6kB]
Get:20 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Sources [46.9kB]
Get:21 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages [3401B]
Get:22 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:23 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources [1088B]
Get:24 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Fetched 4260kB in 3m1s (23.5kB/s)
Failed to fetch [http://ubuntu.tower-net.de/ubuntu/dists/breezy/java/binary-i386/Packages.gz](http://ubuntu.tower-net.de/ubuntu/dists/breezy/java/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.193 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.193 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

I fear to end up with a broken system if I try to upgrade right now. I do not know if these warnings are serious nor if the new repositories will be added in the near future.
Any suggestions?
Many thanks and apologies for the long post.

Larry

---

### Post by aysiu on 2005-10-14
Breezy doesn't have backports, and that "tower" repository looks fishy. I'd take those out and ```
sudo apt-get update
``` again.

---

