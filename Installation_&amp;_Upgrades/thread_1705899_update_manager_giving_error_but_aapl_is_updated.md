---
title: "update manager giving error but aapl is updated"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by kriti.mysty on 2011-03-13
i had no internet for a duration of 2 months. and i just got net.. my update manager has been working a lot as a result. but, after the downloading of update. while its running the pacakegs.. it says completed with error, exit status 2 2.. also, when i remove any package through ubuntu software center, it gets 90% completed and gives the following error

"Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the restart(8) utility, e.g. restart acpid 
acpid start/running, process 3061 
package libqtgui4 exist 
QT_VERSION = 4 
cd: 160: can't cd to /usr/local/bin/ztemtApp/zteusbserial/2.6.32 
dpkg: error processing crossplatformui (--configure): 
 subprocess installed post-installation script returned error exit status 2 
"
downloading, generally gives me,
"The action would require the installation of packages from not authenticated sources."
even though its just a normal package like empathy and audacity..

im not a programmer, im new with ubuntu.
any help would be appreciated.
thanks in advance

---

### Post by mörgæs on 2011-03-13
What happens if you boot the machine and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

?

---

### Post by kriti.mysty on 2011-03-14
> **mörgæs said:**
> What happens if you boot the machine and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```?

it says
"dpkg : error processing crossplat formui (-configur):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
crosspl atformui
E: sub-process /usr/bin/dpkg returned an arror code (1)"

what do i do now?

---

### Post by mörgæs on 2011-03-14
You could try to remove the packages giving trouble by 

```
apt-get --purge remove <package>
```

Can you update after this?

Which version of Ubuntu are you using, by the way?

---

