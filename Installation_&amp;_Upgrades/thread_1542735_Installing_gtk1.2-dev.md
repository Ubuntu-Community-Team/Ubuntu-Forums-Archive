---
title: "Installing gtk1.2-dev"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by sarma on 2010-07-31
Hi all,

Posts of similar kind are attended here I tried most of them and then seeking your suggestions so please don't flame me.

I was working with this ISP binary [_available here_]("http://www.pjrc.com/arm/lpc2k_pgm/") and it requires gtk1.2-dev. After some research I came to know that on my lucid box I can get only gtk2* which is different from gtk1.2-dev. I downloaded deb packages(dependencies of gtk1.2-dev) of those which were not found by apt and used apt-get to install the others. After all that, I got gtk1.2-dev installed.

Now the problem is that "gtk-config" which is used in (the makefile for) building the binary is not found. The pre-compiled binary given in the site crashes on my lucid machine. It was working fine on my jaunty setup, which is now replaced by lucid.

I'd appreciate any suggestions on what to do to get this source compiled and running on my setup.

Cheers,
Sarma

---

