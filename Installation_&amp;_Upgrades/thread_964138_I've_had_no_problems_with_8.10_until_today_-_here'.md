---
title: "I've had no problems with 8.10 until today - here's the issue"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by hyper7 on 2008-10-30
After running

```
sudo apt-get dist-upgrade
```

I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up base-files (4.0.4ubuntu2.1) ...
find: `/var/cache/fonts': No such file or directory
find: `/var/cache/anthy': No such file or directory
chgrp 0 /etc/dictionaries-common/words 
chgrp: cannot dereference `/etc/dictionaries-common/words': No such file or directory
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 123
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm sure I'm overlooking something simple, but I haven't the slightest what it might be.

I've searched and not found a satisfying resolution.

:confused:

---

### Post by hyper7 on 2008-10-30
bump

---

### Post by coolwolf455 on 2008-11-01
I went into synaptic package manager did a search for base-files.
I selected base-files then went up to Package->Force Version.
I selected 4.0.4ubuntu2(intrepid) from the drop down menu then clicked force version, then click apply at the top of synaptic.
After it downgrades the base -files click on "mark all upgrades" button but before you apply them go back into the list and find base-files click on the check box and select "unmark" then apply. The base files must be corrupt so ubuntu will have to fix them and then send them out again. you will just have to ignore the update notices for now. for anyone who uses update manager unselect the base files update for now.

---

