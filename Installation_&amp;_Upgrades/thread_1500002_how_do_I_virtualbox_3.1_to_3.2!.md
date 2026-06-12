---
title: "how do I virtualbox 3.1 to 3.2?!?"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by anystupidname1 on 2010-06-02
Running karmic using download.virtualbox.org/../debian karmic non-free  repo
aptitude update && aptitude search virtualbox
does not show virtualbox-3.2?!? (only 2.0, 3.0, and 3.1)
Trying to install the virtualbox-3.2 deb from their site fails with  conflict message because of 3.1
I've upgraded this box from virtualbox3.0 to 3.1 for the last year or so
What am I missing? Any help appreciated, thanks!

---

### Post by maybeway36 on 2010-06-02
Try removing VirtuaBox 3.1, then installing 3.2. This shouldn't get rid of your virtual machines, because they're stored in your home directory in ~/.VirtualBox

---

### Post by anystupidname1 on 2010-06-02
Any idea why 3.2 isn't listed from the PPA?

---

### Post by anystupidname1 on 2010-06-03
bump?

---

### Post by Dennis N on 2010-06-03
Beginning with Version 3.2, the VirtualBox PPA signing key was changed by Oracle. Add the new signing key, reload the package lists, and 3.2 will be then be available through Synaptic.

get the new key at:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by anystupidname1 on 2010-06-10
Ah! Thank you!

---

### Post by RottNKorpse on 2010-11-21
thank you for the advice Dennis but for me that didnt work it never reloaded to show 3.2 in synaptic.

I uninstalled 3.1 and installed 3.2 so that worked.

I have 64bit 10.10 so maybe thats why the key option didnt work

---

### Post by anystupidname1 on 2010-12-15
The skinny from Dennis' link [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)```
sudo -s -H
apt-get clean
rm /var/lib/apt/lists/* /var/lib/apt/lists/partial/*
apt-get clean && apt-get update
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get install virtualbox-3.2
```

---

