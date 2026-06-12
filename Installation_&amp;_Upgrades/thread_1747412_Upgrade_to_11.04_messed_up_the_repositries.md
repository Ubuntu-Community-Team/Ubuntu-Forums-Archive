---
title: "Upgrade to 11.04 messed up the repositries"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by n0c0d3 on 2011-05-02
I did an upgrade from Xubuntu 10.10 to 11.04 from within the Update Manager, but in order to do that I had to remove some 3rd party repositories, otherwise it wouldn't work. Thuogh I wanted a full upgrade, this didn't seem to be possible so I did a partial upgrade. It seemed to have worked but the repostories are giving problems. 

When I open the Update Manager I get a whole bunch of possible updates (it looks like the partial upgrade). Then I click the check-button but then I get a message I need to do a partial upgrade, so maybe something wasn't installed well when I did the initial partial upgrade. I try do do this, but get the error: "An upgrade from 'natty' to 'maverick' is not supported with this tool." This is pretty obviously very strange, as it would be a downgrade. Also in the sources.list there is no reference to any maverick repo.

The I restart the update manager and press the check-button, or when I try to open the settings, I get the following error-message:
> 
Not all updates can be installed
Run a partial upgrade, to install as many updates as possible.

This can be caused by:
*A previous which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu
Then I can choose the partial upgrade again, which gives the natty/maverich error-message again.

Also from within Synaptic I can't edit the repositories, the same error-message as described when I press the check-button in the Update Manager.

In the sources.list I already disabled a couple of repo's that gave error lik "Failed to fetch.." and than the repo URL.

More info:
bart@Xub64:~/Desktop$ uname -a
Linux Xub64 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

My sources.list file-contents:
> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse
#deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports restricted main multiverse universe
#deb [http://ftp.nl.debian.org/debian](http://ftp.nl.debian.org/debian) sid main
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository
#deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
#deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb apps
#deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
#deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free
#deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) natty main

#deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/InRelease)
#deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/Release.gpg)
#deb [http://ppa.launchpad.net/gwibber-team/ubuntu](http://ppa.launchpad.net/gwibber-team/ubuntu) intrepid main
#deb-src [http://ppa.launchpad.net/gwibber-team/ubuntu](http://ppa.launchpad.net/gwibber-team/ubuntu) intrepid main

#deb-src [http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu/dists/natty/InRelease)
#deb [http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu/dists/natty/Release.gpg)

#deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) natty main
#deb-src [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) natty main

Is there anyone out here that knows what could be going wrong and how to fix his?

Thanks in advance for any help,
Bart

---

### Post by n0c0d3 on 2011-05-09
In the mean time I found a thread with the solution: an update from the command line like described over here:
[http://ubuntuforums.org/showpost.php?p=10715284&postcount=5](http://ubuntuforums.org/showpost.php?p=10715284&postcount=5)

---

