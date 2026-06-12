---
title: "Upgrading Warty to Hoary Please"
date: 2005-04-06
forum: Installation &amp; Upgrades
---

### Post by s0c0 on 2005-04-06
Okay so a friend at school told me that if I upgrade to Hoary certain issues that Warty has will be resolved.  I won't dive into these issues.  I noticed from reading other similiar posts to perform an "apt-get dist upgrade" from the terminal as root...Is this correct?   I remember from debian I had to change my /etc/apt/sources.list to whatever version I wanted.  Don't I have to do this still?  My sources.list looks like this, **do I just change everything to hoary and perform the apt-get dist upgrade?**

[I]deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main[/I]

I have seen similiar posts, but none of them seemed to answer this topic for me.  **Also is hoary stable yet** or is it near stable since a stable O.S. is very important to me over the bells and whistles!  Your help is appreciated   [-o<

---

### Post by seven on 2005-04-06
edit your /etc/apt/sources.list:

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)]/ hoary main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe  multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe 

and run:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade

---

### Post by s0c0 on 2005-04-06
Great, thanks seven.  I've broken too many distro's by not asking so I wanted to make sure.  So is hoary stable or near stable though?

---

### Post by Leif on 2005-04-06
I've got hoary on two machines, and it's been very solid for the last couple of weeks, so go ahead.

---

### Post by s0c0 on 2005-04-08
Thanks, works good.

---

