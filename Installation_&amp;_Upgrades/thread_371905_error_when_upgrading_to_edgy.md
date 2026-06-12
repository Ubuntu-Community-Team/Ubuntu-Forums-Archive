---
title: "error when upgrading to edgy"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by sohaibma on 2007-02-27
when i try to upgrade to edgy using gksu "update-manager -c", it goes fine until modifying the software channels. then it show the following error:

**Error authenticating some packages**

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
avahi-daemon
avahi-utils
bind9-host
dbus
dbus-1-utils
dnsutils
ekiga
evince
firefox
firefox-gnome-support
gdm
gnupg
gtk2-engines-pixbuf
imagemagick
info
kdelibs-data
kdelibs4c2a
libavahi-client3
libavahi-common-data
libavahi-common3
libavahi-core4
libavahi-glib1
libavahi-qt3-1
libbind9-0
libdbus-1-3
libdns21
libgeoip1
libgsf-1-114
libgsf-1-common
libgsf-1-dev
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-common
libgtk2.0-dev
libgtop2-7
libgtop2-common
libisc11
libisccc0
libisccfg1
libkrb53
liblwres9
libmagick9
libmono-cairo1.0-cil
libmono-corlib1.0-cil
libmono-data-tds1.0-cil
libmono-security1.0-cil
libmono-sharpzip0.84-cil
libmono-sqlite1.0-cil
libmono-system-data1.0-cil
libmono-system-web1.0-cil
libmono-system1.0-cil
libmono0
libmono1.0-cil
libnspr4
libnss3
libpng12-0
libpng12-dev
libpoppler1
libpoppler1-glib
libpq4
librpm4
libruby1.8
libsmbclient
libsoup2.2-8
libvlc0
libxine-main1
libxine1
linux-386
linux-image-2.6.17-11-386
linux-image-386
linux-libc-dev
linux-restricted-modules-2.6.17-11-386
linux-restricted-modules-386
linux-restricted-modules-common
mono-common
mono-gac
mono-jit
mono-runtime
poppler-utils
rpm
ruby1.8
samba-common
screen
slocate
smbclient
tar
vlc
vlc-nox
vlc-plugin-alsa
w3m
wxvlc
xserver-xorg-core
xserver-xorg-dev



please help me. how do i fix this error?

---

### Post by zvacet on 2007-02-27
In your source list replace Dapper with Edgy.For example
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) dapper main to 

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) edgy main
Do that with all source list.

---

### Post by UltraSonicSite on 2007-03-01
I get the same thing:


> It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

fuse-utils
libfuse2
libntfs-3g0
ntfs-3g


my Sources list:

[quote="sources.list"]

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main
deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main
[/quote]

Even with everything Edgy, the only way to fix it is through apt-get "Mark All Upgrades" and simply download and install.

---

### Post by Thug14 on 2007-09-01
i am facing the exact same problem;my sources.list has all edgy-stuff only

I do have the Ubuntu edgy alternate cd

sum1 plzz help
 :helpflag:

---

