---
title: "Sources.list problem after 19.10 to 20.04 upgrade"
date: 2020-04-27
forum: Installation &amp; Upgrades
---

### Post by raif on 2020-04-27
On upgrading from Ubuntu 19.10 to 20.04 I am unable to use Software Updater, it says "Failed to download repository information, check internet connection." I've run sudo apt update in Terminal and get error messages like:

```
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target Translations (restricted/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:6
```

It seems that another sources.list file is being used as there are references to other PPAs I use when running Software Updater. But there's just that file and sources.list.saved in /etc/apt/

My /etc/apt/sources.list contents are:

```
# deb cdrom:[Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017)]/ eoan main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ focal restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ eoan universe
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates universe
# deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ eoan multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ eoan-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ eoan-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu eoan partner

deb http://gb.archive.ubuntu.com/ubuntu/ focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu eoan-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ focal-security universe
# deb-src http://security.ubuntu.com/ubuntu eoan-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu eoan-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
```

Where is this other file? What is happening? I've never seen this behaviour before, is it something to do with a change in the way Ubuntu deals with updates in 20.04 (as part of the move to Snap??).

Many thanks in advance for any help

---

### Post by deadflowr on 2020-04-27
The first stanza has restricted listed twice for the same repository
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ focal main **restricted**
deb http://gb.archive.ubuntu.com/ubuntu/ focal **restricted**
```
remove one of them.
probably easier to just comment or delete the second line.


Edit: also, PPAs are always in unique .list files per PPA inside the /etc/apt/sources.list.d directory.
(Unique in that each PPA has it's own file.)

---

### Post by raif on 2020-04-27
Many thanks deadflowr for responding so helpfully & quickly, have changed sources.list and deleted then reinstalled PPAs. That's sorted some of the issues.

But the underlying problem with software updater remains: if I click on settings button to edit my sources via a GUI, I get an empty window. Likewise if I try to open software & updates I get the same empty window.

If I type "software-properties-gtk" in bash, the same empty window opens, there's no error message, bash just gives a new prompt.

(I've not put this in a new thread as still an issue with sources.list albeit about ability to edit via GUI, following update to 20.04).

---

### Post by deadflowr on 2020-04-27
Try with the debug option
```
software-properties-gtk -d
```

---

