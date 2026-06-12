---
title: "[SOLVED] firefox-2 is not available for ubuntu 80.4"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by oalexandrino on 2008-07-13
hello,

I've been trying to install firefox-2 under ubuntu 8.04.

but I'm not being able to do that.

take a look below what I get when I try to remove firefox3 and install firefox2

- after I have removed firefox 3, i run the following command

oalexandrino@oalexandrino:/usr/bin$ sudo apt-get install firefox-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox-2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox-2 has no installation candidate
oalexandrino@oalexandrino:/usr/bin$ 

what's wrong?

any idea?

---

### Post by tech0007 on 2008-07-13
Check that you have 'universe' enabled in 'Software Sources'. then do 'sudo apt-get update' && 'sudo apt-get firefox-2'

---

### Post by Pumalite on 2008-07-13
You have to have 3.0, then add:
sudo aptitude install firefox-2

---

### Post by aysiu on 2008-07-13
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by oalexandrino on 2008-07-13
> **Pumalite said:**
> You have to have 3.0, then add:
sudo aptitude install firefox-2

after I run the command above, look at what I got

oalexandrino@oalexandrino:~$ sudo aptitude install firefox-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for firefox-2
No candidate version found for firefox-2
The following packages are unused and will be REMOVED:
  xulrunner-1.9-gnome-support 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 152kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 132646 files and directories currently installed.)
Removing xulrunner-1.9-gnome-support ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by oalexandrino on 2008-07-13
> **aysiu said:**
> Can you post the output of this command? ```
cat /etc/apt/sources.list
```

look

```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://br.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://br.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy main multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse


```

---

### Post by oalexandrino on 2008-07-13
> **aysiu said:**
> Can you post the output of this command? ```
cat /etc/apt/sources.list
```

look

```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://br.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://br.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://br.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy main multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse


```

the following command doesn't install anything

:(

```
sudo apt-get install firefox-2

```

---

### Post by aysiu on 2008-07-13
Can you also post the output of this command? ```
cat /etc/lsb-release
```

---

### Post by oalexandrino on 2008-07-13
> **aysiu said:**
> Can you also post the output of this command? ```
cat /etc/lsb-release
```

hi!

take a look

```
oalexandrino@oalexandrino:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"
oalexandrino@oalexandrino:~$ 
```

---

### Post by aysiu on 2008-07-13
Okay. The problem is you're running Ubuntu 8.04 (Hardy Heron), but your repositories are mainly for Ubuntu 7.10 (Gutsy Gibbon).

So let's get you a fresh repositories list and try again.

Let's save the old list somewhere: ```
sudo mv /etc/apt/sources.list
``` and create a new list ```
gksudo gedit /etc/apt/sources.list
``` In the new text editor window, paste in ```
deb http://archive.canonical.com/ubuntu hardy partner

deb http://br.archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://br.archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted

deb http://packages.medibuntu.org/ hardy free non-free
``` then save the file and exit the text editor. ```
sudo apt-get update
sudo apt-get install firefox-2
```

---

### Post by oalexandrino on 2008-07-14
> **aysiu said:**
> Okay. The problem is you're running Ubuntu 8.04 (Hardy Heron), but your repositories are mainly for Ubuntu 7.10 (Gutsy Gibbon).

So let's get you a fresh repositories list and try again.

Let's save the old list somewhere: ```
sudo mv /etc/apt/sources.list
``` and create a new list ```
gksudo gedit /etc/apt/sources.list
``` In the new text editor window, paste in ```
deb http://archive.canonical.com/ubuntu hardy partner

deb http://br.archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://br.archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted

deb http://packages.medibuntu.org/ hardy free non-free
``` then save the file and exit the text editor. ```
sudo apt-get update
sudo apt-get install firefox-2
```

man!

it worked!

I do recognize your help. thanks a milion for the support!!!!

---

