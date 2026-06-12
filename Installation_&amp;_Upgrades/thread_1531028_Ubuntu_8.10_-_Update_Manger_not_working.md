---
title: "Ubuntu 8.10 - Update Manger not working"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by Greendan on 2010-07-14
Having an issue running update manager in Ubuntu 8.10. If I run it from the GUI it opens, starts building the dependency tree and then closes again, no error message.

In terminal I run apt-get update and get the following error message:
dan@Bones:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Any ideas anyone?

Edit:
Just tried updating some drivers and got this:

dan@Bones:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
[sudo] password for dan: 
Reading package lists... Done
Bus errordependency tree... 0%

---

### Post by dino99 on 2010-07-14
installing with synaptic is an easier way and more stable

into a console, run:

sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by Greendan on 2010-07-14
I should have mentioned that I was having the same issue with Synaptic, but I ran your commands and it is sorted!

Thanks very much!

---

