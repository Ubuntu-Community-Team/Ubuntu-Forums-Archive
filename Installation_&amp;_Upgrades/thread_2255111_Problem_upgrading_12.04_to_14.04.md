---
title: "Problem upgrading 12.04 to 14.04"
date: 2014-12-02
forum: Installation &amp; Upgrades
---

### Post by michael238 on 2014-12-02
Many thanks for your help with this:

:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

 cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS"


# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise universe
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

## Jedit
# deb [http://switch.dl.sourceforge.net/project/jedit](http://switch.dl.sourceforge.net/project/jedit) / # disabled on upgrade to precise

##firefox dev
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe main multiverse restricted #Added by software-properties

---

### Post by gifford on 2014-12-02
I guess I am a little confused by your post...are you trying to upgrade to Ubuntu 14.04?
The cdrom indicates you have 11.10 in it. How are you trying to upgrade?

---

### Post by Enigma12 on 2014-12-02
First, be aware that I am still definitely a newbie to Linux, so you may choose to ignore my suggestions and wait for someone much more knowledgeable than me to offer advice. Since I have read too many posts here about problems from making a big jump in distros, I will avoid doing that. So far, incremental upgrades have not created any real problems for me. 

What I will suggest is A) backing up all data that needs to be saved, B) downloading a copy of 14.04 ISO, C) burning it onto a CD or DVD (whichever is needed) and D) using that media to reformat the hard drive or partition, then install 14.04, E) reinstall all desired programs from the software center, and F) lastly (if needed) putting back the data from the backups. 

My preference is to store most data (documents, videos, photos, etc.) on a separate hard drive or partition. That should, theoretically, keep it untouched by OS installations. So far, that has worked for me since MS-DOS days. I still do the backups for safety, though.

---

### Post by kansasnoob on 2014-12-02
> **michael238 said:**
> Many thanks for your help with this:

:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

 cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS"


# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise universe
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

## Jedit
# deb [http://switch.dl.sourceforge.net/project/jedit](http://switch.dl.sourceforge.net/project/jedit) / # disabled on upgrade to precise

##firefox dev
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main
[B]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) [COLOR="#FF0000"]lucid[/COLOR]-security main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) [COLOR="#FF0000"]oneiric[/COLOR] main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) [COLOR="#FF0000"]oneiric[/COLOR] universe main multiverse restricted #Added by software-properties[/B]

You still have some Lucid and Oneiric sources activated - see highlighted text above. So comment out those three lines with a # using gedit:

```
sudo gedit /etc/apt/sources.list
```

Then run:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Then check under the Updates tab in the Software Sources GUI and be sure that it's set to notify of new version for LTS versions only.

---

### Post by michael238 on 2014-12-04
That did it. Thank you.

---

