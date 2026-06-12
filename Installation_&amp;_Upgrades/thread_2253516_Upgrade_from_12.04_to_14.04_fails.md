---
title: "Upgrade from 12.04 to 14.04 fails"
date: 2014-11-20
forum: Installation &amp; Upgrades
---

### Post by elias14 on 2014-11-20
Hi, 

I am trying to upgrade from 12.04 to 14.04. When I run 
```
sudo do-release-upgrade
```
I get the following error:

```
Checking package managerReading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done


Calculating the changes


Calculating the changes


Could not calculate the upgrade


An unresolvable problem occurred while calculating the upgrade.


This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu


If none of this applies, then please report this bug using the
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.




Restoring original system state
```

I would prefer not to reinstall the entire system.
I tried to remove all NVIDIA drivers and unselected all other sources in the Update Manager, with no different outcome.

Any help would be appreciated!

---

### Post by irv on 2014-11-20
Before you can upgrade from 12.04 to 14.04 you have to do all the updates then upgrade to the next release from the one you are on and then go by steps to get to the latest release. With that said the best is to do a fresh install of the new release after backing up all your data.

---

### Post by deadflowr on 2014-11-20
Do you have any ppa's?
If so, disable them.

---

### Post by elias14 on 2014-11-20
After unselecting all software sources but the (main) one, I could perform the update.
Then, I could turn them on again. Most of the packages are still running, some I had to reinstall.

So, a direct upgrade from 12.04 to 14.04 can work :)

---

