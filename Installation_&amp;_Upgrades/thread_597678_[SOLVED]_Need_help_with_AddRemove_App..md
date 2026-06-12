---
title: "[SOLVED] Need help with Add/Remove App."
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by grendel2110 on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=581975](http://ubuntuforums.org/showthread.php?t=581975) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There was an almost identical thread about this before, but I wasn't able to extract any help from it. [http://ubuntuforums.org/showthread.php?t=581975](http://ubuntuforums.org/showthread.php?t=581975)

Basically, whenever I try to install anything with Add/Remove Apps., it tells me that I'm not connected to the internet and that I need to reload (this happens whenever I try to select a package to install). On the previous thread discussing this, someone mentioned that the installer (I recently upgraded to gutsy) may have reset the apt-sources. However, when I run 

cat /etc/apt/sources.lst

as that person suggested, I only get 'no such file or directory.'

Anyone know what else I can do/why that command doesn't work?

---

### Post by taurus on 2007-10-30
What's the output of this command from a terminal?

```
ls -la /etc/apt
```

---

### Post by grendel2110 on 2007-10-30
Results of ls -la /etc/apt:

total 36
drwxr-xr-x   4 root root 4096 2007-10-30 04:25 .
drwxr-xr-x 111 root root 4096 2007-10-30 15:28 ..
drwxr-xr-x   2 root root 4096 2007-10-30 04:26 apt.conf.d
-rw-------   1 root root    0 2007-10-15 16:18 secring.gpg
-rw-r--r--   1 root root 4202 2007-10-30 04:22 sources.list
drwxr-xr-x   2 root root 4096 2007-10-15 13:40 sources.list.d
-rw-------   1 root root 1200 2007-10-15 16:18 trustdb.gpg
-rw-r--r--   1 root root 2393 2007-10-15 16:18 trusted.gpg
-rw-r--r--   1 root root 2381 2007-10-15 16:18 trusted.gpg~

Thanks,
Ian

---

### Post by taurus on 2007-10-30
> **grendel2110 said:**
> Results of ls -la /etc/apt:

total 36
drwxr-xr-x   4 root root 4096 2007-10-30 04:25 .
drwxr-xr-x 111 root root 4096 2007-10-30 15:28 ..
drwxr-xr-x   2 root root 4096 2007-10-30 04:26 apt.conf.d
-rw-------   1 root root    0 2007-10-15 16:18 secring.gpg
**[COLOR="Blue"][SIZE="3"]-rw-r--r--   1 root root 4202 2007-10-30 04:22 sources.list[/SIZE][/COLOR]**
drwxr-xr-x   2 root root 4096 2007-10-15 13:40 sources.list.d
-rw-------   1 root root 1200 2007-10-15 16:18 trustdb.gpg
-rw-r--r--   1 root root 2393 2007-10-15 16:18 trusted.gpg
-rw-r--r--   1 root root 2381 2007-10-15 16:18 trusted.gpg~

Thanks,
Ian

There it is.  Are you sure you've entered the right command from a terminal?

```
cat /etc/apt/sources.list
```

---

### Post by grendel2110 on 2007-10-30
Must have copied it wrong. Durr. This looks a lot like the results the guy got on the page I referenced in the top of the thread. Should I follow from there? Thanks.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by taurus on 2007-10-30
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, **deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted**, to comment it out.

Then, remove the # from all the lines that begin with **deb** and **deb-src** (repos).  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by grendel2110 on 2007-10-30
Thanks so much for the help. I allowed more repos and solved the problem without having to edit any source code. I'll leave this as solved, but I'll refer back to the source code you provided for future issues. Danke.

---

