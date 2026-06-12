---
title: "sources.list: amd64 or i386 or mac?"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by bahbo on 2005-10-17
Hi,
I have an AMD64 machine, but don't see anything in /etc/apt/sources.list that indicates this.  So I'm wondering if I have the wrong sources.list file for amd64, or how apt knows that my machine is amd64 and not i386 or a mac.  I did an install with the amd64 cd, but then completely changed the sources.list file (I couldn't find a lot of packages, like transcode).  Right now my sources.list file has the following lines:

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64  Binary-1(20050202)]/ unstable main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Thanks,
Ric

---

### Post by Dr. Nick on 2005-10-17
Not sure how it knows but it does. I have no mention of "64" in my sources file either, it probably has to do with the fact that apt-get knows its 64bit itself so it knows what type its on

---

