---
title: "Cannot upgrade from 16.04"
date: 2018-05-10
forum: Installation &amp; Upgrades
---

### Post by robotsheepboy on 2018-05-10
Trying to upgrade from 16.04 but when I run "update-manager -d" it tells me I'm up to date. 
Terminal gives me the following:

```
$ update-manager -d/usr/bin/update-manager:28: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.  from gi.repository import Gtk
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Dbusmenu was imported without specifying a version first. Use gi.require_version('Dbusmenu', '0.4') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Unity was imported without specifying a version first. Use gi.require_version('Unity', '7.0') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity



```


so far I have done the following: 
ran

```
 sudo apt-get update --fix-missing; sudo dpkg --configure -a; sudo apt-get install -f; sudo apt-get update; sudo apt-get upgrade; sudo update-grub; sudo apt-get update; sudo apt-get upgrade; sudo update-grub; sudo apt autoremove; sudo apt-get clean; sudo apt-get autoclean;sudo apt-get update;
```

went in to my system setting -> software and updates -> other software    and removed all non default on the list
went in to my system setting -> software and updates -> authentithicaton   and restored defaults
went in to my system setting -> software and updates -> updates              and checked that I have it set to notify me to any new version
and finally went to  went in to my system setting -> software and updates -> ubuntu software    and checked all boxes and set "download from" to "other, select best server" which has given me a UK server (I am in the UK).

Have also tried restarting several times.   Any help would be greatly appreciated.

---

### Post by yancek on 2018-05-10
The Ubuntu documentation on upgrading from 16.04 to 18.04 at the link below.  I've found several sites such as the one at the second link below explaining how to do it.  Haven't done it myself so...?  At your own risk, backups needed.

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)

[https://itsfoss.com/upgrade-ubuntu-version/](https://itsfoss.com/upgrade-ubuntu-version/)

---

### Post by robotsheepboy on 2018-05-10
Hi, yeah it doesn't have to be to 18.04 necessarily, I just want to be able to upgrade at all, there's obviously some kind of error preventing that, any help would be much appreciated

---

### Post by robotsheepboy on 2018-05-11
I eventually fixed this by using 

```
$ sudo do-release-upgrade

```

which actually failed initially but had partially installed some of the necessary updates, so I then ran 

```
$ sudo apt-get update --fix-missing; sudo dpkg --configure -a; sudo apt-get install -f; sudo apt-get update; sudo apt-get upgrade;
```

which fixed the faiure, and then I finally repeated 

```
$ sudo do-release-upgrade

```

which then went through without a hitch. Upon restart I am running 18.04

---

