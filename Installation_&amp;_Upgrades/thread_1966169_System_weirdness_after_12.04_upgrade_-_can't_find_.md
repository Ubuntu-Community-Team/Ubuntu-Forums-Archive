---
title: "System weirdness after 12.04 upgrade - can't find hardly anything!"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by petermg on 2012-04-26
I'm using a Gateway Netbook LT4004u which worked great on 11.10.  After the upgrade lightdm wouldn't start up, so I ran "dpkg --configure -a" and then it would run, but it seems like there are many things missing.  When I click on the search button it cannot find ANYTHING.  And it only shows a home icon down below, the white home/house looking icon.  I'm totally lost.  If I log into tty1 I get this message:
```
492 packages can be updated.
```
How do I update them?  Seems like the upgrade didn't fully take??  Also I don't see any network manager and I don't have an icon to log off either.

Also I can't get an IP address when I connect my Ethernet, well I do but it's an ICS (internet connection sharing) IP.  I had ICS running on eth0.  I don't know how to make it a normal connection so I can try to do an update via the command line, or if that will even be needed.  Please help I'm totally lost.

---

### Post by jadtech on 2012-04-26
if you have net connection you can do them updates right from the update manager ..

---

### Post by petermg on 2012-04-26
> **jadtech said:**
> if you have net connection you can do them updates right from the update manager ..

Ok well I got the network working, I edited the NetworkManager.conf and changed eth0 from shared to auto.  Then from the command line in tty1 I did ```
sudo apt-get upgrade
``` and now it's running a bunch of upgrades on packages.  Will update with results.

---

### Post by jadtech on 2012-04-26
hope it works good luck

---

