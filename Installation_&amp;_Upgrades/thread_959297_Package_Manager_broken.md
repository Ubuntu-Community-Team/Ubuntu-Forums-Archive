---
title: "Package Manager broken"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by Robotman on 2008-10-26
I have Ubuntu 8.04 on an HP 2133 Mini Note.  I hadn't updated for a few weeks, and recently downloaded the 55 updates available using Update Manager.  Things went badly though, as I can only get my wireless to work when booting into the "19" version of the kernel and I can't seem to use either Update Manager or Synaptic Package Manager.
Here's the error message I get in Update Manager:
```
Could not initialize the package information

An unresolvable problem occurred while initializing the
package information.

Please report this bug against the 'update-manager' package
and include the following error message:

'E:Encountered a section with no Package:header, E:Problem
with MergeList /var/lib/dpkg/status, E:The package lists or
status file could not be parsed or opened.'
```
Trying to run Synaptic gives the above 'E:' error messages plus one more:
```
E:_cache->open() failed, please report.
```
Does anybody know what I can do to fix this?

---

### Post by Kevbert on 2008-10-26
In terminal, try 
```
sudo apt-get check
sudo apt-get update
```
Please post your sources.list if this doesn't help.

---

### Post by Robotman on 2008-10-26
Sadly both those commands yeild the same 3 'E:' error messages I posted above. :(
Here's my sources.list:
```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

EDIT: Also, I can't seem to open the /var/lib/dpkg/status file with gedit, I get an error stating that gedit can not detect the character coding.

---

### Post by Kevbert on 2008-10-26
Sources.list seems fine.
Had a hunt on the web and found this...
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```

---

### Post by Robotman on 2008-10-26
Thanks for that Kevbert... Update-Manager will run again.  I can install everything but a Java update, which gives this error message:
```
E: /var/cache/archives/sun-java6-bin_6-07-3ubuntu2_1386.deb:
corrupted filesystem tarfile - corrupted package archive
```
I can also use Synaptic to try and fix the 3 broken packages I'm told I still have.
I'm guessing the corrupted package is on the Canadian repository I have in my sources.list.  Is that correct?

---

### Post by Kevbert on 2008-10-26
The java package you can remove with
```
sudo rm /var/cache/apt/archives/sun-java6-bin_6-07-3ubuntu2_1386.deb
```
Make sure that you type this in as shown above as 'rm' is a [COLOR="Red"]dangerous command[/COLOR] that can easily damage your file system if typed in wrongly.  It may be worth trying a different source for that file (I've had problems with the repos in the past, so just try changing the software source server).

---

