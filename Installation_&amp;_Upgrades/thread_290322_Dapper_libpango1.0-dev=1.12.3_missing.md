---
title: "Dapper: libpango1.0-dev=1.12.3 missing"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by mlavikai on 2006-11-01
I have been trying to get gnucash 2 working, and by following threads here in Ubuntuforums, it seems that the package libpango1.0-dev (= 1.12.3-0ubuntu3) is missing from Dapper repository. 

However libpango-1.0 (= 1.12.3-0ubuntu3) exists and is installed in my computer. Is this a bug in repository, or what should I try to do? :confused: 

'Marko

---

### Post by mlavikai on 2006-11-01
Update: 

I checked from packages.ubuntu.com and it seems that Dapper has the libpango1.0 version 1.12.2. However my synaptics shows that there is a version 1.12.3 and that is installed. By checking the package version history I get following information:

```
1.12.13-0ubuntu3 (Now)
1.12.12-0ubuntu3 (Dapper)
```

So, it might seem that that package is from somewhere else. My current sources list is as follows:

```
deb http://fi.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# deb http://fi.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
# deb http://fi.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://fi.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://fi.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://fi.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://fi.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fi.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://fi.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
#deb http://xgl.compiz.info/ dapper main
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
```

Is there a way to find out, where that (libpango-1.0=1.12.3) package is coming from?

---

### Post by mlavikai on 2006-11-01
This is rather strange. I finally managed to compile gnucash 2.0.2, but it required an installation of many development packages. However what I noticed that there were quite many binary packages where the version was higher than the corresponding dev-package. And I have no idea, how this unsynchronization has happened. Basically, solving libpango needed that I manually downloaded dev-package from 

[http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-dev_1.12.3-0ubuntu3_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-dev_1.12.3-0ubuntu3_i386.deb")

and installed it. I will put some notes about gnucash 2.0.2 in thread

[http://www.ubuntuforums.org/showthread.php?p=1620404]("http://www.ubuntuforums.org/showthread.php?p=1620404")

However, does anyone have any idea, why the binary packages are higher than dev-packages?

---

