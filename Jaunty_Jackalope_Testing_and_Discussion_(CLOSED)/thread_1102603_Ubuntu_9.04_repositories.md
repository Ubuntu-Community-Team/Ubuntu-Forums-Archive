---
title: "Ubuntu 9.04 repositories?"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kilinu5889 on 2009-03-21
Hello, I have been messing around with my repositories, and I was wondering may I see what is in in your list? Thank you.

---

### Post by Bakon Jarser on 2009-03-21
> **kilinu5889 said:**
> Hello, I have been messing around with my repositories, and I was wondering may I see what is in in your list? Thank you.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by go7Ul1ai on 2009-03-21
[img]http://localhostr.com/files/d8edcb/Screenshot.png[/img]

That reminds me to delete the duplicate software source.

---

### Post by Bakon Jarser on 2009-03-21
oops, guess i didn't understand what you were asking.

---

### Post by Yashiro on 2009-03-22
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main multiverse restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports universe main multiverse restricted

Will be the final ones I guess. Not sure what the alpha/beta is currently using.

---

### Post by DougieFresh4U on 2009-03-22
This is what I have and by all means it is not the 'official' list as I have some ppa's added as well;
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090204)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb http://ppa.launchpad.net/fta/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/fta/ppa/ubuntu jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/exaile-devel/ppa/ubuntu intrepid main
deb http://cafelinux.org/Downloads/oz-os tinwoodman main
deb http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt intrepid main
deb http://ppa.launchpad.net/pythoneers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/pythoneers/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

```

---

### Post by taavikko on 2009-03-22
```
deb http://archive.ubuntu.com/ubuntu/ jaunty main universe multiverse restricted
deb http://security.ubuntu.com/ubuntu/ jaunty-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe main multiverse restricted
#deb http://archive.ubuntu.com/ubuntu/ jaunty-backports universe main multiverse restricted
#deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed universe main multiverse restricted
```

Is all that's needed for basic installation.

---

### Post by pjalegria on 2009-03-22
Shoud i enable backports ???

---

### Post by andrewabc on 2009-03-22
> **pjalegria said:**
> Shoud i enable backports ???

For 9.04?
I wouldn't think so. It's not even released yet so I would not think there would be backports.

Oddly for 8.10 when I enabled backports it only had updates for 3 programs (brasero, lyx and 1 other). So it seems kinda pointless.

---

### Post by kilinu5889 on 2009-03-22
Ok, thanks guys. I coudlnt install anything before but now I can. Thanks!

---

