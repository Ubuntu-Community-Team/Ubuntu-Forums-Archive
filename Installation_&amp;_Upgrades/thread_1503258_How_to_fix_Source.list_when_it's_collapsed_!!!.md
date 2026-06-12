---
title: "How to fix Source.list when it's collapsed !!!"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by OldSnake on 2010-06-06
Hi there ! :KS
I'm a rookie :lolflag:  in the biggest world of Free OS(Linux/Ubuntu).
i added some links of online repositories in /etc/apt/source/list but i don't know why after few days, i figure out that none of the programs that listed in Ubuntu Software Center aren't able to install and i've faced with this error

 [http://up.iranblog.com/Files/e4066ce691f2426da38b.png](http://up.iranblog.com/Files/e4066ce691f2426da38b.png)

after do some crazy things :-k i got a source.list of new ubuntu 10.4 from my friends then i replace it inside of mine :-\"! when i restart my OS i found out that error hasn't solved.
these are my Software Source's pics after replacing  ![COLOR=Cyan]

*******************
[http://up.iranblog.com/Files/22e14127558748c28f35.png](http://up.iranblog.com/Files/22e14127558748c28f35.png)[/COLOR] [COLOR=Cyan]
[http://up.iranblog.com/Files/92301d6a198f486b93f1.png](http://up.iranblog.com/Files/92301d6a198f486b93f1.png)[/COLOR] [COLOR=Cyan]
[http://up.iranblog.com/Files/5aa72baff91a4e6dab40.png](http://up.iranblog.com/Files/5aa72baff91a4e6dab40.png)[/COLOR] [COLOR=Cyan]
[http://up.iranblog.com/Files/cc352dab9fe34dcd89f3.png](http://up.iranblog.com/Files/cc352dab9fe34dcd89f3.png)[/COLOR] 
[COLOR=Cyan]*******************[/COLOR]
and it's my Source.list , take a look
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb http://ubuntu.gnu.gen.tr/ubuntu/ lucid main restricted
deb-src http://ubuntu.gnu.gen.tr/ubuntu/ lucid main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.gnu.gen.tr/ubuntu/ lucid-updates main restricted
deb-src http://ubuntu.gnu.gen.tr/ubuntu/ lucid-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu lucid universe
# deb-src http://archive.ubuntu.com/ubuntu lucid universe
# deb http://archive.ubuntu.com/ubuntu lucid-updates universe
# deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe
# deb http://security.ubuntu.com/ubuntu lucid-security universe
# deb-src http://security.ubuntu.com/ubuntu lucid-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
[COLOR=Red]# deb http://archive.ubuntu.com/ubuntu lucid multiverse
# deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
# deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse
# deb http://security.ubuntu.com/ubuntu lucid-security multiverse
# deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse[/COLOR]

deb http://ubuntu.gnu.gen.tr/ubuntu/ lucid universe
deb http://security.ubuntu.com/ubuntu/ lucid-security restricted main universe
```i don't know why i have some online links of repositories but they aren't shown in the "Other Software" Or in second pic ! 
what's worng with my Source.list ?
can i solve this problem with ur help or what ?
plz someone help me.
should i reinstall my Os ?
should i Delete all the lines in Source.list do something in terminal ?
i really fall in love with UBUNTU, cause it's to beautiful and handy !

PS: i'm sorry for my awful english cause i'm rookie in english too ! 
anyway .... Much appreciated!!!

---

### Post by davidmohammed on 2010-06-06
you've got various lines commented out - suggest remove # from beginning of some lines.

here is mine to compare against.

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://dl.google.com/linux/deb/ testing non-free
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb http://viewizard.com/linux debian/
```

---

### Post by sgosnell on 2010-06-06
Any line with # as the first character is interpreted as a comment, and not used.  You have to remove the # from the lines you want to use.  You can either do this in gedit or in Synaptic, by choosing the repositories you want activated.

---

