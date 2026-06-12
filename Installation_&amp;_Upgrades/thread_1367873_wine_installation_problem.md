---
title: "wine installation problem"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by greenobsession on 2009-12-30
Hi, everyone. So I have this issue when installing wine, everytime I try to install it, it says

margot@greenobsession:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libopenal1 but it is not installable
        Recommends: ttf-liberation but it is not installable
        Recommends: ttf-mscorefonts-installer but it is not installable
E: Broken packages
margot@greenobsession:~$ 



I don't know how to fix it, I've tried the synaptic>edit>fix broken packages and the sudo apt-get update but nothing seems to work.
And hell, I can't install anything cause it always results in broken packages and unmet dependencies.

help will be greatly appreciated. thanks!:)

---

### Post by zvacet on 2009-12-30
System>admin>software sources>check all under ubuntu software and first two under update tab.Reload.

```
sudo apt-get -f install
```

---

### Post by greenobsession on 2009-12-31
thanks zvacet, but I tried it and this is what I get:

margot@greenobsession:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  grub grub-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
margot@greenobsession:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libopenal1 but it is not installable
        Recommends: ttf-liberation but it is not installable
        Recommends: ttf-mscorefonts-installer but it is not installable
E: Broken packages


now i tried installing libopenal1 but it says it has no installation candidate. :/

---

### Post by zvacet on 2010-01-01
System>admin>software sources>check all under ubuntu software and first tow under updates tab.Reload.

```
sudo apt-get -f install
```

---

