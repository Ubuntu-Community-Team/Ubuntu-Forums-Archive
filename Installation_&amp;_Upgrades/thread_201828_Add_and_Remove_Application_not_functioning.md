---
title: "Add and Remove Application not functioning"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by cjblade54 on 2006-06-22
I upgraded the new Ununtu 6.06 a week ago.  Somehow, it won't let me use the Add/Remove application in the menu.  Everytime I clicked on it, it shows 
Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

And I have followed the instructions as the message shown, but nothing changed.  What should I do next? :-k

---

### Post by aysiu on 2006-06-22
Post the output of these commands: ```
cat /etc/apt/sources.list
sudo aptitude update
```

---

### Post by cjblade54 on 2006-06-22
[QUOTE=aysiu]Post the output of these commands: ```
cat /etc/apt/sources.list
sudo aptitude update
```[/QUOTE]
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

## created by arnieplanetremoved

---

### Post by cjblade54 on 2006-06-22
root@dracula:/# sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [71.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [39.7kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.8kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [19.2kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [37.1kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Get:23 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:24 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:25 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:26 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:27 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Fetched 316kB in 6s (45.4kB/s)
Reading package lists... Done
root@dracula:/#

---

### Post by aysiu on 2006-06-22
They both look good to me.

No errors on the update, and you have sources in your sources.list.

Try the Add/Remove again and see if you run into the same error after updating.

---

### Post by cjblade54 on 2006-06-22
[QUOTE=aysiu]They both look good to me.

No errors on the update, and you have sources in your sources.list.

Try the Add/Remove again and see if you run into the same error after updating.[/QUOTE]

I still have the same issue.  I just noticed that on the right hand corner it has this message:
A error occured, please run Package Manager from the right-click menu or apt=get on a terminal to see what is wrong.  the error message was; "Error: Opening the cache (E:Opening /etc/apt/source.list - ifstream::ifstream (13 Permission denied), E:The list of sources could not be read.)'

---

### Post by megadave on 2006-11-01
I just ran into the same thing and this being the only result through Google I thought I'd update it.  

Over in #ubuntuforums a user named **rikai** helped me out.

After trying many things, actual solution was:

Had to erase all the files in var/lib/apt/lists/*

make sure to leave or recreate the directory named **partial** or you'll get an error.

then run sudo apt-get update

and voila, working synaptic and software installer.

---

