---
title: "Problem with elementary-tweaks on trusty"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by F1lthym0nk3y on 2015-06-21
Hi all,

I followed the guide here:

[https://docs.google.com/document/d/1ZURJITX-eCrhwP1cImwYHMthBXXHJwLrovIfiZh_vwQ/edit?pli=1](https://docs.google.com/document/d/1ZURJITX-eCrhwP1cImwYHMthBXXHJwLrovIfiZh_vwQ/edit?pli=1)

But have an issue installing elementary-tweaks:

```
sudo apt-get install elementary-tweaksReading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 elementary-tweaks : Depends: gala but it is not going to be installed
                     Depends: slingshot-launcher but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
(trusty)ali3n0id@localhost:/usr/bin$ sudo apt-get install gala slingshot-launcher
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gala : Depends: libgala0 (= 0.2.0~r472+pkg32~ubuntu0.3.1) but it is not going to be installed
        Depends: libmutter0d (= 3.12.2-1ubuntu99~elementary0.3.7) but it is not going to be installed
 slingshot-launcher : Depends: libgtk-3-0 (>= 3.14.0) but 3.12.2-0ubuntu15.2~trusty1 is to be installed
E: Unable to correct problems, you have held broken packages.



```

Any ideas ladies and gents?

---

### Post by Frogs Hair on 2015-06-21
I don't see any updates on that PPA for 26 weeks while there have been many updates in trusty. The PPA may be incompatible or you have other software causing the dependency problem. PPA's in general are use at your own risk   

[https://launchpad.net/~elementary-os/+archive/ub](https://launchpad.net/~elementary-os/+archive/ub)

---

