---
title: "installing vmware-player"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by Krischu on 2007-01-08
Hi,

I follwed this HOWTO:

[https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO](https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO)

and after installing the tarball from the VMWARE website, I'm stuck at this point:


sudo apt-get install vmware-player-kernel-modules

apt-get doesn't find these modules.

Where do I get them?

Here is my /etc/apt/sources.list:

#////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
# Line commented out by installer because it failed to verify:
deb [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## die letzten beiden heute, 20.9.06 hinzugefuegt CPK
 deb [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper universe
 deb-src [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 deb-src [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb     [http://www.hellion.org.uk/debian](http://www.hellion.org.uk/debian) sid main
#deb-src [http://www.hellion.org.uk/debian](http://www.hellion.org.uk/debian) sid main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
#
# xgl usw.
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
#////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////


Any clues?

---

### Post by radiant chains on 2007-01-11
You need to enable the multiverse repository. Add 'multiverse' to these two lines in your sources.list

> **Krischu said:**
> 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## die letzten beiden heute, 20.9.06 hinzugefuegt CPK
 deb [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper universe [COLOR="Red"]multiverse[/COLOR]
 deb-src [http://de2.archive.ubuntu.com/ubuntu/](http://de2.archive.ubuntu.com/ubuntu/) dapper universe [COLOR="Red"]multiverse[/COLOR]


---

