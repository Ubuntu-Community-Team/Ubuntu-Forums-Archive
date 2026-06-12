---
title: "How should I Update Ubuntu?"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by Dark Aspect on 2007-10-02
Ok I have Ubuntu 7.04 and with the new version of 7.10 coming out soon I was curious to know how I should update.I would rather not do a clean install of Ubuntu every six mouths so is there a way to update Ubuntu to one version to another with out losing my data?Are there any disadvantages of doing such?

What I want basically is to be able to install the new version of Ubuntu like I would a service pack on windows.someone I knew told me it was possible but I did a clean install from Ubuntu 6.10 to 7.04,so Is it possible?

Farther more if I updated instead of doing a clean install wouldn't that break the 7.04 packages I have installed?

---

### Post by pay on 2007-10-02
You can update it a few ways. I normally change my sources.lst to a gutsy one and then type ```
sudo aptitude dist-upgrade
``` You can also do it with ```
sudo update-manager --check-dist-upgrades --devel-release --proposed --dist-upgrade
```(which is the official method. For some people it breaks some things but all you packages should be upgraded.

---

### Post by Dark Aspect on 2007-10-02
Is it possible to do it off line with a Ubuntu 7.10 disc (when they come out) as an alternative to downloading via terminal?

The reason I ask is my internet might cut out (its a bad connection) and if it did in the middle of a OS upgrade then I might be in bad shape to the point where I might have to do a clean install anyway.

---

### Post by pay on 2007-10-02
You can use the cd to update. just add your cdrom with apt-cdrom```
sudo apt-cdrom add
```If your internet cut out you can still upgrade, you won't even need to download the debs you already downloaded because it just stores those debs untill they are all downloaded and installs them at the end. If something actually goes wrong during the installation of the debs you can just restart and loginto the recovery console and type ```
sudo aptitude dist-upgrade
```and the installation will continue from where it left off.

---

### Post by Dark Aspect on 2007-10-03
Thank you,I think thats all I need.I'll try it the first way since I can resume downloading the update.I have to wait 16 more days for the next release anyway:):)

---

