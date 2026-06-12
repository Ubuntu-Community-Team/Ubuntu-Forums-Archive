---
title: "[SOLVED] Very slow downloads only when downloading packets from repositories"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Tilex on 2008-11-25
Hi guys,

I've a Kubuntu 8.10 64-bit installed on a Core2 installed.  Actually, I just installed my system and I had to fool around with my WUSB54GSC wireless card before internet worked at all.

Now that I get speeds of up to 750 Kb/s on a web server, whenever I try to update my system through Adept or its command-line equivalent (apt-get), I can extremely slow speeds at like 1.5 KB/s or less.

Does anybody have a clue about this?  It never happened to me before with all my Kubuntu installs.

Thanks!

---

### Post by taurus on 2008-11-25
Do you happen to use the Canadian site?  Go into synaptic and use another site like Main Server.  Your speed should be faster now.

---

### Post by Tilex on 2008-11-25
Yes OK thanks taurus I'll try that out.

Before changing anything, I just tried to install "kde-nightly" from repository:
```
deb http://ppa.launchpad.net/project-neon/ubuntu intrepid main
```

and I' downloading at 500KB/s.  

I'll try Main Server once my package database is free, and will post the results here.

Thanks!

---

### Post by Tilex on 2008-11-25
Hum...still awfully slow.  

My repositories already seem to be from Canada; here's my sources.list:
```
# 
# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main restricted

#deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

#DEV packages
deb http://ppa.launchpad.net/project-neon/ubuntu intrepid main

```

Any idea?

---

### Post by Skripka on 2008-11-25
Wierd, this morning  when I updated, I was getting the fastest speeds for grabbing package data that I've seen since installing 8.10 Kubuntu :confused:

---

### Post by Tilex on 2008-11-25
I switched from Canada to Main Server, and I'm getting decent 80KB/s speeds.

I guess the Canada servers were overwhelmed by canadian Linux adoption :P

---

### Post by obscenic on 2008-11-25
I also just went from about 700 B/s (BYTES!) to about 450kB/s when switching from Canada to main. Why are our Canadian repo's so slow?

---

### Post by pourya on 2009-02-08
Thank you so much, I had the same problem using CA servers I had to wait for hours,.... CA servers should be replaced with the Main servers!!!
cheers

---

