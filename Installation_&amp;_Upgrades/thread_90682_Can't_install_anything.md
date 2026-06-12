---
title: "Can't install anything"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by cigarette_burn on 2005-11-15
I lost my OS so I reinstalled and ran apt-get update. I then began to install XMMS etc... but it all told my to run apt-get update. When I did I got this:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Anyone have any ideas? I can't download/install anything and update won't run at all.

---

### Post by Sheco on 2005-11-15
there's another process of apt-get/aptitude/synaptic or a package manager already running, either close it/kill it/reboot.

Either that or youre not running as a privileged used (sudo)

---

### Post by lmandrake on 2005-11-15
You should go with ```
sudo apt-get update
``` and then ```
sudo apt-get install XY
```. For good reasons it's forbidden to install software with normal user rights.

---

### Post by linbetwin on 2005-11-15
You probably have Synaptic, or Update Manager, or Add Applications open, that is why apt-get can't lock the list directory.
 
You must have only one of these applications open. To install xmms you should enable the universe repository in Synaptic.

---

