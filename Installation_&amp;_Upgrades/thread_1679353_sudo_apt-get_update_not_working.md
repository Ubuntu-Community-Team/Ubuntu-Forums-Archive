---
title: "sudo apt-get update not working"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Global Operator on 2011-01-31
Hi there,
 
I was wondering if someone could please help with the follwing issue: I am unable to run **sudo apt-get update** and **sudo apt-get upgrade** it used to work fine. I noticed this was a problem when I tried to install *htop* on all systems 2 worked, one didn't and it now has me stummped
 
Under /etc/apt/ there's a file called sources.conf
 
I believe mine has become corrupted / started not working as of today
 
Below is the code in my sources.conf 
 
```
# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted
#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

```
 
I run Ubuntu 10.10 on all 3 systems in the same network this is the only one that has this issue. 


I tried to touble shoot it by copying the sources.conf from another ubuntu 10.10 computer and had no luck with it I keep getting this error.
 
```

[EMAIL="administrator@ubuntu2:~$"]administrator@ubuntu2:~$[/EMAIL] sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en
  Temporary failure resolving 'security.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
  Temporary failure resolving 'security.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en
  Temporary failure resolving 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
  Temporary failure resolving 'au.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en.bz2)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en.bz2)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en.bz2)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en.bz2)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_AU.bz2)  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
[EMAIL="administrator@ubuntu2:~$"]administrator@ubuntu2:~$[/EMAIL]

```
 
if the file above is not correct can someone please past the correct code in so I can modify mine or if possible can someone help me trouble shoot this a little? :KS
 
many thanks for your help.
 
Global Operator.

---

### Post by papibe on 2011-01-31
The server that translate names like  [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) into an actual IP direction (Domain Name Server), is either down or unresponsive.

Most certainly will be back in a few hours. If you really have to update or install something, you can change the main source server for one that is up and running, and closer to you (in terms of response time). In order to do that, take a look at the section "Download Server" on this [page]("https://help.ubuntu.com/community/Repositories/Ubuntu") (Other -> Best Server). 

It takes a while to determine which one is the better (a few minutes), but it's totally worth it.

Good Luck!

---

