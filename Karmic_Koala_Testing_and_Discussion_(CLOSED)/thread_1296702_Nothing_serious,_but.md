---
title: "Nothing serious, but"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scragar on 2009-10-21
Is there any hope that before karmic is released the liveCD can be updated to include one more step to the package installs which would be to chroot into the new install and reinstall the ubuntu-desktop package so it shows up in apt as being manually installed? It doesn't take long, and it means the next time someone chooses to uninstal evolution or something else which the whole desktop relies on you don't get any serious problems.

You can test this yourself BTW, get a fresh install, try the following commands, choose no when prompted to remove packages, because obviously that's a bad idea on a working system:
```

apt-get --purge autoremove evolution
## result: removes most of the ubuntu desktop because of evolution-dataserver
apt-get --reinstall install ubuntu-desktop
## do it for real, doesn't take long.
apt-get --purge autoremove evolution
## result: doesn't want to remove everything, since it realises the dataserver is needed still.

```

---

### Post by VMC on 2009-10-21
I already uninstalled evolution with no ill effects. I didn't purge though:

$ aptitude show evolution
Package: evolution
State: not installed

---

### Post by scragar on 2009-10-21
> **VMC said:**
> I already uninstalled evolution with no ill effects. I didn't purge though:

$ aptitude show evolution
Package: evolution
State: not installed

That's great, but evolution has multiple dependencies for other things that aren't needed, including evolution-common. Most people right click evolution in synaptic and choose completely remove(hence the autoremove, I added purge because I always purge if I don't want a package), this causes the dependency issues I spoke of. Either the users chicken out of the huge list, or they don't understand and screw up their systems until it get's fixed and they are often scared after that of breaking the system again.

---

### Post by VMC on 2009-10-21
I noticed afterwards that I kept getting updates with evolution as part of the package. I thought at the time some program used parts of evolution. 

I just removed the email client, since I now use Thunderbird.

---

### Post by mc4man on 2009-10-21
Didn't seem to do anything 'bad', and didn't attempt to remove the 'evolution-data-server-common' package which shouldn't be removed
On a fresh install, note the updates

Actually left 2 packages installed that could also be removed

> doug@doug-desktop:~$ sudo apt-get --purge autoremove evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution* evolution-couchdb* evolution-exchange* evolution-indicator*
  evolution-plugins*
0 upgraded, 0 newly installed, 5 to remove and 171 not upgraded.
After this operation, 12.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 118819 files and directories currently installed.)
Removing evolution-plugins ...
Removing evolution-exchange ...
Removing evolution-indicator ...
Removing evolution-couchdb ...
Removing evolution ...
Purging configuration files for evolution ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...

> doug@doug-desktop:~$ sudo apt-get --purge autoremove evolution-common evolution-data-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution-common* evolution-data-server*
0 upgraded, 0 newly installed, 2 to remove and 169 not upgraded.
After this operation, 43.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 118515 files and directories currently installed.)
Removing evolution-common ...
Removing evolution-data-server ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...


---

