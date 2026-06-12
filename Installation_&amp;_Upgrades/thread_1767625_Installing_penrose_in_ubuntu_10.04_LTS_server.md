---
title: "Installing penrose in ubuntu 10.04 LTS server?"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by chuawenching on 2011-05-25
Hi everyone,

Penrose is part of redhat/centos. 

[http://penrose.redhat.com/display/PENROSE/Home](http://penrose.redhat.com/display/PENROSE/Home)

As far i understand there is no direct way to install penrose in ubuntu 10.04 LTS server unless i download the source and build it? I really doubt apt-get is possible here too.

Anyone having experiences doing that?

Thanks.

---

### Post by Toz on 2011-05-25
Well, you could try to use alien ([http://wiki.debian.org/Alien](http://wiki.debian.org/Alien)). It's a package that converts rpm to deb and vice versa. I've used it successfully in the past for other packages. YMMV.

You can type the following commands in a command terminal window to get more information.

To show info about the package:```
apt-cache show alien
```
To see if its installed: ```
apt-cache policy alien
```
To install it: ```
sudo apt-get install alien
```

---

### Post by chuawenching on 2011-05-26
Thanks I will give it a try tonight :)

---

