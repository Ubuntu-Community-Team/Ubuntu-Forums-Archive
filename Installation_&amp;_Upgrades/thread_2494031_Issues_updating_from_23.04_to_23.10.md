---
title: "Issues updating from 23.04 to 23.10"
date: 2024-01-03
forum: Installation &amp; Upgrades
---

### Post by hadley8899 on 2024-01-03
Hi, Im having some issues updating from 23.04 to 23.10 on my dell laptop

So far ive removed any external PPAs i had from /etc/apt/soures.list and /etc/apt/sources.list.d

Ive fully uninstalled all Nvidia drivers and am currently using the open drivers

The error im getting is 

```
Reading state information... Done


Calculating the changes


Calculating the changes


Could not determine the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


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
```

Ive uploaded the main.log and apt.log, Hopefully it helps

Thanks in advance
Ryan

---

### Post by cigtoxdoc on 2024-01-05
Using only  "sudo do release upgrade", I have upgraded the following PCs from Ubuntu Unity 23.04 to Ubuntu Unity 23.10, all without any problems:

Dell Vostro 3500 laptop
Dell Precision 7720 laptop
Lenovo M80 desktop
hp 840 g1 laptop
hp EliteDesk 800 g1 desktop

All of the above have various versions of Studio Pro (Adobe Acrobat equivalent) and all are dual-boot with Win 11 insider build, Win 10 Pro, and in the case of the Vostro 3500, the original Win XP SP3.  I ignored the warning about unofficial packages

John

---

### Post by deadflowr on 2024-01-05
The difference ppa-purge versus simply disabling a repository is that ppa-purge resets any installed package back to the Ubuntu repository version, if possible.
If you have installed any packages from a ppa that also exist in the regular repositories,
then you must run ppa-purge against the ppa in order to return everything back to Ubuntu's normal state.




Edit:

I see you've attached the log files, unfortunately not many users are going to download them. I am one of them.
If you want people to see them use a pastebin site like this one [https://paste.ubuntu.com/]("https://paste.ubuntu.com/")

---

### Post by hadley8899 on 2024-01-05
Ive upgraded now, I think in the end it would have been easier to just do a fresh install, Ive removed everything under the sun (Apart from snaps) from the system, Disabled everything to do with Nvidia (Which I suspect was actually the source of the issue as I had the Graphics driver PPA enabled to get the latest drivers). Thankyou for the replies

---

