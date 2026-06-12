---
title: "Serious Dependency Issues."
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by OisinT on 2009-12-06
This is really starting to bog me down and I've tried everything to fix it.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up checkbox-gtk (0.8.6) ...
Traceback (most recent call last):
  File "/usr/share/checkbox/install/config", line 15, in <module>
    from debconf import Debconf, DebconfCommunicator
ImportError: No module named debconf
dpkg: error processing checkbox-gtk (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up dbus (1.2.16-2) ...
/sbin/runlevel: relocation error: /sbin/runlevel: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
update-rc.d: warning: /etc/init.d/dbus missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/sbin/runlevel: relocation error: /sbin/runlevel: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
start: relocation error: start: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-couchdb:
 evolution-couchdb depends on evolution (>= 2.28.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-couchdb (--configure):
 dependency problNo apport report written because the error message indicates its a followup error from a previous failure.
                                           No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     ems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.28.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.28.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gnome-session-bin; however:
  Package gnome-session-bin is not configured yet.
dpkg: error pNo apport report written because MaxReports is reached already
                                                                           rocessing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm-guest-session:
 gdm-guest-session depends on gdm (>= 2.27.90-0ubuntu2); however:
  Package gdm is not configured yet.
dpkg: error processing gdm-guest-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-session-bin (>= 2.28); however:
  Package gnome-session-bin is not configured yet.
 gnome-session depends on gnome-session-bin (<< 2.29); however:
  Package gnome-session-bin is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-session:
 indicator-session depends on gdm; however:
  Package gdm is not configured yet.
dpkg: error processing indicator-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet-session:
 indicator-applet-session depends on indicator-session; however:
  Package indicator-session is not configured yet.
dpkg: error processing indicator-applet-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on checkbox-gtk; however:
  Package checkbox-gtk is not configured yet.
 ubuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on indicator-applet-session; however:
  Package indicator-applet-session is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-indicator:
 evolution-indicator depends on evolution (>= 2.28.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-indicator (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 checkbox-gtk
 dbus
 dbus-x11
 evolution
 evolution-couchdb
 evolution-exchange
 evolution-plugins
 gnome-session-bin
 gdm
 gdm-guest-session
 gnome-session
 indicator-session
 indicator-applet-session
 ubuntu-desktop
 evolution-indicator
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by sailthesea on 2009-12-06
I'm no expert but that seems to be an error with the source.
 Are you using the right repositories? (I've forgotten which to enable in Jaunty)
 Someone will steer you right I'm sure!;)

---

### Post by OisinT on 2009-12-07
here is my /etc/apt/sources.list anyway if that helps.  thanks

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ie.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports restricted main multiverse universe #Added by software-properties
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
deb http://apt.last.fm/ debian stable
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu karmic main
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu karmic main
# deb http://ftp.de.debian.org/debian sid main
```

---

