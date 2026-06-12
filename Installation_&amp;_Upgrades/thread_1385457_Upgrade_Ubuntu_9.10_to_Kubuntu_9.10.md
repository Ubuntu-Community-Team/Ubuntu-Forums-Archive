---
title: "Upgrade Ubuntu 9.10 to Kubuntu 9.10"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by EggMasta on 2010-01-19
This may be a stupid question, but is there any way to upgrade my install of Ubuntu 9.10 to Kubuntu 9.10 and keep my files and settings?

---

### Post by FlyingBuzz on 2010-01-19
just type
**sudo apt-get intsall kubuntu-kde4-desktop**
in terminal
then enter your user's password
And you will be suggested to download approximately 180 megabytes.
Say 'y' to the question.
After the installation ~700Mb of free disk-space dissapears.
Then you will be able to login into KDE4 environment.

---

### Post by EggMasta on 2010-01-19
owner@owner-laptop:~$ sudo apt-get intsall kubuntu-kde4-desktop
E: Invalid operation intsall

Hmm. Any advice? Are you sure thats the package name?

Edit. Woops. Typo

owner@owner-laptop:~$ sudo apt-get install kubuntu-kde4-desktop
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by kansasnoob on 2010-01-19
Look here:

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

And here:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

