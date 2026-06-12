---
title: "another problem"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by nerd0795 on 2008-04-19
Well i got a problem with installing packages (I hope this is the right place to post)  when I try to download kiba-dock it always says E: could not find package when I try to install the app.  does anyone know how to set get packages from the internet?  I'm using xubuntu.

Here's an example of the problem:
```

alex@alex-desktop:~$ sudo apt-get install kiba-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kiba-plugins

```

---

### Post by Pumalite on 2008-04-19
Post:
cat /etc/apt/sources.list
Or:
System>Administration>Software Sources and enable all

---

### Post by nerd0795 on 2008-04-19
```
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

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
deb http://archive.ubuntu.com/ubuntu/ gutsy universe main
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by Pumalite on 2008-04-19
Your sources.list is basic, but Ok. You are obviously missing the repo that provides kiba-plugins, if there is one. I'm not familiar with it. This is what I found for you:
[http://packages.pardus.org.tr/contrib/binary/kiba-plugins.html](http://packages.pardus.org.tr/contrib/binary/kiba-plugins.html)
You can still use this and see if there are some not enabled:
System>Administration>Software Sources

---

### Post by nerd0795 on 2008-04-19
[http://ubuntuforums.org/showthread.php?t=312789](http://ubuntuforums.org/showthread.php?t=312789)
This is what I'm doing...

---

### Post by Pumalite on 2008-04-19
You have to add tuxfamily to your repos for this to work according to your link.

---

### Post by nerd0795 on 2008-04-19
How do I do that?  Im a complete linux nub (Just got it a day ago)

---

### Post by Pumalite on 2008-04-19
Backup your file:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
Edit:
gksudo gedit /etc/apt/sources.list
Add the lines you need according to this:


. Configure your system to be using Treviño's repository by adding the following to lines in your /etc/apt/sources.list file:
* If you are using Edgy Eft (6.10):
o deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
o deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
* If you are using Feisty (7.04):
o deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
o deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
Save, exit.

Then get the key:

2. Import Trevino's GPG key:
$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
Then install:
3. $ sudo apt-get update
4. $ sudo apt-get install kiba-dock
5. $ sudo apt-get install kiba-dock-dev
6. $ sudo apt-get install kiba-plugins

---

### Post by nerd0795 on 2008-04-19
Is fiesty eye candy default?  I don't know what I have, I know I have Xubuntu 7.10.

---

### Post by Pumalite on 2008-04-19
It's 7.10 then. Sorry but I have to leave. I'll be back tomorrow 8 AM Eastern Time. Cheers.

---

### Post by Pumalite on 2008-04-20
Did you work it out?

---

