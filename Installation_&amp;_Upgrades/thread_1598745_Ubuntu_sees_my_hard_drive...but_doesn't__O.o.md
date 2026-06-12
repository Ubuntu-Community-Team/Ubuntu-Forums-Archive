---
title: "Ubuntu sees my hard drive...but doesn't  O.o"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by GmAz on 2010-10-16
Trying to do a fresh install of Ubuntu 10.10 on my computer.  I have a known working 250Gb drive I want to install it on.  I boot to the live session, click install and when it asks me to choose a hard drive, it sees my disk as sda1, but says there is no partition.  Funny because GParted says there is.  In GParted, I delete the partition and made a new one, formatted it to ext4 and still, the installer sees nothing.  I can mount the drive and use it, but can't install to it.  My other two drives can be used to install, but one is my data drive and I will not use that one, its actually disconnected now so there is no 'OH ****...WRONG DRIVE' problems.  My other drive is my Windows 7 install that I don't want gone either, but Ubuntu can used that drive too just fine.  What gives.  How can I get ubuntu to install on that drive.

[[EDIT]]

NEVERMIND!!!  I found this thread:  [http://ubuntuforums.org/showthread.php?t=1344355&highlight=install+won't+hard+drive](http://ubuntuforums.org/showthread.php?t=1344355&highlight=install+won't+hard+drive)  and did sudo apt-get install dmraid and found it was already installed so I decided to remove it.  Bye bye dmraid and hello hard drive in the installer.

---

