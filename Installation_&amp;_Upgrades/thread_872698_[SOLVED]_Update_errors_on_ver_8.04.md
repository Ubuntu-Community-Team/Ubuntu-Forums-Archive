---
title: "[SOLVED] Update errors on ver 8.04"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by G1ZmO65 on 2008-07-28
Every time I try to install the new updates on Ubuntu 8.04 I get the following message:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.22.3-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.22.3-0ubuntu1_i386.deb)
  Connection failed

This has been happening for weeks now. I keep retrying in case the file is just temporarily unavailable but it seems to be a permanent error.

Any suggestions?

Paul

---

### Post by zvacet on 2008-07-28
In system>admin>software sources change server to **main**.If that doesn´t help 

```
cat /etc/apt/sources.list
```

and post it here.

---

### Post by G1ZmO65 on 2008-07-28
I set the server to Main but got the same failure message

Heres the sources.list

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

---

### Post by zvacet on 2008-07-28
Your source list looks good.Even worst I tried link you posted and it is work for me.Maybe to try 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by G1ZmO65 on 2008-07-29
Arg! You know what it was?

Our work firewall is set to block any link with BEBO in it.

That unfortunately includes that link! LOL

Modified the firewall rules and it's now working! :)

Thanks

Paul

---

