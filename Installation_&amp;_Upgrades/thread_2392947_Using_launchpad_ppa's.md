---
title: "Using launchpad ppa's"
date: 2018-05-27
forum: Installation &amp; Upgrades
---

### Post by garyr2 on 2018-05-27
I have a Debian based system with a QEMU virtual installation for Kubuntu 17.10. I have been trying get a copy of FreeCAD-daily setup and have become very frustrated. I have found bits and pieces that are applicable most of which don't work. Many want me to use a Ubuntu app that doesn't exist on my system nor have I been able to install it from the  normal repository. Many sites outline how to setup launchpad for uploading applications. 

I really need to have a step by step instruction to install everything preferably from the commend line. I could also use some guidance on finding launchpad apps. I find this whole area very confusing. I've been using Debian for almost 20 years so am not exactly a newby.

Please help

garyr

---

### Post by TheFu on 2018-05-27
Generally, launchpad PPAs provide the exact instructions to install the new PPA as a source. **sudo add-apt-repository {copy/paste from the PPA instructions}**
[https://launchpad.net/~freecad-maintainers/+archive/ubuntu/freecad-daily](https://launchpad.net/~freecad-maintainers/+archive/ubuntu/freecad-daily) says ...
```
sudo add-apt-repository ppa:freecad-maintainers/freecad-daily
sudo apt-get update
```
simple.

Whether the daily version works or not is a very different question.  I've also gone with the stable PPAs myself,but I've never tried any CAD on Linux.

Then you do a **sudo apt install {package}**
That's it.

---

### Post by again? on 2018-05-28
I just installed freecad-daily in Xubuntu 17.10. (same default repositories as Kubuntu 17.10)
It's as simple as TheFu says and it works.
```
sudo add-apt-repository ppa:freecad-maintainers/freecad-daily
sudo apt-get update
sudo apt install freecad-daily
```

May care to read this page.
[http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html](http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html)

Take note of the section about ppa-purge.
If you have package conflicts caused by an added ppa, use ppa-purge to disable the
ppa and downgrade packages to the official releases.

---

### Post by garyr2 on 2018-05-28
Thanks for the prompt replies. I have just two questions left.
1. is the daily freecad uploaded automatically or do I have to run apt-get update and apt-get upgrade to get the latest version.
2. Where do I find a list of the ppa's available on Launchpad.


garyr

---

### Post by TheFu on 2018-05-28
You have to update/upgrade daily if that is what you want.  IMHO, daily PPAs should only be used by developers, not end users.  I hope it turns out well for you, but wouldn't bet on it.

PPAs come and go all the time. I don't know of any list. When I see that the Ubuntu repo version is not at the level I need, I'll google for the "{package-name}+PPA".  Using too many PPAs is a good way to get into "APT hell", so it really shouldn't be the go-to method.  Most people learn this the hard way.

PPAs are not "approved".  OTOH, most F/LOSS projects are "just people" trying to do their best.

---

