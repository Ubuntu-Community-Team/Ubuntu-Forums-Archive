---
title: "apt-get error with libappindicator0.1-cil and libgkeyfile1.0-cil"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by saggi.tar on 2011-05-27
Hello all,

I'm hoping you guys might be able to help me with something.

A few weeks ago I was getting ready to upgrade to natty. I ran:

```
# apt-get update && apt-get upgrade
```

Only to notice that a couple of packages were playing up. The specific error message was along the lines of:

```
(...)
Errors were encountered while processing:
 libappindicator0.1-cil
 libgkeyfile1.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So I set out to fix it; I tried 
- # apt-get install -f
- # dpkg --configure -a
- # apt-get purge libappindicator0.1-cil libgkeyfile1.0-cil (followed by a reinstall)
- adding 'deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) maverick main universe' to /etc/apt/sources.list (and retrying the above)

(I ran apt-get update after each of these obviously, which seemed to exit fine).

Eventually I got so fed up that I ran:

```
#apt-get build-dep libappindicator0.1-cil libgkeyfile1.0-cil
```

So as to pull in all of the dependencies (in case I didn't already have them). Now it's even worse! #apt-get upgrade gives:

```
Errors were encountered while processing:
 libnunit2.4-cil
 libnunit-cil-dev
 libmono-cil-dev
 mono-devel
 cli-common-dev
 libappindicator0.1-cil
 libgkeyfile1.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So I decided to ask you guys for help because I am out of my depth!

I'm running on Maverick Ubuntu.

Any help would be much, much appreciated!

p.s. Many support request posts like this are eventually asked for sources.list. So to pre-empt:

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main rest$
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

deb http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick main universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiv$
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe mu$

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-security multiverse

deb http://repository.spotify.com stable non-free # Spotify
deb http://linux.dropbox.com/ubuntu maverick main # Dropbox

```

---

### Post by saggi.tar on 2011-05-29
Any help anyone? I'd really appreciate it.

---

