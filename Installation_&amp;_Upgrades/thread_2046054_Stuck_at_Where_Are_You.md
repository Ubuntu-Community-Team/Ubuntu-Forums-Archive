---
title: "Stuck at Where Are You"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by chrisl121212 on 2012-08-22
Hi, I am trying to dual-boot Windows 7 and Ubuntu 12.04. I got the installation working just fine, but once the copying files is done, I come back and click continue after selecting my location to find out that the continue button is not working. I restarted several times trying to get this installation to work, tried disabling internet like I read I should do, the CD is fine, and I keep reformatting the partition every attempt. I don't know what is going on and I would appreciate if someone could help.

---

### Post by oldfred on 2012-08-24
Maybe you have this issue?

Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it is text based and also does not use the slideshow.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

