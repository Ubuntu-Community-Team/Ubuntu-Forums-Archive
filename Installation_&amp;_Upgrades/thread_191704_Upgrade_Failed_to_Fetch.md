---
title: "Upgrade: Failed to Fetch"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by bigpup on 2006-06-07
I've tried upgrade of Breezy several times over several days, always getting the same fatal error:

Failed to fetch
[http://koti.mbnet.fi/~ots/ubuntu/Breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/Breezy/Packages.gz)  404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/Breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/Breezy/Sources.gz)  404 Not Found

So what?

---

### Post by croak77 on 2006-06-07
Can you post your /etc/apt/sources.list

---

### Post by bigpup on 2006-06-07
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

## created by arniesourcewrite

---

### Post by bigpup on 2006-06-07
I googled the "arniesourcewrite" final tag and found only one hit:
[http://forum.ubuntu.pl/viewtopic.php?t=8181](http://forum.ubuntu.pl/viewtopic.php?t=8181)

Maybe the Poles have answered this problem, but I cannot read it.
I have two identical backups of the sources.list.
Maybe I'll just substitute them?

---

### Post by croak77 on 2006-06-08
You have all Breezy repo's. If you want to upgrade to Dapper you'll need to change all the "breezy"  to "dapper".  Also some of your 3rd party repo's are either obsolete of old. You can delete:

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
 Cause it's 404. Did you add this repo for a reason? There doesn't seem to be any Ubuntu repo at that address anymore.

And:
deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main
It's obsolete. There is a kde 3.5.2 repo now.

After changing  your source.list, make sure to   sudo apt-get update && sudo apt-get dist-upgrade. Not sudo apt-get upgrade.

Here they example sources.list from the wiki.

## All officially supported packages, including security- and other updates
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
 
 ## The source packages (only needed to recompile existing packages)
 #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
 #deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
 #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
 
 ## All community supported packages, including security- and other updates
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
 
 ## The source packages (only needed to recompile existing packages)
 #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
 #deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
 #deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

You can also you a gui tool called update-manager. I haven't used it myself but it should work too.

Link to Upgrade wiki:
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

---

### Post by bigpup on 2006-06-09
When I look at the sources.list file in gedit, it is read only.
How do I get permissions within gedit (or elsewise) to rename or edit the file?

The wiki on RootSudo says to open Terminal and enter :
gksudo gedit
Then I get this message:

> (gedit:9444): GnomeUI-Warning **: While connecting to the session manager:
Authentication Rejected, reason : None of the authentication protocols specified
are supported and host-based authentications failed.

---

### Post by bigpup on 2006-06-09
Oops. Well, gedit seems to be doing the job now, despite the warning.

---

