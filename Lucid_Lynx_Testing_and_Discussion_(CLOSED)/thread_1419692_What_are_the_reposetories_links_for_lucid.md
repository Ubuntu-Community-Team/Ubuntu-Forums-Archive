---
title: "What are the reposetories links for lucid?"
date: 2010-03-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-02
i have this:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/)

i need partenr reposetory and everything eles you can think of.

thanks in advance.

---

### Post by cariboo on 2010-03-02
You can enable the extra repositories in System->Administration->Software Sources, or System->Administration->Synaptic Package Manager->Settings->Repositories

---

### Post by aviramof on 2010-03-02
i know that but it's possible i deleted one i need that is why i asked for the links.

---

### Post by philinux on 2010-03-02
> **aviramof said:**
> i know that but it's possible i deleted one i need that is why i asked for the links.

Default install.
```

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release Candidate amd64 (20091020.3)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security multiverse

```

---

### Post by grandtoubab on 2010-03-02
[QUOTE=philinux;8905707]Default install.
/QUOTE]
Here is mine Upgraded from Karmic:
```
desktop:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ lucid main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid universe
deb http://archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates universe

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.ubuntu.com/ubuntu/ lucid-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-security universe

# deb http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu karmic main
# deb http://archive.canonical.com/ karmic partner
# deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
# deb http://fr.packages.medibuntu.org/ karmic free non-free
# deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
# deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu karmic main ## Cairo-Dock-PPA
# deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/
# deb http://deb.opera.com/opera-beta/ stable non-free

```

---

### Post by aviramof on 2010-03-02
thank you very much tell me please can i add all this 
karmic to lucid or not?

this is what i have now:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://il.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://il.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://il.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid universe
deb http://il.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://il.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://il.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://il.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://il.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://il.archive.ubuntu.com/ubuntu/ lucid-security universe
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://il.archive.ubuntu.com/ubuntu/ lucid-security multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-security multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted
deb http://archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid universe
deb http://archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates universe
deb http://archive.ubuntu.com/ubuntu/ lucid-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-security universe
```

thanks in advance.

---

### Post by Kevbert on 2010-03-03
For medibuntu see [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by ElSlunko on 2010-03-05
Does anyone have a slow Repo Refresh after enabling the google repo?

---

