---
title: "Error Uninstalling Amarok"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by ejs7597 on 2008-07-29
Synaptic or any upgrades will not run. It crashes with the following error.

E: amarok: cannot remove file `/usr/share/doc/kde/HTML/pl/amarok/common'

It appears to be trying to remove amarok, but it can not find the folder and crashes. What should I do?

---

### Post by Pumalite on 2008-07-29
Try:
sudo apt-get remove --purge <packagename>
If not:
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by ejs7597 on 2008-07-29
Neither of those commands worked. 
 
dpkg: error processing amarok (--remove):
 cannot remove file `/usr/share/doc/kde/HTML/pl/amarok/common': Not a directory
Errors were encountered while processing:
 amarok

---

### Post by tuxxy on 2008-07-29
Try this command in terminal;

```
sudo apt-get remove amarok*
```

---

### Post by ejs7597 on 2008-07-29
I get the following errors.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting amarok-xine for regex 'amarok*'
Note, selecting amarok-engine for regex 'amarok*'
Note, selecting amarok for regex 'amarok*'
Note, selecting amarok-engines for regex 'amarok*'
The following packages were automatically installed and are no longer required:
  libglitz-glx1 guile-g-wrap libffi4 libglitz1 guile-library g-wrap
  libboost-python1.34.0 libgwrap-runtime0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  amarok
0 upgraded, 0 newly installed, 1 to remove and 112 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by tuxxy on 2008-07-29
Make sure you have closed amarok, and try and terminate it first then run the command again;

```
killall amarok
```

---

### Post by ejs7597 on 2008-07-29
No process to kill same error
amarok: no process killed

---

### Post by Pumalite on 2008-07-29
Close Synaptic or any other apt-get process you might have going.

---

### Post by ejs7597 on 2008-07-29
Closing Synaptic didn't help. Same errors.  Amarok shows up in Synaptic under broken dependencies. When I mark it for reinstallation I get the following errors.

E: /var/cache/apt/archives/amarok_2%3a1.4.7-0ubuntu3_i386.deb: trying to overwrite `/usr/share/doc/kde/HTML/da', which is also in package konversation

---

### Post by ejs7597 on 2008-07-29
When I run update manager I get the following error.

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by tuxxy on 2008-07-29
This maybe of use to you 

[http://norimuramei.multiply.com/journal/item/12](http://norimuramei.multiply.com/journal/item/12)

---

