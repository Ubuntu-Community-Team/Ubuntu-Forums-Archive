---
title: "/var/lib/dpkg/status No such file or directory"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by stanccito on 2011-10-17
I was working on my website,Connected to internet that time,Update  manager show me that there is one package to update,i hit the update  button.But some things goes weird there,and system halt there.i turn it  off by power key restart it.it check some files and state for missing  files,and there i try to restore it.
After that it successfully logon to my account,but when i try to run update manager, it throw error:
"E: Could not open file /var/lib/dpkg/status - open (2 No such file or  directory), E: The package lists or status file could not be parsed or  opened."

I tried add/remove software and synaptic manager also some problem there.
Also search alot for solution, but no luck.
Tried to update the system through terminal and it says:
sudo: dpkg-restore: command not found
sudo apt-get upgrade
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
sudo dpkg-reconfigure -phigh apt
dpkg-query: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: apt is not installed

---

### Post by e79 on 2011-10-17
Try this:

```
sudo mkdir /var/lib/apt/lists-OLD
``````
sudo mv /var/lib/apt/lists/* /var/lib/apt/lists-OLD
``````
sudo apt-get update && sudo apt-get upgrade
```

Hope this helps.

---

### Post by j8a on 2012-05-17
E:Could not open file /var/lib/dpkg/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened.

I cannot run sudo, what can I do?

---

