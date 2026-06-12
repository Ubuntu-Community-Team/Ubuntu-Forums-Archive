---
title: "Qucs is gone after upgrade from 12.04 to 12.10"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2012-10-29
After an upgrade from 12.04 to 12.10, Qucs (the circuit simulator) is gone and there seems to be nothing to replace it.  I used that frequently.  What was supposed to be the new/replacement circuit editor and simulator in 12.10?

---

### Post by dino99 on 2012-10-29
[https://launchpad.net/ubuntu/+source/qucs](https://launchpad.net/ubuntu/+source/qucs)

---

### Post by arvevans on 2012-10-29
Yes, that helped me to find and re-install Qucs.  Thanks for the pointer.

Since doing yesterday's upgrade I have found several software packages that were removed as part of the upgrade process.  It is frustrating and time consuming to find and re-install these packages.  Seems the upgrade could have been done better.

---

### Post by fransfrans on 2012-12-23
The problem is that Qt4 was removed from ubuntu since 12.10. Qucs still uses Qt3.
However, I have made a qucs-qt4 port and it can be downloaded from a PPA
if you add this to your sources you will be able to install qucs:
ppa:fransschreuder1/qucs

or from the command line:
sudo apt-add repository ppa:fransschreuder1/qucs
sudo apt-get update
sudo apt-get install qucs

The port has been added to the official qucs sourcecode, and I will try to get it back into the official debian/ubuntu repository

---

### Post by aishen on 2013-01-09
Thank you for this ppa : I was waiting for a long time to get qucs in qt4
Happy New Year

---

### Post by fransfrans on 2013-01-09
You're welcome! Please take in mind that this qt4 version is not yet very stable, expect a few bugs. I am (with a new team) working hard on the qt4 version to get everything stable, as well as implementing new functions in qucs.

---

### Post by aishen on 2013-01-21
> **fransfrans said:**
> The problem is that Qt4 was removed from ubuntu since 12.10. Qucs still uses Qt3.
However, I have made a qucs-qt4 port and it can be downloaded from a PPA
if you add this to your sources you will be able to install qucs:
ppa:fransschreuder1/qucs

or from the command line:
sudo apt-add repository ppa:fransschreuder1/qucs
sudo apt-get update
sudo apt-get install qucs

The port has been added to the official qucs sourcecode, and I will try to get it back into the official debian/ubuntu repository

Thanks a lot :)

---

