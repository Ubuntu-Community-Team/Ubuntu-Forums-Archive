---
title: "upgrading to 18.04LTS"
date: 2018-08-03
forum: Installation &amp; Upgrades
---

### Post by chubbtech on 2018-08-03
I get an error message  (see attached screenshot) when upgrading from 17.10 to 18.04LTS

---

### Post by Impavidus on 2018-08-03
Yakkety is Ubuntu 16.10. If you're indeed using 17.10, it shouldn't be there. Try to disable every yakkety repository, then try again.

17.10 is already dead, but as long as the repos haven't been removed, upgrading should work without too much trouble. Don't wait any longer.

---

### Post by coffeecat on 2018-08-03
I presume you read the error message. It refers to Yakkety, which is 16.10. Which means either that you are trying to upgrade from 16.10, not 17.10, or that your 17.10 installation contains one or more 16.10 sources.

If you are indeed running 16.10 and not 17.10, I suggest you don't try to upgrade to 18.04. That way lies frustration and breakage, and I'm not sure that's even possible any more. Backup your data and make a fresh installation of 18.04.

If you believe you are running 17.10, post the output of these two terminal commands:

```
cat /etc/lsb-release
cat /etc/apt/sources.list
```

Please post the output between BBCode code tags to preserve formatting and to make it readable - there is a link in my sig if you aren't sure how to do this.

---

### Post by chubbtech on 2018-08-06
> **coffeecat said:**
> I presume you read the error message. It refers to Yakkety, which is 16.10. Which means either that you are trying to upgrade from 16.10, not 17.10, or that your 17.10 installation contains one or more 16.10 sources.

If you are indeed running 16.10 and not 17.10, I suggest you don't try to upgrade to 18.04. That way lies frustration and breakage, and I'm not sure that's even possible any more. Backup your data and make a fresh installation of 18.04.

If you believe you are running 17.10, post the output of these two terminal commands:

```
cat /etc/lsb-release
cat /etc/apt/sources.list
```

Please post the output between BBCode code tags to preserve formatting and to make it readable - there is a link in my sig if you aren't sure how to do this.
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"

---

### Post by chubbtech on 2018-08-06
# deb cdrom:[Ubuntu 16.10 _Yakkety Yak_ - Release amd64 (20161012.2)]/ yakkety main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) yakkety main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) yakkety-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) yakkety universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) yakkety-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) yakkety multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) yakkety-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) yakkety-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety partner


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-proposed multiverse main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security multiverse

---

### Post by Impavidus on 2018-08-06
Open your sources.list file with your preferred text editor with root permissions, like```
sudo nano /etc/apt/sources.list
```
Put a # at the beginning of every line containing "yakkety" that doesn't already start with a #. Then save the file. In nano, use ctrl+x, reply y to save changes, as indicated at the bottom of the screen. That should fix it.

And keeping the "proposed" repository enabled may make your system less stable.

---

### Post by chubbtech on 2018-08-17
Thanx :)

---

