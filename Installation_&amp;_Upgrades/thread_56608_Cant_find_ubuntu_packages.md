---
title: "Cant find ubuntu packages"
date: 2005-08-13
forum: Installation &amp; Upgrades
---

### Post by Laban on 2005-08-13
I have just installed ubuntu 5.04 and when i try to install apps ubuntu cant find the packages for example.. "sudo apt-get install nvtv" it says "E: Couldnt find package nvtv" what is this how can i fix this is it the database for the packages that is outdated?? Allthough i have been able to install apache2 and php4 for example but many programs it cant find.. please help me =)

---

### Post by Lord Illidan on 2005-08-13
Hi Laban!! Nice to see fresh blood in the Ubuntu Forums!!!

I suggest you have a look at the Ubuntu Guide and install extra repositories>>

[www.ubuntuguide.org](http://www.ubuntuguide.org) 

I see you already know how to use apt-get... Have you used Linux before?

---

### Post by drummer on 2005-08-13
[QUOTE=Laban]I have just installed ubuntu 5.04 and when i try to install apps ubuntu cant find the packages for example.. "sudo apt-get install nvtv" it says "E: Couldnt find package nvtv" what is this how can i fix this is it the database for the packages that is outdated?? Allthough i have been able to install apache2 and php4 for example but many programs it cant find.. please help me =)[/QUOTE]
 Add the extra repositories for Ubuntu:
[http://www.ubuntuguide.org#extrarepositories](http://www.ubuntuguide.org#extrarepositories)

Not all packages can be included by default because of legal/non-free reasons. Adding them should fix your problem

---

### Post by Copter on 2005-08-13
hi!

you probably dont have all repositories enabled. check your /etc/apt/sources.list file. my looks like this
```

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://pl.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://pl.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pl.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://pl.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://pl.archive.ubuntu.com/ubuntu hoary universe
deb-src http://pl.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

deb http://archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
```and i can install nvtv. check also this link [http://ubuntuforums.org/forumdisplay.php?f=41](http://ubuntuforums.org/forumdisplay.php?f=41). maybe you will find more info there.

copter :]

---

### Post by Laban on 2005-08-13
Thanks for the help dudes =) I dont have time know to try out what you have told me to do but ill check it out later and tell you have it have gone thx for helping a newbie out ;)

---

