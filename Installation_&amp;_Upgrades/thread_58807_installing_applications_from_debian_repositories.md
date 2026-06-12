---
title: "installing applications from debian repositories"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by twelvegates on 2005-08-21
Hello,

it seems to me that the Ubuntu repository is missing several applications that are available in Debian, for example gkrellm, fluxbox, icewm, tkdiff and vim-gtk.

Is it a good idea to install such applications from a Debian repository?
If yes from which one?

-Hanspeter

---

### Post by al7kz on 2005-08-21
Hi, 

You need to add more repositories to /etc/apt/sources.list. The ones I use, besides the cd, are:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse
deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse

##Security Mirrors
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

##Backports
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

# Ubuntu Backports
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main restricted universe multiverse
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports main restricted universe multiverse

# Ubuntu Backports Extras

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main restricted universe multiverse
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-extras main restricted universe multiverse

## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

#XFCE
deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

#Marillat
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Regards, al7kz

---

### Post by DJ_Max on 2005-08-21
[QUOTE=twelvegates]Hello,

it seems to me that the Ubuntu repository is missing several applications that are available in Debian, for example gkrellm, fluxbox, icewm, tkdiff and vim-gtk.

Is it a good idea to install such applications from a Debian repository?
If yes from which one?

-Hanspeter[/QUOTE]
 No, don't install packages made for another distribution, you're asking for trouble later on. Besides, all of those packages you've listed are in the Ubuntu repositories already.

You didn't include all the Ubuntu repositories.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

