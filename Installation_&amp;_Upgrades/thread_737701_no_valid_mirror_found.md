---
title: "no valid mirror found"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by asdfoo on 2008-03-27
hi

I'm attempting to upgrade from 64bit 7.04 to 7.10 through synaptic, it downloads a few files and then it says "No valid mirror found"  "While scanning your repository information no mirror entry for the upgrade was found.  This can happen if you run an internal mirror or the if the mirror information ins out of date"

This is my local mirror which I use because it does not count towards my download quota, can someone please tell me what exactly is missing from my local mirror?

$ grep -v '^#' /etc/apt/sources.list

deb [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty main restricted
deb-src [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty main restricted

deb [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty-updates main restricted
deb-src [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty-updates main restricted

deb [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty universe
deb-src [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty universe

deb [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty multiverse
deb-src [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty multiverse

deb [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://ftp.iinet.net.au/linux/ubuntu/](http://ftp.iinet.net.au/linux/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by asdfoo on 2008-03-27
trying anyway, seems to be working so far at "Fetching the upgrades"

Fetching file 1016 of 1570 at 620kb/s

---

