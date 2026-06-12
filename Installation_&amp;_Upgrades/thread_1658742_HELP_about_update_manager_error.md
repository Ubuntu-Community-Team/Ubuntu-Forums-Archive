---
title: "HELP about update manager error"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by fakhrul12 on 2011-01-03
I`m totally new to ubuntu and linux environment so a help is very appreciated.
An error occured with my update manager and it was showing something like this one
> 
**Could not initialize the package information**

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 60 in source list /etc/apt/sources.list'


so anyone who can help me with this?
thanks in advance

---

### Post by Elfy on 2011-01-03
You have errors in the source list - at least line 60.

All lines in source lists should start with #, deb or deb-src - nothing else.

Open the file for editing as root from a terminal

```
gksudo gedit /etc/apt/sources.list
```

Find the error and correct it, then save and run an update from the terminal

```
sudo apt-get update
```

If you are not sure - paste the sources list here.

---

### Post by fakhrul12 on 2011-01-03
hurm...well it showed up something like this one
> 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free
“deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free”which makes me really clueless

---

### Post by drs305 on 2011-01-03
> **fakhrul12 said:**
> hurm...well it showed up something like this one
which makes me really clueless

> 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free
[COLOR="Red"]&#8220;deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free&#8221;[/COLOR] 
It's a duplicate line, so just remove it. The " symbols at the start and end of the line are what is causing the error message. (It's the last line of the file.)

Open for editing with:
```
gksu gedit +60 /etc/apt/sources.list
```

---

### Post by fakhrul12 on 2011-01-04
oh! many thanks all :)
the problem was solved

and i have some questions
what is 'sudo'  and 'gksu' and so forth?

---

### Post by drs305 on 2011-01-04
Here's a good explanation from the Ubuntu community documentation:
[RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by fakhrul12 on 2011-01-04
oh thanks for the info :)
and thanks for everything

---

