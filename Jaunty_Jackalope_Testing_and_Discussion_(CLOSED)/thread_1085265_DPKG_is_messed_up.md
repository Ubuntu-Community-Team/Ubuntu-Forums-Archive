---
title: "DPKG is messed up"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Dj Melik on 2009-03-02
I tried sudo dpkg --configure -a, but it still won't fix it. How can I fix it, here it is.

```
melik@matrix:~$ sudo dpkg --configure -a
[sudo] password for melik: 
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on python-gnomecanvas; however:
  Package python-gnomecanvas is not configured yet.
 python-gnome2 depends on python2.5-gnomecanvas; however:
  Package python2.5-gnomecanvas is not installed.
  Package python-gnomecanvas which provides python2.5-gnomecanvas is not configured yet.
 python-gnome2 depends on python2.6-gnomecanvas; however:
  Package python2.6-gnomecanvas is not installed.
  Package python-gnomecanvas which provides python2.6-gnomecanvas is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
Setting up libedataserver1.2-11 (2.25.92-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libedataserver1.2-11 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up console-setup (1.28ubuntu6) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing console-setup (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on libedataserver1.2-11 (>= 2.25.91); however:
  Package libedataserver1.2-11 is not configured yet.
 deskbar-applet depends on python-gnome2 (>= 2.12.4-1); however:
  Package python-gnome2 is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
Setting up python-problem-report (0.141) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-problem-report (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libcamel1.2-14:
 libcamel1.2-14 depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
dpkg: error processing libcamel1.2-14 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebackend1.2-0:
 libebackend1.2-0 depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
dpkg: error processing libebackend1.2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libebackend1.2-0 (>= 2.25.92); however:
  Package libebackend1.2-0 is not configured yet.
 libedata-book1.2-2 depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libebackend1.2-0 (>= 2.25.92); however:
  Package libebackend1.2-0 is not configured yet.
 libedata-cal1.2-6 depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-about:
 gnome-about depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
dpkg: error processing gnome-about (--configure):
 dependency problems - leaving unconfigured
Setting up python-gconf (2.25.90-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gconf (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libexchange-storage1.2-3:
 libexchange-storage1.2-3 depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
dpkg: error processing libexchange-storage1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libegroupwise1.2-13:
 libegroupwise1.2-13 depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
dpkg: error processing libegroupwise1.2-13 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libedataserver1.2-11 (>= 2.25.91); however:
  Package libedataserver1.2-11 is not configured yet.
 gnome-panel depends on libedataserverui1.2-8 (>= 2.25.91); however:
  Package libedataserverui1.2-8 is not configured yet.
 gnome-panel depends on gnome-about (>= 2.10.0-1); however:
  Package gnome-about is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-7:
 libecal1.2-7 depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
dpkg: error processing libecal1.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-9:
 libebook1.2-9 depends on libcamel1.2-14 (>= 2.25.92); however:
  Package libcamel1.2-14 is not configured yet.
 libebook1.2-9 depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
dpkg: error processing libebook1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libcamel1.2-14 (>= 2.25.92); however:
  Package libcamel1.2-14 is not configured yet.
 evolution-data-server depends on libebackend1.2-0 (>= 2.25.92); however:
  Package libebackend1.2-0 is not configured yet.
 evolution-data-server depends on libebook1.2-9 (>= 2.25.92); however:
  Package libebook1.2-9 is not configured yet.
 evolution-data-server depends on libecal1.2-7 (>= 2.25.92); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libedata-book1.2-2 (>= 2.25.92); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-6 (>= 2.25.92); however:
  Package libedata-cal1.2-6 is not configured yet.
 evolution-data-server depends on libedataserver1.2-11 (>= 2.25.92); however:
  Package libedataserver1.2-11 is not configured yet.
 evolution-data-server depends on libegroupwise1.2-13 (>= 2.25.92); however:
  Package libegroupwise1.2-13 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet:
 indicator-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing indicator-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-gnome2
 libedataserver1.2-11
 console-setup
 libedataserverui1.2-8
 deskbar-applet
 python-problem-report
 libcamel1.2-14
 libebackend1.2-0
 libedata-book1.2-2
 libedata-cal1.2-6
 gnome-about
 python-gconf
 libexchange-storage1.2-3
 libegroupwise1.2-13
 gnome-panel
 python-apport
 libecal1.2-7
 libebook1.2-9
 evolution-data-server
 indicator-applet
 fast-user-switch-applet
 gnome-applets
 apport
 apport-gtk
melik@matrix:~$
```

---

### Post by oldos2er on 2009-03-02
Please post the output of
```
cat /etc/apt/sources.list
```

---

### Post by sandyd on 2009-03-02
try this maybe?

```

sudo apt-get -f install

```

---

### Post by Dj Melik on 2009-03-02
> **oldos2er said:**
> Please post the output of
```
cat /etc/apt/sources.list
```

```
melik@matrix:/usr/X11R6/bin$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090225.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
```

___

@ Carlee: I tried that, no luck :(

BTW, its not a Jaunty bug.. I accidently closed the update process midway.

---

### Post by oldos2er on 2009-03-02
Questions re Jaunty should be posted here: [http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

---

### Post by jpeddicord on 2009-03-02
Moved to Jaunty. And you may be a little stuck there, we're in the middle of the Python 2.5 -> 2.6 transition and dist-upgrading is a no-no. :P

[http://ubuntuforums.org/showthread.php?t=1082102](http://ubuntuforums.org/showthread.php?t=1082102)

---

