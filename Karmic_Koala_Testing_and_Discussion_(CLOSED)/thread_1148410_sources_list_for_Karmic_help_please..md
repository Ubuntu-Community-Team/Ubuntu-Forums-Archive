---
title: "sources list for Karmic help please."
date: 2009-05-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by berthiggins on 2009-05-04
Hi I seem to have borked my sources list on the manual upgrade.
I know that I should have backed it up:(
Can some one please post theirs so that I can compare and fix?

---

### Post by super.rad on 2009-05-04
Heres mine:
```
deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu jaunty main
```
Bottom 2 are the Gnome Colors/Shiki Colors PPA

---

### Post by rudenko_ruslan on 2009-05-04
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ru.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ru.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
```
And that's mine.

---

### Post by taavikko on 2009-05-04
minimal is beautiful...
```
deb http://archive.ubuntu.com/ubuntu/ karmic main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main universe multiverse restricted

deb http://archive.ubuntu.com/ubuntu/ karmic-updates main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main universe multiverse restricted

# deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main universe multiverse restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main universe multiverse restricted
```

---

### Post by berthiggins on 2009-05-04
Thanks guys I will try and report back:P

---

### Post by berthiggins on 2009-05-04
Thanks guys those work for me I have gone for taavikko's minimal one. ( I like minimal too )

---

### Post by alphacrucis2 on 2009-05-05
I seem to have a similar problem. Tried replacing the sources.list as above but i still get:

```
user@desktop:~$ gksu /usr/bin/software-properties-gtk
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 83, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 521, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)  
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```

Any suggestions?

---

### Post by rudenko_ruslan on 2009-05-05
> **alphacrucis2 said:**
> I seem to have a similar problem. Tried replacing the sources.list as above but i still get:

```
user@desktop:~$ gksu /usr/bin/software-properties-gtk
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 83, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 521, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)  
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```

Any suggestions?
I think you must see this thread - [http://ubuntuforums.org/showthread.php?t=1142943](http://ubuntuforums.org/showthread.php?t=1142943)

---

### Post by caryb on 2009-05-05
Unless your a developer or need the source code I hash out the src entries to save extra downloads etc. It also speeds up the update-ing of the package lists.


Cary

---

### Post by alphacrucis2 on 2009-05-05
> **rudenko_ruslan said:**
> I think you must see this thread - [http://ubuntuforums.org/showthread.php?t=1142943](http://ubuntuforums.org/showthread.php?t=1142943)


Thank you. I edited the ubuntu.info file as suggested and all good. Is this one of the traps for young players entering into the world of pre-alpha? No doubt more interesting stuff to come, A good way to learn I suspect:lolflag:

---

