---
title: "APT-GET database is corrupt?"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by MathiasHBG_SWE on 2007-02-22
Today I was re-installing my ATI-drivers and followed the unofficial ATI-wiki at wiki.cchtml.com

Running: 
sudo apt-get install linux-restricted-modules-$(uname -r)

ended up with apt-get freezing at "Configuring linux-restricted-modules-2.6.17-11-generic ..."

After that I cant do anything apt-get related at all, any kind of apt-get/dpkg/synaptic activity detects that there is a package that either isnt installed properly (tells med to run dpkg --configure -a) or that there is a package to be removed.

Ive tried **everything**

sudo apt-get/dpkg remove with all kinds of force... sudo dpkg -r --force-all... you name it... nothing helps! Im stuck! Im at the end of the rope! Is there some apt-get database that is corrupt or what?

I dont know what to do! No one at #ubuntu has been able to help (although many tries, and Im very grateful for that!)

What to do? Please help!

Best regards

Mathias / Sweden

---

### Post by invalid on 2007-02-22
I know this is an obvious assumption, but have you tried to run```
sudo dpkg --configure -a
```as it suggests?

I have seen many identical posts and the poster never did this, which fixed their problems right away.

---

### Post by MathiasHBG_SWE on 2007-02-23
Numerous times, my friend.

Doing it after a frozen install, results in a frosen "Configuring linux-restricted-modules-2.6.17-11-generic ..."

Doing if after a frozen remove actually does not return any errors, but if I then try to do anything else dpkg/apt-get/synaptic-related, the package manager detects the not yet removed package... tries to remove it, and freezes.

---

