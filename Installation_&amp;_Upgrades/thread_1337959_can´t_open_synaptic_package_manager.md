---
title: "can´t open synaptic package manager"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by The-Red-Baron on 2009-11-25
got a problem with my synaptic package manager... it doesn´t  open...could you pleaase help.. thanks.. appreciate it... below is the source list... thanks...

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by staf0048 on 2009-11-25
Hmmm...

Does it open when you type in the following into the terminal?

```

gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic

```

---

### Post by MelDJ on 2009-11-26
what happens if you run update manager/apt-get?

---

### Post by byStanderone on 2009-11-26
...try dpkg --configure -a

---

### Post by The-Red-Baron on 2009-11-26
> **staf0048 said:**
> Hmmm...

Does it open when you type in the following into the terminal?

```

gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic

```
__________________

hello again... here's what happens when i type the command in the terminal... it still could not open...

Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 588, in <module>
    buildIndex(dbdir, addons, progress)
  File "/usr/sbin/update-apt-xapian-index", line 280, in buildIndex
    cache = apt.Cache(memonly=True)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 52, in __init__
    self.open(progress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 65, in open
    self._cache = apt_pkg.GetCache(progress)
SystemError: E:Unable to parse package file /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_intrepid_universe_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.

---

### Post by The-Red-Baron on 2009-11-26
> **byStanderone said:**
> ...try dpkg --configure -a
_____________

helo.. it also doesn't work... dpkg: requested operation requires superuser privilege

thanks for trying to help... (=^_^=)

---

### Post by MelDJ on 2009-11-26
you should type sudo dpkg --configure -a

---

### Post by The-Red-Baron on 2009-11-26
> **MelDJ said:**
> what happens if you run update manager/apt-get?
__________

hello... here's what happens when i try to update manager... 

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_intrepid_universe_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.'

i tried to report it but i still get the same problem...

---

### Post by MelDJ on 2009-11-26
reporting the bug will take time as the dev will need to look at your report and find a way.

you could try: [http://ubuntuforums.org/archive/index.php/t-440883.html](http://ubuntuforums.org/archive/index.php/t-440883.html)

---

