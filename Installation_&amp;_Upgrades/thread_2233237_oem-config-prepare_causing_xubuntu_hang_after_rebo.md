---
title: "oem-config-prepare causing xubuntu hang after reboot"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by Toothskin on 2014-07-07
Hi - somewhat new to the ubuntu forums - hope I provide enough info with this issue and if not, I'll report back ASAP.

Recently began a job involving preparing older laptops from my university (atm, a lot of dell latitudes which previously ran Vista or XP) for resale at a surplus store. We nuke them, quickimage with a FOG server, test hardware, then reimage before sale. I'm very new to all of this, but I've been tasked with updating our xubuntu images since we've been having problems with some machines during testing (with flash in particular). Not sure if installing updates will fix those issues, but updating our images for the FOG server is a skill I need to peg down either way

I'm using oem-config-prepare on one of our machines with xubuntu on it after apt-get update and installing recommended security updates, etc. Runs fine but window manager freezes on xubuntu loading screen. Can log into other TTYs but top reveals that basically nothing related to oem-config is running.

Anyone with experience think they can diagnose what could be going wrong here?

---

### Post by sudodus on 2014-07-08
The recommended (and simplest) way to make an OEM install is to activate it at the beginning of the installation by pressing F4. See this link

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

You can also add the OEM feature manually like this

[https://trisquel.info/en/wiki/oem-installation](https://trisquel.info/en/wiki/oem-installation)

---

