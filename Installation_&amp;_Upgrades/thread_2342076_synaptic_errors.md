---
title: "synaptic errors"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by jgw on 2016-11-03
I was updating with symantic and got the following errors:
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-xenial.list:1 and /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list:2

Apparently I have multiple configuration files for the same program(s).  

Thoughts? (thank you)

---

### Post by ajgreeny on 2016-11-03
I assume you mean **synaptic** errors and have edited the thread title to accommodate that for you?

Lets see the output of terminal commands ```
cat /etc/apt/sources.list
``` and then ```
ls  /etc/apt/sources.list.d/
``` and we can then tell you exactly what needs to be changed.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by jgw on 2016-11-03
Thanks for the reply.  Here are the results:
```
chelo@chelo-1005HA:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta i386 (20150805)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
```

```
chelo@chelo-1005HA:~$ ls /etc/apt/sources.list.d/
atareao-atareao-trusty.list
atareao-atareao-trusty.list.distUpgrade
atareao-atareao-trusty.list.save
diesch-testing-trusty.list
diesch-testing-trusty.list.distUpgrade
diesch-testing-trusty.list.save
jonathonf-ubuntu-mate-1_16-xenial.list
jonathonf-ubuntu-mate-1_16-xenial.list.save
otto-kesselgulasch-gimp-trusty.list
otto-kesselgulasch-gimp-trusty.list.distUpgrade
otto-kesselgulasch-gimp-trusty.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_tictactoe-wood_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_tictactoe-wood_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_tictactoe-wood_ubuntu.list.save
steam.list
steam.list.distUpgrade
steam.list.save
tualatrix-ppa-trusty.list
tualatrix-ppa-trusty.list.distUpgrade
tualatrix-ppa-trusty.list.save
ubuntu-mate-dev-ubuntu-welcome-xenial.list
webupd8team-y-ppa-manager-trusty.list
webupd8team-y-ppa-manager-trusty.list.distUpgrade
webupd8team-y-ppa-manager-trusty.list.save
```

---

### Post by ajgreeny on 2016-11-04
Your sources.list file is a bit convoluted and needs a clear out so open it as root with command ```
sudo -H gedit /etc/apt/sources.list
``` and delete any line with the word **trusty** in it as you are now using **xenial**.

Similarly you need to remove any of the files in the /etc/apt/sources.list.d folder that are for trusty, ie,
```
atareao-atareao-trusty.list
atareao-atareao-trusty.list.distUpgrade
atareao-atareao-trusty.list.save
diesch-testing-trusty.list
diesch-testing-trusty.list.distUpgrade
diesch-testing-trusty.list.save
otto-kesselgulasch-gimp-trusty.list
otto-kesselgulasch-gimp-trusty.list.distUpgrade
otto-kesselgulasch-gimp-trusty.list.save
tualatrix-ppa-trusty.list
tualatrix-ppa-trusty.list.distUpgrade
tualatrix-ppa-trusty.list.save
webupd8team-y-ppa-manager-trusty.list
webupd8team-y-ppa-manager-trusty.list.distUpgrade
webupd8team-y-ppa-manager-trusty.list.save
```

Finally you should run ```
sudo apt-get update && sudo apt-get upgrade
``` to finish the procedure properly.

All PPA and non standard repos should be removed before upgrading the distro version as you appear to have done from trusty to xenial, and are supposed to be automatically disabled if you do not remove them manually.  However, sometimes the automatic disabling does not happen, which seems to be the case here.

---

### Post by jgw on 2016-11-04
I solved the problem.  This was part of my attempt to install mate over unity and I absolutely failed.  This being the case (the problems just kept coming) I decided to simply do a clean install of ubuntu mate which made this, for me, no longer pertinent.

I want to thank all those who replied and apologize to you for this whole thing.  I should have done this in the first place.  Thanks again!

---

### Post by ajgreeny on 2016-11-04
No problem!

If the update problem had been the only one we could quite easily have solved it but as you have now already taken more drastic action that is now a problem overcome.

Thanks for marking as solved. Even though this was really not a solution to your problem it may give a warning to others about multiple DEs on a single OS; some will sit happily side by side but some other combinations can cause problems.

---

