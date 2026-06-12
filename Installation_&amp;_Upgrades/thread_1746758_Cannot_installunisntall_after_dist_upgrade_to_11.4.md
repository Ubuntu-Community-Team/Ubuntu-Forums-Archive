---
title: "Cannot install/unisntall after dist upgrade to 11.4"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by banago on 2011-05-02
Hi guys,

I did a distro upgrade to 11.4 form 10.10 yesterday. Everything works fine and 11.4 seems to be slightly faster to me.

However, when I try to install/uninstall a program I get the following error:

> (Reading database ... 90%**dpkg**: unrecoverable fatal error, aborting:   reading files list for package '**libc6**': Input/output error

I tired:
[LIST]
[*]Synaptec => Custom Filters => Broken - There was no broken package
[*]sudo dpkg --configure -a - Did not do anything
[/LIST]

The problem seems to be with the **libc6** package. Seems most of the applications depend on it. My finding is that on "/var/lib/dpkg/info/" does not exist a libc6.list and seems it is causing the error. 

How can I solve this. Thanks guys.

---

### Post by banago on 2011-05-02
Help anyone?

---

### Post by dino99 on 2011-05-02
open your sources.list:

 sudo gedit /etc/apt/sources.list

you only should have genuine natty repo (no ppa or else), then save and close

from a terminal:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

(open synaptic and check you use "main" server)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by kansasnoob on 2011-05-02
If you're not familiar with the sources.list (software sources) please maximize the terminal and just post the output of:

```
cat /etc/apt/sources.list
```

It would also be helpful if you could "wrap" the text in code tags :)

---

### Post by banago on 2011-05-02
Thanks very much for the help both of you - I really appreciate it.

Yes, I'm unable to analize my source list, so here it goes for you to have a look at it:

```

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://al.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://al.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://al.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://al.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://al.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://al.archive.ubuntu.com/ubuntu/ natty universe
deb http://al.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://al.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://al.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://al.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://al.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://al.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://al.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://al.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

```

**Thanks very very much!**

---

### Post by banago on 2011-05-02
Did you guys have a look?

---

### Post by banago on 2011-05-02
Please help guys.

---

### Post by banago on 2011-05-04
Help!

---

### Post by kansasnoob on 2011-05-04
Not sure what the locale "al" is but I don't see anything seriously wrong so I'd suggest opening the Update Manager, clicking on Settings, and under the Ubuntu Software tab click on "Download from" and select the main server.

Hopefully that gets things sorted, but you'll notice I said, "I don't see anything **seriously** wrong"! There are a couple of tiny things but they're in commented out lines anyway. Look at everything in there that says Maverick, those should be changed to Natty.

---

### Post by banago on 2011-05-06
The AL locale is the Server for Albania because I live in Albania. 

Switched to main server, did the autoclean and stuff - still same error.

The problem lies still with the "libc6" library.

---

### Post by banago on 2011-05-07
It seems I will have to start a new thread.

---

