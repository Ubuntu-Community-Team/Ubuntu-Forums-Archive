---
title: "Feisty - apmd kubuntu-desktop problem"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by screwloose on 2007-04-23
I just upgraded to Feisty, during the process there was an error with the apmd package. I finished the update but haven't rebooted yet as I decided to clear up any problems before rebooting. I can't seem to resolve a problem between apmd and kubuntu-desktop, does anyone have any suggestions?

If I do a apt-get upgrade I get the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up apmd (3.2.2-8ubuntu2) ...
 * Starting Advanced Power Management daemon...                                                           Segmentation fault
                                                                                                   [fail]
invoke-rc.d: initscript apmd, action "start" failed.
dpkg: error processing apmd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on apmd; however:
  Package apmd is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apmd
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by screwloose on 2007-04-23
Looked at the errors closer, and it looks like I jumped the gun a bit. Kubuntu-desktop is not really involved at its dependent on apmd. 

The real problem is that apmd is segfaulting which I don't think it was doing before the feisty upgrade. I can't seem to find any other forum posts with this problem any suggestions?

---

### Post by screwloose on 2007-05-04
I still have this problem, I have tried removing and reinstalling apmd but it still segfaults.

---

