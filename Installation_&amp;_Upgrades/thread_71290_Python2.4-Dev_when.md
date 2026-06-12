---
title: "Python2.4-Dev??? when??"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by aljones15 on 2005-10-02
is there a python2.4-dev lib available for ubuntu?
I tried the debian one, but it says the version of python2.4
ubuntu comes with it isn't compatible with it.
so then i tried downloading the python2.4 from deb package
but it says that to uninstall python it would uninstall bit torrent
and other various essential apps in the same process. anyone got
an old python2.4-dev lib lying around? is there anything I can do to
ensure ubuntu and debian stay more up to date?

thanks,
a

---

### Post by DJ_Max on 2005-10-03
I'm going to write a FAQ on the wiki, as this issues comes up all too often. 
First, Ubuntu is not Debian. Do NOT use Debian packages on your Ubuntu system unless you want problems. 

The package in the Ubuntu repos is *python2.4-dev*.

Ubuntu is up to date on security fixes, but the reason it's so stable is that it doesn't cahse new packages without testing them. But if you must have the lastest, use backports.

---

### Post by aljones15 on 2005-10-07
nah definitely not seeing python2.4-dev anywhere.
I'm pretty confident I have the backports enabled in my lists.

peace,
a

---

### Post by DJ_Max on 2005-10-07
Do a 
```
sudo apt-get install python2.4-dev
```

---

### Post by aljones15 on 2005-10-08
root@alj:/etc/apt # sudo apt-get install python2.4-dev
Reading package lists... Done
Building dependency tree... Done
Package python2.4-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python2.4-dev has no installation candidate


maybe my sources list is fucked up?

here's the list


## Uncomment the following two lines to fetch updated software from the network
deb [http://kr.archive.ubuntu.com/ubuntu](http://kr.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://kr.archive.ubuntu.com/ubuntu](http://kr.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted
deb-src [http://kr.archive.ubuntu.com/ubuntu](http://kr.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://kr.archive.ubuntu.com/ubuntu](http://kr.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://kr.archive.ubuntu.com/ubuntu](http://kr.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://ftp2.caliu.info/backports](http://ftp2.caliu.info/backports) hoary-extras restricted
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports main universe multiverse

---

### Post by aljones15 on 2005-10-08
ahh never mind.
it worked.
I needed to remove one of the comments # things
from my sources list.
updated my last post to reflect that.
sorry about the trouble.

thanks,
a

---

