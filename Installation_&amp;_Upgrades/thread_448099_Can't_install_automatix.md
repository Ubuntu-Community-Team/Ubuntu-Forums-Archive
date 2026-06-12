---
title: "Can't install automatix"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by sfed on 2007-05-18
I have followed [ these]("http://getautomatix.com/wiki/index.php?title=Installation") instructions to install automatix 2.I  also have removed the quotes from echo .....When i try to enter "sudo apt-get update  on terminal i get this message ```
E: Type 'http://www.getautomatix.com/keys/automatix2.key' is not known on line 41 in source list /etc/apt/sources.list

```

My source list is
 ```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://gr.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gr.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://download.java.net/ubuntu/ feisty/


http://www.getautomatix.com/keys/automatix2.key
gpg --import automatix2.key
exit
deb http://www.getautomatix.com/apt feisty main
```

Also i can't open Synaptic .
when i try i get this error 

```
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'http://www.getautomatix.com/keys/automatix2.key' is not known on line 41 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
```

and a quote from my terminal.

```
01:36:02 (88.99 MB/s) - `automatix2.key.**7**' saved [1706/1706]

```

---

### Post by taurus on 2007-05-18
These lines should not be in your /etc/apt/sources.list.

```
http://www.getautomatix.com/keys/automatix2.key
gpg --import automatix2.key
exit
```
You need to go over to Automatix's site and follow the instructions on how to install it again.

---

