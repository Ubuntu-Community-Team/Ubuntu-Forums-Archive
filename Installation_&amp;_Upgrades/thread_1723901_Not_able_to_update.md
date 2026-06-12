---
title: "Not able to update"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by wfiskum on 2011-04-07
I have installed Ubuntu Server 10.10 Here are the contents of the sources.list file:


# 
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://us.extras.ubuntu.com/ubuntu](http://us.extras.ubuntu.com/ubuntu) maverick main
deb-src [http://us.extras.ubuntu.com/ubuntu](http://us.extras.ubuntu.com/ubuntu) maverick main
## deb [http://us.extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/](http://us.extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/)

deb [http://us.security.ubuntu.com/ubuntu](http://us.security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://us.security.ubuntu.com/ubuntu](http://us.security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://us.security.ubuntu.com/ubuntu](http://us.security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://us.security.ubuntu.com/ubuntu](http://us.security.ubuntu.com/ubuntu) maverick-security universe
deb [http://us.security.ubuntu.com/ubuntu](http://us.security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://us.security.ubuntu.com/ubuntu](http://us.security.ubuntu.com/ubuntu) maverick-security multiverse

but when I do the command "sudo apt-get update" I get this error:
Ubuntu 10.10
  root@elmo:/sbin# sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
  Temporary failure resolving 'archive.canonical.com'
Err [http://us.extras.ubuntu.com](http://us.extras.ubuntu.com) maverick Release.gpg
  Temporary failure resolving 'us.extras.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://us.security.ubuntu.com](http://us.security.ubuntu.com) maverick-security Release.gpg
  Temporary failure resolving 'us.security.ubuntu.com'
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
  Temporary failure resolving 'archive.canonical.com'
Err [http://us.extras.ubuntu.com/ubuntu/](http://us.extras.ubuntu.com/ubuntu/) maverick/main Translation-en
  Temporary failure resolving 'us.extras.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
  Temporary failure resolving 'archive.canonical.com'
Err [http://us.security.ubuntu.com/ubuntu/](http://us.security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Temporary failure resolving 'us.security.ubuntu.com'
Err [http://us.extras.ubuntu.com/ubuntu/](http://us.extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
  Temporary failure resolving 'us.extras.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://us.security.ubuntu.com/ubuntu/](http://us.security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
  Temporary failure resolving 'us.security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://us.security.ubuntu.com/ubuntu/](http://us.security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Temporary failure resolving 'us.security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://us.security.ubuntu.com/ubuntu/](http://us.security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
  Temporary failure resolving 'us.security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.security.ubuntu.com/ubuntu/](http://us.security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Temporary failure resolving 'us.security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.security.ubuntu.com/ubuntu/](http://us.security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
  Temporary failure resolving 'us.security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.security.ubuntu.com/ubuntu/](http://us.security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Temporary failure resolving 'us.security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.security.ubuntu.com/ubuntu/](http://us.security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
  Temporary failure resolving 'us.security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Temporary failure resolving 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Temporary failure resolving 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Temporary failure resolving 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Temporary failure resolving 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2)  Temporary failure resolving 'archive.canonical.com'

W: Failed to fetch [http://us.extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Temporary failure resolving 'us.extras.ubuntu.com'

W: Failed to fetch [http://us.extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://us.extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Temporary failure resolving 'us.extras.ubuntu.com'

W: Failed to fetch [http://us.extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://us.extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.extras.ubuntu.com'

W: Failed to fetch [http://us.security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://us.security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Temporary failure resolving 'us.security.ubuntu.com'

W: Failed to fetch [http://us.security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://us.security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Temporary failure resolving 'us.security.ubuntu.com'

W: Failed to fetch [http://us.security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2](http://us.security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.security.ubuntu.com'

W: Failed to fetch [http://us.security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://us.security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Temporary failure resolving 'us.security.ubuntu.com'

W: Failed to fetch [http://us.security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://us.security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.security.ubuntu.com'

W: Failed to fetch [http://us.security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://us.security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Temporary failure resolving 'us.security.ubuntu.com'

W: Failed to fetch [http://us.security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://us.security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.security.ubuntu.com'

W: Failed to fetch [http://us.security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://us.security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Temporary failure resolving 'us.security.ubuntu.com'

W: Failed to fetch [http://us.security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://us.security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
root@elmo:/sbin#
  
I edited have tried the same after removing the us. from the http fields as well, but that gets the same error. 
Any ideas on how i can correct the problem?
Thanks.

---

### Post by Wobblybob on 2011-04-07
you could try downloading from a different server, [Synaptic Package Manager], [Settings], [Repositories] [Ubuntu Software] tab change the server then retry.

---

### Post by wfiskum on 2011-04-08
Hi WobblyBob, thanks for trying.  I found the problem though, actually it was a combination of things:
1. I edited the sources.list file and removed all of the us. from the repositories.
2. I looked at my DNS settings (/etc/resolv.conf) and found a problem.  Seems I hadn't entered the correct IP address for my DNS server, so I fixed that using VI then restarted the network using the command:
sudo /etc/init.d/networking restart          

I was able to get the updates then and away I went.

Thanks!:D

---

