---
title: "[SOLVED] Add/Remove Application Problem"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by vitt1984 on 2008-01-04
Hi everybody!

The Add/Remove Application tool isn't working anymore, after my unistalling Wine.

If i let him run its update check it tells me:

"Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)"

and ok, this could be due to some repositories currently not online. But THEN, if i try to install any applications, it tells me this:

"It's not possible to install (application) on this kind of computer (i386"

which is absurd, because it had been running perfectly with every application until now.

Any ideas ?

Just in case it's needed, here's what comes out of cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0

Edit: i forgot to mention, that the synaptic packet manager, as well as every other application (included a reinstalled Wine), is running fine

---

### Post by Pumalite on 2008-01-04
Post:
uname -a

---

### Post by vitt1984 on 2008-01-04
> **Pumalite said:**
> Post:
uname -a

Linux vittorio-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

oh and by the way, i'm running ubuntu 7.10 on a Inspiron 6400 Dell Laptop

---

### Post by Pumalite on 2008-01-04
These packages are not for your kernel. How did they get in there?
"Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release) Unable to find expected entry web/binary-i386/Packages in Meta-index file (malformed Release file?)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...pdates/Release](http://archive.ubuntu.com/ubuntu/dis...pdates/Release) Unable to find expected entry web/binary-i386/Packages in Meta-index file (malformed Release file?)
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dis...curity/Release](http://archive.ubuntu.com/ubuntu/dis...curity/Release) Unable to find expected entry web/binary-i386/Packages in Meta-index file (malformed Release file?)"

---

### Post by vitt1984 on 2008-01-04
> **Pumalite said:**
> These packages are not for your kernel. How did they get in there?


no idea - i just know that the update always ran fine until the wine uninstalling...

do you think that explains the whole thing ?
should i just comment those three out of the sources.list ?

---

### Post by zvacet on 2008-01-04
```
gsudo gedit /etc/apt/sources.list
```

and change 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted web

to 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted

Save and close.

```
sudo apt-get update
```

---

### Post by Pumalite on 2008-01-04
Yes

---

### Post by vitt1984 on 2008-01-05
Thanks to both, especially for the fast replies! 

Your idea worked great, and now everything's back to work... a mod should change the thread title as [SOLVED].

---

### Post by Partyboi2 on 2008-01-05
> **vitt1984 said:**
> Thanks to both, especially for the fast replies! 

Your idea worked great, and now everything's back to work... a mod should change the thread title as [SOLVED].
You can mark this as solved under "thread tools" at the top of this page. Mod's don't do that. Maybe if it was a premium subscription they might :lolflag:

---

