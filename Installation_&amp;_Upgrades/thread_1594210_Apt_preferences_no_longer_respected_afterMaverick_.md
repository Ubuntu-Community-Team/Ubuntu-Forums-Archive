---
title: "Apt preferences no longer respected afterMaverick upgrade"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Akdor 1154 on 2010-10-12
Hi,

Upgraded to 10.10 with update-manager last night, apart from an xorg.conf.d location change and a custom xfce applet that needed recompiling all went smoothly... until I tried another dist-upgrade.

Previous I had debian lenny and squeeze available in apt - I know this is dumb but a sync program I use requires binary versions to be identical (unison), and I sync with a debian squeeze server.
```
deb http://mirror.aarnet.edu.au/debian/ squeeze main contrib non-free 
deb-src http://mirror.aarnet.edu.au/debian/ squeeze main contrib non-free

deb http://mirror.aarnet.edu.au/debian/ lenny main contrib non-free
deb-src http://mirror.aarnet.edu.au/debian/ lenny main contrib non-free

deb http://volatile.debian.org/debian-volatile/ lenny/volatile main contrib non-free
deb-src http://mirror.aarnet.edu.au/debian-security/ lenny/updates main contrib non-free
```
I got around this by pinning stable and testing to a negative value in /etc/apt/preferences.d/debian:
```
Package: *
Pin: release a=stable
Pin-Priority: -90

Package: *
Pin: release a=testing
Pin-Priority: -85

Package: unison
Pin: release a=testing
Pin-Priority: 1100
```

This worked marvellously in lucid, but maverick apt no longer respects these for some reason:
```
$ apt-cache policy

100 /var/lib/dpkg/status
     release a=now
 [b]
 500 http://volatile.debian.org/debian-volatile/ lenny/volatile/non-free amd64 Packages
     origin volatile.debian.org
 500 http://volatile.debian.org/debian-volatile/ lenny/volatile/contrib amd64 Packages
     origin volatile.debian.org
 500 http://volatile.debian.org/debian-volatile/ lenny/volatile/main amd64 Packages
     origin volatile.debian.org
 500 http://mirror.aarnet.edu.au/debian/ lenny/non-free amd64 Packages
     origin mirror.aarnet.edu.au
 500 http://mirror.aarnet.edu.au/debian/ lenny/contrib amd64 Packages
     origin mirror.aarnet.edu.au
 500 http://mirror.aarnet.edu.au/debian/ lenny/main amd64 Packages
     origin mirror.aarnet.edu.au
 500 http://mirror.aarnet.edu.au/debian/ squeeze/non-free amd64 Packages
     origin mirror.aarnet.edu.au
 500 http://mirror.aarnet.edu.au/debian/ squeeze/contrib amd64 Packages
     origin mirror.aarnet.edu.au
 500 http://mirror.aarnet.edu.au/debian/ squeeze/main amd64 Packages
     origin mirror.aarnet.edu.au[/b]
     
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-backports/multiverse amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-backports,n=maverick,l=Ubuntu,c=multiverse
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-backports/universe amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-backports,n=maverick,l=Ubuntu,c=universe
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-backports/restricted amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-backports,n=maverick,l=Ubuntu,c=restricted
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-backports/main amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-backports,n=maverick,l=Ubuntu,c=main
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-proposed/multiverse amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-proposed,n=maverick,l=Ubuntu,c=multiverse
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-proposed/universe amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-proposed,n=maverick,l=Ubuntu,c=universe
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-proposed/restricted amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-proposed,n=maverick,l=Ubuntu,c=restricted
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-proposed/main amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-proposed,n=maverick,l=Ubuntu,c=main
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-security/multiverse amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-security,n=maverick,l=Ubuntu,c=multiverse
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-security/universe amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-security,n=maverick,l=Ubuntu,c=universe
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-security/restricted amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-security,n=maverick,l=Ubuntu,c=restricted
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-security/main amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-security,n=maverick,l=Ubuntu,c=main
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-updates/multiverse amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-updates,n=maverick,l=Ubuntu,c=multiverse
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-updates/universe amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-updates,n=maverick,l=Ubuntu,c=universe
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-updates/restricted amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-updates,n=maverick,l=Ubuntu,c=restricted
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick-updates/main amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick-updates,n=maverick,l=Ubuntu,c=main
     origin mirror.aarnet.edu.au
 500 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick/restricted Translation-en_AU
 500 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick/multiverse Translation-en_AU
 500 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick/main Translation-en_AU
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick/multiverse amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick,n=maverick,l=Ubuntu,c=multiverse
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick/universe amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick,n=maverick,l=Ubuntu,c=universe
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick/restricted amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick,n=maverick,l=Ubuntu,c=restricted
     origin mirror.aarnet.edu.au
 990 http://mirror.aarnet.edu.au/pub/ubuntu/archive/ maverick/main amd64 Packages
     release v=10.10,o=Ubuntu,a=maverick,n=maverick,l=Ubuntu,c=main
     origin mirror.aarnet.edu.au
     
      500 http://xpra.devloop.org.uk/ squeeze/main amd64 Packages
     origin xpra.devloop.org.uk
 990 http://ppa.launchpad.net/ricotz/ppa/ubuntu/ maverick/main amd64 Packages
     release v=10.10,o=LP-PPA-ricotz,a=maverick,n=maverick,l=Backports PPA,c=main
     origin ppa.launchpad.net
 990 http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main amd64 Packages
     release v=10.10,o=LP-PPA-pidgin-developers,a=maverick,n=maverick,l=PPA by Pidgin Developers,c=main
     origin ppa.launchpad.net
 -90 http://deb.opera.com/opera-beta/ stable/non-free amd64 Packages
     release o=Opera Software ASA,a=stable,n=lenny,l=The Opera web browser,c=non-free
     origin deb.opera.com
 -90 http://deb.opera.com/opera/ stable/non-free amd64 Packages
     release o=Opera Software ASA,a=stable,n=lenny,l=The Opera web browser,c=non-free
     origin deb.opera.com
 500 http://ppa.launchpad.net/maverick-bleed/ppa/ubuntu/ maverick/multiverse amd64 Packages
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/maverick-bleed/ppa/ubuntu/ maverick/universe amd64 Packages
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/maverick-bleed/ppa/ubuntu/ maverick/restricted amd64 Packages
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/maverick-bleed/ppa/ubuntu/ maverick/main amd64 Packages
     origin ppa.launchpad.net
 990 http://ppa.launchpad.net/lazka/ppa/ubuntu/ maverick/main amd64 Packages
     release v=10.10,o=LP-PPA-lazka,a=maverick,n=maverick,l=quodlibet-stable,c=main
     origin ppa.launchpad.net
     
 990 http://ppa.launchpad.net/anyremote/ppa/ubuntu/ maverick/main amd64 Packages
     release v=10.10,o=LP-PPA-anyremote,a=maverick,n=maverick,l=PPA for anyremote,c=main
     origin ppa.launchpad.net
 990 http://extras.ubuntu.com/ubuntu/ maverick/main amd64 Packages
     release v=10.10,o=LP-PPA-app-review-board,a=maverick,n=maverick,l=Application Review Board PPA,c=main
     origin extras.ubuntu.com
 990 http://archive.canonical.com/ubuntu/ maverick/partner amd64 Packages
     release v=10.10,o=Canonical,a=maverick,n=maverick,l=Partner archive,c=partner
     origin archive.canonical.com
Pinned packages:
     unison -> (not found)


```

So... any idea what's going on?

Thanks,
Jarad

---

### Post by Akdor 1154 on 2010-10-12
bump :(

---

