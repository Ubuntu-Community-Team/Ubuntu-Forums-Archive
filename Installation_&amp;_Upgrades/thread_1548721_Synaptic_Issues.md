---
title: "Synaptic Issues"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by Fender89 on 2010-08-08
It seems that Synaptic did a fail removal the other day. Since then, every time I try use it I get this message and am unable to do any package install/uninstalls.

[IMG]http://i70.photobucket.com/albums/i94/joxley24/Screenshot-Changesapplied.png[/IMG]

---

### Post by wilee-nilee on 2010-08-08
Try these two commands from the terminal.

```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by linux18 on 2010-08-08
if that doesn't work, try:
```
 sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center && sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 
 
```

---

### Post by Fender89 on 2010-08-08
> **linux18 said:**
> if that doesn't work, try:
```
 sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center && sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 
 
```

Tried this and got:

```

W: Failed to fetch http://ppa.launchpad.net/user/ppa-nameppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
```

---

### Post by wilee-nilee on 2010-08-08
Have you tried synaptic again?

---

### Post by Fender89 on 2010-08-08
> **wilee-nilee said:**
> Have you tried synaptic again?

Yes, same result.

---

### Post by Fender89 on 2010-08-08
bump

---

### Post by Fender89 on 2010-08-09
I still haven't been able to resolve this. I still can't add/remove any packages.

---

### Post by jmfal on 2010-08-09
Open  software sources=system>administration>software sources

click> other software, make sure all boxes have check in it

close, might say not up to date>reload 

try synaptic again, still having problems try

sudo apt-get install --fix-missing

sometimes a update does strange things, as the one last thu or fri

Might try rebooting into recovery mode and select >try to fix broken packages<

---

### Post by Fender89 on 2010-08-09
> **jmfal said:**
> Open  software sources=system>administration>software sources

click> other software, make sure all boxes have check in it

close, might say not up to date>reload 

try synaptic again, still having problems try

sudo apt-get install --fix-missing

sometimes a update does strange things, as the one last thu or fri

Might try rebooting into recovery mode and select >try to fix broken packages<

It doesn't seem to think there are any broken packages, yet I keep getting the error in the picture..

---

### Post by jmfal on 2010-08-09
what are you trying to remove?

---

### Post by Fender89 on 2010-08-09
> **jmfal said:**
> what are you trying to remove?

I removed gnokii but it seems to have left something behind that interrupts dpkg and wont allow me to install any new packages or updates, giving that same error every time.

---

