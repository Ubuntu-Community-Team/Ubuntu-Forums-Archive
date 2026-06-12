---
title: "Cant remove something"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by PoisoN2003 on 2006-06-27
Hey im trying to update wine when i got an error so i tried to remove what was causing it but it just gave me the same thing as when i tried to update wine

poison@ubuntu:~$ sudo apt-get remove rageircd
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  rageircd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1544kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 178788 files and directories currently installed.)
Removing rageircd ...
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "stop" failed.
dpkg: error processing rageircd (--remove):
 subprocess pre-removal script returned error exit status 1
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 rageircd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by LordRaiden on 2006-06-27
Confused about how this is related to wine. Try:


```
sudo apt-get install --reinstall wine
```

---

### Post by PoisoN2003 on 2006-06-27
its not related to wine im asking how i can remove that thing 
poison@ubuntu:~$ sudo apt-get remove rageircd

if i can remove that i wont get a weird error anymore wine works fine

---

### Post by Jasper Houtman on 2006-06-27
Looks like your Rageirc package is broken.
Just start up synaptic and remove it from there. (system > administration > synaptic package manager).

---

### Post by PoisoN2003 on 2006-06-27
weird it doesnt say any are broken....

---

### Post by Jasper Houtman on 2006-06-27
In that case than just type it into search and do a complete removal on the package.

---

### Post by PoisoN2003 on 2006-06-27
gave me an error once again
E: rageircd: subprocess pre-removal script returned error exit status 1

---

### Post by PoisoN2003 on 2006-06-28
bump... anyone has any ideas what i could do?

---

