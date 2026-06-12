---
title: "Upgrading server 12.10 direct to 14.04"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by gendo_ikari2 on 2014-04-20
I'm seeing lots of talk about desktop, but little to none about server. I have a remote server 12.10 x64 install. With it now being EOL, I was hoping to upgrade it to 14.04. Per this:

[http://fridge.ubuntu.com/2013/03/19/changes-in-ubuntu-releases-decided-by-the-ubuntu-technical-board/](http://fridge.ubuntu.com/2013/03/19/changes-in-ubuntu-releases-decided-by-the-ubuntu-technical-board/)

The key part being "*In the current state of things we allow for  upgrades from a release to the next or from an LTS release to the next  LTS release. The plan here is to change that, so that a user of Ubuntu  12.10 could directly update to Ubuntu 13.10 or 14.04 LTS.*", I was under the impression that once 14.04 went live I would be able to skip over 13.04/10 directly to it. However, I am still only be given the option to upgrade to 13.04. I could manually edit update manager's release-upgrades to switch the prompt from normal to LTS, as has previously been suggested to me, but I'm hesitant to blindly do that without further guidance. 

Does anyone know what the official stance is on this, and, if the plan is to allow a direct update as mentioned in the link above, when this will be implemented? I was hoping to do the update over the Easter long weekend so that I had some extra buffer if things went south. A clean install is only an absolute last resort.

---

### Post by arm-c on 2014-04-22
You can force the upgrade early, however, the auto notification will be pushed after the first point release ~june (See OMG Ubuntu article).  I'd wait a little bit for the LTS notification, or at least search for potential problems.  I'm having issue with VPN and Network Manager.

---

### Post by gendo_ikari2 on 2014-04-22
Hrm, I thought that was just the case for the 12.04 upgrade. If it also the case for 12.10, that presumably means I am left for at least a month past EOL with no support?

---

