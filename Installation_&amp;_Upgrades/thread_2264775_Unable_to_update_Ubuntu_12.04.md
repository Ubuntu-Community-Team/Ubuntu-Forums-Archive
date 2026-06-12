---
title: "Unable to update Ubuntu 12.04"
date: 2015-02-10
forum: Installation &amp; Upgrades
---

### Post by olivier12 on 2015-02-10
I am unable to update my current version of Ubuntu. Here is the output of sudo apt-get update:

```
Err http://archive.canonical.com precise Release.gpg
  Could not connect to archive.canonical.com:80 (91.189.92.191). - connect (111: Connection refused) [IP: 91.189.92.191 80]
Err http://archive.ubuntu.com precise Release.gpg             
  Could not connect to archive.ubuntu.com:80 (91.189.91.15). - connect (111: Connection refused) [IP: 91.189.91.15 80]
Err http://archive.ubuntu.com precise-updates Release.gpg     
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.15 80]
Err http://archive.ubuntu.com precise-backports Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.15 80]
Err http://archive.ubuntu.com precise-security Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.15 80]
Err http://archive.ubuntu.com precise-proposed Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.15 80]
Reading package lists... Done                        
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.91.15). - connect (111: Connection refused) [IP: 91.189.91.15 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.15 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.15 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.15 80]

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.92.191). - connect (111: Connection refused) [IP: 91.189.92.191 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.91.15 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

Here is the content of /etc/apt/sources.list:

```
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe

deb http://archive.ubuntu.com/ubuntu precise-security main restricted universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main universe
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

My /etc/apt/sources.list.d/ directory is empy.
Is there anyway I can update Ubuntu without going throug the CD installation

---

### Post by Karlchen on 2015-02-10
Hello, Olivier12.

The sources.list file looks all right to me.
Has this error when trying to update the local list of available software ocurred only once? Or is this an ongoing problem? When did you first encounter the problem?

Cheers,
Karl
--
P.S.:
I doubt that the root cause will be so bad that it will require re-installing.

---

