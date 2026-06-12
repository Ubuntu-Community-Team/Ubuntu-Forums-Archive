---
title: "Source not found"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2010-08-20
When I update my software I am getting the following error message:

> Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

The strange thing is that in the sources.list this line in commented out. 

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse universe main

# deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main
# deb-src http://ppa.launchpad.net/googlegadgets/ubuntu intrepid main

## handwriting font
deb http://ppa.launchpad.net/andrewsomething/ubuntu lucid main
deb-src http://ppa.launchpad.net/andrewsomething/ubuntu lucid main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse universe main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security multiverse universe main
deb http://packages.medibuntu.org/ lucid non-free free # medibuntu
# deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu karmic main
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
deb http://www.le-web.org/repository stable main # disabled on upgrade to lucid
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu intrepid/
deb http://www.avenard.org/files/ubuntu-repos lucid release

deb http://ppa.launchpad.net/shutter/ppa/ubuntu lucid main
#openbox https://launchpad.net/~k-belding/+archive
# deb http://ppa.launchpad.net/k-belding/ubuntu karmic main
# deb-src http://ppa.launchpad.net/k-belding/ubuntu karmic main
# deb http://ppa.launchpad.net/arzajac/ppa/ubuntu lucid main # disabled on upgrade to lucid

# PPA for Gert Kulyk (to fix system sound problem)
# deb http://ppa.launchpad.net/gkulyk/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/gkulyk/ubuntu karmic main


# Tor
# deb http://mirror.noreply.org/pub/tor jaunty main
# deb-src http://mirror.noreply.org/pub/tor jaunty main


#Congruity and concordance
deb http://ppa.launchpad.net/mathieu-tl/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/mathieu-tl/ppa/ubuntu intrepid main # disabled on upgrade to lucid

## deb http://ppa.launchpad.net/c-korn/vlc/ubuntu lucid main # disabled on upgrade to lucid


# deb http://www.remastersys.klikit-linux.com/repository remastersys/ # disabled on upgrade to karmic


# Pidgin

deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main

#Firefox



# deb http://ppa.launchpad.net/nickel62metal/ubuntu karmic main
# deb http://blognux.free.fr/ubuntu hardy main # disabled on upgrade to karmic
# deb-src http://blognux.free.fr/ubuntu hardy main
# deb http://ppa.launchpad.net/nickel62metal/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/nickel62metal/ppa/ubuntu karmic main

#Nvidia drivers
# deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu lucid main # disabled on upgrade to lucid


# deb http://deb.torproject.org/torproject.org lucid main # disabled on upgrade to lucid
# deb-src http://deb.torproject.org/torproject.org lucid main # disabled on upgrade to lucid
deb http://ppa.launchpad.net/pj-assis/ppa/ubuntu lucid main #Guvcview repo
deb-src http://ppa.launchpad.net/pj-assis/ppa/ubuntu lucid main #Guvcvew repo

# deb http://snapshots.ekiga.net/snapshots/ubuntu/ karmic main

# deb http://getswiftfox.com/builds/debian unstable non-free # disabled on upgrade to lucid

# deb http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu intrepid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu intrepid main # disabled on upgrade to lucid
# deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/ # disabled on upgrade to lucid
deb http://ppa.launchpad.net/amsn-daily/ppa/ubuntu lucid main
deb http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
```

---

### Post by oldos2er on 2010-08-20
Is there something in /etc/apt/sources.list.d for c-korn/vlc ?

---

### Post by Robbyx on 2010-08-20
> **oldos2er said:**
> Is there something in /etc/apt/sources.list.d for c-korn/vlc ?

Yes. This was there:


/etc/apt/sources.list.d/c-korn-vlc-lucid.list


it contains:

deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid main

not knowing what I am doing I had a browsed to that web site and found something to do with lucid at 

[http://ppa.launchpad.net/c-korn/ubuntu/dists/lucid/universe/debian-installer/](http://ppa.launchpad.net/c-korn/ubuntu/dists/lucid/universe/debian-installer/)

I do not know if what I have found relates to vlc or how I should adjust the url.



Robin

---

### Post by Robbyx on 2010-08-26
For the record I have just deleted /etc/apt/sources.list.d/c-korn-vlc-lucid.list and the error message has gone away.

---

