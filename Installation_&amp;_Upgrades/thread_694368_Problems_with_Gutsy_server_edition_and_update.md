---
title: "Problems with Gutsy server edition and update"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by FunkyFrank on 2008-02-12
Hi all,

I've gone through a lot of posts and found similar problems, but wasn't able so far to resolve my problem.
I have to say I'm fairly new to Linux, have been using Gutsy desktop edition for a while now.
I installed Gutsy server edition fresh on an old machine, and I have network connectivity, can ping other machines on the lan and also on the Internet.

However, the moment I try to do 
sudo apt-get update
I run into problems

My original sources.list looks like this:
> # 
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


With this I am running into problems where the machine hangs with the message:
Waiting for headers
I tried different repositories, to no avail.

Then I read this might be a bug in the http request in Ubuntu, and other ppl have switched to ftp rahter than http. Ok, so I modified my sources.list to this:

> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy main restricted
deb-src [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy-updates main restricted
deb-src [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy universe
deb-src [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy universe
deb [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy-updates universe
deb-src [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy multiverse
deb-src [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy multiverse
deb [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy-updates multiverse
deb-src [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [ftp://mirror.pacific.net.au/ubuntu/](ftp://mirror.pacific.net.au/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) gutsy-security universe
deb [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) gutsy-security multiverse


As you can see, I also changed the au.ubuntu... to another mirror.  Also tried the original au.ubuntu mirrors with ftp, but with all the ftp stuff I run into these problems:
> 
Get:1 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security Release.gpg [191B]                                
Get:2 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security/main Translation-en_AU
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security/main Translation-en_AU
Get:3 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security/restricted Translation-en_AU
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security/restricted Translation-en_AU                                                                     
Get:4 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security/universe Translation-en_AU                                                                     
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security/universe Translation-en_AU                                                                       
Get:5 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security/multiverse Translation-en_AU                                                                   
Ign [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security/multiverse Translation-en_AU                                                                     
Get:6 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) gutsy-security Release [51.2kB]                       


Also get timeouts and errors.

So I'm pretty stuck here, how do I get this box to upgrade?

Thanks for any help
Frank

---

