---
title: "package dependencies? OpenOffice.org-core broken?"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Gyanos422 on 2010-05-17
So i upgraded from 9.10 to 10.04. when i ran update manager after the install, it had some stuff for OpenOffice and during the update it hung. I powered off the laptop and turned it back on, booted into ubuntu and tried over but it didn't list the updates again.  Anyway, i tried to install Ubuntu Tweak and i got an error saying 

```
Broken Dependencies.  Your system has broken dependencies. This application can not continue until this is fixed. To fix it run 'gksudo synaptic' or 'sudo apt-get install -f' in a terminal window.
```When i use 'sudo apt-get install -f' i get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 sdparm linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openoffice.org-common openoffice.org-core
Suggested packages:
  openoffice.org-style-industrial openoffice.org-style-hicontrast
  openoffice.org-style-tango openoffice.org-style-crystal
  openoffice.org-style-oxygen
The following NEW packages will be installed:
  openoffice.org-common
The following packages will be upgraded:
  openoffice.org-core
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/46.2MB of archives.
After this operation, 55.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing openoffice.org-core (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 openoffice.org-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Someone please help!

---

### Post by mikewhatever on 2010-05-17
Try reinstalling openoffice.org-core as suggested:
```
sudo apt-get install --reinstall openoffice.org-core
```

---

### Post by Gyanos422 on 2010-05-17
> **mikewhatever said:**
> Try reinstalling openoffice.org-core as suggested:
```
sudo apt-get install --reinstall openoffice.org-core
```

ok i tried that, and this is what i get.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  openoffice.org-core: Depends: openoffice.org-common (> 1:3.2.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So i tried 'apt-get -f install' and it is sending me in circles.

I don't even want OpenOffice really, if i could completely get rid of it that would also help.

---

### Post by mikewhatever on 2010-05-17
Yeah, looks tricky. There should be a way of forcing the removal of broken packages. How about the following:
```
sudo dpkg -r openoffice.org-core
```

---

### Post by Gyanos422 on 2010-05-17
```
dpkg: error processing openoffice.org-core (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 openoffice.org-core

```

I think i'm just going to re-install ubuntu and see if it helps. I've been at this for almost 12 hours. I can't install anything else until this is resolved so F it, i'll just start over...

---

### Post by Gyanos422 on 2010-05-19
so i just decided to format and start anew. After having trouble starting 10.04 install, a little research led me to a solution. Now my laptop is running Lucid and its feels like a new pc. windows xp just slowed this thing down.  and i'm lucky because its like the only one of this model that accepts the wireless card with linux.

thanks for the help anyway!

---

### Post by gnik1 on 2010-05-22
Could you post your solution please?

I am having a problem with update manager erroring at the end of installations of software. Many threads of trials and no luck. 

Maybe yours will solve the problem.

THanks in advance

---

### Post by Gyanos422 on 2010-05-23
I formatted my hard drive and re-installed fresh. Worked like a charm.

---

### Post by gnik1 on 2010-05-25
I had done the same thing the first time it happened to me. I reinstalled Ubuntu and that solved the same problem in the same way. 
But after a while, the problem has returned again.

Sure would like to understand why it happens and how to resolve the issue without having to reinstall ubuntu.

Thanks for replying.

---

