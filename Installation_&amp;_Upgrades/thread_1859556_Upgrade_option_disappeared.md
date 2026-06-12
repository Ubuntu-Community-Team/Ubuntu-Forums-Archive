---
title: "Upgrade option disappeared"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by driven1 on 2011-10-14
While running apt-get to load an application, the software center pops up and announces that 11.10 is now available. Against my better judgement I clicked on the upgrade button. After about 20 minutes all of the headers loaded, and the installer warned that it would take about 5 days at current data rates to download all of the necessary packages. I clicked cancel, and everything went back to normal. So far, so good.

Later, when I had a faster, more reliable connection, I thought I would try again. I ran ```
sudo apt-get update
``` then ```
apt-get dist-upgrade
``` I was promptly informed that my system was up to date and that there where no new packages to install. Huh? What happened to 11.10? So, I tried ```
apt-get autoclean
``` which removed the headers from my first attempt, but that didn't help any. I did apt-get update after every step. I even went back to the software center, but it no longer indicated the availability of a distro upgrade. What am I missing here? How do I get apt to install the upgrade? Thanks

---

