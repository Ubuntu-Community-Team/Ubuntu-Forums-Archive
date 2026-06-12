---
title: "Error message from Software Updater"
date: 2018-07-07
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2018-07-07
18.04 Ubuntu
failed to load software updater
missing repository information
check internet connection

My internet connection is just fine

---

### Post by #&amp;thj^% on 2018-07-07
I'm just not a user of the software updater.
It may help to see the real error (If any) with:
```
sudo apt update
```

---

### Post by s9032g@comcast.net on 2018-07-08
Does not work.
message "Failed to download repository information"
"check internet connection"

---

### Post by #&amp;thj^% on 2018-07-08
> **s9032g@comcast.net said:**
> Does not work.
message "Failed to download repository information"
"check internet connection"

The whole message would have been better, but we will do it the hard way then.
Check your source list for bad repos or PPA's:
```
 cat /etc/apt/sources.list
```
Try changing the Server from which updates come from, I use the Main server.
Are you using a Proxy? In my experience, there are at least three other causes of the failure: incorrect repository location, repository is down, and incorrect proxy settings.

---

### Post by s9032g@comcast.net on 2018-07-09
I don't know how I got "bionic updates" How do I fix this?

<pre><font color="#8AE234"><b>steven@steven-Latitude-E7240</b></font>:<font color="#729FCF"><b>~</b></font>$  cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical&apos;s
## &apos;partner&apos; repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
# deb [http://archive.canonical.com/](http://archive.canonical.com/) bionic partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) bionic partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
<font color="#8AE234"><b>steven@steven-Latitude-E7240</b></font>:<font color="#729FCF"><b>~</b></font>$ 
</pre>

---

### Post by #&amp;thj^% on 2018-07-09
I'm very confused now >> have you upgraded to Bionic and forgotten?
What dose this show:
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04 LTS
Release:	18.04
Codename:	bionic

```
Just to be clear Bionic is 18.04 LTS
Also we need to see the whole output from: 
```
sudo apt update
```
Your answer of "Does not work." just dose not help us here>>>please give us the needed info or we/I can't help you. ;)

---

### Post by s9032g@comcast.net on 2018-07-10
I fixed it. The problem was that I, based on some advice from one of those "20 things to do" blogs, activated and checked off "independent" under "other software". Apparently that caused the error message. As soon as I unselected it the problem went away. Of course I know that I have Bionic. In fact I have loaded it twice. The last time to fix problems caused by a recent update.

---

### Post by #&amp;thj^% on 2018-07-10
> **s9032g@comcast.net said:**
> I don't know how I got "bionic updates" How do I fix this?


You can see where this added confusion then. :)

> **s9032g@comcast.net said:**
>  _Of course I know that I have Bionic. In fact I have loaded it twice._ The last time to fix problems caused by a recent update.
Glad to hear it is working now;)
Happy Buntuing....

---

