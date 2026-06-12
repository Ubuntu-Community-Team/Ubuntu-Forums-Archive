---
title: "&quot;sudo apt-get update&quot; not working"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by kophyo48 on 2011-01-11
Hi,

I am just a newbie using Ubuntu (or any other Linux distribution).

I basically needed to run "sudo apt-get install subversion" but I was told that I need to update my "apt-get".

So when I try "sudo apt-get update". I got the following errors:

Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid Release
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates Release
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/main Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/restricted Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/main Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/restricted Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/universe Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/universe Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/multiverse Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/multiverse Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/main Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/main Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/universe Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/universe Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/multiverse Sources
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/main Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/restricted Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/main Sources
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/restricted Sources
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/universe Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/universe Sources
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/multiverse Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/multiverse Sources
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/main Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/main Sources
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/multiverse Sources
  404 Not Found [IP: 91.189.92.169 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.169 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.



My  /etc/apt/sources.list is as follows:

# 
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted

#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


Please somebody help!!

Many thanks.

--
Phyo

---

### Post by oldos2er on 2011-01-11
8.10 reached its end-of-life last April, but you can try the old-releases repos: [http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/](http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/)

---

### Post by kophyo48 on 2011-01-11
Ah.. didn't know that!

Anyway, I changed all my "[http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/")" links to "[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)" and now it works like a charm.

Thank you so much!

--

Phyo

---

### Post by oldos2er on 2011-01-11
You're welcome.

---

