---
title: "Upgrade from 18.04 to 20.04 failed ..."
date: 2020-10-08
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2020-10-08
I tried to do a routine command line upgrade from 18.04 to 20.04 and received this error:

An unresolvable problem occurred while calculating the upgrade. 

```
This was likely caused by: 
* Unofficial software packages not provided by Ubuntu 
Please use the tool 'ppa-purge' from the ppa-purge 
package to remove software from a Launchpad PPA and 
try the upgrade again. 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 

Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
```

I have never had this happen before so unsure what to do next?

I took a look at the two logs and the only error seems to be tied to "colord":

```
2020-10-08 10:40:19,407 WARNING Can't mark 'ubuntu-desktop' for upgrade (E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.)
2020-10-08 10:40:19,807 ERROR Dist-upgrade failed: 'Broken packages after upgrade: colord'
2020-10-08 10:40:19,808 DEBUG abort called
```

---

### Post by CelticWarrior on 2020-10-08
A release upgrade is anything but routine.

Before giving it another go please assure the system is fully updated: 
```
sudo apt update && sudo apt full-upgrade
```

If there are any error messages please post them here.

---

### Post by michael351 on 2020-10-08
> **CelticWarrior said:**
> A release upgrade is anything but routine.

Before giving it another go please assure the system is fully updated: 
```
sudo apt update && sudo apt full-upgrade
```

If there are any error messages please post them here.

I did that prior to the upgrade attempt. All packages are up to date.

---

### Post by SeijiSensei on 2020-10-08
Are you using any PPAs?  If so, disable them and rerun "sudo apt update".

---

### Post by michael351 on 2020-10-13
I am at a loss trying to upgrade from 18.04 to 20.04 .... I tried 
using ppa-purge and that didn't work as intended. It needs to know exactly which ppa to purge. I have no idea which one is preventing the 20.04 upgrade.As
 the log shows above, something with 'colord' seems to have stopped the installation.

I use Ubuntu as a desktop and media server for my home theater center (Kodi). I don't mess around in the operating system and so much of what is happening during the upgrade is not familiar. I hesitate messing around with PPA's.

Perhaps it is just best to stay with 18.04 (works great) until it expires and then upgrade to 20.04 as a clean install a few years from now when LTS for 18.04 is discontinued.

---

