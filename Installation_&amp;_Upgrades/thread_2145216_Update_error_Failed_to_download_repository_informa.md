---
title: "Update error: Failed to download repository information"
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by mravkov on 2013-05-14
When I open Update Manager and click on the "Check" button, after a short loading, I get "Failed to download repository information" error. At "Details" there is the following information:
W:Failed to fetch [http://ppa.launchpad.net/ogre-team/ogre/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ogre-team/ogre/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ogre-team/ogre/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ogre-team/ogre/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

If it will help, I'm on 12.04 Ubuntu x86(32-bit).

---

### Post by ibjsb4 on 2013-05-14
There is no ogre-team ppa for 12o4.  It need to be remove or just unchecked from your sources list.

[http://ppa.launchpad.net/ogre-team/ogre/ubuntu/dists/](http://ppa.launchpad.net/ogre-team/ogre/ubuntu/dists/)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

