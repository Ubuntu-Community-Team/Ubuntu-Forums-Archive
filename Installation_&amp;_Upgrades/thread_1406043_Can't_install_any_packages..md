---
title: "Can't install any packages."
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by Jordii on 2010-02-13
I can't install any deb-packages. (I download them from another pc because I don't have wireless connection on Ubuntu)
I get the error message:
 
Error: Dependency is not satisfiable: <program> 
 
cat /etc/apt/sources.list
```

[FONT=Batang][SIZE=3]# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted[/SIZE][/FONT]
[FONT=Batang][SIZE=3]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to[/SIZE][/FONT]
[FONT=Batang][SIZE=3]# newer versions of the distribution.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]deb http://nl.archive.ubuntu.com/ubuntu/ karmic main restricted[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic main restricted[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]## Major bug fix updates produced after the final release of the[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## distribution.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://nl.archive.ubuntu.com/ubuntu/ karmic-updates main restricted[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-updates main restricted[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## team. Also, please note that software in universe WILL NOT receive any[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## review or updates from the Ubuntu security team.[/SIZE][/FONT]
[SIZE=3][FONT=Batang]deb http://nl.archive.ubuntu.com/ubuntu/ karmic universe[/FONT][/SIZE]
[SIZE=3][FONT=Batang]deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic universe[/FONT][/SIZE]
[SIZE=3][FONT=Batang]deb http://nl.archive.ubuntu.com/ubuntu/ karmic-updates universe[/FONT][/SIZE]
[SIZE=3][FONT=Batang]deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-updates universe[/FONT][/SIZE]
 
[FONT=Batang][SIZE=3]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## team, and may not be under a free licence. Please satisfy yourself as to[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## your rights to use the software. Also, please note that software in[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## multiverse WILL NOT receive any review or updates from the Ubuntu[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## security team.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://nl.archive.ubuntu.com/ubuntu/ karmic multiverse[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic multiverse[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://nl.archive.ubuntu.com/ubuntu/ karmic-updates multiverse[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-updates multiverse[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]## Uncomment the following two lines to add software from the 'backports'[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## repository.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## N.B. software from this repository may not have been tested as[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## extensively as that contained in the main release, although it includes[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## newer versions of some applications which may provide useful features.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## Also, please note that software in backports WILL NOT receive any review[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## or updates from the Ubuntu security team.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]# deb http://nl.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse[/SIZE][/FONT]
[FONT=Batang][SIZE=3]# deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]## Uncomment the following two lines to add software from Canonical's[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## 'partner' repository.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## This software is not part of Ubuntu, but is offered by Canonical and the[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## respective vendors as a service to Ubuntu users.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]# deb http://archive.canonical.com/ubuntu karmic partner[/SIZE][/FONT]
[FONT=Batang][SIZE=3]# deb-src http://archive.canonical.com/ubuntu karmic partner[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]deb http://security.ubuntu.com/ubuntu karmic-security main restricted[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://security.ubuntu.com/ubuntu karmic-security universe[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://security.ubuntu.com/ubuntu karmic-security universe[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://security.ubuntu.com/ubuntu karmic-security multiverse[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse[/SIZE][/FONT]

```
 
I can't use the CD.

---

### Post by MelDJ on 2010-02-13
what is the program you are installing? 
the program needs a dependency which might not be available in the cd

---

### Post by Jordii on 2010-02-13
> **MelDJ said:**
> what is the program you are installing? 
the program needs a dependency which might not be available in the cd
 
It happens with build-essential, ndiswrapper utils-1..
But, I've got the CD, but my laptop damages the CD, so I don't use it.

---

### Post by MelDJ on 2010-02-13
you can try getting the dependencies from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
but they too might have their own dependencies

---

### Post by Jordii on 2010-02-13
If just my Broadcom B43 driver worked, I could download it all from Synaptic.

---

