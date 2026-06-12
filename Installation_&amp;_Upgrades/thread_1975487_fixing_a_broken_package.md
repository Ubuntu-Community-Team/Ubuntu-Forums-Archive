---
title: "fixing a broken package"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by ajhbergen on 2012-05-07
After upgrading to Ubuntu 12.04 I tried to replace gimp 2.6 from the distro by gimp 2.8 from the repo otto-kesselgulasch/gimp. I have neglected to run autoremove on gimp 2.6.
The gimp has been removed but I cannot re-install it from the main source nor from the external repository. I get the following message 
"The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (<= 2.6.12-z) but 2.8.0-1ubuntu0ppa3~precise is to be installed
        Depends: gimp-data (<= 2.6.12-z) but 2.8.0-1ubuntu0ppa3~precise is to be installed
E: Unable to correct problems, you have held broken packages."

How can I repair the package information? I have tried apt-get -f install, apt-get build-dep 
to no avail.

Anybody can help me with this problem?

Thanks in advance

---

