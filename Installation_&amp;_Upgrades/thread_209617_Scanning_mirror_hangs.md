---
title: "Scanning mirror hangs"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by daune_jf on 2006-07-05
Hi,

I wanted to give Ubuntu a try, and I have just downloaded server version (Drapper) to install it on quite old PC (Celeron 1GHz/20GB IDE HD/512MB RAM)

I burnt ISO, and launched install procedure, but it hangs at 'Configuring apt'/'Scanning the mirror' step. It just blocks at 40%. 

I have requested to check that CD, and it reported no errors.

Is it a problem with my HD?

J-F

---

### Post by bionnaki on 2006-07-22
having the same problem. stuck at 40% - anyone know why? is it a problem with the repos?

---

### Post by taurus on 2006-07-22
If you are using us.archive.ubuntu.com, then yes.  It's currently down so remove the "us" in front and see if you can connect to archive.ubuntu.com.

---

### Post by tim- on 2006-08-31
There's a quick fix to this issue, disable your network devices and it will time out within 30secounds and proceed with the install.  Just enable your network after that and everything should be fine.

---

### Post by woolyg on 2007-04-09
Beautiful, Tim- sorted out my kubuntu install perfectly:) Woolyg

---

### Post by cshapiro on 2007-07-12
Heh. This fix works. but beware that apt-get will comment out all of the URLs in /etc/apt/sources.list. You will have to manually uncomment them to make apt-get work properly again.

---

### Post by alphaone on 2007-08-21
You can kill the processes 'sh' and 'wget' from the busybox console too...

so:

1. Press CTRL - ALT + F2
2. run 'ps -ef'
3. then 'kill -INT' of the processes that start with 'wget' and 'sh' (just a line upper)

The installation process then will continue as normal.

Thanks

[http://www.alphaoneweb.com](http://www.alphaoneweb.com)

---

### Post by toyon on 2007-09-14
> The installation process then will continue as normal.

But how to get back to the GUI install screen after quitting busybox, so you can see what's going on?

---

### Post by Jaryth on 2007-10-18
Nice little workaround tim! Thanks!

---

### Post by flurdy on 2007-10-19
Works a treat.
Im behind a proxy (and installing in vmware) so it was hanging.

This does appear do be a bug that should be reported?

Ps.
Remember to use sudo ifconfig eth0 down
instead of sudo /etc/init.d/networking stop

---

### Post by interconnect on 2007-10-21
i had this problem.. and fixed by just unplugging my ethernet cable.  could someone please post a copy of their /etc/apt/sources.list for (7.10 gutsy gibbon, i386) so i could restore the file the way it was originally intended?  thanks,

---

### Post by interconnect on 2007-10-22
anyone?

---

### Post by Tsume on 2007-11-01
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

