---
title: "Bandwidthd Will Not let me Uninstall"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by ayoalex on 2010-11-06
I am trying to update my bandwidthd but it says that i should reinstall it, but when i do that it just throws me an error. I am running Ubuntu 10.04 in case it helps. I am getting really frustrated by this and don't know to fix it because it wont let me uninstall, reinstall, upgrade, or update. Please help me!! Thank you!

---

### Post by yeats on 2010-11-06
Can you post the specific error messages you're getting?

---

### Post by ayoalex on 2010-11-06
This comes up when i click removal:

dpkp: error processing bandwidthd (--remove):
Package is in a very bad inconsistent state - you should reinstall it before attempting a removal.

but in Synaptic it won't let me selected it as mark for re-installation.

---

### Post by ironic.demise on 2010-11-06
try sudo apt-get remove bandwidth

---

### Post by ayoalex on 2010-11-06
Just tried that and got this


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bandwidth

---

### Post by ironic.demise on 2010-11-06
> **ayoalex said:**
> Just tried that and got this


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bandwidth
Sorry I meant bandwidth*d*
```
sudo apt-get remove bandwidthd
sudo apt-get update
sudo apt-get install bandwidthd
sudo apt-get upgrade
```

Hope helps

---

### Post by ayoalex on 2010-11-06
sorry yeah i wasn't even thinking and just copied what you put into the terminal but any way it STILL didn't work. This is what i got : 

when i type in sudo apt-get remove bandwidthd

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bandwidth
alexander@alexander-laptop:~$ sudo apt-get remove bandwidthd
[sudo] password for alexander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bandwidthd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing bandwidthd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by yeats on 2010-11-06
Try (in a terminal):

```
sudo apt-get -f install
```

and see if that helps.

---

### Post by yeats on 2010-11-06
You might also look at this thread:

[http://ubuntuforums.org/showthread.php?t=500229](http://ubuntuforums.org/showthread.php?t=500229)

---

### Post by ironic.demise on 2010-11-07
```
sudo apt-get install bandwidthd
sudo apt-get upgrade bandwidthd
sudo apt-get remove bandwidthd
```

---

### Post by ironic.demise on 2010-11-07
```
sudo apt-get install bandwidthd
sudo apt-get upgrade bandwidthd
sudo apt-get remove bandwidthd
```

---

