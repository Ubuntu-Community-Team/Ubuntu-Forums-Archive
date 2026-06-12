---
title: "Problems with packages configuring after adept"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by mastergunner on 2007-12-20
I just built a new computer and put Kubuntu 7.10 on it. After installing and putting the 74 new packages on it that adept said I needed to I have a problem with some packages not being configured this is what I did below:

brad@brad:~$ sudo dpkg --configure -a
Setting up gconf2-common (2.20.0-0ubuntu1) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing gconf2-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on gconf2-common (>= 2.20); however:
  Package gconf2-common is not configured yet.
 gconf2 depends on gconf2-common (<< 2.21); however:
  Package gconf2-common is not configured yet.
dpkg: error processing gconf2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgconf2-4:
 libgconf2-4 depends on gconf2-common (>= 2.20); however:
  Package gconf2-common is not configured yet.
 libgconf2-4 depends on gconf2-common (<< 2.21); however:
  Package gconf2-common is not configured yet.
dpkg: error processing libgconf2-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libgksu2-0 depends on gconf2 (>= 2.10.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gksu depends on libgksu2-0 (>= 1.9.6); however:
  Package libgksu2-0 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on gksu (>= 2.0.0-1ubuntu3); however:
  Package gksu is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuzilla:
 ubuntuzilla depends on gdebi; however:
  Package gdebi is not configured yet.
dpkg: error processing ubuntuzilla (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2-common
 gconf2
 libgconf2-4
 libgksu2-0
 gksu
 gdebi
 ubuntuzilla


As you can see I tried to configure the pkgs but they dont want to. I have tried apt-get update and apt-get upgrade but nothing helps. HELP!!!!!!

---

### Post by SOULRiDER on 2007-12-20
Try doing
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by mastergunner on 2007-12-20
This is what I got below. It is still broke.

[sudo] password for brad:
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
brad@brad:~$ sudo aptitude dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

