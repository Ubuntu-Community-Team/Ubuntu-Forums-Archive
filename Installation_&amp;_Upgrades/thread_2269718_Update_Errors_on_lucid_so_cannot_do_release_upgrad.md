---
title: "Update Errors on lucid so cannot do release upgrade"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by britesc on 2015-03-17
Hi,
Before I can upgrade to precis from lucid server I need to get some updates fixed.
All I get is a string of errors.

My sources.list is

> #
# deb cdrom:[Ubuntu-Server 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2)]/ lucid main restricted


#deb cdrom:[Ubuntu-Server 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse


## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse 

The errors are:

> apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  apport landscape-common language-selector-common lsb-release python-apport python-httplib2 python-lazr.restfulclient python-openssl python-pam python-problem-report
  python-wadllib update-manager-core
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0B/1,230kB of archives.
After this operation, 254kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 43390 files and directories currently installed.)
Preparing to replace lsb-release 4.0-0ubuntu8 (using .../lsb-release_4.0-0ubuntu8.1_all.deb) ...
Segmentation fault
dpkg: warning: old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/lsb-release_4.0-0ubuntu8.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139

etc...

I have tried apt-get -f install  ...clean ...autoremove ...purge etc... but still the same errors, I have also tried with aptitude.

As I really need to upgrade this server asap is there please some genius that can advise me how to proceed. Thank you.

Kind regards,

jB

---

### Post by ian-weisser on 2015-03-17
> Preparing to replace lsb-release 4.0-0ubuntu8 (using .../lsb-release_4.0-0ubuntu8.1_all.deb) ...
Segmentation fault
dpkg: warning: old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault
dpkg: error processing /var/cache/apt/archives/lsb-release_4.0-0ubuntu8.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
Segmentation fault
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 139

Let's look a bit more closely at that set of errors.
Seems like dpkg was trying to remove lsb-release so it could install the newer version, but the pre-removal script failed.
So dpkg thought 'well, I'll just try the pre-removal script in the newer package instead', which is really quite clever of it...too bad it failed too.
Subsequent lines are just the error causing loops to terminate, each echoing their own warnings.

I think the first thing you should look at is that pre-removal script.
It's at /var/lib/dpkg/info/lsb-release.prerm 
Can you show us that script?

---

### Post by britesc on 2015-03-19
Hi Ian,

Thanks for the reply.
I have done a bit more digging and it seems there are a number of bugs in the script, which is no longer maintained.
Apparently the solution is to insert a CD of 12.04 and upgrade that way.
I will give that a try as soon as I can and report back if it proves viable.

Kind regards,

jB :cool:

---

### Post by ian-weisser on 2015-03-19
What script?
A CD probably won't help with a segmentation fault.

Upgrading a 5-year-old system to a 3-year-system with this kind of problem may be more trouble than it's worth.
Have you considered backing up your data and rebuilding your server on a fresh install of 14.04?

---

