---
title: "Failed to fetch 404 Error on upgrade."
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by r42xer on 2013-01-30
When I run apt-get update (as root), I get this error message. I can also not install from the Software Center (nor from apt-get install)

```
Ign http://archive.ubuntu.com maverick Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/ maverick/main Translation-en_US
Ign http://archive.ubuntu.com maverick-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://ppa.launchpad.net maverick Release  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://archive.ubuntu.com maverick-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://archive.ubuntu.com maverick Release
Ign http://archive.ubuntu.com maverick-updates Release
Ign http://archive.ubuntu.com maverick-security Release
Hit http://ppa.launchpad.net maverick/main Sources
Ign http://archive.ubuntu.com maverick/main Sources
Ign http://archive.ubuntu.com maverick/restricted Sources
Ign http://archive.ubuntu.com maverick/universe Sources
Ign http://archive.ubuntu.com maverick/multiverse Sources
Ign http://archive.ubuntu.com maverick/main i386 Packages
Ign http://archive.ubuntu.com maverick/restricted i386 Packages
Ign http://archive.ubuntu.com maverick/universe i386 Packages
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick-updates/main Sources
Ign http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Ign http://archive.ubuntu.com maverick-updates/universe Sources
Ign http://archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick-security/main Sources
Ign http://archive.ubuntu.com maverick-security/restricted Sources
Ign http://archive.ubuntu.com maverick-security/universe Sources
Ign http://archive.ubuntu.com maverick-security/multiverse Sources
Ign http://archive.ubuntu.com maverick-security/main i386 Packages
Ign http://archive.ubuntu.com maverick-security/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-security/universe i386 Packages
Ign http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick/main Sources
Ign http://archive.ubuntu.com maverick/restricted Sources
Ign http://archive.ubuntu.com maverick/universe Sources
Ign http://archive.ubuntu.com maverick/multiverse Sources
Ign http://archive.ubuntu.com maverick/main i386 Packages
Ign http://archive.ubuntu.com maverick/restricted i386 Packages
Ign http://archive.ubuntu.com maverick/universe i386 Packages
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick-updates/main Sources
Ign http://archive.ubuntu.com maverick-updates/restricted Sources
Ign http://archive.ubuntu.com maverick-updates/universe Sources
Ign http://archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Ign http://archive.ubuntu.com maverick-security/main Sources
Ign http://archive.ubuntu.com maverick-security/restricted Sources
Ign http://archive.ubuntu.com maverick-security/universe Sources
Ign http://archive.ubuntu.com maverick-security/multiverse Sources
Ign http://archive.ubuntu.com maverick-security/main i386 Packages
Ign http://archive.ubuntu.com maverick-security/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-security/universe i386 Packages
Ign http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Err http://archive.ubuntu.com maverick/main Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick/restricted Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick/universe Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick/multiverse Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick/main i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick/restricted i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick/universe i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/main Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/restricted Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/universe Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/multiverse Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/main Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/restricted Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/universe Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/multiverse Sources
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/main i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.202 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

As you can see, I have the Maverick distribution.

Via Google, I have found several solutions that I have tried. None of them have worked so far. Here they are: 
[LIST]
[*] Removing "independent" from the sources.list (was not present)
[*] Replacing sources.list (did not work)
[*] Changing download server (failed to download server)
[*] Changing apt.conf to remove proxies(does not exist)
[*] Removing unused repos (did nothing)
[*] Upgraded the apt-get manager (did nothing)
[/LIST]

Here is my sources.list, if it helps any.

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
 
deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner
 
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main
 
deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-security multiverse


```

Is there anything I can do?

---

### Post by Warren Hill on 2013-01-30
Ubuntu 10.10 is Maverick is no longer supported in any way.  The repositories are not there any more.

The repositories still exist but have been moved and are no longer being updated. 

If you want to continue using an outdated release then edit /etc/apt/sources.list and change archive.ubuntu.com to old-releases.ubuntu.com

I would not recommend this as there will be no more bug fixes, security patches etc

I strongly suggest you upgrade to 12.04 LTS.  This will be easiest as a clean install as the upgrade path would be via 11.04 and that is not supported any more so the upgrade is unlikely to work.

I suggest you try a live CD/DVD of both Xubuntu  and Ubuntu without installing as the desktop has changed significantly: Xubuntu is more like Ubuntu was in 10.04 and Ubuntu now uses Unity and this may be too slow on older hardware.  Once you have decided which you prefer install it.

Downloads are here:
Ubuntu -- [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Xubuntu -- [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

You can of course go with 12.10 but not being an LTS release you will need to upgrade sooner.

---

### Post by r42xer on 2013-01-30
Ah, great, that makes sense. I would upgrade, but my computer is a school computer.

---

