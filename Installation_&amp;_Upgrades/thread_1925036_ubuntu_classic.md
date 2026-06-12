---
title: "ubuntu classic"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by louis.roux on 2012-02-13
I upgraded to 11.10 and was installing classic desktop by the following command:

sudo apt-get install gnome-panel

but it got interrupted before it was complete and now I get the following message on my terminal when I try to continue the install:

 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

What does that mean?  How do I manually run that command to correct the problem?

---

### Post by uRock on 2012-02-13
Copy & paste into a terminal.```
sudo dpkg --configure -a
```

---

### Post by louis.roux on 2012-02-14
did that but it the says the following:

dpkg: error: parsing file '/var/lib/dpkg/updates/0003' near line 0:
 field name

---

### Post by plucky on 2012-02-14
> **louis.roux said:**
> did that but it the says the following:

dpkg: error: parsing file '/var/lib/dpkg/updates/0003' near line 0:
 field name

Remove all the files in that directory with ```
sudo rm -rf /var/lib/dpkg/updates/*
``` then run ```
sudo apt-get update
``` and post the output.

Good Luck

---

### Post by louis.roux on 2012-02-14
Plucky that worked, thank you

---

