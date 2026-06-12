---
title: "please help! i suspect a broken system!"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by eyefry on 2008-05-30
hi,

i'm a complete newbie and a lay user at that, so please bear with me if this sounds like a silly question (and please help!):

ever since I tried installing timidity using guidelines provided on the ubuntu message boards ([http://ubuntuforums.org/showthread.php?t=276495](http://ubuntuforums.org/showthread.php?t=276495)), i've been getting errors every time i try to install an update or make an upgrade to pretty much any software on my ubuntu hardy heron machine. whenever i run the update manager and try to install a recommended update, i get the following error:

E: timidity: subprocess post-installation script returned error exit status 2
E: timidity-interfaces-extra: dependency problems - leaving unconfigured

i'm smart enough to know that this can't be a good thing, i.e., if i'm unable to get important updates to the OS.

i further tested for this error on terminal with an "apt-get upgrade" command, and the following error message was generated:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
eyefry@eyefry-desktop:~$ y
bash: y: command not found
eyefry@eyefry-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up timidity (2.13.2-19ubuntu1) ...
/etc/default/timidity: 10: Syntax error: "(" unexpected
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of timidity-interfaces-extra:
 timidity-interfaces-extra depends on timidity (= 2.13.2-19ubuntu1); however:
  Package timidity is not configured yet.
dpkg: error processing timidity-interfaces-extra (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 timidity-interfaces-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)

my question is, will i have to reinstall ubuntu? if so, how do i go about this? i've never done so before, and i'm unsure of what to do. i'll be forever grateful if someone clued me into what's happening to my machine.

thanks!

---

### Post by zvacet on 2008-05-30
```
sudo dpkg --configure -a
```

or 

```
sudo dpkg --configure timidity
```

---

### Post by Pumalite on 2008-05-30
Try:
```
sudo dpkg --comfigure timidity-interfaces-extra
```

---

