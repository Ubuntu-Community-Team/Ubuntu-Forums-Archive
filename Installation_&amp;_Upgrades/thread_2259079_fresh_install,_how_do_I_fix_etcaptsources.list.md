---
title: "fresh install, how do I fix /etc/apt/sources.list ?"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by arnicainthemembrane on 2015-01-01
Hi, I just did a fresh install of 13.04. As with many others I am unable to access the repositories in order to download gimp, etc

apt-get update yields a lot of 404 not found messages, etc. 

 I read somewhere in this forum or "ask ubuntu" that a etc/apt/sources.list needs to be edited. Here are the results of gedit /etc/apt/sources.list, how might I edit it to overcome the problem? Bear in mind I am new to this so a link to an "idiots guide to gedit might be a good idea.

thanks!!!

```
sudo gedit /etc/apt/sources.list yielded:

# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
```

---

### Post by schragge on 2015-01-01
Ubuntu 13.04 is past its end of life, unsupported, and all repositories are relegated to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
You may point your */etc/apt/sources.list* to old-releases with this command:
```
sudo sed -i '/canonical\|extras/s/^/#/;/^[^#]/s|//[^/]*|//old-releases.ubuntu.com|'  /etc/apt/sources.list
```

But if this is a fresh install the most reasonable thing would be just to re-install Ubuntu 14.04.

---

### Post by MAFoElffen on 2015-01-01
+1 
Which means that if you take what you highlighted... and changed that portion to what schragge gave you, they would point to that archive. There are also archive mirrors. 

But what you should do, is to upgrade your release to get current or at least on the the last LTS. Ubuntu LTS is support now to 5 years. Before they go EOL. The interim releases are on a short lived 9 month support cycle. It went EOL on January 27 2014. That means it went End of Life almost a year ago. Especially being an interim release, the longer you wait, the more work it will be to get that to do a do-release-upgrade to something current.

Is there a reason you did a fresh install with something almost 2 years old? Why not 12.04LTS of 14.04LTS? Since a fresh install, not too late to do a fresh install of something supported.

---

### Post by Bucky Ball on 2015-01-01
+1 to what MAFoElffen has advised.

Install a supported release. 12.04 LTS and 14.04 LTS have five years support. 14.10 has nine months. Avoid unsupported releases. The older they get the less chance you have of getting support for them here (or elsewhere). 13.04 hasn't had a security update since it reached end-of-life so the older it gets, the more vulnerable your machine will become if it's online. You are also using dated (and unsupported) versions of the software you have installed.

See [here]("http://ubuntuforums.org/showthread.php?t=2229730") re. forum recommendations on EOL releases and links to supported releases.

(PS: Please use [code] tags for code. Clearer, neater, space-saving and easier to read. I have added them to your first post. See the last link in my signature for how to use them.)

Good luck. ;)

---

