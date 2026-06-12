---
title: "Upgrade 12.04 to 14.04 stoped working. -&gt; Some Progs and Fonts are broke"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by Ben_Nemsi on 2015-02-01
Hi there,
I had a well running 12.04 and (stupid me) tried to upgrade to 14.04.
Somewhere in the middle of the upgrade the script stopped. 
I guess it was waiting for an external event which obviously didn't occur.
 After a whole day of restless waiting I had to kill the process.
 Now my desktop says it is upgraded to 14.04.  
 However some of the applications which are reported to be installed wont start or aren't even there.
 

 Is there a safe way to repair this broken 14.04 installation???
 

 Help is highly appreciated :-((
 
Ben

---

### Post by Bashing-om on 2015-02-01
Ben_Nemsi; Hi ! Welcome to the forum.

Sure, it's 'buntu it is always fixable; just depends on the amount of trouble and aggravation one is prepared to endure.
Bet in this instance that there are 3rd party software that the package manager did not know how to cope with (proprietary graphics driver ?).

Let's start with that premise. Post back the outputs - Between Code Tags, please - of terminal commands:
```

cat /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We take care of the possible 3rd party stuff, then move on to seeing what condition the package manager is in and the state of the operating system.

It is in the process
[INDENT][INDENT]the longest journey begins with that 1st step
[/INDENT][/INDENT]

---

### Post by Ben_Nemsi on 2015-02-01
Hi Bashing-om

first of all thanks for your quick reply.

here the result of the proposed command lines
1. Line: cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release i386 (20110720.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty universe
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
# deb http://archive.canonical.com/ lucid partner
# deb http://download.virtualbox.org/virtualbox/debian precise contrib non-free # Bei Aktualisierung zu precise deaktiviert
# deb http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu karmic main # Bei Aktualisierung zu precise deaktiviert
# deb-src http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu karmic main # Bei Aktualisierung zu precise deaktiviert
# deb http://archive.canonical.com/ lucid partner
# deb http://www.duinsoft.nl/pkg debs all # Bei Aktualisierung zu precise deaktiviert

# deb http://us.archive.ubuntu.com/ubuntu main universe
# deb http://www.plexapp.com/repo precise main # Bei Aktualisierung zu precise deaktiviert

```

the second cmd line: tail -v -n +1 /etc/apt/sources.list.d/*
```

==> /etc/apt/sources.list.d/badgerports-lucid.list <==
# Badgerports repository. Contains cli-common-dev required by iFolder.
# deb http://badgerports.org/ precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/badgerports-lucid.list.distUpgrade <==
# Badgerports repository. Contains cli-common-dev required by iFolder.
# deb http://badgerports.org/ precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/badgerports-lucid.list.save <==
# Badgerports repository. Contains cli-common-dev required by iFolder.
deb http://badgerports.org/ lucid main

==> /etc/apt/sources.list.d/btsync.list <==
# YeaSoft's BitTorrent Sync Packaging Repositoy
# deb http://debian.yeasoft.net/btsync precise main # Bei Aktualisierung zu precise deaktiviert
# deb-src http://debian.yeasoft.net/btsync precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/btsync.list.distUpgrade <==
# YeaSoft's BitTorrent Sync Packaging Repositoy
# deb http://debian.yeasoft.net/btsync precise main # Bei Aktualisierung zu precise deaktiviert
# deb-src http://debian.yeasoft.net/btsync precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/danielrichter2007-grub-customizer-lucid.list <==
# deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/danielrichter2007-grub-customizer-lucid.list.distUpgrade <==
# deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/danielrichter2007-grub-customizer-lucid.list.save <==
deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu lucid main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-earth.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/earth/deb/ stable main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/google-earth.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/earth/deb/ stable main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/google-earth.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/earth/deb/ stable main

==> /etc/apt/sources.list.d/lucid-partner.list <==
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
# deb http://archive.canonical.com/ubuntu lucid partner

==> /etc/apt/sources.list.d/lucid-partner.list.distUpgrade <==
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
# deb http://archive.canonical.com/ubuntu lucid partner

==> /etc/apt/sources.list.d/lucid-partner.list.save <==
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
# deb http://archive.canonical.com/ubuntu lucid partner

==> /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list <==
# deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list.distUpgrade <==
# deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list.save <==
deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main

==> /etc/apt/sources.list.d/psyke83-ppa-lucid.list <==
# deb http://ppa.launchpad.net/psyke83/ppa/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/psyke83-ppa-lucid.list.distUpgrade <==
# deb http://ppa.launchpad.net/psyke83/ppa/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/psyke83-ppa-lucid.list.save <==
deb http://ppa.launchpad.net/psyke83/ppa/ubuntu lucid main

==> /etc/apt/sources.list.d/ubuntu-audio-dev-alsa-daily-lucid.list <==
# deb http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/ubuntu-audio-dev-alsa-daily-lucid.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/yorba-ppa-lucid.list <==
# deb http://ppa.launchpad.net/yorba/ppa/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/yorba-ppa-lucid.list.distUpgrade <==
# deb http://ppa.launchpad.net/yorba/ppa/ubuntu precise main # Bei Aktualisierung zu precise deaktiviert

==> /etc/apt/sources.list.d/yorba-ppa-lucid.list.save <==
deb http://ppa.launchpad.net/yorba/ppa/ubuntu lucid main

```

Hope you can tell me how to go on

Thx in advance 
Ben

---

### Post by Bashing-om on 2015-02-01
Ben_Nemsi; Hey, hey ...

The good news is that you look to be up on 'trusty' and I do not see a proprietary driver PPA .
The bad news is all those old 'lucid' PPAs still in use ... in the 3rd party directory "/etc/apt/sources.list.d".

Are you comfortable with a text editor to permit a more organized approach to resolving those old 'lucid' fetches that no longer apply ?

[INDENT][INDENT]looks real doable
[/INDENT][/INDENT]

---

### Post by Ben_Nemsi on 2015-02-01
Hi Bashing-om,

i think i can handle a text editor and wont have trouble withe basics of Linux

go ahead

Ben

---

### Post by Bashing-om on 2015-02-01
Ben_Nemsi; Outstanding:
ok .. those old antiquated sources: I see nothing on 2nd look that is active such that it will effect the system upgrade. 

At a later time one will want to address these 2 in particular
1) [http://badgerports.org/](http://badgerports.org/) lucid main
Pull up in your browser:
[http://badgerports.org/](http://badgerports.org/)
see it is no longer supported. If ya want it still, follow the author's directive, 
In the meantime comment it out by placing a '#' at the start of the line (gksudo gedit /etc/apt/sources.list.d/badgerports-lucid.list) .

2)deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) lucid main
FireFox is well supported in the software repository, is there really a need to resort to a PPA ?
I do suggest to remove this PPA .

And look at all the others and see if they are supported in 14.04 and IF you want them on your system.
-----------------------------------
Now to the situation present;
Execute these terminal commands:
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo dpkg -C

```
These clean up the system, brings everything up to date, checks the package management system, and also reports any problems.
Post back any outputs with errors, in particular the results of "sudo apt-get -f install", "sudo dpkg --configure -a" and "sudo dpkg -C"

In anticipate that ya come out of it clean as a whistle.
The tale is told in the outputs of those last 3 commands.

[INDENT][INDENT][INDENT]maybe YES. all good now
[/INDENT][/INDENT][/INDENT]

---

