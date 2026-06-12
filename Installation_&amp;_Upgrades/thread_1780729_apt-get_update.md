---
title: "apt-get update"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by cstone1983 on 2011-06-12
I just installed a fresh copy of 9.04 and everything installed fine, However I cant do any apt-get update or upgrades 

root@yoda:/etc/apt# apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.30 80]


--------------------------
And this is my source.list which is default on install

#
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse





I can ping google and archive.ubuntu.com fine...not sure whats going on.
Any help would be appreciated

---

### Post by cstone1983 on 2011-06-12
The only thing I have changed is the /etc/network/interfaces to make my card static

auto eth0
iface eth0 inet static
        address 10.10.1.1
        network 10.10.1.0
        netmask 255.255.255.0
        broadcast 10.10.1.255
        gateway 10.10.1.10

---

### Post by coffeecat on 2011-06-12
> **cstone1983 said:**
> I just installed a fresh copy of 9.04

9.04 passed end of life last October and has been unsupported since then. This is why you cannot update. You need to install a supported version, 10.04 (which is Long Term Support), 10.10 or 11.04. Non-LTS releases are supported for only 18 months.

---

