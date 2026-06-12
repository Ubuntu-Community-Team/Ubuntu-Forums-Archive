---
title: "Package Manager error"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by mykk.lue on 2007-06-01
I have a IBM ThinkPad T41 running Ubuntu Feisty and i just installed Automatix 2. I chose to install two things and it gave me a error of how it could not be installed.

I got a automatic update from the ubuntu update manager and so i clicked on it. After checking for files etc. i get this error: 

"A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing zope-cmfplacefulworkflow (NewPackage), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"

I can't udpate now, and the icon is on my panel now and won't go away. I also noticed i can't access Synaptic Package Manager, Automatix or i can't update. What can i do to get rid of this error and fix it?

Thanks.

---

### Post by aysiu on 2007-06-01
It sounds as if you're supposed to file a bug report:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by arnieboy on 2007-06-01
> **mykk.lue said:**
> I have a IBM ThinkPad T41 running Ubuntu Feisty and i just installed Automatix 2. I chose to install two things and it gave me a error of how it could not be installed.

I got a automatic update from the ubuntu update manager and so i clicked on it. After checking for files etc. i get this error: 

"A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing zope-cmfplacefulworkflow (NewPackage), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"

I can't udpate now, and the icon is on my panel now and won't go away. I also noticed i can't access Synaptic Package Manager, Automatix or i can't update. What can i do to get rid of this error and fix it?

Thanks.

try doing this:
```
sudo apt-get clean
```
and then do a 
```
sudo apt-get update
```
and post your errors here.

---

### Post by mykk.lue on 2007-06-04
thanks for the reply, but i still get the same error

'E:Dynamic MMap ran out of room, E:Error occurred while processing zope-cmfplacefulworkflow (NewPackage), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by taurus on 2007-06-04
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by arnieboy on 2007-06-04
> **mykk.lue said:**
> thanks for the reply, but i still get the same error

'E:Dynamic MMap ran out of room, E:Error occurred while processing zope-cmfplacefulworkflow (NewPackage), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
Please do the following:
```
sudo gedit /etc/apt/apt.conf
```
and add the following line in the file that opens up (it MIGHT be empty when you open it):
> APT::Cache-Limit 20000000;
Save the file and close it and then do a 
```
sudo apt-get update
```
to see if that fixes the problem.

---

