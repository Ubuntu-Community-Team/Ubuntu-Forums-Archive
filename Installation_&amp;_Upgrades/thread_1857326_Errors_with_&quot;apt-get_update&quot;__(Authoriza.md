---
title: "Errors with &quot;apt-get update&quot;  (Authorization Required)"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by kgocuser on 2011-10-10
Hi,
 
I have just installed Ubuntu 11.04. When I issue the following command:
 
" sudo apt-get update"
 
I get the following errors:
 
 
>  
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security InRelease
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty InRelease
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates InRelease
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security Release
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty Release
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main TranslationIndex
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates Release
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe TranslationIndex
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main Sources
401 Authorization Required [IP: 91.189.92.171 80]
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted Sources
401 Authorization Required [IP: 91.189.92.171 80]
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe Sources
401 Authorization Required [IP: 91.189.92.171 80]
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse Sources
401 Authorization Required [IP: 91.189.92.171 80]
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main amd64 Packages
401 Authorization Required [IP: 91.189.92.171 80]
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted amd64 Packages
401 Authorization Required [IP: 91.189.92.171 80]
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe amd64 Packages
401 Authorization Required [IP: 91.189.92.171 80]
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse amd64 Packages
401 Authorization Required [IP: 91.189.92.167 80]
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe Translation-en
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main Sources
401 Authorization Required [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted Sources
401 Authorization Required [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe Sources
401 Authorization Required [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse Sources
401 Authorization Required [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main amd64 Packages
401 Authorization Required [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted amd64 Packages
401 Authorization Required [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe amd64 Packages
401 Authorization Required [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse amd64 Packages
401 Authorization Required [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main Sources
401 Authorization Required [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted Sources
401 Authorization Required [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe Sources
401 Authorization Required [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse Sources
401 Authorization Required [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main amd64 Packages
401 Authorization Required [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted amd64 Packages
401 Authorization Required [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe amd64 Packages
401 Authorization Required [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse amd64 Packages
401 Authorization Required [IP: 91.189.88.31 80]
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe Translation-en

 
 
I am not able to figure out the reason for the "Authorization Required" issue,
any help is deeply appreciated
 
 
The content of /etc/apt/sources.list is as follows:
 
[QUOTE] 
#
# deb cdrom:[Ubuntu-Server 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted
#deb cdrom:[Ubuntu-Server 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
 
QUOTE]

---

### Post by raja.genupula on 2011-10-10
Do this.

Open Update Manager->settings->in the first tab choose another server and then try to do update again.

All The best.

---

### Post by kgocuser on 2011-10-10
Hi Raj,
 
Thanks a lot for your reply.
 
I figured out the issue. The problem was that we have a proxy setup in our
site, so what i did is to ask the administrator to let the Unix server bypass the
proxy. Once that was done, things worked perfectly.
 
Thanks again

---

### Post by raja.genupula on 2011-10-10
Hi 
I am glad that you have solved your issue .could you please mark your thread as solved from thread tools.


Enjoy the Ubuntu.

---

