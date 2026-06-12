---
title: "upgraded to 20.04 - software is gone and I can't get it back"
date: 2020-05-16
forum: Installation &amp; Upgrades
---

### Post by nicklikesfire on 2020-05-16
Hi Folks! I use a lot of tagging software and it's fairly important to me. I just upgraded to 20.04 and I've noticed a few things that I had before are missing, and I can't figure out how to get them back.

Puddletag
PyRenamer
UMPlayer

When I run apt update:

[INDENT]Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                         
Hit:4 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) focal InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease
Hit:7 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) focal InRelease
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease          
Hit:9 [http://ppa.launchpad.net/lutris-team/lutris/ubuntu](http://ppa.launchpad.net/lutris-team/lutris/ubuntu) focal InRelease 
Hit:10 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) focal InRelease
Hit:11 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) focal InRelease
Hit:12 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) focal InRelease
Hit:13 [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) xenial InRelease
Hit:14 [http://ppa.launchpad.net/webupd8team/nemo/ubuntu](http://ppa.launchpad.net/webupd8team/nemo/ubuntu) xenial InRelease
Hit:15 [http://ppa.launchpad.net/webupd8team/puddletag/ubuntu](http://ppa.launchpad.net/webupd8team/puddletag/ubuntu) xenial InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.[/INDENT]

As you can see, I had to use old releases on some of these.

When I try to install Puddletag I get:

[INDENT]sudo apt-get install puddletag
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 puddletag : Depends: python-mutagen (>= 1.14) but it is not installable
             Depends: python-qt4 (>= 4.5) but it is not installable
             Depends: python-configobj (>= 4.5) but it is not installable
             Depends: python-audioread but it is not installable
             Depends: python-acoustid but it is not installable
             Recommends: libchromaprint-tools but it is not going to be installed
             Recommends: python-levenshtein but it is not installable
             Recommends: python-mysqldb but it is not installable
E: Unable to correct problems, you have held broken packages.[/INDENT]

PyRenamer just gives me:

[INDENT]sudo apt-get install pyrenamer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pyrenamer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'pyrenamer' has no installation candidate[/INDENT]

Similar thing with Umplayer.

Any ideas how I can get these back? Ho do I prevent this from happening on the next upgrade? Thank you so much!

---

### Post by crip720 on 2020-05-16
Upgrading disables PPAs, will need to go software and updates and re-enable them.  Not quite sure which tab you need to use but would only take a couple of seconds to find right tab in software and updates(the one with PPAs listed).  Usually it is recommended to disable PPAs before upgrades to new versions.

---

### Post by Frogs Hair on 2020-05-16
> Package 'pyrenamer' has no installation candidate

It is also a good idea to find out if the PPA/s have a release candidate for the version you are upgrading to. You'll have to wait until the package maintainer upgrades the PPA or contact them.

---

### Post by oldfred on 2020-05-16
> Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease

You are showing some xenial still & ppa's are xenial.  You need everything to be focal.

And not all ppa's are then necessarily available in focal. Some are not needed, and some become obsolete.

You may  be in the python2 becoming obsolete. 
Python 2 is reaching end-of-life on 1 January 2020 

Ubuntu now uses python3 by default. 
I had one or two apps that were python2, but when manually installing them I stopped install of those, so have no python2.

You need to check if those applications are python2 or python3.

---

### Post by nicklikesfire on 2020-05-16
Many of the PPAs do not have a current release candidate. I went in and changed these to the latest version I could find. Is there a reason I can't continue to use the old versions?

Is it impossible to keep using both versions of Python? Some of my programs definitely need python 2.

Is there no way to keep using old programs? I'm fairly desperate.

Thanks!

---

