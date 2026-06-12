---
title: "apt-get is not working anymore - The repository 'http://at.archive.ubuntu.com/ubuntu"
date: 2018-01-27
forum: Installation &amp; Upgrades
---

### Post by fux.ey on 2018-01-27
Hi,

i want to install libssl-dev, but my apt-get system is not working correctly anymore.  
when i try to apt-get update i get the following:

> W: The repository 'http://at.archive.ubuntu.com/ubuntu zesty Release' does not have a Release file.N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.N: See apt-secure(8) manpage for repository creation and user configuration details.W: The repository 'http://at.archive.ubuntu.com/ubuntu zesty-updates Release' does not have a Release file.N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.N: See apt-secure(8) manpage for repository creation and user configuration details.W: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does not have a Release file.N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.N: See apt-secure(8) manpage for repository creation and user configuration details.W: The repository 'http://at.archive.ubuntu.com/ubuntu zesty-backports Release' does not have a Release file.N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.N: See apt-secure(8) manpage for repository creation and user configuration details.W: GPG-Fehler: [https://repos.influxdata.com/debian](https://repos.influxdata.com/debian) jessie InRelease: Die folgenden Signaturen konnten nicht überprüft werden, weil ihr öffentlicher Schlüssel nicht verfügbar ist: NO_PUBKEY 684A14CF2582E0C5W: The repository 'https://repos.influxdata.com/debian jessie InRelease' is not signed.N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.N: See apt-secure(8) manpage for repository creation and user configuration details.E: Fehlschlag beim Holen von [http://at.archive.ubuntu.com/ubuntu/dists/zesty/main/binary-i386/Packages](http://at.archive.ubuntu.com/ubuntu/dists/zesty/main/binary-i386/Packages)  404  Not FoundE: Fehlschlag beim Holen von [http://at.archive.ubuntu.com/ubuntu/dists/zesty-updates/main/binary-i386/Packages](http://at.archive.ubuntu.com/ubuntu/dists/zesty-updates/main/binary-i386/Packages)  404  Not FoundE: Fehlschlag beim Holen von [http://security.ubuntu.com/ubuntu/dists/zesty-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/zesty-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.161 80]E: Fehlschlag beim Holen von [http://at.archive.ubuntu.com/ubuntu/dists/zesty-backports/main/binary-amd64/Packages](http://at.archive.ubuntu.com/ubuntu/dists/zesty-backports/main/binary-amd64/Packages)  404  Not FoundE: Einige Indexdateien konnten nicht heruntergeladen werden. Sie wurden ignoriert oder alte an ihrer Stelle benutzt.


i i had a look at /ect/apt/sources.list, but seems ok to me:

> #deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty main restricted
# deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty-updates main restricted
# deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty universe
# deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty universe
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty-updates universe
# deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty multiverse
# deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty multiverse
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty-updates multiverse
# deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse
# deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse


i also tried to do this:
sudo rm /var/lib/apt/lists/*
sudo rm /var/cache/apt/*.bin


is there a possibility to completeely reset apt-get ? i have no idea how to fix. 
thanks!

---

### Post by cruzer001 on 2018-01-27
17.04 has reached end of life and the regular software sources are gone.  You need to do an EOL upgrade.

[https://ubuntuforums.org/showthread.php?t=2382832](https://ubuntuforums.org/showthread.php?t=2382832)

---

### Post by Impavidus on 2018-01-28
+1

And next time don't miss the 3 month upgrade window. Or stick to LTS releases.

Instead of an upgrade, you can also try a fresh install. In my experience release upgrades always work, but that's not the case for everyone.

---

