---
title: "problem with upgrading and installing a sofware"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by rirùta on 2012-07-10
Hi,
When trying to run an apt-get command, I get the following error: ```
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```

Can anyone please help me? This is how my /etc/apt/sources.list looks like:
```
# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://tn.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://tn.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://tn.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://tn.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://tn.archive.ubuntu.com/ubuntu/ precise universe
deb http://tn.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://tn.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://tn.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://tn.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://tn.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner
deb http://archive.canonical.com/precise partner
deb-src http://archive.canonical.com/precise partner

```

Thank you very much :)

---

### Post by kc1di on 2012-07-10
hi,
at first glance I don't see a problem with your /etc/apt/sources.list file.  in fact the error message says the error is found in line 59 and I only count 54 lines in your sources list. 
Here are a couple things you can try.

```
sudo apt-get autoclean
sudo apt-get update
```

see if they give you the same message. post any different error you get

---

### Post by codemaniac on 2012-07-10
You can recreate your sources.lst from the below link .

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by neo_1in on 2012-07-10
```
deb http://archive.canonical.com/precise partner
deb-src http://archive.canonical.com/precise partner
```
Above portion is repeated.

Also IMHO, you should comment out 'deb-src' lines unless you really need them.

---

### Post by SlugSlug on 2012-07-10
> **codemaniac said:**
> You can recreate your sources.lst from the below link .

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)


nice link - thanks!

---

### Post by kc1di on 2012-07-10
> **codemaniac said:**
> You can recreate your sources.lst from the below link .

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Thank for the link never knew that one before handy :)

---

### Post by rirùta on 2012-07-10
Thank you all, well it seems that the problem was with the two last lines as neo_1in just said. I commented those lines out and everything is now alright :)

---

