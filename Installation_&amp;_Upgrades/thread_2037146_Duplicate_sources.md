---
title: "Duplicate sources"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by tessem11 on 2012-08-03
Hello every one I am new to ubuntu and have found this error message after I did sudo apt-get update: W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems.
I ran sudo apt-get update again and it came up with the same message any body have an idea on how to fix it?

---

### Post by oldos2er on 2012-08-03
Can you run ```
cat /etc/apt/sources.list
``` and post the output here?

---

### Post by tessem11 on 2012-08-07
sure sorry I am new to this.
```
# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
deb-src http://mirror.us.leaseweb.net/ubuntu/ precise main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.us.leaseweb.net/ubuntu/ precise main restricted
deb-src http://mirror.us.leaseweb.net/ubuntu/ precise multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.us.leaseweb.net/ubuntu/ precise-updates main restricted
deb-src http://mirror.us.leaseweb.net/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.us.leaseweb.net/ubuntu/ precise universe
deb http://mirror.us.leaseweb.net/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.us.leaseweb.net/ubuntu/ precise multiverse
deb http://mirror.us.leaseweb.net/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://mirror.us.leaseweb.net/ubuntu/ precise-security main restricted
deb-src http://mirror.us.leaseweb.net/ubuntu/ precise-security restricted main multiverse universe #Added by software-properties
deb http://mirror.us.leaseweb.net/ubuntu/ precise-security universe
deb http://mirror.us.leaseweb.net/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

deb http://mirror.us.leaseweb.net/ubuntu/ precise-proposed restricted main multiverse universe
deb-src http://mirror.us.leaseweb.net/ubuntu/ precise-proposed restricted main multiverse universe #Added by software-properties
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
deb-src http://download.bitdefender.com/repos/deb/ bitdefender non-free
deb http://packages.mate-desktop.org/repo/ubuntu precise main
deb-src http://packages.mate-desktop.org/repo/ubuntu precise main

```
thanks :)

---

### Post by oldos2er on 2012-08-07
That looks ok. Could you post the results of ```
ls /etc/apt/sources.list.d/
``` ?

---

### Post by tessem11 on 2012-08-14
here it is
```

colingille-freshlight-precise.list
colingille-freshlight-precise.list.save
danielrichter2007-grub-customizer-precise.list
danielrichter2007-grub-customizer-precise.list.save
dropbox.list
dropbox.list.save
eugenesan-java-precise.list
eugenesan-java-precise.list.save
gezakovacs-ppa-precise.list
gezakovacs-ppa-precise.list.save
gnome3-team-gnome3-precise.list
gnome3-team-gnome3-precise.list.save
google-chrome.list
google-chrome.list.save
google-musicmanager.list
google-musicmanager.list.save
gwendal-lebihan-dev-cinnamon-stable-precise.list
gwendal-lebihan-dev-cinnamon-stable-precise.list.save
medibuntu.list
mozillateam-firefox-next-precise.list
mozillateam-firefox-next-precise.list.save
mozillateam-firefox-stable-precise.list
mozillateam-firefox-stable-precise.list.save
nemh-gambas3-precise.list
nemh-gambas3-precise.list.save
nilarimogard-webupd8-precise.list
nilarimogard-webupd8-precise.list.save
opera.list
opera.list.save
otto-kesselgulasch-gimp-precise.list
otto-kesselgulasch-gimp-precise.list.save
pinta-maintainers-pinta-stable-precise.list
pinta-maintainers-pinta-stable-precise.list.save
playonlinux.list
playonlinux.list.save
precise-partner.list
precise-partner.list.save
sebikul-gambas-daily-precise.list
sebikul-gambas-daily-precise.list.save
tualatrix-ppa-precise.list
tualatrix-ppa-precise.list.save
ubuntu-wine-ppa-precise.list
ubuntu-wine-ppa-precise.list.save
virtualbox.list
virtualbox.list.save
webupd8team-java-precise.list
webupd8team-java-precise.list.save
webupd8team-y-ppa-manager-precise.list
webupd8team-y-ppa-manager-precise.list.save
wuala.list.save
yannubuntu-os-uninstaller-precise.list

```

---

### Post by oldos2er on 2012-08-14
> precise-partner.list
precise-partner.list.save

You've got the partner repository enabled in your sources.list as well as in /etc/apt/sources.list.d/precise-partner.list. Remove one of them and run *sudo apt-get update* and there should be no more errors.

```
sudo rm /etc/apt/sources.list.d/precise-partner.*

sudo apt-get update
```

---

### Post by tessem11 on 2012-08-14
thanks again

---

