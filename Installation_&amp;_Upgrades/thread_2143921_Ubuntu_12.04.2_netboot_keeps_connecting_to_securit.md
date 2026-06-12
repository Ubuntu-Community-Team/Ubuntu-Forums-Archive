---
title: "Ubuntu 12.04.2 netboot keeps connecting to security.ubuntu.com despite local mirror"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by jyanga on 2013-05-10
Hi.  I just created a local mirror based on archive.ubuntu.com using apt-mirror.  During network install, the client seems to hang at the point of "Installing the base system".  Looking at the traffic, it seems like the client is attempting to connect to security.ubuntu.com.

base-installer:  Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
base-installer:  Connection failed [91.189.92.184 80]

How can I prevent the client install from going outside of my network and sticking to my local mirror?

INFO:
Ubuntu 12.04.2 Precise AMD64

Help.

---

