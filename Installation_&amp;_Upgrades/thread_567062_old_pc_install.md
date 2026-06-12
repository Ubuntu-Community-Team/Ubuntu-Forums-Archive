---
title: "old pc install"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by cheshire on 2007-10-04
I have a Toshiba Satellite 2140 xcds laptop w/ AMD K6-2 450mhz, 192MB RAM (maxed out), 4GB HD, 2MB onboard video RAM, that I would like to install some version of Ubuntu on.  I have read posts about server installs on low resource systems and would like to give it a try.  My problem is that the laptop has no ethernet connection.  I want to install a wireless pcmcia card after the operating system is setup.  I am new to linux, so maybe I am wrong, but I assume you need an internet connection to add packages you want to the base server install.  Is that correct?  Is there anyway to set up this machine so that it is useable under Ubuntu?  I am just looking to do email, web browsing, and maybe word processing.  Thanks.

---

### Post by mlentink on 2007-10-04
You could give Xubuntu a try, that should work with those specs. You would only need the 'net to install additional packages. Which you would probably need to install drivers for that WiFi card. Couldn't you borrow a PCMCIA card to get it wired first? I stall have a 3Com lying around here just for purposes like that, someone near you might have one too

---

### Post by cheshire on 2007-10-04
Haven't found a wired pcmcia card yet.  I am still looking though.  I will give installing Xubuntu a try and see.

---

### Post by maybeway36 on 2007-10-04
If you need the ndiswrapper packages, check out:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/")
The packages you want are probably **ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb** and **ndiswrapper-common_1.38-1ubuntu1_all.deb**. You should be able to fit them on a floppy to get them to the laptop, and you can update them once internet is working.

---

### Post by Gremlinzzz on 2007-10-04
[http://distrowatch.com/](http://distrowatch.com/)
mepis has a older computer system
[http://distrowatch.com/?newsid=04496](http://distrowatch.com/?newsid=04496)

---

