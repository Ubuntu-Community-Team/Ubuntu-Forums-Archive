---
title: "issues installing ogre 3d on 10.4"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by stuckne1 on 2010-08-22
Hi, I'm a bit new to linux and after using google, I hit ubuntu with the commands...

sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get cleanall

but in a logical order to try to solve my problem. 

First I did this...

I added the lines...(one at a time to the repository)

deb [http://ppa.launchpad.net/ogre-team/ogre/ubuntu](http://ppa.launchpad.net/ogre-team/ogre/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/ogre-team/ogre/ubuntu](http://ppa.launchpad.net/ogre-team/ogre/ubuntu) karmic main 

After much frustration the farthest I can get seems to be a screen with this...


steven@steven-laptop:~$  sudo apt-get install libogre-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libogre-dev: Depends: libogremain-1.7.0 (>= 1.7.0-1~ppa2) but it is not going to be installed
               Depends: libogrepaging-1.7.0 (>= 1.7.0-1~ppa2) but it is not going to be installed
               Depends: libogreterrain-1.7.0 (>= 1.7.0-1~ppa2) but it is not going to be installed
               Depends: libogreproperty-1.7.0 (>= 1.7.0-1~ppa2) but it is not going to be installed
               Depends: libogrertshadersystem-1.7.0 (>= 1.7.0-1~ppa2) but it is not going to be installed
E: Broken packages

Any advice greatly appreciated!

---

### Post by stuckne1 on 2010-08-25
Well, got it installed so disregard.

---

