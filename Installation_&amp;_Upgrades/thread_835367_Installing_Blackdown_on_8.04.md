---
title: "Installing Blackdown on 8.04"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by luccom on 2008-06-20
I am trying to install Blackdown Java2 1.4: j2re1.4  but I can`t find the package in Synaptic this is what I have in my sources.list

```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe

deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted

deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
```

I want to install Blackdown because I need to connect to a old web interface for a cisco pix.

---

### Post by avtolle on 2008-06-20
I've some bad news; Blackdown is no more. [http://www.the-love-shack.net/2007/08/30/blackdown-java-retires/](http://www.the-love-shack.net/2007/08/30/blackdown-java-retires/)

---

### Post by luccom on 2008-06-23
Any Idea what I can do to install a old java version ?

---

### Post by Sef on 2008-06-23
> I want to install Blackdown because I need to connect to a old web interface for a cisco pix.

Are you sure you need to connect with an old version of java?

---

### Post by luccom on 2008-06-23
I have A old Cisco PIX and the web interface is only compatible with Java JRE 1.4 and upgrading the PIX is not a option.

---

### Post by Sef on 2008-06-23
This is the java site where you can download an [old version of java]("http://java.sun.com/products/archive/") including the one you want.

---

