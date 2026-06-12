---
title: "install Error: Wrong architecture 'i386'"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by Juvencio on 2011-01-12
osdlyrics_0.3.20100604-1~lucid1_i386.deb Ubuntu x86 32 bit deb package for Ubuntu 10.04 or later wont install.

I'm running ubuntu 10.4 64bit.

My question is why you can't install 32bit programs on a 64bit system?
If you can then how do I do it?

64bit should run 32bit due to the resin that a 16bit system ran 8bit games/programs.
I know in window 7 you can install 32bit programs on 64bit system.

---

### Post by davidmohammed on 2011-01-12
you can install 32 bit packages on 64 bit - as described [here]("https://help.ubuntu.com/community/32bit_and_64bit").  I suspect you have installed the ia32-libs package.

---

### Post by Juvencio on 2011-01-12
Tanks davidmohammed will read that for future, but I solved how to install osdlyrics on 64bit.

Import the PPA repository:
sudo add-apt-repository ppa:osd-lyrics/ppa

Edit your apt source:
sudo gedit /etc/apt/sources.list

Append the following ppa address:
deb [http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu](http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu](http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu) jaunty main

Add signing key:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4865CF4F

Update & install:
sudo apt-get update
sudo apt-get install osdlyrics

---

