---
title: "apt-get &amp; broken packages"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by Bdfy on 2005-07-28
sudo apt-get check
sudo apt-get update

apt-get install mozilla-firefox
 mozilla-firefox: Depends: libatk1.0-0 (>= 1.9.0) but it is not installable
                   Depends: libbonobo2-0 (>= 2.8.0) but it is not installable
                   Depends: libbonoboui2-0 (>= 2.5.4) but it is not installable
                   Depends: libgconf2-4 (>= 2.9) but it is not installable
                   Depends: libgnome2-0 (>= 2.8.0) but it is not installable
                   Depends: libgnomecanvas2-0 (>= 2.6.0) but it is not installable
                   Depends: libgnomeui-0 (>= 2.8.0) but it is not installable
                   Depends: libgnomevfs2-0 (>= 2.9.90) but it is not installable
                   Depends: libgtk2.0-0 (>= 2.6.0) but it is not installable
                   Depends: libpango1.0-0 (>= 1.8.1) but it is not installable
E: Broken packages

less /etc/apt/sources.list 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse

/etc/apt/sources.list deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.4.2/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.4.2/kubuntu) hoary-updates main
deb [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.4.2/kubuntu](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.4.2/kubuntu) 
hoary-updates main
deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/3.4.2/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/3.4.2/kubuntu) hoary-updates main
deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/3.4.2/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/3.4.2/kubuntu) hoary-up
dates main

---

### Post by Xian on 2005-07-28
Save your current sources.list and then use mine as your own.
Then run an 'apt-get update session'.

Finally, try to install firefox again.

```
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted

deb http://kubuntu.org/hoary-kde342 hoary-updates main
deb-src http://kubuntu.org/hoary-kde342 hoary-updates main
```

---

