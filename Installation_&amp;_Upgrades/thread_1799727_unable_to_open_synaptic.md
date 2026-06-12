---
title: "unable to open synaptic???"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by lalitha niharika on 2011-07-08
I tried to install google earth, java and some other softwares using bleedingedge.Then process was successful, I restarted my computer.I was unable to open google earth.I tried to open synaptic and got the msg to run "dpkg --configure -a" manually.I did it.Again now I am trying to open synaptic,getting this:(" E: The package sun-java6-jre needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."what should I do???

---

### Post by wojox on 2011-07-08
Open your terminal and try:

```
sudo apt-get install --reinstall sun-java6-jre
```

---

### Post by tommcd on 2011-07-08
Problems like this are a good reason not to try to live on the bleeding edge, especially if you do not know how to troubleshoot problems like this. 

If you stick to what is available in the default Ubuntu repos you will never have problems like this.

---

### Post by lalitha niharika on 2011-07-08
got like this:(

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package sun-java6-jre needs to be reinstalled, but I can't find an archive for it.

---

### Post by dino99 on 2011-07-08
sudo apt-get purge sun-java6-jre
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean

sudo dpkg-reconfigure synaptic

sudo apt-get install openjdk-6-jre

---

### Post by lalitha niharika on 2011-07-08
I just updated system and now synaptic is working!!:)

---

