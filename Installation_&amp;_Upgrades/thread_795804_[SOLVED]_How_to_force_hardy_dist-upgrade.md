---
title: "[SOLVED] How to force hardy dist-upgrade"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by leifp on 2008-05-15
Hi, all.

I recently tried to upgrade my laptop from Gutsy to Hardy.  My connection is very slow, so I was forced to stop and restart the upgrade many times.  This worked for a while, and the cached packages were detected, but now when I try to run ```
apt-get dist-upgrade
``` it says
"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

 I know that's not true, because /var/cache/apt has 900 Mb of packages that haven't been installed.

Is there any way to force the upgrade to restart?  I'll even start over from scratch if I must, but I'd prefer it if the cached packages were detected.

Thanks,
Leif

---

### Post by komputes on 2008-05-15
Can you post your /etc/apt/sources.list?

Can you post the output of "uname -a" in the terminal.

Can you try the following:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Be sure to look out for any messages or errors asking you to run a command the fix something that was broken. The system is pretty fool proof and i think they have consiered dropped connections. Either that or you're already in Hardy.

---

### Post by Bubba64 on 2008-05-15
> **leifp said:**
> Hi, all.

I recently tried to upgrade my laptop from Gutsy to Hardy.  My connection is very slow, so I was forced to stop and restart the upgrade many times.  This worked for a while, and the cached packages were detected, but now when I try to run ```
apt-get dist-upgrade
``` it says
"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

 I know that's not true, because /var/cache/apt has 900 Mb of packages that haven't been installed.

Is there any way to force the upgrade to restart?  I'll even start over from scratch if I must, but I'd prefer it if the cached packages were detected.

Thanks,
Leif

Have you looked in synaptic to see if the marked packages can just be installed.

---

### Post by leifp on 2008-05-16
@komputes:

uname -a -> "Linux tenrai 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux"

sudo apt-get update -> no problems

sudo apt-get upgrade -> problem installing emacs22, but it's said that for months, I just use emacs21 or vim.  Probably not related to the dist-upgrade problems.

```

leif@tenrai:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up emacs22-gtk (22.1-0ubuntu5.2) ...
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs22 failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs22
!! and attach the file /tmp/emacs22.yP8132
dpkg: error processing emacs22-gtk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs22-gtk | emacs22 | emacs22-nox; however:
  Package emacs22-gtk is not configured yet.
  Package emacs22 is not installed.
  Package emacs22-gtk which provides emacs22 is not configured yet.
  Package emacs22-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jde:
 jde depends on emacs21 | emacsen; however:
  Package emacs21 is not installed.
  Package emacsen is not installed.
  Package emacs which provides emacsen is not configured yet.
  Package emacs22-gtk which provides emacsen is not configured yet.
dpkg: error processing jde (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs22-gtk
 emacs
 jde
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This is disconcerting, but that one error would stop the whole upgrade, would it?  It didn't before.  I stopped and restarted the upgrade about 4 times before it stopped working.  I should clarify that I don't even see the "Upgrade to 8.04..." option anywhere now.

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by komputes on 2008-05-16
Wow, Well I can definitely tell you that the kernel version is that on Gutsy (7.10), I would try removing these three packages and trying again, 

```

sudo apt-get remove emacs22-gtk emacs jde
sudo apt-get install emacs22-gtk emacs jde


```

if it still gives you an error, I would backup the /home subdirectories in a tar.gz and to reinstall clean from the 8.04 CD.

---

### Post by leifp on 2008-05-16
@Bubba64:

There are no marked packages in synaptic.  Synaptic is reading from the Gutsy repositories, and all the cached packages are from Hardy.

@komputes:

I removed those packages (and dependents) and tried again.  No luck.

---

### Post by Bubba64 on 2008-05-16
> **leifp said:**
> @Bubba64:

There are no marked packages in synaptic.  Synaptic is reading from the Gutsy repositories, and all the cached packages are from Hardy.

@komputes:

I removed those packages (and dependents) and tried again.  No luck.

I understand I think Komputes advice to backup and install with a CD is probably the best idea. If you have nothing to lose I would do a fresh install. The times I have had similar problems is when I had downloads from Automatix or other auto installers. If you do a CD install get the daily ISO this will save you the time of a ton of updates. Good Luck

---

### Post by leifp on 2008-05-20
Magically fixed itself.  Update manager is now showing the distribution upgrade again.  Thanks, everybody.

---

