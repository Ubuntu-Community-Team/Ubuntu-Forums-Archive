---
title: "Broken Packages preventing ugrades - Steam appears to be the root of the issue"
date: 2020-07-07
forum: Installation &amp; Upgrades
---

### Post by tmaxcontact on 2020-07-07
Hi,

Hopefully I'm not breaking any rules. I've scanned the forums for potential fixes but come up empty handed.

sudo apt update followed by sudo apt upgrade leads to the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 steam:i386 : Conflicts: steam-launcher but 1:1.0.0.64 is to be installed
              Conflicts: steam-launcher:i386
 steam-devices : Conflicts: steam-launcher but 1:1.0.0.64 is to be installed
                 Conflicts: steam-launcher:i386
E: Broken packages

___________________________________________________________

I don't know if there's any connection between the two, but software updater works perfectly fine. 

Steam also updates upon launch as per usual. 

When I run sudo apt update I'm told there are 22 packages with requiring upgrades so I'm hopeful of finding a fix. 

Thanks in advance.

---

### Post by dino99 on 2020-07-07
Better to ask on Steam forum

but which ubuntu is it ? which steam version/source is it ?

---

### Post by tmaxcontact on 2020-07-07
It's Ubuntu 20.04 LTS and Steam API:  v020 Package versions: 1591251555

---

### Post by rsteinmetz70112 on 2020-07-08
Why is stream a 386 version?

---

### Post by ubfan1 on 2020-07-08
Please post the output of apt-cache policy steam-installer
The expected version from the standard repos is 61, pool/multiverse/s/steam/steam-installer_1.0.0.61-2ubuntu3_all.deb
You may picking up steam from a repo you added.

---

