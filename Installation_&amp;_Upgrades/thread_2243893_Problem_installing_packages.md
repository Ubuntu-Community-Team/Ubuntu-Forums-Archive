---
title: "Problem installing packages"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by timmyk.2 on 2014-09-11
Greetings. I have just installed Ubuntu Studio on a computer I built. However, it seems to be having issues installing packages. First I started getting "Failed to download repository information" error messages when I tried to install programs from the Ubuntu Software Centre. After some research on the internet I went to "Software & Updates" and played around a bit. The only thing that made a difference was changing "Server for Canada" (I'm Canadian) to "Main server". That stopped the "Failed to download repository information" error messages, but now when I try I get "Requires installation of untrusted packages" messages. Under details it says
```
enblend enfuse freeglut3 hugin hugin-data hugin-tools libboost-signals1.49.0 libpano13-2 libpano13-bin libplot2c2 libzthread-2.3-2
```
I tried installing from the terminal using the "sudo apt-get install" command, which gives a long string of text followed by
```
Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
```
I have tried both of these commands, as well as "sudo apt-get upgrade", but none of them do anything. "Sudo apt-get update" gives a long string of text followed by
```
Some index files failed to download. They have been ignored, or old ones used instead.
```
"Apt-get --fix-missing" just tells me how to use the apt-get command. "Sudo apt-get upgrade" just tells me nothing has been installed or upgraded.

Help would be greatly appreciated!

---

### Post by yancek on 2014-09-12
Which release version of Ubuntu Studio are you using?

---

### Post by timmyk.2 on 2014-09-12
14.04.

---

### Post by claracc on 2014-09-12
Could you please post the contents of the file /etc/apt/sources.list?, better between code tags.

---

### Post by timmyk.2 on 2014-09-12
```
# deb cdrom:[Ubuntu-Studio 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring universe
deb-src http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe
deb-src http://archive.ubuntu.com/ubuntu raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu raring multiverse
deb-src http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb-src http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu raring main
# deb-src http://extras.ubuntu.com/ubuntu raring main
```

---

### Post by claracc on 2014-09-13
As I see, you are running raring ringtail 13.04 ubuntu which reached its end of life support last january.

The repositories have been removed from server and for this reason you cannot install software or receive any security update.

I suggest to install a supported ubuntu release as 12.04 or 14.04.

---

### Post by timmyk.2 on 2014-09-14
I feel really stupid now. I was so sure that I was using the newest version I didn't bother to check. Thanks for the help everyone, and sorry for wasting your time!

---

### Post by claracc on 2014-09-14
You are very welcome, ask questions is not wasting anybody's time.

Regards.

---

