---
title: "W: Duplicate sources.list entry"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by manolomanolo on 2010-04-20
hi to all.
How to solve those?

```
W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_jonoomph_openshot-edge_ubuntu_dists_karmic_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: Duplicate sources.list entry http://linux.dropbox.com karmic/main Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_karmic_main_binary-i386_Packages)
```

That's my sources.list
> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

#OPENSHOT
deb [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu) karmic main

#GETDEB
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps

#KDENLIVE sunab
deb [http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu) karmic main

#COMPIZ FUSION (UNSUPPORTED)
deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) karmic main

#AWN DOCK BAR
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) karmic main

#WINE
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main


---

### Post by plucky on 2010-04-20
Post output of ```
ls -l /etc/apt/sources.list.d/
```

The duplicate sources lists are probably in there.

Good Luck

---

### Post by manolomanolo on 2010-04-20
Thanks for your reply.
You're probably right.

>  ls -l /etc/apt/sources.list.d/
total 148
-rw-r--r-- 1 root root  60 2010-04-20 14:12 ailurus.list
-rw-r--r-- 1 root root  60 2010-04-20 14:12 ailurus.list.save
-rw-r--r-- 1 root root 465 2010-04-20 14:12 akirad.list
-rw-r--r-- 1 root root 463 2010-04-20 14:12 akirad.list.save
-rw-r--r-- 1 root root  92 2010-04-20 14:12 breathe-dev-ppa.list
-rw-r--r-- 1 root root  92 2010-04-20 14:12 breathe-dev-ppa.list.save
-rw-r--r-- 1 root root  72 2010-04-20 14:12 c-korn-vlc.list
-rw-r--r-- 1 root root  72 2010-04-20 14:12 c-korn-vlc.list.save
-rw-r--r-- 1 root root  48 2010-04-20 14:12 dropbox.list
-rw-r--r-- 1 root root  48 2010-04-20 14:12 dropbox.list.save
-rw-r--r-- 1 root root  73 2010-04-20 14:12 dropbox-official-source.list
-rw-r--r-- 1 root root  73 2010-04-20 14:12 dropbox-official-source.list.save
-rw-r--r-- 1 root root  70 2010-04-20 14:12 emesene-ppa.list
-rw-r--r-- 1 root root  70 2010-04-20 14:12 emesene-ppa.list.save
-rw-r--r-- 1 root root  48 2010-04-20 14:12 google-chrome.list
-rw-r--r-- 1 root root  48 2010-04-20 14:12 google-chrome.list.save
-rw-r--r-- 1 root root  71 2010-04-20 14:12 jonoomph-openshot-edge-karmic.list
-rw-r--r-- 1 root root  71 2010-04-20 14:12 jonoomph-openshot-edge-karmic.list.save
-rw-r--r-- 1 root root 273 2010-04-20 14:12 medibuntu.list
-rw-r--r-- 1 root root 273 2010-04-20 14:12 medibuntu.list.save
-rw-r--r-- 1 root root 116 2010-04-20 14:12 mozillateam-firefox-stable.list
-rw-r--r-- 1 root root 116 2010-04-20 14:12 mozillateam-firefox-stable.list.save
-rw-r--r-- 1 root root  68 2010-04-20 14:12 openoffice-pkgs-ppa-karmic.list
-rw-r--r-- 1 root root  68 2010-04-20 14:12 openoffice-pkgs-ppa-karmic.list.save
-rw-r--r-- 1 root root  95 2010-04-20 14:12 openshotdevelopers-ppa.list
-rw-r--r-- 1 root root  95 2010-04-20 14:12 openshotdevelopers-ppa.list.save
-rw-r--r-- 1 root root  69 2010-04-20 14:12 shutter.list
-rw-r--r-- 1 root root  69 2010-04-20 14:12 shutter.list.save
-rw-r--r-- 1 root root  65 2010-04-20 14:12 skype.list
-rw-r--r-- 1 root root  65 2010-04-20 14:12 skype.list.save
-rw-r--r-- 1 root root  90 2010-04-20 14:12 ubuntu-tweak-stable.list
-rw-r--r-- 1 root root  90 2010-04-20 14:12 ubuntu-tweak-stable.list.save
-rw-r--r-- 1 root root  86 2010-04-20 14:12 ubuntu-wine-ppa.list
-rw-r--r-- 1 root root  86 2010-04-20 14:12 ubuntu-wine-ppa.list.save
-rw-r--r-- 1 root root  96 2010-04-20 14:12 virtualbox-offical-source.list
-rw-r--r-- 1 root root  96 2010-04-20 14:12 virtualbox-offical-source.list.save
-rw-r--r-- 1 root root  65 2010-04-20 14:12 yogarine-eclipse-karmic.list


So, where should I prefer removing duplicates?
Thanks

---

### Post by plucky on 2010-04-20
**System > Administration > Software Sources** and un-tick one of the ones that are causing the failures.

i.e

ppa.launchpad.net_jonoomph_openshot-edge_ubuntu_dists
ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_karmic
linux.dropbox.com_ubuntu_dists_karmic_

Good Luck

---

### Post by manolomanolo on 2010-04-20
Now i get this error message but I think it is temporary
> Fetched 3,654B in 2min 1s (30B/s)                                                                                                                           
Reading package lists... Done
W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_GB.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.medibuntu.org http:

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_GB.bz2](http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.medibuntu.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

Now, in my case, why should I prefer removing duplicate soruces from sources.list and not from sources.list.d ?

---

