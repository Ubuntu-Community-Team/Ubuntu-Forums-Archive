---
title: "Update FAIL"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by Antihero20 on 2010-05-31
I try to run the **sudo apt-get update** and I keep getting this errors> Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Sources
  Unable to connect to archive.getdeb.net:http:
Fetched 11.5kB in 45s (255B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/source/Sources.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/source/Sources.gz)  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.

Then I've tried in the Synaptic Package Manager to "reload" but I get a message that says
*Could not download all repository indexes*
and I also get this along with it
> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DEGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24CFailed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/source/Sources.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/source/Sources.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.

I'm running Ubuntu 10.04
Help :(

---

### Post by Elfy on 2010-05-31
```
gpg --keyserver keyserver.ubuntu.com --recv 574DEGPG
gpg --export --armor 574DEGPG  | sudo apt-key add -
```

should deal with the GPG error.

Looks like getdeb is down at the moment - if you want to stop using that for the moment - comment out the getdeb ppa - it will be in /etc/apt/sources.list.d - open the getdeb ppa and put # at the beginning of the line then update again.

---

### Post by crash123 on 2010-05-31
Thanks, forestpiskie: I was just about to post the same question, but you've answered it already.

---

### Post by Antihero20 on 2010-05-31
I get this
> gpg: "574DEGPG" not a key ID: skipping


gpg: WARNING: nothing exported

---

### Post by Antihero20 on 2010-06-06
I still can't update nothing
I don't know, Maybe its something in my source.list
here it is
> # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
## Major bug fix updates produced after the final release of the
## distribution.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) lucid main
deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) lucid main

---

