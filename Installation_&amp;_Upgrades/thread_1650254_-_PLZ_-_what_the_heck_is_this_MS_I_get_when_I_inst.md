---
title: "- PLZ - what the heck is this MS I get when I install vmware workstation 7 ???!!!"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by Objectivity on 2010-12-21
Hi folks,     I installed vmware work station and on final step which was >> &quot; BEFORE YOU CAN RUN VMWARE, SEVERAL MODULES MUST BE COMPILES AND LOADED INTO THE RUNNNG KERNEL &quot;    I click on &quot; INSTALL &quot; and then got this DAMN error :        Unable to build kernel module.    See log file /tmp/vmware-root/setup-15968.log for details.      I HATE IT ! I remember on windows it was easy just 2 clicks ! here seems over 40000 clicks.   Please help.

---

### Post by lemming465 on 2010-12-26
Do you have development tools and kernel headers installed?  Try```

sudo aptitude install build-essentials linux-headers
```
and see if that helps.  Usually the post-install vmware configuration step can be re-run by```
sudo vmware-config-tools.pl
```

---

