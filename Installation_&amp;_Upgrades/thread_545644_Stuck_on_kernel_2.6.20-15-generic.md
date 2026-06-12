---
title: "Stuck on kernel 2.6.20-15-generic"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by cmacdonell on 2007-09-07
Hi,

I'm currently running the 2.6.20-15 generic kernel.  When I run apt-get update, it doesn't offer the -16-generic kernel as an upgrade.  

Here is my /etc/apt/sources.list

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) feisty/

#deb [http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/) feisty-security main restricted
#deb-src [http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Any ideas?

Thanks,
Cam

---

### Post by rsambuca on 2007-09-07
It's because you have disabled your security updates repository - Not a good idea!

You need to remove the number sign from these lines.  Also, I would remove the edgy lines as well, as they shouldn't be in there.


[COLOR="Red"]**#**[/COLOR]deb [http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/) feisty-security main restricted
[COLOR="Red"]**#**[/COLOR]deb-src [http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/) feisty-security main restricted
[COLOR="Red"]# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe (remove this entire line)
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe (remove this entire line)[/COLOR]

---

