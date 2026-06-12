---
title: "`do-release-upgrade` failed halfway during upgrade from 18 to 20"
date: 2022-08-17
forum: Installation &amp; Upgrades
---

### Post by mluisser on 2022-08-17
Trying to release-upgrade from 18 to 20, but `do-release-upgrade` failed with some (probably unrelated gui) error. Now all software sources already point to focal.

When I try to restart `do-release-upgrade`, I get 'Please install all available updates for your release before upgrading.' because all sources already point to focal.

Should I:

A) simply proceed with apt-upgrade or

B) reset the software source to bionic (how? please advise!) and then proceed with `do-release-upgrade`?

`lsb_release -a` still shows Ubuntu 18, bionic beaver.

Thanks!

EDIT - my /etc/apt/sources.list looks like this:


```
# deb cdrom:[Kubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main multiverse restricted universe


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://at.archive.ubuntu.com/ubuntu/ focal main restricted
# deb-src http://at.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://at.archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://at.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://at.archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://at.archive.ubuntu.com/ubuntu/ xenial universe
deb http://at.archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://at.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://at.archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://at.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://at.archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://at.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://at.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://at.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://security.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

Can I just edit this back to bionic and all will be good?

**SOLVED**

I manually edited '/etc/apt/sources.list' and changed from 'focal' to 'bionic'. Since no focal packages were installed yet, I could restart 'do-release-upgrade'.

---

### Post by guiverc on 2022-08-17
If you were still in the downloading stage, you can edit & return sources to point to *bionic*, **however **if packages had already started installing, then you're no longer on *bionic* and changing sources back will likely not have a good/safe/secure result. 

Halfway isn't very descriptive, so I have no idea where you were up to.

If packages were already installing; and it's only a small number, you could manually force the *bionic* packages to be re-installed... then once all that has been done, change sources back to *bionic*, but this is a load of work unless you're *halfway* counter included the download part of the process as a very large percentage of *your halfway*.

Given I don't know where you are, I'd like `apt full-upgrade` and have it try and continue the *release-upgrade* process.


Also note, I've assumed here you're talking about 18.04 to 20.04, as the upgrade process of 18 to 20 differs from 18.04 to 20.04, as the Core 18 server system will upgrade only the system packages when upgrading to  20, with no user applications changing as *snap* packages used by 16, 18, 20 & 22 are identical running equally on all.  Ubuntu has used the *year* format to represent *snap* only products since 2016, with all *deb* based I've assumed using the *year.month* format (*and with deb based releases all deb packages need to upgrade when you release-upgrade unlike snap packages*).

Does lsb_release really say 18?  and not 18.04 as they are different Ubuntu products?  My comment assumes 18.04, so if you're using Ubuntu Core 18 - please ignore this advice as I have less experience with it (*your sources though look like a year.month system*).

---

### Post by Claus7 on 2022-08-17
Hello,

if you are halfway through, can you continue the upgrade process via synaptic package manager? I faced the same issue a long time ago, and this saved me. I hadn't rebooted in the process though, yet just continued the upgrade.

Regards!

---

### Post by mluisser on 2022-08-17
Thank you and sorry for the inaccuracies - it is indeed '[FONT=monospace][COLOR=#000000]Ubuntu 18.04.6 LTS'. I don't think the installation already started, but I'm not 100% sure. How can I find out? 'apt upgrade' says:

[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]1572 upgraded, 152 newly installed, 0 to remove and 1533 not upgraded.[/COLOR]
213 standard security updates[/FONT]
```

EDIT: Didn't actually run the command - this is what it would do.

---

