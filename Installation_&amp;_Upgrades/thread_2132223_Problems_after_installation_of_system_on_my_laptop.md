---
title: "Problems after installation of system on my laptop(hp)"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by otar on 2013-04-04
Hi everyone!

I've installed Ubuntu 12.04 on my laptop and when I turn it on next notification appears:

[B]could not initialize the package information, an unresolvable problem occures while initializing the package information. Please, report this bug against the `update-manager` information package and include the following error massage: `E:Type "partner is not known on line 47 in source list/etc/apt/sources.list`


[/B]then I dont know which updates I have to do. 

For more clarity I bring here my source.list:

david@david-HP-ProBook-4510s:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise universe
deb [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://ge.archive.ubuntu.com/ubuntu/](http://ge.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
david@david-HP-ProBook-4510s:~$ 
Thank you in advance

---

### Post by slickymaster on 2013-04-04
> **otar said:**
> 
```

## Uncomment the following two lines to add software from Canonical's
[COLOR=#ff0000][SIZE=4]'partner' repository.[/SIZE][/COLOR]
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
david@david-HP-ProBook-4510s:~$ 


```


Thank you in advance


Line 47 of your sources list file needs to be commented.
Just edit that line in our sources files:
```
## 'partner' repository.
```

---

