---
title: "can't instal some programs nor Ubuntu 7.10"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by frevh on 2007-12-27
Ubuntu  is new for me; i love it , ..
just installing some niuew programs doesn't work ; update manager shows: system is update  : upgrate starts wel but i got this on the end
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 404 Not Found
 and
publieke sleutel niet beschikbaar is: NO_PUBKEY D0AFFF5E937215FF
 someone can help me?

Frevh

---

### Post by taurus on 2007-12-27
Can you post your /etc/apt/sources.list?  You say you have Gutsy but your error message says it can't find the Fiesty repos!

```
cat /etc/apt/sources.list
```

---

### Post by frevh on 2008-01-02
sorry for late reply
had very nice new jar days....
i wish jou a really good jar; 
jou asked me to post.../etc/apt/sources.list
cat/ don't exist...


fvh@fvh:~$ cat /etc/apt/sources.list
## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
# deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
# deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17
# deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17

deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts

fvh@fvh:~$ 

i don' t understand everithing but looks very interresting for a beginner like me

i hope this will help you to explain me .....
thanks for helping

---

### Post by sciencewhiz on 2008-01-02
> **frevh said:**
> 
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

It looks like Medibuntu no longer has packages at the address above. See the following page for the current medibuntu repository: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ~LoKe on 2008-01-02
Change those repositories to these:
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free


---

### Post by zvacet on 2008-01-02
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]

and in your case type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys D0AFFF5E937215FF
gpg --export --armor D0AFFF5E937215FF  | sudo apt-key add -

---

### Post by frevh on 2008-01-20
Thanks for helping..
I realized i had to do some more efforts to understand something more ;so I learned to work with terminal and other... really interesting....:) 
I  changed key server....and  in software bronnen (dutch ) i set al of of feisty and wonder happend!!!!
i could install gutsy! and other...

i was very proud and thankful  
I hope one day i can help someone but there is still some work to do....

thanks 

frevh :KS

---

