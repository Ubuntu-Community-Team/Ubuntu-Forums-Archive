---
title: "Apt-get install not working"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by fnando on 2005-07-14
Hello there! I'm trying to install some programs using apt-get but no matter what package I choose, it gives the error E: Couldn't find package PACKAGE_NAME....

I tried:

sudo apt-get install sun-j2re1.5
sudo apt-get install bluefish
sudo apt-get install flashplayer-mozilla

I receive the message below for some tries:

> Package PACKAGE_NAME is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


How do I resolve this? Thanx a lot!

---

### Post by badrinarayan on 2005-07-14
All these are in the universe repository. Follow the instructions at [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) and try again.

Regards
Badri

---

### Post by fnando on 2005-07-14
Thank you so!!! I'll try that!

---

