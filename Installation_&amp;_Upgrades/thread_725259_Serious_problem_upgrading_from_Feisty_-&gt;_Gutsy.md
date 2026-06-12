---
title: "Serious problem upgrading from Feisty -&gt; Gutsy"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by rahaydenuk on 2008-03-15
Hi,

I've just tried to upgrade my Kubuntu system from Feisty -> Gutsy following the instructions at [http://kubuntu.org/announcements/7.10-release.php#upgrade](http://kubuntu.org/announcements/7.10-release.php#upgrade). This failed during the distribution upgrade because it couldn't find a desktop meta-package, advising me to install kubuntu-desktop and try again. So I tried "apt-get install kubuntu-desktop" and I get the following error:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  kubuntu-desktop: Depends: kcontrol but it is not going to be installed
                   Depends: kde-systemsettings but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: kicker but it is not going to be installed
                   Depends: kmplayer-konq-plugins but it is not going to be installed
                   Depends: konq-plugins but it is not going to be installed
                   Depends: ksplash but it is not going to be installed
                   Depends: ksplash-engine-moodin but it is not going to be installed
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Recommends: kexi but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
E: Broken packages

```
Trying to manually apt-get install any of the above dependencies fails similarly with its own list of unmet dependencies.

My sources.list is:
```

#
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse


## uPure64 Repository
# deb http://janvitus.interfree.it/ubuntu/ feisty-upure64 main-amd64
# deb-src http://janvitus.interfree.it/ubuntu/ feisty-upure64 main-amd64
deb http://packages.medibuntu.org/ feisty free non-free

# deb http://kubuntu.org/packages/amarok-latest feisty main

deb http://security.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe

```

I've tried apt-get install -f, which doesn't do/find anything.

Anyone help, this is really annoying as it seems to have broken everything to do with KDE?

Thanks,

Richard.

---

### Post by Pumalite on 2008-03-15
Comment out medibuntu.
Uncomment feisty-backports
Sudo update
Try to upgrade again.
I'd use Main Server

---

