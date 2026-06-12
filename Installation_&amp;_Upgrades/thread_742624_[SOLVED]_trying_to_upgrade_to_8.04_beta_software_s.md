---
title: "[SOLVED] trying to upgrade to 8.04 beta software source error."
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by Specter043 on 2008-04-01
when trying to upgrade to the beta, I get this error box, containing this text.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release) Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release) Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release) Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release) Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release) Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)

any ideas how to fix that?

---

### Post by billybisson on 2008-04-10
I have a similar problem too.

I recently installed Xubuntu 8.04 and was working fine, until I started to receive these errors when the update manager launched.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

I have not edited the /etc/sources.list, only clicked on the extra repositories under Software sources. Can someone please help me on this for I don't know whether I am missing out on important updates. 

Thanks

---

### Post by Partyboi2 on 2008-04-10
Can you post your sources.list? From a terminal
```
cat /etc/apt/sources.list
```

---

### Post by Gonzell on 2008-04-12
I've been running the Hardy beta for awhile now and I updated yesterday which happened to uninstall compizconfig-settings-manager which it will not let me install again. When I try, it says this:

> Package compizconfig-settings-manager is not available, but is referred to by another package.

Also, when I try to do an update, I get these errors:

> Failed to fetch [http://gulus.usherbrooke.ca/ubuntu/dists/hardy/Release](http://gulus.usherbrooke.ca/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gulus.usherbrooke.ca/ubuntu/dists/hardy-updates/Release](http://gulus.usherbrooke.ca/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gulus.usherbrooke.ca/ubuntu/dists/hardy-security/Release](http://gulus.usherbrooke.ca/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

It's very frustrating having compiz fusion without my custom settings, lol

---

### Post by Gonzell on 2008-04-12
Oh, and here is the result from cat /etc/apt/sources.list

> chesley@chezb-ubuntu-m:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy main restricted web
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates main restricted web
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy universe
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy universe
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates universe
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy multiverse
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy multiverse
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates multiverse
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security main restricted web
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security main restricted
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security universe
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security universe
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security multiverse
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security multiverse

#reacocard's avant-window-manager
# deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
# deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main

#kde4
# deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
# deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) gutsy main
# deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) gutsy main


---

### Post by Partyboi2 on 2008-04-12
remove the [COLOR=Red]web[/COLOR] word from your sources.list
```
gksudo gedit /etc/apt/sources.list
``````
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy main restricted **[COLOR=Red]web[/COLOR]**
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates main restricted **[COLOR=Red]web[/COLOR]**
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy universe
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy universe
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates universe
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy multiverse
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy multiverse
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates multiverse
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security main restricted **[COLOR=Red]web[/COLOR]**
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security main restricted
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security universe
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security universe
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security multiverse
deb-src [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) hardy-security multiverse

#reacocard's avant-window-manager
# deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
# deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main

#kde4
# deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
# deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) gutsy main
# deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) gutsy main
```Then 
```
sudo apt-get update
```

---

### Post by Gonzell on 2008-04-13
Wow...removing the "web" stuff actually worked.

I wonder how it got in there in the first place though...

---

### Post by Specter043 on 2008-04-14
Worked for me as well.  Thanks!

---

### Post by mkarnicki on 2008-04-29
Thanks, it worked for me also. And I also wonder how did it get there..:lolflag:

---

