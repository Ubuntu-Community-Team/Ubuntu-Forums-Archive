---
title: "Pinning Repo Priority Not Working"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by mattruby on 2013-01-17
I use UbuntuStudio, but I want to use non-mixer, which isn't included in the UbuntuStudio APT repository. (FWIW, I don't see in the UbuntuStudio subforum the kind of expertise I probably need for this problem that's really a general Ubuntu config problem.) The non-mixer developers don't package it for Ubuntu (or for Debian), but some other project packagers do, tracking the latest (and perhaps their own further patched) version. It looks like ppa:kxstudio-team has a good package of it. But [that PPA includes lots of packages]("https://launchpad.net/~kxstudio-team/+archive/ppa/+index?batch=75&memo=450&start=450") that conflict with packages in UbuntuStudio, and I want only non-mixer (and non-daw, and maybe the other non-* packages not included in UbuntuStudio). If I add that PPA but don't do anything else, APT (eg. Software Updater) tells me that dozens of updates are available that I can upgrade from. I don't want to get notified whenever any updates are available except to non-*; I don't want to have to deselect all the other updates but non-*; I don't want to have to use Synaptic and pin the version of every conflicting package in kxstudio (what happens when they add a new package that conflicts?). I just want to rely on Software updater to upgrade only the non-* packages that kxstudio advertises.

The usual technique for deprioritizing a repo so APT ignores later revisions to packages in it, except ones not overridden by the higher priority repo(s), is to pin it. So I followed [the pinning HowTo]("https://help.ubuntu.com/community/PinningHowto"). But the pinning configs don't seem to be getting used by APT.

```

# Before adding kxstudio PPA:
sudo apt-cache policy alsa-base
alsa-base:
  Installed: 1.0.25+dfsg-0ubuntu3
  Candidate: 1.0.25+dfsg-0ubuntu3
  Version table:
 *** 1.0.25+dfsg-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status

# Add kxstudio PPA:
sudo add-apt-repository ppa:kxstudio-team/ppa
#...lots of advisory info from the PPA...
More info: https://launchpad.net/~kxstudio-team/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

# I press Enter
# ...gpg processes key into keyring, including 'public key "Launchpad PPA for KXStudio Team" imported'...
OK

# Add pinning preferences:
sudo vi /etc/apt/preferences.d/kxstudio-team-ppa-quantal-400
Package: *
Pin: release o=LP-PPA-kxstudio-team-ppa
Pin-Priority: 400
:wq

# Apply changes:
apt-get update
# ...successful update...

# Check priorities of a conflicting package:
sudo apt-cache policy alsa-basealsa-base:
  Installed: 1.0.25+dfsg-0ubuntu3
  Candidate: 1.0.25+dfsg-0ubuntu3+fixed1
  Version table:
     1.0.25+dfsg-0ubuntu3+fixed1 0
        500 http://ppa.launchpad.net/kxstudio-team/ppa/ubuntu/ quantal/main amd64 Packages
 *** 1.0.25+dfsg-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status

```

It didn't work: APT wants to upgrade alsa-base from the kxstudio repo, and the kxstudio repo package still has a priority of 500, the same as the UbuntuStudio repo package. Software Updater wants to upgrade dozens of packages that conflict with UbuntuStudio, but I don't' want to.

What should I do to make this work properly?

---

