---
title: "resetting software channels from trusty to back to saucy"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by bigwildman on 2013-10-20
I am unable to update, and add repos.  I upgraded to Ubuntu 13.10, but it now says I am using the developmental trusty channels, and I need some advice on how to reset the channels and get back to the stable release.
 
{Edit: I am now able to update, but I am still unable to install repos or open software sources gtk, any advice would be greatly appreciated.}

---

### Post by heir4c on 2013-10-21
In Your sourceslist you can change the word 'trusty' to 'saucy' and do than a update and upgrade.

Open a terminal and type:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by bigwildman on 2013-10-21
Thanks, that was what I needed. Now I am able to update properly, but  I am still unable to open the software sources program and edit my update settings and repo, and  in addition I am unable to enable any new repos (even via command line). Any suggestions?
Also it is still saying that I am using Ubuntu 14.04

---

### Post by heir4c on 2013-10-21
How you upgrade to 13.10?
Can you open SoftwareCenter and than open from there the software sources?

---

### Post by bigwildman on 2013-10-22
I upgraded via command terminal 2 days before the official release. But when I try to open the software sources it just updates the software list and doesn't open.

---

### Post by howefield on 2013-10-22
What was the command you used to initiate the upgrade ?

---

