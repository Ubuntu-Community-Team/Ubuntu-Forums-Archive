---
title: "Debian main sarge problems with Synaptic"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by Prakash Prabhu on 2005-09-09
Hi,

Whenever I use synaptic to connect to the debian site to download the package
list, it is giving me a 'Failed' error. What could be the reason for this ?

This is my sources.list file in /etc/apt.d/ :

[http://people.csa.iisc.ernet.in/~jprakash/public_html/sources.list](http://people.csa.iisc.ernet.in/~jprakash/public_html/sources.list)

and here is a screenshot of Synaptic :

[http://people.csa.iisc.ernet.in/~jprakash/public_html/Screenshot.png](http://people.csa.iisc.ernet.in/~jprakash/public_html/Screenshot.png)

Is there anything I am missing in here ?

- Prakash

---

### Post by rafakl on 2005-09-09
The files are inaccesibles  :-x

---

### Post by Kyral on 2005-09-09
..Why is this not in Debian's Forums?

---

### Post by Prakash Prabhu on 2005-09-10
This is the sources.list file :

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://ftp.debian.org](http://ftp.debian.org) sarge main
deb [http://ftp.debian.org](http://ftp.debian.org) sarge main

and the screen shot is here :

[http://lightlord.8k.com/images/screenshot.jpg](http://lightlord.8k.com/images/screenshot.jpg)

The main problem is that ( i suspect ) because of this , mplayer is not listed in the list of packages that synaptic shows.

---

