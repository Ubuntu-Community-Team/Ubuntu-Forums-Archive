---
title: "Automatically remove unneeded dependancies"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by rmjb on 2006-07-31
Hi, I came to Ubuntu from a console based debian and I used aptitude there. In aptitude, when a package I was installing had dependencies, they would be marked **A**uto. And later, if I realised I no longer needed that package, the Auto dependencies would automatically be removed.

Synaptic is not currently doing that, how can I get it to?

- rmjb

---

### Post by Ziox on 2006-07-31
using the command line of course :)

sudo aptitude install...

sudo aptitude remove...

ubuntu and debian is very similar, so this should be very familiar to you.

It's unfortunate that Synaptic/APT doesn't use aptitude...I personally use aptitude all the time, and whenever I help people, i'll always tell them to use aptitude instead of apt-get

---

