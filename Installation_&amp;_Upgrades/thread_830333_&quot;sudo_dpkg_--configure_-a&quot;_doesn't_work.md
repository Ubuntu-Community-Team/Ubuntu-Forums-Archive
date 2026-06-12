---
title: "&quot;sudo dpkg --configure -a&quot; doesn't work"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by chrisbenson on 2008-06-15
I upgraded my Ubuntu Server from 7.10 to 8.04, and a lot of my packages seemed to stop working.  When I try to do anything with either apt-get or aptitude, I get errors which end up with:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I run "sudo dpkg --configure -a", I get this error over and over with different package names (which I've consolidated to <PACKAGE> to keep this post brief:

dpkg: error processing <PACKAGE> (--configure):
 subprocess post-installation script returned error exit status 139
Setting up <PACKAGE> (1:3.2.7-5ubuntu2) ...
Segmentation fault

I also get errors like this:

dpkg: dependency problems prevent configuration of <PACKAGE1>:
 <PACKAGE1> depends on <PACKAGE2>; however:
  <PACKAGE2> is not configured yet.
 <PACKAGE2> depends on <PACKAGE3> (>= 117-5); however:
  Package <PACKAGE3> is not configured yet.

Any ideas?  It seems like the distribution upgrade ruined the dependencies on my system.  Is there any way to make it recreate them, assuming that this is my problem?

Thanks,
Chris

---

### Post by bapoumba on 2008-06-15
We can start with your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by Pumalite on 2008-06-15
This might help:
[http://ubuntuforums.org/showthread.php?t=780531](http://ubuntuforums.org/showthread.php?t=780531)
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

### Post by chrisbenson on 2008-06-15
> **bapoumba said:**
> We can start with your sources.list:
```
cat /etc/apt/sources.list
```
Here at my sources:

chris@chrisbenson:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
chris@chrisbenson:~$

---

### Post by bapoumba on 2008-06-15
Your sources.list is fine. Did anything go wrong during your dist-upgrade?
Did you check the links Pumalite posted?

---

### Post by chrisbenson on 2008-06-15
> **bapoumba said:**
> Your sources.list is fine. Did anything go wrong during your dist-upgrade?
Did you check the links Pumalite posted?
From the first link that Pumalite sent, I tried "dpkg --configure -a --force-all"

It went on for a while, and finished with this:

Errors were encountered while processing:
 module-init-tools
 procps
 wpasupplicant
 vim-common
 netbase
 rsync
 hdparm
 groff-base
 openssh-server
 mime-support
 cron
 apparmor
 less
 sysklogd
 klogd
 mysql-server-5.0
 apache2.2-common
 udev
 bind9
 pcmciautils
 console-setup
 ufw
 alsa-utils
 postfix
 dovecot-common
 
 I tried apt-get afterwards, and it still indicates dpkg errors.

---

