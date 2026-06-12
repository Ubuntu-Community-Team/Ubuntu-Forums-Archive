---
title: "Add language support fails in Gutsy"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by mmasroorali on 2007-11-14
Dear All,
I am really frustated. 

I know that in order to add a new language in ubuntu all I need to do is,

[COLOR="Blue"]"go to Ubuntu Gnome desktop menu bar, then point to System > Administration > Language Support. A small language will appear where available supported languages were listed. Select the languages you want to install and configure in your Ubuntu Linux, and click Apply button. Before hitting OK button, ensure that your Internet connection is up and running."[/COLOR]

When I do this, all gutsy does is a very quick local search, then let me know that only available language is English!!!

If I do the same thing from live session CD after installation, all the languages are listed. But in that case, I can install since I am behind proxy.

During istallation, I went for the very default settings. One error occurred when some lines were commented out in /etc/apt/resource (?) or some such (network could not be accessed) due to lack of verication.

Your input will be highly appreciated. 

Regards.

---

### Post by mikewhatever on 2007-11-14
> cat /etc/apt/sources.list

and post the output here.

---

### Post by mmasroorali on 2007-11-14
Here it goes,

[COLOR="Red"]# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse[/COLOR]


Also, how to I enable the proxy for security updates?

[COLOR="Blue"] /etc/bash.bashrc file :
export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/ [/COLOR]

or something else?

It appears that we need a wiki on installation behind proxy. Search at ubuntu wiki returned blanks.

Regards.

---

### Post by mikewhatever on 2007-11-15
Your sources list looks OK, I am not sure why the languages are missing. What do you get in respond to this 
> sudo apt-cache search language-support-*

---

### Post by mmasroorali on 2007-11-15
It appears that after I set the http_proxy in /etc/bashrc.bashrc things have started to work.

---

### Post by mikewhatever on 2007-11-15
> **mmasroorali said:**
> It appears that after I set the http_proxy in /etc/bashrc.bashrc things have started to work.

So you figured it out, congratulations!

---

