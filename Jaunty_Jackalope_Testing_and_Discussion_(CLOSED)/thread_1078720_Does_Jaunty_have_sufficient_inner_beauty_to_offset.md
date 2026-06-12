---
title: "Does Jaunty have sufficient inner beauty to offset the lack of visual improvement?"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-02-23
The question must be asked: Is Jaunty sexy enough under the hood?

---

### Post by go7Ul1ai on 2009-02-23
I'm impressed with the speed and reliability of Jaunty even when it's in Alpha.

---

### Post by ugkbunb on 2009-02-23
> **lee.jarratt said:**
> i'm impressed with the speed and reliability of jaunty even when it's in alpha.

+1

---

### Post by jfernyhough on 2009-02-23
The only way I've managed to break Jaunty is to use a release candidate kernel, and even then it was down to a race condition with ext4 needing a Magic Key reboot. fsck then zeroed a few files, killing the boot structure, though it was surprisingly easy to recover... although Evolution is being a pain at the minute (I think down to keyring access).

This is with Alsa 1.0.19, Pulse 0.9.15 and a considerable number of other PPAs...

For your enjoyment:```
## Main
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Updates
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## Backports
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Proposed
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse

## Commercial
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

## Security
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse

###### Third-Party Repos ######

## Medibuntu
deb http://packages.medibuntu.org/ jaunty free non-free

## Upstream Opera
# deb http://deb.opera.com/opera/ testing non-free

## Wine
deb http://wine.budgetdedicated.com/apt/ intrepid main

## Dropbox
deb http://www.getdropbox.com/static/ubuntu intrepid main
# deb-src http://www.getdropbox.com/static/ubuntu hardy main

## Boxee
deb http://apt.boxee.tv jaunty main
deb http://apt.boxee.tv intrepid main

## VirtualBox
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free


###### PPA ######

## NM 0.7
# deb http://ppa.launchpad.net/network-manager/ubuntu/ jaunty main
# deb-src http://ppa.launchpad.net/network-manager/ubuntu/ jaunty main

## OOo
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu/ jaunty main
# deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu/ jaunty main

## Gnome-Do
deb http://ppa.launchpad.net/do-core/ppa/ubuntu/ intrepid main
# deb-src http://ppa.launchpad.net/do-core/ubuntu/ jaunty main

## Kernelcheck
deb http://ppa.launchpad.net/master-kernel/ubuntu/ hardy main
# deb-src http://ppa.launchpad.net/master-kernel/ubuntu/ jaunty main

## Terminator (tiled consoles)
# deb http://ppa.launchpad.net/gnome-terminator/ubuntu/ jaunty main
# deb-src http://ppa.launchpad.net/gnome-terminator/ubuntu/ jaunty main

## nvidia
deb http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main

## Exaile
# deb http://ppa.launchpad.net/exaile-devel/ubuntu/ jaunty main

## Bluetooth extras
# deb http://ppa.launchpad.net/blueman/ubuntu/ jaunty main

## PulseAudio Fixes - http://ubuntuforums.org/showthread.php?p=5587712
# deb http://ppa.launchpad.net/psyke83/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/psyke83/ubuntu jaunty main

## Wine
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ubuntu hardy main

## GScrot
# deb http://ppa.launchpad.net/gscrot/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/gscrot/ubuntu jaunty main

## Pulseaudio dev
deb http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main

## PackageKit
# deb http://ppa.launchpad.net/packagekit/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/packagekit/ubuntu jaunty main

## Compiz
# deb http://ppa.launchpad.net/compiz/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/compiz/ubuntu jaunty main

## Christoph Korn - various apps (VLC, GIMP and others)
# deb http://ppa.launchpad.net/c-korn/ubuntu jaunty main

## PyRoom
deb http://ppa.launchpad.net/pyroom-dev/ubuntu jaunty main

## KDE4
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu jaunty main

## LyX
# deb http://ppa.launchpad.net/lyx-developers/ubuntu jaunty main

## Kwwii artwork
# deb http://ppa.launchpad.net/kwwii/ppa/ubuntu jaunty main

## Deluge
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main

## XBMC
# deb http://ppa.launchpad.net/team-xbmc/ubuntu hardy main

## FTA (XULRunner-based apps)
deb http://ppa.launchpad.net/fta/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/fta/ubuntu jaunty main

## Pidgin developers
# deb http://ppa.launchpad.net/pidgin-developers/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/pidgin-developers/ubuntu jaunty main

## Inkscape
## Dan's PPA: https://launchpad.net/~danf-1979/+archive
deb http://ppa.launchpad.net/danf-1979/ppa/ubuntu jaunty main

## Unetbootin
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/gezakovacs/ubuntu jaunty main

## Ubuntu Tweak
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main

## Andrewsomething (Sound themes)
deb http://ppa.launchpad.net/andrewsomething/ppa/ubuntu jaunty main

## Next
deb http://ppa.launchpad.net/next-kernel/ppa/ubuntu jaunty main restricted universe multiverse
deb http://ppa.launchpad.net/next-media/ppa/ubuntu jaunty main restricted universe multiverse
deb http://ppa.launchpad.net/next-mono/ppa/ubuntu jaunty main restricted universe multiverse

## PPA for Gianvito Cavasoli (Intrepid builds)
deb http://ppa.launchpad.net/janvitus/ppa/ubuntu intrepid main restricted universe multiverse
# deb-src http://ppa.launchpad.net/janvitus/ppa/ubuntu intrepid main

## Kigo
deb http://ppa.launchpad.net/saschpe/ppa/ubuntu/ jaunty main

## Evo MAPI
deb http://ppa.launchpad.net/jelmer/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/jelmer/ppa/ubuntu jaunty main

## Alsa
deb http://ppa.launchpad.net/pgquiles/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/pgquiles/ppa/ubuntu intrepid main

## Ubuntu Mozilla daily
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main

## Webkit team
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main

## Pidgin msn Pecan
deb http://ppa.launchpad.net/msn-pecan/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/msn-pecan/ppa/ubuntu jaunty main
```

---

### Post by nanog on 2009-02-23
jfernyhough, your source.list is a perfect example of why ubuntu needs an official testing repo. the proliferation of semi-official ppas (e.g. those run by active developers) is completely out of control.

---

### Post by talkingwires on 2009-02-24
> **nanog said:**
> jfernyhough, your source.list is a perfect example of why ubuntu needs an official testing repo. the proliferation of semi-official ppas (e.g. those run by active developers) is completely out of control.I've always thought of Debian as Ubuntu's testing repo. ;)

---

### Post by Nullack on 2009-02-24
I consider Jaunty to be a small release. It fixes some things but I am yet to be truly impressed with fixing long standing fundamental problems with the Linux OS.

---

### Post by plun on 2009-02-24
> **Starks said:**
> The question must be asked: Is Jaunty sexy enough under the hood?

Well....

For my personal needs Jaunty is nearly perfect.  (including a lot of jferny&#347; ppas or from source ):P)

A "nerd" can see this but not a main stream user or a newbie, they will struggle with basic issues for a normal computer user.

One easy thing Ubuntu can do is to throw out Gnomes lower panel and use AWN or Gnome-do as default dock.....

Just to wait another 6 months...:rolleyes:

---

### Post by Kow on 2009-02-24
> **talkingwires said:**
> I've always thought of Debian as Ubuntu's testing repo. ;)

That is exactly true.

Development flow (for Ubuntu):

Debian sid -> Ubuntu dev -> release. In a way we are testing for sid so long as the bugs get reported upstream if applicable. Obviously this isn't perfect because sid is constantly being updated and is never frozen as far as I know while Ubuntu's dev repo has all kinds of time-related restrictions. Sync/merge with sid....freeze for awhile... resync/remerge with sid.

---

### Post by MasterNetra on 2009-02-24
> **talkingwires said:**
> I've always thought of Debian as Ubuntu's testing repo. ;)

Funny I thought Ubuntu was Debian's testing ground considering how long it takes for Debian Releases to edge off the shelf :p

---

### Post by directhex on 2009-02-24
> **Kow said:**
> sid is constantly being updated and is never frozen as far as I know

Sid was essentially frozen (although not technically) for Lenny release last JULY, and only thawed within the last couple of weeks. That's part of the problem, really.

---

### Post by Starks on 2009-02-24
Experimental >>>>>>>> Sid

---

### Post by directhex on 2009-02-24
> **Starks said:**
> Experimental >>>>>>>> Sid

Experimental is a layer on top of Sid, not a release in its own right. Part of that means building against it is a PITA (as it's pinned very low compared to Sid), and that packages may be built against a combination of Sid and Experimental (e.g. packages in Experimental built against Sid GNOME, not Experimental GNOME)

---

