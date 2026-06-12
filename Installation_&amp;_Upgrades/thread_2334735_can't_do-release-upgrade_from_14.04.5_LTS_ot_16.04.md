---
title: "can't do-release-upgrade from 14.04.5 LTS ot 16.04?"
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2016-08-22
Hi,

I'm trying to do-release-upgrade from my 14.04.5 LTS box to 16.04 LTS, but do-release-upgrade tells me that either I have unofficial packages or I'm trying to upgrade from an outdated version, neither of which seems to be true. But other than this message, I can't get out the specifics of why the upgrade is not working.

14.04.5 is listed among the 'current' releases: [http://releases.ubuntu.com/](http://releases.ubuntu.com/) . this is what my system sais:

```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty

```


I filed a bug on this regard, but no response: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1612301](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1612301)

What could be wrong?


Akos

---

### Post by ajgreeny on 2016-08-22
Is your 14.-04.5 system using lots of PPA repos or have you customised it a lot to manually install packages, using software-centre or gdebi, that are not in the standard repos?

If you have done so in the past in this OS you may need to disable the PPAs and remove the manually installed packages or the upgrade system may be totally confused.  The closer your system is to a standard installation from the standard repos only, the easier it will be to upgrade.

I notice in your bug the two following lines
```
InstallationDate: Installed on 2011-11-09 (1736 days ago)
InstallationMedia: Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 
``` which suggests you have first installed this system in 2011 and been distro updating ever since, so I wonder if now might be the moment to make a new start with a clean installation.
The log files you attached to the bug do not help me much, I'm afraid, but may make more sense to others.

---

### Post by ian-weisser on 2016-08-22
I updated your bug to reflect the correct package, based upon the error message.

Please DO NOT BUMP bug reports. The bug tracker is not a support forum. Bumps do nothing there...except annoy Triagers and Developers by making the bug report harder to read.

Expect a bug report to be Triaged in a few weeks or months, and a fix to appear in the next (or following) release of Ubuntu...if (and only if) a Bug Squad Triager can duplicate the problem on their test system. If they cannot duplicate your problem, then they will close your bug report unfixed. You can Triage your own bug report if you wish; it's a bit of work. The key is to find out what kind of Python3 Error is being generated but unhandled.

Do note that most bugs are Triaged by Bug Squad volunteers. Canonical  employs a couple nice developers working on apt (among other projects),  but they are much too busy creating the fixes to Triaged bugs to do much  Triaging themselves.

Your best option for upgrading to 16.04 is to back up your data and install afresh. If it's possible to preserve your existing system partition so you can duplicate the crash and test the fix, please do so - fixing the bug may need that. If you reinstall without preserving the old partiton, then please invalidate (close) the bug report to keep Triagers and Developers from wasting their time trying to track down a bug without enough information and without your help.

---

