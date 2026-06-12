---
title: "upgrading breezy to dapper: problem network"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by biasquez on 2006-09-01
hi, I changed my /etc/apt/sources.list to use dapper & breezy repositories and then:
apt-get update
apt-get dist-upgrade
apt-get upgrade

Now i have 2 kernel, 2.6.12-10 and 2.6.15-26. first kernel starts but network doesn't work (not such device eth0) and secondo kernel doesn't start (black screen). can i fix this problem? thz

---

### Post by randell6564 on 2006-09-01
> **biasquez said:**
> hi, I changed my /etc/apt/sources.list to use dapper & breezy repositories and then:
apt-get update
apt-get dist-upgrade
apt-get upgrade

Now i have 2 kernel, 2.6.12-10 and 2.6.15-26. first kernel starts but network doesn't work (not such device eth0) and secondo kernel doesn't start (black screen). can i fix this problem? thz

This is a bit confusing to me since I never had to manually edit my /etc/apt/sources.list in order to upgrade to Dapper!

I installed Breezy and once I connected to the net I recieved an upgrade notification from 'Update Manager' that there was a newer version of ubuntu available.

After I upgraded, my sources.list was naturally changed to the Dapper repo's.

---

### Post by linear on 2006-09-01
Did you really mean:
> **biasquez said:**
> dapper **&** breezy repositories

You shouldn't mix Dapper and Breezy repos. If you did do this, start with a clean sources.list and attempt to fix things using instructions here: [http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

