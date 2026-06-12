---
title: "Can not install any new software 12.04 lts"
date: 2014-10-09
forum: Installation &amp; Upgrades
---

### Post by hark2014 on 2014-10-09
I have a fresh install of 12.04 lts.  I have installed QGIS on it (which I need) but otherwise have done nothing. When I attempt to install any other software from the software center I get the error "items cannoot be installed or removed until the package catalog is repaired do you want to repair now"?

I select yes....
```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 395056 files and directories currently installed.) 
Unpacking grass-core (from .../grass-core_6.4.4-2~precise4_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/grass-core_6.4.4-2~precise4_amd64.deb (--unpack): 
 trying to overwrite '/usr/bin/x-grass', which is also in package grass 6.4.1-1ubuntu2 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for menu ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/grass-core_6.4.4-2~precise4_amd64.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
dpkg: dependency problems prevent configuration of qgis-plugin-grass: 
 qgis-plugin-grass depends on grass644; however: 
  Package grass644 is not installed. 
dpkg: error processing qgis-plugin-grass (--configure): 
 dependency problems - leaving unconfigured 
```

I have tried everything on this [thread]("http://ubuntuforums.org/showthread.php?t=2060379") and get the following error when I attempt sudo apt-get autoremove -f


```
Errors were encountered while processing:
 /var/cache/apt/archives/grass-core_6.4.4-2~precise4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


And get this error when I attempt sudo dpkg --configure -a


```
Errors were encountered while processing:
 qgis-plugin-grass
```

---

### Post by Vladlenin5000 on 2014-10-09
Please post the errors (if any) of:

```
sudo apt-get update
```


How did you installed QGIS? The problem stems from that...

---

### Post by hark2014 on 2014-10-09
I have updated several times.  I installed it using the software center

---

### Post by Vladlenin5000 on 2014-10-09
> **hark2014 said:**
> I have updated several times.  I installed it using the software center
Software Center is only one of the many APT frontends.
I specifically asked for errors, not how many time have you updated.
I also asked (in an edit) how have you installed QGIS because the error stems from that installation and that installation ONLY.

---

