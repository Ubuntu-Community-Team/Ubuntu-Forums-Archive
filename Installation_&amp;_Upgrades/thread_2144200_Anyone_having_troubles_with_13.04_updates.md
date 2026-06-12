---
title: "Anyone having troubles with 13.04 updates?"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2013-05-11
I'm sticking with 12.04 on our daily driver, but decided to try out 13.04 on a Dell Latitude notebook.  Installed it yesterday afternoon.  Tried to update from terminal (sudo apt-get upgrade, sudo apt-get update) last night and again this morning.  Two repositories are failing.  

us.archive.ubuntu.com & extras.ubuntu.com.  

Ran an update on our 12.04 PC this morning.  It went fine.  

I've had upgrades fail before for a day or two, then it all works again.  But would feel better about it if others are having the same problem.  A quick forum search didn't give me any hits.

---

### Post by grahammechanical on 2013-05-11
How about here

[http://ubuntuforums.org/showthread.php?t=2144181](http://ubuntuforums.org/showthread.php?t=2144181)

---

### Post by Bartender on 2013-05-11
That person's problems seem to be different.  He tried upgrading a previous install.  I nuked and reinstalled.  However, my apt-get sources list might provide some clues?

```

# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu raring-security main restricted
deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu raring-security universe
deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu raring-security multiverse
deb-src http://security.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main
```

I don't see anything obviously wrong here, but that's not saying much because I'm not an expert at troubleshooting repo lists...

Oh, hey, in terminal I got an error message that doesn't make much sense to me...

```
hammer@hammer-D630:~$ sudo gedit /etc/apt/sources.list
[sudo] password for hammer: 

(gedit:2283): IBUS-WARNING **: The owner of /home/hammer/.config/ibus/bus is not root!
```

This notebook was running Mint 13 the last year or so.  Never gave me any grief.

---

### Post by ibjsb4 on 2013-05-11
Here's a shot in the dark :)

[http://ubuntuforums.org/showthread.php?t=2138386](http://ubuntuforums.org/showthread.php?t=2138386)

---

### Post by Bartender on 2013-05-11
Before I fully updated the original installation, I'd followed the steps outlined at several places like OMG Ubuntu for adding the Gnome 3.8 ppa.  

So after all the trouble described above, I went into settings and turned off those two ppa's.  Ran update again from terminal and it appeared to go OK.  Ran Software Updater just to see what would happen and it said software was up-to-date.  

So I went back and turned the two Gnome 3.8 ppa's on again and ran Software Updater.  Failed.  Removed the two gnome ppa's, restart, [follow the steps]("http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome") online again for adding the ppa, then installing the packages.  Looks like it might be working.  I got the window asking if I wanted to run gdm or lightdm, which hadn't happened before.

One more quirk about this process: I was unable to install Gnome Shell from The Software Center.  Error message said something about dependencies that couldn't be met.  So on the OMG Ubuntu page I pasted in the code they had for "If you don't have Gnome Shell Installed".

Yup, it worked.  I've got Gnome 3.8.  For anyone else who comes across this thread; fully update 13.04 BEFORE trying to install Gnome 3.8.

---

