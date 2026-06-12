---
title: "strange error with updates after installing clamav"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by abh83 on 2007-02-25
Hello,

All of a sudden after installing clamav (the anti virus software) from the synaptic package manager I started getting this error message (see screen-shot below) when I try to update. which is also why clamav didn't install correctly.

The error message continues to appear even after i fully removed clamav and all of its configurations.

help is greatly appreciated!
ABH

---

### Post by Stemp on 2007-02-25
Could you please show us your /etc/apt/sources.list file ?

---

### Post by abh83 on 2007-02-25
hope this is right:

> deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://at.archive.ubuntu.com/ubuntu/](http://at.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
#AUTOMATIX REPOS END

---

### Post by Stemp on 2007-02-25
Edit your sources.list :

```
gksudo gedit /etc/apt/sources.list 
```

and remove the automatix lines :

```

deb http://www.getautomatix.com/apt edgy main

```

I advice you to also delete the edgy-proposed lines :

```
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
```

---

### Post by abh83 on 2007-02-25
thx will give this a try!

maybe you can explain the issue a little more? ;)

ABH

---

### Post by abh83 on 2007-02-25
btw if i remove code: deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

wouldn't that prevent automatix from updating?

---

### Post by Stemp on 2007-02-25
> maybe you can explain the issue a little more? 

Sure, automatix add [Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu") to install stuff, and actually getautomatix.com is down. So Synaptic is just complaining about this unreachable site ;)

---

### Post by abh83 on 2007-02-25
well thx again! error message is gone!

ABH

---

### Post by Stemp on 2007-02-25
> btw if i remove code: deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

wouldn't that prevent automatix from updating?

Yes automatix won't update, but it's not a big deal because automatix is just a «script» to install codecs and proprietary softwares. In fact when you install all the non-free things, you may uninstall automatix.

---

