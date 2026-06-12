---
title: "Install of ssmtp - broken packages"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by SageOfSmeg on 2014-06-14
I need help trying to install ssmpt. I keep getting error messages about dependencies and broken packages.

I have already tried...
   apt-get autoclean
   apt-get autoremove
   apt-get -f install
but it has not helped.


This is what I have so far...

```
gjd@gjdpc3:~$ sudo apt-get update
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://gb.archive.ubuntu.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release
Hit http://gb.archive.ubuntu.com precise Release
Hit http://extras.ubuntu.com precise/main Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_GB
Ign http://extras.ubuntu.com precise/main Translation-en
Reading package lists... Done

```

```
gjd@gjdpc3:~$ sudo apt-get install ssmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 ssmtp : Depends: libgnutls-openssl27 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
gjd@gjdpc3:~$ 

```

```
gjd@gjdpc3:~$ sudo apt-get install libgnutls-openssl27
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libgnutls-openssl27 : Depends: libgnutls26 (= 2.12.14-5ubuntu3) but 2.12.14-5ubuntu3.8 is to be installed
E: Unable to correct problems, you have held broken packages.
gjd@gjdpc3:~$ 

```

```
gjd@gjdpc3:~$ apt-cache policy libc6
libc6:
  Installed: 2.15-0ubuntu10
  Candidate: 2.15-0ubuntu10
  Version table:
 *** 2.15-0ubuntu10 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
gjd@gjdpc3:~$ 

```

```
gjd@gjdpc3:~$ apt-cache policy libc6-dev
libc6-dev:
  Installed: (none)
  Candidate: 2.15-0ubuntu10
  Version table:
     2.15-0ubuntu10 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
gjd@gjdpc3:~$ 

```

```
gjd@gjdpc3:~$ cat /etc/apt/sources.list /etc/apt/sources.list.d/*
# 

# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423.1)]/ precise main universe

# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423.1)]/ precise main multiverse universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise main

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise universe

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb http://security.ubuntu.com/ubuntu precise-security multiverse
# deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
 deb http://extras.ubuntu.com/ubuntu precise main
 deb-src http://extras.ubuntu.com/ubuntu precise main
# deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main
deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main
# deb http://ppa.launchpad.net/pitti/postgresql/ubuntu precise main
# deb-src http://ppa.launchpad.net/pitti/postgresql/ubuntu precise main
# deb http://ppa.launchpad.net/pitti/postgresql/ubuntu precise main
# deb-src http://ppa.launchpad.net/pitti/postgresql/ubuntu precise main
gjd@gjdpc3:~$ 

```

Some of the above may not be rellevant.

---

### Post by oldos2er on 2014-06-14
You don't have multiverse enabled, nor, more importantly, any security repo. Example: ```

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
```

[Source]("https://help.ubuntu.com/12.04/sample/sources.list").

---

### Post by SageOfSmeg on 2014-06-14
Thank you, that made it all work now.

---

### Post by oldos2er on 2014-06-14
Great! Thanks for marking the thread 'Solved.'

---

