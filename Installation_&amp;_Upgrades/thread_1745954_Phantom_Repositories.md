---
title: "Phantom Repositories?"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by klausner on 2011-05-01
I thought that the list of repositories shown in Synaptic->Repositories->Other reflected the content on */etc/apt/sources.lst*. But mine don't match at all! Some things I've added via SYnaptic don't show up there, but do appear in *sources.lst*.

Here's what I see:
```
~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://packages.medibuntu.org/ lucid free non-free #medibuntu
deb http://archive.getdeb.net/ubuntu lucid-getdeb apps #getdeb
deb http://deb.opera.com/opera/ stable non-free #opera
deb http://archive.ubuntu.com/ubuntu lucid-backports main universe multiverse restricted

```
and

[IMG]http://farm6.static.flickr.com/5301/5676351692_6ae2c524e9_z.jpg[/IMG]

Aren't they supposed to be in sync?

P.S. This is in lucid.

---

### Post by oldos2er on 2011-05-01
Additional repositories may be installed in /etc/apt/sources.list.d/

---

### Post by klausner on 2011-05-01
> **oldos2er said:**
> Additional repositories may be installed in /etc/apt/sources.list.d/

Thanks. But that doesn't explain why things don't show up in Synaptic or Software Sources.

---

### Post by plucky on 2011-05-01
> **klausner said:**
> Thanks. But that doesn't explain why things don't show up in Synaptic or Software Sources.

Please define **things**.

Post output of ```
ls -l /etc/apt/sources.list.d/
``` please.

---

### Post by klausner on 2011-05-01
> **plucky said:**
> Please define **things**.

Post output of ```
ls -l /etc/apt/sources.list.d/
``` please.

```
~$ ls -l /etc/apt/sources.list.d/
total 16
-rw-r--r-- 1 root root 75 2011-05-01 08:52 tualatrix-ppa-lucid.list
-rw-r--r-- 1 root root 72 2011-05-01 08:52 tualatrix-ppa-lucid.list.save
-rw-r--r-- 1 root root 79 2011-05-01 08:52 ubuntu-x-swat-x-updates-lucid.list
-rw-r--r-- 1 root root 79 2011-05-01 08:52 ubuntu-x-swat-x-updates-lucid.list.save
```

---

