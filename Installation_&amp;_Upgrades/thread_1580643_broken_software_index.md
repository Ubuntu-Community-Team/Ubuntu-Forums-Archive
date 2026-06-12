---
title: "broken software index"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by rswaraj on 2010-09-23
Hi,
I've been using ubuntu 10.04 for a quite long time. Now ive got a problem in update and upgrades. Whenever i try to update or install or remove any software, it shows 'software index is broken'. 

I tried to use sudo apt-get install -f command, but it showed the following message:
swaraj@swaraj-laptop:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

how to overcome this problem?? is it serious?? plz help!!

---

### Post by plucky on 2010-09-24
> **rswaraj said:**
> Hi,
I've been using ubuntu 10.04 for a quite long time. Now ive got a problem in update and upgrades. Whenever i try to update or install or remove any software, it shows 'software index is broken'. 

I tried to use sudo apt-get install -f command, but it showed the following message:
swaraj@swaraj-laptop:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

how to overcome this problem?? is it serious?? plz help!!

That usually means you have two package managers open at the same time.If you have Synaptic or Update Manager open,close them and try again.

Good Luck

---

