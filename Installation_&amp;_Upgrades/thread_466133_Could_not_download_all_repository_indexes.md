---
title: "Could not download all repository indexes"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by kmangwing on 2007-06-06
Ok, I've tried to update my system a couple of times now.  I'm connected to the internet without any problems, and I've had no problems updating in the past.  But whenever I check for updates, i get the message "Could not download all repository indexes"
Then I get a list,

ttp://packages.freecontrib.org/ubuntu/plf/dists/feisty/free/binary-i386/Packages.gz: 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/feistyt/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feistyt/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/feistyt/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feistyt/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/feistyt/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feistyt/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/feistyt/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feistyt/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://packages.freecontrib.org/ubuntu/plf/dists/feisty/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/feisty/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/feisty/free/source/Sources.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/feisty/free/source/Sources.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/feisty/non-free/source/Sources.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/feisty/non-free/source/Sources.gz:) 404 Not Found


Are some of the repositories down or something?

---

### Post by wpshooter on 2007-06-06
I would suggest going into software sources and make sure that everything that you want is checked and then reload/refresh when you exit.  I would then reboot and then see if you can download what you need.

Good luck.

---

### Post by kmangwing on 2007-06-06
I went into the sources list earlier to make sure everything was ok, and I rebooted.  When nothing changed, I rebooted again.  I still haven't been able to get it to work.

---

### Post by zvacet on 2007-06-07
You need to replace plf with medibuntu.See page

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by kmangwing on 2007-06-07
> **zvacet said:**
> You need to replace plf with medibuntu.See page

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

Thanks, I'll give that a try right now

---

### Post by kmangwing on 2007-06-07
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/ffeisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/ffeisty-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feistyt/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feistyt/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feistyt/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feistyt/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feistyt/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feistyt/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feistyt/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feistyt/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Do you guys want me to maybe paste in my sources.list file?

If don't particularly mind reinstalling ubuntu, I've done it almost 3 times.

---

### Post by zvacet on 2007-06-08
```
cat /etc/apt/sources.list
```

and post it here.Why didn´t you use source list i recommended to you?That is exact source list i use.Any way post your source list and we will see what to do next.

---

### Post by kmangwing on 2007-06-08
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feistyt main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

#deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
#deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

#deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) feisty free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) feisty free non-free

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) ffeisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main

---

### Post by arnieboy on 2007-06-08
> **kmangwing said:**
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feistyt main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

#deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
#deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

#deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) feisty free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) feisty free non-free

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) ffeisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
There are a ton of typos in your sources.list.
just delete the following lines from your ***/etc/apt/sources.list*** (they are just ABOVE "**#AUTOMATIX REPOS START**":)
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) ffeisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

Also change the following line at the top of the same file from:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feistyt main restricted universe multiverse
to
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
Save and close the file and a :
```
sudo apt-get update

```

---

### Post by kmangwing on 2007-06-09
I don't remember those typos, and I hadn't really changed anything in the list
But I'm glad you figured it out.  I feel like an idiot, but I'll give it a try.

---

### Post by kmangwing on 2007-06-09
Well, I tried it, and it worked without any problems
Thanks a lot man. I owe you.  I knew there was a reason I switched to Ubuntu.

---

### Post by ricardisimo on 2007-06-30
I'm also getting 404 errors:
```
Could not download all repository indexes... (blahblahblah...) http://kubuntu.org/packages/koffice-latest/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found
http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found
```
Both of the above came from Source-O-Matic, however, so I doubt typos are to blame here. Anyone know if there's an issue with these repos? Thanks in advance for any help. My sources.list below...
```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://seveas.theplayboymansion.net/seveas feisty-seveas all 

# Ubuntu backports project
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 

# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb http://kubuntu.org/packages/kde-latest feisty main 

# Kubuntu.org bleeding edge Koffice
# GPG key: DD4D5088
deb http://kubuntu.org/packages/koffice-latest feisty main 

# Kubuntu.org bleeding edge amaroK
# GPG key: DD4D5088
deb http://kubuntu.org/packages/amarok-latest feisty main 

# Upstream Wine
# GPG key: 387EE263
deb http://wine.budgetdedicated.com/apt feisty main 

# Upstream Opera
# GPG key: 6A423791
deb http://deb.opera.com/opera etch non-free 

# Upstream Beryl
# GPG key: ed8a569e
deb http://media.blutkind.org/xgl/ edgy main-edgy 

# Medibuntu multimedia packages
# GPG key: 0C5A2783
#deb http://medibuntu.sos-sts.com/repo/ feisty free non-free 
deb http://packages.medibuntu.org/ feisty free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com feisty-commercial main 

```

---

### Post by ricardisimo on 2007-07-04
Should I not even be worried about this? My assumption is that Amarok and KOffice elements will never update if I don't fix it. Am I wrong in this? Thanks again.

---

### Post by ricardisimo on 2007-07-05
Let me try putting this another way: Let's say that I have no errors in typing nor in syntax (which is a good guess, since my sources.list comes direct from Source-O-Matic). Is it safe to assume that the problem is with the Amarok and Koffice repositories themselves, and not with me?

---

### Post by NeoLithium on 2007-07-05
Yep. A good way to check is to follow the repo link and see if they sometimes change the directories of the repositories.  However, Ubuntu keeps Amarok and koffice pretty up to date, so it's not too much to worry about, really.  I've had well over a dozen 404 errors over time, sometimes they just close down sections of repos or move directories and it causes a few issues here and there.

---

### Post by ab525 on 2007-07-06
I'm having the same problem, and I don't really want to ignore it, because the repositories sound pretty important.  Here's what I'm getting:

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz: 302 Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz: 302 Found
http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz: 302 Found
http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz: 302 Found
http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz: 302 Found [IP: 91.189.89.6 80]
http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz: 302 Found [IP: 208.113.193.9 80]

```

Here's my sources list:

```
$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ubuntu.beryl-project.org edgy main
```

I'm sorry if this is a particularly inane question, but we all have to learn somehow.

---

### Post by etxabier on 2007-09-27
**This is probably going to annoy a few, but i don't know much about Ubuntu as yet.  I noticed this error when i tried to install a codec to watch AVI files.**

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/main/binary-i386/Packages.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/restricted/binary-i386/Packages.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/main/source/Sources.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/restricted/source/Sources.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/multiverse/binary-i386/Packages.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/universe/binary-i386/Packages.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-updates/main/binary-i386/Packages.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-updates/main/source/Sources.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-updates/restricted/source/Sources.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-security/main/binary-i386/Packages.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-security/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-security/main/source/Sources.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-security/main/source/Sources.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-security/restricted/source/Sources.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/feisty-security/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/fiesty/main/binary-i386/Packages.gz:](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz/dists/fiesty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]

**Did i do something wrong at installation?  here is my source list:**


deb [http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) feisty main restricted
deb-src [http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) feisty-updates main restricted
deb-src [http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://bz.archive.ubuntu.com/ubuntu/](http://bz.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://bz.archive.ubuntu.com/ubuntu/](http://bz.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bz.archive.ubuntu.com/ubuntu/](http://bz.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://bz.archive.ubuntu.com/ubuntu/](http://bz.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) feisty-security main restricted
deb-src [http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty main
deb [http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://bz.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) fiesty main

My system is very stable, but i don't like seeing errors...it annoys me:P  Thanks for you help.

etxabier

---

