---
title: "release upgrade failed"
date: 2022-09-18
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2022-09-18
Hello,

My actual release: 22.04.
When try to upgrade using **do-release-upgrade**, the following message appears:

[COLOR=#0000cd][FONT=courier new]An unresolvable problem occurred while calculating the upgrade. 

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
=== Command detached from window (Sun Sep 18 14:30:03 2022) ===
=== Command terminated with exit status 1 (Sun Sep 18 14:30:13 2022) ===[/FONT][/COLOR]

In main.log I found this error:
[COLOR=#0000cd][FONT=courier new]2022-09-18 15:55:32,702 ERROR Dist-upgrade failed: 'Broken packages after upgrade: gnome-control-center, gnome-shell, libgirepository-1.0-1, ubuntu-desktop'.
[/FONT][/COLOR]
Should I reinstall these packages ?
Thanks.

---

### Post by Impavidus on 2022-09-18
You can try, but I can't guarantee it will work. Could this have something to do with the Python version mix-up in your other thread?

---

### Post by py-ohayo on 2022-09-19
I just tried reinstalling the packages and running the upgrade.
No more errors in **main.log**, but upgrade aborted with same message.
I searched for the word "error" in **apt.log**, but apparently there are no errors.
It is difficult to parse **apt.log** because it is much bigger (266 KB) than **main.log** (less than 1 KB).
This problem is probably somehow related to the mix-up of Python, but how to know if it is?

---

