---
title: "Update Manager error, just since yesterday"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by ScottinSoCal on 2010-06-04
9.10 upgraded to 10.04 several weeks ago. No issues on multiple updates until yesterday.

Yesterday morning, I got notification that there was an update, but got an error that it couldn't connect when I told it to go ahead. I tried it again last night, after work, and it connected but then gave me two errors. First it said I have duplicate repository entries. Then it gave me a list of "unauthenticated" updates it wanted to install. I hit cancel.

Is this an issue with the repository, or an issue with my installation of Ubuntu? Anyone else seen this in the last couple of days?

---

### Post by wojox on 2010-06-04
Post your sources.list up here please.

```
/etc/apt/sources.list
```

---

### Post by llawwehttam on 2010-06-04
> **wojox said:**
> Post your sources.list up here please.

```
/etc/apt/sources.list
```

knowledge base mate:

```
cat /etc/apt/sources.list
```

---

### Post by ScottinSoCal on 2010-06-04
Thanks.

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main # disabled on upgrade to lucid
# deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main # disabled on upgrade to lucid

```

---

### Post by llawwehttam on 2010-06-04
so you started with karmic, installed some jaunty backports and then upgraded to lucid?

That file looks fine to me but I'm no expert with repos.

---

### Post by ScottinSoCal on 2010-06-04
> **llawwehttam said:**
> so you started with karmic, installed some jaunty backports and then upgraded to lucid?

I started with 9.10 on this laptop, then upgraded to 10.04. If that's karmic and lucid, then yes. I never knowingly installed backports. The only thing I installed was the restricted stuff, to get MP3 and all that.

I have some knowledge of *nix OS, but I'm miles away from being any kind of guru.

---

### Post by wojox on 2010-06-04
Go into System > Admin > Software Sources and disable backports then. See what happens.

```
sudo apt-get update; sudo apt-get upgrade
```

---

