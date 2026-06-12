---
title: "Unable to Install Ubuntu SDK"
date: 2014-01-06
forum: Installation &amp; Upgrades
---

### Post by cromat on 2014-01-06
I keep getting dependency issues with the PPA unable to install due to dependency which will not be installed. I have no other broken packages on the system.  Is there something wrong with the PPA?

I am on Ubuntu 13.10 on a XPS 13 FHD Dev Edition.

---

### Post by ian-weisser on 2014-01-07
> **cromat said:**
> Is there something wrong with the PPA?

What's the dependency problem?

---

### Post by cromat on 2014-01-07
Setting up unity-action-doc (1.0.0+13.10.20130716bzr31saucy0) ...
Setting up xserver-common (2:1.14.5-1ubuntu2~saucy1) ...
Setting up xserver-xorg-core (2:1.14.5-1ubuntu2~saucy1) ...
Setting up qtdeclarative5-doc-html (5.0.2-6ubuntu5~saucy1~test1) ...
Processing triggers for libc-bin ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-sdk : Depends: ubuntu-sdk-libs-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
&#10140;  ~  sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
&#10140;  ~  
&#10140;  ~  sudo apt-get install ubuntu-sdk-libs-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-sdk-libs-dev : Depends: libqt5v8-5-dev but it is not going to be installed
                       Depends: libqt5xmlpatterns5-dev but it is not going to be installed
                       Depends: qtscript5-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by ian-weisser on 2014-01-07
After adding the PPA, did you refresh the package cache with **sudo apt-get update** ?

"it is not going to be installed" usually either means a dependency conflict, or it's simply not in the package cache.
Since qtscripts5-dev is only available from PPA (it's not in the Ubuntu repositories), a conflict seems unlikely.

---

### Post by cromat on 2014-01-07
Yes, added ppa, apt-get update , then install. I also tried adding the qt ppa incase but no luck.

---

### Post by cromat on 2014-01-09
Seems to be an issue with the ppa. If I install it through Ubuntu Software Center everything works fine.

---

